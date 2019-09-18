---
title: Centre de données virtuel Azure
description: Ressources portant sur le centre de données virtuel Microsoft Azure
author: tracsman
ms.author: jonor
ms.date: 06/12/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: reference
keywords: Azure
layout: LandingPage
ms.openlocfilehash: 39cb6ac3c31873431206d8c6c525c9ce3467653f
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031581"
---
# <a name="azure-virtual-datacenter-and-the-enterprise-control-plane"></a>Le centre de données virtuel Azure et le plan de contrôle entreprise

Le centre de données virtuel Azure est une approche permettant de tirer le meilleur parti des capacités Azure tout en respectant vos stratégies de sécurité et réseau existantes. Lorsqu’ils déploient des charges de travail d’entreprise dans le cloud, les services informatiques et les unités opérationnelles doivent équilibrer la gouvernance et l’agilité des développeurs. Le centre de données virtuel Azure apporte des modèles pour atteindre cet équilibre en mettant l’accent sur la gouvernance.

## <a name="resources"></a>Ressources

<!-- markdownlint-disable MD033 -->

<table>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="https://aka.ms/VDC/Concepts"><img src="../_images/vdc/virtual-datacenter.svg" alt="Virtual Datacenter e-book" /></a></td>
    <td>
        <h3><a href="https://aka.ms/VDC/Concepts">Centre de données virtuel Azure : Concepts</a></h3>
        <p>Ce livre électronique vous explique comment déployer des charges de travail d’entreprise sur la plateforme cloud Azure tout en respectant vos stratégies de sécurité et de mise en réseau existantes.</p>
    </td>
</tr>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="./networking-vdc.md"><img src="../_images/vdc/vdc-network.png" alt="Network Perspective" /></a></td>
    <td>
        <h3><a href="./networking-vdc.md">Centre de données virtuel Azure : perspective réseau</a></h3>
        <p>Cet article en ligne fournit une vue d’ensemble des modèles et des conceptions de réseau qui permettent de balayer les inquiétudes de nombreux clients concernant la mise à l’échelle, les performances et la sécurité de l’architecture lorsque ces clients envisagent une migration massive vers le cloud.</p>
    </td>
</tr>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="https://aka.ms/VDC/Lift"><img src="../_images/vdc/vdc-lift-and-shift.png" alt="Lift and Shift Guide" /></a></td>
    <td>
        <h3><a href="https://aka.ms/VDC/Lift">Centre de données virtuel Azure : Guide lift-and-shift </a></h3>
        <p>Ce livre blanc porte sur le processus que le personnel des services informatiques et les décisionnaires de l’entreprise peuvent utiliser afin d’identifier et de planifier la migration d’applications et de serveurs vers Azure à l’aide d’une méthode « lift and shift », qui permet de réduire les coûts de développement additionnels tout en optimisant les possibilités d’hébergement cloud.</p>
    </td>
</tr>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="https://aka.ms/VDC/Deck"><img src="../_images/vdc/vdc-deck.png" alt="Presentation Deck" /></a></td>
    <td>
        <h3><a href="https://aka.ms/VDC/Deck">Centre de données virtuel Azure : jeu de présentation </a></h3>
        <p>Cette présentation propose un tour d’horizon des outils et conseils relatifs au centre de données virtuel Azure. Elle couvre les objectifs du centre de données virtuel, les motivations du client, les régions Azure, les éléments d’une automatisation du centre de données virtuel, les centres de données virtuels Azure performants et de confiance, et elle se termine par un plan d’action centré sur les instructions du directeur informatique. Des informations de support et de formation sont également fournies.</p>
    </td>
</tr>
</table>

<!-- markdownlint-enable MD033 -->

<!-- markdownlint-disable MD026 -->

## <a name="what-is-the-azure-virtual-datacenter"></a>Qu’est-ce que le centre de données virtuel Azure ?

Le déploiement des charges de travail vers le cloud crée le besoin de développer et maintenir la confiance dans le cloud au même niveau que celui que vous accordez à vos centres de données existants. Le premier modèle d’assistance en matière de centre de données virtuel Azure est conçu pour répondre à ce besoin grâce à une approche verrouillée des infrastructures virtuelles. Cette approche ne convient pas à tout le monde. Elle est spécifiquement conçue pour guider les services informatiques d’entreprise lors de l’extension de leur infrastructure locale vers le cloud public Azure. Nous appelons cette approche le modèle d’extension de centre de données de confiance. Au fil du temps, plusieurs autres modèles seront proposés, notamment des modèles autorisant l’accès sécurisé à Internet directement à partir d’un centre de données virtuel.

<!-- markdownlint-disable MD033 -->

<img src="../_images/vdc/vdc-components.svg" alt="Virtual Datacenter components" style="max-width:700px;"/>

<!-- markdownlint-enable MD033 -->

Voici les quatre composants indispensables du centre de données virtuel Azure : identité, chiffrement, SDN (Software-Defined Networking) et conformité (y compris les journaux d’activité et rapports).

Dans le modèle de centre de données virtuel Azure, vous pouvez appliquer des stratégies d’isolation, rendre le cloud plus semblable aux centres de données physiques que vous connaissez et atteindre les niveaux de sécurité et de confiance dont vous avez besoin. Quatre composants que toutes les équipes informatiques d’entreprise reconnaîtront rendent cela possible : SDN (Software-Defined Networking), le chiffrement, la gestion des identités ainsi que les standards de conformité et les certifications sous-jacentes de la plateforme Azure. Ces quatre points sont essentiels pour faire d’un centre de données virtuel une extension de confiance de vos investissements d’infrastructure existants.

Continuez à lire le livre électronique sur les [Concepts du datacenter virtuel Azure](https://azure.microsoft.com/resources/azure-virtual-datacenter).
