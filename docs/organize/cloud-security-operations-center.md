---
title: Fonctions d’un centre des opérations de sécurité du cloud
description: Comprendre les fonctionnalités nécessaires pour la sécurité du cloud
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 7c3044e4d5e970b9f78bb46bda2aadf11273e556
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230225"
---
<!-- cSpell:ignore CISO MTTA MTTR SIEM NIST SOCs CDOC -->

# <a name="functions-of-a-cloud-security-operations-center-soc"></a>Fonctions d’un centre des opérations de sécurité du cloud

L’objectif principal d’un centre des opérations de sécurité du cloud est de détecter des attaques actives dirigées contre des ressources d’entreprise, d’y répondre, puis de récupérer d’urgence.

À mesure que le centre des opérations de sécurité du cloud mûrit, les opérations de sécurité doivent :

- Répondre de manière réactive aux attaques détectées par les outils
- Pourchasser de manière proactive des attaques qui ont échappé aux détections réactives

## <a name="modernization"></a>Modernisation

La détection des menaces et la réponse à celles-ci font actuellement l’objet d’une modernisation importante à tous les niveaux.

- **Élévation à la gestion des risques métier :** le centre des opérations de sécurité du cloud devient un composant clé de la gestion des risques pour l’organisation.
- **Métriques et objectifs :** le suivi de l’efficacité du centre des opérations de sécurité du cloud évolue, passant du « temps de détection » aux indicateurs clés suivants :
  - *Réactivité* via un temps moyen d’accusé de réception
  - *Vitesse de correction* via un temps moyen de correction
- **Évolution de la technologie :** la technologie du centre des opérations de sécurité du cloud évolue, passant de l’utilisation exclusive de l’analyse statique des journaux dans les Informations de sécurité et gestion d’événements (SIEM) pour ajouter le recours à des outils spécialisés et des techniques d’analyse sophistiquées. Cela permet de recueillir des informations approfondies sur des ressources qui fournissent des alertes de haute qualité et une expérience d’investigation qui complètent la vue élargie des Informations de sécurité et gestion d’événements. Les deux types d’outils se servent de plus en plus de l’intelligence artificielle et de l’apprentissage automatique (AI/ML), de l’analyse du comportement et du renseignement intégré sur les menaces pour aider à épingler et à hiérarchiser des actions anormales susceptibles d’émaner d’un agresseur malveillant.
- **Chasse aux menaces :** les centres des opérations de sécurité du cloud ajoutent la chasse aux menaces fondée sur des hypothèses afin d’identifier de manière proactive des attaques avancées et d’écarter les alertes bruyantes des files d’attente d’analyses en première ligne.
- **Gestion des incidents :** la discipline est de plus en plus formalisée afin de coordonner les éléments non techniques des incidents avec des équipes en charge des aspects juridiques, de communications et autres.
**Intégration du contexte interne :** pour faciliter la hiérarchisation des activités du centre des opérations de sécurité du cloud telles que les scores de risque relatifs des comptes utilisateurs et des appareils, la sensibilité des données et des applications, et les principales limites d’isolement de sécurité à défendre de près.

 Pour plus d'informations, consultez les pages suivantes :

- [Normes de stratégie et d’architecture&mdash;Opérations de sécurité](https://docs.microsoft.com/security/compass/security-operations-videos-and-decks)
- [Module de l’atelier RSSI 4b : Stratégie de protection contre les menaces](https://docs.microsoft.com/security/ciso-workshop/ciso-workshop-module-4b)
- Série de blogs du Centre d’opérations de cyberdéfense [partie 1](https://www.microsoft.com/security/blog/2019/02/21/lessons-learned-from-the-microsoft-soc-part-1-organization/), [partie 2a](https://www.microsoft.com/security/blog/2019/04/23/lessons-learned-microsoft-soc-part-2-organizing-people/), [partie 2b](https://www.microsoft.com/security/blog/2019/06/06/lessons-learned-from-the-microsoft-soc-part-2b-career-paths-and-readiness/), [partie 3a](https://www.microsoft.com/security/blog/2019/10/07/ciso-series-lessons-learned-from-the-microsoft-soc-part-3a-choosing-soc-tools/), [partie 3b](https://www.microsoft.com/security/blog/2019/12/23/ciso-series-lessons-learned-from-the-microsoft-soc-part-3b-a-day-in-the-life)
- [Guide de gestion des incidents de sécurité informatique du NIST](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)
- [Guide du NIST pour la récupération d’événements de cybersécurité](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-184.pdf)

## <a name="team-composition-and-key-relationships"></a>Composition d’équipe et relations clés

Le centre des opérations de sécurité du cloud est généralement constitué des types de rôles suivants.

- Opérations informatiques (contact régulier proche)
- Informations sur les menaces
- Architecture de la sécurité
- Programme des risques internes
- Ressources juridiques et humaines
- Équipes de communication
- Organisation des risques (le cas échéant)
- Associations, communautés et fournisseurs spécifiques du secteur (avant qu’incident se produise)

## <a name="next-steps"></a>Étapes suivantes

Examinez la fonction d’[architecture de sécurité](./cloud-security-architecture.md).
