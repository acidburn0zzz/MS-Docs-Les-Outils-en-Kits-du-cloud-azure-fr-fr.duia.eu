---
title: Améliorer les opérations de zone d’atterrissage
description: Améliorer les opérations de zone d’atterrissage
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 1e338974e3720609640b23e7123fc003801cb371
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83756513"
---
# <a name="improve-landing-zone-operations"></a>Améliorer les opérations de zone d’atterrissage

Les opérations de zone d’atterrissage fournissent la base initiale pour la gestion des opérations. À mesure que les opérations sont mises à l’échelle, ces améliorations refactorisent les zones d’atterrissage pour répondre aux besoins croissants de performances, de fiabilité et d’excellence opérationnelle.

## <a name="landing-zone-operations-best-practices"></a>Meilleures pratiques pour les opérations de zone d’atterrissage

Les liens suivants fournissent les meilleures pratiques pour améliorer les opérations liées aux zones d’atterrissage.

- [Gestion des serveurs Azure](../../manage/azure-server-management/index.md) : Guide d'intégration pour incorporer les outils et services cloud natifs nécessaires à la gestion des opérations.
- [Supervision hybride](../../manage/monitor/index.md) : De nombreux clients ont déjà beaucoup investi dans System Center Operations Manager. Pour eux, ce guide de supervision hybride permet de comparer les outils de création de rapports natifs du cloud avec les outils Operations Manager. Cette comparaison permet de choisir plus facilement les outils à utiliser pour la gestion opérationnelle.
- [Centraliser les opérations de gestion](../../manage/centralize-operations.md) : Utilisez Azure Lighthouse pour centraliser la gestion des opérations entre plusieurs locataires Azure.
- [Mettre en place une évaluation de l’adéquation opérationnelle](../../manage/operational-fitness-review.md) : Passez en revue un environnement à des fins opérationnelles.
- Meilleures pratiques pour les opérations spécifiques aux charges de travail :
  - [Liste de contrôle de résilience](https://docs.microsoft.com/azure/architecture/checklist/resiliency-per-service?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json)
  - [Analyse du mode d’échec](https://docs.microsoft.com/azure/architecture/resiliency/failure-mode-analysis?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json)
  - [Récupérer après une interruption de service à l’échelle de la région](https://docs.microsoft.com/azure/architecture/resiliency/recovery-loss-azure-region?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json)
  - [Récupérer suite à une altération de données ou à une suppression accidentelle](https://docs.microsoft.com/azure/architecture/framework/resiliency/data-management?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json)

## <a name="four-steps-to-improve-operations-beyond-a-single-landing-zone"></a>Quatre étapes pour améliorer les opérations au-delà d’une seule zone d’atterrissage

La [méthodologie Manage](../../manage/index.md) fournit des instructions générales sur la création de la capacité de gestion des opérations, consultez la rubrique [Gérer la méthodologie](../../manage/index.md). Nous allons utiliser la structure de base de cette méthodologie et les étapes suivantes de cette méthodologie pour améliorer les opérations des zones d’atterrissage et les opérations dans toutes les zones d’atterrissage.

<!-- cSpell:ignore caf -->

![Méthodologie de gestion](../../_images/manage/caf-manage.png)

1. [Établir une base de référence de gestion](../../manage/azure-server-management/index.md) : Une ligne de base de gestion établit la base de la gestion des opérations. Les instructions de cette première étape peuvent être appliquées à n’importe quelle zone d’atterrissage pour améliorer les opérations initiales.
2. [Définir des engagements métier](../../manage/considerations/business-alignment.md) : La compréhension de la gravité et de l’impact de chaque charge de travail au sein d’une zone d’atterrissage établit une « définition de Terminé » pour toutes les améliorations de la gestion continue pour toute zone d’atterrissage. Ce processus permet également d’identifier les exigences en matière de fiabilité, de performances et d’exploitation de chaque charge de travail.
3. [Développer la base de référence de gestion](../../manage/best-practices.md) : Cet ensemble de meilleures pratiques peut être appliqué pour améliorer les opérations de zone d’atterrissage au-delà de la ligne de base initiale.
4. [Principes de conception et d’opérations avancés](../../manage/design-principles.md) : Passez en revue la conception et les opérations de charges de travail, de plates-formes ou de zones d’atterrissage complètes spécifiques pour répondre à des exigences plus poussées.

## <a name="test-driven-development-cycle"></a>Cycle de développement piloté par les tests

Avant de commencer à apporter des améliorations à la sécurité, il est important de comprendre la « définition de Terminé » et tous les « critères d’acceptation ». Pour plus d'informations, consultez les articles consacrés au [développement piloté par les tests des zones d'atterrissage](./test-driven-development.md) et au [développement piloté par les tests dans Azure](./azure-test-driven-development.md).

![Processus de développement piloté par les tests pour les zones d’atterrissage cloud](../../_images/ready/test-driven-development-process.png)

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [améliorer la gouvernance des zones d’atterrissage](./landing-zone-governance.md) pour prendre en charge l’adoption à grande échelle.

> [!div class="nextstepaction"]
> [Améliorer la gouvernance des zones d’atterrissage](./landing-zone-governance.md)
