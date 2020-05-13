---
title: Optimiser les charges de travail migrées
description: Préparez votre charge de travail migrée et ses ressources en vue de les promouvoir en production à l’aide du Cloud Adoption Framework pour Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 1e101a75d3b13cc8cbcb6512d6a0a8b29674d5aa
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83214206"
---
# <a name="release-workloads"></a>Mettre en production les charges de travail

Après avoir déployé une collection de charges de travail et leurs ressources connexes sur le cloud, vous devez les préparer en vue de la mise en production. Au cours de cette phase de l’effort de migration, la collection de charges de travail fait l’objet d’un test de charge. Les charges de travail sont ensuite testées dans l’entreprise, puis optimisées et documentées. Après examen et approbation des déploiements de charges de travail par les équipes métier et informatiques, ces charges de travail peuvent être mises en production ou transmises aux équipes en charge de la gouvernance, de la sécurité et des opérations pour les opérations en cours.

La « mise en production des charges de travail » a pour but de préparer des charges de travail migrées afin de les promouvoir en vue d’une utilisation en production.

## <a name="definition-of-_done_"></a>Définition de « _terminé_ »

Le processus d’optimisation est terminé quand une charge de travail est correctement configurée, dimensionnée et déployée en production.

## <a name="accountability-during-optimization"></a>Responsabilité de l’optimisation

La responsabilité de l’ensemble du processus d’optimisation revient à l’équipe d’adoption du cloud. Cependant, certaines activités de ce processus doivent être confiées aux membres d’autres équipes (stratégie cloud, exploitation du cloud et gouvernance du cloud).

## <a name="responsibilities-during-optimization"></a>Obligations liées à l’optimisation

En plus de la responsabilité d’ensemble, certaines actions doivent être affectées directement à un individu ou à un groupe. Voici quelques-unes des activités qui doivent être confiées à des parties responsables :

- **Tests en entreprise.** Résolvez tous les problèmes de compatibilité empêchant la migration de la charge de travail vers le cloud.
  - Les utilisateurs avancés de l’entreprise doivent participer activement aux tests de la charge de travail migrée. En fonction du degré d’optimisation visé, plusieurs cycles de test peuvent être nécessaires.
- **Plan des changements dans l’entreprise.** Développez un plan qui décrit l’adoption par les utilisateurs, les changements affectant des processus métier et les modifications impactant des indicateurs de performance clés ou des métriques d’apprentissage à la suite des efforts de migration.
- **Référence et optimisation.** Étudiez les tests en entreprise et les tests automatisés pour évaluer les performances par rapport à des références. En fonction de l’utilisation, l’équipe d’adoption du cloud peut affiner le dimensionnement des ressources déployées pour équilibrer les coûts et les performances par rapport aux besoins attendus en production.
- **Prêt pour la production.** Préparez la charge de travail et l’environnement pour prendre en charge l’utilisation continue de la charge de travail en production.
- **Promotion.** Redirigez le trafic en production vers la charge de travail migrée et optimisée. Cette activité représente l’achèvement d’un cycle de version.

En plus des activités principales, quelques activités parallèles nécessitent des affectations et des plans d’exécution spécifiques :

- **Désactivation.** En général, une migration permet de réduire les coûts une fois les ressources de production précédentes désactivées et correctement éliminées.
- **Rétrospective.** Chaque version donne l’occasion d’approfondir les connaissances et d’adopter un état d’esprit axé sur la croissance. Au terme de chaque cycle de mise en production, l’équipe d’adoption du cloud doit évaluer les processus utilisés durant la migration afin d’identifier les améliorations.

## <a name="next-steps"></a>Étapes suivantes

Grâce aux connaissances générales que vous venez d’acquérir sur le processus d’optimisation, vous pouvez à présent lancer le processus en [établissant un plan des changements dans l’entreprise pour la charge de travail candidate](./business-change-plan.md).

> [!div class="nextstepaction"]
> [Plan des changements dans l’entreprise](./business-change-plan.md)
