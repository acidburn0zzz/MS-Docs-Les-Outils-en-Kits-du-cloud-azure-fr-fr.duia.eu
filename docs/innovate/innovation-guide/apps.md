---
title: 'Guide d’innovation Azure : Retenir les clients par le biais d’applications'
description: Apprenez à innover en retenant les clients par le biais d’applications à l’aide d’Azure
author: billyclaymyersmsft
ms.author: wimyers
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 7b6a94830f35f7dde577ba4b7122cdec7e4a711d
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808343"
---
::: zone target="docs"

# <a name="azure-innovation-guide-engage-customers-through-apps"></a>Guide d’innovation Azure : Retenir les clients par le biais d’applications

::: zone-end

::: zone target="chromeless"

# <a name="engage-customers-through-apps"></a>Retenir les clients par le biais d’applications

::: zone-end

L’innovation avec les applications comprend la modernisation de vos applications existantes qui sont hébergées en local et la création d’applications cloud natives en utilisant des conteneurs ou des technologies serverless. Azure fournit des services PaaS comme Azure App Service pour vous aider à moderniser facilement vos applications web et API existantes écrites en .NET, .NET Core, Java, Node.js, Ruby, Python ou PHP pour le déploiement dans Azure.

Avec un modèle de conteneur standard ouvert, la création de microservices ou la mise en conteneur de vos applications existantes et leur déploiement sur Azure est simple lorsque vous utilisez des services gérés tels que Azure Kubernetes Service, Azure Container Instances et Web App pour conteneurs. Les technologies serverless telles que Azure Functions et Azure Logic Apps utilisent un modèle de consommation (payez pour ce que vous utilisez) et vous aident à vous concentrer sur la création de votre application plutôt que sur le déploiement et la gestion de votre infrastructure.

<!-- markdownlint-disable MD025 -->

# <a name="deliver-value-fastertabdelivervaluefaster"></a>[Offrir de la valeur plus rapidement](#tab/DeliverValueFaster)

L’un des avantages des solutions informatiques est la possibilité de recueillir des commentaires plus rapidement et de commencer à fournir de la valeur à votre utilisateur. Qu’il s’agisse d’un client externe ou d’un utilisateur de votre propre entreprise, plus vite vous pouvez obtenir des commentaires sur vos applications, mieux c’est.

## <a name="azure-app-service"></a>Azure App Service

Azure App Service fournit un environnement d’hébergement pour vos applications, ce qui élimine la charge de gestion de l’infrastructure et la mise à jour corrective du système d’exploitation. Il permet l’automatisation de la mise à l’échelle pour répondre aux demandes de vos utilisateurs tout en respectant les limites que vous définissez pour maîtriser les coûts.

Azure App Service offre une prise en charge de première classe pour des langages tels que ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP ou Python. Si vous devez héberger une autre pile d’exécution, Web App pour conteneurs vous permet d’héberger rapidement et facilement un conteneur Docker au sein d’App Service, afin que vous puissiez héberger votre pile de code personnalisée dans un environnement qui vous permet de vous sortir de l’activité du serveur.

### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements de Azure App Service :

1. Accédez à **App Services**.
2. Configurer un nouveau service : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer des services existants : Sélectionnez l’application souhaitée dans la liste des applications hébergées.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-cognitive-services"></a>Azure Cognitive Services

Grâce à Azure Cognitive Services, vous pouvez intégrer l’intelligence avancée directement dans votre application via un ensemble d’API qui vous permettent de tirer parti des algorithmes d’intelligence artificielle et d’apprentissage automatique pris en charge par Microsoft.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements d’Azure Cognitive Services :

1. Accédez à **Cognitive Services**.
2. Configurer un nouveau service : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer des services existants : Sélectionnez le service souhaité dans la liste des services hébergés.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-bot-service"></a>Azure Bot Service

Azure Bot Service étend votre application standard en ajoutant une interface de bot naturelle qui utilise l’intelligence artificielle et l’apprentissage automatique pour créer une nouvelle façon d’interagir avec vos clients.

### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements de services Azure Bot :

1. Accédez à **Services Bot**.
2. Configurer un nouveau service : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer des services existants : Sélectionnez le bot souhaité dans la liste des services hébergés.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.BotService%2FbotServices]" submitText="Go to Bot Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-devops"></a>Azure DevOps

Au cours de votre parcours d’innovation, vous serez éventuellement amené à vous engager sur la voie de DevOps. Microsoft a longtemps bénéficié d’un produit local connu sous le nom de Team Foundation Server (TFS). Au cours de notre propre cycle d’innovation, Microsoft a développé Azure DevOps, un service informatique qui fournit des outils de génération et de mise en production prenant en charge de nombreux langages et destinations pour vos versions. Pour plus d’informations, consultez [Azure DevOps](https://docs.microsoft.com/azure/devops).

## <a name="visual-studio-app-center"></a>Visual Studio App Center

Étant donné que la popularité des applications mobiles continue de croître, la nécessité d’une plate-forme capable de fournir des tests automatisés sur des appareils réels avec des configurations différentes augmente. Visual Studio App Center ne fournit pas seulement un emplacement où vous pouvez tester vos applications pour iOS, Android, Windows et macOS. Il fournit également une plateforme de surveillance qui peut utiliser Azure Application Insights pour analyser vos données de télémétrie rapidement et facilement. Pour plus d’informations, consultez [Vue d’ensemble de Visual Studio App Center](https://docs.microsoft.com/appcenter).

Visual Studio App Center fournit également un service de notification qui vous permet d’utiliser un appel unique pour envoyer des notifications à votre application sur plusieurs plateformes sans avoir à contacter chaque service de notification individuellement. Pour plus d’informations, consultez [Visual Studio App Center Push (ACP)](https://docs.microsoft.com/appcenter/push).

### <a name="learn-more"></a>En savoir plus

- [Vue d'ensemble d'App Service](https://docs.microsoft.com/azure/app-service/overview)
- [Web App pour conteneurs : Exécuter un conteneur personnalisé](https://docs.microsoft.com/azure/app-service/containers/quickstart-docker)
- [Présentation d’Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)
- [Azure pour les développeurs .NET et .NET Core](https://docs.microsoft.com/dotnet/azure/?view=azure-dotnet)
- [Documentation du Kit SDK Azure pour Python](https://docs.microsoft.com/azure/python)
- [Azure pour les développeurs cloud Java](https://docs.microsoft.com/azure/java/?view=azure-java-stable)
- [Créer une application web PHP dans Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-php)
- [Documentation du kit SDK Azure pour JavaScript](https://docs.microsoft.com/azure/javascript)
- [Documentation du Kit Azure SDK pour Go](https://docs.microsoft.com/azure/go)
- [Solutions DevOps](https://azure.microsoft.com/solutions/devops)

# <a name="create-cloud-native-appstabcloudnative"></a>[Créer des applications cloud natives](#tab/CloudNative)

<!-- markdownlint-disable MD026 -->

## <a name="what-are-cloud-native-applications"></a>Présentation des applications cloud natives

Les applications cloud natives sont entièrement créées, et optimisées pour l’échelle et les performances du cloud. Elles sont basées de façon souple sur des architectures de microservices, utilisent des services managés, sont observables et tirent parti d’une livraison continue pour gagner en fiabilité et accélérer la commercialisation. Habituellement, elles sont portables et peuvent s’exécuter sur des environnements dynamiques tels que des clouds publics, privés et hybrides. Les applications cloud natives sont généralement créées à l’aide d’une ou de plusieurs des approches suivantes :

- Microservices
- Sans serveur
- Containers

## <a name="microservices"></a>Microservices

Les microservices sont un style d’architecture logicielle dans laquelle les applications sont constituées de petits modules indépendants qui communiquent entre eux par l’intermédiaire de contrats d’API bien définis. Ces modules de services sont des blocs de construction hautement découplés qui sont assez petits pour mettre en œuvre une seule fonctionnalité. Les microservices vous aident à :

- Générer des services de manière indépendante.
- Mettre à l’échelle les services de manière autonome.
- Utiliser les approches les plus appropriées pour le déploiement et les langages de programmation.
- Isoler les points d’échec.
- Offrir de la valeur plus rapidement.

### <a name="azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS)

Utilisez un service Kubernetes complètement managé pour gérer l’approvisionnement, la mise à niveau et la mise à l’échelle des ressources de cluster à la demande. AKS facilite le déploiement et la gestion des applications en conteneur. Il offre une expérience d'intégration continue et de livraison continue (CI/CD) Kubernetes serverless, ainsi qu'une sécurité et une gouvernance de classe Entreprise. Réunissez vos équipes dédiées aux déploiements et aux opérations sur une même plateforme pour rapidement créer, livrer et mettre à l'échelle des applications en toute confiance.

#### <a name="action"></a>Action

Pour configurer ou surveiller un service Azure Kubernetes :

1. Accédez à **Azure Kubernetes services**.
2. Configurer un nouveau service : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer des services existants : Sélectionnez le service Kubernetes souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.ContainerService%2FmanagedClusters]" submitText="Go to Azure Kubernetes services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="event-based-solutions"></a>Solutions basées sur les événements

### <a name="azure-functions"></a>Azure Functions

Azure Functions fournit une plateforme pour exécuter facilement des petites unités de code ou de fonctions dans le cloud. Les fonctions peuvent être un moyen de commencer à refactoriser votre code dans une architecture de microservices.

Le runtime d’Azure Functions prend en charge de nombreux langages, notamment C#, Java, JavaScript et Python. Pour obtenir la liste complète, consultez [Langages pris en charge dans Azure Functions](https://docs.microsoft.com/azure/azure-functions/supported-languages).

Un autre avantage des fonctions est qu’elles peuvent être déclenchées par des actions et des événements différents, tels que HTTPTriggers, TimerTriggers et des déclencheurs provenant d’autres services Azure tels que Stockage Blob, Event Grid et Service Bus. Pour plus d’informations sur les déclencheurs et les liaisons, consultez [Concepts des déclencheurs et liaisons Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

#### <a name="action"></a>Action

Pour configurer ou surveiller les déploiements Azure Functions :

1. Accédez à **Application de fonction**.
2. Configurer une nouvelle application : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer des applications existantes : Sélectionnez l’application souhaitée dans la liste des applications de fonction.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites/kind/functionapp]" submitText="Go to Azure Functions" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="serverless-solutions"></a>Solutions sans serveur

Créez des applications cloud natives sans approvisionner ni gérer d’infrastructure, grâce à une plateforme complètement managée gérant la mise à l’échelle, la disponibilité et les performances pour vous. Les solutions sans serveur Azure présentent les avantages suivants :

- Amélioration de la rapidité de développement.
- Amélioration des performances de l’équipe.
- Amélioration de l’impact à l’échelle de l’organisation.

### <a name="azure-logic-apps"></a>Azure Logic Apps

Intégrez des données et des applications au lieu de créer du code d’intégration complexe entre des systèmes disparates. Créez visuellement des workflows serverless avec Azure Logic Apps et utilisez vos propres API, fonctions serverless ou connecteurs SaaS prêts à l'emploi, comme Salesforce, Microsoft Office 365 et Dropbox.

#### <a name="action"></a>Action

Pour configurer ou surveiller les applications logiques Azure :

1. Accédez à **Applications logiques**.
2. Configurer une nouvelle application : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer des applications existantes : Sélectionnez l’application logique souhaitée dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Logic%2Fworkflows]" submitText="Go to Azure Logic Apps" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="serverless-api-management"></a>Gestion des API sans serveur

Publiez, sécurisez, transformez, tenez à jour et surveillez des API à l’aide du service complètement managé Gestion des API Azure, qui offre un modèle d’utilisation conçu et implémenté pour les applications serverless.

#### <a name="action"></a>Action

Pour configurer ou surveiller les services Gestion des API :

1. Accédez aux **services Gestion des API**.
2. Configurer un nouveau service : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer des services existants : Sélectionnez le service souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="containers"></a>Containers

Pour moderniser votre portefeuille d’applications, Azure fournit différents services conteneurs pour migrer vos applications existantes vers des conteneurs et créer des applications de microservices cloud natives afin que vous puissiez offrir de la valeur à vos utilisateurs plus rapidement. Utilisez des outils CI/CD et de développeur de bout en bout pour développer, mettre à jour et déployer vos applications conteneurisées. Gérez les conteneurs à l’échelle avec un service d’orchestration de conteneur Kubernetes entièrement géré qui s’intègre à Azure Active Directory. Quel que soit l’endroit où vous vous trouvez dans le parcours de votre application, accélérez le développement de vos applications conteneurisées tout en répondant aux exigences de sécurité.

### <a name="azure-container-instances"></a>Azure Container Instances

Exécutez des conteneurs Docker à la demande dans un environnement Azure serverless géré. Azure Container Instances est une solution adaptée à tous les scénarios qui peut fonctionner dans des conteneurs isolés sans orchestration. Lorsque vous exécutez vos charges de travail dans Container Instances, vous pouvez vous concentrer sur la conception et la création de vos applications au lieu de gérer l’infrastructure qui les exécute.

### <a name="action"></a>Action

Pour configurer ou surveiller des instances de conteneur :

1. Accédez à **Container instances**.
2. Configurer une nouvelle instance de conteneur : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer les instances de conteneur existantes : Sélectionnez l’instance de conteneur souhaitée dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ContainerInstance%2FcontainerGroups]" submitText="Go to Container instances" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="azure-red-hat-openshift"></a>Azure Red Hat OpenShift

Azure Red Hat OpenShift permet un déploiement flexible en libre-service de clusters OpenShift complètement managés. Tenez à jour la conformité réglementaire et concentrez-vous sur le développement de vos applications pendant que les nœuds principaux, les nœuds d’infrastructure et les nœuds d’application sont corrigés, mis à jour et surveillés par Microsoft et Red Hat. Choisissez vos propres solutions de registre, de mise en réseau, de stockage ou de CI/CD. Ou lancez-vous rapidement en utilisant des solutions intégrées avec gestion automatisée du code source, création de conteneurs et d’applications, déploiements, mise à l’échelle, gestion de l’intégrité, etc.

**Accédez à [Azure Red Hat OpenShift](https://docs.microsoft.com/azure/openshift/intro-openshift)**

# <a name="isolate-points-of-failuretabisolatepointsoffailure"></a>[Isoler les points d’échec](#tab/IsolatePointsOfFailure)

Lorsque vous commencez à quitter la phase de test initiale, évaluez les façons d’isoler et de supprimer les points de défaillance. En raison de la nature distribuée de la plateforme cloud Azure, vous pouvez concevoir votre application de manière à réduire les défaillances tout en améliorant également le niveau de performance.

## <a name="azure-front-door-service"></a>Azure Front Door Service

Azure Front Door Service fournit un point d’entrée évolutif et sécurisé que vous pouvez utiliser pour mettre votre application à disposition dans le monde entier. Azure Front Door Service combine l’optimisation du trafic visant à obtenir un meilleur niveau de performance et un basculement mondial instantané. Vous devez utiliser Azure Front Door Service plutôt qu’Azure Traffic Manager si vous avez besoin d’une terminaison de protocole TLS (« déchargement SSL ») ou d’un traitement de couche d’application par requête HTTP/HTTPS.

### <a name="action"></a>Action

Pour configurer ou surveiller les portes d’entrée :

1. Accédez à **Portes d’entrée**.
2. Configurer une nouvelle porte d’entrée : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer les portes d’entrée existantes : Sélectionnez la porte d’entrée souhaitée dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ffrontdoors]" submitText="Go to Front Doors" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="traffic-manager"></a>Traffic Manager

Traffic Manager fournit un équilibrage de charge DNS qui peut être routé en fonction de différentes règles. Cette fonctionnalité permet de garantir la résilience en cas de défaillance de l’un des services déployés. Vous pouvez également empiler Traffic Manager pour utiliser le routage basé sur les défaillances et celui basé sur le niveau de performance afin d’offrir la meilleure expérience possible, en fonction de la géographie.

### <a name="action"></a>Action

Pour configurer ou surveiller des profils Traffic Manager :

1. Accédez à **Profils Traffic Manager**.
2. Configurer un nouveau profil : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer les profils existants : Sélectionnez le profil souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ftrafficmanagerprofiles]" submitText="Go to Traffic Manager profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-content-delivery-network"></a>Azure Content Delivery Network

Azure propose un réseau de distribution de contenu (CDN ou Content Delivery Network) distribué qui vous permet de garantir la remise des ressources en temps voulu en les mettant en cache près de vos utilisateurs. Cette mise en cache permet d’améliorer l’expérience de vos clients. Pendant le téléchargement du contenu, elle prévient également les problèmes causés par les incidents réseau susceptibles de survenir entre le point de terminaison CDN et le centre de données qui héberge votre application. Le CDN peut également être utilisé par des applications qui ne sont pas hébergées dans Azure.

### <a name="action"></a>Action

Pour configurer ou surveiller les profils CDN :

1. Accédez à **Profils CDN**.
2. Configurer un nouveau profil : Sélectionnez **Ajouter** et suivez les invites.
3. Gérer les profils existants : Sélectionnez le profil souhaité dans la liste.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.cdn%2Fprofiles]" submitText="Go to CDN profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>En savoir plus

- [Azure Front Door](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
- [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager)
- [Content Delivery Network](https://docs.microsoft.com/azure/cdn)
