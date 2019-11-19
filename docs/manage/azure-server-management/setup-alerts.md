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
ms.openlocfilehash: 5d7469f8613b38ffdaefb41410409fba0c9109fd
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565297"
---
# <a name="set-up-basic-alerts"></a>Configurer des alertes de base

Une partie essentielle de la gestion des ressources consiste à être averti quand un problème survient. Les alertes vous informent de façon proactive des conditions critiques, sur la base de déclencheurs de métriques, de journaux ou de problèmes d’intégrité du service. Dans le cadre de l’intégration des services de gestion de serveur Azure, vous pouvez configurer des alertes et des notifications qui vous aident à informer vos équipes informatiques de tout problème.

## <a name="azure-monitor-alerts"></a>Alertes Azure Monitor

Azure Monitor offre des fonctionnalités d’[alerte](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview) pour vous avertir par e-mail ou messagerie en cas de problème. Ces fonctionnalités sont basées sur une plateforme de supervision de données commune qui comprend des journaux d’activité et des métriques générés par vos serveurs et d’autres ressources. Un ensemble commun d’outils dans Azure Monitor vous permet d’analyser des données combinées à partir de plusieurs ressources et de les utiliser pour déclencher des alertes. Ces déclencheurs peuvent inclure les éléments suivants :

- Valeurs de métrique
- Requêtes de recherche de journal
- Événements du journal d’activité.
- Contrôle d’intégrité de la plateforme Azure sous-jacente.
- Tests de disponibilité des sites web

Consultez la [liste des sources de données Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/data-sources) pour obtenir une description plus détaillée des sources de données de supervision collectées par ce service.

Pour plus d’informations sur la création et la gestion manuelles des alertes à l’aide du portail Azure, consultez la [documentation Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric).

## <a name="automated-deployment-of-recommended-alerts"></a>Déploiement automatisé des alertes recommandées

Dans ce guide, nous vous recommandons de créer un ensemble de 15 alertes pour la supervision de l’infrastructure de base. Vous trouverez les scripts de déploiement dans le [dépôt GitHub du kit d’alertes Azure](https://github.com/Microsoft/manageability-toolkits).

Ce package crée des alertes pour les états suivants :

- Espace disque insuffisant
- Peu de mémoire disponible
- Utilisation élevée de l’UC
- Arrêts inattendus
- Systèmes de fichiers corrompus
- Pannes matérielles courantes

Le package utilise du matériel serveur HP comme exemple. Modifiez les paramètres dans le fichier de configuration associé afin qu’il reflète votre matériel OEM. Vous pouvez également ajouter des compteurs de performances au fichier de configuration. Pour déployer le package, exécutez le fichier New-CoreAlerts.ps1 file.

## <a name="next-steps"></a>Étapes suivantes

Découvrez les opérations et les mécanismes de sécurité qui prennent en charge vos opérations en cours.

> [!div class="nextstepaction"]
> [Gestion et sécurité continues](./ongoing-management-overview.md)
