---
title: Évaluer chaque charge de travail et affiner les plans
description: Cette section du guide de migration Azure vous aide à évaluer votre environnement en vue de déterminer ce qui doit faire l’objet d’une migration et quelles méthodes utiliser pour cette migration.
author: matticusau
ms.author: mlavery
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 40e62a05101e14fcd7507011d521521e58920ffc
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78225554"
---
# <a name="assess-each-workload-and-refine-plans"></a>Évaluer chaque charge de travail et affiner les plans

Les ressources de ce guide vous aideront à évaluer chaque charge de travail, à vérifier les hypothèses concernant la pertinence de la migration de chaque charge de travail, ainsi qu’à finaliser les décisions architecturales à propos des options de migration.

<!-- markdownlint-disable MD025 -->

# <a name="tools"></a>[outils](#tab/Tools)

Si vous n’avez pas suivi les instructions des liens ci-dessus, vous aurez probablement besoin de données et d’un outil d’évaluation afin de prendre des décisions de migration éclairées. Azure Migrate est l’outil natif qui permet d’évaluer **et** d’effectuer la migration vers Azure. Si ce n’est déjà fait, effectuez les étapes suivantes pour créer un projet de migration de serveur et collecter les données nécessaires.

## <a name="azure-migrate"></a>Azure Migrate

Azure Migrate évalue l’infrastructure, les applications et les données locales pour la migration vers Azure. Ce service :

- Évalue la pertinence de la migration des ressources locales
- Effectue un dimensionnement en fonction des performances
- Fournit des estimations de coût pour l’exécution des ressources locales dans Azure

Si vous envisagez d’utiliser la méthode lift-and-shift, ou si vous en êtes aux premières étapes de l’évaluation de la migration, ce service est fait pour vous. Une fois l’évaluation terminée, utilisez Azure Migrate pour effectuer la migration.

![Vue d’ensemble d’Azure Migrate](./media/assess/azure-migrate-overview-1.png)

### <a name="create-a-new-server-migration-project"></a>Créer un projet de migration de serveur

Pour commencer l’évaluation de la migration de serveur à l’aide d’Azure Migrate, effectuez les étapes suivantes :

1. Sélectionnez **Azure Migrate**.
1. Dans **Vue d’ensemble**, sélectionnez **Évaluer et migrer des serveurs**.
1. Sélectionnez **Ajouter des outils**.
1. Dans **Découvrir, évaluer et migrer des serveurs**, sélectionnez **Ajouter des outils**.
1. Dans **Projet de migration**, sélectionnez votre abonnement Azure, puis créez un groupe de ressources si vous n’en avez pas.
1. Dans **Détails du projet**, spécifiez le nom du projet et l’emplacement auquel vous souhaitez créer le projet, puis sélectionnez **Suivant**.
1. Dans **Sélectionner un outil d’évaluation**, sélectionnez **Ignorer l’ajout d’un outil d’évaluation pour l’instant > Suivant**.
1. Dans **Sélectionner un outil de migration**, sélectionnez **Azure Migrate : Migration de serveur > Suivant**.
1. Dans **Vérifier + ajouter des outils**, passez en revue les paramètres, puis sélectionnez **Ajouter des outils**.
1. L’outil ajouté s’affiche alors dans le projet **Azure Migrate > Serveurs > Outils de migration**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview]" submitText="Assess and migrate servers" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>En savoir plus

- [Vue d’ensemble d’Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview)
- [Migrer des serveurs physiques ou virtualisés vers Azure](https://docs.microsoft.com/azure/migrate/tutorial-migrate-physical-virtual-machines)
- [Azure Migrate dans le Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview)

::: zone-end

## <a name="service-map"></a>Service Map

La solution Service Map détecte automatiquement les composants d’application sur les systèmes Windows et Linux, et mappe la communication entre les services. Elle vous permet d’afficher vos serveurs comme vous les imaginez, en tant que systèmes interconnectés fournissant des services critiques. Elle affiche les connexions entre serveurs, les processus, la latence des connexions entrantes et sortantes, ainsi que les ports au sein de toute architecture TCP connectée, sans nécessiter de configuration autre que l’installation d’un agent.

Azure Migrate utilise Service Map pour améliorer les fonctionnalités de création de rapports et les dépendances dans l’environnement. Les détails complets de cette intégration sont décrits dans [Visualisation des dépendances](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization). Si vous utilisez le service Azure Migration, aucune étape supplémentaire n’est nécessaire pour configurer Service Map et bénéficier de ses avantages. Les instructions suivantes sont fournies à titre de référence, dans le cas où vous souhaiteriez utiliser des Service Map à d’autres fins ou pour d’autres projets.

### <a name="enable-dependency-visualization-using-service-map"></a>Activer la visualisation des dépendances à l’aide de Service Map

Pour utiliser la visualisation des dépendances, téléchargez et installez des agents sur chaque machine locale que vous souhaitez analyser.

- [Microsoft Monitoring agent (MMA)](https://docs.microsoft.com/azure/log-analytics/log-analytics-agent-windows) doit être installé sur chaque machine.
- [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud#install-the-dependency-agent-on-windows) doit être installé sur chaque machine.
- En outre, si certaines de vos machines sont dépourvues de connexion Internet, téléchargez et installez la passerelle Log Analytics sur ces machines.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>En savoir plus

- [Utilisation de la solution Service Map dans Azure](https://docs.microsoft.com/azure/azure-monitor/insights/service-map)
- [Azure Migrate et Service Map : Visualisation des dépendances](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization)

# <a name="challenge-assumptions"></a>[Vérifier les hypothèses](#tab/Challenge-Assumptions)

Dans une migration idéale, chaque ressource (infrastructure, application ou données) serait compatible avec une plateforme cloud et prête pour une migration ou une modernisation. En réalité, toutes les charges de travail ne doivent pas faire l’objet d’une migration vers le cloud. En effet, toutes les ressources ne sont pas compatibles avec les plateformes cloud. Avant d’effectuer la migration d’une charge de travail vers le cloud, évaluez chaque charge de travail et toutes les ressources associées (infrastructure, applications et données).

La [méthodologie de planification du Cloud Adoption Framework](../../plan/index.md) conseille aux lecteurs d’utiliser la méthode de [rationalisation incrémentielle](../../digital-estate/rationalize.md#incremental-rationalization) et la méthode [Puissance 10](../../digital-estate/rationalize.md#release-planning) pour évaluer et planifier la migration. Ce guide indique également une méthode recommandée expliquée en détail concernant l’[utilisation d’Azure Migrate pour évaluer votre patrimoine numérique](../../plan/contoso-migration-assessment.md).

Les liens ci-dessus suggèrent que les hypothèses sont acceptables et qu’elles sont souvent encouragées pendant les étapes de planification de la migration. Mais maintenant, il est temps d’agir. Ces hypothèses doivent être vérifiées pour chacune des charges de travail avant la migration vers le cloud.

## <a name="two-steps-of-incremental-rationalization"></a>Deux étapes de rationalisation incrémentielle

Deux étapes pondérées de façon égale sont nécessaires à la [rationalisation incrémentielle](../../digital-estate/rationalize.md#incremental-rationalization). Ces deux étapes nécessitent des données et des insights concernant l’environnement. Toutefois, chaque méthode respecte la durée et la précision nécessaires à la réussite de la migration.

- **[Planification de type Puissance 10](../../digital-estate/rationalize.md#release-planning) :** lors de la première rationalisation et de la première planification de la mise en production, seul l’un des [5 R de la rationalisation](../../digital-estate/5-rs-of-rationalization.md) doit être utilisé lors de l’évaluation. Estimez et planifiez en fonction de l’option de rationalisation qui correspond le mieux aux motivations globales définies dans le [document relatif aux stratégies d’adoption du cloud](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).

- **Évaluation détaillée de chaque charge de travail :** les hypothèses associées à la planification de type Puissance 10 sont suffisamment acceptables pour créer un plan. Toutefois, ces mêmes hypothèses peuvent entraîner des problèmes importants si elles ne sont pas évaluées avant la migration.

## <a name="challenge-assumptions-and-update-the-plan"></a>Vérifier les hypothèses et mettre à jour le plan

Examinez attentivement les données d’évaluation dans Azure Migrate ou dans l’outil d’évaluation choisi. Ces données fournissent des insights sur les problèmes de compatibilité, les corrections nécessaires, les suggestions de dimensionnement et d’autres considérations.

Avant la migration, utilisez ces données, ainsi que les conversations concernant la découverte que vous avez eues avec le chef produit, les équipes de développement, les administrateurs et les autres personnes impliquées, afin d’évaluer la faisabilité de la migration d’une charge de travail. Utilisez ces éléments de découverte pour vérifier les principales hypothèses concernant cette charge de travail. Si les résultats nécessitent la modification du plan de migration ou d’adoption, mettez à jour le plan en conséquence.

La première étape de cette vérification consiste à [passer en revue les 5 R](../../digital-estate/rationalize.md).

    - La méthode de rationalisation supposée est-elle compatible avec cette charge de travail ? S’agit-il de la meilleure méthode ?
    - La migration de cette charge de travail sera-t-elle impactée par l’une des [lois de réplication](../migration-considerations/migrate/replicate.md#replication-risks---physics-of-replication) ?
    - Cette charge de travail nécessite-t-elle des [activités de correction](../migration-considerations/assess/evaluate.md) avant la migration ?

Ces types de questions permettent de vérifier les hypothèses et de prendre la meilleure décision pour chaque charge de travail.

Pour obtenir la liste complète des questions, ainsi qu’un processus établi pour la validation des hypothèses, consultez [Vue d’ensemble des améliorations du processus d’évaluation](../migration-considerations/assess/index.md).

# <a name="scenarios-and-stakeholders"></a>[Scénarios et parties prenantes](#tab/Scenarios)

## <a name="scenarios"></a>Scénarios

Ce guide aborde les scénarios suivants :

- **Matériel hérité :** effectuez une migration pour supprimer une dépendance à un matériel hérité proche de la fin du support ou de la fin de vie.
- **Croissance de la capacité :** augmentez la capacité des ressources (infrastructure, applications et données), ce que votre infrastructure actuelle ne permet pas.
- **Modernisation du centre de données :** étendez ou modernisez votre centre de données avec la technologie cloud pour que votre entreprise reste à jour et compétitive.
- **Modernisation d’application ou de service :** mettez à jour vos applications pour tirer parti d’une fonctionnalité cloud native. Même si votre objectif premier est de réhéberger la stratégie de migration, la création de plans pour la révision des applications ou des services et pour une modernisation potentielle est un processus courant dans toutes les migrations.

### <a name="organizational-alignment-and-stakeholders"></a>Alignement organisationnel et parties prenantes

La liste complète des parties prenantes varie selon les projets de migration. Il est préférable de supposer que vous ne connaissez pas toutes les parties prenantes au début de la planification d’une migration, puisque les parties prenantes ne sont souvent identifiées que lors de certaines phases du projet. Toutefois, avant de démarrer des projets de migration, identifiez les principaux responsables du service des finances, du service informatique et des groupes d’applications qui sont impliqués dans les efforts globaux de migration cloud de votre organisation.

La mise en place d’une équipe centrale de stratégie cloud, construite autour de ces principales parties prenantes de haut niveau, peut vous aider à préparer votre organisation à l’adoption du cloud et à guider l’ensemble de vos efforts de migration cloud. Cette équipe est chargée de comprendre les technologies cloud et les processus de migration, d’identifier la justification métier des migrations et de déterminer les meilleures solutions de haut niveau pour les efforts de migration. Elle aide également à identifier des applications et des parties prenantes spécifiques et à travailler avec elles pour garantir la réussite de la migration.

Pour plus d’informations sur la préparation de votre organisation aux efforts de migration cloud, consultez les instructions du Cloud Adoption Framework concernant l’[alignement initial de l’organisation](../../plan/initial-org-alignment.md).

# <a name="timelines"></a>[Chronologies](#tab/Timelines)

D’une manière générale, les clients estiment que le scénario de migration couvert par ce guide peut être réalisé en un à six mois.

Voici quelques-uns des facteurs à prendre en compte lors de l’évaluation de la chronologie de votre migration :

- **Ressources (infrastructure, applications et données) à migrer :** Le nombre et la diversité des ressources.
- **Préparation du personnel :** Votre équipe est-elle prête à gérer le nouvel environnement ou a-t-elle besoin d’une formation ?
- **Financement :** Disposez-vous de l’approbation et du budget appropriés pour mener à bien la migration ?
- **Gestion des changements :** Votre entreprise a-t-elle des exigences spécifiques concernant l’implémentation et l’approbation des modifications ?
- **Réglementations sectorielles :** Devez-vous vous conformer aux réglementations du segment ou secteur d’activité ?

# <a name="cost-management"></a>[Gestion des coûts](#tab/ManageCost)

L’évaluation de votre environnement est l’occasion d’effectuer une analyse des coûts. Avec les données collectées par les activités d’évaluation, vous devez être en mesure d’analyser et de prédire les coûts. Cette prédiction des coûts doit tenir compte à la fois des coûts du service de consommation et des coûts ponctuels (tels que l’augmentation de l’entrée de données).

Pendant la migration, plusieurs facteurs peuvent influencer les décisions et les activités d’exécution :

- **Taille du patrimoine numérique :** Comprendre la taille de votre patrimoine numérique aura un impact direct sur les décisions et les ressources requises pour effectuer la migration.
- **Modèles de comptabilité :** Passage d’un modèle structuré des dépenses d’investissement à un modèle fluide des dépenses d’exploitation.

::: zone target="docs"

Les ressources suivantes fournissent des informations connexes :

- [Estimer les coûts du cloud](../migration-considerations/assess/estimate.md)

::: zone-end
