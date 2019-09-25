---
title: Configurer les services de gestion Azure pour un abonnement
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Configurer les services de gestion Azure pour un abonnement
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: a5b1d551f52ae8800e9a29d4c8a92c14965645cc
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221495"
---
# <a name="configure-azure-management-services-at-scale"></a>Configurer les services de gestion Azure à l’échelle

L’intégration des services de gestion Azure à vos serveurs implique deux tâches : le déploiement d’agents de service sur vos serveurs et l’activation des solutions de gestion. Cet article aborde les processus suivants qui vous permettront d’effectuer ces tâches :

- [Déploiement des agents requis sur des machines virtuelles Azure à l’aide d’Azure Policy](#deploy-extensions-to-azure-vms-using-azure-policy)
- [Déploiement des agents requis sur les serveurs locaux](#install-required-agents-on-on-premises-servers)
- [Activer et configurer des solutions](#enable-and-configure-solutions)

> [!NOTE]
> Créez l’[espace de travail log Analytics et le compte Azure Automation](./prerequisites.md#create-a-workspace-and-automation-account) requis avant d’intégrer des machines virtuelles aux services de gestion Azure.

## <a name="deploy-extensions-to-azure-vms-using-azure-policy"></a>Déployer des extensions sur des machines virtuelles Azure à l’aide d’Azure Policy

Toutes les solutions de gestion décrites dans [Outils et services d’administration d’Azure](./tools-services.md) exigent que l’agent Log Analytics soit installé sur les machines virtuelles et les serveurs locaux Azure. Vous pouvez intégrer vos machines virtuelles Azure à grande échelle à l’aide d’Azure Policy. Attribuez une stratégie pour vous assurer que l’agent est installé sur toutes vos machines virtuelles Azure et connecté à l’espace de travail Log Analytics approprié.

Azure Policy dispose d’une [initiative de stratégie](/azure/governance/policy/index#initiative-definition) intégrée qui inclut à la fois l’agent Log Analytics et [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-onboard#the-microsoft-dependency-agent), requis par Azure Monitor pour machines virtuelles.

<!-- TODO: Add these when available.
- [Preview]: Enable Azure Monitor for virtual machine scale sets.
- [Preview]: Enable Azure Monitor for VMs.
 -->

> [!NOTE]
> Pour plus d’informations sur les différents agents de la surveillance Azure, consultez [Vue d’ensemble des agents de surveillance Azure](https://docs.microsoft.com/azure/azure-monitor/platform/agents-overview).

### <a name="assign-policies"></a>Attribuer des stratégies

Pour attribuer les stratégies répertoriées à la section précédente :

1. Dans le Portail Azure, accédez à **Azure Policy** > **Affectations** > **Affecter l’initiative**.

    ![Capture d’écran de l’interface de stratégie du portail](./media/onboarding-at-scale1.png)

2. Dans la page **Assigner une stratégie**, sélectionnez **l’étendue** en cliquant sur les points de suspension (…) et en sélectionnant un groupe d’administration ou un abonnement. Sélectionnez éventuellement un groupe de ressources. Une étendue détermine les ressources ou le groupe de ressources auquel la stratégie est attribuée. Choisissez **Sélectionner** au bas de la page **Étendue**.

3. Sélectionnez les points de suspension (…) en regard de **Définition de stratégie** pour ouvrir la liste des définitions disponibles. Vous pouvez filtrer la définition de l’initiative en indiquant **Azure Monitor** dans la zone **Recherche** :

    ![Capture d’écran de l’interface de stratégie du portail](./media/onboarding-at-scale2.png)

4. Le **Nom de l’attribution** est automatiquement rempli avec le nom de stratégie que vous avez sélectionné, mais vous pouvez le modifier. Vous pouvez également ajouter une description facultative pour fournir plus d’informations sur cette attribution de stratégie. Le champ **Affectée par** est automatiquement renseigné en fonction de l’utilisateur connecté. Ce champ étant facultatif, vous pouvez entrer des valeurs personnalisées.

5. Pour cette stratégie, sélectionnez **Espace de travail Log Analytics** comme agent Log Analytics à associer.

    ![Capture d’écran de l’interface de stratégie du portail](./media/onboarding-at-scale3.png)

6. Vérifiez l’**Emplacement de l’identité managée**. Si cette stratégie est du type [DeployIfNotExists](https://docs.microsoft.com/azure/governance/policy/concepts/effects#deployifnotexists), elle nécessite une identité gérée pour son déploiement. Dans le portail, le compte sera créé comme indiqué dans la case à cocher.

7. Sélectionnez **Attribuer**.

Une fois l’Assistant terminé, l’attribution de stratégie sera déployée dans l’environnement. L’entrée en application de la stratégie peut prendre jusqu’à 30 minutes. Vous pouvez le tester en créant des machines virtuelles au bout de 30 minutes, puis en vérifiant si l’agent MMA (Microsoft Monitoring Agent) est activé sur la machine virtuelle par défaut.

## <a name="install-required-agents-on-on-premises-servers"></a>Installer les agents requis sur les serveurs locaux

> [!NOTE]
> Créez l’[espace de travail log Analytics et le compte Azure Automation](./prerequisites.md#create-a-workspace-and-automation-account) requis avant d’intégrer des serveurs aux services de gestion Azure.

Pour les serveurs locaux, vous devez télécharger et installer manuellement [l’agent Log Analytics et l’agent de dépendances Microsoft](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud) et les configurer pour qu’ils se connectent à l’espace de travail correct. Pour ce faire, spécifiez l’ID de l’espace de travail et les informations de clé que vous pouvez trouver en accédant à votre espace de travail Log Analytics dans le Portail Azure et en sélectionnant **Paramètres** > **Paramètres avancés**.

![Capture d’écran des paramètres avancés de l’espace de travail Log Analytics dans le Portail Azure](./media/onboarding-on-premises.png)

## <a name="enable-and-configure-solutions"></a>Activer et configurer des solutions

Pour activer les solutions, vous devez configurer l’espace de travail Log Analytics. Les machines virtuelles Azure et les serveurs locaux intégrés obtiendront les solutions à partir des espaces de travail Log Analytics auxquels ils sont connectés.

Les solutions suivantes sont traitées dans cette section :

- [Gestion des mises à jour](#update-management)
- [Change Tracking and Inventory](#change-tracking-and-inventory-solutions)
- [Journal d'activité Azure](#azure-activity-log)
- [Azure Log Analytics Agent Health](#azure-log-analytics-agent-health)
- [Analyse anti-programme malveillant](#antimalware-assessment)
- [Azure Monitor pour machines virtuelles](#azure-monitor-for-vms)
- [Centre de sécurité Azure](#azure-security-center)

### <a name="update-management"></a>Update Management

Les solutions Update Management, Change Tracking et d’inventaire nécessitent à la fois un espace de travail Log Analytics et un compte Automation. Pour vous assurer que ces ressources sont correctement configurées, nous vous recommandons d’intégrer le compte Automation. Pour plus d’informations, consultez [Intégrer les solutions Update Management, Change Tracking et Inventory](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

Nous vous recommandons d’activer la solution Update Management pour tous les serveurs. Update Management est gratuit pour les machines virtuelles Azure et les serveurs locaux. Si vous activez Update Management par le biais de votre compte Automation, une [configuration d’étendue](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account#scope-configuration) est créée dans l’espace de travail. Vous devez mettre à jour manuellement l’étendue pour inclure les machines couvertes par le service de mise à jour.

Pour couvrir tous les serveurs existants, ainsi que les futurs serveurs, vous devez supprimer la configuration détendue. Pour ce faire, affichez votre compte Automation dans le Portail Azure, et sélectionnez **Gestion des mises à jour** > **Gérer l’ordinateur** > **Activer sur tous les ordinateurs disponibles et à venir**. L’activation de ce paramètre permet à toutes les machines virtuelles Azure connectées à l’espace de travail d’utiliser Update Management.

![Capture d’écran d’Update Management dans le Portail Azure](./media/onboarding-configuration1.png)

### <a name="change-tracking-and-inventory-solutions"></a>Solutions Change Tracking et Inventory

Pour intégrer les solutions Change Tracking et Inventory, suivez les mêmes étapes que pour Update Management. Pour plus d’informations sur l’intégration de ces solutions à partir de votre compte Automation, consultez [Intégrer les solutions Update Management, Change Tracking et Inventory](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

La solution Change Tracking est gratuite pour les machines virtuelles Azure et coûte 6 euros par nœud et par mois pour les serveurs locaux. Ce coût couvre Change Tracking, Inventory et Desired State Configuration. Si vous souhaitez inscrire uniquement des serveurs locaux spécifiques, vous pouvez les choisir. Nous vous recommandons d’intégrer tous vos serveurs de production.

#### <a name="opt-in-via-the-azure-portal"></a>Accepter via le Portail Azure

1. Accédez au compte Automation pour lequel Change Tracking et Inventory sont activés.
2. Sélectionnez **Suivi des modifications**.
3. Sélectionnez **Gérer des machines** dans le volet supérieur droit.
4. Sélectionnez **Activer sur les ordinateurs sélectionnés**, puis sélectionnez les machines à activer en cliquant sur **Ajouter** en regard du nom de l’ordinateur.
5. Sélectionnez **Activer** pour activer la solution pour ces ordinateurs.

![Capture d’écran de Change Tracking dans le Portail Azure](./media/onboarding-configuration2.png)

#### <a name="opt-in-by-using-saved-searches"></a>S’abonner à l’aide de recherches enregistrées

Vous pouvez également configurer la configuration de l’étendue pour accepter des serveurs locaux. La configuration d’étendue utilise des recherches enregistrées.

Pour créer ou modifier la recherche enregistrée, procédez comme suit :

1. Accédez à l’espace de travail Log Analytics qui est lié à votre compte Automation que vous avez configuré dans les étapes précédentes.

2. Sous **Général**, sélectionnez **Recherches enregistrées**.

3. Dans la zone **Filtre**, entrez **Change Tracking** pour filtrer la liste des recherches enregistrées. Dans les résultats, sélectionnez **MicrosoftDefaultComputerGroup**.

4. Entrez le nom de l’ordinateur ou le VMUUID pour inclure les ordinateurs choisis pour Change Tracking.

    ```kusto
    Heartbeat
    | where AzureEnvironment=~"Azure" or Computer in~ ("list of the on-premises server names", "server1")
    | distinct Computer
    ```

    > [!NOTE]
    > Le nom du serveur doit correspondre exactement à la valeur incluse dans l’expression, et il ne doit pas contenir un suffixe de nom de domaine.

5. Sélectionnez **Enregistrer**.

6. Par défaut, la configuration d’étendue est liée à la recherche enregistrée**MicrosoftDefaultComputerGroup** et sera mise à jour automatiquement.

### <a name="azure-activity-log"></a>Journaux d’activité

Le [Journal d’activité Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) fait également partie d’Azure Monitor. Il fournit un insight sur les événements de niveau abonnement qui se produisent dans Azure.

Pour ajouter cette solution :

1. Dans le Portail Azure, ouvrez **Tous les services** et sélectionnez **Gestion + gouvernance** > **Solutions**.
2. Dans l’affichage **Solutions**, sélectionnez **Ajouter**.
3. Recherchez **Activity Log Analytics** et sélectionnez-le.
4. Sélectionnez **Create** (Créer).

Vous devez spécifier le **nom de l’espace de travail** que vous avez créé à la section précédente et où la solution est activée.

### <a name="azure-log-analytics-agent-health"></a>Azure Log Analytics Agent Health

La solution Azure Log Analytics Agent Health vous donne un aperçu de l’intégrité, des performances et de la disponibilité de vos serveurs Windows et Linux.

Pour ajouter cette solution :

1. Dans le Portail Azure, ouvrez **Tous les services** et sélectionnez **Gestion + gouvernance** > **Solutions**.
2. Dans l’affichage **Solutions**, sélectionnez **Ajouter**.
3. Recherchez **Azure Log Analytics Agent Health** et sélectionnez-le.
4. Sélectionnez **Create** (Créer).

Vous devez spécifier le **nom de l’espace de travail** que vous avez créé à la section précédente et où la solution est activée.

Une fois la création terminée, l’instance de ressource de l’espace de travail indique **AgentHealthAssessment** lorsque vous sélectionnez **Afficher** > **Solutions**.

### <a name="antimalware-assessment"></a>Antimalware Assessment

La solution Antimalware Assessment vous aide à identifier les serveurs infectés ou un risque accru d’infection par des logiciels malveillants.

Pour ajouter cette solution :

1. Dans le Portail Azure, ouvrez **Tous les services** et sélectionnez **Gestion + gouvernance** > **Solutions**.
2. Dans l’affichage **Solutions**, sélectionnez **Ajouter**.
3. Recherchez **Antimalware Assessment** et sélectionnez-le.
4. Sélectionnez **Create** (Créer).

Vous devez spécifier le **nom de l’espace de travail** que vous avez créé à la section précédente et où la solution est activée.

Une fois la création terminée, l’instance de ressource de l’espace de travail indique **AntiMalware** lorsque vous sélectionnez **Afficher** > **Solutions**.

### <a name="azure-monitor-for-vms"></a>Azure Monitor pour machines virtuelles

Vous pouvez activer [Azure Monitor pour machines virtuelles](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview) via la page d’affichage de l’instance de machine virtuelle, comme décrit dans l’article précédent [Activer les services de gestion sur une seule machine virtuelle à des fins d’évaluation](./onboard-single-vm.md). Vous ne devez pas activer les solutions directement à partir de la page **Solutions** comme vous l’avez fait pour les autres solutions décrites dans cet article. Pour les déploiements à grande échelle, il peut être plus aisé d’utiliser l’[automatisation](./onboarding-automation.md) pour activer les solutions appropriées dans l’espace de travail.

### <a name="azure-security-center"></a>Azure Security Center

Dans ce guide, nous vous recommandons d’intégrer tous les serveurs au niveau *Gratuit* d’Azure Security Center par défaut. Cette option vous offre un niveau de base d’évaluations de sécurité et de recommandations de sécurité réalisables pour votre environnement. La mise à niveau vers le niveau *Standard* du Security Center offre des avantages supplémentaires, qui sont abordés en détail dans la [page de tarification de Security Center](https://docs.microsoft.com/azure/security-center/security-center-pricing).

Pour activer le niveau gratuit d’Azure Security Center, procédez comme suit :

1. Accédez à la page du portail **Security Center**.
2. Sélectionnez **Stratégie de sécurité** sous **STRATÉGIE ET CONFORMITÉ**.
3. Trouvez la ressource de l’espace de travail Log Analytics que vous avez créée dans le volet le plus à droite.
4. Sélectionnez **Modifier les paramètres >** pour cet espace de travail.
5. Sélectionnez **Niveau tarifaire**.
6. Sélectionnez l’option **Gratuit**.
7. Sélectionnez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment utiliser l’automatisation pour intégrer des serveurs et créer des alertes.

> [!div class="nextstepaction"]
> [Automatiser l’intégration et la configuration des alertes](./onboarding-automation.md)
