---
title: Comprendre le risque opérationnel pendant la migration cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Comprendre le risque opérationnel pendant la migration cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 078ba561384c07cee6ce3a174d1663f7590e228c
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71220399"
---
<!-- markdownlint-disable MD026 -->

# <a name="understand-business-risk-during-cloud-migration"></a>Comprendre le risque opérationnel pendant la migration cloud

Une bonne compréhension du risque métier est l’un des éléments les plus importants de toute transformation cloud. Le risque entraîne une stratégie, et il influence la supervision et l’application des exigences. Le risque influence fortement la façon dont nous gérons le patrimoine numérique, localement ou dans le cloud.

<!-- markdownlint-enable MD026 -->

## <a name="relativity-of-risk"></a>Relativité du risque

Le risque est relatif. Une petite entreprise disposant de quelques ressources informatiques dans un bâtiment fermé est à faible risque. L’ajout d’utilisateurs et d’une connexion Internet avec un accès à ces ressources accroît le risque. Quand cette petite entreprise se développe au point de figurer dans le classement Fortune 500, les risques augmentent de manière exponentielle. À mesure que le chiffre d’affaires, les processus métier, les nombres d’employés et les ressources informatiques s’accumulent, les risques s’accroissent et fusionnent. Les ressources informatiques qui favorisent la génération de revenus sont exposées à un risque tangible d’arrêt de cette source de revenus en cas de panne. Chaque moment d’arrêt se traduit par des pertes. De même, à mesure que les données s’accumulent, le risque de préjudice pour les clients augmente.

Dans le monde local traditionnel, les équipes de gouvernance informatique se concentrent sur l’évaluation des risques, la création de processus permettant de gérer ces risques et le déploiement de systèmes permettant de s’assurer que les mesures de correction sont correctement mises en œuvre. Ces efforts contribuent à équilibrer les risques nécessaires pour opérer dans un environnement professionnel moderne et connecté.

## <a name="understand-business-risks-in-the-cloud"></a>Comprendre les risques commerciaux dans le cloud

Lors d’une transformation, les mêmes risques relatifs existent.

- Pendant une expérimentation anticipée, quelques ressources sont déployées avec peu ou pas de données pertinentes. Le risque est faible.
- Quand la première charge de travail est déployée, le risque augmente un peu. Ce risque est facilement corrigé en choisissant une application à faible risque par nature avec une base d’utilisateurs réduite.
- À mesure que le nombre de charges de travail mises en ligne augmente, les risques changent à chaque mise en production. La publication de nouvelles applications fait évoluer les risques.
- Quand une entreprise met en ligne les 10 à 20 premières applications, le profil de risque est très différent de celui de la mise en production de la 1 000ème application dans le cloud.

L’accumulation des ressources dans le patrimoine local traditionnel s’est probablement effectuée au fil du temps. La maturité des équipes commerciales et informatiques se développait vraisemblablement de la même manière. Cette croissance parallèle peut avoir tendance à créer un bagage de stratégies inutiles.

Lors d’une transformation cloud, les équipes commerciales et informatiques ont toutes les deux la possibilité de réinitialiser ces stratégies et d’en générer de nouvelles avec un esprit évolué.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-a-business-risk-mvp"></a>Qu’est un MVP de risque métier ?

Un **produit minimum viable** est couramment utilisé pour définir la plus petite unité de quelque chose qui peut produire une valeur tangible. Dans un MVP de risque professionnel, l’équipe de gouvernance cloud part du principe que certaines ressources seront déployées dans un environnement cloud à un moment donné. La nature de ces ressources est inconnue à ce moment-là et l’équipe n’est peut-être pas sûre des types de données qui seront stockés dans ces ressources.

Lors de la planification du risque professionnel, l’équipe de gouvernance cloud pourrait générer le scénario le plus défavorable en mappant chaque stratégie possible au cloud. Toutefois, l’identification de tous les risques commerciaux potentiels pour tous les scénarios d’utilisation du cloud peut prendre beaucoup de temps et de travail, ce qui peut retarder l’implémentation de la gouvernance dans vos charges de travail cloud. Cela n’est pas conseillé, mais c’est une option.

À l’inverse, une approche de MVP peut permettre à l’équipe de définir un point de départ initial et un ensemble d’hypothèses qui seraient vraies pour la plupart/la totalité des ressources. Ce MVP de risque professionnel prend en charge les déploiements de petite échelle ou de test cloud initiaux, puis sert de base pour identifier et corriger progressivement les nouveaux risques à mesure que des besoins métier surviennent ou que des charges de travail supplémentaires sont ajoutées à votre environnement cloud. Ce processus vous permet d’appliquer la gouvernance tout au long du processus d’adoption du cloud.

Voici quelques exemples de base de risques professionnels qui peuvent être inclus dans le cadre d’un MVP :

- Toutes les ressources sont exposées à un risque de suppression (à la suite d’une erreur, d’une méprise ou d’une opération de maintenance).
- Toutes les ressources sont exposées au risque de générer trop de dépenses.
- Toutes les ressources pourraient être compromises par des mots de passe faibles ou des paramètres non sécurisés.
- Toute ressource dont les ports ouverts sont exposés à Internet court un risque de compromission.

Les exemples ci-dessus sont destinés à établir les risques métier de MVP comme une théorie. La liste réelle sera propre à chaque environnement.
Une fois les MVP de risque professionnel établis, ils peuvent être convertis en [stratégies](./index.md) afin de corriger chaque risque.

<!-- markdownlint-enable MD026 -->

## <a name="incremental-risk-mitigation"></a>Atténuation incrémentielle des risques

À mesure que votre organisation déploie plus de charges de travail dans le cloud, les équipes de développement utilisent de plus en plus de ressources cloud. À chaque itération, de nouvelles ressources sont crées et envoyées en préproduction. À chaque mise en production, les charges de travail sont préparées pour la promotion vers la production. Chacun de ces cycles a le potentiel d’introduire des risques professionnels précédemment non identifiés.

En supposant qu’un MVP de risques professionnel est le point de départ de vos efforts initiaux d’adoption du cloud, la gouvernance peut évoluer en parallèle avec votre utilisation croissante des ressources cloud. Lorsque l’équipe de gouvernance cloud travaille en parallèle avec les équipes d’adoption du cloud, la croissance des risques professionnels peut être traitée à mesure qu’ils sont identifiés, fournissant ainsi un modèle permanent et stable pour le développement de la maturité de la gouvernance.

Chaque ressource en préproduction peut facilement être classée en fonction du risque. Les documents de classification des données peuvent être générés ou créés en parallèle avec les cycles de préproduction. Le profil de risque et les points d’exposition peuvent également être documentés. Au fil du temps, une vision très claire du risque professionnel se précisera dans l’organisation.

Avec chaque itération, l’équipe de gouvernance cloud peut travailler avec l’équipe de stratégie cloud pour communiquer rapidement les nouveaux risques, les stratégies d’atténuation, les compromis et les coûts potentiels. Cette option permet aux participants de l’entreprise et aux responsables informatiques d’être partenaires dans des décisions éclairées et matures. Ces décisions informent alors sur la maturité de la stratégie. Si nécessaire, les changements de stratégie produisent de nouveaux éléments de travail pour la maturité de systèmes d’infrastructure centrale. Quand il est nécessaire d’apporter des changements à des systèmes en préproduction, les équipes d’adoption du cloud ont suffisamment de temps pour cette opération, pendant que l’entreprise teste les systèmes en préproduction et développe un plan d’adoption par les utilisateurs.

Cette approche limite les risques, tout en permettant à l’équipe de migrer rapidement. Elle garantit également que les risques sont pris en compte et résolus rapidement avant le déploiement.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment évaluer la tolérance au risque pendant l’adoption du cloud.

> [!div class="nextstepaction"]
> [Évaluer la tolérance au risque](./risk-tolerance.md)
