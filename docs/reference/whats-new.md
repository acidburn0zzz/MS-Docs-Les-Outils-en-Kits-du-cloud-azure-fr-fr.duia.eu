---
title: Nouveautés
description: Découvrez les mises à jour de Microsoft Cloud Adoption Framework pour Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/02/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.openlocfilehash: a3e316d49acaaee00d5ecd10efac9aa15c2dbd49
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80353687"
---
# <a name="whats-new-in-the-microsoft-cloud-adoption-framework"></a>Nouveautés de Microsoft Cloud Adoption Framework

## <a name="fulfilling-the-vision"></a>Concrétisation de la vision

Le Framework est maintenant en disponibilité générale (GA). Toutefois, nous développons encore activement ce framework en collaboration avec les clients, les partenaires et les équipes internes. Pour encourager les partenariats, le contenu est publié dès qu’il est disponible. Ces versions publiques permettent de tester, de valider et d’affiner petit à petit les recommandations.

Les changements importants sont indiqués dans les notes de publication suivantes.

## <a name="migration-update-03022020"></a>Mise à jour de la migration : 02/03/2020

Cette version fait écho aux commentaires sur la continuité de l’approche de migration via plusieurs méthodologies, notamment la stratégie, la planification, la préparation et la migration. L’objectif de cette version a été de permettre aux lecteurs de mieux comprendre le perfectionnement continu de la planification et de l’adoption durant la poursuite du parcours de migration par les clients. Les changements suivants ont été apportés pour respecter l’esprit de cette version :

### <a name="new-articles"></a>Nouveaux articles

- [Équilibre des priorités concurrentes](../strategy/balance-competing-priorities.md) : Décrit l’équilibre des priorités de chaque méthodologie pour rendre compte des stratégies des clients
- [Classification durant l’évaluation des processus](../migrate/migration-considerations/assess/classify.md) : Décrit l’importance de la classification de chaque ressource et de chaque charge de travail avant la migration.

### <a name="restructure-landing-zone-process"></a>Restructurer le processus de la zone d’atterrissage

La première zone d’atterrissage a été retirée du guide de préparation pour constituer sa propre section. Cette approche nous permet de développer le concept de zones d’atterrissage et d’options de zones d’atterrissage. Cela a également conduit à la création de quelques articles supplémentaires :

- [Qu’est-ce qu’une zone d’atterrissage ?](../ready/landing-zone/index.md) : Définit les termes de zone d’atterrissage
- [Première zone d’atterrissage](../ready/landing-zone/first-landing-zone.md) : S’étend sur la comparaison des différentes zones d’atterrissage
- [Zone d’atterrissage de migration](../ready/landing-zone/migrate-landing-zone.md) : Déplacement de l’article précédent sur le blueprint de zone d’atterrissage, pour séparer la définition du blueprint du CAF (Cloud Adoption Framework) de la sélection de la première zone d’atterrissage, et fournir ainsi davantage d’options de zone d’atterrissage.
- Article sur la [zone d’atterrissage Terraform](../ready/landing-zone/terraform-landing-zone.md) : Déplacement de la section « Étendue supplémentaire » de la méthodologie de préparation vers la nouvelle section « Zone d’atterrissage » de la méthodologie de préparation, pour traiter de Terraform, un élément très important de la conversation sur la zone d’atterrissage.
- Regroupement des considérations générales sur les zones d’atterrissage dans la table des matières sous « Considérations générales relatives aux zones d’atterrissage ».
- Déplacement des bonnes pratiques de sécurité de la méthodologie de migration vers une nouvelle section de zone d’atterrissage intitulée « Améliorer la sécurité des zones d’accueil (données sensibles) » pour exposer ces conseils d’aide aux lecteurs plus tôt dans le cycle de vie.

### <a name="refinements-to-the-azure-migration-guide"></a>Améliorations apportées au guide de migration Azure

Les modèles de trafic utilisateur tendent à montrer que cette section de contenu est plus susceptible d’être utilisée par les implémenteurs et les architectes durant leur première migration. Pour permettre une meilleure prise en charge de cette audience, l’objectif du guide de migration a été affiné afin de mieux correspondre à l’intention initiale qui consiste à exposer aux lecteurs les outils utilisés durant une première migration.

- [Vue d’ensemble](../migrate/azure-migration-guide/index.md) : Description plus claire du guide, avec un nombre réduit d’étapes.
- [Évaluer](../migrate/azure-migration-guide/assess.md) : Illustration plus pertinente qui montre que l’évaluation au cours de cette phase se concentre sur l’adéquation technique d’une charge de travail spécifique et des ressources associées. Ajout d’une section Hypothèses difficiles pour montrer que ce niveau d’évaluation fonctionne avec l’approche d’évaluation incrémentielle mentionnée initialement dans la méthodologie de planification.
- [Migration](../migrate/azure-migration-guide/migrate.md) : En réponse aux commentaires des conférences de niveau 1, une référence à UnifyCloud a été ajoutée aux options des outils tiers.
- [Tester, optimiser et promouvoir](../migrate/azure-migration-guide/optimize-and-transform.md) : Alignement du titre de cet article sur d’autres suggestions d’amélioration de processus.

### <a name="refinements-to-migration-process-improvements"></a>Améliorations supplémentaires du processus de migration

- [Vue d’ensemble de l’évaluation](../migrate/migration-considerations/assess/index.md) : Illustration plus pertinente montrant que l’évaluation au cours de cette phase se concentre sur l’adéquation technique d’une charge de travail spécifique et des ressources associées.
- [Liste de contrôle de planification](../migrate/migration-considerations/prerequisites/planning-checklist.md) : Clarification de l’importance de l’alignement des opérations durant la planification des efforts de migration pour garantir une bonne gestion de la charge de travail, une fois la migration effectuée.

### <a name="placement-of-related-articles"></a>Placement d’articles connexes

Chaque liste d’articles ci-dessous a été déplacée. Le trafic est redirigé vers le nouvel emplacement.

- Article sur les [bonnes pratiques d’évaluation](../plan/contoso-migration-assessment.md) : Déplacement de la section « Bonnes pratiques » de la méthodologie de migration vers la nouvelle section « Bonnes pratiques » de la méthodologie de planification. Ce déplacement permet d’exposer les lecteurs à la pratique qui consiste à évaluer les environnements locaux plus tôt dans le cycle de vie.
- Article sur l’[équilibrage du portefeuille](../strategy/balance-the-portfolio.md) : Déplacement de la section « Étendue supplémentaire » de la méthodologie de migration vers la méthodologie de stratégie. Ce déplacement permet d’exposer les lecteurs à ce processus de réflexion plus tôt dans le cycle de vie.

### <a name="alignment-of-the-changes"></a>Alignement des changements

- [Vue d’ensemble de la préparation](../ready/index.md) : Mise à jour des quatre étapes de vue d’ensemble de la préparation pour refléter l’amélioration du processus
- [Vue d’ensemble de la migration](../migrate/index.md) : Mise à jour des étapes de vue d’ensemble de la migration pour refléter l’amélioration du processus
- [Graphique de la méthodologie de migration](../migrate/index.md) : Mise à jour de l’image de la méthodologie pour refléter les changements
- [Graphique de vue d’ensemble](../index.md) : Mises à jour du graphisme de vue d’ensemble pour refléter les changements
