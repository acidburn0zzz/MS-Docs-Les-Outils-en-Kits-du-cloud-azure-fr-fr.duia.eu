---
title: Déployer une charge de travail de base sur Azure
description: Découvrez les principaux composants de l’infrastructure cloud et les charges de travail de base, comme les applications web de base, les machines virtuelles uniques et les réseaux virtuels.
author: alexbuckgit
ms.author: abuck
ms.date: 12/31/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 34673307e33ab8ae9dad979fa3fa958c84be310c
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80997713"
---
# <a name="deploy-a-basic-workload-in-azure"></a>Déployer une charge de travail de base sur Azure

Le terme *charge de travail* est généralement défini comme une unité arbitraire de fonctionnalité, par exemple une application ou un service. Il permet d’envisager une charge de travail sous l’angle des artefacts de code qui sont déployés sur un serveur, et également sous l’angle d’autres services spécifiques à une application. Cette définition se révèle pertinente dans le cas d’une application ou d’un service local(e), mais elle mérite d’être développée pour les applications cloud.

Dans le cloud, une charge de travail englobe non seulement tous les artefacts, mais également les ressources cloud. Les ressources cloud sont ici incluses dans la définition en raison du concept appelé « infrastructure en tant que code ». Comme vous l’avez appris dans [Fonctionnement d’Azure](../../getting-started/what-is-azure.md), les ressources dans Azure sont déployées par un service d’orchestrateur. Ce service d’orchestrateur expose la fonctionnalité via une API web, laquelle peut être appelée à l’aide de plusieurs outils, tels que PowerShell, Azure CLI et le Portail Azure. Cela signifie que vous pouvez spécifier des ressources Azure dans un fichier lisible sur ordinateur qui peut être stocké en même temps que les artefacts de code associés à l’application.

Vous pouvez ainsi définir une charge de travail en termes d’artefacts de code et de ressources cloud nécessaires, ce qui vous permet d’isoler vos charges de travail. Vous pouvez isoler les charges de travail selon la façon dont les ressources sont organisées, la topologie du réseau ou d’autres attributs. L’isolation des charges de travail a pour but d’associer les ressources spécifiques d’une charge de travail à une équipe donnée, afin que cette équipe puisse gérer indépendamment tous les aspects de ces ressources. Cela permet à plusieurs équipes de partager des services de gestion de ressources dans Azure tout en évitant une suppression ou une modification involontaire des ressources d’une autre équipe.

Cette isolation permet également de favoriser ce qui est désigné sous le nom de DevOps. Le DevOps inclut les pratiques de développement logiciel couvrant le développement logiciel et les opérations informatiques décrits ci-dessus, en y ajoutant autant que possible le recours à l’automatisation. Le principe d’intégration continue/livraison continue (CI/CD) est au cœur du DevOps. L’intégration continue fait référence aux processus de génération automatisés qui sont exécutés chaque fois qu’un développeur valide une modification de code. La livraison continue renvoie à des processus automatisés qui déploient ce code sur différents environnements, par exemple un environnement de développement à des fins de test ou un environnement de production pour le déploiement final.

## <a name="basic-workload"></a>Charge de travail de base

Une *charge de travail de base* est généralement définie comme une application web unique, ou un réseau virtuel avec une machine virtuelle.

> [!NOTE]
> Ce guide ne couvre pas le développement d’applications. Pour plus d’informations sur le développement d’applications sur Azure, consultez le [Guide d’Architecture des Applications Azure](https://docs.microsoft.com/azure/architecture/guide).

Que la charge de travail soit une application web ou une machine virtuelle, chacun de ces déploiements nécessite un *groupe de ressources*. Un utilisateur autorisé à créer un groupe de ressources doit le faire avant de suivre les étapes ci-dessous.

## <a name="basic-web-application-paas"></a>Application web de base (PaaS)

Pour une application web de base, sélectionnez un des Démarrages rapides de 5 minutes à partir de la [documentation web apps](https://docs.microsoft.com/azure/app-service) et suivez les étapes.

> [!NOTE]
> Certains des guides de démarrage rapide déploieront un groupe de ressources par défaut. Dans ce cas, il n’est pas nécessaire de créer un groupe de ressources de façon explicite. Vous pouvez également déployer l’application web pour le groupe de ressources créé ci-dessus.

Une fois que vous avez déployé une charge de travail simple, vous pouvez trouver plus d’informations sur les meilleures pratiques pour le déploiement d’une [application web de base](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app) sur Azure.

## <a name="single-windows-or-linux-vm-iaas"></a>Machine virtuelle Windows ou Linux simple (IaaS)

Pour une charge de travail simple exécutable sur une machine virtuelle, la première étape consiste à déployer un réseau virtuel. Toutes les ressources IaaS (Infrastructure as a Service) dans Azure telles que les machines virtuelles, les équilibreurs de charge et les passerelles nécessitent un réseau virtuel. Une fois que vous en saurez plus sur [les réseaux virtuels Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview), suivez les étapes pour [déployer un réseau virtuel dans Azure à l’aide du portail](https://docs.microsoft.com/azure/virtual-network/quick-create-portal). Quand vous spécifiez les paramètres pour le réseau virtuel dans le portail Azure, veillez à indiquer le nom du groupe de ressources créé ci-dessus.

L’étape suivante consiste à décider s’il faut déployer une machine virtuelle simple Windows ou Linux. Pour une machine virtuelle Windows, suivez les étapes pour [déployer une machine virtuelle Windows sur Azure à l’aide du portail](https://docs.microsoft.com/azure/virtual-machines/windows/quick-create-portal). Là encore, lorsque vous spécifiez les paramètres de la machine virtuelle dans le portail Azure, spécifiez le nom du groupe de ressources créé ci-dessus.

Une fois que vous avez suivi les étapes et déployé la machine virtuelle, vous pouvez en savoir plus sur les [meilleures pratiques pour l’exécution d’une machine virtuelle Windows dans Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/single-vm). [Pour une machine virtuelle Linux, déployer une machine virtuelle Linux dans Azure à l’aide du portail](https://docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal). Vous pouvez également en apprendre davantage sur les [meilleures pratiques pour l’exécution d’une machine virtuelle Linux dans Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-linux/single-vm).

## <a name="next-steps"></a>Étapes suivantes

Consultez les [guides de décision en matière d’architecture](../../decision-guides/index.md) pour savoir comment utiliser les composants de l’infrastructure principale dans le cloud Azure.
