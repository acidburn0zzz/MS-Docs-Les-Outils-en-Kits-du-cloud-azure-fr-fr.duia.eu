---
title: Gérer l’accès à votre environnement Azure
description: Découvrez comment configurer un contrôle d’accès pour votre environnement Azure avec un contrôle d’accès en fonction du rôle (RBAC).
author: LijuKodicheraJayadevan
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC, setup
ms.localizationpriority: high
ms.openlocfilehash: efefa348324ab0c9dff86b5d19f7c3f11d9d437d
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83223267"
---
<!-- cSpell:ignore LijuKodicheraJayadevan -->

# <a name="manage-access-to-your-azure-environment-with-role-based-access-control"></a>Gérer l’accès à votre environnement Azure avec des contrôles d’accès en fonction du rôle

La gestion des personnes autorisées à accéder à vos ressources et abonnements Azure constitue une partie importante de votre stratégie de gouvernance Azure, et l’attribution de droits d’accès et de privilèges en fonction des groupes est une bonne pratique. Le traitement des groupes plutôt que des utilisateurs individuels simplifie la maintenance des stratégies d’accès, offre une gestion cohérente des accès entre les équipes et réduit les erreurs de configuration. Le contrôle d’accès en fonction du rôle (RBAC) Azure est la principale méthode de gestion de l’accès dans Azure.

RBAC permet de gérer l’accès aux ressources dans Azure de façon très précise. Il vous permet de gérer qui a accès aux ressources Azure, les opérations réalisables avec ces ressources et les étendues accessibles.

Lorsque vous planifiez votre stratégie de contrôle d’accès, vous pouvez accorder aux utilisateurs les privilèges minimaux requis pour effectuer leur travail. L’image suivante illustre un modèle suggéré pour l’attribution de RBAC.

![Diagramme illustrant les rôles RBAC](./media/manage-access/role-examples.png)

Pour planifier votre stratégie de contrôle d’accès, faites-le si possible en collaboration avec les personnes qui, dans vos organisations, ont un rôle dans les domaines suivants : sécurité et conformité, administration informatique et architecture d’entreprise.

Le Framework d’adoption du cloud offre des conseils supplémentaires sur l’[utilisation du contrôle d’accès en fonction du rôle](../considerations/roles.md) dans le cadre de vos efforts d’adoption du cloud.

::: zone target="chromeless"

## <a name="actions"></a>Actions

**Accorder l’accès à un groupe de ressources :**

Pour accorder à un utilisateur l’accès à un groupe de ressources :

1. Accédez à **Groupes de ressources**.
1. Sélectionnez un groupe de ressources.
1. Sélectionnez **Contrôle d’accès (IAM)** .
1. Sélectionnez **+ Ajouter** > **Ajouter une attribution de rôle**.
1. Sélectionnez un rôle, puis attribuez l’accès à un utilisateur, un groupe ou un principal de service.

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2FSubscriptions%2FResourceGroups]" submitText="Go to resource groups" ::: form-end

**Accorder l’accès à un abonnement :**

Pour accorder à un utilisateur l’accès à un abonnement :

1. Accédez à **Abonnements**.
1. Sélectionnez un abonnement.
1. Sélectionnez **Contrôle d’accès (IAM)** .
1. Sélectionnez **+ Ajouter** > **Ajouter une attribution de rôle**.
1. Sélectionnez un rôle, puis attribuez l’accès à un utilisateur, un groupe ou un principal de service.

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to subscriptions" ::: form-end

::: zone-end

::: zone target="docs"

## <a name="grant-resource-group-access"></a>Accorder l’accès à un groupe de ressources

Pour accorder à un utilisateur l’accès à un groupe de ressources :

1. Accédez à [Groupes de ressources](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2FSubscriptions%2FResourceGroups).
1. Sélectionnez un groupe de ressources.
1. Sélectionnez **Contrôle d’accès (IAM)** .
1. Sélectionnez **+ Ajouter** > **Ajouter une attribution de rôle**.
1. Sélectionnez un rôle, puis attribuez l’accès à un utilisateur, un groupe ou un principal de service.

## <a name="grant-subscription-access"></a>Accorder l’accès à un abonnement

Pour accorder à un utilisateur l’accès à un abonnement :

1. Accédez à [Abonnements](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
1. Sélectionnez un abonnement.
1. Sélectionnez **Contrôle d’accès (IAM)** .
1. Sélectionnez **+ Ajouter** > **Ajouter une attribution de rôle**.
1. Sélectionnez un rôle, puis attribuez l’accès à un utilisateur, un groupe ou un principal de service.

## <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Qu’est-ce que le contrôle d’accès en fonction du rôle (RBAC) ?](https://docs.microsoft.com/azure/role-based-access-control/overview)
- [Framework d’adoption du cloud : Utiliser le contrôle d’accès en fonction du rôle](../considerations/roles.md)

::: zone-end
