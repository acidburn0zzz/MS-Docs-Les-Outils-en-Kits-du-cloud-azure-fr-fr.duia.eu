---
title: Migrer les ressources
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migrer les ressources
author: matticusau
ms.author: mlavery
ms.date: 08/08/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: ce8338fbcd0e21cf0875a207633ce7c9ddf2ff9e
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818759"
---
# <a name="migrate-assets-infrastructure-apps-and-data"></a>Migrer des ressources (infrastructure, applications et données)

Pendant cette phase du parcours, vous utilisez la sortie de la phase d’évaluation pour initier la migration de l’environnement. Ce guide vous aide à identifier les outils appropriés pour atteindre un état « terminé », notamment les outils natifs, tiers et de gestion de projet.

# <a name="native-migration-toolstabtools"></a>[Outils de migration natifs](#tab/Tools)

Les sections suivantes décrivent les outils Azure natifs disponibles pour effectuer ou faciliter la migration. Afin d’obtenir des informations sur le choix des bons outils pour prendre en charge vos efforts de migration, consultez le [guide de décision sur les outils de migration du Framework d’adoption du cloud](../../decision-guides/migrate-decision-guide/index.md).

## <a name="azure-migrate"></a>Azure Migrate

Azure Migrate offre une expérience de migration unifiée et extensible. Azure Migrate offre une expérience dédiée et centralisée pour suivre votre parcours de migration à travers les phases d’évaluation et de migration vers Azure. Il vous offre la possibilité d’utiliser les outils de votre choix et de suivre la progression de la migration sur ces derniers.

Azure Migrate fournit les fonctionnalités suivantes :

1. Fonctionnalités d’évaluation et de migration améliorées :
    - Évaluations Hyper-V.
    - Évaluation VMware améliorée.
    - Migration sans agent de machines virtuelles VMware vers Azure.
1. Suivi unifié de l’évaluation, de la migration et de la progression.
1. Approche extensible avec intégration de fournisseurs de logiciel indépendant (tels que Cloudamize).

Pour effectuer une migration à l’aide de Azure Migrate, procédez comme suit :

1. Recherchez Azure Migrate sous **Tous les services**. Sélectionnez **Azure Migrate** pour continuer.
1. Sélectionnez **Ajouter un outil** pour commencer votre projet de migration.
1. Sélectionnez l’abonnement, le groupe de ressources et la zone géographique pour héberger la migration.
1. Sélectionnez **Sélectionner un outil d’évaluation** > **Azure Migrate : Server Assessment** >  **Suivant**.
1. Sélectionnez **Vérifier + ajouter des outils**, puis vérifiez la configuration. Cliquez sur **Ajouter des outils** pour lancer le travail afin de créer le projet de migration et d’enregistrer les solutions sélectionnées.

<!-- TODO: TBA -->

### <a name="read-more"></a>En savoir plus

- [Tutoriel Azure Migrate - Migrer des serveurs physiques ou virtualisés vers Azure](/azure/migrate/tutorial-migrate-physical-virtual-machines)

## <a name="azure-site-recovery"></a>Azure Site Recovery

Le service Azure Site Recovery peut gérer la migration de ressources locales vers Azure. Il peut également gérer et orchestrer la récupération d’urgence des machines locales et des machines virtuelles Azure à des fins de continuité d’activité et reprise d’activité (BCDR).

Les étapes suivantes décrivent le processus d’utilisation de Site Recovery pour migrer :

> [!TIP]
> Selon votre scénario, ces étapes peuvent différer légèrement. Pour plus d’informations, consultez l’article [Migrer des machines locales vers Azure](/azure/site-recovery/migrate-tutorial-on-premises-azure).

### <a name="prepare-azure-site-recovery-service"></a>Préparer le service Azure Site Recovery

1. Dans le Portail Azure, sélectionnez **+Créer une ressource > Outils de gestion > Sauvegarde et Site Recovery**.
1. Si vous n’avez pas encore créé de coffre de récupération, exécutez l’Assistant pour créer une ressource de **coffre Recovery Services**.
1. Dans le menu **Ressource**, sélectionnez **Site Recovery > Préparer l’infrastructure > Objectif de protection**.
1. Dans **Objectif de protection**, sélectionnez les composants à migrer.
    1. **VMware :** Sélectionnez **Vers Azure > Oui, avec hyperviseur VMware vSphere**.
    1. **Machine physique :** Sélectionnez **Vers Azure > Non virtualisé/Autre**.
    1. **Hyper-V :** Sélectionnez **Vers Azure > Oui, avec Hyper-V**. Si des machines virtuelles Hyper-V sont gérées par VMM, sélectionnez **Oui**.

### <a name="configure-migration-settings"></a>Configurer les paramètres de migration

1. Configurez l’environnement source comme il convient.
1. Configurez l’environnement cible.
    1. Cliquez sur **Préparer l’infrastructure > Cible**, puis sélectionnez l’abonnement Azure que vous souhaitez utiliser.
    1. Spécifiez le modèle de déploiement Resource Manager.
    1. Site Recovery vérifie que vous disposez d’un ou de plusieurs réseaux et comptes Azure Storage compatibles.
1. Configurer une stratégie de réplication.
1. Activez la réplication.
1. Exécutez une migration de test (test de basculement).

### <a name="migrate-to-azure-using-failover"></a>Migrer vers Azure à l’aide du basculement

1. Dans **Paramètres > Éléments répliqués**, sélectionnez la machine > **Basculement**.
1. Dans **Basculer**, sélectionnez un **point de récupération** vers lequel basculer. Sélectionnez le dernier point de récupération.
1. Configurez les paramètres de clé de chiffrement selon vos besoins.
1. Sélectionnez **Arrêter la machine avant de commencer le basculement**. Site Recovery tente d’arrêter les machines virtuelles avant de déclencher le basculement. Le basculement est effectué même en cas d’échec de l’arrêt. Vous pouvez suivre la progression du basculement sur la page Travaux.
1. Vérifiez que la machine virtuelle Azure s’affiche dans Azure comme prévu.
1. Dans **Éléments répliqués**, faites un clic droit sur la machine virtuelle et choisissez **Terminer la migration**.
1. Effectuez toutes les étapes post-migration requises (consultez les informations pertinentes dans ce guide).

::: zone target="chromeless"

::: form action="Create[#create/Microsoft.RecoveryServices]" submitText="Create a Recovery Services vault" :::

::: zone-end

::: zone target="docs"

Pour plus d'informations, consultez les pages suivantes :

- [Migrer des machines locales vers Azure](/azure/site-recovery/migrate-tutorial-on-premises-azure)

::: zone-end

## <a name="azure-database-migration-service"></a>Azure Database Migration Service

Azure Database Migration Service est un service complètement managé qui permet des migrations fluides de diverses sources de base de données vers des plateformes de données Azure avec un temps d’arrêt minime (migrations en ligne). Azure Database Migration Service effectue toutes les étapes requises. Vous pouvez lancer vos projets de migration avec l’assurance que le processus tire parti des meilleures pratiques recommandées par Microsoft.

### <a name="create-an-azure-database-migration-service-instance"></a>Créer une instance Azure Database Migration Service

S’il s’agit de la première fois que vous utilisez Azure Database Migration Service, vous devez inscrire le fournisseur de ressources pour votre abonnement Azure :

1. Sélectionnez **Tous les services**, puis **Abonnements** et choisissez l’abonnement cible.
1. Sélectionnez **Fournisseurs de ressources**.
1. Recherchez `migration`, puis à droite de **Microsoft.DataMigration**, sélectionnez **Inscrire**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to Subscriptions" :::

::: zone-end

Une fois que vous avez inscrit le fournisseur de ressources, vous pouvez créer une instance Azure Database Migration Service.

1. Sélectionnez **+Créer une ressource** et recherchez **Azure Database Migration Service** dans la marketplace.
1. Exécutez l’Assistant **Créer un service de migration**,puis sélectionnez **Créer**.

Le service est maintenant prêt à migrer les bases de données sources prises en charge (par exemple, SQL Server, MySQL, PostgreSQL ou MongoDb).

::: zone target="chromeless"

::: form action="Create[#create/Microsoft.AzureDMS]" submitText="Create an Azure Database Migration Service instance" :::

::: zone-end

::: zone target="docs"

Pour plus d'informations, consultez les pages suivantes :

- [Vue d’ensemble d’Azure Database Migration Service](/azure/dms/dms-overview)
- [Créer une instance Azure Database Migration Service](/azure/dms/quickstart-create-data-migration-service-portal)
- [Azure Migrate dans le Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade)
- [Portail Azure : Créer un projet de migration](https://portal.azure.com/#create/Microsoft.AzureMigrate)

::: zone-end

## <a name="data-migration-assistant"></a>Assistant Migration de données

L’Assistant Migration de données (DMA) vous aide à effectuer une mise à niveau vers une plateforme de données moderne en détectant les problèmes de compatibilité pouvant nuire aux fonctionnalités des bases de données dans votre nouvelle version de SQL Server ou d’Azure SQL Database. DMA recommande des améliorations en matière de fiabilité et de niveau de performance pour votre environnement cible et vous permet de déplacer votre schéma, vos données et vos objets sans contenant de votre serveur source vers votre serveur cible.

> [!NOTE]
> Pour les migrations volumineuses (en termes de nombre et de taille de bases de données), nous vous recommandons d’utiliser Azure Database Migration Service, qui peut migrer des bases de données à l’échelle.
>

Pour prendre en main l’Assistant Migration de données, procédez comme suit.

1. Téléchargez et installez l’Assistant Migration de données à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53595).
1. Créez une évaluation en cliquant sur l’icône **Nouveau (+)** et sélectionnez le type de projet **Évaluation**.
1. Définissez le type de serveur source et cible. Cliquez sur **Créer**.
1. Configurez les options d’évaluation selon vos besoins (nous vous recommandons toutes les valeurs par défaut).
1. Ajoutez les bases de données à évaluer.
1. Cliquez sur **Suivant** pour démarrer l’évaluation.
1. Affichez les résultats dans l’ensemble d’outils de l’Assistant Migration de données.

Pour une entreprise, nous vous recommandons de suivre l’approche décrite dans [Évaluer une entreprise et consolider les rapports d’évaluation à l’aide du DMA](/sql/dma/dma-consolidatereports) pour évaluer plusieurs serveurs, combiner les rapports, puis utiliser les rapports de Power BI fournis pour analyser les résultats.

Pour plus d’informations, notamment sur les étapes d’utilisation détaillées, consultez :

- [Vue d’ensemble de l’Assistant Migration de données](/sql/dma/dma-overview)
- [Évaluer une entreprise et consolider les rapports d’évaluation à l’aide de DMA](/sql/dma/dma-consolidatereports)
- [Analyser les rapports d’évaluation consolidés créés par l’Assistant Migration de données grâce à Power BI](/sql/dma/dma-powerbiassesreport)

## <a name="sql-server-migration-assistant"></a>Assistant Migration SQL Server

L’assistant Migration SQL Server de Microsoft (SSMA) est un outil conçu pour automatiser la migration de base de données vers SQL Server à partir de Microsoft Access, DB2, MySQL, Oracle et SAP ASE. Le concept général consiste à collecter, évaluer et examiner à l’aide de ces outils. Toutefois, en raison des écarts dans le processus pour chacun des systèmes sources, nous vous recommandons de consulter la [documentation détaillée de l’Assistant Migration SQL Server](/sql/ssma/sql-server-migration-assistant).

Pour plus d'informations, consultez les pages suivantes :

- [Vue d’ensemble de l’Assistant Migration SQL Server](/sql/ssma/sql-server-migration-assistant)

## <a name="database-experimentation-assistant"></a>Assistant Expérimentation de base de données

L’Assistant Expérimentation de base de données (DEA) est une nouvelle solution de test A/B pour les mises à niveau SQL Server. Il vous aidera à évaluer une version ciblée de SQL pour une charge de travail donnée. Les clients qui sont en cours de mise à niveau à partir de versions antérieures de SQL Server (SQL Server 2005 et versions ultérieures) vers une nouvelle version de SQL Server peuvent utiliser ces métriques d’analyse.

L’Assistant Expérimentation de base de données contient les activités de flux de travail suivantes :

- **Capture :** La première étape d’un test A/B SQL Server consiste à capturer une trace sur votre serveur source. Le serveur source est généralement le serveur de production.
- **Relecture :** La deuxième étape d’un test A/B SQL Server consiste à relire le fichier de trace qui a été capturé sur vos serveurs cibles. Ensuite, collectez des traces étendues à partir des relectures à des fins d’analyse.
- **Analyse :** La dernière étape consiste à générer un rapport d’analyse à l’aide des traces de relecture. Le rapport d’analyse peut vous aider à mieux comprendre les répercussions du changement proposé sur le niveau de performance.

Pour plus d'informations, consultez les pages suivantes :

- [Vue d’ensemble de l’Assistant Expérimentation de base de données](/sql/dea/database-experimentation-assistant-overview)

# <a name="third-party-migration-toolstabthird-party-tools"></a>[Outils de migration tiers](#tab/third-party-tools)

Plusieurs outils de migration tiers et services de fournisseur de logiciel indépendant (ISV) peuvent vous aider dans le processus de migration. Chacun offre des avantages et des points forts différents. Ces outils incluent :

## <a name="cloudamize"></a>Cloudamize

Cloudamize est un service ISV qui couvre toutes les phases de la stratégie de migration.

[En savoir plus](https://www.cloudamize.com)

## <a name="zerto"></a>Zerto

Zerto fournit une réplication virtuelle qui gère à la fois les environnements Microsoft Hyper-V et VMware vSphere.

[En savoir plus](https://www.zerto.com/solutions/use-cases/data-center-migration-software)

## <a name="carbonite"></a>Carbonite

Carbonite fournit des solutions de migration de serveur et de données pour migrer des charges de travail vers, depuis ou entre des environnements physiques, virtuels ou informatiques.

[En savoir plus](https://www.carbonite.com/data-protection/data-migration-software)

## <a name="movere"></a>Movere

Movere est une solution de détection qui fournit les données et les insights nécessaires pour planifier des migrations cloud et optimiser, surveiller et analyser de manière continue les environnements informatiques en toute confiance.

[En savoir plus](https://www.movere.io)

Consultez le [Centre de migration Azure](https://azure.microsoft.com/migration/support) pour découvrir les organisations qui proposent des solutions technologiques partenaires prêtes à l’emploi pour répondre à vos scénarios de migration et en savoir plus sur d’autres outils de migration et services de support fournis par des tiers.

# <a name="project-management-toolstabproject-management-tools"></a>[Outils de gestion de projet](#tab/project-management-tools)

Les projets qui ne sont pas suivis et gérés sont plus susceptibles de rencontrer des problèmes. Pour garantir un résultat réussi, nous pensons qu’il est important d’utiliser un outil de gestion de projet. De nombreux outils différents sont disponibles et les chefs de projet de votre organisation peuvent déjà avoir leur favori. Microsoft propose les outils de gestion de projet suivants, qui peuvent fonctionner ensemble pour fournir des fonctionnalités plus larges :

- [Microsoft Planner](https://tasks.office.com) : Moyen simple et visuel d’organiser le travail d’équipe.
- [Microsoft Project](https://products.office.com/project/project-and-portfolio-management-software) : Gestion de projets et de portefeuilles, gestion de la capacité des ressources, gestion financière, gestion des feuilles de présence et des calendriers.
- [Microsoft Teams](https://products.office.com/microsoft-teams) : Outil de collaboration et de communication pour les équipes. Teams intègre également Planner et d’autres outils pour améliorer la collaboration.
- [Azure DevOps](https://dev.azure.com) : À l’aide d’Azure DevOps, vous pouvez gérer votre infrastructure sous forme de code ou utiliser les éléments de travail et les tableaux pour gérer les projets. À mesure que vous gagnez en expérience, votre organisation peut tirer parti des fonctionnalités CI/CD.

Ce ne sont pas les seuls outils disponibles. De nombreux autres outils tiers sont largement utilisés dans la communauté de gestion de projet.

## <a name="set-up-for-devops"></a>Configurer pour DevOps

À mesure que vous migrez vers les technologies cloud, vous avez la possibilité de configurer votre organisation pour DevOps et CI/CD. Même si votre organisation gère uniquement l’infrastructure, lorsque vous commencez à gérer votre infrastructure sous forme de code et à utiliser les modèles et pratiques du secteur pour DevOps, vous pouvez commencer à augmenter votre agilité par le biais des pipelines CI/CD. Cela vous permet de vous adapter plus rapidement aux scénarios de modification, de croissance, de mise en production et même de récupération.

[Azure DevOps](https://dev.azure.com) fournit toutes les fonctionnalités et l’intégration requises avec Azure, localement ou même d’autres clouds. Découvrez-en plus [ici](https://azure.microsoft.com/services/devops). Pour une formation guidée, consultez [CI et CD avec Azure DevOps – Démarrage rapide](https://microsoft.github.io/PartsUnlimited/pandp/200.1x-PandP-CICDQuickstartwithVSTS.html).

# <a name="cost-managementtabmanagecost"></a>[Gestion des coûts](#tab/ManageCost)

Lorsque vous migrez des ressources vers votre environnement cloud, il est important d’analyser régulièrement les coûts. Cela vous permet d’éviter des frais d’utilisation inattendus, car le processus de migration peut imposer des conditions d’utilisation supplémentaires sur vos services. Vous pouvez également redimensionner les ressources, le cas échéant, pour équilibrer le coût et la charge de travail (sujet abordé plus en détail dans la section **[Optimisation et transformation](optimize-and-transform.md)** ).
