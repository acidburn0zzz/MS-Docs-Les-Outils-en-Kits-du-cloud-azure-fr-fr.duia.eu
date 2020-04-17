---
title: Présentation de la discipline Base de référence de la sécurité
description: Découvrez l’approche à adopter pour élaborer une discipline Base de référence de la sécurité dans le cadre d’une stratégie de gouvernance cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 5e2549c252b8fddf6cd549215704300a764f4040
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80997269"
---
# <a name="security-baseline-discipline-overview"></a>Présentation de la discipline Base de référence de la sécurité

La base de référence de la sécurité est l’une des [cinq disciplines de la gouvernance du cloud](../governance-disciplines.md) dans le [modèle de gouvernance du Framework d’adoption du cloud](../index.md). La sécurité s’invite dans chaque déploiement informatique, et le cloud fait naître des problèmes de sécurité uniques. De nombreuses entreprises sont soumises à des exigences réglementaires qui font de la protection des données sensibles une priorité organisationnelle majeure, particulièrement lors du passage au cloud. Il est primordial que les équipes de sécurité informatique et de cybersécurité identifient les menaces de sécurité potentielles pour votre environnement cloud, et établissent des processus et procédures pour répondre à ces menaces. La discipline Base de référence de la sécurité garantit que les exigences techniques et les contraintes de sécurité soient appliquées de façon homogène dans les environnements cloud, à mesure que ces exigences gagnent en maturité.

> [!NOTE]
> La gouvernance Base de référence de la sécurité ne remplace pas les équipes, les processus et les procédures informatiques existants que votre organisation utilise pour sécuriser les ressources déployées sur le cloud. L’objectif principal de cette discipline est d’identifier les risques de sécurité potentiels et de fournir des conseils sur l’atténuation des risques au personnel informatique responsable de l’infrastructure de sécurité. Lorsque vous élaborez des stratégies et des processus de gouvernance, veillez à faire participer les équipes informatiques pertinentes à vos processus de planification et de révision.

Cet article décrit l’approche à adopter pour élaborer une discipline Base de référence de la sécurité dans le cadre de votre stratégie de gouvernance cloud. Ce guide s’adresse principalement aux architectes cloud de votre organisation et aux autres membres de votre équipe de gouvernance cloud. Cependant, les décisions, les stratégies et les processus qui découlent de cette discipline doivent impliquer un engagement et des discussions avec les membres concernés au sein de votre équipe de sécurité et votre équipe informatique, en particulier les responsables techniques chargés de l’implémentation de la mise en réseau, du chiffrement et des services d’identité.

Prendre les bonnes décisions en matière de sécurité est un point essentiel pour réussir vos déploiements dans le cloud et favoriser votre succès commercial. Si votre organisation manque d’expertise interne en matière de cybersécurité, envisagez de faire appel à des consultants de sécurité externes dans le cadre de cette discipline. Envisagez également de faire appel aux [Services de conseil Microsoft](https://www.microsoft.com/industry/services/consulting), au service d’adoption du cloud [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) ou à des experts externes pour aborder les préoccupations liées à cette discipline.

## <a name="policy-statements"></a>Policy statements

Les instructions de stratégie exploitables et les exigences d’architecture qui en résultent constituent le fondement d’une discipline Base de référence de la sécurité. Pour prendre connaissance des exemples d’instructions de stratégie, consultez l’article [Instructions de stratégie Base de référence de la sécurité](./policy-statements.md). Ces exemples peuvent servir de point de départ à l’élaboration de stratégies de gouvernance de votre organisation.

> [!CAUTION]
> Les exemples de stratégies émanent de l’expérience commune des clients. Pour mieux corréler ces stratégies aux besoins spécifiques de gouvernance cloud, exécutez les étapes suivantes afin de créer des instructions stratégiques qui répondent aux besoins particuliers de votre entreprise.

## <a name="develop-governance-policy-statements"></a>Développer des instructions de stratégie de gouvernance

Les six étapes suivantes offrent des exemples et des options potentielles à prendre en compte lors de l’élaboration de la gouvernance Base de référence de la sécurité. Chaque étape peut servir de thème de discussion au sein de votre équipe de gouvernance cloud et avec les équipes commerciales, informatiques et de sécurité concernées au sein de votre organisation, en vue d’établir les stratégies et processus nécessaires à la gestion des risques liés à la sécurité.

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
                        <h3>Modèle Base de référence de la sécurité</h3>
                        <p class="x-hidden-focus">Télécharger le modèle pour documenter une discipline Base de référence de la sécurité</p>
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
                        <p class="x-hidden-focus">Appréhendez les motivations et les risques généralement associés à la discipline Base de référence de la sécurité.</p>
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
                        <p class="x-hidden-focus">Indicateurs permettant de déterminer à quel moment il est pertinent d’investir dans la discipline Base de référence de la sécurité.</p>
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
                        <p class="x-hidden-focus">Suggestions de processus pour appuyer la conformité aux stratégies dans la discipline Base de référence de la sécurité.</p>
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
                        <p class="x-hidden-focus">Services Azure qui peuvent être implémentés pour soutenir la discipline Base de référence de la sécurité.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Étapes suivantes

Commencez par évaluer les risques métier dans un environnement spécifique.

> [!div class="nextstepaction"]
> [Comprendre les risques métier](./business-risks.md)
