---
title: Restructurer une application dans un conteneur Azure et Azure SQL Database
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment Contoso réarchitecture une application dans des conteneurs Microsoft Azure et Azure SQL Database.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 6b9d2e5f4b230358985d04aca075cb89e8214422
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70837995"
---
# <a name="rearchitect-an-on-premises-app-to-an-azure-container-and-azure-sql-database"></a>Réarchitecturer une application locale dans un conteneur Azure et Azure SQL Database

Cet article explique comment la société fictive Contoso réarchitecture une application Windows .NET à deux niveaux qui s’exécute sur des machines virtuelles VMware dans le cadre d’une migration vers Azure. Contoso migre la machine virtuelle frontale de l’application vers un conteneur Microsoft Azure et la base de données de l’application vers une base de données Azure SQL.

L’application SmartHotel360 utilisée dans cet exemple est fournie au format open source. Si vous souhaitez l’utiliser à des fins de test, vous pouvez la télécharger à partir de [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat souhaité avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso étant en croissance, son infrastructure et ses systèmes locaux subissent une pression.
- **Gagner en efficacité.** Contoso doit supprimer les procédures inutiles et rationaliser les processus pour les développeurs et les utilisateurs. L’entreprise a besoin d’une informatique rapide et doit éviter de perdre du temps ou d’argent en répondant plus rapidement aux exigences des clients.
- **Gagner en agilité.** le service informatique de Contoso doit être plus réactif face aux besoins de l’entreprise. Elle doit être en mesure de réagir plus rapidement que l’évolution du marché pour réussir dans une économie mondiale. L’informatique ne doit pas devenir une entrave à l’activité.
- **Mise à l’échelle** à mesure que l’entreprise croît, le service informatique de Contoso doit fournir des systèmes capables de croître au même rythme.
- **Réduire les coûts.** Contoso souhaite réduire les coûts de licence.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a épinglé les objectifs de cette migration. Ces objectifs ont été utilisés pour déterminer la meilleure méthode de migration.

<!-- markdownlint-disable MD033 -->

**Objectifs** | **Détails**
--- | ---
**Exigences d’application** | L’application dans Azure restera aussi critique qu’aujourd’hui.<br/><br/> Elle doit offrir le même niveau de performance qu’actuellement dans VMware.<br/><br/> Contoso ne veut plus prendre en charge Windows Server 2008 R2, sur lequel l’application s’exécute actuellement, et est disposé à investir dans l’application.<br/><br/> Contoso veut passer de SQL Server 2008 R2 à une plateforme de base de données PaaS moderne pour réduire les besoins de gestion.<br/><br/> Contoso souhaite tirer parti autant que possible de son investissement dans les licences SQL Server et dans Software Assurance.<br/><br/> Contoso veut pouvoir faire monter en puissance la couche web de l’application.
**Limitations** | L’application consiste en une application ASP.NET et un service WCF (Windows Communication Foundation) s’exécutant sur la même machine virtuelle. Contoso veut la fractionner en deux applications web à l’aide d’Azure App Service.
**Exigences Azure** | Contoso veut déplacer l’application vers Azure et l’exécuter dans un conteneur pour étendre sa durée de vie. L’entreprise ne veut pas tout reprendre à zéro pour implémenter l’application dans Azure.
**DevOps** | Contoso veut passer à un modèle DevOps en utilisant Azure DevOps Services pour les builds de code et le pipeline de mise en production.

<!-- markdownlint-enable MD033 -->

## <a name="solution-design"></a>Conception de la solution

Après avoir défini précisément les objectifs et les exigences, Contoso conçoit et examine une solution de déploiement et identifie le processus de migration, notamment les services Azure qui seront utilisés pour la migration.

### <a name="current-app"></a>Application actuelle

- L’application SmartHotel360 locale est hiérarchisée sur deux machines virtuelles (WEBVM et SQLVM).
- Les machines virtuelles sont situées sur un hôte VMware ESXi **contosohost1.contoso.com** (version 6.5).
- L’environnement VMware est géré par le serveur vCenter Server 6.5 (**vcenter.contoso.com**) s’exécutant sur une machine virtuelle.
- Contoso dispose d’un centre de données local (contoso-datacenter), avec un contrôleur de domaine local (**contosodc1**).
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

### <a name="proposed-architecture"></a>Architecture proposée

- Pour la couche Base de données de l’application, Contoso a comparé Azure SQL Database à SQL Server en se basant sur [cet article](/azure/sql-database/sql-database-features). L’entreprise a choisi d’utiliser Azure SQL Database pour plusieurs raisons :
  - Azure SQL Database est un service managé de base de données relationnelle. Il offre des performances prévisibles à plusieurs niveaux de service, et ne nécessite pratiquement aucune administration. Ses avantages sont une extensibilité dynamique sans aucun temps d’arrêt, une optimisation intelligente intégrée, ainsi qu’une scalabilité et une disponibilité globales.
  - Contoso utilise l’Assistant Migration de données (DMA) facile d’utilisation pour évaluer et migrer la base de données locale vers SQL Azure.
  - Grâce à Software Assurance, Contoso peut échanger ses licences existantes contre une réduction de tarif sur SQL Database, en utilisant Azure Hybrid Benefit pour SQL Server. Cela pourrait leur permettre de réaliser jusqu’à 30 % d’économies.
  - Azure SQL Database fournit plusieurs fonctionnalités de sécurité, notamment le chiffrement permanent, le masquage dynamique des données, la sécurité au niveau des lignes et la détection des menaces.
- Concernant la couche web de l’application, Contoso a décidé de la convertir en conteneur Windows à l’aide d’Azure DevOps Services.
  - Contoso utilise Azure Service Fabric pour déployer l’application et tire l’image conteneur Windows d’Azure Container Registry (ACR).
  - Un prototype visant à étendre l’application pour qu’elle inclue l’analyse des sentiments sera implémenté en tant que service distinct dans Service Fabric, connecté à Cosmos DB. Celui-ci lira les informations de Tweets et affichera des données sur l’application.
- Afin d’implémenter un pipeline DevOps, Contoso utilise Azure DevOps pour la gestion du code source ainsi que des dépôts Git. Des builds et des mises en production automatiques sont utilisées pour générer du code, et le déployer sur Azure Container Registry et Azure Service Fabric.

    ![Architecture du scénario](./media/contoso-migration-rearchitect-container-sql/architecture.png)

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant une liste des avantages et des inconvénients.

<!-- markdownlint-disable MD033 -->

**Considération** | **Détails**
--- | ---
**Avantages** | Le code de l’application SmartHotel360 doit être modifié pour la migration vers Azure Service Fabric. Toutefois, l’effort est minimal, car on utilisera les outils du SDK Service Fabric pour les modifications.<br/><br/> En passant à Service Fabric, Contoso peut commencer à développer rapidement des microservices à ajouter à l’application au fil du temps, sans risque pour la base de code d’origine.<br/><br/> Les conteneurs Windows offrent les mêmes avantages que les conteneurs standard. Ils améliorent la portabilité, la flexibilité et le contrôle.<br/><br/> Contoso peut tirer parti de son investissement dans Software Assurance en utilisant Azure Hybrid Benefit tant pour SQL Server que pour Windows Server.<br/><br/> Après la migration, l’entreprise n’a plus besoin de prendre en charge Windows Server 2008 R2. [Plus d’informations](https://support.microsoft.com/lifecycle)<br/><br/> Contoso peut configurer la couche web de l’application avec plusieurs instances, pour qu’elle ne constitue plus un point de défaillance unique.<br/><br/> Elle ne dépendra plus de SQL Server 2008 R2, qui est une version déjà ancienne.<br/><br/> Azure SQL Database répond aux exigences techniques de Contoso. Les administrateurs de Contoso ont évalué la base de données locale à l’aide de l’Assistant Migration de données et découvert qu’elle était compatible.<br/><br/> SQL Database intègre une tolérance de panne que Contoso n’a pas besoin de configurer. Cela signifie que la couche Données n’est plus un point de basculement unique.
**Inconvénients** | Les conteneurs sont plus complexes que d’autres options de migration. La courbe d’apprentissage pour les conteneurs pourrait poser problème à Contoso. Ils introduisent un nouveau niveau de complexité qui apporte beaucoup de valeur en dépit de la courbe.<br/><br/> L’équipe des opérations chez Contoso devra redoubler d’efforts pour comprendre et prendre en charge Azure, les conteneurs et les microservices pour l’application.<br/><br/> Si Contoso utilise l’Assistant Migration de données au lieu d’Azure Database Migration Service pour migrer la base de données, elle ne disposera pas d’une infrastructure prête pour la migration de bases de données à l’échelle.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processus de migration

1. Contoso provisionne le cluster Azure Service Fabric pour Windows.
2. Il provisionne une instance SQL Azure et y migre la base de données SmartHotel360.
3. Contoso convertit la machine virtuelle de couche web en conteneur Docker à l’aide des outils du SDK Service Fabric.
4. Contoso connecte le cluster Service Fabric et l’ACR, et déploie l’application à l’aide d’Azure Service Fabric.

    ![Processus de migration](./media/contoso-migration-rearchitect-container-sql/migration-process.png)

### <a name="azure-services"></a>Services Azure

**Service** | **Description** | **Coût**
--- | --- | ---
[Assistant Migration de données (DMA)](/sql/dma/dma-overview?view=ssdt-18vs2017) | Évalue et détecte les problèmes de compatibilité qui peuvent avoir un impact sur les fonctionnalités de base de données dans Azure. DMA évalue la parité des fonctionnalités entre SQL sources et cibles, et recommande des améliorations des performances et de la fiabilité. | Cet outil est téléchargeable gratuitement.
[Azure SQL Database](https://azure.microsoft.com/services/sql-database) | Fournit un service de base de données cloud relationnelle entièrement managé et intelligent. | Coût basé sur les fonctionnalités, le débit et la taille. [Plus d’informations](https://azure.microsoft.com/pricing/details/sql-database/managed)
[Azure Container Registry](https://azure.microsoft.com/services/container-registry) | Stocke les images pour tous types de déploiements de conteneur. | Coût basé sur les fonctionnalités, le stockage et la durée d’utilisation. [Plus d’informations](https://azure.microsoft.com/pricing/details/container-registry)
[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric) | Génère et exploite des applications distribuées, scalables et toujours disponibles | Coûts basé sur la taille, l’emplacement et la durée des nœuds de calcul. [Plus d’informations](https://azure.microsoft.com/pricing/details/service-fabric)
[Azure DevOps](/azure/azure-portal/tutorial-azureportal-devops) | Fournit un pipeline d’intégration et de déploiement continus (CI/CD) pour le développement d’applications. Le pipeline démarre avec un dépôt Git pour la gestion du code de l’application, un système de build pour la production de packages et d’autres artefacts de build, et un système Release Management pour le déploiement de modifications sur les environnements de production, de test et de développement.

## <a name="prerequisites"></a>Prérequis

Voici ce dont Contoso a besoin pour exécuter ce scénario :

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
**Abonnement Azure** | Contoso a créé des abonnements plus tôt dans cette série d’articles. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions.<br/><br/> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur.
**Infrastructure Azure** | [Découvrez comment](contoso-migration-infrastructure.md) Contoso a configuré une infrastructure Azure.
**Prérequis pour développeur** | Contoso a besoin des outils suivants sur une station de travail de développeur :<br/><br/> - [Visual Studio 2017 Community Edition : Version 15.5](https://www.visualstudio.com)<br/><br/> - Charge de travail .NET activée.<br/><br/> - [Git](https://git-scm.com)<br/><br/> - [SDK Service Fabric v 3.0 ou ultérieure](/azure/service-fabric/service-fabric-get-started)<br/><br/> - [Docker CE (Windows 10) ou Docker EE (Windows Server)](https://docs.docker.com/docker-for-windows/install), configurés pour utiliser des conteneurs Windows.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment Contoso exécute la migration :

> [!div class="checklist"]
>
> - **Étape 1 : Approvisionner une instance SQL Database dans Azure.** Contoso approvisionne une instance SQL dans Azure. Une fois la machine virtuelle web frontale migrée vers un conteneur Azure, l’instance de conteneur avec l’application web frontale pointe vers cette base de données.
> - **Étape 2 : Créer un Azure Container Registry (ACR).** Contoso provisionne un registre de conteneurs d’entreprise pour les images conteneur Docker.
> - **Étape 3 : Approvisionner Azure Service Fabric.** Il provisionne un cluster Service Fabric.
> - **Étape 4 : Gérer les certificats Service Fabric.** Contoso configure des certificats pour l’accès d’Azure DevOps Services au cluster.
> - **Étape 5 : Migrer la base de données avec DMA.** Elle migre la base de données de l’application à l’aide de l’Assistant Migration de données.
> - **Étape 6 : Configurer Azure DevOps Services.** Contoso configure un nouveau projet dans Azure DevOps Services et importe le code dans le dépôt Git.
> - **Étape 7 : Convertir l’application.** Contoso convertit l’application en conteneur à l’aide d’Azure DevOps et de SDK Tools.
> - **Étape 8 : Configurer le build et la mise en production.** Contoso configure les pipelines de build et de mise en production pour créer et publier l’application sur l’ACR et le cluster Service Fabric.
> - **Étape 9 : Étendre l’application.** Une fois l’application publique, Contoso l’étend pour tirer parti des fonctionnalités Azure et la republie sur Azure à l’aide du pipeline.

## <a name="step-1-provision-an-azure-sql-database"></a>Étape 1 : Provisionner une base de données Azure SQL

Les administrateurs de Contoso provisionnent une base de données Azure SQL.

1. Ils choisissent de créer une **base de données SQL** dans Azure.

    ![Provisionner SQL](./media/contoso-migration-rearchitect-container-sql/provision-sql1.png)

2. Ils spécifient un nom de base de données correspondant à la base de données en cours d’exécution sur la machine virtuelle locale (**SmartHotel.Registration**). Ils placent la base de données dans le groupe de ressources ContosoRG. Il s’agit du groupe de ressources qu’ils utilisent pour les ressources de production dans Azure.

    ![Provisionner SQL](./media/contoso-migration-rearchitect-container-sql/provision-sql2.png)

3. Ils configurent une nouvelle instance de SQL Server (**sql-smarthotel-eus2**) dans la région primaire.

    ![Provisionner SQL](./media/contoso-migration-rearchitect-container-sql/provision-sql3.png)

4. Ils définissent le niveau tarifaire pour qu’il corresponde à leurs besoins en matière de serveur et de base de données. Et ils choisissent d’économiser de l’argent avec Azure Hybrid Benefit, car ils ont déjà une licence SQL Server.
5. Pour le dimensionnement, ils achètent en fonction du nombre de v-Core et définissent les limites des exigences attendues.

    ![Provisionner SQL](./media/contoso-migration-rearchitect-container-sql/provision-sql4.png)

6. Ils créent ensuite l’instance de base de données.

    ![Provisionner SQL](./media/contoso-migration-rearchitect-container-sql/provision-sql5.png)

7. Une fois l’instance créée, ils ouvrent la base de données et notent les informations dont ils auront besoin quand ils utiliseront l’Assistant Migration de données pour la migration.

    ![Provisionner SQL](./media/contoso-migration-rearchitect-container-sql/provision-sql6.png)

**Besoin de plus d’aide ?**

- [Obtenir de l’aide](/azure/sql-database/sql-database-get-started-portal) pour le provisionnement d’une base de données SQL.
- [En savoir plus](/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools) sur les limites de ressources v-Core.

## <a name="step-2-create-an-acr-and-provision-an-azure-container"></a>Étape 2 : Créer un ACR et provisionner un conteneur Azure

Le conteneur Azure est créé à l’aide des fichiers exportés à partir de la machine virtuelle web. Le conteneur est hébergé dans Azure Container Registry (ACR).

1. Les administrateurs de Contoso créent un registre de conteneurs dans le portail Azure.

     ![Container Registry](./media/contoso-migration-rearchitect-container-sql/container-registry1.png)

2. Ils fournissent un nom pour le registre (**contosoacreus2**) et le placent dans la région primaire, dans le groupe de ressources qu’ils utilisent pour leurs ressources d’infrastructure. Ils activent l’accès pour les utilisateurs administrateurs et le configurent comme une référence SKU premium afin de pouvoir utiliser la géoréplication.

    ![Container Registry](./media/contoso-migration-rearchitect-container-sql/container-registry2.png)

## <a name="step-3-provision-azure-service-fabric"></a>Étape 3 : Provisionner Azure Service Fabric

Le conteneur SmartHotel360 s’exécutera dans le cluster Azure Service Fabric. Les administrateurs de Contoso créent le cluster Service Fabric de la façon suivante :

1. Créer une ressource Service Fabric à partir de la Place de marché Azure.

     ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric1.png)

2. Dans **De base**, ils fournissent un nom de service d’annuaire unique pour le cluster et des informations d’identification pour accéder à la machine virtuelle locale. Ils placent la ressource dans le groupe de ressources de production (**ContosoRG**) dans la région primaire USA Est 2.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric2.png)

3. Dans **Configuration du type de nœud**, ils entrent un nom de type de nœud, des paramètres de durabilité, la taille de machine virtuelle et les points de terminaison d’application.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric3.png)

4. Dans **Créer un coffre de clés**, ils créent un coffre de clés dans leur groupe de ressources d’infrastructure pour héberger le certificat.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric4.png)

5. Dans **Stratégies d’accès**, ils activent l’accès aux machines virtuelles pour déployer le coffre de clés.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric5.png)

6. Ils spécifient un nom pour le certificat.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric6.png)

7. Dans la page de synthèse, ils copient le lien qui est utilisé pour télécharger le certificat. Ils en ont besoin pour se connecter au cluster Service Fabric.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric7.png)

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric8.png)

8. Une fois la validation effectuée, ils provisionnent le cluster.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric9.png)

9. Dans l’Assistant Importation de certificat, ils importent le certificat téléchargé sur les ordinateurs de développement. Le certificat est utilisé pour l’authentification auprès du cluster.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric10.png)

10. Une fois le cluster provisionné, ils se connectent à l’Explorateur de clusters Service Fabric.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric11.png)

11. Ils doivent sélectionner le certificat approprié.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric12.png)

12. Service Fabric Explorer se charge, et l’administrateur Contoso peut gérer le cluster.

    ![Service Fabric](./media/contoso-migration-rearchitect-container-sql/service-fabric13.png)

## <a name="step-4-manage-service-fabric-certificates"></a>Étape 4 : Gérer les certificats Service Fabric

Contoso a besoin de certificats de cluster pour autoriser l’accès d’Azure DevOps Services au cluster. Les administrateurs de Contoso configurent cela.

1. Ils ouvrent le Portail Azure et accèdent au coffre de clés.
2. Ils ouvrent les certificats et copient l’empreinte du certificat qui a été créé pendant le processus de provisionnement.

    ![Copier l’empreinte](./media/contoso-migration-rearchitect-container-sql/cert1.png)

3. Ils la copient dans un fichier texte pour référence ultérieure.
4. À présent, ils ajoutent un certificat client en guise de certificat client d’administration sur le cluster. Azure DevOps Services peut alors se connecter au cluster pour déployer des applications dans le pipeline de mise en production. Pour ce faire, ils ouvrent le coffre de clés dans le portail, puis sélectionnent **Certificats** > **Générer/Importer**.

    ![Générer le certificat client](./media/contoso-migration-rearchitect-container-sql/cert2.png)

5. Ils entrent le nom du certificat et fournissent un nom unique X.509 dans **Sujet**.

     ![Nom du certificat](./media/contoso-migration-rearchitect-container-sql/cert3.png)

6. Une fois le certificat créé, ils le téléchargent localement au format PFX.

     ![Télécharger le certificat](./media/contoso-migration-rearchitect-container-sql/cert4.png)

7. À présent, ils reviennent à la liste de certificats dans le coffre de clés et copient l’empreinte du certificat client qui vient d’être créé. Ils l’enregistrent dans le fichier texte.

     ![Empreinte du certificat client](./media/contoso-migration-rearchitect-container-sql/cert5.png)

8. Pour le déploiement d’Azure DevOps Services, ils doivent déterminer la valeur Base64 du certificat. Ils le font sur la station de travail locale du développeur à l’aide de PowerShell. Ils collent la sortie dans un fichier texte pour une utilisation ultérieure.

    ```powershell
    [System.Convert]::ToBase64String([System.IO.File]::ReadAllBytes("C:\path\to\certificate.pfx"))
    ```

     ![Valeur base64](./media/contoso-migration-rearchitect-container-sql/cert6.png)

9. Enfin, ils ajoutent le nouveau certificat au cluster Service Fabric. Pour ce faire, ils ouvrent le cluster dans le portail et sélectionnent **Sécurité**.

     ![Ajouter un certificat client](./media/contoso-migration-rearchitect-container-sql/cert7.png)

10. Ils sélectionnent **Ajouter** > **Client administrateur** et collent l’empreinte du nouveau certificat client. Puis, ils sélectionnent **Ajouter**. Cette opération peut durer jusqu’à 15 minutes.

     ![Ajouter un certificat client](./media/contoso-migration-rearchitect-container-sql/cert8.png)

## <a name="step-5-migrate-the-database-with-dma"></a>Étape 5 : Migrer la base de données avec le DMA

Les administrateurs Contoso peuvent maintenant migrer la base de données SmartHotel360 avec DMA.

### <a name="install-dma"></a>Installer DMA

1. Télécharger l’outil à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53595) sur la machine virtuelle locale SQL Server (**SQLVM**).
2. Exécuter le programme d’installation (DownloadMigrationAssistant.msi) sur la machine virtuelle.
3. Dans la page **Terminer**, sélectionner **Lancer l’Assistant Migration de données Microsoft** avant la fin de l’exécution de l’Assistant.

### <a name="configure-the-firewall"></a>Configurer le pare-feu

Pour se connecter à Azure SQL Database, les administrateurs de Contoso configurent une règle de pare-feu pour autoriser l’accès.

1. Dans les propriétés de **Pare-feu et réseaux virtuels** de la base de données, ils autorisent l’accès aux services Azure et ajoutent une règle pour l’adresse IP cliente de la machine virtuelle SQL Server locale.
2. Une règle de pare-feu au niveau du serveur est créée.

    ![Pare-feu](./media/contoso-migration-rearchitect-container-sql/sql-firewall.png)

**Besoin de plus d’aide ?**

[Découvrez](/azure/sql-database/sql-database-firewall-configure) la création et la gestion des règles de pare-feu pour Azure SQL Database.

### <a name="migrate"></a>Migrer

Les administrateurs de Contoso migrent maintenant la base de données.

1. Dans DMA, ils créent un projet (**SmartHotelDB**), puis sélectionnent **Migration**.
2. Ils sélectionnent le type de serveur source **SQL Server** et la cible **Azure SQL Database**.

    ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-1.png)

3. Dans les détails de la migration, ils ajoutent **SQLVM** comme serveur source, et la base de données **SmartHotel.Registration**.

     ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-2.png)

4. Ils reçoivent un message d’erreur qui semble être associé à l’authentification. Toutefois, après examen, le problème résulte de la présence d’un point (.) dans le nom de la base de données. Pour résoudre ce problème, ils décident de provisionner une nouvelle base de données SQL en utilisant le nom **SmartHotel-Registration**. Quand ils réexécutent DMA, ils peuvent sélectionner **SmartHotel-Registration** et continuer avec l’Assistant.

    ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-3.png)

5. Dans **Sélectionner des objets**, ils sélectionnent les tables de base de données et génèrent un script SQL.

    ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-4.png)

6. Une fois que DMA a créé le script, ils sélectionnent **Déployer le schéma**.

    ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-5.png)

7. DMA vérifie que le déploiement a réussi.

    ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-6.png)

8. À présent, ils commencent la migration.

    ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-7.png)

9. Une fois la migration terminée, Contoso peut vérifier que la base de données est en cours d’exécution sur l’instance SQL Azure.

     ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-8.png)

10. Ils suppriment la base de données SQL supplémentaire **SmartHotel.Registration** dans le portail Azure.

     ![DMA](./media/contoso-migration-rearchitect-container-sql/dma-9.png)

## <a name="step-6-set-up-azure-devops-services"></a>Étape 6 : Configurer Azure DevOps Services

Contoso doit générer l’infrastructure et les pipelines DevOps pour l’application. Pour ce faire, les administrateurs de Contoso créent un projet Azure DevOps, importent leur code, puis les pipelines de build et de mise en production.

1. Dans le compte Azure DevOps de Contoso, ils créent un projet (**ContosoSmartHotelRearchitect**) et sélectionnent **Git** pour la gestion de versions.
![Nouveau projet](./media/contoso-migration-rearchitect-container-sql/vsts1.png)

2. Ils importent le dépôt Git qui détient actuellement leur code d’application. Il se trouve dans un [dépôt public](https://github.com/Microsoft/SmartHotel360-internal-booking-apps) que vous pouvez télécharger.

    ![Télécharger le code d’application](./media/contoso-migration-rearchitect-container-sql/vsts2.png)

3. Une fois le code importé, ils connectent Visual Studio au dépôt et clonent le code à l’aide de Team Explorer.

4. Une fois le référentiel cloné sur la machine du développeur, ils ouvrent le fichier Solution de l’application. L’application web et le service wcf ont chacun un projet distinct dans le fichier.

    ![Fichier solution](./media/contoso-migration-rearchitect-container-sql/vsts4.png)

## <a name="step-7-convert-the-app-to-a-container"></a>Étape 7 : Convertir l’application en conteneur

L’application locale est une application à trois niveaux traditionnelle :

- Elle contient des Web Forms et un service WCF se connectant à SQL Server.
- Elle utilise Entity Framework pour l’intégration aux données dans la base de données SQL, et les expose au moyen d’un service WCF.
- L’application Web Forms interagit avec le service WCF.

Les administrateurs de Contoso convertissent l’application en conteneur à l’aide de Visual Studio et SDK Tools de la façon suivante :

1. À l’aide de Visual Studio, ils examinent le fichier solution (SmartHotel.Registration.sln) dans le répertoire **SmartHotel360-internal-booking-apps\src\Registration** du dépôt local. Deux applications sont affichées. L’application web frontale SmartHotel.Registration.Web et l’application de service WCF SmartHotel.Registration.WCF.

    ![Conteneur](./media/contoso-migration-rearchitect-container-sql/container2.png)

2. Ils cliquent avec le bouton droit sur l’application web > **Ajouter** > **Prise en charge des orchestrateurs de conteneurs**.
3. Dans **Ajouter la prise en charge des orchestrateurs de conteneurs**, ils sélectionnent **Service Fabric**.

    ![Conteneur](./media/contoso-migration-rearchitect-container-sql/container3.png)

4. Ils répètent le processus pour l’application SmartHotel.Registration.WCF.
5. Maintenant, ils observent les changements de l’application.

    - La nouvelle application est **SmartHotel.RegistrationApplication/** .
    - Elle inclut deux services : **SmartHotel.Registration.WCF** et **SmartHotel.Registration.Web**.

    ![Conteneur](./media/contoso-migration-rearchitect-container-sql/container4.png)

6. Visual Studio a créé le fichier Docker et extrait les images nécessaires localement sur l’ordinateur du développeur.

    ![Conteneur](./media/contoso-migration-rearchitect-container-sql/container5.png)

7. Un fichier manifeste (**ServiceManifest.xml**) est créé et ouvert par Visual Studio. Ce fichier indique à Service Fabric comment configurer le conteneur quand il est déployé sur Azure.

    ![Conteneur](./media/contoso-migration-rearchitect-container-sql/container6.png)

8. Un autre fichier manifeste (**ApplicationManifest.xml) contient les applications de configuration pour les conteneurs.

    ![Conteneur](./media/contoso-migration-rearchitect-container-sql/container7.png)

9. Ils ouvrent le fichier **ApplicationParameters/Cloud.xml** et mettent à jour la chaîne de connexion pour connecter l’application à la base de données Azure SQL. La chaîne de connexion se trouve dans la base de données dans le portail Azure.

    ![Chaîne de connexion](./media/contoso-migration-rearchitect-container-sql/container8.png)

10. Ils valident le code mis à jour et l’envoient (push) vers Azure DevOps Services.

    ![Validation](./media/contoso-migration-rearchitect-container-sql/container9.png)

## <a name="step-8-build-and-release-pipelines-in-azure-devops-services"></a>Étape 8 : Pipelines de build et de mise en production dans Azure DevOps Services

Les administrateurs de Contoso configurent maintenant Azure DevOps Services pour lancer le processus de build et mise en production afin de mettre en place les pratiques DevOps.

1. Dans Azure DevOps Services, ils sélectionnent **Build et mise en production** > **Nouveau pipeline**.

    ![Nouveau pipeline](./media/contoso-migration-rearchitect-container-sql/pipeline1.png)

2. Ils sélectionnent **Azure DevOps Services Git** et le dépôt pertinent.

    ![Git et dépôt](./media/contoso-migration-rearchitect-container-sql/pipeline2.png)

3. Dans **Sélectionner un modèle**, ils sélectionnent Fabric avec prise en charge Docker.

     ![Fabric et Docker](./media/contoso-migration-rearchitect-container-sql/pipeline3.png)

4. Ils remplacent l’action d’étiquetage des images par l’action **Générer une image** et configurent la tâche pour utiliser l’ACR provisionné.

     ![Registre](./media/contoso-migration-rearchitect-container-sql/pipeline4.png)

5. Dans la tâche **Pousser des images**, ils configurent l’image pour qu’elle soit poussée vers l’ACR et choisissent d’inclure la dernière étiquette.
6. Dans **Déclencheurs**, ils activent l’intégration continue et ajoutent la branche maître.

    ![Déclencheurs](./media/contoso-migration-rearchitect-container-sql/pipeline5.png)

7. Ils sélectionnent **Enregistrer et mettre en file d’attente** pour démarrer une build.
8. Une fois la génération terminée, ils passent au pipeline de mise en production. Dans Azure DevOps Services, ils sélectionnent **Mises en production** > **Nouveau pipeline**.

    ![Pipeline de mise en production](./media/contoso-migration-rearchitect-container-sql/pipeline6.png)

9. Ils sélectionnent le modèle **Déploiement Azure Service Fabric** et donnent un nom à la phase (**SmartHotelSF**).

    ![Environnement](./media/contoso-migration-rearchitect-container-sql/pipeline7.png)

10. Ils fournissent un nom de pipeline (**ContosoSmartHotel360Rearchitect**). Pour la phase, ils sélectionnent **1 travail, 1 tâche** afin de configurer le déploiement Service Fabric.

    ![Phase et tâche](./media/contoso-migration-rearchitect-container-sql/pipeline8.png)

11. À présent, ils sélectionnent **Nouveau** pour ajouter une nouvelle connexion de cluster.

    ![Nouvelle connexion](./media/contoso-migration-rearchitect-container-sql/pipeline9.png)

12. Dans **Ajouter une connexion du service Service Fabric**, ils configurent la connexion et les paramètres d’authentification utilisés par Azure DevOps Services pour déployer l’application. Le point de terminaison de cluster peut être localisé dans le portail Azure, et ils ajoutent le préfixe **tcp://** .

13. Les informations de certificat collectées sont entrées dans **Empreinte numérique du certificat de serveur** et **Certificat client**.

    ![Certificat](./media/contoso-migration-rearchitect-container-sql/pipeline10.png)

14. Ils sélectionnent le pipeline > **Ajouter un artefact**.

     ![Artefact](./media/contoso-migration-rearchitect-container-sql/pipeline11.png)

15. Ils sélectionnent le projet et le pipeline de build à l’aide de la dernière version.

     ![Créer](./media/contoso-migration-rearchitect-container-sql/pipeline12.png)

16. Notez que l’éclair sur l’artefact est activé.

     ![État de l’artefact](./media/contoso-migration-rearchitect-container-sql/pipeline13.png)

17. Par ailleurs, notez que le déclencheur de déploiement continu est activé.
   ![Déploiement continu activé](./media/contoso-migration-rearchitect-container-sql/pipeline14.png)

18. Ils sélectionnent **Enregistrer** > **Créer une mise en production**.

    ![Libérer](./media/contoso-migration-rearchitect-container-sql/pipeline15.png)

19. Une fois le déploiement terminé, SmartHotel360 exécutera Service Fabric.

    ![Publish](./media/contoso-migration-rearchitect-container-sql/publish4.png)

20. Pour se connecter à l’application, ils dirigent le trafic vers l’adresse IP publique de l’équilibreur de charge Azure qui se trouve devant les nœuds Service Fabric.

    ![Publish](./media/contoso-migration-rearchitect-container-sql/publish5.png)

## <a name="step-9-extend-the-app-and-republish"></a>Étape 9 : Étendre l’application et republier

Une fois l’application et la base de données SmartHotel360 en cours d’exécution dans Azure, Contoso veut étendre l’application.

- Les développeurs de Contoso créent un prototype d’application .NET Core qui s’exécutera sur le cluster Service Fabric.
- L’application sera utilisée pour extraire des données de sentiments à partir de Cosmos DB.
- Ces données seront sous la forme de tweets traités à l’aide d’une fonction serverless Azure et de l’API Analyse de texte Azure Cognitive Services.

### <a name="provision-azure-cosmos-db"></a>Provisionner Azure Cosmos DB

Dans un premier temps, les administrateurs de Contoso provisionnent une base de données Azure Cosmos.

1. Ils créent une ressource Azure Cosmos DB dans la Place de Marché Azure.

    ![Extend](./media/contoso-migration-rearchitect-container-sql/extend1.png)

2. Ils fournissent un nom de base de données (**contososmarthotel**), sélectionnent l’API SQL et placent la ressource dans le groupe de ressources de production, dans la région primaire USA Est 2.

    ![Extend](./media/contoso-migration-rearchitect-container-sql/extend2.png)

3. Dans **Prise en main**, ils sélectionnent **Explorateur de données** et ajoutent une nouvelle collection.
4. Dans **Ajouter une collection**, ils fournissent des ID et définissent la capacité de stockage et le débit.

    ![Extend](./media/contoso-migration-rearchitect-container-sql/extend3.png)

5. Dans le portail, ils ouvrent la nouvelle base de données > **Collection** > **Documents** et sélectionnent **Nouveau Document**.
6. Ils collent le code JSON suivant dans la fenêtre de document. Il s’agit d’exemples de données sous la forme d’un seul tweet.

    ```json
    {
            "id": "2ed5e734-8034-bf3a-ac85-705b7713d911",
            "tweetId": 927750234331580911,
            "tweetUrl": "https://twitter.com/status/927750237331580911",
            "userName": "CoreySandersWA",
            "userAlias": "@CoreySandersWA",
            "userPictureUrl": "",
            "text": "This is a tweet about #SmartHotel360",
            "language": "en",
            "sentiment": 0.5,
            "retweet_count": 1,
            "followers": 500,
            "hashtags": [
                ""
            ]
    }
    ```

    ![Extend](./media/contoso-migration-rearchitect-container-sql/extend4.png)

7. Ils localisent le point de terminaison Cosmos DB et la clé d’authentification. Ceux-ci sont utilisés dans l’application pour se connecter à la collection. Dans la base de données, ils sélectionnent **Clés** et copient l’URI et la clé primaire dans le Bloc-notes.

    ![Extend](./media/contoso-migration-rearchitect-container-sql/extend5.png)

### <a name="update-the-sentiment-app"></a>Mettre à jour l’application de sentiments

Cosmos DB étant provisionné, les administrateurs de Contoso peuvent configurer l’application pour qu’elle s’y connecte.

1. Dans Visual Studio, ils ouvrent le fichier ApplicationModern\ApplicationParameters\cloud.xml dans l’Explorateur de solutions.

    ![Application de sentiments](./media/contoso-migration-rearchitect-container-sql/sentiment1.png)

2. Ils renseignent les deux paramètres suivants :

   ```xml
   <Parameter Name="SentimentIntegration.CosmosDBEndpoint" Value="[URI]" />
   ```

   ```xml
   <Parameter Name="SentimentIntegration.CosmosDBAuthKey" Value="[Key]" />
   ```

    ![Application de sentiments](./media/contoso-migration-rearchitect-container-sql/sentiment2.png)

### <a name="republish-the-app"></a>Republier l’application

Après l’extension de l’application, les administrateurs de Contoso la republient sur Azure à l’aide du pipeline.

1. Ils valident leur code et l’envoient (push) vers Azure DevOps Services. Cette opération lance les pipelines de build et de mise en production.

2. Une fois la génération et le déploiement terminés, SmartHotel360 exécute Service Fabric. La console de gestion Service Fabric affiche maintenant trois services.

    ![Republier](./media/contoso-migration-rearchitect-container-sql/republish3.png)

3. Ils peuvent maintenant cliquer sur les services pour vérifier que l’application SentimentIntegration s’exécute.

    ![Republier](./media/contoso-migration-rearchitect-container-sql/republish4.png)

## <a name="clean-up-after-migration"></a>Nettoyer après la migration

Après la migration, Contoso doit effectuer les étapes de nettoyage suivantes :

- Supprimer les machines virtuelles locales de l’inventaire vCenter.
- Supprimer les machines virtuelles des travaux de sauvegarde locale.
- Mettre à jour la documentation interne afin qu’elle indique les nouveaux emplacements pour l’application SmartHotel360. Afficher la base de données comme étant en cours d’exécution dans Azure SQL Database, et l’application frontend comme étant en cours d’exécution dans Service Fabric.
- Passer en revue toutes les ressources qui interagissent avec les machines virtuelles désactivées, et mettre à jour les paramètres ou la documentation appropriés afin de refléter la nouvelle configuration.

## <a name="review-the-deployment"></a>Examiner le déploiement

Avec les ressources migrées dans Azure, Contoso doit rendre sa nouvelle infrastructure entièrement opérationnelle et la sécuriser.

### <a name="security"></a>Sécurité

- Les administrateurs de Contoso doivent vérifier que leur nouvelle base de données **SmartHotel-Registration** est sécurisée. [Plus d’informations](/azure/sql-database/sql-database-security-overview)
- En particulier, ils doivent mettre à jour le conteneur pour utiliser le protocole SSL avec des certificats.
- Ils devraient envisager d’utiliser Key Vault pour protéger les secrets de leurs applications Service Fabric. [Plus d’informations](/azure/service-fabric/service-fabric-application-secret-management)

### <a name="backups"></a>Sauvegardes

- Contoso doit examiner les besoins de sauvegarde de la base de données Azure SQL. [Plus d’informations](/azure/sql-database/sql-database-automated-backups)
- Les administrateurs de Contoso doivent implémenter des groupes de basculement afin de fournir un basculement régional pour la base de données. [Plus d’informations](/azure/sql-database/sql-database-geo-replication-overview)
- Ils peuvent tirer parti de la géoréplication pour la référence SKU premium d’ACR. [Plus d’informations](/azure/container-registry/container-registry-geo-replication)
- Contoso doit envisager de déployer l’application web dans les régions principales USA Est 2 et USA Centre quand Web App pour conteneurs devient disponible. Les administrateurs de Contoso peuvent configurer Traffic Manager pour garantir le basculement en cas de pannes régionales.
- Cosmos DB effectue des sauvegardes automatiquement. Contoso peut en savoir plus sur ce processus [ici](/azure/cosmos-db/online-backup-and-restore).

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

- Une fois toutes les ressources déployées, Contoso doit attribuer des balises Azure en fonction de la [planification de son infrastructure](contoso-migration-infrastructure.md#set-up-tagging).
- Toutes les licences sont intégrées dans le coût des services PaaS que Contoso consomme. Cela sera déduit de l’Accord Entreprise.
- Contoso va activer Azure Cost Management sous licence de Cloudyn, une filiale de Microsoft. Il s’agit d’une solution de gestion des coûts multicloud qui vous aide à utiliser et à gérer Azure ainsi que d’autres ressources cloud. [En savoir plus](/azure/cost-management/overview) sur Azure Cost Management.

## <a name="conclusion"></a>Conclusion

Cet article décrit comment Contoso a refactorisé l’application SmartHotel360 dans Azure en migrant la machine virtuelle frontale de l’application vers Service Fabric. La base de données de l’application a été migrée vers une base de données Azure SQL.
