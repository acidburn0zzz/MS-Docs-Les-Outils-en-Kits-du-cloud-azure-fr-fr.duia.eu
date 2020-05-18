---
title: Motivations et risques pour l’entreprise dans la discipline de Gestion des coûts
description: Appréhendez et découvrez des exemples de clients ypes qui adoptent une discipline de gestion des coûts dans le cadre d’une stratégie de gouvernance cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 08ae1bab0697fdd7bbffecca18c62e5ae637c2b6
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83220717"
---
<!-- cSpell:ignore prepurchases -->

# <a name="motivations-and-business-risks-in-the-cost-management-discipline"></a>Motivations et risques pour l’entreprise dans la discipline de Gestion des coûts

Cet article décrit les raisons pour lesquelles les clients adoptent une discipline Gestion des coûts au sein d’une stratégie de gouvernance cloud. Des exemples sur les risques métier conduisant à la rédaction d’instructions de stratégie sont également présentés.

## <a name="relevance"></a>Pertinence

En matière de gouvernance des coûts, l’adoption du cloud crée un changement de paradigme. Dans un environnement local classique, la gestion des coûts repose sur des cycles de renouvellement, l’acquisition de centres de données, le renouvellement d’hôtes et des problèmes de maintenance périodiques. Vous pouvez prévoir, planifier et affiner chacun de ces coûts afin de vous aligner aux budgets de dépenses d’investissement annuels.

Pour les solutions cloud, de nombreuses entreprises ont tendance à adopter une approche plus réactive face à la Gestion des coûts. Dans de nombreux cas, les entreprises procèdent à un achat préalable pour une quantité définie de services cloud ou s’engagent à utiliser un certain quota. Dans ce modèle, avec l’optimisation des remises en fonction des prévisions de dépenses de l’entreprise auprès d’un fournisseur de cloud spécifique, le cycle de coût apparaît proactif et planifié. Toutefois, cette perception ne peut devenir réalité que si l’entreprise implémente également des disciplines Gestion des coûts matures.

Le cloud offre des fonctionnalités en libre-service qui étaient inconnues dans les centres de données locaux classiques. Avec ces nouvelles fonctionnalités, les entreprises peuvent être plus agiles, moins restrictives et plus ouvertes à l’adoption de nouvelles technologies. Toutefois, le libre-service présente un inconvénient : les utilisateurs finaux peuvent dépasser involontairement les budgets alloués. À l’inverse, s’ils subissent un changement imprévu dans leurs plans, ces mêmes utilisateurs n’utiliseront peut-être pas tout le quota de services cloud prévu. C’est ce potentiel écart (dans les deux sens) qui justifie les investissements dans une discipline Gestion des coûts au sein de l’équipe de gouvernance.

## <a name="business-risk"></a>Risque métier

La discipline Gestion des coûts vise à lever les principaux risques métier liés aux dépenses à engager pour l’hébergement des charges de travail cloud. Collaborez avec votre entreprise pour identifier ces risques et surveiller la pertinence de chacun d’entre eux lorsque vous planifiez et implémentez vos déploiements cloud.

Les risques diffèrent en fonction de l’organisation, mais ceux liés aux coûts et présentés ci-dessous peuvent vous servir à initier des discussions au sein de votre équipe de gouvernance cloud :

- **Contrôle du budget :** Si vous ne contrôlez pas votre budget, vous risquez d’engager des dépenses excessives auprès d’un fournisseur de cloud.
- **Perte d’utilisation :** Les achats ou engagements préalables qui ne sont pas intégralement utilisés peuvent constituer des investissements perdus.
- **Anomalies de dépenses :** Les pics inattendus (dans les deux directions) peuvent être le signe d’une mauvaise utilisation.
- **Ressources surapprovisionnées :** Quand les ressources sont déployées dans une configuration qui dépasse les besoins d’une application ou d’une machine virtuelle, elles peuvent générer des pertes.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de stratégie Gestion des coûts](./template.md), documentez les risques métier susceptibles d’être introduits par le plan d’adoption du cloud actuel.

Une fois que vous avez compris tous les risques métier réalistes, l’étape suivante consiste à documenter la tolérance de l’activité aux risques, ainsi que les indicateurs et métriques clés permettant de superviser cette tolérance.

> [!div class="nextstepaction"]
> [Comprendre les indicateurs, les métriques et la tolérance au risque](./metrics-tolerance.md)
