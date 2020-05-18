---
title: Préparation aux compétences pour la supervision du cloud
description: Préparation aux compétences pour la supervision du cloud
author: BrianBlanchard
ms.author: magoedte
ms.date: 05/05/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: c32ecde3bc5929bc8ed360b1d792e5f2345bfd8f
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83223675"
---
<!-- cSpell:ignore kusto ITIL -->

# <a name="skills-readiness-for-cloud-monitoring"></a>Préparation aux compétences pour la supervision du cloud

Pendant la phase de planification de votre parcours de migration, l’objectif est de développer les plans nécessaires pour guider l’implémentation. Les plans doivent également inclure la manière dont vous opérerez ces charges de travail avant qu’elles soient transférées ou publiées en production, et non après. Les parties prenantes de l’entreprise s’attendent à ce que vous leur fournissiez des services précieux, et sans interruption. Les membres du personnel informatique se rendent compte qu’ils ont besoin d’acquérir de nouvelles compétences et de s’adapter afin d’utiliser les services Azure intégrés pour superviser efficacement les ressources dans les environnements Azure et hybrides.

L’acquisition des qualifications nécessaires peut être accélérée grâce aux parcours d’apprentissage suivants :

- L’introduction à [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/management/overview) décrit les concepts de base de la gestion et du déploiement de ressources Azure. Le personnel informatique qui gère l’expérience de supervision au sein de l’entreprise doit comprendre les étendues de gestion, le contrôle d’accès en fonction du rôle (RBAC), l’utilisation de modèles Azure Resource Manager et la gestion des ressources à l’aide d’Azure CLI et d’Azure PowerShell.

- Découvrez comment sécuriser des ressources à l’aide d’une stratégie, du contrôle d’accès en fonction du rôle et d’autres services Azure en consultant [Implémenter une sécurité pour la gestion des ressources dans Azure](https://docs.microsoft.com/learn/paths/implement-resource-mgmt-security).

- L’introduction à [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) explique comment utiliser Azure Policy pour créer, attribuer et gérer des stratégies. Azure Policy peut déployer et configurer les agents Azure Monitor, activer la supervision avec Azure Monitor pour machines virtuelles et Azure Security Center, déployer des paramètres de diagnostic, auditer les paramètres de configuration d’invité, et ainsi de suite.

- Introduction à l’[interface de ligne de commande Azure](https://docs.microsoft.com/cli/azure/get-started-with-azure-cli?view=azure-cli-latest) (Azure CLI), qui est notre interface de ligne de commande multiplateforme dédiée à la gestion des ressources Azure. Consultez également l’introduction à [Azure PowerShell](https://docs.microsoft.com/powershell/azure/?view=azps-3.6.1). LinkedIn propose, dans le cadre de son cours de niveau débutant intitulé [Learning Azure Management Tools](https://www.linkedin.com/learning/learning-azure-management-tools) (Découverte des outils de gestion Azure), des sessions couvrant les langages de programmation PowerShell et Azure CLI :

  - [Use the Azure CLI](https://www.linkedin.com/learning/learning-azure-management-tools/use-the-azure-cli) (Utiliser Azure CLI)
  - [Prise en main d’Azure PowerShell](https://www.linkedin.com/learning/learning-azure-management-tools/understand-azure-powershell)

- Découvrez comment écrire des [requêtes de journal dans Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-queries). Le langage de requête Kusto est la ressource principale pour écrire des requêtes de journal Azure Monitor afin d’explorer et d’analyser les données de journal entre les données collectées à partir d’Azure et les dépendances d’applications de ressources hybrides, y compris l’application active.

- Découvrez comment [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) vous aide à voir la disponibilité et les performances de vos applications et services à partir d’un emplacement unique. Pluralsight offre les cours suivants pour vous aider :

  - [Monitoring Microsoft Azure Resources and Workloads](https://app.pluralsight.com/library/courses/microsoft-azure-resources-workloads-monitoring-update/table-of-contents) (Supervision des ressources et charges de travail Microsoft Azure) explique comment utiliser les outils de supervision Microsoft Azure pour superviser les ressources réseau Azure ainsi que les ressources locales.

  - [Microsoft Azure DevOps Engineer: Optimize Feedback Mechanisms](https://www.pluralsight.com/courses/microsoft-azure-optimize-feedback-mechanisms) (Ingénieur Microsoft Azure DevOps : Optimiser les mécanismes de commentaires) vous aide à vous préparer à utiliser Azure Monitor, notamment Application Insights et Log Analytics, pour superviser et optimiser vos applications web.

  - [Microsoft Azure Database Monitoring Playbook](https://www.pluralsight.com/courses/microsoft-azure-database-playbook-monitoring) (Playbook sur la supervision Microsoft Azure Database) explique comment implémenter et utiliser la supervision d’Azure SQL Database, Azure SQL Data Warehouse et Azure Cosmos DB.

  - [Instrumenter des applications avec Azure Monitor Application Insights](https://app.pluralsight.com/library/courses/microsoft-azure-application-insights-web-application-instrument) est un cours approfondi sur l’utilisation du kit SDK Application Insights pour collecter la télémétrie et les événements d’une application avec les composants Angular et Node.js.

- Avec [Azure Arc pour serveurs](https://docs.microsoft.com/azure/azure-arc/servers/overview), découvrez comment gérer vos machines Windows et Linux hébergées en dehors d’Azure de la même façon que vous gérez des machines virtuelles Azure natives.

## <a name="deeper-skills-exploration"></a>Exploration approfondie des qualifications

Au-delà de ces options initiales d’acquisition des qualifications, de nombreuses options d’apprentissage sont disponibles.

### <a name="typical-mappings-of-cloud-it-roles"></a>Mappages typiques des rôles informatiques dans le cloud

Microsoft et ses partenaires offrent un large éventail d’options pour que tous les publics puissent développer leurs qualifications relatives aux services Azure :

- [Microsoft IT Pro Career Center](https://www.microsoft.com/itpro) : Fait office de ressource en ligne gratuite pour vous aider à mettre en correspondance votre parcours de carrière dans le cloud. Découvrez ce que les experts du secteur suggèrent pour votre rôle cloud et les qualifications nécessaires pour y parvenir. Suivez un programme de formation à votre rythme pour acquérir les qualifications dont vous avez le plus besoin pour rester compétent.

Obtenez la reconnaissance officielle de vos connaissances sur Azure au moyen des [examens et formations de certification Microsoft Azure]( https://www.microsoft.com/learning/certification-overview.aspx).

## <a name="azure-devops-and-project-management"></a>Gestion de projets et DevOps Azure

L’environnement cloud hybride perturbe les services informatiques avec des rôles, responsabilités et activités non définis. Les organisations doivent passer à des pratiques de management des services modernes, notamment des méthodologies Agile et DevOps, afin de mieux répondre aux besoins de transformation et d’optimisation des entreprises actuelles d’une manière rationalisée et efficace.

Dans le cadre de la migration vers une plateforme de supervision du cloud, l’équipe informatique chargée de la gestion de la supervision dans l’entreprise doit inclure une formation Agile et une participation aux activités DevOps. Cela nécessite également la prise en compte de la partie _Dev_ dans DevOps en prenant les exigences et en les transformant en exigences agiles organisées, afin de fournir des solutions de supervision minimalement viables qui sont affinées de manière itérative et conformément aux besoins de l’entreprise. Pour que le contrôle de code source gère les packages de solution de supervision itérative et les autres éléments associés, connectez votre projet Azure DevOps Server à un dépôt GitHub Enterprise Server. Cela fournit un lien entre les validations GitHub et les demandes de tirage (pull requests) aux éléments de travail. Vous pouvez utiliser GitHub Enterprise pour le développement afin de prendre en charge l’intégration et le déploiement continus de la supervision, tout en utilisant Azure Boards pour planifier et suivre votre travail.

Pour plus d’informations, consultez les articles suivants :

- [Bien démarrer avec Azure DevOps](https://docs.microsoft.com/learn/modules/get-started-with-devops)

- [Découvrez les bases de la ceinture blanche du dojo DevOps](https://docs.microsoft.com/learn/paths/devops-dojo-white-belt-foundation)

- [Faire évoluer vos activités DevOps](https://docs.microsoft.com/learn/paths/evolve-your-devops-practices)

- [Automatiser vos déploiements avec Azure DevOps](https://docs.microsoft.com/learn/paths/automate-deployments-azure-devops)

## <a name="other-considerations"></a>Autres considérations

Les clients éprouvent souvent des difficultés à gérer, tenir à jour et délivrer les résultats professionnels attendus pour les services que l’équipe informatique est chargée de délivrer. La supervision est considérée comme un élément clé de la gestion de l’infrastructure et de l’entreprise, avec un accent spécifique sur la mesure de la qualité du service et de l’expérience client. Pour atteindre ces objectifs, posez de solides fondations à l’aide d’ITSM et de DevOps. Cela aidera l’équipe de supervision à développer la manière dont elle gère, délivre et prend en charge le service de supervision. L’adoption d’un framework ITSM permet à l’équipe de supervision d’assumer le rôle de fournisseur et d’obtenir une reconnaissance en tant qu’activateur d’entreprise fiable en s’alignant sur les objectifs stratégiques et les besoins de l’organisation.

Pour comprendre les mises à jour apportées au framework ITSM le plus populaire, consultez le [livre blanc sur ITIL v4 et le cloud computing](https://www.axelos.com/case-studies-and-white-papers/itil-4-and-the-cloud), qui est axé sur la manière de combiner les recommandations ITIL existantes aux bonnes pratiques DevOps, Agile et Lean. Pensez également à l’[architecture de référence IT4IT](https://www.opengroup.org/it4it), qui fournit un blueprint de remplacement pour la transformation des services informatiques à l’aide d’un framework agnostique du point de vue des processus.

## <a name="learn-more"></a>En savoir plus

Pour découvrir des parcours d’apprentissage supplémentaires, parcourez le [catalogue Microsoft Learn](https://docs.microsoft.com/learn/browse). Utilisez le filtre Rôles pour faire correspondre les parcours d’apprentissage à votre rôle.
