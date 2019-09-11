---
title: Recommandation en matière de contrôle d’accès en fonction du rôle
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Recommandation en matière de contrôle d’accès en fonction du rôle
author: rotycenh
ms.author: brblanch
ms.date: 11/28/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: BrianBlanchard
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: 897b6f3f5d3c506cc79050dd3453e30b677382b1
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70839151"
---
# <a name="role-based-access-control"></a>Contrôle d’accès en fonction du rôle

Les droits d’accès et les privilèges en fonction du groupe sont une bonne pratique. Le traitement des groupes plutôt que des utilisateurs individuels simplifie la maintenance des stratégies d’accès, offre une gestion cohérente des accès entre les équipes et réduit les erreurs de configuration. L’attribution et la suppression d’utilisateurs dans les groupes appropriés facilitent l’actualisation continue des privilèges d’un utilisateur spécifique. Le [contrôle d’accès en fonction du rôle (RBAC)](/azure/role-based-access-control/overview) Azure offre une gestion précise de l’accès aux ressources et organisée autour des rôles d’utilisateur.

Pour obtenir une vue d’ensemble des pratiques RBAC recommandées dans le cadre d’une stratégie d’identité et de sécurité, consultez les [meilleures pratiques en matière de sécurité du contrôle d’accès et de gestion des identités Azure](/azure/security/azure-security-identity-management-best-practices#use-role-based-access-control).

## <a name="overview-of-role-based-access-control"></a>Vue d’ensemble du contrôle d’accès en fonction du rôle

À l’aide du [contrôle d’accès en fonction du rôle](/azure/role-based-access-control/overview), vous pouvez séparer les tâches au sein de votre équipe et n’accorder qu’un accès suffisant pour des utilisateurs, groupes, principaux de service ou identités managées Azure Active Directory (Azure AD) spécifiques pour effectuer leurs tâches. Plutôt que de donner à tous un accès illimité à votre abonnement ou à vos ressources Azure, vous pouvez limiter les autorisations pour chaque ensemble de ressources.

Les [définitions de rôle RBAC](/azure/role-based-access-control/role-definitions) répertorient les opérations autorisées ou non autorisées pour les utilisateurs ou les groupes affectés à ce rôle. L’[étendue](/azure/role-based-access-control/overview#scope) d’un rôle spécifie les ressources auxquelles ces autorisations définies s’appliquent. Les étendues peuvent être spécifiées à plusieurs niveaux : groupe d’administration, abonnement, groupe de ressources ou ressource. Les étendues sont structurées dans une relation parent-enfant.

![Hiérarchie d’étendues RBAC](./images/rbac-scope.png)

Pour obtenir des instructions détaillées sur l’affectation d’utilisateurs et de groupes à des rôles spécifiques et l’attribution de rôles à des étendues, consultez [Gérer l’accès aux ressources Azure à l’aide du RBAC](/azure/role-based-access-control/role-assignments-portal).

Lorsque vous planifiez votre stratégie de contrôle d’accès, utilisez un modèle d’accès basé sur le privilège minimum qui accorde uniquement aux utilisateurs les autorisations requises pour effectuer leur travail. Le diagramme suivant illustre une suggestion de modèle pour l’utilisation du RBAC par le biais de cette approche.

![Modèle suggéré pour l’utilisation du RBAC](./images/rbac-least-privilege.png)

> [!NOTE]
> Plus les autorisations que vous définissez sont spécifiques ou détaillées, plus il est probable que vos contrôles d’accès deviennent complexes et difficiles à gérer. Cela est particulièrement vrai lorsque la taille de votre parc cloud augmente. Évitez les autorisations spécifiques aux ressources. Au lieu de cela, [utilisez des groupes d’administration](/azure/governance/management-groups) pour un contrôle d’accès au niveau de l’entreprise et des [groupes de ressources](/azure/azure-resource-manager/resource-group-overview#resource-groups) pour un contrôle d’accès au sein d’abonnements. Évitez également les autorisations spécifiques à des utilisateurs. Au lieu de cela, attribuez l’accès à des [groupes dans Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups).

## <a name="using-built-in-rbac-roles"></a>Utilisation des rôles RBAC intégrés

Azure fournit de nombreuses définitions de rôle intégrées, avec trois rôles principaux pour fournir l’accès :

- Le rôle [Propriétaire](/azure/role-based-access-control/built-in-roles#owner) peut tout gérer, y compris l’accès aux ressources.
- Le rôle [Contributeur](/azure/role-based-access-control/built-in-roles#contributor) peut tout gérer, sauf l’accès aux ressources.
- Le rôle [Lecteur](/azure/role-based-access-control/built-in-roles#reader) peut tout afficher, mais ne peut apporter aucune modification.

À partir de ces niveaux d’accès de base, des rôles intégrés supplémentaires fournissent des contrôles plus détaillés pour accéder à des types de ressources spécifiques ou à des fonctionnalités Azure. Par exemple, vous pouvez gérer l’accès aux machines virtuelles à l’aide des rôles intégrés suivants :

- Le rôle [Connexion de l’administrateur aux machines virtuelles](/azure/role-based-access-control/built-in-roles#virtual-machine-administrator-login) peut afficher les machines virtuelles dans le portail et se connecter en tant qu’_administrateur_.
- Le rôle [Contributeur de machines virtuelles](/azure/role-based-access-control/built-in-roles#virtual-machine-contributor) peut gérer des machines virtuelles, mais ne peut pas accéder à ces dernières, au réseau virtuel ni au compte de stockage auquel elles sont connectées.
- Le rôle [Connexion de l’utilisateur aux machines virtuelles](/azure/role-based-access-control/built-in-roles#virtual-machine-user-login) peut afficher les machines virtuelles dans le portail et se connecter en tant qu’utilisateur standard.

Pour obtenir un autre exemple d’utilisation des rôles intégrés pour gérer l’accès à des fonctionnalités spécifiques, consultez la discussion sur le contrôle de l’accès aux fonctionnalités de suivi des coûts dans [Suivi des coûts dans les unités commerciales, les environnements ou les projets](./track-costs.md#provide-the-right-level-of-cost-access).

Pour obtenir la liste complète des rôles intégrés disponibles, consultez [Rôles intégrés pour les ressources Azure](/azure/role-based-access-control/built-in-roles).

## <a name="using-custom-roles"></a>Utilisation de rôles personnalisés

Bien que les rôles intégrés à Azure prennent en charge un large éventail de scénarios de contrôle d’accès, ils peuvent ne pas répondre à tous les besoins de votre organisation ou équipe. Par exemple, si vous avez un seul groupe d’utilisateurs responsable de la gestion des machines virtuelles et des ressources Azure SQL Database, vous voudrez peut-être créer un rôle personnalisé pour optimiser la gestion des contrôles d’accès requis.

La documentation Azure RBAC contient des instructions sur la [création de rôles personnalisés](/azure/role-based-access-control/custom-roles), ainsi que des détails sur le [fonctionnement des définitions de rôle](/azure/role-based-access-control/role-definitions).

## <a name="separation-of-responsibilities-and-roles-for-large-organizations"></a>Séparation des responsabilités et des rôles pour les grandes organisations

RBAC permet aux organisations d’affecter différentes équipes à diverses tâches de gestion au sein de grands parcs cloud. Il permet aux équipes informatiques centrales de contrôler les fonctionnalités principales d’accès et de sécurité, tout en permettant aux développeurs de logiciels et aux autres équipes d’avoir un grand contrôle sur des charges de travail ou groupes de ressources spécifiques.

La plupart des environnements cloud peuvent également bénéficier d’une stratégie de contrôle d’accès qui utilise plusieurs rôles et met l’accent sur une séparation des responsabilités entre ces rôles. Cette approche nécessite que toute modification significative des ressources ou de l’infrastructure implique la réalisation de plusieurs rôles, de sorte que plusieurs personnes doivent passer en revue et approuver une modification. Cette séparation des responsabilités limite la capacité d’une seule personne à accéder à des données sensibles ou à introduire des vulnérabilités à l’insu des autres membres de l’équipe.

Le tableau suivant illustre un modèle commun de séparation des responsabilités informatiques en rôles personnalisés distincts :

<!-- markdownlint-disable MD033 -->

| Groupe | Nom du rôle commun | Responsabilités |
| --- | --- | --- |
| Opérations de sécurité | Responsables des opérations de sécurité | Fournit un aperçu général de la sécurité.<br/><br/> Établit et applique la stratégie de sécurité, comme le chiffrement au repos.<br/><br/> Gère les clés de chiffrement.<br/><br/> Gère les règles de pare-feu. |
| Opérations réseau | NetOps | Gère la configuration et les opérations du réseau au sein de réseaux virtuels, tels que les itinéraires et les Peerings. |
| Opérations systèmes | SysOps | Spécifie les options d’infrastructure de calcul et de stockage et gère les ressources qui ont été déployées. |
| Développement, test et opérations | DevOps | Génère et déploie des fonctionnalités de charge de travail et des applications.<br/><br/> Utilise des fonctionnalités et des applications pour répondre aux contrats de niveau de service (SLA) et à d’autres standards de qualité. |

<!-- markdownlint-enable MD033 -->

La décomposition des actions et des autorisations dans ces rôles standard est souvent identique dans vos applications, vos abonnements ou l’ensemble du parc cloud, même si ces rôles sont exécutés par différentes personnes à différents niveaux. En conséquence, vous pouvez créer un ensemble commun de définitions de rôle RBAC à appliquer sur différentes étendues au sein de votre environnement. Les utilisateurs et les groupes peuvent ensuite se voir attribuer un rôle commun, mais uniquement pour l’étendue des ressources, des groupes de ressources, des abonnements ou des groupes d’administration qu’ils sont chargés de gérer.

Par exemple, dans une [configuration de réseau hub-and-spoke](./hub-spoke-network-topology.md) avec plusieurs abonnements, vous pouvez avoir un ensemble commun de définitions de rôle pour le hub et tous les spokes de charge de travail. Le rôle NetOps d’un abonnement hub peut être attribué aux membres du personnel informatique central de l’organisation, qui sont chargés de gérer la mise en réseau pour les services partagés utilisés par toutes les charges de travail. Le rôle NetOps d’un abonnement spoke de charge de travail peut ensuite être attribué aux membres de cette équipe de charge de travail spécifique, ce qui leur permet de configurer la mise en réseau au sein de cet abonnement pour prendre en charge au mieux leurs exigences en matière de charge de travail. La même définition de rôle est utilisée pour les deux, mais les attributions basées sur l’étendue garantissent que les utilisateurs disposent uniquement de l’accès dont ils ont besoin pour effectuer leur travail.
