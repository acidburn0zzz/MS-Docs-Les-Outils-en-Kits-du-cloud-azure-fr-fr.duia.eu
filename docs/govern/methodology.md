---
title: Régit la méthodologie du cloud
description: Utilisez une approche de gouvernance incrémentielle basée sur un produit minimum viable (MVP) pour prendre en charge les stratégies d’entreprise et passer rapidement à l’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: d1cbf6c608bbea2374cb6325e755fc9367aedc03
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83399606"
---
# <a name="govern-methodology-for-the-cloud"></a>Régit la méthodologie du cloud

L’adoption du cloud est un cheminement, non un objectif. Ce parcours est jalonné d’étapes cruciales et d’avantages commerciaux tangibles. Toutefois, lorsqu’une entreprise entame son parcours d’adoption du cloud, elle sait rarement quel sera son état final. La gouvernance cloud permet de mettre en place un rail de sécurité pour l’entreprise tout au long de son parcours.

Le Framework d’adoption du cloud fournit des guides de gouvernance qui décrivent les expériences d’entreprises fictives, basées cependant sur les expériences de clients réels. Chaque guide suit le client dans les aspects qui touchent à la gouvernance du passage au cloud.

## <a name="envision-an-end-state"></a>Prévoir un état final

Lorsque la fin d’un parcours n’est pas définie, on parle d’errance. Il est important d’élaborer une vision globale de l’état final avant d’entreprendre la première étape. L’infographie suivante sert de référence pour ébaucher un état final. Il ne constitue pas votre point de départ, mais montre une destination potentielle.

![Infographie du modèle de gouvernance du Framework d’adoption du cloud (FAC)](../_images/operational-transformation-govern-large.png)

Le modèle de gouvernance du Framework d’adoption du cloud (FAC) identifie certains domaines clés tout au long du parcours. Chaque domaine est associé à différents types de risques que l’entreprise doit prendre en compte à mesure qu’elle adopte des services cloud. Dans ce framework, le guide de gouvernance identifie certaines actions requises de l’équipe de gouvernance cloud. Chaque principe du modèle de gouvernance du Framework d’adoption du cloud (FAC) est décrit plus en détail. En général, ils incluent les éléments suivants :

**Stratégies d’entreprise :** Les stratégies d’entreprises stimulent la gouvernance cloud. Le guide de gouvernance porte sur des aspects spécifiques de la stratégie d’entreprise :

- **Risques commerciaux :** Identification et compréhension des risques pour l’entreprise.
- **Stratégie et conformité :** Conversion des risques en instructions stratégiques intégrant des exigences de conformité.
- **Processus :** Respect des stratégies élaborées.

**Cinq disciplines de gouvernance cloud :** Ces disciplines soutiennent les stratégies d’entreprise. Chaque discipline protège l’entreprise contre certains pièges potentiels :

- Discipline Gestion des coûts
- Discipline Ligne de base de la sécurité
- Discipline Cohérence des ressources
- Discipline Ligne de base des identités
- Discipline Accélération du déploiement

Au fond, les stratégies d’entreprise font figure de système d’avertissement qui détecte les potentiels problèmes. Les disciplines aident l’entreprise à gérer les risques et forment une sorte de « glissière de sécurité ».

## <a name="grow-to-the-end-state"></a>Parvenir à l’état final

Comme les exigences de gouvernance changent tout au long du parcours d’adoption cloud, il est nécessaire d’adopter une approche différente face à la gouvernance. Les entreprises ne peuvent plus espérer qu’une petite équipe sécurise et jalonne chaque processus _avant de se lancer et de mettre en œuvre une première étape_. Des résultats commerciaux rapides et réguliers sont attendus. La gouvernance informatique doit également évoluer rapidement et suivre le rythme des exigences opérationnelles afin de rester pertinente lors du passage au cloud et d’éviter le phénomène « d’informatique fantôme ».

L’approche de **gouvernance incrémentielle** permet de prendre toute la mesure de ces caractéristiques. La gouvernance incrémentielle repose sur un petit ensemble de stratégies d’entreprise, de processus et d’outils qui visent à établir une base solide pour le passage au cloud et sa gouvernance. Cette base est appelée un **produit minimum viable** (MVP, minimum viable product). Grâce au produit minimum viable, l’équipe responsable peut intégrer rapidement la gouvernance aux implémentations tout au long du cycle d’adoption du cloud. Un produit minimum viable peut être établi à tout moment pendant ce processus. Toutefois, il est conseillé d’adopter un produit minimum viable (MVP) le plus tôt possible.

Quand elle est capable de répondre rapidement à l’évolution des risques, l’équipe de gouvernance cloud peut alors s’impliquer dans d’autres domaines. L’équipe de gouvernance cloud peut jouer le rôle d’éclaireur auprès de l’équipe de stratégie cloud, en devançant les équipes chargées de l’adoption du cloud et en s’éloignant des sentiers battus, afin de mettre rapidement en place des mesures de sécurité permettant de gérer les risques associés aux plans d’adoption. Ces couches de gouvernance juste-à-temps sont des **itérations de gouvernance**. Grâce à cette approche, la stratégie de gouvernance prend une longueur d’avance sur les équipes chargées de l’adoption du cloud.

Le diagramme suivant illustre un MVP de gouvernance simple et trois itérations de gouvernance. Au cours des itérations, des stratégies d’entreprise supplémentaires sont définies afin de gérer les nouveaux risques. La discipline Accélération du déploiement applique ensuite ces modifications à chaque déploiement.

![Exemple d’amélioration incrémentielle de la gouvernance](../_images/govern/incremental-governance-example.png)

> [!NOTE]
> La gouvernance ne remplace pas les fonctions clés telles que la sécurité, la mise en réseau, l’identité, la finance, le DevOps ou les opérations. Tout au long du processus, les interactions et dépendances avec les membres de chaque fonction sont nombreuses. Ces membres doivent être inclus dans l’équipe de gouvernance coud afin d’accélérer la prise de décisions et la mise en œuvre d’actions.

## <a name="next-steps"></a>Étapes suivantes

Utilisez l’[outil de benchmark de gouvernance](https://cafbaseline.com) du Framework d’adoption du cloud pour évaluer votre parcours de transformation et identifier les lacunes de votre organisation parmi les six domaines clés tels que définis dans le framework.

> [!div class="nextstepaction"]
> [Évaluez votre parcours de transformation](./benchmark.md)
