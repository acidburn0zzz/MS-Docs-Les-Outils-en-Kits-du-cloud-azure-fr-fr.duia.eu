---
title: Bonnes pratiques de préparation pour Azure
description: Présentation des bonnes pratiques de préparation pour Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 4410c9628cbdf070d2862ba09812e4b968911419
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76799877"
---
# <a name="best-practices-for-azure-readiness"></a>Meilleures pratiques de préparation pour Azure

Une grande partie de la préparation à l’adoption du cloud consiste à fournir au personnel les compétences techniques nécessaires pour commencer un effort d’adoption du cloud et à préparer votre environnement cible de migration pour les ressources et les charges de travail que vous déplacerez vers le cloud. Les rubriques suivantes décrivent les bonnes pratiques et fournissent des conseils supplémentaires pour aider votre équipe à établir et à préparer votre environnement Azure.

## <a name="azure-fundamentals"></a>Fondamentaux Azure

Utilisez les indications suivantes lors de l’organisation et du déploiement de vos ressources dans l’environnement Azure :

- [Concepts fondamentaux Azure](../considerations/fundamental-concepts.md). Découvrez les concepts fondamentaux et les termes utilisés dans Azure. Découvrez également les relations entre ces concepts.
- [Conventions de nommage et de catégorisation recommandées](../azure-best-practices/naming-and-tagging.md). Passez en revue les recommandations détaillées relatives au nommage et la catégorisation de vos ressources. Celles-ci sont conçues pour prendre en charge les efforts d’adoption du cloud en entreprise.
- [Mise à l’échelle avec plusieurs abonnements Azure](../azure-best-practices/scaling-subscriptions.md). Apprenez-en davantage sur les stratégies de mise à l’échelle avec plusieurs abonnements Azure.
- [Organiser vos ressources avec des groupes d’administration Azure](https://docs.microsoft.com/azure/governance/management-groups/?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment les groupes d’administration Azure peuvent aider à gérer les ressources, les rôles, les stratégies et le déploiement parmi plusieurs abonnements.
- [Créer une cohérence de cloud hybride](../considerations/hybrid-consistency.md). Créez des solutions cloud hybrides qui offrent les avantages de l’innovation du cloud tout en conservant la plupart des aspects pratiques de la gestion locale.

## <a name="networking"></a>Mise en réseau

Utilisez les instructions suivantes pour préparer votre infrastructure réseau cloud à prendre en charge vos charges de travail :

- [Décisions en matière de réseau](../considerations/networking-options.md). Choisissez les services, outils et architectures réseau qui prendront en charge les besoins de votre organisation en termes de charge de travail, de gouvernance et de connectivité.
- [Planification des réseaux virtuels](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment planifier des réseaux virtuels en fonction de vos besoins en isolation, connectivité et emplacements.
- [Bonnes pratiques pour la sécurité réseau](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les bonnes pratiques pour résoudre les problèmes courants liés à la sécurité réseau à l’aide des fonctionnalités Azure intégrées.
- [Réseaux de périmètre](./perimeter-networks.md). Également appelés zones démilitarisées (DMZ), les réseaux de périmètre permettent d’établir une connectivité sécurisée entre vos réseaux cloud et les réseaux de vos centres de données locaux ou physiques, ainsi qu’une connectivité à destination et en provenance d’Internet.
- [Topologie de réseau hub-and-spoke](./hub-spoke-network-topology.md). Hub-and-spoke est un modèle de réseau visant à gérer efficacement les besoins de communication ou de sécurité courants pour les charges de travail complexes, tout en répondant également aux limitations potentielles des abonnements Azure.

## <a name="identity-and-access-control"></a>Contrôle des accès et des identités

Utilisez les instructions suivantes quand vous concevez votre infrastructure de contrôle des accès et des identités afin d’améliorer la sécurité et l’efficacité de gestion de vos charges de travail :

- [Bonnes pratiques pour la sécurité du contrôle d’accès et de gestion des identités Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les bonnes pratiques en matière de gestion des identités et du contrôle d’accès à l’aide de fonctionnalités Azure intégrées.
- [Bonnes pratiques en matière de contrôle d’accès en fonction du rôle](../considerations/roles.md). Le contrôle d’accès en fonction du rôle (RBAC) Azure offre une gestion précise de l’accès aux ressources basée sur des groupes et organisée autour des rôles d’utilisateur.
- [Sécurisation de l’accès privilégié pour les déploiements hybrides et cloud dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Utilisez Azure Active Directory pour vous assurer que les comptes d’administration et d’accès administratif de votre organisation sont sécurisés dans vos environnements cloud et locaux.

## <a name="storage"></a>Stockage

- [Conseils liés à Stockage Azure](../considerations/storage-options.md). Sélectionnez la solution de stockage Azure appropriée pour prendre en charge vos scénarios d’usage.
- [Guide de sécurité du Stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les fonctionnalités de sécurité disponibles dans Stockage Azure.

## <a name="databases"></a>Bases de données

- [Choisir l’option SQL Server correcte dans Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Choisissez la solution PaaS ou IaaS la mieux adaptée à vos charges de travail SQL Server.
- [Bonnes pratiques pour la sécurité des bases de données](https://docs.microsoft.com/azure/security/azure-database-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les bonnes pratiques pour la sécurité des bases de données sur la plateforme Azure.
- [Choisissez le bon magasin de données](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview). La sélection du magasin de données correspondant à vos besoins est une décision de conception primordiale. Il existe des centaines d’implémentations possibles entre les bases de données SQL et NoSQL. Les magasins de données sont souvent classés selon la façon dont ils structurent les données et les types d’opérations qu’ils prennent en charge. Cet article décrit certains des modèles de stockage les plus courants.

## <a name="cost-management"></a>la gestion des coûts ;

- [Suivi des coûts parmi les projets, les environnements et les divisions](./track-costs.md). Découvrez les bonnes pratiques pour la création de mécanismes de suivi des coûts appropriés.
- [Guide pratique pour optimiser votre investissement dans le cloud avec Azure Cost Management](https://docs.microsoft.com/azure/cost-management/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Implémentez une stratégie de gestion des coûts et découvrez les outils disponibles pour répondre aux défis liés aux coûts.
- [Créer et gérer des budgets](https://docs.microsoft.com/azure/cost-management/tutorial-acm-create-budgets?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment créer et gérer des budgets avec Azure Cost Management.
- [Exporter des données de coûts](https://docs.microsoft.com/azure/cost-management/tutorial-export-acm-data?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment créer et gérer des données exportées dans Azure Cost Management.
- [Optimiser les coûts selon les recommandations](https://docs.microsoft.com/azure/cost-management/tutorial-acm-opt-recommendations?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment identifier les ressources sous-utilisées et prendre des mesures pour réduire les coûts à l’aide d’Azure Cost Management et d’Azure Advisor.
- [Utiliser les alertes de coût pour superviser l’utilisation et les dépenses](https://docs.microsoft.com/azure/cost-management/cost-mgt-alerts-monitor-usage-spending?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment utiliser les alertes de Gestion des coûts pour superviser votre utilisation d’Azure et vos dépenses.
