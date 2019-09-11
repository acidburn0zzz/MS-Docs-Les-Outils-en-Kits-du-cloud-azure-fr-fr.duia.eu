---
title: Optimiser et transformer
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Optimiser et transformer
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: c44bcd45783ee6ea61bbbe33b6b76ce7034eca2c
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818895"
---
# <a name="optimize-and-transform"></a>Optimiser et transformer

Maintenant que vous avez migré vos services vers Azure, la phase suivante consiste à passer en revue la solution pour rechercher les domaines d’optimisation possibles. Cela peut inclure la révision de la conception de la solution, le bon dimensionnement des services et l’analyse des coûts.

Cette phase est également une opportunité d’optimiser votre environnement et d’effectuer d’éventuelles transformations de l’environnement. Par exemple, vous avez peut-être effectué une migration de type « réhébergement », et maintenant que vos services s’exécutent sur Azure, vous pouvez revisiter la configuration des solutions ou des services consommés, et éventuellement effectuer une « refactorisation » pour moderniser et augmenter les capacités de votre solution.

# <a name="right-size-assetstaboptimize"></a>[Ressources de bonne taille](#tab/optimize)

Tous les services Azure qui fournissent un modèle de coût basé sur la consommation peuvent être redimensionnés à l’aide du portail Azure, de l’interface CLI ou de PowerShell. La première étape dans le bon dimensionnement d’un service consiste à passer en revue ses métriques d’utilisation. Le service Azure Monitor permet d’accéder à ces métriques. Vous devrez peut-être configurer la collecte des métriques pour le service que vous analysez et attendre un certain temps pour collecter des données significatives en fonction de vos modèles de charge de travail.

1. Accédez à **Surveillance**.
1. Sélectionnez **Métriques**, puis configurez le graphique pour afficher les métriques du service à analyser.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/metrics]" submitText="Go to Monitor" :::

::: zone-end

Voici quelques-uns des services courants que vous pouvez redimensionner.

## <a name="resize-a-virtual-machine"></a>Redimensionner une machine virtuelle

Azure Migrate effectue une analyse de bon dimensionnement dans le cadre de la phase d’évaluation pré-migration, et les machines virtuelles migrées à l’aide de cet outil seront probablement déjà dimensionnées selon vos besoins pré-migration.

Toutefois, pour les machines virtuelles créées ou migrées à l’aide d’autres méthodes, ou dans les cas où les besoins de votre machine virtuelle doivent être ajustés après la migration, vous souhaiterez peut-être affiner le dimensionnement de votre machine virtuelle.

1. Accédez à **Machines virtuelles**.
1. Sélectionnez la machine virtuelle souhaitée dans la liste.
1. Sélectionnez **Taille** et la nouvelle taille souhaitée dans la liste. Vous devrez peut-être ajuster les filtres pour trouver la taille dont vous avez besoin.
1. Sélectionnez **Redimensionner**.

Notez que le redimensionnement des machines virtuelles de production risque de provoquer des interruptions de service. Essayez d’appliquer le bon dimensionnement pour vos machines virtuelles avant de les promouvoir en production.


::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

- [Gérer les réservations pour les ressources Azure](/azure/billing/billing-manage-reserved-vm-instance)
- [Redimensionner une machine virtuelle Windows](/azure/virtual-machines/windows/resize-vm)
- [Redimensionner une machine virtuelle Linux avec Azure CLI](/azure/virtual-machines/linux/change-vm-size)

Les partenaires peuvent utiliser l’espace partenaires pour passer en revue l’utilisation.

- [Dimensionnement des machines virtuelles Microsoft Azure pour une utilisation maximale de la réservation](/partner-center/azure-usage)

::: zone-end

## <a name="resize-a-storage-account"></a>Redimensionner un compte de stockage

1. Allez dans **Comptes de stockage**.
1. Sélectionnez le compte de stockage souhaité.
1. Sélectionnez **Configurer** et ajustez les propriétés du compte de stockage en fonction de vos besoins.
1. Sélectionnez **Enregistrer**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Storage%2FStorageAccounts]" submitText="Go to Storage Accounts" :::

::: zone-end

## <a name="resize-a-sql-database"></a>Redimensionner une base de données SQL

1. Accédez à **Bases de données SQL** ou **Serveurs SQL**, puis sélectionnez le serveur.
1. Sélectionnez la base de données souhaitée.
1. Sélectionnez **Configurer** et la nouvelle taille de niveau de service souhaitée.
1. Sélectionnez **Appliquer**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Sql%2Fservers%2Fdatabases]" submitText="Go to SQL Databases" :::

::: zone-end

# <a name="cost-managementtabmanagecost"></a>[Gestion des coûts](#tab/ManageCost)

Il est important d’effectuer une analyse et un examen des coûts récurrents. Cela vous donne la possibilité de redimensionner les ressources en fonction de vos besoins pour équilibrer les coûts et la charge de travail.

Azure Cost Management fonctionne avec Azure Advisor pour fournir des recommandations d’optimisation des coûts. Azure Advisor vous permet d’optimiser et d’améliorer l’efficacité en identifiant les ressources inactives et sous-utilisées.

1. Sélectionnez **Gestion des coûts + facturation**.
1. Sélectionnez **Recommandations du conseiller** et l’onglet **Coûts**.
1. Utilisez **Impact** et les **Économies annuelles potentielles** pour passer en revue les avantages potentiels.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/ModernBillingMenuBlade/Overview]" submitText="Go to Cost Management + Billing" :::

::: zone-end

Vous pouvez également utiliser le **Advisor** et sélectionner l'onglet **Coûts** pour identifier les recommandations pour des réductions de coûts potentielles.

> [!TIP]
> Pour les services qui ne nécessitent pas de disponibilité continue, l’implémentation d’une solution pour démarrer, arrêter ou suspendre le service en fonction des besoins peut vous aider à gérer les coûts (par exemple pour les machines virtuelles Azure ou Azure SQL Data Warehouse).
>

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorBlade]" submitText="Go to Azure Advisor" :::

::: zone-end

::: zone target="docs"

- [Tutoriel : Optimiser les coûts à partir de recommandations](/azure/cost-management/tutorial-acm-opt-recommendations)
- [Éviter les frais inattendus avec la gestion de la facturation et des coûts dans Azure](/azure/billing/billing-getting-started)
- [Explorer et analyser les coûts avec l’analyse des coûts](/azure/cost-management/quick-acm-cost-analysis)

::: zone-end
