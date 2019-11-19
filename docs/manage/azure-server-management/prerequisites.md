---
title: Planification des prérequis pour les services de gestion de serveur Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Outils et planification des prérequis pour les services de gestion de serveur Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: dafe5f36a59d60fa91816695cae1e1f3784df046
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565305"
---
# <a name="phase-1-prerequisite-planning-for-azure-server-management-services"></a>Phase 1 : Planification des prérequis pour les services de gestion de serveur Azure

Au cours de cette phase, vous allez vous familiariser avec la suite de services de gestion de serveur Azure et planifier le déploiement des ressources nécessaires à la mise en œuvre de ces solutions de gestion.

## <a name="understand-the-tools-and-services"></a>Comprendre les outils et les services

Consultez [Outils et services de gestion de serveur Azure](./tools-services.md) pour avoir un aperçu détaillé de ce qui suit :

- Les zones de gestion impliquées dans les opérations Azure en cours.
- Les services et outils Azure qui vous contribuent à votre support dans ces domaines.

Vous utilisez parallèlement plusieurs de ces services pour satisfaire à vos exigences en matière de gestion. Ces outils sont souvent évoqués tout au long de ce guide.

Les sections suivantes traitent de la planification et de la préparation nécessaires à l’utilisation de ces outils et services.

## <a name="log-analytics-workspace-and-automation-account-planning"></a>Planification de l’espace de travail Log Analytics et du compte Automation

La plupart des services que vous allez utiliser pour intégrer les services de gestion Azure nécessitent un espace de travail Log Analytics et un compte Azure Automation lié.

Un [espace de travail Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) est un environnement unique pour le stockage des données de journal d’activité Azure Monitor. Chaque espace de travail a son propre dépôt de données et sa propre configuration. Les solutions et sources de données sont configurées pour stocker leurs données dans des espaces de travail particuliers. Les solutions de supervision Azure requièrent que tous les serveurs soient connectés à un espace de travail, afin que leurs données de journal puissent être stockées et consultées.

Certains des services de gestion requièrent un compte [Azure Automation](https://docs.microsoft.com/azure/automation/automation-intro). Vous utilisez ce compte et les fonctionnalités d’Azure Automation pour intégrer des services Azure et d’autres systèmes publics afin de déployer, configurer et gérer vos processus de gestion de serveur.

Les services de gestion de serveur Azure suivants requièrent un espace de travail Log Analytics lié et un compte Automation :

- [Azure Update Management](https://docs.microsoft.com/azure/automation/automation-update-management)
- [Change Tracking and Inventory](https://docs.microsoft.com/azure/automation/change-tracking)
- [Runbook Worker hybride](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)
- [Desired State Configuration](https://docs.microsoft.com/azure/virtual-machines/extensions/dsc-overview)

La deuxième phase de ce guide se concentre sur le déploiement de services et de scripts d’automatisation. Elle vous montre comment créer un espace de travail Log Analytics et un compte Automation. Ce guide vous indique également comment utiliser Azure Policy pour que les nouvelles machines virtuelles soient connectées à l’espace de travail correct.

Les exemples de ce guide partent du principe qu’il s’agit d’un déploiement qui n’a pas encore de serveurs déployés dans le cloud. Pour en savoir plus sur les principes et les points à prendre en compte lors de la planification de vos espaces de travail, consultez [Gérer les données du journal et les espaces de travail dans Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).

## <a name="planning-considerations"></a>Considérations en matière de planification

Quand vous préparez les espaces de travail et les comptes dont vous avez besoin pour l’intégration des services de gestion, envisagez les problèmes suivants :

- **Zones géographiques Azure et conformité réglementaire :** Les régions Azure sont organisées en *zones géographiques*. Une [zone géographique Azure](https://azure.microsoft.com/global-infrastructure/geographies) garantit que les conditions de résidence, de souveraineté, de conformité et de résilience des données sont respectées dans les limites géographiques. Si vos charges de travail sont soumises à une souveraineté des données ou à d’autres exigences de conformité, les comptes d’espace de travail et Automation doivent être déployés dans des régions appartenant à la même région géographique Azure que les ressources de charge de travail qu’ils prennent en charge.
- **Nombre d’espaces de travail :** Comme principe directeur, créez le nombre minimal d’espaces de travail requis par zone géographique Azure. Nous vous recommandons d’utiliser au moins un espace de travail pour chaque zone géographique Azure où se trouvent vos ressources de calcul ou de stockage. Cet alignement initial permet d’éviter des problèmes réglementaires lorsque vous migrez des données vers différentes zones géographiques.
- **Conservation et limitation des données :** Vous devrez peut-être également prendre en compte les stratégies de conservation des données ou les exigences de limitation des données lors de la création d’espaces de travail ou de comptes Automation. Pour en savoir plus sur ces principes et sur les points supplémentaires à prendre en compte lors de la planification de vos espaces de travail, consultez [Gérer les données du journal et les espaces de travail dans Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).
- **Mappage des régions :** La liaison d’un espace de travail Log Analytics et d’un compte Azure Automation n’est prise en charge qu’entre certaines régions Azure. Par exemple, si l’espace de travail log Analytics est hébergé dans la région *EastUS*, le compte Automation lié doit être créé dans la région *EastUS2* pour être utilisé avec les services de gestion. Si vous avez un compte Automation qui a été créé dans une autre région, il ne peut pas créer un lien vers un espace de travail dans la région *EastUS*. Le choix de la région de déploiement peut avoir un impact significatif sur les exigences en matière de zones géographiques Azure. Consultez le [tableau des mappages des régions](https://docs.microsoft.com/azure/automation/how-to/region-mappings) pour déterminer la région qui doit héberger vos espaces de travail et vos comptes Automation.
- **Multirésidence de l’espace de travail :** L’agent Azure Log Analytics prend en charge la multirésidence dans certains scénarios, mais il fait face à plusieurs limitations et défis lors de l’exécution dans cette configuration. À moins que Microsoft ait recommandé d’utiliser la multirésidence pour votre scénario, nous vous déconseillons de le configurer sur l’agent Log Analytics.

## <a name="resource-placement-examples"></a>Exemples de placement des ressources

Il existe plusieurs modèles différents pour choisir l’abonnement dans lequel vous placez l’espace de travail Log Analytics et le compte Automation. En résumé, placez l’espace de travail et les comptes Automation dans un abonnement détenu par l’équipe responsable de l’implémentation des services Update Management, Change Tracking et Inventory.

Voici des exemples de déploiement d’espaces de travail et de comptes Automation.

### <a name="placement-by-geography"></a>Placement par zone géographique

Les environnements de petite et moyenne taille ont un seul abonnement et plusieurs centaines de ressources qui s’étendent sur plusieurs zones géographiques Azure. Pour ces environnements, créez un espace de travail Log Analytics et un compte Azure Automation dans chaque zone géographique.

Dans chaque groupe de ressources, vous pouvez créer un espace de travail et un compte de Azure Automation sous la forme d’une paire. Ensuite, déployez la paire sur les machines virtuelles dans la zone géographique correspondante.

Si vos stratégies de conformité des données n’imposent pas que les ressources se trouvent dans des régions spécifiques, vous pouvez également créer une paire pour gérer toutes les machines virtuelles. Nous vous recommandons également de placer les paires d’espace de travail et de compte Automation dans des groupes de ressources distincts pour fournir un contrôle d’accès en fonction du rôle (RBAC) plus granulaire.

L’exemple dans le diagramme suivant présente un abonnement avec deux groupes de ressources, chacun situé dans une zone géographique différente :

![Modèle d’espace de travail pour les environnements petits et moyens](./media/workspace-model-small.png)

### <a name="placement-in-a-management-subscription"></a>Placement dans un abonnement de gestion

Les environnements plus grands s’étendent sur plusieurs abonnements et disposent d’un service informatique central chargé de la surveillance et de la conformité. Pour ces environnements, créez des paires d’espaces de travail et des comptes Automation dans un abonnement de gestion informatique. Dans ce modèle, les ressources de machines virtuelles dans une zone géographique stockent leurs données dans l’espace de travail de la zone géographique correspondante dans l’abonnement de gestion informatique. Si des équipes en charge des applications doivent exécuter des tâches d’automatisation, mais n’ont pas besoin d’un espace de travail lié et de comptes Automation, elles peuvent créer des comptes Automation distincts dans leurs propres abonnements d’application.

![Modèle d’espace de travail pour les grands environnements](./media/workspace-model-large.png)

### <a name="decentralized-placement"></a>Placement décentralisé

Dans un autre modèle pour les grands environnements, l’équipe de développement des applications peut être responsable des correctifs et de la gestion. Dans ce cas, placez les paires d’espace de travail et de compte Automation dans les abonnements de l’équipe en charge des applications avec leurs autres ressources.

  ![Modèle de compte d’espace de travail pour les environnements décentralisés](./media/workspace-model-decentralized.png)

## <a name="create-a-workspace-and-automation-account"></a>Créer un espace de travail et un compte Automation

Une fois que vous choisi la meilleure façon de placer et d’organiser les paires d’espace de travail et de compte, vérifiez que vous avez créé ces ressources avant de commencer le processus d’intégration. Les exemples d’automatisation mentionnés plus loin dans ce guide créent une paire d’espace de travail et de compte Automation pour vous. Toutefois, si vous souhaitez effectuer l’intégration à l’aide du portail Azure et que vous ne n’avez pas de paire d’espace de travail et de compte Automation, vous devez en créer une.

Pour créer un espace de travail Log Analytics à l’aide du portail Azure, consultez [Créer un espace de travail](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace#create-a-workspace). Ensuite, créez un compte Automation correspondant pour chaque espace de travail en suivant les étapes décrites dans [Créer un compte Azure Automation](https://docs.microsoft.com/azure/automation/automation-quickstart-create-account).

> [!NOTE]
> Lorsque vous créez un compte Automation à l’aide du portail Azure, par défaut, le portail tente de créer des comptes d’identification pour Azure Resource Manager et les ressources du modèle de déploiement Classic. Si vous n’avez pas de machines virtuelles classiques dans votre environnement et que vous n’êtes pas coadministrateur de l’abonnement, le portail crée un compte d’identification pour Resource Manager, mais génère une erreur lors du déploiement du compte d’identification Classic. Si vous n’envisagez pas de prendre en charge les ressources classiques, vous pouvez ignorer cette erreur.
>
> Vous pouvez également créer des comptes d’identification à l’aide de [PowerShell](https://docs.microsoft.com/azure/automation/manage-runas-account#create-run-as-account-using-powershell).

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [intégrer vos serveurs](./onboarding-overview.md) aux services de gestion de serveur Azure.

> [!div class="nextstepaction"]
> [Intégration aux services de gestion de serveurs Azure](./onboarding-overview.md)
