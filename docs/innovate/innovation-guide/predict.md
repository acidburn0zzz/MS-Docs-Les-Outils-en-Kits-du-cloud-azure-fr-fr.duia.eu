---
title: 'Guide d’innovation Azure : Prédire et influencer'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Apprenez à prédire et influencer à l’aide d’Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: b2ed1b072d5226649e5248e350edfa3578978c4c
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769258"
---
::: zone target="docs"

# <a name="azure-innovation-guide-predict-and-influence"></a>Guide d’innovation Azure : Prédire et influencer

::: zone-end

::: zone target="chromeless"

# <a name="predict-and-influence"></a>Prédire et influencer

::: zone-end

En guise de pionnier, votre entreprise aura des insights sur les données, le comportement et les besoins de votre base de clients. L’étude de ces insights peut vous aider à prédire les besoins de votre client, avant qu’il n’en soit lui-même conscient. Cet article présente quelques approches permettant de fournir des solutions prédictives. Dans la section ultérieure, l’article présente des approches pour intégrer ces prédictions à votre solution afin d’influencer les comportements des clients.

Le tableau suivant est conçu pour vous aider à trouver la meilleure solution, en fonction de vos besoins d’implémentation.

|de diffusion en continu  |Modèles prédéfinis  |Créer et expérimenter  |Apprentissage et génération avec Python|Compétences requises|
|---------|---------|---------|---------|---------|
|Cognitive Services|OUI|Non|Non|Compétences des développeurs et des API|
|Azure Machine Learning Studio|OUI|OUI|Non|Compréhension générale des algorithmes prédictifs|
|Service Azure Machine Learning|OUI|OUI|OUI|Scientifique des données|

## <a name="azure-cognitive-servicestabcognitiveservices"></a>[Azure Cognitive Services](#tab/CognitiveServices)

Le chemin le plus rapide et le plus simple des prédictions est Azure Cognitive Services. Cognitive Services permet d’effectuer des prédictions basées sur des modèles existants, ne nécessitant aucune formation supplémentaire. Ces services sont optimaux, lorsqu’il n’existe pas de scientifique des données pour l’apprentissage du modèle prédictif. Pour certains services, aucune formation n’est requise. D’autres nécessitent uniquement une formation minimale.

Pour obtenir la liste des services disponibles et la quantité de formation requise, consultez [Cognitive Services et Machine Learning](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-and-machine-learning#service-requirements-for-the-data-model).

### <a name="action"></a>Action

Pour utiliser une API de service cognitif :

1. Accédez à **Cognitive Services**.
2. Cliquez sur **Ajouter +** pour rechercher un service cognitif à partir de la place de marché.
3. Si vous connaissez le nom du service que vous souhaitez utiliser, vous pouvez le saisir dans la zone de texte **Rechercher dans la place de marché**.
4. Sinon, pour obtenir la liste des services cognitifs, cliquez sur le lien **Afficher plus** près de l’en-tête Cognitive Services.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Accédez directement à Cognitive Services dans le [portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts).

::: zone-end

## <a name="azure-machine-learning-studiotabmachinelearningstudio"></a>[Azure Machine Learning Studio](#tab/MachineLearningStudio)

Si les modèles existants dans les services cognitifs ne sont pas alignés sur la prédiction souhaitée, Azure Machine Learning Studio peut offrir un moyen de créer les prédictions souhaitées, sans nécessiter de compétences en matière de science des données.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Vous pouvez utiliser un Azure Machine Learning Studio pour créer un modèle et faire des essais avec :

1. Accédez à **Azure Machine Learning Studio**.
2. Cliquez sur **Créer un espace de travail Machine Learning Studio** et suivez les instructions pour créer un espace de travail.
3. Le nouvel espace de travail fournit une interface de glisser-déplacer pour créer un modèle et l’expérimenter, comme alternative à la formation profonde.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces]" submitText="Go to Azure Machine Learning Studio" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Accédez directement à Azure Machine Learning Studio dans le [Portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces).

::: zone-end

## <a name="azure-machine-learning-servicetabmachinelearningservice"></a>[Service Azure Machine Learning](#tab/MachineLearningService)

Azure Machine Learning service fournit une approche basée sur le code plus poussée, nécessaire pour une formation plus poussée des jeux de données clients. À l’aide de langages tels que Python, les scientifiques des données peuvent former et créer un algorithme visant à prédire les besoins des clients.

### <a name="action"></a>Action

Un scientifique des données peut utiliser un service Azure Machine Learning pour former et créer un modèle à l’aide de langages avancés tels que Python :

1. Accédez à **Azure Machine Learning Service**.
2. Cliquez sur **Créer des espaces de travail Machine Learning Service** et suivez les instructions pour créer un espace de travail.
3. Le nouvel espace de travail offre une approche par code aux scientifiques de données pour former et concevoir des modèles exigeant des analytiques plus avancées pour prévoir les besoins des clients avec précision.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces]" submitText="Go to Azure Machine Learning Service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Accédez directement à Azure Machine Learning Studio dans le [Portail Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces).

::: zone-end

## <a name="influence"></a>Influence

Toutes les approches mentionnées ci-dessus génèrent une API qui expose le modèle de prédiction aux applications. Au sein de votre solution, utilisez l’une de ces approches pour alimenter les données collectées à partir de votre client dans une API prédictive. Les résultats peuvent ensuite être intégrés à l’expérience client comme étape suivante suggérée.

Les étapes suivantes tentent de mettre en forme les modèles de comportements des clients et d’influencer la manière dont ils réagissent. Étant donné que les étapes suivantes sont basées sur des algorithmes prédictifs, elles utilisent les clients précédents et les données disponibles pour prédire les besoins du client et répondre à ce besoin, souvent avant que celui-ci n’en soit même conscience.
