---
title: 'Bien démarrer : Constituer une équipe chargée de la migration vers le cloud'
description: Ce guide aide une équipe chargée de la migration vers le cloud à identifier l'étendue, les livrables et les fonctionnalités requises pour réussir la migration.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.topic: conceptual
ms.date: 04/04/2020
ms.openlocfilehash: 1e67eba9c26787268fe8ce75e4540d03dca48e9d
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230357"
---
# <a name="get-started-build-a-cloud-migration-team"></a>Bien démarrer : Constituer une équipe chargée de la migration vers le cloud

Les équipes chargées de la migration vers le cloud sont l'équivalent moderne des équipes de mise en œuvre technique ou des équipes de projet. Toutefois, la nature du cloud peut nécessiter une structure d'équipe plus fluide. Certaines équipes de migration se consacrent exclusivement à la migration vers le cloud, tandis que d'autres se concentrent sur les innovations qui tirent parti des technologies cloud. Certaines disposent de la vaste expertise technique requise pour entreprendre des efforts d'adoption importants, comme la migration complète d'un centre de données, tandis que d'autres ont des priorités techniques plus ciblées et peuvent passer d'un projet à un autre pour atteindre des objectifs spécifiques, par exemple une équipe de spécialistes des plateformes de données qui contribue à convertir des machines virtuelles SQL en instances SQL PaaS.

Quel que soit le type ou le nombre d'équipes de migration vers le cloud, celles-ci fournissent généralement une expertise en la matière aux partenaires informatiques, d'analyse commerciale ou de mise en œuvre.

## <a name="prerequisites"></a>Prérequis

- [Création d’un compte Azure](https://docs.microsoft.com/learn/modules/create-an-azure-account) : La première étape pour utiliser Azure est de créer un compte.
- [Portail Azure](https://docs.microsoft.com/learn/modules/tour-azure-portal): Découvrez les fonctionnalités du portail et des services Azure, et personnalisez le portail.
- [Présentation d’Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) : Bien démarrer avec Azure. Créez et configurez votre première machine virtuelle dans le cloud.
- [Notions de base d’Azure](https://docs.microsoft.com/learn/paths/azure-for-the-data-engineer) : Découvrez les concepts du cloud, familiarisez-vous avec les avantages, comparez et confrontez les stratégies de base, et explorez l'éventail des services disponibles dans Azure.
- Consultez la [méthodologie Migration](../../migrate/index.md).

## <a name="minimum-scope"></a>Étendue minimale

L'équipe chargée de la migration vers le cloud constitue le noyau de tous les efforts de migration vers le cloud. Cette équipe pilote les modifications techniques qui permettent l’adoption du cloud. Selon les objectifs de l'effort d'adoption, cette équipe peut comprendre des membres aux compétences diverses qui s'occupent d'un large éventail de tâches techniques et commerciales.

Au minimum, l'étendue de l'équipe comprend les aspects suivants :

- Rationalisation du [patrimoine numérique](../../digital-estate/index.md)
- Examen, validation et progression du [backlog de migration classé par ordre de priorité](../../migrate/migration-considerations/assess/release-iteration-backlog.md)
- Exécution de la [première charge de travail](../../digital-estate/rationalize.md#select-the-first-workload) comme opportunité d'apprentissage

## <a name="deliverable"></a>Livrable

Le livrable principal de toute équipe chargée de la migration vers le cloud est la mise en œuvre en temps réel des solutions techniques présentées dans le plan d'adoption, conformément aux exigences de gouvernance et aux résultats opérationnels, en tirant parti de la technologie, des outils et des solutions d'automatisation disponibles.

### <a name="ongoing-monthly-tasks"></a>Tâches mensuelles en cours

- Superviser les [processus de gestion des changements](../../migrate/migration-considerations/prerequisites/technical-complexity.md)
- Gérer les [backlogs de mise en production et de sprint](../../migrate/migration-considerations/assess/release-iteration-backlog.md)
- Créer et tenir à jour la zone d'adoption conformément aux exigences de gouvernance
- Accomplir les tâches techniques décrites dans les [backlogs de sprint](../../migrate/migration-considerations/assess/release-iteration-backlog.md)

### <a name="team-cadence"></a>Cadence de l’équipe

Nous vous recommandons que les équipes qui assurent les fonctionnalités d’adoption du cloud se consacrent à cet effort à plein temps.

Il est préférable que ces équipes se réunissent tous les jours de manière autonome. L’objectif de ces réunions quotidiennes est de mettre à jour rapidement le backlog et de communiquer ce qui a été effectué, ce qui doit être fait aujourd’hui et les différents points de blocage et tout ce qui nécessite un support externe supplémentaire.

Le calendrier de mise en production et la durée des itérations sont propres à chaque entreprise. Toutefois, la durée moyenne semble être une plage d’une à quatre semaines par itération. Quelle que soit la cadence des itérations et des mises en production, nous vous recommandons que l’équipe rencontre toutes les équipes qui l’assistent à la fin de chaque mise en production afin de communiquer le résultat de cette mise en production et de réorganiser les efforts restants. Il est également utile de se réunir en équipe à la fin de chaque sprint, avec l'équipe du [centre d'excellence du cloud](./cloud-center-of-excellence.md) ou l'[équipe de gouvernance du cloud](./cloud-governance.md), pour rester aligné sur les efforts et besoins communs.

Certaines des tâches techniques associées à l’adoption du cloud peuvent devenir répétitives. Les membres de l’équipe doivent tourner tous les 3 à 6 mois pour éviter les problèmes de satisfaction des employés et tenir les compétences à jour. Un siège tournant dans le [centre d’excellence du cloud](./cloud-center-of-excellence.md) ou l’[équipe de gouvernance du cloud](./cloud-governance.md) peut offrir une excellente opportunité de préserver la motivation des employés et d’exploiter de nouvelles innovations.

## <a name="baseline-capability"></a>Fonctionnalités de base

Selon les résultats souhaités par l’entreprise, les aptitudes nécessaires pour fournir des capacités complètes d’adoption du cloud peuvent être fournies par les services suivants :

- Personnes en charge de l'implémentation de l'infrastructure
- Ingénieurs DevOps
- Développeurs d'applications
- Scientifiques des données
- Spécialistes des plateformes de données ou d'applications

Pour une collaboration et une efficacité optimales, nous recommandons que les équipes chargées de l’adoption du cloud se composent en moyenne de six personnes. Ces équipes doivent s’organiser de façon autonome d’un point de vue technique. Nous recommandons vivement que ces équipes incluent également une expertise en matière de gestion de projet, avec une expérience approfondie dans les modèles agile, Scrum ou autres modèles itératifs. Cette équipe est plus efficace lorsqu’elle est gérée à l’aide d’une hiérarchie à plat.

## <a name="out-of-scope"></a>Hors propos

Un soutien supplémentaire du personnel informatique existant peut être nécessaire. L'équipe informatique peut apporter une contribution précieuse à l'adoption du cloud en devenant un courtier cloud et un partenaire pour l'innovation et l'agilité métier.

- [Responsabilités de l'équipe informatique centrale](../../organize/central-it.md)

## <a name="whats-next"></a>Étapes suivantes

L’adoption est intéressante, mais l’adoption anarchique peut produire des résultats inattendus. L'alignement avec l'[équipe de gouvernance du cloud](./cloud-governance.md) permet d'accélérer l'adoption et d'implémenter les meilleures pratiques tout en réduisant les risques métier et les risques techniques.

Ces deux équipes créent un équilibre entre les efforts d'adoption du cloud, mais celui-ci est considéré comme un MVP car il peut ne pas être durable. Chaque équipe endosse plusieurs rôles et caractéristiques, comme indiqué dans les tableaux [*réalisateur, approbateur, consulté, informé* (RACI)](../../organize/raci-alignment.md).

Découvrez-en plus sur les [antimodèles organisationnels : silos et fiefs](../../organize/fiefdoms-silos.md).
