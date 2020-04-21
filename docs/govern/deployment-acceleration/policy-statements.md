---
title: Exemples d’instructions de stratégie pour l’accélération du déploiement
description: Utilisez le Framework d’adoption du cloud pour Azure pour obtenir des exemples de déclarations de stratégie d’accélération du déploiement qui vous aideront à élaborer des déclarations de stratégie.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 18eef9f270e4c9ab8b2ee31268e46f0d4d929e34
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80995525"
---
# <a name="deployment-acceleration-sample-policy-statements"></a>Exemples d’instructions de stratégie pour l’accélération du déploiement

Les instructions de stratégie cloud individuelles sont des recommandations destinées à traiter des risques spécifiques identifiés lors de votre processus d’évaluation des risques. Ces instructions doivent fournir un bref récapitulatif des risques, ainsi que des plans établis pour les gérer. Chaque définition d’instruction doit inclure les informations suivantes :

- **Risque technique :** un récapitulatif du risque que cette stratégie gérera.
- **Instruction de stratégie :** Une explication succincte claire des exigences de la stratégie.
- **Options de conception :** Recommandations exploitables, spécifications ou autres conseils que des équipes informatiques et des développeurs peuvent utiliser lors de l’implémentation de la stratégie.

Les exemples d’énoncés de stratégie suivants traitent des risques métiers courants liés aux configurations. Ces énoncés sont des exemples que vous pouvez référencer lorsque vous rédigez des énoncés de stratégie pour répondre aux besoins de votre organisation. Ces exemples ne sont pas destinés à être normatifs, et il existe potentiellement plusieurs options de stratégie pour gérer chaque risque identifié. Travaillez en étroite collaboration avec les équipes métier et les équipes informatiques pour identifier les meilleures stratégies pour vos propres risques.

## <a name="reliance-on-manual-deployment-or-configuration-of-systems"></a>Dépendance aux déploiements ou configurations manuels des systèmes

**Risque technique :** dépendre des interventions humaines lors d’un déploiement ou d’une configuration augmente le risque d’erreur humaine et réduit la répétabilité et la prévisibilité des configurations et déploiements des systèmes. En règle générale, cela ralentit le déploiement des ressources du système.

**Instruction de stratégie :** dans la mesure du possible, toutes les ressources déployées dans le cloud doivent être déployées à l’aide de modèles ou de scripts d’automatisation.

**Options de conception potentielles** : les [modèles Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/templates/overview) permettent d’utiliser l’infrastructure en tant que code pour déployer vos ressources sur Azure. Vous pouvez également utiliser [Terraform](https://docs.microsoft.com/azure/terraform/terraform-overview), qui vous offre un outil cohérent pour le déploiement local et dans le cloud.

## <a name="lack-of-visibility-into-system-issues"></a>Manque de visibilité sur les problèmes du système

**Risque technique :** une surveillance et des diagnostics insuffisants pour les systèmes métier empêchent le personnel responsable des opérations d’identifier et de corriger les problèmes avant une panne du système. En outre, cela peut augmenter de façon significative le temps nécessaire à la résolution d’une panne.

**Instruction de stratégie :** les stratégies suivantes seront implémentées :

- Des mesures de diagnostics et des métriques clés seront identifiées pour tous les composants et systèmes de production, et des outils de diagnostics et de surveillance seront appliqués à ces systèmes et surveillés de façon régulière par le personnel responsable des opérations.
- L’équipe responsable des opérations envisagera d’utiliser les outils de surveillance et de diagnostics dans les environnements autres que ceux de production, comme les environnements intermédiaires et AQ, pour identifier les problèmes des systèmes avant qu’ils ne se répercutent dans l’environnement de production.

**Options de conception potentielles** : [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor), qui inclut Log Analytics et Application Insights, fournit des outils pour la collecte et l’analyse des données de télémétrie afin de vous aider à comprendre le fonctionnement de vos applications et d’identifier de manière proactive les problèmes qu’elles rencontrent et les ressources dont elles dépendent. En outre, le [journal d’activité Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) signale toutes les modifications effectuées au niveau de la plateforme. Vous devez le superviser et vérifier pour identifier les modifications non conformes.

## <a name="configuration-security-reviews"></a>Révisions de la sécurité des configurations

**Risque technique :** au fil du temps, de nouvelles problématiques ou menaces de sécurité peuvent augmenter les risques liés à un accès non autorisé aux ressources sécurisées.

**Instruction de stratégie :** les processus de gouvernance cloud doivent inclure des révisions mensuelles avec les équipes de gestion de la configuration. L’objectif est d’identifier les modèles d’utilisation ou les acteurs malveillants devant être bloqués par la configuration des ressources cloud.

**Options de conception potentielles** : tous les mois, organisez une réunion destinée à la révision de la sécurité avec les membres de l’équipe de gouvernance et le personnel informatique responsable de la configuration des ressources et applications cloud. Passez en revue les métriques et données de sécurité existantes pour déterminer les écarts dans les outils et la stratégie d’accélération du déploiement actuels, puis mettez à jour la stratégie pour corriger les nouveaux risques.

## <a name="next-steps"></a>Étapes suivantes

Utilisez les exemples mentionnés dans cet article comme point de départ pour développer des stratégies qui répondent à des risques métier spécifiques, dans la continuité de vos plans d’adoption du cloud.

Pour commencer à développer vos instructions de stratégie personnalisées pour la gestion des identités, téléchargez le [modèle de base de référence des identités](../identity-baseline/template.md).

Pour accélérer l’adoption de cette discipline, choisissez le [guide de gouvernance actionnable](../guides/index.md) correspondant le mieux à votre environnement. Modifiez ensuite la conception pour intégrer vos décisions spécifiques en matière de stratégie d’entreprise.

Sur la base des risques et de la tolérance, établissez un processus de gouvernance et de communication en lien avec l’adhésion à la stratégie Accélération du déploiement.

> [!div class="nextstepaction"]
> [Établir des processus de conformité à la stratégie](./compliance-processes.md)
