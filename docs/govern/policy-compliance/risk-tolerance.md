---
title: Évaluer la tolérance au risque
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explication des risques métier associés à une transformation cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 2b8bc595377b2748bd00f306659a46196115e91d
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223545"
---
# <a name="evaluate-risk-tolerance"></a>Évaluer la tolérance au risque

Chaque décision commerciale engendre de nouveaux risques. Tout investissement s'accompagne d'un risque de perte. Les nouveaux produits ou services engendrent des risques de défaillance du marché. Toute modification apportée aux produits ou services actuels peut se traduire par une réduction de la part de marché. La transformation cloud n’apporte aucune solution magique aux risques encourus quotidiennement par les entreprises. Au contraire, les solutions connectées (cloud ou locales) introduisent de nouveaux risques. Le déploiement de ressources dans une installation connectée au réseau accroît également les menaces potentielles en exposant les points faibles de la sécurité à une communauté mondiale beaucoup plus large. Heureusement, les fournisseurs de cloud sont conscients de l’évolution et de l’augmentation de ces risques. Ils investissent fortement afin de réduire et de gérer les risques auxquels leurs clients sont exposés.

Cet article n'est pas consacré aux risques liés au cloud. Il se concentre sur les risques métier associés aux différentes formes de transformation cloud. Plus bas, nous nous pencherons sur les moyens dont disposent les entreprises pour évaluer la tolérance au risque.

<!-- markdownlint-disable MD026 -->

## <a name="what-business-risks-are-associated-with-a-cloud-transformation"></a>Quels sont les risques métier associés à une transformation cloud ?

Les véritables risques métier sont basés sur les détails des transformations spécifiques. Plusieurs risques courants donnent lieu à une discussion pour comprendre les risques propres à l’entreprise.

> [!IMPORTANT]
> Avant de lire ce qui suit, sachez que chacun de ces risques peut être géré. L’objectif de cet article est d’informer et de préparer les lecteurs à des discussions plus productives sur la gestion des risques.

- **Violation des données :** en matière de transformation, la protection des données représente indiscutablement le risque numéro un. Les fuites de données peuvent provoquer des dommages importants pour votre entreprise, entraînant une perte de clients, une baisse de l’activité ou même une responsabilité légale. Tout changement apporté à la façon dont les données sont stockées, traitées ou utilisées engendre un risque. Les transformations cloud entraînent de nombreux changements en matière de gestion des données. Le risque ne doit donc pas être pris à la légère. La [base de référence de sécurité](../security-baseline/index.md), la [classification des données](./data-classification.md) et la [rationalisation incrémentielle](../../digital-estate/rationalize.md#incremental-rationalization) peuvent chacune contribuer à gérer ce risque.

- **Interruption de service :** les opérations métier et les expériences client reposent largement sur les opérations techniques. Les transformations cloud entraînent des changements au niveau des opérations informatiques. Dans certaines organisations, ces changements sont mineurs et faciles à ajuster. Dans d’autres, ils peuvent nécessiter un réoutillage, un réentraînement ou de nouvelles approches pour prendre en charge les opérations cloud. Plus les changements sont importants, plus l’impact potentiel sur les opérations métier et l’expérience client le sont également. La gestion de ce risque exigera la participation de l’entreprise à la planification de la transformation. Les sections relatives à la planification de la mise en production et à la sélection de la première charge de travail dans l’article [Rationalisation incrémentielle](../../digital-estate/rationalize.md#incremental-rationalization) expliquent comment choisir les charges de travail pour les projets de transformation. Le rôle de l’entreprise dans le cadre de cette activité consiste à communiquer le risque des opérations métier que constitue le changement des charges de travail définies comme prioritaires. Le fait d’aider l’équipe informatique à choisir des charges de travail ayant un moindre impact sur les opérations diminuera le risque global.

- **Contrôle du budget :** les modèles de coûts changent dans le cloud. Ce changement peut engendrer des risques associés à des dépassements de coûts ou à des augmentations du coût des marchandises vendues (COGS, Cost of Goods Sold), en particulier des dépenses d’exploitation directement imputables. Quand l’équipe commerciale travaille en étroite collaboration avec l’équipe informatique, une véritable transparence peut être atteinte en matière de coûts et d’utilisation des services par différents programmes, unités opérationnelles ou projets. La section [Gestion des coûts](../cost-management/index.md) fournit des exemples de partenariats entre les équipes commerciales et informatiques sur ce sujet.

Voici quelques-uns des risques les plus fréquemment mentionnés par les clients. L’équipe de gouvernance cloud et les équipes d’adoption du cloud peuvent commencer à développer un profil de risque à mesure que les charges de travail sont migrées et préparées pour la mise en production. Préparez-vous à devoir discuter pour définir, affiner et gérer les risques en fonction des résultats opérationnels et des efforts de transformation souhaités.

## <a name="understanding-risk-tolerance"></a>Appréhender la tolérance au risque

L'identification des risques est un processus relativement direct. Les risques liés à l’informatique sont généralement standard dans tous les secteurs. Toutefois, la tolérance à ces risques est spécifique à chaque organisation. C'est là que les conversations commerciales et informatiques ont tendance à s'enliser. Chacune des parties représentées parle une langue différente. Les comparaisons et les questions suivantes sont conçues pour engager la conversation afin d'aider chaque partie à mieux appréhender et évaluer la tolérance au risque.

## <a name="simple-use-case-for-comparison"></a>Cas d'usage simple à des fins de comparaison

Pour appréhender la tolérance au risque, examinons des données client. Si une entreprise d’un secteur particulier publie des données client sur un serveur non sécurisé, le risque technique de compromission ou de vol de ces données est à peu près identique. Toutefois, la tolérance d’une entreprise à ce risque variera considérablement en fonction de la nature et de la valeur potentielle des données.

- Aux États-Unis, les entreprises du secteur de la santé et de la finance sont soumises à des obligations de conformité strictes imposées par des tiers. On part du principe que les données personnelles ou les données médicales sont extrêmement confidentielles. Les conséquences pour les entreprises de ce type sont graves si elles sont impliquées dans le scénario de risque ci-dessus. Leur tolérance est extrêmement faible. Toutes les données client publiées à l'intérieur ou à l'extérieur du réseau doivent être régies par ces stratégies de conformité tierces.
- Une société de jeux dont les données client se limitent à un nom d’utilisateur, à des temps de jeu et à des scores est moins exposée à des conséquences graves (au-delà d’une réputation compromise) si elle adopte le comportement à risque décrit ci-dessus. Si un risque pèse sur des données non sécurisées, l’impact de ce risque est faible. Par conséquent, dans ce cas, la tolérance au risque est élevée.
- La tolérance d’une PME fournissant des services de nettoyage de tapis à des milliers de clients se situerait entre ces deux extrémités. Les données client peuvent alors être plus robustes et contenir des informations comme l’adresse ou le numéro de téléphone. Dans la mesure où ces informations peuvent être considérées comme des données personnelles, elles doivent être protégées. Cela dit, il se peut qu'aucune obligation de gouvernance spécifique n'impose de sécuriser les données. D'un point de vue informatique, la réponse est simple : sécuriser les données. D'un point de vue commercial, ce n'est peut-être pas aussi simple. L'équipe commerciale aurait besoin de détails supplémentaires avant de pouvoir déterminer un niveau de tolérance pour ce risque.

La section suivante contient des exemples de questions qui peuvent aider l’entreprise à déterminer un niveau de tolérance au risque pour le cas d’utilisation ci-dessus, entre autres.

## <a name="risk-tolerance-questions"></a>Questions relatives à la tolérance au risque

Cette section présente trois catégories de questions : Impact sur les pertes, Probabilité de perte et Coûts d’atténuation. Quand les équipes commerciales et informatiques s’associent pour réfléchir à chacun de ces thèmes, la décision de consacrer des efforts à la gestion des risques et à la tolérance globale à un risque particulier est plus facile à prendre.

**Impact sur les pertes :** Questions visant à déterminer l'impact d'un risque. Il peut être difficile de répondre à ces questions. Il est préférable de quantifier l'impact, mais parfois la conversation seule suffit à identifier la tolérance. Des fourchettes sont également acceptables, surtout si elles incluent les hypothèses qui les ont définies.

- Ce risque peut-il enfreindre les obligations de conformité de tiers ?
- Ce risque peut-il enfreindre les stratégies internes de l’entreprise ?
- Ce risque peut-il entraîner un décès, la perte d’un membre ou une perte de propriété ?
- Ce risque pourrait-il coûter des clients ou des parts de marché ? Si oui, ce coût peut-il être quantifié ?
- Ce risque pourrait-il nuire à l'expérience client ? Ces expériences peuvent-elles affecter les ventes ou les recettes ?
- Ce risque pourrait-il engager une nouvelle responsabilité juridique ? Si oui, existe-t-il un précédent en matière d'attribution de dommages-intérêts dans ce genre de cas ?
- Ce risque pourrait-il entraîner une interruption d'activité pour l'entreprise ? Si oui, pendant combien de temps l'activité serait-elle interrompue ?
- Ce risque pourrait-il ralentir les activités de l'entreprise ? Si oui, dans quelle mesure et pendant combien de temps ?
- À ce stade de la transformation, s'agit-il d'un risque ponctuel ou est-il susceptible de se répéter ?
- Le risque augmente-t-il ou diminue-t-il au fil de la progression de la transformation ?
- Le risque est-il susceptible d'augmenter ou de diminuer avec le temps ?
- Le risque est-il lié à une échéance ? Le risque s'estompera-t-il ou s'aggravera-t-il si rien n'est fait ?

Ces questions de base soulèveront beaucoup d'autres interrogations. Après un dialogue sain, il est conseillé de consigner les risques pertinents et, si possible, de les quantifier.

**Coûts de remédiation des risques :** Questions visant à déterminer le coût de la suppression ou de la minimisation du risque. Ces questions peuvent être assez directes, surtout lorsqu'elles sont représentées dans une fourchette.

- Existe-t-il une solution claire, et quel est son coût ?
- Existe-t-il des options permettant d’empêcher ou de minimiser ce risque ? Quelle est la fourchette de coûts de ces solutions ?
- Comment l'entreprise doit-elle s'y prendre pour choisir la solution la plus efficace et la plus claire ?
- Comment l'entreprise doit-elle s'y prendre pour valider les coûts ?
- Quels autres avantages peuvent découler de la solution de suppression de ce risque ?

Ces questions simplifient à l’extrême les solutions techniques nécessaires à la gestion ou à la suppression des risques. Toutefois, elles communiquent ces solutions de manière à ce que l'entreprise puisse les intégrer rapidement dans un processus décisionnel.

**Probabilité de perte :** Questions visant à déterminer la probabilité que le risque devienne une réalité. Il s'agit du domaine le plus difficile à quantifier. Nous suggérons plutôt à l’équipe de gouvernance cloud de créer des catégories pour la communication de la probabilité, sur la base de données justificatives. Les questions suivantes peuvent vous aider à créer des catégories pertinentes pour l'équipe.

- Des recherches ont-elles été menées sur la probabilité que ce risque se réalise ?
- Le fournisseur peut-il fournir des références ou des statistiques sur la probabilité d’un impact ?
- D'autres entreprises du secteur ou de la branche concernés ont-elles été touchées par ce risque ?
- D'autres entreprises en général ont-elles été touchées par ce risque ?
- Ce risque est-il propre à quelque chose que cette entreprise a mal fait ?

Après avoir répondu à ces questions à qu’à d’autres questions posées par l’équipe de gouvernance cloud, des regroupements de probabilités émergeront probablement. Voici quelques exemples de regroupements pour vous aider à démarrer :

- **Aucune indication :** les recherches n’ont pas été suffisantes pour déterminer la probabilité.
- **Risque faible :** la recherche actuelle indique que la réalisation du risque est peu probable.
- **Risque futur :** actuellement, la probabilité est faible. Toutefois, la poursuite de l’adoption exigerait une nouvelle analyse.
- **Risque moyen :** il est probable que le risque affectera l’entreprise.
- **Risque élevé :** au fil du temps, il est de plus en plus probable que l’entreprise sera confrontée à ce risque.
- **Diminution du risque :** le risque est moyen à élevé. Toutefois, les mesures prises par les équipes informatiques ou commerciales réduisent la probabilité d’un impact.

**Détermination de la tolérance :**

Les trois catégories de questions ci-dessus doivent fournir suffisamment de données pour déterminer les tolérances initiales. Quand le risque et la probabilité sont faibles, et que les coûts de remédiation du risque sont élevés, l’entreprise est peu encline à investir dans des mesures correctives. Quand le risque et la probabilité sont élevés, l’entreprise envisagera probablement d’investir, à condition que les coûts ne dépassent pas les risques potentiels.

## <a name="next-steps"></a>Étapes suivantes

Ce type de conversation peut aider les équipes commerciales et informatiques à évaluer plus efficacement la tolérance. Ces conversations peuvent être utilisées lors de la création des stratégies MVP et lors des révisions incrémentielles des stratégies.

> [!div class="nextstepaction"]
> [Définir la stratégie de l'entreprise](./policy-definition.md)
