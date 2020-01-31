---
title: Risques métier et motivations associés à la Base de référence de la sécurité
description: Risques métier et motivations associés à la Base de référence de la sécurité
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 9d1bf5ef10ec3acd936ba4e66cca374e8365018a
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808955"
---
# <a name="security-baseline-motivations-and-business-risks"></a>Risques métier et motivations associés à la Base de référence de la sécurité

Cet article décrit les raisons pour lesquelles les clients adoptent une discipline Base de référence de la sécurité au sein d’une stratégie de gouvernance cloud. Des exemples sur les risques métier potentiels pouvant conduire à la rédaction d’instructions de stratégie sont également présentés.

<!-- markdownlint-disable MD026 -->

## <a name="security-baseline-relevancy"></a>Pertinence de la Base de référence de la sécurité

La sécurité est une préoccupation majeure de tous les services informatiques. Les déploiements dans le cloud sont confrontés aux mêmes risques de sécurité que les charges de travail hébergées dans des centres de données locaux classiques. Cela étant, la nature des plateformes de cloud public, sans propriété directe sur le matériel physique stockant et exécutant vos charges de travail, signifie que la sécurité du cloud requiert ses propres stratégies et processus.

L’un des principaux éléments qui distingue la gouvernance de la sécurité du cloud de la stratégie de sécurité traditionnelle est la facilité avec laquelle les ressources peuvent être créées, ce qui est susceptible d’ajouter des vulnérabilités si la sécurité n’est pas prise en compte avant le déploiement. La flexibilité offerte par certaines technologies comme [SDN (Software-Defined Networking)](../../decision-guides/software-defined-network/index.md) pour rapidement faire évoluer votre topologie réseau cloud peut aussi modifier votre surface d’attaque de manière imprévisible. Les plateformes cloud fournissent également des outils et des fonctionnalités capables d'améliorer vos fonctionnalités de sécurité au-delà des possibilités des environnements locaux.

Vos investissements et processus en matière de stratégie de sécurité dépendent en grande partie de la nature de votre déploiement dans le cloud. Les déploiements de tests initiaux peuvent nécessiter un minimum de stratégies de sécurité, mais une charge de travail stratégique devra répondre à des besoins de sécurité aussi complexes qu'étendus. À un certain niveau, tous les déploiements doivent respecter une certaine discipline.

La discipline Base de référence de la sécurité couvre les stratégies d'entreprise et les processus manuels que vous pouvez mettre en place pour protéger votre déploiement dans le cloud contre les risques de sécurité.

> [!NOTE]
>S'il est important d'appréhender la [Base de référence des identités](../identity-baseline/index.md) dans le contexte de la Base de référence de la sécurité et de la façon dont cela se rapporte au contrôle d'accès, les [cinq disciplines de la gouvernance cloud](../index.md) considèrent la [Base de référence des identités](../identity-baseline/index.md) comme leur propre discipline, indépendamment de la Base de référence de la sécurité.

## <a name="business-risk"></a>Risque métier

La discipline Base de référence de la sécurité tente de répondre aux principaux risques métier en matière de sécurité. Collaborez avec votre entreprise pour identifier ces risques et surveiller la pertinence de chacun d’entre eux lorsque vous planifiez et implémentez vos déploiements cloud.

Les risques diffèrent en fonction de l’organisation, mais ceux liés à la sécurité et présentés ci-dessous peuvent vous servir à initier des discussions au sein de votre équipe de gouvernance cloud :

- **Violation des données :** Une exposition par inadvertance ou la perte de données sensibles hébergées dans le cloud peut entraîner la perte de clients, des problèmes contractuels ou des conséquences juridiques.
- **Interruption de service :** Les pannes et autres problèmes de performances dus à une infrastructure non sécurisée altèrent le bon déroulement des opérations et peuvent entraîner une perte de productivité ou d'activité.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle Gestion de cloud](./template.md), documentez les risques métier susceptibles d’être introduits par le plan d’adoption du cloud actuel.

Une fois tous les risques métier réalistes appréhendés, l’étape suivante consiste à documenter la tolérance de l’activité aux risques, ainsi que les indicateurs et métriques clés permettant de surveiller cette tolérance.

> [!div class="nextstepaction"]
> [Comprendre les indicateurs, les métriques et la tolérance au risque](./metrics-tolerance.md)
