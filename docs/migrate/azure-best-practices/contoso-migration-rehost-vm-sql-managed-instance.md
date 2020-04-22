---
title: Réhéberger une application locale en migrant vers des machines virtuelles Azure et Azure SQL Database Managed Instance
description: Découvrez comment Contoso réhéberge une application locale sur des machines virtuelles Azure et Azure SQL Database Managed Instance.
author: givenscj
ms.author: abuck
ms.date: 04/02/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 089a772bdc41bc96f327f9d9ce34d2107fd48934
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80996795"
---
<!-- cSpell:ignore givenscj WEBVM SQLVM OSTICKETWEB OSTICKETMYSQL contosohost vcenter contosodc NSGs agentless SQLMI iisreset -->

# <a name="rehost-an-on-premises-app-on-an-azure-vm-and-sql-database-managed-instance"></a>réhéberger une application locale sur une machine virtuelle Azure et SQL Database Managed Instance

Cet article explique comment la société fictive Contoso migre une application frontale Windows .NET à deux niveaux qui s’exécute sur des machines virtuelles VMware vers une machine virtuelle Azure à l’aide du service Azure Migrate. Il explique également la façon dont Contoso migre la base de données d’application vers Azure SQL Database Managed Instance.

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

![Architecture du scénario](./media/contoso-migration-rehost-vm-sql-managed-instance/architecture.png)

### <a name="database-considerations"></a>Considérations liées à la base de données

Dans le cadre de la conception de la solution, Contoso a fait une comparaison des fonctionnalités entre Azure SQL Database et SQL Server Managed Instance. Les administrateurs ont choisi Managed Instance sur la base des considérations suivantes.

- Managed Instance vise à fournir une compatibilité de quasi 100 % avec la dernière version locale de SQL Server. Microsoft recommande Managed Instance aux clients qui exécutent SQL Server localement ou sur une machine virtuelle IaaS et qui souhaitent migrer leurs applications vers un service entièrement managé en changeant le moins possible la conception.
- Contoso a l’intention de migrer un grand nombre d’applications locales vers IaaS. Beaucoup d’entre elles sont fournies par l’ISV. Contoso se rend compte que Managed Instance peut garantir une compatibilité de base de données pour ces applications que SQL Database ne prend peut-être pas en charge.
- Contoso peut effectuer une migration lift-and-shift vers Managed Instance à l’aide d’Azure Database Migration Service entièrement automatisé. Une fois ce service en place, Contoso peut le réutiliser pour les futures migrations de base de données.
- SQL Managed Instance prend en charge SQL Server Agent, qui est un composant essentiel pour l’application SmartHotel360. Contoso a besoin de cette compatibilité, sous peine de devoir recréer les plans de maintenance demandés par l’application.
- Avec Software Assurance, Contoso peut échanger ses licences existantes contre une réduction de tarif sur SQL Database Managed Instance en utilisant Azure Hybrid Benefit pour SQL Server. Contoso peut alors économiser jusqu'à 30 % sur Managed Instance.
- SQL Managed Instance est entièrement contenu dans le réseau virtuel ; il fournit donc une isolation et sécurité accrues pour les données de Contoso. Contoso peut obtenir les avantages du cloud public tout en isolant l’environnement du réseau Internet public.
- Managed Instance prend en charge plusieurs fonctionnalités de sécurité, notamment le chiffrement permanent, le masquage dynamique des données, la sécurité au niveau des lignes et la détection des menaces.

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant la liste des avantages et des inconvénients.

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
3. La couche web sera migrée à l’aide d’une migration lift-and-shift avec Azure Migrate. Ce processus nécessite la préparation de l’environnement VMware local, la configuration et l’activation de la réplication, et la migration des machines virtuelles par leur basculement vers Azure.

     ![Architecture de la migration](./media/contoso-migration-rehost-vm-sql-managed-instance/migration-architecture.png)

### <a name="azure-services"></a>Services Azure

Service | Description | Coût
--- | --- | ---
[Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview) | Azure Database Migration Service permet une migration fluide à partir de plusieurs sources de base de données vers des plateformes de données Azure, avec un temps d’arrêt minimal. | Apprenez-en davantage sur les [régions prises en charge](https://docs.microsoft.com/azure/dms/dms-overview#regional-availability) et sur la [tarification de Database Migration Service](https://azure.microsoft.com/pricing/details/database-migration).
[Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) | Managed Instance est un service de base de données managé qui représente une instance de SQL Server entièrement managée dans le cloud Azure. Il utilise le même code que la dernière version du moteur de base de données SQL Server et offre les dernières fonctionnalités, améliorations en termes de performances et correctifs de sécurité. | L’utilisation de SQL Database Managed Instance exécuté dans Azure entraîne des frais basés sur la capacité. Apprenez-en davantage sur la [tarification de Managed Instance](https://azure.microsoft.com/pricing/details/sql-database/managed).
[Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-overview) | Contoso utilise le service Azure Migrate pour évaluer ses machines virtuelles VMware. Azure Migrate évalue la pertinence de la migration des ordinateurs. Il fournit des estimations de dimensionnement et de coût pour l’exécution des machines dans Azure. | À compter de mai 2018, Azure Migrate devient un service gratuit.

## <a name="prerequisites"></a>Prérequis

Contoso et les autres utilisateurs doivent respecter les prérequis suivants pour ce scénario :

<!-- markdownlint-disable MD033 -->

Spécifications | Détails
--- | ---
**Abonnement Azure** | Vous devez avoir déjà créé un abonnement quand vous effectuez l’évaluation dans le premier article de cette série. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions.<br/><br/> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur de l’abonnement, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur aux ressources et aux groupes de ressources nécessaires.
**Infrastructure Azure** | Contoso configure son infrastructure Azure comme décrit dans [Infrastructure Azure pour la migration](./contoso-migration-infrastructure.md).
**Serveurs locaux** | L’instance vCenter Server locale doit exécuter la version 5.5, 6.0 ou 6.5.<br/><br/> Un hôte ESXi qui exécute la version 5.5, 6.0 ou 6.5<br/><br/> Une ou plusieurs machines virtuelles VMware exécutées sur l’hôte ESXi.
**Machines virtuelles locales** | [Examinez les machines Linux](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros) approuvées pour s’exécuter sur Azure.
**Database Migration Service** | Pour Azure Database Migration Service, vous avez besoin d’un [périphérique VPN local compatible](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).<br/><br/> Vous devez être en mesure de configurer l’appareil VPN local. Il doit avoir une adresse IPv4 publique externe. L’adresse ne peut pas se trouver derrière un périphérique NAT.<br/><br/> Assurez-vous de disposer de l’accès à votre base de données SQL Server locale.<br/><br/> Le Pare-feu Windows doit pouvoir accéder au moteur de base de données source. Découvrez comment [configurer le Pare-feu Windows pour accéder au moteur de base de données](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access).<br/><br/> S’il y a un pare-feu devant votre machine de base de données, ajoutez des règles pour autoriser l’accès à la base de données, et aux fichiers par le biais du port SMB 445.<br/><br/> Les informations d’identification utilisées pour se connecter à l’instance source SQL Server et à l’instance cible Managed Instance doivent appartenir à des membres du rôle serveur sysadmin.<br/><br/> Il vous faut un partage réseau dans votre base de données locale qu’Azure Database Migration Service peut utiliser pour sauvegarder la base de données source.<br/><br/> Vérifiez que le compte de service qui exécute l’instance source de SQL Server dispose d’autorisations d’écriture sur le partage réseau.<br/><br/> Notez l’utilisateur Windows (et son mot de passe) qui dispose d’autorisations complètes sur le partage réseau. Azure Database Migration Service emprunte ces informations d’identifications pour charger les fichiers de sauvegarde sur le conteneur de stockage Azure.<br/><br/> Le processus d’installation SQL Server Express définit le protocole TCP/IP sur **Désactivé** par défaut. Veillez à l’activer.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment Contoso prévoie de configurer le déploiement :

> [!div class="checklist"]
>
> - **Étape 1 : Préparer SQL Database Managed Instance.** Contoso a besoin d’une instance managée existante vers laquelle la base de données SQL Server locale migrera.
> - **Étape 2 : Préparer Azure Database Migration Service.** Contoso doit inscrire le fournisseur de migration de base de données, créer une instance, puis créer un projet Azure Database Migration Service. Contoso doit également configurer un URI (Uniform Resource Identifier) avec signature d’accès partagé (SAP) pour Azure Database Migration Service. Un URI SAP fournit un accès délégué aux ressources du compte de stockage Contoso. Ainsi, Contoso peut accorder des autorisations limitées aux objets de stockage. Contoso configure un URI SAP pour qu’Azure Database Migration Service puisse accéder au conteneur du compte de stockage sur lequel le service charge les fichiers de sauvegarde SQL Server.
> - **Étape 3 : Préparer Azure pour l’outil Migration de serveur Azure Migrate.** L’outil de migration de serveur a été ajouté dans le projet Azure Migrate.
> - **Étape 4 : Préparer l’instance VMware locale pour l’outil Migration de serveur Azure Migrate.** Ils préparent des comptes pour la découverte de machines virtuelles. Ils préparent également la connexion aux machines virtuelles Azure après migration.
> - **Étape 5 : Répliquer les machines virtuelles.** Ils configurent la réplication et de commencer à répliquer des machines virtuelles dans le stockage Azure.
> - **Étape 6 : Migrer la base de données à l’aide d’Azure Database Migration Service.** Contoso migre la base de données.
> - **Étape 7 : Migrer la machine virtuelle avec l’outil Migration de serveur Azure Migrate.** Ils effectuent un test de migration pour vérifier que tout fonctionne correctement, puis opèrent une migration complète pour déplacer les machines virtuelles vers Azure.

## <a name="step-1-prepare-a-sql-database-managed-instance"></a>Étape 1 : Préparer SQL Database Managed Instance

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
    - **SQLMI-DS-EUS2** (10.235.0.0.25).
    - **SQLMI-SAW-EUS2** (10.235.0.128/29). Ce sous-réseau est utilisé pour joindre l’annuaire à Managed Instance.

      ![Managed Instance - Créer un réseau virtuel](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-vnet.png)

4. Une fois le réseau virtuel et les sous-réseaux déployés, ils appairent les réseaux de la façon suivante :

    - Peering de **VNET-SQLMI-EUS2** avec **VNET-HUB-EUS2** (réseau virtuel hub pour la région USA Est 2).
    - Peering de **VNET-SQLMI-EUS2** avec **VNET-PROD-EUS2** (réseau de production).

      ![Peering de réseau](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-peering.png)

5. Ils définissent des paramètres DNS personnalisés. Le système DNS pointe tout d’abord sur les contrôleurs de domaine Azure de Contoso. Azure DNS est secondaire. Les contrôleurs de domaine Azure de Contoso se situent comme suit :

    - Situé sur le sous-réseau **PROD-CC-EUS2**, sur le réseau de production USA Est 2 (**VNET-PROD-EUS2**).
    - Adresse de **CONTOSODC3** : 10.245.42.4.
    - Adresse de **CONTOSODC4** : 10.245.42.5.
    - Programme de résolution d’Azure DNS : 168.63.129.16.

      ![Serveurs DNS du réseau](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-dns.png)

**Besoin de plus d’aide ?**

- Obtenez une vue d’ensemble de [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
- Découvrez comment [créer un réseau virtuel pour SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-vnet-configuration).
- Découvrez comment [configurer le peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-manage-peering).
- Découvrez comment [mettre à jour les paramètres DNS d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory-domain-services/tutorial-create-instance).

### <a name="set-up-routing"></a>Configuration du routage

Managed Instance est placé sur un réseau privé virtuel. Contoso a besoin d’une table de routage pour que le réseau virtuel communique avec le service de gestion Azure. Si le réseau virtuel ne peut pas communiquer avec le service qui le gère, le réseau virtuel devient inaccessible.

Contoso prend en compte ces facteurs :

- La table de routage contient un ensemble de règles (itinéraires) qui spécifient le mode de routage des paquets envoyés à partir de Managed Instance sur le réseau virtuel.
- La table de routage est associée à des sous-réseaux dans lesquels les instances gérées sont déployées. Chaque paquet quittant un sous-réseau est géré en fonction de la table de routage associée.
- Un sous-réseau ne peut être associé qu’à une seule table de routage.
- La création de tables de routage dans Microsoft Azure n’occasionne aucun frais.

 Pour configurer le routage, les administrateurs de Contoso effectuent les opérations suivantes :

1. Ils créent une table de routage définie par l’utilisateur dans le groupe de ressources **ContosoNetworkingRG**.

    ![Table de routage](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table.png)

2. Pour respecter les exigences de Managed Instance, une fois la table de routage (**MIRouteTable**) déployée, ils ajoutent une route avec le préfixe d’adresse 0.0.0.0/0. L’option **Type de tronçon suivant** est définie sur **Internet**

    ![Préfixe de table de routage](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-prefix.png)

3. Ils associent la table de routage au sous-réseau **SQLMI-DB-EUS2** (dans le réseau **VNET-SQLMI-EUS2**).

    ![Sous-réseau de table de routage](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-subnet.png)

**Besoin de plus d’aide ?**

Découvrez comment [configurer des itinéraires pour une instance gérée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started).

### <a name="create-a-managed-instance"></a>Créer une option Managed Instance

À présent, les administrateurs de Contoso peuvent provisionner une instance SQL Database Managed Instance :

1. Comme l’instance gérée sert une application métier, ils la déploient dans la région USA Est 2 primaire de l’entreprise. Ils ajoutent l’instance gérée au groupe de ressources **ContosoRG**.
2. Ils sélectionnent un niveau tarifaire, une taille de calcul et un stockage pour l’instance. Apprenez-en davantage sur la [tarification de Managed Instance](https://azure.microsoft.com/pricing/details/sql-database/managed).

    ![Instance gérée](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-create.png)

3. Une fois l’instance gérée déployée, deux nouvelles ressources apparaissent dans le groupe de ressources **ContosoRG** :

    - Un cluster virtuel si Contoso a plusieurs instances gérées
    - L’instance gérée SQL Server Database

      ![Instance gérée](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-resources.png)

**Besoin de plus d’aide ?**

Découvrez comment [provisionner une instance gérée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started).

## <a name="step-2-prepare-the-azure-database-migration-service"></a>Étape 2 : Préparer Azure Database Migration Service

Pour préparer Azure Database Migration Service, les administrateurs de Contoso doivent effectuer quelques opérations :

- Inscrire le fournisseur Azure Database Migration Service dans Azure.
- Fournir à Azure Database Migration Service l’accès à Stockage Azure pour charger les fichiers de sauvegarde utilisés pour migrer une base de données. Pour fournir l’accès au Stockage Azure, ils créent un conteneur de Stockage Blob Azure. Ils génèrent un URI SAP pour le conteneur de stockage Blob.
- Créer un projet Azure Database Migration Service.

Ensuite, ils effectuent les tâches suivantes :

1. Ils inscrivent le fournisseur de migration de base de données sous l’abonnement.
    ![Database Migration Service - Registre](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-subscription.png)

2. Ils créent un conteneur de stockage Blob. Contoso génère un URI SAP afin qu’Azure Database Migration Service puisse y accéder.

    ![Database Migration Service - Générer un URI SAP](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-sas.png)

3. Ils créent une instance Azure Database Migration Service.

    ![Database Migration Service - Créer une instance](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-instance.png)

4. Ils placent l’instance Azure Database Migration Service dans le sous-réseau **PROD-DC-EUS2** du réseau virtuel **VNET-PROD-DC-EUS2**.
    - Azure Database Migration Service est placé à cet endroit, car le service doit être dans un réseau virtuel pouvant accéder à la machine virtuelle SQL Server locale via une passerelle VPN.
    - **VNET-PROD-EUS2** est appairé à **VNET-HUB-EUS2** et autorisé à utiliser des passerelles distantes. L’option **Utiliser des passerelles distantes** garantit qu’Azure Database Migration Service peut communiquer en fonction des besoins.

        ![Database Migration Service - Configurer le réseau](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-network.png)

**Besoin de plus d’aide ?**

- Découvrez comment [configurer Azure Database Migration Service](https://docs.microsoft.com/azure/dms/quickstart-create-data-migration-service-portal).
- Découvrez comment [créer et utiliser une signature d’accès partagé](https://docs.microsoft.com/azure/storage/blobs/storage-dotnet-shared-access-signature-part-2).

## <a name="step-3-prepare-azure-for-the-azure-migrate-server-migration-tool"></a>Étape 3 : Préparer Azure pour l’outil Migration de serveur Azure Migrate

Les composants Azure dont Contoso a besoin pour migrer les machines virtuelles vers Azure sont les suivants :

- Un réseau virtuel dans lequel les machines virtuelles Azure seront situées après leur création pendant la migration.
- L’outil Migration de serveur Azure Migrate a été provisionné.

La configuration est effectuée´comme suit :

1. **Configurer un réseau :** la société Contoso a déjà configuré un réseau utilisable pour l’outil Migration de serveur Azure Migrate quand elle a [déployé l’infrastructure Azure](./contoso-migration-infrastructure.md).

    - L’application SmartHotel360 est une application de production, et les machines virtuelles seront migrées vers le réseau de production Azure (VNET-PROD-EUS2) dans la région USA Est 2 principale.
    - Les deux machines virtuelles seront placées dans le groupe de ressources ContosoRG utilisé pour les ressources de production.
    - La machine virtuelle frontale de l’application (WEBVM) migrera vers le sous-réseau frontal (PROD-FE-EUS2) dans le réseau de production.
    - La machine virtuelle de la base de données de l’application (SQLVM) migrera vers le sous-réseau de la base de données (PROD-DB-EUS2) dans le réseau de production.

## <a name="step-4-prepare-on-premises-vmware-for-azure-migrate-server-migration"></a>Étape 4 : Préparer l’instance VMware locale pour l’outil Migration de serveur Azure Migrate

Les composants Azure dont Contoso a besoin pour migrer les machines virtuelles vers Azure sont les suivants :

- Un réseau virtuel dans lequel les machines virtuelles Azure seront situées après leur création pendant la migration.
- L’outil Migration de serveur Azure Migrate (OVA) a été provisionné et configuré.

La configuration est effectuée´comme suit :

1. Configurer un réseau : la société Contoso a déjà configuré un réseau utilisable pour l’outil Migration de serveur Azure Migrate lorsqu’elle a [déployé l’infrastructure Azure](./contoso-migration-infrastructure.md).

    - L’application SmartHotel360 est une application de production, et les machines virtuelles seront migrées vers le réseau de production Azure (VNET-PROD-EUS2) dans la région USA Est 2 principale.
    - Les deux machines virtuelles seront placées dans le groupe de ressources ContosoRG utilisé pour les ressources de production.
    - La machine virtuelle frontale de l’application (WEBVM) migrera vers le sous-réseau frontal (PROD-FE-EUS2) dans le réseau de production.
    - La machine virtuelle de la base de données de l’application (SQLVM) migrera vers le sous-réseau de la base de données (PROD-DB-EUS2) dans le réseau de production.

2. Provisionner l’outil Migration de serveur Azure Migrate.

    - À partir d’Azure Migrate, téléchargez l’image OVA et importez-la dans VMWare.

        ![Télécharger le fichier OVA](./media/contoso-migration-rehost-vm/migration-download-ova.png)

    - Démarrez l’image importée et configurez l’outil, en procédant comme suit :

      - Remplir les conditions préalables.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-setup-prerequisites.png)

      - Pointez l’outil sur l’abonnement Azure.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-register-azure.png)

      - Définissez les informations d’identification de VMWare vCenter.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-vcenter-server.png)

      - Ajoutez les informations d’identification basées sur Linux ou Windows pour la découverte.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-credentials.png)

3. Une fois configuré, l’outil peut mettre un certain temps à énumérer tous les ordinateurs virtuels. Une fois terminé, vous constaterez qu’ils sont renseignés dans l’outil Azure Migrate dans Azure.

**Besoin de plus d’aide ?**

[En savoir plus](https://docs.microsoft.com/azure/migrate) sur la configuration de l’outil Migration de serveur Azure Migrate.

### <a name="prepare-on-premises-vms"></a>Préparer des machines virtuelles sur site

Après la migration, Contoso souhaite se connecter aux machines virtuelles Azure et autoriser Azure à gérer les machines virtuelles. Pour ce faire, les administrateurs effectuent les opérations suivantes avant la migration :

1. Pour l’accès via Internet :

    - Activez le protocole RDP ou SSH sur la machine virtuelle locale avant la migration.
    - Elle s’assure que les règles de TCP et UDP sont ajoutées au profil **Public**.
    - Vérifiez que le protocole RDP ou SSH est autorisé dans le pare-feu du système d’exploitation.

2. Pour l’accès via le VPN de site à site :

    - Activez le protocole RDP ou SSH sur la machine virtuelle locale avant la migration.
    - Vérifiez que le protocole RDP ou SSH est autorisé dans le pare-feu du système d’exploitation.
    - Pour Windows, définissez la stratégie SAN du système d’exploitation sur la machine virtuelle locale sur **OnlineAll**.

3. Installez l’agent Azure :

    - [Agent Linux Azure](https://docs.microsoft.com/azure/virtual-machines/extensions/agent-linux)
    - [Agent Windows Azure](https://docs.microsoft.com/azure/virtual-machines/extensions/agent-windows)

4. Divers

   - Pour Windows, aucune mise à jour de Windows ne peut être en attente sur la machine virtuelle lors du déclenchement d’une migration. Autrement, il ne sera pas possible de se connecter à la machine virtuelle avant la fin de la mise à jour.
   - Après migration, on peut consulter les **diagnostics de démarrage** pour afficher une capture d’écran de la machine virtuelle. Si cela ne fonctionne pas, il faut vérifier que la machine virtuelle est en cours d’exécution et consulter ces [conseils de dépannage](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

5. Besoin d’aide ?

   - [En savoir plus](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm#prepare-vms-for-migration) sur la préparation des machines virtuelles pour la migration.

## <a name="step-5-replicate-the-on-premises-vms"></a>Étape 5 : Répliquer les machines virtuelles locales

Les administrateurs de Contoso peuvent exécuter une migration vers Azure, ils doivent configurer et activer la réplication.

Une fois la découverte terminée, vous pouvez commencer la réplication des machines virtuelles VMware sur Azure.

1. Dans le projet Azure Migrate > **Serveurs**, **Azure Migrate : Server Migration**, cliquez sur **Répliquer**.

    ![Répliquer des machines virtuelles](./media/contoso-migration-rehost-vm/select-replicate.png)

2. Dans **Répliquer** > **Paramètres de la source** > **Vos machines sont-elles virtualisées ?** , sélectionnez **Oui, avec VMware vSphere**.

3. Dans **Appliance locale**, sélectionnez le nom de l’appliance Azure Migrate que vous avez configurée > **OK**.

    ![Paramètres de la source](./media/contoso-migration-rehost-vm/source-settings.png)

4. Dans **Machines virtuelles**, sélectionnez les machines à répliquer.
    - Si vous avez exécuté une évaluation des machines virtuelles, vous pouvez appliquer les recommandations relatives au dimensionnement et au type de disque (Premium/Standard) des machines virtuelles qui apparaissent dans les résultats de l’évaluation. Pour ce faire, dans **Importer les paramètres de migration à partir d’une évaluation Azure Migrate ?** , sélectionnez l’option **Oui**.
    - Si vous n’avez pas exécuté d’évaluation ou que vous ne souhaitez pas utiliser les paramètres de l’évaluation, sélectionnez l’option **Non**.
    - Si vous avez choisi d’utiliser l’évaluation, sélectionnez le groupe de machines virtuelles et le nom de l’évaluation.

    ![Sélectionner l’évaluation](./media/contoso-migration-rehost-vm/select-assessment.png)

5. Dans **Machines virtuelles**, recherchez les machines virtuelles en fonction des besoins et cochez chaque machine virtuelle que vous souhaitez migrer. Cliquez ensuite sur **Suivant : Paramètres de la cible**.

6. Dans **Paramètres de la cible**, sélectionnez l’abonnement et la région cible vers laquelle vous allez migrer, puis spécifiez le groupe de ressources dans lequel les machines virtuelles Azure résideront après la migration. Dans **Réseau virtuel**, sélectionnez le réseau virtuel/sous-réseau Azure auquel les machines virtuelles Azure seront jointes après la migration.

7. Dans **Azure Hybrid Benefit**, sélectionnez ce qui suit :

    - Sélectionnez **Non** si vous ne souhaitez pas appliquer Azure Hybrid Benefit. Cliquez ensuite sur **Suivant**.
    - Sélectionnez **Oui** si vous avez des machines Windows Server couvertes par des abonnements Software Assurance ou Windows Server actifs et que vous souhaitez appliquer l’avantage aux machines que vous migrez. Cliquez ensuite sur **Suivant**.

8. Dans **Capacité de calcul**, vérifiez le nom, la taille, le type de disque du système d’exploitation et le groupe à haute disponibilité de la machine virtuelle. Les machines virtuelles doivent satisfaire aux [exigences d’Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#vmware-requirements).

    - **Taille de la machine virtuelle :** si vous utilisez les recommandations de l’évaluation, la liste déroulante Taille de la machine virtuelle contient la taille recommandée. Sinon, Azure Migrate choisit une taille qui correspond à la taille la plus proche dans l’abonnement Azure. Vous pouvez également choisir une taille manuelle dans **Taille de la machine virtuelle Azure**.
    - **Disque du système d’exploitation :** spécifiez le disque du système d’exploitation (démarrage) pour la machine virtuelle. Le disque du système d’exploitation est le disque qui contient le chargeur de démarrage et le programme d’installation du système d’exploitation.
    - **Groupe à haute disponibilité :** si la machine virtuelle doit se trouver dans un groupe à haute disponibilité Azure après la migration, spécifiez-le ici. Ce groupe doit figurer dans le groupe de ressources cible que vous spécifiez pour la migration.

9. Dans **Disques**, indiquez si les disques de machine virtuelle doivent être répliqués sur Azure, puis sélectionnez le type de disque (SSD/HDD standard ou disques managés Premium) dans Azure. Cliquez ensuite sur **Suivant**.
    - Vous pouvez exclure des disques de la réplication.
    - Si vous excluez des disques, ils ne seront pas présents sur la machine virtuelle Azure après la migration.

10. Dans **Passer en revue et démarrer la réplication**, passez en revue les paramètres, puis cliquez sur **Répliquer** pour démarrer la réplication initiale pour les serveurs.

> [!NOTE]
> Vous pouvez mettre à jour les paramètres de réplication à tout moment avant le démarrage de la réplication, dans **Gérer** > **Réplication des machines**. Vous ne pouvez pas changer les paramètres après le démarrage de la réplication.

## <a name="step-6-migrate-the-database-using-the-azure-database-migration-service"></a>Étape 6 : Migrer la base de données à l’aide d’Azure Database Migration Service

Les administrateurs de Contoso doivent créer un projet Azure Database Migration Service, puis migrer la base de données.

### <a name="create-an-azure-database-migration-service-project"></a>Créer un projet Azure Database Migration Service

1. Ils créent un projet Azure Database Migration Service. Ils sélectionnent le type de serveur source **SQL Server** et la cible **Azure SQL Database Managed Instance**.

     ![Database Migration Service - Nouveau projet de migration](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-project.png)

2. L’Assistant Migration s’ouvre.

### <a name="migrate-the-database"></a>Migrer la base de données

1. Dans l’Assistant Migration, ils spécifient la machine virtuelle source où se trouve la base de données locale. Ils entrent les informations d’identification pour accéder à la base de données.

    ![Database Migration Service - Détails de la source](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-wizard-source.png)

2. Ils sélectionnent la base de données à migrer (**SmartHotel.Registration**) :

    ![Database Migration Service - Sélectionner les bases de données sources](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-wizard-source-db.png)

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

## <a name="step-7-migrate-the-vms-with-azure-migrate-server-migration"></a>Étape 7 : Migrer les machines virtuelles avec l’outil Migration de serveur Azure Migrate

Les administrateurs Contoso effectuent une migration de test rapide et vérifient le bon fonctionnement de la machine virtuelle, puis procèdent à la migration de celle-ci.

### <a name="run-a-test-migration"></a>Exécuter un test de migration

1. Dans **Objectifs de migration** > **Serveurs** > **Azure Migrate : Server Migration**, cliquez sur **Tester les serveurs migrés**.

     ![Tester les serveurs migrés](./media/contoso-migration-rehost-linux-vm/test-migrated-servers.png)

2. Cliquez avec le bouton droit sur la machine virtuelle à tester, puis cliquez sur **Migration de test**.

    ![Migration de test](./media/contoso-migration-rehost-linux-vm/test-migrate.png)

3. Dans **Migration de test**, sélectionnez le réseau virtuel Azure dans lequel la machine virtuelle Azure se trouvera après la migration. Nous vous recommandons d’utiliser un réseau virtuel hors production.
4. Le travail **Migration de test** démarre. Supervisez le travail dans les notifications du portail.
5. Une fois la migration terminée, affichez la machine virtuelle Azure migrée dans **Machines virtuelles** dans le portail Azure. Le nom de la machine a le suffixe **-Test**.
6. Une fois le test terminé, cliquez avec le bouton droit sur la machine virtuelle Azure dans **Réplication des machines**, puis cliquez sur **Nettoyer la migration de test**.

    ![Nettoyer la migration](./media/contoso-migration-rehost-linux-vm/clean-up.png)

### <a name="migrate-the-vms"></a>Migrer les machines virtuelles

Les administrateurs de Contoso peuvent à présent opérer une migration complète pour achever le déplacement.

1. Dans le projet Azure Migrate > **Serveurs** > **Azure Migrate : Server Migration**, cliquez sur **Réplication de serveurs**.

    ![Réplication de serveurs](./media/contoso-migration-rehost-linux-vm/replicating-servers.png)

2. Dans **Réplication des machines**, cliquez avec le bouton droit sur la machine virtuelle > **Migrer**.
3. Dans **Migrer** > **Arrêter les machines virtuelles et effectuer une migration planifiée sans perte de données**, sélectionnez **Oui** > **OK**.
    - Par défaut, Azure Migrate arrête la machine virtuelle locale et exécute une réplication à la demande pour synchroniser tout changement apporté à la machine virtuelle depuis la dernière réplication. Cela permet d’éviter toute perte de données.
    - Si vous ne souhaitez pas arrêter la machine virtuelle, sélectionnez **Non**.
4. Un travail de migration démarre pour la machine virtuelle. Suivez le travail dans les notifications Azure.
5. Une fois le travail terminé, vous pouvez afficher et gérer la machine virtuelle à partir de la page **Machines virtuelles**.
6. Enfin, Contoso met à jour les enregistrements DNS pour **WEBVM** sur l’un des contrôleurs de domaine Contoso.

### <a name="update-the-connection-string"></a>Mettre à jour la chaîne de connexion

Dans la dernière étape du processus de migration, les administrateurs de Contoso mettent à jour la chaîne de connexion de l’application pour qu’elle pointe vers la base de données migrée qui s’exécute sur l’instance gérée de Contoso.

1. Dans le portail Azure, ils recherchent la chaîne de connexion en sélectionnant **Paramètres** > **Chaînes de connexion**.

    ![Chaînes de connexion](./media/contoso-migration-rehost-vm-sql-managed-instance/failover4.png)

2. Ils mettent à jour la chaîne avec le nom d’utilisateur et le mot de passe de SQL Database Managed Instance.
3. Une fois la chaîne configurée, ils remplacent la chaîne de connexion actuelle dans le fichier web.config de l’application.
4. Après avoir mis à jour et enregistré le fichier, ils redémarrent IIS sur la machine WEBVM en exécutant `iisreset /restart` dans une fenêtre d’invite de commandes.
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

- Sécuriser les données : Contoso sauvegarde les données sur les machines virtuelles à l’aide du service Sauvegarde Azure. [Plus d’informations](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=/azure/virtual-machines/linux/toc.json)
- Faire en sorte que les applications soient opérationnelles : Contoso réplique les machines virtuelles de l’application dans Azure vers une région secondaire à l’aide de Site Recovery. [Plus d’informations](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)
- Contoso sait maintenant comment gérer SQL Managed Instance, y compris les [sauvegardes de base de données](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

- Contoso dispose déjà d’une licence pour WEBVM. Pour tirer parti de la tarification avec Azure Hybrid Benefit, Contoso convertit la machine virtuelle Azure existante.
- Contoso utilise [Azure Cost Management](https://azure.microsoft.com/services/cost-management) pour s’assurer qu’ils ne dépassent pas les budgets établis par leur direction informatique.

## <a name="conclusion"></a>Conclusion

Cet article décrit comment Contoso réhéberge l’application SmartHotel360 dans Azure en migrant la machine virtuelle du frontend de l’application vers Azure avec le service Azure Migrate. Contoso migre la base de données locale vers Azure SQL Database Managed Instance à l’aide d’Azure Database Migration Service.
