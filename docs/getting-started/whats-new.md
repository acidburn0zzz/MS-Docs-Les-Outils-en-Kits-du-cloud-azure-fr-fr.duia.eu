---
title: Nouveautés
description: Découvrez les mises à jour récemment apportées au Microsoft Cloud Adoption Framework pour Azure.
author: JanetCThomas
ms.author: janet
ms.date: 03/27/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: c701d49a80ea0ec087f26f792b7ffe8dbd4c061f
ms.sourcegitcommit: 1a4b140f09bdaa141037c54a4a3b5577cda269db
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80392495"
---
<!-- markdownlint-disable MD024 -->

# <a name="whats-new-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Nouveautés du Microsoft Cloud Adoption Framework pour Azure

Voici la liste des changements récemment apportés au Cloud Adoption Framework.

Ce framework est le fruit d’une collaboration entre les clients, les partenaires et les équipes internes de Microsoft. Les nouveautés et les mises à jour sont publiées dès qu’elles sont disponibles. De cette façon, vous pouvez tester, valider et affiner les conseils à nos côtés. Nous vous encourageons à faire équipe avec nous afin de développer le Cloud Adoption Framework pour Azure.

## <a name="march-27-2020"></a>27 mars 2020

Nous avons ajouté des conseils concernant les abonnements initiaux que vous devez créer quand vous adoptez Azure.

### <a name="ready-updates"></a>Mises à jour de la préparation

| Article                                                                                                                 | Description                                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Créer vos abonnements Azure initiaux](../ready/azure-best-practices/initial-subscriptions.md)                       | **Nouvel article :** Créez vos abonnements de production et de non-production initiaux et déterminez s’il faut créer des abonnements de bac à sable (sandbox), ainsi qu’un abonnement pour contenir des services partagés. |
| [Créer des abonnements supplémentaires pour mettre à l’échelle votre environnement Azure](../ready/azure-best-practices/scale-subscriptions.md) | Découvrez les raisons pouvant vous amener à créer des abonnements supplémentaires, le déplacement de ressources entre des abonnements et des conseils pour la création d’abonnements.                                                   |
| [Organiser et gérer plusieurs abonnements Azure](../ready/azure-best-practices/organize-subscriptions.md)             | Créez une hiérarchie des groupes d’administration pour mieux organiser, gérer et régir vos abonnements Azure.                                                                                         |

## <a name="march-20-2020"></a>20 mars 2020

Nous avons ajouté des instructions qui incluent les outils, les programmes et le contenu catégorisés par personnage afin de garantir le succès des déploiements d’applications sur Kubernetes, de la preuve de concept à la production, suivi de la mise à l’échelle et de l’optimisation.

### <a name="kubernetes"></a>Kubernetes

| Article                                                                                     | Description                                                                                                                                                                           |
|---------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Développement et déploiement d’applications](../innovate/kubernetes/application-development.md) | **Nouvel article :** Fournit des check-lists, des ressources et des bonnes pratiques pour la planification du développement d’applications, la configuration de pipelines DevOps et l’implémentation de l’ingénierie de fiabilité des sites pour Kubernetes. |
| [Conception et opérations de cluster](../innovate/kubernetes/cluster-design-operations.md) | **Nouvel article :** Fournit des check-lists, des ressources et des bonnes pratiques pour la configuration de clusters, la conception de réseau, la scalabilité durable, la continuité de l’activité et la reprise de l’activité après sinistre pour Kubernetes. |
| [Sécurité des clusters et des applications](../innovate/kubernetes/cluster-application-security.md) | **Nouvel article :** Fournit des check-lists, des ressources et des bonnes pratiques pour la planification de la sécurité, la production et la mise à l’échelle Kubernetes. |

## <a name="march-2-2020"></a>2 mars 2020

En réponse aux commentaires sur la continuité de l’approche de migration dans plusieurs sections du Cloud Adoption Framework, notamment la stratégie, la planification, la préparation et la migration, nous avons effectué les mises à jour suivantes. Ces mises à jour sont conçues pour vous aider à comprendre plus facilement les améliorations apportées à la planification et à l’adoption dans le cadre de votre parcours de migration.

### <a name="strategy-updates"></a>Mises à jour de la stratégie

| Article                                                                       | Description                                                                                                                                    |
|-------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| [Équilibrage du portefeuille](../strategy/balance-the-portfolio.md)                 | Cet article apparaît désormais plus haut dans la méthodologie de stratégie. Le processus de réflexion est ainsi exposé plus tôt dans le cycle de vie. |
| [Équilibrage des&nbsp;priorités&nbsp;concurrentes](../strategy/balance-competing-priorities.md) | **Nouvel article :** Décrit l’équilibrage des priorités dans les différentes méthodologies pour vous aider à préciser votre stratégie.                                         |

### <a name="plan-updates"></a>Mises à jour de la planification

| Article                                                             | Description                                                                                                                                                                           |
|---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Bonnes&nbsp;pratiques&nbsp;d’évaluation](../plan/contoso-migration-assessment.md) | Cet article apparaît désormais dans la nouvelle section « Bonnes pratiques » de la méthodologie de planification. La pratique d’évaluation des environnements locaux est ainsi exposée plus tôt dans le cycle de vie. |

### <a name="ready-updates"></a>Mises à jour de la préparation

| Article                                                                   | Description                                                                                                              |
|---------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| [Qu’est-ce&nbsp;qu’une&nbsp;zone&nbsp;d’atterissage&nbsp;?](../ready/landing-zone/index.md)                 | **Nouvel article :** Définit le terme de zone d’atterrissage.                                                                          |
| [Première zone d’atterrissage](../ready/landing-zone/first-landing-zone.md)         | **Nouvel article :** S’étend sur la comparaison des différentes zones d’atterrissage.                                                     |
| [Zone d’atterrissage de migration](../ready/landing-zone/migrate-landing-zone.md)     | La définition du blueprint Cloud Adoption Framework et la sélection de la première zone d’atterrissage sont désormais traitées séparément.         |
| [Zone d’atterrissage Terraform](../ready/landing-zone/terraform-landing-zone.md) | Apparaît maintenant dans la nouvelle section « Zone d’atterrissage » de la méthodologie de préparation pour hisser Terraform dans la conversation sur les zones d’atterrissage. |

### <a name="migration-updates"></a>Mises à jour de la migration

| Article                                                                                          | Description                                                                                                                                                             |
|--------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Vue d'ensemble](../migrate/azure-migration-guide/index.md)                                            | Mise à jour apportée pour clarifier la description du guide, avec un nombre réduit d’étapes.                                                                                                        |
| [Évaluer](../migrate/azure-migration-guide/assess.md)                                             | Ajout d’une section « Hypothèses difficiles » pour montrer que ce niveau d’évaluation fonctionne avec l’approche d’évaluation incrémentielle mentionnée dans la méthodologie de planification. |
| [Classification durant les processus d’évaluation](../migrate/migration-considerations/assess/classify.md) | **Nouvel article :** Décrit l’importance de la classification de chaque ressource et de chaque charge de travail avant la migration.                                                                    |
| [Migrer](../migrate/azure-migration-guide/migrate.md)                                           | Ajout d’une référence à UnifyCloud aux options des outils tiers en réponse aux commentaires des conférences de niveau 1.                                                         |
| [Test,&nbsp;optimiser&nbsp;et&nbsp;promouvoir](../migrate/azure-migration-guide/optimize-and-transform.md)        | Alignement du titre de cet article sur d’autres suggestions d’amélioration de processus.                                                                                           |
| [Vue d’ensemble de l’évaluation](../migrate/migration-considerations/assess/index.md)                           | Mise à jour apportée pour montrer que l’évaluation au cours de cette phase se concentre sur l’adéquation technique d’une charge de travail spécifique et des ressources associées.                               |
| [Check-list de planification](../migrate/migration-considerations/prerequisites/planning-checklist.md)    | Mise à jour apportée pour clarifier l’importance de l’alignement des opérations durant la planification des efforts de migration afin de garantir une bonne gestion de la charge de travail après la migration.                  |

<!-- test:ignoreNextStep -->
