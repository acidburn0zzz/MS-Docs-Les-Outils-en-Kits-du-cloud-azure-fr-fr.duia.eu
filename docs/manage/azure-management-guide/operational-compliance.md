---
title: Conformité opérationnelle au sein d’Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Garantir la stabilité d’une activité en renforçant la conformité opérationnelle
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 7073df6b697da49429d4086d9f8f3f113583e52d
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557089"
---
# <a name="operational-compliance-in-azure"></a>Conformité opérationnelle au sein d’Azure

La conformité opérationnelle est la deuxième discipline d’une base de référence de gestion cloud.

![Base de référence de gestion cloud](../../_images/manage/management-baseline.png)

L’amélioration de la conformité opérationnelle réduit la probabilité d’une panne liée à la dérive de la configuration ou aux vulnérabilités liées aux systèmes et qui ne sont pas correctement corrigés.

Dans le cas d’un environnement d’entreprise, le tableau suivant présente le minimum suggéré pour toute base de référence de gestion.

|Process  |Outil  |Objectif  |
|---------|---------|---------|
|Gestion des correctifs|Update Management|Gestion et planification des mises à jour|
|Application de stratégies|Azure Policy|Mise en œuvre de la stratégie pour garantir la conformité environnementale et invité|
|Env. Configuration|Azure Blueprint|Conformité automatisée pour les services de base|

::: zone target="docs"

## <a name="update-management"></a>Update Management

::: zone-end
::: zone target="chromeless"

## <a name="update-managementtabupdatemanagement"></a>[Gestion des mises à jour](#tab/UpdateManagement)

::: zone-end

Les ordinateurs gérés par Update Management utilisent les configurations suivantes pour effectuer l’évaluation et les déploiements de mises à jour :

- Microsoft Monitoring Agent (MMA) pour Windows ou Linux
- PowerShell DSC (Desired State Configuration, configuration d’état souhaité) pour Linux
- Runbook Worker hybride Automation
- Services Microsoft Update ou Windows Server Update (WSUS) pour ordinateurs Windows

Pour plus d'informations, consultez [Solution Gestion des mises à jour](https://docs.microsoft.com/azure/automation/automation-update-management)

> [!WARNING]
> Avant d’utiliser la gestion des mises à jour, vous devez intégrer des machines virtuelles ou un abonnement entier à Log Analytics et Azure Automation.
> Il existe deux approches d’intégration : une des deux doit être suivie avant de procéder à la gestion des mises à jour.
>
> - [Machine virtuelle unique](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
> - [Abonnement entier](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)

### <a name="manage-updates"></a>Gérer les mises à jour

Pour appliquer une stratégie à un groupe de ressources :

1. Accédez à [Azure Automation](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
2. Choisissez l’un des **comptes Automation** de la liste.
3. Recherchez la section **Gestion de la configuration** dans la navigation du portail.
4. L’inventaire, la gestion des modifications et la configuration d’état peuvent être utilisés pour contrôler l’état et la conformité opérationnelle des machines virtuelles gérées.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts]" submitText="Assign Policy" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

## <a name="azure-policy"></a>Azure Policy

::: zone-end
::: zone target="chromeless"

## <a name="azure-policytabazurepolicy"></a>[Azure Policy](#tab/AzurePolicy)

::: zone-end

Azure Policy est utilisé pendant les processus de gouvernance. Mais il est également très utilisé au sein de processus de gestion cloud. En plus de l’audit et de la correction des ressources Azure, Azure Policy peut auditer les paramètres internes d’une machine. La validation est effectuée par le client et l’extension de configuration d’invité. L’extension, via le client, valide des paramètres tels que :

- Configuration du système d’exploitation
- La configuration ou la présence de l’application
- Paramètres d'environnement

À ce stade, la configuration d’invité Azure Policy effectue uniquement un audit des paramètres à l’intérieur de la machine. Elle n’applique pas de configurations.

::: zone target="chromeless"

### <a name="action"></a>Action

Attribuez une stratégie intégrée à un groupe d’administration, à un abonnement ou à un groupe de ressources.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted]" submitText="Assign Policy" :::

::: zone-end

::: zone target="docs"

### <a name="apply-a-policy"></a>Appliquer une stratégie

Pour appliquer une stratégie à un groupe de ressources :

1. Accédez à [Azure Policy](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted).
1. Sélectionnez **Assigner une stratégie**.

### <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Azure Policy](https://docs.microsoft.com/azure/azure-policy)
- [Azure Policy - Configuration invité](https://docs.microsoft.com/azure/governance/policy/concepts/guest-configuration)
- [Framework d’adoption du cloud : Guide de décision pour l’application des stratégies](../../decision-guides/policy-enforcement/index.md)

## <a name="azure-blueprints"></a>Azure Blueprints

::: zone-end
::: zone target="chromeless"

## <a name="azure-blueprintstabazureblueprints"></a>[Azure Blueprints](#tab/AzureBlueprints)

::: zone-end

Azure Blueprints permet aux architectes cloud et aux groupes centraux responsables des technologies de l’information de définir un ensemble reproductible de ressources Azure qui implémentent et respectent les normes, modèles et exigences d’une organisation. Azure Blueprints permet aux équipes de développement de créer et mettre en place rapidement de nouveaux environnements et d’avoir confiance en leur conformité aux exigences de l’organisation à l’aide d’un ensemble de composants intégrés, comme la mise en réseau, visant à accélérer le développement et la livraison.

Les blueprints sont un moyen déclaratif d’orchestrer le déploiement de divers modèles de ressources et d’autres artefacts, notamment ceux-ci :

- Attributions de rôle.
- Attributions de stratégies.
- Modèles Azure Resource Manager.
- Groupes de ressources.

L’application d’un blueprint peut appliquer une conformité opérationnelle dans un environnement, si ce n’est pas déjà fait par l’équipe de gouvernance cloud.

### <a name="create-a-blueprint"></a>Créer un blueprint

Pour créer un blueprint :

::: zone target="chromeless"

1. Accédez à **Blueprints – Prise en main**.
1. Dans la section **Créer un blueprint**, sélectionnez **Créer**.
1. Filtrez la liste des blueprints pour sélectionner le blueprint approprié.
1. Entrez le **Nom du blueprint**, puis sélectionnez l’**Emplacement de définition** approprié.
1. Cliquez sur **Suivant : Artefacts >>** et examinez les artefacts inclus dans le blueprint.
1. Cliquez sur **Enregistrer le brouillon**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted]" submitText="Create a blueprint" :::

::: zone-end

::: zone target="docs"

1. Accédez à [Blueprints – Prise en main](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted).
1. Dans la section **Créer un blueprint**, sélectionnez **Créer**.
1. Filtrez la liste des blueprints pour sélectionner le blueprint approprié.
1. Entrez le **Nom du blueprint**, puis sélectionnez l’**Emplacement de définition** approprié.
1. Cliquez sur **Suivant : Artefacts >>** et examinez les artefacts inclus dans le blueprint.
1. Cliquez sur **Enregistrer le brouillon**.

::: zone-end

### <a name="publish-a-blueprint"></a>Publier un blueprint

Pour publier des artefacts de blueprint dans votre abonnement :

::: zone target="chromeless"

1. Accédez à **Blueprints - Définitions de blueprints**.
1. Sélectionnez le blueprint que vous avez créé dans les étapes précédentes.
1. Passez en revue la définition de blueprint et sélectionnez **Publier le blueprint**.
1. Spécifiez une **Version** (par exemple, « 1.0 ») et les **Notes de changement** éventuelles, puis sélectionnez **Publier**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Accédez à [Blueprints - Définitions de blueprints](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Sélectionnez le blueprint que vous avez créé dans les étapes précédentes.
1. Passez en revue la définition de blueprint et sélectionnez **Publier le blueprint**.
1. Spécifiez une **Version** (par exemple, « 1.0 ») et les **Notes de changement** éventuelles, puis sélectionnez **Publier**.

### <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints)
- [Framework d’adoption du cloud : Guide de décision pour la cohérence des ressources](../../decision-guides/resource-consistency/index.md)
- [Exemples de blueprints basés sur des normes](https://docs.microsoft.com/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end
