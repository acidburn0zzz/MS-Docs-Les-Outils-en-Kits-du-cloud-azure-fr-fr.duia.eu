---
title: Effectuer une révision de stratégie cloud
description: Découvrez comment effectuer une révision de la stratégie cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 48e4e759435178e346e08233afeca95ab065711e
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76805062"
---
<!-- markdownlint-disable MD026 -->

# <a name="conduct-a-cloud-policy-review"></a>Effectuer une révision de stratégie cloud

Une révision de stratégie cloud constitue la première étape de la [maturité de la gouvernance](../index.md) dans le cloud. L’objectif de ce processus est de moderniser les stratégies informatiques existantes de l’entreprise. À la fin de ce processus, les stratégies mises à jour fournissent un niveau équivalent de gestion des risques pour les ressources cloud. Cet article explique le processus de révision de stratégie de cloud et son importance.

## <a name="why-perform-a-cloud-policy-review"></a>Pourquoi procéder à une révision de politique cloud ?

La plupart des entreprises gèrent les services informatiques via l’exécution de processus alignés avec des stratégies directrices. Dans les petites entreprises, ces stratégies peuvent sembler anecdotiques et les processus sont vaguement définis. À mesure qu’une entreprise grandit, les stratégies et les processus ont tendance à être documentés de façon plus précise et exécutés de manière plus cohérente.

Tandis que les stratégies informatiques d’entreprise gagnent en maturité, les dépendances aux décisions techniques prises par le passé ont tendance à s’infiltrer dans les stratégies directrices. Par exemple, il est courant de voir que les processus de récupération d’urgence incluent une stratégie qui impose des sauvegardes sur bande hors site. Cette inclusion suppose une dépendance à un type de technologie (sauvegardes sur bande) qui n’est peut-être plus la solution la plus pertinente.

Les transformations cloud créent un point d’inflexion naturel pour réexaminer les décisions en matière de stratégie héritée prises par le passé. Les fonctionnalités techniques et les processus par défaut changent considérablement dans le cloud, comme les risques inhérents. En utilisant l’exemple précédent, le choix d’une stratégie de sauvegarde sur bande est motivé par le risque d’avoir un point de défaillance unique, où les données sont conservées dans un seul emplacement, et par le besoin métier de réduire le profil de risque en atténuant ce risque. Dans un déploiement cloud, plusieurs options sont proposées pour atténuer le risque, avec des objectifs de temps de récupération bien moins élevés. Par exemple :

- Une solution cloud native peut activer la géoréplication dans l’instance Azure SQL Database.
- Une solution hybride peut utiliser Azure Site Recovery pour répliquer une charge de travail IaaS sur Azure.

Lors d’une transformation cloud, les stratégies régissent souvent les nombreux outils, services et processus disponibles pour les équipes d’adoption du cloud. Si ces stratégies reposent sur des technologies héritées, elles peuvent entraver les efforts de l’équipe pour mettre en place les changements. Dans le pire des cas, ce sont des stratégies importantes qui sont complètement ignorées par l’équipe de migration pour appliquer des solutions de contournement. Tout cela n’est pas acceptable.

## <a name="the-cloud-policy-review-process"></a>Le processus de révision de stratégie cloud

Les révisions de stratégie cloud font correspondre les stratégies de sécurité informatique et de gouvernance informatique existantes avec les [cinq disciplines de la gouvernance cloud](../index.md) : [Gestion des coûts](../cost-management/index.md), [Base de référence de sécurité](../security-baseline/index.md), [Base de référence des identités](../identity-baseline/index.md), [Cohérence des ressources](../resource-consistency/index.md) et [Accélération du déploiement](../deployment-acceleration/index.md).

Pour chacune de ces disciplines, le processus de révision suit les étapes ci-dessous :

1. Révision des stratégies locales existantes en lien avec la discipline concernée pour rechercher deux points de données clés : les dépendances héritées et les risques métier identifiés.
2. Évaluation de chacun des risques métier grâce à une question simple : « Le risque existe-t-il toujours dans un modèle cloud ? »
3. Si le risque existe toujours, réécriture de la stratégie en documentant l’atténuation nécessaire des risques métier plutôt que la solution technique.
4. Révision de la stratégie mise à jour avec les équipes d’adoption du cloud pour comprendre les solutions techniques potentielles associées à l’atténuation nécessaire.

## <a name="example-of-a-policy-review-for-a-legacy-policy"></a>Exemple d’une révision de stratégie héritée

Pour illustrer le processus de révision, reprenons la stratégie de sauvegarde sur bande de la section précédente :

- Une stratégie d’entreprise exige que des sauvegardes sur bande hors site soient effectuées pour tous les systèmes de production. Dans cette stratégie, vous pouvez voir deux points de données intéressants :
  - Une dépendance héritée sur une solution de sauvegarde sur bande.
  - Un risque métier supposé en lien avec le stockage des sauvegardes dans le même emplacement physique que l’équipement de production.
- Le risque existe-t-il encore ? Oui. Même dans le cloud, une dépendance sur une seule installation présente des risques. La probabilité que ce risque affecte l’activité est inférieure à celle liée à l’utilisation d’une solution en local, mais le risque existe tout de même.
- Réécrivez la stratégie. En cas de sinistre à l’échelle du centre de données, une solution de restauration (dans les 24 heures suivant la panne) des systèmes de production dans un autre centre de données et emplacement géographique doit être en place.
  - Un autre aspect important doit être pris en compte : la chronologie spécifiée dans le cadre de l’exigence précédente a peut-être été définie selon des contraintes techniques qui ne s’appliquent pas dans le cloud. Assurez-vous de bien comprendre les contraintes techniques et les capacités du cloud avant d’appliquer simplement un objectif de délai/point de récupération existant.
- Procédez à la révision avec les équipes d’adoption du cloud. En fonction de la solution en cours d’implémentation, plusieurs moyens vous permettent de respecter cette stratégie de cohérence des ressources.

## <a name="next-steps"></a>Étapes suivantes

Découvrez plus d’informations sur l’inclusion de la classification des données dans votre stratégie de gouvernance cloud.

> [!div class="nextstepaction"]
> [Classification des données](./data-classification.md)
