---
title: Guide de décision concernant les abonnements
description: Comprenez les stratégies de conception des abonnements et la hiérarchie des groupes d’administration pour organiser vos ressources Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: f7675852a6d9b59e0d06873fee028b701dc729e3
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83215049"
---
# <a name="subscription-decision-guide"></a>Guide de décision concernant les abonnements

Une conception efficace des abonnements aide les organisations à établir une structure pour organiser et gérer les ressources dans Azure pendant une adoption du cloud. Ce guide vous aide à décider quand créer des abonnements supplémentaires et à développer votre hiérarchie de groupes d’administration pour prendre en charge vos priorités métier.

## <a name="prerequisites"></a>Prérequis

L’adoption d’Azure commence par la création d’un abonnement Azure, son association à un compte et le déploiement de ressources comme des machines virtuelles et des bases de données sur l’abonnement. Pour obtenir une vue d’ensemble de ces concepts, consultez [Concepts fondamentaux Azure](../../ready/considerations/fundamental-concepts.md).

- [Créez vos abonnements initiaux.](../../ready/azure-best-practices/initial-subscriptions.md)
- [Créez des abonnements supplémentaires](../../ready/azure-best-practices/scale-subscriptions.md) pour mettre à l’échelle votre environnement Azure.
- [Organisez et gérez vos abonnements](../../ready/azure-best-practices/organize-subscriptions.md) en utilisant des groupes d’administration Azure.

## <a name="model-your-organization"></a>Modélisation de l’organisation

Chaque organisation étant différente, les groupes d’administration Azure sont conçus pour être flexibles. La modélisation de votre patrimoine cloud afin de refléter la hiérarchie de votre organisation vous permet de définir et d’appliquer des stratégies à des niveaux supérieurs de la hiérarchie. Elle s’appuie sur l’héritage pour garantir que ces stratégies sont appliquées automatiquement aux groupes d’administration plus bas dans la hiérarchie. Bien que les abonnements puissent être déplacés entre différents groupes d’administration, il est utile de concevoir une hiérarchie de groupes d’administration initiale qui reflète les besoins anticipés de votre organisation.

Avant de finaliser votre conception des abonnements, réfléchissez aussi à la façon dont la [cohérence des ressources](../resource-consistency/index.md) peut influencer votre choix.

> [!NOTE]
> Les Contrats Entreprise Azure vous permettent de définir une autre hiérarchie organisationnelle à des fins de facturation. Cette hiérarchie est distincte de votre hiérarchie de groupes d’administration, qui met l’accent sur la remise d’un modèle d’héritage pour appliquer facilement des stratégies et un contrôle d’accès appropriés à vos ressources.

## <a name="subscription-design-strategies"></a>Stratégies de conception des abonnements

Tenez compte des stratégies de conception d’abonnement suivantes pour répondre à vos priorités métier.

### <a name="workload-separation-strategy"></a>Stratégie de séparation des charges de travail

À mesure qu’une organisation ajoute de nouvelles charges de travail au cloud, un changement de propriété des abonnements ou une simple séparation des responsabilités peut entraîner la présence de plusieurs abonnements dans les groupes d’administration de production et de non-production. Bien que cette approche fournisse une séparation de base des charges de travail, elle ne tire pas vraiment parti du modèle d’héritage pour appliquer automatiquement des stratégies sur un sous-ensemble de vos abonnements.

![Stratégie de séparation des charges de travail](../../_images/ready/management-group-hierarchy-v2.png)

### <a name="application-category-strategy"></a>Stratégie de catégorie d’application

À mesure que l’encombrement cloud d’une organisation augmente, des abonnements supplémentaires sont généralement créés pour prendre en charge les applications présentant des différences fondamentales en matière de criticité métier, d’exigences de conformité, de contrôles d’accès ou de besoins en protection des données. En s’appuyant sur les abonnements « production » et « non-production », les abonnements prenant en charge ces catégories d’application sont classés selon les cas sous le groupe d’administration de production ou de non-production. Ces abonnements sont généralement détenus et administrés par le personnel chargé de l’exploitation informatique centrale.

![Stratégie de catégorie d’application](../../_images\decision-guides\decision-guide-subscriptions-hierarchy.png)

Chaque organisation classe ses applications différemment, souvent en séparant les abonnements en fonction des applications ou des services, ou en suivant des archétypes d’application. Cette classification est souvent conçue pour prendre en charge les charges de travail qui sont susceptibles de consommer la plupart des ressources d’un abonnement, ou des charges de travail critiques distinctes pour garantir qu’elles ne sont pas en concurrence avec d’autres charges de travail dans les limites de l’abonnement. Voici quelques charges de travail qui peuvent justifier l’utilisation d’un abonnement distinct :

- Les charges de travail critiques
- Les applications s’inscrivant dans le _coût des marchandises vendues_ (COGS) de votre entreprise. Exemple : chaque instance du widget de la société X contient un module Azure IoT qui envoie des données de télémétrie. Ceci peut nécessiter un abonnement dédié à des fins de comptabilité/gouvernance dans le cadre du COGS.
- Les applications soumises à des réglementations (HIPAA ou FedRAMP, par exemple).

### <a name="functional-strategy"></a>Stratégie fonctionnelle

La stratégie fonctionnelle organise les abonnements et les comptes selon des « lignes fonctionnelles », comme la comptabilité, les ventes ou le support informatique, en utilisant une hiérarchie de groupes d’administration.

### <a name="business-unit-strategy"></a>Stratégie d’unité opérationnelle

Le modèle d’unité opérationnelle regroupe les abonnements et les comptes en fonction de la catégorie Pertes et profits, de l’unité opérationnelle, de la division, du centre de profit ou d’une structure métier similaire, en utilisant une hiérarchie de groupes d’administration.

### <a name="geographic-strategy"></a>Stratégie géographique

Pour les organisations internationales, le modèle géographique regroupe les abonnements et les comptes en fonction des zones géographiques, en utilisant une hiérarchie de groupes d’administration.

## <a name="mix-subscription-strategies"></a>Combinaison des stratégies d’abonnement

Les hiérarchies de groupes d’administration peuvent avoir jusqu’à six niveaux de profondeur. Ceci vous offre la flexibilité nécessaire pour créer une hiérarchie qui combine plusieurs de ces stratégies afin de répondre aux besoins de votre organisation. Par exemple, le diagramme ci-dessous montre une hiérarchie organisationnelle qui combine une stratégie d’unité organisationnelle avec une stratégie géographique.

![Stratégie d’abonnement mixte](../../_images\decision-guides\decision-guide-subscriptions-hierarchy-mixed.png)

## <a name="related-resources"></a>Ressources associées

- [Gestion de l’accès aux ressources dans Azure](../../govern/resource-consistency/resource-access-management.md)
- [Plusieurs couches de gouvernance dans les grandes entreprises](../../govern/guides/complex/multiple-layers-of-governance.md)
- [Zones géographiques multiples](../../migrate/azure-best-practices/multiple-regions.md)

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, la conception des abonnements ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour découvrir des stratégies utilisées pour décider de la conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
