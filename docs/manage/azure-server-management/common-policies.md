---
title: Exemples de stratégies Azure Policy courantes
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Exemples de stratégies Azure Policy courantes
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 9eee6f81922c88304c0ca5bf7edd6572daf493d8
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031499"
---
# <a name="common-azure-policy-examples"></a>Exemples de stratégies Azure Policy courantes

[Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) peut vous aider à appliquer la gouvernance à vos ressources cloud. Ce service peut vous aider à créer des barrières de sécurité qui garantissent la conformité à l’échelle de l’entreprise aux exigences de la stratégie de gouvernance. Pour créer des stratégies, utilisez le portail Azure ou les cmdlets PowerShell. Cet article fournit des exemples de cmdlets PowerShell.

> [!NOTE]
> Avec Azure Policy, les stratégies de mise en application (**deployIfNotExists**) ne sont pas déployées automatiquement sur les machines virtuelles existantes. Une mise à jour est nécessaire pour maintenir la conformité de ces machines virtuelles. Pour plus d’informations, consultez [Corriger les ressources non conformes avec Azure Policy](https://docs.microsoft.com/azure/governance/policy/how-to/remediate-resources).

## <a name="common-policy-examples"></a>Exemples de stratégies courantes

Les sections suivantes décrivent certaines stratégies courantes.

### <a name="restrict-resource-regions"></a>Restreindre les régions de la ressource

La conformité aux réglementations et aux stratégies dépend souvent du contrôle de l’emplacement physique où les ressources sont déployées. Vous pouvez utiliser une stratégie intégrée pour permettre aux utilisateurs de créer des ressources uniquement dans les régions Azure autorisées. Vous pouvez trouver cette stratégie dans le portail en recherchant « emplacement » dans la page de définition de stratégie.

Vous pouvez exécuter cette cmdlet pour rechercher la stratégie :

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*location*") }
```

Le script suivant montre comment attribuer la stratégie. Pour utiliser le script, modifiez la valeur `$SubscriptionID` afin qu’elle pointe vers l’abonnement auquel vous souhaitez attribuer la stratégie. Avant d’exécuter le script, vous devez vous connecter à l’aide de la cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0).

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

#Replace the -Name GUID with the policy GUID you want to assign.
$AllowedLocationPolicy = Get-AzPolicyDefinition -Name "e56962a6-4747-49cd-b67b-bf8b01975c4c"

#Replace the locations with the ones you want to specify.
$policyParam = '{"listOfAllowedLocations":{"value":["eastus","westus"]}}'
New-AzPolicyAssignment -Name "Allowed Location" -DisplayName "Allowed locations for resource creation" -Scope $scope -PolicyDefinition $AllowedLocationPolicy -Location eastus -PolicyParameter $policyparam
```

Vous pouvez utiliser ce même script pour appliquer les autres stratégies décrites dans cet article. Remplacez simplement le GUID de la ligne qui définit `$AllowedLocationPolicy` par le GUID de la stratégie que vous souhaitez appliquer.

### <a name="block-certain-resource-types"></a>Bloquer certains types de ressources

Une autre stratégie intégrée couramment utilisée pour contrôler les coûts vous permet de bloquer certains types de ressources. Vous pouvez trouver cette stratégie dans le portail en recherchant « types de ressources autorisées » dans la page de définition de stratégie.

Vous pouvez exécuter cette cmdlet pour rechercher la stratégie :

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*allowed resource types") }
```

Une fois que vous avez identifié la stratégie que vous souhaitez utiliser, vous pouvez modifier l’exemple PowerShell dans la section [Restreindre les régions de ressources](#restrict-resource-regions) pour attribuer la stratégie.

### <a name="restrict-vm-size"></a>Restreindre la taille des machines virtuelles

Azure offre un large éventail de tailles de machines virtuelles qui prennent en charge différents types de charges de travail. Pour contrôler votre budget, vous pouvez créer une stratégie qui autorise uniquement un sous-ensemble de tailles de machines virtuelles dans vos abonnements.

### <a name="deploy-antimalware"></a>Déployer un logiciel anti-programme malveillant

Vous pouvez utiliser cette stratégie pour déployer une extension Microsoft IaaSAntimalware avec une configuration par défaut sur les machines virtuelles qui ne sont pas protégées par un logiciel anti-programme malveillant.

Le GUID de la stratégie est `2835b622-407b-4114-9198-6f7064cbe0dc`.

Le script suivant montre comment attribuer la stratégie. Pour utiliser le script, modifiez la valeur `$SubscriptionID` afin qu’elle pointe vers l’abonnement auquel vous souhaitez attribuer la stratégie. Avant d’exécuter le script, vous devez vous connecter à l’aide de la cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0).

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

$AntimalwarePolicy = Get-AzPolicyDefinition -Name "2835b622-407b-4114-9198-6f7064cbe0dc"

#Replace location “eastus” with the value you want to use.
New-AzPolicyAssignment -Name "Deploy Antimalware" -DisplayName "Deploy default Microsoft IaaSAntimalware extension for Windows Server" -Scope $scope -PolicyDefinition $AntimalwarePolicy -Location eastus –AssignIdentity

```

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur les autres outils et services de gestion de serveur disponibles.

> [!div class="nextstepaction"]
> [Outils et services de gestion de serveur Azure](./tools-services.md)