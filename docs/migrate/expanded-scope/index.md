---
title: Check-list pour le cadre étendu d’une migration cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Check-list pour le cadre étendu d’une migration cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ee164f75b4f3748fce027d0c6c98db5200dcdd71
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548502"
---
# <a name="expanded-scope-for-cloud-migration"></a>Cadre étendu pour une migration cloud

Dans le Framework d’adoption du cloud, le [guide de migration Azure](../azure-migration-guide/index.md) constitue le point de départ suggéré pour les lecteurs intéressés par une migration de réhébergement vers Azure, également appelée migration « lift-and-shift ». Ce guide vous indique les différents prérequis, outils et approches pour la migration des machines virtuelles vers le cloud.

Ce guide est une base de référence efficace qui vous permet de vous familiariser avec ce type de migration, mais il présente certaines conditions. Ces conditions ont pour but de s’adresser à de nombreux lecteurs du Framework d’adoption du cloud, en fournissant une approche simplifiée des migrations. Cette section du Framework d’adoption du cloud traite de certains scénarios de migration à cadre étendu, qui vous aident lorsque ces conditions ne s’appliquent pas.

## <a name="cloud-migration-expanded-scope-checklist"></a>Check-list pour le cadre étendu d’une migration cloud

La check-list suivante décrit des situations complexes qui peuvent nécessiter l’étendue du cadre de la migration, au-delà des instructions du [guide de migration Azure](../azure-migration-guide/index.md).

### <a name="business-driven-scope-expansion"></a>Expansion du cadre basée sur l’activité

- **[Équilibrage du portefeuille](./balance-the-portfolio.md) :** L’équipe de stratégie cloud souhaite investir davantage dans la migration (réhébergement des charges de travail et des applications existantes avec un minimum de modifications) ou dans l’innovation (refactorisation ou recréation des charges de travail et des applications à l’aide d’une technologie cloud moderne). Souvent, la clé du succès réside dans l’équilibre entre ces deux priorités. Dans ce guide, le thème de l’équilibrage du portefeuille de l’adoption cloud est courant, car il est présent dans tous les processus de migration.
- **[Prise en charge des marchés internationaux](../../decision-guides/regions/index.md) :** L’entreprise est implantée dans plusieurs zones géographiques qui ont chacune des exigences de souveraineté des données différentes. Pour répondre à ces exigences, d’autres considérations viennent s’ajouter aux prérequis et à la répartition des ressources pendant la migration.

### <a name="technology-driven-scope-expansion"></a>Expansion du cadre basée sur la technologie

- **[Migration des hôtes VMWare](./vmware-host.md) :** la migration des hôtes VMWare peut accélérer le processus de migration global. Chaque hôte VMWare migré peut déplacer plusieurs charges de travail vers le cloud à l’aide d’une approche lift-and-shift. Après la migration, ces machines virtuelles et charges de travail peuvent rester dans VMWare ou être migrées vers des fonctionnalités cloud modernes.
- **[Migration de SQL Server](./sql-migration.md) :** la migration de serveurs SQL peut accélérer le processus de migration global. Chaque SQL Server migré peut déplacer plusieurs bases de données et services, ce qui peut accélérer plusieurs charges de travail.
- **[Centres de données multiples](./multiple-datacenters.md) :** la migration de plusieurs centres de données rend la migration très complexe. Durant les processus d’évaluation, de migration, d’optimisation et de gestion, d’autres considérations sont abordées pour préparer des environnements plus complexes.
- **[Besoins des données qui dépassent la capacité réseau](./network-capacity-exceeded.md) :** Les entreprises choisissent souvent de passer au cloud, car elles ne sont plus satisfaites de la capacité, de la rapidité ou de la stabilité d’un centre de données existant. Malheureusement, ces mêmes contraintes compliquent le processus de migration, en nécessitant une planification supplémentaire lors des processus de migration et d’évaluation.
- **[Stratégie de gouvernance ou de conformité](./governance-or-compliance.md) :** quand la gouvernance et la conformité sont essentielles à la réussite d’une migration, un alignement supplémentaire entre les équipes de gouvernance informatique et l’équipe d’adoption du cloud est nécessaire.

Si l’une de ces situations complexes est présente dans votre scénario, cette section du Framework d’adoption du cloud vous fournira probablement le type de conseils dont vous avez besoin pour adapter correctement le cadre lors d’un processus de migration.

Ces scénarios sont abordés dans les différents articles de cette section du Framework d’adoption du cloud.

## <a name="next-steps"></a>Étapes suivantes

Parcourez la table des matières située sur la gauche pour répondre à certains besoins ou pour effectuer des changements de cadre. Autre option : la première amélioration du cadre de la liste ([Équilibrage du portefeuille](./balance-the-portfolio.md)) est un bon point de départ pour passer en revue ces scénarios.

> [!div class="nextstepaction"]
> [Équilibrage du portefeuille](./balance-the-portfolio.md)
