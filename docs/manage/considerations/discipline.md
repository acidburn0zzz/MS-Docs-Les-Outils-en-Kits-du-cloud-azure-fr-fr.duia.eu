---
title: Nivellement de la gestion pour les différentes disciplines de gestion cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Nivellement de la gestion pour les différentes disciplines de gestion cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 44bfe58f86a442a5129eee791e3da0f7a6b68031
ms.sourcegitcommit: 73dbedf580951f25bf4b5544b83451cb075b1fa1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72805795"
---
# <a name="management-leveling-across-cloud-management-disciplines"></a>Nivellement de la gestion pour les différentes disciplines de gestion cloud

La clé d’une gestion efficace, quel que soit l’environnement, est la cohérence et la répétabilité des processus. Il existe un nombre infini d’options pour les opérations qui peuvent être effectuées dans Azure. De même, les méthodes de gestion cloud sont quasiment illimitées. Pour assurer la cohérence et la répétabilité, il est important de limiter ces options à un ensemble cohérent de processus et d’outils de gestion qui seront proposés pour les charges de travail hébergées dans le cloud.

## <a name="suggested-management-levels"></a>Niveaux de gestion suggérés

Étant donné que les charges de travail de votre portefeuille informatique ne sont pas toutes les mêmes, il est peu probable qu’un seul niveau de gestion suffise pour chacune d’elles. Pour prendre en charge les différentes charges de travail et les différents engagements métier, il est préférable que l’équipe chargée des opérations cloud ou celle chargée des opérations de plateforme établisse plusieurs niveaux pour la gestion des opérations.

![Gérer les niveaux de gestion et la maturité dans le Framework d’adoption cloud](../../_images/manage/cloud-management-maturity.png)

Les niveaux de gestion suivants (également illustrés ci-dessus) vous sont suggérés comme point de départ :

- **Base de référence de gestion** : Une base de référence de gestion cloud (ou base de référence de gestion) est l’ensemble d’outils, de processus et de tarifs cohérents qui servira de base pour l’ensemble de la gestion cloud dans Azure. Pour établir une base de référence de gestion cloud, consultez le tableau de la section suivante afin de connaître les outils qui sont inclus dans l’offre de base de référence faite à votre entreprise.
- **Base de référence améliorée** : Certaines charges de travail peuvent nécessiter des améliorations de la base de référence qui ne sont pas nécessairement propres à la plateforme ou à la charge de travail. Même si ces améliorations ne sont pas rentables pour toutes les charges de travail, il doit y avoir des solutions, des processus et des outils communs à toutes les charges de travail dont le coût justifie une gestion supplémentaire.
- **Spécialisation de la plateforme** : Dans un environnement donné, il existe des plateformes communes qui sont utilisées par plusieurs charges de travail. Ce partage de l’architecture générale ne change pas la date à laquelle les entreprises passent au cloud. La spécialisation de la plateforme correspond à un niveau élevé de gestion. Elle tire parti des données et d’une connaissance poussée de l’architecture pour fournir un niveau plus élevé de gestion opérationnelle. Comme exemples de spécialisation de plateforme, nous pourrions citer les fonctions de gestion propres à SQL Server, aux conteneurs, à Active Directory ou à d’autres services qui peuvent être mieux gérés par le biais de processus, d’outils et d’architectures cohérents et reproductibles.
- **Spécialisation de la charge de travail** : Pour les charges de travail qui sont véritablement critiques, une gestion plus approfondie, et donc plus coûteuse, peut être justifiée. La spécialisation de la charge de travail utilise les données de télémétrie de la charge de travail pour déterminer des approches plus avancées concernant la gestion quotidienne. Ces mêmes données permettent souvent d’identifier les améliorations devant être apportées à l’automatisation, au déploiement et à la conception, en vue d’atteindre un plus haut niveau de stabilité, de fiabilité et de résilience, par rapport à ce que permet une gestion opérationnelle seule.
- **Non pris en charge** : Il est tout aussi important de communiquer les processus de gestion communs qui ne seront pas fournis par le biais de disciplines de gestion cloud pour les charges de travail classifiées comme non prises en charge ou non critiques.

Les organisations peuvent également choisir d’[externaliser les fonctions associées à un ou plusieurs de ces niveaux de gestion à un fournisseur de services](https://www.microsoft.com/cloud-adoption-framework-offers?ot=manage). Ces fournisseurs de services peuvent utiliser [Azure Lighthouse](https://azure.com/lighthouse) pour fournir une plus grande précision et une plus grande transparence.

Les autres articles de cette série décrivent un certain nombre de processus qui sont généralement communs à ces disciplines.
De même, le [Guide de gestion Azure](../azure-management-guide/index.md) présente des outils qui peuvent aider à chacun de ces processus. Si vous souhaitez obtenir de l’aide pour la création de votre base de référence de gestion, commencez par lire le guide de gestion Azure. Une fois la base de référence établie, cette série d’articles, et les bonnes pratiques qui les accompagnent, peuvent vous aider à étendre votre base de référence afin de définir d’autres niveaux de gestion.

## <a name="cloud-management-disciplines"></a>Disciplines de gestion cloud

Chacun des niveaux de gestion suggérés peut faire appel à différentes disciplines de gestion cloud. Toutefois, le mappage est conçu pour faciliter la recherche des processus et des outils suggérés permettant d’offrir le niveau de gestion cloud le mieux adapté.

Dans la plupart des cas, le « niveau de base de référence de gestion » décrit ci-dessus est constitué de processus et d’outils provenant des disciplines suivantes. Dans chaque cas, quelques processus et outils sont présentés afin de montrer les améliorations apportées aux fonctions de base de référence.

- **Inventaire et visibilité** : La base de référence de gestion doit inclure au minimum un moyen d’inventorier les ressources, et fournir une visibilité sur l’état d’exécution de chaque ressource.
- **Conformité opérationnelle :** Une gestion régulière de la configuration, du dimensionnement, du coût et des performances des ressources est essentielle pour garantir les performances attendues et le bon fonctionnement de la base de référence de gestion.
- **Protection et récupération :** La réduction des interruptions opérationnelles et l’accélération de la récupération après chaque interruption permet d’éviter des pertes de performances et un impact sur le chiffre d’affaires. La détection et la récupération sont des aspects essentiels de cette discipline pour toutes les bases de référence de gestion.

Le niveau de gestion de la spécialisation de plateforme s’appuie sur les processus et les outils qui sont alignés sur les disciplines des opérations de plateforme. De même, le niveau de gestion de la spécialisation de charge de travail s’appuie sur les processus et les outils qui sont alignés sur les disciplines des opérations de charge de travail.

  
## <a name="next-steps"></a>Étapes suivantes

Pour définir chacun des niveaux de gestion cloud, la prochaine étape consiste à comprendre l’[inventaire et la visibilité](./inventory.md).

> [!div class="nextstepaction"]
> [Options d’inventaire et de visibilité](./inventory.md)
