---
title: Réhéberger une application de bureau de service Linux sur Azure et Azure Database pour MySQL
description: Découvrez comment Contoso réhéberge une application Linux locale en la migrant vers des machines virtuelles Azure et Azure Database pour MySQL.
author: givenscj
ms.author: abuck
ms.date: 04/01/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 61398802202a33f9c514cf5a5b6a2528e7b662e4
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83215991"
---
<!-- cSpell:ignore givenscj OSTICKETWEB OSTICKETMYSQL contosohost vcenter contosodc contosoosticket osticket InnoDB binlog systemctl NSGs -->

# <a name="rehost-an-on-premises-linux-app-to-azure-vms-and-azure-database-for-mysql"></a>Réhéberger une application Linux locale vers des machines virtuelles Azure et Azure Database pour MySQL

Cet article explique comment la société fictive Contoso réhéberge une application Apache/MySQL/PHP (LAMP) à deux niveaux et basée sur Linux, en la migrant d’un emplacement local vers Azure à l’aide de machines virtuelles Azure et d’Azure Database pour MySQL.

osTicket, l’application de bureau de service utilisée dans cet exemple, est fournie au format open source. Si vous souhaitez l’utiliser pour vos propres tests, vous pouvez la télécharger à partir de [GitHub](https://github.com/osTicket/osTicket).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat souhaité :

- **Répondre à la croissance de l’entreprise.** Contoso étant en croissance, son infrastructure et ses systèmes locaux subissent une pression.
- **Limiter les risques.** L’application Service Desk est vitale pour l’activité. Contoso veut la migrer vers Azure sans risque.
- **Étendre.** Contoso ne souhaite pas modifier l’application dans l’immédiat. L’entreprise souhaite simplement que l’application reste stable.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a défini les objectifs de cette migration, afin de déterminer la meilleure méthode de migration :

- Après la migration, l’application dans Azure doit offrir les mêmes performances qu’aujourd’hui dans l’environnement VMware local. L’application restera tout aussi vitale dans le cloud que localement.
- Contoso ne souhaite pas investir dans cette application. Elle est importante pour l’activité mais, sous sa forme actuelle, Contoso veut simplement la migrer de manière sécurisée vers le cloud.
- Après avoir effectué quelques migrations d’application Windows, Contoso souhaite apprendre à utiliser une infrastructure basée sur Linux dans Azure.
- Contoso souhaite réduire au minimum les tâches d’administration de base de données après la migration de l’application vers le cloud.

## <a name="proposed-architecture"></a>Architecture proposée

Dans ce scénario :

- Actuellement, l’application est hiérarchisée sur deux machines virtuelles (`OSTICKETWEB` et `OSTICKETMYSQL`).
- Les machines virtuelles sont situées sur un hôte VMware ESXi `contosohost1.contoso.com` (version 6.5).
- L’environnement VMware est géré par vCenter Server 6.5 (`vcenter.contoso.com`) s’exécutant sur une machine virtuelle.
- Contoso dispose d’un centre de données local (`contoso-datacenter`), avec un contrôleur de domaine local (`contosodc1`).
- L’application de couche web sur `OSTICKETWEB` sera migrée vers une machine virtuelle IaaS Azure.
- La base de données de l’application sera migrée vers le service PaaS Azure Database pour MySQL.
- Dans la mesure où Contoso migre une charge de travail de production, les ressources résideront dans le groupe de ressources de production `ContosoRG`.
- La ressource `OSTICKETWEB` sera répliquée vers la région primaire (USA Est 2) et placées dans le réseau de production (`VNET-PROD-EUS2`) :
  - La machine virtuelle web résidera dans le sous-réseau frontal (`PROD-FE-EUS2`).
- La base de données de l’application sera migrée vers le serveur Azure Database pour MySQL à l’aide d’outils d’[Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview).
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

    ![Architecture du scénario](./media/contoso-migration-rehost-linux-vm-mysql/architecture.png)

## <a name="migration-process"></a>Processus de migration

Contoso va effectuer le processus de migration comme suit :

Pour migrer la machine virtuelle web :

- Dans un premier temps, Contoso configure les infrastructures Azure et locale nécessaires pour déployer Azure Migrate.
- Dans la mesure où [l’infrastructure Azure](./contoso-migration-infrastructure.md) est déjà en place, Contoso doit simplement ajouter et configurer la réplication des machines virtuelles par le biais d’Azure Migrate : d’Azure Migrate.
- Une fois tous les éléments préparés, Contoso peut commencer à répliquer la machine virtuelle.
- Une fois la réplication activée et opérationnelle, Contoso effectue le déplacement à l’aide d’Azure Migrate.

Pour migrer la base de données :

1. Contoso approvisionne une instance MySQL dans Azure.
2. Contoso configure Azure Database Migration Service (DMS), en assurant un accès au serveur de base de données local.
3. Contoso migre la base de données vers Azure Database pour MySQL.

    ![Processus de migration](./media/contoso-migration-rehost-linux-vm-mysql/migration-process.png)

### <a name="azure-services"></a>Services Azure

**Service** | **Description** | **Coût**
--- | --- | ---
[Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview) | Contoso utilise le service Azure Migrate pour évaluer ses machines virtuelles VMware. Azure Migrate évalue la pertinence de la migration des ordinateurs. Il fournit des estimations de dimensionnement et de coût pour l’exécution des machines dans Azure. | Bien qu’[Azure Migrate](https://azure.microsoft.com/pricing/details/azure-migrate) soit disponible sans frais supplémentaires, vous pouvez avoir à payer des frais en fonction des outils (internes ou éditeurs de logiciels indépendants) que vous décidez d’utiliser pour l’évaluation et la migration.
[Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview) | Azure Database Migration Service permet une migration fluide à partir de plusieurs sources de base de données vers des plateformes de données Azure, avec un temps d’arrêt minimal. | Apprenez-en davantage sur les [régions prises en charge](https://docs.microsoft.com/azure/dms/dms-overview#regional-availability) et sur la [tarification de Database Migration Service](https://azure.microsoft.com/pricing/details/database-migration).
[Azure Database pour MySQL](https://docs.microsoft.com/azure/mysql) | La base de données est basée sur le moteur du serveur MySQL open source. Il s’agit d’une base de données MySQL complètement managée et de classe Entreprise, appuyée par une communauté, pour le développement et le déploiement d’applications. | En savoir plus sur les options d’évolutivité et de [tarification](https://azure.microsoft.com/pricing/details/mysql) d’Azure Database pour MySQL.

## <a name="prerequisites"></a>Prérequis

Voici ce dont Contoso a besoin pour ce scénario.

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
**Abonnement Azure** | Dans un article précédent, Contoso a créé des abonnements. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial). <br><br> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions. <br><br> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur. <br><br> S’il vous faut plus d’autorisations granulaires, consultez [cet article](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infrastructure Azure** | Contoso configure l’infrastructure Azure comme décrit dans [Infrastructure Azure pour la migration](./contoso-migration-infrastructure.md).
**Serveurs locaux** | Le serveur vCenter Server local doit exécuter la version 5.5, 6.0, 6.5 ou 6.7. <br><br> Un hôte ESXi qui exécute la version 5.5, 6.0, 6.5 ou 6.7. <br><br> Une ou plusieurs machines virtuelles VMware exécutées sur l’hôte ESXi.
**Machines virtuelles locales** | [Examinez les machines Linux](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros) approuvées pour s’exécuter sur Azure.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment les administrateurs de Contoso effectuent la migration :

> [!div class="checklist"]
>
> - **Étape 1 : Préparer Azure pour Server Migration d’Azure Migrate.** L’outil de migration de serveur a été ajouté dans le projet Azure Migrate.
> - **Étape 2 : Préparer l’instance VMware locale pour Server Migration d’Azure Migrate.** Ils préparent des comptes pour la découverte de machines virtuelles. Ils préparent également la connexion à la machine virtuelle Azure après migration.
> - **Étape 3 : Répliquer les machines virtuelles.** Ils configurent la réplication et de commencer à répliquer des machines virtuelles dans le stockage Azure.
> - **Étape 4 : Migrer la machine virtuelle d’application avec Server Migration d’Azure Migrate.** Ils effectuent un test de basculement pour vérifier que tout fonctionne correctement, puis opèrent un basculement complet pour migrer la machine virtuelle vers Azure.
> - **Étape 5 : Migrer la base de données.** Ils configurent la migration à l’aide d’Azure Database Migration Service (DMS).

## <a name="step-1-prepare-azure-for-the-azure-migrate-server-migration-tool"></a>Étape 1 : Préparer Azure pour Azure Migrate : Outil Server Migration

Les composants Azure dont Contoso a besoin pour migrer les machines virtuelles vers Azure sont les suivants :

- Un réseau virtuel dans lequel les machines virtuelles Azure seront situées après leur création pendant la migration.
- Azure Migrate : L’outil Server Migration (OVA) provisionné et configuré.

La configuration est effectuée´comme suit :

1. Configurez un réseau. Contoso a déjà configuré un réseau utilisable pour Server Migration d’Azure Migrate lors du [déploiement de l’infrastructure Azure](./contoso-migration-infrastructure.md).

2. Provisionner l’outil Server Migration d’Azure Migrate.

    - À partir d’Azure Migrate, téléchargez l’image OVA et importez-la dans VMWare.

        ![Télécharger le fichier OVA](./media/contoso-migration-rehost-vm/migration-download-ova.png)

    - Démarrez l’image importée et configurez l’outil, en procédant comme suit :

      - Remplir les conditions préalables.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-setup-prerequisites.png)

      - Pointez l’outil sur l’abonnement Azure.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-register-azure.png)

      - Définissez les informations d’identification de VMWare vCenter.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-vcenter-server.png)

      - Ajoutez les informations d’identification basées sur Linux pour la découverte.

        ![Configurer l’outil](./media/contoso-migration-rehost-vm/migration-credentials.png)

3. Une fois configuré, l’outil peut mettre un certain temps à énumérer tous les ordinateurs virtuels. Une fois terminé, vous constaterez qu’ils sont renseignés dans l’outil Azure Migrate dans Azure.

**Besoin de plus d’aide ?**

[Découvrez](https://docs.microsoft.com/azure/migrate) comment configurer l’outil Server Migration d’Azure Migrate.

## <a name="step-2-prepare-on-premises-vmware-for-azure-migrate-server-migration"></a>Étape 2 : Préparer l’instance VMware locale pour Azure Migrate : Server Migration

Après la migration vers Azure, Contoso souhaite pouvoir se connecter aux machines virtuelles répliquées dans Azure. Pour cela, les administrateurs de Contoso doivent effectuer quelques opérations :

- Pour accéder à la machine virtuelle Azure, ils activent SSH sur la machine virtuelle Linux locale avant la migration. Pour Ubuntu, cette opération peut être effectuée à l’aide de la commande suivante : `sudo apt-get ssh install -y`.

- Après avoir exécuté la migration, ils peuvent consulter les **diagnostics de démarrage** pour voir une capture d’écran de la machine virtuelle.

- Si cela ne fonctionne pas, ils devront vérifier que la machine virtuelle est en cours d’exécution et consulter ces [conseils de dépannage](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

- Installez l’[agent Linux Azure](https://docs.microsoft.com/azure/virtual-machines/extensions/agent-linux).

**Besoin de plus d’aide ?**

- [En savoir plus](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm#prepare-vms-for-migration) sur la préparation des machines virtuelles pour la migration.

## <a name="step-3-replicate-vm"></a>Étape 3 : Répliquer la machine virtuelle

Les administrateurs de Contoso peuvent exécuter une migration vers Azure, ils doivent configurer et activer la réplication.

Une fois la découverte terminée, ils peuvent commencer la réplication de la machine virtuelle d’application vers Azure.

1. Dans le projet Azure Migrate > **Serveurs**, **Azure Migrate : Server Migration**, cliquez sur **Répliquer**.

    ![Répliquer des machines virtuelles](./media/contoso-migration-rehost-linux-vm/select-replicate.png)

2. Dans **Répliquer** > **Paramètres de la source** > **Vos machines sont-elles virtualisées ?** , sélectionnez **Oui, avec VMware vSphere**.

3. Dans **Appliance locale**, sélectionnez le nom de l’appliance Azure Migrate que vous avez configurée > **OK**.

    ![Paramètres de la source](./media/contoso-migration-rehost-linux-vm/source-settings.png)

4. Dans **Machines virtuelles**, sélectionnez les machines à répliquer.
    - Si vous avez exécuté une évaluation des machines virtuelles, vous pouvez appliquer les recommandations relatives au dimensionnement et au type de disque (Premium/Standard) des machines virtuelles qui apparaissent dans les résultats de l’évaluation. Pour ce faire, dans **Importer les paramètres de migration à partir d’une évaluation Azure Migrate ?** , sélectionnez l’option **Oui**.
    - Si vous n’avez pas exécuté d’évaluation ou que vous ne souhaitez pas utiliser les paramètres de l’évaluation, sélectionnez l’option **Non**.
    - Si vous avez choisi d’utiliser l’évaluation, sélectionnez le groupe de machines virtuelles et le nom de l’évaluation.

    ![Sélectionner l’évaluation](./media/contoso-migration-rehost-linux-vm/select-assessment.png)

5. Dans **Machines virtuelles**, recherchez les machines virtuelles en fonction des besoins et cochez chaque machine virtuelle que vous souhaitez migrer. Cliquez ensuite sur **Suivant : Paramètres de la cible**.

6. Dans **Paramètres de la cible**, sélectionnez l’abonnement et la région cible vers laquelle vous allez migrer, puis spécifiez le groupe de ressources dans lequel les machines virtuelles Azure résideront après la migration. Dans **Réseau virtuel**, sélectionnez le réseau virtuel/sous-réseau Azure auquel les machines virtuelles Azure seront jointes après la migration.

7. Dans **Azure Hybrid Benefit**, sélectionnez ce qui suit :

    - Sélectionnez **Non** si vous ne souhaitez pas appliquer Azure Hybrid Benefit. Cliquez ensuite sur **Suivant**.

8. Dans **Capacité de calcul**, vérifiez le nom, la taille, le type de disque du système d’exploitation et le groupe à haute disponibilité de la machine virtuelle. Les machines virtuelles doivent satisfaire aux [exigences d’Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#vmware-requirements).

    - **Taille de la machine virtuelle :** si vous utilisez les recommandations de l’évaluation, la liste déroulante Taille de la machine virtuelle contient la taille recommandée. Sinon, Azure Migrate choisit une taille qui correspond à la taille la plus proche dans l’abonnement Azure. Vous pouvez également choisir une taille manuelle dans **Taille de la machine virtuelle Azure**.
    - **Disque du système d’exploitation :** spécifiez le disque du système d’exploitation (démarrage) pour la machine virtuelle. Le disque du système d’exploitation est le disque qui contient le chargeur de démarrage et le programme d’installation du système d’exploitation.
    - **Groupe à haute disponibilité :** si la machine virtuelle doit se trouver dans un groupe à haute disponibilité Azure après la migration, spécifiez-le ici. Ce groupe doit figurer dans le groupe de ressources cible que vous spécifiez pour la migration.

9. Dans **Disques**, indiquez si les disques de machine virtuelle doivent être répliqués sur Azure, puis sélectionnez le type de disque (SSD/HDD standard ou disques managés Premium) dans Azure. Cliquez ensuite sur **Suivant**.
    - Vous pouvez exclure des disques de la réplication.
    - Si vous excluez des disques, ils ne seront pas présents sur la machine virtuelle Azure après la migration.

10. Dans **Passer en revue et démarrer la réplication**, passez en revue les paramètres, puis cliquez sur **Répliquer** pour démarrer la réplication initiale pour les serveurs.

> [!NOTE]
> Vous pouvez mettre à jour les paramètres de réplication à tout moment avant le démarrage de la réplication, dans **Gérer** > **Réplication des machines**. Vous ne pouvez pas changer les paramètres après le démarrage de la réplication.

## <a name="step-4-migrate-the-vm-with-azure-migrate-server-migration"></a>Étape 4 : Migrer la machine virtuelle avec Azure Migrate : Server Migration

Les administrateurs de Contoso exécutent un test rapide de migration, puis une migration complète pour déplacer la machine virtuelle web.

### <a name="run-a-test-migration"></a>Exécuter un test de migration

1. Dans **Objectifs de migration** > **Serveurs** > **Azure Migrate : Server Migration**, cliquez sur **Tester les serveurs migrés**.

     ![Tester les serveurs migrés](./media/contoso-migration-rehost-linux-vm/test-migrated-servers.png)

2. Cliquez avec le bouton droit sur la machine virtuelle à tester, puis cliquez sur **Migration de test**.

    ![Migration de test](./media/contoso-migration-rehost-linux-vm/test-migrate.png)

3. Dans **Migration de test**, sélectionnez le réseau virtuel Azure dans lequel la machine virtuelle Azure se trouvera après la migration. Nous vous recommandons d’utiliser un réseau virtuel hors production.
4. Le travail **Migration de test** démarre. Supervisez le travail dans les notifications du portail.
5. Une fois la migration terminée, affichez la machine virtuelle Azure migrée dans **Machines virtuelles** dans le portail Azure. Le nom de la machine a le suffixe **-Test**.
6. Une fois le test terminé, cliquez avec le bouton droit sur la machine virtuelle Azure dans **Réplication des machines**, puis cliquez sur **Nettoyer la migration de test**.

    ![Nettoyer la migration](./media/contoso-migration-rehost-linux-vm/clean-up.png)

### <a name="migrate-the-vm"></a>Migrer la machine virtuelle

Les administrateurs de Contoso peuvent à présent opérer une migration complète pour achever le déplacement.

1. Dans le projet Azure Migrate > **Serveurs** > **Azure Migrate : Server Migration**, cliquez sur **Réplication de serveurs**.

    ![Réplication de serveurs](./media/contoso-migration-rehost-linux-vm/replicating-servers.png)

2. Dans **Réplication des machines**, cliquez avec le bouton droit sur la machine virtuelle > **Migrer**.
3. Dans **Migrer** > **Arrêter les machines virtuelles et effectuer une migration planifiée sans perte de données**, sélectionnez **Oui** > **OK**.
    - Par défaut, Azure Migrate arrête la machine virtuelle locale et exécute une réplication à la demande pour synchroniser tout changement apporté à la machine virtuelle depuis la dernière réplication. Cela permet d’éviter toute perte de données.
    - Si vous ne souhaitez pas arrêter la machine virtuelle, sélectionnez **Non**.
4. Un travail de migration démarre pour la machine virtuelle. Suivez le travail dans les notifications Azure.
5. Une fois le travail terminé, vous pouvez afficher et gérer la machine virtuelle à partir de la page **Machines virtuelles**.

## <a name="step-5-provision-azure-database-for-mysql"></a>Étape 5 : Approvisionner Azure Database pour MySQL

Les administrateurs de Contoso provisionnent une instance de base de données MySQL dans la région USA Est 2 principale.

1. Dans le portail Azure, Contoso crée une base de données Azure Database pour MySQL.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/mysql-1.png)

2. Contoso ajoute le nom **contosoosticket** pour la base de données Azure. Contoso ajoute la base de données au groupe de ressources de production **ContosoRG**, puis spécifient les informations d’identification pour celle-ci.
3. La base de données MySQL locale étant la version 5.7, Contoso sélectionne cette version à des fins de compatibilité. Contoso utilise les tailles par défaut, qui correspondent à leurs exigences en matière de base de données.

     ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/mysql-2.png)

4. Pour les **Options de redondance de sauvegarde**, ils sélectionnent **Géoredondant**. Cette option leur permet de restaurer la base de données dans leur région USA Centre secondaire en cas de panne. Contoso ne peut configurer cette option que lors de l’approvisionnement de la base de données.

     ![Redondance](./media/contoso-migration-rehost-linux-vm-mysql/db-redundancy.png)

5. Dans le réseau **VNET-PROD-EUS2** > **Points de terminaison de service**, Contoso ajoute un point de terminaison de service (un sous-réseau de base de données) pour le service SQL.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/mysql-3.png)

6. Après avoir ajouté le sous-réseau, Contoso crée une règle de réseau virtuel qui permet d’accéder à partir du sous-réseau de base de données au réseau de production.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/mysql-4.png)

## <a name="step-6-migrate-the-database"></a>Étape 6 : Migrer la base de données

Il existe plusieurs méthodes pour déplacer la base de données MySQL. Chaque option vous oblige à créer une instance Azure DB pour MySQL pour la cible. Une fois créée, vous pouvez effectuer la migration à l’aide de deux chemins d’accès :

- 6a : Azure Database Migration Service
- 6b : Sauvegarde et restauration de MySQL Workbench

### <a name="step-6a-migrate-the-database-azure-database-migration-service"></a>Étape 6a : Migrer la base de données (Azure Database Migration Service)

Les administrateurs Contoso migrent la base de données à l’aide des services de migration de base de données Azure à l’aide du [didacticiel de migration pas à pas](https://docs.microsoft.com/azure/dms/tutorial-mysql-azure-mysql-online). Ils peuvent effectuer des migrations en ligne, hors connexion et hybrides (préversion) à l’aide de MySQL 5.6 ou 5.7.

> [!NOTE]
> MySQL 8.0 est pris en charge dans Azure Database pour MySQL, mais l’outil DMS ne prend pas encore en charge cette version.

En résumé, vous devez effectuer les opérations suivantes :

- Vérifiez que toutes les conditions préalables à la migration sont satisfaites :

  - La source du serveur MySQL doit correspondre à la version prise en charge par Azure Database pour MySQL. Azure Database pour MySQL prend en charge : l'édition Communauté de MySQL, le moteur InnoDB et la migration entre la source et la cible avec les mêmes versions.
  - Activez la journalisation binaire dans my.ini (Windows) ou my.cnf (Unix). Si vous ne le faites pas, un message `Error in binary logging. Variable binlog_row_image has value 'minimal'. Please change it to 'full. For more information, see https://go.microsoft.com/fwlink/?linkid=873009` s’affiche pendant l’exécution de l’Assistant Migration.
  - L’utilisateur doit avoir le rôle `ReplicationAdmin`.
  - Migrez les schémas de base de données sans clés étrangères ni déclencheurs.

- Créez un réseau virtuel qui se connecte via ExpressRoute ou VPN à votre réseau local.

- Créez un Azure Database Migration Service avec une référence SKU `Premium` connectée au réseau virtuel.

- Assurez-vous que le service Azure Database Migration Service peut accéder à la base de données MySQL via le réseau virtuel. Cela implique de s’assurer que tous les ports entrants sont autorisés entre Azure et MySQL au niveau du réseau virtuel, du VPN réseau et de la machine qui héberge MySQL.

- Exécutez l’outil Azure Database Migration Service :

  - Créez un projet de migration.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-new-project.png)

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-new-project-02.png)

  - Ajoutez une source (base de données locale).

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-source.png)

  - Sélectionnez une cible.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-target.png)

  - Sélectionnez la ou les bases de données à migrer.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-databases.png)

  - Configurez les paramètres avancés.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-settings.png)

  - Démarrez la réplication et résolvez les erreurs éventuelles.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-monitor.png)

  - Effectuez le dernier basculement.
  
    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-cutover.png)

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-cutover-complete.png)

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-cutover-complete-02.png)
  
  - Rétablissez les clés étrangères et les déclencheurs.

  - Modifiez les applications pour qu’elles utilisent la nouvelle base de données.

    ![MySQL](./media/contoso-migration-rehost-linux-vm-mysql/migration-dms-cutover-apps.png)

### <a name="step-6b-migrate-the-database-mysql-workbench"></a>Étape 6b : Migrer la base de données (MySQL Workbench)

Les administrateurs de Contoso migrent la base de données en utilisant la sauvegarde et la restauration, avec des outils MySQL. Contoso installe MySQL Workbench, sauvegardent la base de données à partir de OSTICKETMYSQL, puis la restaurent sur Azure Database pour MySQL.

### <a name="install-mysql-workbench"></a>Installer MySQL Workbench

1. Ils vérifient les [prérequis et téléchargent MySQL Workbench](https://dev.mysql.com/downloads/workbench/?utm_source=tuicool).

2. Contoso installe MySQL Workbench pour Windows conformément aux [instructions d’installation](https://dev.mysql.com/doc/workbench/en/wb-installing.html).

3. Dans MySQL Workbench, Contoso crée une connexion MySQL à OSTICKETMYSQL.

    ![MySQL Workbench](./media/contoso-migration-rehost-linux-vm-mysql/workbench1.png)

4. Contoso exporte la base de données en tant que **osticket** dans un fichier autonome local.

    ![MySQL Workbench](./media/contoso-migration-rehost-linux-vm-mysql/workbench2.png)

5. Une fois la base de données sauvegardée localement, Contoso crée une connexion à l’instance Azure Database pour MySQL.

    ![MySQL Workbench](./media/contoso-migration-rehost-linux-vm-mysql/workbench3.png)

6. À présent, ils peuvent importer (restaurer) la base de données dans l’instance Azure Database pour MySQL à partir du fichier autonome. Un nouveau schéma (osticket) est créé pour l’instance.

    ![MySQL Workbench](./media/contoso-migration-rehost-linux-vm-mysql/workbench4.png)

### <a name="connect-the-vm-to-the-database"></a>Connecter la machine virtuelle à la base de données

La dernière étape du processus de migration consiste pour les administrateurs de Contoso à mettre à jour la chaîne de connexion de l’application pour la faire pointer vers la base de données d’application s’exécutant sur la machine virtuelle **OSTICKETMYSQL**.

1. Ils établissent une connexion SSH à la machine virtuelle **OSTICKETWEB** à l’aide de Putty ou d’un autre client SSH. La machine virtuelle étant privée, Contoso établit la connexion en utilisant l’adresse IP privée.

    ![Connecter à la base de données](./media/contoso-migration-rehost-linux-vm/db-connect.png)

    ![Connecter à la base de données](./media/contoso-migration-rehost-linux-vm/db-connect2.png)

2. Ils ont besoin de s’assurer que la machine virtuelle **OSTICKETWEB** peut communiquer avec la machine virtuelle **OSTICKETMYSQL**. Actuellement, la configuration est codée en dur avec l’adresse IP locale 172.16.0.43.

    **Avant la mise à jour :**

    ![Mettre à jour l’adresse IP](./media/contoso-migration-rehost-linux-vm/update-ip1.png)

    **Après la mise à jour :**

    ![Mettre à jour l’adresse IP](./media/contoso-migration-rehost-linux-vm/update-ip2.png)

3. Ils redémarrent le service avec `systemctl restart apache2`.

    ![Redémarrer](./media/contoso-migration-rehost-linux-vm/restart.png)

4. Enfin, ils mettent à jour les enregistrements DNS pour **OSTICKETWEB** et **OSTICKETMYSQL** sur l’un des contrôleurs de domaine de Contoso.

    ![Mettre à jour le DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

    ![Mettre à jour le DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

**Besoin de plus d’aide ?**

- [En savoir plus](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#run-a-test-migration) sur l’exécution d’un test de basculement.
- [En savoir plus](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#migrate-vms) sur la migration de machines virtuelles vers Azure.

## <a name="review-the-deployment"></a>Examiner le déploiement

L’application étant en cours d’exécution, Contoso doit à présent rendre son infrastructure entièrement opérationnelle et la sécuriser.

## <a name="clean-up-after-migration"></a>Nettoyer après la migration

Une fois la migration terminée, les niveaux de l’application osTicket s’exécutent sur des machines virtuelles Azure.

Contoso doit à présent procéder comme suit :

- Supprimer les machines virtuelles VMware du stock vCenter.
- Supprimer les machines virtuelles locales des travaux de sauvegarde locale.
- Mettre à jour la documentation interne afin qu’elle indique les nouveaux emplacements et adresses IP.
- Passer en revue toutes les ressources qui interagissent avec les machines virtuelles locales, et mettre à jour les paramètres ou la documentation appropriés afin de refléter la nouvelle configuration.
- Contoso a utilisé le service Azure Migrate avec le mappage de dépendance pour évaluer la machine virtuelle **OSTICKETWEB** pour la migration.

### <a name="security"></a>Sécurité

L’équipe de sécurité de Contoso examine la machine virtuelle et la base de données afin d’identifier d’éventuels problèmes de sécurité.

- Elle examine les groupes de sécurité réseau (NSG) pour la machine virtuelle, afin de contrôler l’accès. Contoso utilise des groupes de sécurité réseau pour s’assurer que seul le trafic autorisé vers l’application puisse passer.
- L’équipe prend en considération la sécurisation des données sur les disques de machine virtuelle en utilisant le chiffrement de disque et Azure Key Vault.
- La communication entre la machine virtuelle et l’instance de base de données n’est pas configurée pour SSL. Contoso doit faire cela pour s’assurer que le trafic de base de données ne puisse pas être piraté.

Pour plus d’informations, consultez les [Meilleures pratiques de sécurité pour les charges de travail IaaS dans Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

### <a name="bcdr"></a>BCDR

Pour assurer la continuité d'activité et la reprise d'activité, Contoso effectue les actions suivantes :

- **Sécuriser les données.** Contoso sauvegarde les données sur la machine virtuelle de l’application à l’aide du service Sauvegarde Azure. [Plus d’informations](https://docs.microsoft.com/azure/backup/backup-overview) Contoso n’a pas besoin de configurer la sauvegarde de la base de données. Azure Database pour MySQL crée automatiquement des sauvegardes de serveur et les stocke. Comme Contoso a choisi d’utiliser la géo-redondance pour la base de données, celle-ci est résiliente et prête pour la production.

- **Faire en sorte que les applications soient opérationnelles.** Contoso réplique les machines virtuelles de l’application dans Azure vers une région secondaire à l’aide de Site Recovery. [Plus d’informations](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

- Après le déploiement des ressources, Contoso affecte des balises Azure, conformément aux décisions prises pendant le déploiement de l’[infrastructure Azure](./contoso-migration-infrastructure.md#set-up-tagging).
- Il n’y a aucun problème de licence pour les serveurs Ubuntu de Contoso.
- Contoso utilise [Azure Cost Management](https://azure.microsoft.com/services/cost-management) pour s’assurer qu’ils ne dépassent pas les budgets établis par leur direction informatique.
