---
title: 'Gouvernance pour les entreprises complexes : gouvernance multicouche'
description: Utilisez le Framework d’adoption du cloud pour Azure pour découvrir des niveaux de complexité supérieurs avec la présence de plusieurs couches de gouvernance dans les grandes entreprises.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 36c2653876f0d254a282a7f7ed3abaee2ca82656
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80434399"
---
# <a name="governance-guide-for-complex-enterprises-multiple-layers-of-governance"></a>Guide de gouvernance pour les entreprises complexes : Couches de gouvernance multiples

Lorsque les grandes entreprises ont besoin de plusieurs couches de gouvernance, des niveaux de complexité plus importants doivent être pris en compte dans le produit minimum viable pour la gouvernance, et dans les améliorations ultérieures de la gouvernance.

Voici quelques exemples de complexités :

- Fonctions de gouvernance distribuée.
- Équipe informatique de l’entreprise prenant en charge les organisations informatiques des unités commerciales.
- Équipe informatique de l’entreprise prenant en charge les organisations informatiques réparties dans plusieurs régions.

Cet article explique comment aborder ce type de complexités.

## <a name="large-enterprise-governance-is-a-team-sport"></a>La gouvernance des grandes entreprises est un sport collectif

Les grandes entreprises bien établies comptent souvent dans leurs effectifs des équipes ou des employés qui se concentrent sur les différentes disciplines mentionnées tout au long de ce guide. Ce guide présente une approche pour transformer la gouvernance en un sport collectif.

Dans de nombreuses grandes entreprises, les Cinq disciplines de la gouvernance cloud peuvent représenter des freins à l’adoption. Développer l’expertise cloud dans les domaines de la sécurité, des opérations, des déploiements et de la configuration dans toute une entreprise est une tâche de longue haleine. L’implémentation de la sécurité informatique et de la stratégie de gouvernance informatique de façon holistique peut freiner l’innovation et faire perdre quelques mois, voire quelques années à l’entreprise. Trouver le bon équilibre entre le besoin métier d’innovation et le besoin de gouvernance pour protéger les ressources existantes est un processus délicat.

De par ses fonctionnalités, le cloud peut supprimer ces obstacles à l’innovation, mais aussi accroître les risques. Dans ce guide sur la gouvernance, nous avons montré comment l’entreprise fictive a mis en place des barrières de sécurité pour gérer les risques. Plutôt que de s’attaquer à chacune des disciplines nécessaires pour protéger l’environnement, l’équipe de gouvernance cloud adopte une approche basée sur les risques pour régir les ressources pouvant être déployées, tandis que les autres équipes s’occupent des maturités cloud nécessaires. Plus important encore, à mesure que chaque équipe atteint une maturité cloud, la gouvernance applique toutes les solutions de manière holistique. Dès que chaque équipe atteint un certain niveau de maturité et apporte sa contribution à la solution globale, l’équipe de gouvernance cloud peut créer des étapes-jalons, ce qui permet de développer des innovations et adoptions supplémentaires.

Ce modèle illustre l’évolution d’une collaboration entre l’équipe de gouvernance cloud et les équipes existantes de l’entreprise (sécurité, gouvernance informatique, mise en réseau, etc.). Le guide commence par le produit minimum viable pour la gouvernance et, via les itérations de gouvernance, aboutit à un résultat final holistique.

## <a name="requirements-to-supporting-such-a-team-sport"></a>Exigences pour prendre en charge un tel sport collectif

La première exigence d’un modèle de gouvernance avec plusieurs couches est de comprendre la hiérarchie de la gouvernance. Répondre aux questions suivantes vous aidera à comprendre la hiérarchie globale de la gouvernance :

- Comment la comptabilité cloud (facturation pour les services cloud) est-elle gérée entre les unités commerciales ?
- Comment les responsabilités en matière de gouvernance sont-elles attribuées entre l’équipe informatique de l’entreprise et chaque unité commerciale ?
- Quels sont les types d’environnements gérés par chacune de ces unités informatiques ?

## <a name="central-governance-of-a-distributed-governance-hierarchy"></a>Gouvernance centrale d’une hiérarchie de gouvernance distribuée

Les outils tels que les groupes d’administration permettent à l’équipe informatique de l’entreprise de créer une structure hiérarchique correspondant à la hiérarchie de gouvernance. Grâce à des outils comme Azure Blueprints, des ressources peuvent être appliquées aux différentes couches de cette hiérarchie. Les versions d’Azure Blueprints peuvent être gérées, et plusieurs versions peuvent être appliquées aux groupes d’administration, abonnements ou groupes de ressources. Chacun de ces concepts est décrit en détail dans le produit minimum viable pour la gouvernance.

Le point important à retenir pour chacun de ces outils est la possibilité d’appliquer plusieurs blueprints à une hiérarchie. La gouvernance devient alors un processus en couches. Voici un exemple de cette application hiérarchique de la gouvernance :

- **Équipe informatique de l’entreprise :** elle crée un ensemble de standards et de stratégies qui s’applique à l’ensemble de l’adoption du cloud. Cela est matérialisé dans un blueprint « Planning de référence ». L’équipe informatique de l’entreprise devient alors propriétaire de la hiérarchie du groupe d’administration, et s’assure qu’une version de la base de référence est appliquée à tous les abonnements dans la hiérarchie.
- **Équipe informatique d’unité commerciale ou régionale :** plusieurs équipes informatiques peuvent appliquer une couche de gouvernance supplémentaire en créant leur propre blueprint. Ces blueprints vont permettre de créer d’autres stratégies et standards. Une fois développés, l’équipe informatique de l’entreprise peut appliquer ces blueprints aux nœuds concernés dans la hiérarchie du groupe d’administration.
- **Équipes d’adoption du cloud :** des implémentations et décisions précises au sujet des applications ou des charges de travail peuvent être mises en place et prises par les équipes d’adoption du cloud, au sein du contexte des exigences de la gouvernance. L’équipe peut parfois demander des modèles de cohérence des ressources Azure supplémentaires pour accélérer les efforts d’adoption.

Les détails concernant l’implémentation de la gouvernance à chaque niveau exigeront une certaine coordination entre les équipes. Le produit minimum viable pour la gouvernance et les améliorations de la gouvernance décrits dans ce guide peuvent faciliter la mise en place de cette coordination.
