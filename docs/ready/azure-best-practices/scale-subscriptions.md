---
title: Créer des abonnements supplémentaires pour mettre à l’échelle votre environnement Azure
description: Utilisez Cloud Adoption Framework pour Azure afin de découvrir comment développer une stratégie de mise à l’échelle de votre environnement avec plusieurs abonnements Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: dd052e42bc9685701df831878c12ed37ed42395c
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80359862"
---
# <a name="create-additional-subscriptions-to-scale-your-azure-environment"></a>Créer des abonnements supplémentaires pour mettre à l’échelle votre environnement Azure

Les organisations utilisent souvent plusieurs abonnements Azure pour éviter les limites de ressources par abonnement, et mieux gérer et régir leurs ressources Azure. Il est important de définir une stratégie de mise à l’échelle de vos abonnements.

## <a name="review-fundamental-concepts"></a>Passer en revue les concepts fondamentaux

Quand vous développez votre environnement Azure au-delà de vos [abonnements initiaux](./initial-subscriptions.md), il est important de comprendre les concepts Azure comme les comptes, les locataires, les annuaires et les abonnements. Pour plus d’informations, consultez [Concepts fondamentaux Azure](../considerations/fundamental-concepts.md).

D’autres considérations peuvent nécessiter des abonnements supplémentaires. Gardez les points suivants à l’esprit lorsque vous développez votre patrimoine cloud.

## <a name="technical-considerations"></a>Considérations techniques

**Limites d’abonnement :** Les abonnements ont des limites définies pour certains types de ressources. Par exemple, le nombre de réseaux virtuels dans un abonnement est limité. Quand un abonnement approche ces limites, vous devez créer un autre abonnement et y placer des ressources supplémentaires. Pour plus d’informations, consultez [Azure subscription and service limits (Limites de service et d’abonnement Azure)](https://docs.microsoft.com/azure/azure-subscription-service-limits#general-limits).

**Ressources de modèle classique :** Si vous utilisez Azure depuis un certain temps, vous avez peut-être des ressources qui ont été créées à l’aide du modèle de déploiement classique. Les stratégies Azure, le contrôle d’accès en fonction du rôle, le regroupement de ressources et les étiquettes ne peuvent pas être appliqués aux ressources du modèle classique. Vous devez déplacer ces ressources dans des abonnements qui contiennent uniquement des ressources de modèle classique.

**Coûts :** Il peut y avoir des coûts supplémentaires pour l’entrée et la sortie des données entre les abonnements.

## <a name="business-priorities"></a>Priorités de l’entreprise

Les priorités de votre entreprise peuvent vous amener à créer des abonnements supplémentaires. Ces priorités sont notamment les suivantes :

- Innovation
- Migration
- Coût
- Opérations
- Sécurité
- Gouvernance

Pour découvrir d’autres considérations sur la mise à l’échelle de vos abonnements, consultez le [guide de décision concernant les abonnements](../../decision-guides/subscriptions/index.md) dans Cloud Adoption Framework.

## <a name="moving-resources-between-subscriptions"></a>Déplacement de ressources entre des abonnements

À mesure que votre modèle d’abonnement se développe, vous pouvez décider que certaines ressources appartiennent à d’autres abonnements. De nombreux types de ressources peuvent être déplacés d’un abonnement vers un autre. Vous pouvez également utiliser des déploiements automatisés pour recréer des ressources dans un autre abonnement. Pour plus d’informations, consultez [Déplacer des ressources Azure vers un autre groupe de ressources ou abonnement](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).

## <a name="tips-for-creating-new-subscriptions"></a>Conseils pour la création de nouveaux abonnements

- Identifiez la personne chargée de la création de nouveaux abonnements.
- Déterminez les types de ressources qui sont disponibles dans un abonnement par défaut.
- Déterminez à quoi ressemblera tous les abonnements standard. Les considérations incluent l’accès RBAC, les stratégies, les balises et les ressources d’infrastructure.
- Si possible, [créez des abonnements par programmation](https://docs.microsoft.com/azure/azure-resource-manager/management/programmatically-create-subscription) à l’aide d’un principal de service. Vous devez [accorder une autorisation au principal de service](https://docs.microsoft.com/azure/azure-resource-manager/grant-access-to-create-subscription) pour créer des abonnements. Définissez un groupe de sécurité qui peut demander de nouveaux abonnements via un flux de travail automatisé.
- Si vous êtes un client Accord Entreprise (EA), demandez au support Azure de bloquer la création d’abonnements non-EA pour votre organisation.

## <a name="next-steps"></a>Étapes suivantes

Créez une hiérarchie des groupes d’administration pour mieux [organiser et gérer vos abonnements et ressources](./organize-subscriptions.md).

> [!div class="nextstepaction"]
> [Organiser et gérer vos abonnements et ressources](./organize-subscriptions.md)
