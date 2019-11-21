---
title: Évaluer le patrimoine numérique
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Évaluer le patrimoine numérique
author: matticusau
ms.author: mlavery
ms.date: 08/08/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 31e76ec1f81bc38b03e8f1e480d083983dc85b14
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251418"
---
# <a name="assess-the-digital-estate"></a>Évaluer le patrimoine numérique

Dans une migration idéale, chaque ressource (infrastructure, application ou données) est compatible avec une plateforme cloud et prête pour la migration. En réalité, tous les éléments n’ont pas besoin d’être migrés vers le cloud. En outre, toutes les ressources ne sont pas compatibles avec les plateformes cloud. Avant de migrer une charge de travail vers le cloud, il est important d’évaluer la charge de travail et chaque ressource associée (infrastructure, applications et données).

Les ressources de cette section vous aideront à évaluer votre environnement afin de déterminer s’il convient à la migration et quelles sont les méthodes à envisager.

<!-- markdownlint-disable MD025 -->

# <a name="toolstabtools"></a>[outils](#tab/Tools)

Les outils suivants vous aident à évaluer votre environnement pour déterminer la pertinence de la migration et la meilleure approche à utiliser. Afin d’obtenir des informations utiles sur le choix des bons outils pour prendre en charge vos efforts de migration, consultez le [guide de décision sur les outils de migration du Framework d’adoption du cloud](../../decision-guides/migrate-decision-guide/index.md).

## <a name="azure-migrate"></a>Azure Migrate

Le service Azure Migrate évalue l’infrastructure, les applications et les données locales pour la migration vers Azure. Le service évalue la pertinence de la migration des ressources locales, effectue le dimensionnement en fonction des niveaux de performance et fournit des estimations de coût pour l’exécution des ressources locales dans Azure. Si vous envisagez d’effectuer des migrations lift-and-shift ou si vous êtes dans les premières étapes de l’évaluation de la migration, ce service vous correspond. Une fois l’évaluation terminée, Azure Migrate peut être utilisé pour effectuer la migration.

![Vue d’ensemble d’Azure Migrate](./media/assess/azuremigrate-overview-1.png)

### <a name="create-a-new-server-migration-project"></a>Créer un projet de migration de serveur

Pour commencer par une évaluation de la migration de serveur à l’aide d’Azure Migrate, procédez comme suit :

1. Sélectionnez **Azure Migrate**.
1. Dans **Vue d’ensemble**, cliquez sur **Évaluer et migrer des serveurs**.
1. Sélectionnez **Ajouter des outils**.
1. Dans **Découvrir, évaluer et migrer des serveurs**, cliquez sur **Ajouter des outils**.
1. Dans **Projet de migration**, sélectionnez votre abonnement Azure, puis créez un groupe de ressources si vous n’en avez pas.
1. Dans **Détails du projet**, spécifiez le nom du projet et la géographie dans laquelle vous souhaitez créer le projet, puis cliquez sur **Suivant**.
1. Dans **Sélectionner un outil d’évaluation**, sélectionnez **Ignorer l’ajout d’un outil d’évaluation pour l’instant > Suivant**.
1. Dans **Sélectionner un outil de migration**, sélectionnez **Azure Migrate : Migration de serveur > Suivant**.
1. Dans **Vérifier + ajouter des outils**, passez en revue les paramètres, puis cliquez sur **Ajouter des outils**.
1. L’outil ajouté apparaît alors dans le projet **Azure Migrate > Serveurs > Outils de migration**.

::: zone target="chromeless"

::: form action="Blade[#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview]" submitText="Assess and migrate servers" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>En savoir plus

- [Vue d’ensemble d’Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview)
- [Migrer des serveurs physiques ou virtualisés vers Azure](https://docs.microsoft.com/azure/migrate/tutorial-migrate-physical-virtual-machines)
- [Azure Migrate dans le Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview)

::: zone-end

## <a name="service-map"></a>Service Map

La solution Service Map détecte automatiquement les composants d’application sur les systèmes Windows et Linux, et mappe la communication entre les services. Elle vous permet d’afficher vos serveurs comme vous les imaginez, en tant que systèmes interconnectés fournissant des services critiques. Elle affiche les connexions entre serveurs, les processus, la latence des connexions entrantes et sortantes, ainsi que les ports au sein de toute architecture TCP connectée, sans nécessiter de configuration autre que l’installation d’un agent.

Azure Migrate utilise Service Map pour améliorer les fonctionnalités de création de rapports et les dépendances dans l’environnement. Les détails complets de cette intégration sont décrits dans [Visualisation des dépendances](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization). Si vous utilisez le service Azure Migration, aucune étape supplémentaire n’est requise pour configurer Service Map et obtenir ses avantages. Les instructions suivantes sont fournies à titre de référence si vous souhaitez utiliser des Service Map à d’autres fins ou pour d’autres projets.

### <a name="enable-dependency-visualization-using-service-map"></a>Activer la visualisation des dépendances à l’aide de Service Map

Pour utiliser la visualisation des dépendances, vous devez télécharger et installer des agents sur chaque machine locale que vous souhaitez analyser.

- [Microsoft Monitoring Agent (MMA)](https://docs.microsoft.com/azure/log-analytics/log-analytics-agent-windows) doit être installé sur chaque machine.
- [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud#install-the-dependency-agent-on-windows) doit être installé sur chaque machine.
- En outre, si certaines de vos machines sont dépourvues de connexion Internet, vous devez télécharger et installer la passerelle Log Analytics sur ces machines.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>En savoir plus

- [Utilisation de la solution Service Map dans Azure](https://docs.microsoft.com/azure/azure-monitor/insights/service-map)
- [Azure Migrate et Service Map : Visualisation des dépendances](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization)

# <a name="scenarios-and-stakeholderstabscenarios"></a>[Scénarios et parties prenantes](#tab/Scenarios)

## <a name="scenarios"></a>Scénarios

Ce guide se concentre sur les scénarios suivants :

- **Matériel hérité :** Vous effectuez une migration pour supprimer une dépendance sur un matériel hérité proche de la fin du support ou de la fin de vie.
- **Croissance de la capacité :** Vous devez augmenter la capacité des ressources (infrastructure, applications et données), ce que votre infrastructure actuelle ne peut pas fournir.
- **Modernisation du centre de données :** Vous devez étendre ou moderniser votre centre de données avec la technologie cloud pour vous assurer que votre entreprise reste à jour et compétitive.
- **Modernisation d’application ou de service :** Vous souhaitez mettre à jour vos applications pour tirer parti d’une fonctionnalité cloud native. Même si une stratégie de migration en réhébergement est votre objectif initial, la possibilité de créer des plans pour la révision des application ou services et la modernisation potentielle est un processus courant dans toutes les migrations.

### <a name="organizational-alignment-and-stakeholders"></a>Alignement organisationnel et parties prenantes

La liste complète des parties prenantes varie selon les projets de migration. Il est préférable de supposer que vous ne connaissez pas toutes les parties prenantes au début de la planification d’une migration, puisque les parties prenantes ne sont souvent identifiées que lors de certaines phases du projet. Toutefois, avant de démarrer des projets de migration, vous pouvez identifier les principaux dirigeants d’entreprise à partir du service des finances, de l’infrastructure informatique et des groupes d’applications qui auront un intérêt dans les efforts globaux de migration cloud de votre organisation.

La mise en place d’une équipe centrale de stratégie cloud, construite autour de ces principales parties prenantes de haut niveau, peut vous aider à préparer votre organisation à l’adoption du cloud et à guider l’ensemble de vos efforts de migration cloud. Cette équipe est chargée de comprendre les technologies cloud et les processus de migration, d’identifier la justification métier des migrations et de déterminer les meilleures solutions de haut niveau pour les efforts de migration. Elle aide également à identifier des applications et des parties prenantes spécifiques et à travailler avec elles pour garantir la réussite de la migration.

Pour plus d’informations sur la façon de préparer votre organisation aux efforts de migration cloud, consultez l’article du Framework d’adoption du cloud sur [l’alignement initial de l’organisation](../../plan/initial-org-alignment.md).

# <a name="timelinestabtimelines"></a>[Chronologies](#tab/Timelines)

D’une manière générale, les clients estiment que le scénario de migration couvert par ce guide peut être réalisé en un à six mois.

Voici quelques-uns des facteurs à prendre en compte lors de l’évaluation de la chronologie de votre migration :

- **Ressources (infrastructure, applications et données) à migrer :** Le nombre et la diversité des ressources.
- **Préparation du personnel :** Votre équipe est-elle prête à gérer le nouvel environnement ou a-t-elle besoin d’une formation ?
- **Financement :** Disposez-vous de l’approbation et du budget appropriés pour mener à bien la migration ?
- **Gestion des changements :** Votre entreprise a-t-elle des exigences spécifiques concernant l’implémentation et l’approbation des modifications ?
- **Réglementations sectorielles :** Devez-vous vous conformer aux réglementations du segment ou secteur d’activité ?

# <a name="cost-managementtabmanagecost"></a>[Cost Management](#tab/ManageCost)

L’évaluation de votre environnement est l’occasion idéale d’inclure une étape d’analyse des coûts. À l’aide des données collectées par les activités d’évaluation, vous devez être en mesure d’analyser et de prédire les coûts. Cette prédiction des coûts doit tenir compte à la fois des coûts du service de consommation et des coûts ponctuels (tels que l’augmentation de l’entrée de données).

Pendant la migration, plusieurs facteurs peuvent influencer les décisions et les activités d’exécution :

- **Taille du patrimoine numérique :** Comprendre la taille de votre patrimoine numérique aura un impact direct sur les décisions et les ressources requises pour effectuer la migration.
- **Modèles de comptabilité :** Passage d’un modèle structuré des dépenses d’investissement à un modèle fluide des dépenses d’exploitation.

::: zone target="docs"

Les ressources suivantes fournissent des informations connexes :

- [Estimer les coûts du cloud](../migration-considerations/assess/estimate.md)

::: zone-end
