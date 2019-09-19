---
title: Gestion et sécurité continues
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Gestion et sécurité continues
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7b77181dd8ef6efe655b56489e5d4e6b210382b6
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031369"
---
# <a name="phase-3-ongoing-management-and-security"></a>Phase 3 : Gestion et sécurité continues

Une fois que vous avez intégré les services de gestion Azure, vous devez vous concentrer sur les opérations et les configurations de sécurité qui prendront en charge vos opérations en cours. Nous allons commencer par sécuriser votre environnement en étudiant Azure Security Center. Nous allons ensuite configurer des stratégies pour assurer la conformité de vos serveurs et automatiser les tâches courantes. Cette section couvre les sujets suivants :

- **[Implémenter les recommandations en matière de sécurité.](#address-security-recommendations)** Azure Security Center fournit des recommandations pour améliorer la sécurité de votre environnement. Lorsque vous implémentez ces recommandations, l’impact est reflété dans un score de sécurité.
- **[Activer la stratégie Guest Configuration.](./guest-configuration-policy.md)** Activez la fonctionnalité Guest Configuration d’Azure Policy pour auditer les paramètres d’une machine virtuelle. Par exemple, vous pouvez vérifier si des certificats arrivent à expiration.
- **[Suivre et signaler les changements critiques.](./enable-tracking-alerting.md)** Lorsque vous effectuez un dépannage, la première question à vous poser est la suivante : « qu’est-ce qui a changé ? ». Dans cet article, vous allez apprendre à effectuer le suivi des modifications et à créer des alertes pour surveiller de manière proactive les composants critiques.
- **[Créer des planifications de mise à jour.](./update-schedules.md)** Planifiez l’installation des mises à jour pour vous assurer que tous vos serveurs disposent des versions les plus récentes.
- **[Exemples de stratégies Azure Policy courantes.](./common-policies.md)** Fournit des exemples de stratégies de gestion courantes.

## <a name="address-security-recommendations"></a>Implémenter les recommandations en matière de sécurité

Azure Security Center est l’emplacement central où gérer la sécurité de votre environnement. Une évaluation générale et des recommandations ciblées s’affichent.

Nous vous recommandons de consulter et d’implémenter les recommandations fournies par ce service. Pour plus d’informations sur les avantages supplémentaires d’Azure Security Center, consultez [Suivre les recommandations Azure Security Center](https://docs.microsoft.com/azure/migrate/migrate-best-practices-security-management#best-practice-follow-azure-security-center-recommendations).

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [activer la fonctionnalité de configuration d’invité Azure Policy](./guest-configuration-policy.md).

> [!div class="nextstepaction"]
> [Stratégie Guest Configuration](./guest-configuration-policy.md)
