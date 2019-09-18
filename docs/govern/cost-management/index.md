---
title: Vue d’ensemble de la discipline Gestion des coûts
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explication de Gestion des coûts en lien avec la gouvernance cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: d7f44027bdc7b2b17dc60dd070092b266609188c
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025719"
---
# <a name="cost-management-discipline-overview"></a>Vue d’ensemble de la discipline Gestion des coûts

La gestion des coûts est l’une des [cinq disciplines de la gouvernance du cloud](../governance-disciplines.md) dans le [modèle de gouvernance du Framework d’adoption du cloud](../index.md). Pour de nombreux clients, le contrôle des coûts est une préoccupation majeure lors de l’adoption de technologies cloud. Parvenir à un équilibre entre les demandes de performances, le rythme d’adoption et les coûts des services cloud peut se révéler périlleux. Cela est particulièrement vrai lors des transformations majeures de l’entreprise qui implémente des technologies cloud. Cette section décrit l’approche à adopter pour élaborer une discipline Gestion des coûts dans le cadre d’une stratégie de gouvernance cloud.

> [!NOTE]
> La gouvernance Gestion des coûts ne remplace pas les équipes commerciales, les pratiques de comptabilité et les procédures existantes qui sont impliquées dans la gestion financière des coûts informatiques de votre organisation. Le principal objectif de cette discipline consiste à identifier les potentiels risques cloud en lien avec les dépenses informatiques, et à proposer des conseils d’atténuation des risques aux équipes commerciales et informatiques responsables du déploiement et de la gestion des ressources cloud.

Ce guide s’adresse principalement aux architectes cloud de votre organisation et aux autres membres de votre équipe de gouvernance cloud. Cependant, les décisions, les stratégies et les processus qui découlent de cette discipline doivent impliquer un engagement et des discussions avec les membres concernés dans votre entreprise et vos équipes informatiques, en particulier les responsables de la propriété, de la gestion et du paiement des charges de travail dans le cloud.

## <a name="policy-statements"></a>Policy statements

Les instructions de stratégie exploitables et les exigences d’architecture qui en résultent constituent le fondement d’une discipline Gestion des coûts. Pour prendre connaissance des exemples de déclarations de stratégie, consultez l’article [Instructions de stratégie Gestion des coûts](./policy-statements.md). Ces exemples peuvent servir de point de départ à l’élaboration de stratégies de gouvernance de votre organisation.

> [!CAUTION]
> Les exemples de stratégies émanent de l’expérience commune des clients. Pour mieux corréler ces stratégies aux besoins spécifiques de gouvernance cloud, exécutez les étapes suivantes afin de créer des instructions stratégiques qui répondent aux besoins particuliers de votre entreprise.

## <a name="developing-cost-management-governance-policy-statements"></a>Développement d’instructions de stratégie de gouvernance Gestion des coûts

Les six étapes suivantes vous aideront à définir des stratégies de gouvernance pour contrôler les coûts de votre environnement.

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
                        <h3>Modèle Gestion des coûts</h3>
                        <p class="x-hidden-focus">Télécharger le modèle pour documenter une discipline Gestion des coûts</p>
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
                        <p class="x-hidden-focus">Appréhendez les motivations et les risques généralement associés à la discipline Gestion des coûts.</p>
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
                        <p class="x-hidden-focus">Indicateurs permettant de déterminer à quel moment il est pertinent d’investir dans la discipline Gestion des coûts.</p>
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
                        <p class="x-hidden-focus">Suggestions de processus pour appuyer la conformité aux stratégies dans la discipline Gestion des coûts.</p>
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
                        <p class="x-hidden-focus">Services Azure qui peuvent être implémentés pour soutenir la discipline Gestion des coûts.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

## <a name="next-steps"></a>Étapes suivantes

Commencez par évaluer les risques métier dans un environnement spécifique.

> [!div class="nextstepaction"]
> [Comprendre les risques métier](./business-risks.md)

<!-- markdownlint-enable MD033 -->
