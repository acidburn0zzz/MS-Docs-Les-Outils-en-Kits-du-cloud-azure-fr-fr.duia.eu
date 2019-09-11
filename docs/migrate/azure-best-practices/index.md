---
title: Bonnes pratiques pour la migration Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduction aux bonnes pratiques pour la migration Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: e8a7ae0af3b64a6d7e04555fe64a6189d964b3ff
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70816565"
---
# <a name="azure-migration-best-practices"></a>Bonnes pratiques pour la migration Azure

Azure fournit plusieurs outils pour exécuter une migration. Cette section du Framework d’adoption du cloud est conçue pour aider les lecteurs à implémenter ces outils conformément aux bonnes pratiques de migration. Ces bonnes pratiques sont alignées sur l’un des processus du modèle de migration du Framework d’adoption du cloud illustré ci-dessous.

Développez un processus dans la table des matières sur la gauche pour voir les bonnes pratiques généralement requises pendant ce même processus.

![Modèle de migration du Framework d’adoption du cloud](../../_images/operational-transformation-migrate.png)

> [!NOTE]
> La planification du patrimoine numérique et l’évaluation des ressources représentent deux niveaux différents de planification et d’évaluation de la migration :
>
> - **Planification du patrimoine numérique** : Vous planifiez ou rationalisez le patrimoine numérique pendant la planification pour établir un backlog de migration global. Toutefois, ce plan est basé sur des hypothèses et des détails qui doivent être validés avant de pouvoir migrer une charge de travail.
> - **Évaluation des ressources :** Vous évaluez les ressources d’une charge de travail avant sa migration pour estimer la compatibilité cloud et comprendre l’architecture et les contraintes de taille. Ce processus valide les premières hypothèses et fournit les détails nécessaires pour migrer une ressource individuelle.
