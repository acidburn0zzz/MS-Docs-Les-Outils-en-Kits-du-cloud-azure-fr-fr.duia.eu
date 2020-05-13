---
title: Présentation de la gestion opérationnelle
description: Utilisez le Cloud Adoption Framework pour Azure afin de comprendre les différentes transitions à effectuer pour permettre la gestion opérationnelle dans le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 3e1134d6ea4538a6b0f4c26418c0009d3810a25a
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83216654"
---
# <a name="establish-operational-management-practices-in-the-cloud"></a>Établir des pratiques de gestion opérationnelle dans le cloud

L’adoption du cloud est un catalyseur pour générer de la valeur commerciale. Toutefois, la valeur commerciale réelle est réalisée avec des opérations continues et stables sur les ressources technologiques déployées dans le cloud. Cette section du Framework d'adoption du cloud vous guide au fil des différentes transitions vers la gestion opérationnelle dans le cloud.

## <a name="actionable-best-practices"></a>Bonnes pratiques à utiliser

Les solutions de gestion des opérations modernes créent une vue multicloud des opérations. Les ressources gérées à l’aide des bonnes pratiques suivantes peuvent résider dans le cloud, dans un centre de données existant ou même chez un fournisseur de cloud concurrent. Actuellement, le framework comprend deux bonnes pratiques de référence pour guider la mise en place de la gestion des opérations dans le cloud :

- [Gestion des serveurs Azure](./azure-server-management/index.md) : Guide d'intégration pour incorporer les outils et services cloud natifs nécessaires à la gestion des opérations.
- [Supervision hybride](./monitor/index.md) : De nombreux clients ont déjà beaucoup investi dans System Center Operations Manager. Pour eux, ce guide de supervision hybride permet de comparer les outils de création de rapports natifs du cloud avec les outils Operations Manager. Cette comparaison permet de choisir plus facilement les outils à utiliser pour la gestion opérationnelle.

## <a name="cloud-operations"></a>Opérations cloud

Ces deux bonnes pratiques s'articulent autour d'une méthodologie de gestion des opérations basée sur l'état futur, comme l'illustre le diagramme suivant :

<!-- cSpell:ignore caf -->

![Méthodologie de gestion dans le Framework d’adoption cloud](../_images/manage/caf-manage.png)

**Alignement de l’entreprise :** Dans la méthodologie de gestion, toutes les charges de travail sont classées par état critique et valeur commerciale. Cette classification peut alors être mesurée dans une analyse d’impact, qui calcule la valeur perdue associée à une dégradation des performances ou des interruptions d’activité. À l’aide de cet impact tangible sur le chiffre d’affaires, les équipes des opérations cloud peuvent collaborer avec l’entreprise pour s’engager à équilibrer les coûts et les performances.

**Disciplines des opérations cloud :** Une fois l'entreprise alignée, il est beaucoup plus facile de suivre et de créer des rapports sur les disciplines appropriées des opérations cloud pour chaque charge de travail. La prise de décision dans le cadre de chaque discipline peut ensuite être convertie en conditions d'engagement facilement compréhensibles pour l'entreprise. Cette approche collaborative permet aux parties prenantes de l’entreprise d’agir en partenaires pour trouver le juste équilibre entre les coûts et les performances.

- **Inventaire et visibilité :** La gestion des opérations doit pouvoir au moins faire l’inventaire des ressources et créer une visibilité sur l’état d’exécution de chaque ressource.
- **Conformité opérationnelle :** Une gestion régulière de la configuration, du dimensionnement, du coût et des performances des ressources est essentielle pour assurer les performances attendues.
- **Protection et récupération :** La réduction des interruptions d'activité et l'accélération de la récupération permettent à l'entreprise d'éviter les pertes de performances et les impacts négatifs sur son chiffre d'affaires. La détection et la récupération sont des aspects essentiels de cette discipline.
- **Opérations de plateforme :** Tous les environnements informatiques contiennent un ensemble de plateformes couramment utilisées. Ces plateformes peuvent inclure des magasins de données de type SQL Server ou Azure HDInsight. D'autres plateformes courantes peuvent inclure des solutions de conteneur comme Azure Kubernetes Service (AKS). Quelle que soit la plateforme, la maturité des opérations de plateforme est ciblée sur la personnalisation des opérations en fonction de la façon dont les plateformes communes sont déployées, configurées et utilisées par les charges de travail.
- **Opérations de charge de travail :** Au plus haut niveau de maturité opérationnelle, les équipes en charge des opérations cloud peuvent adapter les opérations aux charges de travail critiques. Pour ces charges de travail, les données disponibles peuvent aider à automatiser la correction, le dimensionnement ou la protection des charges de travail en fonction de leur utilisation.

Vous pouvez consulter des conseils supplémentaires comme le [Framework de révision de la conception (nom de code : Principes de conception dans le cloud)](https://docs.microsoft.com/azure/architecture/framework/resiliency/overview) pour vous aider à prendre des décisions architecturales détaillées concernant chaque charge de travail, dans les disciplines décrites précédemment.

Cette section du framework d'adoption du cloud s'appuie sur chacune des rubriques précédentes pour promouvoir des opérations de cloud computing matures au sein de votre organisation.
