---
title: 'Bien démarrer : Créer des produits et services dans le cloud'
description: Découvrez la méthodologie Innover, approche destinée à vous guider dans le développement de nouveaux produits et services.
author: JanetCThomas
ms.author: janet
ms.date: 05/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 79c428da9d0be27c209fcc30686225217832dbe1
ms.sourcegitcommit: bd9872320b71245d4e9a359823be685e0f4047c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83862498"
---
# <a name="get-started-accelerate-new-product-and-service-innovation-in-the-cloud"></a>Bien démarrer : Accélérer l’innovation dans de nouveaux produits et services dans le cloud

La création de produits et services dans le cloud nécessite une approche différente de la migration. La méthodologie d'innovation du Cloud Adoption Framework pour Azure établit une approche qui oriente le développement de nouveaux produits et services.

Ce guide utilise les sections du Cloud Adoption Framework qui sont mises en évidence dans l’illustration suivante. Bien que l’innovation soit moins prévisible qu’une migration standard, elle est toujours adaptée au contexte d’un plan d’adoption du cloud plus large. Ce guide peut aider votre entreprise à fournir le support nécessaire à l’innovation et à fournir la structure requise pour créer un portefeuille équilibré pendant l’adoption du cloud.

![Commencer à accélérer l’innovation dans le cloud](../_images/get-started/innovation-map.png)

## <a name="step-1-document-the-business-strategy"></a>Étape 1 : Documenter la stratégie métier

Pour éviter les points de blocage courants, créez une stratégie métier claire et concise pour l’innovation. L’alignement des parties prenantes sur les motivations et les résultats métier attendus détermine les décisions prises par l’équipe d’adoption du cloud.

**Livrables :**

- Utilisez le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) pour enregistrer les motivations et les résultats métier souhaités.

<!-- docsTest:ignore "Get started: Accelerate migration" -->

**Conseils pour la prise en charge de l’achèvement des livrables :**

- [Motivations](../strategy/motivations.md) : La première étape de l’alignement stratégique consiste à parvenir à un accord sur les motivations qui sous-tendent l’effort d'innovation. Commencez par identifier et classer les motivations et les thèmes communs aux différentes parties prenantes au sein des équipes commerciales et informatiques.
- [Résultats opérationnels](../strategy/business-outcomes/index.md) : Une fois les motivations alignées, il est possible de capturer les résultats métier souhaités. Ces informations fournissent des métriques claires que vous pouvez utiliser pour mesurer la transformation globale.
- [Équilibrer le portefeuille](../strategy/balance-the-portfolio.md) : En matière d’adoption, l’innovation n’est pas le bon choix pour toutes les charges de travail. Cette approche de l’adoption est plus pertinente pour les nouvelles applications ou charges de travail personnalisées qui _nécessitent_ un remaniement de l’architecture ou des regénérations complètes. Quand les motivations favorisent énormément l’innovation pour toutes les charges de travail, il est important d’évaluer le portefeuille pour s’assurer que ces investissements peuvent produire le retour sur investissement (ROI) souhaité. La modernisation de ressources spécifiques et les efforts de reconstruction à petite échelle peuvent être innovants, mais vous pouvez les mettre en œuvre plus efficacement en suivant [Bien démarrer : Accélérer la migration](./migrate.md).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-2-evaluate-the-business-justification"></a>Étape 2 : Évaluer la justification métier

Dans cette première phase de la réalisation du business case, évaluez le retour élevé initial d’un effort potentiel d’adoption du cloud. L'objectif de cette étape est de s'assurer que toutes les parties prenantes s'alignent sur une question simple : en fonction des données disponibles, l'adoption globale du cloud est-elle une décision métier fondée ? En s’appuyant sur cette question, l’équipe peut mieux s’aligner sur la façon dont ce projet d’innovation répond aux besoins projetés des utilisateurs finaux dans la perspective de l’adoption du cloud.

**Livrables :**

- Utilisez le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) pour enregistrer la justification métier.

**Conseils pour la prise en charge de l’achèvement des livrables :**

- [Justification métier :](../strategy/cloud-migration-business-case.md) Avant d’évaluer chaque opportunité d’innovation dans le cloud, vous devez effectuer une justification métier générale pour établir l’alignement des parties prenantes en ce qui concerne le plan d’adoption global.
- [Consensus sur la valeur métier](../innovate/business-value.md) : La quantification de la valeur d’une innovation peut être difficile au début du processus. L’exercice dans cet article peut vous aider à évaluer l’alignement sur la valeur métier d’un effort d’innovation spécifique.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud |

## <a name="step-3-gather-data-and-analyze-assets-and-workloads"></a>Étape 3 : Collecter des données et analyser les ressources et les charges de travail

Dans la plupart des entreprises, l’innovation peut être accélérée grâce à l’utilisation de ressources existantes, telles que des applications, des machines virtuelles et des données. Lors de la planification de l’innovation, il est important de comprendre quand et comment ces ressources sont migrées vers le cloud.

**Livrables :**

- Données brutes sur l’inventaire existant, notamment applications, machines virtuelles et données.
- Si l’innovation proposée a des dépendances vis-à-vis de l’inventaire existant, effectuez les livrables suivants :
  - Analyse quantitative de tout inventaire de support nécessaire à la prise en charge de l’innovation prévue.
  - Analyse qualitative sur toutes les charges de travail de support nécessaires à la fourniture de l’innovation.
- Calculez le coût du nouvel inventaire nécessaire à la prise en charge de l’effort d’innovation.
- Mettez à jour la justification métier dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) avec des calculs affinés.

**Conseils relatifs aux livrables :**

La découverte et l’évaluation offrent un niveau d’alignement technique plus profond, qui vous aide à créer un plan d'action à utiliser pour migrer les charges de travail dépendantes nécessaires à l’innovation prévue. Ce scénario est très courant dans le cas des entreprises ayant des sources de données, des applications centralisées ou des couches de service nécessaires à la fourniture de l’innovation dans le contexte du reste de l’entreprise. S’il existe des systèmes dépendants, les articles suivants peuvent vous guider dans la découverte et l’évaluation.

- [Inventorier les systèmes existants](../digital-estate/inventory.md) : La première étape consiste à comprendre l’état actuel à partir d’une approche programmatique basée sur les données. Découvrez et rassemblez les données pour activer toutes les activités d’évaluation.
- [Rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) : Rationalisez les efforts d’évaluation pour vous concentrer sur une analyse qualitative de toutes les ressources, éventuellement même pour prendre en charge l’analyse de rentabilité. Ajoutez ensuite une analyse qualitative détaillée pour les 10 premières charges de travail.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud |

## <a name="step-4-plan-for-migration-of-dependent-assets"></a>Étape 4 : Planifier la migration des ressources dépendantes

Quand une nouvelle innovation dépend de charges de travail ou de ressources existantes, le modèle du plan d’adoption du cloud offre une approche accélérée du développement d’un backlog de projet. Le backlog peut ensuite être modifié pour refléter les résultats de la découverte, la rationalisation, les compétences nécessaires et la mise en place de partenariats.

**Livrables :**

- Déployer le modèle de backlog.
- Mettez à jour le modèle pour qu’il reflète les 10 premières charges de travail à migrer.
- Mettez à jour les personnes et la vélocité (temps des personnes) pour estimer le calendrier des mises en production.
- Risques liés au calendrier :
  - Une connaissance insuffisante d’Azure DevOps peut ralentir le processus de déploiement.
  - La complexité et les données disponibles pour chaque charge de travail peuvent également affecter la chronologie.

**Conseils relatifs aux livrables :**

- [Modèle de plan d'adoption du cloud](../plan/template.md) : Déployez le modèle de base.
- [Alignement des charges de travail](../plan/workloads.md) : Définissez les charges de travail dans le backlog.
- [Alignement de l’effort](../plan/assets.md) : Alignez les ressources et les charges de travail dans le backlog afin de définir clairement l’effort pour les charges de travail prioritaires.
- [Alignement des personnes et du calendrier](../plan/iteration-paths.md) : Établissez une itération, une vélocité et des mises en production pour les charges de travail.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud |

## <a name="step-5-align-governance-requirements-to-your-adoption-plan"></a>Étape 5 : Aligner les exigences de gouvernance sur votre plan d’adoption

L’étude des innovations planifiées avec l’équipe de gouvernance vous aide à éviter de nombreux points de blocage. Parfois, de nouvelles solutions novatrices peuvent nécessiter des pratiques qui sont déconseillées du point de vue d’une gouvernance saine. Certaines de ces fonctionnalités requises peuvent même être bloquées par le biais d’outils de mise en œuvre de la gouvernance automatisés.

**Livrables :**

- Créez de la transparence et facilitez la compréhension entre les besoins en innovation et les contraintes de gouvernance.
- Quand cela est nécessaire, mettez à jour les stratégies et les processus afin qu’ils reflètent les modifications ou exceptions touchant les contraintes de gouvernance existantes.

**Conseils relatifs aux livrables :**

Ces liens aident l’équipe d’adoption à comprendre l’approche suivie par l’équipe de gouvernance cloud.

- [Approche de gouvernance](../govern/index.md) : Cette méthodologie décrit un processus de réflexion sur la stratégie et les processus de l’entreprise. Vous pouvez ensuite mettre en place les disciplines nécessaires pour assurer la gouvernance dans le cadre de vos efforts en matière de cloud.
- [Définir la stratégie de l’entreprise](../govern/corporate-policy.md) : Identifiez et atténuez les risques métier.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="step-6-define-operational-needs-and-business-commitments"></a>Étape 6 : Définir les besoins opérationnels et les engagements métier

Définissez le plan des responsabilités opérationnelles à long terme relatif à l’innovation prévue. La base de référence de gestion établie sera-t-elle suffisante pour répondre à vos besoins opérationnels ? Si ce n’est pas le cas, évaluez les options des opérations de financement spécifiques à la technologie qui prend en charge cette innovation.

**Livrables :**

- Effectuez l'évaluation [Microsoft Azure Well-Architected Review](https://docs.microsoft.com/assessments/?id=azure-architecture-review) pour jauger différentes décisions en matière d’architecture et de fonctionnement.
- Ajustez le [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) pour qu’il reflète toutes les opérations avancées nécessaires.

**Conseils pour la prise en charge de l’achèvement des livrables :**

- [Développer la base de référence de gestion](../manage/best-practices.md) : Cette section du Framework d'adoption du cloud vous guide au fil des différentes transitions vers la gestion opérationnelle dans le cloud.
- [Gagner en spécificité avec les opérations avancées](../manage/design-principles.md) : Découvrez comment aller au-delà de votre base de référence de gestion.
- Si des opérations avancées sont nécessaires pour prendre en charge vos besoins opérationnels, évaluez les [engagements métier](../manage/considerations/business-alignment.md) pour déterminer les responsabilités opérationnelles des deux équipes.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe des opérations cloud <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="step-7-deploy-an-aligned-landing-zone"></a>Étape 7 : Déployer une zone d’atterrissage alignée

Toutes les ressources hébergées dans le cloud résident dans une zone d’atterrissage. Cette zone d’atterrissage peut avoir des exigences de gouvernance, de sécurité et de fonctionnement explicites. Il peut également s’agir d’un tout nouvel abonnement, sans prise en charge par d’autres équipes. Dans les deux cas, il est important de commencer avec une zone d’atterrissage qui s’aligne dès le début sur les exigences de gouvernance et de fonctionnement. Le fait de commencer avec une zone d’atterrissage approuvée aide votre équipe à découvrir les violations de stratégie au début du développement, et non au moment où la solution est mise en production. Une découverte précoce permet de supprimer les points de blocage et donne à l’équipe d’adoption et à l’équipe de gouvernance le temps nécessaire pour implémenter les modifications.

**Livrables :**

- Déployez une première zone d’atterrissage pour une expérimentation initiale à faible risque au cours d’une première innovation.
- Développez un plan de refactorisation avec le centre d’excellence du cloud ou l’équipe informatique centrale pour garantir l’alignement de la gouvernance, de la sécurité et opérationnel.
- Risques liés au calendrier :
  - Les exigences de gouvernance, d’exploitation et de sécurité pour les 10 premières charges de travail peuvent considérablement ralentir ce processus. La refactorisation réelle de la première zone d’atterrissage et des zones d’atterrissage suivantes prend beaucoup plus de temps, mais doit s’effectuer parallèlement aux efforts de migration.

**Conseils relatifs aux livrables :**

- [Choisir une zone d’atterrissage](../ready/landing-zone/first-landing-zone.md) : Utilisez cet article pour trouver la bonne approche de déploiement d’une zone d’atterrissage en fonction de votre modèle d’adoption. Déployez ensuite cette base de code standardisée.
- [Développer votre zone d’atterrissage](../ready/considerations/index.md) : Quel que soit le point de départ, identifiez les lacunes dans la zone d’atterrissage déployée afin d’ajouter les composants nécessaires pour l’organisation des ressources, la sécurité, la gouvernance, la conformité et les opérations.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> Équipe de plateforme cloud <li> Équipe d’adoption du cloud | <li> Équipe d’adoption du cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-8-innovate-in-the-cloud"></a>Étape 8 : Innover dans le cloud

La méthodologie Innover fournit des conseils sur les approches de gestion des produits et des outils les plus couramment utilisés pour innover dans le cloud. Ces étapes vous aident à prendre en main cette approche.

**Livrables :**

- Des solutions basées sur la technologie qui enrichissent la vie de vos clients et génèrent de la valeur pour l’entreprise.
- Processus et outils permettant d’effectuer des itérations sur ces solutions plus rapidement et d’ajouter de la valeur à l’aide du cloud :
  - Approches de développement itératif.
  - Applications personnalisées.
  - Expériences basées sur la technologie.
  - Intégration de produits physiques et de technologies à l'aide de l’IoT.
  - Intelligence ambiante : intégration de technologies non intrusives dans un environnement.
  - Azure Cognitive Services : Big Data, IA, Machine Learning et solutions prédictives.

**Conseils relatifs aux livrables :**

- [Consensus sur la valeur métier](../innovate/business-value.md) : Si plus de trois mois se sont écoulés depuis le dernier consensus sur la valeur métier ou si l’un n’a jamais été atteint, commencez ici.
- [Guide d’innovation Azure](../innovate/innovation-guide/index.md) : Utilisez le guide d’innovation Azure pour accélérer le déploiement de solutions innovantes, en vous familiarisant avec les outils et les processus qui peuvent vous aider à créer un produit minimum viable (MVP).
- [Bonnes pratiques en matière d’innovation](../innovate/best-practices/index.md) : Combinez les services Azure afin de créer une chaîne d’outils pour l’invention numérique.
- [Boucles de commentaires](../innovate/considerations/adoption.md) : Développez des boucles de rétroaction améliorées pour fournir rapidement des innovations percutantes à vos clients.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Centre d’excellence de cloud <li> Centre d’excellence de cloud ou équipe informatique centrale |

## <a name="value-statement"></a>Énoncé de la valeur

Les étapes décrites dans ce guide peuvent vous aider, vous et vos équipes, à créer des solutions novatrices dans le cloud qui créent de la valeur métier, qui sont régies correctement et qui sont bien conçues.

## <a name="next-steps"></a>Étapes suivantes

Le Framework d’adoption du cloud est une solution de cycle de vie. Il peut vous aider à commencer un parcours d'innovation. Il peut aussi vous aider à faire progresser la maturité des équipes qui prennent en charge les efforts d'innovation. Les équipes suivantes peuvent utiliser ces prochaines étapes pour que leurs efforts gagnent en maturité. Ces processus parallèles ne sont pas linéaires et ne doivent pas être considérés comme des points de blocage. Au lieu de cela, chacun est un flux de valeur parallèle qui aide à faire murir la préparation globale au cloud de votre entreprise.

| Équipe | Itération suivante |
|---|---|
| Équipe&nbsp;d’adoption du&nbsp;cloud | Les [améliorations des processus](../innovate/considerations/index.md) fournissent des informations sur les approches de fourniture d’innovations qui impactent les clients et favorisent l’adoption récurrente. |
| Équipe&nbsp;de stratégie&nbsp;cloud | La [méthodologie de stratégie](../strategy/index.md) et la [méthodologie de planification](../plan/index.md) sont des processus itératifs qui évoluent avec le plan d’adoption. Revenez à ces pages de présentation et continuez à effectuer des itérations sur vos stratégies métier et techniques. |
| Équipe&nbsp;de plateforme&nbsp;cloud | Revisitez la [méthodologie de préparation](../ready/index.md) pour continuer à faire progresser la plateforme cloud globale qui prend en charge la migration ou d’autres efforts d’adoption. |
| Équipe&nbsp;de gouvernance&nbsp;cloud | Utilisez la [méthodologie de gouvernance](../govern/index.md) pour continuer à améliorer les disciplines, les stratégies et les processus de gouvernance. |
| Équipe&nbsp;des opérations&nbsp;cloud | Appuyez-vous sur la [méthodologie de gestion](../manage/index.md) pour fournir des opérations plus riches dans Azure. |
