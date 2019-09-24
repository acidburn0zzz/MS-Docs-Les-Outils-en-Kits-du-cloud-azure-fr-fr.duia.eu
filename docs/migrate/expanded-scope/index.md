---
title: Check-list pour le cadre étendu d’une migration cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Check-list pour le cadre étendu d’une migration cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/19/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4daf4b01a2fde83de1040f224b8096475a24fe60
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224361"
---
# <a name="expanded-scope-for-cloud-migration"></a>Cadre étendu pour une migration cloud

Dans le Framework d’adoption du cloud, le [guide de migration Azure](../azure-migration-guide/index.md) constitue le point de départ suggéré pour les lecteurs intéressés par une migration de réhébergement vers Azure, également appelée migration « lift-and-shift ». Ce guide vous indique les différents prérequis, outils et approches pour la migration des machines virtuelles vers le cloud.

Ce guide est une base de référence efficace qui vous permet de vous familiariser avec ce type de migration, mais il présente certaines conditions. Ces conditions ont pour but de s’adresser à la majorité des lecteurs du Framework d’adoption du cloud, en fournissant une approche simplifiée des migrations. Cette section du Framework d’adoption du cloud traite de certains scénarios de migration à cadre étendu, qui vous aident lorsque ces conditions ne s’appliquent pas.

## <a name="cloud-migration-expanded-scope-checklist"></a>Check-list pour le cadre étendu d’une migration cloud

La check-list suivante décrit des situations complexes qui peuvent nécessiter l’étendue du cadre de la migration, au-delà des instructions du [guide de migration Azure](../azure-migration-guide/index.md).

- **Changements du cadre basés sur l’activité :**
  - [Équilibrage du portefeuille](./balance-the-portfolio.md)
  - [Prise en charge des marchés internationaux](../../decision-guides/regions/index.md)
  - Considération des coûts lors d’une migration *(à venir au 3e trimestre 2019)*
- **Changements du cadre basés sur la culture :**
  - Gestion des changements et processus d’approbation *(à venir au 3e trimestre 2019)*
  - Préparation de l’exécutif *(à venir au 3e trimestre 2019)*
  - [Préparation des compétences](./suggested-skills.md)
  - Alignement du support (partenaires, services et support) *(à venir au 3e trimestre 2019)*
- **Changements du cadre basés sur les stratégies techniques :**
  - Contraintes de centre de données existantes *(à venir au 3e trimestre 2019)*
  - Migration à grande échelle - Volume élevé ou vélocité des migrations *(à venir au 3e trimestre 2019)*
  - [Centres de données multiples](./multiple-datacenters.md)
  - [Besoins des données qui dépassent la capacité réseau](./network-capacity-exceeded.md)
  - Gestion des changements et documentation de la solution *(à venir au 3e trimestre 2019)*
  - [Stratégie de gouvernance ou de conformité](./governance-or-compliance.md)
- **Changements du cadre en fonction de la charge de travail :**
  - Architecture des charges de travail pour la résilience *(à venir au 3e trimestre 2019)*
  - Alignement de la migration sur les modèles d’application *(à venir au 3e trimestre 2019)*

Si l’une de ces situations complexes correspond à votre scénario, cette section du Framework d’adoption du cloud vous fournira probablement le type de conseils dont vous avez besoin pour adapter correctement le cadre lors d’un processus de migration.

Ces scénarios sont abordés dans les différents articles de cette section du Framework d’adoption du cloud.

## <a name="scope-options-explained"></a>Explication des options de cadre

Pour vous aider à comprendre chacun des scénarios d’extension du cadre, la liste suivante donne un résumé pour chaque titre utilisé dans la check-list ci-dessus.

### <a name="business-driven-scope-changes"></a>Changements du cadre basés sur l’activité

- **Équilibrage du portefeuille d’adoption du cloud :** L’équipe de stratégie cloud souhaite investir davantage dans la migration (réhébergement des charges de travail et des applications existantes avec un minimum de modifications) ou dans l’innovation (refactorisation ou recréation des charges de travail et des applications à l’aide d’une technologie cloud moderne). Souvent, la clé du succès réside dans l’équilibre entre ces deux priorités. Dans ce guide, le thème de l’équilibrage du portefeuille de l’adoption cloud est courant, car il est présent dans tous les processus de migration.
- **Prise en charge des marchés internationaux :** L’entreprise est implantée dans plusieurs zones géographiques qui ont chacune des exigences de souveraineté des données différentes. Pour répondre à ces exigences, d’autres considérations viennent s’ajouter aux prérequis et à la répartition des ressources pendant la migration.

### <a name="culture-driven-scope-changes"></a>Changements du cadre basés sur la culture

- **Gestion des changements et processus d’approbation :** Lorsque la culture de votre organisation est complexe, hautement matricielle ou isolée, les processus liés à la gestion des changements et aux approbations peuvent devenir compliqués. Des conseils sur la gestion de telles situations sont disponibles pour les processus d’évaluation, de migration et d’optimisation.
- **Préparation de la direction :** Des niveaux adaptés de prise en charge de la direction sont essentiels à la réussite de la migration. Si la direction n’est pas prête à s’engager, il est peu probable que des soutiens suivent. Cette situation complexe est abordée lors du processus des prérequis et du processus d’évaluation.
- **Préparation des compétences :** Quand l’équipe d’adoption du cloud ou les autres équipes participantes ne sont pas prêtes, l’ensemble du processus de migration peut devenir compliqué. Ce problème est abordé durant chaque processus de migration, dans une page spécifique de la préparation des compétences.
- **Alignement du support (partenaires, services et support)**  : Dans chacun des processus décrits, il existe plusieurs façons dont les partenaires, les services du fournisseur cloud et le support du fournisseur cloud peuvent contribuer à l’exécution. Dans chacune des sections de processus, une page sur l’alignement du support détaille les options disponibles.

### <a name="technical-strategy-driven-scope-changes"></a>Changements du cadre basés sur les stratégies techniques

- **Contraintes de centre de données existantes :** Les entreprises choisissent souvent de passer au cloud car elles ne sont plus satisfaites de la capacité, de la rapidité et de la stabilité d’un centre de données existant. Malheureusement, ces mêmes contraintes compliquent le processus de migration, en nécessitant une planification supplémentaire lors des processus de migration et d’évaluation.
- **Migration à grande échelle :** Les migrations qui dépassent les 2 000 ressources sont susceptibles de connaître des contraintes qui nécessitent une planification supplémentaire et une approche d’exécution rigoureuse. Les processus d’évaluation et de migration sont ajustés pour prendre en compte la complexité de la mise à l’échelle.
- **Centres de données multiples :** la migration de plusieurs centres de données rend la migration très complexe. Durant les processus d’évaluation, de migration, d’optimisation et de gestion, d’autres considérations sont abordées.
- **Gestion des changements et documentation de la solution :** Les inventaires des grands patrimoines numériques, les architectures de solution complexes, les dettes techniques de longue durée et les interdépendances peuvent engendrer une complexité qui doit être résolue lors des processus d’évaluation, de migration et d’optimisation.
- **Stratégie de gouvernance ou de conformité :** Quand la gouvernance et la conformité sont essentielles à la réussite d’une migration, un alignement supplémentaire entre les équipes de gouvernance informatique et l’équipe d’adoption du cloud est nécessaire.

### <a name="workload-specific-scope-changes"></a>Changements du cadre en fonction de la charge de travail

- **Architecture des charges de travail pour la résilience :** Les principes de conception cloud courants peuvent vous aider à préparer les charges de travail critiques pour une meilleure résilience. Cet article explique quel impact a la résilience sur le processus de migration lorsqu’il s’agit d’une exigence de charge de travail. Il aborde également quelques principes courants à inclure dans la configuration générale de l’environnement afin d’en améliorer la résilience.
- **Alignement de la migration sur les modèles d’application :** Le modèle de migration d’une charge de travail peut affecter le chemin de migration choisi. Cet article décrit quelques changements de cadre à intégrer au niveau des éléments de travail d’un backlog de migration, afin de refléter les différentes approches de migration pour chaque charge de travail.

## <a name="next-steps"></a>Étapes suivantes

Parcourez la table des matières située sur la gauche pour répondre à certains besoins ou pour effectuer des changements de cadre. Autre option : la première amélioration du cadre de la liste ([Équilibrage du portefeuille](./balance-the-portfolio.md)) est un bon point de départ pour passer en revue ces scénarios.

> [!div class="nextstepaction"]
> [Équilibrage du portefeuille](./balance-the-portfolio.md)
