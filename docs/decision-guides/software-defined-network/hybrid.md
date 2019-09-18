---
title: 'Software Defined Networking : Réseau hybride'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Discussion sur la manière dont des réseaux hybrides permettent à vos réseaux virtuels dans le cloud de se connecter à des ressources locales.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 94e285f59442b6632209e1cd6a76c39cfccd337b
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70837855"
---
# <a name="software-defined-networking-hybrid-network"></a>Software Defined Networking : Réseau hybride

L’architecture réseau cloud hybride permet aux réseaux virtuels d’accéder à vos ressources et services locaux, et inversement, en utilisant une connexion WAN dédiée telle qu’ExpressRoute ou une autre méthode de connexion permettant de connecter directement les réseaux.

![Réseau hybride](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/images/expressroute.png)

S’appuyant sur l’architecture réseau virtuel native du cloud, un réseau virtuel hybride est isolé lors de sa création. L’ajout de connectivité à l’environnement locale ouvre l’accès au réseau local et à partir de celui-ci. Cependant, tous les autres ressources ciblant le trafic entrant dans le réseau virtuel doivent être autorisées explicitement. Vous pouvez sécuriser la connexion à l’aide de dispositifs de pare-feu virtuel et de règles d’acheminement pour limiter l’accès, ou spécifier les services accessibles entre les deux réseaux en utilisant des fonctionnalités de routage natif cloud ou en déployant des appliances virtuelles réseau pour gérer le trafic.

Bien que l’architecture réseau hybride prenne en charge les connexions VPN, des connexions WAN dédiées telles qu’ExpressRoute sont favorisées en raison de leurs performances supérieures et de leur sécurité accrue.

## <a name="hybrid-assumptions"></a>Postulats concernant le caractère hybride

Le déploiement d’un réseau virtuel hybride reprend les hypothèses suivantes :

- Vos équipes de sécurité informatique ont harmonisé les stratégies de sécurité réseau locale et cloud pour s’assurer que des réseaux virtuels cloud puissent être approuvés pour communiquer directement avec des systèmes locaux.
- Vos charges de travail cloud nécessitent un accès au stockage, aux applications et aux services hébergés sur vos réseaux locaux ou tiers, ou vos utilisateurs ou applications locaux doivent avoir accès aux ressources hébergées dans le cloud.
- Vous devez migrer les applications et services existants qui dépendent de ressources locales, mais vous ne voulez pas utiliser les ressources en redéveloppement pour supprimer ces dépendances.
- La connexion de vos réseaux locaux à des ressources cloud sur un réseau VPN ou un réseau étendu dédié n’est pas bloquée par la stratégie d’entreprise, les exigences en matière de souveraineté des données ou d’autres problèmes de conformité réglementaire.
- Vos charges de travail ne nécessitent pas plusieurs abonnements pour contourner les limites de ressources d’abonnement, OU vos charges de travail impliquent plusieurs abonnements, mais ne nécessitent pas de gestion centrale de la connectivité ou des services partagés utilisés par des ressources réparties sur plusieurs abonnements.

Lors de l’examen de l’implémentation d’une architecture de réseau virtuel hybride, vos équipes chargées de l’adoption du cloud doivent prendre en compte les problèmes suivants :

- La connexion de réseaux locaux avec des réseaux cloud augmente la complexité de vos exigences de sécurité. Les deux réseaux doivent être protégés contre les vulnérabilités externes et les accès non autorisés des deux côtés de l’environnement hybride.
- Une mise à l’échelle du nombre et de la taille des charges de travail à l’intérieur d’un environnement cloud hybride peut ajouter une complexité considérable à la gestion du routage et du trafic.
- Vous devez développer des stratégies de gestion et de contrôle d’accès compatibles pour maintenir la cohérence de la gouvernance dans l’ensemble de votre organisation.

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations sur les réseaux hybrides dans Azure, consultez :

- [Architecture de référence de réseau hybride](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/expressroute). Les réseaux virtuels hybrides Azure utilisent un circuit ExpressRoute ou un VPN Azure pour connecter votre réseau virtuel aux ressources informatiques non hébergées dans Azure de votre organisation. Cet article décrit les options pour la création d’un réseau hybride dans Azure.
