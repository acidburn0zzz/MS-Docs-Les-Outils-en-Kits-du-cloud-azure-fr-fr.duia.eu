---
title: Présentation de la gestion opérationnelle
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez la gestion opérationnelle dans le framework d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/19/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: manage
ms.openlocfilehash: ed8afc403f217475cb69d4f0bf6742fe64443ae3
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818435"
---
# <a name="establishing-operational-management-practices-in-the-cloud"></a>Mise en place des pratiques de gestion opérationnelle dans le cloud

L’adoption du cloud est un catalyseur pour générer de la valeur commerciale. Toutefois, la valeur commerciale réelle est réalisée avec des opérations continues et stables sur les ressources technologiques déployées dans le cloud. Cette section du Framework d’adoption du cloud guide le lecteur dans différentes transitions vers une gestion opérationnelle dans le cloud.

## <a name="actionable-best-practices"></a>Bonnes pratiques à utiliser

Les solutions de gestion des opérations modernes créent une vue multicloud des opérations. Les ressources gérées à l’aide des bonnes pratiques suivantes peuvent résider dans le cloud, dans un centre de données existant ou même chez un fournisseur de cloud concurrent. Actuellement, le framework comprend deux bonnes pratiques de référence pour guider la mise en place de la gestion des opérations dans le cloud :

* [Gestion des serveurs Azure](./azure-server-management/index.md) : Guide d’intégration pour incorporer les outils et services cloud natifs nécessaires pour gérer les opérations.
* [Supervision hybride](./monitor/index.md) : De nombreux clients ont déjà beaucoup investi dans System Center Operations Manager. Pour eux, ce guide de supervision hybride permet de comparer les outils de création de rapports natifs du cloud avec les outils Operations Manager. Cette comparaison permet de choisir facilement les outils à utiliser pour la gestion opérationnelle.

## <a name="cloud-operations"></a>Opérations cloud

Ces deux bonnes pratiques mènent à une méthodologie d’état futur de la gestion des opérations.

![Méthodologie de gestion CAF](../_images/operate/caf-manage.png)

**Alignement de l’entreprise :** Dans la méthodologie de gestion, toutes les charges de travail sont classées par état critique et valeur commerciale. Cette classification peut alors être mesurée dans une analyse d’impact, qui calcule la valeur perdue associée à une dégradation des performances ou des interruptions d’activité. À l’aide de cet impact tangible sur le chiffre d’affaires, les équipes des opérations cloud peuvent collaborer avec l’entreprise pour s’engager à équilibrer les coûts et les performances.

**Disciplines des opérations cloud :** Une fois que l’entreprise est alignée, il est beaucoup plus facile de suivre et de créer des rapports sur les disciplines appropriées des opérations cloud pour chaque charge de travail. La prise de décision dans le cadre de chaque discipline peut ensuite être convertie en conditions d’engagement facilement compréhensibles pour l’entreprise. Cette approche collaborative permet aux parties prenantes de l’entreprise d’agir en partenaires pour trouver le juste équilibre entre les coûts et les performances.

* Inventaire et visibilité : La gestion des opérations doit pouvoir au moins faire l’inventaire des ressources et créer une visibilité sur l’état d’exécution de chaque ressource.
* Conformité opérationnelle : Une gestion régulière de la configuration, du dimensionnement, des coûts et des performances des ressources est essentielle pour assurer les performances attendues.
* Protéger et récupérer : La réduction des interruptions opérationnelles et l’accélération de la récupération après chaque interruption permet d’éviter des pertes de performances et un impact sur le chiffre d’affaires. La détection et la récupération sont des aspects essentiels de cette discipline.
* Opérations de plateforme : Tous les environnements informatiques contiennent un ensemble de plateformes couramment utilisées. Ces plateformes peuvent inclure des magasins de données de type SQL Server ou HDInsights. D’autres plateformes courantes peut inclure des solutions de conteneur comme kubernetes ou AKS. Quelle que soit la plateforme, la maturité des opérations de plateforme est ciblée sur la personnalisation des opérations en fonction de la façon dont ces plateformes sont déployées, configurées et utilisées par les charges de travail.
* Opérations de charge de travail : Au niveau le plus élevé de la maturité opérationnelle, les équipes des opérations cloud sont en mesure de paramétrer des opérations pour les charges de travail qui sont essentielles à la réussite de l’entreprise. Pour ces charges de travail très critiques, les données disponibles peuvent aider à automatiser la correction, le dimensionnement ou la protection des charges de travail en fonction de leur utilisation.

Vous pouvez consulter des conseils supplémentaires comme le [Framework de révision de conception (nom de code : Principes de conception du cloud)](/azure/architecture/reliability) pour vous aider à prendre des décisions architecturales détaillées concernant chaque charge de travail, dans les disciplines ci-dessus.

Cette section du framework d’adoption du cloud s’appuie sur chacune de ces rubriques pour mettre en place les opérations cloud au sein de votre organisation.
