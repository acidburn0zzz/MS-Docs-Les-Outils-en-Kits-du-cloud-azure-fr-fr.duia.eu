---
title: 'Bien démarrer : Accélérer la migration'
description: Étapes recommandées pour l’alignement des parties prenantes, la planification de la migration, le déploiement d’une zone d’atterrissage et la migration de vos 10 premières charges de travail.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: b943259df90851704c8a4035da10d313589eb5b2
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83752850"
---
# <a name="get-started-accelerate-migration"></a>Bien démarrer : Accélérer la migration

L’alignement correct des parties prenantes de l’entreprise et des services informatiques peut aider votre organisation à surmonter les obstacles à la migration et à accélérer les efforts de migration. Cet article fournit les étapes recommandées pour :

- L’alignement des parties prenantes.
- La planification de la migration.
- Le déploiement d’une zone d’atterrissage.
- La migration des 10 premières charges de travail.

Il peut également contribuer à la réussite à long terme due à une gouvernance et à une gestion adéquates.

Utilisez ce guide pour réduire le nombre d’éléments et de processus nécessaires à l’alignement d’un effort de migration global. Ce processus utilise les sections du Cloud Adoption Framework pour Azure qui sont mises en évidence dans cette illustration.

![Bien démarrer avec la migration dans Azure](../_images/get-started/migration-map.png)

Si votre scénario de migration est atypique, vous pouvez obtenir une évaluation personnalisée de la préparation à la migration de votre organisation en utilisant l’[évaluation menée par l’outil de préparation et de migration stratégique (SMART)](https://docs.microsoft.com/assessments/?id=strategic-migration-assessment). Utilisez-la pour identifier les conseils les mieux adaptés à vos besoins actuels.

## <a name="get-started"></a>Bien démarrer

L’effort et le processus techniques nécessaires à la migration des charges de travail sont relativement simples. Il est important d’effectuer efficacement le processus de migration. La préparation à la migration stratégique a un impact encore plus important sur la chronologie et la réussite de la migration globale.

Pour accélérer l’adoption, vous devez prendre les mesures nécessaires pour soutenir l’équipe d’adoption du cloud pendant la migration. Ce guide décrit ces tâches itératives nécessaires pour aider les clients à appréhender correctement le chemin de migration vers le cloud. Pour montrer l’importance des étapes de support, la migration figure à l’étape 10 de cet article. En réalité, l’équipe chargée de l’adoption du cloud lance probablement la première migration pilote en parallèle avec les étapes 4 ou 5.

## <a name="step-1-align-stakeholders"></a>Étape 1 : Aligner les parties prenantes

Pour éviter les points de blocage de migration courants, créez une stratégie métier claire et concise pour la migration. L’alignement des parties prenantes sur les motivations et les résultats métier attendus détermine les décisions prises par l’équipe d’adoption du cloud.

- [Motivations](../strategy/motivations.md) : La première étape de l’alignement stratégique consiste à parvenir à un accord sur les motivations qui sous-tendent l’effort de migration. Commencez par identifier et classer les motivations et les thèmes communs aux différentes parties prenantes au sein des équipes commerciales et informatiques.
- [Résultats opérationnels](../strategy/business-outcomes/index.md) : Une fois les motivations alignées, il est possible de capturer les résultats métier souhaités. Ces informations fournissent des métriques claires que vous pouvez utiliser pour mesurer la transformation globale.

**Livrables :**

- Utiliser le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) pour enregistrer les motivations et les résultats métier souhaités.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-2-align-partner-support"></a>Étape 2 : Aligner le support des partenaires

Des partenaires, des services Microsoft ou divers programmes Microsoft sont disponibles pour vous soutenir tout au long du processus de migration.

- [Familiarisez-vous avec les options de partenariat](../migrate/migration-considerations/assess/partnership-options.md) pour trouver le niveau de partenariat et de support approprié.

**Livrables :**

- Établir des conditions générales, ou d’autres accords contractuels, avant d’engager les services d’un partenaire de support.
- Identifier les partenaires approuvés dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-3-gather-data-and-analyze-assets-and-workloads"></a>Étape 3 : Collecter des données et analyser les ressources et les charges de travail

La découverte et l’évaluation offrent un niveau d’alignement technique plus approfondi, qui vous aide à élaborer un plan d’action que vous pouvez utiliser pour la mise en œuvre de la stratégie. Au cours de cette étape, vous validez l’analyse de rentabilité en utilisant des données sur l’environnement de l’état actuel. Ensuite, vous effectuez une analyse quantitative de ces données et une évaluation qualitative approfondie des charges de travail ayant la priorité la plus élevée.

- [Inventorier les systèmes existants](../digital-estate/inventory.md) : La première étape consiste à comprendre l’état actuel à partir d’une approche programmatique basée sur les données. Découvrez et rassemblez les données pour activer toutes les activités d’évaluation.
- [Rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) : Rationalisez les efforts d’évaluation pour vous concentrer sur une analyse qualitative de toutes les ressources, éventuellement même pour prendre en charge l’analyse de rentabilité. Ajoutez ensuite une analyse qualitative détaillée pour les 10 premières charges de travail à migrer.

**Livrables :**

- Données brutes sur l’inventaire existant.
- Analyse quantitative sur l’inventaire existant pour affiner la justification métier.
- Analyse qualitative des 10 premières charges de travail.
- Mettre à jour la justification métier dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud |

## <a name="step-4-make-a-business-case"></a>Étape 4 : Créer une analyse de rentabilisation

L’analyse de rentabilité de la migration prendra sans doute la forme d’une conversation itérative entre les parties prenantes. Lors de cette première phase de la réalisation de l’analyse de rentabilisation, évaluez le retour élevé initial d’une migration cloud potentielle. L'objectif de cette étape est de s'assurer que toutes les parties prenantes s'alignent sur une question simple : en fonction des données disponibles, l'adoption globale du cloud est-elle une décision métier fondée ?

- La [création d’une analyse de rentabilité de la migration cloud](../strategy/cloud-migration-business-case.md) est un bon point de départ pour le développement d’une analyse de rentabilité de la migration. La clarté des formules et des outils peut aider à la justification pour l’entreprise.

**Livrables :**

- Utiliser le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) pour enregistrer la justification métier.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de stratégie cloud | <li> Équipe d’adoption du cloud |

## <a name="step-5-create-a-migration-plan"></a>Étape 5 : Créer un plan de migration

Le modèle de plan d’adoption du cloud fournit une approche accélérée pour développer un backlog du projet. Le backlog peut ensuite être modifié pour refléter les résultats de la découverte, la rationalisation, les compétences nécessaires et la mise en place de partenariats.

- [Modèle de plan d’adoption du cloud](../plan/template.md) : Déployez le modèle de base.
- [Alignement des charges de travail](../plan/workloads.md) : Définissez les charges de travail dans le backlog.
- [Alignement de l’effort](../plan/assets.md) : Alignez les ressources et les charges de travail dans le backlog afin de définir clairement l’effort pour les charges de travail prioritaires.
- [Alignement des personnes et du calendrier](../plan/iteration-paths.md) : Établissez l’itération, la vélocité (calendrier des personnes) et les mises en production relatives aux charges de travail migrées.

**Livrables :**

- Déployer le modèle de backlog.
- Mettez à jour le modèle pour qu’il reflète les 10 premières charges de travail à migrer.
- Mettez à jour les personnes et la vélocité pour estimer le calendrier des mises en production.
- Risques liés au calendrier :
  - Une connaissance insuffisante d’Azure DevOps peut ralentir le processus de déploiement.
  - La complexité et les données disponibles pour chaque charge de travail peuvent également affecter la chronologie.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud |

## <a name="step-6-build-a-skills-readiness-plan"></a>Étape 6 : Créer un plan de préparation des compétences

Les employés existants peuvent jouer un rôle pratique dans le cadre de l’effort de migration, mais des compétences supplémentaires peuvent être nécessaires. Dans cette étape, l’équipe identifie les opportunités de développer ces compétences ou d’utiliser des partenaires pour les ajouter.

- [Créez un plan de préparation des compétences](../plan/adapt-roles-skills-processes.md). Évaluez rapidement les compétences nécessaires et existantes pour mieux comprendre les exigences à satisfaire en matière de compétences.

**Livrables :**

- Ajoutez un plan de préparation des compétences au [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud |

## <a name="step-7-deploy-and-align-a-landing-zone"></a>Étape 7 : Déployer et aligner une zone d’atterrissage

Toutes les ressources migrées sont déployées dans une zone d’atterrissage. Initialement, la zone d’atterrissage est simple, afin de prendre en charge des charges de travail plus petites. Au fil du temps, elle est mise à l’échelle afin de gérer des charges de travail plus complexes.

- [Choisir une zone d’atterrissage](../ready/landing-zone/first-landing-zone.md) : Utilisez cet article pour trouver la bonne approche de déploiement d’une zone d’atterrissage en fonction de votre modèle d’adoption. Déployez ensuite cette base de code standardisée.
- [Développer votre zone d’atterrissage](../ready/considerations/index.md) : Quel que soit le point de départ, identifiez les lacunes dans la zone d’atterrissage déployée afin d’ajouter les composants nécessaires pour l’organisation des ressources, la sécurité, la gouvernance, la conformité et les opérations.

**Livrables :**

- Déployer une première zone d’atterrissage pour les migrations initiales à faible risque.
- Élaborez un plan de refactorisation avec le centre d'excellence du cloud ou l'équipe informatique centrale.
- Risques liés au calendrier :
  - Les exigences de gouvernance, d’exploitation et de sécurité pour les 10 premières charges de travail peuvent considérablement ralentir ce processus.
  - La refactorisation réelle de la première zone d’atterrissage et des zones d’atterrissage suivantes prend beaucoup plus de temps, mais doit s’effectuer parallèlement aux efforts de migration.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> Équipe de plateforme cloud | <li> Équipe d’adoption du cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-8-migrate-your-first-10-workloads"></a>Étape 8 : Migrer vos 10 premières charges de travail

L’effort technique nécessaire pour migrer vos 10 premières charges de travail est relativement simple. Il s’agit également d’un processus itératif que vous répéterez à mesure que vous migrerez davantage de ressources. Dans ce processus, vous évaluez vos charges de travail (voir l’étape 4), vous les déployez, puis vous les publiez sur votre environnement de production.

![Phases de l’effort de migration itérative : évaluer, déployer, publier](../_images/migrate/methodology-effort-only.png)

Les outils de migration cloud permettent de migrer toutes les machines virtuelles d’un centre de communication en une seule passe ou itération. Il est plus courant de migrer un plus petit nombre de charges de travail lors de chaque itération. Le fractionnement de la migration en plus petites vagues ou mises en production nécessite davantage de planification, mais un plus petit nombre réduit les risques techniques et l'impact de la gestion des modifications organisationnelles.

À chaque itération, l’équipe d’adoption du cloud devient plus performante dans la migration des charges de travail. Ces étapes permettent de lancer l’équipe technique sur cette courbe de maturité :

1. Migrez vos premières charges de travail en adoptant une approche IaaS pure, en utilisant les outils décrits dans le [guide de migration Azure](../migrate/azure-migration-guide/index.md).
2. Développez les options des outils pour utiliser la migration et la modernisation avec les [scénarios de migration](../migrate/azure-best-practices/contoso-migration-overview.md).
3. Développez votre stratégie technique en adoptant des approches plus larges présentées dans les [bonnes pratiques de migration](../migrate/azure-best-practices/index.md).
4. Améliorez la cohérence, la fiabilité et les performances en adoptant une approche de fabrique de migration efficace, comme indiqué dans [Améliorations du processus de migration](../migrate/migration-considerations/index.md).

**Livrables :**

Amélioration continue de la capacité de l’équipe d’adoption à migrer les charges de travail.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de stratégie cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-9-hand-off-production-workloads-to-cloud-governance"></a>Étape 9 : Transférer les charges de travail de production vers la gouvernance cloud

La gouvernance est un facteur déterminant pour le succès à long terme de tout effort de migration. La vitesse de migration et l’impact sur l’activité sont importants. Mais la vitesse sans gouvernance peut être dangereuse. Votre organisation doit prendre des décisions de gouvernance alignées sur vos modèles d’adoption, et sur vos besoins en matière de gouvernance et de conformité.

- [Approche de gouvernance](../govern/index.md) : Cette méthodologie décrit un processus de réflexion sur la stratégie et les processus de l’entreprise. Vous pouvez ensuite mettre en place les disciplines nécessaires pour assurer la gouvernance dans le cadre de vos efforts d’adoption du cloud.
- [Fondation de gouvernance initiale](../govern/guides/complex/prescriptive-guidance.md) : Identifiez la discipline Base de référence des identités, la discipline Base de référence de la sécurité et la discipline Accélération du déploiement nécessaires à la création d’un produit minimal viable de gouvernance servant de base à toute adoption.

**Livrables :**

- Déployer une fondation de gouvernance initiale.
- Réaliser un benchmark de gouvernance afin de planifier les futures améliorations.
- Risques liés à la chronologie : les stratégies d'amélioration et l'implémentation de la gouvernance peuvent ajouter une à quatre semaines par discipline.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-10-hand-off-production-workloads-to-cloud-operations"></a>Étape 10 : Transférer les charges de travail de production vers les opérations cloud

La gestion des opérations est une autre exigence pour réussir la migration. Migrer des charges de travail individuelles vers le cloud sans comprendre les opérations d’entreprise en cours est une décision risquée. Parallèlement à la migration, vous devez commencer à planifier les opérations à plus long terme.

- [Établir une base de référence de gestion](../manage/index.md)
- [Définir des engagements métier](../manage/considerations/business-alignment.md)
- [Développer la base de référence de gestion](../manage/best-practices.md)
- [Gagner en spécificité avec les opérations avancées](../manage/design-principles.md)

**Livrables :**

- Déployer une base de référence de gestion.
- Compléter le classeur de gestion des opérations.
- Identifier toutes les charges de travail qui nécessitent une évaluation Microsoft Azure Well-Architected Review.
- Risques liés au calendrier :
  - Consultez le classeur : estimation d'une heure par propriétaire d'application.
  - Effectuez l'évaluation Microsoft Azure Well-Architected Review : estimation d'une heure par application.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe des opérations cloud | <li> Équipe de stratégie cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="value-statement"></a>Énoncé de la valeur

Les étapes décrites dans ce guide peuvent aider vos équipes à accélérer leurs efforts de migration grâce à une meilleure gestion des changements et à un alignement des parties prenantes. Suivre ces étapes peut ralentir le processus. Ces étapes éliminent aussi les points de blocage courants et accélèrent la réalisation de la valeur ajoutée pour l’entreprise.

## <a name="next-steps"></a>Étapes suivantes

Le Framework d’adoption du cloud est une solution de cycle de vie. Il peut vous aider à commencer un parcours de migration. Il peut aussi vous aider à faire progresser la maturité des équipes qui prennent en charge les efforts de migration. Les équipes suivantes peuvent utiliser ces prochaines étapes pour que leurs efforts gagnent en maturité. Ces processus parallèles ne sont pas linéaires et ne doivent pas être considérés comme des points de blocage. Au lieu de cela, chacun est un flux de valeur parallèle qui aide à faire murir la préparation globale au cloud de votre entreprise.

| Équipe  | Itération suivante |
|---|---|
| Équipe&nbsp;d’adoption du&nbsp;cloud | Les [améliorations des processus](../migrate/migration-considerations/index.md) fournissent des informations sur la transition vers une fabrique de migration avec des fonctionnalités de migration continues efficaces. |
| Équipe&nbsp;de stratégie&nbsp;cloud | La [méthodologie de stratégie](../strategy/index.md) et la [méthodologie de planification](../plan/index.md) sont des processus itératifs qui évoluent avec le plan d’adoption. Revenez à ces pages de présentation et continuez à effectuer des itérations sur vos stratégies métier et techniques. |
| Équipe&nbsp;de plateforme&nbsp;cloud | Revisitez la [méthodologie de préparation](../ready/index.md) pour continuer à faire progresser la plateforme cloud globale qui prend en charge la migration ou d’autres efforts d’adoption. |
| Équipe&nbsp;de gouvernance&nbsp;cloud | Utilisez la [méthodologie de gouvernance](../govern/index.md) pour continuer à améliorer les disciplines, les stratégies et les processus de gouvernance. |
| Équipe&nbsp;des opérations&nbsp;cloud | Appuyez-vous sur la [méthodologie de gestion](../manage/index.md) pour fournir des opérations plus riches dans Azure. |

Si votre scénario de migration est atypique, vous pouvez obtenir une évaluation personnalisée de la préparation à la migration de votre organisation en utilisant l’[évaluation menée par l’outil de préparation et de migration stratégique (SMART)](https://docs.microsoft.com/assessments/?id=strategic-migration-assessment). En fonction des réponses que vous fournissez lors de l’évaluation, nous pouvons vous aider à identifier les conseils les mieux adaptés à vos besoins actuels.
