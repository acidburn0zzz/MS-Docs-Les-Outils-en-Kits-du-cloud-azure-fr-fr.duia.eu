---
title: Stratégie Guest Configuration
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Stratégie Guest Configuration
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: d51cef67c96057b1929ed8cc86396f20338e932b
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031563"
---
# <a name="guest-configuration-policy"></a>Stratégie Guest Configuration

L’extension Azure Policy [Guest Configuration](/azure/governance/policy/concepts/guest-configuration) vous permet d’auditer les paramètres de configuration d’une machine virtuelle. Guest Configuration est actuellement pris en charge uniquement sur les machines virtuelles Azure.

Vous pouvez retrouver la liste des stratégies Guest Configuration en recherchant la catégorie « Guest Configuration » dans la page du portail Azure Policy. Vous pouvez également en retrouver la liste en exécutant cette cmdlet dans une fenêtre PowerShell :

```powershell
Get-AzPolicySetDefinition | where-object {$_.Properties.metadata.category -eq "Guest Configuration"}
```

> [!NOTE]
> La fonctionnalité Guest Configuration est régulièrement mise à jour pour pouvoir prendre en charge d’autres jeux de stratégies. Vérifiez régulièrement les nouvelles stratégies prises en charge et déterminez si elles répondent à vos besoins.

<!-- TODO: Update these links when available. 

By default, we recommend enabling the following policies:

- [Preview]: Audit to verify password security settings are set correctly inside Linux and Windows machines.
- Audit to verify that certificates are not nearing expiration on Windows VMs.

-->

## <a name="deployment"></a>Déploiement

Utilisez ensuite l’exemple de script PowerShell suivant pour déployer ces stratégies :

- Vérifiez que les paramètres de sécurité du mot de passe sont correctement définis sur les ordinateurs Windows et Linux.
- Vérifiez que les certificats ne sont pas proches de l’expiration sur les machines virtuelles Windows.

 Avant d’exécuter ce script, vous devez vous connecter à l’aide de la cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0). Lorsque vous exécutez le script, vous devez fournir le nom de l’abonnement auquel vous souhaitez appliquer les stratégies.

```powershell
#Assign Guest Configuration policy.
param (
    [Parameter(Mandatory=$true)]
    [string]$SubscriptionName
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
