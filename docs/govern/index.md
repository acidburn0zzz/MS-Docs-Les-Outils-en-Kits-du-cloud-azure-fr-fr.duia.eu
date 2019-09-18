---
title: Gouvernance dans le Framework d’adoption du cloud Microsoft pour Azure
description: Découvrez plus en détail la gouvernance dans le Framework d’adoption du cloud Microsoft pour Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 899306c60be3750cd6165763a63d1d5b1f5eb0a6
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025789"
---
# <a name="governance-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Gouvernance dans le Framework d’adoption du cloud Microsoft pour Azure

Le cloud crée de nouveaux paradigmes pour les technologies sur lesquelles s’appuie l’entreprise. Ces nouveaux paradigmes changent également la façon dont ces technologies sont adoptées, gérées et régies. Alors qu’il est désormais possible de virtuellement déconstruire et recréer un centre de données avec une seule ligne de code exécutée à partir d’un processus sans assistance, nous devons repenser les approches traditionnelles. Ceci est particulièrement vrai pour la gouvernance.

## <a name="get-started-with-cloud-governance"></a>Bien démarrer avec la gouvernance cloud

La gouvernance du cloud est un processus itératif. Pour les organisations qui disposent déjà de stratégies régissant les environnements informatiques locaux, la gouvernance cloud vient en complément de ces stratégies. Cependant, le niveau d’intégration entre les stratégies d’entreprise locales et cloud varie en fonction de la maturité de la gouvernance cloud et du patrimoine numérique dans le cloud. Les processus de gouvernance et les stratégies cloud changent au même rythme que le patrimoine cloud. Les exercices suivants vous aident à commencer à créer les bases initiales de votre gouvernance.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./methodology.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Méthodologie</h3>
Appréhendez les notions élémentaires de la méthodologie pilotant la gouvernance cloud dans le Framework d’adoption du cloud pour commencer à réfléchir à la solution de l’état final.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./benchmark.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Référence</h3>
Évaluez votre état actuel et l’état futur afin d’établir une vision pour l’application du framework.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./initial-foundation.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Fondation de gouvernance initiale</h3>
Commencez votre parcours de gouvernance avec un petit ensemble d’outils de gouvernance facilement implémenté. Cette base de gouvernance initiale est appelée « produit minimum viable » (MVP, Minimum Viable Product).
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./foundation-improvements.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Améliorer la fondation de gouvernance initiale</h3>
Tout au long de l’implémentation du plan d’adoption du cloud, ajoutez de manière itérative des contrôles de gouvernance afin de gérer les risques tangibles à mesure que vous avancez vers l’état final.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="objective-of-this-content"></a>Objectif de ce contenu

Les instructions de cette section du Framework d’adoption du cloud visent deux objectifs :

- Proposer des exemples de guides de gouvernance exploitables qui représentent des expériences communes souvent rencontrées par les clients. Chacun de ces exemples inclut les risques métiers, les stratégies d’entreprise pour l’atténuation des risques et des conseils de conception pour implémenter des solutions techniques. Par définition, les conseils de conception sont propres à Azure. Tout le reste du contenu de ces guides peut être appliqué dans le cadre d’une approche indépendante du cloud ou multicloud.
- Vous aide à créer des solutions de gouvernance personnalisées capables de satisfaire différents besoins métiers, notamment la gouvernance de plusieurs clouds publics grâce à des instructions détaillées sur le développement de stratégies, processus et outils appliqués à l’entreprise.

Ce contenu est destiné à être utilisé par l’équipe de gouvernance cloud. Il peut également servir aux architectes du cloud qui cherchent à développer des fondements solides pour la gouvernance cloud.

## <a name="intended-audience"></a>Public concerné

Le contenu du Framework d’adoption du cloud touche l’activité, la technologie et la culture des entreprises. Cette section du Framework d’adoption du cloud implique d’interagir énormément avec les équipes de la sécurité informatique, de la gouvernance informatique, de la finance, des responsables métier, du réseau, des identités et de l’adoption du cloud. Plusieurs dépendances sont à noter entre ces acteurs et nécessitent une approche de facilitation de la part des architectes cloud qui utilisent ce guide. Cette approche de facilitation auprès de ces équipes peut constituer un effort unique. Dans certains cas, il en résulte des interactions avec ces autres membres du personnel.

L’architecte du cloud joue le rôle de facilitateur et de leader d’opinion pour rassembler tous ces publics. Le contenu figurant dans cette collection de guides est conçu pour aider l’architecte cloud à adapter les discussions en fonction des publics et ainsi prendre les décisions nécessaires. La transformation métier rendue possible par le cloud dépend des conseils donnés par l’architecte du cloud aux équipes métier et informatiques.

**Spécialisation Architecte du cloud dans cette section :** Chaque section du Framework d’adoption du cloud représente une spécialisation ou une variante différente du rôle de l’architecte cloud. La présente section du Framework d’adoption du cloud s’adresse aux architectes du cloud qui se passionnent pour l’atténuation ou la réduction des risques techniques. Des fournisseurs cloud nomment ces spécialistes des *concierges du cloud*, mais nous préférons les appeler *gardiens du cloud* ou *équipe de gouvernance cloud*. Chacun des guides de gouvernance exploitables comporte des articles détaillant la composition et le rôle de l’équipe de gouvernance cloud et son évolution au fil du temps.

## <a name="use-this-guide"></a>Utiliser ce guide

Si vous souhaitez suivre ce guide du début à la fin, ce contenu vous aide à développer une stratégie de gouvernance cloud fiable en même temps que vous implémentez le cloud. Les différentes instructions vous guident à travers la théorie et la mise en pratique de cette stratégie.

Pour un cours théorique accéléré et un accès rapide à l’implémentation Azure, commencez avec la [Vue d’ensemble des guides de gouvernance](./guides/index.md). Grâce à ces guides, vous pouvez commencer pas à pas et améliorer de façon itérative vos besoins de gouvernance en même temps que vos efforts d’adoption du cloud.

## <a name="next-steps"></a>Étapes suivantes

Appréhendez les notions élémentaires de la méthodologie pilotant la gouvernance cloud dans le Framework d’adoption du cloud.

> [!div class="nextstepaction"]
> [Comprendre la méthodologie](./methodology.md)
