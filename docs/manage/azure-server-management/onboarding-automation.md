---
title: Automatiser l’intégration et la configuration des alertes
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Automatiser l’intégration et la configuration des alertes
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 242c8a1a054507c3b1134b1126ea95e3ead74d84
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221376"
---
# <a name="automate-onboarding"></a>Automatiser l’intégration

Pour améliorer l’efficacité du déploiement des services de gestion de serveur Azure, envisagez d’automatiser le déploiement des services de gestion à l’aide des recommandations présentées dans les sections précédentes de ce guide. Le script et les exemples de modèles fournis dans les sections suivantes sont des points de départ pour le développement de votre propre automatisation du processus d’intégration.

## <a name="onboarding-by-using-automation"></a>Intégration à l’aide d’Automation

Ce guide contient un référentiel GitHub d’exemples de code, [CloudAdoptionFramework](https://aka.ms/caf/manage/automation-samples), qui fournit des exemples de scripts et de modèles Azure Resource Manager pour vous aider à automatiser le déploiement des services de gestion de serveur Azure.

Ces exemples de fichiers illustrent l’utilisation des cmdlets Azure PowerShell pour automatiser les tâches suivantes :

1. Créer un [espace de travail log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access) (ou utiliser un espace de travail existant s’il répond à la configuration requise&mdash;, consultez [Planification de l’espace de travail](./prerequisites.md#log-analytics-workspace-and-automation-account-planning)).

2. Créer un compte Automation (ou utiliser un compte existant s’il répond à la configuration requise&mdash;, consultez [Planification de l’espace de travail](./prerequisites.md#log-analytics-workspace-and-automation-account-planning)).

3. Lier le compte Automation et l’espace de travail Log Analytics (pas nécessaire en cas d’intégration via le portail).

4. Activer Update Management, Change Tracking et Inventory pour l’espace de travail.

5. Intégrer des machines virtuelles Azure avec Azure Policy (une stratégie installe l’agent Log Analytics et l’agent Dependency sur les machines virtuelles Azure).

6. Intégration de serveurs locaux en y installant l’agent Log Analytics.

Les fichiers décrits dans le tableau suivant sont utilisés dans cet exemple et vous pouvez les personnaliser pour vos propres scénarios de déploiement.

| Nom de fichier | Description |
|-----------|-------------|
| New-AMSDeployment.ps1 | Principal script d’orchestration qui automatise l’intégration. Ce script PowerShell nécessite un abonnement, mais il créera des groupes de ressources, des emplacements, des espaces de travail et des comptes Automation s’ils n’existent pas. |
| Workspace-AutomationAccount.json | Modèle de Resource Manager qui déploie les ressources de l’espace de travail et du compte Automation. |
| WorkspaceSolutions.json | Modèle Resource Manager qui active les solutions souhaitées dans l’espace de travail Log Analytics. |
| ScopeConfig.json | Modèle Resource Manager qui utilise le modèle d’abonnement pour les serveurs locaux avec la solution Change Tracking. L’utilisation du modèle de consentement est facultative. |
| Enable-VMInsightsPerfCounters.ps1 | Script PowerShell qui active VMInsight pour les serveurs et configure les compteurs de performances. |
| ChangeTracking-Filelist.json | Modèle Resource Manager qui définit la liste des fichiers qui seront surveillés par Change Tracking. |

Vous pouvez exécuter New-AMSDeployment. ps1 à l’aide de la commande suivante :

```powershell
.\New-AMSDeployment.ps1 -SubscriptionName '{Subscription Name}' -WorkspaceName '{Workspace Name}' -WorkspaceLocation '{Azure Location}' -AutomationAccountName {Account Name} -AutomationAccountLocation {Account Location}
```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment configurer des alertes de base pour informer votre équipe des événements et des problèmes de gestion importants.

> [!div class="nextstepaction"]
> [Configuration des alertes de base](./setup-alerts.md)
