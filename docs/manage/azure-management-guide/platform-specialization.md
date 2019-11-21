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
ms.openlocfilehash: 8c3954627ee991f43c2b8d3a94dbd77746d3d4b2
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752942"
---
# <a name="platform-specialization-for-cloud-management"></a>Spécialisation de la plateforme pour la gestion cloud

À l’instar de la ligne de base de gestion améliorée, la spécialisation de la plateforme est une extension qui dépasse la ligne de base de gestion standard. L’image et la liste suivantes présentent les différentes façons d’étendre la base de référence de gestion. Cet article traite des options de spécialisation de la plateforme.

![Au-delà de la base de référence de gestion cloud](../../_images/manage/beyond-the-baseline.png)

- **Opérations de charge de travail :** L'investissement par charge de travail le plus important et le plus haut degré de résilience. Nous recommandons de mettre en place des opérations de charge de travail pour environ 20 % des charges de travail qui pilotent la valeur commerciale. Cette spécialisation est généralement réservée aux charges de travail très importantes ou critiques.
- **Opérations de plateforme :** Les investissements opérationnels sont répartis sur de nombreuses charges de travail. Les améliorations de la résilience affectent toutes les charges de travail qui utilisent la plateforme définie. Nous recommandons de mettre en place des opérations de plateformes pour environ 20 % des plateformes les plus importantes. Cette spécialisation est généralement réservée aux charges de travail de niveau moyen ou critique.
- **Base de référence de gestion améliorée :** L’investissement opérationnel le plus bas. Cette spécialisation améliore légèrement les engagements commerciaux à l’aide d’outils et de processus d’opérations natifs du cloud.

Les opérations de charge de travail et de plateforme nécessitent la modification des principes de conception et d’architecture. Ces modifications peuvent prendre du temps et entraîner des frais d’exploitation accrus. Pour réduire le nombre de charges de travail nécessitant de tels investissements, une base de référence de gestion améliorée peut représenter une amélioration suffisante pour l’engagement métier.

Ce tableau présente quelques processus, outils et effets potentiels courants communs aux lignes de base de gestion améliorée des clients :

|Process  |Outil  |Objectif  |Niveau de gestion suggéré  |
|---------|---------|---------|---------|
|Améliorer la conception du système|Infrastructure Azure Architecture|Améliorer la conception architecturale de la plateforme pour optimiser les opérations|N/A|
|Automatiser la correction|Azure Automation|Répondre aux données de plateforme avancées avec une automatisation spécifique à une plateforme|Opérations de plateforme|
|Catalogue de services|Centre d'applications managées|Fournir un catalogue en libre-service de solutions approuvées répondant aux normes organisationnelles|Opérations de plateforme|
|Performances du conteneur|Azure Monitor pour des conteneurs|Surveillance et diagnostic des conteneurs|Opérations de plateforme|
|Performances des données Platform as a Service (PaaS)|Azure SQL Analytics|Surveillance et diagnostic pour les bases de données PaaS|Opérations de plateforme|
|Performances des données Infrastructure as a service (IaaS)|Vérification d’intégrité SQL Server|Surveillance et diagnostic pour les bases de données IaaS|Opérations de plateforme|

## <a name="high-level-process"></a>Processus de haut niveau

La spécialisation de la plateforme consiste en une exécution disciplinée des quatre processus suivants dans une approche itérative. Chaque processus est expliqué d’une façon plus détaillée dans les sections suivantes de cet article.

- **Améliorer la conception du système :** Améliorez la conception des plateformes ou systèmes communs pour réduire efficacement les interruptions.
- **Automatiser la correction :** Certaines améliorations ne sont pas rentables. Dans ce cas, il peut être plus judicieux d’automatiser la correction et de réduire l’impact des interruptions.
- **Mettre à l’échelle la solution :** Lorsque la conception des systèmes et la correction automatisée sont améliorées, ces modifications peuvent être mises à l’échelle dans l’environnement via le catalogue de services.
- **Amélioration continue :** Vous pouvez utiliser différents outils de surveillance pour identifier les améliorations incrémentielles. Ces améliorations peuvent être abordées lors de la prochaine étape de la conception, de l'automatisation et de la mise à l'échelle du système.

::: zone target="docs"

## <a name="improve-system-design"></a>Améliorer la conception du système

::: zone-end
::: zone target="chromeless"

## <a name="improve-system-designtabsystemsdesign"></a>[Améliorer la conception du système](#tab/SystemsDesign)

::: zone-end

L’amélioration de la conception du système constitue l’approche la plus efficace pour améliorer les opérations de toutes les plateformes communes. Grâce aux améliorations de la conception du système, la stabilité peut s’améliorer et les interruptions d’activité peuvent diminuer. La conception de systèmes individuels n’entre pas dans le cadre du Framework d’adoption cloud pour Azure.

En complément du Framework d’adoption cloud, Azure Architecture Framework fournit les bonnes pratiques permettant d’améliorer la résilience et la conception d’un système spécifique. Ces améliorations peuvent être appliquées à la conception système d’une plateforme ou d’une charge de travail.

Azure Architecture Framework se concentre sur l’amélioration par le biais des cinq principes de la conception système :

- **Scalabilité :** Mise à l’échelle des ressources de plateforme communes pour gérer une charge accrue
- **Disponibilité :** Réduction des interruptions d’activité par l’amélioration du potentiel de disponibilité
- **Résilience :** Amélioration du temps de récupération pour réduire la durée des interruptions
- **Sécurité :** Protection des applications et des données contre les menaces externes
- **Gestion :** Processus opérationnels propres aux ressources de plateforme communes

Les dettes techniques et les défauts architecturaux sont à l'origine de la plupart des interruptions d'activité. Pour les déploiements existants, les améliorations de la conception système peuvent être vues comme le paiement d’une dette technique existante. Pour les nouveaux déploiements, ces améliorations peuvent être vues comme l’évitement d’une dette technique.

L’onglet suivant, **Correction automatisée**, présente différentes solutions pour résoudre les éventuelles dettes techniques qui ne peuvent pas ou ne doivent pas être résolues.

En savoir plus sur [Azure Architecture Framework](https://docs.microsoft.com/azure/architecture/guide/pillars) pour améliorer la conception du système.

Une fois que la conception du système se sera améliorée, revenez à cet article pour trouver de nouvelles opportunités d’améliorer et de faire évoluer ces améliorations dans votre environnement.

::: zone target="docs"

## <a name="automated-remediation"></a>Correction automatisée

::: zone-end
::: zone target="chromeless"

## <a name="automated-remediationtabautomatedremediation"></a>[Correction automatisée](#tab/AutomatedRemediation)

::: zone-end

Certaines dettes techniques ne peuvent pas être résolues. Leur résolution peut être trop coûteuse, ou elle peut être planifiée, mais sa durée de projet peut être longue. Il est possible que l’interruption d’activité n’ait pas un impact significatif sur l’entreprise, ou que la priorité de l’entreprise soit de récupérer rapidement au lieu d’investir dans la résilience.

Lorsque la résolution de la dette technique n’est pas souhaitée, la correction automatisée est généralement la prochaine étape à suivre. L’utilisation d’Azure Automation et d’Azure Monitor pour détecter les tendances et fournir une correction automatisée est l’approche la plus couramment utilisée pour la correction automatisée.

Pour obtenir des conseils sur la correction automatisée, consultez [Azure Automation et les alertes](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

::: zone target="docs"

## <a name="scale-the-solution-with-a-service-catalog"></a>Mettre à l’échelle la solution avec un catalogue de services

::: zone-end
::: zone target="chromeless"

## <a name="scale-the-solution-with-a-service-catalogtabservicecatalog"></a>[Mettre à l’échelle la solution avec un catalogue de services](#tab/ServiceCatalog)

::: zone-end

Un catalogue de services bien géré constitue l’élément indispensable à la spécialisation de plateforme et aux opérations de plateforme. C’est en utilisant un catalogue que les améliorations apportées à la conception et à la correction des systèmes sont mises à l’échelle dans un environnement.

L’équipe de plateforme cloud et l’équipe d’automatisation cloud s’associent pour créer des solutions reproductibles convenant aux plateformes les plus courantes dans n’importe quel environnement. Toutefois, si ces solutions ne sont pas appliquées de manière cohérente, la gestion cloud peut offrir un peu plus qu’une offre de base de référence.

Pour accroître l’adoption et réduire la charge de maintenance de toutes les plateformes optimisées, vous devez ajouter la plateforme à un catalogue de services Azure. Vous pouvez déployer chaque application du catalogue pour un usage interne via le catalogue de services ou en tant qu’offre de la Place de marché pour les utilisateurs externes.

Pour obtenir des instructions sur la publication dans un catalogue de services, consultez la série d’articles concernant la [publication dans un catalogue de services](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app).

### <a name="deploy-applications-from-the-service-catalog"></a>Déployer des applications à partir du catalogue de services

1. Dans le Portail Azure, sélectionnez **Centre d’applications managées (préversion)** .
2. Dans le volet **Parcourir**, sélectionnez **Applications du catalogue de services**.
3. Cliquez sur **+ Ajouter** pour choisir une définition d’application à partir du catalogue de services de votre société.

Toutes les applications gérées que vous traitez sont affichées.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/browseServiceCatalog]" submitText="Go to Virtual Machines" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="manage-service-catalog-applications"></a>Gérer des applications du catalogue de services

1. Dans le Portail Azure, sélectionnez **Centre d’applications managées (préversion)** .
1. Dans le volet **Service**, sélectionnez **Applications du catalogue de services**.

Toutes les applications gérées que vous traitez sont affichées.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/serviceServiceCatalogApps]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="continuous-improvement"></a>Amélioration continue

::: zone-end
::: zone target="chromeless"

## <a name="continuous-improvementtabcontinuousimprovement"></a>[Amélioration continue](#tab/ContinuousImprovement)

::: zone-end

La spécialisation de plateforme et les opérations de plateforme dépendent de boucles de commentaires efficaces entre les équipes chargées de l’adoption, de la plateforme, de l’automatisation et de la gestion. Le fait de baser ces boucles de commentaires sur des données aide chaque équipe à prendre des décisions éclairées. Pour que les opérations de plateforme puissent respecter leurs engagements métier à long terme, il est important d’utiliser des insights propres à la plateforme centralisée.

Les conteneurs et SQL Server sont les plateformes gérées de manière centralisée qui sont les plus couramment utilisées. Les articles suivants peuvent vous aider à commencer la collecte de données d'amélioration continue sur ces plateformes :

- [Performances du conteneur](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
- [Performances de la base de données PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
- [Performances de la base de données IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
