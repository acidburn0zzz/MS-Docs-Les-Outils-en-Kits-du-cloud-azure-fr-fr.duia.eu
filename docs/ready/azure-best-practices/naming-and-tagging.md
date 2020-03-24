---
title: Conventions de nommage et de catégorisation recommandées
description: Découvrez des recommandations détaillées sur le nommage et la catégorisation des ressources visant spécifiquement à soutenir les efforts d’adoption du cloud d’entreprise.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/05/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: readiness, fasttrack-edit
ms.openlocfilehash: 9e60e84659828efdc9802c45cf2f91ad945c8cda
ms.sourcegitcommit: 5d7e93540a679252f1c7207e62cb2ee7213a6ae9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80069790"
---
<!-- cSpell:ignore eastus westus westeurope usgovia accountlookup messagequery -->

# <a name="recommended-naming-and-tagging-conventions"></a>Conventions de nommage et de catégorisation recommandées

Organisez vos ressources cloud pour prendre en charge les exigences en matière de gestion des opérations et de comptabilité. Le respect de conventions bien définies de nommage et d’étiquetage des métadonnées permet de localiser et de gérer rapidement les ressources. Ces conventions vous aident également à associer les coûts d’utilisation du cloud à des équipes commerciales par le biais de mécanismes comptables de récupération des données de facturation et de facturation interne.

L’article [Règles de nommage et restrictions pour les ressources Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) du Centre des architectures Azure fournit des conseils généraux sur les restrictions des plateformes. La discussion suivante étend cette aide avec des recommandations plus détaillées visant spécialement à accompagner les efforts d’adoption du cloud d’entreprise.

Le changement des noms de ressource peut être difficile. Mettez en place une convention de nommage complète avant de commencer tout déploiement important du cloud.

> [!NOTE]
> Chaque entreprise a des exigences différentes en matière d’organisation et de gestion. Ces recommandations constituent un point de départ des discussions au sein de vos équipes d’adoption du cloud.
>
> À mesure que ces discussions avancent, utilisez le modèle suivant pour capturer les décisions de nommage et de catégorisation que vous prenez lorsque vous alignez ces recommandations sur vos besoins métier spécifiques.
>
> Téléchargez le [modèle de suivi des conventions d’attribution de noms et de catégorisation](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx).

## <a name="naming-and-tagging-resources"></a>Nommage et catégorisation des ressources

Votre stratégie de nommage et de catégorisation doit inclure des détails commerciaux et opérationnels dans les noms et les balises de métadonnées des ressources :

- Le côté métier de cette stratégie garantit que les noms et les étiquettes des ressources incluent les informations organisationnelles nécessaires pour identifier les équipes. Utilisez une ressource avec les propriétaires de l’entreprise qui sont responsables des coûts des ressources.
- Le côté opérationnel garantit que les noms et les balises incluent des informations que les équipes informatiques utilisent pour identifier la charge de travail, l’application, l’environnement, le caractère critique et d’autres informations utiles pour la gestion des ressources.

## <a name="resource-naming"></a>Affectation de noms aux ressources

Une convention d’affectation de noms efficace assemble des noms de ressources en utilisant des informations importantes sur les ressources en tant que parties du nom d’une ressource. Par exemple, en utilisant les [conventions de nommage recommandées](#example-names), une ressource IP publique pour une charge de travail SharePoint de production est nommée comme suit : `pip-sharepoint-prod-westus-001`.

À partir du nom, vous pouvez rapidement identifier le type de la ressource, sa charge de travail associée, son environnement de déploiement et la région Azure qui l’héberge.

### <a name="naming-scope"></a>Étendue de l’affectation de noms

Tous les types de ressources Azure ont une étendue qui définit le niveau à partir duquel les noms de ressources doivent être uniques. Une ressource doit avoir un nom unique dans son étendue.

Par exemple, un réseau virtuel possède une étendue de groupe de ressources, ce qui signifie qu’il ne peut y avoir qu’un seul réseau portant le nom `vnet-prod-westus-001` dans un groupe de ressources donné. D’autres groupes de ressources peuvent avoir leur propre réseau virtuel nommé `vnet-prod-westus-001`. Les sous-réseaux, pour donner un autre exemple, sont étendus à des réseaux virtuels, ce qui signifie que chaque sous-réseau d’un réseau virtuel doit être nommé de façon unique.

Certains noms de ressources, tels que les services PaaS avec des points de terminaison publics ou des étiquettes DNS de machine virtuelle, ont des étendues globales, ce qui signifie qu’ils doivent être uniques sur l’ensemble de la plateforme Azure.

Les noms de ressources ont des longueurs limitées. L’équilibrage du contexte incorporé dans un nom avec sa portée et sa longueur est important lorsque vous élaborez vos conventions d’affectation de noms. Pour obtenir plus d’informations sur les règles d’affectation de noms et connaître les caractères autorisés, les étendues et les longueurs de noms pour les types de ressources, consultez [Conventions d’affectation de noms pour les ressources Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming).

### <a name="recommended-naming-components"></a>Composants de noms recommandés

Lorsque vous construisez votre convention d’affectation de noms, identifiez les informations clés que vous souhaitez refléter dans un nom de ressource. Des informations différentes s’appliquent à différents types de ressources. La liste suivante fournit des exemples d’informations utiles lorsque vous construisez des noms de ressources.

Veillez à ce que la longueur des composants de noms soit courte pour éviter de dépasser les limites de longueur de nom des ressources.

| Composant de noms            | Description                                                                                                                                                                                                      | Exemples                                         |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| Unité commerciale               | Division de niveau supérieur de votre entreprise qui est propriétaire de l’abonnement ou de la charge de travail auxquels la ressource appartient. Dans les organisations plus petites, ce composant peut représenter un seul élément organisationnel de haut niveau. | _fin_, _mktg_, _product_, _it_, _corp_           |
| Type d’abonnement           | Description résumée de l’objectif de l’abonnement qui contient la ressource. Souvent ventilée par type d’environnement de déploiement ou charges de travail spécifiques.                                                       | _prod_, _shared_, _client_                       |
| Nom d’application ou de service | Nom de l’application, de la charge de travail ou du service dont la ressource fait partie.                                                                                                                                    | _navigator_, _emissions_, _sharepoint_, _hadoop_ |
| Environnement de déploiement      | Étape du cycle de vie de développement pour la charge de travail prise en charge par la ressource.                                                                                                                              | _prod_, _dev_, _qa_, _stage_, _test_             |
| Région                      | Région Azure dans laquelle les ressources sont déployées.                                                                                                                                                                 | _westus_, _eastus2_, _westeurope_, _usgovia_     |

### <a name="recommended-resource-type-prefixes"></a>Préfixes de type de ressource recommandés

Chaque charge de travail peut être composée de plusieurs ressources et services individuels. L’incorporation de préfixes de type de ressource dans vos noms de ressources facilite l’identification visuelle des composants de l’application ou du service.

La liste suivante répertorie les préfixes de type de ressource Azure recommandés à utiliser lorsque vous définissez vos conventions d’affectation de noms.

<!-- cSpell:disable -->

### <a name="general"></a>Général

| Type de ressource                      | Préfixe de nom |
|---------------------------------|-------------|
| Resource group                  | rg-         |
| Définition de stratégie               | policy-     |
| Instance du service de gestion des API | apim-       |

### <a name="networking"></a>Mise en réseau

| Type de ressource                       | Préfixe de nom |
|----------------------------------|-------------|
| Réseau virtuel                  | vnet-       |
| Subnet                           | snet-       |
| Interfaces réseau          | nic-        |
| Adresse IP publique                | pip-        |
| Équilibreur de charge (interne)         | lbi-        |
| Équilibreur de charge (externe)         | lbe-        |
| Groupe de sécurité réseau     | nsg-        |
| Groupe de sécurité d’application (ASG) | asg-        |
| Passerelle de réseau local            | lgw-        |
| Passerelle de réseau virtuel          | vgw-        |
| Connexion VPN                   | cn-         |
| passerelle d’application              | agw-        |
| Table de routage                      | route-      |
| Profil Traffic Manager          | traf-       |

### <a name="compute-and-web"></a>Calcul et web

| Type de ressource                  | Préfixe de nom |
|-----------------------------|-------------|
| Machine virtuelle             | vm          |
| Jeu de mise à l’échelle de machine virtuelle   | vmss-       |
| Groupe à haute disponibilité            | avail-      |
| Compte de stockage de machine virtuelle          | stvm        |
| Ordinateur connecté à Azure Arc | arcm-       |
| Instance de conteneur          | aci-        |
| Cluster AKS                 | aks-        |
| Cluster Service Fabric      | sf-         |
| Environnement App Service     | ase-        |
| Plan App Service            | plan-       |
| Application web                     | app-        |
| Conteneur de fonctions                | func-       |
| service cloud               | cld-        |
| Notification Hubs           | ntf-        |
| Espace de noms Notification Hubs | ntfns-      |

### <a name="databases"></a>Bases de données

| Type de ressource                     | Préfixe de nom |
|--------------------------------|-------------|
| Serveur Azure SQL Database      | sql-        |
| Base de données Azure SQL             | sqldb-      |
| Base de données Cosmos DB             | cosmos-     |
| Instance Azure Cache pour Redis | redis-      |
| Base de données MySQL                 | mysql-      |
| Base de données PostgreSQL            | psql-       |
| Azure SQL Data Warehouse.       | sqldw-      |
| Azure Synapse Analytics        | syn-        |
| SQL Server Stretch Database    | sqlstrdb-   |

### <a name="storage"></a>Stockage

| Type de ressource       | Préfixe de nom |
|------------------|-------------|
| Compte de stockage  | st          |
| Azure StorSimple | ssimp       |

### <a name="ai--machine-learning"></a>IA + Machine Learning

| Type de ressource                       | Préfixe de nom |
|----------------------------------|-------------|
| Recherche cognitive Azure           | srch-       |
| Azure Cognitive Services         | cog-        |
| Espace de travail Azure Machine Learning | mlw-        |

### <a name="analytics-and-iot"></a>Analytique et IoT

| Type de ressource                      | Préfixe de nom |
|---------------------------------|-------------|
| Serveur Azure Analysis Services  | as-         |
| Espace de travail Azure Databricks      | dbw-        |
| Azure Stream Analytics          | asa-        |
| Azure Data Factory              | adf-        |
| Compte Data Lake Store         | dls         |
| Compte Data Lake Analytics     | dla         |
| Event Hub                       | evh-        |
| Cluster HDInsight - Hadoop      | hadoop-     |
| Cluster HDInsight - HBase       | hbase-      |
| Cluster HDInsight - Kafka       | kafka-      |
| Cluster HDInsight - Spark       | spark-      |
| Cluster HDInsight - Storm       | storm-      |
| Cluster HDInsight - ML Services | mls-        |
| hub IOT                         | iot-        |
| Power BI Embedded               | pbi-        |

### <a name="integration"></a>Intégration

| Type de ressource        | Préfixe de nom |
|-------------------|-------------|
| Logic Apps        | logic-      |
| Service Bus       | sb-         |
| File d’attente Service Bus | sbq-        |
| Rubrique Service Bus | sbt-        |

### <a name="management-and-governance"></a>Gestion et gouvernance

| Type de ressource              | Préfixe de nom |
|-------------------------|-------------|
| Blueprint               | bp-         |
| Coffre de clés               | kv-         |
| Espace de travail Log Analytics | log-        |
| Application Insights    | appi-       |
| Coffre Recovery Services | rsv-        |

### <a name="migration"></a>Migration

| Type de ressource                          | Préfixe de nom |
|-------------------------------------|-------------|
| Projet Azure Migrate               | migr-       |
| Instance Database Migration Service | dms-        |
| Coffre Recovery Services             | rsv-        |

<!-- cSpell:enable -->

## <a name="metadata-tags"></a>Balises de métadonnées

Lorsque vous appliquez des balises de métadonnées à vos ressources cloud, vous pouvez inclure des informations relatives à ces ressources qui n’ont pas pu être incluses dans le nom de la ressource. Vous pouvez utiliser ces informations pour filtrer les ressources et créer des rapports sur ces dernières de manière plus sophistiquée. Vous souhaitez que ces balises incluent le contexte de la charge de travail ou de l’application associée à la ressource, les exigences opérationnelles et les informations de propriété. Ces informations peuvent être utilisées par des équipes informatiques ou commerciales pour rechercher des ressources ou générer des rapports sur l’utilisation des ressources et la facturation.

Les balises que vous appliquez aux ressources et celles qui sont requises ou facultatives diffèrent entre les organisations. La liste suivante fournit des exemples de balises courantes qui capturent des informations et du contexte importants au sujet d’une ressource. Utilisez cette liste comme point de départ pour établir vos propres conventions de catégorisation.

| Nom de la balise                  | Description                                                                                                                                                                                                          | Clé               | Valeur d'exemple                                              |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|------------------------------------------------------------|
| Nom de l'application          | Nom de l’application, du service ou de la charge de travail auxquels la ressource est associée.                                                                                                                                       | _ApplicationName_ | _{app name}_                                               |
| Nom de l’approbateur             | Personne responsable de l’approbation des coûts liés à cette ressource.                                                                                                                                                     | _Approver_        | _{email}_                                                  |
| Budget requis/approuvé  | Argent alloué à cette application, à ce service ou à cette charge de travail.                                                                                                                                                          | _BudgetAmount_    | _{\$}_                                                     |
| Unité commerciale             | Division de niveau supérieur de votre entreprise qui est propriétaire de l’abonnement ou de la charge de travail auxquels la ressource appartient. Dans les organisations plus petites, cette balise peut représenter un élément organisationnel unique ou partagé de haut niveau. | _BusinessUnit_    | _FINANCE_, _MARKETING_, _{Nom du produit}_ , _CORP_, _SHARED_ |
| Centre de coûts               | Centre de coût comptable associé à cette ressource.                                                                                                                                                                | _CostCenter_      | _{number}_                                                 |
| Récupération d'urgence         | Caractère critique pour l’entreprise de l’application, de la charge de travail ou du service.                                                                                                                                                       | _DR_              | _Mission-critical_, _Critical_, _Essential_                |
| Date de fin du projet   | Date à laquelle la mise hors service de l’application, de la charge de travail ou du service est planifiée.                                                                                                                                         | _EndDate_         | _{date}_                                                   |
| Environnement               | Environnement de déploiement de l’application, de la charge de travail ou du service.                                                                                                                                                     | _Env_             | _Prod_, _Dev_, _QA_, _Stage_, _Test_                       |
| Nom du propriétaire                | Propriétaire de l’application, de la charge de travail ou du service.                                                                                                                                                                      | _Propriétaire_           | _{email}_                                                  |
| Nom du demandeur            | Utilisateur qui a demandé la création de cette application.                                                                                                                                                                 | _Requestor_       | _{email}_                                                  |
| Classe du service             | Niveau du contrat de niveau de service de l’application, de la charge de travail ou du service.                                                                                                                                              | _ServiceClass_    | _Dev_, _Bronze_, _Silver_, _Gold_                          |
| Date de début du projet | Date à laquelle l’application, la charge de travail ou le service ont été déployés pour la première fois.                                                                                                                                                  | _StartDate_       | _{date}_                                                   |

## <a name="example-names"></a>Exemples de noms

La section suivante fournit des exemples de noms pour les types de ressources Azure courants dans un déploiement de cloud d’entreprise.

<!-- cSpell:disable -->

<!-- markdownlint-disable MD024 MD033 -->

### <a name="example-names-general"></a>Exemples de noms : Général

| Type de ressource                      | Étendue                              | Format                                                      | Exemples                                                                                                                |
|---------------------------------|------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| Abonnement                    | Compte/ <br/>Contrat Entreprise | \<Unité commerciale\>-\<Type d’abonnement\>-\<\#\#\#\>          | <ul><li>mktg-prod-001 </li><li>corp-shared-001 </li><li>fin-client-001</li></ul>                                        |
| Resource group                  | Abonnement                       | rg-\<Nom de l’application ou du service\>-\<Type d’abonnement\>-\<\#\#\#\> | <ul><li>rg-mktgsharepoint-prod-001 </li><li>rg-acctlookupsvc-share-001 </li><li>rg-ad-dir-services-shared-001</li></ul> |
| Instance du service de gestion des API | Global                             | apim-\<Nom de l’application ou du service\>                                | apim-navigator-prod                                                                                                     |

### <a name="example-names-networking"></a>Exemples de noms : Mise en réseau

| Type de ressource                   | Étendue           | Format                                                               | Exemples                                                                                                                      |
|------------------------------|-----------------|----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Réseau virtuel              | Resource group  | vnet-\<Type d’abonnement\>-\<Région\>-\<\#\#\#\>                     | <ul><li>vnet-shared-eastus2-001 </li><li>vnet-prod-westus-001 </li><li>vnet-client-eastus2-001</li></ul>                      |
| Subnet                       | Réseau virtuel | snet-\<abonnement\>-\<sous-région\>-\<\#\#\#\>                       | <ul><li>snet-shared-eastus2-001 </li><li>snet-prod-westus-001 </li><li>snet-client-eastus2-001</li></ul>                      |
| Interfaces réseau      | Resource group  | nic-\<\#\#\>-\<nom de la machine virtuelle\>-\<abonnement\>\<\#\#\#\>                   | <ul><li>nic-01-dc1-shared-001 </li><li>nic-02-vmhadoop1-prod-001 </li><li>nic-02-vmtest1-client-001</li></ul>                 |
| Adresse IP publique            | Resource group  | pip-\<nom de la machine virtuelle ou de l’application\>-\<Environnement\>-\<sous-région\>-\<\#\#\#\> | <ul><li>pip-dc1-shared-eastus2-001 </li><li>pip-hadoop-prod-westus-001</li></ul>                                              |
| Équilibrage de charge                | Resource group  | lb-\<nom de l’application ou rôle\>\<Environnement\>\<\#\#\#\>                     | <ul><li>lb-navigator-prod-001 </li><li>lb-sharepoint-dev-001</li></ul>                                                        |
| Groupe de sécurité réseau | Sous-réseau ou carte réseau   | nsg-\<Nom de la stratégie ou de l’application\>-\<\#\#\#\>                           | <ul><li>nsg-weballow-001 </li><li>nsg-rdpallow-001 </li><li>nsg-sqlallow-001 </li><li>nsg-dnsbloked-001</li></ul>             |
| Passerelle de réseau local        | Passerelle virtuelle | lgw-\<Type d’abonnement\>-\<Région\>-\<\#\#\#\>                      | <ul><li>lgw-shared-eastus2-001 </li><li>lgw-prod-westus-001 </li><li>lgw-client-eastus2-001</li></ul>                         |
| Passerelle de réseau virtuel      | Réseau virtuel | vgw-\<Type d’abonnement\>-\<Région\>-\<\#\#\#\>                      | <ul><li>vgw-shared-eastus2-001 </li><li>vgw-prod-westus-001 </li><li>vgw-client-eastus2-001</li></ul>                         |
| Connexion de site à site      | Resource group  | cn-\<nom de la passerelle locale\>-to-\<nom de la passerelle virtuelle\>                | <ul><li>cn-lgw-shared-eastus2-001-to-vgw-shared-eastus2-001 </li><li>cn-lgw-shared-eastus2-001-to-shared-westus-001</li></ul> |
| Connexion VPN               | Resource group  | cn-\<abonnment1\>\<région1\>-to-\<abonnement2\>\<région2\>-     | <ul><li>cn-shared-eastus2-to-shared-westus </li><li>cn-prod-eastus2-to-prod-westus</li></ul>                                  |
| Table de routage                  | Resource group  | route-\<Nom de la table de routage\>                                           | <ul><li>lb-navigator-prod-001 </li><li>lb-sharepoint-dev-001</li></ul>                                                        |
| Étiquette DNS                    | Global          | \<Un enregistrement de machine virtuelle\>.[\<région\>.cloudapp.azure.com]                   | <ul><li>dc1.westus.cloudapp.azure.com </li><li>web1.eastus2.cloudapp.azure.com</li></ul>                                      |

### <a name="example-names-compute-and-web"></a>Exemples de noms : Calcul et web

| Type de ressource                  | Étendue          | Format                                                              | Exemples                                                                                                                          |
|-----------------------------|----------------|---------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Machine virtuelle             | Resource group | vm\<nom de la stratégie ou de l’application\>\<\#\#\#\>                              | <ul><li>vmnavigator001 </li><li>vmsharepoint001 </li><li>vmsqlnode001 </li><li>vmhadoop001</li></ul>                              |
| Compte de stockage de machine virtuelle          | Global         | stvm\<type de niveau de performance\>\<nom de l’application ou du produit\>\<région\>\<\#\#\#\> | <ul><li>stvmstcoreeastus2001 </li><li>stvmpmcoreeastus2001 </li><li>stvmstplmeastus2001 </li><li>stvmsthadoopeastus2001</li></ul> |
| Application web                     | Global         | app-\<Nom de l’application\>-\<Environnement\>-\<\#\#\#\>.[{azurewebsites.net}]   | <ul><li>app-navigator-prod-001.azurewebsites.net </li><li>app-accountlookup-dev-001.azurewebsites.net</li></ul>                   |
| Conteneur de fonctions                | Global         | func-\<Nom de l’application\>-\<Environnement\>-\<\#\#\#\>.[{azurewebsites.net}]  | <ul><li>func-navigator-prod-001.azurewebsites.net </li><li>func-accountlookup-dev-001.azurewebsites.net</li></ul>                 |
| service cloud               | Global         | cld-\<Nom de l’application\>-\<Environnement\>-\<\#\#\#\>.[{cloudapp.net}]        | <ul><li>cld-navigator-prod-001.azurewebsites.net </li><li>cld-accountlookup-dev-001.azurewebsites.net</li></ul>                   |
| Hub de notification            | Resource group | ntf-\<Nom de l’application\>-\<Environnement\>                                    | <ul><li>ntf-navigator-prod </li><li>ntf-emissions-dev</li></ul>                                                                   |
| Espace de noms Notification Hubs | Global         | ntfns-\<Nom de l’application\>-\<Environnement\>                                  | <ul><li>ntfns-navigator-prod </li><li>ntfns-emissions-dev</li></ul>                                                               |

### <a name="example-names-databases"></a>Exemples de noms : Bases de données

| Type de ressource                     | Étendue              | Format                                 | Exemples                                                                  |
|--------------------------------|--------------------|----------------------------------------|---------------------------------------------------------------------------|
| Serveur Azure SQL Database      | Global             | sql-\<Nom de l’application\>-\<Environnement\>       | <ul><li>sql-navigator-prod </li><li>sql-emissions-dev</li></ul>           |
| Base de données Azure SQL             | Azure SQL Database | sqldb-\<Nom de la base de données>-\<Environnement\> | <ul><li>sqldb-users-prod </li><li>sqldb-users-dev</li></ul>               |
| Base de données Cosmos DB             | Global             | cosmos-\<Nom de l’application\>-\<Environnement\>    | <ul><li>cosmos-navigator-prod </li><li>cosmos-emissions-dev</li></ul>     |
| Instance Azure Cache pour Redis | Global             | redis-\<Nom de l’application\>-\<Environnement\>     | <ul><li>redis-navigator-prod </li><li>redis-emissions-dev</li></ul>       |
| Base de données MySQL                 | Global             | mysql-\<Nom de l’application\>-\<Environnement\>     | <ul><li>mysql-navigator-prod </li><li>mysql-emissions-dev</li></ul>       |
| Base de données PostgreSQL            | Global             | psql-\<Nom de l’application\>-\<Environnement\>      | <ul><li>psql-navigator-prod </li><li>psql-emissions-dev</li></ul>         |
| Azure SQL Data Warehouse.       | Global             | sqldw-\<Nom de l’application\>-\<Environnement\>     | <ul><li>sqldw-navigator-prod </li><li>sqldw-emissions-dev</li></ul>       |
| SQL Server Stretch Database    | Azure SQL Database | sqlstrdb-\<Nom de l’application\>-\<Environnement\>  | <ul><li>sqlstrdb-navigator-prod </li><li>sqlstrdb-emissions-dev</li></ul> |

### <a name="example-names-storage"></a>Exemples de noms : Stockage

| Type de ressource                        | Étendue  | Format                                                                        | Exemples                                                              |
|-----------------------------------|--------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| Compte de stockage (utilisation générale)     | Global | st\<nom de stockage\>\<\#\#\#\>                                                  | <ul><li>stnavigatordata001 </li><li>stemissionsoutput001</li></ul>    |
| Compte de stockage (journaux de diagnostic) | Global | stdiag\<les 2 premières lettres du nom de l’abonnement et numéro\>\<région\>\<\#\#\#\> | <ul><li>stdiagsh001eastus2001 </li><li>stdiagsh001westus001</li></ul> |
| Azure StorSimple                  | Global | ssimp\<Nom de l’application\>\<Environnement\>                                              | <ul><li>ssimpnavigatorprod </li><li>ssimpemissionsdev</li></ul>       |

### <a name="example-names-ai--machine-learning"></a>Exemples de noms : IA + Machine Learning

| Type de ressource                       | Étendue          | Format                            | Exemples                                                          |
|----------------------------------|----------------|-----------------------------------|-------------------------------------------------------------------|
| Recherche cognitive Azure           | Global         | srch-\<Nom de l’application\>-\<Environnement\> | <ul><li>srch-navigator-prod </li><li>srch-emissions-dev</li></ul> |
| Azure Cognitive Services         | Resource group | cog-\<Nom de l’application\>-\<Environnement\>  | <ul><li>cog-navigator-prod </li><li>cog-emissions-dev</li></ul>   |
| Espace de travail Azure Machine Learning | Resource group | mlw-\<Nom de l’application\>-\<Environnement\>  | <ul><li>mlw-navigator-prod </li><li>mlw-emissions-dev</li></ul>   |

### <a name="example-names-analytics-and-iot"></a>Exemples de noms : Analytique et IoT

| Type de ressource                  | Étendue          | Format                              | Exemples                                                              |
|-----------------------------|----------------|-------------------------------------|-----------------------------------------------------------------------|
| Azure Data Factory          | Global         | adf-\<Nom de l’application\>\<Environnement\>     | <ul><li>adf-navigator-prod </li><li>adf-emissions-dev</li></ul>       |
| Azure Stream Analytics      | Resource group | asa-\<Nom de l’application\>-\<Environnement\>    | <ul><li>asa-navigator-prod </li><li>asa-emissions-dev</li></ul>       |
| Compte Data Lake Analytics | Global         | dla\<Nom de l’application\>\<Environnement\>      | <ul><li>dlanavigatorprod </li><li>dlaemissionsdev</li></ul>           |
| Compte Data Lake Storage   | Global         | dls-\<Nom de l’application\>\<Environnement\>      | <ul><li>dlsnavigatorprod </li><li>dlsemissionsdev</li></ul>           |
| Event Hub                   | Global         | evh-\<Nom de l’application\>-\<Environnement\>    | <ul><li>evh-navigator-prod </li><li>evh-emissions-dev</li></ul>       |
| Cluster HDInsight - HBase   | Global         | hbase-\<Nom de l’application\>-\<Environnement\>  | <ul><li>hbase-navigator-prod </li><li>hbase-emissions-dev</li></ul>   |
| Cluster HDInsight - Hadoop  | Global         | hadoop-\<Nom de l’application\>-\<Environnement\> | <ul><li>hadoop-navigator-prod </li><li>hadoop-emissions-dev</li></ul> |
| Cluster HDInsight - Spark   | Global         | spark-\<Nom de l’application\>-\<Environnement\>  | <ul><li>spark-navigator-prod </li><li>spark-emissions-dev </li></ul>  |
| hub IOT                     | Global         | iot-\<Nom de l’application\>-\<Environnement\>    | <ul><li>iot-navigator-prod </li><li>iot-emissions-dev</li></ul>       |
| Power BI Embedded           | Global         | pbi-\<Nom de l’application\>\<Environnement\>     | <ul><li>pbi-navigator-prod </li><li>pbi-emissions-dev</li></ul>       |

### <a name="example-names-integration"></a>Exemples de noms : Intégration

| Type de ressource        | Étendue       | Format                                                     | Exemples                                                      |
|-------------------|-------------|------------------------------------------------------------|---------------------------------------------------------------|
| Service Bus       | Global      | sb-\<Nom de l’application\>-\<Environnement\>.[{servicebus.windows.net}] | <ul><li>sb-navigator-prod </li><li>sb-emissions-dev</li></ul> |
| File d’attente Service Bus | Service Bus | sbq-\<descripteur de requête\>                                   | <ul><li>sbq-messagequery</li></ul>                            |
| Rubrique Service Bus | Service Bus | sbt-\<descripteur de requête\>                                   | <ul><li>sbt-messagequery</li></ul>                            |
