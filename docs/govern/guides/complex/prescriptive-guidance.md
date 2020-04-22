---
title: 'Gouvernance pour les entreprises complexes : Explication des conseils'
description: Utilisez le Framework d’adoption du cloud pour Azure afin d’établir un produit minimum viable (MVP, minimum viable product) pour la gouvernance qui reflète les bonnes pratiques que doit observer une entreprise complexe.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 50335d2c7e6a628c0fd8886f5d1fac2701d7f286
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80995516"
---
# <a name="governance-guide-for-complex-enterprises-best-practices-explained"></a>Guide de gouvernance pour les entreprises complexes : Explication des conseils

Ce guide de gouvernance commence par un ensemble de [stratégies d’entreprise](./initial-corporate-policy.md) initiales. Ces stratégies permettent de définir un produit minimum viable (MVP) pour la gouvernance. Ce MVP reflète les [meilleures pratiques](./index.md).

Dans cet article, nous allons parler des stratégies de haut niveau qui sont nécessaires pour créer un MVP de gouvernance. Au cœur d’un MVP de gouvernance se trouve la discipline : [Accélération du déploiement](../../deployment-acceleration/index.md). À ce stade, les outils et modèles qui sont appliqués permettent les améliorations incrémentielles nécessaires au développement de la gouvernance à l’avenir.

## <a name="governance-mvp-initial-governance-foundation"></a>Produit minimum viable de gouvernance (fondation de gouvernance initiale)

Grâce à quelques principes simples et à des outils de gouvernance basés sur le cloud, il est possible d’adopter rapidement la gouvernance et une stratégie d’entreprise. Voici la première des trois disciplines de gouvernance à aborder lors d’un processus de gouvernance. Chaque discipline est expliquée plus loin dans cet article.

Pour établir le point de départ, cet article traite des stratégies de haut niveau derrière la base de référence des identités, la base de référence de la sécurité et l’accélération du déploiement. Ces stratégies sont requises pour créer un MVP de gouvernance, qui serve de base pour l’ensemble du processus d’adoption.

![Exemple de MVP de gouvernance incrémentielle](../../../_images/govern/governance-mvp.png)

## <a name="implementation-process"></a>Processus d’implémentation

L’implémentation du MVP de gouvernance dépend de l’identité, de la sécurité et de la mise en réseau. Une fois les dépendances résolues, l’équipe de gouvernance cloud fait des choix sur certains aspects de gouvernance. Les décisions prises par l’équipe de gouvernance cloud et les équipes d’aide sont implémentées par le biais d’un seul package de ressources d’application.

![Exemple de MVP de gouvernance incrémentielle](../../../_images/govern/governance-mvp-implementation-flow.png)

Cette implémentation peut également être décrite à l’aide d’une simple check-list :

1. Sollicitez des décisions concernant les principales dépendances : identité, réseau et chiffrement.
1. Déterminez le modèle à utiliser lors de l’application des stratégies d’entreprise.
1. Déterminez les modèles de gouvernance appropriés pour les disciplines suivantes : cohérence des ressources, identification des ressources, création et journalisation de rapports.
1. Implémentez les outils de gouvernance alignés sur le modèle d’application de stratégie choisi, dans le but d’appliquer des décisions dépendantes et des décisions de gouvernance.

[!INCLUDE [implementation-process](../../../../includes/implementation-process.md)]

## <a name="application-of-governance-defined-patterns"></a>Application de modèles définis par la gouvernance

L’équipe de gouvernance cloud est responsable des décisions et implémentations suivantes. Nombreuses sont celles qui ont besoin du travail d’autres équipes, mais l’équipe de gouvernance cloud devrait être à la fois maître des décisions et de l’implémentation. Les sections suivantes indiquent les décisions prises pour ce cas d’usage, et les détails pour chacune de ces décisions.

### <a name="subscription-design"></a>Conception de l’abonnement

La décision sur la conception de l’abonnement à utiliser détermine la façon dont les abonnements Azure sont structurés, et la façon dont les groupes d’administration Azure sont utilisés pour gérer efficacement l’accès, les stratégies et la conformité de ces abonnements. Dans ce scénario, l’équipe de gouvernance a choisi une **[stratégie d’abonnement mixte](../../../decision-guides/subscriptions/index.md#mixing-subscription-strategies)** .

- Comme les nouvelles requêtes pour des ressources Azure augmentent, un « Département » doit être établi pour chacune des grandes unités commerciales dans chaque géographie opérationnelle. Dans chacun de ces départements, des « abonnements » doivent être créés pour chaque archétype d’application.
- Un archétype d’application est un moyen de regrouper des applications dont les besoins sont similaires. Voici quelques exemples communs : Applications avec des données protégées, applications régies (telles que HIPAA ou FedRAMP), applications à faible risque, applications avec des dépendances locales, applications SAP ou autre mainframe dans Azure, ou applications qui étendent localement des applications SAP ou mainframe. Chaque organisation a ses propres besoins, en fonction des classifications de données et des types d’applications qui alimentent l’entreprise. Le mappage des dépendances de l’investissement numérique peut aider à définir les archétypes d’application dans une organisation.
- Une convention d’affectation de noms commune doit être convenue dans le cadre de la conception de l’abonnement, en tenant compte des deux points précédents.

### <a name="resource-consistency"></a>Cohérence des ressources

Les décisions relatives à la cohérence des ressources déterminent les outils, processus et efforts nécessaires pour garantir que les ressources Azure sont déployées, configurées et gérées de manière cohérente au sein d’un abonnement. Dans ce scénario, la **[cohérence de déploiement](../../../decision-guides/resource-consistency/index.md#deployment-consistency)** a été choisie comme modèle de cohérence des ressources principales.

- Des groupes de ressources sont créés pour les applications à l’aide de l’approche du cycle de vie. Tout ce qui est créé, maintenu et mis hors service ensemble doit résider dans un seul groupe de ressources. Pour plus d’informations, consultez le [Guide de décision pour la cohérence des ressources](../../../decision-guides/resource-consistency/index.md#basic-grouping).
- La stratégie Azure doit être appliquée à tous les abonnements du groupe d’administration associé.
- Dans le cadre du processus de déploiement, les modèles Cohérence des ressources Azure doivent être stockés dans le contrôle du code source pour le groupe de ressources.
- Chaque groupe de ressources est associé à une charge de travail ou à une application spécifique basée sur l’approche par cycle de vie décrit plus haut.
- Les groupes d’administration Azure permettent de mettre à jour les modèles de gouvernance au fur et à mesure que la stratégie de l’entreprise évolue.
- La mise en œuvre à grande échelle d’Azure Policy peut dépasser les échéances fixées par l’équipe et ne pas présenter un intérêt tangible pour le moment. Toutefois, une stratégie simple par défaut doit être créée et appliquée à chaque groupe de gestion pour faire respecter le faible nombre d’instructions portant sur la gouvernance cloud. Cette stratégie est censée définir l’implémentation d’exigences précises en matière de gouvernance. Ces implémentations peuvent ensuite être appliquées à toutes les ressources déployées.

>[!IMPORTANT]
>Chaque fois qu’une ressource d’un groupe de ressources ne partage plus le même cycle de vie, elle doit être déplacée vers un autre groupe de ressources. Il peut s’agir par exemple des bases de données communes et de composants de mise en réseau. Bien que ces éléments puissent servir l’application en cours de développement, ils peuvent également servir à d’autres fins et doivent donc exister dans d’autres groupes de ressources.

### <a name="resource-tagging"></a>Identification des ressources

Les décisions relatives à l’identification des ressources déterminent la façon dont les métadonnées sont appliquées aux ressources Azure au sein d’un abonnement pour prendre en charge les opérations, la gestion et la comptabilité. Dans ce scénario, le modèle **[ Comptabilité](../../../decision-guides/resource-tagging/index.md#resource-tagging-patterns)** a été choisi comme modèle par défaut pour l’identification des ressources.

- Les ressources déployées doivent être étiquetées avec des valeurs pour :
  - Département/Unité de facturation
  - Geography
  - Classification des données
  - Caractère critique
  - Contrat SLA
  - Environnement
  - Archétype d’application
  - Application
  - Propriétaire de l’application
- Ces valeurs ainsi que le groupe d’administration et l’abonnement Azure, associés à une ressource déployée, orientent les décisions en matière de gouvernance, opérations et sécurité.

### <a name="logging-and-reporting"></a>Journalisation et création de rapports

Les décisions relatives à la journalisation et la création de rapports déterminent la façon dont votre magasin stocke les données, et la façon dont les outils de supervision et de création de rapports, qui renseignent le personnel informatique sur l’intégrité opérationnelle, sont structurées. Dans ce scénario, un modèle **[Supervision hybride](../../../decision-guides/logging-and-reporting/index.md)** de journalisation et création de rapports est suggéré, mais pas exigé à ce stade par les équipes de développement.

- Pour le moment, aucune exigence en matière de gouvernance n’a été établie pour les points de données spécifiques qui doivent être collectés à des fins de journalisation et de création de rapports. Il s’agit d’un élément spécifique (qui doit être considéré comme un anti-modèle) à ce scénario fictif. Les normes de journalisation doivent être définies et appliquées dès que possible.
- Une analyse supplémentaire est nécessaire avant de publier les données protégées ou les charges de travail critiques.
- Avant de prendre en charge les données protégées ou les charges de travail critiques, la solution de supervision opérationnelle, qui existe déjà en local, doit avoir accès à l’espace de travail utilisé pour la journalisation. Les applications doivent répondre aux exigences de sécurité et de journalisation associées à l’utilisation du locataire, si l’application doit être conforme à un SLA défini.

## <a name="incremental-of-governance-processes"></a>Incrémentiel des processus de gouvernance

Certaines instructions de stratégie ne peuvent pas ou ne doivent pas être contrôlées par des outils automatisés. D’autres stratégies nécessitent que les équipes en charge de la base de référence locale des identités et de la sécurité informatique fassent des efforts réguliers. L’équipe de gouvernance cloud doit surveiller les processus suivants pour implémenter les huit dernières instructions de stratégie :

**Modifications de la stratégie d’entreprise :** L’équipe de gouvernance cloud apporte des modifications à la conception du MVP de gouvernance, afin d’adopter les nouvelles stratégies. L’avantage du MVP de gouvernance est qu’il permet l’application automatique des nouvelles stratégies.

**Accélération de l’adoption :** L’équipe de gouvernance cloud a passé en revue les scripts de déploiement au sein de plusieurs équipes. Elle gère un ensemble de scripts qui servent de modèles de déploiement. Ces modèles peuvent être utilisés par les équipes d’adoption du cloud et des DevOps pour définir plus rapidement les déploiements. Chaque script contient les exigences nécessaires à l’application des stratégies de gouvernance. Aucun effort supplémentaire des ingénieurs d’adoption du cloud n’est nécessaire. En tant que conservatrice de ces scripts, l’équipe de gouvernance cloud peut implémenter plus rapidement des changements de stratégie. En outre, elle est considérée comme une force d’accélération de l’adoption. Il est ainsi possible d’obtenir des déploiements cohérents sans avoir à imposer une adhésion stricte.

**Formation technique :** L’équipe de gouvernance cloud propose des sessions de formation bimensuelles et a créé deux vidéos à l’intention des ingénieurs. Ces ressources aident les ingénieurs à se familiariser rapidement avec la culture de la gouvernance et avec l’exécution des déploiements. L’équipe ajoute des ressources de formation qui mettent en évidence la différence entre les déploiements en production et les autres, afin que les ingénieurs comprennent l’impact des nouvelles stratégies sur l’adoption du cloud. Il est ainsi possible d’obtenir des déploiements cohérents sans avoir à imposer une adhésion stricte.

**Planification du déploiement :** Avant de déployer toute ressource contenant des données protégées, l’équipe de gouvernance cloud est tenue d’examiner les scripts de déploiement afin de valider l’alignement de la gouvernance. Les équipes existantes dont les déploiements ont déjà été approuvés feront l’objet d’un audit à l’aide d’outils de programmation.

**Audit et création de rapports mensuels :** Tous les mois, l’équipe de gouvernance cloud effectue un audit de tous les déploiements cloud afin de valider l’adéquation continue à la stratégie. Lorsque des écarts sont identifiés, ils sont documentés et partagés avec les équipes d’adoption du cloud. Lorsque l’implémentation ne risque pas d’entraîner une interruption des activités ou une fuite de données, les stratégies sont automatiquement implémentées. À la fin de l’audit, l’équipe de gouvernance cloud compile un rapport pour l’équipe de stratégie cloud et chaque équipe d’adoption du cloud, afin de communiquer sur l’adhésion générale des parties prenantes à la stratégie. Le rapport est également conservé à des fins d’audit et juridiques.

**Révision de la stratégie trimestrielle :** Chaque trimestre, l’équipe de gouvernance cloud et l’équipe de la stratégie cloud examinent les résultats de l’audit et proposent que des modifications soient apportées à la stratégie de l’entreprise. La plupart de ces suggestions sont le résultat d’améliorations continues et de l’observation des modèles d’utilisation. Les modifications de stratégie approuvées sont intégrées à l’outil de gouvernance au cours des cycles d’audit ultérieurs.

## <a name="alternative-patterns"></a>Autres modèles

Si l’un des modèles choisis dans ce guide de gouvernance ne correspond pas aux besoins du lecteur, chaque modèle présente une solution de rechange :

- [Modèles de chiffrement](../../../decision-guides/encryption/index.md)
- [Modèles d’identité](../../../decision-guides/identity/index.md)
- [Modèles de journalisation et de création de rapports](../../../decision-guides/logging-and-reporting/index.md)
- [Modèles d’implémentation de stratégie](../../../decision-guides/policy-enforcement/index.md)
- [Modèles de cohérence des ressources](../../../decision-guides/resource-consistency/index.md)
- [Modèles d’étiquetage des ressources](../../../decision-guides/resource-tagging/index.md)
- [Modèles SDN (Software Defined Networking)](../../../decision-guides/software-defined-network/index.md)
- [Modèles de conception des abonnements](../../../decision-guides/subscriptions/index.md)

## <a name="next-steps"></a>Étapes suivantes

Une fois ce guide implémenté, chaque équipe d’adoption du cloud peut s’appuyer sur une base de gouvernance solide. Parallèlement, l’équipe de gouvernance cloud travaille à la mise à jour continue des stratégies d’entreprise et des disciplines de gouvernance.

Les deux équipes utilisent les indicateurs de tolérance pour identifier le prochain groupe d’améliorations nécessaires à la poursuite de la prise en charge de l’adoption du cloud. La prochaine étape pour cette entreprise est l’amélioration incrémentielle de sa base de référence de gouvernance, afin de prendre en charge les applications ayant des exigences d’authentification multifacteur héritée ou de tiers.

> [!div class="nextstepaction"]
> [Améliorer la discipline Base de référence des identités](./identity-baseline-improvement.md)
