---
title: 'SDN (Software Defined Network) : Cloud natif'
description: Utilisez Cloud Adoption Framework pour Azure afin de découvrir les réseaux virtuels cloud natifs, qui sont indispensables pour déployer des machines virtuelles dans le cloud.
author: rotycenh
ms.author: abuck
ms.date: 02/11/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: a69c196d76db7f633acdfcf0aff6ad72a11872e5
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83215022"
---
# <a name="software-defined-networking-cloud-native"></a>SDN (Software Defined Network) : Cloud natif

Un réseau virtuel cloud natif est indispensable quand il s’agit de déployer des ressources IaaS, comme des machines virtuelles, sur une plateforme cloud. L’accès à des réseaux virtuels à partir de sources externes, similaires au web, nécessite un approvisionnement explicite. Ces types de réseaux virtuels prennent en charge la création de sous-réseaux, de règles d’acheminement, de pare-feu virtuels et de dispositifs de gestion du trafic.

Un réseau virtuel natif dans le cloud ne dépend pas de ressources locales ou d’autres ressources non-cloud de votre organisation pour prendre en charge les charges de travail hébergées dans le cloud. Toutes les ressources requises sont approvisionnées soit dans le réseau virtuel, soit à l’aide d’offres PaaS gérées.

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

- [Guides du Réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm) : Les nouveaux réseaux virtuels Azure sont natifs cloud par défaut. Aidez-vous de ces guides pour planifier la conception et le déploiement de vos réseaux virtuels.
- [Limites des réseaux Azure](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits#networking-limits) : Chaque réseau virtuel et les ressources connectées existent dans un même abonnement. Ces ressources sont soumises aux limites de l’abonnement.
