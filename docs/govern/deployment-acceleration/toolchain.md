---
title: Outils d'accélération du déploiement dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Outils d'accélération du déploiement dans Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: d47162b3e1a6a303e8b346146948667bc42c2326
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222678"
---
# <a name="deployment-acceleration-tools-in-azure"></a>Outils d'accélération du déploiement dans Azure

L'[Accélération du déploiement](./index.md) est l'une des [cinq disciplines de la gouvernance du cloud](../governance-disciplines.md). Cette discipline met l'accent sur les moyens d'établir des stratégies pour régir la configuration ou le déploiement des ressources. Dans les cinq disciplines de la gouvernance du cloud, la discipline Accélération du déploiement implique le déploiement et l’alignement de la configuration. Des activités manuelles ou des activités DevOps entièrement automatisées peuvent être utilisées. Dans les deux cas, les stratégies impliquées sont en grande partie similaires.

Les opérateurs, gardiens et architectes du cloud qui s'intéressent à la gouvernance sont tous susceptibles d'investir beaucoup de temps dans la discipline Accélération du déploiement, qui codifie les stratégies et les exigences dans le cadre de multiples efforts d'adoption du cloud. Les outils de cette chaîne d’outils sont importants pour l’équipe de gouvernance du cloud et ils doivent constituer une priorité absolue dans son parcours d’apprentissage.

La liste suivante énumère les outils Azure qui peuvent contribuer à faire mûrir les stratégies et les processus soutenant cette discipline de gouvernance.

|  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Groupes d'administration Azure](https://docs.microsoft.com/azure/governance/management-groups) | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview) | [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) | [Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/overview) | [Azure Cost Management](https://docs.microsoft.com/azure/cost-management) |
|---------|---------|---------|---------|---------|---------|---------|
|Implémentation de stratégies d’entreprise     |OUI |Non  |Non  |Non | Non |Non |
|Application de stratégies dans les abonnements     |Obligatoire |OUI  |Non  |Non | Non |Non |
|Déploiement des ressources définies     |Non |Non  |OUI  |Non | Non |Non |
|Création d'environnements entièrement conformes      |Obligatoire |Obligatoire  |Obligatoire  |OUI | Non |Non |
|Audit des stratégies      |OUI |Non  |Non  |Non | Non |Non |
|Interrogation des ressources Azure      |Non |Non  |Non  |Non |OUI |Non |
|Rapport sur le coût des ressources      |Non |Non  |Non  |Non |Non |OUI |

Les outils supplémentaires suivants peuvent s'avérer nécessaires pour atteindre des objectifs spécifiques en matière d'accélération du déploiement. Ces outils sont souvent utilisés en dehors de l'équipe de gouvernance, mais restent considérés comme un aspect de la discipline Accélération du déploiement.

|  | [Portail Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Azure DevOps](https://docs.microsoft.com/azure/devops/index) | [Sauvegarde Azure](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|
|Déploiement manuel (ressource unique)     | OUI | OUI  | Non  | Pas efficace | Non | OUI |
|Déploiement manuel (environnement complet)     | Pas efficace | OUI | Non  | Pas efficace | Non | OUI |
|Déploiement automatisé (environnement complet)     | Non  | OUI  | Non  | OUI  | Non | OUI |
|Mise à jour de la configuration d'une seule ressource     | OUI | OUI | Pas efficace | Pas efficace | Non | Oui - Pendant la réplication |
|Mise à jour de la configuration d'un environnement complet     | Pas efficace | OUI | OUI | OUI  | Non | Oui - Pendant la réplication |
|Gestion des dérives de configuration     | Pas efficace | Pas efficace | OUI  | OUI  | Non | Oui - Pendant la réplication |
|Création d'un pipeline automatisé pour déployer du code et configurer des ressources (DevOps)     | Non | Non | Non | OUI | Non | Non |

Outre les outils Azure natifs mentionnés ci-dessus, les clients utilisent souvent des outils tiers pour faciliter l'accélération du déploiement et les déploiements DevOps.
