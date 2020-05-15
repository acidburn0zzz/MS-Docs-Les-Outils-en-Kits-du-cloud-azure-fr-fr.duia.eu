---
title: "Bien démarrer : Assurer l'excellence opérationnelle"
description: Apprenez les bases de l'excellence opérationnelle dans le cadre de la transformation numérique.
author: JanetCThomas
ms.author: janet
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 406db0eb2743b783c409c5b78ce7c2958a216548
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230489"
---
# <a name="get-started-deliver-operational-excellence-during-digital-transformation"></a>Bien démarrer : Assurer l'excellence opérationnelle dans le cadre de la transformation numérique

Comment assurer l'excellence opérationnelle dans le cadre de la transformation numérique ? L'excellence opérationnelle est une fonction métier qui influence directement les décisions informatiques. L'excellence opérationnelle consiste à créer de la valeur pour les clients et les parties prenantes, en gardant constamment à l'esprit l'impact sur le chiffre d'affaires, les risques et les coûts. Cette approche de la gestion des changements organisationnels requiert une stratégie définie, des résultats opérationnels clairs et une planification de la gestion des changements. Du point de vue du cloud, l'impact relatif aux risques et aux coûts est géré par la gestion des changements post-adoption et l'amélioration continue des processus opérationnels. Cela peut inclure l'automatisation des systèmes, les pratiques de gestion des opérations informatiques et la discipline Cohérence des ressources tout au long du cycle de vie du processus d'adoption du cloud. Les étapes décrites dans ce guide peuvent aider l'équipe chargée de la stratégie à diriger la gestion des changements organisationnels nécessaire pour garantir l'excellence opérationnelle de manière cohérente.

L'excellence opérationnelle à l'échelle de l'entreprise et du portefeuille commence par des processus de stratégie et de planification par les pairs afin d'aligner et de rendre compte des attentes en matière de gestion des changements organisationnels. Les étapes suivantes aident les équipes techniques à fournir les disciplines requises pour atteindre l'excellence opérationnelle.

![Prise en main de l'excellence opérationnelle](../_images/get-started/operational-excellence-map.png)

## <a name="step-1-define-a-strategy-to-guide-digital-transformation-and-operational-excellence-expectations"></a>Étape 1 : Définir une stratégie pour guider la transformation numérique et les attentes en matière d'excellence opérationnelle

Une stratégie d'entreprise claire est la base de toute transformation numérique et de tout effort d'excellence opérationnelle. L'équipe informatique peut réduire les coûts et rationaliser les processus informatiques, mais sans stratégie claire, il est difficile de comprendre comment ces changements peuvent affecter les résultats opérationnels visés dans le cadre de l'effort général de transformation.

**Livrables :**

- Enregistrez les motivations, les résultats et les justifications métier dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).
- Veillez à ce que les métriques d'apprentissage soient bien comprises et incluses dans la section des résultats opérationnels, car elles guideront les activités d'excellence opérationnelle et les rapports au sein de l'équipe informatique.

**Conseils relatifs aux livrables :**

- [Identifiez les motivations](../strategy/motivations.md) : Les événements métier critiques et certaines motivations de migration ont tendance à être sensibles aux coûts, ce qui accroît l'importance du contrôle des coûts pour tous les efforts ultérieurs. D'autres motivations tournées vers l'avenir, liées à l'innovation ou à la croissance au travers de la migration, sont susceptibles d'être davantage axées sur le chiffre d'affaires. L'identification des motivations vous aidera à déterminer la propriété à accorder à la gestion des coûts.
- [Résultats opérationnels](../strategy/business-outcomes/index.md) : Certains résultats budgétaires ont tendance à être extrêmement sensibles aux coûts. Lorsque les résultats souhaités correspondent aux métriques budgétaires, vous devez investir très tôt dans la discipline de gouvernance Gestion des coûts.
- [Justification métier :](../strategy/cloud-migration-business-case.md) La justification métier fait office de vue générale du plan financier global pour l'adoption du cloud. Il peut s'agir d'une source intéressante pour les efforts de budgétisation initiaux.
- [Métriques d'apprentissage](../strategy/learning-metrics.md) : Pour maintenir l'alignement entre la stratégie d'entreprise globale et les plans plus tactiques de gestion des changements, il est important d'établir des métriques d'apprentissage afin de montrer la progression itérative et incrémentielle vers le plan.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d'excellence du cloud ou équipe informatique centrale |

## <a name="step-2-develop-an-organizational-change-management-plan-to-span-cloud-adoption"></a>Étape 2 : Élaborer un plan de gestion des changements organisationnels pour couvrir l'adoption du cloud

La gestion des changements organisationnels est une approche itérative visant à réaligner subtilement les personnes, les processus et les technologies afin de prendre en charge une stratégie d'entreprise holistique. Dans le cas de l'excellence opérationnelle pour la transformation numérique, celle-ci s'articulera souvent autour d'un plan d'adoption du cloud centré sur l'informatique.

**Livrables :**

- Mettez à jour le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) afin qu'il reflète les changements nécessaires à la réalisation de la stratégie souhaitée. Les changements enregistrés peuvent inclure les éléments suivants :

  - Une évaluation du patrimoine numérique existant
  - Un plan d'adoption du cloud reflétant les changements nécessaires et le travail impliqué
  - Les changements organisationnels nécessaires pour respecter le plan
  - Un plan pour aborder les compétences nécessaires au bon accomplissement du travail requis par l'équipe existante

**Conseils relatifs aux livrables :**

- [Collectez l'inventaire](../digital-estate/inventory.md) : Établissez une source de données pour l'analyse du patrimoine numérique avant l'adoption.
- [Meilleure pratique - Azure Migrate](../plan/contoso-migration-assessment.md) : Utilisez Azure Migrate pour collecter l'inventaire.
- [Rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) : Dans le cadre de la rationalisation incrémentielle, une analyse quantitative permettra d'identifier les candidats au cloud à des fins de budgétisation.
- [Alignez les modèles de coût et les modèles de prévision](../digital-estate/calculate.md) : Utilisez Azure Cost Management pour aligner les modèles de coût et de prévision en [élaborant des budgets](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json).
- [Créez votre plan d'adoption du cloud](../plan/plan-intro.md#build-your-cloud-adoption-plan) : Créez un plan avec une charge de travail, des ressources et des détails de chronologie exploitables.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d'excellence du cloud ou équipe informatique centrale |

## <a name="step-3-manage-change-across-cloud-adoption-efforts"></a>Étape 3 : Gérer les changements dans le cadre des efforts d'adoption du cloud

La réalisation des résultats opérationnels est le fruit de la livraison continue de vagues d'adoption. Ces vagues peuvent inclure des cycles de migration et d'innovation. Dans les deux cas, l'excellence opérationnelle commence par des cycles réguliers de gestion des changements. Chaque vague (ou mise en production en termes agiles) fournira un ensemble de charges de travail au cloud. Au terme de chaque vague d'adoption, l'équipe chargée de la stratégie cloud sera en mesure de rendre compte des progrès réalisés en termes de métriques d'apprentissage, de résultats opérationnels et de stratégie globale. De même, au terme de chaque vague d'adoption, les équipes chargées de l'adoption auront besoin de mises à jour du backlog reflétant les charges de travail prioritaires du plan, sur la base de toute modification des plans d'activité et des besoins des clients.

**Livrables :**

- Tests et améliorations continus de la stratégie et du plan de gestion des changements en fonction de l'évolution des conditions du marché et de l'achèvement de la dernière vague de changements techniques.

**Conseils relatifs aux livrables :**

- [Planification de la mise en production :](../digital-estate/approach.md) Approches de gestion des changements par la planification de la mise en production.
- [Rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) : Approche itérative de la gestion des changements concentrée sur la gestion du backlog de mise en production pour la prise en charge de vagues de changements gérables.
- [Approche Puissance 10](../digital-estate/rationalize.md#release-planning) : Limiter le plan de gestion des changements pour se concentrer sur l'analyse détaillée et la planification d'une base continue de 10 charges de travail afin d'équilibrer les changements incrémentiels et les efforts d'adoption itératifs.
- [Aligner les chemins d'itération](../plan/iteration-paths.md) : Mise à jour et ajout de détails à chaque mise en production pour garantir les chemins d'itération actuels.
- [Évaluer les charges de travail](../migrate/azure-migration-guide/assess.md?tabs=challenge-assumptions) : Efforts de l'équipe chargée de l'adoption du cloud visant à évaluer et agir sur l'ensemble de priorités de migration le plus récent.
- [Consensus sur la valeur métier](../innovate/business-value.md) : Efforts de l'équipe chargée de l'adoption du cloud visant à assurer l'alignement de la valeur métier chaque fois qu'une nouvelle innovation est mise en production.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud |

## <a name="value-statement"></a>Énoncé de la valeur

Les étapes ci-dessus décrivent une approche orientée entreprise pour établir des exigences d'excellence opérationnelle tout au long du processus de transformation numérique. Cette approche fournit une base cohérente qui résonne à travers diverses autres fonctions du modèle opérationnel.

![Principes d’une architecture partagée](../_images/shared-principles.png)

## <a name="next-steps-to-delivering-operational-excellence-across-the-portfolio"></a>Étapes suivantes pour atteindre l'excellence opérationnelle dans l'ensemble du portefeuille

L'excellence opérationnelle exige une approche disciplinée en matière de fiabilité, de performances, de sécurité et d'optimisation des coûts. Utilisez les autres conseils de prise en main de cette série d'articles pour vous assurer que chacun de ces principes est implémenté par le biais d'approches d'automatisation cohérentes.

- **Optimisation des coûts** : Optimisez continuellement les coûts d'exploitation à l'aide du guide de prise en main consacré à la [gestion des coûts de l'entreprise](./manage-costs.md)
- **Sécurité :** Réduisez les risques en intégrant la sécurité de l'entreprise à l'ensemble du portefeuille à l'aide du guide de prise en main consacré à l'[implémentation de la sécurité dans l'ensemble du portefeuille](./security.md).
- Veillez à ce que les performances des ressources informatiques prennent en charge les processus métier à l'aide du guide de prise en main consacré à la [gestion des performances au sein de l'entreprise](./performance.md).
- Renforcez la fiabilité et réduisez les interruptions d'activité à l'aide du guide de prise en main consacré à l'[implémentation de contrôles pour assurer la fiabilité](./reliability.md).
