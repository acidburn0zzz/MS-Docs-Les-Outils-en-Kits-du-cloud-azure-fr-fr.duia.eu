---
title: Présentation de la discipline Base de référence des identités
description: Découvrez l’approche à adopter pour élaborer une discipline Ligne de base des identités dans le cadre d’une stratégie de gouvernance du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 92e793e2df89bbb70fe51fd7af9ef8fc1456ffa2
ms.sourcegitcommit: 7660521b631ea092fb805df9c9d28ad3024287ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83620655"
---
# <a name="identity-baseline-discipline-overview"></a>Présentation de la discipline Base de référence des identités

La base de référence des identités est l’une des [Cinq disciplines de la gouvernance du cloud](../governance-disciplines.md) dans le [modèle de gouvernance Cloud Adoption Framework](../index.md). L’identité est de plus en plus considérée comme le périmètre de sécurité principal dans le cloud, ce qui constitue un changement par rapport à l’approche traditionnelle de la sécurité réseau. Les services d’identité fournissent les mécanismes de base de contrôle d’accès et d’organisation au sein des environnements informatiques, et la discipline Base de référence des identités vient en complément de la [discipline Base de référence de la sécurité](../security-baseline/index.md) en implémentant de manière cohérente les exigences d’authentification et d’autorisation aux tâches d’adoption du cloud.

> [!NOTE]
> La discipline Ligne de base des identités ne remplace pas les équipes, les processus et les procédures informatiques existants qui permettent à votre entreprise de gérer et de sécuriser les services d’identité. L’objectif principal de cette discipline est d’identifier les risques métier potentiels liés aux identités et de fournir des conseils sur l’atténuation des risques au personnel informatique responsable de l’implémentation, de la gestion et de l’exploitation de votre infrastructure de gestion des identités. Lorsque vous élaborez des stratégies et des processus de gouvernance, veillez à faire participer les équipes informatiques pertinentes à vos processus de planification et de révision.

Cette section des lignes directrices du Framework d’adoption du cloud décrit l’approche à adopter pour élaborer une discipline Base de référence des identités dans le cadre de votre stratégie de gouvernance cloud. Ce guide s’adresse principalement aux architectes cloud de votre organisation et aux autres membres de votre équipe de gouvernance cloud. Cependant, les décisions, les stratégies et les processus qui découlent de cette discipline doivent impliquer un engagement et des discussions avec les membres concernés des équipes informatiques responsables de l’implémentation et de l’administration de vos solutions de gestion des identités.

Si votre organisation manque d’expertise interne en matière de sécurité et d’identités, envisagez de faire appel à des consultants externes pour y remédier. Envisagez également de faire appel aux [Services de conseil Microsoft](https://www.microsoft.com/industry/services/consulting), au service d’adoption du cloud [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) ou à des partenaires externes pour aborder les préoccupations liées à cette discipline.

## <a name="policy-statements"></a>Policy statements

Les déclarations de stratégie exploitables et les exigences d’architecture qui en résultent constituent la base d’une discipline Base de référence des identités. Pour prendre connaissance des exemples de déclarations de stratégie, consultez l’article [Déclarations des stratégies Ligne de base des identités](./policy-statements.md). Ces exemples peuvent servir de point de départ à l’élaboration de stratégies de gouvernance de votre organisation.

> [!CAUTION]
> Les exemples de stratégies émanent de l’expérience commune des clients. Pour mieux corréler ces stratégies aux besoins spécifiques de gouvernance cloud, exécutez les étapes suivantes afin de créer des instructions stratégiques qui répondent aux besoins particuliers de votre entreprise.

## <a name="develop-governance-policy-statements"></a>Développer des instructions de stratégie de gouvernance

Les six étapes suivantes offrent des exemples et des options potentielles à prendre en compte lors de l’élaboration de la discipline Ligne de base des identités. Chaque étape peut servir de thème de discussion au sein de votre équipe de gouvernance, et avec les équipes concernées et les équipes informatiques de votre organisation, en vue d’établir les stratégies et processus nécessaires à la gestion des risques liés aux identités.

<!-- markdownlint-disable MD033 -->

| | |
|---|---|
| <br> ![Icône Modèle](../../_images/govern/process-template.png)   | <br> [Modèle de discipline Base de référence des identités](./template.md) : Télécharger le modèle pour documenter une discipline Base de référence des identités. |
| <br> ![Icône Risques](../../_images/govern/process-risks.png)         | <br> [Risques métier](./business-risks.md) : Appréhendez les motivations et les risques généralement associés à la discipline Base de référence des identités. |
| <br> ![Icône Métriques](../../_images/govern/process-metrics.png)     | <br> [Indicateurs et métriques](./metrics-tolerance.md) : Indicateurs permettant de déterminer à quel moment il est pertinent d’investir dans la discipline Base de référence des identités. |
| <br> ![Icône Adhérence](../../_images/govern/process-enforce.png)   | <br> [Processus d’adhésion à la stratégie](./compliance-processes.md) : Suggestions de processus pour appuyer la conformité aux stratégies dans la discipline Base de référence des identités. |
| <br> ![Icône Maturité](../../_images/govern/process-maturity.png)   | <br> [Maturité](./discipline-improvement.md) : Aligner la maturité de la gestion du cloud avec les phases d’adoption du cloud. |
| <br> ![Icône Chaîne d’outils](../../_images/govern/process-toolchain.png) | <br> [Chaîne d’outils](./toolchain.md) : Services Azure qui peuvent être implémentés pour soutenir la discipline Base de référence des identités. |

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Étapes suivantes

Commencez par évaluer les [risques commerciaux](./business-risks.md) dans un environnement spécifique.

> [!div class="nextstepaction"]
> [Comprendre les risques métier](./business-risks.md)
