---
title: Classification des charges de travail avant la migration
description: Classifiez vos charges de travail quand vous effectuez une évaluation avant la migration.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 0708c394cca50c64813b7eea04a1239586c825af
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80527714"
---
# <a name="workload-classification-before-migration"></a>Classification des charges de travail avant la migration

À chaque itération d’un processus de migration, une ou plusieurs charges de travail sont migrées et promues en charges de travail de production. Avant l’une ou l’autre de ces activités de migration, il est important de classifier chaque charge de travail. La classification permet de clarifier les exigences de gouvernance, de sécurité, d’exploitation et de gestion des données.

Les conseils d’aide suivants s’appuient sur les exigences de catégorisation suggérées, décrites dans l’[article sur les standards de nommage et de catégorisation](../../../ready/azure-best-practices/naming-and-tagging.md#metadata-tags), auxquelles s’ajoutent des éléments d’[exploitation](../../../manage/considerations/criticality.md#criticality-scale) et de [gouvernance](../../../govern/guides/complex/prescriptive-guidance.md#resource-tagging) importants.

Dans cet article, nous suggérons spécifiquement d’ajouter des informations relatives à la criticité et à la sensibilité des données à vos standards de catégorisation existants. Chacun de ces points de données va aider les autres équipes à comprendre quelles sont les charges de travail qui nécessitent éventuellement une attention ou un support supplémentaire.

## <a name="data-sensitivity"></a>Sensibilité des données

Comme indiqué dans l’article sur la [classification des données](../../../govern/policy-compliance/data-classification.md), le processus de classification des données mesure l’impact d’une fuite de données sur l’entreprise ou les clients. Les équipes de gouvernance et de sécurité utilisent la sensibilité ou la classification des données en tant qu’indicateur des risques de sécurité. Durant l’évaluation, l’équipe d’adoption du cloud doit évaluer la classification des données pour chaque charge de travail ciblée dans le cadre de la migration. Elle doit également partager cette classification avec les équipes du support technique. Les charges de travail qui concernent strictement les « données publiques » n’ont pas forcément d’impact sur les équipes du support technique. Toutefois, à mesure que les données se rapprochent de l’extrémité « hautement confidentielle » du spectre, les équipes de gouvernance et de sécurité ont probablement intérêt à participer à l’évaluation de la charge de travail.

Collaborez avec vos équipes de sécurité et de gouvernance le plus tôt possible pour définir les éléments suivants :

- Processus clair pour le partage des charges de travail sur le backlog en incluant des données sensibles
- Compréhension des exigences de gouvernance et de la base de référence de sécurité nécessaires pour différents niveaux de sensibilité des données
- Impact potentiel de la sensibilité des données sur la conception de l’abonnement, les hiérarchies des groupes d’administration ou les exigences de zones d’atterrissage
- Exigences relatives aux tests de classification des données, qui peuvent inclure un ensemble d’outils spécifique ou une étendue de classification définie

## <a name="mission-criticality"></a>Criticité

Comme indiqué dans l’article sur la [criticité de la charge de travail](../../../manage/considerations/criticality.md), la criticité d’une charge de travail est une mesure de l’impact d’une panne sur l’entreprise. Ce point de données aide les équipes de gestion des opérations et de sécurité à évaluer les risques liés aux pannes et aux violations. Durant l’évaluation, l’équipe d’adoption du cloud doit évaluer la criticité de la mission de chaque charge de travail ciblée pour la migration. Elle doit également partager cette classification avec les équipes du support technique. Les charges de travail « faibles » ou « non prises en charge » sont peu susceptibles d’avoir un impact sur les équipes du support technique. Toutefois, à mesure que les charges de travail se rapprochent des classifications « Critique pour la mission » ou « Critique pour l’unité », leurs dépendances opérationnelles deviennent plus évidentes.

Collaborez avec vos équipes des opérations et de sécurité le plus tôt possible pour définir les éléments suivants :

- Processus clair pour le partage des charges de travail sur le backlog en incluant les exigences de prise en charge
- Compréhension des exigences de gestion des opérations et de cohérence des ressources pour différents niveaux de criticité
- Impact potentiel de la criticité sur la conception de l’abonnement, les hiérarchies des groupes d’administration ou les exigences de zones d’atterrissage
- Exigences relatives à la documentation de la criticité, qui peuvent inclure des rapports de trafic ou d’utilisation spécifiques, des analyses financières ou d’autres outils

## <a name="next-steps"></a>Étapes suivantes

Une fois les charges de travail correctement classifiées, il est beaucoup plus facile d’[aligner les priorités de l’entreprise](./business-priorities.md).

> [!div class="nextstepaction"]
> [Aligner les priorités de l’entreprise](./business-priorities.md)
