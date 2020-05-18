---
title: Supervision et création de rapports dans Azure
description: Utilisez le Cloud Adoption Framework pour Azure afin de découvrir comment configurer la supervision, la création de rapports et les alertes dans votre environnement de gestion Azure.
author: timleyden
ms.author: tileyden
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC, setup
ms.localizationpriority: high
ms.openlocfilehash: 0be49567a459915dbe4b8e8db90feae9b47a1e5c
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83223182"
---
<!-- cSpell:ignore timleyden tileyden -->

# <a name="monitoring-and-reporting-in-azure"></a>Supervision et création de rapports dans Azure

Azure offre de nombreux services qui, ensemble, fournissent une solution complète pour la collecte, l’analyse et l’action sur les données de télémétrie de vos applications et des ressources Azure qui les prennent en charge. De plus, ces services peuvent être étendus à la supervision des ressources locales critiques et fournir ainsi un environnement de supervision hybride.

# <a name="azure-monitor"></a>[Azure Monitor](#tab/AzureMonitor)

Azure Monitor fournit un seul hub unifié pour toutes les données de supervision et de diagnostic dans Azure. Vous pouvez l’utiliser pour obtenir une visibilité sur l’ensemble de vos ressources. Grâce à Azure Monitor, vous pouvez rechercher et résoudre les problèmes et optimiser le niveau de performance. Vous pouvez également comprendre le comportement des clients.

- **Superviser et visualiser les métriques.** Les métriques sont des valeurs numériques disponibles à partir des ressources Azure. Elles vous aident à comprendre l’intégrité de vos systèmes. Personnalisez les graphiques de vos tableaux de bord et utilisez des classeurs pour la création de rapports.

- **Interroger et analyser les journaux.** Les journaux incluent les journaux d’activité et les journaux de diagnostic à partir d’Azure. Collectez des journaux supplémentaires provenant d’autres solutions de supervision et de gestion pour vos ressources cloud ou locales. Log Analytics fournit un référentiel central pour agréger toutes ces données. À partir de là, vous pouvez exécuter des requêtes pour aider à résoudre des problèmes ou pour visualiser des données.

- **Configurer des alertes et des actions.** Les alertes vous avertissent de conditions critiques de façon proactive. Des actions correctives peuvent être prises en fonction de déclencheurs activés par des métriques, des journaux ou des problèmes d’intégrité de service. Vous pouvez configurer différentes actions et notifications et envoyer les données à vos outils de gestion des services informatiques.

::: zone target="docs"

 Commencez à superviser vos :

- [Applications](https://docs.microsoft.com/azure/application-insights/app-insights-overview)
- [Containers](https://docs.microsoft.com/azure/monitoring/monitoring-container-overview)
- [Machines virtuelles](https://docs.microsoft.com/azure/monitoring/monitoring-service-map)
- [Réseaux](https://docs.microsoft.com/azure/networking/network-monitoring-overview)

Pour superviser d’autres ressources, recherchez des solutions supplémentaires dans la Place de marché Azure.

Pour explorer Azure Monitor, accédez au [Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview).

## <a name="learn-more"></a>En savoir plus

Pour en savoir plus, consultez la [documentation d’Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics).

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

## <a name="action"></a>Action

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Explore Azure Monitor" :::

::: zone-end

# <a name="azure-service-health"></a>[Azure Service Health](#tab/AzureServiceHealth)

Azure Service Health fournit un affichage personnalisé de l’intégrité des services et régions Azure que vous utilisez. Service Health publie des informations sur les problèmes actuels qui sont utiles pour comprendre l’impact sur vos ressources. Des mises à jour régulières vous tiennent informé de la résolution des problèmes.

Service Health publie également les événements de maintenance planifiée pour vous avertir des prochains changements qui sont susceptibles d’impacter la disponibilité de vos ressources. Configurez des alertes Azure Service Health pour être informé des problèmes liés aux services, de la maintenance planifiée et d’autres changements pouvant avoir un impact sur les services et régions Azure que vous utilisez.

Azure Service Health inclut :

- **Azure Status :** Affichage global de l’intégrité des services Azure.
- **Service Health :** Affichage personnalisé de l’intégrité de vos services Azure.
- **Resource Health :** Affichage plus approfondi de l’intégrité de chacune de vos ressources individuelles.

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

## <a name="action"></a>Action

Pour configurer une alerte Service Health :

1. Accédez à **Service Health**.
2. Sélectionnez **Alertes d’intégrité**.
3. Créez une alerte d’intégrité du service.

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts]" submitText="Go to Service Health" :::

::: zone-end

::: zone target="docs"

Pour configurer une alerte Service Health, accédez au [Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts).

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez la [documentation d’Azure Service Health](https://docs.microsoft.com/azure/service-health).

::: zone-end

# <a name="azure-advisor"></a>[Azure Advisor](#tab/AzureAdvisor)

Azure Advisor est un conseiller personnalisé gratuit basé dans le cloud qui vous aide à suivre et à implémenter de bonnes pratiques pour les déploiements Azure. Il analyse la configuration de vos ressources et les données de télémétrie d’utilisation et suggère des solutions qui peuvent vous aider à optimiser votre environnement. Les recommandations sont réparties selon les catégories suivantes :

- **Haute disponibilité :** vous aide à améliorer la continuité de vos applications stratégiques. Les recommandations peuvent inclure l’ajout de machines virtuelles à un groupe à haute disponibilité ou l’ajout de points de terminaison géoredondants.
- **Sécurité :** permet de détecter les menaces et vulnérabilités pouvant conduire à des failles de sécurité. Les recommandations peuvent inclure l’application du chiffrement des disques ou l’activation de groupes de sécurité réseau.
- **Performances :** pour améliorer la vitesse de vos applications. Les recommandations peuvent inclure l’amélioration des niveaux de performance des requêtes SQL en créant des index ou en reconfigurant vos paramètres de gestion du trafic.
- **Coût :** pour optimiser et réduire vos dépenses Azure globales. Les recommandations peuvent concerner le redimensionnement ou l’arrêt des machines virtuelles sous-exploitées ou encore le transfert vers des réservations Azure pour diminuer le coût total de possession.
- **Excellence opérationnelle :** Pour améliorer la facilité de gestion et l’efficacité des processus et des workflows. Les recommandations peuvent inclure la configuration et l’application des règles Azure Policy, la réparation des règles d’alerte de journal non valides et la configuration des alertes Azure Service Health.

Les recommandations dans Advisor sont basées sur les ressources que vous déployez et les actions que vous effectuez dans Azure. Vous pouvez consulter Advisor régulièrement pour prendre connaissance des dernières recommandations.

::: zone target="chromeless"

## <a name="action"></a>Action

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorBlade]" submitText="Explore Azure Advisor" :::

::: zone-end

::: zone target="docs"

Pour explorer Azure Advisor, accédez au [Portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Expert/AdvisorBlade).

## <a name="learn-more"></a>En savoir plus

Pour en savoir plus, consultez la [documentation d’Azure Advisor](https://docs.microsoft.com/azure/advisor).

::: zone-end

# <a name="azure-security-center"></a>[Centre de sécurité Azure](#tab/AzureSecurityCenter)

Azure Security Center joue également un rôle important dans votre stratégie de supervision. Il peut vous aider à superviser la sécurité de vos machines, réseaux, systèmes de stockage, services de données et applications. Security Center fournit la détection avancée des menaces en utilisant l’apprentissage automatique et l’analytique comportementale pour aider à identifier les menaces actives ciblant vos ressources Azure. Il met également à disposition une protection contre les menaces qui bloque les programmes malveillants ou autres codes indésirables et réduit la surface d’exposition aux attaques par force brute et autres attaques réseau.

Quand Security Center identifie une menace, il déclenche une alerte de sécurité qui indique les étapes à effectuer en réponse à l’attaque. Il fournit également un rapport contenant des informations sur la menace qui a été détectée.

Azure Security Center est proposé en deux niveaux de service : Gratuit et Standard. Les fonctionnalités telles que les recommandations de sécurité sont disponibles gratuitement. Le niveau de service Standard fournit une protection supplémentaire comme la détection avancée des menaces et une protection de l’ensemble des charges de travail cloud hybrides.

::: zone target="chromeless"

## <a name="action"></a>Action

**Essayez gratuitement le niveau de service Standard pendant les 30 premiers jours.**

Après avoir activé et configuré des stratégies de sécurité pour les ressources d’un abonnement, vous pouvez voir l’état de la sécurité de vos ressources et les problèmes éventuels dans la section **Prévention**. Vous pouvez également afficher une liste de ces problèmes dans la mosaïque **Recommandations** .

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Pour explorer Azure Security Center, accédez au [portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez la [documentation d’Azure Security Center](https://docs.microsoft.com/azure/security-center).

::: zone-end
