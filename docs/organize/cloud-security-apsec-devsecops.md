---
title: Comprendre la sécurité des applications et les fonctions DevSecOps
description: Comprenez la sécurité des applications et les fonctions DevSecOps.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 723b7339c29870f267c4b469f2b8a0de79ee026b
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230169"
---
# <a name="application-security-and-devsecops-functions"></a>Sécurité des applications et fonctions DevSecOps

L’objectif de la sécurité des applications et des DevSecOps est d’intégrer des garanties de sécurité dans les processus de développement et les applications métier personnalisées.

## <a name="modernization"></a>Modernisation

Le développement d’applications se transforme rapidement sous plusieurs aspects, dont le modèle d’équipe DevOps, la cadence de publication rapide DevOps et la composition technique des applications via les services cloud et les API. Pour plus d’informations sur ces changements, découvrez comment le cloud change les relations et les responsabilités de sécurité.

Cette modernisation des modèles de développement archaïques présente des opportunités et l’exigence de moderniser la sécurité des applications et des processus de développement. La fusion de la sécurité dans les processus DevOps est souvent appelée DevSecOps, et engendre des changements, dont les suivants :

<!-- TODO: Link needed below? -->
- **La sécurité est intégrée, et non une approbation extérieure :** Le rythme rapide du changement du développement d’applications rend les approches d’analyse et de rapport classiques obsolètes. Ces approches héritées ne peuvent pas tenir le rythme des publications sans ralentir le développement jusqu’à l’arrêt et causer des retards de mise sur le marché, la sous-exploitation des développeurs et la croissance des problèmes en attente de résolution.
  - **Réorganisez-vous** pour engager la sécurité plus tôt dans les processus de développement d’applications, car la résolution des problèmes en amont est moins coûteuse, plus rapide et plus efficace. Si vous attendez que les problèmes surviennent, vous aurez plus de mal à changer la structure.
  - **Intégration native :** Les pratiques de sécurité doivent être intégrées en toute transparence pour éviter les frictions dans les flux de travail de développement et les processus d’intégration continue/de déploiement continu (CI/CD). Pour voir comment GitHub approche cela, consultez [Sécurisation des logiciels, ensemble](https://github.blog/2019-09-18-securing-software-together/).
  - **Sécurité de haut niveau :** La sécurité doit fournir des résultats et des conseils de haute qualité qui permettent aux développeurs de résoudre les problèmes rapidement et ne pas faire perdre de temps aux développeurs avec des faux positifs.
  - **Culture convergée :** Les rôles de sécurité, de développement et d’exploitation doivent contribuer aux éléments clés dans une culture partagée, avec des valeurs partagées et des objectifs et responsabilités partagés.
- **Sécurité agile :** Faites passer la sécurité d’un modèle qui « doit être parfait pour être livré » à une approche agile qui commence par une sécurité viable minimale pour les applications (et pour les processus de développement) qui est continuellement améliorée de manière incrémentielle.
- **Adoptez les fonctionnalités d’infrastructure et de sécurité natives du cloud** pour rationaliser les processus de développement tout en intégrant la sécurité.
- **Gestion des risques liés à la chaîne d’approvisionnement :** Adoptez une approche de « confiance zéro » pour les logiciels open source (OSS) et les composants tiers en validant leur intégrité et en assurant l’application des correctifs de bogues et des mises à jour de ces composants.
- **Apprentissage continu :** La rapidité de publication des services de développement (parfois appelés services PaaS) et la composition évolutive des applications signifient que les membres des équipes de développement, d’exploitation et de sécurité se familiariseront constamment avec de nouvelles technologies.
- **L’approche programmatique** de la sécurité des applications garantit l’amélioration permanente de l’approche agile.

Pour plus de contexte, consultez [Cycle de vie de développement sécurisé Microsoft](https://www.microsoft.com/sdl).

## <a name="team-composition-and-key-relationships"></a>Composition d’équipe et relations clés

La sécurité des applications et les fonctions DevSecOps sont idéalement gérées par les développeurs et équipes d’exploitation familiers avec les questions de sécurité (avec le soutien d’experts en matière de sécurité).

Cette fonction interagit couramment avec d’autres fonctions et experts, notamment :

- Architecture et opérations de sécurité
- Infrastructure de sécurité
- Communications (formation et outils)
- Personnes de sécurité
- Identité et clés
- Équipes de gestion de la conformité et des risques
- Responsables commerciaux clés ou leurs représentants

## <a name="next-steps"></a>Étapes suivantes

Passez en revue la fonction de [sécurité des données](./cloud-security-data-security.md).
