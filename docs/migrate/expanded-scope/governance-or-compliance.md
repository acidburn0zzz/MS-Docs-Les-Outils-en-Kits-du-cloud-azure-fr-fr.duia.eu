---
title: Stratégie de gouvernance ou de conformité
description: Stratégie de gouvernance ou de conformité
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 17952dc4c3ff28f2fcfe1a378a9efb969d65925b
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76803124"
---
# <a name="governance-or-compliance-strategy"></a>Stratégie de gouvernance ou de conformité

Lorsque la gouvernance ou la conformité est requise tout au long d’un effort de migration, une étendue supplémentaire est nécessaire. Les instructions suivantes étendront l’étendue du [guide de migration Azure](../azure-migration-guide/index.md) pour aborder différentes approches afin de répondre aux exigences de gouvernance ou de conformité.

## <a name="general-scope-expansion"></a>Expansion de l’étendue générale

Les activités préalables sont les plus touchées lorsque la gouvernance ou la conformité sont requises. Des ajustements supplémentaires peuvent être nécessaires lors de l’évaluation, de la migration et de l’optimisation.

## <a name="suggested-prerequisites"></a>Prérequis suggérés

La configuration de l’environnement Azure de base peut changer considérablement lors de l’intégration des exigences en matière de gouvernance ou de conformité. Pour comprendre la façon dont les prérequis changent, il est important de comprendre la nature des exigences. Avant de commencer toute migration nécessitant une gouvernance ou une conformité, une approche doit être choisie et implémentée dans l’environnement cloud. Voici quelques approches très performantes couramment observées lors des migrations :

**Approche de gouvernance courante :** Pour la plupart des organisations, le [modèle de gouvernance du Framework d’adoption du cloud](../../govern/guides/index.md) est une approche suffisante qui consiste implémenter un produit minimum viable (MVP), suivi d’itérations ciblées de la maturité de gouvernance pour traiter les risques tangibles identifiés dans le plan d’adoption. Cette approche fournit le minimum d’outils nécessaire pour établir une gouvernance cohérente, de sorte que l’équipe puisse comprendre les outils. Elle développe ensuite ces outils pour résoudre les préoccupations courantes de gouvernance.

**Blueprints de conformité ISO 27001 :** Pour les clients qui doivent adhérer aux normes de conformité ISO, les [exemples de blueprint de services partagés ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-shared/index) peuvent servir de MVP plus efficace pour produire des contraintes de gouvernance plus riches plus tôt dans le processus itératif. L’[exemple App Service Environment/SQL Database ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-ase-sql-workload) se développe sur le blueprint pour mapper les contrôles et déployer une architecture commune pour un environnement d’application. Des blueprints de conformité supplémentaires seront référencés ici à mesure de leur publication.

**Centre de données virtuel :** Un point de départ de gouvernance plus robuste peut être nécessaire. Dans de tels cas, examinez le [Centre de données virtuel (VDC) Azure](../../reference/vdc.md). Cette approche est généralement conseillée lors d’un projet d’adoption à l’échelle de l’entreprise, en particulier si ce projet dépasse 10 000 ressources. C’est également la meilleure option pour les scénarios de gouvernance complexes lorsqu’une des conditions suivantes est requise : exigences de conformité étendues de la part de tiers, expertise approfondie du domaine, ou parité avec des stratégies de gouvernance et des exigences de conformité informatique éprouvées.

### <a name="partnership-option-to-complete-prerequisites"></a>Option de partenariat pour remplir les prérequis

**Services Microsoft :** Les services Microsoft fournissent des offres de solutions qui peuvent s’aligner sur le modèle de gouvernance du Framework d’adoption du cloud, les blueprints de conformité ou les options Centre de données virtuel pour garantir le modèle de gouvernance ou de conformité le plus approprié. Utilisez l’offre de solutions [Secure Cloud Insights (SCI)](https://download.microsoft.com/download/C/7/C/C7CEA89D-7BDB-4E08-B998-737C13107361/Secure_Cloud_Insights_Datasheet_EN_US.pdf) pour établir une image basée sur les données d’un déploiement client dans Azure, valider la maturité de l’implémentation Azure du client tout en identifiant l’optimisation des architectures de déploiement existantes et supprimer les risques relatifs à la disponibilité et à la sécurité de la gouvernance. Selon les insights des clients, vous devriez adopter les approches suivantes :

- **Fondation du cloud :** Établissez les conceptions, les modèles et l’architecture de gouvernance Azure essentiels du client à l’aide de l’offre de solutions [Hybride Cloud Foundation (HCF)](https://download.microsoft.com/download/D/8/7/D872DFD0-1C46-4145-95E4-B5EAB2958B96/Hybrid_Cloud_Foundation_Datasheet_EN_US.pdf). Mappez les exigences du client à l’architecture de référence la plus appropriée. Implémentez un produit minimum viable constitué de services partagés et de charges de travail IaaS.
- **Modernisation du cloud :** Utilisez l’offre de solutions [Cloud Modernisation](https://download.microsoft.com/download/3/7/3/373F90E3-8568-44F3-B096-CD9C1CD28AB7/Cloud_Modernization_Datasheet_EN_US.pdf) comme approche complète pour déplacer des applications; des données et des infrastructures vers un cloud de classe Entreprise, ainsi que pour optimiser et moderniser après le déploiement dans le cloud.
- **Innovez grâce au cloud :** Impliquez les clients avec une approche de solutions de type [centre d’excellence du cloud (CCoE)](https://download.microsoft.com/download/F/8/B/F8BBE4BD-E5F8-4DFB-82F7-C0A4E17051BB/Cloud_Center_of_Excellence_Datasheet_EN_US.pdf) innovante et unique, qui crée une organisation informatique moderne pour permettre une agilité à grande échelle avec DevOps tout en gardant le contrôle. La solution implémente une approche agile pour capturer les besoins de l’entreprise, réutilise les packages de déploiement alignés sur les stratégies de sécurité, de conformité et de management des services et maintient la plateforme Azure alignée sur les procédures opérationnelles.

## <a name="assess-process-changes"></a>Évaluer les changements de processus

Pendant l’évaluation, des décisions supplémentaires sont requises pour s’adapter à l’approche de gouvernance requise. L’équipe de gouvernance du cloud doit fournir à tous les membres de l’équipe d’adoption du cloud des déclarations de stratégie, des conseils architecturaux ou des exigences de gouvernance/conformité avant l’évaluation d’une charge de travail.

### <a name="suggested-action-during-the-assess-process"></a>Action suggérée pendant le processus d’évaluation

Les exigences en matière d’évaluation de la gouvernance et de la conformité sont trop spécifiques au client pour fournir des indications générales sur les étapes réellement effectuées pendant l’évaluation. Cependant, le processus doit inclure des tâches et du temps alloué pour « l’alignement sur les exigences de conformité/gouvernance ». Pour une compréhension plus approfondie de ces exigences, consultez les liens suivants :

Pour une compréhension plus approfondie de la gouvernance, consultez la [vue d’ensemble des cinq disciplines de la gouvernance cloud](../../govern/governance-disciplines.md). Cette section du Framework d’adoption du cloud comprend également des modèles pour documenter les stratégies, les recommandations et les exigences de chacune des cinq sections :

- [Cost Management](../../govern/cost-management/template.md)
- [Base de référence de la sécurité](../../govern/security-baseline/template.md)
- [Resource Consistency]../../govern/resource-consistency/template.md)
- [Identity Baseline]../../govern/identity-baseline/template.md)
- [Accélération du déploiement](../../govern/deployment-acceleration/template.md)

Pour obtenir des conseils sur l’élaboration d’une gouvernance basée sur le modèle de gouvernance du Framework d’adoption du cloud, consultez [Implémentation d’une stratégie de gouvernance cloud](../../govern/corporate-policy.md).

## <a name="optimize-and-promote-process-changes"></a>Changements aux processus d’optimisation et de promotion

Au cours des processus d’optimisation et de promotion, l’équipe de gouvernance cloud doit consacrer le temps nécessaire pour tester et valider l’adhésion aux standards de gouvernance et de conformité. En outre, cette étape est un bon moment pour injecter des processus afin que l’équipe de gouvernance cloud organise des modèles qui pourraient fournir une [accélération de déploiement](../../govern/deployment-acceleration/index.md) supplémentaire pour les projets à venir.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Action suggérée pendant le processus d’optimisation et de promotion

Au cours de ce processus, le plan du projet doit inclure du temps alloué à l’équipe de gouvernance cloud afin d’effectuer une évaluation de la conformité pour chaque charge de travail planifiée pour la promotion en production.

## <a name="next-steps"></a>Étapes suivantes

En guise d’élément final sur la [check-list d’expansion d’étendue](./index.md), revenez à la check-list et réévaluez les exigences d’étendue supplémentaires pour l’effort de migration.

> [!div class="nextstepaction"]
> [Check-list d’expansion d’étendue](./index.md)
