---
title: Préparer une stratégie informatique d’entreprise pour le cloud
description: Permet d’activer un modèle de gouvernance étendu avec des activités clés telles que les changements incrémentiels de la stratégie d’entreprise et l’application automatisée.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 4bb736dc232ae4c1d1989da5c0b31c19e0c07672
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80356966"
---
<!-- markdownlint-disable MD026 -->

# <a name="prepare-corporate-it-policy-for-the-cloud"></a>Préparer une stratégie informatique d’entreprise pour le cloud

La gouvernance cloud est le fruit d’un travail d’adoption sur le long terme, car une vraie transformation durable ne se fait pas du jour au lendemain. Vous avez peu de chances d’obtenir des résultats satisfaisants si vous essayez de fournir une gouvernance cloud complète avant de prendre en charge les modifications clés de la stratégie d’entreprise, et si vous utilisez une méthode rapide et agressive. Nous vous recommandons plutôt d’opter pour une approche incrémentielle.

Ce qui est différent dans notre Framework d’adoption du cloud, c’est le cycle d’achat et sa capacité à réaliser une transformation authentique. Comme il n’existe pas d’obligation à acquérir des dépenses d’investissement importantes, les ingénieurs peuvent commencer plus tôt l’expérimentation et l’adoption. Dans la plupart des cultures d’entreprise, le fait de faire tomber cette barrière financière à l’adoption peut aboutir à des boucles de rétroaction plus courtes, une croissance naturelle et une exécution incrémentielle.

Le passage au cloud implique de changer la gouvernance. Dans beaucoup d’organisations, la transformation de la stratégie d’entreprise permet d’améliorer la gouvernance et d’augmenter les taux de conformité. Ces optimisations sont possibles grâce aux changements incrémentiels de stratégie et à l’application automatique de ces derniers. Pour ce faire, vous disposez de capacités nouvellement définies, que vous pouvez configurer avec votre fournisseur de services cloud.

Cet article décrit les principales activités qui peuvent vous aider à façonner vos stratégies d’entreprise, afin d’obtenir un modèle de gouvernance étendu.

## <a name="define-corporate-policy-to-mature-cloud-governance"></a>Définition de la stratégie d’entreprise pour faire évoluer la gouvernance cloud

Dans la gouvernance traditionnelle et incrémentielle, la stratégie d’entreprise crée la définition pratique de la gouvernance. La plupart des actions de gouvernance informatique cherchent à implémenter la technologie afin de superviser, appliquer, exécuter et automatiser ces stratégies d’entreprise. La gouvernance cloud s’appuie sur des concepts similaires.

![Gouvernance d’entreprise et disciplines de gouvernance](../../_images/operational-transformation-govern-highres.png)

*Figure 1 - Gouvernance d’entreprise et disciplines de gouvernance.*

L’image ci-dessus montre les interactions qu’il existe entre les risques métier, la stratégie, la conformité, la supervision et l’application afin de créer une stratégie de gouvernance. Ensuite, vous sont présentées les cinq disciplines de la gouvernance cloud pour élaborer votre stratégie.

## <a name="review-existing-policies"></a>Révision des stratégies existantes

Dans l’image ci-dessus, la stratégie de gouvernance (risque, stratégie et conformité, supervision et application) commence par l’identification des risques métier. La première étape pour créer une stratégie de gouvernance cloud durable consiste à comprendre en quoi les [risques métier](./business-risk.md) changent dans le cloud. En travaillant avec vos unités commerciales afin de [jauger précisément la tolérance de l’entreprise aux risques](./risk-tolerance.md), vous saurez quel niveau de risques doit être évité. Votre compréhension des nouveaux risques et de la tolérance acceptable peut vous permettre d’effectuer une [révision des stratégies existantes](./cloud-policy-review.md), et de déterminer le niveau de gouvernance requis pour votre organisation.

> [!TIP]
> Si votre organisation est soumise à une conformité tierce, un des plus gros risques métier à prendre en compte est l’adhésion à la [conformité réglementaire](./regulatory-compliance.md). Souvent, ce risque ne peut pas être évité et demande une adhésion stricte. Veillez à comprendre les exigences de conformité tierces avant de commencer une révision de la stratégie.

## <a name="an-incremental-approach-to-cloud-governance"></a>Approche incrémentielle de la gouvernance cloud

Une approche incrémentielle de la gouvernance cloud part du principe qu’il est inacceptable de dépasser le [seuil de tolérance aux risques de l’entreprise](./risk-tolerance.md). Pour elle, le rôle de la gouvernance est d’accélérer les changements de l’entreprise, d’aider les ingénieurs à comprendre les conseils d’architecture et de s’assurer que les [risques métier](./business-risk.md) sont régulièrement communiqués et évités. À l’inverse, le rôle traditionnel de la gouvernance peut devenir un obstacle à l’adoption par les ingénieurs ou par l’entreprise en général.

Avec l’approche incrémentielle de la gouvernance cloud, il existe parfois une opposition naturelle entre les équipes qui développent de nouvelles solutions métier et les équipes qui protègent l’entreprise des risques. Toutefois, dans ce modèle, les deux équipes peuvent devenir des pairs travaillant par incréments ou sprints. De cette manière, l’équipe de gouvernance cloud et les équipes d’adoption du cloud peuvent travailler ensemble à l’exposition, l’évaluation et l’élimination des risques métier. Grâce à cela, il est possible de réduire naturellement l’opposition entre les équipes et établir la collaboration.

## <a name="minimum-viable-product-mvp-for-policy"></a>Produit minimum viable (MVP) pour la stratégie

Pour faire émerger le partenariat entre l’équipe de gouvernance cloud et les équipes d’adoption du cloud, la première étape est un accord concernant le MVP de stratégie. Votre MVP de gouvernance cloud doit reconnaître que les risques métier sont faibles au début, mais vont probablement croître à mesure que votre organisation adopte plus de services cloud au fil du temps.

Par exemple, le risque métier est faible pour une entreprise de déployer cinq machines virtuelles qui ne contiennent aucune donnée HBI (High Business Impact). Plus tard dans le processus d’adoption, lorsque l’entreprise a atteint 1 000 machines virtuelles et qu’elle commence à déplacer les données HBI, le risque métier augmente.

Le MVP de stratégie tente de définir une base pour les stratégies nécessaires au déploiement de _x_ premières machines virtuelles ou le nombre _x_ d’applications, où _x_ est une petite mais significative quantité d’unités en cours d’adoption. Cette stratégie demande peu de contraintes, mais présente les aspects fondamentaux permettant de passer rapidement d’un effort d’adoption cloud incrémentiel au prochain. Grâce au développement incrémentiel de la stratégie, la gouvernance se développe au fil du temps. Grâce à des changements lents et subtils, le MVP de stratégie atteint la parité des fonctionnalités avec les résultats de l’exercice de révision de la stratégie.

## <a name="incremental-policy-growth"></a>Croissance incrémentielle de la stratégie

La croissance incrémentielle de la stratégie est le principal mécanisme permettant de faire évoluer la stratégie et la gouvernance cloud au fil du temps. Elle est également essentielle à l’adoption d’un modèle incrémentiel pour la gouvernance. Pour que ce modèle fonctionne bien, l’équipe de gouvernance doit s’engager à allouer du temps en continu à chaque sprint, de manière à évaluer et implémenter les disciplines de gouvernance changeantes.

**Exigences de temps pour les sprints :** Au début d’une itération, chaque équipe d’adoption du cloud dresse une liste des ressources à migrer ou adopter dans l’incrément actuel. L’équipe de gouvernance cloud est supposée laisser le temps nécessaire aux activités suivantes : examen de la liste, validation de la classification des données pour les ressources, évaluation des nouveaux risques associés à chaque ressource, mise à jour des consignes en matière d’architecture et explication des changements à l’équipe. Ces activités nécessitent en général entre 10 et 30 heures par sprint. Pour ce niveau d’implication, il est également préférable d’avoir au moins un employé dédié qui gère la gouvernance au sein du processus plus large d’adoption du cloud.

**Temps de mise en production requis :** Au début de chaque mise en production, les équipes d’adoption du cloud et l’équipe de stratégie cloud doivent classer par priorité une liste d’applications ou de charges de travail à migrer dans l’itération actuelle ainsi que les activités liées aux changements de l’entreprise. Ces points de données permettent à l’équipe de gouvernance cloud de comprendre très tôt les nouveaux risques métier. Grâce à cela, elle a le temps de s’aligner sur l’entreprise et de jauger la tolérance aux risques de l’entreprise.

## <a name="next-steps"></a>Étapes suivantes

Une stratégie de gouvernance cloud efficace commence par la compréhension des risques métier.

> [!div class="nextstepaction"]
> [Comprendre les risques métier](./business-risk.md)
