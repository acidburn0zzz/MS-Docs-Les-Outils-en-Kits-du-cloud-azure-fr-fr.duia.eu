---
title: Outils de gestion des coûts dans Azure
description: Découvrez comment les outils natifs Azure peuvent contribuer à affiner les stratégies et les processus qui vont dans le sens de la discipline de gouvernance de la gestion des coûts.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 0104ba7ce0e938d9abe763a15537cc35e2d94ecf
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80995562"
---
# <a name="cost-management-tools-in-azure"></a>Outils de gestion des coûts dans Azure

La [gestion des coûts](./index.md) est l’une des [cinq disciplines de la gouvernance cloud](../governance-disciplines.md). Cette discipline vise essentiellement à établir des plans de dépenses cloud, à allouer des budgets cloud, à superviser et à appliquer les budgets cloud, à détecter les anomalies coûteuses et à ajuster le plan de gouvernance cloud en cas d’écarts dans les dépenses réelles.

La liste suivante énumère les outils natifs Azure qui peuvent contribuer à affiner les stratégies et les processus qui soutiennent cette discipline de gouvernance.

| Outil | [Azure portal](https://azure.microsoft.com/features/azure-portal)  | [Azure Cost Management](https://docs.microsoft.com/azure/cost-management-billing/cost-management-billing-overview)  | [Azure EA Content Pack](https://docs.microsoft.com/power-bi/service-connect-to-azure-enterprise)  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) |
|---------|---------|---------|---------|---------|
|Contrat Entreprise obligatoire ?     | Non         | Non         | Oui         | Non         |
|Contrôle du budget     | Non         | Oui         | Non         | Oui         |
|Suivi des dépenses sur une même ressource    | Oui         | Oui         | Oui         | Non         |
|Suivi des dépenses sur plusieurs ressources    | Non         | Oui        | Oui         | Non         |
|Contrôle des dépenses sur une même ressource     | Oui - dimensionnement manuel         | Oui         | Non         | Oui         |
|Assurer le respect des dépenses sur plusieurs ressources    | Non         | Oui         | Non         | Oui         |
|Appliquer les métadonnées de comptabilité aux ressources    | Non         | Non         | Non         | Oui         |
|Surveillance et détection des tendances     | Oui          | Oui        | Oui         | Non         |
|Détection des anomalies de dépenses     | Non         | Oui        | Oui         | Non        |
|Communication des écarts     | Non        | Oui        | Oui        | Non        |
