---
title: Outils et modèles
description: Trouvez les outils et les modèles qui sont disponibles dans Cloud Adoption Framework pour vous aider à accélérer votre adoption du cloud.
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.topic: article
author: JanetCThomas
ms.author: janet
ms.date: 04/14/2020
ms.openlocfilehash: e37019a571d5868b98083e9f7fba0198da2b1ff0
ms.sourcegitcommit: 825f9ae5b6cdd2fa6cb18c14a9733ba9106194f2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81646725"
---
<!-- cSpell:ignore CAF Terraform's -->

# <a name="tools-and-templates"></a>Outils et modèles

L’infrastructure d’adoption du Cloud comprend des outils qui vous aident à implémenter rapidement des modifications techniques. Utilisez ces outils, modèles et évaluations pour accélérer l’adoption du cloud. Les ressources suivantes peuvent vous aider à chaque phase d’adoption. Certains des outils et modèles peuvent être utilisés dans plusieurs phases.

## <a name="strategy"></a>Stratégie

| Ressource | Description |
|----------|-------------|
| [Suivi de parcours cloud](https://docs.microsoft.com/assessments/?mode=pre-assessment&id=cloud-journey-tracker) | Identifiez votre chemin d’adoption du cloud en fonction des besoins de votre entreprise. |
| [Modèle de stratégie&nbsp;&nbsp;et de&nbsp;plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) | Documentez les décisions à mesure que vous exécutez votre stratégie et votre plan d’adoption du cloud. |

## <a name="plan"></a>Plan

| Ressource | Description |
|----------|-------------|
| [Suivi de parcours cloud](https://docs.microsoft.com/assessments/?mode=pre-assessment&id=cloud-journey-tracker) | Identifiez votre chemin d’adoption du cloud en fonction des besoins de votre entreprise. |
| [Modèle de stratégie&nbsp;&nbsp;et de&nbsp;plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) | Documentez les décisions à mesure que vous exécutez votre stratégie et votre plan d’adoption du cloud. |
| [Générateur de plan d’adoption du cloud](../plan/template.md) | Standardisez les processus en déployant un backlog sur [Azure Boards](https://docs.microsoft.com/azure/devops/boards/get-started/what-is-azure-boards) à l’aide du modèle plan d’adoption du cloud. |

## <a name="ready"></a>Ready

| Ressource | Description |
|----------|-------------|
| [Check-list de disponibilité](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/ready/readiness-checklist.docx) | Utilisez cette check-list pour préparer votre environnement en vue de son adoption, y compris la préparation de votre première zone de migration, la personnalisation du plan et son développement. |
| [Modèle de suivi d’attribution de noms et marquage](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx) | Documentez les décisions relatives au nommage et aux normes de marquage pour garantir la cohérence et réduire la durée d’intégration. |
| [Blueprint&nbsp;de base&nbsp;CAF](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready/migration-landing-zone-governance) | Utilisez une implémentation légère d’une fondation de gouvernance initiale pour offrir une expérience pratique avec les outils de gouvernance dans Azure. |
| [Blueprint de zone d’accueil de la migration CAF](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready/migration-landing-zone) | Approvisionnez et préparez l’hébergement des charges de travail en cours de migration à partir d’un environnement local vers Azure. Pour plus d’informations sur ce plan, consultez [Déployer une zone d’atterrissage de migration](https://docs.microsoft.com/azure/architecture/cloud-adoption/ready/azure-readiness-guide/migration-landing-zone). |
| [Blueprint de la zone d’atterrissage Terraform](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready/terraform-landing-zones/landingzone_caf_foundations) | Base de code open source pour la version Terraform des plans CAF. |
| [Registre Terraform](https://registry.terraform.io/search?q=aztfmod) | Site web du registre de Terraform, filtré pour répertorier tous les modules d’infrastructure d’adoption du cloud nécessaires à la création d’une zone d’atterrissage Terraform. |

## <a name="govern"></a>Gouvernance

| Ressource | Description |
|----------|-------------|
| [Évaluation de benchmark de gouvernance](https://cafbaseline.com) | Identifiez les lacunes entre votre état actuel et vos priorités métier et recevez les ressources appropriées pour vous aider à combler ces lacunes. |
| [Blueprint&nbsp;de base&nbsp;CAF](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready/migration-landing-zone-governance) | Implémentation légère d’une fondation de gouvernance initiale pour offrir une expérience pratique relative aux outils de gouvernance dans Azure. |
| [Modèle de processus de gouvernance](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Governance%20Discipline%20Template.docx) | Définissez l’ensemble de base des processus de gouvernance utilisés pour appliquer chaque discipline de gouvernance. |
| [Modèle de processus Cost Management](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Cost%20Management%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur la gestion des coûts. |
| [Modèle de processus d’accélération du déploiement](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Deployment%20Acceleration%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur l’accélération du déploiement. |
| [Modèle de processus d’identité](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Identity%20Baseline%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation en vous concentrant sur les exigences relatives aux identités. |
| [Modèle de processus de cohérence des ressources](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Resource%20Consistency%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur la cohérence des ressources. |
| [Modèle de processus Base de référence de la sécurité](https://archcenter.blob.core.windows.net/cdn/fusion/governance/Security%20Baseline%20Discipline%20Template.docx) | Définissez les instructions de stratégie et les conseils de conception qui vous permettent de faire évoluer la gouvernance cloud au sein de votre organisation, en vous concentrant sur la ligne de base de sécurité. |

## <a name="manage"></a>Gérer

| Ressource | Description |
|----------|-------------|
| [Évaluation de l’architecture Azure](https://docs.microsoft.com/assessments/?id=azure-architecture-review) | Cette évaluation en ligne vous aidera à définir des architectures et des options d’opérations spécifiques à la charge de travail. |
| [Best&nbsp;practices&nbsp;source&nbsp;code](https://github.com/microsoft/CloudAdoptionFramework/tree/master/manage/Automation-Best-Practices) | Ce code source déployable complète et accélère l’adoption des conseils de bonnes pratiques de gestion des serveurs Azure. Utilisez ce code source pour activer rapidement la gestion des opérations et établir une ligne de base des opérations. |
| [Classeur Operations Management](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) | Documentez les décisions relatives à la gestion des opérations dans le cloud et facilitez les conversations avec les parties prenantes de l’entreprise pour garantir le respect des contrats de niveau de service, des investissements dans le domaine de la résilience et l’allocation de budgets liés aux opérations. |

## <a name="organize"></a>Organiser

| Ressource | Description |
|----------|-------------|
| [Diagramme RACI entre les équipes](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx) | Pour suivre les décisions de structure organisationnelle au fur et à mesure, téléchargez et modifiez le modèle de feuille de calcul RACI. |
