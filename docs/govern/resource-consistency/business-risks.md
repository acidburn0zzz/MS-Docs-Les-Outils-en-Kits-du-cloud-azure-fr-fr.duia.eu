---
title: Risques métier et motivations associés à la discipline Cohérence des ressources
description: Utilisez le Framework d’adoption du cloud pour Azure pour comprendre ce qu’est, pour un client type, l’adoption d’une discipline de cohérence des ressources dans le cadre d’une stratégie de gouvernance cloud.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 17b39eba50b11ee1124e174f3bc89f3e6dada3e2
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83218252"
---
# <a name="motivations-and-business-risks-in-the-resource-consistency-discipline"></a>Risques métier et motivations associés à la discipline Cohérence des ressources

Cet article décrit les raisons pour lesquelles les clients adoptent une discipline Cohérence des ressources au sein d’une stratégie de gouvernance cloud. Des exemples sur les risques métier potentiels pouvant conduire à la rédaction d’instructions de stratégie sont également présentés.

<!-- markdownlint-disable MD026 -->

## <a name="relevance"></a>Pertinence

En matière de déploiement de ressources et de charges de travail, le cloud offre davantage d’agilité et de flexibilité par rapport à la plupart des centres de données locaux traditionnels. Toutefois, ces avantages potentiels liés au cloud sont également associés à d’éventuels inconvénients en termes de gestion, qui peuvent grandement compromettre la réussite de votre adoption du cloud. Quelles ressources avez-vous déployées ? Quelles équipes possèdent quelles ressources ? Avez-vous suffisamment de ressources pour héberger une charge de travail ? Comment savez-vous que les charges de travail sont intègres ?

La cohérence des ressources est essentielle pour garantir que les ressources sont déployées, mises à jour et configurées de manière homogène et renouvelable et s’assurer que les interruptions de service sont réduites et corrigées aussi vite que possible.

La discipline Cohérence des ressources se charge d’identifier et d’atténuer les risques métier associés aux aspects opérationnels de votre déploiement cloud. La cohérence des ressources comprend l’analyse des applications, charges de travail et performances des ressources. Elle inclut également les tâches nécessaires pour répondre aux demandes de mise à l’échelle, fournir des fonctionnalités de récupération d'urgence, atténuer les violations de Contrat de niveau de service (SLA) de performances et prévenir de façon proactive les violations de ces SLA par le biais de la correction automatisée.

Dans le cadre des déploiements de test initiaux, vous aurez seulement besoin d’adopter certaines normes de marquage et d’affectation de noms rapides pour répondre à vos besoins en matière de cohérence des ressources. Dès que votre adoption du cloud gagnera en maturité et que vous déploierez des ressources critiques de plus en plus complexes, le besoin d’investir dans la discipline Cohérence des ressources s’intensifie rapidement.

## <a name="business-risk"></a>Risque métier

La discipline Cohérence des ressources tente de répondre aux principaux risques métier opérationnels. Collaborez avec vos équipes métier et informatiques pour identifier ces risques et surveiller la pertinence de chacun d’entre eux lors de la planification et de l’implémentation de vos déploiements cloud.

Les risques diffèrent en fonction de l’organisation, mais ceux présentés ci-dessous peuvent vous servir à lancer des discussions au sein de votre équipe de gouvernance cloud :

- **Coûts opérationnels inutiles.** Des ressources obsolètes ou inutilisées, ou des ressources surapprovisionnées quand la demande est faible génèrent des coûts opérationnels inutiles.
- **Ressources sous-provisionnées.** Les ressources faisant l’objet d’une demande plus élevée que celle anticipée peuvent causer des interruptions de l’activité, car les ressources cloud se retrouvent submergées par cette demande.
- **Gestion inefficace.** L’absence de cohérence dans le marquage et le nommage des métadonnées associées aux ressources peut compliquer le travail du personnel informatique. Celui-ci peut en effet perdre du temps à rechercher les ressources des tâches de gestion ou à identifier les informations relatives à la propriété ou à la comptabilité des ressources. La gestion perd en efficacité, ce qui peut engendrer une augmentation des coûts et ralentir l’équipe informatique dans son travail de traitement des interruptions de service et autres problèmes opérationnels.
- **Interruption de l’activité.** Les interruptions de service entraînant des violations des SLA de votre organisation peuvent conduire à une perte d’activité et avoir d’autres impacts financiers pour votre entreprise.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de discipline Cohérence des ressources](./template.md), documentez les risques métier susceptibles d’être introduits par le plan d’adoption du cloud actuel.

Une fois tous les risques métier réalistes appréhendés, l’étape suivante consiste à documenter la tolérance de l’activité aux risques, ainsi que les indicateurs et métriques clés permettant de surveiller cette tolérance.

> [!div class="nextstepaction"]
> [Comprendre les indicateurs, les métriques et la tolérance au risque](./metrics-tolerance.md)
