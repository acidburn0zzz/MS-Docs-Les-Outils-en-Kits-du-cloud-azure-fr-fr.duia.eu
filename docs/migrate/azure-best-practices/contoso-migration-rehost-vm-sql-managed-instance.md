---
title: Réhéberger une application locale en migrant vers des machines virtuelles Azure et Azure SQL Database Managed Instance
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment Contoso réhéberge une application locale sur des machines virtuelles Azure et Azure SQL Database Managed Instance.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 59a18ab71befd7b4f60c4e0a97ecb6af28690d7f
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752840"
---
# <a name="rehost-an-on-premises-app-on-an-azure-vm-and-sql-database-managed-instance"></a>réhéberger une application locale sur une machine virtuelle Azure et SQL Database Managed Instance

Cet article explique comment la société fictive Contoso migre une application frontale Windows .NET à deux niveaux qui s’exécute sur des machines virtuelles VMware vers une machine virtuelle Azure à l’aide du service Azure Site Recovery. Il explique également la façon dont Contoso migre la base de données d’application vers Azure SQL Database Managed Instance.

> [!NOTE]
> Azure SQL Database Managed Instance est actuellement en préversion.

L’application SmartHotel360 utilisée dans cet exemple est fournie au format open source. Si vous souhaitez l’utiliser à des fins de test, vous pouvez la télécharger à partir de [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique de Contoso a travaillé en étroite collaboration avec ses partenaires commerciaux pour comprendre le résultat que l’entreprise souhaite obtenir avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso se développe. Il en découle une pression accrue sur l’infrastructure et les systèmes locaux et de l’entreprise.
- **Gagner en efficacité.** Contoso doit supprimer les procédures inutiles et rationaliser les processus pour ses développeurs et ses utilisateurs. L’entreprise a besoin d’une informatique rapide et doit éviter les pertes de temps ou d’argent afin de répondre plus rapidement aux exigences des clients.
- **Gagner en agilité.** le service informatique de Contoso doit être plus réactif face aux besoins de l’entreprise. Elle doit être en mesure de réagir plus rapidement que l’évolution du marché pour réussir dans une économie mondiale. L’informatique chez Contoso ne doit pas devenir une entrave à l’activité.
- **Mise à l’échelle** à mesure que l’entreprise croît, l’informatique de Contoso doit fournir des systèmes capables de croître au même rythme.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a identité les objectifs de cette migration. L’entreprise utilise des objectifs de migration pour déterminer la meilleure méthode de migration.

- Après la migration, l’application dans Azure devra offrir le même niveau de performance qu’aujourd’hui dans l’environnement VMware local de Contoso. Migrer vers le cloud ne signifie nullement que les performances de l’application deviennent moins importantes.
- Contoso ne souhaite pas investir dans l’application. Elle est vitale pour l’entreprise, mais Contoso souhaite simplement la migrer dans sa forme actuelle vers le cloud.
- Une fois l’application migrée, les tâches d’administration de base de données devront être réduites au minimum.
- Contoso ne souhaite pas utiliser Azure SQL Database pour cette application et recherche des alternatives.

## <a name="solution-design"></a>Conception de la solution

Après avoir défini précisément les objectifs et exigences, Contoso conçoit et examine une solution de déploiement, et identifie le processus de migration, notamment les services Azure à utiliser pour la migration.

### <a name="current-architecture"></a>Architecture actuelle

- Contoso a un centre de données principal (**contoso-datacenter**). Le centre de données principal se trouve dans la ville de New York dans l’Est des États-Unis.
- Contoso a trois branches locales supplémentaires aux États-Unis.
- Le centre de données principal est connecté à Internet par le biais d’une connexion Ethernet Fiber Metro (500 Mbits/s).
- Chaque branche est connectée localement à Internet par le biais de connexions de qualité professionnelle, avec des tunnels VPN IPsec vers le centre de données principal. Cette configuration permet au réseau entier d’être connecté en permanence, et elle optimise la connectivité Internet.
- Le centre de données principal est entièrement virtualisé avec VMware. Contoso dispose de deux hôtes de virtualisation ESXi 6.5 gérés par vCenter Server 6.5.
- Contoso utilise Active Directory pour la gestion d’identité. Contoso utilise des serveurs DNS sur le réseau interne.
- Contoso a un contrôleur de domaine local (**contosodc1**).
- Les contrôleurs de domaine s’exécutent sur des machines virtuelles VMware. Les contrôleurs de domaine au niveau des branches locales s’exécutent sur des serveurs physiques.
- L’application SmartHotel360 est répartie en niveaux sur deux machines virtuelles (**WEBVM** et **SQLVM**) qui se trouvent sur un hôte VMware ESXi version 6.5 (**contosohost1.contoso.com**).
- L’environnement VMware est géré par vCenter Server 6.5 (**vcenter.contoso.com**) s’exécutant sur une machine virtuelle.

![Architecture actuelle de Contoso](./media/contoso-migration-rehost-vm-sql-managed-instance/contoso-architecture.png)

### <a name="proposed-architecture"></a>Architecture proposée

Dans ce scénario, Contoso veut migrer son application de voyage locale à deux niveaux de la façon suivante :

- Migrer la base de données de l’application (**SmartHotelDB**) vers une instance Azure SQL Managed Instance.
- Migrer la machine **WebVM** frontale vers une machine virtuelle Azure.
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

![Architecture du scénario](media/contoso-migration-rehost-vm-sql-managed-instance/architecture.png)

### <a name="database-considerations"></a>Considérations liées à la base de données

Dans le cadre de la conception de la solution, Contoso a fait une comparaison des fonctionnalités entre Azure SQL Database et SQL Server Managed Instance. Les administrateurs ont choisi Managed Instance sur la base des considérations suivantes.

- Managed Instance vise à fournir une compatibilité de quasi 100 % avec la dernière version locale de SQL Server. Microsoft recommande Managed Instance aux clients qui exécutent SQL Server localement ou sur une machine virtuelle IaaS et qui souhaitent migrer leurs applications vers un service entièrement managé en changeant le moins possible la conception.
- Contoso a l’intention de migrer un grand nombre d’applications locales vers IaaS. Beaucoup d’entre elles sont fournies par l’ISV. Contoso se rend compte que Managed Instance peut garantir une compatibilité de base de données pour ces applications que SQL Database ne prend peut-être pas en charge.
- Contoso peut simplement effectuer une migration lift-and-shift vers Managed Instance à l’aide d’Azure Database Migration Service entièrement automatisé. Une fois ce service en place, Contoso peut le réutiliser pour les futures migrations de base de données.
- SQL Managed Instance prend en charge SQL Server Agent, qui est essentiel pour l’application SmartHotel360. Contoso a besoin de cette compatibilité, sous peine de devoir recréer les plans de maintenance demandés par l’application.
- Avec Software Assurance, Contoso peut échanger ses licences existantes contre une réduction de tarif sur SQL Database Managed Instance en utilisant Azure Hybrid Benefit pour SQL Server. Contoso peut alors économiser jusqu'à 30 % sur Managed Instance.
- SQL Managed Instance est entièrement contenu dans le réseau virtuel ; il fournit donc une isolation et sécurité accrues pour les données de Contoso. Contoso peut obtenir les avantages du cloud public tout en isolant l’environnement du réseau Internet public.
- Managed Instance prend en charge plusieurs fonctionnalités de sécurité, notamment Always Encrypted, le masquage dynamique des données, la sécurité au niveau des lignes et la détection des menaces.

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant une liste des avantages et des inconvénients.

<!-- markdownlint-disable MD033 -->

**Considération** | **Détails**
--- | ---
**Avantages** | WEBVM est déplacé vers Azure sans changement, ce qui simplifie la migration.<br/><br/> SQL Managed Instance prend en charge les spécifications techniques et les objectifs de Contoso.<br/><br/> Managed Instance offre une compatibilité de 100 % avec le déploiement actuel, tout en permettant à Contoso de ne plus utiliser SQL Server 2008 R2.<br/><br/> Contoso peut tirer parti de son investissement dans Software Assurance en utilisant Azure Hybrid Benefit pour SQL Server et Windows Server.<br/><br/> Elle peut réutiliser Azure Database Migration Service pour d’autres migrations futures.<br/><br/> SQL Managed Instance intègre une tolérance de panne que Contoso n’a pas besoin de configurer. Cela signifie que la couche Données n’est plus un point de basculement unique.
**Inconvénients** | La machine WEBVM exécute Windows Server 2008 R2. Bien que ce système d’exploitation soit pris en charge par Azure, cette plateforme n’est plus prise en charge. [Plus d’informations](https://support.microsoft.com/help/956893)<br/><br/> La couche web reste un point unique de basculement et seule la machine WEBVM fournit les services.<br/><br/> Contoso devra continuer à prendre en charge la couche web de l’application comme machine virtuelle au lieu d’opter pour un service managé, comme Azure App Service.<br/><br/> Pour la couche Données, Managed Instance n’est peut-être pas la meilleure solution si Contoso veut personnaliser le système d’exploitation ou le serveur de base de données, ou si l’entreprise veut exécuter des applications tierces avec SQL Server. L’exécution de SQL Server sur une machine virtuelle IaaS peut apporter cette flexibilité.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processus de migration

Contoso migre les niveaux web et données de son application SmartHotel360 vers Azure en effectuant les étapes suivantes :

1. Contoso disposant déjà d’une infrastructure Azure en place, il faut simplement ajouter quelques composants Azure spécifiques pour ce scénario.
2. La couche Données sera migrée à l’aide d’Azure Database Migration Service. Le service se connecte à la machine virtuelle SQL Server locale par le biais d’une connexion VPN site à site entre le centre de données de Contoso et Azure. Le service migre ensuite la base de données.
3. La couche web sera migrée à l’aide d’une migration lift-and-shift avec Site Recovery. Ce processus nécessite la préparation de l’environnement VMware local, la configuration et l’activation de la réplication, et la migration des machines virtuelles par leur basculement vers Azure.

     ![Architecture de la migration](media/contoso-migration-rehost-vm-sql-managed-instance/migration-architecture.png)

### <a name="azure-services"></a>Services Azure

Service | Description | Coût
--- | --- | ---
[Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview) | Azure Database Migration Service permet une migration fluide à partir de plusieurs sources de base de données vers des plateformes de données Azure, avec un temps d’arrêt minimal. | Apprenez-en davantage sur les [régions prises en charge](https://docs.microsoft.com/azure/dms/dms-overview#regional-availability) et sur la [tarification de Database Migration Service](https://azure.microsoft.com/pricing/details/database-migration).
[Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) | Managed Instance est un service de base de données managé qui représente une instance de SQL Server entièrement managée dans le cloud Azure. Il utilise le même code que la dernière version du moteur de base de données SQL Server et offre les dernières fonctionnalités, améliorations en termes de performances et correctifs de sécurité. | L’utilisation de SQL Database Managed Instance exécuté dans Azure entraîne des frais basés sur la capacité. Apprenez-en davantage sur la [tarification de Managed Instance](https://azure.microsoft.com/pricing/details/sql-database/managed).
[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery) | Le service Site Recovery orchestre et gère la migration et la reprise d’activité pour les machines virtuelles Azure, les machines virtuelles locales et les serveurs physiques. | Lors de la réplication vers Azure, des frais sur le Stockage Azure sont facturés. Des machines virtuelles Azure sont créées en cas de basculement et entraînent des frais. Apprenez-en davantage sur les [frais et la tarification de Site Recovery](https://azure.microsoft.com/pricing/details/site-recovery).

## <a name="prerequisites"></a>Prérequis

Contoso et les autres utilisateurs doivent respecter les prérequis suivants pour ce scénario :

<!-- markdownlint-disable MD033 -->

Configuration requise | Détails
--- | ---
**S’inscrire à la préversion de Managed Instance** | Vous devez être inscrit pour tester la préversion publique limitée de SQL Database Managed Instance. Vous avez besoin d’un abonnement Azure pour vous [inscrire](https://portal.azure.com#create/Microsoft.SQLManagedInstance). La confirmation d’inscription prend quelques jours. Veillez donc à vous inscrire avant de commencer le déploiement de ce scénario.
**Abonnement Azure** | Vous devez avoir déjà créé un abonnement quand vous effectuez l’évaluation dans le premier article de cette série. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions.<br/><br/> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur de l’abonnement, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur.<br/><br/> Si vous avez besoin d’autorisations plus précises, consultez [Utiliser le contrôle d’accès en fonction du rôle pour gérer l’accès à Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infrastructure Azure** | Contoso configure son infrastructure Azure comme décrit dans [Infrastructure Azure pour la migration](./contoso-migration-infrastructure.md).
**Site Recovery (local)** | Votre instance locale de vCenter Server doit exécuter la version 5.5, 6.0 ou 6.5<br/><br/> Un hôte ESXi qui exécute la version 5.5, 6.0 ou 6.5<br/><br/> Une ou plusieurs machines virtuelles VMware exécutées sur l’hôte ESXi.<br/><br/> Les machines virtuelles doivent répondre aux [exigences Azure](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#azure-vm-requirements).<br/><br/> Configuration [réseau](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#network) et [stockage](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#storage) prise en charge.
**Database Migration Service** | Pour Azure Database Migration Service, vous avez besoin d’un [périphérique VPN local compatible](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).<br/><br/> Vous devez être en mesure de configurer l’appareil VPN local. Il doit avoir une adresse IPv4 publique externe. L’adresse ne peut pas se trouver derrière un périphérique NAT.<br/><br/> Veillez à disposer de l’accès à votre base de données SQL Server locale.<br/><br/> Le Pare-feu Windows doit pouvoir accéder au moteur de base de données source. Découvrez comment [configurer le Pare-feu Windows pour accéder au moteur de base de données](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access).<br/><br/> S’il y a un pare-feu devant votre machine de base de données, ajoutez des règles pour autoriser l’accès à la base de données, et aux fichiers par le biais du port SMB 445.<br/><br/> Les informations d’identification utilisées pour se connecter à l’instance source SQL Server et à l’instance cible Managed Instance doivent appartenir à des membres du rôle serveur sysadmin.<br/><br/> Il vous faut un partage réseau dans votre base de données locale qu’Azure Database Migration Service peut utiliser pour sauvegarder la base de données source.<br/><br/> Vérifiez que le compte de service qui exécute l’instance source de SQL Server dispose d’autorisations d’écriture sur le partage réseau.<br/><br/> Notez l’utilisateur Windows (et son mot de passe) qui dispose d’autorisations complètes sur le partage réseau. Azure Database Migration Service emprunte ces informations d’identifications pour charger les fichiers de sauvegarde sur le conteneur de stockage Azure.<br/><br/> Le processus d’installation SQL Server Express définit le protocole TCP/IP sur **Désactivé** par défaut. Veillez à l’activer.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment Contoso prévoie de configurer le déploiement :

> [!div class="checklist"]
>
> - **Étape 1 : Configurer une SQL Database Managed Instance.** Contoso a besoin d’une instance managée existante vers laquelle la base de données SQL Server locale migrera.
> - **Étape 2 : Préparer Azure Database Migration Service.** Contoso doit inscrire le fournisseur de migration de base de données, créer une instance, puis créer un projet Azure Database Migration Service. Contoso doit également configurer un URI (Uniform Resource Identifier) avec signature d’accès partagé (SAP) pour Azure Database Migration Service. Un URI SAP fournit un accès délégué aux ressources du compte de stockage Contoso. Ainsi, Contoso peut accorder des autorisations limitées aux objets de stockage. Contoso configure un URI SAP pour qu’Azure Database Migration Service puisse accéder au conteneur du compte de stockage sur lequel le service charge les fichiers de sauvegarde SQL Server.
> - **Étape 3 : Préparer Azure pour Site Recovery.** Contoso doit créer un compte de stockage afin de conserver les données répliquées pour Site Recovery. Ils doivent également créer un coffre Azure Recovery Services.
> - **Étape 4 : Préparer une machine virtuelle VMware locale pour Site Recovery.** Contoso doit préparer des comptes pour la découverte de machines virtuelles et l’installation d’agents, afin d’établir une connexion aux machines virtuelles Azure après basculement.
> - **Étape 5 : Répliquer les machines virtuelles.** pour la réplication, Contoso configure les environnements source et cible de Site Recovery ainsi qu’une stratégie de réplication, et commence la réplication des machines virtuelles vers Stockage Azure.
> - **Étape 6 : Migrer la base de données à l’aide d’Azure Database Migration Service.** Contoso migre la base de données.
> - **Étape 7 : Migrer les machines virtuelles à l’aide de Site Recovery.** Contoso exécute un test de basculement pour vérifier que tout fonctionne. Ensuite, Contoso exécute un basculement complet pour migrer les machines virtuelles vers Azure.

## <a name="step-1-prepare-a-sql-database-managed-instance"></a>Étape 1 : Préparer SQL Database Managed Instance

Pour configurer Azure SQL Database Managed Instance, Contoso a besoin d’un sous-réseau qui remplit les conditions suivantes :

- Le sous-réseau doit être dédié. Il doit être vide et ne doit contenir aucun autre service cloud. Le sous-réseau ne doit pas être un sous-réseau de passerelle.
- Une fois l’instance gérée créée, Contoso ne doit pas ajouter de ressources au sous-réseau.
- Aucun groupe de sécurité réseau ne doit être associé au sous-réseau.
- Le sous-réseau doit avoir une table de routage définie par l’utilisateur. Le seul itinéraire attribué doit être 0.0.0.0/0 tronçon suivant vers Internet.
- Système DNS personnalisé facultatif : si un système DNS personnalisé est spécifié sur le réseau virtuel Azure, vous devez ajouter l’adresse IP des programmes de résolution récursifs d’Azure (par exemple 168.63.129.16) à la liste. Découvrez comment [configurer un système DNS personnalisé pour Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-custom-dns).
- Le sous-réseau ne doit pas avoir de point de terminaison de service (stockage ou SQL) associé. Les points de terminaison doivent être désactivés sur le réseau virtuel.
- Le sous-réseau doit avoir un minimum de 16 adresses IP. Découvrez comment [dimensionner le sous-réseau Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-vnet-configuration).
- Dans l’environnement hybride de Contoso, des paramètres DNS personnalisés sont nécessaires. Contoso configure les paramètres DNS pour utiliser un ou plusieurs des serveurs DNS Azure de l’entreprise. Apprenez-en davantage sur la [personnalisation du système DNS](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-custom-dns).

### <a name="set-up-a-virtual-network-for-the-managed-instance"></a>Configurer un réseau virtuel pour Managed Instance

Les administrateurs de Contoso configurent le réseau virtuel de la façon suivante :

1. Ils créent un réseau virtuel (**VNET-SQLMI-EU2**) dans la région primaire USA Est 2. Ils ajoutent le réseau virtuel au groupe de ressources **ContosoNetworkingRG**.
2. Ils attribuent l’espace d’adressage 10.235.0.0/24. Ils vérifient que la plage ne chevauche pas d’autres réseaux dans l’entreprise.
3. Ils ajoutent deux sous-réseaux au réseau :
    - **SQLMI-DS-EUS2** (10.235.0.0.25)
    - **SQLMI-SAW-EUS2** (10.235.0.128/29). Ce sous-réseau est utilisé pour joindre l’annuaire à Managed Instance.

      ![Managed Instance - Créer un réseau virtuel](media/contoso-migration-rehost-vm-sql-managed-instance/mi-vnet.png)

4. Une fois le réseau virtuel et les sous-réseaux déployés, ils appairent les réseaux de la façon suivante :

    - Peering de **VNET-SQLMI-EUS2** avec **VNET-HUB-EUS2** (réseau virtuel hub pour la région USA Est 2).
    - Peering de **VNET-SQLMI-EUS2** avec **VNET-PROD-EUS2** (réseau de production).

      ![Peering de réseau](media/contoso-migration-rehost-vm-sql-managed-instance/mi-peering.png)

5. Ils définissent des paramètres DNS personnalisés. Le système DNS pointe tout d’abord sur les contrôleurs de domaine Azure de Contoso. Azure DNS est secondaire. Les contrôleurs de domaine Azure de Contoso se situent comme suit :

    - Situé sur le sous-réseau **PROD-CC-EUS2**, sur le réseau de production USA Est 2 (**VNET-PROD-EUS2**)
    - Adresse de **CONTOSODC3** : 10.245.42.4
    - Adresse de **CONTOSODC4** : 10.245.42.5
    - Programme de résolution d’Azure DNS : 168.63.129.16

      ![Serveurs DNS du réseau](media/contoso-migration-rehost-vm-sql-managed-instance/mi-dns.png)

**Besoin de plus d’aide ?**

- Obtenez une vue d’ensemble de [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
- Découvrez comment [créer un réseau virtuel pour SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-vnet-configuration).
- Découvrez comment [configurer le peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-manage-peering).
- Découvrez comment [mettre à jour les paramètres DNS d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started-dns).

### <a name="set-up-routing"></a>Configuration du routage

Managed Instance est placé sur un réseau privé virtuel. Contoso a besoin d’une table de routage pour que le réseau virtuel communique avec le service de gestion Azure. Si le réseau virtuel ne peut pas communiquer avec le service qui le gère, le réseau virtuel devient inaccessible.

Contoso prend en compte ces facteurs :

- La table de routage contient un ensemble de règles (itinéraires) qui spécifient le mode de routage des paquets envoyés à partir de Managed Instance sur le réseau virtuel.
- La table de routage est associée à des sous-réseaux dans lesquels les instances gérées sont déployées. Chaque paquet quittant un sous-réseau est géré en fonction de la table de routage associée.
- Un sous-réseau ne peut être associé qu’à une seule table de routage.
- La création de tables de routage dans Microsoft Azure n’occasionne aucun frais.

 Pour configurer le routage, les administrateurs de Contoso effectuent les opérations suivantes :

1. Ils créent une table de routage définie par l’utilisateur dans le groupe de ressources **ContosoNetworkingRG**.

    ![Table de routage](media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table.png)

2. Pour respecter les exigences de Managed Instance, une fois la table de routage (**MIRouteTable**) déployée, ils ajoutent une route avec le préfixe d’adresse 0.0.0.0/0. L’option **Type de tronçon suivant** est définie sur **Internet**

    ![Préfixe de table de routage](media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-prefix.png)

3. Ils associent la table de routage au sous-réseau **SQLMI-DB-EUS2** (dans le réseau **VNET-SQLMI-EUS2**).

    ![Sous-réseau de table de routage](media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-subnet.png)

**Besoin de plus d’aide ?**

Découvrez comment [configurer des itinéraires pour une instance gérée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal).

### <a name="create-a-managed-instance"></a>Créer une option Managed Instance

À présent, les administrateurs de Contoso peuvent provisionner une instance SQL Database Managed Instance :

1. Comme l’instance gérée sert une application métier, ils la déploient dans la région USA Est 2 primaire de l’entreprise. Ils ajoutent l’instance gérée au groupe de ressources **ContosoRG**.
2. Ils sélectionnent un niveau tarifaire, une taille de calcul et un stockage pour l’instance. Apprenez-en davantage sur la [tarification de Managed Instance](https://azure.microsoft.com/pricing/details/sql-database/managed).

    ![Instance gérée](media/contoso-migration-rehost-vm-sql-managed-instance/mi-create.png)

3. Une fois l’instance gérée déployée, deux nouvelles ressources apparaissent dans le groupe de ressources **ContosoRG** :

    - Un cluster virtuel si Contoso a plusieurs instances gérées
    - L’instance gérée SQL Server Database

      ![Instance gérée](media/contoso-migration-rehost-vm-sql-managed-instance/mi-resources.png)

**Besoin de plus d’aide ?**

Découvrez comment [provisionner une instance gérée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal).

## <a name="step-2-prepare-the-azure-database-migration-service"></a>Étape 2 : Préparer Azure Database Migration Service

Pour préparer Azure Database Migration Service, les administrateurs de Contoso doivent effectuer quelques opérations :

- Inscrire le fournisseur Azure Database Migration Service dans Azure.
- Fournir à Azure Database Migration Service l’accès à Stockage Azure pour charger les fichiers de sauvegarde utilisés pour migrer une base de données. Pour fournir l’accès au Stockage Azure, ils créent un conteneur de Stockage Blob Azure. Ils génèrent un URI SAP pour le conteneur de stockage Blob.
- Créer un projet Azure Database Migration Service.

Ensuite, ils effectuent les tâches suivantes :

1. Ils inscrivent le fournisseur de migration de base de données sous l’abonnement.
    ![Database Migration Service - Registre](media/contoso-migration-rehost-vm-sql-managed-instance/dms-subscription.png)

2. Ils créent un conteneur de stockage Blob. Contoso génère un URI SAP afin qu’Azure Database Migration Service puisse y accéder.

    ![Database Migration Service - Générer un URI SAP](media/contoso-migration-rehost-vm-sql-managed-instance/dms-sas.png)

3. Ils créent une instance Azure Database Migration Service.

    ![Database Migration Service - Créer une instance](media/contoso-migration-rehost-vm-sql-managed-instance/dms-instance.png)

4. Ils placent l’instance Azure Database Migration Service dans le sous-réseau **PROD-DC-EUS2** du réseau virtuel **VNET-PROD-DC-EUS2**.
    - Azure Database Migration Service est placé à cet endroit, car le service doit être dans un réseau virtuel pouvant accéder à la machine virtuelle SQL Server locale via une passerelle VPN.
    - **VNET-PROD-EUS2** est appairé à **VNET-HUB-EUS2** et autorisé à utiliser des passerelles distantes. L’option **Utiliser des passerelles distantes** garantit qu’Azure Database Migration Service peut communiquer en fonction des besoins.

        ![Database Migration Service - Configurer le réseau](media/contoso-migration-rehost-vm-sql-managed-instance/dms-network.png)

**Besoin de plus d’aide ?**

- Découvrez comment [configurer Azure Database Migration Service](https://docs.microsoft.com/azure/dms/quickstart-create-data-migration-service-portal).
- Découvrez comment [créer et utiliser une signature d’accès partagé](https://docs.microsoft.com/azure/storage/blobs/storage-dotnet-shared-access-signature-part-2).

## <a name="step-3-prepare-azure-for-the-site-recovery-service"></a>Étape 3 : Préparer Azure pour le service Site Recovery

Plusieurs éléments Azure sont nécessaires afin que Contoso puisse configurer Site Recovery pour la migration de ses machines virtuelles de couche web (**WEBMV**) :

- Un réseau virtuel où se trouvent les ressources basculées
- Un compte de stockage pour accueillir les données répliquées
- Un coffre Recovery Services dans Azure.

Les administrateurs de Contoso configurent Site Recovery de la façon suivante :

1. La machine virtuelle étant un frontend web pour l’application SmartHotel360, Contoso la fait basculer vers son réseau (**VNET-PROD-EUS2**) et son sous-réseau (**PROD-FE-EUS2**) de production existants. Le réseau et le sous-réseau se trouvent dans la région primaire USA Est 2. Contoso a configuré le réseau quand ils ont [déployé l’infrastructure Azure](./contoso-migration-infrastructure.md).
2. Ils créent un compte de stockage (**contosovmsacc20180528**). Contoso utilise un compte à usage général. Contoso sélectionne le stockage standard et la réplication de stockage localement redondant.

    ![Site Recovery - Créer le compte de stockage](media/contoso-migration-rehost-vm-sql-managed-instance/asr-storage.png)

3. Une fois le compte de stockage et le réseau en place, ils créent un coffre (**ContosoMigrationVault**). Contoso place le coffre dans le groupe de ressources **ContosoFailoverRG**, dans la région primaire USA Est 2.

    ![Recovery Services - Créer le coffre](media/contoso-migration-rehost-vm-sql-managed-instance/asr-vault.png)

**Besoin de plus d’aide ?**

Découvrez comment [configurer Azure pour Site Recovery](https://docs.microsoft.com/azure/site-recovery/tutorial-prepare-azure).

## <a name="step-4-prepare-on-premises-vmware-for-site-recovery"></a>Étape 4 : Préparer une machine virtuelle VMware locale pour Site Recovery

Pour préparer VMware pour Site Recovery, les administrateurs de Contoso doivent effectuer ces tâches :

- Préparer un compte sur l’instance de vCenter Server ou sur l’hôte vSphere ESXi. Le compte automatise la découverte des machines virtuelles
- Préparer un compte permettant l’installation automatique du service Mobilité sur les machines virtuelles VMware que Contoso souhaite répliquer
- Préparer les machines virtuelles locales afin qu’elles se connectent aux machines virtuelles Azure une fois celles-ci créées après le basculement

### <a name="prepare-an-account-for-automatic-discovery"></a>Préparer un compte pour la découverte automatique

Site Recovery doit pouvoir accéder aux serveurs VMware pour :

- Détectez automatiquement les machines virtuelles. Un compte en lecture seule est au minimum nécessaire.
- Orchestrer la réplication, le basculement et la restauration automatique. Contoso a besoin d’un compte qui peut exécuter des opérations telles que la création et la suppression de disques, ainsi que l’allumage de machines virtuelles.

Les administrateurs de Contoso configurent le compte en effectuant ces tâches :

1. Crée un rôle au niveau du vCenter.
2. Attribue les autorisations requises à ce rôle.

**Besoin de plus d’aide ?**

Découvrez comment [créer et affecter un rôle pour la découverte automatique](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial-prepare-on-premises#prepare-an-account-for-automatic-discovery).

### <a name="prepare-an-account-for-mobility-service-installation"></a>Préparer un compte pour l’installation du service Mobilité

Le service Mobilité doit être installé sur la machine virtuelle que Contoso souhaite répliquer. Contoso prend en compte ces facteurs concernant le service mobilité :

- Site Recovery peut effectuer une installation automatique par push de ce composant, quand Contoso active la réplication pour la machine virtuelle.
- Pour une installation automatique par push, Contoso doit préparer un compte utilisé par Site Recovery pour accéder à la machine virtuelle.
- Ce compte est spécifié quand la réplication est configurée dans la console Azure.
- Contoso doit avoir un domaine ou un compte local disposant des autorisations nécessaires pour l’installation sur la machine virtuelle.

**Besoin de plus d’aide ?**

Découvrez comment [créer un compte pour une installation push du service Mobilité](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial-prepare-on-premises#prepare-an-account-for-mobility-service-installation).

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Préparer la connexion aux machines virtuelles Azure après le basculement

Après le basculement vers Azure, Contoso souhaite pouvoir se connecter aux machines virtuelles répliquées dans Azure. Pour se connecter aux machines virtuelles répliquées dans Azure, les administrateurs de Contoso doivent effectuer certaines tâches sur la machine virtuelle locale avant la migration :

1. Pour un accès via Internet, ils activent RDP sur la machine virtuelle locale avant le basculement. Ils vérifient que des règles TCP et UDP sont ajoutées pour le profil **Public**, et que RDP est autorisé dans **Pare-feu Windows** > **Applications autorisées** pour tous les profils.
2. Pour un accès via le VPN de site à site de Contoso, ils activent RDP sur la machine locale. Ils autorisent RDP dans **Pare-feu Windows** > **Applications et fonctionnalités autorisées** pour les réseaux **Domaine et Privé**.
3. Ils définissent la stratégie SAN du système d’exploitation sur la machine virtuelle locale sur **OnlineAll**.

Les administrateurs de Contoso doivent également vérifier ces éléments quand ils exécutent un basculement :

- Aucune mise à jour de Windows ne doit être en attente sur la machine virtuelle quand un basculement est déclenché. Si des mises à jour de Windows sont en attente, les utilisateurs de Contoso ne peuvent pas se connecter à la machine virtuelle tant que la mise à jour n’est pas terminée.
- Après le basculement, les administrateurs doivent examiner les **diagnostics de démarrage** pour voir une capture d’écran de la machine virtuelle. S’ils ne peuvent pas voir les diagnostics de démarrage, ils doivent vérifier que la machine virtuelle est en cours d’exécution, puis passer en revue les [conseils de dépannage](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

## <a name="step-5-replicate-the-on-premises-vms-to-azure"></a>Étape 5 : Répliquer les machines virtuelles locales sur Azure

Avant d’exécuter une migration vers Azure, les administrateurs de Contoso doivent configurer et activer la réplication pour les machines virtuelles locales.

### <a name="set-a-replication-goal"></a>Définir un objectif de réplication

1. Dans le coffre, sous le nom du coffre (**ContosoVMVault**), ils définissent un objectif de réplication (**Prise en main** > **Site Recovery** > **Préparer l’infrastructure**).
2. Ils spécifient que les machines sont situées localement, qu’elles s’exécutent sur VMware et qu’elles sont répliquées sur Azure.

    ![Préparer l’infrastructure - Objectif de protection](./media/contoso-migration-rehost-vm-sql-managed-instance/replication-goal.png)

### <a name="confirm-deployment-planning"></a>Confirmer la planification d’un déploiement

Pour continuer, les administrateurs de Contoso doivent confirmer que la planification du déploiement est terminée. Ils sélectionnent **Oui, je l’ai fait**. Dans ce déploiement, Contoso migre une seule machine virtuelle, la planification du déploiement n’est donc pas nécessaire.

### <a name="set-up-the-source-environment"></a>Configurer l’environnement source

Les administrateurs de Contoso configurent maintenant l’environnement source. Pour configurer leur environnement source, ils téléchargent un modèle OVF et l’utilisent pour déployer le serveur de configuration et ses composants associés sous la forme d’une machine virtuelle VMware locale hautement disponible. Les composants sur le serveur sont les suivants :

- Le serveur de configuration qui coordonne les communications entre l’infrastructure locale et Azure. Le serveur de configuration gère la réplication des données.
- Le serveur de traitement qui fait office de passerelle de réplication. Le serveur de traitement :
  - Reçoit les données de réplication.
  - Optimise les données de réplication en utilisant la mise en cache, la compression et le chiffrement.
  - Envoie les données de réplication vers Stockage Azure.
- Le serveur de processus installe également le service Mobilité sur les machines virtuelles à répliquer. Le serveur de traitement effectue la découverte automatique des machines virtuelles VMware locales.
- Une fois la machine virtuelle du serveur de configuration créée et démarrée, Contoso inscrit le serveur dans le coffre.

Pour configurer l’environnement source, les administrateurs de Contoso effectuent les opérations suivantes :

1. Ils téléchargent le modèle OVF à partir du portail Azure (**Préparer l’infrastructure** > **Source** > **Serveur de configuration**).

    ![Ajouter un serveur de configuration](./media/contoso-migration-rehost-vm-sql-managed-instance/add-cs.png)

2. Le modèle est importé dans VMware pour créer et déployer la machine virtuelle.

    ![Déployer le modèle OVF](./media/contoso-migration-rehost-vm-sql-managed-instance/vcenter-wizard.png)

3. Quand ils activent la machine virtuelle pour la première fois, elle démarre dans un environnement d’installation Windows Server 2016. Ils acceptent le contrat de licence et entrent un mot de passe d’administrateur.
4. Une fois l’installation terminée, ils se connectent à la machine virtuelle comme administrateur. À la première connexion, l’outil de configuration d’Azure Site Recovery s’exécute automatiquement.
5. Dans l’outil de configuration de Site Recovery, ils entrent un nom à utiliser pour inscrire le serveur de configuration dans le coffre.
6. L’outil vérifie la connexion de la machine virtuelle à Azure. Une fois la connexion établie, ils sélectionnent **Se connecter** pour se connecter à l’abonnement Azure. Les informations d’identification doivent avoir accès au coffre dans lequel le serveur de configuration est inscrit.

    ![Inscrire le serveur de configuration](./media/contoso-migration-rehost-vm-sql-managed-instance/config-server-register2.png)

7. L’outil effectue des tâches de configuration, puis redémarre. Ils se reconnectent à la machine. L’Assistant Gestion de serveur de configuration démarre automatiquement.
8. Dans l’Assistant, Contoso sélectionne la carte réseau qui doit recevoir le trafic de réplication. Une fois configuré, ce paramètre ne peut pas être modifié.
9. Ils sélectionnent l’abonnement, le groupe de ressources et le coffre Recovery Services dans lequel inscrire le serveur de configuration.

    ![Sélectionner le coffre Recovery Services](./media/contoso-migration-rehost-vm-sql-managed-instance/cswiz1.png)

10. Ils téléchargent et installent MySQL Server et VMware PowerCLI. Ensuite, ils valident les paramètres du serveur.
11. Après la validation, ils entrent le FQDN ou l’adresse IP de l’instance vCenter Server ou de l’hôte vSphere. Ils gardent le port par défaut et entrent un nom d’affichage pour l’instance vCenter Server dans Azure.
12. Ils spécifient le compte créé précédemment pour que Site Recovery puisse découvrir automatiquement les machines virtuelles VMware disponibles pour la réplication.
13. Ils entrent les informations d’identification pour que le service Mobilité soit installé automatiquement quand la réplication est activée. Pour des machines virtuelles Windows, le compte doit disposer d’autorisations d’administrateur local sur celles-ci.

    ![Configurer vCenter Server](./media/contoso-migration-rehost-vm-sql-managed-instance/cswiz2.png)

14. Une fois l’inscription terminée, dans le portail Azure, ils revérifient que le serveur de configuration et le serveur VMware sont répertoriés dans la page **Source** du coffre. La détection peut prendre 15 minutes ou plus.
15. Site Recovery se connecte aux serveurs VMware en utilisant les paramètres spécifiés et découvre les machines virtuelles.

### <a name="set-up-the-target"></a>Configurer la cible

Les administrateurs de Contoso doivent à présent configurer l’environnement de réplication cible :

1. Dans **Préparer l’infrastructure** > **Cible**, Contoso sélectionne les paramètres de la cible.
2. Site Recovery vérifie qu’il existe un compte de stockage et un réseau dans la cible spécifiée.

### <a name="create-a-replication-policy"></a>Créer une stratégie de réplication

Une fois la source et la cible configurées, les administrateurs de Contoso créent une stratégie de réplication et l’associe au serveur de configuration :

1. Dans **Préparer l’infrastructure** > **Paramètres de réplication** > **Stratégie de réplication** >  **Créer et associer**, ils créent la stratégie **ContosoMigrationPolicy**.
2. Contoso utilise les paramètres par défaut :
    - **Seuil d’objectif de point de récupération :** la valeur par défaut est de 60 minutes. Cette valeur définit la fréquence à laquelle les points de récupération sont créés. Une alerte est générée lorsque la réplication continue dépasse cette limite.
    - **Conservation des points de récupération :** La valeur par défaut est 24 heures. Cette valeur spécifie la durée de la fenêtre de rétention pour chaque point de récupération. Les machines virtuelles répliquées peuvent être récupérées à n’importe quel point dans une fenêtre.
    - **Fréquence des instantanés de cohérence des applications :** la valeur par défaut est de 1 heure. Cette valeur spécifie la fréquence à laquelle les captures instantanées de cohérence d’application sont créées.

    ![Stratégie de réplication - Créer](./media/contoso-migration-rehost-vm-sql-managed-instance/replication-policy.png)

3. La stratégie est automatiquement associée au serveur de configuration.

    ![Stratégie de réplication - Associer](./media/contoso-migration-rehost-vm-sql-managed-instance/replication-policy2.png)

**Besoin de plus d’aide ?**

- Une procédure pas à pas complète de ces étapes est décrite dans [Configurer la récupération d’urgence pour des machines virtuelles VMware locales](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial).
- Des instructions détaillées sont disponibles pour vous aider à [configurer l’environnement source](https://docs.microsoft.com/azure/site-recovery/vmware-azure-set-up-source), à [déployer le serveur de configuration](https://docs.microsoft.com/azure/site-recovery/vmware-azure-deploy-configuration-server) et à [configurer les paramètres de réplication](https://docs.microsoft.com/azure/site-recovery/vmware-azure-set-up-replication).

### <a name="enable-replication"></a>Activer la réplication

Maintenant, les administrateurs de Contoso peuvent commencer à répliquer la machine WebVM.

1. Dans **Répliquer l’application** > **Source** > **Répliquer**, ils sélectionnent les paramètres de la source.
2. Ils indiquent qu’ils veulent activer les machines virtuelles, sélectionnent l’instance vCenter Server et définissent le serveur de configuration.

    ![Activer la réplication - Source](./media/contoso-migration-rehost-vm-sql-managed-instance/enable-replication1.png)

3. Ils spécifient les paramètres cibles, notamment le groupe de ressources et le réseau où se trouve la machine virtuelle Azure après le basculement. Ils spécifient le compte de stockage où stocker les données répliquées.

    ![Activer la réplication - Cible](./media/contoso-migration-rehost-vm-sql-managed-instance/enable-replication2.png)

4. Ils sélectionnent **WebVM** pour la réplication. Site Recovery installe le service Mobilité sur chaque machine virtuelle quand la réplication est activée.

    ![Activer la réplication - Sélectionner la machine virtuelle](./media/contoso-migration-rehost-vm-sql-managed-instance/enable-replication3.png)

5. Ils vérifient que la stratégie de réplication appropriée est sélectionnée et activent la réplication pour la machine virtuelle **WEBVM**. Contoso suit la progression de la réplication dans **Travaux**. Une fois le travail **Finaliser la protection** exécuté, la machine est prête pour le basculement.

6. Dans le portail Azure, dans **Éléments principaux**, ils peuvent voir l’état des machines virtuelles répliquées sur Azure :

    ![Vue de l’infrastructure](./media/contoso-migration-rehost-vm-sql-managed-instance/essentials.png)

**Besoin de plus d’aide ?**

La procédure pas à pas complète de ces étapes est décrite dans [Activer la réplication](https://docs.microsoft.com/azure/site-recovery/vmware-azure-enable-replication).

## <a name="step-6-migrate-the-database"></a>Étape 6 : Migrer la base de données

Les administrateurs de Contoso doivent créer un projet Azure Database Migration Service, puis migrer la base de données.

### <a name="create-an-azure-database-migration-service-project"></a>Créer un projet Azure Database Migration Service

1. Ils créent un projet Azure Database Migration Service. Ils sélectionnent le type de serveur source **SQL Server** et la cible **Azure SQL Database Managed Instance**.

     ![Database Migration Service - Nouveau projet de migration](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-project.png)

2. L’Assistant Migration s’ouvre.

### <a name="migrate-the-database"></a>Migrer la base de données

1. Dans l’Assistant Migration, ils spécifient la machine virtuelle source où se trouve la base de données locale. Ils entrent les informations d’identification pour accéder à la base de données.

    ![Database Migration Service - Détails de la source](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-wizard-source.png)

2. Ils sélectionnent la base de données à migrer (**SmartHotel.Registration**) :

    ![Database Migration Service - Sélectionner les bases de données sources](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-wizard-sourcedb.png)

3. Pour la cible, ils entrent le nom de l’instance gérée dans Azure et les informations d’identification d’accès.

    ![Database Migration Service - Détails de la cible](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-target-details.png)

4. Dans **Nouvelle activité** > **Exécuter la migration**, ils spécifient les paramètres d’exécution de la migration :
    - Informations d’identification de la source et de la cible.
    - La base de données à migrer.
    - Le partage réseau créé sur la machine virtuelle locale. Azure Database Migration Service prend les sauvegardes sources sur ce partage.
        - Le compte de service qui exécute l’instance source de SQL Server doit avoir des autorisations d’écriture sur ce partage réseau.
        - Le chemin du nom de domaine complet (FQDN) du partage doit être utilisé.
    - L’URI SAP qui donne à Azure Database Migration Service l’accès au conteneur du compte de stockage dans lequel le service charge les fichiers de sauvegarde pour la migration.

        ![Database Migration Service - Configurer les paramètres de migration](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-migration-settings.png)

5. Ils enregistrent les paramètres de migration, puis exécutent la migration.
6. Dans **Vue d’ensemble**, ils surveillent l’état de la migration.

    ![Database Migration Service - Surveiller](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-monitor1.png)

7. Une fois la migration terminée, ils vérifient que les bases de données cibles existent sur l’instance gérée.

    ![Database Migration Service - Vérifier la migration de base de données](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-monitor2.png)

## <a name="step-7-migrate-the-vm"></a>Étape 7 : Migrer la machine virtuelle

Les administrateurs de Contoso exécutent un rapide test de basculement, puis migrent la machine virtuelle.

### <a name="run-a-test-failover"></a>Exécuter un test de basculement

Avant de migrer la machine virtuelle WEBVM, un test de basculement permet de s’assurer que tout fonctionne comme prévu. Les administrateurs effectuent les étapes suivantes :

1. Ils exécutent un basculement de test jusqu’au dernier point dans le temps disponible (**Dernier point traité**).
2. Ils sélectionnent **Arrêter la machine avant de commencer le basculement**. Cette option étant sélectionnée, Site Recovery tente d’arrêter la machine virtuelle source avant de déclencher le basculement. Le basculement se poursuit même en cas d’échec de l’arrêt.
3. Le test de basculement est exécuté : a. Une vérification des prérequis est effectuée pour s’assurer que toutes les conditions nécessaires pour la migration sont en place.
    b. Le basculement traite les données pour permettre la création d’une machine virtuelle Azure. Si le dernier point de récupération est sélectionné, un point de récupération est créé à partir des données.
    c. Une machine virtuelle Azure est créée en utilisant les données traitées à l’étape précédente.
4. Une fois le basculement terminé, la machine virtuelle Azure répliquée apparaît dans le portail Azure. Ils vérifient que tout fonctionne correctement : la machine virtuelle a la taille appropriée, elle est connectée au réseau approprié et elle est en cours d’exécution.
5. Après avoir vérifié le basculement de test, ils nettoient le basculement et consignent les observations éventuelles.

### <a name="migrate-the-vm"></a>Migrer la machine virtuelle

1. Après avoir vérifié que le basculement de test a fonctionné comme prévu, les administrateurs de Contoso créent un plan de récupération pour la migration et y ajoutent une machine WEBVM :

     ![Créer un plan de récupération - Sélectionner des éléments](./media/contoso-migration-rehost-vm-sql-managed-instance/recovery-plan.png)

2. Ils exécutent un basculement sur le plan, en sélectionnant le dernier point de récupération. Ils spécifient que Site Recovery doit essayer d’arrêter la machine virtuelle locale avant de déclencher le basculement.

    ![Basculement](./media/contoso-migration-rehost-vm-sql-managed-instance/failover1.png)

3. Après le basculement, elle vérifie que l’ordinateur virtuel Azure s’affiche comme prévu dans le portail Azure.

   ![Détails du plan de récupération](./media/contoso-migration-rehost-vm-sql-managed-instance/failover2.png)

4. Après la vérification, ils effectuent la migration pour terminer le processus, arrêtent la réplication de la machine virtuelle ainsi que la facturation de Site Recovery pour la machine virtuelle.

    ![Basculement - Terminer la migration](./media/contoso-migration-rehost-vm-sql-managed-instance/failover3.png)

### <a name="update-the-connection-string"></a>Mettre à jour la chaîne de connexion

Dans la dernière étape du processus de migration, les administrateurs de Contoso mettent à jour la chaîne de connexion de l’application pour qu’elle pointe vers la base de données migrée qui s’exécute sur l’instance gérée de Contoso.

1. Dans le portail Azure, ils recherchent la chaîne de connexion en sélectionnant **Paramètres** > **Chaînes de connexion**.

    ![Chaînes de connexion](./media/contoso-migration-rehost-vm-sql-managed-instance/failover4.png)

2. Ils mettent à jour la chaîne avec le nom d’utilisateur et le mot de passe de SQL Database Managed Instance.
3. Une fois la chaîne configurée, ils remplacent la chaîne de connexion actuelle dans le fichier web.config de l’application.
4. Après avoir mis à jour et enregistré le fichier, ils redémarrent IIS sur la machine WEBVM en exécutant `IISRESET /RESTART` dans une fenêtre d’invite de commandes.
5. Une fois IIS redémarré, l’application utilise la base de données qui s’exécute sur SQL Database Managed Instance.
6. À ce stade, ils peuvent arrêter la machine SQLVM locale. La migration est terminée.

**Besoin de plus d’aide ?**

- Découvrez comment [exécuter un test de basculement](https://docs.microsoft.com/azure/site-recovery/tutorial-dr-drill-azure).
- Découvrez comment [créer un plan de récupération](https://docs.microsoft.com/azure/site-recovery/site-recovery-create-recovery-plans).
- Découvrez comment [basculer vers Azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-failover).

## <a name="clean-up-after-migration"></a>Nettoyer après la migration

Une fois la migration terminée, l’application SmartHotel360 s’exécute sur une machine virtuelle Azure, et la base de données SmartHotel360 est disponible dans Azure SQL Database Managed Instance.

Contoso doit à présent effectuer les tâches de nettoyage suivantes :

- Supprimer la machine virtuelle WEBVM de l’inventaire vCenter Server
- Supprimer la machine virtuelle SQLVM de l’inventaire vCenter Server
- Supprimer les machines virtuelles WEBVM et SQLVM des travaux de sauvegarde locaux.
- Mettre à jour la documentation interne afin qu’elle indique le nouvel emplacement et l’adresse IP de WEBVM
- Supprime SQLVM de la documentation interne. En guise d’alternative, Contoso peut réviser la documentation afin de signaler que SQLVM a été supprimée et ne figure plus dans l’inventaire des machines virtuelles
- Passer en revue toutes les ressources qui interagissent avec les machines virtuelles qui ont été mises hors service Mettre à jour les paramètres ou la documentation appropriés afin de refléter la nouvelle configuration

## <a name="review-the-deployment"></a>Examiner le déploiement

Les ressources ayant été migrées dans Azure, Contoso doit rendre sa nouvelle infrastructure entièrement opérationnelle et la sécuriser.

### <a name="security"></a>Sécurité

L’équipe de sécurité de Contoso examine les machines virtuelles Azure et SQL Database Managed Instance pour détecter d’éventuels problèmes de sécurité liés à son implémentation.

- L’équipe examine les groupes de sécurité réseau qui sont utilisés pour contrôler l’accès à la machine virtuelle. Les groupes de sécurité réseau aident à s’assurer que seul le trafic autorisé à accéder à l’application peut passer.
- L’équipe de sécurité de Contoso prend également en considération la sécurisation des données sur le disque à l’aide d’Azure Disk Encryption et d’Azure Key Vault.
- L’équipe active la détection des menaces sur l’instance gérée. La détection des menaces envoie une alerte à l’équipe de sécurité/au système de support de Contoso afin d’ouvrir un ticket en cas de détection d’une menace. Apprenez-en davantage sur la [détection des menaces pour Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-threat-detection).

     ![Sécurité de Managed Instance - Détection des menaces](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-security.png)

Pour en savoir plus sur les pratiques de sécurité pour les machines virtuelles, consultez [Bonnes pratiques de sécurité pour les charges de travail IaaS dans Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

### <a name="bcdr"></a>BCDR

Pour assurer la continuité et la reprise d’activité (BCDR), Contoso effectue les actions suivantes :

- Sécuriser les données : Contoso sauvegarde les données sur les machines virtuelles à l’aide du service Sauvegarde Azure. [Plus d’informations](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)
- Faire en sorte que les applications soient opérationnelles : Contoso réplique les machines virtuelles de l’application dans Azure vers une région secondaire à l’aide de Site Recovery. [Plus d’informations](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)
- Contoso sait maintenant comment gérer SQL Managed Instance, y compris les [sauvegardes de base de données](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

- Contoso dispose déjà d’une licence pour WEBVM. Pour tirer parti de la tarification avec Azure Hybrid Benefit, Contoso convertit la machine virtuelle Azure existante.
- Contoso active Azure Cost Management sous licence de Cloudyn, une filiale de Microsoft. Cost Management est une solution de gestion des coûts multicloud qui aide Contoso à utiliser et à gérer Azure et d’autres ressources cloud. Apprenez-en davantage sur [Azure Cost Management](https://docs.microsoft.com/azure/cost-management/overview).

## <a name="conclusion"></a>Conclusion

Cet article décrit comment Contoso réhéberge l’application SmartHotel360 dans Azure en migrant la machine virtuelle du frontend de l’application vers Azure avec le service Site Recovery. Contoso migre la base de données locale vers Azure SQL Database Managed Instance à l’aide d’Azure Database Migration Service.
