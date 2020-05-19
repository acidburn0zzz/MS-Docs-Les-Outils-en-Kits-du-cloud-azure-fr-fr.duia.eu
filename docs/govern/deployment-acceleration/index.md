---
title: Vue d’ensemble de la discipline Accélération du déploiement
description: Utilisez le Cloud Adoption Framework pour Azure pour comprendre l’accélération du déploiement par rapport à la gouvernance du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6db5662a5e470730116310a291ac669192e0f3e4
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83400637"
---
# <a name="deployment-acceleration-discipline-overview"></a>Vue d’ensemble de la discipline Accélération du déploiement

L’accélération du déploiement est l’une des [cinq disciplines de la gouvernance du cloud](../governance-disciplines.md) dans le [modèle de gouvernance du Framework d’adoption du cloud](../index.md). Cette discipline met l'accent sur les moyens d'établir des stratégies pour régir la configuration ou le déploiement des ressources. Dans les cinq disciplines de la discipline Gouvernance du cloud, l’accélération du déploiement inclut le déploiement, l’alignement de la configuration et la réutilisabilité des scripts. Des activités manuelles ou des activités DevOps entièrement automatisées peuvent être utilisées. Dans les deux cas, les stratégies sont en grande partie similaires. Au fur et à mesure que cette discipline mûrit, l’équipe de gouvernance du cloud peut jouer le rôle de partenaire dans les stratégies DevOps et de déploiement, en accélérant les déploiements et en éliminant les freins à l’adoption du cloud, grâce à la mise en œuvre de ressources réutilisables.

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

| | |
|---|---|
| <br> ![Icône Modèle](../../_images/govern/process-template.png) | [Modèle de discipline Accélération du déploiement](./template.md) : Télécharger le modèle pour documenter une discipline Accélération du déploiement. |
| <br> ![Icône Risques](../../_images/govern/process-risks.png) | [Risques métier](./business-risks.md) : Appréhendez les motivations et les risques généralement associés à la discipline Accélération du déploiement.|
| <br> ![Icône Métriques](../../_images/govern/process-metrics.png) | [Indicateurs et métriques](./metrics-tolerance.md) : Indicateurs permettant de déterminer à quel moment il est pertinent d’investir dans la discipline Accélération du déploiement. |
| <br> ![Icône Adhérence](../../_images/govern/process-enforce.png) | [Processus d’adhésion à la stratégie](./compliance-processes.md) : Suggestions de processus pour appuyer la conformité aux stratégies dans la discipline Accélération du déploiement. |
| <br> ![Icône Maturité](../../_images/govern/process-maturity.png) | [Maturité](./discipline-improvement.md) : Aligner la maturité de la gestion du cloud avec les phases d’adoption du cloud.|
| <br> ![Icône Chaîne d’outils](../../_images/govern/process-toolchain.png) | [Chaîne d’outils](./toolchain.md) : Services Azure qui peuvent être implémentés pour soutenir la discipline Accélération du déploiement. |

## <a name="next-steps"></a>Étapes suivantes

Commencez par évaluer les [risques commerciaux](./business-risks.md) dans un environnement spécifique.

> [!div class="nextstepaction"]
> [Comprendre les risques métier](./business-risks.md)

<!-- markdownlint-enable MD033 -->
