---
title: Automatiser l’intégration
description: Utilisez les exemples de fichiers d’intégration pour faciliter l’automatisation du déploiement de vos services de gestion de serveur Azure dans un but d’amélioration de l’efficacité.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 4281638b7badf9b672ba3a38d2daa847b7604e7e
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80356387"
---
# <a name="automate-onboarding"></a>Automatiser l’intégration

Pour améliorer l’efficacité du déploiement des services de gestion de serveur Azure, envisagez d’automatiser le déploiement conformément aux sections précédentes de ce guide. Le script et les exemples de modèles fournis dans les sections suivantes sont des points de départ pour le développement de votre propre automatisation du processus d’intégration.

Ce guide contient un référentiel GitHub de prise en charge d’exemples de code, [CloudAdoptionFramework](https://aka.ms/caf/manage/automation-samples). Ce référentiel fournit des exemples de scripts et de modèles Azure Resource Manager pour vous aider à automatiser le déploiement des services de gestion de serveur Azure.

Les exemples de fichiers illustrent l’utilisation des cmdlets Azure PowerShell pour automatiser les tâches suivantes :

- Créer un [espace de travail Log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access). (Ou utiliser un espace de travail existant s’il est conforme aux exigences. Pour plus d’informations, consultez [Planification de l’espace de travail](./prerequisites.md#log-analytics-workspace-and-automation-account-planning).)

- Créer un compte Automation. (Ou utiliser un compte existant s’il est conforme aux exigences. Pour plus d’informations, consultez [Planification de l’espace de travail](./prerequisites.md#log-analytics-workspace-and-automation-account-planning).)

- Lier le compte Automation et l’espace de travail Log Analytics. Cette étape n’est pas requise si vous intégrez à l’aide du portail Azure.

- Activer Update Management ainsi que Change Tracking et Inventory pour l’espace de travail.

- Intégrer des machines virtuelles Azure à l’aide d’Azure Policy. Une stratégie installe l’agent Log Analytics et l’agent Microsoft Dependency sur les machines virtuelles Azure.

- Intégration de serveurs locaux en y installant l’agent Log Analytics.

Les fichiers décrits dans le tableau suivant sont utilisés dans cet exemple. Vous pouvez les personnaliser pour prendre en charge vos propres scénarios de déploiement.

| Nom de fichier | Description |
|-----------|-------------|
| New-AMSDeployment.ps1 | Principal script d’orchestration qui automatise l’intégration. Il crée des groupes de ressources ainsi que des emplacements, des espaces de travail et des comptes Automation s’ils n’existent pas déjà. Ce script PowerShell requiert un abonnement existant. |
| Workspace-AutomationAccount.json | Modèle de Resource Manager qui déploie les ressources de l’espace de travail et du compte Automation. |
| WorkspaceSolutions.json | Modèle Resource Manager, qui active les solutions souhaitées dans l’espace de travail Log Analytics. |
| ScopeConfig.json | Modèle Resource Manager qui utilise le modèle d’abonnement pour les serveurs locaux avec la solution Change Tracking. L’utilisation du modèle de consentement est facultative. |
| Enable-VMInsightsPerfCounters.ps1 | Script PowerShell, qui active les insights de machines virtuelles pour les serveurs et configure les compteurs de performances. |
| ChangeTracking-FileList.json | Modèle Resource Manager qui définit la liste des fichiers qui seront surveillés par Change Tracking. |

Utilisez la commande suivante pour exécuter New-AMSDeployment. ps1 :

```powershell
.\New-AMSDeployment.ps1 -SubscriptionName '{Subscription Name}' -WorkspaceName '{Workspace Name}' -WorkspaceLocation '{Azure Location}' -AutomationAccountName {Account Name} -AutomationAccountLocation {Account Location}
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment configurer des alertes de base pour informer votre équipe des événements et des problèmes de gestion importants.

> [!div class="nextstepaction"]
> [Configurer des alertes de base](./setup-alerts.md)
