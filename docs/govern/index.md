---
title: Gouvernance dans le Framework d’adoption du cloud Microsoft pour Azure
description: Utilisez le Cloud Adoption Framework pour Azure pour apprendre à évaluer les stratégies existantes, à créer une fondation de gouvernance initiale et à ajouter des outils de gouvernance de manière itérative.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5c5ba323856ef3eb9612c7abdd733bfa32c6725f
ms.sourcegitcommit: 7660521b631ea092fb805df9c9d28ad3024287ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83620500"
---
# <a name="governance-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Gouvernance dans le Framework d’adoption du cloud Microsoft pour Azure

Le cloud crée de nouveaux paradigmes pour les technologies sur lesquelles s’appuie l’entreprise. Ces nouveaux paradigmes changent également la façon dont ces technologies sont adoptées, gérées et régies. Alors qu’il est désormais possible de virtuellement déconstruire et recréer un centre de données avec une seule ligne de code exécutée à partir d’un processus sans assistance, nous devons repenser les approches traditionnelles. Ceci est particulièrement vrai pour la gouvernance.

La gouvernance du cloud est un processus itératif. Pour les organisations qui disposent déjà de stratégies régissant les environnements informatiques locaux, la gouvernance cloud vient en complément de ces stratégies. Cependant, le niveau d’intégration entre les stratégies d’entreprise locales et cloud varie en fonction de la maturité de la gouvernance cloud et du patrimoine numérique dans le cloud. Les processus de gouvernance et les stratégies cloud changent au même rythme que le patrimoine cloud. Les exercices suivants vous aident à commencer à créer les bases initiales de votre gouvernance.

<!-- markdownlint-disable MD033 -->

| | |
|---|---|
| <br> ![1](../_images/icons/1.png) | <br> [Méthodologie](./methodology.md) : Appréhendez les notions élémentaires de la méthodologie pilotant la gouvernance cloud dans le Framework d’adoption du cloud pour commencer à réfléchir à la solution de l’état final. |
| <br> ![2](../_images/icons/2.png) | <br> [Référence](./benchmark.md) : Évaluez votre état actuel et l’état futur afin d’établir une vision pour l’application du framework. |
| <br> ![3](../_images/icons/3.png) | <br> [Fondation de gouvernance initiale](./initial-foundation.md) : Commencez votre parcours de gouvernance avec un petit ensemble d’outils de gouvernance facilement implémenté. Cette base de gouvernance initiale est appelée « produit minimum viable » (MVP, Minimum Viable Product).                                |
| <br> ![4](../_images/icons/4.png) | <br> [Améliorer la fondation de gouvernance initiale](./foundation-improvements.md) : Tout au long de l’implémentation du plan d’adoption du cloud, ajoutez de manière itérative des contrôles de gouvernance afin de gérer les risques tangibles à mesure que vous avancez vers l’état final. |

## <a name="objective-of-this-content"></a>Objectif de ce contenu

Les instructions de cette section du Framework d’adoption du cloud visent deux objectifs :

- Proposer des exemples de guides de gouvernance exploitables qui représentent des expériences communes souvent rencontrées par les clients. Chacun de ces exemples inclut les risques métiers, les stratégies d’entreprise pour l’atténuation des risques et des conseils de conception pour implémenter des solutions techniques. Par définition, les conseils de conception sont propres à Azure. Tout le reste du contenu de ces guides peut être appliqué dans le cadre d’une approche indépendante du cloud ou multicloud.
- Vous aide à créer des solutions de gouvernance personnalisées capables de satisfaire différents besoins métiers, notamment la gouvernance de plusieurs clouds publics grâce à des instructions détaillées sur le développement de stratégies, processus et outils appliqués à l’entreprise.

Ce contenu est destiné à être utilisé par l’équipe de gouvernance cloud. Il peut également servir aux architectes du cloud qui cherchent à développer des fondements solides pour la gouvernance cloud.

## <a name="intended-audience"></a>Public concerné

Le contenu du Framework d’adoption du cloud touche l’activité, la technologie et la culture des entreprises. Cette section du Framework d’adoption du cloud implique d’interagir énormément avec les équipes de la sécurité informatique, de la gouvernance informatique, de la finance, des responsables métier, du réseau, des identités et de l’adoption du cloud. Plusieurs dépendances sont à noter entre ces acteurs et nécessitent une approche de facilitation de la part des architectes cloud qui utilisent ce guide. Cette approche de facilitation auprès de ces équipes peut constituer un effort unique. Dans certains cas, il en résulte des interactions avec ces autres membres du personnel.

L’architecte du cloud joue le rôle de facilitateur et de leader d’opinion pour rassembler tous ces publics. Le contenu figurant dans cette collection de guides est conçu pour aider l’architecte cloud à adapter les discussions en fonction des publics et ainsi prendre les décisions nécessaires. La transformation métier rendue possible par le cloud dépend des conseils donnés par l’architecte du cloud aux équipes métier et informatiques.

**Spécialisation Architecte du cloud dans cette section :** Chaque section du Framework d’adoption du cloud représente une spécialisation ou une variante différente du rôle de l’architecte cloud. La présente section du Framework d’adoption du cloud s’adresse aux architectes du cloud qui se passionnent pour l’atténuation ou la réduction des risques techniques. Des fournisseurs cloud nomment ces spécialistes des _concierges du cloud_, mais nous préférons les appeler _gardiens du cloud_ ou _équipe de gouvernance cloud_. Chacun des guides de gouvernance exploitables comporte des articles détaillant la composition et le rôle de l’équipe de gouvernance cloud et son évolution au fil du temps.

## <a name="use-this-guide"></a>Utiliser ce guide

La lecture de bout en bout du contenu de méthodologie de la gouvernance vous aide à mettre en œuvre une stratégie de gouvernance du cloud solide parallèlement avec l’implémentation du cloud. Les différentes instructions vous guident à travers la théorie et la mise en pratique de cette stratégie.

Pour un cours théorique accéléré et un accès rapide à l’implémentation Azure, commencez avec la [Vue d’ensemble des guides de gouvernance](./guides/index.md). Grâce à ces guides, vous pouvez commencer pas à pas et améliorer de façon itérative vos besoins de gouvernance en même temps que vos efforts d’adoption du cloud.
