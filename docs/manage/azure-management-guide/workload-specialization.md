---
title: Charges de travail spécialisées pour la gestion cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin d’en savoir plus sur les opérations spécialisées de gestion cloud des charges de travail.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: e2eac3d49f38a8b15ed822e177afb224afa20270
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80356435"
---
# <a name="workload-specialization-for-cloud-management"></a>Spécialisation de la charge de travail pour la gestion cloud

La spécialisation de la charge de travail repose sur les concepts décrits dans [Spécialisation de la charge de travail](./platform-specialization.md).

![Au-delà de la base de référence de gestion cloud](../../_images/manage/beyond-the-baseline.png)

- **Opérations de charge de travail :** L'investissement par charge de travail le plus important et le plus haut degré de résilience. Nous recommandons de mettre en place des opérations de charge de travail pour environ 20 % des charges de travail qui pilotent la valeur commerciale. Cette spécialisation est généralement réservée aux charges de travail très importantes ou critiques.
- **Opérations de plateforme :** Les investissements opérationnels sont répartis sur de nombreuses charges de travail. Les améliorations de la résilience affectent toutes les charges de travail qui utilisent la plateforme définie. Nous recommandons de mettre en place des opérations de plateformes pour environ 20 % des plateformes les plus importantes. Cette spécialisation est généralement réservée aux charges de travail de niveau moyen ou critique.
- **Base de référence de gestion améliorée :** L’investissement opérationnel le plus bas. Cette spécialisation améliore légèrement les engagements commerciaux à l’aide d’outils et de processus d’opérations natifs du cloud.

## <a name="high-level-process"></a>Processus de haut niveau

La spécialisation de la charge de travail consiste en une exécution disciplinée des quatre processus suivants dans une approche itérative. Chaque processus est expliqué plus en détail dans [Spécialisation de la plateforme](./platform-specialization.md).

- **Améliorer la conception du système :** Améliorez la conception d’une charge de travail spécifique pour réduire efficacement les interruptions.
- **Automatiser la correction :** Certaines améliorations ne sont pas rentables. Dans ce cas, il peut être plus judicieux d’automatiser la correction et de réduire l’impact des interruptions.
- **Mettre à l’échelle la solution :** À mesure que vous améliorez la conception des systèmes et la correction automatisée, vous pouvez mettre ces modifications à l’échelle dans l’environnement via le catalogue de services.
- **Amélioration continue :** Vous pouvez utiliser différents outils de surveillance pour identifier les améliorations incrémentielles. Ces améliorations peuvent être abordées lors de la prochaine étape de la conception, de l'automatisation et de la mise à l'échelle du système.

## <a name="cultural-change"></a>Changement culturel

La spécialisation de la charge de travail entraîne souvent un changement culturel dans les processus informatiques traditionnels qui se concentrent sur la configuration d’une ligne de base de gestion, les lignes de base améliorées et les opérations de plateforme. Ces types d’offres peuvent être mis à l’échelle dans l’environnement. La spécialisation de la charge de travail est similaire à la spécialisation de la plateforme (dans l’exécution). Toutefois, contrairement aux plateformes courantes, la spécialisation requise par les charges de travail individuelles n’est pas souvent mise à l’échelle.

Lorsque la spécialisation de la charge de travail est requise, la gestion opérationnelle évolue souvent au-delà d’un point de vue informatique central. L’approche suggérée dans le cadre du Framework d’adoption du cloud est une distribution de fonctionnalités de gestion du cloud.

Dans ce modèle, les tâches opérationnelles, telles que la surveillance, le déploiement, DevOps et d’autres fonctions d’innovation, sont déplacées vers une organisation de développement d’applications ou d’unité commerciale. La plateforme cloud et l’équipe de surveillance du cloud de base fournissent toujours la ligne de base de gestion dans l’environnement.

Ces équipes centralisées guident et demandent aux équipes de charge de travail des équipes spécialisées concernant les opérations de leurs charges de travail. Mais la responsabilité opérationnelle quotidienne se situe dans une équipe de gestion cloud gérée en dehors de celle-ci. Ce type de contrôle distribué est un des principaux indicateurs de maturité dans un centre d’excellence cloud.

## <a name="beyond-platform-specialization-application-insights"></a>Au-delà de la spécialisation de plateforme : Application Insights

Des détails supplémentaires sur la charge de travail spécifique sont requis pour fournir des opérations de charge de travail claires. Au cours de la phase d’amélioration permanente, Application Insights sera nécessaire pour la chaîne d’outils de gestion cloud.

|Condition requise|Outil|Objectif|
|---|---|---|
|Monitoring des applications|Application Insights|Surveillance et diagnostic pour les applications|
|Performances, disponibilité et utilisation|Application Insights|Surveillance avancée des applications avec le tableau de bord d’application, les mappages composites, l’utilisation et le suivi|

### <a name="deploy-application-insights"></a>Déployer Application Insights

1. Dans le portail Azure, sélectionnez **Application Insights**.
1. Sélectionnez **+ Ajouter** afin d’ajouter une ressource Application Insights pour surveiller votre application web en direct.
1. Suivez les invitations qui s’affichent à l’écran.

Pour obtenir de l’aide sur la configuration de votre application pour la surveillance, consultez [Hub Azure Monitor Application Insights](https://docs.microsoft.com/azure/azure-monitor/azure-monitor-app-hub).

::: zone target="chromeless"

::: form action="OpenBlade[#create/Microsoft.AppInsights]" submitText="Create Application Insight resources" :::

::: zone-end

### <a name="monitor-performance-availability-and-usage"></a>Surveiller les performances, la disponibilité et l’utilisation

1. Dans le portail Azure, recherchez **Application Insights**.
1. Choisissez l’une des ressources Application Insights dans la liste.

Application Insights contient différents types d’options pour la surveillance des performances, de la disponibilité, de l’utilisation et des dépendances. Chacun de ces affichages des données d’application fournit une clarté dans la boucle de commentaires d’amélioration continue.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Insights%2FComponents]" submitText="Monitor applications" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
