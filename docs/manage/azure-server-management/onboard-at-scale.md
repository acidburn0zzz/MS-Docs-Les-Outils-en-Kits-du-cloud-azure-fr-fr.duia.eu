---
title: Configurer le service pour un abonnement
description: Découvrez comment configurer les services de gestion de serveur Azure pour un abonnement en déployant des agents de service sur vos serveurs et en activant des solutions de gestion.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 9347c0c9517327dfa01bc49e344dfcc8ed90e60d
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219714"
---
<!-- cSpell:ignore VMUUID kusto -->

# <a name="configure-azure-server-management-services-at-scale"></a>Configurer les services de gestion de serveur Azure à l’échelle

Vous devez effectuer ces deux tâches pour intégrer les services de gestion de serveur Azure dans vos serveurs :

- Déployer des agents de service sur vos serveurs.
- Activer les solutions de gestion.

Cet article aborde les trois processus suivants nécessaires pour effectuer ces tâches :

1. Déployer les agents requis sur des machines virtuelles Azure à l’aide d’Azure Policy.
1. Déployer les agents requis sur les serveurs locaux.
1. Activer et configurer les solutions.

> [!NOTE]
> Créez l’[espace de travail Log Analytics et le compte Azure Automation](./prerequisites.md#create-a-workspace-and-automation-account) requis avant d’intégrer des machines virtuelles dans des services de gestion de serveur Azure.

## <a name="use-azure-policy-to-deploy-extensions-to-azure-vms"></a>Utilisez Azure Policy pour déployer des extensions sur des machines virtuelles Azure

Toutes les solutions de gestion décrites dans [Outils et services d’administration d’Azure](./tools-services.md) requièrent que l’agent Log Analytics soit installé sur les machines virtuelles et les serveurs locaux Azure. Vous pouvez intégrer vos machines virtuelles Azure à grande échelle à l’aide d’Azure Policy. Attribuez une stratégie pour vous assurer que l’agent est installé sur vos machines virtuelles Azure et connecté à l’espace de travail Log Analytics approprié.

Azure Policy dispose d’une [initiative de stratégie](https://docs.microsoft.com/azure/governance/policy/concepts/definition-structure#initiatives) intégrée qui inclut l’agent Log Analytics et [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-onboard#the-microsoft-dependency-agent), requis par Azure Monitor pour machines virtuelles.

<!-- TODOBACKLOG: Add these when available.
**Preview:** Enable Azure Monitor for virtual machine scale sets.
**Preview:** Enable Azure Monitor for VMs.
 -->

> [!NOTE]
> Pour plus d’informations sur les différents agents de la surveillance Azure, consultez [Vue d’ensemble des agents de surveillance Azure](https://docs.microsoft.com/azure/azure-monitor/platform/agents-overview).

### <a name="assign-policies"></a>Attribuer des stratégies

Pour attribuer les stratégies décrites dans la section précédente :

1. Dans le Portail Azure, accédez à **Azure Policy** > **Affectations** > **Affecter l’initiative**.

    ![Capture d’écran de l’interface de stratégie du portail](./media/onboarding-at-scale1.png)

2. Dans la page **Assigner une stratégie**, définissez l’**Étendue** en sélectionnant les points de suspension (...), puis en sélectionnant un groupe d’administration ou un abonnement. Sélectionnez éventuellement un groupe de ressources. Choisissez **Sélectionner** au bas de la page **Étendue**. L’étendue détermine les ressources ou le groupe de ressources auquel la stratégie est attribuée.

3. Sélectionnez les points de suspension ( **…** ) en regard de **Définition de stratégie** pour ouvrir la liste des définitions disponibles. Pour filtrer la définition de l’initiative, entrez **Azure Monitor** dans la zone **Recherche** :

    ![Capture d’écran de l’interface de stratégie du portail](./media/onboarding-at-scale2.png)

4. Le **Nom de l’attribution** est automatiquement rempli avec le nom de stratégie que vous avez sélectionné, mais vous pouvez le modifier. Vous pouvez également ajouter une description facultative pour fournir plus d’informations sur cette attribution de stratégie. Le champ **Affectée par** est automatiquement renseigné en fonction de l’utilisateur connecté. Ce champ est facultatif et prend en charge des valeurs personnalisées.

5. Pour cette stratégie, sélectionnez **Espace de travail Log Analytics** comme agent Log Analytics à associer.

    ![Capture d’écran de l’interface de stratégie du portail](./media/onboarding-at-scale3.png)

6. Cochez la case **Emplacement de l’identité managée**. Si cette stratégie est du type [DeployIfNotExists](https://docs.microsoft.com/azure/governance/policy/concepts/effects#deployifnotexists), une identité gérée est requise pour son déploiement. Dans le portail, le compte sera créé comme indiqué par la case à cocher.

7. Sélectionnez **Attribuer**.

Après que vous avez terminé l’Assistant, l’attribution de stratégie est déployée dans l’environnement. L’entrée en application de la stratégie peut prendre jusqu’à 30 minutes. Pour tester, créez des machines virtuelles au bout de 30 minutes et vérifiez que Microsoft Monitoring Agent est activé sur la machine virtuelle par défaut.

## <a name="install-agents-on-on-premises-servers"></a>Installer des agents sur des serveurs locaux

> [!NOTE]
> Créez l’[espace de travail Log Analytics et le compte Azure Automation](./prerequisites.md#create-a-workspace-and-automation-account) requis avant d’intégrer les services de gestion de serveur Azure dans les serveurs.

Pour les serveurs locaux, vous devez télécharger et installer manuellement [l’agent Log Analytics et l’agent de dépendances Microsoft](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud) et les configurer pour qu’ils se connectent à l’espace de travail correct. Vous devez spécifier l’ID de l’espace de travail et les informations de clé. Pour obtenir ces informations, accédez à votre espace de travail Log Analytics sur le portail Azure, puis sélectionnez **Paramètres** > **Paramètres avancés**.

![Capture d’écran des paramètres avancés de l’espace de travail Log Analytics dans le Portail Azure](./media/onboarding-on-premises.png)

## <a name="enable-and-configure-solutions"></a>Activer et configurer des solutions

Pour activer les solutions, vous devez configurer l’espace de travail Log Analytics. Les machines virtuelles Azure et les serveurs locaux intégrés obtiendront les solutions à partir des espaces de travail Log Analytics auxquels ils sont connectés.

### <a name="update-management"></a>Update Management

Les solutions Update Management, Change Tracking et d’inventaire nécessitent à la fois un espace de travail Log Analytics et un compte Automation. Pour vous assurer que ces ressources sont correctement configurées, nous vous recommandons d’intégrer votre compte Automation. Pour plus d’informations, consultez [Intégrer les solutions Update Management, Change Tracking et Inventory](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

Nous vous recommandons d’activer la solution Update Management pour tous les serveurs. Update Management est gratuit pour les machines virtuelles Azure et les serveurs locaux. Si vous activez Update Management par le biais de votre compte Automation, une [configuration d’étendue](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account#scope-configuration) est créée dans l’espace de travail. Mettez à jour manuellement l’étendue pour inclure les machines couvertes par le service Update Management.

Pour couvrir vos serveurs existants ainsi que les futurs serveurs, vous devez supprimer la configuration détendue. Pour ce faire, accédez à votre compte Automation dans le portail Azure. Sélectionnez **Update Management** > **Gérer les machines** > **Activer sur toutes les machines disponibles et futures**. Ce paramètre permet à toutes les machines virtuelles Azure connectées à l’espace de travail d’utiliser Update Management.

![Capture d’écran d’Update Management dans le Portail Azure](./media/onboarding-configuration1.png)

### <a name="change-tracking-and-inventory-solutions"></a>Solutions Change Tracking et Inventory

Pour intégrer les solutions Change Tracking et Inventory, suivez les mêmes étapes que pour Update Management. Pour plus d’informations sur la façon d’intégrer ces solutions à partir de votre compte Automation, consultez [Intégrer les solutions Update Management, Change Tracking et Inventory](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

La solution Change Tracking est gratuite pour les machines virtuelles Azure et coûte 6 euros par nœud et par mois pour les serveurs locaux. Ce coût couvre Change Tracking, Inventory et Desired State Configuration. Si vous voulez inscrire uniquement des serveurs locaux spécifiques, vous pouvez les choisir. Nous vous recommandons d’intégrer tous vos serveurs de production.

#### <a name="opt-in-via-the-azure-portal"></a>Accepter via le Portail Azure

1. Accédez au compte Automation pour lequel Change Tracking et Inventory sont activés.
2. Sélectionnez **Suivi des modifications**.
3. Sélectionnez **Gérer les machines** dans le volet supérieur droit.
4. Sélectionnez **Activer sur les machines sélectionnées**. Sélectionnez ensuite **Ajouter** en regard du nom de l’ordinateur.
5. Sélectionnez **Activer** pour activer la solution pour ces ordinateurs.

![Capture d’écran de Change Tracking dans le Portail Azure](./media/onboarding-configuration2.png)

#### <a name="opt-in-by-using-saved-searches"></a>S’abonner à l’aide de recherches enregistrées

Vous pouvez également configurer la configuration de l’étendue pour accepter des serveurs locaux. La configuration d’étendue utilise des recherches enregistrées.

Pour créer ou modifier la recherche enregistrée, suivez les étapes ci-dessous :

1. Accédez à l’espace de travail Log Analytics lié au compte Automation que vous avez configuré dans les étapes précédentes.

1. Sous **Général**, sélectionnez **Recherches enregistrées**.

1. Dans la zone **Filtre**, entrez **Change Tracking** pour filtrer la liste des recherches enregistrées. Dans les résultats, sélectionnez **MicrosoftDefaultComputerGroup**.

1. Entrez le nom de l’ordinateur ou le VMUUID pour inclure les ordinateurs choisis pour Change Tracking.

    ```kusto
    Heartbeat
    | where AzureEnvironment=~"Azure" or Computer in~ ("list of the on-premises server names", "server1")
    | distinct Computer
    ```

    > [!NOTE]
    > Le nom du serveur doit correspondre exactement à la valeur incluse de l’expression, et il ne doit pas contenir un suffixe de nom de domaine.

1. Sélectionnez **Enregistrer**. Par défaut, la configuration d’étendue est liée à la recherche enregistrée **MicrosoftDefaultComputerGroup**. Elle sera mise à jour automatiquement.

### <a name="azure-activity-log"></a>Journaux d’activité

Le [Journal d’activité Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) fait également partie d’Azure Monitor. Il fournit un insight sur les événements de niveau abonnement qui se produisent dans Azure.

Pour mettre en œuvre cette solution :

1. Sur le portail Azure, ouvrez **Tous les services**, puis sélectionnez **Gestion + gouvernance** > **Solutions**.
2. Dans l’affichage **Solutions**, sélectionnez **Ajouter**.
3. Recherchez **Activity Log Analytics** et sélectionnez-le.
4. Sélectionnez **Create** (Créer).

Vous devez spécifier le **nom de l’espace de travail** que vous avez créé à la section précédente et où la solution est activée.

### <a name="azure-log-analytics-agent-health"></a>Azure Log Analytics Agent Health

La solution Azure Log Analytics Agent Health fait des rapports sur l’intégrité, les performances et la disponibilité de vos serveurs Windows et Linux.

Pour mettre en œuvre cette solution :

1. Sur le portail Azure, ouvrez **Tous les services**, puis sélectionnez **Gestion + gouvernance** > **Solutions**.
2. Dans l’affichage **Solutions**, sélectionnez **Ajouter**.
3. Recherchez **Azure Log Analytics Agent Health** et sélectionnez-le.
4. Sélectionnez **Create** (Créer).

Vous devez spécifier le **nom de l’espace de travail** que vous avez créé à la section précédente et où la solution est activée.

Une fois la création terminée, l’instance de ressource de l’espace de travail indique **AgentHealthAssessment** lorsque vous sélectionnez **Afficher** > **Solutions**.

### <a name="antimalware-assessment"></a>Antimalware Assessment

La solution Antimalware Assessment vous aide à identifier les serveurs infectés ou un risque accru d’infection par des logiciels malveillants.

Pour mettre en œuvre cette solution :

1. Sur le portail Azure, ouvrez **Tous les services**, puis sélectionnez **Gestion + gouvernance** > **Solutions**.
2. Dans l’affichage **Solutions**, sélectionnez **Ajouter**.
3. Recherchez et sélectionnez **Antimalware Assessment**.
4. Sélectionnez **Create** (Créer).

Vous devez spécifier le **nom de l’espace de travail** que vous avez créé à la section précédente et où la solution est activée.

Une fois la création terminée, l’instance de ressource de l’espace de travail indique **AntiMalware** lorsque vous sélectionnez **Afficher** > **Solutions**.

### <a name="azure-monitor-for-vms"></a>Azure Monitor pour machines virtuelles

Vous pouvez activer [Azure Monitor pour machines virtuelles](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview) via la page d’affichage de l’instance de machine virtuelle, comme décrit dans [Activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation](./onboard-single-vm.md). Vous ne devez pas activer les solutions directement à partir de la page **Solutions** comme vous le faites pour les autres solutions décrites dans cet article. Pour les déploiements à grande échelle, il peut être plus aisé d’utiliser l’[automatisation](./onboarding-automation.md) pour activer les solutions appropriées dans l’espace de travail.

### <a name="azure-security-center"></a>Azure Security Center

Nous vous recommandons d’intégrer tous vos serveurs dans le niveau Azure Security Center *Gratuit*. Cette option fournit un niveau de base d’évaluations de sécurité et de recommandations de sécurité réalisables pour votre environnement. Si vous mettez à niveau vers le niveau *Standard*, vous bénéficiez d’avantages supplémentaires, qui sont abordés en détail dans la [page de tarification de Security Center](https://docs.microsoft.com/azure/security-center/security-center-pricing).

Pour activer le niveau gratuit d’Azure Security Center, procédez comme suit :

1. Accédez à la page du portail **Security Center**.
2. Sous **STRATÉGIE ET CONFORMITÉ**, sélectionnez **Stratégie de sécurité**.
3. Trouvez la ressource de l’espace de travail Log Analytics que vous avez créée dans le volet de droite.
4. Sélectionnez **Modifier les paramètres** pour cet espace de travail.
5. Sélectionnez **Niveau tarifaire**.
6. Sélectionnez l’option **Gratuit**.
7. Sélectionnez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment utiliser l’automatisation pour intégrer des serveurs et créer des alertes.

> [!div class="nextstepaction"]
> [Automatiser l’intégration et la configuration des alertes](./onboarding-automation.md)
