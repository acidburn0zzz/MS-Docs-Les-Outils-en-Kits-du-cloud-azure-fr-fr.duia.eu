---
title: Définir la stratégie de l’entreprise en matière de gouvernance cloud
description: Découvrez comment établir une stratégie pour refléter et corriger les risques.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 92c04d53e59d8876291794c5da74104ec62412a9
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806048"
---
# <a name="define-corporate-policy-for-cloud-governance"></a>Définir la stratégie de l’entreprise en matière de gouvernance cloud

Lorsque vous avez analysé les risques connus et les tolérances aux risques connexes pour le processus de transformation cloud de votre entreprise, la prochaine étape consiste à établir une stratégie qui aborde explicitement ces risques et à définir les étapes nécessaires pour les corriger dans la mesure du possible.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-corporate-it-policy-become-cloud-ready"></a>Comment la politique informatique de l’entreprise peut devenir prête pour le cloud ?

Dans la gouvernance traditionnelle et incrémentielle, la stratégie d’entreprise crée la définition pratique de la gouvernance. La plupart des actions de gouvernance informatique cherchent à implémenter la technologie afin de superviser, appliquer, exécuter et automatiser ces stratégies d’entreprise. La gouvernance cloud s’appuie sur des concepts similaires.

![Gouvernance d’entreprise et disciplines de gouvernance](../../_images/operational-transformation-govern-highres.png)

*Figure 1 - Gouvernance d’entreprise et disciplines de gouvernance.*

L’image ci-dessus illustre la relation entre les risques métiers, la stratégie et la conformité, ainsi que les mécanismes de surveillance et d’application qui doivent interagir dans le cadre de votre stratégie de gouvernance. Les cinq disciplines de la gouvernance cloud vous permettent de gérer ces interactions et d’élaborer votre stratégie.

La gouvernance cloud est le fruit d’un travail d’adoption sur le long terme, car une vraie transformation durable ne se fait pas du jour au lendemain. Vous avez peu de chances d’obtenir des résultats satisfaisants si vous essayez de fournir une gouvernance cloud complète avant de prendre en charge les modifications clés de la stratégie d’entreprise, et si vous utilisez une méthode rapide et agressive. Nous vous recommandons plutôt d’opter pour une approche incrémentielle.

Ce qui est différent dans notre Framework d’adoption du cloud, c’est le cycle d’achat et sa capacité à réaliser une transformation authentique. Comme il n’existe pas d’obligation à acquérir des dépenses d’investissement importantes, les ingénieurs peuvent commencer plus tôt l’expérimentation et l’adoption. Dans la plupart des cultures d’entreprise, le fait de faire tomber cette barrière financière à l’adoption peut aboutir à des boucles de rétroaction plus courtes, une croissance naturelle et une exécution incrémentielle.

Le passage au cloud implique de changer la gouvernance. Dans beaucoup d’organisations, la transformation de la stratégie d’entreprise permet d’améliorer la gouvernance et d’augmenter les taux de conformité. Ces optimisations sont possibles grâce aux changements incrémentiels de stratégie et à l’application automatique de ces derniers. Pour ce faire, vous disposez de capacités nouvellement définies, que vous pouvez configurer avec votre fournisseur de services cloud.

<!-- markdownlint-enable MD026 -->

## <a name="review-existing-policies"></a>Révision des stratégies existantes

La gouvernance est un processus continu. Vous devez régulièrement examiner votre stratégie avec le personnel de votre service informatique et vos parties prenantes pour vous assurer que les ressources hébergées dans le cloud continuent de respecter les objectifs et les exigences généraux de votre entreprise. Votre compréhension des nouveaux risques et de la tolérance acceptable peut vous permettre d’effectuer une [révision des stratégies existantes](./cloud-policy-review.md), et de déterminer le niveau de gouvernance requis pour votre organisation.

> [!TIP]
> Si votre organisation utilise des fournisseurs ou d’autres partenaires commerciaux approuvés, l’un des plus grands risques métier à prendre en compte peut être un manque de [respect de la réglementation](./regulatory-compliance.md) par ces organisations externes. Souvent, ce risque ne peut pas être évité et demande une adhésion stricte aux exigences de la part de toutes les parties. Veillez à identifier et comprendre les exigences de conformité tierces avant de commencer une révision de la stratégie.

## <a name="create-cloud-policy-statements"></a>Créer des instructions de stratégie cloud

Les stratégies d’informatique cloud établissent des exigences, des normes et des objectifs que le personnel de votre service informatique et vos systèmes automatisés devront prendre en charge. Les décisions de cette stratégie constituent un facteur primordial dans la conception de votre [architecture cloud](./governance-alignment.md) et la façon dont vous mettrez en œuvre les [processus d’adhésion à votre stratégie](./processes.md).

Les instructions de stratégie cloud individuelles sont des recommandations destinées à traiter des risques spécifiques identifiés lors de votre processus d’évaluation des risques. Bien que ces stratégies puissent être intégrées dans la documentation de votre stratégie d’entreprise générale, les énoncés de la stratégie cloud dont il est question dans les lignes directrices du Framework d’adoption du cloud constituent davantage un résumé des risques et des plans pour y faire face. Chaque définition doit inclure les informations suivantes :

- **Risque métier :** un récapitulatif du risque que cette stratégie gérera.
- **Instruction de stratégie :** une explication succincte claire des exigences de la stratégie.
- **Conseils techniques ou de conception** : suggestions, spécifications ou autres conseils pratiques pour prendre en charge et appliquer cette stratégie que les équipes informatiques et les développeurs peuvent utiliser lors de la conception et de la construction de leurs déploiements cloud.

Si vous avez besoin d’aide pour commencer à définir des stratégies, consultez les [disciplines de gouvernance](../governance-disciplines.md)présentées dans l’aperçu de la section gouvernance. Les articles pour chacune de ces disciplines comprennent des exemples de risques métiers communs rencontrés lors de la migration vers le cloud et des exemples de stratégies utilisées pour corriger ces risques (par exemple, consultez les [exemples de définitions de stratégies](../cost-management/policy-statements.md) de la discipline Gestion des coûts).

## <a name="incremental-governance-and-integrating-with-existing-policy"></a>Gouvernance progressive et intégration à la stratégie existante

Les ajouts planifiés à votre environnement de cloud computing doivent toujours être vérifiés pour s’assurer de leur conformité à la stratégie existante, et la stratégie doit être mise à jour pour tenir compte de tous les problèmes qui ne sont pas déjà couverts. Vous devez également effectuer une [révision régulière de la stratégie cloud](./cloud-policy-review.md) pour vous assurer que votre stratégie de cloud est à jour et synchronisée avec toute nouvelle stratégie d’entreprise.

La nécessité d’intégrer la stratégie de cloud à vos stratégies informatiques existantes dépend largement de la maturité de vos processus de gouvernance du cloud et de la taille de votre patrimoine cloud. Voir l’article sur [la gouvernance incrémentale et le MVP](./index.md) de la stratégie pour une discussion plus large sur l’intégration des stratégies pendant la transformation de votre cloud.

## <a name="next-steps"></a>Étapes suivantes

Après avoir défini vos stratégies, rédigez un guide de conception d’architecture pour fournir au personnel informatique et aux développeurs des conseils pratiques.

> [!div class="nextstepaction"]
> [Aligner votre guide de conception de gouvernance sur la stratégie d’entreprise](./governance-alignment.md)
