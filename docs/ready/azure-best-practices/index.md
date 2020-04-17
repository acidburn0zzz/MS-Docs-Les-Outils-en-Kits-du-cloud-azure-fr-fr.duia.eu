---
title: Meilleures pratiques de préparation pour Azure
description: Découvrez des bonnes pratiques et d’autres conseils pour aider votre équipe à établir et préparer votre environnement Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 107764931a6188f6976c5cfb8af0f74082c21e2b
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80997799"
---
# <a name="best-practices-for-azure-readiness"></a>Meilleures pratiques de préparation pour Azure

La préparation au cloud nécessite de donner au personnel les compétences techniques nécessaires pour commencer un travail d’adoption du cloud et pour préparer votre environnement cible de migration pour les ressources et les charges de travail que vous déplacerez dans le cloud. Lisez ces bonnes pratiques et autres conseils pour aider votre équipe à préparer votre environnement Azure.

## <a name="azure-fundamentals"></a>Fondamentaux Azure

Organisez et déployez vos ressources dans l’environnement Azure.

- [Concepts fondamentaux Azure](../considerations/fundamental-concepts.md). Découvrez les principaux concepts et termes relatifs à Azure, et la manière dont ces concepts sont liés les uns aux autres.
- [Créez vos abonnements initiaux](./initial-subscriptions.md). Établissez un ensemble initial d’abonnements Azure pour commencer votre adoption du cloud.
- [Mettez à l’échelle votre environnement Azure avec plusieurs abonnements](../azure-best-practices/scale-subscriptions.md). Comprenez les raisons et les stratégies pour créer des abonnements supplémentaires afin de mettre à l’échelle votre environnement Azure.
- [Organiser vos ressources avec des groupes d’administration Azure](../azure-best-practices/organize-subscriptions.md). Découvrez comment les groupes d’administration Azure peuvent aider à gérer les ressources, les rôles, les stratégies et le déploiement parmi plusieurs abonnements.
- [Suivez les conventions de nommage et d’étiquetage recommandées](../azure-best-practices/naming-and-tagging.md). Passez en revue les recommandations détaillées relatives au nommage et la catégorisation de vos ressources. Celles-ci sont conçues pour prendre en charge les efforts d’adoption du cloud en entreprise.
- [Créer une cohérence de cloud hybride](../considerations/hybrid-consistency.md). Créez des solutions cloud hybrides qui offrent les avantages de l’innovation du cloud tout en conservant la plupart des aspects pratiques de la gestion locale.

## <a name="networking"></a>Mise en réseau

Préparez votre infrastructure réseau cloud pour prendre en charge vos charges de travail.

- [Décisions en matière de réseau](../considerations/networking-options.md). Choisissez les services, outils et architectures réseau qui prendront en charge les besoins de votre organisation en termes de charge de travail, de gouvernance et de connectivité.
- [Planification des réseaux virtuels](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Planifiez des réseaux virtuels en fonction de vos besoins d’isolation, de connectivité et d’emplacement.
- [Bonnes pratiques pour la sécurité réseau](https://docs.microsoft.com/azure/security/fundamentals/network-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les bonnes pratiques pour résoudre les problèmes courants liés à la sécurité réseau à l’aide des fonctionnalités Azure intégrées.
- [Réseaux de périmètre](./perimeter-networks.md). Établissez une connectivité sécurisée entre vos réseaux cloud et les réseaux de vos centres de données locaux ou physiques, ainsi qu’une connectivité à destination et en provenance d’Internet.
- [Topologie de réseau hub-and-spoke](./hub-spoke-network-topology.md). Gérez efficacement les exigences courantes en matière de communication ou de sécurité pour les charges de travail compliquées, et faites face aux potentielles limitations des abonnements Azure.

## <a name="identity-and-access-control"></a>Contrôle des accès et des identités

Concevez votre infrastructure de contrôle des accès et des identités afin d’améliorer la sécurité et l’efficacité de gestion de vos charges de travail.

- [Bonnes pratiques pour la sécurité du contrôle d’accès et de gestion des identités Azure](https://docs.microsoft.com/azure/security/fundamentals/identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les bonnes pratiques en matière de gestion des identités et du contrôle d’accès à l’aide de fonctionnalités Azure intégrées.
- [Bonnes pratiques en matière de contrôle d’accès en fonction du rôle](../considerations/roles.md). Profitez d’une gestion précise de l’accès basé sur des groupes pour les ressources organisées autour des rôles d’utilisateur.
- [Sécurisation de l’accès privilégié pour les déploiements hybrides et cloud dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Vérifiez que les comptes privilégiés et avec un accès administratif dans votre organisation sont sécurisés dans vos environnements cloud et local.

## <a name="storage"></a>Stockage

- [Conseils liés à Stockage Azure](../considerations/storage-options.md). Sélectionnez la solution de stockage Azure appropriée pour prendre en charge vos scénarios d’usage.
- [Guide de sécurité du Stockage Azure](https://docs.microsoft.com/azure/storage/blobs/security-recommendations?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les fonctionnalités de sécurité disponibles dans Stockage Azure.

## <a name="databases"></a>Bases de données

- [Choisir l’option SQL Server correcte dans Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Choisissez la solution PaaS ou IaaS la mieux adaptée à vos charges de travail SQL Server.
- [Bonnes pratiques pour la sécurité des bases de données](https://docs.microsoft.com/azure/security/azure-database-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les bonnes pratiques pour la sécurité des bases de données sur la plateforme Azure.
- [Choisissez le bon magasin de données](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview). Sélectionnez le magasin de données approprié pour répondre à vos besoins. Des centaines de choix d’implémentation sont disponibles parmi les bases de données SQL et NoSQL. Les magasins de données sont souvent classés selon la façon dont ils structurent les données et les types d’opérations qu’ils prennent en charge. Cet article décrit plusieurs modèles de stockage courants.

## <a name="cost-management"></a>la gestion des coûts ;

- [Suivi des coûts parmi les projets, les environnements et les divisions](./track-costs.md). Découvrez les bonnes pratiques pour la création de mécanismes de suivi des coûts appropriés.
- [Guide pratique pour optimiser votre investissement dans le cloud avec Azure Cost Management](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Implémentez une stratégie de gestion des coûts et découvrez les outils disponibles pour répondre aux défis liés aux coûts.
- [Créer et gérer des budgets](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment créer et gérer des budgets avec Azure Cost Management.
- [Exporter des données de coûts](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-export-acm-data?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment exporter des données de coût à l’aide d’Azure Cost Management.
- [Optimiser les coûts selon les recommandations](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment identifier les ressources sous-utilisées et réduire les coûts à l’aide d’Azure Cost Management et d’Azure Advisor.
- [Utiliser les alertes de coût pour superviser l’utilisation et les dépenses](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-alerts-monitor-usage-spending?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment utiliser les alertes de Gestion des coûts pour superviser votre utilisation d’Azure et vos dépenses.
