---
title: Premier projet d’adoption du cloud
description: En savoir plus sur l’implémentation de votre premier projet d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 90e21047f8d64f15ef3c94ebe82e31ba615c4d38
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78225251"
---
<!-- markdownlint-disable MD026 -->

# <a name="first-cloud-adoption-project"></a>Premier projet d’adoption du cloud

Il existe une courbe d’apprentissage et un engagement de délai pour la planification de l’adoption du cloud. Même pour les équipes expérimentées, une bonne planification prend du temps : le temps nécessaire pour aligner les parties prenantes, le temps nécessaire pour collecter et analyser les données, le temps nécessaire pour valider les décisions à long terme ainsi que le temps nécessaire pour aligner les personnes, les processus et la technologie. Dans les efforts d’adoption les plus productifs, la planification progresse parallèlement à l’adoption. Elle s’améliore à chaque version et à chaque migration de charge de travail vers le cloud. Il est important de comprendre la différence entre un plan d’adoption du cloud et une stratégie d’adoption du cloud. Vous avez besoin d’une stratégie bien définie pour faciliter et guider l’implémentation d’un plan d’adoption du cloud.

Le Framework d’adoption du cloud pour Azure décrit les processus d’adoption du cloud et le fonctionnement des charges de travail hébergées dans le cloud. Chacun des processus des phases de définition de stratégie, de planification, de préparation, d’adoption et d’exploitation nécessite de légères extensions des compétences techniques, commerciales et opérationnelles. Certaines de ces compétences peuvent provenir d’un apprentissage dirigé. Mais beaucoup d’entre elles sont acquises de manière efficace via une expérience pratique.

Le démarrage d’un premier processus d’adoption parallèlement au développement de la planification offre certains avantages :

- Établir un état d’esprit axé sur la croissance pour encourager l’apprentissage et l’exploration
- Permettre à l’équipe de développer les compétences nécessaires
- Créer des situations qui encouragent de nouvelles approches de la collaboration
- Identifier les lacunes au niveau des compétences et les besoins potentiels au niveau du partenariat
- Fournir des entrées concrètes à la planification

## <a name="first-project-criteria"></a>Premier critère de projet

Votre premier projet d’adoption doit s’aligner sur vos [motivations](./motivations.md) pour l’adoption du cloud. Dans la mesure du possible, votre premier projet doit également montrer la progression vers un [résultat opérationnel](./business-outcomes/business-outcome-template.md) défini.

## <a name="first-project-expectations"></a>Attentes du premier projet

Le premier projet d’adoption de votre équipe va probablement entraîner un déploiement de production d’un certain genre. Mais cela n’est pas toujours le cas. Établissez les attentes appropriées dès le début. Voici quelques attentes judicieuses à définir :

- Ce projet est une source d’apprentissage.
- Ce projet peut entraîner des déploiements de production, mais cela va probablement nécessiter d’abord des efforts supplémentaires.
- Le résultat de ce projet est un ensemble d’exigences claires visant à fournir une solution de production à long terme.

## <a name="first-project-examples"></a>Exemples de premiers projets

Pour étayer les critères précédents, cette liste fournit un exemple de premier projet pour chaque catégorie de motivation :

- **Événements métier critiques :** Quand la motivation principale est un événement métier critique, l’implémentation d’un outil tel qu’[Azure Site Recovery](../migrate/azure-migration-guide/migrate.md?tabs=Tools#azure-site-recovery) peut constituer un bon premier projet. Durant la migration, vous pouvez utiliser cet outil pour migrer rapidement les ressources du centre de données. Toutefois, au cours du premier projet, vous pouvez être amené à l’utiliser simplement comme outil de reprise d’activité, ce qui réduit les dépendances à l’égard des ressources de reprise après sinistre dans le centre de données.

- **Motivations de la migration :** Quand la migration est la principale motivation, il est sage de commencer par la migration d’une charge de travail non critique. Le [Guide de configuration Azure](../ready/azure-setup-guide/index.md) et le [Guide de migration Azure](../migrate/azure-migration-guide/index.md) peuvent vous aider à migrer votre première charge de travail.

- **Motivations de l’innovation :** Quand l’innovation est la principale motivation, la création d’un environnement de développement/test ciblé peut constituer un excellent premier projet.

Voici d’autres exemples de projets de première adoption :

- **Continuité d’activité et reprise d’activité (BCDR)**  : Au-delà d’Azure Site Recovery, vous pouvez implémenter plusieurs stratégies BCDR en tant que premier projet.
- **Non-production :** Déployez une instance de non-production d’une charge de travail.
- **Archive :** Le stockage froid peut imposer des contraintes au centre de ressources. Le déplacement de ces données vers le cloud constitue un atout fiable.
- **Fin du support :** La migration des ressources ayant atteint la fin du support constitue un autre atout qui renforce les compétences techniques. Cela peut également permettre de faire des économies sur les coûts onéreux des contrats de support ou des frais de licence.
- **VDI (interface de bureau virtuel) :** La création de bureaux virtuels pour les employés distants peut être un atout. Dans certains cas, ce premier projet d’adoption peut également permettre de réduire la dépendance à l’égard de réseaux privés coûteux au profit d’une connectivité Internet publique standard.
- **Développement/Test :** Supprimez les développements/tests des environnements locaux pour fournir aux développeurs le contrôle, l’agilité et les fonctionnalités du libre-service.
- **Applications simples (moins de cinq) :** Modernisez et migrez une application simple pour acquérir rapidement une expérience de développement et d’exploitation.
- **Labs de performances :** Quand vous avez besoin de performances à grande échelle dans un environnement lab, utilisez le cloud pour provisionner rapidement et à moindre coût ces labs sur une brève période.
- **Plateforme de données :** Création d’un lac de données avec une capacité de calcul scalable pour les charges de travail d’analytique, de rapport ou de machine learning, et migration vers des bases de données managées à l’aide de méthodes de création d’image mémoire et de restauration ou de services de migration de données.

## <a name="next-steps"></a>Étapes suivantes

Une fois que le premier projet d’adoption du cloud a commencé, l’équipe chargée de la stratégie cloud peut se tourner vers le [plan d’adoption du cloud](../plan/index.md) à plus long terme.

> [!div class="nextstepaction"]
> [Créer votre plan d’adoption du cloud](../plan/index.md)
