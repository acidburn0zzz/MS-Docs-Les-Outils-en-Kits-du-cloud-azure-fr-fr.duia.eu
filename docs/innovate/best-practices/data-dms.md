---
title: 'Innovation cloud : Service de migration des données'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Innovation cloud : service de migration de données'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: c75efe3576bb61ecb116ab22e4946b8d87da3d4a
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683432"
---
# <a name="collect-data-through-the-migration-and-modernization-of-existing-data-sources"></a>Collecter des données dans le cadre de la migration et de la modernisation de sources de données existantes

Les entreprises possèdent souvent une variété de données existantes qui peuvent être [démocratisées](../considerations/data.md). Quand l’hypothèse client implique l’utilisation de données existantes pour créer des solutions modernes, la première étape peut consister à migrer et moderniser les données pour préparer les inventions et les innovations. En vue d’aligner la migration et la modernisation sur les efforts de migration existants d’un plan d’adoption du cloud, il peut être plus simple de les réaliser dans le cadre de la [méthodologie de migration](../../migrate/index.md).

## <a name="use-of-this-article"></a>Utilisation de cet article

Cet article présente une série d’approches qui s’alignent sur les processus de migration, mais qui peuvent s’aligner encore mieux sur les chaînes d’outils de migration standard. Pendant le processus d’évaluation de la méthodologie de migration, l’équipe d’adoption du cloud évalue l’état actuel et l’état futur souhaité de la ressource à migrer. Quand ce processus s’inscrit dans un effort d’innovation, les deux équipes d’adoption du cloud peuvent utiliser cet article pour prendre ces décisions.

## <a name="primary-toolset"></a>Ensemble d’outils principal

Pour la migration et la modernisation de données résidant actuellement localement, l’outil Azure le plus fréquemment choisi est [Database Migration Service (DMS)](https://docs.microsoft.com/azure/dms), qui fait partie de la chaîne d’outils [Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview). Pour les sources de données SQL Server existantes, l’[Assistant Migration de données](/sql/dma/dma-overview) (DMA, Data Migration Assistant) peut également offrir une assistance pour l’évaluation et la migration de structures de données moins nombreuses.

[Database Migration Service (DMS)](https://docs.microsoft.com/azure/dms) peut également être utilisé pour la prise en charge des migrations Oracle et NoSQL, et ce, pour certains types de bases de données sources et cibles, notamment pour les migrations d’Oracle vers PostgreSQL ou de MongoDB vers Cosmos DB. Les équipes d’adoption ont plus souvent recours à des outils tiers ou à des scripts de migration personnalisés pour migrer vers Cosmos DB, HDInsight ou des options de machine virtuelle IaaS.

## <a name="considerations-and-guidance"></a>Aide et aspects à prendre en considération

Quand vous utilisez DMS pour la migration et la modernisation de données, il est important de comprendre la plateforme actuellement utilisée pour héberger les données (source), la version ainsi que la plateforme et la version futures les mieux adaptées à l’hypothèse client (cible). La liste suivante présente les paires de source et cible à examiner avec l’équipe de migration. Chacune d’elles est accompagnée d’un choix d’outils et d’un lien vers un guide basés sur ces considérations.

**Type de migration :** Dans le cas d’une migration hors connexion, le temps d’arrêt de l’application commence en même temps que le lancement de la migration. Dans le cas d’une migration en ligne, le temps d’arrêt est limité à la durée du basculement à la fin de la migration. Nous vous suggérons de réfléchir au temps d’arrêt d’activité acceptable et de tester une migration hors connexion pour déterminer si le délai de restauration est approprié. Si ce n’est pas le cas, effectuez une migration en ligne.

|Source  |Cible  |Outil  |Type de migration  |Assistance  |
|---------|---------|---------|---------|---------|
|SQL Server|Azure SQL Database|DMS|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Azure SQL Database|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Azure SQL Database Managed Instance|DMS|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Azure SQL Database Managed Instance|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|RDS SQL Server|Azure SQL Database (ou Managed Instance)|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|
|MySQL|Azure Database pour MySQL|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-mysql-azure-mysql-online)|
|PostgreSQL|Azure Database pour PostgreSQL|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-postgresql-azure-postgresql-online)|
|MondoDB|API Mongo d’Azure Cosmos DB|DMS|Hors ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db)|
|MongoDB|API Mongo d’Azure Cosmos DB|DMS|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db-online)|
|Oracle|Gamme d’options PaaS et IaaS|Tiers ou Azure Migrate|Divers|[Decision Tree](../../migrate/expanded-scope/data-oracle-migration.md)|
|Différentes bases de données NoSQL|Cosmo DB ou options IaaS|Migrations procédurales ou Azure Migrate|Divers|[Decision Tree](../../migrate/expanded-scope/data-no-sql-migration.md)|
