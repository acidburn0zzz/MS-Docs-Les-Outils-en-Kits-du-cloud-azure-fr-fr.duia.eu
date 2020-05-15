---
title: 'Bien démarrer : Améliorer la fiabilité avec les contrôles appropriés'
description: Découvrez les principes fondamentaux de l’amélioration de la fiabilité grâce aux contrôles de gouvernance et à une base de référence de gestion.
author: JanetCThomas
ms.author: janet
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 8e17c53a2a54a212fa312b62b2ff527497583919
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230469"
---
<!-- docsTest:ignore Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template -->

# <a name="get-started-improve-reliability-with-the-right-controls"></a>Bien démarrer : Améliorer la fiabilité avec les contrôles appropriés

Comment appliquer les bons contrôles pour améliorer la fiabilité ? Ce guide aide à réduire les interruptions liées aux incohérences dans la configuration, l’organisation des ressources, les bases de référence de sécurité ou la protection des ressources. Les étapes de ce guide aident l’équipe des opérations à équilibrer la fiabilité et les coûts dans le portefeuille informatique, et l’équipe de gouvernance à s’assurer que l’équilibre est appliqué de manière cohérente. La fiabilité dépend également d’autres rôles et fonctions. Cet article mappe ces différentes fonctions de support pour vous aider à créer un alignement entre chacune des équipes impliquées.

Les équipes en charge de la gestion et de la gouvernance des opérations sont des partenaires de poids équivalent dans la fiabilité de l’entreprise. Les décisions prises en matière de pratiques opérationnelles définissent la base de référence de la fiabilité. Les approches utilisées pour régir l’environnement global garantissent la cohérence entre toutes les ressources. Les deux premières étapes de ce guide aident les deux équipes à se lancer. Bien qu’elles soient listées de manière séquentielle, les étapes suivantes peuvent être effectuées en parallèle. Les étapes qui suivront aideront l’ensemble de l’entreprise à progresser de concert vers des solutions plus fiables dans toutes ses composantes.

![Démarrer avec la fiabilité de l’entreprise](../_images/get-started/reliability-map.png)

## <a name="step-1-establish-operations-management-requirements"></a>Étape 1 : Établissement des exigences de gestion des opérations

Toutes les charges de travail ne sont pas égales au moment de leur création. Dans n’importe quel environnement, il existe des charges de travail qui ont un impact direct et constant sur l’activité. Il existe également des charges de travail et des processus métier de prise en charge qui ont un impact plus faible sur l’activité globale. Au cours de cette étape, l’équipe des opérations cloud identifie et implémente les exigences initiales pour prendre en charge le portefeuille informatique global.

**Livrables :**

- Implémentez une base de référence de gestion afin de définir les opérations standard nécessaires pour toutes les charges de travail de production.
- Négociez des engagements métier avec l’équipe de stratégie cloud afin de développer un plan pour les opérations avancées et les exigences de résilience.
- Développez votre base de référence de gestion, si des opérations supplémentaires sont nécessaires pour la majorité des charges de travail.
- Appliquez des exigences d’opérations avancées aux zones d’atterrissage et aux ressources qui prennent en charge des charges de travail plus critiques.
- Documentez les décisions d’opérations dans le portefeuille informatique au sein du [classeur de gestion des opérations](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Conseils pour la prise en charge de l’achèvement des livrables :**

- **[Base de référence de gestion](../manage/considerations/discipline.md) :**

  - [Inventaire et visibilité](../manage/considerations/inventory.md) : Les [outils natifs Cloud](../manage/azure-management-guide/inventory.md) peuvent vous aider à [collecter des données](../manage/monitor/data-collection.md), à [configurer des alertes](../manage/monitor/index.md) et à implémenter la [plateforme de supervision](../manage/monitor/index.md) qui correspond le mieux à votre modèle d’exploitation.
  - [Conformité opérationnelle](../manage/considerations/operational-compliance.md) : Les pourcentages d’interruptions les plus élevés ont tendance à être liés à des modifications de la configuration des ressources ou à des pratiques de maintenance médiocres. Suivez le [guide de gestion des serveurs Azure](../manage/azure-server-management/index.md) pour mettre en œuvre les outils natifs Cloud afin de gérer les mises à jour correctives et les modifications de la configuration des ressources.
  - [Protection et récupération](../manage/considerations/protect.md) : Les pannes sont inévitables sur n’importe quelle plateforme. Si une interruption se produit, soyez prêt à la réduire avec des [solutions de sauvegarde et de récupération](../manage/azure-management-guide/protect-recover.md).

- **[Opérations avancées](../manage/design-principles.md) :** Utilisez la base de référence de gestion comme base pour les conversations sur l’[alignement métier](../manage/considerations/business-alignment.md) afin de clarifier ce qui concerne la [criticité](../manage/considerations/criticality.md), l’[impact commercial](../manage/considerations/impact.md) et les [engagements opérationnels](../manage/considerations/commitment.md). L’alignement métier aide à quantifier et à valider les demandes d’une [base de référence améliorée](../manage/azure-management-guide/enhanced-baseline.md), la gestion de [plateformes technologiques spécifiques](../manage/azure-management-guide/workload-specialization.md) ou les [opérations propres aux charges de travail](../manage/azure-management-guide/platform-specialization.md).

- **Guider une évaluation de l’architecture :** Des changements d’architecture au niveau de la charge de travail peuvent être nécessaires pour répondre aux exigences des opérations. [Azure Architecture Framework](https://docs.microsoft.com/azure/architecture/framework/cost/tradeoffs) et l’[examen de l’architecture Azure](https://docs.microsoft.com/assessments?id=azure-architecture-review) peuvent aider à guider ces conversations avec le propriétaire technique d’une charge de travail spécifique.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe des opérations cloud | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="step-2-consistently-apply-the-management-baseline"></a>Étape 2 : Appliquer de manière cohérente la base de référence de gestion

La fiabilité de l’entreprise nécessite une application cohérente de la base de référence de gestion. Cette cohérence, qui provient d’une stratégie d’entreprise appropriée, de processus informatiques et d’outils automatisés, vise à régir l’implémentation de la base de référence de gestion pour toutes les ressources affectées.

**Livrables :**

- Garantissez l’application correcte de la base de référence de gestion pour tous les systèmes concernés.
- Documentez vos conseils de conception, processus et stratégies de cohérence des ressources dans le [modèle de discipline Cohérence des ressources](../govern/resource-consistency/template.md).

**Conseils pour la prise en charge de l’achèvement des livrables :**

- Assurez-vous que toutes les charges de travail et toutes les ressources suivent des [conventions de nommage et d’étiquetage appropriées](../ready/azure-best-practices/naming-and-tagging.md) et [appliquez les conventions d’étiquetage à l’aide d’Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/govern-tags), en mettant l’accent sur les étiquettes liées à la « criticité ».
- Si vous débutez avec la gouvernance cloud, établissez des [disciplines, des processus et des stratégies de gouvernance](../govern/index.md) à l’aide de la méthodologie de gouvernance.
- Si vous débutez avec la discipline Gestion des coûts, vous pouvez consulter l’[article sur les améliorations de la gestion des coûts](../govern/guides/complex/cost-management-improvement.md), en vous concentrant sur la section consacrée à l’[implémentation](../govern/guides/complex/cost-management-improvement.md#incremental-improvement-of-the-best-practices).

> [!NOTE]
> **Étapes pour démarrer des partenariats de fiabilité avec d’autres équipes :** Diverses décisions tout au long du cycle de vie de l’adoption du cloud peuvent avoir un impact direct sur la fiabilité. Les étapes suivantes aident à mettre en relief les partenariats et les efforts de support nécessaires pour offrir une fiabilité cohérente dans le portefeuille informatique.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe des opérations cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="step-3-define-your-strategy"></a>Étape 3 : Définir votre stratégie

**Livrables :**

- Enregistrez les motivations, les résultats et les justifications métier dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).
- Assurez-vous que la base de référence de gestion fournit un support opérationnel qui s’aligne sur la direction stratégique de l’adoption du cloud.

**Conseils pour la prise en charge de l’achèvement des livrables :**

- [Comprendre les motivations](../strategy/motivations.md) : Les événements métier critiques et certaines motivations de migration ont tendance à être sensibles aux coûts, ce qui accroît l’importance du contrôle des coûts pour tous les efforts ultérieurs. D’autres motivations orientées vers l’avenir liées à l’innovation ou à la croissance au travers de la migration sont susceptibles d’être davantage axées sur le chiffre d’affaires. La compréhension des motivations vous aide à mesurer l’importance que doit avoir une gestion des postes prioritaires.
- [Résultats opérationnels](../strategy/business-outcomes/index.md) : Certains résultats budgétaires ont tendance à être extrêmement sensibles aux coûts. Quand les résultats souhaités correspondent aux métriques budgétaires, vous devez investir tôt dans la discipline de gouvernance Gestion des coûts.
- [Justification métier :](../strategy/cloud-migration-business-case.md) La justification métier fait office de vue générale du plan financier global pour l’adoption du cloud. Elle peut être une bonne source pour les efforts de budgétisation initiaux.

Les décisions stratégiques affectent directement la fiabilité, tout au long du cycle de vie de l’adoption et jusqu’aux opérations à long terme. La clarté stratégique améliore les efforts de fiabilité.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="step-4-develop-a-cloud-adoption-plan"></a>Étape 4 : Développer un plan d’adoption du cloud

Le patrimoine numérique (ou l’analyse du portefeuille informatique existant) peut vous aider à valider la justification métier et à fournir une vue précise de l’ensemble du portefeuille informatique. Le plan d’adoption offre une clarté quant à la chronologie des activités pendant l’adoption. L’alignement de ce plan et de l’analyse du patrimoine numérique permet de planifier les futures dépendances de gestion des opérations. En outre, le fait de comprendre le plan invite l’équipe des opérations cloud à prendre part aux cycles de développement pour évaluer et planifier les modifications à apporter à la base de référence de gestion, ce qui est nécessaire pour fournir des opérations de charge de travail.

**Livrables :**

- Mettez à jour le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) afin qu’il reflète les modifications nécessaires pour réaliser la stratégie souhaitée. Les modifications enregistrées peuvent inclure les éléments suivants :
  - Une évaluation du patrimoine numérique existant
  - Un plan d’adoption du cloud reflétant les modifications nécessaires et le travail impliqué
  - Le changement organisationnel nécessaire pour respecter le plan
  - Un plan pour traiter les compétences nécessaires au bon accomplissement du travail requis par l’équipe existante
- Collaborez avec l’équipe de gouvernance pour aligner les modèles de coût et les modèles de prévision, y compris les efforts pour commencer à optimiser les dépenses grâce à une analyse quantitative.

**Conseils pour la prise en charge de l’achèvement des livrables :**

- [Collecter l’inventaire](../digital-estate/inventory.md). Établissez une source de données pour l’analyse du patrimoine numérique avant l’adoption.
- [Bonne pratique : Azure Migrate](../plan/contoso-migration-assessment.md). Utilisez Azure Migrate pour collecter l’inventaire.
- [Rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) : Au cours de la rationalisation incrémentielle, une analyse quantitative peut identifier les candidats au cloud à des fins de budgétisation.
- [Aligner les modèles de coût et les modèles de prévision](../digital-estate/calculate.md). Utilisez Azure Cost Management pour aligner les modèles de coût et de prévision en [créant des budgets](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json).
- [Créer votre plan d’adoption du cloud](../plan/plan-intro.md#build-your-cloud-adoption-plan). Créez un plan avec une charge de travail, des ressources et des détails de chronologie actionnables.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="step-5-implement-landing-zone-best-practices"></a>Étape 5 : Implémenter les bonnes pratiques pour les zones d’atterrissage

La méthodologie de préparation du Cloud Adoption Framework se concentre principalement sur le développement de zones d’atterrissage pour héberger des charges de travail dans le cloud. Pendant l’implémentation des zones d’atterrissage, plusieurs décisions peuvent affecter les opérations. Consultez l’équipe des opérations cloud afin qu’elle vous aide à examiner la zone d’atterrissage pour les améliorations des opérations. Consultez également l’équipe de gouvernance cloud pour comprendre les stratégies de « cohérence des ressources » et les conseils de conception susceptibles d’affecter la conception de la zone d’atterrissage.

**Livrables :**

- Déployez une ou plusieurs zones d’atterrissage pouvant héberger des charges de travail dans le plan d’adoption à court terme.
- Vérifiez que toutes les zones d’atterrissage répondent aux décisions opérationnelles et aux exigences de cohérence des ressources.

**Conseils pour la prise en charge de l’achèvement des livrables :**

- [Améliorer les opérations de zone d’atterrissage](../ready/considerations/landing-zone-operations.md) : Bonnes pratiques pour l’amélioration des opérations au sein d’une zone d’atterrissage donnée.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe des opérations cloud <li> Équipe de stratégie cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="step-6-complete-waves-of-adoption-effort-and-change"></a>Étape 6 : Achever les vagues de l’effort d’adoption et des changements

Les opérations à long terme peuvent être affectées par les décisions prises pendant les efforts de migration et d’innovation. Le maintien d’un alignement cohérent au début des processus d’adoption aide à supprimer les obstacles aux mises en production et à réduire les efforts nécessaires pour intégrer de nouvelles solutions aux pratiques de gestion des opérations.

**Livrables :**

- Testez la disponibilité opérationnelle des déploiements de production à l’aide de stratégies de cohérence des ressources.
- Validez le respect des exigences des opérations et de la conception de la cohérence des ressources.
- Documentez les exigences des opérations avancées dans le [classeur de gestion des opérations](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx).

**Conseils pour la prise en charge de l’achèvement des livrables :**

- [Liste de vérification de la préparation de l’environnement](../migrate/migration-considerations/prerequisites/planning-checklist.md)
- [Liste de vérification de la prépromotion](../migrate/migration-considerations/optimize/ready.md)
- [Liste de vérification de la mise en production](../migrate/migration-considerations/optimize/promote.md)

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud <li> Équipe des opérations cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="value-statement"></a>Énoncé de la valeur

Les étapes ci-dessus vous aident à implémenter les contrôles et les processus appropriés nécessaires pour garantir la fiabilité dans l’entreprise et toutes les ressources hébergées.
