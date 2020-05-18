---
title: Comprendre et aligner la hiérarchie du portefeuille
description: Comprendre et aligner la hiérarchie du portefeuille
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 8b7b81c6d931eb5a5518bedfff665c580c7e9053
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230645"
---
<!-- cSpell:ignore matrixed ISVs -->

<!-- markdownlint-disable MD026 -->

# <a name="understand-and-align-the-portfolio-hierarchy"></a>Comprendre et aligner la hiérarchie du portefeuille

Les besoins des entreprises sont souvent pris en charge, améliorés ou accélérés à l’aide de technologies de l’information. Un ensemble de technologies offrant une valeur commerciale définie est appelé _charge de travail_. Cette collection peut inclure des applications, des serveurs ou machines virtuelles, des données, des appareils, ou d’autres ressources regroupées de manière similaire.

En règle générale, un acteur commercial et un responsable technique partagent la responsabilité de la prise en charge en continu de chaque charge de travail. Dans certaines phases du cycle de vie de la charge de travail, ces rôles sont clairement énoncés. Dans des phases plus opérationnelles du cycle de vie d’une charge de travail, ces rôles peuvent être transférés vers une équipe de gestion des opérations partagées ou une équipe d’opérations cloud. À mesure qu’augmente le nombre de charges de travail, les rôles (déclarés ou implicites) deviennent plus complexes et plus matriciels.

La plupart des entreprises s’appuient sur plusieurs charges de travail pour fournir des fonctions métier essentielles. La collection de charges de travail et actifs, ainsi que des projets, personnes, processus et investissements associés est appelée un _portefeuille_. La matrice du personnel commercial, de développement et d’exploitation nécessite de disposer d’une hiérarchie de portefeuille pour comprendre comment les charges de travail et les services connexes s’assemblent.

Cet article fournit des définitions claires pour les niveaux de la hiérarchie du portefeuille. L’article aligne chacune des équipes sur la responsabilité appropriée à chaque niveau, ainsi que sur la source de la meilleure orientation pour que cette équipe puisse répondre aux attentes correspondant à ce niveau. Dans cet article, chaque niveau de la hiérarchie est également appelé _étendue_.

## <a name="portfolio-hierarchy"></a>Hiérarchie du portefeuille

Les charges de travail et leurs ressources connexes sont au cœur de tout portefeuille. Les étendues ou couches supplémentaires ci-dessous définissent la façon dont ces charges de travail sont vues et dans quelle mesure elles sont affectées par la matrice d’équipes de support potentielles.

Lors du déploiement de votre première charge de travail, il se peut que celle-ci et ses ressources soient la seule étendue définie. Les autres couches peuvent être définies explicitement à mesure que des charges de travail supplémentaires sont déployées.

![Hiérarchie cloud-portefeuille de portefeuille, plateforme, utilitaires de zones d’atterrissage/plateformes, charges de travail/solutions et ressources. Liste en ordre décroissant dans une relation parent-enfant imbriquée.](../../_images/ready/hierarchy.png)

Bien que les conditions puissent varier, toutes les solutions informatiques incluent des ressources et des charges de travail :

- **Ressource :** les ressources sont la plus petite unité de fonction technique prenant en charge une charge de travail ou une solution.
- **Charge de travail :** les charges de travail sont la plus petite unité de support informatique pour l’entreprise. Une charge de travail est une collection de ressources (infrastructures, d’applications et données) qui prend en charge un objectif métier commun ou l’exécution d’un processus métier commun.

Lorsque des entreprises prennent en charge des charges de travail par le biais d’approches matricielles ou centralisées, il existe probablement une hiérarchie plus large pour prendre en charge ces charges de travail :

- **Zone d’atterrissage :** les zones d’atterrissage permettent aux charges de travail d’accéder à tous les _utilitaires de base_ (ou plomberie partagée) fournis par une _fondation de plateforme_ nécessaires pour prendre en charge une ou plusieurs charges de travail.
- **Utilitaires de base :** services informatiques partagés requis pour que les charges de travail fonctionnent à l’intérieur du portefeuille technologique et commercial.
- **Fondation de plateforme :** structure organisationnelle destinée à centraliser des solutions de base et veiller à ce que ces contrôles soient appliqués pour toutes les zones d’atterrissage.
- **Plateformes cloud :** en fonction de la stratégie globale de prise en charge du _portefeuille_ dans son ensemble, les clients peuvent avoir besoin de plusieurs plateformes cloud avec des déploiements distincts de fondation de plateforme pour gérer plusieurs régions, solutions hybrides, voire solutions multicloud.
- **Portefeuille :** dans une perspective technologique, le portefeuille est la collection de charges de travail, ressources et ressources connexes qui couvre toutes les plateformes cloud. dans une perspective commerciale, le portefeuille est la collection de projets, personnes, processus et investissements qui soutiennent et gèrent le portefeuille technologique pour générer des résultats commerciaux. Ensemble, ces deux perspectives reflètent le _portefeuille_.

## <a name="hierarchy-accountability-and-guidance"></a>Responsabilité et guidance de la hiérarchie

Chaque couche de la hiérarchie du portefeuille est gérée par une partie responsable. Le diagramme suivant montre la correspondance entre l’équipe responsable et la guidance à l’appui de ses décisions commerciales et techniques, ainsi que l’implémentation technique qui s’ensuit.

> [!NOTE]
> Les équipes mentionnées dans la section suivante peuvent être des équipes virtuelles ou des individus. Pour certaines variantes de cette hiérarchie, certaines des équipes responsables peuvent être réduites, comme décrit dans les variantes de responsabilité ci-dessous.

![Responsabilité alignée sur la hiérarchie](../../_images/ready/hierarchy-with-roles.png)

- **Portefeuille :** l’équipe de stratégie cloud et le Centre d’excellence du cloud (CCoE) utilisent les méthodologies Stratégie et Plan pour guider les décisions qui affectent l’ensemble du portefeuille. L’équipe de stratégie cloud est responsable du niveau d’entreprise de la hiérarchie globale du portefeuille cloud. Elle doit également être informée des décisions concernant l’environnement, les zones d’atterrissage et les charges de travail hautement prioritaires.
- **Plateforme cloud :** l’équipe de gouvernance cloud est responsable des aspects qui garantissent la cohérence au sein de chaque environnement conformément à la méthodologie de gouvernance. L’équipe de gouvernance cloud est responsable de la gouvernance de toutes les ressources dans tous les environnements. L’équipe de gouvernance cloud doit être consultée concernant tout changement pouvant nécessiter une exception aux règles de gouvernance ou une modification de celles-ci. L’équipe de gouvernance cloud doit également être informée des progrès concernant la charge de travail et l’adoption de ressources.
- **Zone d’atterrissage et fondations de plateforme :** l’équipe de plateforme cloud est responsable du développement des zones d’atterrissage et des utilitaires de plateforme qui sous-tendent l’adoption. L’équipe d’automatisation cloud est chargée d’automatiser le développement d’une prise en charge continue de ces zones d’atterrissage et utilitaires de plateforme. Les deux équipes utilisent la méthodologie de préparation pour guider l’implémentation. Les deux équipes doivent être informées de la progression de l’adoption de la charge de travail et de toute modification de l’entreprise ou de l’environnement.
- **Charge de travail :** l’adoption se produit au niveau de la charge de travail. Les équipes d’adoption cloud utilisent les méthodologies Migration et Innovation pour mettre en place des processus évolutifs destinés à accélérer l’adoption. Une fois l’adoption terminée, la propriété des charges de travail est transférée à une équipe d’opérations cloud qui utilise la méthodologie Gestion pour guider la gestion des opérations. Les deux équipes doivent être à l’aise avec l’utilisation de l’Infrastructure Azure Architecture pour prendre des décisions architecturales détaillées qui affectent les charges de travail qu’elles prennent en charge. Les deux équipes doivent être informées des modifications apportées aux zones d’atterrissage et aux environnements. Les deux équipes peuvent occasionnellement contribuer aux fonctionnalités de la zone d’atterrissage.
- **Ressource :** les ressources relèvent généralement la responsabilité de l’équipe d’opérations cloud. Celle-ci utilise la ligne de base de la gestion dans la méthodologie Gestion pour guider les décisions en matière de gestion des opérations. Elle doit également utiliser Azure Advisor et l’Infrastructure Azure Architecture pour apporter aux ressources et à l’architecture des changements spécifiques nécessaires pour répondre aux exigences des opérations avancées.

### <a name="accountability-variants"></a>Variantes de responsabilité :

- **Environnement unique :** quand une entreprise n’a besoin que d’un seul environnement, un Centre d’excellence du cloud n’est généralement pas requis.
- **Zone d’atterrissage unique :** si un environnement ne contient qu’une seule zone d’atterrissage, les capacités de gouvernance et de plateforme peuvent également être consolidées dans une seule équipe.
- **Charge de travail unique :** certaines entreprises n’ont besoin que d’une ou de quelques charges de travail dans une zone d’atterrissage et un environnement. Dans ces cas, le besoin de répartition des tâches entre les équipes de gouvernance, de plateforme et d’opérations est faible.

## <a name="common-workload-and-accountability-examples"></a>Exemples courants de charge de travail et de responsabilité

Les exemples suivants illustrent la hiérarchie du portefeuille.

### <a name="commercial-off-the-shelf-cots-workloads"></a>Charges de travail du commerce

Traditionnellement, les entreprises ont privilégié les solutions logicielles du commerce pour alimenter les processus métier. Ces solutions sont installées, configurées, puis exploitées. La configuration modifie peu l’architecture des solutions. Dans ces scénarios, toute adoption cloud de solutions du commerce aboutit à une transition vers une équipe d’opérations cloud. L’équipe d’opérations cloud devient alors propriétaire technique des solutions logicielles et assume la responsabilité de la gestion de la configuration, du coût, des cycles de mise à jour corrective et d’autres besoins opérationnels.

Ces charges de travail comprennent des packages de comptabilité, des logiciels de logistique ou des solutions spécifiques du secteur. Dans la terminologie de Microsoft, les fournisseurs de ces packages sont appelés éditeurs de logiciels indépendants (ISV). De nombreux éditeurs de logiciels indépendants proposent un service pour déployer et maintenir une instance de leur package logiciel dans vos abonnements. Ils peuvent également proposer une version du package logiciel qui s’exécute dans leur propre environnement hébergé dans le cloud, fournissant une alternative de plateforme en tant que service (PaaS) à la charge de travail. À l’exception des offres PaaS, les équipes d’opérations cloud sont chargées de veiller au respect des exigences de conformité opérationnelle de base pour ces charges de travail, et devraient travailler avec l’équipe de gouvernance cloud pour aligner les coûts, les performances et d’autres piliers de l’architecture.

### <a name="in-development-with-active-revisions"></a>En développement avec révisions actives

Quand une solution du commerce ou une offre PaaS n’est pas adaptée aux besoins métier ou s’il n’existe aucune solution, les entreprises créent des charges de travail développées sur mesure. En règle générale, un petit pourcentage du portefeuille informatique global utilise cette approche des charges de travail. Cependant, ces charges de travail tendent à générer une contribution anormalement élevée de l’informatique aux résultats commerciaux, en particulier à ceux liés à de nouvelles sources de revenus. Ces charges de travail ont tendance à bien correspondre aux nouvelles idées en matière d’innovation.

En raison de divers mouvements qui plongent leur racines dans des méthodologies agiles et des pratiques de DevOps, ces charges de travail favorisent un alignement des équipes commerciale et de DevOps par rapport à la gestion informatique traditionnelle. Pour ces charges de travail, il se peut qu’il n’y ait pas de transfert à l’équipe d’opérations cloud pendant plusieurs années. Dans ces cas, l’équipe de développement fait office de propriétaire technique de la charge de travail.

En raison du facteur temps et des contraintes de capital associées, les options de développement personnalisé sont souvent limitées aux opportunités à haute valeur ajoutée. Les innovations applicatives, l’analyse approfondie des données ou les fonctions métier critiques sont des exemples typiques de cela.

### <a name="breakfix-or-sunset-development"></a>Rupture/correction ou développement de temporisation

Une fois qu’une charge de travail développée sur mesure atteint sa maturité maximale, l’équipe de développement peut être réaffectée à d’autres projets. Dans ces cas, la propriété technique passe généralement à une équipe d’opérations cloud. Si de petites corrections sont nécessaires, l’équipe d’opérations fait appel à des développeurs.

Dans certains cas, l’équipe de développement passe à un projet destiné à remplacer la charge de travail actuelle. Elle peut également passer à autre chose pour la simple raison que l’opportunité commerciale à laquelle répond la charge de travail disparaît progressivement. Ce sont là des exemples de scénarios de temporisation, où l’équipe d’opérations cloud fait office de propriétaire technique jusqu’à ce que la charge de travail ne soit plus nécessaire.

Dans les deux scénarios, l’équipe d’opérations cloud fait généralement office de propriétaire technique et de décisionnaire à long terme. Elle recrute également des développeurs d’applications quand des changements opérationnels nécessitent des modifications d’architecture conséquentes.

### <a name="mission-critical-workloads"></a>Charges de travail critiques

Au sein de chaque entreprise, il existe des charges de travail dont l’importance est telle qu’elles ne peuvent absolument pas échouer. Ces charges de travail critiques sont généralement associées à des propriétaires d’opérations et de développement exerçant divers niveaux de responsabilité. Ces équipes doivent aligner les changements opérationnels et architecturaux pour minimiser les perturbations de la solution de production. Ces scénarios nécessitent une forte concentration sur la séparation des tâches. À cette fin, l’équipe d’opérations est généralement responsable des changements opérationnels quotidiens dans l’environnement de production. Lorsque ces changements opérationnels nécessitent une modification architecturale, ils sont effectués par l’équipe de développement ou d’adoption dans un environnement hors production, avant que l’équipe d’opérations les applique à la production.

Les charges de travail critiques nécessitant une séparation des tâches ont trait, par exemple, à des solutions SAP, Oracle ou d’autres solutions d’ERP, qui concernent plusieurs unités commerciales au sein de l’entreprise.

## <a name="strategy-portfolio-alignment"></a>Alignement du portefeuille stratégique

Comme indiqué dans l’article sur l’équilibrage du portefeuille, il est important de comprendre les objectifs stratégiques de l’effort d’adoption du cloud et d’aligner le portefeuille pour la prise en charge de cette transformation. Quelques types courants d’alignements du portefeuille stratégique contribuent à la structuration de la hiérarchie du portefeuille. Les sections suivantes fournissent des exemples d’alignement du portefeuille et d’impact sur la hiérarchie de celui-ci.

### <a name="innovation-or-development-led-portfolio"></a>Portefeuille guidé par l’innovation ou le développement

Certaines entreprises, en particulier les start-ups connaissance une croissance rapide, ont un pourcentage de projets de développement personnalisé supérieur à la moyenne. Dans des portefeuilles chargés en matière de développement, l’environnement, la zone d’atterrissage et les charges de travail sont souvent compressés. Il peut y avoir des environnements (de production ou non) spécifiques dédiés à des charges de travail spécifiques. Il en résulte un rapport un à un entre l’environnement, la zone d’atterrissage et la charge de travail. De plus, étant donné que l’environnement héberge des solutions personnalisées, le pipeline de DevOps et la création de rapports au niveau application peuvent remplacer le besoin de fonctions pour les opérations et la gouvernance. Pour ces clients, une concentration réduite sur les opérations, la gouvernance ou d’autres rôles associés est probable. Il est également fréquent de mettre davantage l’accent sur les responsabilités des équipes d’adoption et d’automatisation cloud.

**Alignement du portefeuille :** le portefeuille informatique se concentrera probablement sur les charges de travail et les propriétaires de charges de travail pour prendre des décisions critiques en matière d’architecture. Ces équipes trouveront probablement plus de valeur dans la guidance de l’Infrastructure Azure Architecture lors des activités d’adoption et d’opérations.
**Définitions de limites :** les limites logiques, même au niveau entreprise, se concentreront probablement sur la segmentation des environnements de production et hors production. Il peut également y avoir une segmentation claire entre produits dans le portefeuille de logiciels des entreprises. Parfois, il peut également y avoir une segmentation entre le développement et les instances clientes hébergées.

### <a name="operations-led-portfolio"></a>Portefeuille guidé par les opérations

Les organisations internationales disposant d’équipes d’opérations informatiques plus établies se concentrent généralement davantage sur la gouvernance et les opérations que sur le développement. Dans ces organisations, un pourcentage plus élevé de charges de travail s’aligne généralement sur les catégories de rupture/correction ou du commerce gérées par des propriétaires techniques au sein de l’équipe d’opérations cloud.

**Alignement du portefeuille :** le portefeuille informatique est aligné sur les charges de travail, mais celles-ci sont à leur tour alignées sur des unités opérationnelles ou commerciales. Il peut également y avoir une organisation autour d’exigences de segmentation liées aux modèles de financement, au secteur ou autres.
**Définitions de limites :** les zones d’atterrissage regrouperont probablement des applications dans des archétypes d’application pour conserver des opérations similaires dans une segmentation similaire. Les environnements feront probablement référence à des constructions physiques telles qu’un centre de données, une nation, une région de fournisseur de cloud ou d’autres normes d’organisation opérationnelle.

### <a name="migration-led-portfolio"></a>Portefeuille guidé par la migration

À l’instar des portefeuilles guidés par les opérations, un portefeuille largement constitué via une migration est basé sur des moteurs commerciaux spécifiques qui ont conduit à la migration de ressources existantes. En règle générale, le centre de données est le principal facteur de ces moteurs.

**Alignement du portefeuille :** le portefeuille informatique peut être aligné sur la charge de travail, mais il est plus probable qu’il soit aligné sur les ressources. Si des transitions vers des opérations informatiques se sont produites dans l’histoire de l’entreprise, il se peut que le mappage de nombreuses ressources activement utilisées vers une charge de travail financée ne soit pas aisé. Dans ces cas, de nombreuses ressources peuvent ne pas avoir de charge de travail définie ou effacer le propriétaire de la charge de travail jusqu’à un stade tardif du processus de migration.
**Définitions de limites :** les zones d’atterrissage regrouperont probablement les applications dans des limites reflétant la segmentation locale. Bien qu’il ne s’agisse pas d’une meilleure pratique, les environnements correspondent souvent au nom du centre de données local et aux zones d’atterrissage qui représentent des pratiques de segmentation du réseau. Il est préférable d’adhérer à une segmentation qui s’aligne plus étroitement avec un portefeuille guidé par les opérations.

### <a name="governance-led-portfolio"></a>Portefeuille guidé par la gouvernance

L’alignement sur des équipes de gouvernance doit avoir lieu le plus tôt possible. En utilisant des pratiques de gouvernance et des outils de gouvernance cloud, les portefeuilles et les limites environnementales peuvent équilibrer au mieux les besoins d’efforts en matière d’innovation, d’opérations et de migration.

- **Alignement du portefeuille :** les portefeuilles guidés par la gouvernance ont tendance à inclure des points de données qui capturent des détails d’innovation et d’opérations, tels que la charge de travail, le propriétaire des opérations, la classification des données et la criticité opérationnelle. Ces points de données créent une vue complète du portefeuille.
- **Définitions de limites :** les limites d’un portefeuille guidé par la gouvernance tendent à privilégier les opérations par rapport à l’innovation tout en utilisant une hiérarchie dirigée par le groupe de gestion qui correspond aux critères d’unité commerciale et d’environnement de développement. À chaque niveau de la hiérarchie, une limite de gouvernance cloud peut recevoir différents degrés d’application de stratégie pour permettre le développement et la flexibilité créative. Dans le même temps, des exigences de qualité de production peuvent être appliquées à des abonnements de production pour assurer la séparation des tâches et la cohérence des opérations.
