---
title: Aligner les efforts sur les métriques d’apprentissage
description: Découvrez comment ajuster les efforts pour mesurer et communiquer l’impact d’une transformation sur l’entreprise.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: b7a6081f37899f11716eca07b7e6a371bcefcc94
ms.sourcegitcommit: 26caeb6b7f4e14df30bf16727d0b1b3d63b9c0c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78337892"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-can-we-align-efforts-to-meaningful-learning-metrics"></a>Comment aligner les efforts sur des métriques d’apprentissage explicites ?

La [vue d’ensemble des résultats métier](./business-outcomes/index.md) a expliqué comment mesurer et communiquer l’impact qu’une transformation aura sur l’entreprise. Malheureusement, il peut se passer des années avant que certains de ces résultats produisent des résultats mesurables. Le conseil d’administration et la direction ne sont pas satisfaits par des rapports qui affichent un delta de 0 % pendant de longues périodes.

Les métriques d’apprentissage sont des métriques provisoires et à plus court terme qui peuvent être liées à des résultats métiers à plus long terme. Ces métriques s’alignent bien sur une volonté de croissance et aident à positionner la culture de manière à ce qu’elle devienne plus résiliente. Au lieu de mettre en évidence l’absence prévue de progression vers un objectif métier à long terme, les métriques d’apprentissage mettent en évidence les premiers indicateurs de réussite. Les métriques surveillent également les premiers indicateurs de défaillance, susceptibles de produire la plus grande opportunité de tirer des enseignements et d’ajuster le plan.

Comme avec la plupart des éléments de ce Framework, nous supposons que vous êtes familiarisé avec le [parcours de transformation](../govern/guides/index.md) qui est le mieux adapté aux résultats métiers souhaités. Cet article présente quelques métriques d’apprentissage pour chaque parcours de transformation, afin d’illustrer le concept.

## <a name="cloud-migration"></a>Migration cloud

Cette transformation est axée sur le coût, la complexité et l’efficacité, en mettant l’accent sur les opérations informatiques. Les données les plus facilement mesurées derrière cette transformation sont le déplacement des ressources vers le cloud. Dans ce type de transformation, le patrimoine numérique est mesuré par des machines virtuelles, des racks ou des clusters qui hébergent ces machines virtuelles, des coûts opérationnels de centre de données, des dépenses d’investissement requises pour maintenir les systèmes et l’amortissement de ces ressources dans le temps.

À mesure que les machines virtuelles sont déplacées vers le cloud, la dépendance vis-à-vis des ressources héritées locales est réduite. Le coût de la maintenance des ressources est également réduit. Malheureusement, les entreprises ne peuvent pas bénéficier d’une réduction des coûts tant que les clusters ne sont pas mis hors service et que les baux de centres de données n’ont pas expiré. Dans de nombreux cas, la valeur totale de l’effort n’est pas réalisée tant que les cycles de dépréciation ne sont pas terminés.

Consultez toujours le directeur financier ou le bureau des finances avant de créer des relevés financiers. Toutefois, les équipes informatiques peuvent généralement estimer les coûts monétaires actuels et les coûts monétaires futurs pour chaque machine virtuelle en fonction du processeur, de la mémoire et du stockage consommé. Vous pouvez ensuite appliquer cette valeur à chaque machine virtuelle migrée pour estimer les économies immédiates et la valeur monétaire future de l’effort.

## <a name="application-innovation"></a>Innovation des applications

L’innovation basée sur le cloud porte principalement sur l’expérience client et la volonté du client d’utiliser les produits et services fournis par l’entreprise. Il faut du temps pour que les incréments de modification affectent les comportements d’achat des consommateurs ou des clients. Toutefois, les cycles d’innovation des applications ont tendance à être bien plus courts que dans les autres formes de transformation. Nous vous conseillons de commencer par comprendre les comportements spécifiques que vous souhaitez influencer et d’utiliser ces comportements en tant que métriques d’apprentissage. Par exemple, dans une application de e-commerce, le nombre total d’achats ou d’achats de modules complémentaires peut être le comportement cible. Pour une entreprise vidéo, le visionnage des flux vidéo peut être la cible.

La difficulté avec les métriques de comportement des clients est qu’elles peuvent être facilement influencées par des variables externes. Il est donc souvent important d’inclure des statistiques connexes avec les métriques d’apprentissage. Ces statistiques connexes peuvent inclure la cadence de publication, les bogues résolus par version, la couverture du code des tests unitaires, le nombre de consultations de page, le débit des pages, le temps de chargement des pages et d’autres métriques de performances d’application. Chacune peut afficher différentes activités et modifications apportées à la base de code et l’expérience client pour effectuer une mise en corrélation avec les modèles de comportement client de niveau supérieur.

## <a name="data-innovation"></a>Innovation des données

La modification d’un secteur, la disruption de marchés ou la transformation de produits et services peuvent prendre des années. Dans un effort d’innovation des données dans le cloud, l’expérimentation est essentielle à la mesure du succès. Soyez transparent en partageant des métriques de prédiction telles que le pourcentage de probabilité, le nombre d’expérimentations ayant échoué et le nombre de modèles entraînés. Les échecs s’accumulent plus rapidement que les réussites. Ces métriques pouvant être décourageantes, l’équipe de direction doit comprendre le temps et l’investissement nécessaires pour les utiliser correctement.

En revanche, certains indicateurs positifs sont souvent associés à l’apprentissage piloté par les données : la centralisation des jeux de données hétérogènes, l’entrée des données et la démocratisation des données. Alors que l’équipe est en train de se renseigner sur le client de demain, des résultats réels peuvent se produire immédiatement. La prise en charge des métriques d’apprentissage peut inclure les éléments suivants :

- Nombre de modèles disponibles
- Nombre de sources de données de partenaire consommées
- Appareils produisant des données d’entrée
- Volume de données d’entrée
- Types de données

Une métrique encore plus précieuse est le nombre de tableaux de bord créés à partir de sources de données combinées. Ce nombre reflète les processus métiers en l’état actuel qui sont affectés par les nouvelles sources de données. En partageant les nouvelles sources de données de manière ouverte, votre entreprise peut tirer parti des données à l’aide d’outils de création de rapports comme Power BI pour produire des Insights incrémentaux et générer des modifications métiers.

## <a name="next-steps"></a>Étapes suivantes

Une fois les métriques d’apprentissage alignées, vous pouvez commencer à [évaluer le patrimoine numérique](../digital-estate/index.md) par rapport à ces métriques. Le résultat est constitué d’un [backlog de transformation ou d’un backlog de migration](../migrate/migration-considerations/prerequisites/technical-complexity.md).

> [!div class="nextstepaction"]
> [Évaluer le patrimoine numérique](../digital-estate/index.md)
