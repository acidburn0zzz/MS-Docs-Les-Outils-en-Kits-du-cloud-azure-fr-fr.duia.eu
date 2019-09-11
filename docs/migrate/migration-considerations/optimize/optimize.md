---
title: Évaluer et redimensionner les ressources cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Évaluer et redimensionner les ressources cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 3709b37e1604ff966d043c142e86a1dbb78ecffb
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70836627"
---
# <a name="benchmark-and-resize-cloud-assets"></a>Évaluer et redimensionner les ressources cloud

La surveillance de l’utilisation et des dépenses revêt une importance capitale pour les infrastructures cloud. Les organisations paient les ressources qu’elles consomment au fil du temps. Quand l’utilisation dépasse les seuils contractuels, les coûts peuvent augmenter de façon rapide. Les rapports de gestion des coûts vous aident à surveiller les dépenses et ainsi d’analyser et suivre l’utilisation du cloud, les coûts et les tendances. Grâce aux rapports d’utilisation dans le temps, vous pouvez détecter des anomalies par rapport aux tendances normales. La mauvaise utilisation de ressources dans un déploiement cloud est visible dans les rapports d’optimisation. Notez les mauvaises utilisations de ressources dans les rapports d’analyse des coûts.

Dans les modèles locaux traditionnels, la réquisition des systèmes informatiques est coûteuse et fastidieuse. Les processus nécessitent souvent des cycles de révision des dépenses de capital et peuvent même nécessiter un processus annuel de planification. Par conséquent, il est courant d’acheter plus que nécessaire. Il est tout aussi courant pour les administrateurs informatiques de surapprovisionner les ressources en vue de répondre aux demandes futures prévues.

Dans le cloud, les modèles de comptabilité et d’approvisionnement éliminent les retards à l’origine des surachats. Lorsqu’une ressource a besoin de ressources supplémentaires, elle peut être mise à l’échelle presque instantanément. Cela signifie que les ressources peuvent être réduites en toute sécurité pour réduire les ressources consommées et les coûts. Au cours de l’évaluation et de l’optimisation, l’équipe d’adoption cloud cherche à trouver l’équilibre entre les performances et les coûts, en provisionnant les ressources pour qu’elles ne soient pas plus volumineuses ou petites que nécessaire pour répondre aux demandes de production.

<!-- markdownlint-disable MD026 -->

## <a name="should-assets-be-optimized-during-or-after-the-migration"></a>Les ressources doivent-elles être optimisées pendant ou après la migration ?

Quand une ressource doit-elle être optimisée, &mdash;pendant ou après la migration ? La réponse simple est *les deux*. Toutefois, cela n’est pas tout à fait exact. Pour expliquer comment procéder, observez les deux scénarios de base pour l’optimisation du dimensionnement des ressources :

- **Redimensionnement planifié.** Souvent, une ressource est clairement surchargée et sous-exploitée et doit être redimensionnée lors du déploiement. Déterminer si une ressource a été redimensionnée avec succès dans ce cas requiert un test d’acceptation utilisateur après la migration. Si un utilisateur expérimenté ne note pas de pertes de performances ou de fonctionnalités pendant le test, vous pouvez conclure que la ressource a été dimensionnée avec succès.
- **Optimisation.** Dans les cas où la nécessité de l’optimisation est incertaine, les équipes informatiques doivent utiliser une approche reposant sur les données pour la gestion de la taille des ressources. À l’aide des évaluations des performances de la ressource, une équipe informatique peut prendre des décisions éclairées quant à la taille, aux services, à l’échelle et à l’architecture les plus appropriés pour une solution. L’équipe peut ensuite redimensionner et tester les théories sur les performances après la migration.

Pendant la migration, utilisez des hypothèses et expérimentez le dimensionnement. Toutefois, une véritable optimisation des ressources nécessite des données provenant des performances réelles dans un environnement cloud. Pour une véritable optimisation, l’équipe informatique doit tout d’abord implémenter des approches pour analyser les performances et l’utilisation des ressources.

## <a name="benchmark-and-optimize-with-azure-cost-management"></a>Évaluation et optimisation avec Azure Cost Management

[Azure Cost Management](/azure/cost-management/overview), concédé sous licence par Cloudyn, une filiale Microsoft, gère les dépenses cloud avec transparence et précision. Ce service analyse, évalue, alloue et optimise les coûts du cloud.

Les données d’historique peuvent aider à gérer les coûts en analysant l’utilisation et les coûts dans le temps pour identifier les tendances, qui sont ensuite utilisées pour prévoir les dépenses futures. La gestion des coûts propose aussi des rapports d’estimation des coûts très utiles. La répartition des coûts permet de gérer les coûts en analysant les coûts en fonction des stratégies de balisage. La répartition des coûts dans la rétrofacturation et la facturation interne met en évidence l’utilisation des ressources et les coûts associés dans le but d’influencer les comportements de consommation ou de facturer les clients du locataire. Le contrôle d’accès facilite la gestion des coûts en autorisant les utilisateurs et les équipes à accéder uniquement aux données de gestion des coûts dont ils ont besoin. La gestion des coûts est aussi facilitée par les alertes, qui vous avertissent automatiquement en cas de dépenses inhabituelles ou excessives. Les alertes peuvent aussi être envoyées automatiquement à d’autres parties prenantes en cas d’anomalies de dépenses et de risques de dépenses excessives. Plusieurs rapports prennent en charge les alertes basées sur les seuils budgétaires et de coûts.

## <a name="improve-efficiency"></a>Améliorer l’efficacité

La gestion des coûts vous permet de déterminer quelle est l’utilisation optimale des machines virtuelles et d’identifier ou de supprimer les machines virtuelles inactives, ainsi que les disques non attachés. Les informations fournies par les rapports d’optimisation du dimensionnement et les rapports de mauvaise utilisation des ressources permettent d’élaborer un plan visant à réduire la taille ou supprimer les machines virtuelles inactives.

## <a name="next-steps"></a>Étapes suivantes

Une fois qu’une charge de travail a été testée et optimisée, il est temps de [préparer la charge de travail pour la promotion](./ready.md).

> [!div class="nextstepaction"]
> [Préparer une charge de travail migrée pour la promotion en production](./ready.md)
