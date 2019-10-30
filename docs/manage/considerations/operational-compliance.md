---
title: 'Conformité opérationnelle : Gestion cloud et opérations'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Conformité opérationnelle : Gestion cloud et opérations'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: bb6e4584da87d992f85b6ce90e21081c9c19d7c3
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682540"
---
# <a name="operational-compliance-in-cloud-management"></a>Conformité opérationnelle dans la gestion cloud

La conformité opérationnelle s’appuie sur la discipline de l’[inventaire et la visibilité](./inventory.md) comme première étape exploitable de la gestion cloud. Cette discipline est axée sur les révisions de télémétrie régulières et les mesures correctives (mesures proactives et réactives). Cette discipline est la pierre angulaire qui maintient l’équilibre entre la sécurité, la gouvernance, les performances et les coûts.

## <a name="components-of-operations-compliance"></a>Composants de conformité des opérations

Le maintien de la conformité envers les engagements opérationnels requiert l’analyse, l’automatisation et la correction humaine. Une conformité opérationnelle efficace nécessite une cohérence dans quelques processus critiques :

1. Cohérence des ressources
2. Cohérence de l’environnement
3. Cohérence de la configuration des ressources
4. Cohérence des mises à jour
5. Automatisation de la correction

### <a name="resource-consistency"></a>Cohérence des ressources

L’action la plus efficace pour une équipe de gestion cloud en matière de conformité opérationnelle consiste à établir une cohérence dans l’organisation et le balisage des ressources. Lorsque les ressources sont organisées et marquées de manière cohérente, toutes les autres tâches opérationnelles deviennent plus faciles. Pour obtenir des conseils plus approfondis sur la cohérence des ressources, consultez la [phase de gouvernance](../../govern/index.md) du cycle de vie dans l’adoption du cloud. Plus précisément, les [articles sur les bases de la gouvernance initiale](../../govern/initial-foundation.md) illustrent des méthodes pour commencer à développer la cohérence des ressources.

### <a name="environment-consistency"></a>Cohérence de l’environnement

Les environnements cohérents, ou zones d’accueil, constituent la deuxième étape la plus importante vers la conformité opérationnelle. Lorsque les zones d’accueil sont cohérentes et appliquées par le biais d’outils automatisés, il est beaucoup moins complexe de diagnostiquer et de résoudre les problèmes opérationnels. Pour obtenir des conseils plus approfondis sur la cohérence de l’environnement, consultez la [phase de préparation](../../ready/index.md) du cycle de vie dans l’adoption du cloud. Les exercices de cette phase établissent un processus reproductible pour définir et affiner une approche cohérente du code en priorité pour le développement d’environnements basés sur le cloud.

### <a name="resource-configuration-consistency"></a>Cohérence de la configuration des ressources

En s’appuyant sur les approches de gouvernance et de préparation, la gestion du cloud doit inclure des processus de surveillance et d’évaluation en continu du respect des exigences en matière de cohérence des ressources. À mesure que les charges de travail changent ou que de nouvelles versions sont adoptées, il est essentiel que les processus de gestion du cloud évaluent toutes modifications de configuration, qui ne sont pas facilement encadrées par des moyens automatisés.

Lorsque des incohérences sont découvertes, certaines sont résolues par la cohérence des mises à jour et d’autres peuvent être corrigées automatiquement.

### <a name="update-consistency"></a>Cohérence des mises à jour

La stabilité permet des opérations stables. Toutefois, certaines modifications sont nécessaires dans les processus de gestion du cloud. Plus précisément, les modifications régulières des correctifs et des performances sont essentielles pour réduire les interruptions et contrôler les coûts.

L’un des nombreux avantages d’une méthodologie de gestion du cloud mature est la stabilisation et le contrôle des modifications nécessaires.

Toute ligne de base de gestion du cloud doit inclure un moyen de planifier, de contrôler et éventuellement d’automatiser les mises à jour nécessaires. Ces mises à jour doivent au moins inclure des correctifs, mais elles peuvent également inclure des performances, le dimensionnement et d’autres aspects de la mise à jour des ressources.

### <a name="remediation-automation"></a>Automatisation de la correction

En tant que ligne de base améliorée pour la gestion du cloud, certaines charges de travail peuvent tirer parti de la correction automatisée. Lorsqu’une charge de travail rencontre généralement des problèmes qui ne peuvent pas être résolus par le biais de modifications du code ou de l’architecture, l’automatisation des mises à jour peut réduire la charge de gestion du cloud et accroître la satisfaction des utilisateurs.

La plupart des problèmes, qui sont assez courants à automatiser, doivent être résolus par la résolution de la dette technique. Lorsque la résolution à long terme est préférable, elle doit être l’option par défaut. Toutefois, il existe un certain nombre de scénarios d’entreprise qui rendent difficile la justification d’importants investissements en matière de résolution de la dette technique. Lorsque la résolution de la dette technique ne peut pas être justifiée, mais que la mise à jour est un problème courant et coûteux, la correction automatisée est la meilleure solution.

## <a name="next-steps"></a>Étapes suivantes

La[protection et la récupération](./protect.md) sont les points suivants à prendre en compte dans une ligne de base de gestion du cloud.

> [!div class="nextstepaction"]
> [Protection et récupération](./protect.md)
