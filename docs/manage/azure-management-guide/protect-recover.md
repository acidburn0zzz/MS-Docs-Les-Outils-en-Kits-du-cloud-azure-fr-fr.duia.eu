---
title: Protéger et récupérer dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Garantir la stabilité de l’entreprise en diminuant le temps de récupération
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: a79164435772f571849d0a836f43b53ce3bca087
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557004"
---
# <a name="protect-and-recover-in-azure"></a>Protéger et récupérer dans Azure

La protection et la récupération constituent la troisième et dernière discipline dans toute ligne de base de gestion cloud.

![Base de référence de gestion cloud](../../_images/manage/management-baseline.png)

Dans le dernier article « Conformité opérationnelle », l’objectif est de réduire la probabilité d’une interruption d’activité. Cet article « Protéger et récupérer » vise à réduire la durée et l’impact des pannes qui ne peuvent pas être évitées.

Dans le cas d’un environnement d’entreprise, le tableau suivant présente le minimum suggéré pour toute base de référence de gestion.

|Process  |Outil  |Objectif  |
|---------|---------|---------|
|Protection des données|Sauvegarde Azure|Sauvegarder des données et des machines virtuelles dans le cloud|
|Protéger l'environnement|Azure Security Center|

::: zone target="docs"

## <a name="azure-backup"></a>Sauvegarde Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-backuptabupdbackupatemanagement"></a>[Sauvegarde Azure](#tab/UpdbackupateManagement)

::: zone-end

Sauvegarde Azure est le service Azure qui vous permet de sauvegarder (ou de protéger) et de récupérer vos données dans le cloud Microsoft. Sauvegarde Azure remplace votre solution actuelle de sauvegarde locale ou hors site par une solution informatique la fois fiable, sécurisée et économique. Il peut également être utilisé pour protéger et récupérer des ressources locales via une solution cohérente.

### <a name="enable-backup-for-an-azure-vm"></a>Activer la sauvegarde pour une machine virtuelle Azure

1. Dans le Portail Azure, sélectionnez **Machines virtuelles**, puis la machine virtuelle que vous souhaitez répliquer.
1. Dans **Opérations**, sélectionnez **Sauvegarde**.
1. Créez un coffre Recovery Services ou sélectionnez-en un existant.
1. Sélectionnez **Créer (ou modifier) une nouvelle stratégie**.
1. Configurez la planification et la période de rétention.
1. Sélectionnez **OK**.
1. Sélectionnez **Activer la Sauvegarde Azure**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

[Vue d'ensemble](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup)

## <a name="azure-site-recovery"></a>Azure Site Recovery

::: zone-end
::: zone target="chromeless"

## <a name="azure-site-recoverytabsiterecovery"></a>[Azure Site Recovery](#tab/siterecovery)

::: zone-end

Azure Site Recovery est un composant essentiel de votre stratégie de récupération d’urgence.

Le service Azure Site Recovery vous permet de répliquer des machines virtuelles et des charges de travail hébergées dans une région Azure primaire vers une copie hébergée dans une région secondaire. Lorsqu’une panne se produit dans votre région primaire, vous pouvez basculer vers la copie en cours d’exécution dans la région secondaire et continuer à accéder à vos applications et services à partir de là. Cette approche proactive de la récupération peut réduire de manière significative les temps de récupération. Lorsque l’environnement de récupération n’est plus nécessaire, le trafic de production peut revenir à l’environnement d’origine.

### <a name="replicate-an-azure-vm-to-another-region-with-site-recovery-service"></a>Répliquer une machine virtuelle Azure vers une autre région avec le service Site Recovery

Les étapes suivantes décrivent le processus d’utilisation du service Site Recovery pour répliquer une machine virtuelle Azure vers une autre région (Azure vers Azure) :

>
> [!TIP]
> Selon votre scénario, les étapes exactes peuvent différer légèrement.
>

### <a name="enable-replication-for-the-azure-vm"></a>Activer la réplication des machines virtuelles Azure

1. Dans le Portail Azure, sélectionnez **Machines virtuelles**, puis la machine virtuelle que vous souhaitez répliquer.
1. Dans **Opérations**, sélectionnez **Récupération d’urgence**.
1. Dans **Configurer la récupération d’urgence** > **Région cible**, sélectionnez la région cible vers laquelle vous allez effectuer la réplication.
1. Pour ce démarrage rapide, acceptez les autres paramètres par défaut.
1. Sélectionnez **Activer la réplication**, démarrant un travail permettant la réplication pour la machine virtuelle.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="verify-settings"></a>Vérifier les paramètres

Une fois le travail de réplication terminé, vous pouvez vérifier l’état et l’intégrité de la réplication et tester le déploiement.

1. Dans le menu Machine virtuelle, sélectionnez **Récupération d’urgence**.
2. Vérifiez l’intégrité de la réplication, les points de récupération qui ont été créés ainsi que les régions sources et cibles sur la carte.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="learn-more"></a>En savoir plus

- [Vue d’ensemble d’Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)
- [Répliquer une machine virtuelle Azure vers une autre région](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)
