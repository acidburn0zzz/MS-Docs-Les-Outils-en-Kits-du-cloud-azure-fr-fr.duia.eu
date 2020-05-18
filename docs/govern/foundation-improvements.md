---
title: Améliorer votre fondation de gouvernance cloud initiale
description: Utilisez le Framework d’adoption du cloud pour Azure pour savoir comment améliorer progressivement la fondation de votre gouvernance cloud initiale.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/13/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 41535db6452be0b8efea9a91329169326c444ab0
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83220207"
---
# <a name="improve-your-initial-cloud-governance-foundation"></a>Améliorer votre fondation de gouvernance cloud initiale

Cet article suppose que vous avez établi une [fondation de gouvernance cloud initiale](./initial-foundation.md). À mesure que votre plan d’adoption du cloud est implémenté, des risques tangibles émergent des approches proposées que les équipes sont susceptibles de suivre pour adopter le cloud. Au fur et à mesure que ces risques sont évoqués dans les conversations sur la planification des versions, utilisez la grille suivante pour identifier rapidement quelques bonnes pratiques pour anticiper le plan d’adoption afin d’éviter que des risques ne deviennent des menaces réelles.

## <a name="maturity-vectors"></a>Vecteurs de maturité

À tout moment, vous pouvez appliquer les bonnes pratiques suivantes à la fondation de gouvernance initiale pour traiter le risque ou le besoin mentionné dans le tableau ci-dessous.

> [!IMPORTANT]
> L’organisation des ressources peut influencer la manière dont ces bonnes pratiques sont appliquées. Il est important de commencer par les recommandations qui conviennent le mieux à la fondation de gouvernance cloud initiale que vous avez implémentée à l’étape précédente.

| Risque/besoin | Entreprise standard | Entreprise complexe |
|---|---|---|
| Données sensibles dans le cloud | [Amélioration de la discipline](./guides/standard/security-baseline-improvement.md) | [Amélioration de la discipline](./guides/complex/security-baseline-improvement.md) |
| Applications stratégiques dans le cloud | [Amélioration de la discipline](./guides/standard/resource-consistency-improvement.md) | [Amélioration de la discipline](./guides/complex/resource-consistency-improvement.md) |
| Gestion des coûts du cloud | [Amélioration de la discipline](./guides/standard/cost-management-improvement.md) | [Amélioration de la discipline](./guides/complex/cost-management-improvement.md) |
| Multicloud | [Amélioration de la discipline](./guides/standard/multicloud-improvement.md) | [Amélioration de la discipline](./guides/complex/multicloud-improvement.md) |
| Gestion des identités complexes/héritées | N/A | [Amélioration de la discipline](./guides/complex/identity-baseline-improvement.md) |
| Couches de gouvernance multiples | N/A | [Amélioration de la discipline](./guides/complex/multiple-layers-of-governance.md) |

## <a name="next-steps"></a>Étapes suivantes

Outre l’application de bonnes pratiques, la méthodologie de gouvernance dans le Framework d’adoption du cloud peut être personnalisée en fonction des contraintes de l’entreprise. Après avoir suivi les recommandations applicables, [évaluez la stratégie d’entreprise pour comprendre les exigences de personnalisation supplémentaires](./corporate-policy.md).

> [!div class="nextstepaction"]
> [Évaluer la stratégie d’entreprise](./corporate-policy.md)
