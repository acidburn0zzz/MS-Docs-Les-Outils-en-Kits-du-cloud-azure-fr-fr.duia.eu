---
title: 'SDN (Software Defined Network) : PaaS uniquement'
description: Découvrez les avantages et les limitations d’un modèle architectural PaaS uniquement dans la mise en réseau à définition logicielle (SDN) dans le cloud.
author: rotycenh
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: fd1ffbbc6ad871e2302d6e582caec7977d20a4df
ms.sourcegitcommit: 25cd1b3f218d0644f911737a6d5fd259461b2458
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80225681"
---
# <a name="software-defined-networking-paas-only"></a>SDN (Software Defined Network) : PaaS uniquement

Lorsque vous implémentez une ressource PaaS (platform as a service), le processus de déploiement crée automatiquement un réseau sous-jacent supposé, qui comprend un nombre limité de contrôles sur ce réseau. Ces contrôles incluent, entre autres, l’équilibrage de charge, le blocage des ports et les connexions à d’autres services PaaS.

Dans Azure, différents types de ressources PaaS peuvent être [déployés dans](https://docs.microsoft.com/azure/virtual-network/virtual-network-for-azure-services) ou [connectés à](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) un réseau virtuel. De cette manière, ces ressources peuvent s’intégrer à votre infrastructure existante de mise en réseau virtuelle. D'autres services, tels qu'[App Service Environment](https://docs.microsoft.com/azure/app-service/environment/intro), [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/intro-kubernetes) et [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), doivent être déployés au sein du réseau virtuel. La plupart du temps, une architecture de mise en réseau « PaaS uniquement », qui ne s’appuie que sur ces capacités de mise en réseau natives par défaut fournies par les ressources PaaS, est suffisante pour répondre aux exigences de connectivité et de gestion du trafic d’une charge de travail.

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
