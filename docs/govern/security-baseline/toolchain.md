---
title: Outils de base de référence de la sécurité dans Azure
description: Découvrez comment les outils natifs Azure peuvent contribuer à affiner les stratégies et les processus qui vont dans le sens de la discipline de gouvernance de base de référence de la sécurité.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 53321f274480094d5ff9db91f282a825594536fc
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80997232"
---
# <a name="security-baseline-tools-in-azure"></a>Outils de base de référence de la sécurité dans Azure

La discipline [Base de référence de la sécurité](./index.md) est l’une des [cinq disciplines de la gouvernance cloud](../governance-disciplines.md). Cette discipline se concentre sur l’établissement de stratégies qui protègent le réseau, les ressources et, plus important encore, les données qui résideront sur la solution d’un fournisseur de services cloud. Parmi les cinq disciplines de la gouvernance cloud, la discipline Base de référence de la sécurité implique la classification du parc numérique et des données. Elle implique également la documentation relative aux risques, à la tolérance métier et aux stratégies d’atténuation associées à la sécurité des données, des ressources et des réseaux. D’un point de vue technique, cette discipline englobe également la participation aux décisions concernant le [chiffrement](../../decision-guides/encryption/index.md), la [configuration réseau requise](../../decision-guides/software-defined-network/index.md), les [stratégies d’identités hybrides](../../decision-guides/identity/index.md) et les outils d’[automatisation de l’application](../../decision-guides/policy-enforcement/index.md) des stratégies de sécurité dans les [groupes de ressources](../../decision-guides/resource-consistency/index.md).

La liste suivante énumère les outils Azure qui peuvent contribuer au développement des stratégies et des processus soutenant cette discipline de base de référence de la sécurité.

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

Il est également courant pour les clients d’utiliser des outils tiers pour faciliter les activités de base de référence de la sécurité. Pour plus d’informations, consultez l’article [Intégrer les solutions de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-partner-integration).

En plus des outils de sécurité, le [Microsoft Trust Center](https://www.microsoft.com/microsoft-365/business/compliance-solutions#office-KeyMessages-k3j63yo) contient de nombreux conseils, rapports et documents connexes qui peuvent vous aider à effectuer des évaluations des risques dans le cadre de votre processus de planification de migration.
