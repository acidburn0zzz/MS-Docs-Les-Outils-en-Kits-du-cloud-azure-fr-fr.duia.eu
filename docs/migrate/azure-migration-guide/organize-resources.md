---
title: Organiser vos ressources Azure efficacement
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Meilleures pratiques pour organiser efficacement vos ressources Azure afin d’en faciliter la gestion.
author: laraaleite
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: e47e7e5f8528580d4aa268fd90e7aa838e5f70ba
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73239958"
---
# <a name="organize-your-azure-resources"></a>Organiser vos ressources Azure

Utilisez les fonctionnalités et les bonnes pratiques suivantes afin de sécuriser les ressources qui sont essentielles pour votre système. balisez les ressources afin de les suivre selon la valeur qu’elles ont pour votre organisation.

<!-- markdownlint-disable MD024 MD025 -->

# <a name="azure-management-groups-and-hierarchytabazuremanagmentgroupsandhierarchy"></a>[Hiérarchie et groupes d’administration Azure](#tab/AzureManagmentGroupsAndHierarchy)

L’organisation des ressources dans Azure est structurée en quatre niveaux : les groupes d’administration, les abonnements, les groupes de ressources et les ressources. L’illustration suivante montre les relations entre ces niveaux.

![Diagramme illustrant les relations de la hiérarchie d’administration](./media/organize-resources/scope-levels.png)

- **Groupes d’administration :** ce sont des conteneurs qui vous permettent de gérer plus facilement l’accès, la stratégie et la conformité pour plusieurs abonnements. Tous les abonnements dans un groupe d’administration héritent automatiquement des conditions appliquées à ce groupe d’administration.
- **Abonnements :** un abonnement regroupe les comptes d’utilisateur et les ressources qui ont été créées par ces comptes d’utilisateur. Pour chaque abonnement, il existe des limites ou quotas sur la quantité de ressources que vous pouvez créer et utiliser. Les organisations peuvent utiliser des abonnements pour gérer les coûts et les ressources qui sont créées par les utilisateurs, les équipes ou les projets.
- **Groupes de ressources :** Un groupe de ressources est un conteneur logique dans lequel les ressources Azure comme les applications web, les bases de données et les comptes de stockage sont déployées et gérées.
- **Ressources :** les ressources sont des instances de services que vous créez, telles que des machines virtuelles, un stockage ou des bases de données SQL.

## <a name="scope-of-management-settings"></a>Portée des paramètres d’administration

Vous pouvez appliquer des paramètres d’administration, tels que des stratégies et des contrôles d’accès en fonction du rôle, à tous les niveaux d’administration. Le niveau que vous sélectionnez détermine à quel point le paramètre est appliqué. Les niveaux inférieurs héritent des paramètres des niveaux supérieurs. Par exemple, quand vous appliquez une stratégie à un abonnement, cette stratégie est également appliquée à la totalité des groupes de ressources et des ressources dans cet abonnement.

En règle générale, il est judicieux d’appliquer les paramètres critiques à des niveaux supérieurs et les exigences spécifiques au projet à des niveaux inférieurs. Par exemple, vous pouvez vous assurer que toutes les ressources de votre organisation sont déployées sur certaines régions. Pour ce faire, appliquez une stratégie à l’abonnement qui spécifie les emplacements autorisés. Lorsque les autres utilisateurs de votre organisation ajouteront de nouveaux groupes de ressources et des ressources, les emplacements autorisés seront automatiquement appliqués. Pour en savoir plus sur les stratégies, consultez la section de ce guide consacrée à la gouvernance, à la sécurité et à la conformité.

Pour planifier votre stratégie de conformité, faites-le si possible en collaboration avec les personnes qui, dans vos organisations, ont un rôle dans les domaines suivants : sécurité et conformité, administration informatique, architecture d’entreprise, réseau, finances et provisionnement.

::: zone target="docs"

## <a name="create-a-management-level"></a>Créer un niveau d’administration

Vous pouvez créer un groupe d’administration, des abonnements supplémentaires ou des groupes de ressources.

### <a name="create-management-group"></a>Créer un groupe d’administration

Créez un groupe d’administration pour gérer plus facilement l’accès, la stratégie et la conformité pour plusieurs abonnements.

1. Accédez à [Groupes d’administration](https://portal.azure.com/#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade).
2. Sélectionnez **Ajouter un groupe d’administration**.

### <a name="create-subscription"></a>Créer un abonnement

Utilisez des abonnements pour gérer les coûts et les ressources qui sont créées par les utilisateurs, les équipes ou les projets.

1. Accédez à [Abonnements](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
1. Sélectionnez **Ajouter**.

### <a name="create-resource-group"></a>Créer un groupe de ressources

Créez un groupe de ressources pour regrouper des ressources comme les applications web, les bases de données et les comptes de stockage qui partagent le même cycle de vie, les mêmes autorisations et les mêmes stratégies.

1. Accédez à [Groupes de ressources](https://portal.azure.com/#create/Microsoft.ResourceGroup).
1. Sélectionnez **Ajouter**.
1. Sélectionnez l’**Abonnement** sous lequel vous souhaitez créer votre groupe de ressources.
1. Entrez un nom pour le **groupe de ressources**.
1. Sélectionnez une **région** pour l’emplacement du groupe de ressources.

## <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Présentation de la gestion des accès aux ressources dans Azure](../../govern/resource-consistency/resource-access-management.md)
- [Organiser vos ressources avec des groupes d’administration Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview)
- [Limites du service d’abonnement](https://docs.microsoft.com/azure/azure-subscription-service-limits)

::: zone-end

::: zone target="chromeless"

## <a name="actions"></a>Actions

**Créer un groupe d’administration :**

Créez un groupe d’administration pour gérer plus facilement l’accès, la stratégie et la conformité pour plusieurs abonnements.

1. Accédez à **Groupes d’administration**.
1. Sélectionnez **Ajouter un groupe d’administration**.

::: form action="OpenBlade[#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade]" submitText="Go to Management groups" :::

**Créer un abonnement supplémentaire :**

Utilisez des abonnements pour gérer les coûts et les ressources qui sont créées par les utilisateurs, les équipes ou les projets.

1. Accédez à **Abonnements**.
1. Sélectionnez **Ajouter**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to Subscriptions" :::

**Créer un groupe de ressources :**

Créez un groupe de ressources pour regrouper des ressources comme les applications web, les bases de données et les comptes de stockage qui partagent le même cycle de vie, les mêmes autorisations et les mêmes stratégies.

1. Accédez aux **Groupes de ressources**.
1. Sélectionnez **Ajouter**.
1. Sélectionnez l’**Abonnement** sous lequel vous souhaitez créer votre groupe de ressources.
1. Entrez un nom pour le **groupe de ressources**.
1. Sélectionnez une **région** pour l’emplacement du groupe de ressources.

::: form action="Create[#create/Microsoft.ResourceGroup]" submitText="Create a resource group" :::

::: zone-end

# <a name="naming-standardstabnamingstandards"></a>[Conventions de nommage](#tab/NamingStandards)

Adoptez des conventions de nommage standard pour identifier les ressources dans le portail, sur les factures et dans les scripts. Vous avez déjà probablement de telles conventions pour votre infrastructure locale. Lorsque vous ajoutez Azure à votre environnement, vous devez étendre ces normes d’attribution de noms à vos ressources Azure. Les conventions de nommage rendent la gestion de l’environnement plus facile à tous les niveaux. Vous pouvez utiliser Azure Policy pour appliquer les standards de nommage à l’ensemble de votre environnement Azure.

::: zone target="docs"

Nous vous conseillons de passer en revue et d’adopter les [modèles et pratiques recommandés](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions).

>[!TIP]
>N’utilisez pas de caractères spéciaux (`-` ou `_`) comme premier ou dernier caractère d’un nom quel qu’il soit. Ces caractères entraînent l’échec de la plupart des règles de validation.

::: zone-end

| Entité | Étendue | Longueur | Casse | Caractères valides | Modèle suggéré | Exemples |
| --- | --- | --- | --- | --- | --- | --- |
|Resource group |Subscription |1-90 |Insensible à la casse |Alphanumériques, trait de soulignement, parenthèses, trait d’union, point (sauf à la fin) et caractères Unicode |`<service short name>-<environment>-rg` |`profx-prod-rg` |
|Groupe à haute disponibilité |Resource group |1-80 |Insensible à la casse |Alphanumériques, trait de soulignement et trait d’union |`<service-short-name>-<context>-as` |`profx-sql-as` |
|Tag |Entité associée |512 (nom), 256 (valeur) |Insensible à la casse |Alphanumérique |`"key" : "value"` |`"department" : "Central IT"` |

# <a name="resource-tagstabresourcetags"></a>[Balises de ressource](#tab/ResourceTags)

Les étiquettes sont utiles pour identifier rapidement vos ressources et groupes de ressources. Vous appliquez des balises à vos ressources Azure pour les organiser de façon logique par catégories. Chaque balise se compose d’un nom et d’une valeur. Par exemple, vous pouvez appliquer le nom « Environnement » et la valeur « Production » à toutes les ressources en production.

Une fois que vous avez appliqué une balise, vous pouvez utiliser son nom et sa valeur pour récupérer toutes les ressources dans votre abonnement. En utilisant des étiquettes, vous pouvez facilement récupérer les ressources associées de différents groupes de ressources, ce qui est utile si vous souhaitez organiser les ressources pour la facturation ou l’administration.

Vous pouvez également utiliser des étiquettes pour beaucoup d’autres choses. Voici quelques utilisations courantes :

- **Métadonnées et documentation :** Les administrateurs peuvent facilement voir les détails des ressources sur lesquelles ils travaillent en appliquant une étiquette comme « PropriétaireProjet ».
- **Automatisation :** il se peut que vous ayez des scripts s’exécutant régulièrement qui effectuent une action basée sur une valeur d’étiquette telle que « HeureArrêt » ou « DateDéprovisionnement ».
- **Facturation :** les étiquettes peuvent apparaître sur votre facture. Vous pouvez utiliser des étiquettes comme « CentreCoûts » ou « FacturerÀ » pour faciliter la segmentation de votre facture.

Chaque ressource ou groupe de ressources peut inclure un maximum de 15 paires nom/valeur de balise. Toutefois, cette limitation s’applique uniquement aux étiquettes qui sont directement appliquées au groupe de ressources ou à la ressource.

Pour plus d’informations sur le balisage, consultez [Conventions d’affectation de noms du centre des architectures Azure pour les ressources Azure](../../ready/azure-best-practices/naming-and-tagging.md#metadata-tags)

::: zone target="docs"

## <a name="apply-a-resource-tag"></a>Appliquer une étiquette de ressource

Pour appliquer une étiquette à un groupe de ressources :

1. Accédez à [Groupes de ressources](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups).
1. Sélectionnez un groupe de ressources.
1. Sélectionner **Étiquettes**.
1. Entrez un nouveau nom et une nouvelle valeur, ou sélectionnez un nom et une valeur existants dans la liste déroulante.

## <a name="learn-more"></a>En savoir plus

Pour en savoir plus, consultez [Organiser vos ressources Azure à l’aide d’étiquettes](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

::: zone-end

::: zone target="chromeless"

## <a name="action"></a>Action

**Appliquer une étiquette de ressource :**

Pour appliquer une étiquette à un groupe de ressources :

1. Accédez à **Groupes de ressources**.
1. Sélectionnez un groupe de ressources.
1. Sélectionner **Étiquettes**.
1. Entrez un nouveau nom et une nouvelle valeur, ou sélectionnez un nom et une valeur existants.

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups]" submitText="Go to resource groups" :::

::: zone-end
