---
title: Gestion de cloud
description: Découvrez comment développer les approches commerciales et techniques nécessaires à une gestion efficace du cloud à l’aide du Cloud Adoption Framework pour Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 8a33ae2b86c7e78b4148e656f56080c403c5db47
ms.sourcegitcommit: 7660521b631ea092fb805df9c9d28ad3024287ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83621280"
---
# <a name="cloud-management-in-the-cloud-adoption-framework"></a>Gestion de cloud dans le Framework d’adoption du cloud

Le suivi d’une [stratégie de cloud](../strategy/index.md) nécessite une planification, une préparation et une adoption solides. Mais c’est l’exploitation continue des ressources numériques qui offre des résultats tangibles pour l’entreprise. Sans la planification d’opérations de solutions cloud fiables et bien gérées, ces efforts offrent peu de valeur. Les exercices suivants vous aident à développer les approches métier et techniques nécessaires pour fournir une gestion de cloud qui dynamise les opérations continues.

## <a name="get-started"></a>Bien démarrer

Pour vous préparer à cette phase du cycle d’adoption du cloud, le framework suggère les exercices suivants :

<!-- markdownlint-disable MD033 -->

| | |
|---|---|
| <br> ![1](../_images/icons/1.png) | <br> [Établir une base de référence de gestion](./azure-management-guide/index.md) : Définissez les classifications de criticité, les outils de gestion de cloud et les processus requis pour respecter votre engagement minimal en termes de gestion des opérations.                                |
| <br> ![2](../_images/icons/2.png) | <br> [Définir des engagements métier](./considerations/business-alignment.md) : Documentez les charges de travail prises en charge pour établir des engagements opérationnels avec l’entreprise et convenez des investissements de gestion de cloud pour chaque charge de travail.                                |
| <br> ![3](../_images/icons/3.png) | <br> [Développer la base de référence de gestion](./best-practices.md) : En fonction des engagements métier et des décisions opérationnelles, tirez parti des bonnes pratiques incluses pour mettre en œuvre les outils de gestion de cloud requis.                                |
| <br> ![4](../_images/icons/4.png) | <br> [Principes de conception et d’opérations avancés](./design-principles.md) : Les plateformes ou charges de travail nécessitant un niveau d’engagement métier plus élevé peuvent nécessiter un examen approfondi de l’architecture pour respecter les engagements en matière de résilience et de fiabilité.  |

Les étapes précédentes créent des approches actionnables pour suivre la méthodologie de gestion du Framework d’adoption du cloud.

<!-- cSpell:ignore CAF -->

![Méthodologie de gestion dans le Framework d’adoption du cloud](../_images/manage/caf-manage.png)

Comme évoqué l’article sur l’[alignement de l’entreprise](./considerations/business-alignment.md), toutes les charges de travail ne sont pas critiques. Tout portefeuille comprend différents niveaux de besoins de gestion opérationnelle. Les efforts d’alignement de l’entreprise facilitent la capture de l’impact commercial et la négociation des coûts de gestion avec l’entreprise afin de garantir les outils et les processus de gestion opérationnelle les plus appropriés.

Les instructions de la section de gestion du Framework d’adoption du cloud visent deux objectifs :

- Proposer des exemples d’approches actionnables de gestion des opérations qui représentent des expériences communes souvent rencontrées par les clients.
- Vous aider à créer des solutions de gestion personnalisées en fonction des engagements métier.

Ce contenu est destiné à être utilisé par l’équipe des opérations cloud. Il peut également servir aux architectes du cloud qui cherchent à développer des fondements solides pour les opérations cloud ou les principes de conception du cloud.

Le contenu du Framework d’adoption du cloud touche l’activité, la technologie et la culture des entreprises. Cette section du Framework d’adoption du cloud implique d’interagir énormément avec les équipes des opérations informatiques, de la gouvernance informatique, de la finance, des responsables métier, du réseau, des identités et de l’adoption du cloud. Plusieurs dépendances sont à noter entre ces acteurs et nécessitent une approche de facilitation de la part des architectes cloud qui utilisent ce guide. Cette approche de facilitation auprès de ces équipes constitue rarement un effort unique.

L’architecte du cloud joue le rôle de facilitateur et de leader d’opinion pour rassembler tous ces publics. Le contenu figurant dans cette collection de guides est conçu pour aider l’architecte cloud à adapter les discussions en fonction des publics et ainsi prendre les décisions nécessaires. La transformation métier rendue possible par le cloud dépend des conseils donnés par l’architecte du cloud aux équipes métier et informatiques.

Chaque section du Framework d’adoption du cloud représente une spécialisation ou une variante différente du rôle de l’architecte cloud. La présente section du Framework d’adoption du cloud s’adresse aux architectes du cloud qui se passionnent pour les opérations et la gestion de solutions de déploiement. Au sein de ce framework, ces spécialistes sont souvent désignés sous le terme d’_opérations cloud_ ou collectivement comme l’_équipe des opérations cloud_.

Si vous souhaitez suivre ce guide du début à la fin, ce contenu vous aide à développer une stratégie des opérations cloud fiable. Les différentes instructions vous guident à travers la théorie et la mise en pratique de cette stratégie.

Vous pouvez aussi appliquer la méthodologie pour [Établir des engagements métier clairs](./considerations/business-alignment.md).

<!-- TODO: For a crash course on the theory and quick access to Azure implementation, get started with the [governance guides overview](TODO). Using this guidance, you can start small and iteratively improve your governance needs in parallel with cloud adoption efforts. -->
