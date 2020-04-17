---
title: Protéger et récupérer dans Azure
description: Découvrez comment garantir la stabilité de l’entreprise en réduisant le délai de reprise et la probabilité d’une interruption de l’activité.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: f4b6b2d5d944e3176b2f36ef713955a4c29324f9
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80426570"
---
<!-- cSpell:ignore siterecovery -->

# <a name="protect-and-recover-in-azure"></a>Protéger et récupérer dans Azure

_Protéger et récupérer_ constituent la troisième et dernière discipline de toute ligne de base de gestion cloud.

![Base de référence de gestion cloud](../../_images/manage/management-baseline.png)

Dans [Conformité opérationnelle dans Azure](./operational-compliance.md), l’objectif est de réduire la probabilité d’une interruption d’activité. Cet article actuel vise à réduire la durée et l’impact des pannes qui ne peuvent pas être évitées.

Dans le cas d’un environnement d’entreprise, ce tableau présente le minimum suggéré pour toute ligne de base de gestion :

|Process  |Outil  |Objectif  |
|---------|---------|---------|
|Protection des données|Sauvegarde Azure|Sauvegardez des données et des machines virtuelles dans le cloud.|
|Protéger l'environnement|Azure Security Center|Renforcer la sécurité et fournir une protection avancée contre les menaces pour vos charges de travail hybrides.|

::: zone target="docs"

## <a name="azure-backup"></a>Sauvegarde Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-backup"></a>[Azure Backup](#tab/AzureBackup)

::: zone-end

Sauvegarde Azure vous permet de sauvegarder, protéger et récupérer vos données dans le cloud Microsoft. Sauvegarde Azure remplace votre solution de sauvegarde locale ou hors site existante par une solution informatique. Cette nouvelle solution est fiable, sécurisée et économique. Sauvegarde Azure peut également être utilisé pour protéger et récupérer des ressources locales via une solution cohérente.

### <a name="enable-backup-for-an-azure-vm"></a>Activer la sauvegarde pour une machine virtuelle Azure

1. Dans le portail Azure, sélectionnez **Machines virtuelles**, puis la machine virtuelle que vous souhaitez répliquer.
1. Dans le volet **Opérations**, sélectionnez **Sauvegarde**.
1. Créez ou sélectionnez un coffre Recovery Services Azure existant.
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

## <a name="azure-site-recovery"></a>[Azure Site Recovery](#tab/siterecovery)

::: zone-end

Azure Site Recovery est un composant essentiel de votre stratégie de récupération d’urgence.

Site Recovery réplique les machines virtuelles et les charges de travail hébergées dans une région Azure primaire. Il les réplique vers une copie hébergée dans une région secondaire. Lorsqu’une panne se produit dans votre région primaire, vous basculez vers la copie en cours d’exécution dans la région secondaire. Vous accédez toujours à vos applications et services à partir de là. Cette approche proactive de la récupération peut réduire de manière significative les temps de récupération. Lorsque l’environnement de récupération n’est plus nécessaire, le trafic de production peut revenir à l’environnement d’origine.

### <a name="replicate-an-azure-vm-to-another-region-with-site-recovery"></a>Répliquer une machine virtuelle Azure vers une autre région avec Site Recovery

Les étapes suivantes décrivent le processus d’utilisation de Site Recovery pour une réplication Azure-to-Azure, c’est-à-dire, une réplication d’une machine virtuelle Azure vers une autre région.
>
> [!TIP]
> Selon votre scénario, les étapes exactes peuvent différer légèrement.
>

### <a name="enable-replication-for-the-azure-vm"></a>Activer la réplication des machines virtuelles Azure

1. Dans le portail Azure, sélectionnez **Machines virtuelles**, puis la machine virtuelle que vous souhaitez répliquer.
1. Dans le volet **Opérations**, sélectionnez **Récupération d’urgence**.
1. Sélectionnez **Configurer la récupération d’urgence** > **Région cible** et choisissez la région cible vers laquelle vous allez effectuer la réplication.
1. Pour ce démarrage rapide, acceptez les valeurs par défaut pour toutes les autres options.
1. Sélectionnez **Activer la réplication**, démarrant un travail permettant la réplication pour la machine virtuelle.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="verify-settings"></a>Vérifier les paramètres

Une fois le travail de réplication terminé, vous pouvez vérifier l’état et l’intégrité de la réplication et tester le déploiement.

1. Dans le menu Machine virtuelle, sélectionnez **Récupération d’urgence**.
1. Vérifiez l’intégrité de la réplication, les points de récupération qui ont été créés ainsi que les régions sources et cibles sur la carte.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="learn-more"></a>En savoir plus

- [Vue d’ensemble d’Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)
- [Répliquer une machine virtuelle Azure vers une autre région](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)
