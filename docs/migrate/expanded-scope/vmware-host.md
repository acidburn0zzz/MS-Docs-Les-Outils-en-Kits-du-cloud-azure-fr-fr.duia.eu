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
ms.openlocfilehash: b09c1dcbb36e5f630ca0ae86c95c5c874e29d60b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558607"
---
# <a name="accelerate-migration-with-vmware-hosts"></a>Accélérer la migration grâce aux hôtes VMWare

La migration d’hôtes VMWare entiers permet de déplacer plusieurs charges de travail et plusieurs ressources en une seule migration. Les conseils suivants développent le contenu du guide de migration [Azure](../azure-migration-guide/index.md) pour traiter la migration d’hôte VMWare.

## <a name="general-scope-expansion"></a>Expansion de l’étendue générale

La majeure partie des efforts requis ici se dérouleront pendant l’établissement des conditions préalables, mais aussi pendant les processus de migration d’un effort de migration.

## <a name="suggested-prerequisites"></a>Prérequis suggérés

Lors de la migration de votre premier hôte VMWare vers Azure, un certain nombre de conditions préalables doivent être remplies pour préparer l’identité, le réseau et les exigences de gestion. Une fois ces conditions préalables remplies, chaque hôte supplémentaire devrait nécessiter beaucoup moins d’efforts pour migrer. Ces conditions préalables s’alignent sur quelques efforts clés : sécuriser votre environnement Azure, mais aussi gérer et mettre en réseau votre cloud privé.

### <a name="secure-your-azure-environment"></a>Sécuriser votre environnement Azure

Implémentez la solution cloud appropriée pour la connectivité RBAC et Réseau dans votre environnement Azure. Le guide sur la [sécurisation de votre environnement](https://docs.microsoft.com/azure/vmware-cloudsimple/private-cloud-secure.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) peut vous aider lors de cette implémentation.

### <a name="private-cloud-management"></a>Gestion de cloud privé

L’établissement de la gestion du cloud privé passe par 2 tâches obligatoires et une tâche facultative. Nous vous recommandons d’[élever les privilèges](https://docs.microsoft.com/azure/vmware-cloudsimple/escalate-privileges.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) et de [configurer les applications et les charges de travail DNS et DHCP](https://docs.microsoft.com/azure/vmware-cloudsimple/dns-dhcp-setup.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) de vos clouds privés.

Nous vous recommandons aussi de [migrer des charges de travail à l’aide de réseaux étendus de couche 2](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-layer-2-vpn.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json).

### <a name="private-cloud-networking"></a>Mise en réseau de cloud privé

Une fois les exigences de gestion établies, vous pouvez procéder à la mise en réseau de votre cloud privé en suivant ces procédures recommandées :

- [Connexion VPN à un cloud privé](https://docs.microsoft.com/azure/vmware-cloudsimple/set-up-vpn.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connexion au réseau local avec ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-connection.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Connexion au réseau virtuel Azure avec ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/azure-expressroute-connection.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurer la résolution de noms DNS](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-dns-setup.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

### <a name="integration-with-the-cloud-adoption-plan"></a>Intégration au plan d’adoption du cloud

Une fois les conditions préalables remplies, chaque hôte VMWare sera inclus dans le [plan d’adoption du cloud ](../../plan/template.md). Dans le plan d’adoption du cloud, ajoutez chaque hôte à migrer en tant que [charge de travail distincte](../../plan/workloads.md). Au sein de chaque charge de travail, les machines virtuelles à migrer peuvent être ajoutées sous forme de [ressources](../../plan/workloads.md). Pour ajouter en masse des charges de travail et des ressources au plan d’adoption, veuillez consulter l’article [Ajouter/modifier des éléments de travail avec Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="migrate-process-changes"></a>Migrer les changements de processus

Au cours de chaque itération, l’équipe chargée de l’adoption traite le backlog afin de migrer les charges de travail ayant la priorité la plus élevée. Le processus ne change pas énormément pour les hôtes VMWare. Lorsque la prochaine charge de travail du backlog est un hôte VMWare, la seule différence est l’outil utilisé.

### <a name="suggested-action-during-the-migrate-process"></a>Action suggérée pendant le processus de migration

Voici quelques exemples d’outils qui peuvent être utilisés dans l’effort de migration :

- [Outils VMWare natifs](https://docs.microsoft.com/azure/vmware-cloudsimple/migrate-workloads.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Azure Data Box](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-using-azure-data-box.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

Sinon, vous pouvez migrer les charges de travail par le biais d’un basculement de récupération d’urgence en utilisant ces ressources :

- [Sauvegarder des machines virtuelles de charge de travail](https://docs.microsoft.com/azure/vmware-cloudsimple/backup-workloads-veeam.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurer un cloud privé en tant que site de récupération d’urgence à l’aide de Zerto](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-zerto.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurer un cloud privé en tant que site de reprise d’activité avec VMware SRM](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-site-recovery-manager.md?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

## <a name="next-steps"></a>Étapes suivantes

Revenez à la [check-list d’expansion d’étendue](./index.md) pour vous assurer que votre méthode de migration est entièrement alignée.

> [!div class="nextstepaction"]
> [Check-list d’expansion d’étendue](./index.md)
