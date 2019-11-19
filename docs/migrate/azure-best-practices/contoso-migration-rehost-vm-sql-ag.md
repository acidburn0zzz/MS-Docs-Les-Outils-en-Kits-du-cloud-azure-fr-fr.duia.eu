---
title: Réhéberger une application en la migrant vers des machines virtuelles Azure et des groupes de disponibilité Always On SQL Server
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment Contoso réhéberge une application locale en la migrant vers des machines virtuelles Azure et des groupes de disponibilité Always On SQL Server.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: fdde1d3619b8340fad31f4241bffeff9c51f0b38
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566519"
---
# <a name="rehost-an-on-premises-app-on-azure-vms-and-sql-server-always-on-availability-groups"></a>Réhéberger une application locale sur des machines virtuelles Azure et des groupes de disponibilité Always On SQL Server

Cet article explique comment la société fictive Contoso réhéberge une application Windows .NET à deux niveaux qui s’exécute sur des machines virtuelles VMware dans le cadre d’une migration vers Azure. Contoso effectue une migration de la machine virtuelle frontale de l’application vers une machine virtuelle Azure et de la base de données de l’application vers une machine virtuelle Azure SQL Server s’exécutant dans un cluster de basculement Windows Server avec des groupes de disponibilité Always On SQL Server.

L’application SmartHotel360 utilisée dans cet exemple est fournie au format open source. Si vous souhaitez l’utiliser à des fins de test, vous pouvez la télécharger à partir de [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat qu’ils souhaitent obtenir avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso étant en croissance, son infrastructure et ses systèmes locaux subissent une pression.
- **Gagner en efficacité.** Contoso doit supprimer les procédures inutiles et rationaliser les processus pour les développeurs et les utilisateurs. L’entreprise a besoin d’une informatique rapide et doit éviter de perdre du temps ou d’argent en répondant plus rapidement aux exigences des clients.
- **Gagner en agilité.** le service informatique de Contoso doit être plus réactif face aux besoins de l’entreprise. Elle doit être en mesure de réagir plus rapidement que l’évolution du marché pour réussir dans une économie mondiale. L’informatique ne doit pas devenir une entrave à l’activité.
- **Mise à l’échelle** à mesure que l’entreprise croît, le service informatique de Contoso doit fournir des systèmes capables de croître au même rythme.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a épinglé les objectifs de cette migration. Ces objectifs ont été utilisés pour déterminer la meilleure méthode de migration :

- Après la migration, l’application dans Azure devra offrir les mêmes performances qu’aujourd’hui dans l’environnement VMware. L’application restera tout aussi vitale dans le cloud que localement.
- Contoso ne souhaite pas investir dans cette application. Elle est importante pour l’activité mais, sous sa forme actuelle, Contoso veut simplement la migrer de manière sécurisée vers le cloud.
- La base de données locale de l’application a connu des problèmes de disponibilité. Contoso souhaite qu’elle soit déployée dans Azure en tant que cluster de haute disponibilité, avec des fonctionnalités de basculement.
- Contoso souhaite mettre à niveau de sa plateforme SQL Server 2008 R2 actuelle vers SQL Server 2017.
- Contoso ne souhaite pas utiliser Azure SQL Database pour cette application et recherche des alternatives.

## <a name="solution-design"></a>Conception de la solution

Après avoir défini précisément les objectifs et exigences, Contoso conçoit et examine une solution de déploiement, et identifie le processus de migration, notamment les services Azure à utiliser pour la migration.

### <a name="current-architecture"></a>Architecture actuelle

- L’application est hiérarchisée sur deux machines virtuelles (WEBVM et SQLVM).
- Les machines virtuelles sont situées sur un hôte VMware ESXi **contosohost1.contoso.com** (version 6.5).
- L’environnement VMware est géré par le serveur vCenter Server 6.5 (**vcenter.contoso.com**) s’exécutant sur une machine virtuelle.
- Contoso dispose d’un centre de données local (contoso-datacenter), avec un contrôleur de domaine local (**contosodc1**).

### <a name="proposed-architecture"></a>Architecture proposée

Dans ce scénario :

- Contoso migrera le WEBVM frontal d’application vers une machine virtuelle IaaS Azure.
  - La machine virtuelle frontale dans Azure sera déployée dans le groupe de ressources ContosoRG (utilisé pour les ressources de production).
  - Elle se trouvera dans le réseau de production Azure (VNET-PROD-EUS2) dans la région East US2 principale.
- La base de données de l’application va être migrée vers une machine virtuelle Azure SQL Server.
  - Elle se trouvera dans le réseau de base de données Azure de Contoso (PROD-DB-EUS2) dans la région East US2 principale.
  - Elle sera placée dans un cluster de basculement Windows Server à deux nœuds, qui utilise les groupes de disponibilité Always On SQL Server.
  - Dans Azure, les deux nœuds de machine virtuelle SQL Server du cluster seront déployés dans le groupe de ressources ContosoRG.
  - Ils se trouveront dans le réseau de production Azure (VNET-PROD-EUS2) dans la région East US2 principale.
  - Les machines virtuelles exécuteront Windows Server 2016 avec l’édiction Entreprise de SQL Server 2017. Contoso n’a pas de licences pour ce système d’exploitation et utilisera donc une image dans la place de marché Azure qui fournit la licence associée à un contrat d’entreprise contre paiement.
  - Indépendamment de noms uniques, les deux machines virtuelles utilisent les mêmes paramètres.
- Contoso va déployer un équilibreur de charge interne qui écoute le trafic sur le cluster et le dirige vers le nœud de cluster approprié.
  - L’équilibreur de charge interne sera déployé dans ContosoNetworkingRG (utilisé pour les ressources de mise en réseau).
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

![Architecture du scénario](media/contoso-migration-rehost-vm-sql-ag/architecture.png)

### <a name="database-considerations"></a>Considérations liées à la base de données

Dans le cadre de la conception de la solution, Contoso a fait une comparaison des fonctionnalités entre Azure SQL Database et SQL Server. Les administrateurs ont choisi une machine virtuelle Azure Iaas exécutant SQL Server sur la base des considérations suivantes :

- L’utilisation d’une machine virtuelle Azure exécutant SQL Server semble être une bonne solution si Contoso a besoin de personnaliser le système d’exploitation ou le serveur de base de données, ou s’il souhaite colocaliser et exécuter des applications tierces sur la même machine virtuelle.
- À l’aide de l’Assistant Migration des données, Contoso peut facilement évaluer et migrer vers une base de données Azure SQL.

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant une liste des avantages et des inconvénients.

<!-- markdownlint-disable MD033 -->

**Considération** | **Détails**
--- | ---
**Avantages** | WEBVM est déplacé vers Azure sans changement, ce qui simplifie la migration.<br/><br/> Le niveau SQL Server s’exécute sur SQL Server 2017 et Windows Server 2016. Ceci rend obsolète leur système d’exploitation Windows Server 2008 R2 en cours d’exécution. SQL Server 2017 prend en charge les spécifications techniques et les objectifs de Contoso. Il assure une compatibilité intégrale lors de la migration depuis SQL Server 2008 R2.<br/><br/> Contoso peut tirer profit de son investissement dans Software Assurance en utilisant Azure Hybrid Benefit.<br/><br/> Un déploiement SQL Server haute disponibilité dans Azure assure une tolérance de panne afin que la couche de données d’application ne soit plus un point de basculement unique.
**Inconvénients** | WEBVM exécute Windows Server 2008 R2. Le système d’exploitation est pris en charge par Azure pour certains rôles (juillet 2018). [Plus d’informations](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines)<br/><br/> La couche web de l’application reste un point de basculement unique.<br/><br/> Contoso devra continuer à prendre en charge la couche web comme une machine virtuelle Azure au lieu d’opter pour un service managé, comme Azure App Service.<br/><br/> Avec la solution choisie, Contoso devra continuer à gérer deux machines virtuelles SQL Server au lieu de passer à une plateforme managée comme Azure SQL Database Managed Instance. En outre, avec Software Assurance, Contoso pourrait remplacer leurs licences existantes par des tarifs préférentiels sur Azure SQL Database Managed Instance.

<!-- markdownlint-enable MD033 -->

### <a name="azure-services"></a>Services Azure

**Service** | **Description** | **Coût**
--- | --- | ---
[Assistant de migration des données](https://docs.microsoft.com/sql/dma/dma-overview?view=ssdt-18vs2017) | DMA s’exécute localement depuis l’ordinateur SQL Server sur site et migre la base de données sur un VPN de site à site vers Azure. | DMA est un outil téléchargeable gratuitement.
[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery) | Site Recovery orchestre et gère la migration et la récupération d’urgence pour les machines virtuelles Azure, les machines virtuelles locales et les serveurs physiques. | Lors de la réplication vers Azure, des frais sur le Stockage Azure sont facturés. Des machines virtuelles Azure sont créées en cas de basculement, et entraînent des frais. [En savoir plus](https://azure.microsoft.com/pricing/details/site-recovery) sur les frais et la tarification.

## <a name="migration-process"></a>Processus de migration

L’équipe d’administrateurs de Contoso migre les machines virtuelles de l’application vers Azure.

- Elle migrera la machine virtuelle frontale vers la machine virtuelle Azure à l’aide de Site Recovery :
  - Dans un premier temps, elle va préparer et configurer les composants Azure et préparer l’infrastructure VMware locale.
  - Une fois tous les éléments préparés, la réplication de la machine virtuelle peut commencer.
  - Lorsque la réplication est activée et opère, la machine virtuelle est mígrée en la basculant vers Azure.
- Elle va migrer la base de données vers un cluster SQL Server dans Azure, à l’aide de l’Assistant Migration de données (DMA).
  - Dans un premier temps, elle doit approvisionner les machines virtuelles SQL Server dans Azure et configurer le cluster, un équilibreur de charge interne et des groupes de disponibilité Always On.
  - Lorsque tout cela est en place, on peut migrer la base de données.
- Après la migration, l’équipe activera la protection Always On pour la base de données.

![Processus de migration](media/contoso-migration-rehost-vm-sql-ag/migration-process.png)

## <a name="prerequisites"></a>Prérequis

Voici ce que doit faire Contoso pour ce scénario.

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
**Abonnement Azure** | Contoso a déjà créé un abonnement dans un précédent article de cette série. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions.<br/><br/> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur.<br/><br/> S’il vous faut plus d’autorisations granulaires, consultez [cet article](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infrastructure Azure** | [Découvrez comment](./contoso-migration-infrastructure.md) Contoso configure une infrastructure Azure.<br/><br/> Apprenez-en davantage sur les configurations de [réseau](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#network) et de [stockage](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#storage) requises pour Site Recovery.
**Site Recovery (local)** | L’instance vCenter Server locale doit exécuter la version 5.5, 6.0 ou 6.5.<br/><br/> Un hôte ESXi qui exécute la version 5.5, 6.0 ou 6.5<br/><br/> Une ou plusieurs machines virtuelles VMware exécutées sur l’hôte ESXi.<br/><br/> Les machines virtuelles doivent répondre aux [exigences Azure](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#azure-vm-requirements).<br/><br/> Configuration [réseau](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#network) et [stockage](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#storage) prise en charge.<br/><br/> Les machines virtuelles que vous souhaitez répliquer doivent satisfaire aux [conditions requises par Azure](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#azure-vm-requirements).

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment Contoso exécutera la migration :

> [!div class="checklist"]
>
> - **Étape 1 : Préparer un cluster.** créez un cluster pour le déploiement de deux nœuds de machine virtuelle SQL Server dans Azure.
> - **Étape 2 : Déployer et configurer le cluster.** préparez un cluster Azure SQL Server. Les bases de données sont migrées vers ce cluster existant.
> - **Étape 3 : Déployer l’équilibreur de charge.** déployez un équilibreur de charge pour équilibrer le trafic vers les nœuds SQL Server.
> - **Étape 4 : Préparer Azure pour Site Recovery.** créez un compte de stockage Azure pour accueillir les données répliquées et un coffre Recovery Services.
> - **Étape 5 : Préparer une machine virtuelle VMware locale pour Site Recovery.** préparez des comptes pour la découverte de machines virtuelles et l’installation d’agents. Préparez les machines virtuelles locales afin que les utilisateurs puissent se connecter aux machines virtuelles Azure après la migration.
> - **Étape 6 : Répliquer les machines virtuelles.** activez la réplication des machines virtuelles sur Azure.
> - **Étape 7 : Installer l’Assistant Migration de données.** Téléchargez et installez l’Assistant Migration de données.
> - **Étape 8 : Migrer la base de données avec DMA.** migrez la base de données vers Azure.
> - **Étape 9 : Protéger la base de données.** Créez un groupe de disponibilité Always On pour le cluster.
> - **Étape 10 : Migrer la machine virtuelle d’application web.** Exécutez un test de basculement afin de vérifier que tout fonctionne bien. Procédez ensuite au basculement complet vers Azure.

## <a name="step-1-prepare-a-sql-server-always-on-availability-group-cluster"></a>Étape 1 : Préparer un cluster de groupes de disponibilité Always On SQL Server

Les administrateurs de Contoso configurent le cluster de la façon suivante :

1. Deux machines virtuelles SQL Server sont créées en sélectionnant l’image de SQL Server 2017 Enterprise Windows Server 2016 dans la place de marché Azure.

    ![Référence SKU de la machine virtuelle SQL](media/contoso-migration-rehost-vm-sql-ag/sql-vm-sku.png)

2. Dans l’**Assistant Créer une machine virtuelle** > **Fonctions de base**, on configure :

    - Noms pour les machines virtuelles : **SQLAOG1** et **SQLAOG2**.
    - Étant donné que les machines sont vitales pour l’entreprise, on active SSD comme type de disque de machine virtuelle.
    - Des informations d’identification sont spécifiées pour la machine.
    - Les machines virtuelles sont déployées dans la région primaire USA Est 2, dans le groupe de ressources ContosoRG.

3. Dans **Taille**, on commence par la référence SKU D2s_V3 pour les deux machines virtuelles. Elles seront mises à l’échelle ultérieurement, en fonction des besoins.
4. Dans **Paramètres**, on procède comme suit :

    - Étant donné que ces machines virtuelles sont des bases de données critiques pour l’application, des disques disque managé sont utilisés.
    - Les machines sont placées dans le réseau de production de la région primaire USA Est 2(**VNET-PROD-EUS2**), dans le sous-réseau de la base de données (**PROD-DB-EUS2**).
    - Un nouveau groupe à haute disponibilité est créé : **SQLAOGAVSET**, avec deux domaines d’erreur et cinq domaines de mise à jour.

      ![Machine virtuelle SQL](media/contoso-migration-rehost-vm-sql-ag/sql-vm-settings.png)

5. Dans **Paramètres SQL Server**, la connectivité SQL sur le réseau virtuel (privé) est limitée sur le port par défaut 1433. Pour l’authentification, les mêmes informations d’identification que sur le site sont utilisées (**contosoadmin**).

    ![Machine virtuelle SQL](media/contoso-migration-rehost-vm-sql-ag/sql-vm-db.png)

**Besoin de plus d’aide ?**

- [Obtenir de l’aide](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#1-configure-basic-settings) pour l’approvisionnement d’une machine virtuelle SQL Server.
- [En savoir plus sur la](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-availability-group-prereq#create-sql-server-vms) configuration de machines virtuelles pour les différentes références SKU de SQL Server.

## <a name="step-2-deploy-and-set-up-the-cluster"></a>Étape 2 : Déployer et configurer le cluster

Voici comment procèdent les administrateurs de Contoso pour configurer le cluster :

1. Un compte de stockage Azure est configuré en tant que le témoin de cloud.
2. Les machines virtuelles SQL Server sont ajoutées au domaine Active Directory dans le centre de données local Contoso.
3. Le cluster est créé dans Azure.
4. Le témoin cloud est configuré.
5. Enfin, les groupes de disponibilité SQL Always On sont activés.

### <a name="set-up-a-storage-account-as-cloud-witness"></a>Configurer un compte de stockage en tant que témoin de cloud

Pour configurer un témoin de cloud, Contoso a besoin d’un compte de stockage Azure qui contiendra le fichier blob utilisé pour l’arbitrage du cluster. Le même compte de stockage peut être utilisé afin de configurer un témoin cloud pour plusieurs clusters.

Les administrateurs de Contoso créent un compte de stockage de la façon suivante :

1. Un nom identifiable est spécifié pour le compte (**contosocloudwitness**).
2. Un compte polyvalent général est déployé, avec stockage localement redondant (LRS).
3. Ce compte est placé dans une région tierce, à savoir les USA Centre Sud. Il est placé en dehors des régions primaire et secondaire et reste donc disponible en cas de panne régionale.
4. Il se trouve dans le groupe de ressources de Contoso, qui contient les ressources d’infrastructure, **ContosoInfraRG**.

    ![Témoin de cloud](media/contoso-migration-rehost-vm-sql-ag/witness-storage.png)

5. Lors de la création du compte de stockage, des clé d'accès principale et secondaire sont générées pour lui. La clé d’accès principale est nécessaire pour créer le témoin de cloud. La clé s’affiche sous le nom du compte de stockage > **Clés d’accès**.

    ![Clé d’accès](media/contoso-migration-rehost-vm-sql-ag/access-key.png)

### <a name="add-sql-server-vms-to-contoso-domain"></a>Ajouter des machines virtuelles SQL Server au domaine Contoso

1. Contoso ajoute SQLAOG1 et SQLAOG2 au domaine contoso.com.
2. Ensuite, sur chaque machine virtuelle le cluster de basculement et les outils Windows sont installés.

### <a name="set-up-the-cluster"></a>Configurer le cluster

Avant de configurer le cluster, les administrateurs prennent un instantané du disque du système d’exploitation sur chaque machine.

![instantané](media/contoso-migration-rehost-vm-sql-ag/snapshot.png)

1. Ensuite, elle exécute un script assemblé pour créer le cluster de basculement Windows.

    ![Créer un cluster](media/contoso-migration-rehost-vm-sql-ag/create-cluster1.png)

2. Après la création du cluster, on vérifie que les machines virtuelles s’affichent en tant que nœuds de cluster.

     ![Créer un cluster](media/contoso-migration-rehost-vm-sql-ag/create-cluster2.png)

### <a name="configure-the-cloud-witness"></a>Configurer le témoin de cloud

1. Les administrateurs configurent le témoin de cloud à l’aide de l’**Assistant de configuration de quorum** dans le gestionnaire du cluster de basculement.
2. Dans l’Assistant, on sélectionne un témoin de cloud avec le compte de stockage.
3. Une fois que le témoin de cloud est configuré, il s’affiche dans le composant logiciel enfichable Gestionnaire du Cluster de basculement.

    ![Témoin de cloud](media/contoso-migration-rehost-vm-sql-ag/cloud-witness.png)

### <a name="enable-sql-server-always-on-availability-groups"></a>Activer les groupes de disponibilité SQL Server Always On

Les administrateurs peuvent désormais activer Always On :

1. Dans le Gestionnaire de configuration SQL Server, les **groupes de disponibilité Always On** sont activés pour le service **SQL Server (MSSQLSERVER)** .

    ![Activer Always On](media/contoso-migration-rehost-vm-sql-ag/enable-alwayson.png)

2. Le service est redémarré pour que les modifications prennent effet.

Une fois la solution Always On activée, Contoso peut configurer le groupe de disponibilité Always On qui protègera la base de données SmartHotel360.

**Besoin de plus d’aide ?**

- [En savoir plus sur](https://docs.microsoft.com/windows-server/failover-clustering/deploy-cloud-witness) le témoin de cloud et la configuration d’un compte de stockage pour celui-ci.
- [Obtenir des instructions](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-availability-group-tutorial) pour la configuration d’un cluster et la création d’un groupe de disponibilité.

## <a name="step-3-deploy-the-azure-load-balancer"></a>Étape 3 : Déployer Azure Load Balancer

Les administrateurs souhaitent maintenant déployer un équilibreur de charge interne situé devant les nœuds de cluster. L’équilibrage de charge écoute le trafic et le dirige vers le nœud approprié.

![Équilibrage de la charge](media/contoso-migration-rehost-vm-sql-ag/architecture-lb.png)

L’équilibrage de charge est créé comme suit :

1. Dans le Portail Azure > **Mise en réseau** > **Équilibreur de charge**, un nouvel équilibreur de charge interne est configuré : **ILB-PROD-DB-EUS2-SQLAOG**.
2. L’équilibreur de charge est placé dans le réseau de production **VNET-PROD-EUS2**, dans le sous-réseau de base de données **PROD-DB-EUS2**.
3. Une adresse IP statique lui est affectée : 10.245.40.100.
4. En tant qu’élément de mise en réseau, l’équilibreur de charge est déployé dans le groupe de ressources de mise en réseau **ContosoNetworkingRG**.

    ![Équilibrage de la charge](media/contoso-migration-rehost-vm-sql-ag/lb-create.png)

Après le déploiement de l’équilibreur de charge interne, ils doivent le configurer. Ils créent un pool d’adresses principal et configurent un probe d’intégrité et une règle d’équilibrage de charge.

### <a name="add-a-back-end-pool"></a>Ajouter un pool principal

Pour distribuer le trafic vers les machines virtuelles du cluster, les administrateurs de Contoso configurent un pool d’adresses principal qui contient les adresses IP des cartes réseau pour les machines virtuelles qui recevront le trafic à partir de l’équilibreur de charge.

1. Dans les paramètres de l’équilibreur de charge dans le portail, Contoso ajoute un pool principal : **ILB-PROD-DB-EUS-SQLAOG-BEPOOL**.
2. Il associe le pool au groupe à haute disponibilité SQLAOGAVSET. Les machines virtuelles dans l’ensemble (**SQLAOG1** et **SQLAOG2**) sont ajoutées au pool.

    ![Pool de back-ends](media/contoso-migration-rehost-vm-sql-ag/backend-pool.png)

### <a name="create-a-health-probe"></a>Créer une sonde d’intégrité

Les administrateurs créent une sonde d’intégrité pour permettre à l’équilibreur de charge de surveiller l’état de l’application. La sonde d’intégrité ajoute ou supprime dynamiquement des machines virtuelles de la rotation de l’équilibreur de charge en fonction de leur réponse aux vérifications d’intégrité.

La sonde est créée comme suit :

1. Dans les paramètres de l’équilibreur de charge dans le portail, Contoso crée une sonde d’intégrité : **SQLAlwaysOnEndPointProbe**.
2. La sonde est configurée pour surveiller les machines virtuelles sur le port TCP 59999.
3. Un intervalle de 5 secondes et un seuil de 2 sont définis entre les sondes. Si deux sondes échouent, la machine virtuelle est considérée comme défectueuse.

    ![Sonde](media/contoso-migration-rehost-vm-sql-ag/nlb-probe.png)

### <a name="configure-the-load-balancer-to-receive-traffic"></a>Configurer l’équilibreur de charge pour recevoir le trafic

Les administrateurs de Contoso ont maintenant besoin d’une règle d’équilibreur de charge pour définir la distribution du trafic vers les machines virtuelles.

- L’adresse IP frontale gère le trafic entrant.
- Le pool d’IP principal reçoit le trafic.

La règle est créée comme suit :

1. Dans les paramètres de l’équilibreur de charge dans le portail, une nouvelle règle d’équilibrage de charge est ajoutée : **SQLAlwaysOnEndPointListener**.
2. Ils définissent un écouteur frontal pour recevoir le trafic entrant du client SQL sur TCP 1433.
3. Ils spécifient le pool principal vers lequel le trafic sera acheminé et le port sur lequel les machines virtuelles écoutent le trafic.
4. Ils activent l’adresse IP flottante (retour direct du serveur). Cela est toujours nécessaire pour SQL Always On.

    ![Sonde](media/contoso-migration-rehost-vm-sql-ag/nlb-probe.png)

**Besoin de plus d’aide ?**

- [Obtenez une vue d’ensemble](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview) d’Azure Load Balancer.
- [En savoir plus sur la](https://docs.microsoft.com/azure/load-balancer/tutorial-load-balancer-basic-internal-portal) création d’un équilibreur de charge.

## <a name="step-4-prepare-azure-for-the-site-recovery-service"></a>Étape 4 : Préparer Azure pour le service Site Recovery

Les composants Azure dont Contoso a besoin pour déployer Site Recovery sont les suivants :

- Un réseau virtuel dans lequel les machines virtuelles seront situées après leur création pendant le basculement.
- Un compte de stockage Azure pour accueillir les données répliquées.
- Un coffre Recovery Services dans Azure.

Ils configurent cela comme suit :

1. Contoso a déjà crée un réseau/sous-réseau utilisable pour Site Recovery lors du [déploiement de l’infrastructure Azure](./contoso-migration-rehost-vm-sql-ag.md).

    - L’application SmartHotel360 est une application de production, et WEBVM sera migrée vers le réseau de production Azure (VNET-PROD-EUS2) dans la région USA Est 2 principale.
    - La machine virtuelle WEBVM sera placée dans le groupe de ressources ContosoRG utilisé pour les ressources de production et dans le sous-réseau de production (PROD-FE-EUS2).

2. Les administrateurs créent un compte de stockage Azure (contosovmsacc20180528) dans la région principale.

    - Ils utilisent un compte à usage général, avec un stockage standard et une réplication de stockage localement redondant.
    - Ce compte doit se trouver dans la même région que le coffre.

      ![Stockage Site Recovery](media/contoso-migration-rehost-vm-sql-ag/asr-storage.png)

3. Avec le réseau et le compte de stockage en place, Contoso crée à présent un coffre Recovery Services (**ContosoMigrationVault**) et le place dans le groupe de ressources **ContosoFailoverRG**, dans la région USA Est 2 principale.

    ![Coffre Recovery Services](media/contoso-migration-rehost-vm-sql-ag/asr-vault.png)

**Besoin de plus d’aide ?**

[En savoir plus sur la](https://docs.microsoft.com/azure/site-recovery/tutorial-prepare-azure) configuration d’Azure pour Site Recovery.

## <a name="step-5-prepare-on-premises-vmware-for-site-recovery"></a>Étape 5 : Préparer VMware en local pour Site Recovery

Voici ce que les administrateurs de Contoso préparent localement :

- Un compte sur le serveur vCenter ou sur l’hôte vSphere ESXi pour automatiser la détection de machines virtuelles.
- Un compte permettant l’installation automatique du service Mobilité sur les machines virtuelles VMware à répliquer.
- Des paramètres de machine virtuelle locale pour que Contoso puisse se connecter aux machines virtuelles Azure répliquées après le basculement.

### <a name="prepare-an-account-for-automatic-discovery"></a>Préparer un compte pour la découverte automatique

Site Recovery doit pouvoir accéder aux serveurs VMware pour :

- Détectez automatiquement les machines virtuelles.
- Orchestrer la réplication, le basculement et la restauration automatique.
- Au moins un compte en lecture seule est nécessaire. Il vous faut un compte qui peut exécuter des opérations telles que la création et la suppression de disques, et l’allumage de machines virtuelles.

Les administrateurs de Contoso configurent le compte de la façon suivante :

1. Ils créent un rôle au niveau du vCenter.
2. Ils attribuent ensuite à ce rôle les autorisations nécessaires.

### <a name="prepare-an-account-for-mobility-service-installation"></a>Préparer un compte pour l’installation du service Mobilité

Le service Mobilité doit être installé sur chaque machine virtuelle.

- Site Recovery peut faire une installation automatique par push de ce composant lorsque la réplication est activée pour la machine virtuelle.
- Vous avez besoin d’un compte dont Site Recovery pourra se servir pour accéder à la machine virtuelle pour l’installation par push. Vous spécifiez ce compte quand vous configurez la réplication dans la console d’Azure.
- Il vous faut un compte de domaine ou local avec les autorisations nécessaires pour l’installation sur la machine virtuelle.

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Préparer la connexion aux machines virtuelles Azure après le basculement

Après le basculement, Contoso souhaite pouvoir se connecter à des machines virtuelles Azure. Pour ce faire, les administrateurs effectuent les opérations suivantes avant la migration :

1. Pour l’accès via Internet :

   - Elle active le protocole RDP sur la machine virtuelle locale avant le basculement.
   - Elle s’assure que les règles de TCP et UDP sont ajoutées au profil **Public**.
   - Elle vérifie que le protocole RDP est autorisé dans **Pare-feu Windows** > **Applications autorisées** pour tous les profils.

2. Pour l’accès via le VPN de site à site :

   - Elle active le protocole RDP sur l’ordinateur local.
   - Elle autorise le protocole RDP dans **Pare-feu Windows** -> **Applications et fonctionnalités autorisées** pour les réseaux **Domaine et privé**.
   - Elle définit la stratégie SAN du système d’exploitation sur la machine virtuelle locale sur **OnlineAll**.

De plus, quand elle opèrent un basculement, elle doit vérifier les points suivants :

- Aucune mise à jour de Windows ne peut être en attente sur la machine virtuelle lors du déclenchement d’un basculement. Autrement, les utilisateurs ne pourront pas se connecter à la machine virtuelle avant la fin de la mise à jour.
- Après basculement, on peut consulter les **diagnostics de démarrage** pour afficher une capture d’écran de la machine virtuelle. Si cela ne fonctionne pas, il faut vérifier que la machine virtuelle est en cours d’exécution et consulter ces [conseils de dépannage](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

**Besoin de plus d’aide ?**

- [En savoir plus sur la](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial-prepare-on-premises#prepare-an-account-for-automatic-discovery) création et l’attribution d’un rôle pour la détection automatique.
- [En savoir plus sur la](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial-prepare-on-premises#prepare-an-account-for-mobility-service-installation) création d’un compte pour une installation push du service Mobilité.

## <a name="step-6-replicate-the-on-premises-vms-to-azure-with-site-recovery"></a>Étape 6 : Répliquer les machines virtuelles locales sur Azure avec Site Recovery

Avant de pouvoir exécuter une migration vers Azure, les administrateurs doivent configurer et activer la réplication.

### <a name="set-a-replication-goal"></a>Définir un objectif de réplication

1. Dans le coffre, sous le nom du coffre (ContosoVMVault), on définit un objectif de réplication (**Prise en main** > **Site Recovery** > **Préparer l’infrastructure**).
2. On spécifie que les ordinateurs sont situés localement, qu’ils s’exécutent sur VMware et qu’ils sont répliqués sur Azure.

    ![Objectif de réplication](./media/contoso-migration-rehost-vm-sql-ag/replication-goal.png)

### <a name="confirm-deployment-planning"></a>Confirmer la planification d’un déploiement

Pour continuer, il faut confirmer que la planification du déploiement est terminée en sélectionnant **Yes, I have done it** (Oui, c’est fait). Dans ce scénario, Contoso ne migre qu’une machine virtuelle et n’a pas besoin de planification du déploiement.

### <a name="set-up-the-source-environment"></a>Configurer l’environnement source

Ils doivent maintenant configurer leur environnement source. Pour ce faire, elle télécharge un modèle OVF et l’utilise pour déployer le serveur de configuration Site Recovery comme étant une machine virtuelle VMware locale hautement disponible. Une fois le serveur de configuration opérationnel, Contoso l’inscrit dans le coffre.

Le serveur de configuration exécute plusieurs composants :

- Le composant de serveur de configuration qui coordonne la communication entre les ordinateurs locaux et Azure, et gère la réplication des données.
- Le serveur de traitement qui fait office de passerelle de réplication. Il reçoit les données de réplication, les optimise grâce à la mise en cache, la compression et le chiffrement et les envoie vers le stockage Azure.
- De plus, le serveur de processus installe le service Mobilité sur les machines virtuelles que vous voulez répliquer et effectue la détection automatique sur les machines virtuelles VMware locales.

Les administrateurs de Contoso suivent les étapes ci-dessous :

1. Dans le coffre, elle télécharge le modèle OVF à partir de **Préparer l’Infrastructure** > **Source** > **Serveur de configuration**.

    ![Télécharger le modèle OVF](./media/contoso-migration-rehost-vm-sql-ag/add-cs.png)

2. Le modèle est importé dans VMware pour créer et déployer la machine virtuelle.

    ![Modèle OVF](./media/contoso-migration-rehost-vm-sql-ag/vcenter-wizard.png)

3. Lors de l’activation de la machine virtuelle pour la première fois, celle-ci démarre dans un environnement d’installation de Windows Server 2016. Contoso accepte le contrat de licence, puis entrent un mot de passe d’administrateur.
4. Une fois l’installation terminée, Contoso se connecte à la machine virtuelle en tant qu’administrateur. À la première connexion, l’outil de configuration d’Azure Site Recovery s’exécute par défaut.
5. Dans l’outil, Contoso spécifie un nom à utiliser pour l’inscription du serveur de configuration dans le coffre.
6. L’outil vérifie que la machine virtuelle peut se connecter à Azure. Une fois la connexion établie, Contoso se connecte à l’abonnement Azure. Les informations d’identification doivent avoir accès au coffre dans lequel vous souhaitez inscrire le serveur de configuration.

    ![Inscrire un serveur de configuration](./media/contoso-migration-rehost-vm-sql-ag/config-server-register2.png)

7. L’outil effectue des tâches de configuration, puis redémarre.
8. Contoso se reconnecte à l’ordinateur et l’Assistant de gestion du serveur de configuration démarre automatiquement.
9. Dans l’Assistant, Contoso sélectionne la carte réseau qui doit recevoir le trafic de réplication. Une fois configuré, ce paramètre ne peut pas être modifié.
10. L’abonnement, le groupe de ressources et le coffre dans lequel inscrire le serveur de configuration sont sélectionnés.
        ![coffre](./media/contoso-migration-rehost-vm-sql-ag/cswiz1.png)

11. Ensuite, elle télécharge puis installe MySQL Server et VMware PowerCLI.
12. Après la validation, Contoso spécifie le nom de domaine complet (FQDN) ou l’adresse IP du serveur vCenter ou de l’hôte vSphere. On quitte le port par défaut, puis on spécifie un nom convivial pour le serveur vCenter.
13. Le compte qu’ils ont créés pour la détection automatique et les informations d’identification utilisées pour installer automatiquement le service Mobilité sont spécifiés. Pour des machines virtuelles Windows, le compte doit disposer des privilèges d’administrateur local sur celles-ci.

    ![vCenter](./media/contoso-migration-rehost-vm-sql-ag/cswiz2.png)

14. Une fois l’inscription terminée, dans le portail Azure, ils vérifient attentivement que le serveur de configuration et le serveur VMware sont répertoriés dans la page **Source** du coffre. La détection peut prendre 15 minutes ou plus.
15. Site Recovery se connecte ensuite aux serveurs VMware en utilisant les paramètres spécifiés et détecte les machines virtuelles.

### <a name="set-up-the-target"></a>Configurer la cible

Maintenant, les administrateurs de Contoso spécifient les paramètres de réplication de la cible.

1. Dans **Préparer l’infrastructure** > **Cible**, Contoso sélectionne les paramètres de la cible.
2. Site Recovery vérifie qu’il existe un compte de stockage et un réseau Azure dans la cible spécifiée.

### <a name="create-a-replication-policy"></a>Créer une stratégie de réplication

Ils peuvent maintenant créer une stratégie de réplication.

1. Dans **Préparer l’infrastructure** > **Paramètres de réplication** > **Stratégie de réplication** >  **Créer et associer**, ils créent une stratégie **ContosoMigrationPolicy**.
2. Contoso utilise les paramètres par défaut :
    - **Seuil d’objectif de point de récupération :** la valeur par défaut est de 60 minutes. Cette valeur définit la fréquence à laquelle les points de récupération sont créés. Une alerte est générée lorsque la réplication continue dépasse cette limite.
    - **Conservation des points de récupération :** La valeur par défaut est 24 heures. Cette valeur spécifie la durée de la fenêtre de rétention pour chaque point de récupération. Les machines virtuelles répliquées peuvent être récupérées à n’importe quel point dans une fenêtre.
    - **Fréquence des instantanés de cohérence des applications :** La valeur par défaut est une heure. Cette valeur spécifie la fréquence à laquelle les captures instantanées de cohérence d’application sont créées.

        ![Créer une stratégie de réplication](./media/contoso-migration-rehost-vm-sql-ag/replication-policy.png)

3. La stratégie est automatiquement associée au serveur de configuration.

    ![Associer la stratégie de réplication](./media/contoso-migration-rehost-vm-sql-ag/replication-policy2.png)

### <a name="enable-replication"></a>Activer la réplication

Ils peuvent maintenant commencer à répliquer la machine WebVM.

1. Dans **Répliquer l’application** > **Source** >  **+Répliquer**, Contoso sélectionne les paramètres de la source.
2. Ces paramètres indiquent qu’ils souhaitent activer les machines virtuelles, puis sélectionnent le serveur vCenter et le serveur de configuration.

    ![Activer la réplication](./media/contoso-migration-rehost-vm-sql-ag/enable-replication1.png)

3. On spécifie maintenant les paramètres de la cible, dont le groupe de ressources et le réseau virtuel, ainsi que le compte de stockage dans lequel les données répliquées seront stockées.

     ![Activer la réplication](./media/contoso-migration-rehost-vm-sql-ag/enable-replication2.png)

4. Ils sélectionnent la machine WebVM pour la réplication, vérifie la stratégie de réplication et active la réplication. Site Recovery installe le service Mobilité sur la machine virtuelle quand la réplication est activée.

    ![Activer la réplication](./media/contoso-migration-rehost-vm-sql-ag/enable-replication3.png)

5. Contoso suit la progression de la réplication dans **Travaux**. Une fois le travail **Finaliser la protection** exécuté, la machine est prête pour le basculement.
6. Dans le portail Azure, dans **Bases**, ils peuvent afficher la structure des machines virtuelles répliquées sur Azure.

    ![Vue de l’infrastructure](./media/contoso-migration-rehost-vm-sql-ag/essentials.png)

**Besoin de plus d’aide ?**

- Une procédure pas à pas complète de toutes ces étapes est décrite dans [Configurer la récupération d’urgence pour des machines virtuelles VMware locales](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial).
- Des instructions détaillées sont disponibles pour vous aider à [configurer l’environnement source](https://docs.microsoft.com/azure/site-recovery/vmware-azure-set-up-source), à [déployer le serveur de configuration](https://docs.microsoft.com/azure/site-recovery/vmware-azure-deploy-configuration-server) et à [configurer les paramètres de réplication](https://docs.microsoft.com/azure/site-recovery/vmware-azure-set-up-replication).
- Vous pouvez en apprendre davantage sur l’[activation de la réplication](https://docs.microsoft.com/azure/site-recovery/vmware-azure-enable-replication).

## <a name="step-7-install-the-data-migration-assistant-dma"></a>Étape 7 : Installer l’Assistant Migration de données (DMA)

Les administrateurs Contoso vont migrer la base de données SmartHotel360 vers la machine virtuelle Azure **SQLAOG1** avec DMA. Le DMA est configuré comme suit :

1. Télécharger l’outil à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53595) sur la machine virtuelle locale SQL Server (**SQLVM**).
2. Exécuter le programme d’installation (DownloadMigrationAssistant.msi) sur la machine virtuelle.
3. Dans la page **Terminer**, sélectionner **Lancer l’Assistant Migration de données Microsoft** avant la fin de l’exécution de l’Assistant.

## <a name="step-8-migrate-the-database-with-dma"></a>Étape 8 : Migrer la base de données avec le DMA

1. Dans le DMA,ils exécutent une nouvelle migration, **SmartHotel**.
2. Sélectionner le **Type de serveur source** comme **serveur SQL Server sur machines virtuelles Azure**.

    ![DMA](media/contoso-migration-rehost-vm-sql-ag/dma-1.png)

3. Dans les détails de la migration, ajouter **SQLVM** comme serveur source et **SQLAOG1** comme cible. Spécifier des informations d’identification pour chaque machine.

     ![DMA](media/contoso-migration-rehost-vm-sql-ag/dma-2.png)

4. Créer une part locale pour la base de données et les informations de configuration. Elle doit être accessible en écriture par le compte de Service SQL sur SQLVM et SQLAOG1.

    ![DMA](media/contoso-migration-rehost-vm-sql-ag/dma-3.png)

5. Contoso sélectionne les connexions qui doivent être migrées et démarre la migration. Une fois celle-ci terminée, DMA affiche la migration comme ayant réussi.

    ![DMA](media/contoso-migration-rehost-vm-sql-ag/dma-4.png)

6. Vérifie que la base de données est en cours d’exécution sur **SQLAOG1**.

    ![DMA](media/contoso-migration-rehost-vm-sql-ag/dma-5.png)

DMA se connecte à la machine virtuelle SQL Server locale via une connexion VPN site à site entre le centre de données de Contoso et Azure, puis migre la base de données.

## <a name="step-9-protect-the-database-with-always-on"></a>Étape 9 : Protéger la base de données avec Always On

Les administrateurs de Contoso peuvent désormais protéger la base de données de l’application en cours d’exécution sur **SQLAOG1** grâce aux groupes de disponibilité Always On. Ils configurent Always On à l’aide de SQL Management Studio, puis attribuent un écouteur grâce au clustering Windows.

### <a name="create-an-always-on-availability-group"></a>Créer un groupe de disponibilité Always On

1. Dans SQL Management Studio, ils effectuent un clic droit sur **Haute disponibilité Always On** pour démarrer l’**Assistant du nouveau groupe de disponibilité**.
2. Dans **Spécifier les options**, nommer le groupe de disponibilité **SHAOG**. Dans **Sélectionner les bases de données**, ils sélectionnent la base de données SmartHotel360.

    ![Groupe de disponibilité Always On](media/contoso-migration-rehost-vm-sql-ag/aog-1.png)

3. Dans **Spécifier les réplicas**, ajouter les deux nœuds SQL en tant que réplicas de disponibilité et les configurer pour assurer un basculement automatique avec validation synchrone.

     ![Groupe de disponibilité Always On](media/contoso-migration-rehost-vm-sql-ag/aog-2.png)

4. Un écouteur est configuré pour le groupe (**SHAOG**) et le port. L’adresse IP de l’équilibreur de charge interne est ajouté en tant qu’adresse IP statique (10.245.40.100).

    ![Groupe de disponibilité Always On](media/contoso-migration-rehost-vm-sql-ag/aog-3.png)

5. L’amorçage automatique est activé dans **Sélectionner la synchronisation des données**. Avec cette option, SQL Server crée automatiquement les réplicas secondaires pour chaque base de données du groupe, pour que Contoso n’ait pas à les sauvegarder et à les restaurer manuellement. Après la validation, le groupe de disponibilité est créé.

    ![Groupe de disponibilité Always On](media/contoso-migration-rehost-vm-sql-ag/aog-4.png)

6. Contoso a rencontré un problème lors de la création du groupe. Elle n’utilise pas la sécurité intégrée d’Active Directory et doit donc accorder des autorisations au compte de connexion SQL pour créer les rôles de cluster de basculement Windows.

    ![Groupe de disponibilité Always On](media/contoso-migration-rehost-vm-sql-ag/aog-5.png)

7. Une fois que le groupe est créé, Contoso peut le voir dans SQL Management Studio.

### <a name="configure-a-listener-on-the-cluster"></a>Configurer un écouteur sur le cluster

Lors de la dernière étape de configuration du déploiement SQL, les administrateurs configurent l’équilibreur de charge interne en tant qu’écouteur sur le cluster et met l’écouteur en ligne. Ils utilisent un script pour effectuer cette tâche.

![Écouteur de cluster](media/contoso-migration-rehost-vm-sql-ag/cluster-listener.png)

### <a name="verify-the-configuration"></a>Vérifier la configuration

Une fois que tout est configuré, Contoso dispose désormais dans Azure d’un groupe de disponibilité fonctionnelle qui utilise la base de données migrée. Les administrateurs le vérifient en se connectant à l’équilibreur de charge interne dans SQL Management Studio.

![Connexion de l’équilibreur de charge interne](media/contoso-migration-rehost-vm-sql-ag/ilb-connect.png)

**Besoin de plus d’aide ?**

- En savoir plus sur la création d’un [groupe de disponibilité](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-availability-group-tutorial#create-the-availability-group) et d’un [écouteur](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-availability-group-tutorial#configure-listener).
- [Configurer le cluster pour qu’il utilise l’adresse IP de l’équilibreur de charge](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-alwayson-int-listener#configure-the-cluster-to-use-the-load-balancer-ip-address) (manuellement).
- [En savoir plus](https://docs.microsoft.com/azure/storage/blobs/storage-dotnet-shared-access-signature-part-2) sur la création et l’utilisation de SAP.

## <a name="step-10-migrate-the-vm-with-site-recovery"></a>Étape 10 : Migrer la machine virtuelle avec Site Recovery

Les administrateurs de Contoso exécutent un rapide test de basculement, puis migrent la machine virtuelle.

### <a name="run-a-test-failover"></a>Exécuter un test de basculement

L’exécution d’un test de basculement permet de vérifier que tout fonctionne comme prévu avant la migration.

1. Ils exécutent un test de basculement jusqu’au dernier point dans le temps disponible (**Dernier point traité**).
2. Contoso sélectionne **Shut down machine before beginning failover** (Arrêter la machine avant de commencer le basculement), de façon à ce que Site Recovery tente d’arrêter la machine virtuelle source avant de déclencher le basculement. Le basculement est effectué même en cas d’échec de l’arrêt.
3. Le test de basculement est exécuté :

    - Une vérification des prérequis est effectuée pour garantir que toutes les conditions nécessaires pour la migration sont en place.
    - Le basculement traite les données pour permettre la création d’une machine virtuelle Azure. Si vous avez sélectionné le dernier point de récupération, un point de récupération est créé à partir des données.
    - Une machine virtuelle Azure est créée en utilisant les données traitées à l’étape précédente.

4. Une fois le basculement terminé, la machine virtuelle Azure répliquée apparaît dans le portail Azure. Ils vérifient que la machine virtuelle est de la taille appropriée, qu’elle est connectée au réseau approprié et qu’elle est en cours d’exécution.
5. Après ces vérifications, ils nettoient le basculement, puis consignent et enregistrent les observations éventuelles.

### <a name="run-a-failover"></a>Exécuter un basculement

1. Après avoir vérifié que le test de basculement a fonctionné comme prévu, les administrateurs de Contoso créent un plan de récupération pour la migration et y ajoutent une machine WEBVM.

     ![Plan de récupération](./media/contoso-migration-rehost-vm-sql-ag/recovery-plan.png)

2. Contoso exécute un basculement sur le plan. Contoso sélectionne le dernier point de récupération et spécifient que Site Recovery doit essayer d’arrêter la machine virtuelle locale avant de déclencher le basculement.

    ![Basculement](./media/contoso-migration-rehost-vm-sql-ag/failover1.png)

3. Après le basculement, elle vérifie que l’ordinateur virtuel Azure s’affiche comme prévu dans le portail Azure.

    ![Plan de récupération](./media/contoso-migration-rehost-vm-sql-ag/failover2.png)

4. Après avoir vérifié la machine virtuelle dans Azure, elle achève le processus de migration, arrête la réplication de la machine virtuelle, et arrête la facturation de Site Recovery pour la machine virtuelle.

    ![Basculement](./media/contoso-migration-rehost-vm-sql-ag/failover3.png)

### <a name="update-the-connection-string"></a>Mettre à jour la chaîne de connexion

La dernière étape du processus de migration pour Contoso consiste à mettre à jour la chaîne de connexion de l’application pour qu’elle pointe vers la base de données migrée s’exécutant sur l’écouteur SHAOG. Cette configuration est modifiée sur la machine virtuelle WEBVM en cours d’exécution dans Azure. Cette configuration se trouve dans le fichier web.config de l’application ASP.

1. Rechercher le fichier sous C:\inetpub\SmartHotelWeb\web.config. Modifier le nom du serveur afin de refléter le nom de domaine complet d’AOG : shaog.contoso.com.

    ![Basculement](./media/contoso-migration-rehost-vm-sql-ag/failover4.png)

2. Après avoir mis à jour et enregistré le fichier, elle redémarre IIS sur la machine WEBVM. Pour ce faire, elle entre la commande IISRESET /RESTART à partir d’une invite de commande.
3. Après le redémarrage d’IIS, l’application utilise la base de données en cours d’exécution sur l’instance SQL MI.

**Besoin de plus d’aide ?**

- [En savoir plus sur](https://docs.microsoft.com/azure/site-recovery/tutorial-dr-drill-azure) l’exécution d’un test de basculement.
- [Découvrez](https://docs.microsoft.com/azure/site-recovery/site-recovery-create-recovery-plans) comment créer un plan de récupération.
- [Découvrez](https://docs.microsoft.com/azure/site-recovery/site-recovery-failover) comment basculer vers Azure.

### <a name="clean-up-after-migration"></a>Nettoyer après la migration

Après la migration, l’application SmartHotel360 s’exécute sur une machine virtuelle Azure, et la base de données SmartHotel360 se trouve dans le cluster Azure SQL.

Contoso doit à présent effectuer les étapes de nettoyage suivantes :

- Supprimer les machines virtuelles locales de l’inventaire vCenter.
- Supprimer les machines virtuelles des travaux de sauvegarde locale.
- Mettre à jour la documentation interne afin qu’elle indique les nouveaux emplacements et les adresses IP des machines virtuelles.
- Passer en revue toutes les ressources qui interagissent avec les machines virtuelles désactivées, et mettre à jour les paramètres ou la documentation appropriés afin de refléter la nouvelle configuration.
- Ajouter les deux nouvelles machines virtuelle (SQLAOG1 et SQLAOG2) aux systèmes de surveillance de la production.

### <a name="review-the-deployment"></a>Examiner le déploiement

Avec les ressources migrées dans Azure, Contoso doit rendre sa nouvelle infrastructure entièrement opérationnelle et la sécuriser.

### <a name="security"></a>Sécurité

L’équipe de sécurité de Contoso examine les machines virtuelles Azure WEBVM, SQLAOG1 et SQLAOG2 afin d’identifier d’éventuels problèmes de sécurité.

- L’équipe examine les groupes de sécurité réseau (NSG) pour la machine virtuelle afin de contrôler l’accès. Contoso utilise des groupes de sécurité réseau pour s’assurer que seul le trafic autorisé vers l’application puisse passer.
- Elle prend également en considération la sécurisation des données sur le disque à l’aide d’Azure Disk Encryption et de Key Vault.
- L’équipe doit évaluer le chiffrement transparent des données (TDE), puis l’activer sur la base de données SmartHotel360 qui s’exécute sur le nouvel AOG SQL. [Plus d’informations](https://docs.microsoft.com/sql/relational-databases/security/encryption/transparent-data-encryption?view=sql-server-2017)

Pour plus d’informations, consultez les [Meilleures pratiques de sécurité pour les charges de travail IaaS dans Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

## <a name="bcdr"></a>BCDR

Pour assurer la continuité et la reprise d’activité (BCDR), Contoso effectue les actions suivantes :

- Pour sécuriser les données : Contoso sauvegarde les données sur les machines virtuelles WEBVM, SQLAOG1 et SQLAOG2 à l’aide du service Sauvegarde Azure. [Plus d’informations](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)
- Contoso va également apprendre à utiliser le stockage Azure pour sauvegarder SQL Server directement sur le stockage d’objets blob. [Plus d’informations](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-use-storage-sql-server-backup-restore)
- Pour que les applications soient opérationnelles : Contoso réplique les machines virtuelles de l’application dans Azure vers une région secondaire à l’aide de Site Recovery. [Plus d’informations](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

1. Contoso a un contrat de licence pour sa machine WEBVM et tirera parti d’Azure Hybrid Benefit. Contoso va convertir les machines virtuelles Azure existantes pour tirer parti de cette tarification.
2. Contoso va activer Azure Cost Management sous licence de Cloudyn, une filiale de Microsoft. Il s’agit d’une solution de gestion des coûts multicloud qui vous aide à utiliser et à gérer Azure ainsi que d’autres ressources cloud. [En savoir plus](https://docs.microsoft.com/azure/cost-management/overview) sur Azure Cost Management.

## <a name="conclusion"></a>Conclusion

Cet article décrit comment Contoso a réhébergé l’application SmartHotel360 dans Azure en migrant la machine virtuelle frontale de l’application vers Azure à l’aide du service Site Recovery. Contoso a migré la base de données de l’application vers un cluster SQL Server configuré dans Azure et a protégé la base de données dans un groupe de disponibilité Always On de SQL Server.
