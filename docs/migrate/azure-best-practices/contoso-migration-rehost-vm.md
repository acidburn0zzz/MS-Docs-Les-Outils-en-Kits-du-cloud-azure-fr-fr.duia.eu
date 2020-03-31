---
title: Réhéberger une application locale sur des machines virtuelles Azure avec Azure Site Recovery
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à réhéberger une application locale avec une migration de machines locales vers Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: a3874de7d2dc78edfcf9e483661748749856cc17
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80355755"
---
<!-- cSpell:ignore NSGs WEBVM SQLVM contosohost vcenter contosodc agentless -->

# <a name="rehost-an-on-premises-app-on-azure-vms"></a>Réhéberger une application locale sur des machines virtuelles Azure

Cet article explique comment la société fictive Contoso réhéberge une application frontale Windows .NET à deux niveaux qui s’exécute sur des machines virtuelles VMware en migrant les machines virtuelles de l’application vers celles d’Azure.

L’application SmartHotel360 utilisée dans cet exemple est fournie au format open source. Si vous souhaitez l’utiliser à des fins de test, vous pouvez la télécharger à partir de [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat qu’ils souhaitent obtenir avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso étant en croissance, son infrastructure et ses systèmes locaux subissent une pression.
- **Limiter les risques.** l’application SmartHotel360 est vitale pour l’activité de Contoso. Il veut migrer l’application vers Azure sans risque.
- **Étendre.** Contoso ne souhaite pas modifier l’application, mais veut s’assurer qu’elle est stable.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a épinglé les objectifs de cette migration. Ces objectifs sont utilisés pour déterminer la meilleure méthode de migration :

- Après la migration, l’application dans Azure devra offrir les mêmes performances qu’aujourd’hui dans l’environnement VMware. L’application restera tout aussi vitale dans le cloud que localement.
- Contoso ne souhaite pas investir dans cette application. Elle est importante pour l’activité mais, sous sa forme actuelle, Contoso veut simplement la migrer de manière sécurisée vers le cloud.
- Contoso ne souhaite pas modifier le modèle d’exploitation de cette application. Contoso souhaite interagir avec elle dans le cloud comme elle le fait en local actuellement.
- Contoso ne souhaite pas modifier les fonctionnalités de l’application. Seul son emplacement doit changer.

## <a name="solution-design"></a>Conception de la solution

Après avoir défini précisément les objectifs et les exigences, Contoso conçoit et examine une solution de déploiement et identifie le processus de migration, notamment les services Azure qui seront utilisés pour la migration.

### <a name="current-app"></a>Application actuelle

- L’application est hiérarchisée sur deux machines virtuelles (**WEBVM** et **SQLVM**).
- Les machines virtuelles sont situées sur un hôte VMware ESXi **contosohost1.contoso.com** (version 6.5).
- L’environnement VMware est géré par le serveur vCenter Server 6.5 (**vcenter.contoso.com**) s’exécutant sur une machine virtuelle.
- Contoso dispose d’un centre de données local (contoso-datacenter), avec un contrôleur de domaine local (**contosodc1**).

### <a name="proposed-architecture"></a>Architecture proposée

- Dans la mesure où l’application représente une charge de travail de production, les machines virtuelles de l’application dans Azure résideront dans le groupe de ressources de production ContosoRG.
- Les machines virtuelles de l’application seront migrées vers la région Azure primaire (USA Est 2), et placées dans le réseau de production (VNET-PROD-EUS2).
- La machine virtuelle web frontale résidera dans le sous-réseau frontal (PROD-FE-EUS2) du réseau de production.
- La machine virtuelle de la base de données résidera dans le sous-réseau de la base de données (PROD-FE-EUS2) du réseau de production.
- Les machines virtuelles locales dans le centre de données Contoso seront désaffectées une fois la migration terminée.

![Architecture du scénario](./media/contoso-migration-rehost-vm/architecture.png)

### <a name="database-considerations"></a>Considérations liées à la base de données

Dans le cadre de la conception de la solution, Contoso a fait une comparaison des fonctionnalités entre Azure SQL Database et SQL Server. Les administrateurs ont choisi SQL Server exécuté sur une machine virtuelle IaaS Azure sur la base des considérations suivantes :

- L’utilisation d’une machine virtuelle Azure exécutant SQL Server semble être une bonne solution si Contoso a besoin de personnaliser le système d’exploitation ou le serveur de base de données, ou s’il souhaite colocaliser et exécuter des applications tierces sur la même machine virtuelle.
- Avec Software Assurance, dans le futur Contoso pourra échanger ses licences existantes contre une réduction de tarif sur SQL Database Managed Instance en utilisant Azure Hybrid Benefit pour SQL Server. Ceci permettra économiser jusqu'à 30 % sur Managed Instance.

### <a name="solution-review"></a>Examen de la solution

Contoso évalue la conception proposée en dressant la liste des avantages et des inconvénients.

<!-- markdownlint-disable MD033 -->

**Considération** | **Détails**
--- | ---
**Avantages** | Les deux machines virtuelles de l’application seront déplacées vers Azure sans changement, ce qui simplifie la migration.<br/><br/> Dans la mesure où Contoso utilise une approche lift-and-shift pour les deux machines virtuelles de l’application, aucun outil de migration ou de configuration spécial n’est nécessaire pour la base de données de l’application.<br/><br/> Contoso peut tirer profit de son investissement dans Software Assurance en utilisant Azure Hybrid Benefit.<br/><br/> Contoso conserve le contrôle total des machines virtuelles de l’application dans Azure.
**Inconvénients** | WEBVM et SQLVM exécutent Windows Server 2008 R2. Le système d’exploitation est pris en charge par Azure pour certains rôles (juillet 2018). [Plus d’informations](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines)<br/><br/> Les couches web et données de l’application resteront un point de basculement unique.<br/><br/> SQLVM est en cours d’exécution sur SQL Server 2008 R2, qui ne bénéficie pas du support standard. Toutefois, la prise en charge est assurée pour les machines virtuelles Azure (juillet 2018). [Plus d’informations](https://support.microsoft.com/help/956893)<br/><br/> Contoso devra continuer à prendre en charge l’application sous forme de machines virtuelles Azure au lieu d’opter pour un service managé, tel qu’Azure App Service et Azure SQL Database.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processus de migration

Contoso migrera les machines virtuelles frontales et de base de données d’application vers des machines virtuelles Azure avec la méthode sans agent de l’outil Migration de serveur Azure Migrate.

- Dans un premier temps, Contoso prépare et configure les composants Azure pour l’outil Migration de serveur Azure Migrate et prépare l’infrastructure VMware locale.
- Dans la mesure où l’[infrastructure Azure](./contoso-migration-infrastructure.md) est déjà en place, Contoso doit simplement ajouter et configurer la réplication des machines virtuelles via l’outil Migration de serveur Azure Migrate.
- Une fois tous les éléments préparés, Contoso peut commencer à répliquer les machines virtuelles.
- Lorsque la réplication est activée et opère, la machine virtuelle est migrée en la basculant vers Azure.

![Processus de migration](./media/contoso-migration-rehost-vm/migration-process-az-migrate.png)

### <a name="azure-services"></a>Services Azure

**Service** | **Description** | **Coût**
--- | --- | ---
[Migration de serveur Azure Migrate](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm) | Le service orchestre et gère la migration de vos applications et charges de travail locales, ainsi que les instances de machine virtuelle AWS/GCP. | Lors de la réplication vers Azure, des frais sur le Stockage Azure sont facturés. Des machines virtuelles Azure sont créées en cas de basculement, et entraînent des frais. [En savoir plus](https://azure.microsoft.com/pricing/details/azure-migrate) sur les frais et la tarification.

## <a name="prerequisites"></a>Prérequis

Voici ce dont Contoso a besoin pour exécuter ce scénario.

<!-- markdownlint-disable MD033 -->

**Configuration requise** | **Détails**
--- | ---
**Abonnement Azure** | Contoso a créé des abonnements dans un précédent article de cette série. Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Si vous créez un compte gratuit, vous êtes l’administrateur de votre abonnement et pouvez effectuer toutes les actions.<br/><br/> Si vous utilisez un abonnement existant et que vous n’êtes pas l’administrateur, vous devez collaborer avec l’administrateur pour qu’il vous donne les autorisations Propriétaire ou Contributeur.<br/><br/> S’il vous faut plus d’autorisations granulaires, consultez [cet article](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infrastructure Azure** | [Découvrez comment](./contoso-migration-infrastructure.md) Contoso configure une infrastructure Azure.<br/><br/> En savoir plus sur les [conditions requises](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm#prerequisites) spécifiques pour l’outil Migration de serveur Azure Migrate.
**Serveurs locaux** | Les serveurs vCenter locaux doivent exécuter la version 5.5, 6.0 ou 6.5<br/><br/> Les hôtes ESXi doivent exécuter la version 5.5, 6.0 ou 6.5<br/><br/> Une ou plusieurs machines virtuelles VMware doivent s’exécuter sur l’hôte ESXi.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Étapes du scénario

Voici comment les administrateurs de Contoso exécuteront la migration :

> [!div class="checklist"]
>
> - **Étape 1 : Préparer Azure pour l’outil Migration de serveur Azure Migrate.** L’outil de migration de serveur a été ajouté dans le projet Azure Migrate.
> - **Étape 2 : Préparer l’instance VMware locale pour l’outil Migration de serveur Azure Migrate.** Ils préparent des comptes pour la découverte de machines virtuelles. Ils préparent également la connexion aux machines virtuelles Azure après basculement.
> - **Étape 3 : Répliquer les machines virtuelles.** Ils configurent la réplication et de commencer à répliquer des machines virtuelles dans le stockage Azure.
> - **Étape 4 : Migrer les machines virtuelles avec l’outil Migration de serveur Azure Migrate.** Ils effectuent un test de basculement pour vérifier que tout fonctionne correctement, puis opèrent un basculement complet pour migrer les machines virtuelles vers Azure.

## <a name="step-1-prepare-azure-for-the-azure-migrate-server-migration-tool"></a>Étape 1 : Préparer Azure pour l’outil Migration de serveur Azure Migrate

Les composants Azure dont Contoso a besoin pour migrer les machines virtuelles vers Azure sont les suivants :

- Un réseau virtuel dans lequel les machines virtuelles Azure seront situées après leur création pendant le basculement.
- L’outil Migration de serveur Azure Migrate a été provisionné.

La configuration est effectuée´comme suit :

1. Configurer un réseau : la société Contoso a déjà configuré un réseau utilisable pour l’outil Migration de serveur Azure Migrate lorsqu’elle a [déployé l’infrastructure Azure](./contoso-migration-infrastructure.md).

    - L’application SmartHotel360 est une application de production, et les machines virtuelles seront migrées vers le réseau de production Azure (VNET-PROD-EUS2) dans la région USA Est 2 principale.
    - Les deux machines virtuelles seront placées dans le groupe de ressources ContosoRG utilisé pour les ressources de production.
    - La machine virtuelle frontale de l’application (WEBVM) migrera vers le sous-réseau frontal (PROD-FE-EUS2) dans le réseau de production.
    - La machine virtuelle de la base de données de l’application (SQLVM) migrera vers le sous-réseau de la base de données (PROD-DB-EUS2) dans le réseau de production.

2. Provisionner l’outil Migration de serveur Azure Migrate : avec le réseau et le compte de stockage en place, Contoso crée à présent un coffre Recovery Services (ContosoMigrationVault) et le place dans le groupe de ressources ContosoFailoverRG, dans la région USA Est 2 principale.

    ![Outil Migration de serveur Azure Migrate](./media/contoso-migration-rehost-vm/server-migration-tool.png)

**Besoin de plus d’aide ?**

[En savoir plus](https://docs.microsoft.com/azure/migrate) sur la configuration de l’outil Migration de serveur Azure Migrate.

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Préparer la connexion aux machines virtuelles Azure après le basculement

Après le basculement, Contoso souhaite se connecter aux machines virtuelles Azure. Pour ce faire, les administrateurs effectuent les opérations suivantes avant la migration :

1. Pour l’accès via Internet :

    - Elle active le protocole RDP sur la machine virtuelle locale avant le basculement.
    - Elle s’assure que les règles de TCP et UDP sont ajoutées au profil **Public**.
    - Elle vérifie que le protocole RDP est autorisé dans **Pare-feu Windows** > **Applications autorisées** pour tous les profils.

2. Pour l’accès via le VPN de site à site :

    - Elle active le protocole RDP sur l’ordinateur local.
    - Elle autorise le protocole RDP dans **Pare-feu Windows** -> **Applications et fonctionnalités autorisées** pour les réseaux **Domaine et privé**.
    - Elle définit la stratégie SAN du système d’exploitation sur la machine virtuelle locale sur **OnlineAll**.

De plus, quand elle opèrent un basculement, elle doit vérifier les points suivants :

- Aucune mise à jour de Windows ne peut être en attente sur la machine virtuelle lors du déclenchement d’un basculement. Autrement, il ne sera pas possible de se connecter à la machine virtuelle tant que la mise à jour ne sera pas terminée.
- Après basculement, on peut consulter les **diagnostics de démarrage** pour afficher une capture d’écran de la machine virtuelle. Si cela ne fonctionne pas, il faut vérifier que la machine virtuelle est en cours d’exécution et consulter ces [conseils de dépannage](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

**Besoin de plus d’aide ?**

- [En savoir plus](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm#prepare-vms-for-migration) sur la préparation des machines virtuelles pour la migration

## <a name="step-3-replicate-the-on-premises-vms"></a>Étape 3 : Répliquer les machines virtuelles locales

Les administrateurs de Contoso peuvent exécuter une migration vers Azure, ils doivent configurer et activer la réplication.

Une fois la découverte terminée, vous pouvez commencer la réplication des machines virtuelles VMware sur Azure.

1. Dans le projet Azure Migrate > **Serveurs**, **Azure Migrate : Server Migration**, sélectionnez **Répliquer**.

    ![Répliquer des machines virtuelles](./media/contoso-migration-rehost-vm/select-replicate.png)

2. Dans **Répliquer** > **Paramètres de la source** > **Vos machines sont-elles virtualisées ?** , sélectionnez **Oui, avec VMware vSphere**.

3. Dans **Appliance locale**, sélectionnez le nom de l’appliance Azure Migrate que vous avez configurée > **OK**.

    ![Paramètres de la source](./media/contoso-migration-rehost-vm/source-settings.png)

4. Dans **Machines virtuelles**, sélectionnez les machines à répliquer.
    - Si vous avez exécuté une évaluation des machines virtuelles, vous pouvez appliquer les recommandations relatives au dimensionnement et au type de disque (Premium/Standard) des machines virtuelles qui apparaissent dans les résultats de l’évaluation. Pour ce faire, dans **Importer les paramètres de migration à partir d’une évaluation Azure Migrate ?** , sélectionnez l’option **Oui**.
    - Si vous n’avez pas exécuté d’évaluation ou que vous ne souhaitez pas utiliser les paramètres de l’évaluation, sélectionnez l’option **Non**.
    - Si vous avez choisi d’utiliser l’évaluation, sélectionnez le groupe de machines virtuelles et le nom de l’évaluation.

    ![Sélectionner l’évaluation](./media/contoso-migration-rehost-vm/select-assessment.png)

5. Dans **Machines virtuelles**, recherchez les machines virtuelles en fonction des besoins et cochez chaque machine virtuelle que vous souhaitez migrer. Ensuite, sélectionnez **Next: Paramètres de la cible**.

6. Dans **Paramètres de la cible**, sélectionnez l’abonnement et la région cible vers laquelle vous allez migrer, puis spécifiez le groupe de ressources dans lequel les machines virtuelles Azure résideront après la migration. Dans **Réseau virtuel**, sélectionnez le réseau virtuel/sous-réseau Azure auquel les machines virtuelles Azure seront jointes après la migration.

7. Dans **Azure Hybrid Benefit**, sélectionnez ce qui suit :

    - Sélectionnez **Non** si vous ne souhaitez pas appliquer Azure Hybrid Benefit. Sélectionnez ensuite **Suivant**.
    - Sélectionnez **Oui** si vous avez des machines Windows Server couvertes par des abonnements Software Assurance ou Windows Server actifs et que vous souhaitez appliquer l’avantage aux machines que vous migrez. Sélectionnez ensuite **Suivant**.

8. Dans **Capacité de calcul**, vérifiez le nom, la taille, le type de disque du système d’exploitation et le groupe à haute disponibilité de la machine virtuelle. Les machines virtuelles doivent satisfaire aux [exigences d’Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#vmware-requirements).

    - **Taille de la machine virtuelle :** si vous utilisez les recommandations de l’évaluation, la liste déroulante Taille de la machine virtuelle contient la taille recommandée. Sinon, Azure Migrate choisit une taille qui correspond à la taille la plus proche dans l’abonnement Azure. Vous pouvez également choisir une taille manuelle dans **Taille de la machine virtuelle Azure**.
    - **Disque du système d’exploitation :** spécifiez le disque du système d’exploitation (démarrage) pour la machine virtuelle. Le disque du système d’exploitation est le disque qui contient le chargeur de démarrage et le programme d’installation du système d’exploitation.
    - **Groupe à haute disponibilité :** si la machine virtuelle doit se trouver dans un groupe à haute disponibilité Azure après la migration, spécifiez-le ici. Ce groupe doit figurer dans le groupe de ressources cible que vous spécifiez pour la migration.

9. Dans **Disques**, indiquez si les disques de machine virtuelle doivent être répliqués sur Azure, puis sélectionnez le type de disque (SSD/HDD standard ou disques managés Premium) dans Azure. Sélectionnez ensuite **Suivant**.
    - Vous pouvez exclure des disques de la réplication.
    - Si vous excluez des disques, ils ne seront pas présents sur la machine virtuelle Azure après la migration.

10. Dans **Passer en revue et démarrer la réplication**, examinez les paramètres, puis sélectionnez **Répliquer** pour lancer la réplication initiale des serveurs.

> [!NOTE]
> Vous pouvez mettre à jour les paramètres de réplication à tout moment avant le démarrage de la réplication, dans **Gérer** > **Réplication des machines**. Vous ne pouvez pas changer les paramètres après le démarrage de la réplication.

## <a name="step-4-migrate-the-vms"></a>Étape 4 : Migrer les machines virtuelles

Les administrateurs de Contoso exécutent un test rapide de basculement, puis un basculement complet pour migrer les machines virtuelles.

### <a name="run-a-test-failover"></a>Exécuter un test de basculement

1. Dans **Objectifs de migration** > **Serveurs** > **Azure Migrate : Server Migration**, sélectionnez **Tester les serveurs migrés**.

     ![Tester les serveurs migrés](./media/contoso-migration-rehost-vm/test-migrated-servers.png)

2. Cliquez avec le bouton droit sur la machine virtuelle à tester, puis sélectionnez **Migration de test**.

    ![Migration de test](./media/contoso-migration-rehost-vm/test-migrate.png)

3. Dans **Migration de test**, sélectionnez le réseau virtuel Azure dans lequel la machine virtuelle Azure se trouvera après la migration. Nous vous recommandons d’utiliser un réseau virtuel hors production.
4. Le travail **Migration de test** démarre. Supervisez le travail dans les notifications du portail.
5. Une fois la migration terminée, affichez la machine virtuelle Azure migrée dans **Machines virtuelles** dans le portail Azure. Le nom de la machine a le suffixe **-Test**.
6. Une fois le test terminé, cliquez avec le bouton droit sur la machine virtuelle Azure dans **Réplication des machines**, puis sélectionnez **Nettoyer la migration de test**.

    ![Nettoyer la migration](./media/contoso-migration-rehost-vm/clean-up.png)

### <a name="migrate-the-vms"></a>Migrer les machines virtuelles

Les administrateurs de Contoso peuvent à présent opérer un basculement complet pour achever la migration.

1. Dans le projet Azure Migrate > **Serveurs** > **Azure Migrate : Server Migration**, puis sélectionnez **Réplication de serveurs**.

    ![Réplication de serveurs](./media/contoso-migration-rehost-vm/replicating-servers.png)

2. Dans **Réplication des machines**, cliquez avec le bouton droit sur la machine virtuelle > **Migrer**.
3. Dans **Migrer** > **Arrêter les machines virtuelles et effectuer une migration planifiée sans perte de données**, sélectionnez **Oui** > **OK**.
    - Par défaut, Azure Migrate arrête la machine virtuelle locale et exécute une réplication à la demande pour synchroniser tout changement apporté à la machine virtuelle depuis la dernière réplication. Cela permet d’éviter toute perte de données.
    - Si vous ne souhaitez pas arrêter la machine virtuelle, sélectionnez **Non**.
4. Un travail de migration démarre pour la machine virtuelle. Suivez le travail dans les notifications Azure.
5. Une fois le travail terminé, vous pouvez afficher et gérer la machine virtuelle à partir de la page **Machines virtuelles**.

**Besoin de plus d’aide ?**

- [En savoir plus sur](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#run-a-test-migration) l’exécution d’un test de basculement.
- [En savoir plus](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#migrate-vms) sur la migration de machines virtuelles vers Azure.

## <a name="clean-up-after-migration"></a>Nettoyer après la migration

Une fois la migration terminée, les niveaux de l’application SmartHotel360 s’exécutent sur des machines virtuelles Azure.

Contoso doit à présent effectuer les étapes de nettoyage suivantes :

- Au terme de la migration, arrêtez la réplication.
- Supprimer la machine virtuelle WEBVM de l’inventaire vCenter.
- Supprimer la machine virtuelle SQLVM de l’inventaire vCenter.
- Supprimer les machines virtuelles WEBVM et SQLVM des travaux de sauvegarde locaux.
- Mettre à jour la documentation interne afin qu’elle indique le nouvel emplacement et les adresses IP des machines virtuelles.
- Passer en revue toutes les ressources qui interagissent avec les machines virtuelles, et mettre à jour les paramètres ou la documentation appropriés afin de refléter la nouvelle configuration.

## <a name="review-the-deployment"></a>Examiner le déploiement

L’application étant en cours d’exécution, Contoso doit à présent la rendre entièrement opérationnelle et la sécuriser dans Azure.

### <a name="security"></a>Sécurité

L’équipe de sécurité de Contoso examine les machines virtuelles Azure afin d’identifier d’éventuels problèmes de sécurité.

- Pour contrôler l’accès, l’équipe examine les groupes de sécurité réseau (NSG) des machines virtuelles. Les groupes de sécurité réseau sont utilisés pour s’assurer que seul le trafic autorisé vers l’application puisse atteindre celle-ci.
- L’équipe envisage également la sécurisation des données sur le disque à l’aide d’Azure Disk Encryption et de Key Vault.

Pour plus d’informations, consultez les [Meilleures pratiques de sécurité pour les charges de travail IaaS dans Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

## <a name="bcdr"></a>BCDR

Pour assurer la continuité et la reprise d’activité (BCDR), Contoso effectue les actions suivantes :

- Sécuriser les données : Contoso sauvegarde les données sur les machines virtuelles à l’aide du service Sauvegarde Azure. [Plus d’informations](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)
- Faire en sorte que les applications soient opérationnelles : Contoso réplique les machines virtuelles de l’application dans Azure vers une région secondaire à l’aide de Site Recovery. [Plus d’informations](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

### <a name="licensing-and-cost-optimization"></a>Gestion des licences et optimisation des coûts

1. Contoso a un contrat de licence pour ses machines virtuelles et tirera parti d’Azure Hybrid Benefit. Contoso va convertir les machines virtuelles Azure existantes pour tirer parti de cette tarification.
2. Contoso va activer Azure Cost Management sous licence de Cloudyn, une filiale de Microsoft. Il s’agit d’une solution de gestion des coûts multicloud qui vous aide à utiliser et à gérer Azure ainsi que d’autres ressources cloud. [En savoir plus](https://docs.microsoft.com/azure/cost-management/overview) sur Azure Cost Management.

## <a name="conclusion"></a>Conclusion

Cet article décrit comment Contoso a réhébergé l’application SmartHotel360 dans Azure en migrant les machines virtuelles de l’application vers des machines virtuelles Azure avec l’outil Migration de serveur Azure Migrate.
