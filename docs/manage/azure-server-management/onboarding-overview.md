---
title: Intégrer les services de gestion de serveur Azure
description: Intégrez les services de gestion de serveur Azure à l’aide des informations relatives aux machines virtuelles Azure et aux serveurs locaux.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 0396ccaf952bc9d7812304af5d1d9c9952b751cc
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219629"
---
# <a name="phase-2-onboarding-azure-server-management-services"></a>Phase 2 : Intégration aux services de gestion de serveurs Azure

Une fois que vous êtes familiarisé avec les [outils](./tools-services.md) et la [planification](./prerequisites.md) impliquées dans les services de gestion Azure, vous êtes prêt pour la deuxième phase. La phase 2 fournit des instructions pas à pas pour l’intégration de ces services et leur utilisation avec vos ressources Azure. Commencez par évaluer ce processus d’intégration avant de l’adopter largement dans votre environnement.

> [!NOTE]
> Les approches d’automatisation présentées dans les sections ultérieures de ce guide sont destinées à des déploiements qui n’ont pas encore de serveurs déployés dans le cloud. Elles vous demandent d’avoir le rôle de propriétaire sur un abonnement pour créer toutes les ressources et stratégies nécessaires. Si vous avez déjà créé les ressources de l’espace de travail Log Analytics et du compte Automation, nous vous recommandons de transmettre ces ressources dans les paramètres appropriés lorsque vous lancez les exemples de scripts d’automatisation.

## <a name="onboarding-processes"></a>Processus d’intégration

Cette section du guide couvre les processus d’intégration suivants pour les machines virtuelles Azure et les serveurs locaux :

- **Activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation à l’aide du portail**. Utilisez ce processus pour vous familiariser avec les services de gestion de serveur Azure.
- **Configurer les services de gestion pour un abonnement à l’aide du portail** Ce processus vous aide à configurer l’environnement Azure afin que toutes les nouvelles machines virtuelles qui sont provisionnées utilisent automatiquement les services de gestion. Utilisez cette approche si vous préférez l’expérience du portail Azure aux scripts et aux lignes de commande.
- **Configurer les services de gestion pour un abonnement à l’aide d’Azure Automation** Ce processus est entièrement automatisé. Créez simplement un abonnement ; les scripts configurent l’environnement de façon à utiliser les services de gestion pour toutes les machines virtuelles nouvellement provisionnées. Utilisez cette approche si vous êtes familiarisé avec les scripts PowerShell et les modèles Azure Resource Manager, ou si vous souhaitez apprendre à les utiliser.

Les procédures pour chacune de ces approches sont différentes.

> [!NOTE]
> Lorsque vous utilisez le portail Azure, la séquence d’étapes d’intégration diffère des étapes d’intégration automatisées. Le portail offre une expérience d’intégration plus simple.

Le schéma suivant illustre le modèle de déploiement recommandé pour les services de gestion :

![Schéma du modèle de déploiement recommandé](./media/recommended-deployment.png)

Comme indiqué dans le schéma précédent, l’agent Log Analytics a une configuration d’_inscription automatique_ et d’_adhésion_ pour les serveurs locaux :

- **Inscription automatique :** Lorsque l’agent Log Analytics est installé sur un serveur et configuré pour se connecter à un espace de travail, les solutions activées sur cet espace de travail sont automatiquement appliquées au serveur.
- **Accepter :** Même si l’agent est installé et connecté à l’espace de travail, la solution n’est pas appliquée, sauf si elle est ajoutée à la configuration d’étendue du serveur dans l’espace de travail.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment intégrer une machine virtuelle unique à l’aide du portail pour évaluer le processus d’intégration.

> [!div class="nextstepaction"]
> [Intégrer une machine virtuelle Azure unique à des fins d’évaluation](./onboard-single-vm.md)
