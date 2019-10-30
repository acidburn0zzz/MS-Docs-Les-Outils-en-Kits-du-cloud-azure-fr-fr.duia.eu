---
title: Spécialisation de la plateforme pour la gestion cloud dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Améliorez les opérations de gestion cloud spécifiques à la plateforme.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 0386a8c30758cce6c1c3d23bfa73d1f90e919692
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556970"
---
# <a name="platform-specialization-for-cloud-management"></a>Spécialisation de la plateforme pour la gestion cloud

À l’instar de la ligne de base de gestion améliorée, la spécialisation de la plateforme est une extension qui dépasse la ligne de base de gestion standard. Voir ci-dessous une liste visuelle et à puces des façons permettant de développer la ligne de base de gestion. Cet article traite de l’option de spécialisation de la plateforme.

![Au-delà de la base de référence de gestion cloud](../../_images/manage/beyond-the-baseline.png)

- **Opérations de charge de travail :** Plus grand investissement d’opérations par charge de travail. Degré de résilience le plus élevé. Suggéré pour +/- 20% des charges de travail qui pilotent la valeur commerciale. Généralement réservé aux charges de travail importantes ou critiques.
- **Opérations de plateforme :** Les investissements opérationnels sont répartis sur de nombreuses charges de travail. Les améliorations de la résilience ont un impact sur toutes les charges de travail qui tirent parti de la plate-forme définie. Suggéré pour +/- 20% des plateformes les plus importantes. Généralement réservé aux charges de travail de niveau moyen ou critique.
- **Base de référence de gestion améliorée :** Investissement opérationnel le plus bas. Des engagements commerciaux légèrement améliorés à l’aide d’outils et de processus d’opérations natifs du cloud.

Les opérations de charge de travail et de plateforme peuvent nécessiter la modification des principes de conception et d’architecture. Ces modifications peuvent prendre du temps et entraîner des frais d’exploitation accrus. Pour réduire le nombre de charges de travail nécessitant de tels investissements, une base de référence de gestion améliorée peut représenter une amélioration suffisante pour l’engagement commercial.

Le tableau suivant présente quelques processus, outils et impacts potentiels courants communs aux lignes de base de gestion améliorée des clients.

|Process  |Outil  |Objectif  |Niveau de gestion suggéré  |
|---------|---------|---------|---------|
|Améliorer la conception du système|Infrastructure Azure Architecture|Améliorez la conception architecturale de la plateforme pour améliorer les opérations|
|Automatiser la correction|Azure Automation|Répondre aux données de plateforme avancées avec une automatisation spécifique à une plateforme|Opérations de plateforme|
|Catalogue de services|Centre d'applications managées|Fournir un catalogue en libre-service de solutions approuvées répondant aux normes organisationnelles|Opérations de plateforme|
|Performances du conteneur|Azure Monitor pour conteneurs|Surveillance et diagnostic des conteneurs|Opérations de plateforme|
|Performances des données PaaS|Azure SQL Analytics|Surveillance et diagnostic pour les bases de données PaaS|Opérations de plateforme|
|Performances des données IaaS|Vérification d’intégrité SQL Server|Surveillance et diagnostic pour les bases de données IaaS|Opérations de plateforme|

## <a name="high-level-process"></a>Processus de haut niveau

La spécialisation de la plateforme consiste en une exécution disciplinée des quatre processus suivants dans une approche itérative. Chaque processus est expliqué d’une façon plus détaillée dans les sections suivantes de cet article.

- **Améliorer la conception du système :** Améliorez la conception des systèmes communs (ou plateformes) pour réduire efficacement les interruptions.
- **Automatiser la correction :** Certaines améliorations ne sont pas rentables. Dans ce cas, il peut être plus judicieux d’automatiser la correction et de réduire l’impact des interruptions.
- **Mettre à l’échelle la solution :** Lorsque la conception des systèmes et la correction automatisée sont améliorées, ces modifications peuvent être mises à l’échelle dans l’environnement via le catalogue de services.
- **Amélioration continue :** Vous pouvez utiliser divers outils de supervision pour découvrir les améliorations incrémentielles qui peuvent être apportées dans la prochaine étape de la conception du système, de l’automatisation et de la mise à l’échelle.

::: zone target="docs"

## <a name="improve-system-design"></a>Améliorer la conception du système

::: zone-end
::: zone target="chromeless"

## <a name="improve-system-designtabsystemsdesign"></a>[Améliorer la conception du système](#tab/SystemsDesign)

::: zone-end

L’amélioration de la conception du système constitue l’approche la plus efficace pour améliorer les opérations de toutes les plateformes communes. Grâce aux améliorations de la conception du système, la stabilité peut s’améliorer et les interruptions d’activité peuvent diminuer. La conception de systèmes individuels n’entre pas dans le cadre du Cloud Adoption Framework. En complément de celui-ci, Azure Architecture Framework fournit les bonnes pratiques permettant d’améliorer la résilience et la conception d’un système spécifique. Ces améliorations peuvent être appliquées à la conception système d’une plateforme ou d’une charge de travail.

Azure Architecture Framework se concentre sur l’amélioration par le biais des cinq principes de la conception système :

- **Scalabilité :** Mise à l’échelle des ressources de plateforme communes pour gérer une charge accrue.
- **Disponibilité :** Diminution des interruptions d’activité par l’amélioration du potentiel de disponibilité.
- **Résilience :** Amélioration du temps de récupération pour réduire la durée des interruptions.
- **Sécurité :** Protection des applications et des données contre les menaces externes.
- **Gestion :** Processus opérationnels propres aux ressources de plateforme communes.

La plupart des interruptions d’activité correspondent à une certaine forme de dette technique ou de défaillance dans l’architecture. Pour les déploiements existants, les améliorations de la conception système peuvent être vues comme le paiement d’une dette technique existante. Pour les nouveaux déploiements, les améliorations de la conception système peuvent être vues comme l’évitement d’une dette technique. La section suivante, « Correction automatisée », vous permet de résoudre les éventuelles dettes techniques qui ne peuvent pas ou ne doivent pas être résolues.

En savoir plus sur [Azure Architecture Framework](https://docs.microsoft.com/azure/architecture/guide/pillars) pour améliorer la conception du système.

Une fois que la conception du système se sera améliorée, revenez à cet article pour trouver de nouvelles opportunités d’améliorer et de faire évoluer ces améliorations dans votre environnement.

::: zone target="docs"

## <a name="automated-remediation"></a>Correction automatisée

::: zone-end
::: zone target="chromeless"

## <a name="automated-remediationtabautomatedremediation"></a>[Correction automatisée](#tab/AutomatedRemediation)

::: zone-end

Certaines dettes techniques ne peuvent pas être résolues. En effet, leur résolution peut être trop coûteuse. La résolution peut être planifiée, mais sa durée de projet peut être longue. Il est possible que l’interruption d’activité n’ait pas un impact significatif sur l’entreprise ou que la priorité de l’entreprise soit de récupérer rapidement au lieu d’investir dans la résilience.

Lorsque la résolution de la dette technique n’est pas souhaitée, la correction automatisée est généralement le choix à faire. L’utilisation d’Azure Automation et d’Azure Monitor pour détecter les tendances et fournir une correction automatisée est l’approche la plus couramment utilisée pour la correction automatisée.

Pour obtenir des conseils sur la correction automatisée, consultez cet article concernant [Azure Automation et les alertes](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

::: zone target="docs"

## <a name="scale-the-solution-with-a-service-catalog"></a>Mettre à l’échelle la solution avec un catalogue de services

::: zone-end
::: zone target="chromeless"

## <a name="scale-the-solution-with-a-service-catalogtabservicecatalog"></a>[Mettre à l’échelle la solution avec un catalogue de services](#tab/ServiceCatalog)

::: zone-end

L’élément indispensable à la spécialisation de plateforme et aux opérations de plateforme est un catalogue de services bien géré. C’est ainsi que les améliorations apportées à la conception et à la correction des systèmes sont mises à l’échelle dans un environnement. L’équipe de plateforme cloud et l’équipe d’automatisation cloud s’associent pour créer des solutions reproductibles convenant aux plateformes les plus courantes dans n’importe quel environnement. Toutefois, si ces solutions ne sont pas exploitées de manière cohérente, la gestion cloud peut offrir un peu plus qu’une offre de base de référence.

Pour accroître l’adoption et réduire la charge de maintenance de toutes les plateformes optimisées, la plateforme doit être ajoutée à un catalogue de services au sein d’Azure. Chaque application du catalogue peut être déployée pour un usage interne via le catalogue de services ou en tant qu’offre de la Place de marché pour les utilisateurs externes.

Pour obtenir des instructions sur la publication dans un catalogue de services, consultez la série d’articles concernant la [publication dans un catalogue de services](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app).

### <a name="deploy-applications-from-the-service-catalog"></a>Déployer des applications à partir du catalogue de services

1. Dans la Portail Azure, recherchez **Centre d’applications managées (préversion)** .
2. Cliquez sur **Applications du catalogue de services** sous la section **Parcourir** de la navigation dans le portail.
3. Cliquez sur **+ Ajouter** pour choisir une définition d’application à partir du catalogue de services de votre société.

Toutes les applications gérées que vous traitez sont affichées ici.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/browseServiceCatalog]" submitText="Go to Virtual Machines" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="manage-service-catalog-applications"></a>Gérer des applications du catalogue de services

1. Dans la Portail Azure, recherchez **Centre d’applications managées (préversion)** .
2. Cliquez sur **Applications du catalogue de services** sous la section **Service** de la navigation dans le portail.

Toutes les applications gérées que vous traitez sont affichées ici.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/serviceServiceCatalogApps]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="continuous-improvement"></a>Amélioration continue

::: zone-end
::: zone target="chromeless"

## <a name="continuous-improvementtabcontinuousimprovement"></a>[Amélioration continue](#tab/ContinuousImprovement)

::: zone-end

La spécialisation de plateforme et les opérations de plateforme dépendent de boucles de commentaires efficaces entre les équipes chargées de l’adoption, de la plateforme, de l’automatisation et de la gestion. Le fait de baser ces boucles de commentaires sur des données permet à chaque équipe de prendre des décisions éclairées. Pour que les opérations de plateforme puissent respecter leurs engagements commerciaux à long terme, il est important de tirer parti des insights propres à la plateforme centralisée. Étant donné que les conteneurs et SQL Server sont les plateformes gérées de manière centralisée qui sont les plus couramment utilisées, voici quelques articles qui vous aideront à vous familiariser avec la collecte de données en vue d’une amélioration continue.

[Performances des conteneurs](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
[Performances des bases de données PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
[Performances des bases de données IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
