---
title: Rationalisation du cloud
description: Passez en revue les options disponibles pour rationaliser un patrimoine numérique.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/16/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: 1a74487a77388e6260c177096d9563dbe6646cf2
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806558"
---
# <a name="cloud-rationalization"></a>Rationalisation du cloud

La rationalisation du cloud est le processus qui consiste à évaluer des ressources dans le but de déterminer la meilleure manière de migrer ou de moderniser chaque ressource présente dans le cloud. Pour plus d’informations sur le processus de rationalisation, consultez [Qu’est-ce qu’un patrimoine numérique ?](./index.md)

## <a name="rationalization-context"></a>Contexte de la rationalisation

Les cinq R de la rationalisation mentionnés dans cet article constituent un excellent moyen d’étiqueter un état futur potentiel pour toute charge de travail considérée comme candidate pour un transfert dans le cloud. Toutefois, ce processus d’étiquetage doit être placé dans le contexte approprié avant de tenter de rationaliser l’environnement. Passez en revue les mythes suivants pour comprendre le contexte :

- **Mythe : Il est facile de prendre des décisions de rationalisation en début de processus.** Une rationalisation précise requiert une connaissance détaillée de la charge de travail et des ressources associées (applications, machines virtuelles et données). Plus important encore, les décisions de rationalisation précises prennent du temps. Nous vous recommandons d’appliquer un [processus de rationalisation incrémentielle](./rationalize.md#incremental-rationalization).

- **Mythe : L’adoption du cloud doit attendre que toutes les charges de travail soient rationalisées.** La rationalisation de l’intégralité du portefeuille informatique ou même d’un centre de données peut retarder la création de la valeur commerciale de plusieurs mois, voire de plusieurs années. La rationalisation complète doit être évitée dans la mesure du possible. Au lieu de cela, appliquez l’[approche Puissance 10 pour la planification des mises en production](./rationalize.md#release-planning) pour prendre des décisions judicieuses sur les 10 charges de travail à prendre en compte pour l’adoption du cloud.

- **Mythe : La justification métier doit attendre que toutes les charges de travail soient rationalisées.** Pour développer une justification métier pour un effort d’adoption du cloud, émettez quelques hypothèses de base au niveau du portefeuille. Lorsque les motivations sont alignées sur l’innovation, on suppose qu’une réarchitecture est nécessaire. Lorsque les motivations sont alignées sur l’innovation, on suppose qu’un réhébergement est nécessaire. Ces hypothèses peuvent accélérer le processus de justification métier. Les hypothèses sont ensuite contestées et les budgets sont affinés pendant la phase d’évaluation du cycle d’adoption de chaque charge de travail.

Examinez à présent les cinq R de rationalisation suivants pour vous familiariser avec le processus à long terme. Lors du développement de votre plan d’adoption du cloud, choisissez l’option qui convient le mieux à vos motivations, aux résultats pour l’entreprise et à l’environnement actuel. L’objectif de la rationalisation du patrimoine numérique est de définir une ligne de base, et non pas de rationaliser chaque charge de travail.

## <a name="the-five-rs-of-rationalization"></a>Les 5 R de la rationalisation

Les 5 R de la rationalisation listés ici décrivent les options de rationalisation les plus courantes.

## <a name="rehost"></a>Réhébergement

Également appelé migration _lift-and-shift_, le réhébergement déplace une ressource vers le fournisseur de cloud choisi, en apportant des modifications minimales à l’architecture globale.

Les facteurs les plus courants sont les suivants :

- Réduire les dépenses d’investissement
- Libérer de l’espace dans un centre de données
- Accélérer le retour sur investissement dans le cloud

Facteurs d’analyse quantitative :

- Taille de la machine virtuelle (processeur, mémoire, stockage)
- Dépendances (trafic réseau)
- Compatibilité des ressources

Facteurs d’analyse qualitative :

- Tolérance au changement
- Priorités de l’entreprise
- Événements critiques pour l’entreprise
- Dépendances de processus

## <a name="refactor"></a>Refactorisation

Les options PaaS (Platform as a service) permettent de réduire les coûts d’exploitation associés à de nombreuses applications. Il est judicieux de refactoriser légèrement une application pour qu’elle corresponde à un modèle PaaS.

La refactorisation s’applique également au processus de développement d’applications, dans lequel du code est refactorisé pour permettre à une application de répondre à de nouvelles opportunités commerciales.

Les facteurs les plus courants sont les suivants :

- Mises à jour plus rapides
- Portabilité du code
- Une plus grande efficacité du cloud (ressources, vitesse, coût, opérations managées)

Facteurs d’analyse quantitative :

- Taille des ressources d’application (processeur, mémoire, stockage)
- Dépendances (trafic réseau)
- Trafic utilisateur (consultations de page, temps passé sur une page, temps de chargement)
- Plateforme de développement (langages, plateforme de données, services de niveau intermédiaire)
- Base de données (UC, mémoire, stockage, version)

Facteurs d’analyse qualitative :

- Investissements continus
- Options de cloud bursting/Chronologies
- Dépendances des processus métier

## <a name="rearchitect"></a>Réarchitecture

Certaines applications vieillissantes ne sont pas compatibles avec les fournisseurs de cloud, en raison des décisions qui ont été prises concernant l’architecture lors de la conception de l’application. Dans ce cas, l’application doit subir une réarchitecture avant d’être transformée.

Dans d’autres cas, les applications qui sont compatibles avec le cloud mais qui ne sont pas natives dans le cloud peuvent entraîner des problèmes d’efficacité et de coût si vous les réarchitecturez pour en faire des applications natives du cloud.

Les facteurs les plus courants sont les suivants :

- Mise à l’échelle et agilité de l’application
- Adoption facilitée des nouvelles fonctionnalités cloud
- Piles de technologies mixtes

Facteurs d’analyse quantitative :

- Taille des ressources d’application (processeur, mémoire, stockage)
- Dépendances (trafic réseau)
- Trafic utilisateur (consultations de page, temps passé sur une page, temps de chargement)
- Plateforme de développement (langages, plateforme de données, services de niveau intermédiaire)
- Base de données (UC, mémoire, stockage, version)

Facteurs d’analyse qualitative :

- Investissements continus en augmentation
- Coûts d’exploitation
- Boucles de rétroaction et investissements DevOps potentiels.

## <a name="rebuild"></a>Reconstruire

Dans certains scénarios, les efforts nécessaires à la réarchitecture d’une application peuvent être trop importants pour justifier tout investissement supplémentaire. C’est particulièrement vrai pour les applications qui répondaient autrefois aux besoins de l’entreprise, mais qui ne sont plus prises en charge ou ne sont plus alignées sur les processus métier actuels. Dans ce cas, une nouvelle base de code est créée pour s’aligner sur l’approche [cloud native](https://azure.microsoft.com/overview/cloudnative).

Les facteurs les plus courants sont les suivants :

- Accélérer l’innovation
- Créer des applications plus rapidement
- Réduire les coûts d’exploitation

Facteurs d’analyse quantitative :

- Taille des ressources d’application (processeur, mémoire, stockage)
- Dépendances (trafic réseau)
- Trafic utilisateur (consultations de page, temps passé sur une page, temps de chargement)
- Plateforme de développement (langages, plateforme de données, services de niveau intermédiaire)
- Base de données (UC, mémoire, stockage, version)

Facteurs d’analyse qualitative :

- Baisse de la satisfaction des utilisateurs finaux
- Processus d’entreprise limités dans leur fonctionnalité
- Amélioration potentielle des coûts, de l’expérience ou du chiffre d’affaires

## <a name="replace"></a>Replace

Les solutions sont généralement implémentées à l’aide de la technologie et de l’approche les mieux adaptées sur le moment. Parfois, les applications SaaS peuvent fournir toutes les fonctionnalités nécessaires à l’application hébergée. Dans ces scénarios, une charge de travail peut être programmée pour un remplacement futur, ce qui évite tout effort de transformation.

Les facteurs les plus courants sont les suivants :

- Normaliser les bonnes pratiques du secteur
- Accélérer l’adoption des approches basées sur les processus d’entreprise
- Réallouer les investissements de développement dans des applications qui créent un avantage compétitif ou autre avantage

Facteurs d’analyse quantitative :

- Réductions des coûts d’exploitation généraux
- Taille de la machine virtuelle (processeur, mémoire, stockage)
- Dépendances (trafic réseau)
- Ressources à mettre hors service
- Base de données (UC, mémoire, stockage, version)

Facteurs d’analyse qualitative :

- Analyse coûts-avantages de l’architecture actuelle par rapport à une solution SaaS
- Diagramme des processus métier
- Schémas de données
- Processus personnalisés ou automatisés

## <a name="next-steps"></a>Étapes suivantes

Collectivement, vous pouvez appliquer ces cinq R de la rationalisation à un patrimoine numérique en vue de prendre des décisions de rationalisation concernant l’état futur de chaque application.

> [!div class="nextstepaction"]
> [Qu’est-ce qu’un patrimoine numérique ?](./index.md)
