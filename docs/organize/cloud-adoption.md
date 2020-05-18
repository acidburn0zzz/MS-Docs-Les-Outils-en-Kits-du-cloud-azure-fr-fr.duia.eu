---
title: Présentation des fonctions d’adoption du cloud
description: Découvrez comment les fonctions d’adoption du cloud donnent accès à des solutions techniques vous permettant de composer vos équipes de façon appropriée.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/20/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: ac8307d3af159f3d6d35ccf2ded55f77786a33d7
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83215872"
---
# <a name="cloud-adoption-functions"></a>Fonctions d’adoption du cloud

Les fonctions d’adoption du cloud permettent d’implémenter des solutions techniques dans le cloud. Comme tout projet informatique, les personnes qui effectuent réellement le travail en déterminent la réussite. Les équipes qui assurent les fonctions d’adoption du cloud nécessaires peuvent être composées de plusieurs experts ou partenaires d’implémentation.

Les équipes chargées de l’adoption du cloud sont l’équivalent moderne des équipes de mise en œuvre technique ou des équipes de projet. Toutefois, la nature du cloud peut nécessiter une équipe à la structure plus fluide. Certaines équipes se concentrent exclusivement sur la migration cloud, tandis que d’autres équipes se concentrent sur des innovations qui tirent parti des technologies cloud. Certaines équipes incluent une expertise technique large, nécessaire pour les efforts d’adoption importants comme la migration complète d’un centre de données. D’autres équipes ont un objectif technique plus spécifique et peuvent passer d’un projet à l’autre pour atteindre des objectifs spécifiques. Par exemple, une équipe de spécialistes de la plateforme de données qui aident à convertir des machines virtuelles SQL en instances SQL PaaS.

Quel que soit le type ou le nombre d’équipes chargées de l’adoption du cloud, les fonctionnalités nécessaires pour l’adoption du cloud sont fournies par des experts en informatique ou en analyse d’entreprise ou par des partenaires d’implémentation.

Selon les résultats opérationnels souhaités, les compétences nécessaires pour assurer des fonctions complètes d’adoption du cloud peuvent être les suivantes :

- Personnes en charge de l’implémentation de l’infrastructure
- Ingénieurs DevOps
- Développeurs d’applications
- Scientifiques des données
- Spécialistes des plateformes de données ou des applications

Pour une collaboration et une efficacité optimales, nous recommandons que les équipes chargées de l’adoption du cloud se composent en moyenne de six personnes. Ces équipes doivent s’organiser de façon autonome d’un point de vue technique. Nous recommandons vivement que ces équipes incluent également une expertise en matière de gestion de projet, avec une expérience approfondie dans les modèles agile, Scrum ou autres modèles itératifs. Cette équipe est plus efficace lorsqu’elle est gérée à l’aide d’une hiérarchie à plat.

## <a name="preparation"></a>Préparation

- [Création d’un compte Azure](https://docs.microsoft.com/learn/modules/create-an-azure-account) : La première étape pour utiliser Azure est de créer un compte.
- [Portail Azure](https://docs.microsoft.com/learn/modules/tour-azure-portal): Découvrez les fonctionnalités du portail et des services Azure, et personnalisez le portail.
- [Présentation d’Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) : Bien démarrer avec Azure. Créez et configurez votre première machine virtuelle dans le cloud.
- [Notions de base d’Azure](https://docs.microsoft.com/learn/paths/azure-for-the-data-engineer) : Découvrez les concepts du cloud, familiarisez-vous avec les avantages, comparez et confrontez les stratégies de base et explorez l’éventail des services disponibles dans Azure.
- Consultez la [méthodologie Migration](../migrate/index.md).

## <a name="minimum-scope"></a>Étendue minimale

L’équipe chargée de la migration cloud constitue le noyau de tous les efforts de migration cloud. Cette équipe pilote les modifications techniques qui permettent l’adoption du cloud. Selon les objectifs de l’effort d’adoption, cette équipe peut comprendre des membres aux compétences diverses qui s’occupent d’un large éventail de tâches techniques et commerciales.

Au minimum, l’étendue de l’équipe comprend les aspects suivants :

- [Rationalisation du patrimoine numérique](../digital-estate/index.md)
- Examen, validation et progression du [backlog de migration classé par ordre de priorité](../migrate/migration-considerations/assess/release-iteration-backlog.md)
- Exécution de la [première charge de travail](../digital-estate/rationalize.md#select-the-first-workload) comme opportunité d’apprentissage.

## <a name="deliverable"></a>Livrable

Le besoin principal pour une fonction d’adoption du cloud est l’implémentation rapide et de qualité des solutions techniques présentées dans le plan d’adoption. Ces solutions doivent s’aligner sur les exigences de gouvernance et les résultats opérationnels, et tirer parti de la technologie, des outils et des solutions d’automatisation disponibles pour l’équipe.

**Tâches de planification précoces :**

- Exécuter la [rationalisation du patrimoine numérique](../digital-estate/index.md).
- Examiner, valider et faire avancer le [backlog de migration classé par ordre de priorité](../migrate/migration-considerations/assess/release-iteration-backlog.md).
- Commencer l’exécution de la [première charge de travail](../digital-estate/rationalize.md#select-the-first-workload) comme opportunité d’apprentissage.

**Tâches mensuelles en cours :**

- Superviser les [processus de gestion des changements](../migrate/migration-considerations/prerequisites/technical-complexity.md).
- Gérer les [backlogs de mise en production et de sprint](../migrate/migration-considerations/assess/release-iteration-backlog.md).
- Créer et maintenir la zone d’atterrissage d’adoption conformément aux exigences de gouvernance.
- Exécuter les tâches techniques définies dans les [backlogs de sprint](../migrate/migration-considerations/assess/release-iteration-backlog.md).

**Cadence des réunions :**

Nous recommandons que les équipes qui assurent les fonctions d’adoption du cloud se consacrent à cet effort à temps plein.

Il est préférable que ces équipes se réunissent tous les jours de manière autonome. L’objectif de ces réunions quotidiennes est de mettre à jour rapidement le backlog et de communiquer ce qui a été effectué, ce qui doit être fait aujourd’hui et les différents points de blocage et tout ce qui nécessite un support externe supplémentaire.

Le calendrier de mise en production et la durée des itérations sont propres à chaque entreprise. Toutefois, la durée moyenne semble être une plage d’une à quatre semaines par itération. Quelle que soit la cadence des itérations et des mises en production, nous vous recommandons que l’équipe rencontre toutes les équipes qui l’assistent à la fin de chaque mise en production afin de communiquer le résultat de cette mise en production et de réorganiser les efforts restants. De même, il est intéressant que l’équipe organise une réunion à la fin de chaque sprint avec l’équipe du centre d’excellence cloud ou l’équipe chargée de la gouvernance cloud, afin de rester alignée sur les efforts et les besoins de support communs.

Certaines des tâches techniques associées à l’adoption du cloud peuvent devenir répétitives. Les membres de l’équipe doivent tourner tous les 3 à 6 mois pour éviter les problèmes de satisfaction des employés et tenir les compétences à jour. Un roulement dans le centre d’excellence cloud ou l’équipe chargée de la gouvernance cloud peut offrir un excellent moyen de préserver la motivation des employés et de mobiliser de nouvelles innovations.

Découvrez plus en détail la fonction d’un [centre d’excellence cloud](./cloud-center-of-excellence.md) ou d’une [équipe chargée de la gouvernance cloud](./cloud-governance.md).

## <a name="next-steps"></a>Étapes suivantes

- [Créer une équipe chargée de l’adoption du cloud](../get-started/team/cloud-adoption.md)
- Alignez les efforts d’adoption du cloud avec les [fonctions de gouvernance cloud](./cloud-governance.md) pour accélérer l’adoption et implémenter les meilleures pratiques, tout en réduisant les risques métier et techniques.
