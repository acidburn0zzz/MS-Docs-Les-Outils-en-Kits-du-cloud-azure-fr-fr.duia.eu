---
title: Fonction de sécurité d’infrastructure cloud et de point de terminaison
description: Comprendre la fonction de sécurité d’infrastructure cloud et de point de terminaison.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.topic: conceptual
ms.date: 05/15/2020
ms.openlocfilehash: 427ab031953652c32c77a24e73fb0a0e4cfa10af
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83755427"
---
# <a name="function-of-cloud-infrastructure-and-endpoint-security"></a>Fonction de sécurité d’infrastructure cloud et de point de terminaison

Une équipe de sécurité du cloud travaillant sur la sécurité d’infrastructure et de point de terminaison fournit des contrôles de protection, de détection et de réponse pour des composants d’infrastructure et de réseau exploités par des applications d’entreprise et des utilisateurs.

## <a name="modernization"></a>Modernisation

Des centres de données à définition logicielle et d’autres technologies cloud aident à résoudre des problèmes de longue date liés à la sécurité d’infrastructure et de point de terminaison, à savoir :

- **Détection d'erreurs d'inventaire et de configuration** bien plus fiable pour des ressources hébergées dans le cloud, car elles sont toutes immédiatement visibles (contrairement à un centre de données physique).
- **Gestion des vulnérabilités** devenant une partie essentielle de la gestion de la posture de sécurité globale.
- **Ajout de technologies de conteneur** devant être gérées et sécurisées par une ou plusieurs équipes d’infrastructure et de réseau à mesure que l’organisation adopte cette technologie à grande échelle. Pour obtenir un exemple, consultez [Sécurité des conteneurs dans Security Center](https://docs.microsoft.com/azure/security-center/container-security).
- **Consolidation de l’agent de sécurité** et la simplification de l’outil pour réduire la surcharge de maintenance et de performances des agents et outils de sécurité.
- **Mise en liste verte d’applications** et filtrage du réseau interne devenant beaucoup plus faciles à configurer et à déployer pour des serveurs hébergés dans le cloud (à l’aide d’ensembles de règles générés par apprentissage automatique). Pour obtenir des exemples Azure, consultez les rubriques sur les [contrôles d’application adaptatifs](https://docs.microsoft.com/azure/security-center/security-center-adaptive-application) et le [renforcement du réseau adaptatif](https://docs.microsoft.com/azure/security-center/security-center-adaptive-network-hardening).
- **Modèles automatisés** pour la configuration de l’infrastructure et de la sécurité beaucoup plus faciles à utiliser avec des centres de données à définition logicielle dans le cloud. Exemple Azure : [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview)
- **Accès Juste assez (JEA) et Juste-à-temps (JIT)** permettant l’application pratique des principes de privilège minimum à l’accès privilégié pour les serveurs et les points de terminaison.
- **Expérience utilisateur** devenant critique, car les utilisateurs peuvent de plus en plus choisir ou acheter leurs appareils de point de terminaison.
- **Gestion unifiée des points de terminaison** permettant de gérer la posture de sécurité de tous les appareils de point de terminaison, y compris des PC mobiles et traditionnels, ainsi que de fournir des signaux d’intégrité d’appareil critiques pour les solutions de contrôle d’accès Confiance Zéro.
- **Architectures de sécurité réseau** et contrôles partiellement réduits par le passage à des architectures d’application cloud, mais restant une mesure de sécurité fondamentale. Pour plus d’informations, consultez [Autonomie et sécurité du réseau](https://docs.microsoft.com/azure/architecture/framework/security/network-security-containment).

## <a name="team-composition-and-key-relationships"></a>Composition d’équipe et relations clés

La sécurité d’infrastructure cloud et de point de terminaison interagit généralement avec les rôles suivants :

- Architecture et opérations informatiques
- Architecture de la sécurité
- Centre des opérations de sécurité
- Équipe de conformité
- Équipe d’audit

## <a name="next-steps"></a>Étapes suivantes

Examinez la fonction de [renseignement sur les menaces](./cloud-security-threat-intelligence.md).
