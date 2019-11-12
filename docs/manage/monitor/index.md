---
title: Guide de supervision du cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Vue d’ensemble d’Azure Monitor et de System Center Operations Manager
author: MGoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 315ba0898f6a301af6f91614290c51244fbf6eb0
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564920"
---
# <a name="cloud-monitoring-guide-introduction"></a>Guide de supervision du cloud : Introduction

Le cloud représente un changement fondamental dans la façon dont les entreprises obtiennent et utilisent les ressources technologiques. Par le passé, elles étaient propriétaires et responsables de tous les niveaux technologiques, des infrastructures aux logiciels. À présent, le cloud permet aux grandes entreprises de provisionner et de consommer des ressources en fonction des besoins.

Bien que le cloud offre une flexibilité presque illimitée en termes de choix de conception, les entreprises recherchent une méthodologie éprouvée et cohérente dans l’adoption de technologies cloud. Chaque entreprise a ses propres objectifs et sa propre chronologie d’adoption du cloud. Il est donc quasiment impossible d’offrir une seule et unique approche, adaptée à toutes.

![Diagramme représentant les stratégies d’adoption du cloud](./media/monitoring-management-guidance-cloud-and-on-premises/introduction-cloud-adoption.png)

Cette transformation numérique permet également de moderniser votre infrastructure, vos charges de travail et vos applications. En fonction de la stratégie et des objectifs de l’entreprise, l’adoption d’un modèle de cloud hybride s’intègre généralement dans le parcours de migration des installations locales vers un fonctionnement total dans le cloud. Au cours de ce parcours, les équipes informatiques sont contraintes d’adopter et de valoriser rapidement le cloud. Elles doivent aussi comprendre comment superviser efficacement l’application ou le service qui migre vers Azure tout en assurant la continuité des opérations informatiques et DevOps.

Les parties prenantes souhaitent utiliser des outils cloud de gestion et de supervision SaaS. Par conséquent, elles cherchent à comprendre ce que les services et solutions peuvent apporter en matière de visibilité de bout en bout, de réduction des coûts et d’allègement des tâches liées à l’infrastructure et à la maintenance des outils traditionnellement utilisés pour les opérations informatiques logicielles.

Toutefois, les équipes informatiques préfèrent continuer à utiliser les outils dans lesquels elles ont investi de manière conséquente. Cette approche prend en charge leurs processus d’opérations de service pour superviser les deux modèles cloud, avec l’objectif éventuel de passer à une offre SaaS. Pour les équipes informatiques, ce choix n’est pas seulement motivé par la quantité de temps nécessaire à la planification des ressources et au financement de la migration. Il vient aussi de la difficulté à identifier les produits ou services Azure appropriés ou applicables pour effectuer la transition.

Ce guide est une référence détaillée pour aider les directeurs informatiques d’entreprise, les décideurs d’entreprise, les architectes d’application et les développeurs d’application à comprendre ce qui suit :

* Les plateformes de supervision Azure, avec une présentation et une comparaison de leurs fonctionnalités.
* La solution la plus adaptée pour superviser des charges de travail hybrides, privées et natives Azure.
* L’approche recommandée de supervision de bout en bout de l’infrastructure et des applications, notamment les solutions pouvant être déployées pour la migration des charges de travail courantes vers Azure.

Ce guide n’est pas un article de procédure pour utiliser ou configurer des services et solutions Azure individuels, mais il les référence comme sources quand ils sont applicables ou disponibles. Après la lecture de ce guide, vous saurez comment utiliser une charge de travail en suivant les bonnes pratiques et modèles suivants.

Si vous n’êtes pas familiarisé avec Azure Monitor et System Center Operations Manager et que vous voulez mieux comprendre ce qui les rend uniques et dans quelle mesure ils sont comparables, consultez [Vue d’ensemble de nos plateformes de supervision](./platform-overview.md).

## <a name="audience"></a>Audience

Ce guide est destiné en priorité aux administrateurs d’entreprise, aux services des opérations, de la sécurité et de la conformité informatiques, aux architectes d’application, aux propriétaires de développement de charge de travail et aux propriétaires d’opérations de charge de travail.

## <a name="how-this-guide-is-structured"></a>Structure de ce guide

Cet article fait partie d’une série. Les articles suivants sont destinés à être lus ensemble, dans l’ordre suivant :

* Introduction (cet article)
* [Stratégie de supervision pour les modèles de déploiement cloud](./cloud-models-monitor-overview.md)
* [Collecte des données appropriées](./data-collection.md)
* [Alertes](./alerting.md)

## <a name="products-and-services"></a>Produits et services

Quelques logiciels et services sont disponibles pour vous aider à superviser et à gérer diverses ressources hébergées dans Azure, votre réseau d’entreprise ou d’autres fournisseurs de cloud. Il s'agit de :

* System Center Operations Manager
* Azure Monitor, qui comprend maintenant Log Analytics et Application Insights
* Azure Policy et Azure Blueprints
* Azure Automation
* Azure Logic Apps
* Hubs d'événements Azure

Cette première version du guide couvre nos plateformes de supervision actuelles : Azure Monitor et System Center Operations Manager. Elle décrit également la stratégie recommandée pour superviser chacun des modèles de déploiement dans le cloud. Il couvre aussi la première série de recommandations en supervision, en commençant par la collecte de données et les alertes.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Stratégie de supervision pour les modèles de déploiement cloud](./cloud-models-monitor-overview.md)
