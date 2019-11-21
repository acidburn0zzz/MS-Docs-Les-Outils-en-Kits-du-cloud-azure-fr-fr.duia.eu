---
title: 'Guide d’innovation Azure : Prédire et influencer'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Apprenez à prédire et influencer à l’aide d’Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 506387c87a714964692dde7c082fa31c981b0c6f
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251832"
---
::: zone target="docs"

# <a name="azure-innovation-guide-predict-and-influence"></a>Guide d’innovation Azure : Prédire et influencer

::: zone-end

::: zone target="chromeless"

# <a name="predict-and-influence"></a>Prédire et influencer

::: zone-end

En tant que pionnier, votre entreprise a un aperçu des données, du comportement et des besoins de sa clientèle. L’étude de ces informations peut vous aider à prédire les besoins de vos clients, éventuellement avant qu’ils n’en soit eux-même conscients. Cet article présente quelques approches permettant de fournir des solutions prédictives. Dans la section finale, l’article présente des approches pour intégrer les prédictions à votre solution afin d’influencer les comportements des clients.

Le tableau suivant peut vous aider à trouver la meilleure solution, en fonction de vos besoins d’implémentation.

|Service  |Modèles prédéfinis  |Créer et expérimenter  |Apprendre et créer avec Python|Compétences requises|
|---------|---------|---------|---------|---------|
|Azure Cognitive Services|OUI|Non|Non|Compétences des développeurs et des API|
|Azure Machine Learning Studio|OUI|OUI|Non|Compréhension générale des algorithmes prédictifs|
|Service Azure Machine Learning|OUI|OUI|OUI|Scientifique des données|

## <a name="azure-cognitive-servicestabcognitiveservices"></a>[Azure Cognitive Services](#tab/CognitiveServices)

La voie la plus rapide et la plus simple pour prédire les besoins des clients est Azure Cognitive Services. Cognitive Services permet d’effectuer des prédictions basées sur des modèles existants, ne nécessitant aucune formation supplémentaire. Ces services sont optimaux et efficaces lorsqu’il n’y a aucun spécialiste des données au sein du personnel pour effectuer l’apprentissage du modèle prédictif. Pour certains services, aucune formation n’est requise. D’autres nécessitent uniquement une formation minimale.

Pour obtenir la liste des services disponibles et connaître la quantité d’apprentissage pouvant être nécessaire, consultez [Cognitive Services et Machine Learning](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-and-machine-learning#service-requirements-for-the-data-model).

### <a name="action"></a>Action

Pour utiliser une API Cognitive Services :

1. Dans le [Portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts), accédez à **Cognitive Services**.
2. Sélectionnez **Ajouter** pour trouver une API Cognitive Services dans la Place de marché Azure.
3. Effectuez l’une des actions suivantes :
   - Si vous connaissez le nom du service que vous souhaitez utiliser, saisissez-le dans la zone **Rechercher dans la Place de marché**.
   - Pour obtenir la liste des API Cognitive Services, cliquez sur le lien **Afficher plus** à côté du titre Cognitive Services.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Accédez directement à Cognitive Services dans le [portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts).

::: zone-end

## <a name="azure-machine-learning-studiotabmachinelearningstudio"></a>[Azure Machine Learning Studio](#tab/MachineLearningStudio)

Si les modèles existants dans Cognitive Services ne sont pas alignés sur votre prédiction souhaitée, Azure Machine Learning Studio peut offrir un moyen de créer les prédictions souhaitées, sans nécessiter les compétences d’un scientifique des données.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Vous pouvez utiliser Azure Machine Learning Studio pour créer un modèle et l’expérimenter en procédant comme suit :

1. Dans le [Portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces), accéder à **Azure Machine Learning Studio**.
2. Sélectionnez **Créer un espace de travail Machine Learning Studio**, puis suivez les invites pour créer un espace de travail.

   Le nouvel espace de travail fournit une interface de glisser-déplacer pour créer un modèle et l’expérimenter comme alternative à la formation approfondie.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces]" submitText="Go to Azure Machine Learning Studio" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Accédez directement à Azure Machine Learning Studio dans le [Portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces).

::: zone-end

## <a name="azure-machine-learning-servicetabmachinelearningservice"></a>[Service Azure Machine Learning](#tab/MachineLearningService)

Azure Machine Learning service fournit une approche plus poussée basée sur le code qui est nécessaire pour une formation plus approfondie des jeux de données clients. À l’aide de langages informatiques tels que Python, les scientifiques des données peuvent effectuer l’apprentissage et créer un algorithme visant à prédire les besoins des clients.

### <a name="action"></a>Action

Un scientifique des données peut utiliser Azure Machine Learning service pour créer un modèle et en effectuer l’apprentissage à l’aide de langages informatiques avancés tels que Python :

1. Accédez à **Azure Machine Learning service**.
2. Sélectionnez **Créer des espaces de travail Machine Learning service**, puis suivez les invites pour créer un espace de travail.
3. Le nouvel espace de travail offre une approche axée sur le code aux scientifiques des données pour effectuer l’apprentissage et permettre la création de modèles exigeant des analytiques plus avancées pour prédire avec précision les besoins des clients.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces]" submitText="Go to Azure Machine Learning service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Accédez directement à Azure Machine Learning Studio dans le [Portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces).

::: zone-end

## <a name="influence"></a>Influence

Toutes les approches mentionnées précédemment génèrent une API qui expose le modèle de prédiction aux applications. Au sein de votre solution, utilisez l’une de ces approches pour alimenter les données collectées auprès de votre client dans une API prédictive. Les résultats peuvent ensuite être intégrés à l’expérience client comme étape suivante suggérée.

Ces étapes suivantes suggérées peuvent aider à façonner les modèles de comportement des clients et à influencer leur réaction. Comme ces étapes sont basées sur des algorithmes prédictifs, elles utilisent les besoins antérieurs des clients et les données disponibles pour prédire leurs besoins futurs et y répondre, souvent avant même que les clients eux-mêmes n’aient conscience du besoin en question.
