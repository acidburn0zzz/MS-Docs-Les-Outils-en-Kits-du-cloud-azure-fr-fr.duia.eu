---
title: Présentation de la discipline Cohérence des ressources
description: Découvrez l’approche à adopter pour élaborer une discipline Cohérence des ressources dans le cadre d’une stratégie de gouvernance du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 56cfb87e16b54e3b8b7dd72f482a085a2eee34ff
ms.sourcegitcommit: 7660521b631ea092fb805df9c9d28ad3024287ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83621270"
---
# <a name="resource-consistency-discipline-overview"></a>Présentation de la discipline Cohérence des ressources

La cohérence des ressources est une des [Cinq disciplines de gouvernance du cloud](../governance-disciplines.md) dans le [modèle de gouvernance Cloud Adoption Framework](../index.md). Elle se concentre sur les moyens à utiliser pour établir des stratégies en lien avec la gestion opérationnelle d’un environnement, d’une application ou d’une charge de travail. Les équipes des opérations informatiques offrent souvent une analyse des applications, des charges de travail et des performances des ressources. En général, elles exécutent également les tâches nécessaires pour répondre aux demandes de mise à l’échelle, corriger les violations de SLA et prévenir de façon proactive les violations de contrat de niveau de service de performances via la correction automatisée. Parmi les Cinq disciplines de gouvernance du cloud, la discipline Cohérence des ressources permet de garantir que les ressources sont configurées de manière cohérente, de sorte qu’elles sont découvrables par le service informatique, sont incluses dans les solutions de récupération et peuvent être intégrées à des processus opérationnels reproductibles.

> [!NOTE]
> La discipline Cohérence des ressources ne remplace pas les équipes, les processus et les procédures informatiques existants qui permettent à votre organisation de gérer efficacement les ressources basées sur le cloud. L’objectif principal de cette discipline est d’identifier les risques métier potentiels et de fournir des conseils sur l’atténuation des risques au personnel informatique responsable de la gestion de vos ressources dans le cloud. Lorsque vous élaborez des stratégies et des processus de gouvernance, veillez à faire participer les équipes informatiques pertinentes à vos processus de planification et de révision.

Cette section du Framework d’adoption du cloud explique comment développer une discipline Cohérence des ressources dans le cadre de votre stratégie de gouvernance cloud. Ce guide s’adresse principalement aux architectes cloud de votre organisation et aux autres membres de votre équipe de gouvernance cloud. Cependant, les décisions, les stratégies et les processus qui découlent de cette discipline doivent impliquer un engagement et des discussions avec les membres concernés des équipes informatiques responsables de l’implémentation et de l’administration de vos solutions de cohérence des ressources.

Si votre organisation manque d’expertise interne en matière de stratégies de cohérence des ressources, envisagez de faire appel à des consultants externes pour y remédier. Envisagez également de faire appel aux [Services de conseil Microsoft](https://www.microsoft.com/industry/services/consulting), au service d’adoption du cloud [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) ou à des experts de l’adoption du cloud externes pour aborder les thèmes relatifs à l’organisation, au suivi et à l’optimisation de vos ressources basées sur le cloud.

## <a name="policy-statements"></a>Policy statements

Les instructions de stratégie exploitables et les exigences d’architecture qui en résultent constituent le fondement d’une discipline Cohérence des ressources. Pour prendre connaissance des exemples d’instructions de stratégie, consultez l’article [Instructions sur les stratégies Cohérence des ressources](./policy-statements.md). Ces exemples peuvent servir de point de départ à l’élaboration de stratégies de gouvernance de votre organisation.

> [!CAUTION]
> Les exemples de stratégies émanent de l’expérience commune des clients. Pour mieux corréler ces stratégies aux besoins spécifiques de gouvernance cloud, exécutez les étapes suivantes afin de créer des instructions stratégiques qui répondent aux besoins particuliers de votre entreprise.

## <a name="develop-governance-policy-statements"></a>Développer des instructions de stratégie de gouvernance

Les six étapes suivantes offrent des exemples et des options potentielles à prendre en compte lors de l’élaboration de votre discipline Cohérence des ressources. Chaque étape peut servir de point de départ de la discussion au sein de votre équipe de gouvernance du cloud et avec les équipes concernées et les équipes informatiques de votre organisation, en vue d’établir les stratégies et processus nécessaires à la gestion des risques liés à la discipline Cohérence des ressources.

<!-- markdownlint-disable MD033 -->

| | |
|---|---|
| <br> ![Icône Modèle](../../_images/govern/process-template.png) | <br> [Modèle de discipline Cohérence des ressources](./template.md) : Télécharger le modèle pour documenter la discipline Cohérence des ressources. |
| <br> ![Icône Risques](../../_images/govern/process-risks.png) | <br> [Risques métier](./business-risks.md) : Appréhendez les motivations et les risques généralement associés à la discipline Cohérence des ressources. |
| <br> ![Icône Métriques](../../_images/govern/process-metrics.png) | <br> [Indicateurs et métriques](./metrics-tolerance.md) : Indicateurs permettant de déterminer à quel moment il est pertinent d’investir dans la discipline Cohérence des ressources. |
| <br> ![Icône Adhérence](../../_images/govern/process-enforce.png) | <br> [Processus d’adhésion à la stratégie](./compliance-processes.md) : Suggestions de processus pour appuyer la conformité aux stratégies dans la discipline Cohérence des ressources. |
| <br> ![Icône Maturité](../../_images/govern/process-maturity.png) | <br> [Maturité](./discipline-improvement.md) : Aligner la maturité de la gestion du cloud avec les phases d’adoption du cloud.  |
| <br> ![Icône Chaîne d’outils](../../_images/govern/process-toolchain.png) | <br> [Chaîne d’outils](./toolchain.md) : Services Azure qui peuvent être implémentés pour soutenir la discipline Cohérence des ressources. |

## <a name="next-steps"></a>Étapes suivantes

Commencez par évaluer les [risques commerciaux](./business-risks.md) dans un environnement spécifique.

> [!div class="nextstepaction"]
> [Comprendre les risques métier](./business-risks.md)
