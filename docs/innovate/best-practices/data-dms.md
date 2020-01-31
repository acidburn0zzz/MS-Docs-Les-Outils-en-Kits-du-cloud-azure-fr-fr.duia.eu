---
title: 'Innovation cloud : Azure Database Migration Service'
description: Innovation cloud – Azure Database Migration Service
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 44ebe7e28eea56d1b7e61b5926a9588f4c985ae1
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808666"
---
# <a name="collect-data-through-the-migration-and-modernization-of-existing-data-sources"></a>Collecter des données dans le cadre de la migration et de la modernisation de sources de données existantes

Les entreprises ont souvent différents types de données existantes qu’elles peuvent [démocratiser](../considerations/data.md). Quand l’hypothèse d’un client implique l’utilisation de données existantes pour créer des solutions modernes, la première étape peut consister à migrer et moderniser les données pour préparer les inventions et les innovations. En vue d’aligner la migration et la modernisation sur les efforts de migration existants d’un plan d’adoption du cloud, vous pouvez les réaliser plus facilement dans le cadre de la [méthodologie de migration](../../migrate/index.md).

## <a name="use-of-this-article"></a>Utilisation de cet article

Cet article décrit une série d’approches qui s’alignent sur le processus de migration. Vous pouvez mieux aligner ces approches sur le chaîne d’outils de migration standard.

Pendant le processus d’évaluation de la méthodologie de migration, une équipe d’adoption du cloud évalue l’état actuel et l’état futur souhaité de la ressource à migrer. Quand ce processus s’inscrit dans un effort d’innovation, les deux équipes d’adoption du cloud peuvent utiliser cet article comme pour effectuer ces évaluations.

## <a name="primary-toolset"></a>Ensemble d’outils principal

Lorsque vous migrez et modernisez des données locales, l’outil Azure le plus couramment choisi est [Azure Database Migration Service](https://docs.microsoft.com/azure/dms). Ce service fait partie de la vaste chaîne d'outils [Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview). Pour les sources de données SQL Server existantes, l’[Assistant Migration de données](https://docs.microsoft.com/sql/dma/dma-overview) peut vous aider à évaluer et à migrer un petit nombre de structures de données.

Pour prendre en charge les migrations Oracle et NoSQL, vous pouvez également utiliser [Database Migration Service](https://docs.microsoft.com/azure/dms) pour certains types de bases de données source/cible. Les exemples incluent des migrations d’Oracle vers PostgreSQL et de MongoDB vers Cosmos DB. D’une manière plus générale, les équipes d’adoption utilisent des outils partenaires ou des scripts personnalisés pour migrer vers Azure Cosmos DB, Azure HDInsight ou des options de machine virtuelle basées sur infrastructure as a service (IaaS).

## <a name="considerations-and-guidance"></a>Aide et aspects à prendre en considération

Quand vous utilisez Azure Database Migration Service pour la migration et la modernisation des données, il est important de comprendre ce qui suit :

- La plateforme actuelle pour l’hébergement de la source de données.
- La version actuelle.
- La plateforme future et la version qui prend le mieux en charge l’hypothèse ou la cible du client.

Le tableau suivant présente les paires de source et cible à examiner avec l’équipe de migration. Chaque paire comprend un choix d’outils et un lien vers un guide associé.

### <a name="migration-type"></a>Type de migration

Dans le cas d’une migration hors connexion, le temps d’arrêt de l’application commence en même temps que le lancement de la migration. Dans le cas d’une migration en ligne, le temps d’arrêt est limité à la durée du basculement à la fin de la migration.

Nous vous suggérons de décider du temps d’arrêt acceptable pour votre entreprise et de tester une migration hors connexion. Ceci permet de vérifier si la durée de la restauration correspond à un temps d’arrêt acceptable. Si la durée de la restauration est inacceptable, effectuez une migration en ligne.

|Source  |Cible  |Outil  |Type de migration  |Assistance  |
|---------|---------|---------|---------|---------|
|SQL Server|Azure SQL Database|Database Migration Service|Hors connexion|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Azure SQL Database|Database Migration Service|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Azure SQL Database Managed Instance|Database Migration Service|Hors connexion|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Azure SQL Database Managed Instance|Database Migration Service|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Azure SQL Database ou instance gérée d’Azure SQL Database|Database Migration Service|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|
|MySQL|Azure Database pour MySQL|Database Migration Service|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-mysql-azure-mysql-online)|
|PostgreSQL|Azure Database pour PostgreSQL|Database Migration Service|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-postgresql-azure-postgresql-online)|
|MongoDB|API Mongo d’Azure Cosmos DB|Database Migration Service|Hors connexion|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db)|
|MongoDB|API Mongo d’Azure Cosmos DB|Database Migration Service|En ligne|[Didacticiel](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db-online)|
|Oracle|Différentes options de plateforme en tant que service (PaaS) et d’IaaS|L’outil d’un partenaire ou Azure Migrate|Hors connexion ou en ligne|[Arbre de décision](../../migrate/expanded-scope/data-oracle-migration.md)|
|Différentes options de bases de données NoSQL|Cosmo DB ou options IaaS|Migrations procédurales ou Azure Migrate|Hors connexion ou en ligne|[Arbre de décision](../../migrate/expanded-scope/data-no-sql-migration.md)|
