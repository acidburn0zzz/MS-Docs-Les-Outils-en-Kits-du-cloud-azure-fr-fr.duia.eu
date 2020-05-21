---
title: Regénérer une application locale à Azure AD
description: Découvrez comment Contoso recrée une application sur Azure avec Azure App Service, Azure Kubernetes Service, Azure Cosmos DB, Azure Functions et Azure Cognitive Services.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 04e5d34da71fb67ce6608aea5f1db5dc6f90f705
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83401116"
---
<!-- docsTest:ignore SmartHotel360 SmartHotel360-Backend Pet.Checker vcenter.contoso.com contoso-datacenter git aks ContosoRG PetCheckerFunction -->

<!-- cSpell:ignore givenscj WEBVM SQLVM contosohost vcenter contosodc smarthotel contososmarthotel smarthotelcontoso smarthotelpetchecker petchecker smarthotelakseus smarthotelacreus smarthotelpets kubectl contosodevops visualstudio azuredeploy cloudapp smarthotelsettingsurl appsettings -->

# <a name="rebuild-an-on-premises-app-on-azure"></a>Regénérer une application locale sur Azure AD

Cet article explique comment la société fictive Contoso reconstruit une application Windows .NET à deux niveaux qui s’exécute sur des machines virtuelles VMware dans le cadre d’une migration vers Azure. Contoso migre la machine virtuelle frontale de l’application vers une application web Azure App Service. Le backend de l'application est généré à l’aide de microservices déployés sur des conteneurs gérés par Azure Kubernetes Service (AKS). Le site interagit avec Azure Functions pour fournir des fonctionnalités de photos d’animaux.

L’application SmartHotel360 utilisée dans cet exemple est fournie au format open source. Si vous souhaitez l’utiliser à des fins de test, vous pouvez la télécharger à partir de [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat qu’ils souhaitent obtenir avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso se développe et souhaite fournir des expériences différenciées pour les clients sur les sites web de Contoso.
- **Soyez agile.** Contoso doit être en mesure de réagir plus rapidement que l’évolution du marché pour réussir dans une économie mondiale.
- **Mise à l’échelle** L’équipe informatique de Contoso doit prévoir des systèmes capables d’évoluer au même rythme que l’entreprise.
- **Réduire les coûts.** Contoso souhaite réduire les coûts de licence.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a épinglé les exigences d’application pour cette migration. Ces exigences ont été utilisées pour déterminer la meilleure méthode de migration :

- L’application dans Azure est toujours aussi critique qu’aujourd’hui. Elle doit offrir de bonnes performances et se mettre à l’échelle facilement.
- L’application ne doit pas utiliser de composants IaaS. Tout doit être créé pour utiliser des services PaaS ou sans serveur.
- Les builds de l’application doivent s’exécuter dans des services cloud, et les conteneurs doivent résider dans un registre de conteneurs privé à l’échelle de l’entreprise dans le cloud.
- Le service API utilisé pour les photos d’animaux doit être précis et fiable dans le monde réel, car les décisions prises par l’application doivent être respectées dans les hôtels. Tout animal auquel l’accès est accordé est autorisé à séjourner dans les hôtels.
- Pour satisfaire aux exigences d’un pipeline DevOps, Contoso utilisera Azure DevOps pour la gestion du code source avec des dépôts Git. Des builds et mises en production automatisées seront utilisées pour générer du code et pour le déployer sur Azure App Service, Azure Functions et AKS.
- Différents pipelines CI/CD sont nécessaires pour les microservices sur le serveur backend et pour le site web sur le serveur frontal.
- Les services backend ont un cycle de mise en production différent de l’application web frontale. Pour remplir cette condition, ils déploieront deux pipelines différents.
- Contoso nécessite l’approbation de la direction pour tout le déploiement du site web frontal, et le pipeline CI/CD doit la fournir.

## <a name="solution-design"></a>Conception de la solution

Après avoir défini précisément les objectifs et exigences, Contoso conçoit et examine une solution de déploiement, et identifie le processus de migration, notamment les services Azure à utiliser pour la migration.

### <a name="current-app"></a>Application actuelle

- L’application SmartHotel360 locale est hiérarchisée sur deux machines virtuelles (WEBVM et SQLVM).
- Les machines virtuelles sont situées sur un hôte VMware ESXi **contosohost1.contoso.com** (version 6.5).
- L’environnement VMware est géré par le serveur vCenter Server 6.5 (**vcenter.contoso.com**) s’exécutant sur une machine virtuelle.
- Contoso dispose d’un centre de données local (**contoso-datacenter**), avec un contrôleur de domaine local (**contosodc1**).
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

### <a name="proposed-architecture"></a>Architecture proposée

- Le front-end de l’application est déployé en tant qu’application web Azure App Service, dans la région Azure primaire.
- Une fonction Azure fournit les chargements de photos d’animaux, et le site interagit avec cette fonctionnalité.
- La fonction de photos d’animaux utilise l’API Vision par ordinateur d’Azure Cognitive Services et Azure Cosmos DB.
- Le serveur principal du site est créé à l’aide de microservices. Ces derniers seront déployés sur des conteneurs gérés dans AKS.
- Les conteneurs seront générés à l’aide d’Azure DevOps, et envoyés à Azure Container Registry.
- Pour l’instant, Contoso déploie manuellement l’application web et le code de fonction à l’aide de Visual Studio.
- Les microservices sont déployés à l’aide d’un script PowerShell qui appelle des outils de ligne de commande de Kubernetes.

    ![Architecture du scénario](./media/contoso-migration-rebuild/architecture.png)

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant la liste des avantages et des inconvénients.

<!-- markdownlint-disable MD033 -->

**Considération** | **Détails**
--- | ---
**Avantages** | L’utilisation de solutions PaaS et sans serveur pour le déploiement de bout en bout réduit considérablement le temps de gestion pour Contoso. <br><br> La migration vers une architecture de microservices permet à Contoso d’étendre facilement la solution au fil du temps. <br><br> Les nouvelles fonctionnalités peuvent être mises en ligne sans interruption des bases de code de solutions existantes. <br><br> L’application web est configurée avec plusieurs instances sans point de défaillance unique. <br><br> La mise à l'échelle automatique sera activée afin que l’application puisse traiter les variations de volume du trafic. <br><br> Avec la migration vers des services PaaS, Contoso peut mettre hors service des solutions obsolètes s’exécutant sur le système d’exploitation Windows Server 2008 R2. <br><br> Azure Cosmos DB a une tolérance de panne intégrée qui ne nécessite aucune configuration par Contoso. Cela signifie que la couche Données n’est plus un point de basculement unique.
**Inconvénients** | Les conteneurs sont plus complexes que d’autres options de migration. La courbe d’apprentissage pourrait poser problème à Contoso. Ils introduisent un nouveau niveau de complexité qui apporte de la valeur en dépit de la courbe. <br><br> L’équipe des opérations chez Contoso doit redoubler d’efforts pour comprendre et prendre en charge Azure, les conteneurs et les microservices pour l’application. <br><br> Contoso n’a pas encore totalement implémenté le DevOps pour la solution entière. Contoso doit y réfléchir pour le déploiement de services vers AKS, Azure Functions et Azure App Service.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processus de migration

1. Contoso provisionne Azure Container Registry, AKS et Azure Cosmos DB.
2. Contoso approvisionne l’infrastructure pour le déploiement, notamment l’application web Azure App Service, le compte de stockage, la fonction et l’API.
3. Une fois l’infrastructure en place, ils vont construire leurs images conteneurs de microservices à l’aide d’Azure DevOps qui les envoie au registre de conteneurs.
4. Contoso déploiera ces microservices vers l’AKS à l’aide d’un script PowerShell.
5. Enfin, ils déploieront la fonction et l’application web.

    ![Processus de migration](./media/contoso-migration-rebuild/migration-process.png)

### <a name="azure-services"></a>Services Azure

**Service** | **Description** | **Coût**
--- | --- | ---
[AKS](https://docs.microsoft.com/sql/dma/dma-overview?view=ssdt-18vs2017) | Simplifie le déploiement, la gestion et les opérations de Kubernetes. Utilisez un service d'orchestration de conteneur Kubernetes entièrement géré. | AKS est un service gratuit. Vous payez uniquement pour les machines virtuelles, le stockage associé et la consommation des ressources réseau. [Plus d’informations](https://azure.microsoft.com/pricing/details/kubernetes-service)
[Azure Functions](https://azure.microsoft.com/services/functions) | Accélère le développement avec une expérience de calcul sans serveur pilotée par événements. Mettez à l’échelle à la demande. | Payez uniquement pour les ressources consommées. L’offre est facturée sur la base des exécutions et de la consommation de ressources par seconde. [Plus d’informations](https://azure.microsoft.com/pricing/details/functions)
[Azure Container Registry](https://azure.microsoft.com/services/container-registry) | Stocke les images pour tous types de déploiements de conteneur. | Coût basé sur les fonctionnalités, le stockage et la durée d’utilisation. [Plus d’informations](https://azure.microsoft.com/pricing/details/container-registry)
[Azure App Service](https://azure.microsoft.com/services/app-service/containers) | Créez, déployez et mettez à l’échelle rapidement des applications web, mobiles et API de classe entreprise exécutables sur toute plateforme. | Les plans App Service sont facturés par seconde. [Plus d’informations](https://azure.microsoft.com/pricing/details/app-service/windows)

## <a name="prerequisites"></a>Prérequis

Voici ce dont Contoso a besoin pour ce scénario :

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
Abonnement Azure | <li> Dans un article précédent, Contoso a créé des abonnements. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial). <li> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions. <li> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur.
Infrastructure Azure | <li> Découvrez [comment Contoso configure une infrastructure Azure](./contoso-migration-infrastructure.md).
Prérequis pour développeur | Contoso a besoin des outils suivants sur une station de travail de développeur : <li>  [Visual Studio 2017 Community Edition : Version 15.5](https://visualstudio.microsoft.com) <li> Charge de travail .NET activée. <li> [Git](https://git-scm.com) <li> [Azure PowerShell](https://azure.microsoft.com/downloads) <li> [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) <li> [Docker CE (Windows 10) ou Docker EE (Windows Server)](https://docs.docker.com/docker-for-windows/install), configurés pour utiliser des conteneurs Windows.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment Contoso exécutera la migration :

> [!div class="checklist"]
>
> - **Étape 1 : Approvisionnez AKS et Azure Container Registry.** Contoso approvisionne le cluster AKS géré et le registre de conteneurs à l’aide de PowerShell.
> - **Étape 2 : Générer des conteneurs Docker.** Ils configurent l’intégration continue (CI) pour les conteneurs Docker à l’aide d’Azure DevOps et les poussent vers le registre de conteneurs.
> - **Étape 3 : Déployer les microservices principaux.** Ils déploient le reste de l’infrastructure qu’utiliseront les microservices principaux.
> - **Étape 4 : Déployer l’infrastructure frontale.** Ils déploient l’infrastructure frontale, dont Stockage Blob pour les photos d’animaux, Azure Cosmos DB et l’API Vision par ordinateur.
> - **Étape 5 : Migrer le serveur principal.** Ils déploient les microservices et de les exécutent sur AKS pour migrer le serveur principal.
> - **Étape 6 : Publier le frontal.** Ils publient l’application SmartHotel360 sur Azure App Service, ainsi que la Function App qui sera appelée par le service de gestion des animaux.

## <a name="step-1-provision-back-end-resources"></a>Étape 1 : Approvisionner les ressources backend

Les administrateurs de Contoso exécutent un script de déploiement pour créer le cluster Kubernetes managé à l’aide d’AKS et d’Azure Container Registry.

- Les instructions de cette section utilisent le référentiel **SmartHotel360-Backend**.
- Le référentiel GitHub **SmartHotel360-Backend** contient tous les logiciels pour cette partie du déploiement.

### <a name="ensure-prerequisites"></a>Répondre aux prérequis

1. Avant de commencer, les administrateurs de Contoso s’assurent que tous les logiciels requis sont installés sur la machine de développement qu’ils utilisent pour le déploiement.
2. Ils clonent le référentiel localement sur la machine de développement à l’aide de Git :

    `git clone https://github.com/Microsoft/SmartHotel360-Backend.git`

### <a name="provision-aks-and-azure-container-registry"></a>Approvisionner AKS et Azure Container Registry

Les administrateurs de Contoso effectuent le provisionnement comme suit :

1. Ils ouvrent le dossier à l’aide de Visual Studio Code, et accèdent au répertoire **/deploy/k8s** qui contient le script **gen-aks-env.ps1**.

2. Ils exécutent le script pour créer le cluster Kubernetes géré à l’aide d’AKS et d’Azure Container Registry.

   ![AKS](./media/contoso-migration-rebuild/aks1.png)

3. Après avoir ouvert le fichier, ils mettent à jour le paramètre $location en définissant **eastus2**, puis enregistrent le fichier.

   ![AKS](./media/contoso-migration-rebuild/aks2.png)

4. Dans Visual Studio Code, ils sélectionnent **Affichage** > **Terminal intégré** pour ouvrir le terminal intégré.

   ![AKS](./media/contoso-migration-rebuild/aks3.png)

5. Dans le terminal intégré PowerShell, ils se connectent à Azure à l’aide de la commande Connect-AzureRmAccount. [Découvrez comment](https://docs.microsoft.com/powershell/azure/get-started-azureps) commencer à utiliser PowerShell.

   ![AKS](./media/contoso-migration-rebuild/aks4.png)

6. Ils authentifient Azure CLI en exécutant la commande `az login`, et en suivant les instructions pour s’authentifier à l’aide de leur navigateur web. [En savoir plus](https://docs.microsoft.com/cli/azure/authenticate-azure-cli?view=azure-cli-latest) sur la connexion avec Azure CLI.

   ![AKS](./media/contoso-migration-rebuild/aks5.png)

7. Ils exécutent la commande suivante, en passant le nom de groupe de ressources **ContosoRG**, le nom du cluster AKS **smarthotel-aks-eus2**, et le nouveau nom de registre.

   ```PowerShell
   .\gen-aks-env.ps1  -resourceGroupName ContosoRg -orchestratorName smarthotelakseus2 -registryName smarthotelacreus2
   ```

   ![AKS](./media/contoso-migration-rebuild/aks6.png)

8. Azure crée un autre groupe de ressources contenant les ressources pour le cluster AKS.

   ![AKS](./media/contoso-migration-rebuild/aks7.png)

9. Une fois le déploiement terminé, ils installent l’outil en ligne de commande `kubectl`. L’outil est déjà installé dans Azure Cloud Shell.

   `az aks install-cli`

10. Ils vérifient la connexion au cluster en exécutant la commande `kubectl get nodes`. Le nœud porte le même nom que la machine virtuelle dans le groupe de ressources créé automatiquement.

    ![AKS](./media/contoso-migration-rebuild/aks8.png)

11. Ils exécutent la commande suivante pour démarrer le tableau de bord Kubernetes :

    `az aks browse --resource-group ContosoRG --name smarthotelakseus2`

12. Un onglet de navigateur s’ouvre sur le tableau de bord. Il s’agit d’une connexion par tunnel utilisant Azure CLI.

    ![AKS](./media/contoso-migration-rebuild/aks9.png)

## <a name="step-2-configure-the-back-end-pipeline"></a>Étape 2 : Configurer le pipeline backend

### <a name="create-an-azure-devops-project-and-build"></a>Créer un projet Azure DevOps et une build

Contoso crée un projet Azure DevOps et configure une build CI pour créer le conteneur, puis transmet celui-ci au registre de conteneurs. Les instructions de cette section utilisent le référentiel [SmartHotel360-Backend](https://github.com/Microsoft/SmartHotel360-Backend).

1. À partir de visualstudio.com, ils créent une organisation (**contosodevops360.visualstudio.com**), puis la configurent pour utiliser Git.

2. Ils créent un projet (**SmartHotelBackend**) utilisant Git pour la gestion de version, et Agile pour le flux de travail.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts1.png)

3. Ils importent le [dépôt GitHub](https://github.com/Microsoft/SmartHotel360-Backend).

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts2.png)

4. Dans **Pipelines**, ils sélectionnent **Générer** et créent un pipeline en utilisant Azure Repos Git comme source, à partir du dépôt.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts3.png)

5. Ils sélectionnent l’option permettant de démarrer avec un projet vide.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts4.png)

6. Ils sélectionnent **Hosted Linux Preview** (Préversion Linux hébergée) pour le pipeline de build.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts5.png)

7. Dans **Phase 1**, ils ajoutent une tâche **Docker Compose**. Cette tâche génère le Docker compose.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts6.png)

8. Ils répètent l’opération pour ajouter une autre tâche **Docker Compose**. Celle-ci transmet les conteneurs au registre de conteneurs.

     ![Azure DevOps](./media/contoso-migration-rebuild/vsts7.png)

9. Ils sélectionnent la première tâche (générer) et configurent la build avec l’abonnement, l’autorisation et le registre de conteneurs.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts8.png)

10. Ils spécifient le chemin du fichier **docker-compose.yaml** dans le dossier **src** du dépôt. Ils sélectionnent l’option permettant de générer des images de service et incluent la dernière étiquette. Quand l’action devient **Build service images** (Générer les images de service), le nom de la tâche Azure DevOps devient **Build services automatically** (Générer les services automatiquement).

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts9.png)

11. Maintenant, ils configurent la deuxième tâche de Docker (envoyer). Ils sélectionnent l’abonnement et le registre de conteneurs **smarthotelacreus2**.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts10.png)

12. Là encore, ils entre le fichier dans le fichier docker-compose.yaml, puis sélectionnent **Push service images** (Envoyer des images de service) et incluent la dernière balise. Quand l’action devient **Push service images** (Envoyer des images de service), le nom de la tâche Azure DevOps devient **Push services automatically** (Envoyer les services automatiquement).

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts11.png)

13. Une fois les tâches Azure DevOps configurées, Contoso enregistre le pipeline de build et démarre le processus de génération.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts12.png)

14. Ils sélectionnent la tâche de build pour vérifier la progression.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts13.png)

15. Une fois la build terminée, le registre de conteneurs montre les nouveaux référentiels qui sont remplis des conteneurs utilisés par les microservices.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts14.png)

### <a name="deploy-the-back-end-infrastructure"></a>Déployer l’infrastructure backend

Une fois le cluster AKS créé et les images Docker générées, les administrateurs de Contoso déploient le reste de l’infrastructure qu’utiliseront les microservices principaux.

- Les instructions de cette section utilisent le référentiel [SmartHotel360-Backend](https://github.com/Microsoft/SmartHotel360-Backend).
- Le dossier **/deploy/k8s/arm** contient un script unique pour créer tous les éléments.

Ils déploient comme suit :

1. Ils ouvrent une invite de commandes de développeur et utilisent la commande `az login` pour l’abonnement Azure.

2. Ils utilisent le fichier deploy.cmd pour déployer les ressources Azure dans le groupe de ressources **ContosoRG** et la région **EUS2**, en tapant la commande suivante :

    ```azurecli
    .\deploy.cmd azuredeploy ContosoRG -c eastus2
    ```

    ![Déployer le serveur principal](./media/contoso-migration-rebuild/backend1.png)

3. Dans le portail Azure, ils capturent la chaîne de connexion pour chaque base de données en vue d’une utilisation ultérieure.

    ![Déployer le serveur principal](./media/contoso-migration-rebuild/backend2.png)

### <a name="create-the-back-end-release-pipeline"></a>Créer le pipeline de mise en production backend

Les administrateurs de Contoso doivent à présent procéder comme suit :

- Déployer le contrôleur d’entrée NGINX pour autoriser le trafic entrant vers les services.
- Déployer les microservices sur le cluster AKS.
- Dans un premier temps, ils mettent à jour les chaînes de connexion en fonction des microservices à l’aide d’Azure DevOps. Ensuite, ils configurent un nouveau pipeline de mise en production Azure DevOps pour déployer les microservices.
- Les instructions de cette section utilisent le référentiel [SmartHotel360-Backend](https://github.com/Microsoft/SmartHotel360-Backend).
- Certains paramètres de configuration (par exemple Active Directory B2C) ne sont pas évoqués dans cet article. Pour plus d’informations sur ces paramètres, consultez le référentiel ci-dessus.

Ils créent le pipeline :

1. À l’aide de Visual Studio, ils mettent à jour le fichier **/deploy/k8s/config_local.yml** avec les informations de connexion de base de données qu’ils ont notées précédemment.

    ![Connexions de base de données](./media/contoso-migration-rebuild/back-pipe1.png)

2. Ils ouvrent Azure DevOps et dans le projet SmartHotel360, dans **Mises en production**, ils sélectionnent **+Nouveau pipeline**.

    ![Nouveau pipeline](./media/contoso-migration-rebuild/back-pipe2.png)

3. Ils sélectionnent **Projet vide** pour démarrer le pipeline sans modèle.
4. Ils fournissent les noms de la phase et du pipeline.

      ![Nom de la phase](./media/contoso-migration-rebuild/back-pipe4.png)

      ![Nom du pipeline](./media/contoso-migration-rebuild/back-pipe5.png)

5. Ils ajoutent un artefact.

     ![Ajoutez un artefact](./media/contoso-migration-rebuild/back-pipe6.png)

6. Ils sélectionnent **Git** comme type de source, puis spécifient le projet, la source et la branche principale pour l’application SmartHotel360.

    ![Paramètres de l’artefact](./media/contoso-migration-rebuild/back-pipe7.png)

7. Ils sélectionnent le lien de tâche.

    ![Lien de tâche](./media/contoso-migration-rebuild/back-pipe8.png)

8. Ils ajoutent une nouvelle tâche Azure PowerShell afin de pouvoir exécuter un script PowerShell dans un environnement Azure.

    ![PowerShell dans Azure](./media/contoso-migration-rebuild/back-pipe9.png)

9. Ils sélectionnent l’abonnement Azure pour la tâche, puis sélectionnent le script **deploy.ps1** à partir du dépôt Git.

    ![Exécuter le script](./media/contoso-migration-rebuild/back-pipe10.png)

10. Ils ajoutent des arguments au script. Le script supprimera tout le contenu du cluster (à l’exception de **l’entrée** et du **contrôleur d’entrée**) et déploiera les microservices.

    ![Arguments de script](./media/contoso-migration-rebuild/back-pipe11.png)

11. Ils définissent la version Azure PowerShell par défaut sur la dernière version, puis enregistrent le pipeline.

12. Ils reviennent à la page **Mise en production** et créent manuellement une mise en production.

    ![Nouvelle mise en production](./media/contoso-migration-rebuild/back-pipe12.png)

13. Ils sélectionnent la mise en production après l’avoir créée et, dans **Actions**, ils sélectionnent **Déployer**.

      ![Déployer la mise en production](./media/contoso-migration-rebuild/back-pipe13.png)

14. Quand le déploiement est terminé, ils exécutent la commande suivante pour vérifier l’état des services, à l’aide d’Azure Cloud Shell : `kubectl get services`.

## <a name="step-3-provision-front-end-services"></a>Étape 3 : Provisionner les services frontaux

Les administrateurs de Contoso doivent déployer l’infrastructure qui sera utilisée par les applications frontales. Ils créent :

- Un conteneur de stockage d’objets BLOB pour stocker les images d’animaux
- Une base de données Azure Cosmos DB pour stocker des documents contenant des informations sur les animaux
- API Vision par ordinateur pour le site web.

Les instructions de cette section utilisent le dépôt [SmartHotel360-Website](https://github.com/microsoft/smartHotel360-website).

### <a name="create-blob-storage-containers"></a>Créer des conteneurs de Stockage Blob

1. Sur le portail Azure, ils ouvrent le compte de stockage créé, puis sélectionnent **Objets blob**.
2. Ils créent un conteneur **Pets** avec le niveau d’accès public défini sur conteneur. Les utilisateurs chargeront leurs photos d’animaux sur ce conteneur.

    ![Objet blob de stockage](./media/contoso-migration-rebuild/blob1.png)

3. Ils créent un deuxième conteneur nommé **Settings** (Paramètres). Un fichier contenant tous les paramètres de l’application frontale sera placé dans ce conteneur.

    ![Objet blob de stockage](./media/contoso-migration-rebuild/blob2.png)

4. Ils capturent les détails d’accès au compte de stockage dans un fichier texte pour référence ultérieure.

    ![Objet blob de stockage](./media/contoso-migration-rebuild/blob2.png)

### <a name="provision-an-azure-cosmos-db-database"></a>Provisionner une base de données Azure Cosmos DB

Les administrateurs de Contoso provisionnent une base de données Azure Cosmos DB à utiliser pour les informations sur les animaux.

1. Ils créent une **Azure Cosmos DB** dans la Place de marché Azure.

    ![Azure Cosmos DB](./media/contoso-migration-rebuild/cosmos1.png)

2. Ils spécifient un nom (**contososmarthotel**), sélectionnent l’API SQL, puis la placent dans le groupe de ressources de production **ContosoRG**, dans la région principale USA Est 2.

    ![Azure Cosmos DB](./media/contoso-migration-rebuild/cosmos2.png)

3. Ils ajoutent une nouvelle collection à la base de données, avec la capacité et le débit par défaut.

    ![Azure Cosmos DB](./media/contoso-migration-rebuild/cosmos3.png)

4. Ils notent les informations de connexion à la base de données pour référence ultérieure.

    ![Azure Cosmos DB](./media/contoso-migration-rebuild/cosmos4.png)

### <a name="provision-computer-vision"></a>Approvisionner l’API Vision par ordinateur

Les administrateurs de Contoso provisionnent l’API Vision par ordinateur. L’API est appelée par la fonction pour évaluer les images chargées par les utilisateurs.

1. Ils créent une instance de l’**API Vision par ordinateur** dans la Place de marché Azure.

     ![Vision par ordinateur](./media/contoso-migration-rebuild/vision1.png)

2. Ils approvisionnent l’API (**smarthotelpets**) dans le groupe de ressources de production **ContosoRG**, dans la région principale USA Est 2.

    ![Vision par ordinateur](./media/contoso-migration-rebuild/vision2.png)

3. Ils enregistrent les paramètres de connexion de l’API dans un fichier texte pour référence ultérieure.

     ![Vision par ordinateur](./media/contoso-migration-rebuild/vision3.png)

### <a name="provision-the-azure-web-app"></a>Provisionner l’application web Azure

Les administrateurs de Contoso provisionnent l’application web à l’aide du portail Azure.

1. Ils sélectionnent **Application web** dans le portail.

    ![Application web](./media/contoso-migration-rebuild/web-app1.png)

2. Ils fournissent un nom pour l’application (**smarthotelcontoso**), exécutent celle-ci sur Windows, puis la placent dans le groupe de ressources de production **ContosoRG**. Ils créent une instance d’Application Insights pour la supervision de l’application.

    ![Nom de l’application web](./media/contoso-migration-rebuild/web-app2.png)

3. Cela fait, ils accèdent à l’adresse de l’application pour vérifier si celle-ci a été correctement créée.

4. À présent, dans le portail Azure, ils créent un emplacement de préproduction pour le code. Le pipeline effectuera le déploiement sur cet emplacement. Ainsi, le code n’est pas mis en production tant que les administrateurs n’effectuent pas une mise en production.

    ![Emplacement de préproduction pour l’application web](./media/contoso-migration-rebuild/web-app3.png)

### <a name="provision-the-azure-function-app"></a>Provisionner l’application de fonction Azure

Dans le portail Azure, les administrateurs de Contoso provisionnent l’application de fonction.

1. Ils sélectionnent **Application de fonction**.

   ![Créer une application de fonction](./media/contoso-migration-rebuild/function-app1.png)

2. Ils fournissent un nom d’application (**smarthotelpetchecker**). Ils placent l’application dans le groupe de ressources de production **ContosoRG**. Ils configurent l’emplacement d’hébergement sur **Plan de consommation** et placent l’application dans la région USA Est 2. Un compte de stockage est créé, ainsi qu’une instance d’Application Insights pour la supervision.

   ![Paramètres Function App](./media/contoso-migration-rebuild/function-app2.png)

3. Une fois l’application déployée, ils accèdent à l’adresse de l’application pour vérifier si celle-ci a été correctement créée.

## <a name="step-4-set-up-the-front-end-pipeline"></a>Étape 4 : Configurer le pipeline frontal

Les administrateurs de Contoso créent deux projets différents pour le site frontal.

1. Dans Azure DevOps, ils créent un projet **SmartHotelFrontend**.

   ![Projet frontal](./media/contoso-migration-rebuild/function-app1.png)

2. Ils importent le référentiel Git [SmartHotel360 front-end](https://github.com/Microsoft/SmartHotel360-Website) dans le nouveau projet.

3. Pour l’application de fonction, ils créent un autre projet Azure DevOps (**SmartHotelPetChecker**), puis y importent le référentiel Git [PetChecker](https://github.com/sonahander/SmartHotel360-PetCheckerFunction).

### <a name="configure-the-web-app"></a>Configurer l’application web

À présent, les administrateurs de Contoso configurent l’application web pour utiliser des ressources Contoso.

1. Ils se connectent au projet Azure DevOps, puis clonent le référentiel localement sur la machine de développement.
2. Dans Visual Studio, ils ouvrent le dossier pour afficher tous les fichiers contenus dans le référentiel.

    ![Fichiers du dépôt](./media/contoso-migration-rebuild/configure-webapp1.png)

3. Ils mettent à jour la configuration selon les besoins.

    - Lorsque l’application web démarre, elle recherche le paramètres d’application **SettingsUrl**.
    - Cette variable doit contenir une URL pointant vers un fichier de configuration.
    - Par défaut, le paramètre utilisé est un point de terminaison public.

4. Ils mettent à jour le fichier /config-sample.json/sample.json.

    - Il s’agit du fichier de configuration pour le web en cas d’utilisation d’un point de terminaison public.
    - Ils modifient les sections **urls** et **pets_config** avec les valeurs de points de terminaison d’API AKS, des comptes de stockage et de la base de données Azure Cosmos DB.
    - Les URL doivent correspondre au nom DNS de la nouvelle application web que Contoso va créer.
    - Pour Contoso, il s’agit de **smarthotelcontoso.eastus2.cloudapp.azure.com**.

    ![Paramètres Json](./media/contoso-migration-rebuild/configure-webapp2.png)

5. Une fois le fichier mis à jour, ils le renomment **smarthotelsettingsurl**, puis le chargent dans le stockage d’objets blob créé précédemment.

    ![Renommer et charger](./media/contoso-migration-rebuild/configure-webapp3.png)

6. Ils sélectionnent le fichier pour obtenir l’URL. Cette URL est utilisée par l’application quand celle-ci extrait les fichiers de configuration.

    ![URL de l’application](./media/contoso-migration-rebuild/configure-webapp4.png)

7. Dans le fichier **appsettings.Production.json**, ils mettent à jour **SettingsURL** sur l’URL du nouveau fichier.

    ![Mettre à jour l’URL](./media/contoso-migration-rebuild/configure-webapp5.png)

### <a name="deploy-the-website-to-azure-app-service"></a>Déployer le site web sur Azure App Service

Les administrateurs de Contoso peuvent maintenant publier le site web.

1. Ils ouvrent Azure DevOps et, dans le projet **SmartHotelFrontend**, dans **Builds et mises en production**, ils sélectionnent **+Nouveau pipeline**.
2. Ils sélectionnent **Azure DevOps Git** comme source.
3. Ils sélectionnent le modèle **ASP.NET Core**.
4. Ils passent en revue le pipeline et vérifient que les options **Publier des projets web** et **Compresser les projets publiés** sont sélectionnés.

    ![Paramètres du pipeline](./media/contoso-migration-rebuild/vsts-publish-front2.png)

5. Dans **Déclencheurs**, ils activent l’intégration continue et ajoutent la branche maître. Ainsi, chaque fois que la solution a du nouveau code validé dans la branche principale, le pipeline de build démarre.

    ![Intégration continue](./media/contoso-migration-rebuild/vsts-publish-front3.png)

6. Ils sélectionnent **Enregistrer et mettre en file d’attente** pour démarrer une génération.
7. Une fois la génération terminée, ils configurent un pipeline de mise en production à l’aide du **Déploiement d’Azure App Service**.
8. Ils fournissent **Staging** (Préproduction) comme nom de phase.

    ![Nom de l’environnement](./media/contoso-migration-rebuild/vsts-publish-front4.png)

9. Ils ajoutent un artefact, puis sélectionnent la build qu’ils ont configurée.

     ![Ajoutez un artefact](./media/contoso-migration-rebuild/vsts-publish-front5.png)

10. Ils sélectionnent l’icône représentant un éclair qui se trouve sur l’artefact, puis activent le déclencheur de déploiement continu.

    ![Déploiement continu](./media/contoso-migration-rebuild/vsts-publish-front6.png)
11. Dans **Environnement**, ils sélectionnent **1 travail, 1 tâche** sous **Préproduction**.
12. Après avoir sélectionné l’abonnement et le nom de l’application, ils ouvrent la tâche **Déployer Azure App Service**. Le déploiement est configuré pour utiliser l’emplacement de déploiement de **préproduction**. Cette opération génère automatiquement le code en vue de sa revue et de son approbation dans cet emplacement.

     ![Emplacement](./media/contoso-migration-rebuild/vsts-publish-front7.png)

13. Dans le **Pipeline**, ils ajoutent une nouvelle phase.

    ![Nouvel environnement](./media/contoso-migration-rebuild/vsts-publish-front8.png)

14. Ils sélectionnent **Déploiement d’Azure App Service sur un emplacement** et nomment l’environnement **Prod**.
15. Ils sélectionnent **1 travail, 2 tâches**, l’abonnement, le nom de l’App Service, puis l’emplacement de **préproduction**.

    ![Nom de l’environnement](./media/contoso-migration-rebuild/vsts-publish-front10.png)

16. Ils suppriment du pipeline le **déploiement d’Azure App Service sur l’emplacement**. Il y avait été placé au cours des étapes précédentes.

    ![Supprimer du pipeline](./media/contoso-migration-rebuild/vsts-publish-front11.png)

17. Ils enregistrent le pipeline. Sur le pipeline, ils sélectionnent **Conditions de postdéploiement**.

    ![Postdéploiement](./media/contoso-migration-rebuild/vsts-publish-front12.png)

18. Ils activent **Approbations de postdéploiement**, puis ajoutent un responsable du développement en tant qu’approbateur.

    ![Approbations de postdéploiement](./media/contoso-migration-rebuild/vsts-publish-front13.png)

19. Dans le pipeline de build, ils lancent manuellement une build. Cette opération déclenche le nouveau pipeline de mise en production, qui déploie le site sur l’emplacement de préproduction. Pour Contoso, l’URL de l’emplacement est `https://smarthotelcontoso-staging.azurewebsites.net/`.

20. Une fois la build terminée et la mise en production déployée sur l’emplacement, Azure DevOps envoie un e-mail au responsable du développement pour recueillir son approbation.

21. Le responsable du développement sélectionne **Afficher l’approbation** et peut approuver ou rejeter la demande dans le portail Azure DevOps.

    ![E-mail d’approbation](./media/contoso-migration-rebuild/vsts-publish-front14.png)

22. Le responsable écrit un commentaire, puis approuve. Cette opération démarre l’échange des emplacements de **préproduction** et de **production**, puis place la build en production.

    ![Approuver et échanger](./media/contoso-migration-rebuild/vsts-publish-front15.png)

23. Le pipeline termine l’échange.

    ![Échange effectué](./media/contoso-migration-rebuild/vsts-publish-front16.png)

24. L’équipe vérifie l’emplacement de **production** pour s’assurer que l’application web est en production à l’adresse `https://smarthotelcontoso.azurewebsites.net/`.

### <a name="deploy-the-petchecker-function-app"></a>Déployer l’application de fonction PetChecker

Les administrateurs de Contoso déploient l’application comme suit.

1. Ils clonent le dépôt localement sur la machine de développement en se connectant au projet Azure DevOps.
2. Dans Visual Studio, ils ouvrent le dossier pour afficher tous les fichiers contenus dans le référentiel.
3. Ils ouvrent le fichier **src/PetCheckerFunction/local.settings.json**, puis ajoutent les paramètres d’application pour le stockage, la base de données Azure Cosmos DB et l’API Vision par ordinateur.

    ![Déployer la fonction](./media/contoso-migration-rebuild/function5.png)

4. Ils valident le code, puis le synchronisent sur Azure DevOps, en envoyant (push) leurs modifications.
5. Ils ajoutent un nouveau pipeline de build, puis sélectionnent **Azure DevOps Git** comme source.
6. Ils sélectionnent le modèle **ASP.NET Core (.NET Framework)** .
7. Ils acceptent les valeurs par défaut pour le modèle.
8. Dans **Déclencheurs**, ils sélectionnent **Activer l’intégration continue**, puis **Enregistrer et mettre en file d’attente** pour démarrer une build.
9. Une fois la build terminée, ils génèrent un pipeline de mise en production et y ajoutent le **déploiement d’Azure App Service sur un emplacement**.
10. Ils nomment l’environnement **Prod**, puis sélectionnent l’abonnement. Ils définissent le **Type d’application** sur **Application de fonction** et nomment l’App Service **smarthotelpetchecker**.

    ![Conteneur de fonctions](./media/contoso-migration-rebuild/petchecker2.png)

11. Ils ajoutent un artefact **Build**.

    ![Artefact](./media/contoso-migration-rebuild/petchecker3.png)

12. Ils activent **Déclencheur de déploiement continu**, puis sélectionnent **Enregistrer**.
13. Ils sélectionnent **Mettre en file d’attente une nouvelle build** pour exécuter le pipeline CI/CD complet.
14. Une fois déployée, la fonction apparaît dans le portail Azure, avec l’état **En cours d’exécution**.

    ![Déployer la fonction](./media/contoso-migration-rebuild/function6.png)

15. Ils accèdent à l’application pour vérifier que l’intelligence artificielle de Pet Checker (Vérificateur d’animaux) fonctionne comme prévu sur `http://smarthotel360public.azurewebsites.net/pets`.

16. Ils sélectionnent l’avatar pour charger une image.

    ![Déployer la fonction](./media/contoso-migration-rebuild/function7.png)

17. La première photo qu'ils souhaitent vérifier est celle d’un petit chien.

    ![Déployer la fonction](./media/contoso-migration-rebuild/function8.png)

18. L’application renvoie un message d’acceptation.

    ![Déployer la fonction](./media/contoso-migration-rebuild/function9.png)

## <a name="review-the-deployment"></a>Examiner le déploiement

Une fois les ressources migrées dans Azure, Contoso doit rendre la nouvelle infrastructure entièrement opérationnelle et la sécuriser.

### <a name="security"></a>Sécurité

- Contoso doit s’assurer que les nouvelles bases de données sont sécurisées. [Plus d’informations](https://docs.microsoft.com/azure/sql-database/sql-database-security-overview)
- L’application doit être mise à jour pour utiliser le protocole SSL avec des certificats. L’instance de conteneur doit être redéployée pour répondre sur le port 443.
- Contoso devrait envisager d’utiliser Key Vault pour protéger les secrets de ses applications Service Fabric. [Plus d’informations](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-secret-management)

### <a name="backups-and-disaster-recovery"></a>Sauvegardes et récupération d’urgence

- Contoso doit examiner les [besoins de sauvegarde de la base de données Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).
- Contoso devrait envisager d’implémenter des [groupes de basculement SQL afin de fournir un basculement régional pour la base de données](https://docs.microsoft.com/azure/sql-database/sql-database-auto-failover-group).
- Contoso peut utiliser la [géoréplication pour la référence (SKU) premium d’Azure Container Registry](https://docs.microsoft.com/azure/container-registry/container-registry-geo-replication).
- Azure Cosmos DB est sauvegardé automatiquement. Contoso peut [en savoir plus](https://docs.microsoft.com/azure/cosmos-db/online-backup-and-restore) sur ce processus.

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

- Une fois toutes les ressources déployées, Contoso doit affecter des balises Azure en fonction de la [planification de son infrastructure](./contoso-migration-infrastructure.md#set-up-tagging).
- Toutes les licences sont intégrées dans le coût des services PaaS que Contoso consomme. Cela sera déduit de l’Accord Entreprise.
- Contoso permettra à [Azure Cost Management](https://docs.microsoft.com/azure/cost-management-billing/cost-management-billing-overview) d’analyser et de gérer les ressources Azure.

## <a name="conclusion"></a>Conclusion

Dans cet article, Contoso regénère l’application SmartHotel360 dans Azure. La machine virtuelle frontale de l’application locale est regénérée sur Web Apps dans les applications web Azure App Service. Le backend de l'application est généré à l’aide de microservices déployés sur des conteneurs gérés par Azure Kubernetes Service (AKS). Contoso a amélioré les fonctionnalités de l’application avec une application de photo d’animaux.

## <a name="suggested-skills"></a>Compétences suggérées

Microsoft Learn est une nouvelle approche de l’apprentissage. La préparation aux nouvelles compétences et responsabilités qui accompagnent l’adoption du cloud n’est pas facile. Microsoft Learn offre une approche plus gratifiante de l’apprentissage pratique qui vous permet d’atteindre vos objectifs plus rapidement. Gagnez des points et des niveaux et accomplissez davantage.

Voici plusieurs exemples de parcours d’apprentissage personnalisés sur Microsoft Learn en ligne avec l’application Contoso SmartHotel360 dans Azure.

- **[Déployer un site web sur Azure avec Azure App Service ](https://docs.microsoft.com/learn/paths/deploy-a-website-with-azure-app-service):** Web Apps dans Azure vous permet de publier et de gérer votre site web facilement sans avoir à utiliser les ressources réseau, stockage ou serveurs sous-jacents. Vous pouvez donc vous concentrer sur les fonctionnalités de votre site web et vous appuyer sur la plateforme Azure robuste pour fournir un accès sécurisé à votre site.

- **[Traitez et classifiez les images avec les services Azure Cognitive Vision ](https://docs.microsoft.com/learn/paths/classify-images-with-vision-services):** Azure Cognitive Services propose des fonctionnalités prédéfinies pour activer la vision par ordinateur dans vos applications. Découvrez comment utiliser les services Cognitive Vision pour détecter des visages, étiqueter et classifier des images, et identifier des objets.
