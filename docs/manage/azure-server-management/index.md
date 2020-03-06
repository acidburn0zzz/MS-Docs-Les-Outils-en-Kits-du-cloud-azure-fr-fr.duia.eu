---
title: Vue d’ensemble des services de gestion de serveurs Azure
description: Comprenez le plan normatif que fournit cette section du Framework d’adoption du cloud pour déployer les services de gestion de serveurs dans votre environnement.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: c6afdfe05a9245d729b17d1d56f3c64ffa6107bd
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78341672"
---
# <a name="overview-of-azure-server-management-services"></a>Vue d’ensemble des services de gestion de serveurs Azure

Les services de gestion de serveurs Azure fournissent une expérience cohérente pour gérer les serveurs à grande échelle. Ces services couvrent à la fois les systèmes d’exploitation Linux et Windows. Ils peuvent être utilisés dans des environnements de production, de développement et de test. Les services de gestion de serveurs peuvent aussi prendre en charge les machines virtuelles Azure IaaS, les serveurs physiques et les machines virtuelles hébergées localement ou dans d’autres environnements d’hébergement.

La suite de services de gestion de serveurs Azure comprend les services dans le diagramme suivant : ![Diagramme du modèle d’opérations Azure](./media/operations-diagram.png)

Cette section du Framework d’adoption du cloud Microsoft fournit un plan normatif actionnable pour déployer les services de gestion de serveurs dans votre environnement. Ce plan vous aide à vous orienter rapidement vers ces services, avec un ensemble de phases de gestion incrémentielles pour toutes les tailles d’environnement.

Pour faire simple, nous avons regroupé les tâches décrites dans ce guide en trois phases :

![Les trois phases d’intégration de la suite de gestion de serveurs Azure](./media/operations-stages.png)

<!-- markdownlint-disable MD026 -->

## <a name="why-use-azure-server-management-services"></a>Pourquoi utiliser les services de gestion de serveurs Azure ?

Les services de gestion de serveurs Azure offrent les avantages suivants :

- **Mode natif dans Azure :** Les services de gestion de serveurs sont intégrés en mode natif à Azure Resource Manager. Ils sont constamment améliorés afin de fournir de nouvelles fonctionnalités et capacités.
- **Windows et Linux :** Les machines Windows et Linux ont la même expérience de gestion cohérente.
- **Hybride :** Les services de gestion de serveurs couvrent les machines virtuelles Azure IaaS ainsi que les serveurs virtuels et physiques hébergés localement ou dans d’autres environnements d’hébergement.
- **Sécurité :** Microsoft consacre des ressources substantielles à toutes les formes de sécurité. Cet investissement protège non seulement l’infrastructure Azure, mais étend aussi les technologies et l’expertise qui en résulte afin de protéger les ressources des clients où qu’elles soient.

## <a name="next-steps"></a>Étapes suivantes

Familiarisez-vous avec les [outils, services et planification](./prerequisites.md) impliqués dans l’adoption de la suite de gestion de serveurs Azure.

> [!div class="nextstepaction"]
> [Planification et outils prérequis](./prerequisites.md)
