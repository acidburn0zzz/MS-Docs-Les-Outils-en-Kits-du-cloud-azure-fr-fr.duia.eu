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
ms.openlocfilehash: c649ef695e74dce0ae2ec21e1e0d666abc2a65e9
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565826"
---
# <a name="tools-to-interact-with-devices-in-azure"></a>Outils permettant d’interagir avec des appareils dans Azure

Comme décrit dans l’article conceptuel sur l’[interaction avec des appareils](../considerations/devices.md), les appareils utilisés pour interagir avec un client dépendent tous de l’expérience ambiante nécessaire pour satisfaire le besoin du client et favoriser l’adoption. Le délai entre le déclencheur qui suscite le besoin du client et la capacité de votre solution à y répondre représente sont des facteurs déterminants d’une utilisation renouvelée. Les expériences ambiantes permettent de réduire le temps de réponse et de créer une meilleure expérience pour vos clients en incorporant votre solution dans l’environnement immédiat des clients.

![Framework d’adoption du cloud : approche de l’interaction avec les appareils](../../_images/innovate/ambient-experiences.png)

## <a name="alignment-to-the-methodology"></a>Alignement sur la méthodologie

Ce type d’invention numérique peut être réalisé sur la base de l’un des niveaux d’expérience ambiante suivants. Ces niveaux s’alignent sur la méthodologie indiquée dans l’image précédente. La table des matières à gauche sur cette page inclut des rubriques d’aide technique permettant d’accélérer l’invention numérique. Ces articles sont regroupés par niveau d’expérience ambiante pour s’aligner sur la méthodologie.

- **Expérience mobile :** les applications mobiles font généralement partie de l’environnement d’un client. Dans certains scénarios, un appareil mobile peut fournir suffisamment d’interactivité pour rendre une solution ambiante.
- **Réalité mixte :** parfois, l’environnement naturel d’un client doit être modifié par la réalité mixte. L’engagement d’un client dans cette réalité mixte peut produire une forme d’expérience ambiante.
- **Réalité intégrée :** s’approchant de l’ambiance réelle, les solutions de réalité intégrée sont axées sur l’utilisation d’un appareil physique du client pour intégrer la solution dans des comportements naturels.
- **Réalité ajustée :** quand l’une des solutions précédentes utilise l’analyse prédictive pour produire une interaction avec un client dans son environnement naturel, cette solution crée la forme d’expérience ambiante la plus élevée.

## <a name="toolchain"></a>Chaîne d’outils

Dans Azure, vous utilisez fréquemment les outils suivants pour accélérer l’invention numérique pour chaque niveau de solution ambiante ci-dessus. Ces outils sont regroupés selon l’expérience nécessaire pour réduire la complexité de l’alignement des outils sur cette expérience.

- Expérience mobile : Azure App Service, PowerApps, Microsoft Flow, Intune
- Réalité mixte : Unity, Azure Spatial Anchors, HoloLens
- Réalité intégrée : Azure IoT Hub, Azure Sphere, Kinect DK
- Réalité ajustée : cloud IoT à appareil, Azure Digital Twins + HoloLens

## <a name="get-started"></a>Prise en main

La table des matières sur le côté gauche de cette page met en avant de nombreux articles. Ces articles vous aident à prendre en main chacun des outils de cette chaîne d’outils.

> [!NOTE]
> Certains liens peuvent pointer vers d’autres contenus que ceux du framework d’adoption du cloud pour vous aider à aller au-delà de la portée de ce framework.
