---
title: "Bien démarrer : Créer un centre d'excellence du cloud"
description: Ce guide aide une équipe chargée d'un centre d'excellence du cloud à identifier l'étendue, les livrables et les fonctionnalités requises pour réussir l'adoption du cloud.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.topic: conceptual
ms.date: 04/04/2020
ms.openlocfilehash: 59e01530d66fe55e76123a6de229944b4259175c
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230393"
---
<!-- cSpell:ignore deprioritize -->

# <a name="get-started-build-a-cloud-center-of-excellence"></a>Bien démarrer : Créer un centre d'excellence du cloud

Un centre d'excellence de cloud (CCoE) crée un équilibre entre vitesse et stabilité.

Un CCoE peut accélérer les efforts d'innovation et de migration tout en réduisant le coût global du changement et en améliorant l'agilité de l'entreprise. Il peut nettement accélérer le délai de commercialisation. À mesure que les pratiques collectives évoluent, les indicateurs de qualité tels que la fiabilité, l'efficacité des performances, la sécurité, la maintenabilité et la satisfaction client s'améliorent. Ces gains d'efficacité, d'agilité et de qualité sont particulièrement importants si votre entreprise prévoit une migration cloud à grande échelle ou si elle souhaite utiliser le cloud pour stimuler les innovations associées à la différenciation du marché.

Un modèle CCoE crée également un changement culturel important au niveau informatique. Dans une approche CCoE, l’informatique joue fondamentalement le rôle de courtier de services, de partenaire ou de représentant pour l’entreprise. Il s'agit d'un changement de paradigme par rapport à la vision traditionnelle de l'informatique en tant qu'unité d'opérations ou couche d'abstraction entre l'entreprise et les ressources informatiques.

En l'absence d'approche CCoE, l'informatique a tendance à mettre l'accent sur le contrôle et la responsabilité centrale, qui agissent comme des feux de circulation à une intersection. Lorsque le CCoE réussit, l’accent est mis sur la liberté et la délégation de responsabilités, ce qui ressemble davantage à un rond-point qu’à un carrefour classique. Aucune des deux approches n'est bonne ou mauvaise, il s'agit simplement de visions alternatives de la responsabilité et de la gestion. Si vous souhaitez établir un modèle libre-service qui permet aux unités opérationnelles de prendre leurs propres décisions tout en respectant un ensemble de lignes directrices et de contrôles établis et reproductibles, un modèle de CCoE peut s'inscrire dans votre stratégie technologique.

## <a name="prerequisites"></a>Prérequis

- Assurez-vous que votre entreprise a une réelle volonté de croissance et que le service informatique est disposé à déléguer les responsabilités centrales. Comme indiqué ci-dessus, le but d’un CCoE est d’échanger le contrôle contre de l’agilité et de la vitesse.
- Assurez-vous d'avoir le soutien des dirigeants et des principales parties prenantes.

## <a name="minimum-scope"></a>Étendue minimale

Le principal objectif de l’équipe du CCoE est d’accélérer l’adoption du cloud via des solutions cloud ou hybrides.

L’objectif du CCoE est de :

- Aider à construire une organisation informatique moderne grâce à des approches agiles pour saisir et mettre en œuvre les exigences de l’entreprise.
- Utiliser des packages de déploiement réutilisables qui s’alignent sur les stratégies de sécurité, de conformité et d’administration des services.
- Gérer une plateforme Azure fonctionnelle en l’alignant sur des procédures opérationnelles.
- Passer en revue et approuver l’utilisation des outils cloud natifs.
- Au fil du temps, normaliser et automatiser les solutions et les composants de plateforme couramment requis.

## <a name="deliverables"></a>Livrables

L’accélération des efforts du CCoE est possible avec le soutien des parties prenantes de l’entreprise. Les efforts du CCoE sont consacrés à des améliorations à long terme de l'agilité et de la rapidité d'action de l'entreprise. La définition de l’impact des modèles d’exploitation actuels et la valeur des améliorations sont utiles en tant qu’outil de négociation et guide pour le CCoE.

Documentez ce qui suit :

- Établissez un ensemble de résultats et d’objectifs opérationnels qui sont attendus en raison de l’agilité et de la rapidité de l’entreprise.
- Définissez clairement les points faibles créés par les processus informatiques actuels (tels que la vitesse, l’agilité, la stabilité et les défis liés aux coûts).
- Définissez clairement l’impact historique de ces points faibles (tels que la perte de parts de marché, les gains des concurrents en termes de fonctionnalités et de fonctions, les mauvaises expériences client et les augmentations de budget).
- Définissez les opportunités d’amélioration de l’entreprise qui sont bloquées par les points faibles et les modèles opérationnels actuels.
- Établissez des chronologies et des métriques liées à ces opportunités.

Ces points de données ne constituent pas une attaque contre l’informatique. Ils aident plutôt le CCoE à tirer les leçons du passé et à établir un backlog réaliste et un plan d’amélioration.

### <a name="solutions-and-controls"></a>Solutions et contrôles

Chaque membre du CCoE est chargé de comprendre les contraintes, les risques et les protections nécessaires qui ont conduit à l’ensemble actuel des contrôles informatiques. Les efforts collectifs du CCoE devraient transformer cette compréhension en solutions ou en contrôles natifs (ou hybrides) du cloud, qui permettent d’obtenir les résultats métier souhaités en libre-service. À mesure que des solutions sont créées, elles sont partagées avec diverses équipes sous forme de contrôles ou de processus automatisés qui servent de garde-fous pour divers efforts. Ces garde-fous permettent d’orienter les activités gratuites des différentes équipes, tout en déléguant des responsabilités aux participants dans les différents efforts de migration ou d’innovation.

Exemples de cette transition :

| Scénario | Solution pré-CCoE | Solution post-CCoE |
|---------|---------|---------|
| Approvisionner un serveur SQL Server de production | Les équipes réseau, informatique et de plateforme de données approvisionnent différents composants durant plusieurs jours, voire plusieurs semaines. | L’équipe qui demande le serveur déploie une instance PaaS d’Azure SQL Database. Vous pouvez également utiliser un modèle pré-approuvé pour déployer toutes les ressources IaaS dans le cloud en quelques heures. |
| Approvisionner un environnement de développement | Les équipes chargées des réseaux, des technologies de l'information, du développement et des DevOps s'entendent sur les spécifications et déploient un environnement. | L’équipe de développement définit ses propres spécifications et déploie un environnement basé sur le budget alloué. |
| Mettre à jour les exigences de sécurité pour améliorer la protection des données | Les équipes chargées de la mise en réseau, de l’informatique et de la sécurité mettent à jour différents appareils réseau et machines virtuelles dans plusieurs environnements afin d’ajouter des protections. | Les outils de gouvernance du cloud permettent de mettre à jour les stratégies qui peuvent être appliquées immédiatement à toutes les ressources dans tous les environnements cloud. |

### <a name="negotiations"></a>Négociations

Chaque effort du CCoE repose sur un processus de négociation continu. L’équipe CCoE négocie avec les fonctions informatiques existantes pour réduire le contrôle central. Dans cette négociation, les compromis pour l’entreprise sont la liberté, l’agilité et la rapidité. La valeur du compromis pour les équipes informatiques existantes est fournie sous la forme de nouvelles solutions. Les nouvelles solutions offrent à l’équipe informatique existante un ou plusieurs des avantages suivants :

- Possibilité d’automatiser les problèmes courants.
- Amélioration de la cohérence (réduction des frustrations quotidiennes).
- Possibilité d’apprendre et de déployer de nouvelles solutions techniques.
- Réduction des incidents de gravité élevée (moins de correctifs rapides ou de réponses aux demandes d’intervention urgente).
- Possibilité d’élargir son étendue technique, en traitant des sujets plus larges.
- Participation à des solutions d’entreprise de niveau supérieur, en traitant l’impact de la technologie.
- Réduction des tâches de maintenance subalternes.
- Augmentation de la stratégie technologique et de l’automatisation.

En échange de ces avantages, la fonction informatique existante peut échanger les valeurs suivantes, qu'elles soient réelles ou perçues :

- Sentiment de contrôle des processus d’approbation manuels.
- Sentiment de stabilité grâce au contrôle des changements.
- Sentiment de sécurité du travail comme suite à l’exécution de tâches nécessaires mais répétitives.
- Sentiment de cohérence qui découle de l’adhésion aux fournisseurs de solutions informatiques existants.

Dans les entreprises saines désireuses d’adopter le cloud, ce processus de négociation est une conversation dynamique entre les pairs et les équipes informatiques partenaires. Les détails techniques peuvent être complexes, mais ils sont gérables lorsque le service informatique comprend parfaitement l'objectif et appuie les efforts du CCoE.

### <a name="meeting-cadence"></a>Cadence des réunions

Le CCoE est une fonction composée d'équipes très sollicitées. Il est important de permettre une collaboration organique et de suivre la croissance grâce à un référentiel/catalogue de solutions commun. Optimiser les interactions naturelles mais réduire le nombre de réunions. Lorsque cette fonction arrive à maturité, les équipes doivent tenter de limiter les réunions dédiées. La participation à des réunions récurrentes, telles que les réunions de mise en place hébergées par l’équipe d’adoption du cloud, fournira des entrées de données. En parallèle, une réunion après chaque plan de publication est partagée peut fournir un point tactile minimal pour cette équipe.

**Soutien et engagement des parties prenantes de l'entreprise :** Les équipes du CCoE peuvent faire la preuve d’une grande réactivité dans certains domaines. Cependant, les objectifs de haut niveau, comme l’agilité commerciale et le délai de commercialisation, peuvent prendre beaucoup plus de temps. Au cours de la maturation, il existe un risque élevé que le CCoE se décourage ou soit découragé de se concentrer sur d’autres efforts informatiques.

Au cours des six à neuf premiers mois des efforts du CCoE, nous recommandons que les intervenants opérationnels allouent du temps pour rencontrer mensuellement les dirigeants informatiques et le CCoE. Ces réunions peuvent être mises en place de façon flexible. Le simple fait de rappeler aux membres du CCoE et à leurs dirigeants l’importance de ce programme peut contribuer grandement au succès du CCoE.

De plus, nous recommandons que les parties prenantes de l’entreprise s’informent sur les progrès et les obstacles rencontrés par l’équipe du CCoE. La plupart de leurs efforts sembleront porter sur des détails techniques. Toutefois, il est important que les intervenants opérationnels comprennent la progression du plan afin qu’ils puissent s’engager lorsque l’équipe s’essouffle ou se laisse distraire par d’autres priorités.

**Les parties prenantes informatiques soutiennent la vision :** Le succès des efforts du CCoE nécessite beaucoup de négociations avec les membres actuels de l’équipe informatique. Lorsque le processus se passe bien, toute l’informatique contribue à la solution et se sent à l’aise avec le changement. Lorsque ce n'est pas le cas, certains membres de l'équipe informatique existante peuvent vouloir s'en tenir aux mécanismes de contrôle pour diverses raisons. Le soutien des parties prenantes informatiques est essentiel au succès du CCoE lorsque de telles situations se produisent. Il est important d’encourager et de renforcer les objectifs généraux du CCoE pour surmonter les obstacles à une négociation adéquate. En de rares occasions, les parties prenantes informatiques peuvent même avoir besoin d'intervenir et de sortir d'une impasse ou d'une égalité de voix pour que le CCoE continue de progresser.

**Les parties prenantes informatiques soutiennent les priorités :** Un CCoE peut représenter un engagement important pour toute équipe informatique aux ressources limitées. Le fait de retirer les architectes expérimentés des projets à court terme pour se concentrer sur les gains à long terme risque de poser des difficultés aux membres de l’équipe qui ne font pas partie du CCoE. Les dirigeants et les parties prenantes informatiques doivent demeurer concentrés sur l’objectif du CCoE. L’appui des dirigeants et des parties prenantes informatiques est nécessaire pour éviter que les opérations quotidiennes soient perturbées au profit des tâches du CCoE.

**Les parties prenantes informatiques fournissent protection et responsabilité :** L’équipe du CCoE expérimentera de nouvelles approches. Certaines de ces approches ne s’harmoniseront pas bien avec les opérations existantes ou les contraintes techniques. Il existe un risque réel que le CCoE subisse des pressions ou des recours de la part d’autres équipes en cas d’échec des expériences. Il est important d'encourager l'équipe et de la mettre à l'abri des conséquences des opportunités d'apprentissage « Fail-fast ». Il est tout aussi important de tenir l’équipe responsable de sa volonté de croissance, de s’assurer qu’elle tire des leçons de ces expériences et de trouver de meilleures solutions.

## <a name="baseline-capability"></a>Fonctionnalités de base

Un modèle CCoE nécessite une collaboration entre chacune des fonctionnalités suivantes :

- Adoption du cloud (plus précisément, les architectes de solutions).
- Stratégie cloud (plus précisément, les chefs de projet et les responsables de programme).
- Gouvernance cloud.
- Plateforme cloud.
- Automatisation du cloud.

Ce modèle nécessite également le soutien des dirigeants et des principales parties prenantes.

La direction informatique est la première et la plus évidente des parties prenantes. Les responsables informatiques jouent un rôle important. Cependant, ce processus requiert le soutien du responsable des investissements et des cadres informatiques.

Celui des parties prenantes de l’entreprise est moins évident. L'agilité et le délai de commercialisation de l'entreprise sont les principales motivations pour former un CCoE. Parmi les parties prenantes de l’entreprise, citons les dirigeants, les cadres financiers, les cadres d’exploitation et les propriétaires de produits professionnels.

## <a name="whats-next"></a>Étapes suivantes

Un modèle CCoE nécessite des [fonctionnalités de la plateforme cloud](./cloud-platform.md) et des [fonctionnalités d'automatisation du cloud](./cloud-automation.md). La prochaine étape consiste à aligner les [fonctionnalités de la plateforme cloud](./cloud-platform.md).
