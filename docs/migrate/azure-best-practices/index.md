---
title: Bonnes pratiques pour la migration Azure
description: Découvrez comment implémenter les outils nécessaires pour vous conformer aux bonnes pratiques en matière de migration cloud à l’aide du Cloud Adoption Framework pour Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 22f2718775b194196f65672f0cbc1712d0a3a4ac
ms.sourcegitcommit: afe10f97fc0e0402a881fdfa55dadebd3aca75ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80433544"
---
# <a name="best-practices-for-cloud-migration"></a>Bonnes pratiques pour la migration cloud

Nous vous recommandons d’utiliser le [Guide de migration Azure](../azure-migration-guide/index.md) dans le Cloud Adoption Framework comme point de départ si vous souhaitez migrer vers Azure. Ce guide décrit les outils et les approches de base pour la migration des machines virtuelles vers le cloud. Cette section du Cloud Adoption Framework couvre une série de bonnes pratiques qui vont au-delà des outils de base natifs du cloud.

## <a name="cloud-migration-best-practice-checklist"></a>Liste de contrôle des bonnes pratiques en matière de migration cloud

La liste de contrôle suivante décrit des situations complexes qui peuvent nécessiter l’étendue du cadre de la migration, au-delà des instructions du [guide de migration Azure](../azure-migration-guide/index.md).

### <a name="business-driven-scope-expansion"></a>Expansion du cadre basée sur l’activité

- **[Prise en charge des marchés internationaux](./multiple-regions.md) :** L’entreprise est implantée dans plusieurs zones géographiques qui ont chacune des exigences de souveraineté des données différentes. Pour répondre à ces exigences, d’autres considérations viennent s’ajouter aux prérequis et à la répartition des ressources pendant la migration.

### <a name="technology-driven-scope-expansion"></a>Expansion du cadre basée sur la technologie

- **[Migration VMware](./vmware-host.md) :** la migration des hôtes VMware peut accélérer le processus de migration global. Chaque hôte VMware migré peut déplacer plusieurs charges de travail vers le cloud à l’aide d’une approche lift-and-shift. Après la migration, ces machines virtuelles et charges de travail peuvent rester dans VMware ou être migrées vers des fonctionnalités cloud modernes.
- **[Migration de SQL Server](./sql-migration.md) :** la migration de serveurs SQL peut accélérer le processus de migration global. Chaque SQL Server migré peut déplacer plusieurs bases de données et services, ce qui peut accélérer plusieurs charges de travail.
- **[Centres de données multiples](./multiple-datacenters.md) :** la migration de plusieurs centres de données rend la migration beaucoup plus complexe. Durant les processus d’évaluation, de migration, d’optimisation et de gestion, d’autres considérations sont abordées pour préparer des environnements plus complexes.
- **[Besoins des données qui dépassent la capacité réseau](./network-capacity-exceeded.md) :** Les entreprises choisissent souvent de passer au cloud, car elles ne sont plus satisfaites de la capacité, de la rapidité ou de la stabilité d’un centre de données existant. Malheureusement, ces mêmes contraintes compliquent le processus de migration, en nécessitant une planification supplémentaire lors des processus de migration et d’évaluation.
- **[Stratégie de gouvernance ou de conformité](./governance-or-compliance.md) :** quand la gouvernance et la conformité sont essentielles à la réussite d’une migration, un alignement supplémentaire entre les équipes de gouvernance informatique et l’équipe d’adoption du cloud est nécessaire.

Si l’une de ces situations complexes est présente dans votre scénario, cette section du Framework d’adoption du cloud vous fournira probablement le type de conseils dont vous avez besoin pour adapter correctement le cadre lors d’un processus de migration.

Ces scénarios sont abordés dans les différents articles de cette section du Framework d’adoption du cloud.

## <a name="next-steps"></a>Étapes suivantes

Parcourez la table des matières située sur la gauche pour répondre à certains besoins ou pour effectuer des changements de cadre. Autre option : la première amélioration du cadre de la liste ([Prise en charge des marchés internationaux](./multiple-regions.md)) est un bon point de départ pour passer en revue ces scénarios.

> [!div class="nextstepaction"]
> [Prise en charge des marchés internationaux](./multiple-regions.md)
