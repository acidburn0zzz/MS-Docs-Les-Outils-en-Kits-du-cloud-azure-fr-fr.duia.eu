---
title: Activer les services de gestion de serveur sur une seule machine virtuelle à des fins d’évaluation
description: Activer les services de gestion de serveur sur une seule machine virtuelle à des fins d’évaluation
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: d73b9f5a13150b0c3b13feff3f21a765a36ac4a8
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808037"
---
# <a name="enable-server-management-services-on-a-single-vm-for-evaluation"></a>Activer les services de gestion de serveur sur une seule machine virtuelle à des fins d’évaluation

Découvrez comment activer les services de gestion de serveur sur une seule machine virtuelle à des fins d’évaluation.

> [!NOTE]
> Créez l’[espace de travail Log Analytics et le compte Azure Automation](./prerequisites.md#create-a-workspace-and-automation-account) requis avant d’implémenter des services de gestion Azure sur une machine virtuelle.

Il est facile d’intégrer des services de gestion de serveur Azure dans des machines virtuelles individuelles dans le portail Azure. Vous pouvez vous familiariser avec ces services avant de les intégrer. Quand vous sélectionnez une instance de machine virtuelle, toutes les solutions de la liste des [outils et services de gestion](./tools-services.md) apparaissent dans le menu **Opérations** ou **Supervision**. Vous sélectionnez une solution et suivez l’Assistant pour l’intégrer.

![Capture d’écran des paramètres de machine virtuelle dans le portail Azure](./media/onboarding-single-vm.png)

## <a name="related-resources"></a>Ressources associées

Pour plus d’informations sur l’intégration de ces solutions dans des machines virtuelles individuelles, consultez :

- [Intégrer les solutions Update Management, Change Tracking et Inventory à partir d’une machine virtuelle Azure](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-vm)
- [Intégrer Azure Monitor pour machines virtuelles](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-single-vm)

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment utiliser Azure Policy pour intégrer des machines virtuelles Azure à grande échelle.

> [!div class="nextstepaction"]
> [Configurer les services de gestion Azure pour un abonnement](./onboard-at-scale.md)
