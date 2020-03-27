---
title: Guide de décision pour l’application de la stratégie
description: Utilisez le Framework d’adoption du cloud pour Azure afin de découvrir les abonnements d’application de stratégie comme priorité de conception essentielle dans les migrations Azure.
author: rotycenh
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: f873e95e70fbc9afb06a4603d4be6f9e757d869f
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80355545"
---
# <a name="policy-enforcement-decision-guide"></a>Guide de décision pour l’application de la stratégie

La définition d’une stratégie n’est efficace que si elle peut être appliquée dans toute l’organisation. Un aspect clé de la planification de toute migration vers le cloud consiste à déterminer la meilleure façon de combiner les outils fournis par la plateforme cloud avec vos processus informatiques existants afin d’optimiser la conformité à la stratégie pour l’ensemble de vos ressources cloud.

![Traçage des options d’application de la stratégie de la moins complexe à la plus complexe, dans l’ordre des liens ci-dessous](../../_images/decision-guides/decision-guide-policy-enforcement.png)

Passer à : [Bonnes pratiques pour la base de référence](#baseline-best-practices) | [Supervision de la conformité à la stratégie](#policy-compliance-monitoring) | [Application de la stratégie](#policy-enforcement) | [Stratégie à l’échelle de l’organisation](#cross-organization-policy) | [Application automatisée](#automated-enforcement)

À mesure que grandira votre patrimoine cloud, vous aurez besoin de gérer et d’appliquer vos stratégies à un éventail plus vaste de ressources et d’abonnements. Pour répondre à l’augmentation du nombre de vos ressources et des besoins de stratégie de votre organisation, vous devez étendre la portée de vos processus d’application des stratégies afin de garantir une application cohérente des stratégies et une détection rapide des violations.

Les mécanismes d’application des stratégies fournis par la plateforme au niveau de la ressource ou de l’abonnement sont généralement suffisants pour les petits patrimoines cloud. Les déploiements plus grands justifient une portée d’application plus étendue et peuvent nécessiter des mécanismes d’application plus sophistiqués impliquant des standards de déploiement, des regroupements et une organisation des ressources, ainsi que l’intégration de l’application des stratégies aux systèmes de journalisation et de création de rapports.

Les principaux facteurs permettant de déterminer la portée de vos processus d’application des stratégies sont les [besoins de gouvernance cloud](../../govern/index.md) de votre organisation, la taille et la nature de votre patrimoine cloud, et la façon dont votre [conception d’abonnements](../subscriptions/index.md) reflète votre organisation. L’augmentation de la taille de votre patrimoine et la nécessité de gérer l’application des stratégies de manière centralisée justifient une extension de la portée d’application.

## <a name="baseline-best-practices"></a>Bonnes pratiques pour la base de référence

Pour un abonnement unique et des déploiements cloud simples, de nombreuses stratégies d’entreprise peuvent être appliquées à l’aide de fonctionnalités natives des ressources et des abonnements Azure. L’utilisation cohérente des modèles évoqués dans les [guides de décision](../index.md) du Framework d’adoption du cloud peut aider à établir un niveau de base de référence pour la conformité des stratégies, sans nécessiter d’investissements particuliers en application des stratégies. Voici quelques fonctionnalités :

- Des [modèles de déploiement](../resource-consistency/index.md) peuvent approvisionner des ressources avec une structure et une configuration normalisées.
- Des [normes de marquage et de nommage](../resource-tagging/index.md) peuvent vous aider à organiser vos opérations et à répondre aux exigences comptables et commerciales.
- Des restrictions liées à la gestion du trafic et au réseau peuvent être implémentées via le [Software Defined Networking](../software-defined-network/index.md).
- Un [contrôle d’accès en fonction du rôle](../identity/index.md) peut sécuriser et isoler vos ressources cloud.

Commencez la planification de l’application de votre stratégie cloud en examinant comment les modèles standard décrits dans ces guides peuvent vous aider à répondre aux besoins de votre organisation.

## <a name="policy-compliance-monitoring"></a>Surveillance de la conformité à la stratégie

Au-delà de la simple utilisation des mécanismes d’application des stratégies fournis par la plateforme Azure, une première étape consiste à vérifier que les applications et les services cloud sont conformes à la stratégie organisationnelle. Cela comprend l’implémentation de fonctionnalités de notification pour alerter les parties responsables qu’une ressource n’est plus conforme. La [journalisation et la génération de rapports](../logging-and-reporting/index.md) effectives de l’état de conformité des charges de travail cloud constituent un aspect essentiel d’une stratégie d’application de stratégie d’entreprise.

À mesure que vos ressources cloud augmentent, des outils supplémentaires tels qu’[Azure Security Center](https://docs.microsoft.com/azure/security-center) peuvent offrir une sécurité intégrée et une détection des menaces, et vous aider à appliquer une gestion centralisée de la stratégie ainsi qu’à générer des alertes pour vos ressources cloud et locales.

## <a name="policy-enforcement"></a>Application de stratégies

Dans Azure, vous pouvez appliquer des paramètres de configuration et des règles de création de ressources au niveau du groupe d’administration, de l’abonnement ou du groupe de ressources, afin de garantir l’alignement des stratégies.

[Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) est un service Azure pour la création, l’assignation et la gestion des stratégies. Ces stratégies appliquent différentes règles et effets sur vos ressources, qui restent donc conformes aux normes et aux contrats de niveau de service de l’entreprise. Azure Policy évalue vos ressources afin d’épingler toute non-conformité avec les stratégies assignée. Par exemple, vous pouvez limiter la taille de référence SKU des machines virtuelles dans votre environnement. Après avoir implémenté une stratégie correspondante, la conformité des ressources nouvelles et existantes est évaluée. Avec une stratégie appropriée, les ressources existantes peuvent être mises en conformité.

## <a name="cross-organization-policy"></a>Stratégie à l’échelle de l’organisation

À mesure que vos ressources cloud augmentent pour couvrir de nombreux abonnements nécessitant une application, vous devez vous concentrer sur une stratégie d’application à l’échelle du patrimoine cloud afin de garantir la cohérence des stratégies.

Votre [abonnement](../subscriptions/index.md) doit prendre en considération la stratégie par rapport à la structure de votre organisation. En plus de vous aider à prendre en charge une organisation complexe au sein de votre abonnement, des [groupes d’administration Azure](../../ready/azure-best-practices/organize-subscriptions.md) peuvent être utilisés pour assigner des règles Azure Policy à plusieurs abonnements.

## <a name="automated-enforcement"></a>Application automatisée

Si les modèles de déploiement normalisés sont efficaces à petite échelle, la solution [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) permet un approvisionnement et une orchestration de déploiement normalisés à grande échelle de solutions Azure. Les charges de travail de plusieurs abonnements peuvent être déployées avec des paramètres de stratégie cohérents pour toutes les ressources créées.

Pour des environnements informatiques intégrant des ressources cloud et locales, il se peut que vous deviez utiliser des systèmes de journalisation et de génération de rapports pour offrir des fonctionnalités de surveillance hybrides. Vos systèmes de surveillance opérationnelle tiers ou personnalisées peuvent offrir des fonctionnalités d’application de stratégie supplémentaires. Pour des patrimoines cloud plus grands ou plus complexes, vous devez réfléchir à la meilleure façon d’intégrer ces systèmes à vos ressources cloud.

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, l’application des stratégies ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
