---
title: Développer un plan de changement pour l’entreprise
description: Utilisez le Cloud Adoption Framework pour Azure afin de voir comment un plan de changement pour l’entreprise peut vous aider à implémenter un plan d’adoption plus large visant les utilisateurs.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: fd8db03a28c5372ad5ca796607a079ffdcbe4f92
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80355282"
---
# <a name="business-change-plan"></a>Plan de changement pour l’entreprise

Traditionnellement, le service informatique a supervisé la mise en production des nouvelles charges de travail. Au cours d’une transformation majeure, comme la migration d’un centre de données ou une migration cloud, il est possible d’appliquer un modèle similaire d’adoption cloud par les prospects informatiques. Toutefois, l’approche traditionnelle pourrait laisser passer des occasions de réaliser une valeur commerciale supplémentaire. Pour cette raison, avant qu’une charge de travail migrée soit promue en production, il est suggéré d’implémenter une approche plus large pour l’adoption par les utilisateurs. Cet article décrit les façons dont un plan des changements opérationnels s’ajoute à un plan standard d’adoption par les utilisateurs.

## <a name="traditional-user-adoption-approach"></a>Approche traditionnelle de l’adoption par les utilisateurs

Les plans d’adoption par les utilisateurs se concentrent sur la façon dont les utilisateurs adopteront une nouvelle technologie ou changeront pour une technologie donnée. Cette approche a fait ses preuves en matière d’initiation des utilisateurs à de nouveaux outils. Dans un plan classique d’adoption par les utilisateurs, le service informatique se concentre sur l’installation, la configuration, la maintenance et la formation associées aux changements techniques introduits dans l’environnement de l’entreprise.

Bien que les approches puissent varier, les thèmes généraux sont présents dans la plupart des plans d’adoption par les utilisateurs. Ces thèmes sont généralement fondés sur une approche de contrôle des risques et de facilitation qui s’aligne sur les améliorations incrémentielles. La matrice Eason, illustrée dans la figure ci-dessous, représente les facteurs qui sous-tendent ces thèmes pour un éventail de types d’adoption.

![Matrice Eason des préoccupations relatives à l’adoption par les utilisateurs](../../../_images/migrate/eason-matrix.jpg)

*Matrice Eason des types d’adoption par les utilisateurs.*

Ces thèmes reposent souvent sur l’hypothèse que l’introduction de nouvelles solutions aux utilisateurs doit se concentrer en grande partie sur le contrôle des risques et la facilitation du changement. En outre, le service informatique s’est principalement concentré sur les risques liés aux changements technologiques et à la facilitation de ces changements.

## <a name="create-business-change-plans"></a>Créer des plan de changements dans l’entreprise

Un plan des changements opérationnels va au-delà des changements techniques et suppose que chaque mise en production d’un effort de migration entraîne un certain niveau de changement dans les processus métier. Il regarde en amont et en aval des changements techniques. Les questions suivantes permettent aux participants de réfléchir à l’adoption par les utilisateurs du point de vue des changements opérationnels, afin d’optimiser l’impact sur l’activité :

**Questions en amont.** Les questions en amont examinent les impacts ou les changements qui surviennent avant l’adoption par les utilisateurs :

- Un [résultat métier](../../../strategy/business-outcomes/index.md) attendu a-t-il été quantifié ?
- L’impact sur l’entreprise correspond-il à des [paramètres d’apprentissage](../../../strategy/learning-metrics.md) définis ?
- Quels sont les processus métier et les équipes qui tirent parti de cette solution technique ?
- Qui dans l’entreprise peut le mieux coordonner les utilisateurs avancés pour les tests et les commentaires ?
- Les chefs d’entreprise concernés ont-ils participé à l’établissement des priorités et à la planification de la migration ?
- Existe-t-il des événements ou dates critiques pour l’entreprise qui peuvent être concernés par ces changements ?
- Le plan des changements opérationnels maximise-t-il l’impact tout en minimisant la perturbation des activités ?
- Un temps d’arrêt est-il prévu ? Une fenêtre de temps d’arrêt a-t-elle été communiquée aux utilisateurs finaux ?

**Questions en aval.** Une fois l’adoption terminée, les changements opérationnels peuvent commencer. Malheureusement, c’est là que s’arrêtent de nombreux plans d’adoption par les utilisateurs. Les questions en aval aident l’équipe de stratégie cloud à se concentrer sur la transformation une fois que les changements techniques sont terminés :

- Les utilisateurs professionnels réagissent-ils bien aux changements ?
- L’anticipation du niveau de performance a-t-elle été maintenue, maintenant que les changements techniques ont été adoptés ?
- Les processus métier ou les expériences client évoluent-ils de la façon prévue ?
- D’autres changements sont-ils nécessaires pour réaliser les paramètres d’apprentissage ?
- Les changements se sont-ils alignés sur les résultats métier ciblés ? Si ce n’est pas le cas, pourquoi ?
- D’autres changements sont-ils nécessaires pour contribuer aux résultats métier ?
- Des effets négatifs ont-ils été observés à la suite de ces changements ?

Le plan des changements opérationnels varie d’une société à une autre. L’objectif de ces questions est de mieux intégrer l’entreprise dans les changements associés à chaque mise en production. En considérant chaque mise en production non pas comme un changement technologique à adopter, mais plutôt comme un plan des changements opérationnels, les résultats métier peuvent devenir plus accessibles.

## <a name="next-steps"></a>Étapes suivantes

Une fois que les changements opérationnels sont documentés et planifiés, les [tests d’entreprise](./business-test.md) peuvent commencer.

> [!div class="nextstepaction"]
> [Conseils pour les tests d’entreprise (UAT) pendant la migration](./business-test.md)

## <a name="references"></a>References

<!-- cSpell:ignore Eason -->

- Eason, K. (1988) _Information technology and organizational change_, New York : Taylor and Francis.
