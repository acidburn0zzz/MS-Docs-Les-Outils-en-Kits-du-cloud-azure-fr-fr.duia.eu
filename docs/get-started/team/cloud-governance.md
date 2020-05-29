---
title: 'Bien démarrer : Créer une équipe chargée de la gouvernance cloud'
description: Établissez le cadre et les livrables de l’équipe de gouvernance ainsi que les capacités nécessaires pour préparer une gouvernance cloud réussie.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.topic: conceptual
ms.date: 05/15/2020
ms.openlocfilehash: f27ca49738a987780729b9354e9a4653d5ecafcd
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83814237"
---
# <a name="get-started-build-a-cloud-governance-team"></a>Bien démarrer : Créer une équipe chargée de la gouvernance cloud

Une équipe de gouvernance cloud veille à ce que les risques et la tolérance aux risques en matière d'adoption cloud soient évalués et gérés correctement. L’équipe identifie les risques que l'entreprise ne peut tolérer, et les convertit en stratégies de gouvernance d'entreprise.

![Bien démarrer avec la création d’une équipe de gouvernance cloud](../../_images/get-started/governance-team-map.png)

## <a name="step-1-determine-whether-a-cloud-governance-team-is-needed"></a>Étape 1 : Déterminer si une équipe de gouvernance cloud est nécessaire

Les recommandations officielles du Cloud Adoption Framework pour Azure stipulent qu’il faut toujours créer une équipe de gouvernance cloud. Dans un premier temps, l'équipe peut être très petite. Quelle que soit sa taille, son rôle s’avèrera important. Si une équipe n’est pas nécessaire, un groupe ou un membre d’équipe existante doit accepter d’assumer les responsabilités associées aux [fonctions de gouvernance cloud](../../organize/cloud-governance.md).

**Livrables :**

- Déterminer si vous avez besoin d’une équipe de gouvernance cloud.
- Documentez la décision et les personnes responsables dans le [modèle RACI (Réalisateur, Approbateur, Consulté, Informé)](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx) de la feuille de calcul `Org Alignment`.

**Conseils relatifs aux livrables :**

- Les [fonctions de gouvernance cloud](../../organize/cloud-governance.md) peuvent être déjà réparties entre plusieurs personnes ou équipes. Avoir une équipe intitulée « Équipe de gouvernance cloud » ne revêt que peu d’importance, mais les capacités requises doivent être liées à un tiers ou une équipe responsable.
- Si la stratégie d’adoption du cloud à long terme de l’entreprise peut être livrée à partir d’une zone d’atterrissage dans un environnement cloud, le volume des efforts de gouvernance et d’exploitation peut être suffisamment petit pour être remis par une personne ou une équipe. Cette équipe est peu susceptible de porter le titre d’« Équipe de gouvernance cloud », puisqu’elle remplit de nombreuses fonctions au-delà de la gouvernance cloud. Même pour cette équipe, ce guide de démarrage permet de s’assurer qu’elle est en mesure de remplir cette fonction importante de gouvernance.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud |

## <a name="step-2-align-with-other-teams"></a>Étape 2 : Aligner avec d’autres équipes

L’équipe de gouvernance garantit la cohérence et l’adhésion à un ensemble de stratégies communes. Ces stratégies proviennent d’un alignement continu avec d’autres équipes.

Avant de mettre en place des stratégies ou une gouvernance cloud automatisée, l’équipe de gouvernance cloud doit collaborer avec d’autres équipes identifiées dans le modèle RACI et ce, afin de garantir l’alignement sur des sujets critiques tels que la sécurité, le coût, les performances, les opérations et le déploiement. Les étapes 4 et 5 contribuent à faciliter l’alignement.

**Livrables :**

- Discutez de l’implémentation de l'état et des plans d’adoption actuels avec chaque équipe.

**Conseils relatifs aux livrables :**

- Passez en revue le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) de votre entreprise avec les membres de l’équipe de stratégie cloud pour comprendre les motivations, les métriques et la stratégie.
- Passez en revue le [modèle de plan d’adoption du cloud](../../plan/template.md) de votre entreprise avec les membres de l’équipe d’adoption du cloud pour comprendre les calendriers et la hiérarchisation.
- Consultez le [classeur Operations Management](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) de l’équipe d’exploitation pour comprendre les engagements et les conditions d’exploitation qui ont été établis avec l’entreprise.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-3-establish-a-cadence-with-other-teams"></a>Étape 3 : Établir une cadence avec d’autres équipes

L’adoption du cloud s’effectue généralement par vagues ou mises en production. Une cadence régulière alignée sur ces mises en production permet à l’équipe de gouvernance cloud de prévoir la suite et de comprendre les risques qui seront introduits dans la prochaine vague. Le fait de rester en contact étroit avec les équipes d’exploitation, de stratégie et d’adoption au cours de la planification et de la révision aide aussi l’équipe de gouvernance à anticiper les risques.

**Livrables :**

- Établissez une cadence les équipes de soutien. Dans la mesure du possible, alignez cette cadence sur les cycles de mise en production et de planification.
- Établissez une cadence distincte directement avec l’équipe de stratégie cloud (ou plusieurs membres de l’équipe) afin de passer en revue les risques associés à la prochaine vague d’adoption et de mesurer le niveau de tolérance de l'équipe envers ces risques.

**Conseils relatifs aux livrables :**

- Pour plus d’informations sur les cadences des réunions, consultez [Fonctions de gouvernance cloud](../../organize/cloud-governance.md#deliverable).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe des opérations cloud |

## <a name="step-4-review-the-methodology"></a>Étape 4 : Passer en revue la méthodologie

Pour faciliter la mise en place d'une vision d’avenir pour la gouvernance et d'une approche de travail permettant de concrétiser cette vision, passez en revue la méthodologie de gouvernance du Cloud Adoption Framework.

**Livrables :**

- Se familiariser avec la méthodologie, l’approche et l’implémentation qui prend en charge la méthodologie de gouvernance.

**Conseils relatifs aux livrables :**

- Passez en revue la [méthodologie de gouvernance](../../govern/methodology.md).

**Équipe responsable :**

- L’équipe de gouvernance cloud est responsable de l’établissement d’une vision et d’une approche de la gouvernance.

## <a name="step-5-complete-the-governance-benchmark"></a>Étape 5 : Terminer le benchmark de gouvernance

La gouvernance est un vaste sujet. Une évaluation rapide peut aider l'équipe à comprendre où commencer.

**Livrables :**

- Effectuez l’évaluation de benchmark de gouvernance en fonction des conversations avec les différentes parties prenantes. Vous pouvez également demander à d’autres équipes d’effectuer elles-mêmes l’évaluation.

**Conseils relatifs aux livrables :**

- Utilisez le [benchmark de gouvernance](../../govern/benchmark.md) pour évaluer vos besoins de gouvernance et vos priorités.

**Équipe responsable :**

- L’équipe de gouvernance cloud doit comprendre les lacunes identifiées dans le benchmark de gouvernance, puis fournir un plan directeur en matière de gouvernance susceptible de combler ces lacunes.

## <a name="step-6-implement-the-initial-governance-best-practice-and-configuration"></a>Étape 6 : Implémenter les bonnes pratiques et la configuration initiales en matière de gouvernance

La méthodologie de gouvernance comprend deux approches d’une fondation de gouvernance initiale. Passez en revue chaque approche et implémentez celle qui correspond le mieux à vos besoins.

**Livrables :**

- Déployer les configurations d’organisation et les outils de gouvernance de base nécessaires pour régir l’environnement lors des quelques prochaines vagues d’efforts d’adoption.

**Conseils relatifs aux livrables :**

- Pour obtenir des conseils sur la configuration et l’implémentation, consultez [Établir une fondation de gouvernance cloud initiale](../../govern/initial-foundation.md).

**Équipe responsable :**

- L’équipe de gouvernance cloud est responsable de l’examen et de l’implémentation des bonnes pratiques de gouvernance et d’une fondation de gouvernance initiale.

## <a name="step-7-continuously-improve-governance-maturity"></a>Étape 7 : Améliorer en permanence la maturité de la gouvernance

Les besoins de gouvernance augmentent à mesure que des efforts d'adoption du cloud sont déployés. Maintenez l’alignement avec le plan d’adoption actuel afin de garantir que l’approche de la gouvernance est capable de maintenir les niveaux de gouvernance et de contrôle appropriés.

**Livrables :**

- Implémenter des améliorations de la gouvernance pour se protéger en cas d’évolution des risques et des besoins de gouvernance.

**Conseils relatifs aux livrables :**

- Pour améliorer la fondation de gouvernance initiale, implémentez des [scénarios de gouvernance étendus](../../govern/foundation-improvements.md).

**Équipe responsable :**

- L’équipe de gouvernance cloud est responsable de l’alignement avec les plans d’adoption actuels.

## <a name="step-8-evaluate-landing-zone-changes"></a>Étape 8 : Évaluer les changements de zone d’atterrissage

À mesure que les zones d’atterrissage sont déployées et développées, de nouveaux risques ou violations de gouvernance peuvent émerger. Examinez régulièrement les configurations de zone d’atterrissage afin d’identifier les écarts par rapport à la stratégie qui ne sont pas interceptés par les outils de gouvernance natifs du cloud. Vérifiez que chaque déploiement de zone d’atterrissage respecte les recommandations en matière de gouvernance de zone d’atterrissage.

**Livrables :**

- Aidez l’équipe de plateforme cloud à développer des améliorations des zones d’atterrissage qui doivent être conformes aux stratégies de gouvernance.

**Conseils relatifs aux livrables :**

- Améliorez la [gouvernance des zones d’atterrissage](../../ready/considerations/landing-zone-governance.md).

**Équipe responsable :**

- L’équipe de gouvernance cloud doit s’assurer que chaque déploiement de zone d’atterrissage respecte les règles de gouvernance.

## <a name="step-9-adoption-handoffs"></a>Étape 9 : Transferts d’adoption

À mesure que de nouveaux efforts d’adoption sont déployés, l’équipe d’adoption du cloud transfère les responsabilités opérationnelles à l’équipe des opérations cloud et aux équipes de gouvernance cloud. Maintenez l’alignement avec les cadence de mise en production d’adoption afin de garantir un alignement correct de la documentation et des stratégies et d'aider l'équipe à assumer la responsabilité des charges de travail.

**Livrables :**

- Passez en revue et acceptez régulièrement les transferts issus des autres équipes d’adoption du cloud.

**Conseils relatifs aux livrables :**

- Établissez un processus pour l’[intégration des nouvelles charges de travail et ressources](https://docs.microsoft.com/azure/azure-resource-manager/custom-providers/concepts-resource-onboarding).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et de soutien |
| --- | --- |
| <li> Équipes d’adoption du cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud |

## <a name="whats-next"></a>Étapes suivantes

Toutes les entreprises sont uniques et il en va de même pour leurs besoins en matière de gouvernance. Choisissez le niveau de maturité adapté à votre organisation et utilisez le Cloud Adoption Framework pour sélectionner les pratiques, les processus et les outils susceptibles de vous aider à y parvenir.

Plus la gouvernance cloud mûrit, plus vite les équipes sont en mesure d’adopter le cloud. Les efforts continus en matière d’adoption du cloud ont tendance à faire mûrir les opérations informatiques. Pour intégrer la gouvernance au développement opérationnel, développez une [équipe des opérations cloud](./cloud-operations.md) ou collaborez étroitement avec votre équipe des opérations cloud existante.
