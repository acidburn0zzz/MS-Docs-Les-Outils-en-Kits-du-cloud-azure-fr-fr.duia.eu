---
title: Améliorer votre fondation de gouvernance cloud initiale
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment améliorer de façon incrémentielle votre fondation de gouvernance cloud initiale.
author: BrianBlanchard
ms.author: brblanch
ms.date: 01/03/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: d4a0338daa65ea4269077f15acee05cd99a5fb10
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031779"
---
# <a name="improve-your-initial-cloud-governance-foundation"></a>Améliorer votre fondation de gouvernance cloud initiale

Cet article suppose que vous avez établi une [fondation de gouvernance cloud initiale](./initial-foundation.md). À mesure que votre plan d’adoption du cloud est implémenté, des risques tangibles émergent des approches proposées que les équipes sont susceptibles de suivre pour adopter le cloud. Au fur et à mesure que ces risques sont évoqués dans les conversations sur la planification des versions, utilisez la grille suivante pour identifier rapidement quelques pratiques recommandées pour anticiper le plan d’adoption afin d’éviter que des risques ne deviennent des menaces réelles.

## <a name="maturity-vectors"></a>Vecteurs de maturité

À tout moment, vous pouvez appliquer les instructions normatives suivantes à la fondation de gouvernance initiale pour traiter le risque ou le besoin mentionné dans le tableau ci-dessous.

> [!IMPORTANT]
> L’organisation des ressources peut affecter la façon dont ces instructions normatives sont appliquées. Il est important de commencer par les recommandations qui conviennent le mieux à la fondation de gouvernance cloud initiale que vous avez implémentée à l’étape précédente.

|Risque/besoin | Petites et moyennes entreprises | Grandes entreprises |
|---|---|---|
|Données sensibles dans le cloud|[Instructions normatives](./guides/standard/security-baseline-improvement.md)|[Instructions normatives](./guides/complex/security-baseline-improvement.md)|
|Applications critiques dans le cloud|[Instructions normatives](./guides/standard/resource-consistency-improvement.md)|[Instructions normatives](./guides/complex/resource-consistency-improvement.md)|
|Gestion des coûts du cloud|[Instructions normatives](./guides/standard/cost-management-improvement.md)|[Instructions normatives](./guides/complex/cost-management-improvement.md)|
|Multicloud|[Instructions normatives](./guides/standard/multicloud-improvement.md)|[Instructions normatives](./guides/complex/multicloud-improvement.md)|
|Gestion des identités complexes/héritées|         |[Instructions normatives](./guides/complex/identity-baseline-improvement.md)|
|Couches de gouvernance multiples|         |[Instructions normatives](./guides/complex/multiple-layers-of-governance.md)|

## <a name="next-steps"></a>Étapes suivantes

Outre l’application d’instructions normatives, la méthodologie de gouvernance dans le Framework d’adoption du cloud peut être personnalisée en fonction des contraintes de l’entreprise. Après avoir suivi les recommandations applicables, [évaluez la stratégie d’entreprise pour comprendre les exigences de personnalisation supplémentaires](./corporate-policy.md).

> [!div class="nextstepaction"]
> [Évaluer la stratégie d’entreprise](./corporate-policy.md)
