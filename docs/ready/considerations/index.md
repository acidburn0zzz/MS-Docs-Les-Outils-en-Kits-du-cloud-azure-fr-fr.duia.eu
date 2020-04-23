---
title: Développer votre zone d’atterrissage
description: Utiliser le Cloud Adoption Framework pour Azure pour apprendre à développer une zone d’atterrissage
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: cbfbadebd635891d680da29091ca572611712e09
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81120792"
---
# <a name="expand-your-landing-zone"></a>Développer votre zone d’atterrissage

Cette section de la méthodologie de préparation repose sur les principes de [refactorisation de la zone d’atterrissage](../landing-zone/refactor.md). Comme indiqué dans cet article, une approche de refactorisation pour l’infrastructure en tant que code supprime les bloqueurs de la réussite métier tout en minimisant les risques. Cette série d’articles suppose que vous avez déployé votre première zone d’atterrissage et que vous souhaitez maintenant la développer pour répondre aux besoins de l’entreprise.

## <a name="shared-architecture-principles"></a>Principes d’une architecture partagée

Le développement de votre zone d’atterrissage fournit une approche orientée code pour incorporer les principes suivants dans la zone d’atterrissage et plus largement dans votre environnement cloud global.

![Principes d’une architecture partagée](../../_images/ready/shared-principles.png)

Ces mêmes principes d’architecture sont partagés par [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview), [Azure Architecture Framework](https://docs.microsoft.com/azure/architecture/framework) et les solutions du [Centre des architectures Azure](https://docs.microsoft.com/azure/architecture).

## <a name="applying-these-principles-to-your-landing-zone-improvements"></a>Application de ces principes à vos améliorations de zone d’atterrissage

Pour garantir un meilleur alignement avec les méthodologies du Cloud Adoption Framework, les principes ci-dessus sont regroupés en améliorations de zone d’atterrissage exploitables :

- Considérations de base : Refactorisez une zone d’atterrissage pour affiner l’hébergement, les notions de base et d’autres éléments fondamentaux.
- Développements liés aux opérations : Ajoutez des configurations de gestion des opérations pour améliorer **les performances, la fiabilité et l’excellence opérationnelle**.
- Développements liés à la gouvernance : Ajoutez des configurations de gouvernance pour améliorer **les coûts, la fiabilité, la sécurité** et la cohérence.
- Développements liés à la sécurité : Ajoutez des configurations de **sécurité** pour améliorer la protection des données sensibles et des systèmes critiques.

> [!WARNING]
> Les équipes d’adoption qui ont pour objectif à moyen terme (dans les 24 mois) d’**héberger plus de 1 000 ressources (applications, infrastructure ou ressources de données) dans le cloud** doivent considérer chacun de ces développements au début de leur parcours d’adoption du cloud. Pour tous les autres modèles d’adoption, les développements de zones d’atterrissage peuvent être des itérations parallèles, favorisant un succès métier précoce.

## <a name="next-steps"></a>Étapes suivantes

Avant de refactoriser votre première zone d’atterrissage, il est important de comprendre le [développement piloté par les tests des zones d’atterrissage](./test-driven-development.md).

> [!div class="nextstepaction"]
> [Développement piloté par les tests des zones d’atterrissage](./test-driven-development.md)
