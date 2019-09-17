---
title: Sécuriser et gérer
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Outils de supervision et de gestion sécurisés
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 652637905f9de09972eed199f85245e99fb60e29
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022584"
---
# <a name="secure-monitoring-and-management-tools"></a>Outils de supervision et de gestion sécurisés

Une fois la migration terminée, les ressources migrées doivent être gérées par des opérations informatiques contrôlées. Cet article n’a pas pour but de suggérer une quelconque déviation par rapport aux bonnes pratiques opérationnelles. Considérez plutôt ce qui suit comme le minimum viable pour sécuriser et gérer des ressources migrées : soit au moyen d’opérations informatiques, soit de manière indépendante à mesure que ces opérations sont disponibles en ligne.

## <a name="monitoring"></a>Surveillance

La *supervision* consiste à collecter et à analyser des données afin de déterminer les performances, l’intégrité et la disponibilité de votre application métier et des ressources dont elle dépend. Azure comprend plusieurs services qui effectuent individuellement un rôle ou une tâche spécifique dans l’espace d’analyse. Ensemble, ces services fournissent une solution complète pour la collecte, l’analyse et l’action sur les données de télémétrie de vos applications de charge de travail et des ressources Azure qui les prennent en charge. Bénéficiez d’une visibilité sur l’intégrité et les performances de vos applications, de votre infrastructure et de vos données dans Azure à l’aide d’outils de supervision du cloud comme Azure Monitor, Log Analytics et Application Insights. Utilisez ces outils de supervision du cloud pour passer à l’action et intégrer vos solutions de management des services :

- **Supervision principale** L’analyse principale assure la surveillance essentielle et obligatoire des ressources Azure. Ces services nécessitent une configuration minimale et collectent des données de télémétrie de base utilisées par les services de surveillance Premium.
- **Supervision approfondie des applications et des infrastructures.** Les services Azure offrent de puissantes fonctionnalités de collecte et d’analyse des données de supervision à un niveau approfondi. Ces services s’appuient sur l’analyse principale et tirent profit des fonctionnalités communes dans Azure. Ils fournissent des données collectées à la fonctionnalité d’analyse puissante pour vous donner des informations uniques sur vos applications et votre infrastructure.

Découvrez-en plus sur [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) pour la supervision des ressources migrées.

## <a name="security-monitoring"></a>Surveillance de la sécurité

Reposez-vous sur Azure Security Center pour bénéficier de fonctionnalités unifiées de supervision de la sécurité et de notification avancée contre les menaces sur l’ensemble de vos charges de travail cloud hybrides. Azure Security Center offre une visibilité et un contrôle complets sur la sécurité des applications cloud dans Azure. Détectez rapidement les menaces et prenez les mesures nécessaires pour y remédier. Par ailleurs, réduisez l’exposition en activant la protection adaptative contre les menaces. Le tableau de bord intégré offre des insights instantanés sur les alertes de sécurité et les vulnérabilités nécessitant votre attention. Azure Security Center peut vous aider à accomplir de nombreuses tâches, notamment celles-ci :

- **Supervision centralisée des stratégies.** Assurez la conformité aux exigences de sécurité obligatoires ou de votre société en gérant de façon centralisée les stratégies de sécurité dans les charges de travail cloud hybrides.
- **Évaluation continue de la sécurité.** Supervisez la sécurité des machines, réseaux, services de stockage et de données, et des applications pour découvrir d’éventuels problèmes de sécurité.
- **Recommandations exploitables.** Remédiez aux vulnérabilités de sécurité avant qu’elles ne puissent être exploitées par des attaquants. Incluez des recommandations de sécurité hiérarchisées et exploitables.
- **Défenses cloud avancées.** Minimisez les menaces avec un accès juste-à-temps aux ports de gestion et la mise sur liste verte pour contrôler les applications exécutées sur vos machines virtuelles.
- **Alertes et incidents classés par ordre de priorité.** Concentrez-vous en premier lieu sur les menaces les plus importantes avec les incidents et alertes de sécurité classés par ordre de priorité.
- **Solutions de sécurité intégrées.** Collectez, recherchez et analysez les données de sécurité à partir d’un large éventail de sources, dont les solutions partenaires connectées.

Découvrez-en plus sur [Azure Security Center](https://docs.microsoft.com/azure/security-center) pour sécuriser les ressources migrées.

## <a name="protect-assets-and-data"></a>Protéger les ressources et les données

Sauvegarde Azure fournit un moyen de protéger les machines virtuelles, les fichiers et les données. Sauvegarde Azure peut vous aider à accomplir de nombreuses tâches, notamment celles-ci :

- Sauvegarde de machines virtuelles
- Sauvegarde de fichiers
- Sauvegarde de bases de données SQL Server
- Récupération de ressources protégées

Découvrez-en plus sur [Sauvegarde Azure](https://docs.microsoft.com/azure/backup) pour protéger les ressources migrées.
