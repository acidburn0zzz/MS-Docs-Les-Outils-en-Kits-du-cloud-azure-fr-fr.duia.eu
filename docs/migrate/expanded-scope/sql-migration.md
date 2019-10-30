---
title: Accélérer la migration grâce à une migration SQL
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Accélérer la migration grâce à une migration SQL
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4af94af91874ac666f45a917eed003b3cf881c51
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558611"
---
# <a name="accelerate-migration-with-a-sql-migration"></a>Accélérer la migration grâce à une migration SQL

La migration d’instances entières peut accélérer les efforts de migration de la charge de travail. L’aide suivante étendra la portée du [guide de migration Azure](../azure-migration-guide/index.md) en migrant un serveur SQL Server en dehors d’un effort de migration centré sur la charge de travail. Cette approche peut amorcer la migration de plusieurs charges de travail grâce à une seule migration de plateforme de données.

## <a name="general-scope-expansion"></a>Expansion de l’étendue générale

La majeure partie de l’effort nécessaire à l’expansion de cette portée se produit au cours des processus de détermination des prérequis, d’évaluation, de migration et d’optimisation d’un effort de migration.

<!-- markdownlint-disable MD026 -->

## <a name="is-this-expanded-scope-right-for-you"></a>Cette portée élargie vous convient-elle ?

L’approche recommandée décrite dans le [guide de migration Azure](../azure-migration-guide/index.md) consiste à migrer chaque structure de données avec les charges de travail associées dans le cadre d’un seul effort de migration. L’approche itérative de la migration réduit la découverte, l’évaluation et d’autres tâches qui peuvent créer des entraves et ralentir les retours de valeur métier.

Toutefois, certaines structures de données peuvent être migrées plus efficacement par le biais d’une migration distincte de plateforme de données. Voici quelques exemples qui peuvent entraîner l’utilisation de ce guide à la portée étendue :

- **Fin du service :** Le déplacement rapide d’une instance pour éviter des problèmes de fin du service peut justifier l’utilisation de ce guide en dehors des efforts de migration standard.
- **Services SQL Server :** La structure de données fait partie d’une solution plus large qui requiert l’exécution de SQL Server sur une machine virtuelle. Cela est courant pour les solutions qui tirent parti des services SQL Server tels que SQL Server Reporting Services, SQL Server Integration Services ou SQL Server Analysis Services.
- **Bases de données à haute densité et faible utilisation :** Le serveur SQL Server a une densité élevée de bases de données. Chacune de ces bases de données a un faible volume de transactions et nécessite peu de ressources de calcul. D’autres solutions plus modernes doivent être prises en compte, mais une approche IaaS peut entraîner une réduction significative des coûts d’exploitation.
- **Coût total de possession :** Le cas échéant, [Azure Hybrid Benefits](https://azure.microsoft.com/pricing/hybrid-benefit) peut être appliqué au prix catalogue, créant ainsi le coût de possession le plus bas pour les serveurs SQL Server. Cela est particulièrement courant pour les clients qui hébergent SQL Server dans des scénarios multicloud.
- **Accélérateur de migration :** La migration lift-and-shift d’une instance peut déplacer plusieurs bases de données en une seule itération. Cette approche permet parfois aux itérations ultérieures de se concentrer plus spécifiquement sur les applications et les machines virtuelles et de migrer plus de charges de travail en une seule itération.
- **Migration des hôtes VMWare :** Une architecture locale courante comprend les applications et les machines virtuelles sur un hôte virtuel et les bases de données sur un appareil sans système d’exploitation. Lors de la migration de cette architecture courante, la migration de l’hôte VMWare vers le service Azure VMWare (AVS) peut être complétée par ce guide pour migrer des instances entières afin de prendre en charge ces hôtes virtuels. Pour obtenir des instructions complémentaires, consultez [Migration de l’hôte VMWare](./vmware-host.md).

Si aucun des critères ci-dessus ne s’applique à cette migration, il peut être préférable de poursuivre le [processus de migration standard](../index.md). Dans le processus standard, les structures de données sont migrées de manière itérative parallèlement à chaque charge de travail.

Si ce guide correspond à vos critères, continuez avec ce guide de portée élargie comme un effort dans le cadre du [processus de migration standard](../index.md). Au cours de la phase des prérequis, l’effort peut être intégré au plan d’adoption global.

## <a name="suggested-prerequisites"></a>Prérequis suggérés

Avant d’effectuer une migration vers SQL Server, commencez par une extension du **domaine numérique** en incluant un patrimoine de données. Le patrimoine de données enregistre un inventaire des ressources de données prises en compte pour la migration. Les tableaux suivants décrivent une méthode d’enregistrement du patrimoine de données.

### <a name="server-inventory"></a>Inventaire de serveur

Voici un exemple d’inventaire de serveur pour les serveurs SQL Server :

|SQL Server|Objectif|Version|[Caractère critique](../../manage/considerations/criticality.md)|[Sensibilité](../../govern/policy-compliance/data-classification.md)|Nombre de bases de données|SSIS|SSRS|SSAS|Cluster|Nombre de nœuds|
|---------|---------|---------|---------|---------|---------|---------|---------|
|sql-01|Applications principales|2016|Critique pour la mission|Hautement confidentiel|40|N/A|N/A|N/A|OUI|3|
|sql-02|Applications principales|2016|Critique pour la mission|Hautement confidentiel|40|N/A|N/A|N/A|OUI|3|
|sql-03|Applications principales|2016|Critique pour la mission|Hautement confidentiel|40|N/A|N/A|N/A|OUI|3|
|sql-04|BI|2012|Élevé|XX|6|N/A|Confidentiel|Oui – cube multidimensionnel|Non|1|
|sql-05|Intégration|2008 R2|Faible|Généralités|20|OUI|N/A|N/A|Non|1|

### <a name="database-inventory"></a>Inventaire de base de données

Voici un exemple d’inventaire de base de données pour l’un des serveurs SQL Server ci-dessus :

|Serveur|Base de données|[Caractère critique](../../manage/considerations/criticality.md)|[Sensibilité](../../govern/policy-compliance/data-classification.md)|Résultats DMA|Correction DMA|Plateforme cible|
|---------|---------|---------|---------|---------|---------|---------|
|sql-01|DB-1|Critique pour la mission|Hautement confidentiel|Compatible|N/A|Azure SQL Database|
|sql-01|DB-2|Élevé|Confidentiel|Modification requise du schéma|Modifications implémentées|Azure SQL Database|
|sql-01|DB-1|Élevé|Généralités|Compatible|N/A|Azure SQL Managed Instance|
|sql-01|DB-1|Faible|Hautement confidentiel|Modification requise du schéma|Modifications planifiées|Azure SQL Managed Instance|
|sql-01|DB-1|Critique pour la mission|Généralités|Compatible|N/A|Azure SQL Managed Instance|
|sql-01|DB-2|Élevé|Confidentiel|Compatible|N/A|Azure SQL Database|

### <a name="integration-with-the-cloud-adoption-plan"></a>Intégration au plan d’adoption du cloud

Une fois la détection terminée, le plan peut être inclus dans le [plan d’adoption du cloud](../../plan/template.md). Dans le plan d’adoption du cloud, ajoutez chaque instance à migrer en tant que de [charge de travail distincte](../../plan/workloads.md). Au sein de chaque charge de travail, les bases de données et les services (SSIS, SSAS, SSRS) peuvent chacun être ajoutés en tant que [ressources](../../plan/workloads.md). Pour ajouter des charges de travail et des ressources en masse au plan d’adoption, consultez [ajout et modification d’éléments de travail avec Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

Une fois que les charges de travail et les ressources sont incluses dans le plan, l’équipe peut poursuivre un processus de migration standard en utilisant le plan d’adoption pour guider ses efforts. Lorsque l’équipe d’adoption passe aux processus d’évaluation, de migration et d’optimisation, les modifications suivantes doivent être prises en compte dans les efforts.

## <a name="assessment-process-changes"></a>Modifications du processus d’évaluation

Si une base de données du plan peut être migrée vers une plateforme de données (PaaS), utilisez l’Assistant Migration de données pour évaluer la compatibilité de la base de données sélectionnée. Lorsque la base de données requiert des conversions de schémas, il est recommandé d’effectuer ces conversions dans le cadre du processus d’évaluation afin d’éviter toute interruption du pipeline de migration.

### <a name="suggested-action-during-the-assessment-process"></a>Action suggérée pendant le processus d’évaluation

Pour les bases de données qui peuvent être migrées vers une solution PaaS, les actions suivantes sont effectuées au cours du processus d’évaluation.

- **Évaluer avec l’Assistant Migration de données :** Utilisez l’Assistant Migration de données pour détecter les problèmes de compatibilité qui peuvent avoir un impact sur les fonctionnalités de la base de données dans votre instance cible gérée par Azure SQL Database, pour recommander des améliorations de performance et de fiabilité, ainsi que pour déplacer le schéma, les données et les objets sans relation contenant-contenu de votre serveur source vers votre serveur cible. Pour plus d’informations, consultez [Assistant Migration de données](/sql/dma/dma-overview).
- **Corriger et convertir :** En fonction des résultats de l’Assistant Migration de données, convertissez le schéma de données source pour résoudre les problèmes de compatibilité. Testez le schéma de données converti avec les applications dépendantes.

## <a name="migrate-process-changes"></a>Migrer les changements de processus

Pendant la migration, il existe plusieurs options d’outils et d’approches. Cependant, chaque approche suit un processus simple : migrer le schéma, les données et les objets. Synchronisez les données avec la source de données cible.

La cible et la source de la structure de données et des services peuvent rendre ces deux étapes complexes, dans une certaine mesure. Consultez chacune des sections suivantes pour comprendre quel est le meilleur choix d’outils en fonction de vos décisions de migration.

### <a name="suggested-action-during-the-migrate-process"></a>Action suggérée pendant le processus de migration

Le chemin suggéré pour la migration et la synchronisation utilise une combinaison des trois outils suivants. Les sections suivantes présentent des options de migration et de synchronisation plus complexes qui permettent un éventail plus large de solutions cibles et sources.

|Option de migration|Objectif|
|---------|---------|
|[Azure Database Migration Service](/sql/dma/dma-overview)|Azure DMS prend en charge les migrations en ligne (temps d’arrêt minimal) et hors connexion (une fois) à l’échelle vers une instance gérée par Azure SQL Database à partir de SQL Server 2005, SQL Server 2008 et SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 et SQL Server 2017.|
|[Réplication transactionnelle](/sql/relational-databases/replication/administration/enhance-transactional-replication-performance)|La réplication transactionnelle vers une instance gérée par Azure SQL Database est prise en charge pour les migrations à partir de : SQL Server 2012 (SP2 CU8, SP3 ou version ultérieure), SQL Server 2014 (RTM CU10 ou version ultérieure, ou SP1 CU3 ou version ultérieure), SQL Server 2016, SQL Server 2017|
|[Chargement en masse](/sql/t-sql/statements/bulk-insert-transact-sql)|Utilisez le chargement en masse vers une instance gérée par Azure SQL Database pour les données stockées dans SQL Server 2005, SQL Server 2008 et SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 et SQL Server 2017.|

### <a name="guidance-and-tutorials-for-suggested-migration-process"></a>Conseils et didacticiels pour le processus de migration suggéré

Le choix de la meilleure aide pour la migration à l’aide de DMS dépend de la plateforme source et cible de votre choix. Le tableau suivant présente les didacticiels pour chacune des approches standard de migration d’une base de données SQL à l’aide de DMS.

|Source  |Cible  |Outil  |Type de migration  |Assistance  |
|---------|---------|---------|---------|---------|
|SQL Server|Azure SQL Database|DMS|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Azure SQL Database|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Azure SQL Database Managed Instance|DMS|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Azure SQL Database Managed Instance|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Azure SQL Database (ou Managed Instance)|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|

### <a name="guidance-and-tutorials-for-various-services-to-equivalent-paas-solutions"></a>Conseils et didacticiels pour différents services destinés à des solutions PaaS équivalentes

Après le déplacement des bases de données d’un serveur SQL vers DMS, le schéma et les données peuvent être réhébergés dans plusieurs solutions PaaS. Toutefois, d’autres services requis peuvent toujours s’exécuter sur ce serveur. Les trois didacticiels suivants vous aideront à déplacer SSIS, SSAS et SSRS vers des services PaaS équivalents sur Azure.

|Source  |Cible  |Outil  |Type de migration  |Assistance  |
|---------|---------|---------|---------|---------|
|Service d’intégration SQL Server|Integration Runtime Data Factory|Azure Data Factory|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/data-factory/create-azure-ssis-integration-runtime)|
|SQL Server Analysis Service – Modèle tabulaire|Azure Analysis Services|SSDT|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)|
|SQL Server Reporting Service|Power BI Report Server|Power BI|Hors ligne|[Didacticiel](/power-bi/report-server/migrate-report-server)|

### <a name="guidance-and-tutorials-for-migration-from-sql-server-to-an-iaas-instance-of-sql-server"></a>Conseils et didacticiels pour la migration de SQL Server vers une instance IaaS de SQL Server

Après la migration des bases de données et des services vers des instances PaaS, certaines structures de données et certains services peuvent toujours ne pas être compatibles avec PaaS. Lorsque des contraintes existantes empêchent la migration de structures de données ou de services, le didacticiel ci-dessous peut vous aider à migrer les différentes ressources du portefeuille de données vers les solutions Azure IaaS.

Cette approche peut être utilisée pour migrer des bases de données sur SQL Server, ou d’autres services en cours d’exécution sur le serveur SQL Server source.

|Source  |Cible  |Outil  |Type de migration  |Assistance  |
|---------|---------|---------|---------|---------|
|SQL Server à instance unique|SQL Server sur IaaS|Différentes possibilités|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)|

## <a name="optimization-process-changes"></a>Modifications du processus d’optimisation

Pendant l’optimisation, chaque structure de données, service ou instance peut être testé, optimisé et promu en production. Il s’agit là de l’impact le plus important d’une déviation par rapport à un modèle de migration par charge de travail.

Dans l’idéal, les charges de travail, applications et machines virtuelles dépendantes sont migrées dans la même itération que l’instance. Lorsque ce scénario idéal se produit, la charge de travail peut être testée avec la source de données. Une fois le test effectué, la structure de données peut être promue en production et le processus de synchronisation peut s’arrêter.

Malheureusement, la modification la plus importante apportée au processus d’optimisation au cours d’une migration non basée sur la charge de travail survient lorsqu’il y a un laps de temps significatif entre la migration des base de données et la migration des charges de travail. Lorsque plusieurs bases de données sont migrées dans le cadre d’une migration vers SQL Server, ces bases de données peuvent coexister dans le cloud et localement pendant plusieurs itérations. Pendant ce délai d’exécution, il est nécessaire de maintenir la synchronisation des données jusqu’à ce que les ressources dépendantes soient migrées, testées et promues.

Tant que toutes les charges de travail dépendantes n’ont pas été promues, l’équipe est responsable de la prise en charge de la synchronisation des données du système source vers le système cible. Cette synchronisation consomme la bande passante réseau, les coûts du cloud et, plus important encore, le temps des personnes. L’alignement correct du plan d’adoption sur la « charge de travail » de la migration vers SQL Server, ainsi que sur toutes les charges de travail/applications dépendantes, réduira ces frais généraux coûteux.

### <a name="suggested-action-during-the-optimization-process"></a>Action suggérée pendant le processus d’optimisation

Pendant les processus d’optimisation, les tâches suivantes doivent être effectuées à chaque itération jusqu’à ce que toutes les structures de données et tous les services aient été promus en production.

1. Validez la synchronisation des données.
2. Testez toutes les applications migrées.
3. Optimisez l’application et la structure des données pour ajuster les coûts.
4. Promouvez les applications en production.
5. Testez le trafic local continu par rapport à la base de données locale.
6. Terminez la synchronisation de toute donnée promue en production.
7. Terminez la base de données source d’origine.

Tant que l’étape 5 n’est pas réussie, les bases de données et la synchronisation ne peuvent pas être terminées. Tant que toutes les bases de données d’un SQL Server n’ont pas franchi les étapes 1 à 7, le SQL Server local doit être traité comme une production et toute la synchronisation doit être maintenue.

## <a name="next-steps"></a>Étapes suivantes

Revenez à la [liste de vérification d’expansion d’étendue](./index.md) pour vous assurer que votre méthode de migration est entièrement alignée.

> [!div class="nextstepaction"]
> [Liste de contrôle d’expansion d’étendue](./index.md)
