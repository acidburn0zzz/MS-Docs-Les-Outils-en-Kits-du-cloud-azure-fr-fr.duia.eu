---
title: Guide de gouvernance pour les entreprises standard
description: Suivez une entreprise standard fictive à différents stades de maturité de gouvernance à mesure qu’elle définit un produit minimum viable (MVP) sur la base de bonnes pratiques.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 481a617d3a09ae1f81fe313dd557314aed8f4f29
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706843"
---
# <a name="standard-enterprise-governance-guide"></a>Guide de gouvernance pour les entreprises standard

## <a name="overview-of-best-practices"></a>Vue d’ensemble des bonnes pratiques

Ce guide de gouvernance suit les expériences d’une entreprise fictive à différents stades de maturité. Il est basé sur les expériences de clients réels. Les bonnes pratiques se fondent sur les contraintes et les besoins de l’entreprise fictive.

Comme point de départ rapide, cette présentation définit un produit minimum viable (MVP) pour la gouvernance, basé sur les meilleures pratiques. Elle fournit également des liens vers des améliorations de gouvernance, qui ajoutent des bonnes pratiques à mesure que de nouveaux risques métier ou techniques émergent.

> [!WARNING]
> Ce MVP est un point de départ de base, qui se fonde sur un ensemble de postulats. Même cet ensemble minimal de meilleures pratiques se fonde sur des stratégies d’entreprise, qui sont axées sur des risques métier et des tolérances aux risques uniques. Pour déterminer si ces postulats s’appliquent à vous, lisez la [plus longue description](./narrative.md) qui suit cet article.

### <a name="governance-best-practices"></a>Bonnes pratiques de gouvernance

Ces bonnes pratiques servent de base sur laquelle une organisation peut s’appuyer pour ajouter de manière cohérente et rapide des garde-fous en matière de gouvernance dans vos abonnements.

### <a name="resource-organization"></a>Organisation des ressources

Le schéma suivant montre la hiérarchie MVP de gouvernance pour organiser les ressources.

![Schéma d’organisation des ressources](../../../_images/govern/resource-organization.png)

Chaque application doit être déployée dans la zone appropriée du groupe d’administration, de l’abonnement et de la hiérarchie des groupes de ressources. Lors de la planification du déploiement, l’équipe de gouvernance cloud crée les nœuds nécessaires dans la hiérarchie pour donner aux équipes d’adoption du cloud les moyens d’agir.

1. Un groupe d’administration pour chaque type d’environnement (par exemple, production, développement et test).
2. Deux abonnements, un pour les charges de travail de production et un autre pour les charges de travail de non-production.
3. Une [nomenclature cohérente](../../../ready/azure-best-practices/naming-and-tagging.md) doit être appliquée à chaque niveau de cette hiérarchie de regroupement.
4. Les groupes de ressources doivent être déployés de manière à prendre en compte le cycle de vie de leur contenu : tous les contenus développés ensemble sont gérés ensemble et mis hors service ensemble. Pour plus d’informations sur les bonnes pratiques relatives aux groupes de ressources, consultez [cette page](../../../decision-guides/resource-consistency/index.md).
5. Le [choix de la région](../../../decision-guides/regions/index.md) est extrêmement important, notamment pour la mise en place du réseau, de la supervision et de l’audit pour le basculement/la restauration automatique. Il convient également de vérifier que les [références SKU nécessaires](https://azure.microsoft.com/global-infrastructure/services) sont disponibles dans les régions privilégiées.

Voici un exemple de modèle utilisé :

![Exemple d’organisation des ressources pour une entreprise de taille intermédiaire](../../../_images/govern/mid-market-resource-organization.png)

Ces modèles laissent de l’espace pour la croissance sans compliquer la hiérarchie inutilement.

[!INCLUDE [governance-of-resources](../../../../includes/caf-governance-of-resources.md)]

## <a name="iterative-governance-improvements"></a>Améliorations itératives de la gouvernance

Une fois que ce MVP a été déployé, des couches supplémentaires de gouvernance peuvent être rapidement intégrées à l’environnement. Voici quelques méthodes permettant d’améliorer le MVP afin de répondre aux besoins spécifiques de l’entreprise :

- [Base de référence de sécurité pour les données protégées](./security-baseline-improvement.md)
- [Configurations des ressources pour les applications critiques](./resource-consistency-improvement.md)
- [Contrôles pour la gestion des coûts](./cost-management-improvement.md)
- [Contrôles pour l’évolution multicloud](./multicloud-improvement.md)

<!-- markdownlint-disable MD026 -->

## <a name="what-does-this-guidance-provide"></a>Que fournit ce guide ?

Dans le MVP, les pratiques et les outils venant de la discipline [Accélération du déploiement](../../deployment-acceleration/index.md) ont été conçus pour appliquer rapidement la stratégie d’entreprise. Plus précisément, le MVP utilise Azure Blueprints, Azure Policy et les groupes d’administration Azure pour appliquer quelques stratégies d’entreprise basiques, comme le définit le scénario pour cette entreprise fictive. Ces stratégies d’entreprise sont appliquées à l’aide de modèles Resource Manager et de stratégies Azure afin d’établir une petite base de référence pour les identités et la sécurité.

![Exemple de MVP de gouvernance incrémentielle](../../../_images/govern/governance-mvp.png)

## <a name="incremental-improvement-of-governance-practices"></a>Amélioration incrémentielle des pratiques de gouvernance

Au fil du temps, ce MVP de gouvernance servira à améliorer les pratiques de gouvernance. À mesure que le processus d’adoption avance, les risques métier augmentent. Différentes disciplines au sein du modèle de gouvernance du Framework d’adoption du cloud changeront pour gérer ces risques. D’autres articles de cette série traitent de l’amélioration incrémentielle de la stratégie d’entreprise et de son impact sur l’entreprise fictive. Ces améliorations se produisent dans trois disciplines :

- La gestion des coûts, à mesure que l’adoption avance.
- La base de référence de la sécurité, à mesure que les données protégées sont déployées.
- La cohérence des ressources, à mesure que les opérations informatiques commencent à gérer les charges de travail critiques.

![Exemple de MVP de gouvernance incrémentielle](../../../_images/govern/governance-improvement.png)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous connaissez le MVP de gouvernance et que vous avez une idée des améliorations de gouvernance à suivre, lisez le scénario correspondant pour en savoir plus.

> [!div class="nextstepaction"]
> [Lire le scénario correspondant](./narrative.md)
