---
title: 'Gouvernance pour les entreprises standard : Explication des conseils'
description: Utilisez le Framework d’adoption du cloud pour Azure afin d’établir un produit minimum viable (MVP, minimum viable product) pour la gouvernance qui reflète les bonnes pratiques que doit observer une entreprise standard.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: b7f8b26833a98ac02a867b466e58f5214334a0b5
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219991"
---
# <a name="standard-enterprise-governance-guide-best-practices-explained"></a>Guide de gouvernance pour les entreprises standard : Explication des conseils

Ce guide de gouvernance commence par un ensemble de [stratégies d’entreprise](./initial-corporate-policy.md) initiales. Ces stratégies permettent de définir un produit minimum viable (MVP) pour la gouvernance reflétant les [meilleures pratiques](./index.md).

Dans cet article, nous allons parler des stratégies de haut niveau qui sont nécessaires pour créer un MVP de gouvernance. Au cœur d’un MVP de gouvernance se trouve la discipline : [Accélération du déploiement](../../deployment-acceleration/index.md). À ce stade, les outils et modèles qui sont appliqués permettent les améliorations incrémentielles nécessaires au développement de la gouvernance à l’avenir.

## <a name="governance-mvp-initial-governance-foundation"></a>Produit minimum viable de gouvernance (fondation de gouvernance initiale)

Grâce à quelques principes simples et à des outils de gouvernance basés sur le cloud, il est possible d’adopter rapidement la gouvernance et une stratégie d’entreprise. Voici les trois premières disciplines de gouvernance à aborder lors d’un processus de gouvernance. Chaque discipline est expliquée plus loin dans cet article.

<!--docsTest:ignore "Identity Baseline, Security Baseline, and Deployment Acceleration disciplines" -->

Pour établir le point de départ, cet article traite des stratégies de haut niveau derrière la base de référence des identités, la base de référence de la sécurité et l’accélération du déploiement. Ces disciplines sont requises pour créer un MVP de gouvernance, qui serve de base pour l’ensemble du processus d’adoption.

![Exemple de MVP de gouvernance incrémentielle](../../../_images/govern/governance-mvp.png)

## <a name="implementation-process"></a>Processus d’implémentation

L’implémentation du MVP de gouvernance dépend de l’identité, de la sécurité et de la mise en réseau. Une fois les dépendances résolues, l’équipe de gouvernance cloud fait des choix sur certains aspects de gouvernance. Les décisions prises par l’équipe de gouvernance cloud et les équipes d’aide sont implémentées par le biais d’un seul package de ressources d’application.

![Exemple de MVP de gouvernance incrémentielle](../../../_images/govern/governance-mvp-implementation-flow.png)

Cette implémentation peut également être décrite à l’aide d’une simple check-list :

1. Sollicitez des décisions concernant les dépendances principales : identité, mise en réseau, surveillance et chiffrement.
2. Déterminez le modèle à utiliser lors de l’application des stratégies d’entreprise.
3. Déterminez les modèles de gouvernance appropriés pour les disciplines suivantes : cohérence des ressources, identification des ressources, création et journalisation de rapports.
4. Implémentez les outils de gouvernance alignés sur le modèle d’application de stratégie choisi, dans le but d’appliquer des décisions dépendantes et des décisions de gouvernance.

[!INCLUDE [implementation-process](../../../../includes/implementation-process.md)]

## <a name="application-of-governance-defined-patterns"></a>Application de modèles définis par la gouvernance

L’équipe de gouvernance cloud est responsable des décisions et implémentations suivantes. Beaucoup ont besoin du travail d’autres équipes, mais l’équipe de gouvernance cloud devrait être à la fois maître des décisions et de l’implémentation. Les sections suivantes indiquent les décisions prises pour ce cas d’usage, et les détails pour chacune de ces décisions.

### <a name="subscription-design"></a>Conception de l’abonnement

La décision sur la conception de l’abonnement à utiliser détermine la façon dont les abonnements Azure sont structurés, et la façon dont les groupes d’administration Azure sont utilisés pour gérer efficacement l’accès, les stratégies et la conformité de ces abonnements. Dans ce scénario, l’équipe de gouvernance a établi des abonnements pour les charges de travail de production et de non-production (modèle de conception d’abonnement [production-and-nonproduction](../../../ready/azure-best-practices/initial-subscriptions.md)).

- Il est peu probable que les département doivent intervenir dans ce processus. Les déploiements sont en principe limités au sein d’une même unité de facturation. Au stade de l’adoption, il se peut même qu’il n’y ait pas de contrat entreprise pour centraliser la facturation. Il est probable que ce niveau d’adoption soit géré par un seul abonnement Azure avec paiement à l’utilisation.
- Indépendamment de l’utilisation du portail EA ou de l’existence d’un contrat entreprise, un modèle d’abonnement doit quand même être défini et convenu afin de minimiser le nombre de demandes administratives ne portant pas sur la facturation.
- Une convention d’affectation de noms commune doit être convenue dans le cadre de la conception de l’abonnement, en tenant compte des deux points précédents.

### <a name="resource-consistency"></a>Cohérence des ressources

Les décisions relatives à la cohérence des ressources déterminent les outils, processus et efforts nécessaires pour garantir que les ressources Azure sont déployées, configurées et gérées de manière cohérente au sein d’un abonnement. Dans ce scénario, la [cohérence de déploiement](../../../decision-guides/resource-consistency/index.md#deployment-consistency) a été choisie comme modèle de cohérence des ressources principales.

- Des groupes de ressources sont créés pour les applications à l’aide de l’approche du cycle de vie. Tout ce qui est créé, maintenu et mis hors service ensemble doit résider dans un seul groupe de ressources. Pour plus d’informations, consultez le [Guide de décision pour la cohérence des ressources](../../../decision-guides/resource-consistency/index.md#basic-grouping).
- La stratégie Azure doit être appliquée à tous les abonnements du groupe d’administration associé.
- Dans le cadre du processus de déploiement, les modèles Cohérence des ressources Azure doivent être stockés dans le contrôle du code source pour le groupe de ressources.
- Chaque groupe de ressources est associé à une charge de travail ou à une application spécifique basée sur l’approche par cycle de vie décrit plus haut.
- Les groupes d’administration Azure permettent de mettre à jour les modèles de gouvernance au fur et à mesure que la stratégie de l’entreprise évolue.
- La mise en œuvre à grande échelle d’Azure Policy peut dépasser les échéances fixées par l’équipe et ne pas présenter un intérêt tangible pour le moment. Toutefois, une stratégie simple par défaut doit être créée et appliquée à chaque groupe de gestion pour faire respecter le faible nombre d’instructions portant sur la gouvernance cloud. Cette stratégie est censée définir l’implémentation d’exigences précises en matière de gouvernance. Ces implémentations peuvent ensuite être appliquées à toutes les ressources déployées.

>[!IMPORTANT]
>Chaque fois qu’une ressource d’un groupe de ressources ne partage plus le même cycle de vie, elle doit être déplacée vers un autre groupe de ressources. Il peut s’agir par exemple des bases de données communes et de composants de mise en réseau. Bien que ces éléments puissent servir l’application en cours de développement, ils peuvent également servir à d’autres fins et doivent donc exister dans d’autres groupes de ressources.

### <a name="resource-tagging"></a>Identification des ressources

Les décisions relatives à l’identification des ressources déterminent la façon dont les métadonnées sont appliquées aux ressources Azure au sein d’un abonnement pour prendre en charge les opérations, la gestion et la comptabilité. Dans ce scénario, le modèle [Classification](../../../decision-guides/resource-tagging/index.md#resource-tagging-patterns) a été choisi comme modèle par défaut pour l’identification des ressources.

- Les ressources déployées doivent être étiquetées avec :
  - Classification des données
  - Caractère critique
  - Contrat SLA
  - Environnement
- Ces quatre valeurs guideront la gouvernance, les opérations et les décisions en matière de sécurité.
- Si ce guide de gouvernance est mis en œuvre pour une unité opérationnelle ou une équipe au sein d’une grande entreprise, le balisage doit également inclure des métadonnées pour l’unité de facturation.

### <a name="logging-and-reporting"></a>Journalisation et création de rapports

Les décisions relatives à la journalisation et la création de rapports déterminent la façon dont votre magasin stocke les données, et la façon dont les outils de supervision et de création de rapports, qui renseignent le personnel informatique sur l’intégrité opérationnelle, sont structurées. Dans cette narration, un [modèle cloud natif](../../../decision-guides/logging-and-reporting/index.md#cloud-native)** pour la journalisation et la création de rapports est suggéré.

## <a name="incremental-improvement-of-governance-processes"></a>Amélioration incrémentielle des processus de gouvernance

Avec l’évolution de la gouvernance, certaines instructions de stratégie ne peuvent ou ne doivent pas être contrôlées par des outils automatisés. D’autres stratégies donnent lieu à des efforts de la part de l’équipe de sécurité informatique et de l’équipe de gestion des identités localement au fil du temps. Pour aider à réduire les nouveaux risques au fur et à mesure qu’ils surviennent, l’équipe de gouvernance cloud supervise les processus suivants.

**Accélération de l’adoption :** L’équipe de gouvernance cloud a passé en revue les scripts de déploiement au sein de plusieurs équipes. Celles-ci gèrent un ensemble de scripts qui servent de modèles de déploiement. Ces modèles sont utilisés par les équipes d’adoption du cloud et des DevOps pour définir plus rapidement les déploiements. Chacun de ces scripts contient les exigences nécessaires à l’implémentation d’un jeu de stratégies de gouvernance, sans effort supplémentaire de la part des ingénieurs chargés de l’adoption du cloud. En tant que conservatrice de ces scripts, l’équipe de gouvernance cloud peut implémenter plus rapidement des changements de stratégie. En raison de la conservation des scripts, l’équipe de gouvernance cloud est considérée comme une source d’accélération de l’adoption. Cela permet d’uniformiser les déploiements sans forcer l’adhésion de façon stricte.

**Formation technique :** L’équipe de gouvernance cloud propose des sessions de formation bimensuelles et a créé deux vidéos à l’intention des ingénieurs. Ces documents forment rapidement les ingénieurs à la culture de gouvernance et aux opérations réalisées pendant les déploiements. L’équipe ajoute des ressources de formation qui mettent en évidence entre les déploiements en production et les autres, afin que les ingénieurs comprennent l’impact des nouvelles stratégies sur l’adoption du cloud. Cela permet d’uniformiser les déploiements sans forcer l’adhésion de façon stricte.

**Planification du déploiement :** Avant de déployer toute ressource contenant des données protégées, l’équipe de gouvernance du cloud examine les scripts de déploiement pour valider l’adéquation de la ressource à la gouvernance. Les équipes existantes dont les déploiements ont déjà été approuvés feront l’objet d’un audit à l’aide d’outils de programmation.

**Audit et création de rapports mensuels :** Tous les mois, l’équipe de gouvernance cloud effectue un audit de tous les déploiements cloud afin de valider l’adéquation continue à la stratégie. Lorsque des écarts sont identifiés, ils sont documentés et partagés avec les équipes d’adoption du cloud. Lorsque l’implémentation ne risque pas d’entraîner une interruption des activités ou une fuite de données, les stratégies sont automatiquement implémentées. À la fin de l’audit, l’équipe de gouvernance cloud compile un rapport pour l’équipe de stratégie cloud et chaque équipe d’adoption du cloud, afin de communiquer sur l’adhésion générale des parties prenantes à la stratégie. Le rapport est également conservé à des fins d’audit et juridiques.

**Révision de la stratégie trimestrielle :** Chaque trimestre, l’équipe de gouvernance du cloud et l’équipe de stratégie cloud examinent les résultats de l’audit et proposent que des modifications soient apportées à la stratégie de l’entreprise. La plupart de ces suggestions sont le résultat d’améliorations continues et de l’observation des modèles d’utilisation. Les modifications de stratégie approuvées sont intégrées à l’outil de gouvernance au cours des cycles d’audit ultérieurs.

## <a name="alternative-patterns"></a>Autres modèles

Si l’un des modèles choisis dans ce guide de gouvernance ne correspond pas aux exigences du lecteur, chaque modèle possède une solution de rechange :

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

Les deux équipes utilisent les indicateurs de tolérance pour identifier le prochain groupe d’améliorations nécessaires à la poursuite de la prise en charge de l’adoption du cloud. Pour l’entreprise fictive dans ce guide, l’étape suivante consiste à améliorer la base de référence de sécurité en vue du transfert des données protégées vers le cloud.

> [!div class="nextstepaction"]
> [Améliorer la base référence de la sécurité](./security-baseline-improvement.md)
