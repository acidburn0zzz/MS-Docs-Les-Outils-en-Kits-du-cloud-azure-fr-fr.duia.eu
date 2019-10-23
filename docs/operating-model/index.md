---
title: Introduction au modèle d’exploitation
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez le modèle de fonctionnement du Framework d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.custom: operating-model
ms.openlocfilehash: 77e3ded1f76b096655a7831bc1950bf28bd4c86b
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683810"
---
# <a name="establish-an-operating-model-for-the-cloud"></a>Établir un modèle de fonctionnement pour le cloud

L’adoption du cloud est un effort itératif qui se concentre sur ce que vous faites dans le cloud. La stratégie cloud décrit la transformation numérique pour guider les programmes métier, plusieurs équipes exécutant les projets d’adoption. La planification et la préparation aident à garantir le succès de chacun de ces éléments importants. Toutes les étapes de l’adoption du cloud sont comparables à des projets tangibles avec des objectifs, des calendriers et des budgets gérables.

Ces efforts d’adoption sont relativement faciles à suivre et à mesurer, même quand ils impliquent plusieurs versions et itérations projetées. Chaque phase du cycle de vie d’adoption est importante. Chaque phase est sujette à des obstacles potentiels au niveau de l’entreprise, de la culture et des contraintes technologiques. Toutefois, chaque phase dépend fortement du modèle de fonctionnement sous-jacent.

**Si l’adoption décrit ce que vous effectuez, le modèle de fonctionnement définit les acteurs et modalités sous-jacents favorisant l’adoption.**

Selon Satya Nadella, **« la culture mange la stratégie pour le petit déjeuner »** . Le modèle de fonctionnement est l’incarnation de la culture informatique, capturée dans de nombreux processus mesurables. Quand le cloud repose sur un modèle de fonctionnement fort, la culture conduit à la stratégie, accélérant l’adoption et la réalisation des valeurs métier. À l’inverse, quand l’adoption réussit mais qu’il n’existe aucun modèle de fonctionnement, les retours peuvent être impressionnants mais de très courte durée. Pour une réussite à long terme, il est vital que l’adoption et les modèles de fonctionnement progressent en parallèle.

## <a name="establish-your-operating-model"></a>Établir votre modèle de fonctionnement

Les modèles de fonctionnement actuels peuvent évoluer afin de prendre en charge l’adoption du cloud. Un modèle de fonctionnement moderne vous aidera à éliminer les blocages non techniques à l’adoption du cloud.

Cette section du Framework d’adoption du cloud fournit un modèle de fonctionnement exploitable afin de guider les décisions non techniques. Ce modèle de fonctionnement se compose de trois méthodologies qui aident à la création de votre propre modèle de fonctionnement du cloud :

- [Gouverner](../govern/index.md) : garantir la cohérence parmi les efforts d’adoption. S’aligner sur les besoins de gouvernance ou de conformité afin de maintenir un environnement intercloud bien géré.
- [Gérer](../manage/index.md) : Aligner les processus en cours pour la gestion opérationnelle de la technologie afin d’optimiser la réalisation de la valeur et de réduire les disruptions.
- [Organiser](../organize/index.md) : à mesure que le modèle de fonctionnement murit, il en va de même de l’organisation des différentes équipes et fonctionnalités qui le prennent en charge.

## <a name="aligning-operating-models"></a>Alignement des modèles de fonctionnement

Le cloud et l’économie numérique ont révélé la nécessité de disposer de plusieurs modèles de fonctionnement. Parfois, c’est une exigence de prise en charge de plusieurs clouds publics qui dicte ce besoin. Plus généralement, le besoin est mis en évidence par le passage d’un environnement local au cloud. Dans les deux scénarios, il est important d’aligner les modèles de fonctionnement pour optimiser les performances et réduire la redondance au minimum.

Les analystes prévoient l’adoption multicloud à des volumes élevés. De nombreux clients font leur cette prédiction. Malheureusement, les clients signalent des défis importants concernant l’exploitation de plusieurs clouds. La duplication des ressources, processus, compétences et technologies engendre une augmentation des coûts, au lieu des économies que laissait entrevoir le cloud. Pour éviter cette tendance, les clients sont invités à adopter un modèle de fonctionnement spécialisé. Quand vous alignez des modèles de fonctionnement, il doit toujours y avoir un **modèle de fonctionnement général**. Les **modèles de fonctionnement spécialisés** supplémentaires seraient exploités pour des scénarios spécifiques afin de prendre en charge des écarts par rapport au modèle standard.

- **Modèle de fonctionnement général :** Le modèle de fonctionnement général s’aligne sur une plateforme cloud publique ou privée unique. Les opérations de cette plateforme définissent les standards, stratégies et processus opérationnels. Ce modèle de fonctionnement doit être le principal moyen d’alimenter la stratégie cloud de mise en œuvre. Dans ce modèle, l’objectif est de tirer parti du fournisseur de cloud principal pour la majeure partie de l’adoption du cloud.

- **Modèle de fonctionnement spécialisé :** Les résultats métier spécifiques peuvent être mieux adaptés à un autre fournisseur de cloud. En présence d’un cas métier attrayant, les standards, stratégies et processus issus du modèle de fonctionnement général sont appliqués au nouveau fournisseur de cloud, mais sont ensuite modifiés pour s’adapter au cas d’usage spécialisé.

Si Azure est la principale plateforme de choix, les guides et les bonnes pratiques indiquées dans chacune des sections du modèle de fonctionnement mentionnées ci-dessus s’avèreront utiles pour la création de votre modèle de fonctionnement. Toutefois, ce framework reconnaît que tous nos lecteurs n’ont pas adopté Azure comme plateforme principale. Pour tenir compte de ce public plus large, vous pouvez appliquer le contenu théorique de chaque section à des modèles de fonctionnement de cloud public ou privé avec des résultats similaires.

## <a name="next-steps"></a>Étapes suivantes

La gouvernance est une première étape commune vers l’établissement d’un modèle de fonctionnement pour le cloud.

> [!div class="nextstepaction"]
> [Découvrir la gouvernance cloud](../govern/index.md)
