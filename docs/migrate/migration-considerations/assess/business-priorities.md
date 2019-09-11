---
title: Préserver les priorités de l’entreprise durant un processus de transformation à long terme
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Préservez les priorités de l’entreprise durant un processus de transformation à long terme.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 05d9441eb8867ff47ad23ccc44a9b58d8e010499
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70839091"
---
# <a name="business-priorities---maintaining-alignment"></a>Priorités de l’entreprise – Préservation de l’alignement

Une *transformation* est souvent définie comme un changement spectaculaire ou spontané. Au niveau du tableau, un changement peut ressembler à une transformation spectaculaire. Toutefois, pour ceux qui travaillent dans le processus de changement d’une organisation, une transformation est un peu trompeuse. Sous la surface, une transformation est mieux décrite sous la forme d’une série de transitions correctement exécutées d’un état à un autre.

La durée nécessaire à la rationalisation ou à la transition d’une charge de travail varie en fonction de la complexité technique impliquée. Toutefois, même lorsque ce processus peut être appliqué rapidement à une seule charge de travail ou à un seul groupe d’applications, il faut du temps pour produire des changements substantiels parmi une base d’utilisateurs. Il faut davantage de temps pour que les changements se propagent dans les différentes couches de processus métier existants. Si l’on s’attend à ce que la transformation façonne les modèles de comportement des consommateurs, les résultats peuvent prendre plus de temps à produire des résultats significatifs.

Malheureusement, le marché n’attend pas que les entreprises fassent leur transition. Les modèles de comportement des consommateurs changent d’eux-mêmes, souvent de manière inattendue. La perception que le marché a d’une société et de ses produits peut être influencée par les réseaux sociaux ou le positionnement d’un concurrent. Les changements rapides et inattendus du marché exigent des entreprises qu’elles soient agiles et réactives.

La capacité d’exécuter des processus et des transitions techniques requiert un effort constant et stable. Des décisions rapides et des actions prestes sont nécessaires pour répondre aux conditions du marché. Ces deux éléments sont contradictoires, ce qui favorise le désalignement des priorités. Cet article décrit des approches pour préserver l’alignement transitoire pendant les efforts de migration.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-business-and-technical-priorities-stay-aligned-during-a-migration"></a>Comment les priorités techniques et celles de l’entreprise peuvent-elles rester alignées pendant une migration ?

Les équipes d’adoption du cloud et de gouvernance cloud se concentrent sur l’exécution de l’itération et de la mise en production actuelles. Les itérations fournissent des incréments stables de travail techniques, ce qui évite les interruptions coûteuses qui, sans cela, ralentiraient la progression des efforts de migration. Les mises en production garantissent que l’effort technique et l’énergie restent concentrés sur les objectifs stratégiques de la migration des charges de travail. Un projet de migration peut nécessiter de nombreuses mises en production sur une période prolongée. Au moment où il se terminera, les conditions du marché auront probablement changé de manière significative.

En parallèle, l’équipe de stratégie cloud se concentre sur l’exécution du plan des changements opérationnels et la préparation de la prochaine mise en production. L’équipe de stratégie cloud examine généralement au moins une mise en production à l’avance, surveille l’évolution des conditions de marché et ajuste le backlog de migration en conséquence. Cet accent mis sur la gestion de la transformation et l’ajustement du plan crée des pivots naturels autour du travail technique. Lorsque les priorités de l’entreprise évoluent, l’adoption est en retard d’une mise en production seulement, créant ainsi une agilité technique et commerciale.

## <a name="business-alignment-questions"></a>Questions relatives à l’alignement de l’entreprise

Les questions suivantes peuvent aider l’équipe de stratégie cloud à définir et classer par ordre de priorité le backlog de migration pour garantir que l’effort de transformation s’aligne au mieux sur les besoins actuels de l’entreprise.

- L’équipe d’adoption du cloud a-t-elle identifié une liste de charges de travail prêtes pour la migration ?
- L’équipe d’adoption du cloud a-t-elle sélectionné un candidat pour une migration initiale dans cette liste de charges de travail ?
- Les équipes d’adoption et de gouvernance cloud disposent-elles de toutes les données nécessaires concernant la réussite de la charge de travail et de l’environnement cloud ?
- La charge de travail candidate livre-t-elle l’impact le plus pertinent pour l’entreprise dans la prochaine mise en production ?
- D’autres charges de travail sont-elles de meilleures candidates à la migration ?

## <a name="tangible-actions"></a>Actions tangibles

Pendant l’exécution du plan des changements opérationnels, l’équipe de stratégie cloud surveille les résultats positifs et négatifs. Lorsque ces observations requièrent des changements techniques, les ajustements sont ajoutés à titre d’éléments de travail au backlog de mise en production pour qu’ils soient prioritaires lors de l’itération suivante.

Lorsque le marché évolue, l’équipe de stratégie cloud collabore avec l’entreprise pour comprendre comment répondre au mieux aux changements. Lorsque cette réponse requiert une modification des priorités de migration, le backlog de migration est ajusté. Cela donne la priorité aux charges de travail qui étaient précédemment moins prioritaires.

## <a name="next-steps"></a>Étapes suivantes

Grâce à des priorités de l’entreprise correctement alignées, l’équipe d’adoption du cloud peut commencer, en toute confiance, à [évaluer les charges de travail](./evaluate.md) pour développer des plans d’architecture et de migration.

> [!div class="nextstepaction"]
> [Évaluer les charges de travail](./evaluate.md)
