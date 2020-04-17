---
title: Sécuriser et gérer
description: Explorez plus en détail les méthodes de sécurité et de gestion que vous pouvez utiliser pour gérer votre environnement après avoir migré vers Azure.
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 7e9dd472d2913979211959d1f230bf4fb9c33cba
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80432932"
---
<!-- markdownlint-disable MD024 MD025 DOCSMD001 -->

# <a name="secure-and-manage"></a>Sécuriser et gérer

Après la migration de votre environnement vers Azure, il est important de prendre en compte la sécurité et les méthodes utilisées pour gérer l’environnement. Azure fournit de nombreuses fonctionnalités et capacités pour répondre à ces besoins dans votre solution.

# <a name="azure-monitor"></a>[Azure Monitor](#tab/monitor)

Azure Monitor optimise la disponibilité et les performances de vos applications en fournissant une solution complète pour collecter, analyser et agir sur les données de télémétrie de vos environnements cloud et locaux. Il vous aide à comprendre le fonctionnement de vos applications et identifie de façon proactive les problèmes qui les affectent et les ressources dont elles dépendent.

## <a name="use-and-configure-azure-monitor"></a>Utiliser et configurer Azure Monitor

1. Accédez à **Monitor** dans le Portail Azure.
2. Sélectionnez **Métriques**, **Journaux** ou **Service Health** pour des vues d’ensemble.
3. Sélectionnez l’une des insights pertinentes.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Go to Azure Monitor" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>En savoir plus

- [Vue d’ensemble d’Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview).

::: zone-end

# <a name="azure-service-health"></a>[Azure Service Health](#tab/serviceHealth)

Azure Service Health vous fournit des directives et un support personnalisés quand vous êtes confrontés à des problèmes dans le cadre des services Azure. Il peut vous avertir, vous aider à comprendre l’impact des problèmes et vous tenir informer de la résolution du problème. Il peut également vous aider à préparer une maintenance planifiée et des modifications pouvant avoir une incidence sur la disponibilité de vos ressources.

Azure Service Health inclut :

- **Azure Status :** Affichage global de l’intégrité des services Azure.
- **Service Health :** Affichage personnalisé de l’intégrité de vos services Azure.
- **Resource Health :** Affichage plus approfondi de l’intégrité des ressources individuelles configurées pour vous par vos services Azure.

Combinés, ces expériences vous offrent une vue complète de l’intégrité d’Azure, à un niveau de détails pertinent pour vous.

## <a name="access-service-health"></a>Accéder à Service Health

1. Accédez à **Monitor** dans le Portail Azure.
2. sélectionnez **Service Health**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/serviceIssues]" submitText="Go to Service Health" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez la [documentation d’Azure Service Health](https://docs.microsoft.com/azure/service-health).

::: zone-end

# <a name="azure-advisor"></a>[Azure Advisor](#tab/advisor)

Azure Advisor est un conseiller personnalisé basé dans le cloud qui décrit les meilleures pratiques à suivre pour optimiser vos déploiements Azure. Il analyse les données de télémétrie d’utilisation et la configuration de vos ressources. Il recommande ensuite des solutions pour améliorer les performances, la sécurité et la haute disponibilité de vos ressources tout en réduisant vos dépenses Azure globales.

## <a name="access-azure-advisor"></a>Accéder à Azure Advisor

1. Accédez à **Advisor** dans le Portail Azure ou recherchez la ressource.
2. Sélectionnez **Haute disponibilité**, **Sécurité**, **Niveau de performance** ou **Coût**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorMenuBlade/overview]" submitText="Go to Azure Advisor" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>En savoir plus

[Vue d’ensemble](https://docs.microsoft.com/azure/advisor/advisor-overview).

::: zone-end

# <a name="azure-security-center"></a>[Centre de sécurité Azure](#tab/security)

Azure Security Center est un système unifié de gestion de la sécurité de l’infrastructure qui renforce la posture de sécurité de vos centres de données et fournit une protection avancée contre les menaces pour vos charges de travail hybrides dans le cloud&mdash;(dans Azure ou non),&mdash;ainsi qu’en local.

## <a name="access-azure-security-center"></a>Accéder à Azure Security Center

1. Accédez à **Security Center** dans le Portail Azure ou recherchez la ressource.
2. Sélectionnez **Recommandations**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/0]" submitText="Go to Security Center" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>En savoir plus

[Vue d'ensemble](https://docs.microsoft.com/azure/security-center/security-center-intro)

::: zone-end

# <a name="azure-backup"></a>[Azure Backup](#tab/backup)

Sauvegarde Azure est le service Azure qui vous permet de sauvegarder (ou de protéger) et de restaurer vos données dans le cloud Microsoft. Sauvegarde Azure remplace votre solution actuelle de sauvegarde locale ou hors site par une solution informatique la fois fiable, sécurisée et économique.

## <a name="enable-backup-for-an-azure-vm"></a>Activer la sauvegarde pour une machine virtuelle Azure

1. Dans le portail Azure, sélectionnez **Machines virtuelles**, puis la machine virtuelle que vous souhaitez répliquer.
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

::: zone-end

# <a name="azure-site-recovery"></a>[Azure Site Recovery](#tab/siteRecovery)

Plus haut dans ce guide, nous avons abordé la manière dont Azure Site Recovery peut être utilisé dans le cadre de l’exécution de la migration. Mais le service forme également un composant essentiel dans votre stratégie de récupération d’urgence une fois la migration terminée.

Le service Azure Site Recovery vous permet de répliquer des machines virtuelles et des charges de travail hébergées dans une région Azure primaire vers une copie hébergée dans une région secondaire. Lorsqu’une panne se produit dans votre région primaire, vous pouvez basculer vers la copie en cours d’exécution dans la région secondaire et continuer à accéder à vos applications et services à partir de là. Une fois que la panne de la copie principale de votre machine virtuelle est de nouveau en cours d’exécution, vous pouvez effectuer une restauration automatique.

## <a name="replicate-an-azure-vm-to-another-region-with-site-recovery-service"></a>Répliquer une machine virtuelle Azure vers une autre région avec le service Site Recovery

Les étapes suivantes décrivent le processus d’utilisation du service Site Recovery pour répliquer une machine virtuelle Azure vers une autre région (Azure vers Azure) :

>
> [!TIP]
> Selon votre scénario, les étapes exactes peuvent différer légèrement.
>

## <a name="enable-replication-for-the-azure-vm"></a>Activer la réplication des machines virtuelles Azure

1. Dans le portail Azure, sélectionnez **Machines virtuelles**, puis la machine virtuelle que vous souhaitez répliquer.
1. Dans **Opérations**, sélectionnez **Récupération d’urgence**.
1. Dans **Configurer la récupération d’urgence** > **Région cible**, sélectionnez la région cible vers laquelle vous allez effectuer la réplication.
1. Pour ce démarrage rapide, acceptez les autres paramètres par défaut.
1. Sélectionnez **Activer la réplication**. Cette opération démarre un travail consistant à activer la réplication pour la machine virtuelle.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

## <a name="verify-settings"></a>Vérifier les paramètres

Une fois le travail de réplication terminé, vous pouvez vérifier l’état et l’intégrité de la réplication et tester le déploiement.

1. Dans le menu Machine virtuelle, sélectionnez **Récupération d’urgence**.
2. Vérifiez l’intégrité de la réplication, les points de récupération qui ont été créés ainsi que les régions sources et cibles sur la carte.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>En savoir plus

- [Vue d’ensemble d’Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)
- [Répliquer une machine virtuelle Azure vers une autre région](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

::: zone-end
