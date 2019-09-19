---
title: Intégration aux services de gestion de serveurs Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Intégration aux services de gestion de serveurs Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 330e297b4fb63eaa376e8b6dac0ccf77c2a16ef4
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031313"
---
# <a name="phase-2-onboarding-azure-server-management-services"></a>Phase 2 : Intégration aux services de gestion de serveurs Azure

Quand vous êtes familiarisé avec les [outils](./tools-services.md) et la [planification](./prerequisites.md) impliqués dans les services de gestion Azure, vous êtes prêt pour la deuxième phase, qui fournit des instructions pas à pas pour l’intégration de ces services en vue de leur utilisation avec vos ressources Azure. Commencez par évaluer ce processus d’intégration avant de l’adopter largement dans votre environnement.

> [!NOTE]
> Les approches d’automatisation présentées dans les sections ultérieures de ce guide sont destinées à des déploiements qui n’ont pas encore de serveurs déployés dans le cloud. Elles vous demandent d’avoir le rôle de propriétaire sur un abonnement pour créer toutes les ressources et stratégies nécessaires. Si vous avez déjà créé les ressources de l’espace de travail Log Analytics et du compte Automation, nous vous recommandons de transmettre ces ressources dans les paramètres appropriés lors du lancement des exemples de scripts d’automatisation.

## <a name="onboarding-processes"></a>Processus d’intégration

Cette section du guide couvre les processus d’intégration suivants pour les machines virtuelles Azure et les serveurs locaux :

- **Activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation à l’aide du portail**. Utilisez ce processus pour vous familiariser avec les services de gestion de serveur Azure.
- **Configurer les services de gestion pour un abonnement à l’aide du portail** Ce processus vous aide à configurer l’environnement Azure afin que toutes les nouvelles machines virtuelles qui sont provisionnées utilisent automatiquement les services de gestion. Utilisez cette approche si vous préférez l’expérience du portail Azure aux scripts et aux lignes de commande.
- **Configurer les services de gestion pour un abonnement à l’aide d’Azure Automation** Ce processus est entièrement automatisé. Il vous suffit de créer un abonnement ; les scripts configurent l’environnement de façon à utiliser les services de gestion pour toutes les machines virtuelles nouvellement provisionnées. Utilisez cette approche si vous êtes familiarisé avec les scripts PowerShell et les modèles Azure Resource Manager, ou si vous souhaitez apprendre à les utiliser.

Les procédures pour chacune de ces approches sont différentes.

> [!NOTE]
> La séquence des étapes d’intégration lors de l’utilisation du portail Azure diffère des étapes d’intégration automatisées, car le portail offre une expérience d’intégration plus simple.

Le schéma suivant illustre le modèle de déploiement recommandé pour les services de gestion. 

![Schéma du modèle de déploiement recommandé](./media/recommended-deployment.png)

> [!NOTE]
> Comme indiqué dans le schéma précédent, l’agent Log Analytics a une configuration d’*inscription automatique* et d’*adhésion* pour les serveurs locaux. L’*inscription automatique* signifie que quand l’agent Log Analytics est installé sur un serveur et configuré pour se connecter à un espace de travail, les solutions activées sur cet espace de travail s’appliquent automatiquement au serveur. Une *adhésion* signifie que même si l’agent est installé et connecté à l’espace de travail, la solution n’est pas appliquée, sauf si elle est ajoutée à la configuration d’étendue du serveur dans l’espace de travail.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment intégrer une machine virtuelle unique à l’aide du portail pour évaluer le processus d’intégration.

> [!div class="nextstepaction"]
> [Intégrer une machine virtuelle Azure unique à des fins d’évaluation](./onboard-single-vm.md)