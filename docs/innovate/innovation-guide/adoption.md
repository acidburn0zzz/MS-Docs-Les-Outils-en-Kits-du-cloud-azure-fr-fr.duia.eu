---
title: 'Innovation Azure : Se préparer aux commentaires'
description: Découvrez comment utiliser Azure Tools pour collecter des commentaires d’ordre quantitatif et qualitatif sur les applications web et les API hébergées dans GitHub.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: e39a13702f0734e592c7dfbefa90ec5f34846359
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80356668"
---
::: zone target="docs"

# <a name="azure-innovation-guide-prepare-for-customer-feedback"></a>Guide d’innovation Azure : Préparer les commentaires des clients

::: zone-end

::: zone target="chromeless"

# <a name="prepare-for-customer-feedback"></a>Préparer les commentaires des clients

::: zone-end

L’adoption, l’engagement et la rétention des utilisateurs sont essentiels à une innovation réussie. Pourquoi ?

La création d’une solution innovante n’a pas pour objet de donner aux utilisateurs ce qu’ils veulent ou pensent vouloir. Il s’agit de formuler une hypothèse qui peut être testée et améliorée. Ce test se présente sous deux formes :

- **Quantitative (test de commentaires) :** Ces commentaires mesurent les actions que nous espérons voir.
- **Qualitative (commentaires des clients) :** Ces commentaires nous indiquent ce que ces mesures signifient pour le client.

Avant d’intégrer des retours d’informations, vous devez disposer d’un référentiel partagé pour votre solution. Un référentiel centralisé offre un moyen d’enregistrer et de traiter tous les commentaires relatifs à votre projet. [GitHub](https://github.com) est l’endroit pour trouver un logiciel open source. Il s’agit également de l’une des plateformes les plus couramment utilisées pour héberger les référentiels de code source pour les applications développées pour le commerce. L’article sur la [création de référentiels GitHub](https://docs.microsoft.com/azure/devops/pipelines/repos/github?view=azure-devops&tabs=yaml) peut vous aider à prendre en main votre référentiel.

Chacun des outils suivants dans Azure s’intègre à (ou est compatible avec) des projets hébergés dans GitHub :

## <a name="quantitative-feedback-for-web-apps"></a>[Commentaires quantitatifs pour les applications web](#tab/Quantitative-Apps)

Application Insights est un outil d’analyse qui fournit des commentaires quantitatifs presque en temps réel sur l’utilisation de votre application. Ces commentaires peuvent vous aider à tester et valider votre hypothèse actuelle pour façonner la fonctionnalité suivante ou le récit utilisateur dans votre backlog.

### <a name="action"></a>Action

Pour afficher des données quantitatives sur vos applications :

1. Accédez à **Application Insights**.
   - Si votre application n’apparaît pas dans la liste, sélectionnez **Ajouter** et suivez les invites pour démarrer la configuration d’Application Insights.
   - Si l’application souhaitée figure dans la liste, sélectionnez-la.
1. Le volet **Présentation** contient des statistiques sur l’application. Sélectionnez **Tableau de bord de l’application** pour créer un tableau de bord personnalisé afin d’afficher des données plus pertinentes pour votre hypothèse.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Insights%2FComponents]" submitText="Go to Application Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Pour afficher les données relatives à vos applications, accédez au [Portail Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Insights%2FComponents).

::: zone-end

### <a name="learn-more"></a>En savoir plus

- [Configurer Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/learn/quick-monitor-portal)
- [Bien démarrer avec Azure Monitor Application Insights](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-users)
- [Créer un tableau de bord de télémétrie](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)

## <a name="quantitative-feedback-for-apis"></a>[Commentaires quantitatifs pour les API](#tab/Quantitative-APIs)

L’économie connectée change la façon dont les entreprises innovent. Les marchés et les secteurs sont perturbés plus rapidement que jamais. La perturbation prend de nombreuses formes et les entreprises doivent s’adapter au _dilemme de l’innovateur_ : définir le rythme des changements sans se heurter à l’activité commerciale.

Les entreprises utilisent des API en externe pour modifier la façon dont elles interagissent avec leurs clients et partenaires. En interne, elles utilisent des API pour connecter en toute transparence des parties distinctes de l’entreprise. L’économie d’API fonctionne sur quatre supports fondamentaux : les réseaux sociaux, la mobilité, l’analyse et le cloud. Les applications et les services peuvent être liés rapidement et à moindre coût pour créer une proposition de valeur étendue.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Pour enregistrer des données quantitatives sur vos API :

1. Accédez aux **services Gestion des API**.
2. Sélectionnez l’API souhaitée dans la liste.
3. Sélectionnez **Paramètres de diagnostic** dans la section **Surveillance**.

Pour afficher des données quantitatives sur vos API :

1. Accédez aux **services Gestion des API**.
2. Sélectionnez l’API souhaitée dans la liste.
3. Sélectionnez **Application** dans la section **Surveillance**.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2FService]" submitText="Go to API Management services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Pour ouvrir les services Gestion des API, accédez au [Portail Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2FService).

::: zone-end

### <a name="learn-more"></a>En savoir plus

- [Utiliser Azure Monitor pour obtenir des commentaires sur les API](https://docs.microsoft.com/azure/api-management/api-management-howto-use-azure-monitor)

## <a name="qualitative-feedback"></a>[Commentaires qualitatifs](#tab/Qualitative)

Le backlog (ou tableau) est l’emplacement où les commentaires sont enregistrés en tant que récits utilisateur. C’est également là que le travail associé est suivi en tant que tâches actionnables. Azure Boards peut être intégré directement dans GitHub, ce qui permet une expérience transparente entre la gestion du travail de commentaires et tout code source.

::: zone target="docs"

### <a name="action"></a>Action

Azure Boards et Azure Pipelines requièrent un portail distinct de GitHub et d’Azure. Bien démarrer avec [Azure DevOps](https://dev.azure.com).

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

### <a name="action"></a>Action

Pour créer un projet DevOps :

1. Accédez aux **projets Azure DevOps**.
2. Sélectionnez **Créer un projet DevOps**.
3. Sélectionnez **Runtime, framework et service**.

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.VisualStudio%2FAccount%2FProject]" submitText="Go to Azure DevOps Projects" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>En savoir plus

Ces articles vous aideront à centraliser et à gérer les commentaires en utilisant Azure Boards avec GitHub :

- [Prise en main d’Azure Boards](https://docs.microsoft.com/azure/devops/boards/get-started/?view=azure-devops)
- [Azure Boards and GitHub](https://docs.microsoft.com/azure/devops/boards/github?view=azure-devops)

## <a name="close-the-loop-with-pipelines"></a>[Fermer la boucle avec des pipelines](#tab/pipelines)

Le fait d’agir sur les commentaires ne signifie pas toujours ajouter la fonctionnalité demandée par le client. Toutefois, chaque point de données doit entraîner une modification. Cette modification peut être un changement de votre point de vue. Il peut également s’agir d’une modification technique totalement différente de celle demandée. Dans les deux cas, les pipelines et les outils de déploiement comme Azure Pipelines vous permettent de publier rapidement ces modifications afin qu’elles puissent être transmises fréquemment avec le client.

### <a name="action"></a>Action

Pour afficher les déploiements actuels dans votre pipeline :

1. Accédez à **App Services**.
2. Sélectionnez l’application souhaitée dans la liste.
3. Sélectionnez **Centre de déploiement** dans la section **Déploiement** du volet Services d’application.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2FSites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Pour afficher vos applications dans App Service, accédez au [Portail Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2FSites).

::: zone-end

### <a name="learn-more"></a>En savoir plus

Commencer à créer vos pipelines de déploiement :

- [Créer votre premier pipeline](https://docs.microsoft.com/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)
- [Tâches de mise en production GitHub](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/github-release?view=azure-devops)
