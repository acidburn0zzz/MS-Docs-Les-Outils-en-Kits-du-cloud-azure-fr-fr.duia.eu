---
title: Vue d’ensemble de la discipline Accélération du déploiement
description: Utilisez le Cloud Adoption Framework pour Azure pour comprendre l’accélération du déploiement par rapport à la gouvernance du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 3c83e40ab6d08b461095385ac58cf64d74da86a9
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "77708969"
---
# <a name="deployment-acceleration-discipline-overview"></a>Vue d’ensemble de la discipline Accélération du déploiement

L’accélération du déploiement est l’une des [cinq disciplines de la gouvernance du cloud](../governance-disciplines.md) dans le [modèle de gouvernance du Framework d’adoption du cloud](../index.md). Cette discipline met l'accent sur les moyens d'établir des stratégies pour régir la configuration ou le déploiement des ressources. Dans les cinq disciplines de la gouvernance du cloud, l’accélération du déploiement inclut le déploiement, l’alignement de la configuration et la réutilisabilité des scripts. Des activités manuelles ou des activités DevOps entièrement automatisées peuvent être utilisées. Dans les deux cas, les stratégies sont en grande partie similaires. Au fur et à mesure que cette discipline mûrit, l’équipe de gouvernance du cloud peut jouer le rôle de partenaire dans les stratégies DevOps et de déploiement, en accélérant les déploiements et en éliminant les freins à l’adoption du cloud, grâce à la mise en œuvre de ressources réutilisables.

Cet article décrit le processus d’accélération du déploiement qu’une entreprise expérimente durant les phases de planification, de construction, d’adoption et d’exploitation d’une solution cloud. Il est impossible pour tout un document de prendre en compte les exigences d’une organisation. En tant que telle, chaque section de cet article décrit les activités minimales et potentielles suggérées. L’objectif initial de ces activités est de vous aider à créer un [produit minimum viable (MVP) de stratégie](../policy-compliance/index.md#minimum-viable-product-mvp-for-policy), mais aussi à établir un framework pour une amélioration de la [stratégie incrémentielle](../policy-compliance/index.md#incremental-policy-growth). L’équipe de gouvernance du cloud doit décider combien investir dans ces activités pour améliorer l’accélération du déploiement.

> [!NOTE]
> La discipline Accélération du déploiement ne remplace pas les équipes, les processus et les procédures informatiques existants qui permettent à votre entreprise de déployer et de configurer efficacement les ressources cloud. L’objectif principal de cette discipline est d’identifier les risques métier potentiels et de fournir des conseils sur l’atténuation des risques au personnel informatique responsable de la gestion de vos ressources dans le cloud. Lorsque vous élaborez des stratégies et des processus de gouvernance, veillez à faire participer les équipes informatiques pertinentes à vos processus de planification et de révision.

Ce guide s’adresse principalement aux architectes cloud de votre organisation et aux autres membres de votre équipe de gouvernance cloud. Cependant, les décisions, les stratégies et les processus qui découlent de cette discipline doivent impliquer un engagement et des discussions avec les membres concernés dans votre entreprise et vos équipes informatiques, en particulier les responsables du déploiement et de la configuration des charges de travail dans le cloud.

## <a name="policy-statements"></a>Policy statements

Les déclarations de stratégie exploitables et les exigences d’architecture qui en résultent constituent la base d’une discipline Accélération du déploiement. Pour prendre connaissance des exemples de déclarations de stratégie, consultez l’article [Déclarations de stratégie d’accélération du déploiement](./policy-statements.md). Ces exemples peuvent servir de point de départ à l’élaboration de stratégies de gouvernance de votre organisation.

> [!CAUTION]
> Les exemples de stratégies émanent de l’expérience commune des clients. Pour mieux corréler ces stratégies aux besoins spécifiques de gouvernance cloud, exécutez les étapes suivantes afin de créer des instructions stratégiques qui répondent aux besoins particuliers de votre entreprise.

## <a name="develop-governance-policy-statements"></a>Développer des instructions de stratégie de gouvernance

Les six étapes suivantes vous aideront à définir des stratégies de gouvernance pour contrôler le déploiement et la configuration des ressources dans votre environnement cloud.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsE">
<li style="display: flex; flex-direction: column;">
    <a href="./template.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-template.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Accélération du déploiement</h3>
                        <p class="x-hidden-focus">Télécharger le modèle pour documenter une discipline Accélération du déploiement</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li><li style="display: flex; flex-direction: column;">
    <a href="./business-risks.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-risks.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Risques commerciaux</h3>
                        <p class="x-hidden-focus">Appréhendez les motivations et les risques généralement associés à la discipline Accélération du déploiement.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./metrics-tolerance.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-metrics.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Indicateurs et métriques</h3>
                        <p class="x-hidden-focus">Indicateurs permettant de déterminer à quel moment il est pertinent d’investir dans la discipline Accélération du déploiement.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./compliance-processes.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-enforce.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Développer des processus d’adhésion à la stratégie</h3>
                        <p class="x-hidden-focus">Suggestions de processus pour appuyer la conformité aux stratégies dans la discipline Accélération du déploiement.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./discipline-improvement.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-maturity.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Maturité</h3>
                        <p class="x-hidden-focus">Adéquation de la maturité de la gestion du cloud avec les phases d’adoption du cloud.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./toolchain.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-toolchain.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Chaîne d’outils</h3>
                        <p class="x-hidden-focus">Services Azure qui peuvent être implémentés pour soutenir la discipline Accélération du déploiement.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

## <a name="next-steps"></a>Étapes suivantes

Commencez par évaluer les [risques commerciaux](./business-risks.md) dans un environnement spécifique.

> [!div class="nextstepaction"]
> [Comprendre les risques métier](./business-risks.md)

<!-- markdownlint-enable MD033 -->
