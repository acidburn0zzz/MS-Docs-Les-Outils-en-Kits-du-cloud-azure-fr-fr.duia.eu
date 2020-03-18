---
title: Gestion et sécurité continues
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à vous concentrer sur les opérations et les configurations de sécurité qui prennent en charge vos opérations en cours.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: a68479bf128ea79383a5529b82a7866e399abc71
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79094583"
---
# <a name="phase-3-ongoing-management-and-security"></a>Phase 3 : Gestion et sécurité continues

Une fois que vous avez intégré les services de gestion de serveur Azure, vous devez vous concentrer sur les opérations et les configurations de sécurité qui prendront en charge vos opérations en cours. Nous allons commencer par sécuriser votre environnement en étudiant Azure Security Center. Nous allons ensuite configurer des stratégies pour assurer la conformité de vos serveurs et automatiser les tâches courantes. Cette section couvre les sujets suivants :

- **[Implémenter les recommandations en matière de sécurité.](#address-security-recommendations)** Azure Security Center fournit des recommandations pour améliorer la sécurité de votre environnement. Lorsque vous implémentez ces recommandations, vous constatez que l’impact est reflété dans un score de sécurité.
- **[Activer la stratégie Guest Configuration.](./guest-configuration-policy.md)** Utilisez la fonctionnalité Guest Configuration d’Azure Policy pour auditer les paramètres d’une machine virtuelle. Par exemple, vous pouvez vérifier si des certificats arrivent à expiration.
- **[Suivre et signaler les changements critiques.](./enable-tracking-alerting.md)** Lorsque vous effectuez un dépannage, la première question à vous poser est la suivante : « qu’est-ce qui a changé ? ». Dans cet article, vous allez apprendre à effectuer le suivi des modifications et à créer des alertes pour surveiller de manière proactive les composants critiques.
- **[Créer des planifications de mise à jour.](./update-schedules.md)** Planifiez l’installation des mises à jour pour vous assurer que tous vos serveurs disposent des versions les plus récentes.
- **[Exemples de stratégies Azure Policy courantes.](./common-policies.md)** Cet article fournit des exemples de stratégies de gestion courantes.

## <a name="address-security-recommendations"></a>Implémenter les recommandations en matière de sécurité

Azure Security Center est l’emplacement central où gérer la sécurité de votre environnement. Une évaluation générale et des recommandations ciblées s’affichent.

Nous vous recommandons de consulter et d’implémenter les recommandations fournies par ce service. Pour plus d’informations sur les avantages supplémentaires d’Azure Security Center, consultez [Suivre les recommandations Azure Security Center](https://docs.microsoft.com/azure/migrate/migrate-best-practices-security-management#best-practice-follow-azure-security-center-recommendations).

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [activer la fonctionnalité de configuration d’invité Azure Policy](./guest-configuration-policy.md).

> [!div class="nextstepaction"]
> [Stratégie Guest Configuration](./guest-configuration-policy.md)
