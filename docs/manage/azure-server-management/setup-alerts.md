---
title: Configurer des alertes de base
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Configurer des alertes de base
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5b11a97e78d5fcd1b2a2cc866f5a7062bc6a2977
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71032493"
---
# <a name="set-up-basic-alerts"></a>Configurer des alertes de base

Une partie essentielle de la gestion des ressources consiste à être averti quand un problème survient. Les alertes vous avertissent de conditions critiques de façon proactive. Elles peuvent reposer sur des déclencheurs activés par des métriques, des journaux ou des problèmes d’intégrité de service. Dans le cadre de l’intégration des services de gestion de serveur Azure, vous pouvez configurer des alertes et des notifications qui peuvent vous aider à informer vos équipes informatiques de tout problème.

## <a name="azure-monitor-alerts"></a>Alertes Azure Monitor

Azure Monitor offre des fonctionnalités d’[alerte](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview) pour vous avertir par e-mail ou messagerie en cas de problème. Ces fonctionnalités sont basées sur une plateforme de supervision de données commune qui comprend des journaux d’activité et des métriques générés par vos serveurs et d’autres ressources. Cette plateforme vous permet d’analyser les données combinées à partir de plusieurs ressources à l’aide d’un ensemble commun d’outils dans Azure Monitor, que vous pouvez utiliser pour déclencher des alertes. Ces déclencheurs peuvent inclure les éléments suivants :

- Valeurs de métrique
- Requêtes de recherche de journal
- Événements du journal d’activité
- Contrôle d’intégrité de la plateforme Azure sous-jacente
- Tests de disponibilité des sites web

Consultez la [liste des sources de données Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/data-sources) pour obtenir une description plus détaillée des sources de données de supervision collectées par ce service.

Pour plus d’informations sur la création et la gestion manuelles des alertes à l’aide du portail, consultez la [documentation Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric).

## <a name="automated-deployment-of-recommended-alerts"></a>Déploiement automatisé des alertes recommandées

Dans ce guide, nous vous recommandons d’activer un ensemble de 15 alertes pour la supervision de l’infrastructure de base. Vous trouverez les scripts de déploiement dans le [dépôt GitHub du kit d’alertes Azure](https://github.com/Microsoft/manageability-toolkits).

Ce package crée des alertes pour l’espace disque insuffisant, la mémoire disponible insuffisante, l’utilisation élevée de l’UC, les arrêts inattendus, les systèmes de fichiers endommagés et les défaillances matérielles courantes. Le package utilise du matériel serveur HP comme exemple. Vous devez changer les paramètres dans le fichier de configuration associé afin qu’il reflète votre matériel OEM. Vous pouvez également ajouter des compteurs de performances au fichier de configuration. Pour déployer le package, exécutez le fichier New-CoreAlerts.ps1 file.

## <a name="next-steps"></a>Étapes suivantes

Découvrez les opérations et les mécanismes de sécurité qui prennent en charge vos opérations en cours.

> [!div class="nextstepaction"]
> [Gestion et sécurité continues](./ongoing-management-overview.md)
