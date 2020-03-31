---
title: Créer des planifications de mise à jour
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à gérer les planifications de mise à jour à l’aide du portail Azure ou des nouveaux modules d’applet de commande PowerShell.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 64f2ee1d148cc769325bdb60dabe2deba5d04351
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80356336"
---
# <a name="create-update-schedules"></a>Créer des planifications de mise à jour

Vous pouvez gérer les planifications de mise à jour à l’aide du portail Azure ou des nouveaux modules d’applet de commande PowerShell.

Pour créer une planification de mise à jour par le biais du portail Azure, consultez [Planifier un déploiement de mises à jour](https://docs.microsoft.com/azure/automation/automation-tutorial-update-management#schedule-an-update-deployment).

Le module Az.Automation prend désormais en charge la configuration de la gestion des mises à jour à l’aide d’Azure PowerShell. [La version 1.7.0](https://www.powershellgallery.com/packages/Az/1.7.0) du module ajoute la prise en charge de la cmdlet [New-AzAutomationUpdateManagementAzureQuery](https://docs.microsoft.com/powershell/module/az.automation/new-azautomationupdatemanagementazurequery?view=azps-1.7.0). Cette cmdlet vous permet d’utiliser des étiquettes, des emplacements et des recherches enregistrées pour configurer des planifications de mise à jour d’un groupe flexible d’ordinateurs.

## <a name="example-script"></a>Exemple de script

L’exemple de script de cette section illustre l’utilisation de l’étiquetage et de l’interrogation pour créer des groupes dynamiques d’ordinateurs auxquels vous pouvez appliquer des planifications de mise à jour. Il effectue les actions suivantes. Vous pouvez vous référer aux implémentations des actions spécifiques quand vous créez vos propres scripts.

- Crée une planification de mise à jour Azure Automation qui s’exécute tous les samedis à 8 heures.
- Crée une requête pour les machines qui satisfont à ces critères :
  - Déployée dans l’emplacement Azure `westus`, `eastus` ou `eastus2`
  - Avoir une étiquette `Owner` appliquée avec pour valeur `JaneSmith`
  - Avoir une étiquette `Production` appliquée avec pour valeur `true`
- Applique la planification de mise à jour aux ordinateurs interrogés et définit une fenêtre de mise à jour de deux heures.

Avant d’exécuter l’exemple de script, vous devez vous connecter à l’aide de l’applet de commande [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0). Lorsque vous démarrez le script, entrez les informations suivantes :

- L’ID d’abonnement cible
- Le groupe de ressources cible
- Le nom de votre espace de travail Log Analytics
- Le nom de votre compte Azure Automation

```powershell

    <#
        .SYNOPSIS
            This script orchestrates the deployment of the solutions and the agents.
        .Parameter SubscriptionName
        .Parameter WorkspaceName
        .Parameter AutomationAccountName
        .Parameter ResourceGroupName

    #>

    param (
        [Parameter(Mandatory=$true)]
        [string]$SubscriptionId,

        [Parameter(Mandatory=$true)]
        [string]$ResourceGroupName,

        [Parameter(Mandatory=$true)]
        [string]$WorkspaceName,

        [Parameter(Mandatory=$true)]
        [string]$AutomationAccountName,

        [Parameter(Mandatory=$false)]
        [string]$scheduleName = "SaturdayCriticalSecurity"
    )

    Import-Module Az.Automation

    $startTime = ([DateTime]::Now).AddMinutes(10)
    $schedule = New-AzAutomationSchedule -ResourceGroupName $ResourceGroupName `
        -AutomationAccountName $AutomationAccountName `
        -StartTime $startTime `
        -Name $scheduleName `
        -Description "Saturday patches" `
        -DaysOfWeek Saturday `
        -WeekInterval 1 `
        -ForUpdateConfiguration

    # Using AzAutomationUpdateManagementAzureQuery to create dynamic groups.

    $queryScope = @("/subscriptions/$SubscriptionID/resourceGroups/")

    $query1Location =@("westus", "eastus", "eastus2")
    $query1FilterOperator = "Any"
    $ownerTag = @{"Owner"= @("JaneSmith")}
    $ownerTag.add("Production", "true")

    $DGQuery = New-AzAutomationUpdateManagementAzureQuery -ResourceGroupName $ResourceGroupName `
        -AutomationAccountName $AutomationAccountName `
        -Scope $queryScope `
        -Tag $ownerTag

    $AzureQueries = @($DGQuery)

    $UpdateConfig = New-AzAutomationSoftwareUpdateConfiguration -ResourceGroupName $ResourceGroupName `
        -AutomationAccountName $AutomationAccountName `
        -Schedule $schedule `
        -Windows `
        -Duration (New-TimeSpan -Hours 2) `
        -AzureQuery $AzureQueries `
        -IncludedUpdateClassification Security,Critical
```

## <a name="next-steps"></a>Étapes suivantes

Consultez des exemples d’implémentation de [stratégies courantes dans Azure](./common-policies.md) qui peuvent vous aider à gérer vos serveurs.

> [!div class="nextstepaction"]
> [Stratégies courantes dans Azure](./common-policies.md)
