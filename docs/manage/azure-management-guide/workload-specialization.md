---
title: Spécialisation de la charge de travail pour la gestion cloud dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Améliorer les opérations de gestion cloud spécifiques à la charge de travail
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 51bdf23ccb2262202dfa095c5e9b57f727d11d3b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556987"
---
# <a name="workload-specialization-for-cloud-management"></a>Spécialisation de la charge de travail pour la gestion cloud

La spécialisation de la charge de travail repose sur les concepts décrits dans [Spécialisation de la charge de travail](./platform-specialization.md).

![Au-delà de la base de référence de gestion cloud](../../_images/manage/beyond-the-baseline.png)

- **Opérations de charge de travail :** Plus grand investissement d’opérations par charge de travail. Degré de résilience le plus élevé. Suggéré pour +/- 20% des charges de travail qui pilotent la valeur commerciale. Généralement réservé aux charges de travail importantes ou critiques.
- **Opérations de plateforme :** Les investissements opérationnels sont répartis sur de nombreuses charges de travail. Les améliorations de la résilience ont un impact sur toutes les charges de travail qui tirent parti de la plate-forme définie. Suggéré pour +/- 20% des plateformes les plus importantes. Généralement réservé aux charges de travail de niveau moyen ou critique.
- **Base de référence de gestion améliorée :** Investissement opérationnel le plus bas. Des engagements commerciaux légèrement améliorés à l’aide d’outils et de processus d’opérations natifs du cloud.

## <a name="high-level-process"></a>Processus de haut niveau

La spécialisation de la charge de travail consiste en une exécution disciplinée des quatre processus suivants dans une approche itérative. Chaque processus est expliqué plus en détail dans l’article [Spécialisation de la plateforme](./platform-specialization.md).

- **Améliorer la conception du système :** Améliorez la conception d’une charge de travail spécifique pour réduire efficacement les interruptions.
- **Automatiser la correction :** Certaines améliorations ne sont pas rentables. Dans ce cas, il peut être plus judicieux d’automatiser la correction et de réduire l’impact des interruptions.
- **Mettre à l’échelle la solution :** Lorsque la conception des systèmes et la correction automatisée sont améliorées, ces modifications peuvent être mises à l’échelle dans l’environnement via le catalogue de services.
- **Amélioration continue :** Vous pouvez utiliser divers outils de supervision pour découvrir les améliorations incrémentielles qui peuvent être apportées dans la prochaine étape de la conception du système, de l’automatisation et de la mise à l’échelle.

## <a name="cultural-change"></a>Changement culturel

La spécialisation de charge de travail entraîne souvent un changement culturel. Les processus informatiques traditionnels sont ceux qui se concentrent sur la configuration d’une ligne de base de gestion, les lignes de base améliorées et les opérations de plateforme. Ces types d’offre peuvent être mis à l’échelle dans l’environnement. La spécialisation de la charge de travail est très similaire à la spécialisation de la plateforme (dans l’exécution). Toutefois, contrairement aux plateformes courantes, la spécialisation requise par les charges de travail individuelles n’est pas souvent mise à l’échelle.

Lorsque la spécialisation de la charge de travail est requise, il est courant que la gestion opérationnelle évolue au-delà d’un point de vue informatique central. L’approche suggérée dans le cadre de le Framework d’adoption du cloud est une distribution de fonctionnalités de gestion du cloud.

Dans ce modèle, les tâches opérationnelles, telles que la surveillance, le déploiement, DevOps et d’autres fonctions d’innovation, sont déplacées vers une organisation de développement d’applications ou d’unité commerciale. La plateforme cloud et l’équipe de surveillance du cloud de base fournissent toujours la ligne de base de gestion dans l’environnement. Ces équipes centralisées guident et demandent aux équipes de charge de travail des équipes spécialisées concernant les opérations de leurs charges de travail. Mais la responsabilité opérationnelle quotidienne se situe dans une équipe de gestion cloud gérée en dehors de celle-ci. Ce type de contrôle distribué est l’un des principaux indicateurs du centre d’excellence de cloud.

## <a name="beyond-platform-specialization---application-insights"></a>Au-delà de la spécialisation de la plateforme-Application Insights

Des détails supplémentaires sur la charge de travail spécifique sont requis pour fournir des opérations de charge de travail claires. Au cours de la phase d’amélioration permanente, Application Insights sera nécessaire pour la chaîne d’outils de gestion cloud.

|Surveillance des applications|Application Insights|Surveillance et diagnostics pour les applications| |Performances, disponibilité, utilisation|Application Insights|Surveillance avancée des applications avec le tableau de bord d’application, les mappages composites, l’utilisation et le suivi|

### <a name="deploy-application-insights"></a>Déployer Application Insights

1. Dans le portail Azure, recherchez **Application Insights**.
2. Cliquez sur **+ Ajouter** pour ajouter une ressource Application Insights pour surveiller votre application web en direct.
3. Suivez les invitations qui s’affichent à l’écran

Pour obtenir de l’aide sur la configuration de votre application pour la surveillance, consultez [Hub Azure Monitor Application Insights](https://docs.microsoft.com/azure/azure-monitor/azure-monitor-app-hub).

::: zone target="chromeless"

::: form action="OpenBlade[#create/Microsoft.AppInsights]" submitText="Create Application Insight resources" :::

::: zone-end

### <a name="monitor-performance-availability-and-usage"></a>Surveiller les performances, la disponibilité et l’utilisation

1. Dans le portail Azure, recherchez **Application Insights**.
2. Choisissez l’une des ressources Application Insights dans la liste

La navigation pour Application Insights contient diverses options pour la surveillance des performances, de la disponibilité, de l’utilisation et des dépendances. Chacun de ces affichages des données d’application fournit une clarté dans la boucle de commentaires d’amélioration continue.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Monitor applications" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
