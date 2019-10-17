---
title: Gouvernance, sécurité et conformité dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Apprenez à configurer la gouvernance, la sécurité et la conformité pour votre environnement Azure.
author: tvuylsteke
ms.author: kfollis
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC, setup
ms.localizationpriority: high
ms.openlocfilehash: c43cf0d12ba26ee0298e79f2f6b90cc5773b2df6
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72379048"
---
# <a name="governance-security-and-compliance-in-azure"></a>Gouvernance, sécurité et conformité dans Azure

Lorsque vous établissez une stratégie d’entreprise et planifiez vos stratégies de gouvernance, vous pouvez utiliser des outils et des services tels que Azure Policy, Azure Blueprints et Azure Security Center pour appliquer et automatiser les décisions de gouvernance de votre organisation. Avant de commencer votre planification de la gouvernance, utilisez l’[outil Governance Benchmark](https://cafbaseline.com) pour identifier les lacunes potentielles dans l’approche de gouvernance cloud de votre organisation. Pour plus d’informations sur la façon de développer des processus de gouvernance, consultez l’[aide du Framework d’adoption du cloud pour Azure au sujet de la gouvernance](../../govern/index.md).

# <a name="azure-blueprintstabazureblueprints"></a>[Azure Blueprints](#tab/AzureBlueprints)

Azure Blueprints permet aux architectes cloud et aux groupes centraux responsables des technologies de l’information de définir un ensemble reproductible de ressources Azure qui implémentent et respectent les normes, modèles et exigences d’une organisation. Azure Blueprints permet aux équipes de développement de créer et mettre en place rapidement de nouveaux environnements et d’avoir confiance en leur conformité aux exigences de l’organisation à l’aide d’un ensemble de composants intégrés, comme la mise en réseau, visant à accélérer le développement et la livraison.

Les blueprints sont un moyen déclaratif d’orchestrer le déploiement de divers modèles de ressources et d’autres artefacts, notamment ceux-ci :

- Attributions de rôle.
- Attributions de stratégies.
- Modèles Azure Resource Manager.
- Groupes de ressources.

## <a name="create-a-blueprint"></a>Créer un blueprint

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

## <a name="publish-a-blueprint"></a>Publier un blueprint

Pour publier des artefacts de blueprint dans votre abonnement :

::: zone target="chromeless"

1. Accédez à **Blueprints - Définitions de blueprints**.
1. Sélectionnez le blueprint que vous avez créé dans les étapes précédentes.
1. Passez en revue la définition de blueprint et sélectionnez **Publier le blueprint**.
1. Spécifiez une **Version** (par exemple, _1.0_) et les **Notes de changement** éventuelles, puis sélectionnez **Publier**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Accédez à [Blueprints - Définitions de blueprints](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Sélectionnez la définition de blueprint que vous avez créée dans les étapes précédentes.
1. Passez en revue la définition de blueprint et sélectionnez **Publier le blueprint**.
1. Spécifiez une **Version** (par exemple, _1.0_) et les **Notes de changement** éventuelles, puis sélectionnez **Publier**.

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints)
- [Framework d’adoption du cloud : Guide de décision pour la cohérence des ressources](../../decision-guides/resource-consistency/index.md)
- [Exemples de blueprints basés sur des normes](/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end

# <a name="azure-policytabazurepolicy"></a>[Azure Policy](#tab/AzurePolicy)

Azure Policy est un service utilisé pour créer, attribuer et gérer des stratégies. Ces stratégies appliquent des règles à vos ressources afin qu’elles restent conformes aux standards et aux contrats de niveau de service de l’entreprise. Azure Policy analyse vos ressources pour identifier celles qui ne sont pas conformes aux stratégies que vous implémentez. Par exemple, vous pouvez disposer d’une stratégie qui n’autorise que les machines virtuelles d’une certaine taille à s’exécuter dans votre environnement. Une fois implémentée, cette stratégie évalue les machines virtuelles existantes dans votre environnement ainsi que toutes les nouvelles machines virtuelles qui y sont déployées. L’évaluation de la stratégie génère des événements de conformité que vous pouvez utiliser à des fins de supervision et de création de rapports.

Envisagez des stratégies communes pour :

- appliquer la catégorisation pour les ressources et les groupes de ressources ;
- restreindre des régions pour les ressources déployées ;
- restreindre les références SKU coûteuses pour des ressources spécifiques ;
- auditer l’utilisation des fonctionnalités facultatives importantes telles que la fonctionnalité Disques managés Azure.

::: zone target="chromeless"

## <a name="action"></a>Action

Attribuez une stratégie intégrée à un groupe d’administration, à un abonnement ou à un groupe de ressources.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted]" submitText="Assign Policy" :::

::: zone-end

::: zone target="docs"

## <a name="apply-a-policy"></a>Appliquer une stratégie

Pour appliquer une stratégie à un groupe de ressources :

1. Accédez à [Azure Policy](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted).
1. Sélectionnez **Assigner une stratégie**.

## <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Azure Policy](https://docs.microsoft.com/azure/azure-policy)
- [Framework d’adoption du cloud : Guide de décision pour l’application des stratégies](../../decision-guides/policy-enforcement/index.md)

::: zone-end

# <a name="azure-security-centertabazuresecuritycenter"></a>[Centre de sécurité Azure](#tab/AzureSecurityCenter)

Azure Security Center joue un rôle important dans votre stratégie de gouvernance. Il vous aide à assurer un haut niveau de sécurité, car il :

- Fournit une vue unifiée de la sécurité sur l’ensemble de vos charges de travail.
- Collecte, explore et analyse les données de sécurité à partir d’un large éventail de sources, dont les pare-feu et d’autres solutions partenaires.
- Fournit des recommandations de sécurité actionnables pour corriger les problèmes avant qu’ils ne soient exploités de façon malveillante.
- Peut être utilisé pour appliquer des stratégies de sécurité sur l’ensemble de vos charges de travail cloud hybrides pour garantir la conformité aux normes de sécurité.

La plupart des fonctionnalités de sécurité, telles que la stratégie de sécurité et les recommandations, sont disponibles gratuitement. Certaines des fonctionnalités plus avancées, telles que l’accès aux machines virtuelles juste-à-temps et la prise en charge des charges de travail hybrides, sont disponibles au niveau standard de Security Center. L’accès aux machines virtuelles juste-à-temps peut aider à réduire la surface d’attaque du réseau en contrôlant l’accès aux ports de gestion sur les machines virtuelles Azure.

> [!TIP]
> L’Azure Security Center est activé par défaut dans chaque abonnement. Nous vous recommandons d’activer la collecte de données depuis des machines virtuelles pour autoriser Azure Security Center à installer son agent et à commencer la collecte des données.

::: zone target="docs"

Pour explorer Azure Security Center, accédez au [portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

## <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Centre de sécurité Azure](https://docs.microsoft.com/azure/security-center)
- [Accès juste-à-temps aux machines virtuelles](https://docs.microsoft.com/azure/security-center/security-center-just-in-time#how-does-just-in-time-access-work)
- [Niveaux tarifaires Standard et Gratuit](https://azure.microsoft.com/pricing/details/security-center)
- [Framework d’adoption du cloud : Discipline de la gouvernance relative à la base de référence de la sécurité](../../govern/security-baseline/index.md)

::: zone-end

::: zone target="chromeless"

## <a name="action"></a>Action

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end
