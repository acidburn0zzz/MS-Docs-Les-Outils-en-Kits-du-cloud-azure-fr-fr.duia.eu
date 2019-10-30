---
title: 'Guide d’innovation Azure : Impliquer par le biais d’applications'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Apprenez à innover en vous engageant sur des applications à l’aide d’Azure.
author: billyclaymyersmsft
ms.author: wimyers
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: df91d44d9b1efc2196b8b322c247dd39ef3d0d1e
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769360"
---
::: zone target="docs"

# <a name="azure-innovation-guide-engage-through-apps"></a>Guide d’innovation Azure : Impliquer par le biais d’applications

::: zone-end

::: zone target="chromeless"

# <a name="engage-through-apps"></a>Impliquer par le biais d’applications

::: zone-end

L’innovation avec les applications comprend la modernisation de vos applications existantes hébergées en local, ainsi que la création d’applications cloud natives à l’aide de conteneurs ou de technologies sans serveur. En ce qui concerne la modernisation d’applications, Azure fournit des services PaaS comme Azure App Service pour moderniser facilement vos applications Web et API existantes écrites en .NET, .NET Core, Java, node. js, Ruby, Python ou PHP pour le déploiement dans Azure. Avec un modèle de conteneur standard ouvert, la création de microservices ou la mise en conteneur de vos applications existantes et leur déploiement sur Azure est simple grâce à des services gérés tels que les services Kubernetes Azure, Azure Container Instances et les Web App pour conteneurs. Les technologies sans serveur telles que Azure Functions et Azure Logic Apps vous aident à vous concentrer sur la création de votre application à l’aide d’un modèle de consommation (payez pour ce que vous utilisez) au lieu de déployer et de gérer l’infrastructure.

<!-- markdownlint-disable MD025 -->

# <a name="deliver-value-fastertabdelivervaluefaster"></a>[Offrir de la valeur plus rapidement](#tab/DeliverValueFaster)

L’un des avantages des solutions basées sur le cloud est la possibilité de recueillir des commentaires plus rapidement et de commencer à fournir de la valeur à votre utilisateur final. Qu’il s’agisse d’un client externe ou d’un utilisateur de votre propre entreprise, plus vous pouvez obtenir des commentaires plus rapidement sur vos applications, mieux c’est.

## <a name="azure-app-service"></a>Azure App Service

Azure App Service fournit un environnement d’hébergement pour vos applications, ce qui élimine la charge de gestion de l’infrastructure et la mise à jour corrective du système d’exploitation. Il permet l’automatisation de la mise à l’échelle pour répondre aux besoins de vos utilisateurs, tout en étant délimité par vos soins pour assurer le contrôle des coûts.

Azure App Service offre une prise en charge de première classe pour des langages tels que ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP ou Python. Si vous devez héberger une autre pile d’exécution, Web App pour conteneurs vous permet d’héberger rapidement et facilement un conteneur Docker au sein de l’environnement Azure App Service, hébergeant ainsi votre pile de code personnalisée dans un environnement qui vous permet de vous sortir de l’activité du serveur.

### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements de Azure App Service :

1. Accédez à **App Services**.
2. Configurer un nouveau service : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer des services existants : Sélectionnez l’application souhaitée dans la liste des applications hébergées.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-cognitive-services"></a>Azure Cognitive Services

Azure Cognitive Services vous permet d’intégrer l’intelligence avancée directement dans votre application via un ensemble d’API, ce qui vous permet de tirer parti des algorithmes d’intelligence artificielle et de Machine Learning pris en charge par Microsoft.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements de Azure Cognitive Service :

1. Accédez à **Cognitive Services**.
2. Configurer un nouveau service : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer des services existants : Sélectionnez le service souhaité dans la liste des services hébergés.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-bot-services"></a>Azure Bot Services

Les services Azure bot étendent votre application standard pour inclure une interface de bot naturelle qui utilise l’intelligence artificielle et le Machine Learning pour créer une nouvelle interaction pour vos clients.

### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements de services Azure Bot :

1. Accédez à **Services Bot**.
2. Configurer un nouveau service : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer des services existants : Sélectionnez le bot souhaité dans la liste des services hébergés.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.BotService%2FbotServices]" submitText="Go to Bot Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-devops"></a>Azure DevOps

Pendant votre parcours d’innovation, vous vous retrouverez sur le chemin d’accès à DevOps. Microsoft a longtemps bénéficié d’un produit local connu sous le nom de Team Foundation Server (TFS). Au cours de notre propre cycle d’innovation, Microsoft a développé Azure DevOps pour être un service cloud qui fournit des outils de génération et de mise en production prenant en charge de nombreux langages et destinations différents pour vos versions. [Azure DevOps](https://docs.microsoft.com/azure/devops)

## <a name="visual-studio-app-center"></a>Visual Studio App Center

Étant donné que la popularité des applications mobiles continue de croître, la nécessité d’une plate-forme capable de fournir des tests automatisés sur des appareils réels avec des configurations différentes augmente. Visual Studio App Center fournit non seulement un emplacement au sein duquel vous pouvez tester vos applications sur iOS, Android, Windows et macOS, mais il offre également une plateforme d’analyse avec la possibilité de tirer parti de Azure Application Insights pour obtenir rapidement et facilement des informations sur vos données de télémétrie. Pour plus d’informations, consultez la [vue d’ensemble du centre d’applications Visual Studio](https://docs.microsoft.com/appcenter).

Visual Studio App Center fournit également un service de notification qui permet à un appel unique d’envoyer des notifications à votre application sur plusieurs plateformes sans avoir à contacter chaque service de notification individuellement. Pour plus d’informations, consultez [Visual Studio App Center Push (ACP)](https://docs.microsoft.com/appcenter/push).

### <a name="read-more"></a>En savoir plus

- [Vue d'ensemble d'App Service](https://docs.microsoft.com/azure/app-service/overview)
- [Web Apps pour les conteneurs : Exécuter un conteneur personnalisé](https://docs.microsoft.com/azure/app-service/containers/quickstart-docker)
- [Présentation d’Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)
- [Azure pour les développeurs .NET et .NET Core](https://docs.microsoft.com/dotnet/azure/?view=azure-dotnet)
- [Documentation du Kit SDK Azure pour Python](https://docs.microsoft.com/azure/python)
- [Azure pour les développeurs cloud Java](https://docs.microsoft.com/azure/java/?view=azure-java-stable)
- [Créer une application web PHP dans Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-php)
- [Documentation du kit SDK Azure pour JavaScript](https://docs.microsoft.com/azure/javascript)
- [Documentation du Kit Azure SDK pour Go](https://docs.microsoft.com/azure/go)
- [Solutions DevOps](https://azure.microsoft.com/solutions/devops)

# <a name="cloud-native-appstabcloudnative"></a>[Applications cloud natives](#tab/CloudNative)

<!-- markdownlint-disable MD026 -->

## <a name="what-are-cloud-native-applications"></a>Présentation des applications cloud natives

Les applications cloud natives sont entièrement créées, et optimisées pour l’échelle et les performances du cloud. Elles sont basées de façon souple sur des architectures de microservices, utilisent des services managés, sont observables et tirent parti d’une livraison continue pour gagner en fiabilité et accélérer la commercialisation. En général, elles sont portables et peuvent s’exécuter sur des environnements dynamiques tels que des clouds publics, privés et hybrides. Les applications cloud natives sont généralement créées à l’aide d’une ou de plusieurs des méthodes suivantes :

- Microservices
- Sans serveur
- Conteneur

## <a name="microservices"></a>Microservices

Les microservices constituent un style d’architecture logicielle dans laquelle les applications sont constituées de petits modules indépendants qui communiquent entre eux à l’aide de contrats d’API bien définis. Ces modules de services sont des blocs de construction hautement découplés qui sont assez petits pour mettre en œuvre une seule fonctionnalité. Les microservices vous aident à :

- Générer des services de manière indépendante.
- Mettre à l’échelle les services de manière autonome.
- Utiliser les approches les plus appropriées pour le déploiement et le langage de programmation.
- Isoler les points d’échec.
- Offrir de la valeur plus rapidement.

### <a name="azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS)

Utilisez un service Kubernetes entièrement managé pour gérer le provisionnement, la mise à niveau et la mise à l’échelle des ressources de cluster à la demande. AKS facilite le déploiement et la gestion des applications en conteneur. Il offre une expérience d'intégration continue et de livraison continue (CI/CD) Kubernetes serverless, ainsi qu'une sécurité et une gouvernance de classe Entreprise. Réunissez vos équipes dédiées aux déploiements et aux opérations sur une même plateforme pour rapidement créer, livrer et mettre à l'échelle des applications en toute confiance.

#### <a name="action"></a>Action

Pour configurer ou superviser Azure Kubernetes Services :

1. Accédez **Kubernetes Services**.
2. Configurer un nouveau service : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer des services existants : Sélectionnez le service Kubernetes souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.ContainerService%2FmanagedClusters]" submitText="Go to Kubernetes Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="event-based-solutions"></a>Solutions basées sur les événements

### <a name="azure-functions"></a>Azure Functions

Azure Functions fournit une plateforme pour exécuter facilement des petits morceaux de code, ou fonctions avec le cloud. Les fonctions peuvent être un moyen de commencer à refactoriser votre code dans une architecture de microservices.

Le runtime d’Azure Functions prend en charge de nombreux langages, notamment C#, Java, JavaScript et Python. Pour une liste complète, consultez la page [Langages pris en charge dans Azure Functions](https://docs.microsoft.com/azure/azure-functions/supported-languages).

Un autre avantage des fonctions est la possibilité d’être déclenchées par des actions et des événements différents, tels que HTTPTriggers, TimerTriggers et des déclencheurs à partir d’autres services Azure tels que le stockage d’objets BLOB, EventGrid et ServiceBus. Pour plus d’informations sur les déclencheurs et les liaisons, consultez [Concepts des déclencheurs et liaisons Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

#### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements Azure Functions :

1. Accédez à **Application de fonction**.
2. Configurer une nouvelle application : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer des applications existantes : Sélectionnez l’application souhaitée dans la liste des applications de fonction.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites/kind/functionapp]" submitText="Go to Azure Functions" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="serverless-solutions"></a>Solutions sans serveur

Créez des applications cloud natives sans approvisionner ni gérer d’infrastructure, grâce à une plateforme gérant la mise à l’échelle, la disponibilité et les performances pour vous. Les solutions sans serveur Azure présentent les avantages suivants :

- Amélioration de la vitesse de développement
- Amélioration des performances d'équipe
- Amélioration de l'impact à l'échelle de l'organisation

### <a name="azure-logic-apps"></a>Azure Logic Apps

Intégrez des données et des applications au lieu de créer du code d’intégration complexe entre des systèmes disparates. Créez visuellement des workflows serverless avec Azure Logic Apps et utilisez vos propres API, fonctions serverless ou connecteurs SaaS prêts à l'emploi, comme Salesforce, Microsoft Office 365 et Dropbox.

#### <a name="action"></a>Action

Pour configurer ou surveiller Azure Logic Apps :

1. Accédez à **Applications logiques**.
2. Configurer une nouvelle application : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer des applications existantes : Sélectionnez l’API logique souhaitée dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Logic%2Fworkflows]" submitText="Go to Azure Logic Apps" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="serverless-api-management"></a>Gestion des API sans serveur

Publiez, sécurisez, transformez, maintenez et surveillez des API à l'aide du service complètement managé Gestion des API Azure, qui offre un modèle d'utilisation conçu et implémenté pour les applications serverless.

#### <a name="action"></a>Action

Pour configurer ou surveiller les services Gestion des API :

1. Accédez aux **services Gestion des API**.
2. Configurer un nouveau service : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer des services existants : Sélectionnez le service souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="containers"></a>Containers

En ce qui concerne la modernisation de votre portefeuille d’applications, Azure fournit différents services de conteneur pour déplacer vos applications existantes vers des conteneurs, et pour créer des applications de microservices natives en cloud afin de fournir à vos utilisateurs une valeur ajoutée plus rapidement. Utilisez des outils CI/CD et de développeur de bout en bout pour développer, mettre à jour et déployer vos applications conteneurisées. Gérez les conteneurs à l’échelle avec un service d’orchestration de conteneur Kubernetes entièrement géré qui s’intègre à Azure Active Directory. Quel que soit l’endroit où vous vous trouvez dans le parcours de votre application, accélérez le développement de vos applications conteneurisées tout en répondant aux exigences de sécurité.

### <a name="azure-container-instances"></a>Azure Container Instances

Exécutez des conteneurs Docker à la demande dans un environnement Azure serverless géré. Azure Container Instances (ACI) est une solution adaptée à tous les scénarios qui peut fonctionner dans des conteneurs isolés, sans orchestration. En exécutant vos charges de travail dans ACI, vous pouvez vous concentrer sur la conception et la création de vos applications au lieu de gérer l’infrastructure qui les exécute.

### <a name="action"></a>Action

Pour configurer ou surveiller des instances de conteneur :

1. Accédez à **Container instances**.
2. Configurer une nouvel instance de conteneur : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer les instances de conteneur existantes : Sélectionnez l’instance de conteneur souhaitée dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ContainerInstance%2FcontainerGroups]" submitText="Go to Container instances" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

Azure Red Hat OpenShift permet un déploiement flexible en libre-service de clusters OpenShift complètement managés. Maintenez la conformité réglementaire et concentrez-vous sur le développement de vos applications ; les nœuds principaux, les nœuds d'infrastructure et les nœuds d'application sont corrigés, mis à jour et surveillés par Microsoft et Red Hat. Choisissez vos propres solutions de registre, de mise en réseau, de stockage et CI/CD, commencez rapidement à utiliser les solutions intégrées avec la gestion automatisée du code source, les builds de conteneurs et d’applications, les déploiements, la mise à l’échelle, la gestion de l’intégrité et bien plus encore.

**Accédez à [Azure Red Hat OpenShift](https://docs.microsoft.com/azure/openshift/intro-openshift)**

# <a name="isolate-points-of-failuretabisolatepointsoffailure"></a>[Isoler les points d’échec](#tab/IsolatePointsOfFailure)

Lorsque vous commencez à quitter la phase de test initiale, évaluez les façons d’isoler et de supprimer les points de défaillance. En raison de la nature distribuée du cloud Azure, vous pouvez concevoir votre application pour réduire les échecs tout en améliorant également les performances.

## <a name="azure-front-door"></a>Azure Front Door

Azure Front Door fournit un point d’entrée évolutif et sécurisé pour fournir votre application dans le monde entier. Azure Front Door combine l’optimisation du trafic pour obtenir de meilleures performances et un basculement global instantané. Azure Front Door doit être préféré à Traffic Manager si vous recherchez une terminaison de protocole TLS (« déchargement SSL ») ou un traitement de couche d’application par requête HTTP/HTTPS.

### <a name="action"></a>Action

Pour configurer ou surveiller les portes d’entrée :

1. Accédez à **Portes d’entrée**.
2. Configurer une nouvelle porte d’entrée  : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer les portes d’entrée existantes : Sélectionnez la porte d’entrée souhaitée dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ffrontdoors]" submitText="Go to Front Doors" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="traffic-manager"></a>Traffic Manager

Traffic Manager fournit un équilibrage de charge DNS qui peut être routé en fonction de différentes règles. Cela permet de garantir la résilience en cas d’échec de l’un des services déployés. Vous pouvez également empiler Traffic Manager pour utiliser le routage basé sur les défaillances et le routage basé sur les performances, ce qui offre la meilleure expérience possible en fonction de la géographie.

### <a name="action"></a>Action

Pour configurer ou surveiller des profils Traffic Manager :

1. Accédez à **Profils Traffic Manager**.
2. Configurer un nouveau profil : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer les profils existants : Sélectionnez le profil souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ftrafficmanagerprofiles]" submitText="Go to Traffic Manager profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-content-delivery-network"></a>Azure Content Delivery Network

Azure propose un réseau de distribution de contenu (CDN, Content Delivery Network) distribué qui vous permet de garantir la remise en temps voulu des ressources en les mettant à la disposition des utilisateurs finaux. Cette mise en cache permet d’améliorer l’expérience de vos clients et d’éviter les problèmes lors du téléchargement de contenu dû à des problèmes de réseau entre le point de terminaison CDN et le centre de données hébergeant votre application. Ce CDN peut également être utilisé par des applications qui ne sont pas hébergées dans Azure.

### <a name="action"></a>Action

Pour configurer ou surveiller des profils CDN :

1. Accédez à **Profils CDN**.
2. Configurer un nouveau profil : cliquez sur le lien **Ajouter +** et suivez les invites.
3. Gérer les profils existants : Sélectionnez le profil souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.cdn%2Fprofiles]" submitText="Go to CDN profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="read-more"></a>En savoir plus

- [Azure Front Door](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
- [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager)
- [Content Delivery Network](https://docs.microsoft.com/azure/cdn)
