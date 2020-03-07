---
title: Mise à l’échelle avec plusieurs abonnements Azure
description: Découvrez comment mettre à l’échelle avec plusieurs abonnements Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 6a893ce6f8620b31fcf23d8c3e8581e95035bdcf
ms.sourcegitcommit: 26caeb6b7f4e14df30bf16727d0b1b3d63b9c0c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78337749"
---
# <a name="scale-with-multiple-azure-subscriptions"></a>Mettre à l’échelle avec plusieurs abonnements Azure

Les organisations ont souvent besoin de plusieurs abonnements Azure en raison de ressources limitées et d’autres considérations de gouvernance. Il est important de disposer d’une stratégie de mise à l’échelle de vos abonnements.

## <a name="production-and-nonproduction-workloads"></a>Charges de travail de production et non-production

Lors du déploiement de votre première charge de travail de production dans Azure, vous devez commencer avec deux abonnements : un pour votre environnement de production et l’autre pour votre environnement de non-production (développement/test).

![Un modèle d’abonnement de base indiquant des clés à côté des cases intitulées « Production » et « Non-production »](../../_images/ready/basic-subscription-model.png)

Nous vous recommandons cette approche pour plusieurs raisons :

- Azure propose des offres d’abonnement spécifiques pour les charges de travail de développement et de test. Ces offres fournissent des tarifs réduits sur les services et licences Azure.
- Vos environnements de production et de non-production auront probablement différents ensembles de stratégies Azure. L’utilisation d’abonnements différents facilite l’application de chaque ensemble distinct de stratégies au niveau de l’abonnement.
- Vous pouvez avoir besoin de certains types de ressources Azure dans un abonnement de développement/test pour les tests. Avec un abonnement distinct, vous pouvez utiliser ces types de ressources sans les rendre disponibles dans votre environnement de production.
- Vous pouvez utiliser les abonnements de développement/test comme des environnements de bac à sable isolés. Ces bacs à sable permettent aux administrateurs et aux développeurs de créer et détruire rapidement des ensembles complets de ressources Azure. Cette isolation peut également aider à résoudre les problèmes de sécurité et de protection des données.
- Les seuils de coût acceptables varieront probablement entre les abonnements de production et de développement/test.

## <a name="other-reasons-for-multiple-subscriptions"></a>Autres raisons d’abonnements multiples

D’autres situations peuvent nécessiter des abonnements supplémentaires. Gardez les points suivants à l’esprit lorsque vous développez votre patrimoine cloud.

- Les abonnements ont des limites différentes pour différents types de ressources. Par exemple, le nombre de réseaux virtuels dans un abonnement est limité. Lorsqu’un abonnement approche de l’une de ses limites, vous devrez créer un autre abonnement et y placer les nouvelles ressources.

  Pour plus d’informations, consultez [Abonnement Azure et limites, quotas et contraintes de service](https://docs.microsoft.com/azure/azure-subscription-service-limits).

- Chaque abonnement peut implémenter ses propres stratégies pour les types de ressources déployables et les régions prises en charge.

- Les abonnements dans les régions du cloud public et celles du cloud souverain ou du cloud public présentent des limitations différentes. Celles-ci sont souvent pilotées par différents niveaux de classification des données entre les environnements.

- Si vous séparez complètement différents ensembles d’utilisateurs pour des raisons de sécurité ou de conformité, vous pouvez avoir besoin d’abonnements distincts. Par exemple, les organisations gouvernementales nationales peuvent être amenées à limiter l’accès d’un abonnement aux citoyens uniquement.

- Différents abonnements peuvent avoir différents types d’offres, chacun avec ses propres conditions et avantages.

- Des problèmes de confiance peuvent exister entre les propriétaires d’un abonnement et le propriétaire des ressources à déployer. L’utilisation d’un autre abonnement avec un autre propriétaire peut atténuer ces problèmes. Toutefois, vous devez également tenir compte des problèmes de mise en réseau et de protection des données qui surviendront dans ce déploiement.

- Des contrôles financiers ou géopolitiques rigides peuvent nécessiter des arrangements financiers distincts pour des abonnements spécifiques. Ces préoccupations peuvent concerner la souveraineté des données, les sociétés ayant plusieurs filiales ou la comptabilité et la facturation distinctes pour les unités commerciales de différents pays et différentes devises.

- Les ressources Azure créées à l’aide du modèle de déploiement classique doivent être isolées dans leur propre abonnement. La sécurité des ressources classiques diffère de celle des ressources déployées via Azure Resource Manager. Les stratégies Azure ne peuvent pas être appliquées aux ressources classiques.

- Les administrateurs de service qui utilisent des ressources classiques ont les mêmes autorisations de contrôle d’accès en fonction du rôle (RBAC) que les propriétaires d’un abonnement. Il est difficile de restreindre suffisamment l’accès de ces administrateurs de service dans un abonnement qui mélange les ressources classiques et celles de Resource Manager.

Vous pouvez également choisir de créer des abonnements supplémentaires pour d’autres raisons commerciales ou techniques spécifiques à votre organisation. Il peut y avoir des coûts supplémentaires pour l’entrée et la sortie des données entre les abonnements.

Vous pouvez déplacer de nombreux types de ressources d’un abonnement à un autre ou utiliser des déploiements automatisés pour migrer des ressources vers un autre abonnement. Pour plus d’informations, consultez [Déplacer des ressources Azure vers un autre groupe de ressources ou abonnement](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).

## <a name="manage-multiple-subscriptions"></a>Gérer des abonnements multiples

Si vous disposez de quelques abonnements seulement, les gérer de manière indépendante est relativement simple. Cependant, si vous avez un grand nombre d’abonnements, vous devriez envisager de créer une hiérarchie de groupes d’administration pour simplifier la gestion de vos abonnements et de vos ressources.

Les groupes d’administration permettent une gestion efficace des accès, des stratégies et de la conformité des abonnements d’une organisation. Chaque groupe d’administration est un conteneur pour un ou plusieurs abonnements.

Les groupes d’administration sont organisés dans une hiérarchie unique. Vous définissez cette hiérarchie dans votre locataire Azure Active Directory (Azure AD) pour l’aligner sur la structure et les besoins de votre organisation. Le niveau supérieur est appelé le *groupe d’administration racine*. Vous pouvez définir jusqu’à six niveaux de groupes d’administration dans votre hiérarchie. Chaque abonnement est contenu dans un seul groupe d’administration.

Azure fournit quatre niveaux d’étendue de la gestion : groupes d’administration, abonnements, groupes de ressources et ressources. Tout accès ou stratégie appliqué à un niveau de la hiérarchie est hérité par les niveaux inférieurs. Le propriétaire d’une ressource ou d’un abonnement ne peut pas modifier une stratégie héritée. Cette limitation permet d’améliorer la gouvernance.

> [!NOTE]
> Notez que l’héritage des balises n’est pas disponible actuellement, mais qu’il le sera bientôt.

En vous appuyant sur ce modèle d’héritage, vous pouvez organiser les abonnements dans votre hiérarchie de façon à ce que chaque abonnement suive les stratégies et les contrôles de sécurité appropriés.

![Les quatre niveaux d’étendue pour l’organisation de vos ressources Azure](../../ready/azure-setup-guide/media/organize-resources/scope-levels.png)

Toute attribution d’accès et de stratégie au groupe d’administration racine s’appliquent à toutes les ressources du répertoire. Examinez attentivement les éléments que vous définissez au niveau de cette étendue. Incluez uniquement les affectations dont vous avez besoin.

Lorsque vous définissez initialement votre hiérarchie de groupes d’administration, vous devez d’abord créer le groupe d’administration racine. Vous déplacez ensuite tous les abonnements existants dans le répertoire vers le groupe d’administration racine. Les nouveaux abonnements sont toujours créés dans le groupe d’administration racine. Vous pouvez les déplacer ultérieurement vers un autre groupe d’administration.

Lorsque vous déplacez un abonnement vers un groupe d’administration existant, il hérite des stratégies et des attributions de rôle de la hiérarchie de groupes d’administration au-dessus de lui. Une fois que vous avez établi plusieurs abonnements pour vos charges de travail Azure, vous devez créer des abonnements supplémentaires pour contenir les services Azure partagés par d’autres abonnements.

![Exemple d’une hiérarchie de groupes d’administration](../../_images/ready/management-group-hierarchy.png)

Pour plus d’informations, consultez [Organiser vos ressources avec des groupes d’administration Azure](https://docs.microsoft.com/azure/governance/management-groups).

## <a name="tips-for-creating-new-subscriptions"></a>Conseils pour la création de nouveaux abonnements

- Identifiez la personne qui sera responsable de la création de nouveaux abonnements.
- Déterminez les ressources qui seront dans un abonnement par défaut.
- Déterminez à quoi ressemblera tous les abonnements standard. Les considérations incluent l’accès RBAC, les stratégies, les balises et les ressources d’infrastructure.
- Si possible, [utilisez un principal de service](https://docs.microsoft.com/azure/azure-resource-manager/grant-access-to-create-subscription) pour créer des abonnements. Définissez un groupe de sécurité qui peut demander de nouveaux abonnements via un flux de travail automatisé.
- Si vous êtes un client Accord Entreprise (EA), demandez au support Azure de bloquer la création d’abonnements non-EA pour votre organisation.

## <a name="related-resources"></a>Ressources associées

- [Concepts fondamentaux Azure](../considerations/fundamental-concepts.md).
- [Organiser vos ressources avec des groupes d’administration Azure](https://docs.microsoft.com/azure/governance/management-groups).
- [Élever l’accès pour gérer tous les abonnements et groupes d’administration Azure](https://docs.microsoft.com/azure/role-based-access-control/elevate-access-global-admin).
- [Déplacer des ressources Azure vers un autre groupe de ressources ou un autre abonnement](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).

## <a name="next-steps"></a>Étapes suivantes

Passez en revue les [conventions de nommage et de catégorisation recommandées](./naming-and-tagging.md) à suivre lors du déploiement de vos ressources Azure.

> [!div class="nextstepaction"]
> [Conventions de nommage et de catégorisation recommandées](./naming-and-tagging.md)
