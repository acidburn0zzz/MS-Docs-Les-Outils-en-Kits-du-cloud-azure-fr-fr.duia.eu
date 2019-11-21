---
title: 'Guide d’innovation Azure : Démocratiser les données'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Apprenez à démocratiser des données à l’aide d’Azure
author: absheik
ms.author: absheik
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 5203ae99a7cf3c5e78f72edf020234f3ea703d36
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251863"
---
::: zone target="docs"

# <a name="azure-innovation-guide-democratize-data"></a>Guide d’innovation Azure : Démocratiser les données

::: zone-end

::: zone target="chromeless"

# <a name="democratize-data"></a>Démocratiser les données

::: zone-end

L’une des premières étapes de démocratisation des données consiste à améliorer leur détectabilité. Le catalogage et la gestion du partage de données peuvent aider les entreprises à tirer le meilleur parti de leurs ressources d’informations existantes. Un catalogue de données permet aux utilisateurs qui gèrent les données de détecter et comprendre facilement les sources de données. Azure Data Catalog permet la gestion au sein d’une entreprise, tandis que Azure Data Share permet la gestion et le partage en dehors de l’entreprise.

Les services Azure qui fournissent le traitement des données, comme Azure Time Series Insights et Stream Analytics, sont d’autres fonctionnalités que les clients et partenaires exploitent avec succès pour leurs besoins en matière d’innovation.

# <a name="catalogtabcatalog"></a>[Catalogue](#tab/Catalog)

## <a name="azure-data-catalog"></a>Azure Data Catalog

Azure Data Catalog résout les problèmes de découverte des consommateurs de données en plus de permettre aux producteurs de données de gérer les ressources d’informations. Il comble l'écart entre l'informatique et l'entreprise en permettant à toute personne de transmettre ses connaissances. Vous pouvez stocker vos données à l’emplacement de votre choix et vous connecter avec les outils que vous souhaitez utiliser. Avec Azure Data Catalog, vous pouvez contrôler les personnes autorisées à détecter les actifs de données inscrits. Vous pouvez intégrer des outils et processus existants à l’aide d’API REST ouvertes.

> [!div class="checklist"]
>
> - Register
> - Rechercher et annoter
> - Connecter et gérer

::: zone target="docs"

**Accédez à la [documentation Azure Data Catalog](https://docs.microsoft.com/azure/data-catalog)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Action

Vous pouvez utiliser un seul Azure Data Catalog par organisation. Si un catalogue a déjà été créé pour votre organisation, vous ne pouvez pas en ajouter d’autres.

Pour créer un Azure Data Catalog pour votre organisation :

1. Accédez à **Azure Data Catalog**.
2. Sélectionnez **Create** (Créer).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataCatalog%2Fcatalogs]" submitText="Go to Azure Data Catalog" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="sharetabshare"></a>[Partager](#tab/Share)

## <a name="azure-data-share"></a>Azure Data Share

L’équilibre entre le partage ouvert des données et le contrôle des données partagées et avec qui elles le sont est une partie primordiale de l’innovation. Tout en s’efforçant de démocratiser les données, les organisations peuvent facilement être submergées par l’énormité du volume, du rythme et du cycle de vie de ces données. Azure Data Share permet de s’assurer que le fournisseur peut contrôler la façon dont ses données sont utilisées, en spécifiant des conditions d’utilisation. Le consommateur de données doit accepter ces conditions pour recevoir les données. Les fournisseurs de données peuvent spécifier la fréquence à laquelle les consommateurs de leurs données doivent recevoir des mises à jour. Le fournisseur de données peut à tout moment révoquer l’accès aux nouvelles mises à jour.

> [!div class="checklist"]
>
> - Créer un partage Data Share
> - Ajouter des jeux de données à votre partage Data Share
> - Activer une planification de synchronisation pour votre partage Data Share
> - Ajouter des destinataires à votre partage Data Share

::: zone target="docs"
**Accédez à la [documentation Azure Data Share](https://docs.microsoft.com/azure/data-share)**

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Pour créer un partage de données :

1. Accédez à **Azure Data Share**.
2. Sélectionnez **Créer un partage de données**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataShare%2Faccounts]" submitText="Go to Azure Data Shares" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="insightstabinsights"></a>[Insights](#tab/Insights)

## <a name="azure-time-series-insights"></a>Azure Time Series Insights

Les capacités d’innovation des données de Azure Time Series Insights sont infinies. Il permet une exploration des données en temps quasi réel des flux de données et du stockage multicouche pour les données de séries chronologiques IoT. Il offre également des modèles de séries chronologiques pour la contextualisation des données de télémétrie brutes et la dérivation d’insights basés sur les ressources. Vous pouvez bénéficier d’une intégration fluide et continue à d’autres solutions de données, fournir une analyse de la cause première et une détection des anomalies, notamment des options d’application personnalisées sur la plateforme Time Series Insights.

> [!div class="checklist"]
>
> - Planifiez votre environnement Time Series Insights.
> - Visualisez les données dans l’Explorateur.
> - Comprenez la rétention des données.
> - Développez et partagez des vues personnalisées.

::: zone target="docs"

**Accédez à la [vue d’ensemble d’Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-update-overview)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Action

Pour créer un environnement Azure Time Series Insights :

1. Accédez aux **environnements Azure Time Series Insights**.
2. Sélectionnez **Créer un environnement Time Series Insights**.
3. Pointez cet environnement vers une source d’événements, Azure IoT Hub ou Event Hub.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.TimeSeriesInsights%2Fenvironments]" submitText="Go to Azure Time Series Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
