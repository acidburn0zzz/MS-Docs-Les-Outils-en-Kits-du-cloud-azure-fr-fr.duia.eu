---
title: Outils de cohérence des ressources dans Azure
description: Découvrez comment les outils natifs Azure peuvent contribuer à affiner les stratégies et les processus qui vont dans le sens de la discipline Cohérence des ressources.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a64cbd53cdd4c524b370681ebedf1f8282ac2a93
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83217946"
---
# <a name="resource-consistency-tools-in-azure"></a>Outils de cohérence des ressources dans Azure

La [Cohérence des ressources](./index.md) est l'une des [Cinq disciplines de la gouvernance du cloud](../governance-disciplines.md). Elle se concentre sur les moyens à utiliser pour établir des stratégies en lien avec la gestion opérationnelle d’un environnement, d’une application ou d’une charge de travail. Parmi les cinq disciplines de la gouvernance cloud, la Cohérence des ressources comprend la supervision des performances des applications, des charges de travail et des ressources. Elle inclut également les tâches nécessaires pour répondre aux demandes de mise à l’échelle, corriger les violations de contrat de niveau de service de performances et prévenir ces violations de façon proactive via la correction automatisée.

La liste suivante énumère les outils Azure qui peuvent contribuer à faire mûrir les stratégies et les processus soutenant cette discipline.

| Outil | [Azure portal](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/management/overview)  | [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) | [Azure Automation](https://docs.microsoft.com/azure/automation/automation-intro) | [Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) | [Azure Backup](https://docs.microsoft.com/azure/backup/backup-overview) | [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|---------|
| Déployer des ressources                             | Oui | Oui | Oui | Oui | Non  | Non | Non |
| Gestion des ressources                             | Oui | Oui | Oui | Oui | Non  | Non | Non |
| Déploiement des ressources à l'aide de modèles             | Non  | Oui | Non  | Oui | Non  | Non | Non |
| Déploiement d'un environnement orchestré          | Non  | Non  | Oui | Non  | Non  | Non | Non |
| Définition de groupes de ressources                       | Oui | Oui | Oui | Non  | Non  | Non | Non |
| Gestion de la charge de travail et des propriétaires de compte           | Oui | Oui | Oui | Non  | Non  | Non | Non |
| Gestion de l'accès conditionnel aux ressources       | Oui | Oui | Oui | Non  | Non  | Non | Non |
| Configuration des utilisateurs RBAC                         | Oui | Non  | Non  | Non  | Oui | Non | Non |
| Attribution de rôles et d'autorisations aux ressources | Oui | Oui | Oui | Non  | Oui | Non | Non |
| Définition des dépendances entre les ressources        | Non  | Oui | Oui | Non  | Non  | Non | Non |
| Application du contrôle d'accès                         | Oui | Oui | Oui | Non  | Oui | Non | Non |
| Évaluation de la disponibilité et de l'extensibilité          | Non  | Non  | Non  | Oui | Non  | Non | Non |
| Application d'étiquettes aux ressources                      | Oui | Oui | Oui | Non  | Non  | Non | Non |
| Affectation de règles Azure Policy                    | Oui | Oui | Oui | Non  | Non  | Non | Non |
| Application de la correction automatique                  | Non  | Non  | Non  | Oui | Non  | Non | Non |
| Gérer la facturation                               | Oui | Non  | Non  | Non  | Non  | Non | Non |
| Préparation des ressources pour la récupération d'urgence         | Oui | Oui | Oui | Non  | Non  | Oui | Oui |
| Récupération des données lors d'une panne ou d'une violation du contrat de niveau de service     | Non | Non  | Non  | Non  | Non  | Oui | Oui |
| Récupération des applications et des données lors d'une panne ou d'une violation du contrat de niveau de service     | Non | Non  | Non  | Non  | Non  | Oui | Oui |

Outre ces outils et fonctionnalités de cohérence des ressources, vous devez superviser les ressources que vous avez déployées afin de déceler les éventuels problèmes de performances et d'intégrité. [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) est la solution de supervision et de création de rapports par défaut d'Azure. Azure Monitor fournit des fonctionnalités de surveillance de vos ressources cloud. Cette liste présente la fonctionnalité qui répond aux exigences de surveillance les plus courantes.

| Outil | [Azure portal](https://azure.microsoft.com/features/azure-portal) | [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) | [Log Analytics](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview) | [API REST Azure Monitor](https://docs.microsoft.com/rest/api/monitor) |
|----------------------------------------------------|--------------|----------------------|---------------|------------------------|
| Enregistrement des données de télémétrie des machines virtuelles                 | Non           | Non                   | Oui           | Non                     |
| Enregistrement des données de télémétrie du réseau virtuel              | Non           | Non                   | Oui           | Non                     |
| Enregistrement des données de télémétrie des services PaaS                   | Non           | Non                   | Oui           | Non                     |
| Enregistrement des données de télémétrie des applications                     | Non           | Oui                  | Non            | Non                     |
| Configuration des rapports et alertes                       | Oui          | Non                   | Non            | Oui                    |
| Planification de rapports réguliers ou d'analyses personnalisées        | Non           | Non                   | Non            | Non                     |
| Visualisation et analyse des données de journal et de performance     | Oui          | Non                   | Non            | Non                     |
| Intégration à une solution de supervision locale ou tierce     | Non           | Non                   | Non            | Oui                    |

Lors de la planification de votre déploiement, vous devrez penser à l'emplacement où seront stockées vos données de journalisation, et à la manière dont vous intègrerez les [services de création de rapports et de supervision](../../decision-guides/logging-and-reporting/index.md) basés sur le cloud à vos processus et outils existants.

> [!NOTE]
> Les organisations utilisent également des outils DevOps tiers pour superviser les charges de travail et les ressources. Pour plus d’informations, consultez [Intégrations d’outils DevOps](https://azure.microsoft.com/products/devops-tool-integrations).

## <a name="next-steps"></a>Étapes suivantes

Apprenez à créer, assigner et gérer des [définitions de stratégies](https://docs.microsoft.com/azure/governance/policy) dans Azure.
