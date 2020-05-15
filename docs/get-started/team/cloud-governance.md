---
title: 'Bien démarrer : Créer une équipe de gouvernance cloud'
description: Établissez le cadre et les livrables de l’équipe de gouvernance ainsi que les capacités nécessaires pour préparer une gouvernance cloud réussie.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.topic: conceptual
ms.date: 04/04/2020
ms.openlocfilehash: 5b1d1cb9213b40242e95af60bead9ef3a919054a
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230381"
---
<!-- docsTest:ignore Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template -->

# <a name="get-started-build-a-cloud-governance-team"></a>Bien démarrer : Créer une équipe de gouvernance cloud

Une équipe de gouvernance cloud garantit que les risques et la tolérance aux risques sont évalués et gérés correctement. Cette équipe garantit une identification correcte des risques que l’entreprise ne peut pas tolérer. Les membres de cette équipe convertissent les risques en stratégies d’entreprise de gouvernance.

![Bien démarrer avec la création d’une équipe de gouvernance cloud](../../_images/get-started/governance-team-map.png)

## <a name="step-1-determine-if-a-cloud-governance-team-is-needed"></a>Étape 1 : Déterminer si une équipe de gouvernance cloud est nécessaire

Les recommandations officielles du Cloud Adoption Framework stipulent qu’il faut toujours créer une équipe de gouvernance cloud. Dans un premier temps, cette équipe peut être très petite. Toutefois, quelle que soit sa taille, ce rôle s’avèrera important. Si une équipe n’est pas nécessaire, un groupe ou un membre d’équipe doit accepter d’assumer les responsabilités associées aux [fonctions de gouvernance cloud](../../organize/cloud-governance.md).

**Livrables :**

- Déterminer si vous avez besoin d’une équipe de gouvernance cloud.
- Documenter la décision et les personnes responsables dans le modèle [RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx) sous l’onglet Alignement de l’organisation.

**Conseils relatifs aux livrables :**

- Les [fonctions de gouvernance cloud](../../organize/cloud-governance.md) peuvent être déjà réparties entre plusieurs personnes ou équipes. Avoir une équipe intitulée « Équipe de gouvernance cloud » ne revêt que peu d’importance. Toutefois, les capacités requises doivent être liées à un tiers ou une équipe responsable.
- Si la stratégie d’adoption du cloud à long terme de l’entreprise peut être livrée à partir d’une zone d’atterrissage dans un environnement cloud, le volume des efforts de gouvernance et d’exploitation peut être suffisamment petit pour être remis par une personne ou une équipe. Cette équipe est peu susceptible de porter le titre d’« Équipe de gouvernance cloud », puisqu’elle remplit de nombreuses fonctions au-delà de la gouvernance cloud. Même pour cette équipe, le guide de démarrage suivant permet de s’assurer qu’elle est prête à remplir cette fonction importante de gouvernance.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud |

## <a name="step-2-align-with-other-teams"></a>Étape 2 : Aligner avec d’autres équipes

L’équipe de gouvernance garantit la cohérence et l’adhésion à un ensemble de stratégies communes. Ces stratégies proviennent d’un alignement continu avec d’autres équipes. Avant de mettre en place des stratégies ou une gouvernance cloud automatisée, l’équipe de gouvernance cloud doit collaborer avec d’autres équipes identifiées dans le modèle RACI afin de garantir l’alignement sur des sujets critiques tels que la sécurité, le coût, les performances, les opérations et le déploiement. Les étapes 4 et 5 peuvent aider à faciliter l’alignement.

**Livrables :**

- Discuter de l’implémentation actuelle et des plans d’adoption actuels avec chaque équipe.

**Conseils relatifs aux livrables :**

- Passez en revue le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) de votre entreprise avec les membres de l’équipe de stratégie cloud pour comprendre les motivations, les métriques et la stratégie.
- Passez en revue le [modèle de plan d’adoption du cloud](../../plan/template.md) de votre entreprise avec les membres de l’équipe d’adoption du cloud pour comprendre les calendriers et la hiérarchisation.
- Consultez le [classeur Operations Management](https://raw.githubusercontent.com/microsoft/cloudadoptionframework/master/manage/opsmanagementworkbook.xlsx) de l’équipe d’exploitation pour comprendre les engagements et les conditions d’exploitation qui ont été établis avec l’entreprise.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-3-establish-a-cadence-with-other-teams"></a>Étape 3 : Établir une cadence avec d’autres équipes

L’adoption du cloud s’effectue généralement par vagues (ou mises en production). Une cadence régulière alignée sur ces mises en production permettra à l’équipe de gouvernance cloud de prévoir la suite et de comprendre les risques qui seront introduits dans la prochaine vague. Le fait de rester en contact étroit avec les équipes d’exploitation, de stratégie et d’adoption au cours de la planification et de la révision aidera l’équipe de gouvernance à anticiper les risques.

**Livrables :**

- Établir une cadence avec chacune des équipes de support. Dans la mesure du possible, aligner cette cadence sur les cycles de mise en production et de planification.
- Établir une cadence distincte directement avec l’équipe de stratégie cloud (ou plusieurs membres de l’équipe) afin de passer en revue les risques associés à la prochaine vague d’adoption et de mesurer le niveau de tolérance envers ces risques.

**Conseils relatifs aux livrables :**

- Pour obtenir des conseils supplémentaires sur le respect des cadences, consultez les [fonctions de la gouvernance cloud](../../organize/cloud-governance.md#deliverable).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe des opérations cloud |

## <a name="step-4-review-the-methodology"></a>Étape 4 : Passer en revue la méthodologie

Passez en revue la méthodologie de gouvernance du Cloud Adoption Framework afin de vous aider à mettre en place une vision d’avenir pour la gouvernance et une approche de travail permettant de concrétiser cette vision.

**Livrables :**

- Se familiariser avec la méthodologie, l’approche et l’implémentation qui prend en charge la méthodologie de gouvernance.

**Conseils relatifs aux livrables :**

- Passez en revue la [méthodologie de gouvernance](../../govern/methodology.md).

**Équipe responsable :**

- L’équipe de gouvernance cloud est responsable de l’établissement d’une vision et d’une approche de la gouvernance.

## <a name="step-5-complete-the-governance-benchmark"></a>Étape 5 : Terminer le benchmark de gouvernance

La gouvernance est un vaste sujet. Cette évaluation rapide peut vous aider à comprendre où commencer.

**Livrables :**

- Effectuer l’évaluation de benchmark de gouvernance en fonction des conversations avec les différentes parties prenantes (ou demander à d’autres équipes d’effectuer elles-mêmes l’évaluation).

**Conseils relatifs aux livrables :**

- Évaluez vos besoins de gouvernance et vos priorités avec [le benchmark de gouvernance](../../govern/benchmark.md).

**Équipe responsable :**

- L’équipe de gouvernance cloud doit comprendre les lacunes identifiées dans le benchmark de gouvernance et fournir un plan directeur en matière de gouvernance susceptible de combler ces lacunes.

## <a name="step-6-implement-the-initial-governance-best-practice-and-configuration"></a>Étape 6 : Implémenter les bonnes pratiques et la configuration initiales en matière de gouvernance

La méthodologie de gouvernance comprend deux approches d’une fondation de gouvernance initiale. Passez en revue chacune d’elles et implémentez celle qui correspond le mieux à vos besoins.

**Livrables :**

- Déployer les configurations d’organisation et les outils de gouvernance de base nécessaires pour régir l’environnement lors des quelques prochaines vagues d’efforts d’adoption.

**Conseils relatifs aux livrables :**

- Passez en revue les [bonnes pratiques initiales](../../govern/initial-foundation.md) relatives à la configuration et à l’implémentation.

**Équipe responsable :**

- L’équipe de gouvernance cloud est responsable de l’examen et de l’implémentation des bonnes pratiques de gouvernance et d’une fondation de gouvernance initiale.

## <a name="step-7-continuously-improve-the-governance-maturity"></a>Étape 7 : Améliorer en permanence la maturité de la gouvernance

Les besoins de gouvernance augmentent à mesure que les phases supplémentaires d’adoption du cloud sont terminées. Maintenez l’alignement avec le plan d’adoption actuel afin de garantir que l’approche de la gouvernance est capable de maintenir les niveaux de gouvernance et de contrôle appropriés.

**Livrables :**

- Implémenter des améliorations de la gouvernance pour se protéger en cas d’évolution des risques et des besoins de gouvernance.

**Conseils relatifs aux livrables :**

- Implémentez des [scénarios de gouvernance étendus](../../govern/foundation-improvements.md) pour améliorer la fondation de gouvernance initiale.

**Équipe responsable :**

- L’équipe de gouvernance cloud est responsable de l’alignement avec les plans d’adoption actuels.

## <a name="step-8-evaluate-landing-zone-changes"></a>Étape 8 : Évaluer les changements de zone d’atterrissage

À mesure que les zones d’atterrissage sont déployées et développées, de nouveaux risques ou violations de gouvernance peuvent émerger. Examinez régulièrement les configurations de zone d’atterrissage afin d’identifier les écarts par rapport à la stratégie qui ne sont pas interceptés par les outils de gouvernance natifs du cloud. Vérifiez que chaque déploiement de zone d’atterrissage respecte les recommandations en matière de gouvernance de zone d’atterrissage.

**Livrables :**

- Aider l’équipe de plateforme cloud à développer des améliorations des zones d’atterrissage qui sont conformes aux stratégies de gouvernance.

**Conseils relatifs aux livrables :**

- Améliorez la [gouvernance des zones d’atterrissage](../../ready/considerations/landing-zone-governance.md).

**Équipe responsable :**

- L’équipe de gouvernance cloud doit s’assurer que chaque déploiement de zone d’atterrissage respecte les règles de gouvernance.

## <a name="step-9-adoption-handoffs"></a>Étape 9 : Transferts d’adoption

À mesure que de nouveaux efforts d’adoption sont terminés, l’équipe d’adoption du cloud transfère les responsabilités opérationnelles à l’équipe des opérations cloud et aux équipes de gouvernance cloud. Maintenez l’alignement avec les mises en production d’adoption afin de garantir un alignement correct de la documentation et des stratégies pour assumer la responsabilité des charges de travail.

**Livrables :**

- Passer en revue et accepter régulièrement les transferts à partir des équipes d’adoption du cloud.

**Conseils relatifs aux livrables :**

- Établissez un processus pour l’[intégration des nouvelles charges de travail et ressources](https://docs.microsoft.com/azure/azure-resource-manager/custom-providers/concepts-resource-onboarding).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipes d’adoption du cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud |

## <a name="whats-next"></a>Étapes suivantes

Chaque entreprise est unique, il en va de même pour ses besoins en matière de gouvernance. Choisissez le niveau de maturité adapté à votre organisation et utilisez le Framework d’adoption du cloud pour sélectionner les pratiques, les processus et les outils qui vont vous aider à y parvenir.

Au fur et à mesure que la gouvernance cloud mûrit, les équipes sont en mesure d’adopter le cloud selon un rythme plus rapide. Les efforts continus en matière d’adoption du cloud ont tendance à faire mûrir les opérations informatiques. Développez une [équipe des opérations cloud](./cloud-operations.md) ou collaborez étroitement avec votre équipe des opérations cloud pour vous assurer que la gouvernance fait partie du développement des opérations.
