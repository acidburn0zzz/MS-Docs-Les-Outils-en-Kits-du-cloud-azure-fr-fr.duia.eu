---
title: 'Guide d’innovation Azure : Préparer les commentaires des clients'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Préparer les commentaires des clients
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: ec17c66fa92abc292a19a8e74c215111d8638a05
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769362"
---
::: zone target="docs"

# <a name="azure-innovation-guide-prepare-for-customer-feedback"></a>Guide d’innovation Azure : Préparer les commentaires des clients

::: zone-end

::: zone target="chromeless"

# <a name="prepare-for-customer-feedback"></a>Préparer les commentaires des clients

::: zone-end

L’adoption, l’engagement et la rétention des utilisateurs sont essentiels à une innovation réussie. Pourquoi ?

La création d’une solution innovante n’a pas pour objet de donner à l’utilisateur ce qu’il veut ou pense souhaiter. Il s’agit de formuler une hypothèse qui peut être testée et améliorée. Ce test se présente sous deux formes : Quantitatif (commentaires sur le test), ou les actions que nous espérons voir. Qualitatif (commentaires des clients), pour nous indiquer ce que ces mesures signifient pour le client. Ensemble, ils informent l’hypothèse suivante et la prochaine amélioration de la solution. Ces boucles de commentaires constituent la base du [processus Développer-mesurer-apprendre](../considerations/adoption.md) au cœur de cette méthodologie.

Avant d’intégrer des boucles de commentaires, un référentiel partagé pour votre solution est indispensable. Un référentiel centralisé offre un moyen d’enregistrer et de traiter toutes les informations relatives à votre projet.  [GitHub](https://github.com/) est l’endroit pour trouver un logiciel open source. Il s’agit également de l’une des plateformes les plus couramment utilisées pour héberger le référentiel de code source pour les applications développées dans le commerce. L’article sur la [création de référentiels GitHub](https://docs.microsoft.com/azure/devops/pipelines/repos/github?view=azure-devops&tabs=yaml) peut vous aider à démarrer avec vos référentiels.

Chacun des outils suivants dans Azure s’intègre à (ou est compatible avec) des projets hébergés dans GitHub :

## <a name="quantitative-feedback-for-web-appstabquantitative-apps"></a>[Commentaires quantitatifs pour les applications web](#tab/Quantitative-Apps)

Application Insights est un outil d’analyse qui permet d’obtenir des commentaires quantitatifs presque en temps réel sur l’utilisation de votre application. Ce feedback peut vous aider à tester et valider votre hypothèse actuelle pour mettre en forme la fonctionnalité suivante ou le récit utilisateur dans votre backlog.

### <a name="action"></a>Action

Pour afficher des données quantitatives sur vos applications :

1. Accédez à **App Insights**.
2. Si votre application n’apparaît pas dans la liste, cliquez sur le lien **Ajouter +** et suivez les invites pour démarrer la configuration d’Application Insights.
3. Si l’application souhaitée figure dans la liste, sélectionnez-la.
4. Le volet **Présentation** contient des statistiques sur l’application. Le lien **Tableau de bord de l’application** vous permet de créer un tableau de bord personnalisé pour afficher les données qui sont plus pertinentes pour votre hypothèse.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Go to App Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Pour afficher les données concernant vos applications, accédez au [Portail Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents).

::: zone-end

### <a name="learn-more"></a>En savoir plus

- [Configurer Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/learn/quick-monitor-portal)
- [Bien démarrer avec Azure Monitor Application Insights](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-users)
- [Créer un tableau de bord de télémétrie](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)

## <a name="quantitative-feedback-for-apistabquantitative-apis"></a>[Commentaires quantitatifs pour les API](#tab/Quantitative-APIs)

L’économie connectée change la façon dont les entreprises innovent.  Les marchés et les secteurs sont perturbés plus rapidement que jamais. La perturbation prend de nombreuses formes et les entreprises doivent s’adapter au **« dilemme »** : définir le rythme des modifications sans se heurter à une activité commerciale.

Les entreprises utilisent des API en externe pour modifier la façon dont elles interagissent avec les clients et leurs partenaires. En interne, ils utilisent des API pour connecter en toute transparence des parties distinctes de l’entreprise. L’économie d’API fonctionne sur quatre supports fondamentaux : social, mobile, l’analyse et le cloud. Les applications et les services peuvent être liés rapidement et à moindre coût pour créer une proposition de valeur étendue.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Pour enregistrer des données quantitatives sur vos API :

1. Accédez au **service Gestion des API**.
2. Sélectionnez l’API souhaitée dans la liste.
3. Choisissez **Paramètres de diagnostic** dans la section **Surveillance**.

Pour afficher des données quantitatives sur vos API :

1. Accédez au **service Gestion des API**.
2. Sélectionnez l’API souhaitée dans la liste.
3. Choisissez **Application** dans la section **Surveillance**.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management Service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Pour ouvrir le service Gestion des API, accédez au [Portail Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice).

::: zone-end

### <a name="learn-more"></a>En savoir plus

Cet article peut vous aider à utiliser [Azure Monitor pour obtenir des commentaires sur les API](https://docs.microsoft.com/azure/api-management/api-management-howto-use-azure-monitor)

## <a name="qualitative-feedbacktabqualitative"></a>[Commentaires qualitatifs](#tab/Qualitative)

Le backlog (ou tableau) est l’emplacement où les commentaires sont enregistrés en tant que récits utilisateur. C’est également là que le travail associé est suivi en tant que tâches actionnables. Azure Boards peut être intégré directement dans GitHub, ce qui permet une expérience transparente entre la gestion du travail de commentaires et tout code source.

::: zone target="docs"

### <a name="action"></a>Action

Azure Boards et Azure Pipelines requièrent un portail distinct de GitHub et d’Azure.
Pour commencer à utiliser l’un de ces outils, accédez à [Azure DevOps](https://dev.azure.com/)

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

### <a name="action"></a>Action

Pour créer un projet DevOps :

1. Accédez au **projet Azure DevOps**.
2. Cliquez sur **Créer un projet DevOps**.
3. Choisissez **Runtime, framework et service**.

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/microsoft.visualstudio%2Faccount%2Fproject]" submitText="Go to Azure DevOps Project" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>En savoir plus

Les liens suivants vous aideront à centraliser et à gérer les commentaires à l’aide d’Azure Boards avec GitHub :

- [Prise en main d’Azure Boards](https://docs.microsoft.com/azure/devops/boards/boards/kanban-quickstart?view=azure-devops)
- [Azure Boards & GitHub](https://docs.microsoft.com/azure/devops/boards/boards/kanban-quickstart?view=azure-devops)

## <a name="close-the-loop-with-pipelinestabpipelines"></a>[Fermer la boucle avec des pipelines](#tab/pipelines)

Le fait d’agir sur les commentaires peut ne pas toujours aboutir à la fonctionnalité demandée par le client. Toutefois, chaque point de données doit entraîner une modification. Cette modification peut avoir un impact sur votre point de vue. Il peut également s’agir d’une modification technique totalement différente de celle demandée. Dans les deux cas, les pipelines et les outils de déploiement comme Azure Pipelines vous permettent de publier rapidement ces modifications, de sorte qu’elles puissent être partagées avec le client fréquemment.

Pour afficher les déploiements actifs liés à vos applications hébergées dans Azure :

### <a name="action"></a>Action

Pour afficher les déploiements actuels dans votre pipeline :

1. Accédez à **App Service**.
2. Sélectionnez l’application souhaitée dans la liste.
3. Choisissez **Centre de déploiement** dans la section **Déploiement** du volet Services d’application.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Pour afficher vos applications dans App Service, accédez au [Portail Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites).

::: zone-end

### <a name="learn-more"></a>En savoir plus

Vous trouverez ci-dessous des liens supplémentaires pour commencer à créer vos pipelines de déploiement :

- [Créer votre premier pipeline](https://docs.microsoft.com/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)
- [Tâches de fin GitHub](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/github-release?view=azure-devops)
