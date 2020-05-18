---
title: Fonctions d’une architecture de sécurité cloud
description: Comprendre la fonction de l’architecture de sécurité cloud
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6956415f8a98e04ef0887ac153f714cf3d2820c3
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230165"
---
# <a name="cloud-security-architecture-functions"></a>Fonctions de l’architecture de sécurité cloud

L’architecture de sécurité traduit les objectifs commerciaux et d’assurance de l’organisation dans la documentation et les diagrammes afin de guider les décisions techniques de sécurité.

## <a name="modernization"></a>Modernisation

L’architecture de sécurité est affectée par différents facteurs :

- **Modèle d’engagement continu :** La publication continue de mises à jour logicielles et de fonctionnalités cloud rend les modèles d’engagement fixes obsolètes. Les architectes doivent être engagés auprès de toutes les équipes travaillant dans des domaines techniques pour guider les décisions tout au long du cycle de vie de capacité des équipes.
- **Sécurité dans le cloud :** Intégrez des fonctionnalités de sécurité dans le cloud pour réduire le temps d’activation et les coûts de maintenance courante (matériel, logiciels, temps et efforts).
- **Sécurité du cloud :** Assurez-vous que toutes les ressources cloud, notamment les applications de logiciel en tant que service (SaaS), les machines virtuelles d’infrastructure en tant que service (IaaS) et les applications et services de plateforme en tant que service (PaaS).  Cela doit inclure la découverte et la sécurité à la fois des services approuvés et non approuvés.
- **Intégration des identités :** Les architectes de sécurité doivent garantir un alignement étroit avec les équipes d’identité pour aider les organisations à répondre à la fois aux objectifs de productivité et de garanties en matière de sécurité.
- **Intégration du contexte interne** dans les conceptions de sécurité, comme le contexte de la gestion de posture et les incidents examinés par le [centre] des opérations de sécurité (SOC). Cela doit inclure des éléments tels que les scores de risque relatifs des comptes d’utilisateur et des appareils, la sensibilité des données et les limites d’isolation de sécurité clés pour une défense active.

## <a name="team-composition-and-key-relationships"></a>Composition d’équipe et relations clés

L’architecture de sécurité est idéalement fournie par une personne ou équipe dédiée, mais les contraintes de ressources peuvent nécessiter l’attribution de cette fonction à un individu avec d’autres responsabilités.

L’architecture de sécurité doit avoir un large éventail de relations au sein de l’organisation de sécurité, avec des parties prenantes clés dans d’autres organisations et avec des pairs dans des organisations externes. Les principales relations internes doivent inclure :

- Informatique/architectes d’entreprise
- Gestion de la posture de sécurité
- Directeurs de technologie
- Responsables commerciaux clés ou leurs représentants
- Pairs de l’industrie et autres membres de la communauté de sécurité

Les architectes de sécurité doivent influencer activement [la stratégie et les normes de sécurité](./cloud-security-policy-standards.md).

## <a name="next-steps"></a>Étapes suivantes

Passez en revue la fonction de [gestion de la conformité de la sécurité cloud](./cloud-security-compliance-management.md).
