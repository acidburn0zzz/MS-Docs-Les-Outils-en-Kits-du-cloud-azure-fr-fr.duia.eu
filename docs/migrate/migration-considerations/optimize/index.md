---
title: Optimiser les charges de travail migrées
description: Optimiser les charges de travail migrées
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 87235584bc9da0f1a9e5124408b587eec864af48
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76801883"
---
# <a name="optimize-migrated-workloads"></a>Optimiser les charges de travail migrées

Après avoir migré une charge de travail vers le cloud (ressources connexes incluses), vous devez la préparer pour la promouvoir et l’utiliser en production. Au cours de ce processus, des activités préparent la charge de travail, dimensionnent les ressources dépendantes et préparent l’entreprise à l’entrée en production de la charge de travail cloud migrée.

L’optimisation a pour but de préparer une charge de travail migrée afin de la promouvoir en vue d’une utilisation en production.

## <a name="definition-of-done"></a>Définition de « *terminé* »

Le processus d’optimisation est terminé quand une charge de travail est correctement configurée, dimensionnée et utilisée en production.

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
