---
title: Outils d'accélération du déploiement dans Azure
description: Découvrez comment les outils natifs Azure peuvent contribuer à affiner les stratégies et les processus qui vont dans le sens de la discipline Accélération du déploiement.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 356373e71bc12c7927debdb64f036f8774809860
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83220224"
---
# <a name="deployment-acceleration-tools-in-azure"></a>Outils d'accélération du déploiement dans Azure

La [discipline Accélération du déploiement](./index.md) est l'une des [cinq disciplines de la gouvernance du cloud](../governance-disciplines.md). Cette discipline met l'accent sur les moyens d'établir des stratégies pour régir la configuration ou le déploiement des ressources. Dans les cinq disciplines de la gouvernance du cloud, la discipline Accélération du déploiement implique le déploiement et l’alignement de la configuration. Des activités manuelles ou des activités DevOps entièrement automatisées peuvent être utilisées. Dans les deux cas, les stratégies impliquées sont en grande partie similaires.

Les opérateurs, gardiens et architectes du cloud qui s'intéressent à la gouvernance sont tous susceptibles d'investir beaucoup de temps dans la discipline Accélération du déploiement, qui codifie les stratégies et les exigences dans le cadre de multiples efforts d'adoption du cloud. Les outils de cette chaîne d’outils sont importants pour l’équipe de gouvernance du cloud et ils doivent constituer une priorité absolue dans son parcours d’apprentissage.

La liste suivante énumère les outils Azure qui peuvent contribuer à faire mûrir les stratégies et les processus soutenant cette discipline de gouvernance.

|  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Groupes d'administration Azure](https://docs.microsoft.com/azure/governance/management-groups) | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/management/overview) | [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) | [Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/overview) | [Azure Cost Management](https://docs.microsoft.com/azure/cost-management) |
|---------|---------|---------|---------|---------|---------|---------|
| Implémentation de stratégies d’entreprise     | Oui | Non  | Non  | Non | Non | Non |
| Application de stratégies dans les abonnements     | Obligatoire | Oui  | Non  | Non | Non | Non |
| Déploiement des ressources définies     | Non | Non  | Oui  | Non | Non | Non |
| Création d'environnements entièrement conformes      | Obligatoire | Obligatoire  | Obligatoire  | Oui | Non | Non |
| Audit des stratégies      | Oui | Non  | Non  | Non | Non | Non |
| Interrogation des ressources Azure      | Non | Non  | Non  | Non | Oui | Non |
| Rapport sur le coût des ressources      | Non | Non  | Non  | Non | Non | Oui |

Les outils supplémentaires suivants peuvent s'avérer nécessaires pour atteindre des objectifs spécifiques en matière d'accélération du déploiement. Ces outils sont souvent utilisés en dehors de l'équipe de gouvernance, mais restent considérés comme un aspect de la discipline Accélération du déploiement.

|  | [Azure portal](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/management/overview)  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Azure DevOps](https://docs.microsoft.com/azure/devops) | [Azure Backup](https://docs.microsoft.com/azure/backup/backup-overview) | [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|
| Déploiement manuel (ressource unique)     | Oui | Oui  | Non  | Pas efficace | Non | Oui |
| Déploiement manuel (environnement complet)     | Pas efficace | Oui | Non  | Pas efficace | Non | Oui |
| Déploiement automatisé (environnement complet)     | Non  | Oui  | Non  | Oui  | Non | Oui |
| Mise à jour de la configuration d'une seule ressource     | Oui | Oui | Pas efficace | Pas efficace | Non | Oui - Pendant la réplication |
| Mise à jour de la configuration d'un environnement complet     | Pas efficace | Oui | Oui | Oui  | Non | Oui - Pendant la réplication |
| Gestion des dérives de configuration     | Pas efficace | Pas efficace | Oui  | Oui  | Non | Oui - Pendant la réplication |
| Création d'un pipeline automatisé pour déployer du code et configurer des ressources (DevOps)     | Non | Non | Non | Oui | Non | Non |

Outre les outils Azure natifs mentionnés ci-dessus, les clients utilisent souvent des outils tiers pour faciliter l'accélération du déploiement et les déploiements DevOps.
