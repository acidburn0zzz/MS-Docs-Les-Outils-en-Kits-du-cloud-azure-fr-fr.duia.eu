---
title: Inventaire et visibilité dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment configurer l’inventaire, la supervision, la création de rapports et les alertes pour votre environnement de gestion Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 4969681cbc6fbb71da70f3ced09b5e4616c773b5
ms.sourcegitcommit: 7df593a67a2e77b5f61c815814af9f0c36ea5ebd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75781774"
---
# <a name="inventory-and-visibility-in-azure"></a>Inventaire et visibilité dans Azure

_Inventaire et visibilité_ est la première des trois disciplines dans une ligne de base de gestion cloud.

![Base de référence de gestion cloud](../../_images/manage/management-baseline.png)

Cette discipline vient en premier, car il est essentiel de collecter les données opérationnelles appropriées lorsque vous prenez des décisions sur les opérations. Les équipes de gestion cloud doivent comprendre ce qui est géré et la façon dont ces ressources sont exploitées. Cet article décrit les différents outils qui fournissent à la fois un inventaire et une visibilité à l’état d’exécution de l’inventaire.

Dans le cas d’un environnement d’entreprise, le tableau suivant présente le minimum suggéré pour une base de référence de gestion.

|Process  |Outil  |Objectif  |
|---------|---------|---------|
|Surveiller l’intégrité des services Azure|Azure Service Health|Intégrité, performances et diagnostics pour les services s’exécutant dans Azure|
|Centralisation des journaux|Log Analytics|Journalisation centralisée pour tous les objectifs de visibilité|
|Surveillance de la centralisation|Azure Monitor|Surveillance centralisée des données opérationnelles et des tendances|
|Inventaire de machine virtuelle et suivi des modifications|Suivi des modifications et inventaire Azure|Inventorier les machines virtuelles et surveiller les modifications au niveau du système d’exploitation invité|
|Supervision des abonnements|Journaux d’activité|Surveillance des modifications au niveau de l’abonnement|
|Surveillance du système d’exploitation invité|Azure Monitor pour machines virtuelles|Surveillance des modifications et des performances des machines virtuelles|
|Analyse du réseau|Azure Network Watcher|Surveillance des modifications et des performances du réseau|
|Supervision DNS|DNS Analytics|Sécurité, performances et opérations de DNS|

::: zone target="docs"

## <a name="azure-service-health"></a>Azure Service Health

::: zone-end
::: zone target="chromeless"

## <a name="azure-service-healthtabazureservicehealth"></a>[Azure Service Health](#tab/AzureServiceHealth)

::: zone-end

Azure Service Health fournit un affichage personnalisé de l’intégrité de vos services et régions Azure. Service Health publie des informations sur les problèmes actuels qui sont utiles pour comprendre l’impact sur vos ressources. Des mises à jour régulières vous tiennent informé de la résolution des problèmes.

Service Health publie également les événements de maintenance planifiée pour vous avertir des prochains changements susceptibles d’affecter la disponibilité de vos ressources. Configurez des alertes Azure Service Health pour être informé des problèmes liés aux services, de la maintenance planifiée et d’autres changements pouvant avoir un impact sur vos services et régions Azure.

Azure Service Health inclut :

- **Azure Status :** Affichage global de l’intégrité des services Azure.
- **Service Health :** Affichage personnalisé de l’intégrité de vos services Azure.
- **Resource Health :** Affichage plus approfondi de l’intégrité de vos ressources individuelles.

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Action

Pour configurer une alerte Service Health :

1. Accédez à **Service Health**.
2. Sélectionnez **Alertes d’intégrité**.
3. Créez une alerte d’intégrité du service.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts]" submitText="Go to Service Health" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Pour configurer une alerte Service Health, accédez au [Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts).

### <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez la [documentation d’Azure Service Health](https://docs.microsoft.com/azure/service-health).

## <a name="log-analytics"></a>Log Analytics

::: zone-end
::: zone target="chromeless"

## <a name="log-analyticstablog-analytics"></a>[Log Analytics](#tab/Log-Analytics)

::: zone-end

Un [espace de travail Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) est un environnement unique pour le stockage des données de journal d’activité Azure Monitor. Chaque espace de travail a son propre dépôt de données et sa propre configuration. Les solutions et sources de données sont configurées pour stocker leurs données dans des espaces de travail particuliers. Les solutions de supervision Azure requièrent que tous les serveurs soient connectés à un espace de travail, afin que leurs données de journal puissent être stockées et consultées.

::: zone target="chromeless"

### <a name="action"></a>Action

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.OperationalInsights%2Fworkspaces]" submitText="Explore Azure Monitor" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez la [documentation relative à la création d’un espace de travail Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace).

## <a name="azure-monitor"></a>Azure Monitor

::: zone-end
::: zone target="chromeless"

## <a name="azure-monitortabazure-monitor"></a>[Azure Monitor](#tab/Azure-Monitor)

::: zone-end

Avec Azure Monitor, vous bénéficiez d’un seul hub unifié pour toutes les données de supervision et de diagnostic dans Azure, ainsi que d’une visibilité sur l’ensemble de vos ressources. Grâce à Azure Monitor, vous pouvez rechercher et résoudre les problèmes et optimiser le niveau de performance. Vous pouvez également comprendre le comportement des clients.

- **Superviser et visualiser les métriques.** Les métriques sont des valeurs numériques disponibles à partir des ressources Azure. Elles vous aident à comprendre l’intégrité de vos systèmes. Personnalisez les graphiques de vos tableaux de bord et utilisez des classeurs pour la création de rapports.

- **Interroger et analyser les journaux.** Les journaux incluent les journaux d’activité et les journaux de diagnostic à partir d’Azure. Collectez des journaux supplémentaires provenant d’autres solutions de supervision et de gestion pour vos ressources cloud ou locales. Log Analytics fournit un référentiel central pour agréger toutes ces données. À partir de là, vous pouvez exécuter des requêtes pour aider à résoudre des problèmes ou pour visualiser des données.

- **Configurer des alertes et des actions.** Les alertes vous avertissent de conditions critiques. Des actions correctives peuvent être prises en fonction de déclencheurs activés par des métriques, des journaux ou des problèmes d’intégrité de service. Vous pouvez configurer différentes actions et notifications et envoyer les données à vos outils de gestion des services informatiques.

::: zone target="chromeless"

### <a name="action"></a>Action

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Explore Azure Monitor" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

 Commencez à superviser vos :

- [Applications](https://docs.microsoft.com/azure/application-insights/app-insights-overview)
- [Containers](https://docs.microsoft.com/azure/monitoring/monitoring-container-overview)
- [Machines virtuelles](https://docs.microsoft.com/azure/monitoring/monitoring-service-map)
- [Réseaux](https://docs.microsoft.com/azure/networking/network-monitoring-overview)

Pour superviser d’autres ressources, recherchez des solutions supplémentaires dans la Place de marché Azure.

Pour explorer Azure Monitor, accédez au [Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview).

### <a name="learn-more"></a>En savoir plus

Pour en savoir plus, consultez la [documentation d’Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics).

## <a name="onboard-solutions"></a>Solutions intégrées

::: zone-end
::: zone target="chromeless"

## <a name="onboard-solutionstabconfigure-solutions"></a>[Solutions intégrées](#tab/Configure-solutions)

::: zone-end

Pour activer les solutions, vous devez configurer l’espace de travail Log Analytics. Les machines virtuelles Azure et les serveurs locaux intégrés obtiennent les solutions à partir des espaces de travail Log Analytics auxquels ils sont connectés.

Il existe deux approches pour l’intégration :

- [Machine virtuelle unique](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
- [Abonnement entier](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)

Chaque article vous guide tout au long d’une série d’étapes pour intégrer ces solutions :

- Update Management
- Suivi des modifications et inventaire
- Journaux d’activité
- Azure Log Analytics Agent Health
- Antimalware Assessment
- Azure Monitor pour machines virtuelles
- Azure Security Center

Chacune des étapes précédentes vous aidera à établir l’inventaire et la visibilité.
