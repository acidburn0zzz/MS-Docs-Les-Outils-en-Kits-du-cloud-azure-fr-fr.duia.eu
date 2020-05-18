---
title: Impact des décisions du marché mondial
description: Utilisez le Cloud Adoption Framework pour Azure afin de comprendre comment les décisions du marché mondial peuvent affecter le parcours de transformation vers le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 8dba91bf7bd87395d3b5c55cf99480f8c6a54bd4
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83221448"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-will-global-market-decisions-affect-the-transformation-journey"></a>Comment les décisions du marché mondial vont-elles affecter le parcours de transformation ?

Le cloud ouvre de nouvelles opportunités à l’échelle mondiale. Les obstacles aux activités mondiales sont considérablement réduits, car les entreprises obtiennent les moyens de déployer des ressources sur le marché sans avoir à investir massivement dans de nouveaux centres de données. Malheureusement, cela entraîne également un surcroît de complexité des points de vue technique et juridique.

## <a name="data-sovereignty"></a>Souveraineté des données

De nombreuses régions géopolitiques ont établi des réglementations relatives à la souveraineté des données. Ces réglementations limitent l’emplacement de stockage des données, la nature des données qui peuvent quitter le pays d’origine ainsi que le type de données collecté auprès des habitants de la région concernée. Avant d’utiliser une solution cloud dans une zone géographique étrangère, vous devez comprendre comment le fournisseur de cloud gère la souveraineté des données. Pour plus d’informations sur l’approche d’Azure concernant chaque zone géographique, consultez [Zones géographiques d’Azure](https://azure.microsoft.com/global-infrastructure/geographies). Pour plus d’informations sur la conformité dans Azure, consultez [La confidentialité chez Microsoft](https://www.microsoft.com/trust-center/privacy) dans le Centre de gestion de la confidentialité Microsoft.

Le reste de cet article suppose qu’un conseiller juridique a examiné et approuvé les opérations pouvant être effectuées dans un pays étranger.

## <a name="business-units"></a>Unités commerciales

Il est important de comprendre quelles sont les unités commerciales qui opèrent dans les pays étrangers, et quels sont les pays affectés. Ces informations sont utilisées pour concevoir des solutions d’hébergement, de facturation et de déploiement sur le fournisseur de cloud.

## <a name="employee-usage-patterns"></a>Modèles d’utilisation des employés

Il est important de comprendre comment les utilisateurs du monde entier accèdent aux applications qui ne sont pas hébergées dans leur pays. Les réseaux WAN mondiaux (réseaux étendus) routent les utilisateurs en fonction de contrats existants. Dans un monde local classique, certaines contraintes limitent la conception des réseaux WAN. Ces contraintes peuvent donner lieu à de mauvaises expériences utilisateur si elles ne sont pas bien comprises avant l’adoption du cloud.

Dans un modèle de cloud, une connectivité Internet standard offre également de nombreuses nouvelles options. La communication des informations relatives à la répartition des employés sur plusieurs zones géographiques peut aider l’équipe d’adoption du cloud à concevoir des solutions WAN produisant des expériences utilisateur positives **et** susceptibles de réduire les coûts liés aux réseaux.

## <a name="external-user-usage-patterns"></a>Modèles d’utilisation des utilisateurs externes

Il est également important de comprendre les modèles d’utilisation des utilisateurs externes tels que les clients ou les partenaires. Tout comme les modèles d’utilisation des employés, les modèles d’utilisation des utilisateurs externes peuvent affecter négativement le niveau de performance des déploiements sur le cloud. Quand une base d’utilisateurs importante ou critique réside dans un pays étranger, il peut être judicieux d’inclure une stratégie de déploiement mondiale dans la conception globale de la solution.

## <a name="next-steps"></a>Étapes suivantes

Découvrez les [compétences nécessaires au cours de la phase de stratégie](./suggested-skills.md) de votre parcours d’adoption du cloud.

> [!div class="nextstepaction"]
> [Compétences nécessaires pendant la phase de stratégie](./suggested-skills.md)
