---
title: Guide de décision concernant les abonnements
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment utiliser un abonnement de plateforme cloud comme un service principal lors des migrations Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 06/07/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 0997698660f19ff47a2eebe6dcdccb122e7f20b5
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70906095"
---
# <a name="subscription-decision-guide"></a>Guide de décision concernant les abonnements

Une conception efficace des abonnements aide les organisations à établir une structure pour organiser les ressources dans Azure pendant une adoption du cloud.

Chaque ressource dans Azure, telle qu’une machine virtuelle ou une base de données, est associée à un abonnement. L’adoption d’Azure commence par la création d’un abonnement Azure, son association à un compte et le déploiement de ressources sur l’abonnement. Pour obtenir une vue d’ensemble de ces concepts, consultez [Concepts fondamentaux Azure](../../ready/considerations/fundamental-concepts.md).

Avec la croissance de votre patrimoine numérique Azure, vous devrez probablement créer des abonnements supplémentaires pour répondre à vos besoins. Azure vous permet de définir une hiérarchie de groupes d’administration pour organiser vos abonnements et appliquer facilement la bonne stratégie aux bonnes ressources. Pour plus d’informations, consultez [Mise à l’échelle avec plusieurs abonnements Azure](../../ready/considerations/scaling-subscriptions.md).

Voici quelques exemples de base de l’utilisation de groupes d’administration pour séparer différentes charges de travail :

- **Production et hors production :** certaines entreprises créent des groupes d’administration pour séparer leurs abonnements Production de leurs abonnements Hors production. Les groupes d’administration permettent à ces clients de gérer plus facilement les rôles et les stratégies. Par exemple, un abonnement Hors production peut permettre aux développeurs de bénéficier d’un accès **Contributeur**. Toutefois, dans un abonnement Production, ils bénéficient seulement d’un accès **Lecteur**.
- **Services internes et services externes :** tout comme pour les charges de travail Production et Hors production, les entreprises ont souvent des besoins, des stratégies et des rôles différents pour les services internes et les services externes (destinés aux clients).

Ce guide de décision présente différentes approches pour organiser votre hiérarchie de groupes d’administration.

## <a name="subscription-design-patterns"></a>Modèles de conception des abonnements

Chaque organisation étant différente, les groupes d’administration Azure sont conçus pour être flexibles. La modélisation de votre patrimoine cloud afin de refléter la hiérarchie de votre organisation vous permet de définir et d’appliquer des stratégies à des niveaux supérieurs de la hiérarchie. Elle s’appuie sur l’héritage pour garantir que ces stratégies sont appliquées automatiquement aux groupes d’administration plus bas dans la hiérarchie. Bien que les abonnements puissent être déplacés entre différents groupes d’administration, il est utile de concevoir une hiérarchie de groupes d’administration initiale qui reflète les besoins anticipés de votre organisation.

Avant de finaliser votre conception des abonnements, réfléchissez aussi à la façon dont la [cohérence des ressources](../resource-consistency/index.md) peut influencer votre choix.

> ![REMARQUE] Les Contrats Entreprise Azure vous permettent de définir une autre hiérarchie organisationnelle à des fins de facturation. Cette hiérarchie est distincte de votre hiérarchie de groupes d’administration, qui met l’accent sur la remise d’un modèle d’héritage pour appliquer facilement des stratégies et un contrôle d’accès appropriés à vos ressources.

Les modèles d’abonnements suivants reflètent une augmentation initiale de la sophistication de conception des abonnements, suivie de plusieurs hiérarchies plus avancées susceptibles de s’aligner correctement avec votre organisation :

### <a name="single-subscription"></a>Abonnement unique

Un seul abonnement par compte peut s’avérer suffisant pour les organisations qui doivent déployer un petit nombre de ressources hébergées dans le cloud. C’est le premier modèle d’abonnement que vous implémenterez au début de votre adoption du cloud, car il vous permet d’effectuer des déploiements à petite échelle à des fins d’expérimentation ou de preuve de concept, afin d’explorer les fonctionnalités du cloud.

### <a name="production-and-nonproduction-pattern"></a>Modèle de production et de non-production

Une fois que vous êtes prêt à déployer une charge de travail dans un environnement de production, vous devez ajouter un abonnement supplémentaire. Cela vous permet de conserver vos données de production et autres ressources hors de vos environnements de développement/test. Vous pouvez aussi appliquer facilement deux différents ensembles de stratégies sur les ressources dans les deux abonnements.

![Modèle d’abonnement de production et de non-production](../../_images/ready/basic-subscription-model.png)

### <a name="workload-separation-pattern"></a>Modèle de séparation des charges de travail

À mesure qu’une organisation ajoute de nouvelles charges de travail au cloud, un changement de propriété des abonnements ou une simple séparation des responsabilités peut entraîner la présence de plusieurs abonnements dans les groupes d’administration de production et de non-production. Bien que cette approche fournisse une séparation de base des charges de travail, elle ne tire pas vraiment parti du modèle d’héritage pour appliquer automatiquement des stratégies sur un sous-ensemble de vos abonnements.

![Modèle de séparation des charges de travail](../../_images/ready/management-group-hierarchy.png)

### <a name="application-category-pattern"></a>Modèle de catégorie d’application

À mesure que l’encombrement cloud d’une organisation augmente, des abonnements supplémentaires sont généralement créés pour prendre en charge les applications présentant des différences fondamentales en matière de criticité métier, d’exigences de conformité, de contrôles d’accès ou de besoins en protection des données. Reposant sur le modèle d’abonnement « production et non-production », les abonnements prenant en charge ces catégories d’applications sont classés sous le groupe d’administration de production ou de non-production selon le cas. Ces abonnements sont généralement détenus et administrés par le personnel chargé des opérations informatiques à un niveau centralisé.

![Modèle de catégorie d’application](../../_images/infra-subscriptions/application.png)

Chaque organisation classe ses applications différemment, souvent en séparant les abonnements en fonction des applications ou des services, ou en suivant des archétypes d’application. Cette classification est souvent conçue pour prendre en charge les charges de travail qui sont susceptibles de consommer la plupart des ressources d’un abonnement, ou des charges de travail critiques distinctes pour garantir qu’elles ne sont pas en concurrence avec d’autres charges de travail dans les limites de l’abonnement. Voici quelques charges de travail qui peuvent justifier l’utilisation d’un abonnement distinct dans ce modèle :

- Les charges de travail critiques
- Les applications comportant des données protégées
- Les applications expérimentales
- Les applications soumises à des réglementations (HIPAA ou FedRAMP)
- Les charges de travail par lots
- Les charges de travail de Big data comme Hadoop
- Les charges de travail conteneurisées utilisant des orchestrateurs de déploiement comme Kubernetes
- Les charges de travail d’analytique

### <a name="functional-pattern"></a>Modèle fonctionnel

Le modèle fonctionnel organise les abonnements et les comptes selon des lignes fonctionnelles, telles que la finance, les ventes ou le support informatique, à l’aide d’une hiérarchie de groupes d’administration.

### <a name="business-unit-pattern"></a>Modèle d’unité commerciale

Le modèle d’unité commerciale regroupe les abonnements et les comptes en fonction de la catégorie Pertes et profits, de l’unité commerciale, de la division, du centre de profit ou d’une structure métier similaire, à l’aide d’une hiérarchie de groupes d’administration.

### <a name="geographic-pattern"></a>Modèle géographique

Pour les organisations internationales, le modèle géographique regroupe les abonnements et les comptes en fonction des zones géographiques, à l’aide d’une hiérarchie de groupes d’administration.

## <a name="mixed-patterns"></a>Modèles mixtes

Les hiérarchies de groupes d’administration peuvent avoir jusqu’à six niveaux de profondeur. Cela vous offre la flexibilité nécessaire pour créer une hiérarchie qui combine plusieurs de ces modèles afin de répondre aux besoins de votre organisation. Par exemple, le diagramme ci-dessous montre une hiérarchie organisationnelle qui combine un modèle d’unité commerciale avec un modèle géographique.

![Modèle d’abonnement mixte](../../_images/infra-subscriptions/mixed.png)

## <a name="related-resources"></a>Ressources associées

- [Gestion de l’accès aux ressources dans Azure](../../governance/resource-consistency/azure-resource-access.md)
- [Plusieurs couches de gouvernance dans les grandes entreprises](/azure/architecture/cloud-adoption/governance/journeys/large-enterprise/multiple-layers-of-governance)
- [Zones géographiques multiples](/azure/architecture/cloud-adoption/migrate/expanded-scope/multiple-regions)

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, la conception des abonnements ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
