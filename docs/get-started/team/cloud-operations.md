---
title: 'Bien démarrer : Créer une équipe des opérations cloud'
description: Ce guide aide une équipe des opérations cloud à comprendre l’étendue, les livrables et les fonctionnalités dont elle est responsable.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.topic: conceptual
ms.date: 05/15/2020
ms.openlocfilehash: 02317405adc974e9836bb3e64b881da3296e3d8e
ms.sourcegitcommit: bd9872320b71245d4e9a359823be685e0f4047c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83862430"
---
# <a name="get-started-build-a-cloud-operations-team"></a>Bien démarrer : Créer une équipe des opérations cloud

Une équipe des opérations se concentre sur la supervision, la réparation et la correction des problèmes liés aux opérations et aux ressources informatiques traditionnelles. Dans le cloud, la plupart des dépenses d’investissement et des activités opérationnelles sont transférés vers le fournisseur de cloud, ce qui donne à l’équipe chargée des opérations informatiques la possibilité d’améliorer et de fournir une valeur ajoutée significative.

![Bien démarrer avec la création d’une équipe des opérations cloud](../../_images/get-started/operations-team-map.png)

## <a name="step-1-determine-whether-a-cloud-operations-team-is-needed"></a>Étape 1 : Déterminer si une équipe des opérations cloud est nécessaire

Avant de mettre en production des charges de travail, il convient de s'entendre sur la responsabilité des [fonctions des opérations cloud](../../organize/cloud-operations.md). Pour certains portefeuilles, les responsabilités opérationnelles peuvent rester dans les équipes DevOps et d’adoption du cloud. Pour d'autres, un fournisseur de services gérés doté d'une expérience dans le domaine des opérations cloud peut assumer la responsabilité des tâches opérationnelles en cours.

En l'absence de contrat lié aux opérations du fournisseur de services ou DevOps, on peut supposer qu'un membre du service informatique devra valider les tâches opérationnelles en cours liées à la gestion des charges de travail de production.

**Livrables :**

- Déterminez si vous avez besoin d’une équipe des opérations cloud.
- Documentez la décision et les personnes responsables dans le [modèle RACI (Réalisateur, Approbateur, Consulté, Informé)](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx) de la feuille de calcul `Org Alignment`.

**Conseils relatifs aux livrables :**

- Les [fonctions des opérations cloud](../../organize/cloud-operations.md) peuvent être déjà réparties entre plusieurs personnes ou équipes. Déterminez si une équipe des opérations cloud est nécessaire. Un certain niveau d'opérations s'impose systématiquement pour les charges de travail de production.
- Si la stratégie d’adoption du cloud à long terme de l’entreprise peut être livrée à partir d’une zone d’atterrissage dans un environnement cloud, les efforts de gouvernance et des opérations peuvent être suffisamment réduits pour être fournis par une personne ou une équipe. Il est peu probable que cette équipe soit appelée équipe des opérations cloud, car elle remplira de nombreuses fonctions. Pour cette personne ou équipe, les conseils suivants contribuent à veiller à ce qu'elle soit en mesure de remplir cette fonction importante des opérations.

<!-- markdownlint-disable MD033 -->

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud |

## <a name="step-2-align-with-other-teams"></a>Étape 2 : Aligner avec d’autres équipes

L’équipe des opérations cloud hérite des responsabilités opérationnelles de toutes les charges de travail du portefeuille de production. Ces responsabilités peuvent varier d'une charge de travail à une autre, en fonction des attentes et des engagements pris par l'équipe auprès des parties prenantes de l'entreprise. En matière d'architecture, les décisions prises par les équipes d’adoption du cloud en termes de migration et d'innovation influencent également les engagements opérationnels de ces équipes.

Avant d’implémenter les différentes pratiques opérationnelles en cours, il est important que l'équipe des opérations cloud s'aligne avec d’autres équipes. L’équipe doit collaborer avec d’autres équipes identifiées dans le modèle RACI afin de garantir l’alignement sur des sujets critiques tels que la sécurité, les coûts, les performances, la gouvernance, l'adoption et le déploiement. Les étapes 4 et 5 contribuent à faciliter cet alignement.

**Livrables :**

- Discutez de l’implémentation de l'état et des plans d’adoption actuels avec chaque équipe.

**Conseils relatifs aux livrables :**

- Pour comprendre les motivations, les métriques et la stratégie, passez en revue le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) de votre entreprise avec les membres de l’équipe de stratégie cloud.
- Pour comprendre les calendriers et la hiérarchisation, passez en revue le [modèle de plan d’adoption du cloud](../../plan/template.md) de votre entreprise avec les membres de l’équipe d’adoption du cloud.
- Pour comprendre les exigences opérationnelles et engagements établis par l'équipe avec l’entreprise, commencez à développer le [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li>  Équipe des opérations cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Centre d'excellence du cloud ou équipe informatique centrale |

## <a name="step-3-establish-a-cadence-with-other-teams"></a>Étape 3 : Établir une cadence avec d’autres équipes

L’adoption du cloud s’effectue généralement par vagues ou mises en production. Une cadence régulière alignée sur ces mises en production permet à l’équipe des opérations cloud de préparer les transferts au terme de la vague suivante. Le fait de rester en contact étroit avec les équipes de stratégie, d’adoption et de gouvernance au cours de la planification et de la révision aide l’équipe des opérations à anticiper les demandes opérationnelles.

**Livrables :**

- Établissez une cadence les équipes de soutien. Dans la mesure du possible, alignez cette cadence sur les cycles de mise en production et de planification.
- Établissez une cadence distincte directement avec l’équipe de stratégie cloud ou plusieurs de ses membres afin de passer en revue les exigences opérationnelles associées à la prochaine vague d’adoption.

**Conseils relatifs aux livrables :**

- Pour obtenir des conseils supplémentaires sur les cadences des réunions, consultez la section « livrables » des [fonctions d'opérations cloud](../../organize/cloud-operations.md#deliverables).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe des opérations cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud |

## <a name="step-4-review-the-methodology"></a>Étape 4 : Passer en revue la méthodologie

Pour mettre en place une vision d’avenir pour la gestion des opérations et une approche de travail permettant de concrétiser cette vision, passez en revue la méthodologie de gestion du Cloud Adoption Framework.

**Livrables :**

- Familiarisez-vous avec la méthodologie, l’approche et l’implémentation qui prend en charge la méthodologie de gestion.

**Conseils relatifs aux livrables :**

- Passez en revue la [méthodologie de gestion dans la Cloud Adoption Framework](../../manage/index.md).

**Équipe responsable :**

- L’équipe des opérations cloud est responsable de la vision et de l’approche en matière de gestion des opérations.

## <a name="step-5-implement-the-operations-baseline"></a>Étape 5 : Implémenter la base de référence pour les opérations

Si aucune pratique opérationnelle n’est déployée dans vos environnements cloud, commencez par la base de référence pour les opérations. Cette base de référence implémente des pratiques cloud natives « no-ops/low-ops » pour fournir un niveau de base de protection opérationnelle.

**Livrables :**

- Déployez les configurations de gestion de serveur Azure de base nécessaires pour utiliser l’environnement lors des quelques vagues d’efforts d’adoption suivantes.

**Conseils relatifs aux livrables :**

- Implémentez la configuration de [base de référence pour les opérations](../../manage/azure-server-management/index.md).

**Équipe responsable :**

- L’équipe des opérations cloud est chargée d'implémenter la base de référence pour les opérations.

## <a name="step-6-align-business-commitments"></a>Étape 6 : Aligner des engagements métier

Passez en revue les engagements de base de référence pour les opérations de l'équipe avec les parties prenant de l’entreprise. Cette base de référence vous aide à évaluer les exigences générales relatives à la plupart des charges de travail. En outre, le processus vous permet d’identifier les parties prenantes pour différentes charges de travail et de documenter leurs attentes opérationnelles en cours.

**Livrables :**

- Documentez les attentes des parties prenantes de l’entreprise.
- Déterminez si des opérations avancées sont requises pour des charges de travail ou des plateformes spécifiques.

**Conseils relatifs aux livrables :**

- Créez un [alignement de l'entreprise](../../manage/considerations/business-alignment.md) dans le cloud.
- Documentez le portefeuille et les attentes en matière d'opérations dans le [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Équipe responsable :**

- L’équipe des opérations cloud doit comprendre les attentes métier et est responsable de l’alignement en cours avec ces attentes.

## <a name="step-7-operations-maturity"></a>Étape 7 : Maturité des opérations

En procédant continuellement à des améliorations opérationnelles, l’équipe peut :

- Améliorer la base de référence pour les opérations.
- Améliorer les opérations de plateforme.
- Implémenter les opérations spécifiques aux charges de travail.

À mesure que des charges de travail supplémentaires sont transférées vers les opérations cloud, il apparaît clair que les opérations doivent être améliorées.

**Livrables :**

- Améliorez la maturité des opérations pour prendre en charge les engagements envers les parties prenantes de l'entreprise.

**Conseils relatifs aux livrables :**

- Évaluez les meilleures options en matière de [gestion des opérations avancées](../../manage/design-principles.md).

**Équipe responsable :**

- L’équipe des opérations cloud est responsable des améliorations opérationnelles et de la maturité au fil du temps.

## <a name="step-8-scale-operations-consistency-through-governance"></a>Étape 8 : Mettre à l’échelle la cohérence des opérations via la gouvernance

À mesure que la planification des opérations gagne en maturité, l'équipe doit se coordonner régulièrement avec l’équipe de gouvernance cloud pour appliquer les exigences opérationnelles à tout le portefeuille.

**Livrables :**

- Aidez l’équipe de gouvernance cloud à implémenter de nouvelles exigences en matière de cohérence des ressources.

**Conseils relatifs aux livrables :**

- Consultez le [guide de gouvernance pour améliorer la cohérence des ressources](../../govern/guides/complex/resource-consistency-improvement.md).

<!-- markdownlint-disable MD033 -->

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe des opérations cloud |

## <a name="step-9-adoption-handoffs"></a>Étape 9 : Transferts d’adoption

À mesure que de nouveaux efforts d’adoption sont déployés, l’équipe d’adoption du cloud transfère les responsabilités opérationnelles aux équipes des opérations cloud et de gouvernance cloud. Pour garantir un alignement correct de la documentation et des stratégies afin assumer la responsabilité des charges de travail, l'équipe doit maintenir l’alignement avec les mises en production d’adoption.

**Livrables :**

- Passez en revue et acceptez régulièrement les transferts issus des équipes d’adoption du cloud.

**Conseils relatifs aux livrables :**

- Établissez un processus pour l’[intégration des nouvelles charges de travail et ressources](https://docs.microsoft.com/azure/azure-resource-manager/custom-providers/concepts-resource-onboarding).

<!-- markdownlint-disable MD033 -->

| Équipe responsable | Équipes en charge et de soutien |
| --- | --- |
| <li> Équipes d’adoption du cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud |

## <a name="whats-next"></a>Étapes suivantes

Au fur et à mesure de l’évolution de l’adoption et des opérations, il est important de définir et d’automatiser les meilleures pratiques de gouvernance qui étendent les besoins informatiques existants. La formation d’un centre d’excellence du cloud est une étape importante de la mise à l’échelle de l’adoption du cloud, des opérations du cloud et des efforts de gouvernance du cloud.

Pour en savoir plus :

- [Fonctions du centre d’excellence du cloud](../../organize/cloud-center-of-excellence.md)
- [Antimodèles organisationnels : Silos et fiefs](../../organize/fiefdoms-silos.md)

Alignez les responsabilités entre les équipes en développant une matrice qui identifie les parties en charge, responsables, consultées et informées (RACI). Téléchargez et modifiez le [modèle de feuille de calcul RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx).
