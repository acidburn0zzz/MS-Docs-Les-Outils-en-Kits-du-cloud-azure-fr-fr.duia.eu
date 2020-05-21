---
title: Comprendre les fonctions de migration vers le cloud
description: Comprendre les fonctions de migration vers le cloud.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.topic: conceptual
ms.date: 04/04/2020
ms.openlocfilehash: 876705322aad42ac2dac0eb29d7291d6d6df71ec
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83401001"
---
# <a name="cloud-migration-functions"></a>Fonctions de migration cloud

Les équipes chargées de la migration vers le cloud sont l’équivalent moderne des équipes de mise en œuvre technique ou des équipes de projet. Toutefois, la nature du cloud peut nécessiter une équipe à la structure plus fluide. Certaines équipes de migration se concentrent exclusivement sur la migration cloud, tandis que d’autres se concentrent sur des innovations qui tirent parti des technologies cloud. Certaines incluent l’expertise technique large requise pour effectuer des efforts d’adoption importants, comme une migration complète de centre de données, tandis que d’autres ont un objectif technique plus étroit et peuvent passer d’un projet à l’autre pour atteindre des objectifs spécifiques, par exemple une équipe de spécialistes en plateforme de données qui aident à convertir des machines virtuelles SQL en instances SQL PaaS.

Quel que soit le type ou le nombre d’équipes de migration vers le cloud, ces équipes fournissent généralement une expertise pour l’informatique, l’analyse commerciale ou les partenaires de mise en œuvre.

## <a name="prerequisites"></a>Prérequis

- [Création d’un compte Azure](https://docs.microsoft.com/learn/modules/create-an-azure-account) : La première étape pour utiliser Azure est de créer un compte.
- [Portail Azure](https://docs.microsoft.com/learn/modules/tour-azure-portal): Découvrez les fonctionnalités du portail et des services Azure, et personnalisez le portail.
- [Présentation d’Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) : Bien démarrer avec Azure. Créez et configurez votre première machine virtuelle dans le cloud.
- [Notions de base d’Azure](https://docs.microsoft.com/learn/paths/azure-for-the-data-engineer) : Découvrez les concepts du cloud, familiarisez-vous avec les avantages, comparez et confrontez les stratégies de base, et explorez l'éventail des services disponibles dans Azure.
- Consultez la [méthodologie Migration](../migrate/index.md).

## <a name="minimum-scope"></a>Étendue minimale

L'équipe chargée de la migration vers le cloud constitue le noyau de tous les efforts de migration vers le cloud. Cette équipe pilote les modifications techniques qui permettent l’adoption du cloud. Selon les objectifs de l’effort d’adoption, cette équipe peut comprendre des membres aux compétences diverses qui s’occupent d’un large éventail de tâches techniques et commerciales.

Au minimum, l’étendue de l’équipe comprend les aspects suivants :

- [Rationalisation du patrimoine numérique](../digital-estate/index.md)
- Examen, validation et progression du [backlog de migration classé par ordre de priorité](../migrate/migration-considerations/assess/release-iteration-backlog.md)
- Exécution de la [première charge de travail](../digital-estate/rationalize.md#select-the-first-workload) comme opportunité d’apprentissage.

## <a name="deliverable"></a>Livrable

Le livrable principal de toute équipe chargée de la migration vers le cloud est la mise en œuvre en temps réel des solutions techniques présentées dans le plan d'adoption, conformément aux exigences de gouvernance et aux résultats opérationnels, en tirant parti de la technologie, des outils et des solutions d'automatisation disponibles.

### <a name="ongoing-monthly-tasks"></a>Tâches mensuelles en cours

- Superviser le [processus de gestion des changements](../migrate/migration-considerations/prerequisites/technical-complexity.md).
- Gérer les [backlogs de mise en production et de sprint](../migrate/migration-considerations/assess/release-iteration-backlog.md)
- Créer et tenir à jour la zone d’adoption conformément aux exigences de gouvernance.
- Accomplir les tâches techniques décrites dans les [backlogs de sprint](../migrate/migration-considerations/assess/release-iteration-backlog.md)

### <a name="team-cadence"></a>Cadence de l’équipe

Nous vous recommandons que les équipes qui assurent les fonctionnalités d’adoption du cloud se consacrent à cet effort à plein temps.

Il est préférable que ces équipes se réunissent tous les jours de manière autonome. L’objectif de ces réunions quotidiennes est de mettre à jour rapidement le backlog et de communiquer ce qui a été effectué, ce qui doit être fait aujourd’hui et les différents points de blocage et tout ce qui nécessite un support externe supplémentaire.

Le calendrier de mise en production et la durée des itérations sont propres à chaque entreprise. Toutefois, la durée moyenne semble être une plage d’une à quatre semaines par itération. Quelle que soit la cadence des itérations et des mises en production, nous vous recommandons que l’équipe rencontre toutes les équipes qui l’assistent à la fin de chaque mise en production afin de communiquer le résultat de cette mise en production et de réorganiser les efforts restants. Il est également utile de se réunir en équipe à la fin de chaque sprint, avec l'équipe du [centre d'excellence du cloud](../organize/cloud-center-of-excellence.md) ou l'[équipe de gouvernance du cloud](./cloud-governance.md), pour rester aligné sur les efforts et besoins communs.

Certaines des tâches techniques associées à l’adoption du cloud peuvent devenir répétitives. Les membres de l’équipe doivent tourner tous les 3 à 6 mois pour éviter les problèmes de satisfaction des employés et tenir les compétences à jour. Un siège tournant dans le [centre d’excellence du cloud](../organize/cloud-center-of-excellence.md) ou l’[équipe de gouvernance du cloud](./cloud-governance.md) peut offrir une excellente opportunité de préserver la motivation des employés et d’exploiter de nouvelles innovations.

## <a name="baseline-capability"></a>Fonctionnalités de base

Selon les résultats souhaités par l’entreprise, les aptitudes nécessaires pour fournir des capacités complètes d’adoption du cloud peuvent être fournies par les services suivants :

- Personnes en charge de l’implémentation de l’infrastructure
- Ingénieurs DevOps
- Développeurs d’applications
- Scientifiques des données
- Spécialistes des plateformes de données ou des applications

Pour une collaboration et une efficacité optimales, nous recommandons que les équipes chargées de l’adoption du cloud se composent en moyenne de six personnes. Ces équipes doivent s’organiser de façon autonome d’un point de vue technique. Nous recommandons vivement que ces équipes incluent également une expertise en matière de gestion de projet, avec une expérience approfondie dans les modèles agile, Scrum ou autres modèles itératifs. Cette équipe est plus efficace lorsqu’elle est gérée à l’aide d’une hiérarchie à plat.

## <a name="out-of-scope"></a>Hors propos

Un soutien supplémentaire du personnel informatique existant peut être nécessaire. L’informatique peut être un contributeur important à l’adoption du cloud en devenant un courtier cloud et un partenaire pour l’innovation et l’agilité métier.

- [Responsabilités de l'équipe informatique centrale](../organize/central-it.md)

## <a name="whats-next"></a>Étapes suivantes

L’adoption est intéressante, mais l’adoption anarchique peut produire des résultats inattendus. L’alignement avec [l’équipe de gouvernance du cloud](./cloud-governance.md) accélère l’adoption et les meilleures pratiques,tout en réduisant les risques commerciaux et techniques.

Ces deux équipes créent un équilibre entre les efforts d’adoption du cloud, mais elles sont considérées comme un MVP, car elles peuvent ne pas être durables. Chaque équipe endosse plusieurs rôles et caractéristiques, comme indiqué dans les tableaux [*réalisateur, approbateur, consulté, informé* (RACI)](../organize/raci-alignment.md).

Découvrez-en plus sur les [antimodèles organisationnels : silos et fiefs](../organize/fiefdoms-silos.md).
