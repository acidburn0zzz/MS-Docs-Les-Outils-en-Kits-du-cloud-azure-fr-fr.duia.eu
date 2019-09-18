---
title: 'Software Defined Networking : PaaS uniquement'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Discussion à propos du modèle « PaaS uniquement » pour le Software Defined Networking dans le cloud.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 704dbb16be57c4203199ca972aa61b520eece3ca
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71023541"
---
# <a name="software-defined-networking-paas-only"></a>Software Defined Networking : PaaS uniquement

Lorsque vous implémentez une ressource PaaS (platform as a service), le processus de déploiement crée automatiquement un réseau sous-jacent supposé, qui comprend un nombre limité de contrôles sur ce réseau. Ces contrôles incluent, entre autres, l’équilibrage de charge, le blocage des ports et les connexions à d’autres services PaaS.

Dans Azure, différents types de ressources PaaS peuvent être [déployés dans](https://docs.microsoft.com/azure/virtual-network/virtual-network-for-azure-services) ou [connectés à](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) un réseau virtuel. De cette manière, ces ressources peuvent s’intégrer à votre infrastructure existante de mise en réseau virtuelle. D’autres services, tels qu’[App Service Environment](https://docs.microsoft.com/azure/app-service/environment/intro), [Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/intro-kubernetes), et [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), doivent être déployés au sein du réseau virtuel. La plupart du temps, une architecture de mise en réseau « PaaS uniquement », qui ne s’appuie que sur ces capacités de mise en réseau natives par défaut fournies par les ressources PaaS, est suffisante pour répondre aux exigences de connectivité et de gestion du trafic d’une charge de travail.

Si vous envisagez d’utiliser une architecture de mise en réseau « PaaS uniquement », vérifiez bien que les postulats requis s’alignent sur vos exigences.

## <a name="paas-only-assumptions"></a>Postulats concernant « PaaS uniquement »

Les postulats suivants sont admis lorsque l’on déploie une architecture de mise en réseau « PaaS uniquement » :

- L’application déployée est une application autonome ou dépendante d’autres ressources PaaS uniquement nécessitant pas de réseau virtuel.
- L’équipe qui s’occupe des opérations informatiques peut mettre à jour les outils, les formations et les processus afin de prendre en charge la gestion, la configuration et le déploiement d’applications PaaS autonomes.
- L’application PaaS ne fait pas partie d’un effort de migration cloud plus large incluant des ressources IaaS.

Ces postulats sont des qualificateurs minimaux qui s’alignent sur le déploiement d’un réseau « PaaS uniquement ». Bien que cette approche soit conforme aux exigences d’un déploiement pour une seule application, chaque équipe d’adoption du cloud doit réfléchir aux questions suivantes portant sur le long terme :

- L’échelle ou la portée de ce déploiement s’étendra-t-elle et demandera-t-elle d’avoir accès à des ressources non PaaS ?
- En plus de la solution actuelle, d’autres déploiements PaaS sont-ils prévus ?
- L’organisation a-t-elle planifié d’autres migrations cloud à l’avenir ?

Les réponses à ces questions ne doivent pas empêcher une équipe de choisir une solution « PaaS uniquement », mais doivent être prises en compte avant de prendre une décision finale.
