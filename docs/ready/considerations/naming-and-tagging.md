---
title: 'Prêt : Conventions de nommage et de catégorisation recommandées'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Cet article fournit des recommandations détaillées sur le nommage et la catégorisation des ressources visant spécifiquement à soutenir les efforts d’adoption du cloud d’entreprise.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: readiness
ms.openlocfilehash: 003e212326959b593071f8230d2ddc0dba646909
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72378277"
---
# <a name="ready-recommended-naming-and-tagging-conventions"></a>Prêt : Conventions de nommage et de catégorisation recommandées

L’organisation des ressources informatiques de manière à aider à la gestion opérationnelle et à prendre en charge les exigences comptables est un défi courant qui concerne les efforts importants en matière d’adoption du cloud. En appliquant des conventions bien définies de nommage et de catégorisation de métadonnées aux ressources hébergées dans le cloud, le personnel informatique peut rapidement trouver et gérer les ressources. Des noms et des balises bien définis aident également à aligner les coûts d’utilisation du cloud sur les équipes commerciales à l’aide des mécanismes comptables de récupération des données de facturation et de facturation interne.

L’article [Règles de nommage et restrictions pour les ressources Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) du Centre des architectures Azure fournit des recommandations générales sur les conventions de nommage et les discussions relatives aux restrictions de nommage et aux règles des plateformes. La discussion suivante étend cette aide générique avec des recommandations plus détaillées visant spécifiquement à prendre en charge les efforts d’adoption du cloud d’entreprise.

Les noms de ressources peuvent être difficiles à modifier. Faites en sorte que vos équipes d’adoption du cloud établissent une convention d’affectation de noms complète avant de commencer un déploiement important du cloud.

> [!NOTE]
> Chaque entreprise a des exigences différentes en matière d’organisation et de gestion. Les recommandations présentées dans cet article constituent un point de départ pour des discussions au sein de vos équipes d’adoption du cloud.
>
> À mesure que ces discussions progressent, utilisez le modèle suivant pour capturer les décisions d’attribution de noms et de catégorisation que vous prenez lorsque vous alignez ces recommandations en fonction de vos besoins professionnels spécifiques.
>
> Téléchargez le [modèle de suivi des conventions d’attribution de noms et de catégorisation](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx).

## <a name="naming-and-tagging-resources"></a>Nommage et catégorisation des ressources

Votre stratégie de nommage et de catégorisation doit inclure des détails commerciaux et opérationnels dans les noms et les balises de métadonnées des ressources :

- Le côté commercial de cette stratégie garantit que les noms et balises des ressources incluent les informations organisationnelles nécessaires pour identifier les équipes. Utilisez une ressource avec les propriétaires de l’entreprise qui sont responsables des coûts des ressources.
- Le côté opérationnel garantit que les noms et les balises incluent des informations que les équipes informatiques utilisent pour identifier la charge de travail, l’application, l’environnement, le caractère critique et d’autres informations utiles pour la gestion des ressources.

### <a name="resource-naming"></a>Affectation de noms aux ressources

Une convention d’affectation de noms efficace assemble des noms de ressources en utilisant des informations importantes sur les ressources en tant que parties du nom d’une ressource. Par exemple, à l’aide des conventions d’affectation de noms recommandées décrites [plus loin dans cet article](#sample-naming-convention), une ressource IP publique pour une charge de travail SharePoint de production est nommée comme suit : `pip-sharepoint-prod-westus-001`.

À partir du nom, vous pouvez rapidement identifier le type de la ressource, sa charge de travail associée, son environnement de déploiement et la région Azure qui l’héberge.

#### <a name="naming-scope"></a>Étendue de l’affectation de noms

Tous les types de ressources Azure ont une étendue qui définit la façon dont ces ressources peuvent être managées par rapport à d’autres types de ressources. En termes de conventions d’affectation de noms, cela signifie qu’une ressource doit avoir un nom unique dans son étendue.

Par exemple, un réseau virtuel possède une étendue de groupe de ressources, ce qui signifie qu’il ne peut y avoir qu’un seul réseau portant le nom `vnet-prod-westus-001` dans un groupe de ressources donné. D’autres groupes de ressources peuvent avoir leur propre réseau virtuel nommé `vnet-prod-westus-001`. Les sous-réseaux, pour donner un autre exemple, sont étendus à des réseaux virtuels, ce qui signifie que chaque sous-réseau d’un réseau virtuel doit être nommé de façon unique.

Certains noms de ressources, tels que les services PaaS avec des points de terminaison publics ou des étiquettes DNS de machine virtuelle, ont des étendues globales, ce qui signifie qu’ils doivent être uniques sur l’ensemble de la plateforme Azure.

Les noms de ressources ont des longueurs limitées. L’équilibrage du contexte incorporé dans un nom avec sa portée et sa longueur est important lorsque vous élaborez vos conventions d’affectation de noms. Pour obtenir plus d’informations sur les règles d’affectation de noms et connaître les caractères autorisés, les étendues et les longueurs de noms pour les types de ressources, consultez [Conventions d’affectation de noms pour les ressources Azure](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions).

#### <a name="recommended-naming-components"></a>Composants de noms recommandés

Lorsque vous construisez votre convention d’affectation de noms, identifiez les informations clés que vous souhaitez refléter dans un nom de ressource. Des informations différentes s’appliquent à différents types de ressources. La liste suivante fournit des exemples d’informations utiles lorsque vous construisez des noms de ressources.

Veillez à ce que la longueur des composants de noms soit courte pour éviter de dépasser les limites de longueur de nom des ressources.

| Composant de noms | Description | Exemples |
| --- | --- | --- |
| Unité commerciale | Division de niveau supérieur de votre entreprise qui est propriétaire de l’abonnement ou de la charge de travail auxquels la ressource appartient. Dans les organisations plus petites, ce composant peut représenter un seul élément organisationnel de haut niveau. | *fin*, *mktg*, *product*, *it*, *corp* |
| Type d’abonnement | Description résumée de l’objectif de l’abonnement qui contient la ressource. Souvent ventilée par type d’environnement de déploiement ou charges de travail spécifiques. | *prod,* s*hared, client* |
| Nom d’application ou de service | Nom de l’application, de la charge de travail ou du service dont la ressource fait partie. | *navigator*, *emissions*, *sharepoint*, *hadoop* |
| Environnement de déploiement | Étape du cycle de vie de développement pour la charge de travail prise en charge par la ressource. | *prod, dev, qa, stage, test* |
| Région | Région Azure dans laquelle les ressources sont déployées. | *westus, eastus2, westeurope, usgovia* |

#### <a name="recommended-resource-type-prefixes"></a>Préfixes de type de ressource recommandés

Chaque charge de travail peut être composée de plusieurs ressources et services individuels. L’incorporation de préfixes de type de ressource dans vos noms de ressources facilite l’identification visuelle des composants de l’application ou du service.

La liste suivante répertorie les préfixes de type de ressource Azure recommandés à utiliser lorsque vous définissez vos conventions d’affectation de noms.

| Type de ressource                       | Préfixe de nom de ressource |
| ----------------------------------- | -------------------- |
| Resource group                      | rg-                  |
| Réseau virtuel Azure                     | vnet-                |
| Passerelle de réseau virtuel             | vnet-gw-             |
| Connexion à la passerelle                  | cn-                  |
| Subnet                              | snet-                |
| Groupe de sécurité réseau              | nsg-                 |
| Machines virtuelles Azure                    | vm-                  |
| Compte de stockage de machine virtuelle                  | stvm                 |
| Adresse IP publique                           | pip-                 |
| Azure Load Balancer                       | lb-                  |
| Carte d’interface réseau                                 | nic-                 |
| Azure Service Bus                         | sb-                  |
| Files d’attente Azure Service Bus                  | sbq-                 |
| Applications Azure App Service                    | azapp-               |
| Applications Azure Functions                       | azfun-               |
| Services cloud Azure                      | azcs-                |
| Azure SQL Database                  | sqldb-               |
| Azure Cosmos DB (anciennement Azure DocumentDB) | cosdb-               |
| Cache Azure pour Redis               | redis-               |
| Azure Database pour MySQL            | mysql-               |
| Azure SQL Data Warehouse                  | sqldw-               |
| SQL Server Stretch Database         | sqlstrdb-            |
| Stockage Azure                       | stor                 |
| Azure StorSimple                          | ssimp                |
| Recherche Azure                        | srch-                |
| Azure Cognitive Services                  | cs-                  |
| Espace de travail Azure Machine Learning    | aml-                 |
| Azure Data Lake Storage             | dls                  |
| Service Analytique Azure Data Lake           | dla                  |
| Azure HDInsight – Spark                   | hdis-                |
| Azure HDInsight – Hadoop                  | hdihd-               |
| Azure HDInsight – R Server                | hdir-                |
| Azure HDInsight – HBase                   | hdihb-               |
| Power BI Embedded                   | pbiemb               |
| Azure Stream Analytics                    | asa-                 |
| Azure Data Factory                        | df-                  |
| Hubs d'événements Azure                           | evh-                 |
| Azure IoT Hub                       | aih-                 |
| Azure Notification Hubs                   | anh-                 |
| Espace de noms d’Azure Notification Hubs          | anhns-               |

### <a name="metadata-tags"></a>Balises de métadonnées

Lorsque vous appliquez des balises de métadonnées à vos ressources cloud, vous pouvez inclure des informations relatives à ces ressources qui n’ont pas pu être incluses dans le nom de la ressource. Vous pouvez utiliser ces informations pour filtrer les ressources et créer des rapports sur ces dernières de manière plus sophistiquée. Vous souhaitez que ces balises incluent le contexte de la charge de travail ou de l’application associée à la ressource, les exigences opérationnelles et les informations de propriété. Ces informations peuvent être utilisées par des équipes informatiques ou commerciales pour rechercher des ressources ou générer des rapports sur l’utilisation des ressources et la facturation.

Les balises que vous appliquez aux ressources et celles qui sont requises ou facultatives diffèrent entre les organisations. La liste suivante fournit des exemples de balises courantes qui capturent des informations et du contexte importants au sujet d’une ressource. Utilisez cette liste comme point de départ pour établir vos propres conventions de catégorisation.

| Nom de la balise                  | Description                                                                                                                                                                                                    | Clé               | Exemple de valeur                                   |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------|
| Nom de l’application          | Nom de l’application, du service ou de la charge de travail auxquels la ressource est associée.                                                                                                                                 | *ApplicationName* | *{app name}*                                    |
| Nom de l’approbateur             | Personne responsable de l’approbation des coûts liés à cette ressource.                                                                                                                                               | *Approver*        | *{email}*                                       |
| Budget requis/approuvé  | Argent alloué à cette application, à ce service ou à cette charge de travail.                                                                                                                                                    | *BudgetAmount*    | *{\$}*                                          |
| Unité commerciale             | Division de niveau supérieur de votre entreprise qui est propriétaire de l’abonnement ou de la charge de travail auxquels la ressource appartient. Dans les organisations plus petites, cette balise peut représenter un élément organisationnel unique ou partagé de haut niveau. | *BusinessUnit*    | *FINANCE, MARKETING, {Product Name}, CORP, SHARED* |
| Centre de coûts               | Centre de coût comptable associé à cette ressource.                                                                                                                                                          | *CostCenter*      | *{number}*                                      |
| Récupération d'urgence         | Caractère critique pour l’entreprise de l’application, de la charge de travail ou du service.                                                                                                                                                | *DR*              | *Mission-critical, Critical, Essential*         |
| Date de fin du projet   | Date à laquelle la mise hors service de l’application, de la charge de travail ou du service est planifiée.                                                                                                                                  | *EndDate*         | *{date}*                                        |
| Environnement               | Environnement de déploiement de l’application, de la charge de travail ou du service.                                                                                                                                              | *Env*             | *Prod, Dev, QA, Stage, Test*                    |
| Nom du propriétaire                | Propriétaire de l’application, de la charge de travail ou du service.                                                                                                                                                                | *Propriétaire*           | *{email}*                                       |
| Nom du demandeur            | Utilisateur qui a demandé la création de cette application.                                                                                                                                                          | *Requestor*       | *{email}*                                       |
| Classe du service             | Niveau du contrat de niveau de service de l’application, de la charge de travail ou du service.                                                                                                                                       | *ServiceClass*    | *Dev, Bronze, Silver, Gold*                     |
| Date de début du projet | Date à laquelle l’application, la charge de travail ou le service ont été déployés pour la première fois.                                                                                                                                           | *StartDate*       | *{date}*                                        |

## <a name="sample-naming-convention"></a>Exemple de convention d’affectation de noms

La section suivante fournit des exemples de modèles d’affectation de noms pour les types de ressources Azure courants qui sont déployés au cours d’un déploiement de cloud d’entreprise.

<!-- markdownlint-disable MD033 -->

### <a name="subscriptions"></a>Abonnements

| Type de ressource   | Étendue                        | Format                                             | Exemples                                     |
|--------------|------------------------------|----------------------------------------------------|----------------------------------------------|
| Subscription | Compte/contrat Entreprise | \<Unité commerciale\>-\<Type d’abonnement\>-\<\#\#\#\> | <ul><li>mktg-prod-001 </li><li>corp-shared-001 </li><li>fin-client-001</li></ul> |

### <a name="resource-groups"></a>Groupes de ressources

| Type de ressource     | Étendue        | Format                                                     | Exemples                                                                            |
|----------------|--------------|------------------------------------------------------------|-------------------------------------------------------------------------------------|
| Resource group | Subscription | rg-\<Nom de l’application/du service\>-\<Type d’abonnement\>-\<\#\#\#\> | <ul><li>rg-mktgsharepoint-prod-001 </li><li>rg-acctlookupsvc-share-001 </li><li>rg-ad-dir-services-shared-001</li></ul> |

### <a name="virtual-networking"></a>Réseau virtuel

| Type de ressource               | Étendue           | Format                                                                | Exemples                                                                                              |
|--------------------------|-----------------|-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Réseau virtuel Azure          | Resource group  | vnet-\<Type d’abonnement\>-\<Région\>-\<\#\#\#\>                      | <ul><li>vnet-shared-eastus2-001 </li><li>vnet-prod-westus-001 </li><li>vnet-client-eastus2-001</li></ul>                                  |
| Passerelle virtuelle de réseau virtuel     | Réseau virtuel | vnet-gw-v-\<Type d’abonnement\>-\<Région\>-\<\#\#\#\>                 | <ul><li>vnet-gw-v-shared-eastus2-001 </li><li>vnet-gw-v-prod-westus-001 </li><li>vnet-gw-v-client-eastus2-001</li></ul>                   |
| Passerelle locale de réseau virtuel       | Passerelle virtuelle | vnet-gw-l-\<Type d’abonnement\>-\<Région\>-\<\#\#\#\>                 | <ul><li>vnet-gw-l-shared-eastus2-001 </li><li>vnet-gw-l-prod-westus-001 </li><li>vnet-gw-l-client-eastus2-001</li></ul>                   |
| Connexions site à site | Resource group  | cn-\<nom de la passerelle locale\>-to-\<nom de la passerelle virtuelle\>                 | <ul><li>cn-l-gw-shared-eastus2-001-to-v-gw-shared-eastus2-001 </li><li>cn-l-gw-shared-eastus2-001-to-shared-westus-001</li></ul> |
| Connexions au réseau virtuel         | Resource group  | cn-\<abonnment1\>\<région1\>-to-\<abonnement2\>\<région2\>-      | <ul><li>cn-shared-eastus2-to-shared-westus </li><li>cn-prod-eastus2-to-prod-westus</li></ul>                                     |
| Subnet                   | Réseau virtuel | snet-\<abonnement\>-\<sous-région\>-\<\#\#\#\>                       | <ul><li>snet-shared-eastus2-001 </li><li>snet-prod-westus-001 </li><li>snet-client-eastus2-001</li></ul>                                  |
| Groupe de sécurité réseau   | Sous-réseau ou carte réseau   | nsg-\<nom de la stratégie ou de l’application\>-\<\#\#\#\>                             | <ul><li>nsg-weballow-001 </li><li>nsg-rdpallow-001 </li><li>nsg-sqlallow-001 </li><li>nsg-dnsbloked-001</li></ul>                                  |
| Adresse IP publique                | Resource group  | pip-\<nom de la machine virtuelle ou de l’application\>-\<Environnement\>-\<sous-région\>-\<\#\#\#\> | <ul><li>pip-dc1-shared-eastus2-001 </li><li>pip-hadoop-prod-westus-001</li></ul>                                                 |

### <a name="azure-virtual-machines"></a>Machines virtuelles Azure

| Type de ressource         | Étendue          | Format                                                              | Exemples                                                                             |
|--------------------|----------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Machines virtuelles Azure    | Resource group | vm\<nom de la stratégie ou de l’application\>\<\#\#\#\>                              | <ul><li>vmnavigator001 </li><li>vmsharepoint001 </li><li>vmsqlnode001 </li><li>vmhadoop001</li></ul>                              |
| Compte de stockage de machine virtuelle | Globale         | stvm\<type de niveau de performance\>\<nom de l’application ou du produit\>\<région\>\<\#\#\#\> | <ul><li>stvmstcoreeastus2001 </li><li>stvmpmcoreeastus2001 </li><li>stvmstplmeastus2001 </li><li>stvmsthadoopeastus2001</li></ul> |
| Étiquette DNS          | Globale         | \<Un enregistrement de machine virtuelle\>.[\<région\>.cloudapp.azure.com]                  | <ul><li>dc1.westus.cloudapp.azure.com </li><li>web1.eastus2.cloudapp.azure.com</li></ul>                        |
| Azure Load Balancer      | Resource group | lb-\<nom de l’application ou rôle\>\<Environnement\>\<\#\#\#\>                    | <ul><li>lb-navigator-prod-001 </li><li>lb-sharepoint-dev-001</li></ul>                                          |
| Carte d’interface réseau                | Resource group | nic-\<\#\#\>-\<nom de la machine virtuelle\>-\<abonnement\>\<\#\#\#\>                  | <ul><li>nic-01-dc1-shared-001 </li><li>nic-02-vmhadoop1-prod-001 </li><li>nic-02-vmtest1-client-001</li></ul>            |

### <a name="paas-services"></a>Services PaaS

| Type de ressource     | Étendue  | Format                                                              | Exemples                                                                                 |
|----------------|--------|---------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Azure App Service    | Globale | azapp-\<Nom de l’application\>-\<Environnement\>-\<\#\#\#\>.[{azurewebsites.net}] | <ul><li>azapp-navigator-prod-001.azurewebsites.net </li><li>azapp-accountlookup-dev-001.azurewebsites.net</li></ul> |
| Application Azure Functions   | Globale | azfun-\<Nom de l’application\>-\<Environnement\>-\<\#\#\#\>.[{azurewebsites.net}] | <ul><li>azfun-navigator-prod-001.azurewebsites.net </li><li>azfun-accountlookup-dev-001.azurewebsites.net</li></ul> |
| Services cloud Azure | Globale | azcs-\<Nom de l’application\>-\<Environnement\>-\<\#\#\#\>.[{cloudapp.net}]       | <ul><li>azcs-navigator-prod-001.azurewebsites.net </li><li>azcs-accountlookup-dev-001.azurewebsites.net</li></ul>   |

### <a name="azure-service-bus"></a>Azure Service Bus

| Type de ressource         | Étendue       | Format                                                     | Exemples                           |
|--------------------|-------------|------------------------------------------------------------|------------------------------------|
| Azure Service Bus        | Globale      | sb-\<Nom de l’application\>-\<Environnement\>.[{servicebus.windows.net}] | <ul><li>sb-navigator-prod </li><li>sb-emissions-dev</li></ul> |
| Files d’attente Azure Service Bus | Service Bus | sbq-\<descripteur de requête\>                                   | <ul><li>sbq-messagequery</li></ul>                   |

### <a name="databases"></a>Bases de données

| Type de ressource                          | Étendue              | Format                                | Exemples                                       |
|-------------------------------------|--------------------|---------------------------------------|------------------------------------------------|
| Azure SQL Database                  | Globale             | sqldb-\<Nom de l’application\>-\<Environnement\>    | <ul><li>sqldb-navigator-prod </li><li>sqldb-emissions-dev</li></ul>       |
| Azure Cosmos DB (anciennement DocumentDB) | Globale             | cosdb-\<Nom de l’application\>-\<Environnement\>    | <ul><li>cosdb-navigator-prod </li><li>cosdb-emissions-dev</li></ul>       |
| Cache Azure pour Redis               | Globale             | redis-\<Nom de l’application\>-\<Environnement\>    | <ul><li>redis-navigator-prod </li><li>redis-emissions-dev</li></ul>       |
| Azure Database pour MySQL            | Globale             | mysql-\<Nom de l’application\>-\<Environnement\>    | <ul><li>mysql-navigator-prod </li><li>mysql-emissions-dev</li></ul>       |
| Azure SQL Data Warehouse                  | Globale             | sqldw-\<Nom de l’application\>-\<Environnement\>    | <ul><li>sqldw-navigator-prod </li><li>sqldw-emissions-dev</li></ul>       |
| SQL Server Stretch Database         | Azure SQL Database | sqlstrdb-\<Nom de l’application\>-\<Environnement\> | <ul><li>sqlstrdb-navigator-prod </li><li>sqlstrdb-emissions-dev</li></ul> |

### <a name="storage"></a>Stockage

| Type de ressource                              | Étendue  | Format                                                                        | Exemples                                   |
|-----------------------------------------|--------|-------------------------------------------------------------------------------|--------------------------------------------|
| Compte de stockage Azure – usage général     | Globale | st\<nom de stockage\>\<\#\#\#\>                                                  | <ul><li>stnavigatordata001 </li><li>stemissionsoutput001</li></ul>    |
| Compte de stockage Azure – journaux de diagnostic | Globale | stdiag\<les 2 premières lettres du nom de l’abonnement et numéro\>\<région\>\<\#\#\#\> | <ul><li>stdiagsh001eastus2001 </li><li>stdiagsh001westus001</li></ul> |
| Azure StorSimple                              | Globale | ssimp\<Nom de l’application\>\<Environnement\>                                              | <ul><li>ssimpnavigatorprod </li><li>ssimpemissionsdev</li></ul>       |

### <a name="ai--machine-learning"></a>IA + Machine Learning

| Type de ressource                       | Étendue          | Format                            | Exemples                               |
|----------------------------------|----------------|-----------------------------------|----------------------------------------|
| Recherche Azure                     | Globale         | srch-\<Nom de l’application\>-\<Environnement\> | <ul><li>srch-navigator-prod </li><li>srch-emissions-dev</li></ul> |
| Azure Cognitive Services               | Resource group | cs-\<Nom de l’application\>-\<Environnement\>   | <ul><li>cs-navigator-prod </li><li>cs-emissions-dev</li></ul>     |
| Espace de travail Azure Machine Learning | Resource group | aml-\<Nom de l’application\>-\<Environnement\>  | <ul><li>aml-navigator-prod </li><li>aml-emissions-dev</li></ul>   |

### <a name="analytics"></a>Analytics

| Type de ressource                | Étendue  | Format                             | Exemples                                 |
|---------------------------|--------|------------------------------------|------------------------------------------|
| Azure Data Factory        | Globale | df-\<Nom de l’application\>\<Environnement\>     | <ul><li>df-navigator-prod </li><li>df-emissions-dev</li></ul>       |
| Azure Data Lake Storage   | Globale | dls-\<Nom de l’application\>\<Environnement\>     | <ul><li>dlsnavigatorprod </li><li>dlsemissionsdev</li></ul>         |
| Service Analytique Azure Data Lake | Globale | dla\<Nom de l’application\>\<Environnement\>     | <ul><li>dlanavigatorprod </li><li>dlaemissionsdev</li></ul>         |
| Azure HDInsight – Spark         | Globale | hdis-\<Nom de l’application\>-\<Environnement\>  | <ul><li>hdis-navigator-prod </li><li>hdis-emissions-dev </li></ul>  |
| Azure HDInsight – Hadoop        | Globale | hdihd-\<Nom de l’application\>-\<Environnement\> | <ul><li>hdihd-hadoop-prod </li><li>hdihd-emissions-dev</li></ul>    |
| Azure HDInsight – R Server      | Globale | hdir-\<Nom de l’application\>-\<Environnement\>  | <ul><li>hdir-navigator-prod </li><li>hdir-emissions-dev</li></ul>   |
| Azure HDInsight – HBase         | Globale | hdihb-\<Nom de l’application\>-\<Environnement\> | <ul><li>hdihb-navigator-prod </li><li>hdihb-emissions-dev</li></ul> |
| Power BI Embedded         | Globale | pbiemb\<Nom de l’application\>\<Environnement\>  | <ul><li>pbiem-navigator-prod </li><li>pbiem-emissions-dev</li></ul> |

### <a name="internet-of-things-iot"></a>Internet des objets (IoT)

| Type de ressource                         | Étendue          | Format                             | Exemples                                 |
|------------------------------------|----------------|------------------------------------|------------------------------------------|
| Azure Stream Analytics sur IoT Edge | Resource group | asa-\<Nom de l’application\>-\<Environnement\>   | <ul><li>asa-navigator-prod </li><li>asa-emissions-dev</li></ul>     |
| Azure IoT Hub                      | Globale         | aih-\<Nom de l’application\>-\<Environnement\>   | <ul><li>aih-navigator-prod </li><li>aih-emissions-dev</li></ul>     |
| Hubs d'événements Azure                          | Globale         | evh-\<Nom de l’application\>-\<Environnement\>   | <ul><li>evh-navigator-prod </li><li>evh-emissions-dev</li></ul>     |
| Azure Notification Hubs                   | Resource group | anh-\<Nom de l’application\>-\<Environnement\>   | <ul><li>evh-navigator-prod </li><li>evh-emissions-dev</li></ul>     |
| Espace de noms d’Azure Notification Hubs         | Globale         | anhns-\<Nom de l’application\>-\<Environnement\> | <ul><li>anhns-navigator-prod </li><li>anhns-emissions-dev</li></ul> |
