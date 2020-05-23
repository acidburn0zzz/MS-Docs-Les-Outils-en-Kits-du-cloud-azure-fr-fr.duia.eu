---
title: Développer votre zone d’atterrissage
description: Utiliser Cloud Adoption Framework pour Azure afin d’apprendre à développer une zone d’atterrissage.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 0964da23da680755ea9d6c35fef0996e986780b4
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83756564"
---
# <a name="expand-your-landing-zone"></a>Développer votre zone d’atterrissage

Cette section de la méthodologie de préparation repose sur les principes de [refactorisation de la zone d’atterrissage](../landing-zone/refactor.md). Comme indiqué dans cet article, une approche de refactorisation pour l’infrastructure en tant que code supprime les bloqueurs de la réussite métier tout en minimisant les risques. Cette série d’articles suppose que vous avez déployé votre première zone d’atterrissage et que vous souhaitez maintenant la développer pour répondre aux besoins de l’entreprise.

## <a name="shared-architecture-principles"></a>Principes d’une architecture partagée

Le développement de votre zone d’atterrissage fournit une approche orientée code pour incorporer les principes suivants dans la zone d’atterrissage et plus largement dans votre environnement cloud global.

![Principes d’une architecture partagée](../../_images/ready/shared-principles.png)

Ces mêmes principes d’architecture sont partagés par [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview), [Microsoft Azure Well-Architected Framework](https://docs.microsoft.com/azure/architecture/framework) et les solutions du [Centre des architectures Azure](https://docs.microsoft.com/azure/architecture).

## <a name="applying-these-principles-to-your-landing-zone-improvements"></a>Application de ces principes à vos améliorations de zone d’atterrissage

Pour garantir un meilleur alignement avec les méthodologies du Cloud Adoption Framework, les principes ci-dessus sont regroupés en améliorations de zone d’atterrissage exploitables :

- Considérations de base : refactorisez une zone d’atterrissage pour affiner l’hébergement, les notions de base et d’autres éléments fondamentaux.
- Extension des opérations : ajoutez des configurations de gestion des opérations pour améliorer **les performances, la fiabilité et l’excellence opérationnelle**.
- Extension de la gouvernance : ajoutez des configurations de gouvernance pour améliorer **les coûts, la fiabilité, la sécurité** et la cohérence.
- Extension de la sécurité : ajoutez des configurations de **sécurité** pour améliorer la protection des données sensibles et des systèmes critiques.

> [!WARNING]
> Les équipes d’adoption qui ont pour objectif à moyen terme (dans les 24 mois) d’**héberger plus de 1 000 ressources (applications, infrastructure ou ressources de données) dans le cloud** doivent considérer chacun de ces développements au début de leur parcours d’adoption du cloud. Pour tous les autres modèles d’adoption, les développements de zones d’atterrissage peuvent être des itérations parallèles, favorisant un succès métier précoce.

## <a name="next-steps"></a>Étapes suivantes

Avant de refactoriser votre première zone d’atterrissage, il est important de comprendre le [développement piloté par les tests des zones d’atterrissage](./test-driven-development.md).

> [!div class="nextstepaction"]
> [Développement piloté par les tests des zones d’atterrissage](./test-driven-development.md)
