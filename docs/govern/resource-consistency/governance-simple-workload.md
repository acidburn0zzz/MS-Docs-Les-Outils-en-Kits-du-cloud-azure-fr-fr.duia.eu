---
title: Conception de gouvernance pour une charge de travail simple
description: Découvrez le processus de conception d’un modèle de gouvernance des ressources dans Azure pour subvenir aux besoins d’une seule équipe et d’une charge de travail simple.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: e68b8bc71e3a7cd306b4cfd8bc39628276d53031
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83399170"
---
# <a name="governance-design-for-a-simple-workload"></a>Conception de gouvernance pour une charge de travail simple

Ce guide a pour but de vous aider à comprendre comment concevoir un modèle de gouvernance des ressources dans Azure destiné à prendre en charge une seule équipe et une charge de travail simple. Vous allez passer en revue plusieurs exigences de gouvernance hypothétiques, puis étudier plusieurs exemples d’implémentation qui répondent à ces exigences.

Dans la phase préparatoire à l’adoption, notre objectif est de déployer une charge de travail simple vers Azure. Il en résulte les exigences suivantes :

- Gestion des identités pour un seul **propriétaire de charge de travail** qui est responsable du déploiement et la gestion de la charge de travail simple. Le propriétaire de la charge de travail requiert une autorisation pour créer, lire, mettre à jour et supprimer des ressources, ainsi que pour déléguer ces droits à d’autres utilisateurs dans le système de gestion d’identité.
- Gérez toutes les ressources de la charge de travail simple en tant qu’unité de gestion unique.

## <a name="azure-licensing"></a>Gestion des licences Azure

Avant de commencer la conception du modèle de gouvernance, il est important de comprendre comment Azure est concédé sous licence. En effet, les comptes d’administration associés à votre licence Azure ont le plus haut niveau d’accès à toutes vos ressources Azure. Ces comptes d’administration constituent la base de votre modèle de gouvernance.

> [!NOTE]
> Si votre organisation dispose déjà d’un [contrat entreprise Microsoft](https://www.microsoft.com/licensing/licensing-programs/enterprise) qui n’inclut pas Azure, Azure peut être ajouté en effectuant un engagement financier initial. Pour plus d’informations, consultez [Gestion des licences Azure pour l’entreprise](https://azure.microsoft.com/pricing/enterprise-agreement).

Lorsqu’Azure a été ajouté au Contrat Entreprise de votre organisation, cette dernière a été invitée à créer un **compte Azure**. Pendant le processus de création du compte, un **propriétaire de compte Azure** a été créé, ainsi qu’un locataire Azure Active Directory (Azure AD) avec un compte **d’administrateur général**. Un client Azure AD est une construction logique qui représente une instance d’Azure AD dédiée et sécurisée.

![Compte Azure avec propriétaire du compte Azure et administrateur général Azure AD](../../_images/govern/design/governance-3-0.png)
_Figure 1 : Un compte Azure avec un propriétaire du compte Azure et un administrateur général Azure AD._

## <a name="identity-management"></a>Gestion des identités

Azure utilise uniquement [Azure AD](https://docs.microsoft.com/azure/active-directory) pour authentifier les utilisateurs et autoriser l’accès utilisateur aux ressources. Azure AD est donc notre système de gestion d’identité. L’administrateur général Azure AD a le plus haut niveau d’autorisations et peut effectuer toutes les actions liées à l’identité, y compris la création d’utilisateurs et l’attribution d’autorisations.

Nous devons autoriser la gestion des identités pour un seul **propriétaire de charge de travail** qui est responsable du déploiement et la gestion de la charge de travail simple. Le propriétaire de la charge de travail requiert une autorisation pour créer, lire, mettre à jour et supprimer des ressources, ainsi que pour déléguer ces droits à d’autres utilisateurs dans le système de gestion d’identité.

Notre administrateur général Azure AD crée le compte de **propriétaire de la charge de travail** pour le propriétaire de la charge de travail :

![L’administrateur général Azure AD crée le compte du propriétaire de la charge de travail](../../_images/govern/design/governance-1-2.png)
_Figure 2 : L’administrateur général Azure AD crée le compte d’utilisateur du propriétaire de la charge de travail._

Vous ne pouvez pas assigner d’autorisation d’accès aux ressources tant que cet utilisateur n’a pas été ajouté à un **abonnement**. C’est donc ce que vous allez faire dans les deux sections suivantes.

## <a name="resource-management-scope"></a>Étendue de la gestion des ressources

Étant donné que le nombre de ressources déployées par votre organisation augmente, la complexité de la gouvernance des ressources augmente également. Azure implémente une hiérarchie de conteneur logique pour permettre à votre organisation de gérer vos ressources dans des groupes à différents niveaux de granularité, également appelée **étendue**.

Le niveau supérieur de l’étendue de gestion des ressources est le niveau **abonnement**. Un abonnement est créé par le **propriétaire du compte** Azure, qui établit l’engagement financier et est responsable du paiement de toutes les ressources Azure associées à l’abonnement :

![Le propriétaire du compte Azure crée un abonnement](../../_images/govern/design/governance-1-3.png)
_Figure 3 : Le propriétaire de compte Azure crée un abonnement._

Une fois l’abonnement créé, le **propriétaire du compte** Azure associe un client Azure AD à l’abonnement. Ce client Azure AD est utilisé pour authentifier et autoriser les utilisateurs :

![Le propriétaire du compte Azure associe l’abonné Azure AD à l’abonnement](../../_images/govern/design/governance-1-4.png)
_Figure 4 : Le propriétaire du compte Azure associe le client Azure AD à l’abonnement._

Vous avez peut-être remarqué qu’il n’y a actuellement aucun utilisateur associé à l’abonnement, ce qui signifie que personne n’est autorisé à gérer les ressources. En réalité, le **propriétaire du compte** est le propriétaire de l’abonnement et a l’autorisation d’agir sur une ressource dans l’abonnement. Toutefois, en pratique, le **propriétaire du compte** est probablement une personne de finances dans votre organisation et n’est pas responsable de la création, lecture, mise à jour et suppression de ressources. Ces tâches seront effectuées par le **propriétaire de la charge de travail**. Par conséquent, vous devez ajouter le **propriétaire de la charge de travail** à l’abonnement et lui attribuer des autorisations.

Dans la mesure où le **propriétaire du compte** est actuellement le seul utilisateur autorisé à ajouter le **propriétaire de la charge de travail** à l’abonnement, il doit ajouter le **propriétaire de la charge de travail** à l’abonnement :

![Le propriétaire du compte Azure ajoute le **propriétaire de la charge de travail** à l’abonnement](../../_images/govern/design/governance-1-5.png)
_Figure 5 : Le propriétaire du compte Azure ajoute le propriétaire de la charge de travail à l’abonnement._

Le **propriétaire du compte** Azure accorde des autorisations au **propriétaire de la charge de travail** en assignant un rôle de [Contrôle d’accès en fonction du rôle (RBAC)](https://docs.microsoft.com/azure/role-based-access-control). Le rôle RBAC spécifie un ensemble d’autorisations dont le **propriétaire de la charge de travail** dispose comme type de ressource individuelle ou ensemble de types de ressources.

Notez que dans cet exemple, le **propriétaire du compte** a attribué le [rôle de **propriétaire** intégré](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) :

![Le rôle de propriétaire intégré a été attribué au **propriétaire de la charge de travail**](../../_images/govern/design/governance-1-6.png)
_Figure 6 : Le rôle de propriétaire intégré a été attribué au propriétaire de la charge de travail._

Le rôle de **propriétaire** intégré accorde toutes les autorisations au **propriétaire de la charge de travail** pour l’étendue d’abonnement.

> [!IMPORTANT]
> Le **propriétaire de compte** Azure est responsable de l’engagement financier associé à l’abonnement, mais le **propriétaire de la charge de travail** dispose des mêmes autorisations. Le **propriétaire du compte** doit approuver le **propriétaire de la charge de travail** pour déployer des ressources comprises dans le budget de l’abonnement.

Le niveau suivant de l’étendue de la gestion est le niveau **groupe de ressources**. Un groupe de ressources est un conteneur logique pour ressources. Les opérations appliquées au niveau du groupe de ressources s’appliquent à toutes les ressources d’un groupe. En outre, il est important de noter que les autorisations pour chaque utilisateur sont héritées du niveau supérieur suivant, sauf si elles sont explicitement modifiées dans cette portée.

Pour illustrer ceci, nous allons examiner ce qui se passe lorsque le **propriétaire de la charge de travail** crée un groupe de ressources :

![Le **propriétaire de la charge de travail** crée un groupe de ressources](../../_images/govern/design/governance-1-7.png)
_Figure 7 : Le propriétaire de la charge de travail crée un groupe de ressources et hérite du rôle de propriétaire intégré pour l’étendue du groupe de ressources._

Là encore, le rôle de **propriétaire** intégré accorde toutes les autorisations au **propriétaire de la charge de travail** pour l’étendue du groupe de ressources. Comme indiqué précédemment, ce rôle est hérité du niveau d’abonnement. Si un rôle différent est attribué à cet utilisateur dans cette étendue, il s’applique à cette étendue uniquement.

Le niveau le plus bas de l’étendue de la gestion est le niveau **ressource**. Les opérations appliquées au niveau de la ressource s’appliquent uniquement à la ressource elle-même. Là encore, les autorisations au niveau de la ressource sont héritées de l’étendue du groupe de ressources. Par exemple, nous allons examiner ce qui se passe si le **propriétaire de la charge de travail** déploie un [réseau virtuel](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) dans le groupe de ressources :

![Le **propriétaire de la charge de travail** crée une ressource](../../_images/govern/design/governance-1-8.png)
_Figure 8 : Le propriétaire de la charge de travail crée une ressource et hérite du rôle de propriétaire intégré pour l’étendue de la ressource._

Le **propriétaire de la charge de travail** hérite du rôle de propriétaire au niveau de l’étendue d’une ressource, ce qui signifie que le propriétaire de la charge de travail dispose de toutes les autorisations pour le réseau virtuel.

## <a name="implement-the-basic-resource-access-management-model"></a>Implémenter le modèle de gestion d’accès aux ressources de base

Apprenons maintenant à implémenter le modèle de gouvernance conçu précédemment.

Pour commencer, votre organisation nécessite un compte Azure. Si votre organisation dispose déjà d’un [contrat entreprise Microsoft](https://www.microsoft.com/licensing/licensing-programs/enterprise) qui n’inclut pas Azure, Azure peut être ajouté en effectuant un engagement financier initial. Pour plus d’informations, consultez [Gestion des licences Azure pour l’entreprise](https://azure.microsoft.com/pricing/enterprise-agreement).

Lors de la création de votre compte Azure, vous devez spécifier une personne de votre organisation comme étant le **propriétaire du compte** Azure. Un client Azure Active Directory (Azure AD) est ensuite créé par défaut. Le **propriétaire du compte** Azure doit [créer le compte d’utilisateur](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory) de la personne **propriétaire de la charge de travail** de votre organisation.

Ensuite, le **propriétaire du compte** Azure doit [créer un abonnement](https://docs.microsoft.com/partner-center/create-a-new-subscription) et [associer le client Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) à cet abonnement.

Enfin, maintenant que l’abonnement est créé que le client Azure AD lui est associé, vous pouvez [ajouter le **propriétaire de la charge de travail** à l’abonnement intégré au **rôle de** propriétaire](https://docs.microsoft.com/azure/billing/billing-add-change-azure-subscription-administrator#to-assign-a-user-as-an-administrator).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déployer une charge de travail de base sur Azure](../../infrastructure/virtual-machines/basic-workload.md)

<!-- --->

> [!div class="nextstepaction"]
> [En savoir plus sur l’accès aux ressources pour plusieurs équipes](./governance-multiple-teams.md)
