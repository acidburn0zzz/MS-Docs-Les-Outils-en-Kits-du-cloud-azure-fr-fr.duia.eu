---
title: Centraliser les opérations de gestion
description: Découvrez comment centraliser les opérations de gestion à l’aide d’un seul locataire Azure Active Directory pour tous les utilisateurs. La gestion centralisée simplifie les opérations de gestion et réduit les coûts de maintenance.
author: JnHs
ms.author: jenhayes
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 6d777a1c919e72c55d8c6202ef1c32f44d9444d9
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219476"
---
<!-- cSpell:ignore jenhayes -->

# <a name="centralize-management-operations"></a>Centraliser les opérations de gestion

Pour la plupart des organisations, l’utilisation d’un seul locataire Azure Active Directory (Azure AD) pour tous les utilisateurs simplifie les opérations de gestion et réduit les coûts de maintenance. Cela est dû au fait que toutes les tâches de gestion peuvent être effectuées par des utilisateurs désignés, des groupes d’utilisateurs ou des principaux de service au sein de ce locataire.

Nous vous recommandons d’utiliser un seul locataire Azure AD pour votre organisation si possible. Toutefois, il peut arriver qu’une organisation soit amenée à gérer plusieurs locataires Azure AD pour les raisons suivantes :

- il s’agit de filiales entièrement indépendantes.
- Elles fonctionnent indépendamment dans plusieurs zones géographiques.
- Certaines conditions légales ou de conformité s’appliquent.
- Il existe des acquisitions d’autres organisations (parfois temporaire jusqu’à ce qu’une stratégie de regroupement des locataires à long terme soit définie).

Lorsqu’une architecture multilocataire est nécessaire, [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/overview) offre un moyen de centraliser et de simplifier les opérations de gestion. Les abonnements de plusieurs locataires peuvent être intégrés pour la [gestion des ressources déléguées Azure](https://docs.microsoft.com/azure/lighthouse/concepts/azure-delegated-resource-management). Cette option permet aux utilisateurs spécifiés du locataire gérant pour effectuer [des fonctions de gestion inter-locataires](https://docs.microsoft.com/azure/lighthouse/concepts/cross-tenant-management-experience) de manière centralisée et évolutive.

Par exemple, supposons que votre organisation dispose d’un seul locataire, `Tenant A`. L’organisation acquiert ensuite deux locataires supplémentaires, `Tenant B` et `Tenant C`, et vous avez des raisons métier qui vous demandent d’assurer la maintenance en tant que locataires distincts.

Votre organisation souhaite utiliser les mêmes définitions de stratégie, pratiques de sauvegarde et processus de sécurité sur tous les locataires. Étant donné que vous avez déjà des utilisateurs (notamment des groupes d’utilisateurs et des principaux de service) qui sont chargés de l’exécution de ces tâches dans le Locataire A, vous pouvez intégrer tous les abonnements du Locataire B et du Locataire C afin que ces mêmes utilisateurs du Locataire A puissent exécuter ces tâches. Le locataire A devient alors le locataire gestionnaire pour le locataire B et le locataire C.

![Utilisateurs du Locataire A qui gèrent des ressources dans le Locataire B et dans le Locataire C](../_images/manage/enterprise-azure-lighthouse.jpg)

Pour plus d’informations, consultez [Azure Lighthouse dans les scénarios d’entreprise](https://docs.microsoft.com/azure/lighthouse/concepts/enterprise).
