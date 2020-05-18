---
title: Refactoriser une application en la migrant vers Azure App Service et Azure SQL Database Managed Instance
description: Découvrez comment Contoso réhéberge une application locale en la migrant vers une application web Azure App Service et une instance Azure SQL Database Managed Instance.
author: givenscj
ms.author: abuck
ms.date: 04/02/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 0e288b29077d68ee4b0c0522537abe0baaa276ac
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83223692"
---
<!-- cSpell:ignore givenscj WEBVM SQLVM contosohost vcenter contosodc smarthotel SQLMI SHWCF SHWEB -->

# <a name="refactor-an-on-premises-app-to-an-azure-app-service-web-app-and-azure-sql-managed-instance"></a>Refactoriser une application locale vers une application web Azure App Service et une instance Azure SQL Database Managed Instance

Cet article explique comment la société fictive Contoso refactorise une application Windows .NET à deux niveaux qui s’exécute sur des machines virtuelles VMware dans le cadre d’une migration vers Azure. Ils migrent la machine virtuelle frontale de l’application vers une application web Azure App Service. Il explique également la façon dont Contoso migre la base de données d’application vers Azure SQL Database Managed Instance.

L’application SmartHotel360 utilisée dans cet exemple est fournie au format open source. Si vous souhaitez l’utiliser à des fins de test, vous pouvez la télécharger à partir de [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat qu’ils souhaitent obtenir avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso étant en croissance, son infrastructure et ses systèmes locaux sont soumis à une charge importante.
- **Gagner en efficacité.** Contoso doit supprimer les procédures inutiles et rationaliser les processus pour les développeurs et les utilisateurs. L’entreprise a besoin d’une informatique rapide et doit éviter de perdre du temps ou d’argent en répondant plus rapidement aux exigences des clients.
- **Gagner en agilité.**  le service informatique de Contoso doit être plus réactif face aux besoins de l’entreprise. Elle doit être en mesure de réagir plus rapidement que l’évolution du marché pour réussir dans une économie mondiale. L’informatique ne doit pas devenir une entrave à l’activité.
- **Mise à l’échelle** à mesure que l’entreprise croît, le service informatique de Contoso doit fournir des systèmes capables de croître au même rythme.
- **Réduire les coûts.** Contoso souhaite réduire les coûts de licence.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a épinglé les objectifs de cette migration. Ces objectifs ont été utilisés pour déterminer la meilleure méthode de migration.

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
**Application** | L’application dans Azure restera aussi critique qu’aujourd’hui. <br><br> Elle doit offrir le même niveau de performance qu’actuellement dans VMware. <br><br> L’équipe ne souhaite pas investir dans l’application. Pour l’instant, les administrateurs veulent simplement déplacer l’application de façon sécurisée vers le cloud. <br><br> L’équipe veut cesser de prendre en charge Windows Server 2008 R2, sur lequel l’application s’exécute actuellement. <br><br> L’équipe veut aussi passer de SQL Server 2008 R2 à une plateforme de base de données PaaS moderne, de façon à réduire les tâches de gestion. <br><br> Contoso souhaite tirer parti autant que possible de son investissement dans les licences SQL Server et dans Software Assurance. <br><br> En outre, Contoso veut limiter les risques liés à un point de défaillance unique sur le niveau web.
**Limitations** | L’application consiste en une application ASP.NET et un service WCF (Windows Communication Foundation) s’exécutant sur la même machine virtuelle. Ils veulent fractionner cela en deux applications web utilisant Azure App Service.
**Microsoft Azure** | Contoso veut déplacer l’application vers Azure, mais ne veut pas l’exécuter sur des machines virtuelles. Contoso veut utiliser des services PaaS d’Azure pour les couches Web et Données.
**DevOps** | Contoso veut passer à un modèle DevOps, en utilisant Azure DevOps pour les builds et les pipelines de mise en production.

<!-- markdownlint-enable MD033 -->

## <a name="solution-design"></a>Conception de la solution

Après avoir défini précisément les objectifs et exigences, Contoso conçoit et examine une solution de déploiement, et identifie le processus de migration, notamment les services Azure à utiliser pour la migration.

### <a name="current-app"></a>Application actuelle

- L’application SmartHotel360 locale est hiérarchisée sur deux machines virtuelles (WEBVM et SQLVM).
- Les machines virtuelles sont situées sur un hôte VMware ESXi **contosohost1.contoso.com** (version 6.5).
- L’environnement VMware est géré par le serveur vCenter Server 6.5 (**vcenter.contoso.com**) s’exécutant sur une machine virtuelle.
- Contoso dispose d’un centre de données local (contoso-datacenter), avec un contrôleur de domaine local (**contosodc1**).
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

### <a name="proposed-solution"></a>Solution proposée

- Pour le niveau web de l’application, Contoso a décidé d’utiliser Azure App Service. Ce service PaaS permet de déployer l’application avec seulement quelques changements de configuration. Contoso utilisera Visual Studio pour apporter les modifications et déployer deux applications web. L’une pour le site web, et l’autre pour le service WCF.
- Pour satisfaire aux exigences d’un pipeline DevOps, Contoso a choisi Azure DevOps pour la gestion du code source avec des dépôts Git. Des builds et la mise en production automatisées seront utilisées pour générer le code et le déployer sur Azure App Service.

### <a name="database-considerations"></a>Considérations liées à la base de données

Dans le cadre de la conception de la solution, Contoso a fait une comparaison des fonctionnalités entre Azure SQL Database et SQL Server Managed Instance. Les administrateurs ont choisi Managed Instance sur la base des considérations suivantes.

- Managed Instance vise à fournir une compatibilité de quasi 100 % avec la dernière version locale de SQL Server. Microsoft recommande Managed Instance aux clients qui exécutent SQL Server localement ou sur une machine virtuelle IaaS et qui souhaitent migrer leurs applications vers un service entièrement managé en changeant le moins possible la conception.
- Contoso a l’intention de migrer un grand nombre d’applications locales vers IaaS. Beaucoup d’entre elles sont fournies par l’ISV. Contoso se rend compte que Managed Instance peut garantir une compatibilité de base de données pour ces applications que SQL Database ne prend peut-être pas en charge.
- Contoso peut simplement effectuer une migration lift-and-shift vers Managed Instance à l’aide d’Azure Database Migration Service entièrement automatisé. Une fois ce service en place, Contoso peut le réutiliser pour les futures migrations de base de données.
- SQL Managed Instance prend en charge SQL Server Agent, qui est essentiel pour l’application SmartHotel360. Contoso a besoin de cette compatibilité, sous peine de devoir recréer les plans de maintenance demandés par l’application.
- Avec Software Assurance, Contoso peut échanger ses licences existantes contre une réduction de tarif sur SQL Database Managed Instance en utilisant Azure Hybrid Benefit pour SQL Server. Contoso peut alors économiser jusqu'à 30 % sur Managed Instance.
- SQL Managed Instance est entièrement contenu dans le réseau virtuel ; il fournit donc une isolation et sécurité accrues pour les données de Contoso. Contoso peut obtenir les avantages du cloud public tout en isolant l’environnement du réseau Internet public.
- Managed Instance prend en charge plusieurs fonctionnalités de sécurité, notamment Always Encrypted, le masquage dynamique des données, la sécurité au niveau des lignes et la détection des menaces.

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant une liste des avantages et des inconvénients.

<!-- markdownlint-disable MD033 -->

**Considération** | **Détails**
--- | ---
**Avantages** | Le code de l’application SmartHotel360 ne nécessite pas de modification avant sa migration vers Azure. <br><br> Contoso peut tirer parti de son investissement dans Software Assurance en utilisant Azure Hybrid Benefit tant pour SQL Server que pour Windows Server. <br><br> Après la migration, Windows Server 2008 R2 ne devra plus être pris en charge. Pour plus d’informations, consultez [Stratégie de cycle de vie Microsoft](https://aka.ms/lifecycle). <br><br> Contoso peut configurer la couche web de l’application avec plusieurs instances, pour qu’elle ne constitue plus un point de défaillance unique. <br><br> La base de données ne dépendra plus de SQL Server 2008 R2, qui est une version déjà ancienne. <br><br> SQL Managed Instance prend en charge les spécifications techniques et les objectifs de Contoso. <br><br> Managed Instance offre une compatibilité de 100 % avec le déploiement actuel, tout en permettant à Contoso de ne plus utiliser SQL Server 2008 R2. <br><br> Contoso peut tirer parti de son investissement dans Software Assurance en utilisant Azure Hybrid Benefit pour SQL Server et Windows Server. <br><br> Elle peut réutiliser Azure Database Migration Service pour d’autres migrations futures. <br><br> SQL Managed Instance intègre une tolérance de panne que Contoso n’a pas besoin de configurer. Cela signifie que la couche Données n’est plus un point de basculement unique.
**Inconvénients** | Azure App Service ne prend en charge le déploiement que d’une seule application pour chaque application web. Cela signifie que deux applications web doivent être approvisionnées (l’une pour le site web et l’autre pour le service WCF). <br><br> Pour la couche Données, Managed Instance n’est peut-être pas la meilleure solution si Contoso veut personnaliser le système d’exploitation ou le serveur de base de données, ou si l’entreprise veut exécuter des applications tierces avec SQL Server. L’exécution de SQL Server sur une machine virtuelle IaaS peut apporter cette flexibilité.

<!-- markdownlint-enable MD033 -->

## <a name="proposed-architecture"></a>Architecture proposée

![Architecture du scénario](./media/contoso-migration-refactor-web-app-sql-managed-instance/architecture.png)

### <a name="migration-process"></a>Processus de migration

1. Contoso provisionne une instance Azure SQL Database Managed Instance et y migre la base de données SmartHotel360 avec Azure Database Migration Service (DMS).
2. Contoso approvisionne et configure des applications web et y déploie l’application SmartHotel360.

    ![Processus de migration](./media/contoso-migration-refactor-web-app-sql-managed-instance/migration-process.png)

### <a name="azure-services"></a>Services Azure

**Service** | **Description** | **Coût**
--- | --- | ---
[Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview) | Azure Database Migration Service permet une migration fluide à partir de plusieurs sources de base de données vers des plateformes de données Azure, avec un temps d’arrêt minimal. | Apprenez-en davantage sur les [régions prises en charge](https://docs.microsoft.com/azure/dms/dms-overview#regional-availability) et sur la [tarification de Database Migration Service](https://azure.microsoft.com/pricing/details/database-migration).
[Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) | Managed Instance est un service de base de données managé qui représente une instance de SQL Server entièrement managée dans le cloud Azure. Il utilise le même code que la dernière version du moteur de base de données SQL Server et offre les dernières fonctionnalités, améliorations en termes de performances et correctifs de sécurité. | L’utilisation de SQL Database Managed Instance exécuté dans Azure entraîne des frais basés sur la capacité. Apprenez-en davantage sur la [tarification de Managed Instance](https://azure.microsoft.com/pricing/details/sql-database/managed).
[Azure App Service](https://docs.microsoft.com/azure/app-service/overview) | Créez des applications cloud performantes en utilisant une plateforme entièrement gérée. | Coût en fonction de la taille, de l’emplacement et de la durée d’utilisation. [Plus d’informations](https://azure.microsoft.com/pricing/details/app-service/windows)
[Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/what-is-azure-pipelines) | Fournit un pipeline d’intégration et de déploiement continus (CI/CD) pour le développement d’applications. Le pipeline démarre avec un dépôt Git pour la gestion du code de l’application, un système de build pour la production de packages et d’autres artefacts de build, et un système Release Management pour le déploiement de modifications sur les environnements de production, de test et de développement.

## <a name="prerequisites"></a>Prérequis

Voici ce dont Contoso a besoin pour exécuter ce scénario :

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
**Abonnement Azure** | Contoso a créé des abonnements dans un article précédent. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial). <br><br> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions. <br><br> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur.
**Infrastructure Azure** | [Découvrez comment](./contoso-migration-infrastructure.md) Contoso configure une infrastructure Azure.

<!--markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment Contoso exécutera la migration :

> [!div class="checklist"]
>
> - **Étape 1 : Configurer une SQL Database Managed Instance.** Contoso a besoin d’une instance managée existante vers laquelle la base de données SQL Server locale migrera.
> - **Étape 2 : Migrer avec Azure Database Migration Service (DMS).** Contoso migre la base de données de l’application à l’aide d’Azure Database Migration Service.
> - **Étape 3 : Approvisionner des applications web.** Contoso provisionne les deux applications web.
> - **Étape 4 : Configurer Azure DevOps.** Contoso crée un projet Azure DevOps et importe le dépôt Git.
> - **Étape 5 : Configurer des chaînes de connexion.** Contoso configure les chaînes de connexion afin que l’application web du niveau web, l’application web du service WCF et l’instance SQL puissent communiquer.
> - **Étape 6 : Configurer des pipelines de build et de mise en production.** Pour terminer, Contoso configure des pipelines de build et de mise en production pour créer l’application et la déployer dans deux applications web distinctes.

## <a name="step-1-set-up-a-sql-database-managed-instance"></a>Étape 1 : Configurer une SQL Database Managed Instance

Pour configurer Azure SQL Database Managed Instance, Contoso a besoin d’un sous-réseau qui remplit les conditions suivantes :

- Le sous-réseau doit être dédié. Il doit être vide et ne doit contenir aucun autre service cloud. Le sous-réseau ne doit pas être un sous-réseau de passerelle.
- Une fois l’instance gérée créée, Contoso ne doit pas ajouter de ressources au sous-réseau.
- Aucun groupe de sécurité réseau ne doit être associé au sous-réseau.
- Le sous-réseau doit avoir une table de routage définie par l’utilisateur. Le seul itinéraire attribué doit être 0.0.0.0/0 tronçon suivant vers Internet.
- Si un DNS personnalisé facultatif est spécifié pour le réseau virtuel, l’adresse IP virtuelle `168.63.129.16` pour les programmes de résolution récursifs dans Azure doit être ajoutée à la liste. Découvrez comment [configurer un DNS personnalisé pour une instance managée Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-custom-dns).
- Le sous-réseau ne doit pas avoir de point de terminaison de service (stockage ou SQL) associé. Les points de terminaison doivent être désactivés sur le réseau virtuel.
- Le sous-réseau doit avoir un minimum de 16 adresses IP. Découvrez comment [dimensionner le sous-réseau Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-configure-vnet-subnet).
- Dans l’environnement hybride de Contoso, des paramètres DNS personnalisés sont nécessaires. Contoso configure les paramètres DNS pour utiliser un ou plusieurs des serveurs DNS Azure de l’entreprise. Apprenez-en davantage sur la [personnalisation du système DNS](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-custom-dns).

### <a name="set-up-a-virtual-network-for-the-managed-instance"></a>Configurer un réseau virtuel pour Managed Instance

Les administrateurs de Contoso configurent le réseau virtuel de la façon suivante :

1. Ils créent un réseau virtuel (**VNET-SQLMI-EU2**) dans la région primaire USA Est 2. Ils ajoutent le réseau virtuel au groupe de ressources **ContosoNetworkingRG**.
2. Ils attribuent l’espace d’adressage 10.235.0.0/24. Ils vérifient que la plage ne chevauche pas d’autres réseaux dans l’entreprise.
3. Ils ajoutent deux sous-réseaux au réseau :
    - **SQLMI-DS-EUS2** (10.235.0.0.25).
    - **SQLMI-SAW-EUS2** (10.235.0.128/29). Ce sous-réseau est utilisé pour joindre l’annuaire à Managed Instance.

      ![Managed Instance - Créer un réseau virtuel](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-vnet.png)

4. Une fois le réseau virtuel et les sous-réseaux déployés, ils appairent les réseaux de la façon suivante :

    - Peering de **VNET-SQLMI-EUS2** avec **VNET-HUB-EUS2** (réseau virtuel hub pour la région USA Est 2).
    - Peering de **VNET-SQLMI-EUS2** avec **VNET-PROD-EUS2** (réseau de production).

      ![Peering de réseau](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-peering.png)

5. Ils définissent des paramètres DNS personnalisés. Le système DNS pointe tout d’abord sur les contrôleurs de domaine Azure de Contoso. Azure DNS est secondaire. Les contrôleurs de domaine Azure de Contoso se situent comme suit :

    - Situé sur le sous-réseau **PROD-CC-EUS2**, sur le réseau de production USA Est 2 (**VNET-PROD-EUS2**).
    - Adresse de **CONTOSODC3** : 10.245.42.4.
    - Adresse de **CONTOSODC4** : 10.245.42.5.
    - Programme de résolution d’Azure DNS : 168.63.129.16.

      ![Serveurs DNS du réseau](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-dns.png)

**Besoin de plus d’aide ?**

- Obtenez une vue d’ensemble de [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
- Découvrez comment [créer un réseau virtuel pour SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-configure-vnet-subnet).
- Découvrez comment [configurer le peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-manage-peering).
- Découvrez comment [mettre à jour les paramètres DNS d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory-domain-services/tutorial-create-instance).

### <a name="set-up-routing"></a>Configuration du routage

Managed Instance est placé sur un réseau privé virtuel. Contoso a besoin d’une table de routage pour que le réseau virtuel communique avec le service de gestion Azure. Si le réseau virtuel ne peut pas communiquer avec le service qui le gère, le réseau virtuel devient inaccessible.

Contoso prend en compte ces facteurs :

- La table de routage contient un ensemble de règles (itinéraires) qui spécifient le mode de routage des paquets envoyés à partir de Managed Instance sur le réseau virtuel.
- La table de routage est associée à des sous-réseaux dans lesquels les instances gérées sont déployées. Chaque paquet quittant un sous-réseau est géré en fonction de la table de routage associée.
- Un sous-réseau ne peut être associé qu’à une seule table de routage.
- La création de tables de routage dans Microsoft Azure n’occasionne aucun frais.

 Pour configurer le routage, les administrateurs de Contoso effectuent les opérations suivantes :

1. Ils créent une table de routage définie par l’utilisateur dans le groupe de ressources **ContosoNetworkingRG**.

    ![Table de routage](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table.png)

2. Pour respecter les exigences de Managed Instance, une fois la table de routage (**MIRouteTable**) déployée, ils ajoutent une route avec le préfixe d’adresse 0.0.0.0/0. L’option **Type de tronçon suivant** est définie sur **Internet**

    ![Préfixe de table de routage](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-prefix.png)

3. Ils associent la table de routage au sous-réseau **SQLMI-DB-EUS2** (dans le réseau **VNET-SQLMI-EUS2**).

    ![Sous-réseau de table de routage](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-subnet.png)

**Besoin de plus d’aide ?**

Découvrez comment [configurer des itinéraires pour une instance gérée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started).

### <a name="create-a-managed-instance"></a>Créer une option Managed Instance

À présent, les administrateurs de Contoso peuvent provisionner une instance SQL Database Managed Instance :

1. Comme l’instance gérée sert une application métier, ils la déploient dans la région USA Est 2 primaire de l’entreprise. Ils ajoutent l’instance gérée au groupe de ressources **ContosoRG**.
2. Ils sélectionnent un niveau tarifaire, une taille de calcul et un stockage pour l’instance. Apprenez-en davantage sur la [tarification de Managed Instance](https://azure.microsoft.com/pricing/details/sql-database/managed).

    ![Instance gérée](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-create.png)

3. Une fois l’instance gérée déployée, deux nouvelles ressources apparaissent dans le groupe de ressources **ContosoRG** :

    - Un cluster virtuel si Contoso a plusieurs instances gérées
    - L’instance gérée SQL Server Database

      ![Instance gérée](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-resources.png)

**Besoin de plus d’aide ?**

Découvrez comment [provisionner une instance gérée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started).

## <a name="step-2-migrate-with-azure-database-migration-service-dms"></a>Étape 2 : Migrer avec Azure Database Migration Service (DMS)

Les administrateurs Contoso la migrent à l’aide des services de migration de base de données Azure (DMS) en s’appuyant sur le [didacticiel de migration pas à pas](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online). Ils peuvent effectuer des migrations en ligne, hors connexion et hybrides (préversion).

En résumé, vous devez effectuer les opérations suivantes :

- Créer un service Azure Database Migration Service (DMS) avec une référence SKU `Premium` connectée au réseau virtuel.
- Vous assurer que le service Azure Database Migration Service (DMS) peut accéder au SQL Server à distance via le réseau virtuel. Cela implique de s’assurer que tous les ports entrants sont autorisés entre Azure et SQL Server au niveau du réseau virtuel, du VPN réseau et de la machine qui héberge SQL Server.
- Configurer Azure Database Migration Service :
  - Créez un projet de migration.
  - Ajoutez une source (base de données locale).
  - Sélectionnez une cible.
  - Sélectionnez la ou les bases de données à migrer.
  - Configurez les paramètres avancés.
  - Démarrez la réplication.
  - Résolvez les erreurs.
  - Effectuez le dernier basculement.

## <a name="step-3-provision-web-apps"></a>Étape 3 : Approvisionner des applications web

La base de données étant migrée, les administrateurs Contoso peuvent maintenant provisionner les deux applications web.

1. Ils sélectionnent **Application web** dans le portail.

    ![Application web](./media/contoso-migration-refactor-web-app-sql-managed-instance/web-app1.png)

2. Ils fournissent un nom pour l’application (**SHWEB-EUS2**), exécutent celle-ci sur Windows, puis la placent dans le groupe de ressources de production **ContosoRG**. Ils créent une application web et un plan Azure App Service.

    ![Application web](./media/contoso-migration-refactor-web-app-sql-managed-instance/web-app2.png)

3. Une fois l’application web approvisionnée, ils répètent le processus pour créer une application web pour le service WCF (**SHWCF-EUS2**)

    ![Application web](./media/contoso-migration-refactor-web-app-sql-managed-instance/web-app3.png)

4. Cela fait, ils accèdent à l’adresse des applications pour vérifier si celles-ci ont été correctement créées.

## <a name="step-4-set-up-azure-devops"></a>Étape 4 : Configurer Azure DevOps

Contoso doit générer l’infrastructure et les pipelines DevOps pour l’application. Pour cela, les administrateurs Contoso créent un projet DevOps, importent le code, puis configurent les pipelines de build et de mise en production.

1. Dans le compte Azure DevOps de Contoso, ils créent un projet (**ContosoSmartHotelRefactor**) et sélectionnent **Git** pour la gestion de version.

    ![Nouveau projet](./media/contoso-migration-refactor-web-app-sql-managed-instance/vsts1.png)

2. Ils importent le dépôt Git qui détient actuellement leur code d’application. Il se trouve dans un [référentiel GitHub public](https://github.com/Microsoft/SmartHotel360-Registration) que vous pouvez télécharger.

    ![Télécharger le code d’application](./media/contoso-migration-refactor-web-app-sql-managed-instance/vsts2.png)

3. Une fois le code importé, ils connectent Visual Studio au dépôt et clonent le code à l’aide de Team Explorer.

    ![Se connecter à un projet](./media/contoso-migration-refactor-web-app-sql-managed-instance/devops1.png)

4. Une fois le référentiel cloné sur la machine du développeur, ils ouvrent le fichier Solution de l’application. L’application web et le service wcf ont chacun un projet distinct dans le fichier.

    ![Fichier solution](./media/contoso-migration-refactor-web-app-sql-managed-instance/vsts4.png)

## <a name="step-5-configure-connection-strings"></a>Étape 5 : Configuration des chaînes de connexion

Les administrateurs Contoso doivent faire en sorte que les applications web et la base de données puissent communiquer. Pour ce faire, ils configurent des chaînes de connexion dans le code et dans les applications web.

1. Dans l’application web pour le service WCF (**SHWCF-EUS2**) > **Paramètres** > **Paramètres de l'application**, ils ajoutent une nouvelle chaîne de connexion nommée **DefaultConnection**.
2. La chaîne de connexion est extraite de la base de données **SmartHotel-Registration**, et doit être mise à jour avec les informations d’identification correctes.

    ![Chaîne de connexion](./media/contoso-migration-refactor-web-app-sql-managed-instance/string1.png)

3. Dans Visual Studio, ils ouvrent le projet **SmartHotel.Registration.wcf** à partir du fichier solution. La section **connectionStrings** du fichier web.config pour le service WCF **SmartHotel.Registration.Wcf** doit être mise à jour avec la chaîne de connexion.

     ![Chaîne de connexion](./media/contoso-migration-refactor-web-app-sql-managed-instance/string2.png)

4. La section **client** du fichier web.config pour **SmartHotel.Registration.Web** doit être modifiée de façon à ce qu’elle pointe vers le nouvel emplacement du service WCF. Il s’agit de l’URL de l’application web WCF qui héberge le point de terminaison de service.

    ![Chaîne de connexion](./media/contoso-migration-refactor-web-app-sql-managed-instance/strings3.png)

5. Une fois les modifications apportées au code, les administrateurs doivent valider les modifications. À l’aide de Team Explorer dans Visual Studio, ils effectuent la validation et la synchronisation.

## <a name="step-6-set-up-build-and-release-pipelines-in-azure-devops"></a>Étape 6 : Configurer les pipelines de build et de mise en production dans Azure DevOps

Les administrateurs de Contoso configurent maintenant Azure DevOps pour lancer le processus de build et mise en production.

1. Dans Azure DevOps, ils sélectionnent **Build et mise en production** > **Nouveau pipeline**.

    ![Nouveau pipeline](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline1.png)

2. Ils sélectionnent **Azure Repos Git** et le dépôt pertinent.

    ![Git et dépôt](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline2.png)

3. Dans **Sélectionner un modèle**, ils sélectionnent le modèle ASP.NET pour leur build.

     ![Modèle ASP.NET](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline3.png)

4. Le nom **ContosoSmartHotelRefactor-ASP.NET-CI** est utilisé pour la build. Ils sélectionnent **Enregistrer et mettre en file d’attente**.

     ![Enregistrer et mettre en file d’attente](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline4.png)

5. La première build est alors lancée. Ils sélectionnent le numéro de build pour surveiller le processus. Une fois le processus terminé, ils peuvent voir les commentaires associés à ce dernier, puis sélectionner **Artifacts** pour passer en revue les résultats de la build.

    ![Révision](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline5.png)

6. Le dossier **drop** contient les résultats de la build.

    - Les deux fichiers zip sont les packages qui contiennent les applications.
    - Ces fichiers sont utilisés dans le pipeline de mise en production pour le déploiement sur Azure App Service.

     ![Artefact](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline6.png)

7. Ils sélectionnent **Mises en production** >  **+Nouveau pipeline**.

    ![Nouveau pipeline](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline7.png)

8. Ils sélectionnent le modèle de déploiement pour Azure App Service.

    ![Modèle de déploiement Azure App Service](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline8.png)

9. Ils nomment le pipeline de mise en production **ContosoSmartHotel360Refactor** et spécifient le nom de l’application web WCF (SHWCF-EUS2) pour le nom de la **phase**.

    ![Environnement](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline9.png)

10. Sous les phases, ils sélectionnent **1 travail, 1 tâche** pour configurer le déploiement du service WCF.

    ![Déployer WCF](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline10.png)

11. Ils vérifient que l’abonnement est sélectionné et autorisé, puis sélectionnent le **Nom de l’App Service**.

     ![Sélectionner le nom du service de l’application](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline11.png)

12. Dans le pipeline > **Artefacts**, ils sélectionnent **+Ajouter un artefact**, puis ils choisissent de générer avec le pipeline **ContosoSmarthotel360Refactor**.

     ![Build](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline12.png)

13. Ils sélectionnent l’éclair qui se trouve sur l’artefact coché pour activer le déclencheur de déploiement continu.

     ![Éclair](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline13.png)

14. Le déclencheur de déploiement continu doit être défini sur **Activé**.

    ![Déploiement continu activé](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline14.png)

15. À présent, ils reviennent à la phase « 1 travail, 1 tâche », puis sélectionnent **Déployer Azure App Service**.

    ![Déployer Azure App Service](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline15.png)

16. Sous **Sélectionner un fichier ou dossier**, ils recherchent le fichier **SmartHotel.Registration.Wcf.zip** qui a été créé lors de la génération, puis ils sélectionnent **Enregistrer**.

    ![Enregistrer WCF](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline16.png)

17. Ils sélectionnent **Pipeline** > **Phases** **+Ajouter** afin d’ajouter un environnement pour **SHWEB-EUS2**. Ils sélectionnent un autre déploiement Azure App Service.

    ![Ajouter un environnement](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline17.png)

18. Ils répètent ensuite le processus pour publier l’application web (**SmartHotel.Registration.Web.zip**) sur l’application web correcte.

    ![Publier l’application web](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline18.png)

19. Une fois qu’il est enregistré, le pipeline de mise en production apparaît comme suit.

     ![Résumé du pipeline de mise en production](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline19.png)

20. Ils reviennent à **Build**, puis sélectionnent **Déclencheurs** > **Activer l’intégration continue**. Ceci active le pipeline pour que, quand des modifications sont validées dans le code, une build complète et une mise en production soient effectuées.

    ![Activer l’intégration continue](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline20.png)

21. Ils sélectionnent **Enregistrer et mettre en file d’attente** pour exécuter le pipeline complet. Une nouvelle build est déclenchée, qui à son tour crée la première mise en production de l’application sur Azure App Service.

    ![Enregistrer le pipeline](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline21.png)

22. Les administrateurs Contoso peuvent suivre le processus du pipeline de build et de mise en production depuis Azure DevOps. Une fois la build terminée, la mise en production commence.

    ![Générer et mettre en production l’application](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline22.png)

23. Une fois que le pipeline a terminé, les deux sites ont été déployés et l’application est opérationnelle en ligne.

    ![Terminer la mise en production](./media/contoso-migration-refactor-web-app-sql-managed-instance/pipeline23.png)

À ce stade, la migration de l’application vers Azure a réussi.

## <a name="clean-up-after-migration"></a>Nettoyer après la migration

Après la migration, Contoso doit effectuer les étapes de nettoyage suivantes :

- Supprimer les machines virtuelles locales de l’inventaire vCenter.
- Supprimer les machines virtuelles des travaux de sauvegarde locale.
- Mettre à jour la documentation interne afin qu’elle indique les nouveaux emplacements pour l’application SmartHotel360. Afficher la base de données en cours d’exécution dans la base de données Azure SQL Database Managed Instance et le front-end en cours d’exécution dans les deux applications web.
- Passer en revue toutes les ressources qui interagissent avec les machines virtuelles désactivées, et mettre à jour les paramètres ou la documentation appropriés afin de refléter la nouvelle configuration.

## <a name="review-the-deployment"></a>Examiner le déploiement

Avec les ressources migrées dans Azure, Contoso doit rendre sa nouvelle infrastructure entièrement opérationnelle et la sécuriser.

### <a name="security"></a>Sécurité

- Contoso doit vérifier que sa nouvelle base de données **SmartHotel-Registration** est sécurisée. [Plus d’informations](https://docs.microsoft.com/azure/sql-database/sql-database-security-overview)
- En particulier, Contoso doit mettre à jour les applications web pour qu’elles utilisent SSL avec des certificats.

### <a name="backups"></a>Sauvegardes

- Contoso doit examiner les besoins de sauvegarde d’Azure SQL Database Managed Instance. [Plus d’informations](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups)
- Contoso doit aussi découvrir comment gérer les sauvegardes et les restaurations de SQL Database. [Découvrez plus d’informations](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups) sur les sauvegardes automatiques.
- Contoso doit envisager d’implémenter des groupes de basculement afin de fournir un basculement régional pour la base de données. [Plus d’informations](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)
- Pour la résilience de l’application web, Contoso doit envisager son déploiement dans les régions principales USA Est 2 et USA Centre. Contoso peut configurer Traffic Manager pour garantir le basculement en cas de pannes régionales.

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

- Une fois toutes les ressources déployées, Contoso doit affecter des balises Azure en fonction de la [planification de son infrastructure](./contoso-migration-infrastructure.md#set-up-tagging).
- Toutes les licences sont intégrées dans le coût des services PaaS que Contoso consomme. Cela sera déduit de l’Accord Entreprise.
- Contoso utilise [Azure Cost Management](https://azure.microsoft.com/services/cost-management) pour s’assurer qu’ils ne dépassent pas les budgets établis par leur direction informatique.

## <a name="conclusion"></a>Conclusion

Cet article décrit comment Contoso a refactorisé l’application SmartHotel360 dans Azure en migrant la machine virtuelle frontale de l’application vers deux applications web Azure App Service. La base de données de l’application a été migrée vers Azure SQL Database Managed Instance.
