---
title: 'Se préparer à la complexité culturelle : alignement des rôles et des responsabilités'
description: Préparez-vous à la complexité culturelle en alignant les rôles et les responsabilités.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 186772796694d6ef60a923c5098760a573d8db6d
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76801492"
---
# <a name="prepare-for-cultural-complexity-aligning-roles-and-responsibilities"></a>Se préparer à la complexité culturelle : alignement des rôles et des responsabilités

Une bonne compréhension de la culture requise pour exécuter les centres de données existants est importante pour la réussite de toute migration. Dans certaines organisations, la gestion des centres de données est contenue dans des équipes d’opérations informatiques centralisées. Dans ces équipes centralisées, les rôles et les responsabilités tendent à être bien définis et bien compris dans toute l’équipe. Pour les entreprises de plus grande taille, en particulier celles liées par des exigences de conformité tierces, la culture tend à être plus nuancée et complexe. La complexité de la culture peut entraîner des obstacles difficiles à comprendre et longs à surmonter.

Dans les deux scénarios, il est judicieux d’investir dans la documentation des rôles et des responsabilités requis pour effectuer une migration. Cet article présente certains des rôles et responsabilités observés dans le cadre de la migration d’un centre de données, afin de servir de modèle pour la documentation qui peut favoriser la clarté tout au long de l’exécution.

## <a name="business-functions"></a>Fonctions commerciales

Dans toute migration, il existe quelques fonctions clés qui sont le mieux exécutées par l’entreprise, dans la mesure du possible. L’équipe informatique est souvent capable d’effectuer les tâches suivantes. Toutefois, la participation de membres de l’entreprise peut contribuer à réduire les obstacles plus tard dans le processus d’adoption. Cela garantit également un investissement mutuel des parties prenantes principales tout au long du processus de migration.

| Process | Activité | Description |
|---------|---------|---------|
| Évaluer | Objectifs métier | Définissez les résultats métier souhaités de l’effort de migration. |
| Évaluer | Priorités | Assurez l’alignement sur l’évolution des priorités de l’entreprise et des conditions du marché. |
| Évaluer | Justification | Validez les hypothèses qui sous-tendent l’évolution des justifications métier. |
| Évaluer | Risque | Aidez l’équipe d’adoption du cloud à comprendre l’impact des risques commerciaux tangibles. |
| Évaluer | Approbation | Passez en revue et approuvez l’impact commercial des modifications d’architecture proposées. |
| Optimiser | Changement du plan | Définissez un plan de consommation du changement au sein de l’entreprise, y compris les périodes de faible activité et les gels de modifications. |
| Optimiser | Test | Alignez les utilisateurs avancés capables de valider le niveau de performance et les fonctionnalités. |
| Sécuriser et gérer | Impact de l’interruption | Aidez l’équipe d’adoption du cloud à quantifier l’impact d’une interruption du processus métier. |
| Sécuriser et gérer | Validation du contrat de niveau de service (SLA) | Aidez l’équipe d’adoption du cloud à définir des contrats de niveau de service et des tolérances acceptables pour les pannes d’activité. |

Au final, l’équipe d’adoption du cloud est responsable de chacune de ces activités. Toutefois, l’établissement de responsabilités et d’une cadence régulière avec l’entreprise pour l’exécution de ces activités sur un rythme établi peut améliorer l’alignement et la cohésion des parties prenantes avec l’entreprise.

## <a name="common-roles-and-responsibilities"></a>Rôles et responsabilités courants

Chaque processus au sein de la discussion sur les principes de migration du Framework d’adoption du cloud comprend un article de processus traitant des activités spécifiques visant à aligner les rôles et les responsabilités. Par souci de clarté lors de l’exécution, une seule partie responsable doit être affectée pour chaque activité, ainsi que les parties responsables nécessaires pour prendre en charge ces activités. Toutefois, la liste suivante contient une série de rôles et de responsabilités courants qui ont un impact plus important sur l’exécution de la migration. Ces rôles doivent être identifiés au début de l’effort de migration.

> [!NOTE]
> Dans le tableau suivant, une partie responsable doit commencer l’alignement des rôles. Cette colonne doit être personnalisée pour s’adapter aux processus existants en vue d’une exécution efficace. Idéalement, une seule personne doit être nommée en tant que partie responsable.

| Process | Activité | Description | Partie responsable |
|---------|---------|---------|---------|
| Configuration requise | Patrimoine numérique | Alignez l’inventaire existant sur les hypothèses de base, en fonction des résultats métier. | équipe de stratégie cloud |
| Configuration requise | Backlog de migration | Classez par ordre de priorité la séquence des charges de travail à migrer. | équipe de stratégie cloud |
| Évaluer | Architecture | Défiez les hypothèses initiales pour définir l’architecture cible en fonction des métriques d’utilisation. | équipe d’adoption du cloud |
| Évaluer | Approbation | Approuvez l’architecture proposée. | équipe de stratégie cloud |
| Migrer | Accès à la réplication | Accès aux ressources et hôtes locaux existants pour établir des processus de réplication. | équipe d’adoption du cloud |
| Optimiser | Ready | Vérifiez que le système répond aux exigences en matière de niveau de performance et de coût avant la promotion. | équipe d’adoption du cloud |
| Optimiser | Promouvoir | Autorisations pour promouvoir une charge de travail en production et rediriger le trafic de production. | équipe d’adoption du cloud |
| Sécuriser et gérer | Transition d’opérations | Documentez les systèmes de production avant les opérations de production. | équipe d’adoption du cloud |

> [!CAUTION]
> Pour ces activités, les autorisations et les privilèges influencent de manière importante la partie responsable, qui doit avoir un accès direct aux systèmes de production dans l’environnement existant ou doit disposer d’un moyen de sécuriser l’accès par d’autres intervenants responsables. Déterminer ce tiers responsable influence directement la stratégie de promotion pendant les processus de migration et d’optimisation.

## <a name="next-steps"></a>Étapes suivantes

Lorsque l’équipe a une compréhension générale des rôles et des responsabilités, il est temps de commencer à préparer les détails techniques de la migration. Comprendre [la complexité technique et la gestion des changements](./technical-complexity.md) peut aider à préparer l’équipe d’adoption du cloud à la complexité technique de la migration en l’alignant sur un processus incrémentiel de gestion des changements.

> [!div class="nextstepaction"]
> [Complexité technique et gestion des changements](./technical-complexity.md)
