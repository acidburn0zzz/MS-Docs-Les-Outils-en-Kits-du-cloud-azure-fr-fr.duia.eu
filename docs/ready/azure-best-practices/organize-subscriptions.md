---
title: Organiser et gérer plusieurs abonnements Azure
description: Utilisez Cloud Adoption Framework pour Azure afin découvrir comment créer une hiérarchie de groupes d’administration en vue de simplifier la gestion de vos abonnements et de vos ressources.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 7f232b6af4dc501b775d99a567cdca11dc0500a2
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83223420"
---
# <a name="organize-and-manage-multiple-azure-subscriptions"></a>Organiser et gérer plusieurs abonnements Azure

Si vous disposez de quelques abonnements seulement, les gérer de manière indépendante est relativement simple. Cependant, si vous avez un grand nombre d’abonnements, créez une hiérarchie des groupes d’administration afin de mieux gérer vos abonnements et vos ressources.

## <a name="azure-management-groups"></a>Groupes d’administration Azure

Les groupes d’administration Azure permettent une gestion efficace des accès, des stratégies et de la conformité des abonnements d’une organisation. Chaque groupe d’administration est un conteneur pour un ou plusieurs abonnements.

Les groupes d’administration sont organisés dans une hiérarchie unique. Vous définissez cette hiérarchie dans votre locataire Azure Active Directory (Azure AD) pour l’aligner sur la structure et les besoins de votre organisation. Le niveau supérieur est appelé le _groupe d’administration racine_. Vous pouvez définir jusqu’à six niveaux de groupes d’administration dans votre hiérarchie. Chaque abonnement est contenu dans un seul groupe d’administration.

Azure propose quatre niveaux d’étendue de la gestion :

- Groupes d’administration
- Abonnements
- Groupes de ressources
- Ressources

Tout accès ou stratégie appliqué à un niveau de la hiérarchie est hérité par les niveaux inférieurs. Le propriétaire d’une ressource ou d’un abonnement ne peut pas modifier une stratégie héritée. Cette limitation permet d’améliorer la gouvernance.

> [!NOTE]
> L’héritage des étiquettes n’est pas encore pris en charge, mais il le sera bientôt.

Ce modèle d’héritage vous permet d’organiser les abonnements dans votre hiérarchie de façon à ce que chaque abonnement suive les stratégies et les contrôles de sécurité appropriés.

![Les quatre niveaux d’étendue pour l’organisation de vos ressources Azure](../../ready/azure-setup-guide/media/organize-resources/scope-levels.png)

Toute attribution d’accès et de stratégie au groupe d’administration racine s’appliquent à toutes les ressources du répertoire. Examinez attentivement les éléments que vous définissez au niveau de cette étendue. Incluez uniquement les affectations dont vous avez besoin.

## <a name="create-your-management-group-hierarchy"></a>Créer votre hiérarchie de groupes d’administration

Quand vous définissez votre hiérarchie de groupes d’administration, créez d’abord le groupe d’administration racine. Déplacez ensuite tous les abonnements existants dans l’annuaire vers le groupe d’administration racine. Les nouveaux abonnements sont toujours créés dans le groupe d’administration racine. Vous pouvez ensuite les déplacer vers un autre groupe d’administration.

Quand vous déplacez un abonnement vers un groupe d’administration existant, il hérite des stratégies et des attributions de rôle de la hiérarchie de groupes d’administration au-dessus de lui. Une fois que vous avez établi plusieurs abonnements pour vos charges de travail Azure, vous pouvez créer des abonnements supplémentaires pour contenir les services Azure partagés par d’autres abonnements.

Si vous envisagez un développement de votre environnement Azure, vous devez créer maintenant des groupes d’administration pour la production et la non-production, et appliquer des stratégies et des contrôles d’accès appropriés au niveau de ces groupes d’administration. Les nouveaux abonnements hériteront des contrôles appropriés à mesure qu’ils seront ajoutés à chaque groupe d’administration.

![Exemple d’une hiérarchie de groupes d’administration](../../_images/ready/management-group-hierarchy-v2.png)

## <a name="example-use-cases"></a>Exemples de cas d’utilisation

Voici quelques exemples de base de l’utilisation de groupes d’administration pour séparer différentes charges de travail :

- **Charges de travail de production et non-production :** Utilisez les groupes d’administration pour gérer plus facilement les différents rôles et les différentes stratégies entre les abonnements de production et les abonnements de non-production. Par exemple, les abonnements de non-production peuvent accorder aux développeurs un accès de contributeur tandis que les développeurs en production disposent d’un accès de lecteur.
- **Services internes et services externes :** Les entreprises ont souvent des besoins, des stratégies et des rôles différents pour les services internes et les services externes destinés aux clients.

## <a name="related-resources"></a>Ressources associées

Passez en revue les ressources suivantes pour en savoir plus sur l’organisation et la gestion de vos ressources Azure.

- [Organiser vos ressources avec des groupes d’administration Azure](https://docs.microsoft.com/azure/governance/management-groups)
- [Élever l’accès pour gérer tous les abonnements et groupes d’administration Azure](https://docs.microsoft.com/azure/role-based-access-control/elevate-access-global-admin)
- [Déplacer des ressources Azure vers un autre groupe de ressources ou un autre abonnement.](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription)

## <a name="next-steps"></a>Étapes suivantes

Passez en revue les [conventions de nommage et de catégorisation recommandées](./naming-and-tagging.md) à suivre lors du déploiement de vos ressources Azure.

> [!div class="nextstepaction"]
> [Conventions de nommage et de catégorisation recommandées](./naming-and-tagging.md)
