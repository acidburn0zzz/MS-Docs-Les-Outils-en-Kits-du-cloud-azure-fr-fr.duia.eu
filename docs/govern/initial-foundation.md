---
title: Établir une fondation de gouvernance cloud initiale
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Commencez à utiliser la gouvernance cloud en établissant une fondation de gouvernance cloud initiale.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 3e1f2c1b54a55a740376ba1d1c45c13dc9e7e26d
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71032481"
---
# <a name="establish-an-initial-cloud-governance-foundation"></a>Établir une fondation de gouvernance cloud initiale

L’établissement d’une gouvernance cloud est un vaste effort itératif. Il est difficile de trouver un juste équilibre entre vitesse et contrôle, en particulier lors des premières phases de l’adoption du cloud. Les instructions de gouvernance dans le Framework d’adoption du cloud contribuent à fournir cet équilibre par le biais d’une approche agile de l’adoption.

Cet article présente deux options permettant d’établir une fondation initiale pour la gouvernance. Les deux options permettent d’adapter et de développer les contraintes de gouvernance à mesure que le plan d’adoption est implémenté et que les besoins deviennent plus clairement définis. Par défaut, la fondation initiale suppose une position d’isolation et de contrôle. Par ailleurs, elle porte davantage sur l’organisation des ressources que sur la gouvernance des ressources. Ce point de départ léger est appelé _produit minimum viable_ (MVP, Minimum Viable Product) pour la gouvernance. L’objectif du MVP est de réduire les obstacles à l’établissement d’une position de gouvernance initiale, puis de permettre une maturation rapide de la solution pour répondre à une variété de risques tangibles.

## <a name="already-using-the-cloud-adoption-framework"></a>Framework d’adoption du cloud déjà en cours d’utilisation

Si vous avez suivi le Framework d’adoption du cloud, vous avez peut-être déjà déployé un MVP de gouvernance. Les instructions sont un aspect fondamental de tout modèle de fonctionnement. Elle est présente à chaque phase du cycle de vie de l’adoption du cloud. Ainsi, le [Framework d’adoption du cloud](../index.md) fournit des instructions qui injectent de la gouvernance dans les activités liées à l’implémentation de votre [plan d’adoption du cloud](../plan/index.md). Un exemple de cette intégration de la gouvernance consiste à utiliser des blueprints pour déployer une ou plusieurs zones d’accueil présentes dans les instructions de [préparation](../ready/index.md). Voici un autre exemple d’instruction pour l’[application d’un scale-out aux abonnements](../ready/considerations/scaling-subscriptions.md). Si vous avez suivi l’une de ces recommandations, les sections suivantes du MVP sont simplement une révision de vos décisions de déploiement existantes. Après un examen rapide, passez directement à [Améliorer la solution de gouvernance initiale et appliquer des contrôles recommandés](./foundation-improvements.md).

## <a name="establish-an-initial-governance-foundation"></a>Établir une fondation de gouvernance initiale

Voici deux exemples de fondations de gouvernance initiales (également appelées MVP de gouvernance) illustrant l’application d’une solide fondation pour la gouvernance à des déploiements nouveaux ou existants. Choisissez le MVP qui correspond le mieux aux besoins de votre entreprise pour commencer :

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./guides/standard/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guide de gouvernance standard</h3>
                        <p>Guide pour la plupart des organisations basées sur le modèle à deux abonnements recommandé, conçu pour les déploiements dans plusieurs régions, mais sans englober les clouds publics et souverains/gouvernementaux.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./guides/complex/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guide de gouvernance pour les entreprises complexes</h3>
                        <p>Guide pour les entreprises qui sont gérées par plusieurs unités commerciales informatiques indépendantes ou qui englobent des clouds publics et souverains/gouvernementaux.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>
<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Étapes suivantes

Une fois qu’une fondation de gouvernance est en place, appliquez les recommandations appropriées pour améliorer la solution et vous protéger contre les risques tangibles.

> [!div class="nextstepaction"]
> [Améliorer la fondation de gouvernance initiale](./foundation-improvements.md)