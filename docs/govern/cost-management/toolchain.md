---
title: Outils de gestion des coûts dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Outils de gestion des coûts dans Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 3b301f8dfcc50539f4325901cd32553368a0da55
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222639"
---
# <a name="cost-management-tools-in-azure"></a>Outils de gestion des coûts dans Azure

La [gestion des coûts](./index.md) est l’une des [cinq disciplines de la gouvernance cloud](../governance-disciplines.md). Cette discipline vise essentiellement à établir des plans de dépenses cloud, à allouer des budgets cloud, à superviser et à appliquer les budgets cloud, à détecter les anomalies coûteuses et à ajuster le plan de gouvernance cloud en cas d’écarts dans les dépenses réelles.

La liste suivante énumère les outils natifs Azure qui peuvent contribuer à affiner les stratégies et les processus qui soutiennent cette discipline de gouvernance.

| Outil | [Portail Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Cost Management](https://docs.microsoft.com/azure/cost-management/overview-cost-mgt)  | [Azure EA Content Pack](https://docs.microsoft.com/power-bi/service-connect-to-azure-enterprise)  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) |
|---------|---------|---------|---------|---------|
|Contrat Entreprise obligatoire ?     | Non         | Non         | OUI         | Non         |
|Contrôle du budget     | Non         | OUI         | Non         | OUI         |
|Suivi des dépenses sur une même ressource    | OUI         | OUI         | OUI         | Non         |
|Suivi des dépenses sur plusieurs ressources    | Non         | OUI        | OUI         | Non         |
|Contrôle des dépenses sur une même ressource     | Oui - dimensionnement manuel         | OUI         | Non         | OUI         |
|Assurer le respect des dépenses sur plusieurs ressources    | Non         | OUI         | Non         | OUI         |
|Appliquer les métadonnées de comptabilité aux ressources    | Non         | Non         | Non         | OUI         |
|Surveillance et détection des tendances     | OUI          | OUI        | OUI         | Non         |
|Détection des anomalies de dépenses     | Non         | OUI        | OUI         | Non        |
|Communication des écarts     | Non        | OUI        | OUI        | Non        |
