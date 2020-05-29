---
title: Équilibrer les priorités concurrentes
description: Découvrez les stratégies d’équilibrage des priorités concurrentes.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 7a09f6fe1dd337d1c42eb193cc23c9aa9519e6b9
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83815410"
---
# <a name="balance-competing-priorities"></a>Équilibrer les priorités concurrentes

Le choix d’une transformation numérique est souvent perçu comme une contrainte par les parties prenantes des équipes commerciales et technologiques. La réussite d’une organisation dépend largement de sa capacité à équilibrer les priorités concurrentes.

À l’instar d’autres transformations numériques, l’adoption du cloud expose des priorités concurrentes tout au long du cycle de vie de l’adoption. Comme pour d’autres formes de transformation, la capacité à trouver un juste équilibre entre ces priorités a un impact significatif sur l’obtention d’une valeur métier. L’équilibrage de ces priorités concurrentes nécessite des conversations ouvertes, parfois difficiles, entre les parties prenantes (et de temps à autre avec des contributeurs individuels).

Cet article décrit certaines des priorités concurrentes communément abordées durant l’exécution de chaque méthodologie. Nous espérons que cette prise de conscience vous aidera à mieux vous préparer aux discussions à venir lors du développement de votre stratégie d’adoption du cloud.

<!-- cSpell:ignore caf -->

![Vue d’ensemble du cycle de vie de l’adoption du cloud](../_images/caf-overview.png)

Les sections suivantes reflètent le flux du cycle de vie d’adoption du cloud ci-dessus. Toutefois, il est important de reconnaitre que l’adoption du cloud est un processus itératif (et non séquentiel) et que ces priorités concurrentes apparaissent (et parfois réapparaissent) à différents moments de votre parcours d’adoption du cloud.

## <a name="general-theme-of-the-cloud-adoption-framework-approach"></a>Thème général de l’approche du Cloud Adoption Framework

Les solutions monolithiques et la planification avancée reposent sur une série d’hypothèses qui peuvent (ou non) se révéler exactes au fil du temps. L’adoption du cloud est souvent une nouvelle expérience pour l’entreprise et les équipes techniques. Comme pour la plupart des nouvelles expériences et opportunités d’apprentissage, il est fort probable que ces hypothèses se révèlent fausses.

L’adoption de principes agiles éprouvés faisant suite à des décisions techniques différées est l’approche à privilégier pour la plupart des instructions de ce framework. Cette approche suit un processus cohérent : établir un état final général, passer rapidement à l’implémentation initiale, tester et valider des hypothèses et enfin refactoriser tôt pour évaluer les hypothèses. Cet état d’esprit axé sur le développement maximise l’apprentissage et minimise les risques pour la valeur métier. Il requiert cependant une certaine tolérance de l’ambiguïté.

Parfois, l’ambiguïté peut être plus effrayante (voire plus dangereuse) que de fausses hypothèses. Bien que ce framework privilégie l’apprentissage et l’élimination de l’ambiguïté durant l’exécution, de nombreuses situations nécessitent que l’équipe se tourne vers des approches basées sur des analyses ou des hypothèses. Dans les sections suivantes, nous tentons de présenter au moins un « exemple d’étendue développée » pour illustrer les cas de figure où une seconde itération plus approfondie est justifiée.

## <a name="balance-during-the-strategy-phase"></a>Équilibrage pendant la phase de stratégie

L’objectif principal de la méthodologie de stratégie est de développer l’alignement entre les parties prenantes. Une fois définie, cette position stratégique alignée favorise des comportements dans chacune des méthodologies pour garantir l’adéquation entre les décisions techniques et les résultats métier souhaités. Le fait d’encourager l’alignement entre les parties prenantes crée un ensemble commun de priorités concurrentes : la **profondeur de la justification** et le **délai avant l’impact commercial**.

**Priorités concurrentes** :

- **Profondeur de la justification :** Avant de pouvoir prendre une direction stratégique, les parties prenantes exigent souvent une analyse financière approfondie et une justification métier complète. Malheureusement, la collecte et l’analyse des données peuvent engendrer des délais.
- **Délai avant l’impact commercial :** Inversement, les parties prenantes sont souvent tenues pour responsables de l’obtention de résultats métier dans des délais d’exécution fixés. Les opérations d’analyse et d’évaluation qui prennent du temps peuvent mettre en danger l’obtention de ces résultats avant même le début du travail technique.

**Étendue minimale** : Pour parvenir à cet équilibre, les parties prenantes doivent entamer des discussions au début du processus. La méthodologie de stratégie suggère de limiter l’étendue de l’alignement durant ces premiers efforts. Dans l’approche suggérée, les parties prenantes tentent de s’aligner autour d’un ensemble de motivations de base, de résultats mesurables et d’une justification métier générale. Les parties prenantes doivent s’engager rapidement sur un petit nombre de projets initiaux ou de pilotes pour mettre en avant les opportunités d’apprentissage requises.

**Exemple d’étendue développée** : Si l’analyse métier initiale indique un risque élevé d’influence négative sur l’entreprise, les parties prenantes peuvent être contraintes de ralentir et d’évaluer avec prudence une analyse plus poussée durant la justification métier.

## <a name="balance-during-the-plan-phase"></a>Équilibrage pendant la phase de planification

À l’instar des priorités de la phase de stratégie, au cours de la phase de planification, il est nécessaire d’équilibrer la profondeur de la planification initiale en fonction des décisions techniques retardées.

**Priorités concurrentes** :

- La **profondeur de la planification initiale** concernant l’implémentation technique dans le cloud contient souvent un grand nombre d’hypothèses. Cela est particulièrement vrai si l’équipe a des lacunes en matière de compétences, si l’environnement souffre de décalages dans le domaine de la découverte ou si les états finaux sur le plan architectural ne sont pas clairement définis. Toutes ces hypothèses sont courantes dans les plans détaillés d’adoption du cloud. La mise en place d’expérimentations, de pilotes et d’analyses qualitatives est nécessaire pour éliminer ces hypothèses.
- Les **décisions techniques différées** reposent sur le fait que plus la décision technique peut être retardée, plus elle est précise. Le respect des principes de planification de produit agile contribue à retarder les décisions techniques. Elles sont donc prises au bon moment, avec suffisamment d’informations. Toutefois, cette approche entraîne un degré d’ambiguïté nettement plus élevé dans le plan initial.

**Étendue minimale** : Des approches de développement de produit agile sont suggérées pour favoriser des actions rapides dans des plans gérables. La méthodologie de planification recommande les étapes suivantes pour atteindre cet équilibre. Inventoriez l’ensemble de l’espace numérique à l’aide d’outils de découverte automatisés, mais utilisez la rationalisation incrémentielle pour planifier les 1 à 3 prochains mois de travail. Veillez au bon alignement de l’organisation pour pouvoir agir rapidement. Créez un plan de préparation des compétences pour l’équipe affectée. Utilisez le modèle de plan d’adoption du cloud pour déployer rapidement un backlog initial.

**Exemple d’étendue développée** : Parfois, la mise en place d’un plan d’adoption du cloud peut répondre à un événement commercial urgent ou à fort impact. Quand la réussite passe par le déplacement d’un grand nombre de ressources pendant une période fixe, les étapes ci-dessus sont souvent suivies d’un effort de planification plus soutenu. La clé du succès dans ces scénarios est de planifier suffisamment pour lancer la procédure, puis de planifier l’engagement complet. Cette approche réduit la probabilité d’un blocage des résultats métier causé par la planification.

## <a name="balance-during-the-ready-phase"></a>Équilibrage pendant la phase Ready (Prêt)

Quand les équipes d’adoption se préparent à faire leurs premiers pas dans le cloud, elles sont souvent confrontées à des priorités concurrentes entre le délai d’adoption et les opérations à long terme. L’équipe peut avoir du mal à honorer ses impératifs tout en assurant la bonne gestion de ses activités. Ce conflit est nécessaire dans les environnements informatiques traditionnels, où l’acte de développement d’une plateforme passe par des ressources physiques et des cycles d’acquisition. Toutefois, quand la plateforme informatique est entièrement définie dans le code, les tactiques de développement traditionnelles (comme la refactorisation) réduisent la nécessité d’une bonne gestion initiale.

**Priorités concurrentes** :

- **Opérations à long terme** : Les clients sont souvent bloqués par la volonté d’avoir un environnement cloud qui répond à la parité des fonctionnalités avec les systèmes actuels de gestion des opérations, de gouvernance et de sécurité. Dans une étude récente, plus de 90 % des clients ont déclaré avoir eu besoin d’aide pour surmonter cette difficulté. Cet inhibiteur peut provoquer des mois de retard, repoussant voire éliminant l’impact métier.
- **Durée d’adoption** : Les outils basés sur le cloud, comme Azure Policy, Azure Blueprints et les groupes d’administration, facilitent la refactorisation dans l’ensemble de la plateforme informatique. Des zones d’atterrissage prédéfinies fournissent également des positions optimisées pour accélérer le déploiement sur un environnement qui répond déjà à de nombreuses exigences en matière de parité des fonctionnalités. Il est donc possible d’accélérer le délai de commercialisation avec un impact minimal sur les opérations à long terme.

**Étendue minimale** : La méthodologie de préparation établit une voie directe entre adoption rapide et opérations à long terme. Cette approche commence par une présentation de base des outils permettant de refactoriser l’environnement. En fonction de ces outils et des exigences environnementales, les clients sont dirigés vers une sélection de zones d’atterrissage prédéfinies (chacune étant fournie à l’aide de modèles Infrastructure as Code). Ce code peut ensuite être refactorisé au cours de l’adoption du cloud pour améliorer les opérations, la sécurité et les postures de gestion.

<!-- docsTest:ignore "Govern and Manage methodologies" -->

**Exemple d’étendue développée** : Pour les équipes dont le plan d’adoption prévoit à moyen terme (dans les 24 mois) d’héberger **plus de 1 000 ressources (applications, infrastructures ou ressources de données) dans le cloud**, une vue plus fiable des zones d’atterrissage est suggérée. Dans ces situations, les méthodologies de gouvernance et de gestion doivent être prises en compte durant les conversations initiales sur les zones d’atterrissage. Cependant, cette considération plus approfondie ajoute souvent des semaines ou des mois à un plan d’adoption du cloud. Pour minimiser l’impact sur les résultats métier, l’équipe d’adoption doit piloter les charges de travail réelles dans le cloud parallèlement à la création d’une zone d’atterrissage plus avancée et d’une solution d’architecture centrale.

## <a name="balance-during-the-migrate-phase"></a>Équilibrage pendant la phase de migration

Lors des efforts de migration, il est courant pour les équipes d’adoption de supposer que les charges de travail seront réhébergées « telles quelles » dans le cloud, dans leur configuration actuelle. Cette approche entre directement en concurrence avec la démarche prospective selon laquelle il est nécessaire de réarchitecturer chaque charge de travail pour mieux tirer parti des capacités du cloud. Néanmoins, les deux ne sont pas mutuellement exclusives et peuvent être complémentaires si elles sont gérées par le biais d’un processus commun.

**Priorités concurrentes** :

- **Réhébergement :** Les clients assimilent souvent la migration à un mouvement _lift-and-shift_ consistant à répliquer toutes les ressources dans le cloud dans leur configuration actuelle. Il en résulte une dérive minime au sein du portefeuille informatique. Cette approche est également le moyen le plus rapide de mettre hors service des ressources dans un centre de données existant.
- **Réarchitecture :** La modernisation de l’architecture de chaque charge de travail maximise la valeur du cloud en termes de coûts, de performances et d’opérations. Cependant, cette approche est beaucoup plus lente et nécessite souvent l’accès au code source de chaque application.

**Étendue minimale** : Lors des étapes préliminaires de planification, utilisez l’option de réhébergement pour la planification. Sachez toutefois que cette option est une hypothèse métier initiale et non une décision technique. Dans la méthodologie de migration, il est à prévoir que l’équipe d’adoption conteste cette hypothèse pour chaque charge de travail migrée. Cette méthodologie suit les approches d’évaluation, de migration et de promotion pour chaque charge de travail, groupe ou charge de travail créant une fabrique de migration. Pendant la phase d’évaluation, l’équipe d’adoption évalue l’adéquation technique et l’architecture de chaque charge de travail. Ce travail d’évaluation entraîne rarement une approche « lift-and-shift » pure, car la plupart des composants de l’architecture ont tendance à être sélectionnés pour refactorisation et modernisation.

**Exemple d’étendue développée** : Pour les charges de travail critiques ou très sensibles, comme celles émanant d’un ordinateur mainframe ou d’une application de microservices multiniveau, une évaluation plus approfondie de la charge de travail peut être nécessaire pendant la phase d’évaluation. Dans ces situations de réarchitecture, les clients doivent utiliser Microsoft Azure Well-Architected Review et Microsoft Azure Well-Architected Framework pour affiner les exigences de la charge de travail pendant l’évaluation.

## <a name="balance-during-the-innovate-phase"></a>Équilibrage pendant la phase d’innovation

Une véritable innovation orientée client crée des priorités concurrentes entre la nécessité de fournir un ensemble de fonctionnalités planifiées et un processus de développement reposant sur l’empathie envers les clients.

**Priorités concurrentes** :

- **Focus sur les fonctionnalités :** Les plans initiaux en matière d’innovation s’appuient sur les fonctionnalités existantes de l’espace numérique et du cloud pour établir un ensemble de fonctionnalités répondant aux besoins des clients. Il est facile de paramétrer le plan de manière à privilégier l’implémentation technique, d’où des efforts de développement axés sur les fonctionnalités. Cette approche aboutit souvent à la satisfaction temporaire des parties prenantes, mais réduit la probabilité de stimuler des innovations ayant un impact sur les comportements des clients.
- **Empathie envers les clients :** Les plans initiaux constituent une partie importante de l’aspect métier du développement et doivent être inclus dans les comptes rendus réguliers. Toutefois, l’empathie manifestée envers les clients lors des phases d’apprentissage, de mesure et de création est une mesure plus précise de la réussite d’un effort d’innovation. Le fait de se concentrer sur le client plutôt que sur les fonctionnalités a davantage de chances d’aboutir à la satisfaction du client, à la fois à court terme et à long terme, et d’avoir un impact positif sur l’activité.

**Étendue minimale** : La méthodologie d’innovation montre comment intégrer stratégie et plans grâce à un consensus sur la valeur métier. Le guide présente des outils cloud natifs qui peuvent accélérer chaque discipline d’innovation, puis accompagne les bonnes pratiques en vue de leur implémentation. Enfin, la section sur les améliorations de processus montre les approches à suivre pour développer l’empathie envers les clients tout en respectant les plans et les stratégies du parcours d’adoption du cloud. Cette approche se concentre sur la mise en œuvre de solutions d’innovation en réduisant le plus possible la part de la technologie.

**Exemple d’étendue développée** : Parfois, une innovation peut dépendre de charges de travail critiques hautement sensibles. Lorsque le « client » est un utilisateur interne, l’effort de développement peut être à la fois critique et hautement sensible au cours des premières itérations. Dans ces scénarios, les équipes d’adoption doivent s’appuyer sur Microsoft Azure Well-Architected Review et Microsoft Azure Well-Architected Framework pour évaluer la conception architecturale avancée au début du processus.

## <a name="balance-during-the-govern-phase"></a>Équilibrage pendant la phase de gouvernance

La pratique de la gouvernance du cloud demande un équilibre constant entre deux priorités concurrentes : vitesse et agilité contre environnement bien gouverné. L’équipe de gouvernance du cloud se concentre sur l’évaluation et la minimisation des risques pour l’entreprise grâce à la mise en place de contrôles uniformes et à la minimisation des changements. L’équipe d’adoption se concentre sur l’optimisation des résultats métier, ce qui entraîne de nouveaux risques et crée naturellement des changements.

**Priorités concurrentes** :

- **Bien gouverné :** Chaque contrôle conçu pour minimiser les risques bloque certains aspects du changement ou limite les options de conception. Le contrôle est essentiel à un environnement bien gouverné. Cependant, quand les contrôles sont conçus et déployés de manière isolée, ils peuvent être aussi dangereux que les risques qu’ils sont censés prévenir.
- **Vitesse et agilité :** La vitesse et l’agilité sont des exigences métier fondamentales dans l’économie numérique. Elles nécessitent toutes les deux la capacité de stimuler le changement avec un minimum d’inhibiteurs d’innovation ou d’adoption. Quand le changement est conduit indépendamment de la gouvernance, il génère de nouveaux risques qui peuvent nuire à l’entreprise de manière involontaire.

**Étendue minimale** : La méthodologie de gouvernance suggère que ni la gouvernance ni l’adoption ne doivent se produire de manière isolée. Cette méthodologie commence par la compréhension des disciplines de gouvernance et par une conversation sur les risques, les politiques et les processus métier. En tant que membre actif tout au long du parcours d’adoption du cloud, l’équipe de gouvernance peut implémenter un ensemble minimum de garde-fous pour faire face aux risques tangibles dans le plan d’adoption du cloud. Au fil du temps, l’équipe de gouvernance peut refactoriser et étendre ces garde-fous pour répondre à de nouveaux risques. Cette approche optimise l’apprentissage et l’innovation tout en minimisant les risques.

**Exemple d’étendue développée** : Quand le risque métier est élevé, en particulier au début de la phase d’adoption, l’équipe de gouvernance du cloud peut être amenée à accélérer l’expansion des implémentations de gouvernance. Les mêmes instructions et exercices peuvent servir à rehausser le niveau de gouvernance, mais il peut être nécessaire de rapprocher les échéances. Dans certains scénarios, un état avancé de gouvernance peut même être requis durant le déploiement des premières zones d’atterrissage.

## <a name="balance-during-the-manage-phase"></a>Équilibrage pendant la phase de gestion

Le modèle économique du service informatique en matière de gestion des opérations n’a cessé d’évoluer au cours de la dernière décennie. À mesure que la maintenance du matériel s’éloigne des tâches de base du service informatique, la vision de la gestion des opérations change aussi. Alors que le service informatique se concentre davantage sur la création de valeur métier, les équipes de gestion des opérations doivent trouver un équilibre entre deux stratégies contradictoires : « no ops/low ops » (pas d’opérations/opérations réduites) contre mise en œuvre de vastes investissements.

**Priorités concurrentes** :

- **Investissements étendus :** La vision traditionnelle de la gestion des opérations consiste à investir de manière égale dans la prévention des pannes, la récupération rapide et la supervision de l’environnement. Cette approche peut être coûteuse et parfois faire double emploi avec les produits de prise en charge mis à disposition par le fournisseur de cloud.
- **Non-opérations et faibles opérations :** Utilisez les outils d’exploitation natifs du cloud pour minimiser les tâches répétitives et récurrentes précédemment réalisées par des employés à temps plein. La réduction de ces dépendances opérationnelles dans le modèle de gestion des opérations libère ces employés pour générer plus de valeur. Seule, cette approche peut conduire à une prise en charge inadéquate des opérations.

**Étendue minimale** : La méthodologie de gestion suggère d’établir une ligne de base de gestion « no-ops » (pas d’opérations) native Cloud. Étant donné que cette ligne de base ne permet pas de répondre à tous les besoins métier, collaborez avec l’entreprise pour définir des engagements et mieux aligner les investissements. Développez la base de référence pour répondre aux besoins communs de toutes les charges de travail. Instruisez ensuite aux équipes responsables des plateformes ou de charges de travail spécifiques de mettre en œuvre des solutions bien gérées dans un environnement bien géré.

**Exemple d’étendue développée** : Dans la plupart des environnements, le pourcentage de charges de travail dont la valeur métier justifie des investissements importants de la part du service informatique dans les opérations est faible. Dans ces scénarios, l’équipe informatique peut utiliser Microsoft Azure Well-Architected Review et Microsoft Azure Well-Architected Framework pour mener des opérations plus approfondies.

## <a name="balance-during-the-organize-phase"></a>Équilibrage pendant la phase d’organisation

Les priorités concurrentes énumérées tout au long de cet article reflètent la volonté pour les services informatiques de répondre aux demandes de l’entreprise en termes de rapidité et d’agilité. Ce même décalage se retrouve dans les organigrammes (ou les structures d’équipes virtuelles) pour mieux prendre en charge les résultats métier. À mesure que les responsables informatiques réfléchissent à la structure des équipes, deux priorités concurrentes sont généralement abordées : contrôle centralisé contre contrôle délégué.

**Priorités concurrentes** :

- **Contrôle centralisé :** Ce modèle d’exploitation porte sur la centralisation de tous les contrôles requis pour appliquer des politiques rigides. Dans ce modèle, le service informatique est un frein à l’innovation, à la vitesse et à l’agilité. Cependant, il peut assurer un degré plus élevé de stabilité, de conformité et de sécurité.
- **Contrôle délégué :** Ce modèle d’exploitation distribué part du principe que chaque équipe DevOps ou équipe d’application métier fournit son propre ensemble de contrôles, en fonction des solutions nécessaires pour répondre aux objectifs métier. Dans ce modèle, l’informatique met en place des garde-fous pour maintenir les équipes sur la bonne voie, mais minimise autant que possible les contraintes techniques forcées.

**Étendue minimale** : La plupart des organisations sont confrontées à un ensemble naturel d’évolutions au fil du temps. La méthodologie d’organisation décrit la série d’évolutions la plus courante. Nous suggérons aux équipes de s’efforcer de passer à une structure Centre d’excellence de cloud pour mettre en place des approches de contrôle délégué.

**Exemple d’étendue développée** : Il existe de nombreuses situations qui déclenchent la nécessité d’un contrôle centralisé. Les exigences de conformité tierces et l’exposition temporaire à la sécurité sont deux exemples déclenchant un contrôle centralisé. Dans ces situations, il est généralement nécessaire d’établir des stratégies de limitation et des contrôles rigides et fixes. Cependant, pour assurer la continuité de l’innovation et de l’adoption, les équipes d’informatique centralisée sont encouragées à mettre en œuvre ces contrôles en fonction de l’aspect critique et de la sensibilité de chaque charge de travail. Le fait de créer des environnements avec moins de contrôles, mais avec une étendue ou un profil de risque réduit, offre une certaine flexibilité même lorsque des contrôles sont nécessaires.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [équilibrer la migration, l’innovation et l’expérimentation](./balance-the-portfolio.md) pour optimiser la valeur de vos efforts de migration vers le cloud.

> [!div class="nextstepaction"]
> [Équilibrage du portefeuille](./balance-the-portfolio.md)
