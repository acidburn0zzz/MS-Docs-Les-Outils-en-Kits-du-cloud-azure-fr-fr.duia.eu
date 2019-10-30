---
title: 'Innovation cloud : outils permettant d’interagir avec des appareils dans Azure'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Outils permettant d’interagir avec des appareils dans Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: a8dcdf770e31a1b0fb380ac0fe85bb2fe9c8ed0b
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683394"
---
# <a name="tools-to-interact-with-devices-in-azure"></a>Outils permettant d’interagir avec des appareils dans Azure

Comme décrit dans l’article théorique sur l’[interaction avec des appareils](../considerations/devices.md), les appareils utilisés pour interagir avec le client dépendent tous du niveau d’expérience ambiante nécessaire pour satisfaire le besoin du client et favoriser l’adoption. Le délai entre le déclencheur suscitant le besoin du client et la capacité de votre solution à y répondre représente un facteur déterminant d’une utilisation renouvelée. Les expériences ambiantes permettent de réduire le temps de réponse et de créer une meilleure expérience pour vos clients en incorporant votre solution dans l’environnement immédiat des clients.

![Framework d’adoption du cloud : approche de l’interaction avec les appareils](../../_images/innovate/ambient-experiences.png)

## <a name="alignment-to-the-methodology"></a>Alignement sur la méthodologie

Ce type d’invention numérique peut être réalisé sur la base de l’un des niveaux d’expérience ambiante suivants, conformément à la méthodologie illustrée ci-dessus. La table des matières, à gauche, inclut des rubriques d’aide technique permettant d’accélérer l’invention numérique. Ces articles ont été regroupés selon les mêmes niveaux d’expériences ambiantes pour s’aligner sur la méthodologie :

- **Expérience mobile :** les applications mobiles font généralement partie de l’environnement des clients. Dans certains scénarios, un appareil mobile peut offrir un niveau d’interactivité suffisant pour rendre une solution ambiante.
- **Réalité mixte :** parfois, l’environnement naturel d’un client doit être modifié par la réalité mixte. L’engagement des clients dans cette réalité mixte peut produire une forme d’expérience ambiante.
- **Réalité intégrée :** s’approchant de l’ambiance réelle, les solutions de réalité intégrée sont axées sur l’utilisation d’un appareil qui existe dans la réalité physique du client pour intégrer la solution dans des comportements naturels.
- **Réalité ajustée :** quand l’une des solutions ambiantes ci-dessus utilise l’analyse prédictive pour produire une interaction avec le client dans son environnement naturel, la solution crée la forme d’expérience ambiante la plus élevée.

## <a name="toolchain"></a>Chaîne d’outils

Dans Azure, les outils suivants sont fréquemment utilisés afin d’accélérer l’invention numérique pour chaque niveau de solution ambiante ci-dessus. Ces outils ont été regroupés selon le niveau d’expérience nécessaire pour réduire la complexité de l’alignement des outils sur les expériences requises.

- Expérience mobile : App Service, PowerApps, Microsoft Flow, Intune
- Réalité mixte : Unity, Azure Spatial Anchors, HoloLens
- Réalité intégrée : Azure IoT Hub, Azure Sphere, Kinect DK
- Réalité ajustée : IoT cloud à appareil, Digital Twins + HoloLens

## <a name="get-started"></a>Prise en main

La table des matières, à gauche, inclut de nombreux articles qui vous aideront à prendre en main chacun des outils de cette chaîne.

> [!NOTE]
> Certains liens pointent vers des contenus s’éloignant du framework d’adoption du cloud, vous permettant d’aller au-delà de la portée de ce framework.
