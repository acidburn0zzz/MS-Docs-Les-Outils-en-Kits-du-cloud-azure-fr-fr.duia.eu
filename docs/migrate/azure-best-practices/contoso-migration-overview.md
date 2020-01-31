---
title: Vue d’ensemble d’exemples de migration d’application pour Azure
description: Fournit une vue d’ensemble des exemples de migration d’application inclus dans le cadre de la section Migration du Framework d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: c2e0a27e432141feee526d4cb5fe54380fcde583
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807374"
---
# <a name="application-migration-patterns-and-examples"></a>Modèles et exemples de migration d’application

Cette section du Framework d’adoption du cloud fournit des exemples de plusieurs scénarios de migration courants qui illustrent la façon dont vous pouvez migrer une infrastructure locale vers le cloud [Microsoft Azure](https://azure.microsoft.com/overview/what-is-azure).

## <a name="introduction"></a>Introduction

Azure fournit l’accès à un ensemble complet de services cloud. En tant que développeur et professionnel de l’informatique, vous pouvez utiliser ces services pour créer, déployer et gérer des applications sur un éventail d’outils et de frameworks à travers un réseau mondial de centres de données. Votre entreprise étant confrontée aux défis associés à la transition numérique, le cloud Azure vous permet de trouver la solution pour optimiser les ressources et les opérations, communiquer avec vos clients et employés et transformer vos produits.

Toutefois, Azure reconnaît que, malgré tous les avantages proposés par le cloud en termes de vitesse et de flexibilité, de réduction des coûts, de performances et de fiabilité, de nombreuses organisations vont devoir exécuter des centres de données locaux pendant un certain temps. C’est pour répondre à ces barrières concernant l’adoption du cloud qu’Azure propose une stratégie de cloud hybride qui crée des ponts entre vos centres de données locaux et le cloud public Azure. Par exemple, vous pouvez utiliser des ressources cloud Azure comme Sauvegarde Azure pour protéger des ressources locales, ou utiliser des analyses Azure pour obtenir des informations sur les charges de travail locales.

Dans le cadre de la stratégie de cloud hybride, Azure fournit toujours plus de solutions pour migrer les applications et les charges de travail locales vers le cloud. En suivant une procédure simple, vous pouvez évaluer l’intégralité de vos ressources locales pour déterminer comment elles s’exécuteront dans le cloud Azure. Une fois cette évaluation approfondie obtenue, vous pouvez migrer des ressources vers Azure en toute confiance. Quand les ressources sont opérationnelles dans Azure, vous pouvez les optimiser pour conserver et améliorer l’accès, la flexibilité, la sécurité et la fiabilité.

## <a name="migration-patterns"></a>Modèles de migration

Les stratégies pour la migration vers le cloud sont classées sous quatre grands modèles : réhébergement, refactorisation, réarchitecture ou régénération. La stratégie que vous adoptez dépend des facteurs qui pilotent votre activité et des objectifs de la migration. Vous pouvez adopter plusieurs modèles. Par exemple, vous pouvez choisir de réhéberger des applications simples ou des applications qui ne sont pas essentielles pour votre activité, mais réarchitecturer celles qui sont plus complexes et vitales pour l’entreprise. Examinons ces modèles.

<!-- markdownlint-disable MD033 -->

**Modèle** | **Définition** | **Quand utiliser**
--- | --- | ---
**Réhébergement** | Souvent appelé migration _lift-and-shift_. Cette option ne nécessite pas de modifications du code et vous permet de migrer rapidement vos applications existantes vers Azure. Chaque application est migrée en l’état, pour profiter des avantages du cloud, sans les risques et les coûts associés aux modifications du code. | Quand vous devez déplacer rapidement des applications dans le cloud.<br/><br/> Quand vous voulez déplacer une application sans la modifier.<br/><br/> Quand vos applications sont architecturées de façon à tirer parti de l’extensibilité de l’[IaaS Azure](https://azure.microsoft.com/overview/what-is-iaas) après la migration.<br/><br/> Quand des applications sont importantes pour votre activité, mais que vous n’avez pas besoin de modifications immédiates de leurs fonctionnalités.
**Refactorisation** | Souvent appelée « réempaquetage », la refactorisation nécessite des modifications minimales des applications pour qu’elles puissent se connecter au [PaaS Azure](https://azure.microsoft.com/overview/what-is-paas) et utiliser des offres cloud.<br/><br/> Par exemple, vous pouvez migrer vos applications existantes vers Azure App Service ou Azure Kubernetes Service.<br/><br/> Vous pouvez aussi refactoriser vos bases de données relationnelles et non relationnelles en options telles qu’Azure SQL Database Managed Instance, Azure Database pour MySQL, Azure Database pour PostgreSQL ou Azure Cosmos DB. | Si votre application peut être facilement repackagée pour fonctionner dans Azure.<br/><br/> Si vous voulez appliquer des pratiques DevOps innovantes fournie par Azure, ou si vous envisagez d’utiliser DevOps avec une stratégie de conteneur pour les charges de travail.<br/><br/> Pour la refactorisation, vous devez penser à la portabilité de votre base de code existante et à la disponibilité des compétences en développement.
**Réarchitecture** | La réarchitecture pour la migration porte principalement sur la modification et l’extension des fonctionnalités et de la base de code de l’application, avec comme objectif d’optimiser l’architecture de l’application pour la scalabilité du cloud.<br/><br/> Par exemple, vous pouvez décomposer une application monolithique en un groupe de microservices qui fonctionnent ensemble et sont facilement mis à l’échelle.<br/><br/> Vous pouvez aussi réarchitecturer vos bases de données relationnelles et non relationnelles vers une solution de base de données complètement managée, comme Azure SQL Database Managed Instance, Azure Database pour MySQL, Azure Database pour PostgreSQL et Azure Cosmos DB. | Quand votre application nécessite des révisions majeures pour incorporer de nouvelles fonctionnalités, ou pour fonctionner efficacement sur une plateforme cloud.<br/><br/> Quand vous voulez utiliser des investissements faits dans des applications existantes, répondre à des exigences d’extensibilité, appliquer des pratiques Azure DevOps innovantes et minimiser l’utilisation de machines virtuelles.
**Recréation** | La recréation va encore plus loin en recréant une application à partir de rien, en utilisant les technologies du cloud Azure.<br/><br/> Par exemple, vous pouvez créer des applications entièrement nouvelles avec des technologies [cloud natives](https://azure.com/cloudnative) comme Azure Functions, Azure AI, Azure SQL Database Managed Instance et Azure Cosmos DB. | Quand vous voulez un développement rapide, et que les applications existantes ont des fonctionnalités et une durée de vie limitées.<br/><br/> Quand vous êtes prêt à accélérer l’innovation pour votre activité (notamment les pratiques DevOps fournies par Azure), à créer de nouvelles applications en utilisant les technologies cloud natives et à tirer parti des avancées de l’IA, de Blockchain et d’IoT.

<!-- markdownlint-enable MD033 -->

## <a name="migration-example-articles"></a>Articles d’exemples de migration

Les articles de cette section fournissent des exemples de plusieurs scénarios de migration courants. Chacun de ces exemples comprend des informations générales et des scénarios de déploiement détaillés qui illustrent comment configurer une infrastructure de migration et évaluer l’adéquation des ressources locales pour la migration. D’autres articles seront ajoutés à cette section au fil du temps.

![Projets courants de migration/modernisation](./media/migration-patterns.png)

*Catégories de projets courants de migration et de modernisation.*

Les articles de la série sont résumés ci-dessous.

- Chaque scénario de migration est piloté par des objectifs métier légèrement différents, qui déterminent la stratégie de migration.
- Pour chaque scénario de déploiement, nous fournissons des informations sur les axes stratégiques et les objectifs, une proposition d’architecture, des étapes pour effectuer la migration,ainsi que des recommandations pour le nettoyage et des étapes à effectuer une fois la migration terminée.

### <a name="assessment"></a>Évaluation

**Article** | **Détails**
--- | ---
[Évaluer les ressources locales à migrer vers Azure](./contoso-migration-assessment.md) | Cet article explique comment exécuter l’évaluation d’une application locale s’exécutant sur VMware. Dans l’exemple, un exemple d’organisation évalue les machines virtuelles de l’application à l’aide du service Azure Migrate, et la base de données SQL Server de l’application à l’aide de l’Assistant Migration de données.

### <a name="infrastructure"></a>Infrastructure

**Article** | **Détails**
--- | ---
[Déployer une infrastructure Azure](./contoso-migration-infrastructure.md) | Cet article explique comment une organisation peut préparer son infrastructure locale et son infrastructure Azure pour la migration. L’exemple d’infrastructure établi dans cet article est référencé dans les autres exemples fournis dans cette section.

### <a name="windows-server-workloads"></a>Charges de travail Windows Server

**Article** | **Détails**
--- | ---
[Réhéberger une application sur des machines virtuelles Azure](./contoso-migration-rehost-vm.md) | Cet article fournit un exemple de migration de machines virtuelles d’applications locales vers des machines virtuelles Azure à l’aide du service Site Recovery.
[Réarchitecturer une application dans des conteneurs Azure et Azure SQL Database](./contoso-migration-rearchitect-container-sql.md) | Cet article fournit un exemple de migration d’une application tout en restructurant la couche web de l’application comme un conteneur Windows s’exécutant dans Azure Service Fabric, et la base de données avec Azure SQL Database.

### <a name="linux-workloads"></a>Charges de travail Linux

**Article** | **Détails**
--- | ---
[Réhéberger une application Linux sur des machines virtuelles Azure et Azure Database pour MySQL](./contoso-migration-rehost-linux-vm-mysql.md) | Cet article fournit un exemple de migration d’une application hébergée sur Linux vers des machines virtuelles Azure à l’aide de Site Recovery. La société migre la base de données d’application vers Azure Database pour MySQL à l’aide de MySQL Workbench.
[Réhéberger une application Linux sur des machines virtuelles Azure](./contoso-migration-rehost-linux-vm.md) | Cet exemple explique comment effectuer une migration lift-and-shift d’une application Linux vers des machines virtuelles Azure à l’aide du service Site Recovery.

### <a name="sql-server-workloads"></a>Charges de travail SQL Server

**Article** | **Détails**
--- | ---
[Réhéberger une application sur une machine virtuelle Azure et SQL Database Managed Instance](./contoso-migration-rehost-vm-sql-managed-instance.md) | Cet article fournit un exemple de migration lift-and-shift vers Azure pour une application locale. Cela implique la migration de la machine virtuelle frontale de l’application à l’aide d’[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview), et la base de données de l’application vers une instance Azure SQL Database Managed Instance à l’aide d’[Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview).
[Réhéberger une application sur des machines virtuelles Azure et dans un groupe de disponibilité SQL Server Always On](./contoso-migration-rehost-vm-sql-ag.md) | Cet exemple explique comment migrer une application et des données à l’aide de machines virtuelles SQL Server hébergées sur Azure. Il utilise Site Recovery pour migrer les machines virtuelles de l’application, et Azure Database Migration Service pour migrer la base de données de l’application vers un cluster SQL Server protégé par un groupe de disponibilité Always On.

### <a name="aspnet-php-and-java-apps"></a>Applications ASP.NET, PHP et Java

**Article** | **Détails**
--- | ---
[Refactoriser une application vers une application web Azure et Azure SQL Database](./contoso-migration-refactor-web-app-sql.md) | Cet exemple explique comment migrer une application Windows locale vers une application web Azure et la base de données de l’application vers une instance Azure SQL Server avec l’Assistant Migration de données.
[Refactoriser une application Linux vers plusieurs régions à l’aide d’Azure App Service, Azure Traffic Manager et Azure Database pour MySQL](./contoso-migration-refactor-linux-app-service-mysql.md) | Cet exemple explique comment migrer une application Linux locale vers une application web Azure dans plusieurs régions Azure à l’aide d’Azure Traffic Manager, intégré à GitHub de façon à assurer une livraison continue. La base de données de l’application est migrée vers une instance Azure Database pour MySQL.
[Régénérer une application dans Azure](./contoso-migration-rebuild.md) | Cet article fournit un exemple de régénération d’une application locale en utilisant une série de fonctionnalités et de services managés Azure, notamment Azure App Service, Azure Kubernetes Service (AKS), Azure Functions, Azure Cognitive Services et Azure Cosmos DB.
[Refactoriser Team Foundation Server sur Azure DevOps Services](./contoso-migration-tfs-vsts.md) | Cet article fournit un exemple de migration d’un déploiement local de Team Foundation Server vers Azure DevOps Services dans Azure.

### <a name="migration-scaling"></a>Mise à l’échelle de la migration

**Article** | **Détails**
--- | ---
[Mettre à l’échelle une migration vers Azure](./contoso-migration-scale.md) | Cet article explique comment un exemple d’organisation se prépare à mettre à l’échelle une migration complète vers Azure.

### <a name="demo-apps"></a>Applications de démonstration

Les articles d’exemples fournis dans cette section utilisent deux applications de démonstration : SmartHotel360 et osTicket.

- **SmartHotel360 :** cette application a été développée par Microsoft comme application de test que vous pouvez utiliser quand vous travaillez avec Azure. Elle est fournie en open source et vous pouvez la télécharger à partir de [GitHub](https://github.com/Microsoft/SmartHotel360). Il s’agit d’une application ASP.NET connectée à une base de données SQL Server. Dans les scénarios décrits dans ces articles, la version actuelle de cette application est déployée sur deux machines virtuelles VMware exécutant Windows Server 2008 R2 et SQL Server 2008 R2. Les machines virtuelles de l’application sont hébergées localement et managées par vCenter Server.
- **osTicket :** application open source de tickets pour Service Desk qui s’exécute sur Linux. Vous pouvez le télécharger à partir de [GitHub](https://github.com/osTicket/osTicket). Dans les scénarios décrits dans ces articles, la version actuelle de cette application est déployée localement sur deux machines virtuelles VMware exécutant Ubuntu 16.04 LTS et utilisant Apache 2, PHP 7.0 et MySQL 5.7.
