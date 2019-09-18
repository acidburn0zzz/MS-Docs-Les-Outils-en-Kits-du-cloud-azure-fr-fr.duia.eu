---
title: Guide de supervision du cloud - Collecte des données appropriées
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Choisir quand utiliser Azure Monitor ou System Center Operations Manager dans Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 06/26/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 8b0aebe00d987ac49ba965fc1982c1615372ba92
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71032188"
---
# <a name="cloud-monitoring-guide-collecting-the-right-data"></a>Guide de supervision du cloud : Collecte des données appropriées

Cet article décrit quelques éléments à prendre en compte pour la collecte de données de supervision dans une application cloud.

Pour observer l’intégrité et la disponibilité de votre solution cloud, vous devez configurer les outils de supervision pour collecter un niveau de signaux basés sur des états de défaillance prévisibles. Ces signaux sont les symptômes de la défaillance, mais n’en sont pas la cause. Les outils de supervision utilisent des métriques et, dans le cas de diagnostics avancés et de l’analyse de la cause racine, ils utilisent également des journaux.

Planifiez la supervision et la migration avec soin. Commencez par inclure le propriétaire du service de supervision, le responsable de l’exploitation et d’autres personnes associées pendant la phase de planification, et continuez à les impliquer tout au long du cycle de développement et de publication. Leur but premier sera de développer une configuration de supervision basée sur les critères suivants :

- Quelle est la composition du service, et ces dépendances sont-elles supervisées aujourd’hui ? Si oui, plusieurs outils sont-ils impliqués ? Y a-t-il une opportunité de consolider sans introduire de risques ?
- Quel est le contrat SLA du service, et comment puis-je le mesurer et le communiquer ?
- À quoi doit ressembler le tableau de bord du service quand un incident se produit ? À quoi doit ressembler le tableau de bord pour le propriétaire du service et pour l’équipe qui assure le support du service ?
- Quelles sont les métriques produites par la ressource que je dois superviser ?  
- Comment le propriétaire du service, les équipes de support et les autres membres du personnel feront-ils des recherches dans les journaux ?

La façon dont vous répondez à ces questions ainsi que les critères d’alerte déterminent la façon dont vous allez utiliser la plateforme de supervision. Si vous migrez depuis une plateforme de supervision existante ou d’un ensemble d’outils de supervision existants, utilisez la migration comme une opportunité de réévaluer les signaux que vous collectez. Ceci est spécialement vrai maintenant qu’il y a plusieurs facteurs de coûts à prendre en compte lors de la migration ou de l’intégration à une plateforme de supervision basée sur le cloud, comme Azure Monitor. Rappelez-vous que vous devez pouvoir réagir aux données de supervision. Les données que vous collectez doivent être optimisées de façon à vous donner une vision générale de l’intégrité globale du service. L’instrumentation définie pour identifier les incidents réels doit être aussi simple, aussi prévisible et aussi fiable que possible.

## <a name="develop-a-monitoring-configuration"></a>Développer une configuration de supervision

Le propriétaire et l’équipe du service de supervision suivent généralement un ensemble commun d’activités pour développer une configuration de supervision. Ces activités commencent dès les premières étapes de planification, se poursuivent via les tests et les validations dans un environnement hors production, et s’étendent jusqu’au déploiement en production. Les configurations de supervision sont dérivées des modes de défaillance connus, des résultats des tests de défaillances simulées et de l’expérience de plusieurs personnes au sein de l’organisation (Service Desk, exploitation, ingénieurs et développeurs). De telles configurations supposent que le service existe déjà, qu’il va être migré dans le cloud et qu’il n’a pas été réarchitecturé.

Surveillez l’intégrité et la disponibilité de ces services dès le début du processus de développement, de façon à obtenir des résultats en matière de qualité du niveau de service. Si vous supervisez la conception de ce service ou de cette application a posteriori, vos résultats ne seront pas aussi satisfaisants.

Pour accélérer la résolution de l’incident, tenez compte des recommandations suivantes :

- Définissez un tableau de bord pour chaque composant du service.
- Utilisez des métriques pour guider le diagnostic approfondi, et pour identifier une solution ou un contournement du problème si vous ne pouvez pas déterminer une cause racine.
- Utilisez les fonctionnalités d’exploration du tableau de bord ou prenez en charge la personnalisation de la vue pour l’examiner plus en détails.
- Si vous avez besoin de journaux détaillés, les métriques doivent avoir permis de cibler les critères de recherche. Si ce n’est pas le cas, améliorez vos mesures pour l’incident suivant.

L’adoption de cet ensemble de principes vous offre des insights en quasi temps réel ainsi qu’une meilleure gestion de votre service.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Stratégie d’alerte](./alerting.md)
