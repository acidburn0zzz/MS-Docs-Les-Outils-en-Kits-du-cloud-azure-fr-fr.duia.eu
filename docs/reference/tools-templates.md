---
title: Outils et modèles
description: Trouvez les outils et les modèles qui sont disponibles dans Cloud Adoption Framework pour vous aider à accélérer votre adoption du cloud.
author: JanetCThomas
ms.author: janet
ms.date: 04/14/2020
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.topic: article
ms.openlocfilehash: 3968e453eb89a0f00d7fd23eeec90fb6a947cd05
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83756054"
---
<!-- cSpell:ignore Terraform's -->

# <a name="tools-and-templates"></a>Outils et modèles

L’infrastructure d’adoption du Cloud comprend des outils qui vous aident à implémenter rapidement des modifications techniques. Utilisez ces outils, modèles et évaluations pour accélérer l’adoption du cloud. Les ressources suivantes peuvent vous aider à chaque phase d’adoption. Certains des outils et modèles peuvent être utilisés dans plusieurs phases.

## <a name="strategy"></a>Stratégie

| Ressource | Description |
|----------|-------------|
| [Suivi de parcours cloud](https://docs.microsoft.com/assessments/?mode=pre-assessment&id=cloud-journey-tracker) | Identifiez votre chemin d’adoption du cloud en fonction des besoins de votre entreprise. |
| [Modèle de stratégie&nbsp;et &nbsp;de&nbsp;plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) | Documentez les décisions à mesure que vous exécutez votre stratégie et votre plan d’adoption du cloud. |

## <a name="plan"></a>Plan

| Ressource | Description |
|----------|-------------|
| [Suivi de parcours cloud](https://docs.microsoft.com/assessments/?mode=pre-assessment&id=cloud-journey-tracker) | Identifiez votre chemin d’adoption du cloud en fonction des besoins de votre entreprise. |
| [Modèle de stratégie&nbsp;et &nbsp;de&nbsp;plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) | Documentez les décisions à mesure que vous exécutez votre stratégie et votre plan d’adoption du cloud. |
| [Générateur de plan d’adoption du cloud](../plan/template.md) | Standardisez les processus en déployant un backlog sur [Azure Boards](https://docs.microsoft.com/azure/devops/boards/get-started/what-is-azure-boards) à l’aide du modèle plan d’adoption du cloud. |

## <a name="ready"></a>Ready

| Ressource | Description |
|----------|-------------|
| [Check-list de disponibilité](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/ready/readiness-checklist.docx) | Utilisez cette check-list pour préparer votre environnement en vue de son adoption, y compris la préparation de votre première zone de migration, la personnalisation du plan et son développement. |
| [Modèle de suivi d’attribution de noms et marquage](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx) | Documentez les décisions relatives au nommage et aux normes de marquage pour garantir la cohérence et réduire la durée d’intégration. |
| [Blueprint&nbsp;de base&nbsp;CAF](https://github.com/Microsoft/CloudAdoptionFramework/tree/master/ready/migration-landing-zone-governance) | Utilisez une implémentation légère d’une fondation de gouvernance initiale pour offrir une expérience pratique avec les outils de gouvernance dans Azure. |
| [Blueprint de zone d’accueil de la migration CAF](https://github.com/Microsoft/CloudAdoptionFramework/tree/master/ready/migration-landing-zone) | Approvisionnez et préparez l’hébergement des charges de travail en cours de migration à partir d’un environnement local vers Azure. Pour plus d’informations sur ce plan, consultez [Déployer une zone d’atterrissage de migration](../ready/landing-zone/migrate-landing-zone.md). |
| [Blueprint de la zone d’atterrissage Terraform](../ready/landing-zone/terraform-landing-zone.md) | Base de code open source pour la version Terraform des blueprints des zones d'atterrissage CAF. |
| [Registre Terraform](https://registry.terraform.io/search?q=aztfmod) | Site web du registre de Terraform, filtré pour lister tous les modules du Cloud Adoption Framework nécessaires à la création d’une zone d’atterrissage Terraform. |

## <a name="govern"></a>Gouvernance

| Ressource | Description |
|----------|-------------|
| [Évaluation de benchmark de gouvernance](https://cafbaseline.com) | Identifiez les lacunes entre votre état actuel et vos priorités métier et recevez les ressources appropriées pour vous aider à combler ces lacunes. |
| [Blueprint&nbsp;de base&nbsp;CAF](https://github.com/Microsoft/CloudAdoptionFramework/tree/master/ready/migration-landing-zone-governance) | Implémentation légère d’une fondation de gouvernance initiale pour offrir une expérience pratique relative aux outils de gouvernance dans Azure. |
| [Modèle de processus de gouvernance](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Governance%20Discipline%20Template.docx) | Définissez l’ensemble de base des processus de gouvernance utilisés pour appliquer chaque discipline de gouvernance. |
| [Modèle de processus Cost Management](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Cost%20Management%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur la gestion des coûts. |
| [Modèle de processus d’accélération du déploiement](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Deployment%20Acceleration%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur l’accélération du déploiement. |
| [Modèle de processus d’identité](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Identity%20Baseline%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation en vous concentrant sur les exigences relatives aux identités. |
| [Modèle de processus de cohérence des ressources](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Resource%20Consistency%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur la cohérence des ressources. |
| [Modèle de processus de ligne de base de la sécurité](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Security%20Baseline%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur la ligne de base de sécurité. |

## <a name="manage"></a>Gérer

| Ressource | Description |
|----------|-------------|
| [Microsoft Azure Well-Architected Review](https://docs.microsoft.com/assessments/?id=azure-architecture-review) | Cette évaluation en ligne vous aidera à définir des architectures et des options d’opérations spécifiques à la charge de travail. |
| [Best&nbsp;practices&nbsp;source&nbsp;code](https://github.com/Microsoft/CloudAdoptionFramework/tree/master/manage/Automation-Best-Practices) | Ce code source déployable complète et accélère l’adoption des bonnes pratiques pour les services de gestion des serveurs Azure. Utilisez ce code source pour activer rapidement la gestion des opérations et établir une ligne de base des opérations. |
| [Classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) | Documentez les décisions relatives à la gestion des opérations dans le cloud et facilitez les conversations avec les parties prenantes de l’entreprise pour garantir le respect des contrats de niveau de service, des investissements dans le domaine de la résilience et l’allocation de budgets liés aux opérations. |

## <a name="organize"></a>Organiser

| Ressource | Description |
|----------|-------------|
| [Diagramme RACI entre les équipes](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx) | Pour suivre les décisions de structure organisationnelle au fur et à mesure, téléchargez et modifiez le modèle de feuille de calcul RACI. |
