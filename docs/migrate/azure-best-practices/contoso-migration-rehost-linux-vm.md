---
title: réhéberger une application Linux locale sur des machines virtuelles Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment Contoso réhéberge une application Linux locale en la migrant vers des machines virtuelles Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: c1d7549a820b8f830fc577ce82ebc4d2f1dbfcb2
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566544"
---
# <a name="rehost-an-on-premises-linux-app-to-azure-vms"></a>réhéberger une application Linux locale sur des machines virtuelles Azure

Cet article explique comment la société fictive Contoso réhéberge une application Apache MySQL PHP (LAMP) à deux niveaux et basée sur Linux à l’aide de machines virtuelles IaaS Azure.

osTicket, l’application de bureau de service utilisée dans cet exemple, est fournie au format open source. Si vous souhaitez l’utiliser à des fins de test, vous pouvez la télécharger à partir de [GitHub](https://github.com/osTicket/osTicket).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat qu’ils souhaitent obtenir avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso étant en croissance, son infrastructure et ses systèmes locaux subissent une pression.
- **Limiter les risques.** l’application de Service Desk est vitale pour l’activité de Contoso. Contoso veut la migrer vers Azure sans risque.
- **Étendre.** Contoso ne souhaite pas modifier l’application dans l’immédiat. L’entreprise veut simplement qu’elle soit stable.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a épinglé les objectifs de cette migration, afin de déterminer la meilleure méthode de migration :

- Après la migration, l’application dans Azure doit offrir les mêmes performances qu’aujourd’hui dans l’environnement VMware local. L’application restera tout aussi vitale dans le cloud que localement.
- Contoso ne souhaite pas investir dans cette application. Elle est importante pour l’activité mais, sous sa forme actuelle, Contoso veut simplement la migrer de manière sécurisée vers le cloud.
- Contoso ne souhaite pas modifier le modèle d’exploitation de cette application. L’entreprise souhaite interagir avec elle dans le cloud de la même façon qu’actuellement.
- Contoso ne souhaite pas modifier les fonctionnalités de l’application. Seul son emplacement doit changer.
- Après avoir effectué quelques migrations d’application Windows, Contoso souhaite apprendre à utiliser une infrastructure basée sur Linux dans Azure.

## <a name="solution-design"></a>Conception de la solution

Après avoir défini précisément les objectifs et les exigences, Contoso conçoit et examine une solution de déploiement et identifie le processus de migration, notamment les services Azure qui seront utilisés pour la migration.

### <a name="current-app"></a>Application actuelle

- L’application OSTicket est répartie sur deux machines virtuelles (**OSTICKETWEB** et **OSTICKETMYSQL**).
- Les machines virtuelles sont situées sur un hôte VMware ESXi **contosohost1.contoso.com** (version 6.5).
- L’environnement VMware est géré par le serveur vCenter Server 6.5 (**vcenter.contoso.com**) s’exécutant sur une machine virtuelle.
- Contoso dispose d’un centre de données local (**contoso-datacenter**), avec un contrôleur de domaine local (**contosodc1**).

### <a name="proposed-architecture"></a>Architecture proposée

- Dans la mesure où l’application représente une charge de travail de production, les machines virtuelles dans Azure résideront dans le groupe de ressources de production **ContosoRG**.
- Les machines virtuelles seront migrées vers la région primaire (USA Est 2), et placées dans le réseau de production (VNET-PROD-EUS2) :
  - La machine virtuelle web résidera dans le sous-réseau frontal (PROD-FE-EUS2).
  - La machine virtuelle de l’instance de base de données résidera dans le sous-réseau de la base de données (PROD-DB-EUS2).
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

![Architecture du scénario](./media/contoso-migration-rehost-linux-vm/architecture.png)

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant une liste des avantages et des inconvénients.

<!-- markdownlint-disable MD033 -->

**Considération** | **Détails**
--- | ---
**Avantages** | Les deux machines virtuelles de l’application seront déplacées vers Azure sans changement, ce qui simplifie la migration.<br/><br/> Dans la mesure où Contoso utilise une approche lift-and-shift pour les deux machines virtuelles de l’application, aucun outil de migration ou de configuration spécial n’est nécessaire pour la base de données de l’application.<br/><br/> Contoso conserve le contrôle total des machines virtuelles de l’application dans Azure. <br/><br/> Les machines virtuelles de l’application fonctionnent sous Ubuntu 16.04-TLS, une distribution Linux approuvée. [Plus d’informations](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros)
**Inconvénients** | La couche Web et Données de l’application restera un point de basculement unique. <br/><br/> Contoso devra continuer à prendre en charge l’application sous forme de machines virtuelles Azure au lieu d’opter pour un service géré, comme Azure App Service et Azure Database pour MySQL.<br/><br/> Contoso sait bien que, en faisant simple avec une migration de machines virtuelles lift-and-shift, elle ne profite pas complètement des fonctionnalités offertes par [Azure Database pour MySQL](https://docs.microsoft.com/azure/mysql/overview) (haute disponibilité intégrée, niveau de performance prédictible, mise à l’échelle simple, sauvegardes automatiques et sécurité intégrée).

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processus de migration

Contoso effectuera la migration comme suit :

- Dans un premier temps, Contoso prépare et configure les composants Azure pour l’outil Migration de serveur Azure Migrate et prépare l’infrastructure VMware locale.
- Dans la mesure où l’[infrastructure Azure](./contoso-migration-infrastructure.md) est déjà en place, Contoso doit simplement ajouter et configurer la réplication des machines virtuelles via l’outil Migration de serveur Azure Migrate.
- Une fois tous les éléments préparés, Contoso peut commencer à répliquer les machines virtuelles.
- Lorsque la réplication est activée et opère, la machine virtuelle est migrée en la basculant vers Azure.

![Processus de migration](./media/contoso-migration-rehost-linux-vm/migration-process-az-migrate.png)

### <a name="azure-services"></a>Services Azure

**Service** | **Description** | **Coût**
--- | --- | ---
[Migration de serveur Azure Migrate](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm) | Le service orchestre et gère la migration de vos applications et charges de travail locales, ainsi que les instances de machine virtuelle AWS/GCP. | Lors de la réplication vers Azure, des frais sur le Stockage Azure sont facturés. Des machines virtuelles Azure sont créées en cas de basculement, et entraînent des frais. [En savoir plus](https://azure.microsoft.com/pricing/details/azure-migrate) sur les frais et la tarification.

## <a name="prerequisites"></a>Prérequis

Voici ce dont Contoso a besoin pour ce scénario.

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
**Abonnement Azure** | Contoso a créé des abonnements dans un précédent article de cette série. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions.<br/><br/> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur.<br/><br/> S’il vous faut plus d’autorisations granulaires, consultez [cet article](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infrastructure Azure** |  [Découvrez comment](./contoso-migration-infrastructure.md) Contoso configure une infrastructure Azure.<br/><br/> En savoir plus sur les [conditions requises](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm#prerequisites) spécifiques pour l’outil Migration de serveur Azure Migrate.
**Serveurs locaux** | L’instance vCenter Server locale doit exécuter la version 5.5, 6.0 ou 6.5.<br/><br/> Un hôte ESXi qui exécute la version 5.5, 6.0 ou 6.5<br/><br/> Une ou plusieurs machines virtuelles VMware exécutées sur l’hôte ESXi.
**Machines virtuelles locales** | [Examinez les machines Linux](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros) approuvées pour s’exécuter sur Azure.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment Contoso effectue la migration :

> [!div class="checklist"]
>
> - **Étape 1 : Préparer Azure pour l’outil Migration de serveur Azure Migrate.** L’outil de migration de serveur a été ajouté dans le projet Azure Migrate.
> - **Étape 2 : Préparer l’instance VMware locale pour l’outil Migration de serveur Azure Migrate.** Ils préparent des comptes pour la découverte de machines virtuelles. Ils préparent également la connexion aux machines virtuelles Azure après basculement.
> - **Étape 3 : Répliquer les machines virtuelles.** Ils configurent la réplication et de commencer à répliquer des machines virtuelles dans le stockage Azure.
> - **Étape 4 : Migrer les machines virtuelles avec l’outil Migration de serveur Azure Migrate.** Ils effectuent un test de basculement pour vérifier que tout fonctionne correctement, puis opèrent un basculement complet pour migrer les machines virtuelles vers Azure.

## <a name="step-1-prepare-azure-for-the-azure-migrate-server-migration-tool"></a>Étape 1 : Préparer Azure pour l’outil Migration de serveur Azure Migrate

Les composants Azure dont Contoso a besoin pour migrer les machines virtuelles vers Azure sont les suivants :

- Un réseau virtuel dans lequel les machines virtuelles Azure seront situées après leur création pendant le basculement.
- L’outil Migration de serveur Azure Migrate a été provisionné.

La configuration est effectuée´comme suit :

1. **Configurer un réseau :** la société Contoso a déjà configuré un réseau utilisable pour l’outil Migration de serveur Azure Migrate quand elle a [déployé l’infrastructure Azure](./contoso-migration-infrastructure.md).

    - L’application SmartHotel360 est une application de production, et les machines virtuelles seront migrées vers le réseau de production Azure (VNET-PROD-EUS2) dans la région USA Est 2 principale.
    - Les deux machines virtuelles seront placées dans le groupe de ressources ContosoRG utilisé pour les ressources de production.
    - La machine virtuelle frontale de l’application (WEBVM) migrera vers le sous-réseau frontal (PROD-FE-EUS2) dans le réseau de production.
    - La machine virtuelle de la base de données de l’application (SQLVM) migrera vers le sous-réseau de la base de données (PROD-DB-EUS2) dans le réseau de production.

2. **Provisionner l’outil Migration de serveur Azure Migrate :** Avec le réseau et le compte de stockage en place, Contoso crée à présent un coffre Recovery Services (ContosoMigrationVault) et le place dans le groupe de ressources ContosoFailoverRG, dans la région USA Est 2 principale.

    ![Outil Migration de serveur Azure Migrate](./media/contoso-migration-rehost-linux-vm/server-migration-tool.png)

**Besoin de plus d’aide ?**

[En savoir plus](https://docs.microsoft.com/azure/migrate) sur la configuration de l’outil Migration de serveur Azure Migrate.

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Préparer la connexion aux machines virtuelles Azure après le basculement

Après le basculement vers Azure, Contoso souhaite pouvoir se connecter aux machines virtuelles répliquées dans Azure. Pour cela, les administrateurs de Contoso doivent effectuer quelques opérations :

- Pour accéder aux machines virtuelles par Internet, ils activent SSH sur la machine virtuelle Linux locale avant la migration. Pour Ubuntu, cette opération peut être effectuée à l’aide de la commande suivante : **Sudo apt-get ssh install -y**.
- Après avoir opéré la migration (basculement), ils peuvent consulter les **Diagnostics de démarrage** pour afficher une capture d’écran de la machine virtuelle.
- Si cela ne fonctionne pas, ils devront vérifier que la machine virtuelle est en cours d’exécution et consulter ces [conseils de dépannage](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

**Besoin de plus d’aide ?**

- [En savoir plus](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm#prepare-vms-for-migration) sur la préparation des machines virtuelles pour la migration

## <a name="step-3-replicate-the-on-premises-vms"></a>Étape 3 : Répliquer les machines virtuelles locales

Les administrateurs de Contoso peuvent exécuter une migration vers Azure, ils doivent configurer et activer la réplication.

Une fois la découverte terminée, vous pouvez commencer la réplication des machines virtuelles VMware sur Azure.

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
    - Sélectionnez **Oui** si vous avez des machines Windows Server couvertes par des abonnements Software Assurance ou Windows Server actifs et que vous souhaitez appliquer l’avantage aux machines que vous migrez. Cliquez ensuite sur **Suivant**.

8. Dans **Compute**, vérifiez le nom de la machine virtuelle, sa taille, le type de disque du système d’exploitation et le groupe à haute disponibilité. Les machines virtuelles doivent satisfaire aux [exigences d’Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#agentless-migration-vmware-vm-requirements).

    - **Taille de la machine virtuelle :** si vous utilisez les recommandations de l’évaluation, la liste déroulante Taille de la machine virtuelle contient la taille recommandée. Sinon, Azure Migrate choisit une taille qui correspond à la taille la plus proche dans l’abonnement Azure. Vous pouvez également choisir une taille manuelle dans **Taille de la machine virtuelle Azure**.
    - **Disque du système d’exploitation :** spécifiez le disque du système d’exploitation (démarrage) pour la machine virtuelle. Le disque du système d’exploitation est le disque qui contient le chargeur de démarrage et le programme d’installation du système d’exploitation.
    - **Groupe à haute disponibilité :** si la machine virtuelle doit se trouver dans un groupe à haute disponibilité Azure après la migration, spécifiez-le ici. Ce groupe doit figurer dans le groupe de ressources cible que vous spécifiez pour la migration.

9. Dans **Disques**, indiquez si les disques de machine virtuelle doivent être répliqués sur Azure, puis sélectionnez le type de disque (SSD/HDD standard ou disques managés Premium) dans Azure. Cliquez ensuite sur **Suivant**.
    - Vous pouvez exclure des disques de la réplication.
    - Si vous excluez des disques, il ne seront pas présents sur la machine virtuelle Azure après la migration.

10. Dans **Passer en revue et démarrer la réplication**, passez en revue les paramètres, puis cliquez sur **Répliquer** pour démarrer la réplication initiale pour les serveurs.

> [!NOTE]
> Vous pouvez mettre à jour les paramètres de réplication à tout moment avant le démarrage de la réplication, dans **Gérer** > **Réplication des machines**. Vous ne pouvez pas changer les paramètres après le démarrage de la réplication.

## <a name="step-4-migrate-the-vms"></a>Étape 4 : Migrer les machines virtuelles

Les administrateurs de Contoso exécutent un test rapide de basculement, puis un basculement complet pour migrer les machines virtuelles.

### <a name="run-a-test-failover"></a>Exécuter un test de basculement

1. Dans **Objectifs de migration** > **Serveurs** > **Azure Migrate : Server Migration**, cliquez sur **Tester les serveurs migrés**.

     ![Tester les serveurs migrés](./media/contoso-migration-rehost-linux-vm/test-migrated-servers.png)

2. Cliquez avec le bouton droit sur la machine virtuelle à tester, puis cliquez sur **Migration de test**.

    ![Migration de test](./media/contoso-migration-rehost-linux-vm/test-migrate.png)

3. Dans **Migration de test**, sélectionnez le réseau virtuel Azure dans lequel la machine virtuelle Azure se trouvera après la migration. Nous vous recommandons d’utiliser un réseau virtuel hors production.
4. Le travail **Migration de test** démarre. Supervisez le travail dans les notifications du portail.
5. Une fois la migration terminée, affichez la machine virtuelle Azure migrée dans **Machines virtuelles** dans le portail Azure. Le nom de la machine a le suffixe **-Test**.
6. Une fois le test terminé, cliquez avec le bouton droit sur la machine virtuelle Azure dans **Réplication des machines**, puis cliquez sur **Nettoyer la migration de test**.

    ![Nettoyer la migration](./media/contoso-migration-rehost-linux-vm/clean-up.png)

### <a name="migrate-the-vms"></a>Migrer les machines virtuelles

Les administrateurs de Contoso peuvent à présent opérer un basculement complet pour achever la migration.

1. Dans le projet Azure Migrate > **Serveurs** > **Azure Migrate : Server Migration**, cliquez sur **Réplication de serveurs**.

    ![Réplication de serveurs](./media/contoso-migration-rehost-linux-vm/replicating-servers.png)

2. Dans **Réplication des machines**, cliquez avec le bouton droit sur la machine virtuelle > **Migrer**.
3. Dans **Migrer** > **Arrêter les machines virtuelles et effectuer une migration planifiée sans perte de données**, sélectionnez **Oui** > **OK**.
    - Par défaut, Azure Migrate arrête la machine virtuelle locale et exécute une réplication à la demande pour synchroniser tout changement apporté à la machine virtuelle depuis la dernière réplication. Cela permet d’éviter toute perte de données.
    - Si vous ne souhaitez pas arrêter la machine virtuelle, sélectionnez **Non**.
4. Un travail de migration démarre pour la machine virtuelle. Suivez le travail dans les notifications Azure.
5. Une fois le travail terminé, vous pouvez afficher et gérer la machine virtuelle à partir de la page **Machines virtuelles**.

### <a name="connect-the-vm-to-the-database"></a>Connecter la machine virtuelle à la base de données

La dernière étape du processus de migration consiste pour les administrateurs de Contoso à mettre à jour la chaîne de connexion de l’application pour qu’elle pointe vers la base de données de l’application s’exécutant sur la machine virtuelle **OSTICKETMYSQL**.

1. Ils établissent une connexion SSH à la machine virtuelle **OSTICKETWEB** à l’aide de Putty ou d’un autre client SSH. La machine virtuelle étant privée, ils établissent la connexion en utilisant l’adresse IP privée.

    ![Connecter à la base de données](./media/contoso-migration-rehost-linux-vm/db-connect.png)

    ![Connecter à la base de données](./media/contoso-migration-rehost-linux-vm/db-connect2.png)

2. Ils ont besoin de s’assurer que la machine virtuelle **OSTICKETWEB** peut communiquer avec la machine virtuelle **OSTICKETMYSQL**. Actuellement, la configuration est codée en dur avec l’adresse IP locale 172.16.0.43.

    **Avant la mise à jour :**

    ![Mettre à jour l’adresse IP](./media/contoso-migration-rehost-linux-vm/update-ip1.png)

    **Après la mise à jour :**

    ![Mettre à jour l’adresse IP](./media/contoso-migration-rehost-linux-vm/update-ip2.png)

3. Contoso redémarre le service avec la commande **systemctl restart apache2**.

    ![Redémarrer](./media/contoso-migration-rehost-linux-vm/restart.png)

4. Enfin, ils mettent à jour les enregistrements DNS pour **OSTICKETWEB** et **OSTICKETMYSQL** sur l’un des contrôleurs de domaine de Contoso.

    ![Mettre à jour le DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

    ![Mettre à jour le DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

**Besoin de plus d’aide ?**

- [En savoir plus sur](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#run-a-test-migration) l’exécution d’un test de basculement.
- [En savoir plus](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#migrate-vms) sur la migration de machines virtuelles vers Azure.

## <a name="clean-up-after-migration"></a>Nettoyer après la migration

Une fois la migration terminée, les niveaux de l’application osTicket s’exécutent sur des machines virtuelles Azure.

À présent, Contoso doit effectuer un nettoyage de la façon suivante :

- Supprimer les machines virtuelles locales de l’inventaire vCenter.
- Supprimer les machines virtuelles locales des travaux de sauvegarde locale.
- Mettre à jour sa documentation interne pour afficher le nouvel emplacement et les adresses IP pour OSTICKETWEB et OSTICKETMYSQL.
- Passer en revue toutes les ressources qui interagissent avec les machines virtuelles, et mettre à jour les paramètres ou la documentation appropriés afin de refléter la nouvelle configuration.
- Contoso a utilisé le service Azure Migrate avec le mappage de dépendance pour évaluer les machines virtuelles pour la migration. Les administrateurs doivent supprimer de la machine virtuelle Microsoft Monitoring Agent et Microsoft Dependency Agent, qu’ils ont installés à cette fin.

## <a name="review-the-deployment"></a>Examiner le déploiement

L’application étant en cours d’exécution, Contoso doit à présent rendre son infrastructure entièrement opérationnelle et la sécuriser.

### <a name="security"></a>Sécurité

L’équipe de sécurité de Contoso examine les machines virtuelles OSTICKETWEB les OSTICKETMYSQL pour détecter d’éventuels problèmes de sécurité.

- L’équipe examine les groupes de sécurité réseau (NSG) des machines virtuelles pour en contrôler l’accès. Contoso utilise des groupes de sécurité réseau pour s’assurer que seul le trafic autorisé vers l’application puisse passer.
- L’équipe prend également en considération la sécurisation des données sur les disques de machine virtuelle à l’aide de Disk Encryption et d’Azure Key Vault.

Pour plus d’informations, consultez [Bonnes pratiques de sécurité pour les charges de travail IaaS dans Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

### <a name="bcdr"></a>BCDR

Pour assurer la continuité d'activité et la reprise d'activité, Contoso effectue les actions suivantes :

- **Sécuriser les données.** Contoso sauvegarde les données sur les machines virtuelles à l’aide du service Sauvegarde Azure. [Plus d’informations](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)
- **Faire en sorte que les applications soient opérationnelles.** Contoso réplique les machines virtuelles de l’application dans Azure vers une région secondaire à l’aide de Site Recovery. [Plus d’informations](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

- Après déploiement des ressources, Contoso affecte des balises Azure de la manière définie lors du [déploiement de l’infrastructure Azure](./contoso-migration-infrastructure.md#set-up-tagging).
- Contoso n’a aucun problème de licence avec les serveurs Ubuntu.
- Contoso va activer Azure Cost Management sous licence de Cloudyn, une filiale de Microsoft. Il s’agit d’une solution de gestion des coûts multicloud qui vous aide à utiliser et à gérer Azure ainsi que d’autres ressources cloud. [En savoir plus](https://docs.microsoft.com/azure/cost-management/overview) sur Azure Cost Management.
