---
title: Activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: e9d5e17e87d79d8d1fdf7239298a973959103a37
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71032314"
---
# <a name="enable-management-services-on-a-single-vm-for-evaluation"></a>Activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation

Découvrez comment activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation.

> [!NOTE]
> Créez l’[espace de travail log Analytics et le compte Azure Automation](./prerequisites.md#create-a-workspace-and-automation-account) requis avant d’intégrer des machines virtuelles aux services de gestion Azure.

L’intégration de machines virtuelles individuelles aux services de gestion de serveur Azure est simple dans le portail Azure. Ce dernier vous permet de vous familiariser avec ces services avant de les intégrer à vos machines virtuelles. Quand vous sélectionnez une instance de machine virtuelle, toutes les solutions abordées dans la liste des [outils et services de gestion](./tools-services.md) apparaissent dans le menu **Opérations** ou **Supervision**. Vous pouvez sélectionner chaque solution et suivre l’Assistant pour l’intégrer.

![Capture d’écran des paramètres de machine virtuelle dans le portail Azure](./media/onboarding-single-vm.png)

## <a name="related-resources"></a>Ressources associées

Pour plus d’informations sur l’intégration de machines virtuelles individuelles à chaque solution, consultez :

- [Intégrer les solutions Update Management, Change Tracking et Inventory à partir d’une machine virtuelle Azure](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-vm)
- [Intégrer Azure Monitor pour machine virtuelle](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-single-vm)

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment utiliser Azure Policy pour intégrer des machines virtuelles Azure à grande échelle.

> [!div class="nextstepaction"]
> [Configurer les services de gestion Azure pour un abonnement](./onboard-at-scale.md)
