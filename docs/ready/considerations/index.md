---
title: Considérations relatives aux zones d’accueil Azure
description: Découvrez en quoi les zones d’accueil constituent les éléments constitutifs de tout environnement d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/20/2019
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 5eb0dc016bcfe7778727b5a61e392e3dd3581539
ms.sourcegitcommit: 238e7a06b56950cebdcc8f75924849fc995e6ff2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2020
ms.locfileid: "77173368"
---
# <a name="landing-zone-considerations"></a>Considérations relatives aux zones d’accueil

Une zone d’accueil est l’élément constitutif de tout environnement d’adoption du cloud. Le terme *zone d’accueil* décrit un environnement qui a été provisionné et préparé pour héberger des charges de travail dans un environnement cloud tel qu’Azure. Une zone d’accueil entièrement fonctionnelle est le livrable final de toute itération de méthodologie de disponibilité du Framework d’adoption du cloud.

![Considérations relatives aux zones d’accueil](../../_images/ready/landing-zone-considerations.png)

Cette image montre les principales considérations lors de l’implémentation d’un déploiement de zone d’accueil. Ces considérations peuvent être classées en trois catégories : hébergement, fondamentaux Azure et gouvernance.

## <a name="hosting-considerations"></a>Considérations en matière d’hébergement

Toutes les zones d’accueil fournissent une structure aux options d’hébergement. La structure est créée explicitement par le biais de contrôles de gouvernance ou naturellement par le biais de l’adoption de services au sein de la zone d’accueil. Les articles suivants peuvent vous aider à prendre des décisions qui sont ensuite répercutées dans le blueprint ou dans les scripts d’automatisation qui créent la zone d’accueil :

- **[Décisions en matière de calcul](./compute-options.md)** . Afin de réduire la complexité opérationnelle, alignez les options de calcul avec l’objectif de la zone d’accueil. Cette décision peut être appliquée à l’aide de chaînes d’outils d’automatisation, telles que des initiatives Azure Policy et des blueprints de zone d’accueil.
- **[Décisions en matière de stockage](./storage-options.md)** . Choisissez la solution de stockage Azure appropriée pour prendre en charge vos besoins en charges de travail.
- **[Décisions en matière de réseau](./networking-options.md).** Choisissez les services, outils et architectures réseau qui prendront en charge les besoins de votre organisation concernant la charge de travail, la gouvernance et la connectivité.
- **[Décisions en matière de base de données](./data-options.md)** . Identifiez la technologie de base de données qui convient le mieux à vos besoins en termes de charge de travail.

## <a name="azure-fundamentals"></a>Fondamentaux Azure

Chaque zone d’accueil fait partie d’une solution plus large ayant comme objectif d’organiser les ressources dans un environnement cloud. Pour une organisation, les fondamentaux Azure sont des éléments constitutifs essentiels.

- **[Concepts fondamentaux Azure](./fundamental-concepts.md).** Découvrez les concepts fondamentaux et les termes utilisés pour organiser les ressources dans Azure et quel est le lien entre les différents concepts.
- **[Guide de décision pour la cohérence des ressources](../../decision-guides/resource-consistency/index.md)** . Une fois que vous avez compris tous les fondamentaux, le guide de décision concernant l’organisation des ressources peur vous aider à prendre des décisions permettant de structurer la zone d’accueil.

## <a name="governance-considerations"></a>Considérations sur la gouvernance

Les méthodologies de gouvernance du Framework d’adoption du cloud établissent un processus pour régir l’environnement dans son ensemble. Toutefois, il existe de nombreux cas d’usage qui nécessitent de prendre des décisions de gouvernance différentes pour chaque zone d’atterrissage. En effet, dans de nombreux scénarios, une base de référence de gouvernance différente est appliquée pour chacune des zones d’atterrissage, même si les bases de référence sont établies de manière globale. Cela est vrai pour les quelques premières zones d’accueil déployées par une organisation.

Les articles suivants vous aideront à prendre des décisions liées à la gouvernance concernant votre zone d’accueil. Vous pouvez factoriser chaque décision dans vos bases de référence de gouvernance.

- **Exigences en matière de coûts**. En fonction des facteurs de motivation d’adoption du cloud et des engagements opérationnels pris dans le cadre de cet environnement par une organisation, différentes configurations de gestion des coûts peuvent devoir être changées pour la zone d’accueil.
- **Décisions en matière de supervision**. En fonction des exigences opérationnelles de cette zone d’accueil, différents outils de supervision peuvent être déployés. L’article sur les décisions en matière de supervision permet d’identifier les outils dont le déploiement est le plus utile.
- **Utilisation du contrôle d’accès en fonction du rôle**. Le [contrôle d’accès en fonction du rôle (RBAC)](../considerations/roles.md) Azure offre une gestion précise de l’accès aux ressources basée sur des groupes et organisée autour des rôles d’utilisateur.
- **Décisions en matière de stratégie**. Les [exemples de blueprints Azure](https://docs.microsoft.com/azure/governance/blueprints/samples) fournissent des blueprints de conformité précréés, chacun avec des initiatives de stratégie prédéfinies. Les décisions en matière de stratégie aident à sélectionner le meilleur blueprint ou la meilleure initiative en fonction des exigences et des contraintes.
- **[Créer une cohérence de cloud hybride](./hybrid-consistency.md)** . Créez des solutions de cloud hybride qui offrent à votre organisation les avantages de l’innovation du cloud tout en conservant la plupart des aspects pratiques de la gestion locale.
