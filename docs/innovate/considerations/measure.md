---
title: Mesurer l’impact sur le client
description: Définissez le flux client souhaité et établissez des métriques d’apprentissage de façon à mesurer le comportement et l’adoption du client.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: bb7399f6c937ed433d4d8610a15153c10f01659c
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83222502"
---
# <a name="measure-for-customer-impact"></a>Mesure de l’impact sur le client

Il existe plusieurs façons de mesurer l’impact sur le client. Cet article doit vous aider à définir des mesures afin de valider des hypothèses qui résultent d’un effort pour [Développer en faisant preuve d’empathie vis-à-vis du client](./build.md).

## <a name="strategic-metrics"></a>Métriques stratégiques

Au cours de la [phase de stratégie](../../strategy/index.md) du cycle de vie de l’adoption du cloud, nous examinons les [motivations](../../strategy/motivations.md) et les [résultats opérationnels](../../strategy/business-outcomes/index.md). Ces pratiques fournissent un ensemble de métriques permettant de tester l’impact sur les clients. Lorsque l’innovation est réussie, vous avez tendance à voir les résultats alignés sur vos objectifs stratégiques.

Avant d’établir des métriques d’apprentissage, définissez quelques métriques stratégiques qui doivent être impactées par cette innovation. En général, ces métriques stratégiques s’alignent sur une ou plusieurs des catégories de résultats suivantes :
    - [Agilité de l’entreprise](../../strategy/business-outcomes/agility-outcomes.md)
    - [Engagement client](../../strategy/business-outcomes/engagement-outcomes.md)
    - [Portée du client](../../strategy/business-outcomes/reach-outcomes.md)
    - [Impact financier](../../strategy/business-outcomes/fiscal-outcomes.md)
    - [Performances de la solution](../../strategy/business-outcomes/fiscal-outcomes.md), dans le cas de l’innovation opérationnelle.

Documentez les métriques convenues et assurez un suivi régulier de leur impact. Toutefois, ne vous attendez pas à ce que l’une de ces métriques fasse émerger des résultats pour plusieurs itérations. Pour plus d’informations sur le paramétrage et sur l’alignement des attentes sur les parties impliquées, consultez [Engagement à l’itération](./index.md#commitment-to-iteration).

Au-delà des métriques relatives aux motivations et aux résultats opérationnels, cet article porte sur les métriques d’apprentissage conçues pour orienter la découverte transparente et les itérations axées sur le client. Pour plus d’informations sur ces aspects, consultez [Engagement pour la transparence](./index.md#commitment-to-transparency).

## <a name="learning-metrics"></a>Métriques d’apprentissage

Quand la première version d’un produit minimum viable (MVP, minimum viable product), quel qu’il soit, est partagée avec les clients (de préférence à la fin de la première itération de développement), il n’y a aucun impact sur les métriques stratégiques. Après plusieurs itérations, l’équipe peut toujours éprouver des difficultés à changer suffisamment de comportements pour affecter sensiblement les métriques stratégiques. Pendant les processus d’apprentissage (par exemple, lors des cycles développer-mesurer-apprendre), nous recommandons que l’équipe adopte des métriques d’apprentissage. Ces métriques de suivi et ces opportunités d’apprentissage.

### <a name="customer-flow-and-learning-metrics"></a>Flux client et métriques d’apprentissage

Si une solution MVP valide une hypothèse axée sur le client, la solution entraîne des changements de comportement chez les clients. Ces changements de comportement dans les cohortes des clients devraient améliorer les résultats opérationnels. Gardez à l’esprit que la modification du comportement des clients est généralement un processus en plusieurs étapes. Comme chaque étape offre l’opportunité de mesurer l’impact, l’équipe d’adoption peut apprendre constamment et développer une meilleure solution.

Le processus d’apprentissage relatif aux changements de comportement des clients commence par le mappage du flux souhaité par une solution MVP.

![Flux client utilisé pour déterminer les métriques d’apprentissage](../../_images/innovate/customer-flow-learning-metrics.png)

Dans la plupart des cas, un flux client possède un point de départ facilement défini et au maximum deux points de terminaison. Entre les points de départ et de terminaison, différentes métriques d’apprentissage sont utilisées comme mesures dans la boucle de rétroaction :

1. **Point de départ – déclencheur initial :** le point de départ est le scénario qui déclenche la nécessité de cette solution. Quand cette solution est développée dans un esprit d’empathie vis-à-vis du client, ce déclencheur initial doit inciter un client à essayer la solution MVP.
2. **Besoin client satisfait :** l’hypothèse est validée quand la solution a répondu à un besoin du client.
3. **Étapes de la solution :** ce terme désigne les étapes nécessaires pour faire passer le client du déclencheur initial à un résultat satisfaisant. Chaque étape produit une métrique d’apprentissage basée sur la décision du client de passer à l’étape suivante.
4. **Adoption individuelle concrétisée :** quand le déclencheur se présente de nouveau, si le client choisit encore la solution répondant à ses besoins, l’adoption individuelle est concrétisée.
5. **Indicateur de résultat opérationnel :** quand un client se comporte d’une manière contribuant au résultat opérationnel défini, un indicateur de résultat opérationnel est observé.
6. **Innovation réelle :** quand les _indicateurs de résultats opérationnels_ et l’_adoption individuelle_ sont observés à l’échelle souhaitée, vous avez réalisé une véritable innovation.

Chaque étape du flux client génère des métriques d’apprentissage. Après chaque itération (ou version), une nouvelle version de l’hypothèse est testée. Des ajustements de la solution sont également testés parallèlement pour refléter les ajustements de l’hypothèse. Quand les clients suivent la voie prescrite à une étape donnée, une métrique positive est enregistrée. Quand les clients s’écartent de la voie prescrite, une métrique négative est enregistrée.

Ces compteurs d’alignement et d’écart créent des métriques d’apprentissage. Chacune d’elles doit être enregistrée et suivie à mesure que l’équipe d’adoption du cloud progresse vers les résultats opérationnels et l’innovation réelle. Dans [Apprendre avec les clients](./learn.md), nous allons évoquer comment appliquer ces métriques pour apprendre et développer de meilleures solutions.

### <a name="group-and-observe-customer-partners"></a>Regrouper et observer les partenaires clients

La définition du partenaire client représente la première mesure définissant les métriques d’apprentissage. Tout client qui participe à des cycles d’innovation se qualifie comme partenaire client. Pour mesurer le comportement de façon précise, vous devez utiliser un modèle de cohorte pour définir les partenaires clients. Dans ce modèle, les clients sont regroupés pour aiguiser la compréhension de leurs réponses aux modifications du MVP. Ces groupes ressemblent généralement à ce qui suit :

- **Groupe d’expérimentation ou représentatif :** regroupement de clients sur la base de leur participation à une expérience spécifique pour tester les modifications au fil du temps.
- **Segment :** regroupement des clients selon la taille de l’entreprise.
- **Secteur :** regroupement des clients en fonction du _secteur d’activité_ qu’ils représentent.
- **Données démographiques individuelles :** regroupement basé sur des données démographiques personnelles, telles que l’âge et l’emplacement physique.

Ces types de regroupements vous aident à valider les métriques d’apprentissage sur plusieurs échantillons de clients vous choisissant comme partenaire pendant vos efforts d’innovation. Toutes les métriques suivantes doivent être dérivées du regroupement de clients définissable.

## <a name="next-steps"></a>Étapes suivantes

À mesure que les métriques de formation s’accumulent, l’équipe peut commencer à [apprendre avec les clients](./learn.md).

> [!div class="nextstepaction"]
> [Apprendre avec les clients](./learn.md)

<!-- cSpell:ignore Ries -->

Certains concepts de cet article s’appuient sur les sujets initialement abordés dans l’ouvrage [The Lean Startup](http://theleanstartup.com/book) d’Eric Ries.
