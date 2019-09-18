---
title: 'Software Defined Networking : Zone DMZ cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Cette architecture réseau permet un accès limité entre vos réseaux locaux et ceux basés sur le cloud.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 6dfee69d20afac27c735f2ff77abbadc2816ca26
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70837503"
---
# <a name="software-defined-networking-cloud-dmz"></a>Software Defined Networking : Zone DMZ cloud

L’architecture de réseau DMZ cloud permet un accès limité entre vos réseaux locaux et ceux basés sur le cloud en utilisant un réseau privé virtuel (VPN) pour les connecter. Bien que le modèle DMZ soit couramment utilisé lorsque vous souhaitez sécuriser l’accès externe à un réseau, l’architecture DMZ cloud présentée ici est spécifiquement conçue pour assurer la sécurité de l’accès au réseau local à partir de ressources cloud et inversement.

![Architecture réseau hybride sécurisée](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/images/dmz-private.png)

Cette architecture est conçue pour prendre en charge les scénarios dans lesquels votre organisation souhaite commencer à intégrer les charges de travail basées sur le cloud avec celles en local, mais qu’elle ne dispose pas de stratégies de sécurité cloud suffisamment matures ou qu’elle n’a pas acquis de connexion WAN dédiée sécurisée entre les deux environnements. Par conséquent, les réseaux cloud doivent être traités en tant que zone démilitarisée (DMZ) afin de garantir la sécurité des services locaux.

La DMZ déploie des appliances virtuelles réseau (NVA) pour implémenter des fonctionnalités de sécurité telles que des pare-feu et l’inspection des paquets. Le trafic circulant entre les services et applications basés sur le cloud et ceux en local doit passer par la DMZ où il est audité. Les connexions VPN et les règles qui autorisent le trafic via le réseau DMZ sont strictement contrôlées par les équipes de sécurité informatique.

## <a name="cloud-dmz-assumptions"></a>Hypothèses relatives à la zone démilitarisée cloud

Le déploiement d’une zone DMZ cloud comprend les hypothèses suivantes :

- Vos équipes de sécurité n’ont pas complètement aligné les exigences et les stratégies de sécurité locales et celles basées sur le cloud.
- Vos charges de travail cloud nécessitent un accès à un sous-ensemble réduit de services hébergés sur vos réseaux locaux ou tiers ou vos utilisateurs ou applications locaux doivent bénéficier d’un accès réduit aux ressources hébergées dans le cloud.
- L’implémentation d’une connexion VPN entre vos réseaux locaux et le fournisseur de cloud n’est pas empêchée par une stratégie d’entreprise, des exigences réglementaires ou des problèmes de compatibilité technique.
- Vos charges de travail ne nécessitent pas plusieurs abonnements pour contourner les limites de ressources d’abonnement, ou elles impliquent plusieurs abonnements mais ne nécessitent pas de gestion centrale de la connectivité ou des services partagés utilisés par les ressources réparties sur plusieurs abonnements.

Lors de l’examen de l’implémentation d’une architecture de réseau virtuel DMZ cloud, votre équipe chargée de l’adoption du cloud doit prendre en compte les problèmes suivants :

- La connexion de réseaux locaux avec des réseaux cloud augmente la complexité de vos exigences de sécurité. Même si les connexions entre les réseaux cloud et l’environnement local sont sécurisées, vous devez toujours veiller à la sécurité des ressources cloud. Toutes les adresses IP publiques créées pour accéder aux charges de travail basées dans le cloud doivent être correctement sécurisées à l’aide d’une [zone DMZ publique](/azure/architecture/reference-architectures/dmz/secure-vnet-dmz) ou d’un [pare-feu Azure](/azure/firewall).
- L’architecture DMZ cloud sert souvent de tremplin, pendant que la sécurité de la connectivité est renforcée et que la stratégie de sécurité est alignée entre les réseaux locaux et cloud, ce qui permet une plus large adoption de l’architecture de mise en réseau hybride à grande échelle. Toutefois, elle peut également s’appliquer aux déploiements isolés avec des besoins spécifiques en matière de sécurité, d’identité et de connectivité que satisfait l’approche DMZ cloud.

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations sur l’implémentation d’une zone DMZ cloud, consultez :

- [Implémenter une zone DMZ entre Azure et votre centre de données local](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid). Cet article explique comment implémenter une architecture réseau hybride sécurisée dans Azure.
