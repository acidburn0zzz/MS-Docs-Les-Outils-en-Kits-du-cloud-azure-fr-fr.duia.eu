---
title: Documentation sur le Microsoft Cloud Adoption Framework pour Azure
description: Obtenez les outils, les conseils et les explications qui vous aideront à modeler les stratégies et à aboutir aux résultats métier souhaités dans toutes les phases du cycle de vie de l’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.custom: homepage
ms.openlocfilehash: 46be63c2dfe2e4eb5e617c4d74edfc835bf1ddc0
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230249"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-the-microsoft-cloud-adoption-framework-for-azure"></a>Qu’est-ce que le Microsoft Cloud Adoption Framework pour Azure ?

Le Microsoft Cloud Adoption Framework pour Azure est un guide éprouvé conçu pour vous aider à créer et à implémenter les stratégies commerciales et technologiques nécessaires pour le succès de votre organisation dans le cloud. Il fournit les meilleures pratiques, la documentation et les outils dont les architectes cloud, les professionnels de l’informatique et les décideurs commerciaux ont besoin pour atteindre avec succès leurs objectifs à court et à long terme.

En utilisant les meilleures pratiques du Microsoft Cloud Adoption Framework pour Azure, les organisations peuvent mieux aligner leurs stratégies commerciales et techniques pour assurer leur succès. Pour en savoir plus, regardez la vidéo suivante.

<!-- markdownlint-disable MD034 -->

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4tyzr]

<!-- markdownlint-enable MD034 -->

Le Cloud Adoption Framework rassemble les meilleures pratiques d’adoption du cloud des employés, partenaires et clients de Microsoft. Il fournit un ensemble d’outils, de conseils et de témoignages qui aident à façonner des stratégies technologiques, commerciales et humaines pour obtenir les résultats commerciaux souhaités pendant le processus d’adoption. Ces conseils s’alignent sur les phases suivantes du cycle de vie de l’adoption du cloud, ce qui permet d’accéder facilement aux bons conseils au bon moment.

<!-- markdownlint-disable MD033 -->

|                                                    |                                                                                                                          |                                                |                                                                                                              |  |  |  |  |
|----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|--------------------------------------------------------------------------------------------------------------|--|--|--|--|
| ![Icône de stratégie](./_images/icons/strategy.png) | [Stratégie](./strategy/index.md) : définir la justification professionnelle et les résultats attendus de l’adoption.  | <br>![Icône Planification](./_images/icons/plan.png)  | [Planification](./plan/index.md) : Aligner les plans d’adoption actionnables sur les résultats métier. |  |  |  |  |
| ![Icône Préparation](./_images/icons/ready.png)        | <br>[Prêt](./ready/index.md) : Préparer l’environnement cloud pour les modifications planifiées. | ![Icône Migration](./_images/icons/adopt.png)     | <br>[Migration](./migrate/index.md) : Migrer et moderniser les charges de travail existantes.             |  |  |  |  |
| ![Icône Innovation](./_images/icons/innovate.png)        | <br>[Innovation :](./innovate/index.md) Développer de nouvelles solutions hybrides ou cloud natives. | ![Icône Gouvernance](./_images/icons/govern.png)     | <br>[Gouverner](./govern/index.md) : Gouverner l’environnement et les charges de travail.             |  |  |  |  |
| ![Icône Gestion](./_images/icons/manage.png) | <br>[Gérer](./manage/index.md) : Gestion des opérations pour les solutions cloud et hybrides. | ![Icône Organisation](./_images/icons/organize.png)     | <br>[Organiser](./organize/index.md) : Gouverner l’environnement et les charges de travail.             |  |  |  |  |

## <a name="understand-the-lifecycle"></a>Comprendre le cycle de vie

Chacune des méthodologies capturées ci-dessus fait partie d’un large cycle de vie d’adoption du cloud. L’image suivante relie chaque méthodologie pour illustrer le cycle de vie global. Le Framework d’adoption du cloud est un framework du cycle de vie complet qui guide les clients tout au long des différentes phases de l’adoption en leur fournissant des méthodologies comme approches spécifiques pour surmonter les blocages courants.

<!-- cSpell:ignore caf -->

::: image type="content" source="./_images/caf-overview-new.svg" alt-text="Overview of the Cloud Adoption Framework" :::

## <a name="intent"></a>Intentionnel

Le cloud change radicalement la façon dont les entreprises se procurent, utilisent et sécurisent les ressources informatiques. Jusqu’ici, elles étaient propriétaires et responsables de tous les aspects informatiques, de l’infrastructure aux logiciels. En passant au cloud, les entreprises peuvent provisionner et consommer des ressources seulement quand elles en ont besoin. Bien que le cloud offre une formidable flexibilité quant aux choix de conception, les entreprises ont besoin d’une méthodologie éprouvée et cohérente pour l’adoption de technologies cloud. Le Framework d’adoption du cloud Microsoft pour Azure répond à ce besoin, en aidant à la prise des décisions tout au long de l’adoption du cloud.

L’adoption du cloud n’est cependant qu’un moyen d’atteindre un objectif final. Une adoption réussie du cloud débute bien avant le choix du fournisseur de la plateforme cloud. Elle commence quand les décisionnaires informatiques et métier prennent conscience du fait que le cloud peut accélérer un objectif de transformation métier spécifique. Le Framework d’adoption du cloud peut les aider à aligner des stratégies en matière de transformation technique, culturelle et métier de façon à atteindre les objectifs métier souhaités.

Le Framework d’adoption du cloud fournit une aide technique pour Microsoft Azure. Étant donné que les entreprises clientes peuvent encore être dans la phase de sélection d’un fournisseur cloud ou avoir une stratégie multicloud intentionnelle, le framework donne des conseils d’ordre général indépendants du cloud pour les décisions stratégiques quand c’est possible.

## <a name="intended-audience"></a>Public concerné

Cette aide concerne l’activité, les technologies et la culture des entreprises. Voici la liste des rôles affectés : directeurs métier, décisionnaires métier, décisionnaires informatiques, département financier, administrateurs d’entreprise, opérations informatiques, conformité et sécurité informatiques, gouvernance informatique, propriétaires de développements de charges de travail et propriétaires d’opérations de charges de travail. Chaque rôle utilise son propre vocabulaire, chacun ayant des objectifs et des indicateurs de performance clés différents. Un même ensemble de contenus ne peut pas s’adresser de façon efficace à tous les publics.

L’**architecte cloud** entre en jeu. L’architecte du cloud joue le rôle de facilitateur et de leader d’opinion pour rassembler tous ces publics. Nous avons conçu cette collection de guides pour aider les architectes du cloud à adapter les discussions en fonction des publics et faciliter la prise de décision. La transformation métier rendue possible par le cloud dépend des conseils donnés par le rôle d’architecte du cloud aux équipes métier et informatiques.

Chaque section du Framework d’adoption du cloud représente une spécialisation ou une variante différente du rôle de l’architecte cloud. Ces sections permettent également de partager les responsabilités quant à l’architecture cloud entre les membres d’une équipe d’architectes cloud. Par exemple, la section dédiée à la gouvernance est conçue pour les architectes du cloud qui s’intéressent à la réduction des risques techniques. Certains fournisseurs cloud nomment ces spécialistes des « dépositaires du cloud ». Nous préférons le terme _gardien du cloud_ ou, considéré collectivement, _équipe de gouvernance cloud_.

## <a name="how-to-use-the-microsoft-cloud-adoption-framework-for-azure"></a>Utilisation du framework d’adoption du cloud Microsoft pour Azure

Si votre entreprise découvre Azure, elle doit commencer par [comprendre et documenter les décisions d’alignement fondamentales](./get-started/cloud-concepts.md). Si la transformation numérique de votre entreprise implique le cloud, la compréhension de ces concepts fondamentaux vous aidera à chaque étape du processus.

<!-- docsTest:ignoreNextStep -->

> [!div class="nextstepaction"]
> [Prise en main](./get-started/index.md)
