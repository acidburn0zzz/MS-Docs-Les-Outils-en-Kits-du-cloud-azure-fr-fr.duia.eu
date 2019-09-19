---
title: Alignement des ressources sur des charges de travail hiérarchisées
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Alignement des ressources sur des charges de travail hiérarchisées
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 9d98a9e368f71310a05ae6242ef75a57771824d5
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70837615"
---
# <a name="align-assets-to-prioritized-workloads"></a>Aligner les ressources sur des charges de travail hiérarchisées

La charge de travail est une description conceptuelle d’un ensemble de ressources : les machines virtuelles, les applications et les sources de données. L’article précédent intitulé [Hiérarchiser et définir des charges de travail](./workloads.md) a donné des conseils pour la collecte des données qui définiront la charge de travail. Avant la migration, quelques entrées techniques de cette liste nécessitent une validation supplémentaire. Cet article permet de valider les entrées suivantes :

- **Applications** : répertorie toutes les applications incluses dans cette charge de travail.
- **Machines virtuelles/serveurs** : répertorie l’ensemble des machines virtuelles ou serveurs inclus dans la charge de travail.
- **Sources de données** : répertorie toutes les sources de données incluses dans la charge de travail.
- **Dépendances** : répertorie toutes les dépendances de ressources non incluses dans la charge de travail.

Plusieurs options s’offrent à vous pour assembler ces données. Voici quelques-unes des approches les plus courantes.

## <a name="alternative-inputs-migrate-modernize-innovate"></a>Entrées alternatives : Migrer, Moderniser, Innover

L’objectif des points de données précédents est de capturer des dépendances et des efforts techniques relatifs comme aide à la hiérarchisation. Selon la transition souhaitée, vous pouvez rassembler des points de données alternatifs pour prendre en charge la hiérarchisation appropriée.

**Migrer :** pour les purs efforts de migration, les dépendances de ressources et d’inventaire existantes servent de mesure de la complexité relative.

**Moderniser :** lorsque l’objectif d’une charge de travail est de moderniser des applications ou d’autres ressources, ces points de données restent de solides mesures de la complexité. Toutefois, il peut être judicieux d’ajouter une entrée pour les opportunités de modernisation à la documentation relative à la charge de travail.

**Innovation :** lorsque les données ou la logique métier subissent une modification importante au cours d’un effort d’adoption du cloud, elles sont considérées comme une transformation de type *Innover*. Il en va de même lorsque vous créez de nouvelles données ou une nouvelle logique métier. Pour les scénarios de type Innover, la migration des ressources représente probablement le plus petit effort requis. Pour ces scénarios, l’équipe doit concevoir un ensemble d’entrées de données techniques pour mesurer la complexité relative.

## <a name="azure-migrate"></a>Azure Migrate

Azure Migrate fournit un ensemble de fonctions de regroupement qui peuvent accélérer l’agrégation des applications, des machines virtuelles, des sources de données et des dépendances. Une fois les charges de travail définies de manière conceptuelle, elles peuvent être utilisées comme base pour le regroupement de ressources en fonction du mappage des dépendances.

La documentation Azure Migrate fournit des conseils sur la façon de [regrouper les machines en fonction des dépendances](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies).

## <a name="configuration-management-database"></a>Base de données de gestion de configuration

Certaines organisations disposent d’une base de données de gestion de configuration (CMDB) bien gérée dans leurs outils existants pour la gestion des opérations. Elles peuvent également utiliser la base de données CMDB pour fournir les points de données d’entrée décrits précédemment.

## <a name="next-steps"></a>Étapes suivantes

[Passez en revue les décisions de rationalisation](./review-rationalization.md) basées sur l’alignement des actifs et les définitions des charges de travail.

> [!div class="nextstepaction"]
> [Passer en revue les décisions de rationalisation](./review-rationalization.md)