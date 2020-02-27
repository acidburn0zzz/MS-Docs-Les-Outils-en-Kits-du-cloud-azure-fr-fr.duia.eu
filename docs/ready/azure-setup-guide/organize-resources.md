---
title: Organiser vos ressources Azure efficacement
description: Meilleures pratiques pour organiser efficacement vos ressources Azure afin d’en faciliter la gestion.
author: laraaleite
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC, setup
ms.localizationpriority: high
ms.openlocfilehash: eb2564239548f77084fbc38d93003346a07e8e84
ms.sourcegitcommit: 1de39a4c3954512892f11e3d1330a04e95ce187d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77567756"
---
# <a name="organize-your-azure-resources"></a>Organiser vos ressources Azure

L’organisation de vos ressources informatiques est essentielle pour sécuriser, gérer et suivre les coûts relatifs à vos charges de travail. Pour organiser vos ressources, utilisez les hiérarchies d’administration au sein de la plateforme Azure, implémentez des conventions d’affectation de noms bien pensées et appliquez la catégorisation des ressources.

<!-- markdownlint-disable MD024 MD025 -->

# <a name="azure-management-groups-and-hierarchy"></a>[Hiérarchie et groupes d’administration Azure](#tab/AzureManagmentGroupsAndHierarchy)

Azure fournit quatre niveaux d’étendue de la gestion : groupes d’administration, abonnements, groupes de ressources et ressources. L’illustration suivante montre les relations entre ces niveaux.

   ![Diagramme illustrant les relations de la hiérarchie d’administration](./media/organize-resources/scope-levels.png)

- **Groupes d’administration :** Ces groupes sont des conteneurs qui vous permettent de gérer plus facilement l’accès, la stratégie et la conformité pour plusieurs abonnements. Tous les abonnements dans un groupe d’administration héritent automatiquement des conditions appliquées à ce groupe d’administration.
- **Abonnements :** Un abonnement regroupe les comptes d’utilisateur et les ressources qui ont été créées par ces derniers. Chaque abonnement a des limites ou quotas sur la quantité de ressources que vous pouvez créer et utiliser. Les organisations peuvent utiliser des abonnements pour gérer les coûts et les ressources qui sont créées par les utilisateurs, les équipes ou les projets.
- **Groupes de ressources :** Un groupe de ressources est un conteneur logique dans lequel les ressources Azure comme les applications web, les bases de données et les comptes de stockage sont déployées et gérées.
- **Ressources :** les ressources sont des instances de services que vous créez, telles que des machines virtuelles, un stockage ou des bases de données SQL.

## <a name="scope-of-management-settings"></a>Portée des paramètres d’administration

Vous pouvez appliquer des paramètres d’administration, tels que des stratégies et des contrôles d’accès en fonction du rôle, à tous les niveaux d’administration. Le niveau que vous sélectionnez détermine à quel point le paramètre est appliqué. Les niveaux inférieurs héritent des paramètres des niveaux supérieurs. Par exemple, quand vous appliquez une stratégie à un abonnement, cette stratégie est également appliquée à la totalité des groupes de ressources et des ressources dans cet abonnement.

En règle générale, il est judicieux d’appliquer les paramètres critiques à des niveaux supérieurs et les exigences spécifiques au projet à des niveaux inférieurs. Par exemple, vous voudrez vous assurer que toutes les ressources de votre organisation sont déployées dans certaines régions. Pour ce faire, appliquez une stratégie à l’abonnement qui spécifie les emplacements autorisés. Lorsque les autres utilisateurs de votre organisation ajouteront de nouveaux groupes de ressources et des ressources, les emplacements autorisés seront automatiquement appliqués. Pour en savoir plus sur les stratégies, consultez la section de ce guide consacrée à la gouvernance, à la sécurité et à la conformité.

Si vous disposez de quelques abonnements seulement, il est relativement simple de les gérer de manière indépendante. Si le nombre d’abonnements que vous utilisez augmente, envisagez de créer une hiérarchie de groupes d’administration pour simplifier la gestion de vos abonnements et de vos ressources. Pour plus d’informations sur la gestion de plusieurs abonnements, consultez [Mise à l’échelle avec plusieurs abonnements Azure](../azure-best-practices/scaling-subscriptions.md).

Planifiez votre stratégie de conformité en collaboration avec les personnes qui, dans vos organisations, ont un rôle dans les domaines suivants : sécurité et conformité, administration informatique, architecture d’entreprise, réseau, finances et approvisionnement.

::: zone target="docs"

## <a name="create-a-management-level"></a>Créer un niveau d’administration

Vous pouvez créer un groupe d’administration, des abonnements supplémentaires ou des groupes de ressources.

### <a name="create-a-management-group"></a>Créer un groupe d’administration

Créez un groupe d’administration pour gérer plus facilement l’accès, la stratégie et la conformité pour plusieurs abonnements.

1. Accédez à [Groupes d’administration](https://portal.azure.com/#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade).
2. Sélectionnez **Ajouter un groupe d’administration**.

### <a name="create-a-subscription"></a>Création d’un abonnement

Utilisez des abonnements pour gérer les coûts et les ressources qui sont créées par les utilisateurs, les équipes ou les projets.

1. Accédez à [Abonnements](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
1. Sélectionnez **Ajouter**.

### <a name="create-a-resource-group"></a>Créer un groupe de ressources

Créez un groupe de ressources pour regrouper des ressources comme les applications web, les bases de données et les comptes de stockage qui partagent le même cycle de vie, les mêmes autorisations et les mêmes stratégies.

1. Accédez à [Groupes de ressources](https://portal.azure.com/#create/Microsoft.ResourceGroup).
1. Sélectionnez **Ajouter**.
1. Sélectionnez l’**Abonnement** sous lequel vous souhaitez créer votre groupe de ressources.
1. Entrez un nom pour le **groupe de ressources**.
1. Sélectionnez une **région** pour l’emplacement du groupe de ressources.

## <a name="learn-more"></a>En savoir plus

Pour plus d'informations, consultez les rubriques suivantes :

- [Notions de base d’Azure](../considerations/fundamental-concepts.md)
- [Mise à l’échelle avec plusieurs abonnements Azure](../azure-best-practices/scaling-subscriptions.md)
- [Comprendre la gestion des accès aux ressources dans Azure](../../govern/resource-consistency/resource-access-management.md)
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

1. Accédez à **Groupes de ressources**.
1. Sélectionnez **Ajouter**.
1. Sélectionnez l’**Abonnement** sous lequel vous souhaitez créer votre groupe de ressources.
1. Entrez un nom pour le **groupe de ressources**.
1. Sélectionnez une **région** pour l’emplacement du groupe de ressources.

::: form action="Create[#create/Microsoft.ResourceGroup]" submitText="Create a resource group" :::

::: zone-end

# <a name="naming-standards"></a>[Conventions de nommage](#tab/NamingStandards)

Adoptez des conventions standard en matière d’affectation de noms pour identifier les ressources dans le Portail Azure, sur les factures et dans les scripts. Votre stratégie de nommage doit inclure des détails commerciaux et opérationnels dans les noms de ressources :

- Le côté commercial de cette stratégie doit s’assurer que les noms de ressources incluent les informations organisationnelles nécessaires pour identifier les équipes. Utilisez une ressource avec les propriétaires de l’entreprise qui sont responsables des coûts des ressources.

- Le côté opérationnel doit s’assurer que les noms incluent les informations dont les équipes informatiques ont besoin. Utilisez les détails qui identifient la charge de travail, l’application, l’environnement, le caractère critique et d’autres informations utiles pour la gestion des ressources.

Différents types de ressources peuvent se distinguer en matière de limites de longueur et de caractères autorisés, dont la plupart sont répertoriés dans l’[article Conventions d’affectation de noms](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions) des meilleures pratiques Azure. Pour obtenir plus d’informations et des recommandations visant spécifiquement à prendre en charge les efforts de l’entreprise dans le cadre de l’adoption du cloud, consultez l’[aide du Framework d’adoption du cloud au sujet de l’attribution de noms et de la catégorisation](../azure-best-practices/naming-and-tagging.md).

Le tableau suivant présente les modèles d’affectation de noms pour quelques exemples de types de ressources Azure.

::: zone target="docs"

>[!TIP]
>N’utilisez pas de caractères spéciaux (`-` ou `_`) comme premier ou dernier caractère d’un nom quel qu’il soit. Ces caractères entraînent l’échec de la plupart des règles de validation.

::: zone-end

| Entité | Étendue | Longueur | Casse | Caractères valides | Modèle suggéré | Exemple |
| --- | --- | --- | --- | --- | --- | --- |
|Resource group |Abonnement |1-90 |Insensible à la casse |Alphanumériques, trait de soulignement, parenthèses, trait d’union, point (sauf à la fin) et caractères Unicode |`<service short name>-<environment>-rg` |`profx-prod-rg` |
|Groupe à haute disponibilité |Resource group |1-80 |Insensible à la casse |Alphanumériques, trait de soulignement et trait d’union |`<service-short-name>-<context>-as` |`profx-sql-as` |
|Tag |Entité associée |512 (nom), 256 (valeur) |Insensible à la casse |Alphanumérique |`"key" : "value"` |`"department" : "Central IT"` |

# <a name="resource-tags"></a>[Balises de ressource](#tab/ResourceTags)

Les étiquettes sont utiles pour identifier rapidement vos ressources et groupes de ressources. Vous appliquez des balises à vos ressources Azure pour les organiser de façon logique par catégories. Chaque balise se compose d’un nom et d’une valeur. Par exemple, vous pouvez appliquer le nom « Environnement » et la valeur « Production » à toutes les ressources en production. Les balises doivent inclure le contexte de la charge de travail ou de l’application associée à la ressource, les exigences opérationnelles et les informations de propriété.

Une fois que vous avez appliqué une balise, vous pouvez utiliser son nom et sa valeur pour récupérer toutes les ressources dans votre abonnement. Lorsque vous organisez des ressources pour la facturation ou l’administration, les balises vous permettent de récupérer des ressources associées à partir de différents groupes de ressources.

Vous pouvez également utiliser des étiquettes pour beaucoup d’autres choses. Voici quelques utilisations courantes :

- **Métadonnées et documentation :** Les administrateurs peuvent facilement voir les détails des ressources sur lesquelles ils travaillent en appliquant une balise comme « PropriétaireProjet ».
- **Automatisation :** Il se peut que vous ayez des scripts s’exécutant régulièrement qui effectuent une action basée sur une valeur de balise telle que « HeureArrêt » ou « DateDéprovisionnement ».
- **Optimisation des coûts :** Vous pouvez allouer des ressources aux équipes et aux ressources qui sont responsables du coût. Dans Azure Cost Management, vous pouvez appliquer l’étiquette de centre de coût comme filtre pour obtenir les frais basés sur l’utilisation d’une équipe ou d’un département.

Chaque ressource ou groupe de ressources peut inclure un maximum de 50 paires nom/valeur de balise. Cette limitation s’applique uniquement aux balises directement appliquées au groupe de ressources ou à la ressource.

Pour obtenir d’autres recommandations et exemples de catégorisation, consultez l’[aide du Framework d’adoption du cloud au sujet de la catégorisation](../azure-best-practices/naming-and-tagging.md).

::: zone target="docs"

## <a name="apply-a-resource-tag"></a>Appliquer une étiquette de ressource

Pour appliquer une étiquette à un groupe de ressources :

1. Accédez à [Groupes de ressources](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups).
1. Sélectionnez un groupe de ressources.
1. Sélectionnez **Attribuer des étiquettes**.
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
