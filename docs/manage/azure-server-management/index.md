---
title: Vue d’ensemble des services de gestion de serveurs Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduction aux services de gestion de serveurs Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 4d1ada9d47e54f4b0d3828ce93b2d55f3eda8a34
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025921"
---
# <a name="overview-of-azure-server-management-services"></a>Vue d’ensemble des services de gestion de serveurs Azure

Les services de gestion de serveurs Azure fournissent aux clients une expérience cohérente pour la gestion de leurs serveurs à grande échelle. Ces services couvrent les systèmes d’exploitation Linux et Windows, et peuvent être utilisés dans des environnements de production, de développement et de test. Ils peuvent aussi prendre en charge les machines virtuelles Azure IaaS, les serveurs physiques et les machines virtuelles hébergées localement ou dans d’autres environnements d’hébergement. 

Le diagramme ci-dessous illustre les services inclus dans la suite de services de gestion de serveurs Azure. 

![Diagramme du modèle d’opérations Azure](./media/operations-diagram.png)

Les instructions de cette section du Framework d’adoption du cloud Microsoft fournissent un plan normatif actionnable pour le déploiement de services de gestion de serveurs dans votre environnement. Ce plan a pour objectif de vous orienter rapidement vers ces services, avec un ensemble de phases de gestion incrémentielles pour toutes les tailles d’environnement.

Pour faire simple, nous avons regroupé les tâches décrites dans ce guide en trois phases :

![Les trois phases d’intégration de la suite de gestion de serveurs Azure](./media/operations-stages.png)

<!-- markdownlint-disable MD026 -->

## <a name="why-use-azure-management-services"></a>Pourquoi utiliser les services de gestion Azure ?

Les services de gestion Azure offrent les avantages suivants :

- **Caractère natif dans Azure.** Les services de gestion sont intégrés en mode natif à Azure Resource Manager. Ils sont constamment améliorés afin de fournir de nouvelles fonctionnalités et capacités.
- **Windows et Linux**. Les machines Windows et Linux fournissent la même expérience de gestion cohérente.
- **Caractère hybride.** Les services de gestion couvrent les machines virtuelles Azure IaaS ainsi que les serveurs virtuels et physiques hébergés localement ou dans d’autres environnements d’hébergement.
- **Sécurité.** Microsoft consacre des ressources substantielles à toutes les formes de sécurité. Cet investissement protège non seulement l’infrastructure cloud Azure, mais étend également les technologies et l’expertise qui en résulte afin de protéger les ressources des clients partout où elles résident.

## <a name="next-steps"></a>Étapes suivantes

Familiarisez-vous avec les [outils, services et planification](./prerequisites.md) impliqués dans l’adoption de la suite de gestion de serveurs Azure.

> [!div class="nextstepaction"]
> [Planification et outils prérequis](./prerequisites.md)
