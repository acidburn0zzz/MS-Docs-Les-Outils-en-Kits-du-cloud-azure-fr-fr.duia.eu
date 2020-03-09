---
title: Outils de gestion des coûts dans Azure
description: Découvrez comment les outils natifs Azure peuvent contribuer à affiner les stratégies et les processus qui vont dans le sens de la discipline de gouvernance de la gestion des coûts.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 70014352d4b7f64f5c73a0fda96ef453f1a77176
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708782"
---
# <a name="cost-management-tools-in-azure"></a>Outils de gestion des coûts dans Azure

La [gestion des coûts](./index.md) est l’une des [cinq disciplines de la gouvernance cloud](../governance-disciplines.md). Cette discipline vise essentiellement à établir des plans de dépenses cloud, à allouer des budgets cloud, à superviser et à appliquer les budgets cloud, à détecter les anomalies coûteuses et à ajuster le plan de gouvernance cloud en cas d’écarts dans les dépenses réelles.

La liste suivante énumère les outils natifs Azure qui peuvent contribuer à affiner les stratégies et les processus qui soutiennent cette discipline de gouvernance.

| Outil | [Azure portal](https://azure.microsoft.com/features/azure-portal)  | [Azure Cost Management](https://docs.microsoft.com/azure/cost-management/overview-cost-mgt)  | [Azure EA Content Pack](https://docs.microsoft.com/power-bi/service-connect-to-azure-enterprise)  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) |
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
