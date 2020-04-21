---
title: Niveaux de gestion dans la gestion cloud
description: Découvrez comment restreindre les options de gestion cloud à un ensemble cohérent de processus et d’outils que vous pouvez proposer pour les charges de travail hébergées dans le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 6033f12b1604818fef4c70f1863b7a99fb4c51e6
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80809068"
---
# <a name="management-leveling-across-cloud-management-disciplines"></a>Nivellement de la gestion pour les différentes disciplines de gestion cloud

Les clés d’une gestion efficace, quel que soit l’environnement, sont la cohérence et la répétabilité des processus. Il existe un nombre infini d’options pour les opérations qui peuvent être effectuées dans Azure. De même, les méthodes de gestion cloud sont quasiment illimitées. Pour assurer la cohérence et la répétabilité, il est important de limiter ces options à un ensemble cohérent de processus et d’outils de gestion qui seront proposés pour les charges de travail hébergées dans le cloud.

## <a name="suggested-management-levels"></a>Niveaux de gestion suggérés

Étant donné que les charges de travail de votre portefeuille informatique varient, il est peu probable qu’un seul niveau de gestion suffise pour chacune d’elles. Pour vous aider à prendre en charge des charges de travail et des engagements métier différents, nous suggérons que les équipes chargées des opérations cloud ou des opérations de plateforme établissent plusieurs niveaux pour la gestion des opérations.

![Gérer les niveaux de gestion et la maturité dans le Framework d’adoption cloud](../../_images/manage/cloud-management-maturity.png)

Pour commencer, envisagez d’établir les niveaux de gestion indiqués dans le diagramme ci-dessus et suggérés dans la liste suivante :

- **Base de référence de gestion :** Une base de référence de gestion cloud (ou base de référence de gestion) est un ensemble d’outils, de processus et de tarifs cohérents qui servent de base pour l’ensemble de la gestion cloud dans Azure. Pour établir une base de référence de gestion cloud et déterminer quels outils inclure dans l’offre de base de référence faite à votre entreprise, consultez la liste dans la section « Disciplines de gestion du cloud ».
- **Base de référence améliorée :** Certaines charges de travail peuvent nécessiter des améliorations de la base de référence qui ne sont pas nécessairement propres à la plateforme ou à la charge de travail. Bien que ces améliorations ne soient pas rentables pour toutes les charges de travail, il doit y avoir des solutions, des processus et des outils communs à toutes les charges de travail qui puissent justifier le coût du support de gestion supplémentaire.
- **Spécialisation de plateforme :** Dans un environnement donné, certaines plateformes courantes sont utilisées par différentes charges de travail. Ce partage de l’architecture générale ne change pas la date à laquelle les entreprises passent au cloud. La spécialisation de la plateforme correspond à un niveau élevé de gestion. Elle applique des données et une connaissance poussée de l’architecture pour fournir un niveau plus élevé de gestion opérationnelle. Comme exemples de spécialisation de plateforme, nous pourrions citer les fonctions de gestion propres à SQL Server, aux conteneurs, à Active Directory ou à d’autres services qui peuvent être mieux gérés par le biais de processus, d’outils et d’architectures cohérents et reproductibles.
- **Spécialisation de charge de travail :** Pour les charges de travail qui sont véritablement critiques, une gestion plus approfondie, et donc plus coûteuse, peut être justifiée. La spécialisation de la charge de travail applique les données de télémétrie de la charge de travail pour déterminer des approches plus avancées concernant la gestion quotidienne. Ces mêmes données permettent souvent d’identifier les améliorations devant être apportées à l’automatisation, au déploiement et à la conception, en vue d’atteindre un plus haut niveau de stabilité, de fiabilité et de résilience, par rapport à ce que permet une gestion opérationnelle seule.
- **Non pris en charge :** Il est tout aussi important de communiquer les processus de gestion communs qui ne seront pas fournis par le biais de disciplines de gestion cloud pour les charges de travail classifiées comme non prises en charge ou non critiques.

Les organisations peuvent également choisir d’[externaliser les fonctions associées à un ou plusieurs de ces niveaux de gestion à un fournisseur de services](https://aka.ms/adopt/partneroffers). Ces fournisseurs de services peuvent utiliser [Azure Lighthouse](https://azure.com/lighthouse) pour fournir une plus grande précision et une plus grande transparence.

Les autres articles de cette série décrivent des processus qui sont généralement communs à chacune de ces disciplines.
De même, le [Guide de gestion Azure](../azure-management-guide/index.md) présente des outils qui peuvent aider à chacun de ces processus. Si vous souhaitez obtenir de l’aide pour la création de votre base de référence de gestion, commencez par lire le guide de gestion Azure. Après avoir établi la base de référence, cette série d’articles et les bonnes pratiques qui les accompagnent, peuvent vous aider à étendre votre base de référence afin de définir d’autres niveaux de gestion.

## <a name="cloud-management-disciplines"></a>Disciplines de gestion cloud

Chaque niveau de gestion suggéré peut faire appel à diverses disciplines de gestion cloud. Toutefois, le mappage est conçu pour faciliter la recherche des processus et des outils suggérés permettant d’offrir le niveau de gestion cloud le mieux adapté.

Dans la plupart des cas, le *niveau de base de référence de gestion* mentionné plus haut est constitué de processus et d’outils provenant des disciplines suivantes. Dans chaque cas, quelques processus et outils sont présentés afin de montrer les *améliorations apportées aux fonctions de base de référence*.

- **Inventaire et visibilité :** La base de référence de gestion doit inclure au minimum un moyen d’inventorier les ressources, et fournir une visibilité sur l’état d’exécution de chaque ressource.
- **Conformité opérationnelle :** Une gestion régulière de la configuration, du dimensionnement, du coût et des performances des ressources est essentielle pour garantir les performances attendues et le bon fonctionnement de la base de référence de gestion.
- **Protection et récupération :** La réduction des interruptions opérationnelles et l’accélération de la récupération après chaque interruption vous permet d’éviter des pertes de performances et un impact sur le chiffre d’affaires. La détection et la récupération sont des aspects essentiels de cette discipline pour toutes les bases de référence de gestion.

Le niveau de gestion de la spécialisation de plateforme s’appuie sur les processus et les outils alignés sur les disciplines des opérations de plateforme. De même, le niveau de gestion de la spécialisation de charge de travail s’appuie sur les processus et les outils alignés sur les disciplines des opérations de charge de travail.

## <a name="next-steps"></a>Étapes suivantes

Pour définir chacun des niveaux de gestion cloud, la prochaine étape consiste à comprendre l’[inventaire et la visibilité](./inventory.md).

> [!div class="nextstepaction"]
> [Options d’inventaire et de visibilité](./inventory.md)
