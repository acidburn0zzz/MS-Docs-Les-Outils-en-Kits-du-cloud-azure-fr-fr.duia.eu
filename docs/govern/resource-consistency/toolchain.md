---
title: Outils de cohérence des ressources dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Outils de cohérence des ressources dans Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: e67d172b936c37aefb6764a304aaaf8f6788ffbe
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031244"
---
# <a name="resource-consistency-tools-in-azure"></a>Outils de cohérence des ressources dans Azure

La discipline [Cohérence des ressources](./index.md) est l'une des [cinq disciplines de la gouvernance cloud](../governance-disciplines.md). Elle se concentre sur les moyens à utiliser pour établir des stratégies en lien avec la gestion opérationnelle d’un environnement, d’une application ou d’une charge de travail. Parmi les cinq disciplines de la gouvernance cloud, la Cohérence des ressources comprend la supervision des performances des applications, des charges de travail et des ressources. Elle inclut également les tâches nécessaires pour répondre aux demandes de mise à l’échelle, corriger les violations de contrat de niveau de service de performances et prévenir ces violations de façon proactive via la correction automatisée.

La liste suivante énumère les outils Azure qui peuvent contribuer à faire mûrir les stratégies et les processus soutenant cette discipline de gouvernance.

| Outil | [Portail Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)  | [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) | [Azure Automation](https://docs.microsoft.com/azure/automation/automation-intro) | [Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) | [Sauvegarde Azure](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|---------|
| Déployer des ressources                             | OUI | OUI | OUI | OUI | Non  | Non | Non |
| Gestion des ressources                             | OUI | OUI | OUI | OUI | Non  | Non | Non |
| Déploiement des ressources à l'aide de modèles             | Non  | OUI | Non  | OUI | Non  | Non | Non |
| Déploiement d'un environnement orchestré          | Non  | Non  | OUI | Non  | Non  | Non | Non |
| Définition de groupes de ressources                       | OUI | OUI | OUI | Non  | Non  | Non | Non |
| Gestion de la charge de travail et des propriétaires de compte           | OUI | OUI | OUI | Non  | Non  | Non | Non |
| Gestion de l'accès conditionnel aux ressources       | OUI | OUI | OUI | Non  | Non  | Non | Non |
| Configuration des utilisateurs RBAC                         | OUI | Non  | Non  | Non  | OUI | Non | Non |
| Attribution de rôles et d'autorisations aux ressources | OUI | OUI | OUI | Non  | OUI | Non | Non |
| Définition des dépendances entre les ressources        | Non  | OUI | OUI | Non  | Non  | Non | Non |
| Application du contrôle d'accès                         | OUI | OUI | OUI | Non  | OUI | Non | Non |
| Évaluation de la disponibilité et de l'extensibilité          | Non  | Non  | Non  | OUI | Non  | Non | Non |
| Application d'étiquettes aux ressources                      | OUI | OUI | OUI | Non  | Non  | Non | Non |
| Affectation de règles Azure Policy                    | OUI | OUI | OUI | Non  | Non  | Non | Non |
| Application de la correction automatique                  | Non  | Non  | Non  | OUI | Non  | Non | Non |
| Gérer la facturation                               | OUI | Non  | Non  | Non  | Non  | Non | Non |
| Préparation des ressources pour la récupération d'urgence         | OUI | OUI | OUI | Non  | Non  | OUI | OUI |
|Récupération des données lors d'une panne ou d'une violation du contrat de niveau de service     | Non | Non  | Non  | Non  | Non  | OUI | OUI |
|Récupération des applications et des données lors d'une panne ou d'une violation du contrat de niveau de service     | Non | Non  | Non  | Non  | Non  | OUI | OUI |

Outre ces outils et fonctionnalités de cohérence des ressources, vous devez superviser les ressources que vous avez déployées afin de déceler les éventuels problèmes de performances et d'intégrité. [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) est la solution de supervision et de création de rapports par défaut d'Azure. Azure Monitor fournit des fonctionnalités de surveillance de vos ressources cloud. Cette liste présente la fonctionnalité qui répond aux exigences de surveillance les plus courantes.

| Outil | [Portail Azure](https://azure.microsoft.com/features/azure-portal) | [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) | [Log Analytics](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview) | [API REST Azure Monitor](https://docs.microsoft.com/rest/api/monitor) |
|----------------------------------------------------|--------------|----------------------|---------------|------------------------|
| Enregistrement des données de télémétrie des machines virtuelles                 | Non           | Non                   | OUI           | Non                     |
| Enregistrement des données de télémétrie du réseau virtuel              | Non           | Non                   | OUI           | Non                     |
| Enregistrement des données de télémétrie des services PaaS                   | Non           | Non                   | OUI           | Non                     |
| Enregistrement des données de télémétrie des applications                     | Non           | OUI                  | Non            | Non                     |
| Configuration des rapports et alertes                       | OUI          | Non                   | Non            | OUI                    |
| Planification de rapports réguliers ou d'analyses personnalisées        | Non           | Non                   | Non            | Non                     |
| Visualisation et analyse des données de journal et de performance     | OUI          | Non                   | Non            | Non                     |
| Intégration à une solution de supervision locale ou tierce     | Non           | Non                   | Non            | OUI                    |

Lors de la planification de votre déploiement, vous devrez penser à l'emplacement où seront stockées vos données de journalisation, et à la manière dont vous intègrerez les [services de création de rapports et de supervision](../../decision-guides/logging-and-reporting/index.md) basés sur le cloud à vos processus et outils existants.

> [!NOTE]
> Les organisations utilisent également des outils DevOps tiers pour superviser les charges de travail et les ressources. Pour plus d’informations, consultez [Intégrations d’outils DevOps](https://azure.microsoft.com/products/devops-tool-integrations).

## <a name="next-steps"></a>Étapes suivantes

Apprenez à créer, assigner et gérer des [définitions de stratégies](https://docs.microsoft.com/azure/governance/policy) dans Azure.
