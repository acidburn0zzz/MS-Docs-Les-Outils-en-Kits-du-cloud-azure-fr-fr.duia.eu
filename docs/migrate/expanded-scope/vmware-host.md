---
title: Accélérer la migration grâce aux hôtes VMWare
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Accélérer la migration grâce aux hôtes VMWare
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 66a39d53adeaf73e96cf04bdc5f80fc9574b675a
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72980205"
---
# <a name="accelerate-migration-with-vmware-hosts"></a>Accélérer la migration grâce aux hôtes VMWare

La migration d’hôtes VMWare entiers permet de déplacer plusieurs charges de travail et plusieurs ressources en une seule migration. Les conseils suivants développent le contenu du guide de migration [Azure](../azure-migration-guide/index.md) pour traiter la migration d’hôte VMWare. La majeure partie des efforts requis ici se déroulent pendant l’établissement des conditions préalables, mais aussi pendant les processus de migration d’un effort de migration.

## <a name="suggested-prerequisites"></a>Prérequis suggérés

Lors de la migration de votre premier hôte VMWare vers Azure, vous devez remplir un certain nombre de conditions préalables pour préparer l’identité, le réseau et les exigences de gestion. Une fois ces conditions préalables remplies, chaque hôte supplémentaire devrait nécessiter beaucoup moins d’efforts pour migrer. Les sections suivantes décrivent plus en détail ces conditions préalables.

### <a name="secure-your-azure-environment"></a>Sécuriser votre environnement Azure

Implémentez la solution cloud appropriée pour la connectivité Contrôle d'accès en fonction du rôle et Réseau dans votre environnement Azure. Le guide sur la [sécurisation de votre environnement](https://docs.microsoft.com/azure/vmware-cloudsimple/private-cloud-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) peut vous aider lors de cette implémentation.

### <a name="private-cloud-management"></a>Gestion de cloud privé

L’établissement de la gestion du cloud privé passe par 2 tâches obligatoires et une tâche facultative. Nous vous recommandons d’[élever les privilèges](https://docs.microsoft.com/azure/vmware-cloudsimple/escalate-privileges?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) et de [configurer les applications et les charges de travail DNS et DHCP](https://docs.microsoft.com/azure/vmware-cloudsimple/dns-dhcp-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) de vos clouds privés.

Nous vous recommandons aussi de [migrer des charges de travail à l’aide de réseaux étendus de couche 2](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-layer-2-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json).

### <a name="private-cloud-networking"></a>Réseau de cloud privé

Une fois les exigences de gestion établies, vous pouvez procéder à la mise en réseau de votre cloud privé en suivant ces procédures recommandées :

- [Connexion VPN à un cloud privé](https://docs.microsoft.com/azure/vmware-cloudsimple/set-up-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connexion au réseau local avec ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connexion au réseau virtuel Azure avec ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/azure-expressroute-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurer la résolution de noms DNS](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-dns-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

### <a name="integration-with-the-cloud-adoption-plan"></a>Intégration au plan d’adoption du cloud

Une fois que vous avez rempli les autres conditions préalables, vous devez inclure chaque hôte VMWare dans le [plan d’adoption du Cloud](../../plan/template.md). Dans le plan d’adoption du cloud, ajoutez chaque hôte à migrer en tant que [charge de travail distincte](../../plan/workloads.md). Au sein de chaque charge de travail, ajoutez les machines virtuelles à migrer sous forme de [ressources](../../plan/workloads.md). Pour ajouter en masse des charges de travail et des ressources au plan d’adoption, veuillez consulter l’article [Ajouter/modifier des éléments de travail avec Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="migrate-process-changes"></a>Migrer les changements de processus

Au cours de chaque itération, l’équipe chargée de l’adoption traite le backlog afin de migrer les charges de travail ayant la priorité la plus élevée. Le processus ne change pas énormément pour les hôtes VMWare. Lorsque la prochaine charge de travail du backlog est un hôte VMWare, la seule différence est l’outil utilisé.

Vous pouvez utiliser les outils suivants dans l’effort de migration :

- [Outils VMWare natifs](https://docs.microsoft.com/azure/vmware-cloudsimple/migrate-workloads?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Azure Data Box](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-using-azure-data-box?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

Sinon, vous pouvez migrer les charges de travail par le biais d’un basculement de récupération d’urgence en utilisant ces ressources :

- [Sauvegarder des machines virtuelles de charge de travail](https://docs.microsoft.com/azure/vmware-cloudsimple/backup-workloads-veeam?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurer un cloud privé en tant que site de récupération d’urgence à l’aide de Zerto](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-zerto?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurer un cloud privé en tant que site de reprise d’activité avec VMware SRM](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-site-recovery-manager?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

## <a name="next-steps"></a>Étapes suivantes

Revenez à la check-list d’expansion d’étendue pour vous assurer que votre méthode de migration est entièrement alignée.

> [!div class="nextstepaction"]
> [Check-list d’expansion d’étendue](./index.md)
