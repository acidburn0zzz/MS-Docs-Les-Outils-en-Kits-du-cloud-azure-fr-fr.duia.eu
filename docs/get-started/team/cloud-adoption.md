---
title: "Bien démarrer : Créer une équipe chargée de l'adoption du cloud"
description: Définissez le champ d'action de l'équipe chargée de l'adoption du cloud, les livrables ainsi que les capacités nécessaires pour préparer une adoption réussie du cloud.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.topic: conceptual
ms.date: 05/15/2020
ms.openlocfilehash: 33744f6911ec724c517a7fa93979a8adbdd370c1
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83814460"
---
# <a name="get-started-build-a-cloud-adoption-team"></a>Bien démarrer : Créer une équipe chargée de l'adoption du cloud

Les équipes chargées de l’adoption du cloud sont l’équivalent moderne des équipes de mise en œuvre technique ou des équipes de projet. La nature du cloud peut nécessiter des structures d'équipe plus fluides.

Certaines équipes chargées de l'adoption du cloud se consacrent exclusivement à la migration vers le cloud, tandis que d'autres se concentrent sur les innovations qui tirent parti des technologies cloud. Certaines disposent de la vaste expertise technique requise pour entreprendre des efforts d'adoption importants, comme la migration complète d'un centre de données, tandis que d'autres ont des priorités techniques plus ciblées.

Une équipe plus petite peut passer d’un projet à un autre afin d'atteindre des objectifs spécifiques. Par exemple une équipe de spécialistes des plateformes de données peut se concentrer sur la conversion des machines virtuelles SQL Database en instances SQL PaaS.

![Bien démarrer avec la création d'une équipe chargée de l'adoption du cloud](../../_images/get-started/adoption-team-map.png)

## <a name="step-1-determine-the-type-of-adoption-team-you-need"></a>Étape 1 : Déterminer le type d'équipe d'adoption dont vous avez besoin

Les équipes chargées de l'adoption du cloud ont tendance à se lancer dans un ou plusieurs des types d'adoption suivants :

- Migration des charges de travail existantes
- Modernisation des charges de travail et des ressources existantes
- Modification architecturale des charges de travail et des ressources existantes
- Développement de nouvelles charges de travail

L'adoption d'un portefeuille informatique requiert généralement un mélange de ces types d'efforts. Malheureusement, chaque type requiert des compétences et un état d'esprit différents. Plus une équipe d'adoption est spécialisée, plus elle est efficace et performante dans sa spécialité. Inversement, la maîtrise de l'ensemble des options d'implémentation de l'adoption du cloud peut sembler insurmontable à ces équipes plus spécialisées.

Lors de la création d'une équipe chargée de l'adoption du cloud, l'alignement sur une des méthodologies d'adoption permettra d'accélérer l'élargissement des compétences collectives de l'équipe.

**Livrables :**

- Déterminez la méthodologie sur laquelle l'équipe s'aligne le mieux : la méthodologie de migration ou la méthodologie d'innovation.
- Pour chaque méthodologie, une expérience d'intégration en quatre étapes permet à l'équipe d'identifier les outils et les processus nécessaires à la maîtrise du domaine correspondant. Investissez du temps, en équipe, pour passer en revue les premières étapes et identifier les outils et scénarios dont vous aurez le plus besoin lors des premières itérations.
- Mettez à jour le [modèle RACI](../../organize/raci-alignment.md) (Réalisateur, Approbateur, Consulté, Informé) de votre entreprise pour aider les autres à comprendre qui fait partie de l'équipe et quelle méthodologie l'équipe s'attachera à appliquer.

**Conseils relatifs aux livrables :**

- La [Présentation de la méthodologie de migration](../../migrate/index.md) décrit le processus, les outils et les approches de migration et de modernisation d'un portefeuille de charges de travail.
- La [Présentation de la méthodologie d'innovation](../../innovate/index.md) décrit le processus, les outils et les approches d'ajout au portefeuille de charges de travail natives du cloud.
- [Identifiez les motivations](../../strategy/motivations.md) qui sous-tendent cet effort pour déterminer si elles s'alignent davantage sur les efforts de migration ou d'innovation.

## <a name="step-2-align-your-team-with-other-supporting-teams"></a>Étape 2 : Aligner votre équipe sur d'autres équipes de soutien

Si le projet d'adoption du cloud de votre entreprise est suffisamment avancé pour y intégrer des équipes de soutien, vous trouverez peut-être la liste des équipes et des experts correspondants dans le [modèle RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx) de votre entreprise (gouvernance cloud, opérations cloud, centre d'excellence du cloud ou autres équipes similaires).

**Livrables :**

- Passez en revue les conseils relatifs à la conception, les bases de référence opérationnelles, les stratégies et les processus des différentes équipes de soutien afin d'identifier les garde-fous qui ont été établis pour guider l'adoption du cloud.
- Passez en revue les conseils avec d'autres équipes chargées de l'adoption du cloud pour identifier les limites que vous pourriez rencontrer en raison de ces garde-fous.

**Conseils relatifs aux livrables :**

- [Évaluer la stratégie d'entreprise](../../govern/corporate-policy.md) décrit les étapes à suivre pour définir la stratégie d'entreprise, qui pourrait limiter les décisions que peut prendre l'équipe en toute sécurité dans l'environnement cloud de l'entreprise.
- [Disciplines de gouvernance](../../govern/corporate-policy.md) décrit les types de contrôles ou de processus disciplinés que l'équipe de gouvernance est susceptible d'avoir mis en place pour garantir une adoption sûre et conforme du cloud.
- La [Méthodologie de gestion](../../manage/index.md) décrit les éléments à prendre en considération dans une base de référence des opérations cloud pour fournir une gestion de base des opérations.

<!-- markdownlint-disable MD033 -->

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> L'équipe chargée de la stratégie cloud a pour mission de maintenir une structure RACI claire tout au long du cycle d'adoption du cloud. | Passez en revue les conseils et exigences des équipes suivantes : <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d'excellence du cloud ou équipe informatique centrale <li> Autres équipes chargée de l'adoption du cloud ou personnes figurant sur la liste du modèle RACI |

## <a name="step-3-begin-your-adoption-journey"></a>Étape 3 : Entamer votre parcours d'adoption

Selon le type d'équipe d'adoption dont vous faites partie, vous commencerez par l'un de ces parcours :

- Bien démarrer : Migrer des charges de travail vers le cloud
- Bien démarrer : Créer des produits ou services

Ces guides de démarrage fourniront des conseils pour les différentes équipes répertoriées, ainsi que divers degrés d'obligations et de responsabilités. Utilisez ces guides comme référence pour comprendre comment votre équipe s'intègre dans le reste du parcours. Utilisez-les également pour identifier les niveaux de soutien auxquels vous pouvez vous attendre de la part de l'entreprise.

Au final, l'équipe chargée de l'adoption du cloud a pour mission d'atteindre les objectifs de migration assignés ou de développer de nouveaux produits. Si la mission des équipes de soutien consiste à veiller à ce que chaque étape soit franchie, il incombe à chaque équipe d'adoption du cloud de s'assurer qu'elle reçoit le soutien dont elle a besoin pour réussir. Si l'équipe responsable n'existe pas ou si elle a besoin de soutien supplémentaire pour franchir les étapes qui lui sont confiées, l'équipe chargée de l'adoption est encouragée à s'associer à d'autres équipes pour atteindre ses livrables.

**Livrables :**

- Devenez de plus en plus performant dans la mise en œuvre de la méthodologie associée à votre approche d'adoption.
- Aidez d'autres équipes à franchir les étapes dont elles sont responsables, même si  ces étapes constituent des obstacles à vos efforts d'adoption.

**Conseils relatifs aux livrables :**

- Dans le guide de démarrage de la migration, l'équipe d'adoption est responsable de l'[étape 10 : migrer votre première charge de travail](../migrate.md#step-8-migrate-your-first-10-workloads).
- Dans le guide de démarrage des nouveaux produits, l'équipe d'adoption est responsable de l'[étape 8 : innover dans le cloud](../innovate.md#step-8-innovate-in-the-cloud).

Toutes les autres étapes de ces check-lists sont conçues pour faciliter la gestion de l'effort.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe de gouvernance cloud <li> Équipe des opérations cloud <li> Centre d'excellence du cloud ou équipe informatique centrale <li> Équipe de stratégie cloud |

## <a name="step-4-expand-your-skills-with-scenarios-and-best-practices"></a>Étape 4 : Développer vos compétences à l'aide de scénarios et de bonnes pratiques

Après une ou deux itérations d'adoption, l'équipe d'adoption du cloud maîtrisera les bases de sa méthodologie principale. À partir de là, elle sera prête à aborder d'autres scénarios et à commencer à appliquer des bonnes pratiques supplémentaires.

**Livrables :**

- Améliorez vos compétences et renforcez votre expérience pour aborder des scénarios d'adoption plus complexes.

**Conseils relatifs aux livrables :**

L’équipe peut examiner et développer ses compétences en consultant les conseils suivants :

- Migrez de nouveaux types de charges de travail ou relevez des défis de migration plus complexes à l'aide de [scénarios](../../migrate/azure-best-practices/contoso-migration-overview.md) et de [bonnes pratiques](../../migrate/azure-best-practices/index.md).
- Innovez grâce à de nouvelles solutions natives du cloud ou relevez des défis d'innovation plus complexes à l'aide de [scénarios](../../innovate/kubernetes/index.md) et de [bonnes pratiques](../../innovate/best-practices/index.md).

**Équipe responsable :**

- Il incombe à l'équipe chargée de l'adoption du cloud d'élargir ses compétences.

## <a name="step-5-build-a-cloud-adoption-factory"></a>Étape 5 : Créer une fabrique d'adoption du cloud

À mesure que l'équipe se familiarisera avec différents scénarios d'adoption, elle gagnera en productivité et en rapidité. Cette section de conseils permettra à l'équipe de passer à la vitesse supérieure en matière d'adoption.

L'approche de la fabrique d'adoption du cloud examine les processus qui sous-tendent les efforts d'adoption. En raison d'un manque de compréhension et de communication claire, la plupart des contraintes de temps liées à la migration et à l'innovation proviennent du grand nombre de réunions. Une définition claire des processus et des interactions à différents stades du parcours d'adoption du cloud permettra de lever les obstacles culturels et politiques.

**Livrables :**

- Améliorez les processus de réalisation pour créer une fabrique d'adoption hautement optimisée.

**Conseils relatifs aux livrables :**

- Des conseils sur les processus de soutien des [efforts de migration](../../migrate/migration-considerations/index.md) sont disponibles à la section Améliorations des processus de la méthodologie de migration.
- Dans la méthodologie d'innovation, les conseils se concentrent sur les [processus d'innovation](../../innovate/considerations/index.md) qui se traduisent par moins de technologie et par un développement de produit plus efficace.

**Équipe responsable :**

- L'équipe d'adoption du cloud est responsable de la mise en place des processus qui font passer l'adoption au niveau supérieur.

## <a name="whats-next"></a>Étapes suivantes

L’adoption du cloud est un formidable objectif, mais une adoption anarchique peut produire des résultats inattendus. Pour accélérer l'adoption et implémenter les meilleures pratiques tout en réduisant les risques métier et les risques techniques, alignez l'adoption du cloud sur les [fonctions de gouvernance cloud](../../organize/cloud-governance.md).

L’alignement avec l’équipe de gouvernance cloud crée un équilibre entre les efforts d’adoption du cloud, mais cela est considéré comme un produit minimum viable (MVP), car il peut être durable. Chaque équipe endosse plusieurs rôle, comme indiqué dans les [graphiques RACI](../../organize/raci-alignment.md).

Découvrez-en plus sur la manière de surmonter les [antimodèles organisationnels : silos et fiefs](../../organize/fiefdoms-silos.md).
