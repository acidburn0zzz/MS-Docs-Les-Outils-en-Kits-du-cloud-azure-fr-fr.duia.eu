---
title: Conformité opérationnelle au sein d’Azure
description: Garantir la stabilité d’une activité en renforçant la conformité opérationnelle
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 9df0d1e36cbd926725ec5622087b57a2b8eae9ce
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808190"
---
# <a name="operational-compliance-in-azure"></a>Conformité opérationnelle au sein d’Azure

La _conformité opérationnelle_ est la deuxième discipline d’une base de référence de gestion cloud.

![Base de référence de gestion cloud](../../_images/manage/management-baseline.png)

L’amélioration de la conformité opérationnelle réduit la probabilité d’une panne liée à la dérive de la configuration ou aux vulnérabilités liées aux systèmes et qui ne sont pas correctement corrigées.

Dans le cas d’un environnement d’entreprise, ce tableau présente le minimum suggéré pour toute base de référence de gestion.

|Process  |Outil  |Objectif  |
|---------|---------|---------|
|Gestion des correctifs|Update Management|Gestion et planification des mises à jour|
|Application de stratégies|Azure Policy|Mise en œuvre de la stratégie pour garantir la conformité environnementale et invité|
|Configuration de l’environnement|Azure Blueprints|Conformité automatisée pour les services de base|
|Configuration de ressource|DSC (Desired State Configuration)|Configuration automatisée sur le système d’exploitation invité et quelques aspects de l’environnement|

::: zone target="docs"

## <a name="update-management"></a>Update Management

::: zone-end
::: zone target="chromeless"

## <a name="update-managementtabupdatemanagement"></a>[Gestion des mises à jour](#tab/UpdateManagement)

::: zone-end

Les ordinateurs gérés par Update Management utilisent les configurations suivantes pour effectuer l’évaluation et les déploiements de mises à jour :

- Microsoft Monitoring Agent (MMA) pour Windows ou Linux
- PowerShell DSC (Desired State Configuration, configuration d’état souhaité) pour Linux
- Runbook Worker hybride Azure Automation
- Services Microsoft Update ou Windows Server Update (WSUS) pour ordinateurs Windows

Pour plus d'informations, consultez [Solution Gestion des mises à jour](https://docs.microsoft.com/azure/automation/automation-update-management).

> [!WARNING]
> Avant d’utiliser la gestion des mises à jour, vous devez intégrer des machines virtuelles ou un abonnement entier à Log Analytics et Azure Automation.
>
> Il existe deux approches pour l’intégration :
>
> - [Machine virtuelle unique](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
> - [Abonnement entier](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)
>
> Vous devez suivre une de ces approches avant de procéder à la gestion des mises à jour.

### <a name="manage-updates"></a>Gérer les mises à jour

Pour appliquer une stratégie à un groupe de ressources :

1. Accédez à [Azure Automation](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
1. Sélectionnez **Comptes Automation**, puis choisissez un des comptes répertoriés.
1. Sélectionnez **Gestion de la configuration**.
1. L’**inventaire**, la **gestion des modifications** et la **configuration d’état** peuvent être utilisés pour contrôler l’état et la conformité opérationnelle des machines virtuelles gérées.

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

Azure Policy est utilisé pendant les processus de gouvernance. Il est également très utilisé au sein de processus de gestion cloud. En plus de l’audit et de la correction des ressources Azure, Azure Policy peut auditer les paramètres internes d’une machine. La validation est effectuée par le client et l’extension de configuration d’invité. L’extension, via le client, valide des paramètres tels que :

- Configuration du système d’exploitation.
- Configuration ou présence de l’application.
- Paramètres d'environnement.

Actuellement, la configuration d’invité Azure Policy effectue uniquement un audit des paramètres à l’intérieur de la machine. Elle n’applique pas de configurations.

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

Avec Azure Blueprints, les architectes cloud et les groupes d’informatique centrale peuvent définir un ensemble reproductible de ressources Azure. Ces ressources implémentent et respectent les normes, modèles et exigences d’une organisation.

Avec Azure Blueprints, les équipes de développement peuvent rapidement créer et mettre en place de nouveaux environnements. Elles ont également la garantie que les environnements créés sont conformes aux exigences de l’organisation. Pour cela, elles utilisent un ensemble de composants intégrés, comme la mise en réseau, visant à accélérer le développement et la livraison.

Les blueprints sont un moyen déclaratif d’orchestrer le déploiement de différents modèles de ressources et d’autres artefacts, notamment ceux-ci :

- Attributions de rôle.
- Attributions de stratégies.
- Modèles Azure Resource Manager.
- Groupes de ressources.

L’application d’un blueprint peut appliquer une conformité opérationnelle dans un environnement, si ce n’est pas déjà fait par l’équipe de gouvernance cloud.

### <a name="create-a-blueprint"></a>Créer un blueprint

Pour créer un blueprint :

::: zone target="chromeless"

1. Accédez à **Blueprints – Prise en main**.
1. Dans le volet **Créer un blueprint**, sélectionnez **Créer**.
1. Filtrez la liste des blueprints pour sélectionner le blueprint approprié.
1. Dans la zone **Nom du blueprint**, entrez le nom du blueprint.
1. Sélectionnez **Emplacement de définition**, puis choisissez l’emplacement correspondant.
1. Sélectionnez **Suivant : Artefacts >>** , puis examinez les artefacts inclus dans le blueprint.
1. Sélectionnez **Enregistrer le brouillon**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted]" submitText="Create a blueprint" :::

::: zone-end

::: zone target="docs"

1. Accédez à [Blueprints – Prise en main](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted).
1. Dans le volet **Créer un blueprint**, sélectionnez **Créer**.
1. Filtrez la liste des blueprints pour sélectionner le blueprint approprié.
1. Dans la zone **Nom du blueprint**, entrez le nom du blueprint.
1. Sélectionnez **Emplacement de définition**, puis choisissez l’emplacement correspondant.
1. Sélectionnez **Suivant : Artefacts >>** , puis examinez les artefacts inclus dans le blueprint.
1. Sélectionnez **Enregistrer le brouillon**.

::: zone-end

### <a name="publish-a-blueprint"></a>Publier un blueprint

Pour publier des artefacts de blueprint dans votre abonnement :

::: zone target="chromeless"

1. Accédez à **Blueprints - Définitions de blueprints**.
1. Sélectionnez le blueprint que vous avez créé dans les étapes précédentes.
1. Passez en revue la définition de blueprint et sélectionnez **Publier le blueprint**.
1. Dans la zone **Version**, entrez une version, par exemple « 1.0 ».
1. Dans la zone **Notes de changement**, entrez vos notes.
1. Sélectionnez **Publier**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Accédez à [Blueprints - Définitions de blueprints](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Sélectionnez le blueprint que vous avez créé dans les étapes précédentes.
1. Passez en revue la définition de blueprint et sélectionnez **Publier le blueprint**.
1. Dans la zone **Version**, entrez une version, par exemple « 1.0 ».
1. Dans la zone **Notes de changement**, entrez vos notes.
1. Sélectionnez **Publier**.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints)
- [Framework d’adoption du cloud : Guide de décision pour la cohérence des ressources](../../decision-guides/resource-consistency/index.md)
- [Exemples de blueprints basés sur des normes](https://docs.microsoft.com/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end
