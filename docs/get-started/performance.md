---
title: 'Bien démarrer : Garantir des performances cohérentes à l’échelle d’un portefeuille'
description: Découvrez les bases de la gestion des performances d'un portefeuille, notamment le maintien des performances, la définition des attentes et la création d'un alignement au sein de votre organisation.
author: JanetCThomas
ms.author: janet
ms.date: 05/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: b200fb8dee07c016338beed9b9356d00e26a8abd
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83814339"
---
# <a name="get-started-ensure-consistent-performance-across-a-portfolio"></a>Bien démarrer : Garantir des performances cohérentes à l’échelle d’un portefeuille

Comment garantir des performances adéquates dans un portefeuille de charges de travail ? Les étapes décrites dans ce guide peuvent vous aider à établir des processus pour maintenir ce niveau de performances.

Les performances dépendent également d’autres rôles et fonctions. Cet article mappe ces fonctions de support pour vous aider à créer un alignement entre les équipes impliquées.

La gestion centralisée des opérations est l’approche la plus courante pour obtenir des performances cohérentes à l’échelle du portefeuille. Les décisions relatives aux pratiques opérationnelles définissent la base de référence des opérations ainsi que toute amélioration holistique.

La première étape de ce guide permettra à l’équipe des opérations de bien démarrer. Les étapes qui suivront aideront l'ensemble de l'entreprise à progresser de concert vers des performances d'entreprise à l'échelle du portefeuille de charges de travail.

![Bien démarrer avec la gestion des performances d’entreprise](../_images/get-started/performance-map.png)

## <a name="step-1-establish-operations-management-requirements"></a>Étape 1 : Établir des exigences de gestion des opérations

La base de référence de gestion des opérations, décrite dans le cadre du Microsoft Cloud Adoption Framework pour Azure, fournit un ensemble de contrôles et d'outils d'opérations natifs du cloud pour garantir la cohérence des opérations. L'extension de cette base de référence à l'aide d'outils d'automatisation permet de superviser et d'automatiser les performances afin de répondre à des exigences de performances cohérentes à l'échelle du portefeuille.

**Livrables :**

- Améliorer la base de référence de gestion de façon à inclure des tâches de correction automatisées relatives aux écarts par rapport aux attentes de performances.
- Lorsque des modèles de données propres à la charge de travail ou des changements d'architecture sont nécessaires pour répondre aux exigences de performances, utilisez des opérations propres à la charge de travail pour assurer un meilleur contrôle des performances.
- Documentez les décisions relatives aux opérations dans le portefeuille informatique au sein du [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx). Concentrez-vous sur l'intégration des décisions d'automatisation des performances à la section **Conformité opérationnelle** de l'onglet **Base de référence**.

**Conseils relatifs aux livrables :**

- L'article consacré à la [base de référence de gestion améliorée](../manage/azure-management-guide/enhanced-baseline.md) présente des exemples d'utilisation d'outils tels qu'Azure Automation pour ajouter des améliorations liées aux performances. Cette approche peut aider à maintenir la cohérence des performances grâce à des modifications de base de la taille et de l'échelle des ressources de prise en charge.
- L'article [Opérations propres à la charge de travail](../manage/azure-management-guide/platform-specialization.md) utilise l'évaluation Découverte de Microsoft Azure Well-Architected Framework pour fournir des conseils sur l'automatisation d'une charge de travail spécifique. Cette approche de la gestion des performances est particulièrement utile lorsque des données propres à la charge de travail doivent guider les actions opérationnelles.
- Les recommandations précédentes partent du principe qu'une implémentation existante d'une [base de référence de gestion](../manage/considerations/discipline.md) prend en charge le portefeuille complet de charges de travail.

> [!NOTE]
> Diverses décisions tout au long du cycle de vie de l’adoption du cloud peuvent avoir un impact direct sur les performances. Les étapes suivantes aident à mettre en relief les partenariats et les efforts de support nécessaires pour offrir des performances cohérentes dans le portefeuille informatique.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe des opérations cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-2-consistent-application-of-the-management-baseline"></a>Étape 2 : Application cohérente de la base de référence de gestion

À mesure que la base de gestion s'améliore, il est important de s'assurer que ces améliorations profitent à la discipline de gouvernance Cohérence des ressources. Cela garantira l’application de la base de référence améliorée dans tous les environnements managés.

**Livrables :**

- Garantir l’application correcte de la base de référence de gestion améliorée pour tous les systèmes concernés.
- Documenter vos conseils de conception, processus et stratégies pour la cohérence des ressources dans le [modèle de discipline Cohérence des ressources](../govern/resource-consistency/template.md).

**Conseils relatifs aux livrables :**

- Vérifiez que toutes les charges de travail et ressources respectent les [conventions d'affectation de noms et de balisage appropriées](../ready/azure-best-practices/naming-and-tagging.md). [Appliquez les conventions de balisage à l'aide d'Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/govern-tags), avec un accent particulier sur les balises de « criticité ».
- Si vous débutez avec la gouvernance cloud, établissez des [disciplines, des processus et des stratégies de gouvernance](../govern/index.md) à l'aide de la méthodologie de gouvernance.
- Si vous débutez avec la discipline de gouvernance Gestion des coûts, vous pouvez consulter l'[article consacré aux améliorations de la gestion des coûts](../govern/guides/complex/cost-management-improvement.md), en vous concentrant sur la section portant sur l'[implémentation](../govern/guides/complex/cost-management-improvement.md#incremental-improvement-of-the-best-practices).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-3-define-strategy"></a>Étape 3 : Définir une stratégie

Les décisions stratégiques affectent directement les performances, tout au long du cycle de vie de l’adoption et jusqu’aux opérations à long terme. La clarté stratégique améliore les efforts en matière de performances dans le portefeuille. Cette clarté permet également à l'équipe des opérations de comprendre quelles charges de travail nécessitent un degré de spécialisation des charges de travail et des opérations avancées.

**Livrables :**

- Enregistrer les motivations, les résultats et les justifications métier dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).
- Vérifier que la base de référence de gestion fournit un soutien opérationnel aligné sur l'orientation stratégique d'adoption du cloud.

**Conseils relatifs aux livrables :**

- [Comprendre les motivations](../strategy/motivations.md) : Les événements métier critiques et certaines motivations de migration ont tendance à être sensibles aux coûts, ce qui accroît l'importance du contrôle des coûts pour tous les efforts ultérieurs. D'autres motivations tournées vers l'avenir, liées à l'innovation ou à la croissance au travers de la migration, sont susceptibles d'être davantage axées sur le chiffre d'affaires. L’identification des motivations peut vous aider à déterminer la propriété à accorder à la gestion des coûts.
- [Résultats opérationnels](../strategy/business-outcomes/index.md) : Certains résultats budgétaires ont tendance à être extrêmement sensibles aux coûts. Lorsque les résultats souhaités correspondent aux métriques budgétaires, vous devez investir tôt dans la discipline de gouvernance Gestion des coûts.
- [Justification métier :](../strategy/cloud-migration-business-case.md) La justification métier fait office de vue générale du plan financier pour l'adoption du cloud. Il peut s'agir d'une source intéressante pour les efforts de budgétisation initiaux.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-4-assess-and-plan-for-workload-adoption"></a>Étape 4 : Évaluer et planifier l’adoption des charges de travail

Le patrimoine numérique (ou l'analyse du portefeuille informatique existant) peut vous aider à valider la justification métier et à fournir une vue précise du portefeuille informatique. Le plan d’adoption offre une clarté quant au calendrier des activités pendant l’adoption. L'alignement de ce plan et de l'analyse du patrimoine numérique permet de planifier les futures dépendances de la gestion des opérations.

Le fait de comprendre le plan invite également l'équipe chargée des opérations cloud à intégrer le cycle de développement. L'équipe peut ensuite évaluer et planifier les modifications de la base de référence de gestion qui sont nécessaires pour fournir des opérations de charge de travail.

**Livrables :**

- Mettre à jour le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) pour refléter les modifications déclenchées par l’analyse du patrimoine numérique.
- Collaborer avec l’équipe des opérations cloud pour définir clairement la criticité et l’impact commercial de chaque charge de travail dans le plan d’adoption à court terme et à long terme.
- Collaborer avec l’équipe des opérations cloud afin d’établir un calendrier pour la préparation des opérations.

**Conseils relatifs aux livrables :**

- [Collecter l’inventaire](../digital-estate/inventory.md) : Établissez une source de données pour l'analyse du patrimoine numérique avant l'adoption.
- [Bonne pratique : Azure Migrate](../plan/contoso-migration-assessment.md). Utilisez Azure Migrate pour collecter l’inventaire.
- [Rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) : Au cours de la rationalisation incrémentielle, utilisez une analyse quantitative pour identifier les candidats au cloud à des fins de budgétisation.
- [Aligner les modèles de coût et les modèles de prévision](../digital-estate/calculate.md): Utilisez Azure Cost Management pour aligner les modèles de coût et de prévision en [élaborant des budgets](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json).
- [Créer votre plan d’adoption du cloud](../plan/plan-intro.md#build-your-cloud-adoption-plan) : Élaborez un plan avec des détails sur la charge de travail, les ressources et le calendrier.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-5-expand-the-landing-zones"></a>Étape 5 : Étendre les zones d’atterrissage

La méthodologie de préparation du Cloud Adoption Framework se concentre principalement sur le développement de zones d’atterrissage pour héberger des charges de travail dans le cloud. Lors de l'implémentation de la zone d'atterrissage, certaines décisions peuvent affecter les opérations.

Consultez l’équipe des opérations cloud afin qu’elle vous aide à évaluer la zone d’atterrissage et à déterminer si des améliorations peuvent être apportées aux opérations. Consultez également l'équipe de gouvernance cloud pour identifier les stratégies de « cohérence des ressources » et les conseils de conception susceptibles d'affecter la conception de la zone d'atterrissage.

**Livrables :**

- Déployer une ou plusieurs zones d'atterrissage susceptibles d'héberger des charges de travail dans le plan d'adoption à court terme.
- Vérifier que toutes les zones d'atterrissage répondent aux décisions opérationnelles et aux exigences de cohérence des ressources.

**Conseils relatifs aux livrables :**

- [Améliorer les opérations de zone d’atterrissage](../ready/considerations/landing-zone-operations.md) : Bonnes pratiques pour l'amélioration des opérations au sein d'une zone d’atterrissage.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe des opérations cloud <li> Équipe de stratégie cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-6-adoption"></a>Étape 6 : Adoption

Les opérations à long terme peuvent être affectées par les décisions que vous prenez dans le cadre des efforts de migration et d'innovation. Le maintien d'un alignement cohérent au début des processus d'adoption permet de lever les obstacles à la mise en production. Il réduit également l'effort nécessaire pour intégrer de nouvelles solutions dans les pratiques de gestion des opérations.

**Livrables :**

- Tester la disponibilité opérationnelle des déploiements de production à l'aide de stratégies Cohérence des ressources.
- Valider l'adhésion aux conseils de conception pour la cohérence des ressources, ainsi qu'aux exigences opérationnelles.
- Documenter les exigences des opérations avancées dans le [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Conseils relatifs aux livrables :**

- [Liste de vérification de la préparation de l’environnement](../migrate/migration-considerations/prerequisites/planning-checklist.md)
- [Liste de vérification de la prépromotion](../migrate/migration-considerations/optimize/ready.md)
- [Liste de vérification de la mise en production](../migrate/migration-considerations/optimize/promote.md)

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud <li> Équipe des opérations cloud <li> Équipe de stratégie cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="value-statement"></a>Énoncé de la valeur

Les étapes précédentes vous aideront à implémenter des contrôles et des processus pour garantir les performances de l'entreprise et de toutes les ressources hébergées.
