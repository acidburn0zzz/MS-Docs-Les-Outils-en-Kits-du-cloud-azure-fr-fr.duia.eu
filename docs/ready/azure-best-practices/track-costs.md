---
title: Suivre les coûts dans les unités commerciales et les environnements
description: Utilisez le Cloud Adoption Framework pour Azure afin de découvrir les décisions et les approches d’implémentation relatives à la création de mécanismes de suivi.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: ce9ce90d429064eeb8e848fd203aec11d042e539
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80354535"
---
# <a name="track-costs-across-business-units-environments-or-projects"></a>Suivi des coûts dans les unités commerciales, les environnements ou les projets

[La création d’une organisation soucieuse des coûts](../../organize/cost-conscious-organization.md) requiert une visibilité des données relatives aux coûts et un accès (ou une étendue) correctement défini à celles-ci. Cet article sur les meilleures pratiques décrit les décisions et les approches d’implémentation visant à créer des mécanismes de suivi.

![Plan du processus attentif aux coûts](../../_images/ready/cost-optimization-process.png)

## <a name="establish-a-well-managed-environment-hierarchy"></a>Établir une hiérarchie d’environnement bien managée

Le contrôle des coûts, de la même façon que la gouvernance et d’autres constructions de gestion, dépend d’un environnement bien managé. L’établissement d’un tel environnement (et particulièrement un environnement complexe) requiert des processus cohérents dans la classification et l’organisation de toutes les ressources.

Les ressources incluent l’ensemble des machines virtuelles, des sources de données et des applications déployées dans le cloud. Azure fournit plusieurs mécanismes de classification et d’organisation des ressources. La rubrique [Organiser et gérer vos abonnements Azure](../azure-best-practices/organize-subscriptions.md) fournit les informations sur l’organisation des ressources en fonction de plusieurs critères afin d’établir un environnement bien managé. Cet article se concentre sur l’application des concepts fondamentaux d’Azure pour fournir une visibilité des coûts du cloud.

### <a name="classification"></a>classification ;

La *catégorisation* est un moyen simple de classer les ressources. La catégorisation associe des métadonnées à une ressource. Ces métadonnées peuvent être utilisées pour classer la ressource en fonction de divers points de données. Lorsque des balises sont utilisées pour classer des ressources dans le cadre d’un effort de gestion des coûts, les sociétés ont souvent besoin des balises suivantes : unité commerciale, service, code de facturation, zone géographique, environnement, projet et charge de travail ou « catégorisation d’application ». Azure Cost Management peut utiliser ces balises pour créer des affichages différents de données de coûts.

La catégorisation est un moyen primaire de comprendre les données dans les rapports de coûts. Il s’agit d’un élément fondamental de tout environnement bien managé. C’est également la première étape pour établir la gouvernance appropriée de tout environnement.

La première étape dans le suivi précis des informations relatives aux coûts dans les unités commerciales, les environnements et les projets consiste à définir un standard de catégorisation. La seconde étape consiste à s’assurer que le standard de catégorisation est appliqué de manière cohérente. Les articles suivants peuvent vous aider à effectuer chacune de ces étapes :

- [Développer des standards de nommage et de catégorisation](../azure-best-practices/naming-and-tagging.md)
- [Établir un MVP de gouvernance pour appliquer les standards de catégorisation](../../govern/guides/complex/index.md)

### <a name="resource-organization"></a>Organisation des ressources

Il existe plusieurs approches pour organiser les ressources. Cette section décrit une meilleure pratique basée sur les besoins d’une grande entreprise avec des structures de coût réparties entre les unités commerciales, les zones géographiques et les organisations informatiques. Une meilleure pratique similaire pour une organisation plus petite et moins complexe est disponible dans le [guide de gouvernance pour les entreprises standard](../../govern/guides/standard/index.md).

Dans le cas d’une grande entreprise, le modèle suivant pour les groupes d’administration, les abonnements et les groupes de ressources créera une hiérarchie permettant à chaque équipe d’avoir le niveau de visibilité approprié pour accomplir ses tâches. Lorsque l’entreprise a besoin de contrôles de coûts pour empêcher les dépassements de budget, elle peut appliquer des outils de gouvernance tels qu’Azure Blueprints ou Azure Policy aux abonnements au sein de cette structure pour bloquer rapidement les futures erreurs de coût.

![Diagramme d’organisation des ressources pour une grande entreprise](../../_images/govern/large-enterprise-resource-organization.png)

Dans le diagramme précédent, la racine de la hiérarchie des groupes d’administration contient un nœud pour chaque unité commerciale. Dans cet exemple, la société multinationale a besoin d’une visibilité sur les unités commerciales régionales, de sorte qu’elle crée un nœud pour la zone géographique sous chaque unité commerciale de la hiérarchie.

Dans chaque zone géographique, il existe un nœud distinct pour les environnements de production et hors production afin d’isoler les contrôles des coûts, de l’accès et de la gouvernance. Pour permettre des opérations plus efficaces et des investissements en opérations plus judicieux, la société utilise des abonnements pour isoler davantage les environnements de production avec différents niveaux d’engagements en matière de niveau de performance opérationnel. Enfin, la société utilise des groupes de ressources pour capturer les unités déployables d’une fonction, appelées applications.

Le diagramme montre les meilleures pratiques, mais n’inclut pas les options suivantes :

- De nombreuses entreprises limitent les opérations à une seule région géopolitique. Cette approche réduit la nécessité de diversifier les disciplines de gouvernance ou les données de coût en fonction des exigences locales de souveraineté des données. Dans ce cas, un nœud géographique est inutile.
- Certaines entreprises préfèrent mieux séparer les environnements de développement, de test et de contrôle qualité dans des abonnements distincts.
- Quand une société intègre une équipe Centre d’excellence du cloud (CCoE), les abonnements aux services partagés dans chaque nœud géographique peuvent réduire les ressources dupliquées.
- Des efforts d’adoption plus petits peuvent avoir une hiérarchie de gestion bien plus petite. Il est courant de voir un seul nœud racine pour le service informatique de l’entreprise, avec un seul niveau de nœuds subordonnés dans la hiérarchie pour différents environnements. Il ne s’agit pas d’une violation des meilleures pratiques pour un environnement bien managé. Toutefois, cela rend plus difficile la proposition d’un modèle d’accès de moindres droits pour le contrôle des coûts et d’autres fonctions importantes.

Le reste de cet article suppose l’utilisation de l’approche recommandée dans le diagramme précédent. Toutefois, les articles suivants peuvent vous aider à appliquer l’approche à une organisation de ressources qui correspond le mieux à votre entreprise :

- [Mettre à l’échelle votre environnement Azure avec plusieurs abonnements](../azure-best-practices/scale-subscriptions.md)
- [Organiser et gérer vos abonnements Azure](../azure-best-practices/organize-subscriptions.md)
- [Déployer un MVP de gouvernance pour gérer les standards en matière d’environnements bien managés](../../govern/guides/complex/index.md)

## <a name="provide-the-right-level-of-cost-access"></a>Fournir le niveau approprié en matière d’accès aux coûts

La gestion des coûts est une activité d’équipe. La section du Framework d’adoption du cloud relative à la préparation de l’organisation définit un petit nombre d’équipes principales et décrit la façon dont ces équipes prennent en charge les efforts d’adoption du cloud. Cet article développe les définitions d’équipe afin de définir l’étendue et les rôles à attribuer aux membres de chaque équipe pour obtenir le niveau de visibilité approprié des données de gestion des coûts.

- Les **rôles** définissent ce qu’un utilisateur peut faire sur plusieurs ressources.
- L’**étendue** définit les ressources (utilisateur, groupe, principal de service ou identité managée) sur lesquelles un utilisateur peut intervenir.

En règle générale et à titre de meilleure pratique, nous vous suggérons de disposer d’un modèle basé sur le privilège minimum pour affecter des personnes à différents rôles et étendues.

### <a name="roles"></a>Rôles

Azure Cost Management prend en charge les rôles intégrés suivants pour chaque étendue :

- [Propriétaire](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner). Peut afficher les coûts et tout gérer, y compris la configuration des coûts.
- [Contributeur](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor). Peut afficher les coûts et tout gérer, y compris la configuration des coûts, à l’exclusion du contrôle d’accès.
- [Lecteur](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#reader). Peut tout afficher, y compris les données et la configuration des coûts, mais ne peut pas apporter de modifications.
- [Contributeur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor). Peut afficher les coûts et gérer leur configuration.
- [Lecteur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-reader) Peut afficher les données et la configuration des coûts.

En règle générale et à titre de meilleure pratique, les membres de toutes les équipes doivent être affectés au rôle de Contributeur Cost Management. Celui-ci accorde un accès permettant de créer et gérer les budgets et les exportations pour une surveillance et une création de rapports plus efficaces sur les coûts. Toutefois, les membres de l’[équipe de stratégie cloud](../../organize/cloud-strategy.md) doivent être définis sur Lecteur Cost Management uniquement. Cela est dû au fait qu’ils ne sont pas impliqués dans le paramétrage des budgets au sein de l’outil Azure Cost Management.

### <a name="scope"></a>Étendue

Les paramètres d’étendue et de rôle suivants vont créer la visibilité requise dans la gestion des coûts. Cette meilleure pratique peut nécessiter des modifications mineures pour s’aligner sur les décisions relatives à l’organisation des ressources.

- [Équipe d’adoption du cloud](../../organize/cloud-adoption.md). Les responsabilités liées aux modifications d’optimisation continue nécessitent un accès du contributeur Cost Management au niveau du groupe de ressources.

  - **Environnement de travail**. Au minimum, l’équipe d’adoption du cloud doit déjà avoir un accès [Contributeur](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) à tous les groupes de ressources concernés, ou au moins à ces groupes associés aux activités de développement/test ou de déploiement continu. Aucun paramètre d’étendue supplémentaire n’est requis.
  - **Environnements de production**. Lorsque une séparation appropriée des responsabilités a été établie, l’équipe d’adoption du cloud ne pourra probablement pas continuer à accéder aux groupes de ressources associés à ses projets. Les groupes de ressources qui prennent en charge les instances de production de leurs charges de travail auront besoin d’une étendue supplémentaire pour permettre à cette équipe de mieux comprendre l’impact de ses décisions sur les coûts de production. Le paramétrage de l’étendue du [contributeur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) pour les groupes de ressources de production de cette équipe permettra à l’équipe de surveiller les coûts et de définir des budgets en fonction de l’utilisation et des investissements continus dans les charges de travail prises en charge.

- [Équipe de stratégie cloud](../../organize/cloud-strategy.md). Les responsabilités relatives au suivi des coûts entre plusieurs projets et unités commerciales nécessitent un accès Lecteur Cost Management au niveau racine de la hiérarchie des groupes d’administration.

  - Attribuez à cette équipe un accès [Lecteur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-reader) au groupe d’administration. Cela garantira une visibilité permanente de tous les déploiements associés aux abonnements régis par cette hiérarchie de groupes d’administration.

- [Équipe de gouvernance cloud](../../organize/cloud-governance.md). Les responsabilités relatives à la gestion des coûts, à l’alignement du budget et à la création de rapports pour tous les efforts d’adoption nécessitent un accès Contributeur Cost Management au niveau racine de la hiérarchie des groupes d’administration.

  - Dans un environnement bien managé, l’équipe de gouvernance cloud a probablement un degré d’accès plus élevé, ce qui rend inutile l’attribution d’une étendue supplémentaire pour un [Contributeur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor).

<!-- cSpell:ignore automations -->

- [Centre d’excellence du cloud](../../organize/cloud-center-of-excellence.md). La responsabilité de la gestion des coûts associés aux services partagés requiert un accès Contributeur Cost Management au niveau de l’abonnement. En outre, cette équipe peut nécessiter un accès Contributeur Cost Management aux groupes de ressources ou aux abonnements contenant des ressources déployées par les automatisations du CCoE pour comprendre comment ces automatisations influencent les coûts.

  - **Services partagés**. Lorsqu’un centre d’excellence du cloud est engagé, la meilleure pratique consiste à ce que les ressources managées par le CCoE soient prises en charge à partir d’un abonnement de services partagés centralisé au sein d’un modèle hub and spoke. Dans ce scénario, le CCoE est susceptible d’avoir un accès contributeur ou propriétaire à cet abonnement, ce qui rend inutile l’attribution d’une étendue supplémentaire pour un [Contributeur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor).
  - **Automatisation/contrôles du CCoE**. Le CCoE fournit généralement des contrôles et des scripts de déploiement automatisés aux équipes d’adoption du cloud. Le CCoE a la responsabilité de comprendre comment ces accélérateurs influencent les coûts. Pour obtenir cette visibilité, l’équipe a besoin d’un accès [Contributeur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) à tous les groupes de ressources ou abonnements qui exécutent ces accélérateurs.

- **Équipe des opérations cloud**. La responsabilité de la gestion des coûts continus des environnements de production nécessite un accès Contributeur Cost Management à tous les abonnements de production.

  - La recommandation générale place les ressources de production et hors production dans des abonnements distincts qui sont régis par des nœuds de la hiérarchie des groupes d’administration associés aux environnements de production. Dans un environnement bien managé, les membres de l’équipe responsable des opérations ont probablement un accès propriétaire ou contributeur aux abonnements de production, ce qui rend inutile le rôle [Contributeur Cost Management](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor).

## <a name="additional-cost-management-resources"></a>Ressources de gestion des coûts supplémentaires

Azure Cost Management est un outil bien documenté permettant de définir des budgets et de bénéficier d’une visibilité sur les coûts du cloud pour Azure ou AWS. Une fois que vous avez établi l’accès à une hiérarchie d’environnements bien managée, les articles suivants peuvent vous aider à utiliser cet outil pour surveiller et contrôler les coûts.

### <a name="get-started-with-azure-cost-management"></a>Prise en main d’Azure Cost Management

Pour plus d’informations sur la prise en main d’Azure Cost Management, consultez le [Guide pratique pour optimiser votre investissement dans le cloud avec Azure Cost Management](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json).

### <a name="use-azure-cost-management"></a>utiliser Azure Cost Management

- [Créer et gérer des budgets](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets)
- [Exporter des données de coûts](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-export-acm-data)
- [Optimiser les coûts selon les recommandations](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations)
- [Utiliser les alertes de coût pour superviser l’utilisation et les dépenses](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-alerts-monitor-usage-spending)

### <a name="use-azure-cost-management-to-govern-aws-costs"></a>Utiliser Azure Cost Management pour régir les coûts d’AWS

- [Intégration des rapports sur les coûts et l’utilisation d’AWS](https://docs.microsoft.com/azure/cost-management-billing/costs/aws-integration-set-up-configure)
- [Gérer les coûts d’AWS](https://docs.microsoft.com/azure/cost-management/aws-integration-manage)

### <a name="establish-access-roles-and-scope"></a>Établir l’accès, les rôles et l’étendue

- [Compréhension de l’étendue de la gestion des coûts](https://docs.microsoft.com/azure/cost-management/understand-work-scopes)
- [Définition de l’étendue d’un groupe de ressources](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal)
