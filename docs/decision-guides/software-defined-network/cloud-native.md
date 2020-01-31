---
title: 'SDN (Software Defined Network) : Cloud natif'
description: Présentation des services de réseau virtuel natifs dans le cloud.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 8b5983ace8d56fa219d88e921fa6da7263d486fb
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806643"
---
# <a name="software-defined-networking-cloud-native"></a>SDN (Software Defined Network) : Cloud natif

Un réseau virtuel cloud natif est indispensable lors du déploiement de ressources IaaS telles que des machines virtuelles sur une plateforme cloud. L’accès à des réseaux virtuels à partir de sources externes, similaires au web, nécessite un approvisionnement explicite. Ces types de réseaux virtuels prennent en charge la création de sous-réseaux, de règles d’acheminement, de pare-feu virtuels et de dispositifs de gestion du trafic.

Un réseau virtuel cloud natif ne dépend pas de ressources locales ou d’autres ressources non cloud de votre organisation pour prendre en charge les charges de travail hébergées dans le cloud. Toutes les ressources requises sont approvisionnées soit dans le réseau virtuel, soit à l’aide d’offres PaaS gérées.

## <a name="cloud-native-assumptions"></a>Conditions nécessaires pour le cloud natif

Le déploiement d’un réseau virtuel cloud natif suppose ce qui suit :

- Les charges de travail que vous déployez sur le réseau virtuel ne dépendent pas d’applications ou de services qui ne sont accessibles que depuis votre réseau local. À moins de fournir des points de terminaison accessibles sur l’Internet public, les applications et services locaux hébergés en interne ne sont pas utilisables par des ressources hébergées sur une plateforme cloud.
- La gestion des identités et le contrôle d’accès de votre charge de travail dépendent des services d’identité de la plateforme cloud ou de serveurs IaaS hébergés dans votre environnement cloud. Vous n’aurez pas besoin de vous connecter directement à des services d’identité hébergés localement ou dans d’autres emplacements externes.
- Il n’est pas nécessaire que vos services d’identité prennent en charge la connexion unique (SSO) avec des annuaires locaux.

Les réseaux virtuels cloud natifs n’ont pas de dépendances externes. Ainsi, leur déploiement et leur configuration sont simples, de sorte que cette architecture constitue souvent un choix optimal à des fins expérimentales, ou pour d’autres déploiements autonomes plus petits ou à itérations rapides.

Les autres problèmes que votre équipe chargée de l’adoption du cloud doit prendre en compte lors de la discussion d’une architecture réseau virtuel native dans le cloud sont les suivants :

- Des charges de travail existantes conçues pour s’exécuter dans un centre de données local peuvent nécessiter des modifications importantes pour tirer parti de fonctionnalités cloud telles que des services de stockage ou d’authentification.
- Les réseaux cloud natifs sont gérés uniquement à l’aide des outils de gestion de plateforme cloud. Par conséquent, la gestion et la stratégie peuvent diverger au fil du temps par rapport aux normes informatiques existantes.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les réseaux virtuels cloud natifs sur la plateforme Azure, consultez :

- [Réseau virtuel Azure : guides pratiques](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm). Les réseaux virtuels Azure nouvellement créés sont natifs du cloud par défaut. Aidez-vous de ces guides pour planifier la conception et le déploiement de vos réseaux virtuels.
- [Limites d’abonnement : Mise en réseau](https://docs.microsoft.com/azure/azure-subscription-service-limits?toc=/azure/virtual-network/toc.json#networking-limits). Un réseau virtuel et des ressources connectées ne peuvent exister que dans un abonnement unique, et sont liés par des limites d’abonnement.
