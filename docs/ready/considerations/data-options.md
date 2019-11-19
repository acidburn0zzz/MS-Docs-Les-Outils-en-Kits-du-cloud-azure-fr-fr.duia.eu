---
title: Passer en revue vos options de données
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Passer en revue vos options de données pour les charges de travail Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 950465788053fa0977a158a5363cb6271e65b3e6
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73243324"
---
# <a name="review-your-data-options"></a>Passer en revue vos options de données

Lorsque vous préparez votre environnement de zone d’accueil pour votre adoption du cloud, vous devez déterminer la configuration requise en données pour l’hébergement de vos charges de travail. Les produits et services de base de données d’Azure prennent en charge un large éventail de scénarios et de fonctionnalités pour le stockage de données. La façon dont vous configurez votre environnement de zone d’accueil pour prendre en charge votre configuration requise en données dépend des exigences techniques, métier et de gouvernance des charges de travail.

## <a name="identify-data-services-requirements"></a>Identifier la configuration requise pour les services de données

Dans le cadre de l’évaluation et de la préparation de votre zone d’accueil, vous devez identifier les banques de données que votre zone d’accueil doit prendre en charge. Le processus implique l’évaluation de l’ensemble des applications et services qui composent vos charges de travail afin de déterminer leurs exigences en matière de banque de données et d’accès. Une fois que vous avez identifié et documenté ces exigences, vous pouvez créer des stratégies pour votre zone d’accueil afin de contrôler les types de ressources autorisés en fonction de vos besoins quant aux charges de travail.

Pour chaque application ou service que vous allez déployer dans votre environnement de zone d’accueil, utilisez l’arbre de décision suivant comme point de départ pour vous aider à déterminer les outils ou services de banque de données à utiliser :

![Arbre de décision pour les services de base de données Azure](../../_images/ready/data-decision-tree.png)

### <a name="key-questions"></a>Questions clés

Répondez aux questions suivantes sur vos charges de travail pour vous aider à prendre des décisions en vous basant sur l’arbre de décision des services de base de données Azure :

- **Avez-vous besoin du contrôle total ou de la pleine propriété de votre logiciel de base de données ou de votre système d’exploitation hôte ?** Dans certains scénarios, vous devez disposer d’un niveau élevé de contrôle ou de propriété de la configuration logicielle et des serveurs hôtes pour vos charges de travail de base de données. Dans ces scénarios, vous pouvez déployer des machines virtuelles Infrastructure as a service (IaaS) personnalisées pour contrôler entièrement le déploiement et la configuration des services de données. Si vous n’avez pas ces exigences, les services de base de données managés par Platform as a service (PaaS) peuvent réduire vos coûts de gestion et d’opérations.
- **Vos charges de travail utiliseront-elles une technologie de base de données relationnelle ?** Si oui, quelle technologie prévoyez-vous d’utiliser ? Azure fournit des fonctionnalités de base de données PaaS managées pour [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), [MySQL](https://docs.microsoft.com/azure/mysql/overview), [PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview) et [MariaDB](https://docs.microsoft.com/azure/mariadb/overview).
- **Vos charges de travail utiliseront-elles SQL Server ?** Dans Azure, vous pouvez exécuter vos charges de travail dans les instances [SQL Server basées sur IaaS sur des machines virtuelles Azure](https://azure.microsoft.com/services/virtual-machines/sql-server) ou sur le [service hébergé Azure SQL Database basé sur PaaS](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview). Le choix de l’option à utiliser est principalement une question de savoir si vous souhaitez gérer votre base de données, appliquer des correctifs et effectuer des sauvegardes, ou si vous souhaitez déléguer ces opérations à Azure. Dans certains scénarios, des problèmes de compatibilité peuvent nécessiter l’utilisation de SQL Server hébergé par IaaS. Pour plus d’informations sur la façon de choisir l’option appropriée pour vos charges de travail, consultez [Choisir l’option SQL Server appropriée dans Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).
- **Vos charges de travail utiliseront-elles le stockage de base de données clé/valeur ?** [Le cache Azure pour Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview) offre une solution de stockage de données clé/valeur mise en cache et à hautes performances qui peut alimenter des applications rapides et évolutives. [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) fournit également des fonctionnalités de stockage clé/valeur à usage général.
- **Vos charges de travail utiliseront-elles des données de document ou de graphique ?** [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) est un service de base de données multimodèle qui prend en charge un large éventail de types de données et d’API. Azure Cosmos DB fournit également des fonctionnalités de base de données pour documents et graphiques.
- **Vos charges de travail utiliseront-elles des données de familles de colonnes ?** [Apache HBase dans Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/hbase/apache-hbase-overview) est basé sur Apache Hadoop. Il prend en charge de grandes quantités de données non structurées et semi-structurées dans une base de données sans schéma, organisée par familles de colonnes.
- **Vos charges de travail nécessiteront-elles des fonctionnalités Analytique données de grande capacité ?** Vous pouvez utiliser [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) pour stocker et interroger efficacement des données structurées à l’échelle du pétaoctet. Pour les charges de travail Big Data non structurées, vous pouvez utiliser [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake) pour stocker et analyser des fichiers de plusieurs pétaoctets et des milliards d’objets.
- **Vos charges de travail nécessiteront-elles des fonctionnalités de moteur de recherche ?** Vous pouvez utiliser [Recherche Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search) pour créer des index de recherche informatiques basés sur l’intelligence artificielle, qui peuvent être intégrés à vos applications.
- **Vos charges de travail utiliseront-elles des données de série chronologique ?** [Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-overview) est conçu pour stocker, visualiser et interroger de grandes quantités de données de série chronologique, comme celles générées par les appareils IoT.

> [!NOTE]
> En savoir plus sur l’évaluation des options de base de données pour l’ensemble de vos applications et services dans le [guide de l’architecture des applications Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-comparison).

## <a name="common-database-scenarios"></a>Scénarios de base de données courants

Le tableau suivant illustre quelques configurations requises des scénarios d’utilisation courants et les services de base de données recommandés pour les gérer :

| **Scénario** | **Service de données** |
|-----|-----|
| J’ai besoin d’une base de données multimodèle distribuée à l’échelle mondiale avec prise en charge des choix NoSQL. | [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) |
| J’ai besoin d’une base de données relationnelle complètement managée qui s’approvisionne rapidement, est mise à l’échelle immédiatement et inclut des fonctionnalités de sécurité et d’intelligence intégrées. | [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) |
| J’ai besoin d’une base de données relationnelle MySQL évolutive et complètement managée avec une haute disponibilité et une sécurité intégrées, sans coût supplémentaire. | [Azure Database pour MySQL](https://docs.microsoft.com/azure/mysql/overview) |
| J’ai besoin d’une base de données relationnelle PostgreSQL évolutive et complètement managée avec une haute disponibilité et une sécurité intégrées, sans coût supplémentaire. | [Base de données Azure pour PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview) |
| J’ai l’intention d’héberger des applications SQL Server d’entreprise dans le cloud et d’avoir le contrôle total du système d’exploitation du serveur. | [SQL Server sur les machines virtuelles](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview) |
| J’ai besoin d’un entrepôt de données élastique complètement managé proposant une sécurité à chaque niveau d’échelle, sans coût supplémentaire. | [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) |
| J’ai besoin de ressources de stockage Data Lake qui peuvent prendre en charge les clusters Hadoop ou les données HDFS. | [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake) |
| J’ai besoin d’un débit élevé et d’un accès cohérent et à faible latence pour mes données afin de prendre en charge des applications rapides et évolutives. | [Cache Azure pour Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview) |
| J’ai besoin d’une base de données relationnelle MariaDB évolutive et complètement managée avec une haute disponibilité et une sécurité intégrées, sans coût supplémentaire. | [Azure Database for MariaDB](https://docs.microsoft.com/azure/mariadb/overview) |

## <a name="regional-availability"></a>Disponibilité régionale

Azure vous permet d’offrir des services à l’échelle dont vous avez besoin pour atteindre vos clients et partenaires,  _où qu’ils soient_. Un facteur clé dans la planification de votre déploiement cloud consiste à déterminer quelle région Azure hébergera vos ressources de charge de travail.

La plupart des services de base de données sont généralement disponibles dans la majorité des régions Azure. Toutefois, il existe quelques régions, ciblant principalement les clients gouvernementaux, qui prennent en charge uniquement un sous-ensemble de ces produits. Avant de choisir les régions dans lesquelles vous allez déployer vos ressources de base de données, nous vous recommandons de consulter la [page Régions](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=data-factory,sql-server-stretch-database,redis-cache,database-migration,sql-data-warehouse,postgresql,mariadb,cosmos-db,mysql,sql-database) pour vérifier l’état le plus récent de la disponibilité régionale.

Pour en savoir plus sur l’infrastructure globale d’Azure, consultez la [page Régions Azure](https://azure.microsoft.com/global-infrastructure/regions). Vous pouvez également afficher [les produits disponibles par région](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=all) pour obtenir des détails spécifiques sur les services globaux disponibles dans chaque région Azure.

## <a name="data-residency-and-compliance-requirements"></a>Conditions de résidence et de conformité des données

Des exigences légales et contractuelles relatives au stockage de données s’appliquent souvent à vos charges de travail. Ces exigences peuvent varier en fonction de l’emplacement de votre organisation, de la juridiction des ressources physiques qui hébergent vos banques de données et de votre secteur d’activité. Les composants des obligations de données à prendre en compte incluent la classification des données, l’emplacement des données et les responsabilités respectives pour la protection des données dans le cadre du modèle de responsabilité partagée. Pour obtenir de l’aide sur la compréhension de ces exigences, consultez le livre blanc  [Assurer la conformité de la résidence et de la sécurité des données avec Azure](https://azure.microsoft.com/resources/achieving-compliant-data-residency-and-security-with-azure).

Une partie de vos efforts de conformité peut inclure le contrôle de l’emplacement physique de vos ressources de base de données. Les régions Azure sont organisées en groupes appelés zones géographiques. Une  [zone géographique Azure](https://azure.microsoft.com/global-infrastructure/geographies)  garantit que les exigences de résidence, de souveraineté, de conformité et de résilience des données sont respectées dans les limites géographiques et politiques. Si vos charges de travail sont soumises à une souveraineté des données ou à d’autres exigences de conformité, vous devez déployer vos ressources de stockage dans des régions situées dans une zone géographique Azure conforme.

## <a name="establish-controls-for-database-services"></a>Établir des contrôles pour les services de base de données

Lorsque vous préparez votre environnement de zone d’accueil, vous pouvez établir des contrôles qui limitent les banques de données que les utilisateurs peuvent déployer. Les contrôles peuvent vous aider à gérer les coûts et à limiter les risques de sécurité, tout en permettant aux développeurs et aux équipes informatiques de déployer et de configurer les ressources nécessaires pour prendre en charge vos charges de travail.

Après avoir identifié et documenté la configuration requise de votre zone d’accueil, vous pouvez utiliser [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) pour contrôler les ressources de base de données que vous autorisez les utilisateurs à créer. Les contrôles peuvent prendre la forme [d’autorisations ou de refus de création de types de ressources de base de données](https://docs.microsoft.com/azure/governance/policy/samples/allowed-resource-types). Par exemple, vous pouvez limiter les utilisateurs à la création de ressources Azure SQL Database uniquement. Vous pouvez également utiliser une stratégie pour contrôler les options autorisées lors de la création d’une ressource, comme la [restriction des références SKU de SQL Database qui peuvent être approvisionnées](https://docs.microsoft.com/azure/governance/policy/samples/allowed-sql-db-skus) ou [l’autorisation d’installer uniquement des versions spécifiques du serveur SQL](https://docs.microsoft.com/azure/governance/policy/samples/require-sql-12) sur une machine virtuelle IaaS.

Les stratégies peuvent être étendues à des ressources, des groupes de ressources, des abonnements et des groupes d’administration. Vous pouvez inclure vos stratégies dans les définitions d’[Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints/overview) et les appliquer à plusieurs reprises à l’ensemble de votre parc cloud.
