---
title: Concepts fondamentaux Azure
description: Découvrez les concepts fondamentaux et les termes utilisés dans Azure, ainsi que la façon dont les concepts sont liés entre eux.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: d11e69014a9e46f916afb5bc8caf083c930ce725
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76799146"
---
# <a name="azure-fundamental-concepts"></a>Concepts fondamentaux Azure

Découvrez les concepts fondamentaux et les termes qui sont utilisés dans Azure, ainsi que la façon dont les concepts sont liés entre eux.

## <a name="azure-terminology"></a>Terminologie Azure

Il est utile de connaître les définitions suivantes lorsque vous commencez vos efforts d’adoption du cloud Azure :

- **Ressource :** Une entité gérée par Azure. Les exemples incluent les machines virtuelles, les réseaux virtuels et les comptes de stockage Azure.
- **Abonnement :** Un conteneur logique pour vos ressources. Chaque ressource Azure est associée à un seul abonnement. La création d’un abonnement est la première étape de l’adoption d’Azure.
- **Compte Azure :** L’adresse de messagerie que vous fournissez lors de la création d’un abonnement Azure est le compte Azure associé à l’abonnement. Le tiers associé au compte de messagerie est responsable des coûts mensuels engendrés par les ressources de l’abonnement. Lorsque vous créez un compte Azure, vous fournissez vos informations de contact et vos détails de facturation, comme une carte de crédit. Vous pouvez utiliser le même compte Azure (adresse e-mail) pour plusieurs abonnements. Chaque abonnement est associé à un seul compte Azure.
- **Administrateur de compte :** Le tiers associé à l’adresse de messagerie utilisée pour créer un abonnement Azure. Il incombe à l’administrateur de compte de payer tous les coûts engendrés par les ressources de l’abonnement.
- **Azure Active Directory (Azure AD) :** Un service Microsoft basé sur le cloud qui gère les identités et les accès. Azure AD permet à vos employés de se connecter et d’accéder aux ressources.
- **Locataire Azure AD :** Une instance dédiée et approuvée d’Azure AD. Un locataire Azure AD est automatiquement créé quand votre organisation souscrit un abonnement à un service cloud Microsoft tel que Microsoft Azure, Microsoft Intune ou Office 365. Un locataire Azure représente une seule organisation.
- **Répertoire Azure AD :** Chaque locataire Azure a un annuaire Azure AD dédié et approuvé. L’annuaire contient les utilisateurs, les groupes et les applications du locataire. Cet annuaire est utilisé pour exécuter des fonctions de gestion des identités et des accès en relation avec les ressources du client. Un répertoire peut être associé à plusieurs abonnements, mais chaque abonnement est associé à un seul répertoire.
- **Groupes de ressources :** Des conteneurs logiques que vous utilisez pour regrouper les ressources associées dans un abonnement. Chaque ressource ne peut exister que dans un seul groupe de ressources. Les groupes de ressources permettent des regroupements plus précis au sein d’un abonnement. Ils sont couramment utilisés pour représenter une collection de ressources nécessaires à la prise en charge d’une charge de travail, d’une application ou d’une fonction spécifique au sein d’un abonnement.
- **Groupes d’administration :** Conteneurs logiques que vous utilisez pour un ou plusieurs abonnements. Vous pouvez définir une hiérarchie de groupes d’administration, d’abonnements, de groupes de ressources et de ressources pour gérer efficacement l’accès, les stratégies et la conformité par le biais de l’héritage.
- **Région :** Ensemble de centres de données Azure déployés au sein d’un périmètre défini par la latence. Les centres de données sont connectés via un réseau dédié, régional et à faible latence. La plupart des ressources Azure s’exécutent dans une région Azure spécifique.

## <a name="azure-subscription-purposes"></a>Objectifs de l’abonnement Azure

Un abonnement Azure remplit plusieurs fonctions. Un abonnement Azure est :

- **Un accord légal.** Chaque abonnement est associé à une [offre Azure](https://azure.microsoft.com/support/legal/offer-details) (par exemple une version d’évaluation gratuite ou un paiement à l’utilisation). Chaque offre présente un plan tarifaire, des avantages et des conditions générales associées. Vous choisissez une offre Azure lorsque vous créez un abonnement.
- **Un accord de paiement.** Lorsque vous créez un abonnement, vous fournissez des informations de paiement pour cet abonnement, comme un numéro de carte de crédit. Chaque mois, les coûts engendrés par les ressources déployées sur cet abonnement sont calculés et facturés par le biais de ce mode de paiement.
- **Une limite d’échelle.** Des limites d’échelle sont définies pour un abonnement. Les ressources de l’abonnement ne peuvent pas dépasser les limites d’échelle définies. Par exemple, il existe une limite sur le nombre de machines virtuelles que vous pouvez créer dans un seul abonnement.
- **Une limite administrative.** Un abonnement peut agir comme une limite pour l’administration, la sécurité et la stratégie. Azure fournit également d’autres mécanismes pour répondre à ces besoins, comme les groupes d’administration, les groupes de ressources et le contrôle d’accès en fonction du rôle.

## <a name="azure-subscription-considerations"></a>Considérations relatives aux abonnements Azure

Lorsque vous créez un abonnement Azure, vous effectuez plusieurs choix clés sur l’abonnement :

- **Qui est responsable du paiement de l’abonnement ?** Le tiers associé à l’adresse e-mail que vous fournissez lors de la création d’un abonnement par défaut est l’administrateur de compte de l’abonnement. Le tiers associé à cette adresse de messagerie est chargé de payer tous les coûts engagés par les ressources de l’abonnement.
- **Quelle offre Azure m’intéresse-t-elle ?** Chaque abonnement est associé à une [offre Azure](https://azure.microsoft.com/support/legal/offer-details) spécifique. Vous pouvez choisir l’offre Azure qui répond le mieux à vos besoins. Par exemple, si vous envisagez d’utiliser un abonnement pour exécuter des charges de travail hors production, vous pouvez choisir l’offre Dev/Test - Paiement à l’utilisation ou l’offre Enterprise Dev/Test.

> [!NOTE]
> Lorsque vous vous inscrivez à Azure, vous pourriez voir l’expression *Créer un compte Azure*. Vous créez un compte Azure lorsque vous créez un abonnement Azure et que vous associez l’abonnement à un compte e-mail.

## <a name="azure-administrative-roles"></a>Rôles d’administration d’Azure

Azure définit trois types de rôles pour l’administration des abonnements, des identités et des ressources :

- Rôles d’administrateur d’abonnements classique
- Rôles de contrôle d’accès en fonction du rôle (RBAC) Azure
- Rôles d’administrateur Azure Active Directory (Azure AD)

Le rôle d’administrateur de compte pour un abonnement Azure est attribué au compte e-mail utilisé pour créer l’abonnement Azure. L’administrateur de compte est le responsable de la facturation de l’abonnement. L’administrateur de compte peut gérer les détails de l’abonnement dans le [Centre des comptes Azure](https://account.azure.com/Subscriptions).

Par défaut, le rôle d’administrateur de service pour un abonnement est également affecté au compte e-mail utilisé pour créer l’abonnement Azure. L’administrateur de service dispose des autorisations d’accès à l’abonnement équivalentes au rôle de propriétaire RBAC. L’Administrateur de service a également un accès complet au portail Azure. L’administrateur de compte peut modifier l’administrateur de service en lui attribuant un autre compte e-mail.

Lorsque vous créez un abonnement Azure, vous pouvez l’associer à un locataire Azure AD existant. Dans le cas contraire, un nouveau locataire Azure AD avec un annuaire associé est créé. Le rôle d’administrateur général dans l’annuaire Azure AD est attribué au compte e-mail utilisé pour créer l’abonnement Azure AD.

Un compte e-mail peut être associé à plusieurs abonnements Azure. L’administrateur de compte peut transférer l’abonnement à un autre compte.

Pour obtenir une description détaillée des rôles définis dans Azure, consultez [rôles d’administrateur d’abonnement classiques, rôles RBAC Azure et rôles d’administrateur Azure AD](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles).

## <a name="subscriptions-and-regions"></a>Abonnements et régions

Chaque ressource Azure est associée de manière logique à un seul abonnement. Lorsque vous créez une ressource, vous choisissez l’abonnement Azure sur lequel vous souhaitez déployer cette ressource. Vous pouvez déplacer ultérieurement une ressource vers un autre abonnement.

Un abonnement n’est pas lié à une région Azure spécifique. Toutefois, chaque ressource Azure est déployée dans une seule région. Vous pouvez avoir des ressources dans plusieurs régions associées au même abonnement.

> [!NOTE]
> La plupart des ressources Azure sont déployées dans une région spécifique. Toutefois, certains types de ressources sont considérés comme des ressources globales, comme les stratégies que vous définissez à l’aide des services Azure Policy.

## <a name="related-resources"></a>Ressources associées

Les ressources suivantes fournissent des informations détaillées sur les concepts abordés dans cet article :

- [Fonctionnement d’Azure](../../getting-started/what-is-azure.md)
- [Gestion de l’accès aux ressources dans Azure](../../govern/resource-consistency/resource-access-management.md)
- [Présentation d’Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)
- [Contrôle d’accès en fonction du rôle (RBAC) pour les ressources Azure](https://docs.microsoft.com/azure/role-based-access-control/overview)
- [Qu’est-ce qu’Azure Active Directory ?](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)
- [Associer ou ajouter un abonnement Azure à votre locataire Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)
- [Topologies pour Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies)
- [Abonnements, licences, comptes et locataires pour les offres cloud de Microsoft](https://docs.microsoft.com/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous comprenez les concepts fondamentaux d’Azure, découvrez comment [mettre à l’échelle avec plusieurs abonnements Azure](../azure-best-practices/scaling-subscriptions.md).

> [!div class="nextstepaction"]
> [Mettre à l’échelle avec plusieurs abonnements Azure](../azure-best-practices/scaling-subscriptions.md)
