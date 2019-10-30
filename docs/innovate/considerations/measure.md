---
title: 'Innovation cloud : Measure'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduction à l’innovation cloud - Contenu sur la mesure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 00928171c3bfba1638a7e8e43ea08df4745754d2
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558435"
---
# <a name="measure-for-customer-impact"></a>Mesure de l’impact sur le client

Il existe plusieurs façons de mesurer l’impact sur le client. Cet article vous aide à définir les mesures vous permettant de valider les hypothèses que vous avez créées en [développant une solution en faisant preuve d’empathie vis-à-vis du client](./build.md).

## <a name="strategic-metrics"></a>Métriques stratégiques

Au cours de la [phase de stratégie](../../strategy/index.md) du cycle de vie de l’adoption du cloud, les lecteurs sont assistés dans la création et la documentation des [motivations](../../strategy/motivations.md) et des [résultats opérationnels](../../strategy/business-outcomes/index.md). Ces exercices offrent un ensemble de métriques à utiliser pour tester l’impact sur le client. Quand une innovation réussit, elle produit des résultats alignés sur les objectifs de la stratégie.

Avant d’établir des métriques d’apprentissage, définissez quelques métriques stratégiques que cette innovation est censée impacter. En général, ces métriques stratégiques s’alignent sur une ou plusieurs des catégories de résultats suivantes : [Agilité de l’entreprise](../../strategy/business-outcomes/agility-outcomes.md), [Engagement client](../../strategy/business-outcomes/engagement-outcomes.md), [Portée commerciale](../../strategy/business-outcomes/reach-outcomes.md), [Impact financier](../../strategy/business-outcomes/fiscal-outcomes.md) ou, dans le cas d’une innovation opérationnelle, [Performances de la solution](../../strategy/business-outcomes/fiscal-outcomes.md).

Documentez les métriques convenues et assurez un suivi régulier de l’impact. Toutefois, ne vous attendez pas à ce que l’une de ces métriques fasse émerger des résultats pour plusieurs itérations. Consultez [Engagement à l’itération](./index.md#commitment-to-iteration) pour aligner les attentes.

Au-delà des métriques relatives aux motivations et aux résultats opérationnels, cet article porte sur les métriques d’apprentissage conçues pour orienter la découverte transparente et les itérations axées sur le client. Consultez [Engagement à la transparence](./index.md#commitment-to-transparency) pour aligner les attentes.

## <a name="learning-metrics"></a>Métriques d’apprentissage

Quand la première version d’un produit minimum viable (MVP, minimum viable product), quel qu’il soit, est partagée avec les clients (de préférence à la fin de la première itération de développement), il n’y a aucun impact sur les métriques stratégiques. Après plusieurs itérations, l’équipe peut toujours éprouver des difficultés à changer suffisamment les comportements pour impacter les métriques stratégiques de façon significative. Pendant les processus d’apprentissage (par exemple, lors des cycles développer-mesurer-apprendre), il est recommandé à l’équipe d’adopter des métriques d’apprentissage. Il est plus simple de suivre ces métriques et d’en tirer parti dans le cadre d’opportunités d’apprentissage.

### <a name="customer-flow-and-learning-metrics"></a>Flux client et métriques d’apprentissage

Si une solution MVP valide une hypothèse axée sur le client, la solution entraîne des changements de comportement chez les clients. Ces comportements observés dans différentes cohortes de clients vont favoriser les résultats opérationnels. Heureusement, le changement de comportement des clients s’effectue souvent en plusieurs étapes. Chaque étape offre l’opportunité de mesurer l’impact, permettant à l’équipe d’adoption d’apprendre et de développer une meilleure solution.

Le processus d’apprentissage relatif aux changements de comportement des clients commence par la représentation du flux souhaité, créé par une solution MVP.

![Flux client utilisé pour déterminer les métriques d’apprentissage](../../_images/innovate/customer-flow-learning-metrics.png)

Dans la plupart des cas, un flux client possède un point de départ facilement défini et au maximum deux points de terminaison. Entre les points de départ et de terminaison, différentes métriques d’apprentissage sont utilisées comme mesures dans la boucle de rétroaction :

1. **Point de départ - déclencheur initial :** le point de départ représente le scénario qui déclenche le besoin vis-à-vis de cette solution. Quand cette solution est développée dans un esprit d’empathie vis-à-vis du client, ce déclencheur initial doit inciter un client à essayer la solution MVP.
2. **Besoin client satisfait :** l’hypothèse est validée quand la solution a répondu à un besoin du client.
3. **Étapes de la solution :** chaque étape nécessaire pour faire progresser le client du déclencheur initial jusqu’à un résultat satisfaisant est une étape de la solution. Chaque étape produit une métrique d’apprentissage basée sur la décision du client de passer à l’étape suivante.
4. **Adoption individuelle concrétisée :** quand le déclencheur se présente de nouveau, si le client choisit encore la solution pour satisfaire son besoin une nouvelle fois, l’adoption individuelle est concrétisée.
5. **Indicateur de résultat opérationnel :** quand un client se comporte d’une manière contribuant positivement au résultat opérationnel défini, un indicateur de résultat opérationnel est observé.
6. **Innovation réelle :** quand les « indicateurs de résultat opérationnel » et l’« adoption individuelle » sont observés à l’échelle souhaitée, une innovation réelle a été réalisée.

Chaque étape du flux client génère des métriques d’apprentissage. Après chaque itération (ou version), une nouvelle version de l’hypothèse est testée. Des ajustements de la solution sont également testés parallèlement pour refléter les ajustements de l’hypothèse. Quand les clients suivent la voie prescrite à une étape donnée, une métrique positive est enregistrée. Quand les clients s’écartent de la voie prescrite pour la satisfaction de leur besoin, une métrique négative est enregistrée.

Ces compteurs d’alignement et d’écart créent des métriques d’apprentissage. Chacune d’elles doit être enregistrée et suivie à mesure que l’équipe d’adoption du cloud progresse vers la réalisation des résultats opérationnels et de l’innovation réelle. L’article suivant, [Apprendre avec les clients](./learn.md), explique comment tirer parti de ces métriques pour apprendre et développer de meilleures solutions.

### <a name="grouping-and-observing-customer-partners"></a>Regroupement et observation des partenaires clients

La définition du partenaire client représente la première mesure définissant les métriques d’apprentissage. Tout client participant à des cycles d’innovation se qualifie comme partenaire client. Pour mesurer le comportement de façon précise, il est important de définir les partenaires clients dans un modèle de cohorte. Dans ce modèle, le regroupement des clients permet de mieux comprendre comment ils répondent à une modification du MVP, quelle qu’elle soit. Les partenaires clients sont généralement regroupés en fonction de points de données, par exemple :

- **Groupe d’expérimentation ou représentatif :** regroupement basé sur la participation de clients à une expérience spécifique pour tester les modifications au fil du temps.
- **Segment :** regroupement des clients selon la taille de l’entreprise.
- **Secteur :** regroupement des clients en fonction du secteur d’activité qu’ils représentent.
- **Données démographiques individuelles :** regroupement basé sur des données démographiques personnelles, telles que l’âge ou l’emplacement physique.

Ce type de regroupement permet de valider les métriques d’apprentissage sur plusieurs échantillons de clients vous choisissant comme partenaire pour leurs efforts d’innovation. Toutes les métriques suivantes doivent être observées selon un regroupement de clients définissable.

## <a name="next-steps"></a>Étapes suivantes

À mesure que les métriques de formation s’accumulent, l’équipe peut commencer à [apprendre avec les clients](./learn.md).

> [!div class="nextstepaction"]
> [Apprendre avec les clients](./learn.md)

Certains concepts de cet article s’appuient sur les sujets initialement abordés dans l’ouvrage [The Lean Startup](http://theleanstartup.com/book) d’Eric Ries.
