---
title: Les cinq disciplines de la gouvernance cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez les cinq disciplines de gouvernance cloud dans le cadre de l’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: f072870caf18eb460ccc3a34e02d7d1f44872406
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223148"
---
# <a name="the-five-disciplines-of-cloud-governance"></a>Les cinq disciplines de la gouvernance cloud

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsI">
    <li style="display: flex; flex-direction: column;">
        <div class="cardSize">
            <div class="cardPadding" style="padding-bottom:10px;">
                <div class="card" style="padding-bottom:10px;">
                    <div class="cardText" style="padding-left:0px;">
Toute modification apportée à des processus métier ou à des plates-formes technologiques présente un risque. Les équipes de gouvernance cloud, dont les membres sont parfois appelés gardiens du cloud, sont chargées de minimiser ces risques et d’interrompre au minimum l’adoption et l’innovation.<br/><br/>Le modèle de gouvernance du cadre d’adoption du cloud guide ces décisions (indépendamment de la plateforme cloud choisie) en se concentrant sur le <a href="./corporate-policy.md">développement d’une stratégie d’entreprise</a> et les <a href="#disciplines-of-cloud-governance">cinq disciplines de gouvernance cloud</a>. Les <a href="./guides/index.md">guides de conception actionnables</a> illustrent ce modèle qui utilise des services Azure. Découvrez les disciplines du modèle de gouvernance cloud du cadre d’adoption du cloud.
                    </div>
                </div>
            </div>
        </div>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="../_images/operational-transformation-govern-highres.png" style="display: flex; flex-direction: column; flex: 1 0 auto;">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardText" style="padding-left:0px;">
    <img src="../_images/operational-transformation-govern-highres.png" alt="Diagram of the Cloud Adoption Framework governance model: Corporate policy and governance disciplines">
    <br>
    <i>Figure 1 - Diagramme de la stratégie d’entreprise et les cinq disciplines de la gouvernance cloud.</i>
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="disciplines-of-cloud-governance"></a>Disciplines de gouvernance cloud

Quelle que soit la plateforme cloud, il existe des disciplines de gouvernance communes qui contribuent à éclairer les stratégies et à aligner les chaînes d’outils. Ces disciplines orientent les décisions en matière de niveau d’automatisation et de mise en œuvre de la stratégie d’entreprise entre plateformes cloud.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsA">
<li style="display: flex; flex-direction: column;">
    <a href="./cost-management/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/cost-management.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Cost Management</h3>
                        <p>Les coûts constituent une préoccupation majeure pour les utilisateurs du cloud. Développez des stratégies de contrôle des coûts pour toutes les plateformes cloud.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./security-baseline/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/security-baseline.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Base de référence de la sécurité</h3>
                        <p>La sécurité est un sujet complexe propre à chaque entreprise. Une fois les exigences de sécurité définies, les stratégies de gouvernance cloud sont appliquées aux configurations réseau, données et ressources.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./identity-baseline/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/identity-baseline.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Base de référence des identités</h3>
                        <p>En matière d'application des exigences d'identité, les incohérences peuvent augmenter le risque de violation. La discipline Base de référence des identités veille à ce que l’identité soit appliquée de manière cohérente à toutes les tâches d’adoption du cloud.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./resource-consistency/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/resource-consistency.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Cohérence des ressources</h3>
                        <p>Les opérations cloud dépendent d’une configuration cohérente des ressources. Les outils de gouvernance permettent de configurer de manière cohérente les ressources afin de gérer les risques d’intégration, de détectabilité et de récupération.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./deployment-acceleration/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../_images/govern/deployment-acceleration.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Accélération du déploiement</h3>
                        <p>La centralisation, la standardisation et la cohérence des approches de déploiement et de configuration améliorent les pratiques de gouvernance. Lorsqu’elles sont disponibles via des outils de gouvernance cloud, elles créent un facteur cloud qui permet d’accélérer les activités de déploiement.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->
