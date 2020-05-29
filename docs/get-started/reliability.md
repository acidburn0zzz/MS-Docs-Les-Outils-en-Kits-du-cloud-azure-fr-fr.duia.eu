---
title: 'Bien démarrer : Améliorer la fiabilité avec les contrôles appropriés'
description: Découvrez les principes fondamentaux de l’amélioration de la fiabilité grâce aux contrôles de gouvernance et à une base de référence de gestion.
author: JanetCThomas
ms.author: janet
ms.date: 05/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 0f7ae79bbcc9fb4c02a0c9e731d2e826f4682138
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83814815"
---
# <a name="get-started-improve-reliability-with-the-right-controls"></a>Bien démarrer : Améliorer la fiabilité avec les contrôles appropriés

Comment appliquer les bons contrôles pour améliorer la fiabilité ? Cet article vous aide à réduire les interruptions en lien avec :

- Les incohérences de configuration
- L'organisation des ressources
- Les bases de référence de sécurité
- La protection des ressources

Les étapes décrites dans cet article aideront l'équipe des opérations à trouver un équilibre entre fiabilité et coûts au sein du portefeuille informatique. Cet article aidera également l'équipe de gouvernance à vérifier que cet équilibre est appliqué de manière cohérente. La fiabilité dépend également d’autres rôles et fonctions. Cet article mappe les fonctions de support pour vous aider à créer un alignement entre les équipes impliquées.

Les équipes en charge de la gestion et de la gouvernance des opérations sont des partenaires de poids équivalent dans la fiabilité de l’entreprise. Les décisions que vous prenez en matière de pratiques opérationnelles définissent la base de référence de la fiabilité. Les approches utilisées pour régir l’environnement global garantissent la cohérence entre toutes les ressources.

Les deux premières étapes de cet article aideront les deux équipes à se lancer. Elles sont présentées de manière séquentielle, mais vous pouvez les exécuter en parallèle. Les étapes qui suivront aideront l'ensemble de l'entreprise à progresser de concert vers des solutions plus fiables dans toutes ses composantes.

![Démarrer avec la fiabilité de l’entreprise](../_images/get-started/reliability-map.png)

## <a name="step-1-establish-operations-management-requirements"></a>Étape 1 : Établir des exigences de gestion des opérations

Toutes les charges de travail ne sont pas égales au moment de leur création. Dans n’importe quel environnement, il existe des charges de travail qui ont un impact direct et constant sur l’activité. Il existe également des charges de travail et des processus métier de prise en charge qui ont un impact plus faible sur l’activité globale. Au cours de cette étape, l’équipe des opérations cloud identifie et implémente les exigences initiales pour prendre en charge le portefeuille informatique global.

**Livrables :**

- Implémentez une base de référence de gestion afin de définir les opérations standard requises pour toutes les charges de travail de production.
- Négociez des engagements métier avec l’équipe de stratégie cloud afin de développer un plan pour les opérations avancées et les exigences de résilience.
- Développez votre base de référence de gestion, si des opérations supplémentaires sont nécessaires pour la majorité des charges de travail.
- Appliquez des exigences opérationnelles avancées aux zones d'atterrissage et aux ressources qui prennent en charge les charges de travail les plus critiques.
- Documentez les décisions d’opérations dans le portefeuille informatique au sein du [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Conseils relatifs aux livrables :**

- [Base de référence de gestion](../manage/considerations/discipline.md) :

  - [Inventaire et visibilité](../manage/considerations/inventory.md) : [Les outils natifs Cloud](../manage/azure-management-guide/inventory.md) peuvent vous aider à [collecter des données](../manage/monitor/data-collection.md) et à [configurer des alertes](../manage/monitor/index.md). Les outils peuvent également vous aider à implémenter la [plateforme de surveillance](../manage/monitor/index.md) qui correspond le mieux à votre modèle d'exploitation.
  - [Conformité opérationnelle](../manage/considerations/operational-compliance.md) : Les pourcentages d’interruptions les plus élevés ont tendance à être liés à des modifications de la configuration des ressources ou à des pratiques de maintenance médiocres. Suivez le [guide de gestion des serveurs Azure](../manage/azure-server-management/index.md) pour implémenter les outils natifs Cloud qui permettront de gérer les mises à jour correctives et les modifications de la configuration des ressources.
  - [Protection et récupération](../manage/considerations/protect.md) : Les pannes sont inévitables sur n’importe quelle plateforme. Si une interruption se produit, soyez prêt à la réduire avec des [solutions de sauvegarde et de récupération](../manage/azure-management-guide/protect-recover.md).
- [Opérations avancées](../manage/design-principles.md) : Appuyez-vous sur la base de référence de gestion pour vos conversations d'[alignement métier](../manage/considerations/business-alignment.md). Celle-ci vous aidera à discuter clairement de la [criticité](../manage/considerations/criticality.md), de l'[impact sur l'activité](../manage/considerations/impact.md) et des [engagements opérationnels](../manage/considerations/commitment.md). L’alignement métier aide à quantifier et à valider les demandes d’une [base de référence améliorée](../manage/azure-management-guide/enhanced-baseline.md), la gestion de [plateformes technologiques spécifiques](../manage/azure-management-guide/workload-specialization.md) ou les [opérations propres aux charges de travail](../manage/azure-management-guide/platform-specialization.md).
- **Guider une évaluation de l’architecture :** Des changements d’architecture au niveau de la charge de travail peuvent être nécessaires pour répondre aux exigences des opérations. [Microsoft Azure Well-Architected Framework](https://docs.microsoft.com/azure/architecture/framework/cost/tradeoffs) et [Microsoft Azure Well-Architected Review](https://docs.microsoft.com/assessments?id=azure-architecture-review) peuvent guider ces conversations avec le propriétaire technique d'une charge de travail spécifique.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe des opérations cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-2-consistently-apply-the-management-baseline"></a>Étape 2 : Appliquer de manière cohérente la base de référence de gestion

La fiabilité de l’entreprise nécessite une application cohérente de la base de référence de gestion. Cette cohérence repose sur une stratégie d'entreprise, des processus informatiques et des outils automatisés appropriés. Ces ressources régissent l'implémentation de la base de référence de gestion pour toutes les ressources concernées.

**Livrables :**

- Garantissez l’application correcte de la base de référence de gestion pour tous les systèmes concernés.
- Documentez vos conseils de conception, processus et stratégies de cohérence des ressources dans le [modèle de discipline Cohérence des ressources](../govern/resource-consistency/template.md).

**Conseils relatifs aux livrables :**

- Vérifiez que toutes les charges de travail et ressources respectent les [conventions d'affectation de noms et de balisage appropriées](../ready/azure-best-practices/naming-and-tagging.md). [Appliquez les conventions de balisage à l'aide d'Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/govern-tags), avec un accent particulier sur les balises de criticité.
- Si vous débutez en matière de gouvernance cloud, établissez des [disciplines, des processus et des stratégies de gouvernance](../govern/index.md) à l'aide de la méthodologie de gouvernance.
- Si vous débutez dans la discipline Gestion des coûts, suivez les conseils de l'article consacré aux [améliorations de la gestion des coûts](../govern/guides/complex/cost-management-improvement.md). Concentrez-vous sur la section portant sur l'[implémentation](../govern/guides/complex/cost-management-improvement.md#incremental-improvement-of-the-best-practices).

> [!NOTE]
> **Étapes pour démarrer des partenariats de fiabilité avec d’autres équipes :** Diverses décisions tout au long du cycle de vie de l’adoption du cloud peuvent avoir un impact direct sur la fiabilité. Les étapes suivantes mettent en relief les partenariats et les efforts de soutien nécessaires pour assurer une fiabilité constante dans l'ensemble du portefeuille informatique.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-3-define-your-strategy"></a>Étape 3 : Définir votre stratégie

Les décisions stratégiques ont une incidence directe sur la fiabilité. Elles se répercutent sur le cycle de vie de l'adoption et sur les opérations à long terme. La clarté stratégique améliore les efforts de fiabilité.

**Livrables :**

- Enregistrer les motivations, les résultats et les justifications métier dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).
- Vérifier que la base de référence de gestion fournit un soutien opérationnel aligné sur l'orientation stratégique d'adoption du cloud.

**Conseils relatifs aux livrables :**

- [Comprendre les motivations](../strategy/motivations.md) : Les événements métier critiques et certaines motivations de migration ont tendance à être sensibles aux coûts. Ces domaines peuvent accroître l'importance du contrôle des coûts pour tous les efforts ultérieurs D'autres motivations tournées vers l'avenir, liées à l'innovation ou à la croissance au travers de la migration, sont susceptibles d'être davantage axées sur le chiffre d'affaires. L'identification des motivations vous aidera à déterminer la priorité à accorder à la gestion des coûts.
- [Résultats opérationnels](../strategy/business-outcomes/index.md) : Certains résultats budgétaires ont tendance à être extrêmement sensibles aux coûts. Lorsque les résultats souhaités correspondent aux métriques budgétaires, vous devez investir tôt dans la discipline de gouvernance Gestion des coûts.
- [Justification métier :](../strategy/cloud-migration-business-case.md) La justification métier fait office de vue générale du plan financier global pour l'adoption du cloud. Il peut s'agir d'une source intéressante pour les efforts de budgétisation initiaux.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-4-develop-a-cloud-adoption-plan"></a>Étape 4 : Développer un plan d’adoption du cloud

Le patrimoine numérique (ou l'analyse du portefeuille informatique existant) peut vous aider à valider la justification métier. Il peut fournir une vue précise du portefeuille informatique global. Le plan d’adoption offre une clarté quant au calendrier des activités pendant l’adoption.

L'alignement de ce plan et de l'analyse du patrimoine numérique permet de planifier les futures dépendances de la gestion des opérations. Le fait de comprendre le plan d'adoption invite également l'équipe chargée des opérations cloud à intégrer le cycle de développement. Elle peut ensuite évaluer et planifier les modifications de la base de référence de gestion qui sont nécessaires pour fournir des opérations de charge de travail.

**Livrables :**

- Mettez à jour le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) afin qu'il reflète les changements nécessaires à l'application de la stratégie souhaitée. Les changements enregistrés peuvent inclure :

  - Une évaluation du patrimoine numérique existant
  - Un plan d'adoption du cloud reflétant les changements nécessaires et le travail impliqué
  - Le changement organisationnel nécessaire pour respecter le plan
  - Un plan pour aborder les compétences nécessaires au bon accomplissement du travail requis par l'équipe existante
- Collaborez avec l'équipe de gouvernance pour aligner les modèles de coûts et les modèles de prévision. Ce processus comprend des efforts permettant de commencer à optimiser les dépenses grâce à une analyse quantitative.

**Conseils relatifs aux livrables :**

- [Collecter l’inventaire](../digital-estate/inventory.md) : Établissez une source de données pour l’analyse du patrimoine numérique avant l’adoption.
- [Meilleures pratiques - Azure Migrate](../plan/contoso-migration-assessment.md) : Utilisez Azure Migrate pour collecter l’inventaire.
- [Rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) : Au cours de la rationalisation incrémentielle, une analyse quantitative peut identifier les candidats au cloud à des fins de budgétisation.
- [Aligner les modèles de coût et les modèles de prévision](../digital-estate/calculate.md): Utilisez Azure Cost Management pour aligner les modèles de coût et de prévision en [élaborant des budgets](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json).
- [Créer votre plan d’adoption du cloud](../plan/plan-intro.md#build-your-cloud-adoption-plan) : Créez un plan avec des détails de calendrier, de charges de travail et de ressources actionnables.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-5-implement-landing-zone-best-practices"></a>Étape 5 : Implémenter les bonnes pratiques pour les zones d’atterrissage

La méthodologie de préparation (Ready) du Cloud Adoption Framework pour Azure se concentre principalement sur le développement de zones d'atterrissage pour héberger des charges de travail dans le cloud. Pendant l’implémentation des zones d’atterrissage, plusieurs décisions peuvent affecter les opérations. Consultez l’équipe des opérations cloud afin qu’elle vous aide à évaluer la zone d’atterrissage et à déterminer si des améliorations peuvent être apportées aux opérations. Consultez également l'équipe de gouvernance cloud pour identifier les stratégies Cohérence des ressources et les conseils de conception susceptibles d'affecter la conception de la zone d'atterrissage.

**Livrables :**

- Déployer une ou plusieurs zones d'atterrissage capables d'héberger des charges de travail dans le cadre du plan d'adoption à court terme.
- Vérifier que toutes les zones d'atterrissage répondent aux décisions opérationnelles et aux exigences de cohérence des ressources.

**Conseils relatifs aux livrables :**

- [Améliorer les opérations de zone d’atterrissage](../ready/considerations/landing-zone-operations.md) : Bonnes pratiques pour l’amélioration des opérations au sein d’une zone d’atterrissage donnée.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe des opérations cloud <li> Équipe de stratégie cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-6-complete-waves-of-adoption-effort-and-change"></a>Étape 6 : Achever les vagues de l’effort d’adoption et des changements

Les opérations à long terme peuvent être affectées par les décisions prises pendant les efforts de migration et d’innovation. Le maintien d'un alignement cohérent au début des processus d'adoption permet de lever les obstacles à la mise en production. Il réduit également l'effort nécessaire pour introduire de nouvelles solutions dans les pratiques de gestion des opérations.

**Livrables :**

- Tester la disponibilité opérationnelle des déploiements de production à l'aide de stratégies Cohérence des ressources.
- Valider le respect des exigences des opérations et de la conception de la cohérence des ressources.
- Documenter les exigences des opérations avancées dans le [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Conseils relatifs aux livrables :**

- [Liste de vérification de la préparation de l’environnement](../migrate/migration-considerations/prerequisites/planning-checklist.md)
- [Liste de vérification de la prépromotion](../migrate/migration-considerations/optimize/ready.md)
- [Liste de vérification de la mise en production](../migrate/migration-considerations/optimize/promote.md)

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud <li> Équipe des opérations cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="value-statement"></a>Énoncé de la valeur

Ces étapes vous aident à implémenter les contrôles et les processus nécessaires pour garantir la fiabilité dans l'entreprise et toutes les ressources hébergées.
