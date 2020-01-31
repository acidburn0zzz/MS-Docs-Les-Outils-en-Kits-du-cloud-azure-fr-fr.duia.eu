---
title: Bonnes pratiques pour la migration Azure
description: Introduction aux bonnes pratiques pour la migration Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 5cc4a0cfdfe605fdd374055e782db2f0ce47c13f
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807289"
---
# <a name="azure-migration-best-practices"></a>Bonnes pratiques pour la migration Azure

Azure fournit plusieurs outils pour exécuter une migration. Cette section du Framework d’adoption du cloud est conçue pour aider les lecteurs à implémenter ces outils conformément aux bonnes pratiques de migration. Ces bonnes pratiques sont alignées sur l’un des processus du modèle de migration du Framework d’adoption du cloud illustré ci-dessous.

Développez un processus dans la table des matières sur la gauche pour voir les bonnes pratiques généralement requises pendant ce même processus.

![Modèle de migration du Framework d’adoption du cloud](../../_images/operational-transformation-migrate.png)

> [!NOTE]
> La planification du patrimoine numérique et l’évaluation des ressources représentent deux niveaux différents de planification et d’évaluation de la migration :
>
> - **Planification du patrimoine numérique** : Vous planifiez ou rationalisez le patrimoine numérique pendant la planification pour établir un backlog de migration global. Toutefois, ce plan est basé sur des hypothèses et des détails qui doivent être validés avant de pouvoir migrer une charge de travail.
> - **Évaluation des ressources :** Vous évaluez les ressources individuelles d’une charge de travail avant sa migration pour estimer la compatibilité cloud et comprendre l’architecture et les contraintes de taille. Ce processus valide les premières hypothèses et fournit les détails nécessaires pour migrer une ressource individuelle.
