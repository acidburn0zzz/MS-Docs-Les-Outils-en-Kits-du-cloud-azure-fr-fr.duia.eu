---
title: Stratégie Guest Configuration
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à tirer parti de l’extension Azure Policy Guest Configuration pour auditer les paramètres de configuration d’une machine virtuelle Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 938934e1a45d8f8abebede6cca8dcd9987cfb7e0
ms.sourcegitcommit: bd9872320b71245d4e9a359823be685e0f4047c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83861461"
---
# <a name="guest-configuration-policy"></a>Stratégie Guest Configuration

Vous pouvez utiliser l’extension Azure Policy [Guest Configuration](https://docs.microsoft.com/azure/governance/policy/concepts/guest-configuration) pour auditer les paramètres de configuration d’une machine virtuelle. Guest Configuration est actuellement pris en charge uniquement sur les machines virtuelles Azure.

Pour trouver la liste des stratégies Guest Configuration, recherchez « Guest Configuration » dans la page du portail Azure Policy. Ou bien exécutez cette cmdlet dans une fenêtre PowerShell pour trouver la liste :

```powershell
Get-AzPolicySetDefinition | where-object {$_.Properties.metadata.category -eq "Guest Configuration"}
```

> [!NOTE]
> La fonctionnalité Guest Configuration est régulièrement mise à jour pour pouvoir prendre en charge d’autres jeux de stratégies. Vérifiez régulièrement les nouvelles stratégies prises en charge et évaluez leur utilité.

<!-- TODOBACKLOG: Update these links when available. 

By default, we recommend that you enable the following policies:

- **Preview:** Audit to verify that password-security settings are correct on Linux and Windows machines.
- Audit to verify that certificates are not nearing expiration on Windows VMs.

-->

## <a name="deployment"></a>Déploiement

Utilisez l’exemple de script PowerShell suivant pour déployer ces stratégies sur :

- Vérifiez que les paramètres de sécurité du mot de passe sont correctement définis sur les ordinateurs Windows et Linux.
- Vérifiez que les certificats ne sont pas proches de l’expiration sur les machines virtuelles Windows.

 Avant d’exécuter ce script, utilisez la cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) pour vous connecter. Lorsque vous exécutez le script, vous devez fournir le nom de l’abonnement auquel vous souhaitez appliquer les stratégies.

```powershell

    # Assign Guest Configuration policy.

    param (
        [Parameter(Mandatory=$true)]
        [string] $SubscriptionName
    )

    $Subscription = Get-AzSubscription -SubscriptionName $SubscriptionName
    $scope = "/subscriptions/" + $Subscription.Id

    $PasswordPolicy = Get-AzPolicySetDefinition -Name "3fa7cbf5-c0a4-4a59-85a5-cca4d996d5a6"
    $CertExpirePolicy = Get-AzPolicySetDefinition -Name "b6f5e05c-0aaa-4337-8dd4-357c399d12ae"

    New-AzPolicyAssignment -Name "PasswordPolicy" -DisplayName "[Preview]: Audit that password security settings are set correctly inside Linux and Windows machines" -Scope $scope -PolicySetDefinition $PasswordPolicy -AssignIdentity -Location eastus

    New-AzPolicyAssignment -Name "CertExpirePolicy" -DisplayName "[Preview]: Audit that certificates are not expiring on Windows VMs" -Scope $scope -PolicySetDefinition $CertExpirePolicy -AssignIdentity -Location eastus

```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [activer le suivi des modifications et les alertes](./enable-tracking-alerting.md) pour les modifications critiques des fichiers, des services, des logiciels et du Registre.

> [!div class="nextstepaction"]
> [Activer le suivi et les alertes pour les changements critiques](./enable-tracking-alerting.md)
