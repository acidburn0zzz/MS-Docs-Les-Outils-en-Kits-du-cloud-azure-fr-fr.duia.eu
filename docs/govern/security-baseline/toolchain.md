---
title: Outils de base de référence de la sécurité dans Azure
description: Découvrez comment les outils natifs Azure peuvent contribuer à affiner les stratégies et les processus qui vont dans le sens de la discipline Ligne de base de la sécurité.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 51e0a253a7e66f70ec440dd7be969f324afb795c
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83217674"
---
# <a name="security-baseline-tools-in-azure"></a>Outils de base de référence de la sécurité dans Azure

La [discipline Ligne de base de la sécurité](./index.md) est l’une des [Cinq disciplines de gouvernance du cloud](../governance-disciplines.md). Cette discipline se concentre sur l’établissement de stratégies qui protègent le réseau, les ressources et, plus important encore, les données qui résideront sur la solution d’un fournisseur de services cloud. Parmi les cinq disciplines de la gouvernance cloud, la discipline Base de référence de la sécurité implique la classification du parc numérique et des données. Elle implique également la documentation relative aux risques, à la tolérance métier et aux stratégies d’atténuation associées à la sécurité des données, des ressources et des réseaux. D’un point de vue technique, cette discipline englobe également la participation aux décisions concernant le [chiffrement](../../decision-guides/encryption/index.md), la [configuration réseau requise](../../decision-guides/software-defined-network/index.md), les [stratégies d’identités hybrides](../../decision-guides/identity/index.md) et les outils d’[automatisation de l’application](../../decision-guides/policy-enforcement/index.md) des stratégies de sécurité dans les [groupes de ressources](../../decision-guides/resource-consistency/index.md).

La liste suivante énumère les outils Azure qui peuvent contribuer au développement des stratégies et des processus soutenant cette discipline.

| Outil | [Portail Azure](https://azure.microsoft.com/features/azure-portal) et [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/management/overview)  | [Azure Key Vault](https://docs.microsoft.com/azure/key-vault)  | [Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Centre de sécurité Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) | [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) |
|------------------------------------------------------------|---------------------------------|-----------------|----------|--------------|-----------------------|---------------|
| Appliquer des contrôles d’accès aux ressources et à la création de ressources   | Oui                             | Non              | Oui      | Non           | Non                    | Non            |
| Sécuriser les réseaux virtuels                                    | Oui                             | Non              | Non       | Oui          | Non                    | Non            |
| Chiffrer les disques virtuels                                     | Non                              | Oui             | Non       | Non           | Non                    | Non            |
| Chiffrer le stockage et bases de données PaaS                         | Non                              | Oui             | Non       | Non           | Non                    | Non            |
| Gérer les services d’identité hybride                            | Non                              | Non              | Oui      | Non           | Non                    | Non            |
| Restreindre les types de ressources autorisés                         | Non                              | Non              | Non       | Oui          | Non                    | Non            |
| Appliquer des restrictions géo-régionales                          | Non                              | Non              | Non       | Oui          | Non                    | Non            |
| Surveiller l’intégrité de la sécurité des réseaux et des ressources          | Non                              | Non              | Non       | Non           | Oui                   | Oui           |
| Détecter les activités malveillantes                                  | Non                              | Non              | Non       | Non           | Oui                   | Oui           |
| Détecter les vulnérabilités de manière préemptive                        | Non                              | Non              | Non       | Non           | Oui                   | Non            |
| Configurer la sauvegarde et la récupération d’urgence                     | Oui                             | Non              | Non       | Non           | Non                    | Non            |

Vous pouvez consulter une liste complète des outils et services de sécurité Azure dans l’article [Services et technologies de sécurité disponibles sur Azure](https://docs.microsoft.com/azure/security/fundamentals/services-technologies).

Les clients utilisent généralement des outils tiers pour activer les activités de la discipline Ligne de base de la sécurité. Pour plus d’informations, consultez l’article [Intégrer les solutions de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-partner-integration).

En plus des outils de sécurité, le [Microsoft Trust Center](https://www.microsoft.com/microsoft-365/business/compliance-solutions#office-KeyMessages-k3j63yo) contient de nombreux conseils, rapports et documents connexes qui peuvent vous aider à effectuer des évaluations des risques dans le cadre de votre processus de planification de migration.
