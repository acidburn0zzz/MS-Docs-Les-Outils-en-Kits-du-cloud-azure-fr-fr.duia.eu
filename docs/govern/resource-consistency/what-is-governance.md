---
title: Qu’est-ce que la gouvernance des ressources cloud ?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Fonctionnement de la gouvernance des ressources cloud sur Azure
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 083b18c0c8c5edc0dc21a198df32e8934929299c
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71032185"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-cloud-resource-governance"></a>Qu’est-ce que la gouvernance des ressources cloud ?

Dans l’article [Fonctionnement d’Azure](../../getting-started/what-is-azure.md), vous avez appris qu’Azure est une collection de serveurs et de matériel réseau sur lesquels fonctionnent du matériel virtualisé et des logiciels pour le compte des utilisateurs. Azure garantit l’agilité des services informatiques et de développement d’applications de votre organisation en les aidant à créer, lire, mettre à jour et supprimer des ressources en fonction de leurs besoins.

Toutefois, même si l’accès illimité aux ressources peut rendre les développeurs plus agiles, il peut également générer des coûts imprévus. Par exemple, une équipe de développement peut être autorisée à déployer un ensemble de ressources à des fins de test mais oublier de les supprimer une fois les tests terminés. Ces ressources continueront d’engendrer des coûts, même si elles ne sont plus autorisées ou nécessaires.

La solution est la gouvernance de l’accès aux ressources. La **gouvernance** consiste à gérer, superviser et auditer en continu l’utilisation des ressources Azure afin d’atteindre les objectifs et de satisfaire aux exigences de votre organisation.

<!-- markdownlint-disable MD034 -->

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE2ii94]

<!-- markdownlint-enable MD034 -->

Ces exigences étant propres à chaque organisation, une approche unique de la gouvernance n’est pas utile. Au lieu de cela, il appartient à chaque organisation de concevoir son propre modèle de gouvernance à l’aide des deux principaux outils de gouvernance d’Azure : le **contrôle d’accès en fonction du rôle (RBAC)** et la **stratégie de ressources**.

Le RBAC définit des rôles, qui eux-mêmes définissent les opérations autorisées pour chaque utilisateur est attribué à ces rôles. Par exemple, le rôle **propriétaire** autorise toutes les opérations (créer, lire, mettre à jour et supprimer) sur une ressource, tandis que le rôle **lecteur** autorise uniquement les opérations de lecture. Les rôles peuvent être définis globalement et appliqués à de nombreux types de ressources, ou définis de manière plus restrictive et appliqués à seulement quelques types de ressources.

Les stratégies de ressources définissent des règles pour la création de ressources. Par exemple, une stratégie de ressources peut limiter la référence SKU d’une machine virtuelle à une taille pré-approuvée particulière. Une autre stratégie de ressources peut imposer l’application d’une étiquette pour un centre de coûts au moment de la demande de création de la ressource.

Lors de la configuration de ces outils, il est important de trouver un équilibre entre la gouvernance et l’agilité organisationnelle. Plus votre stratégie de gouvernance sera restrictive, moins vos développeurs et vos ingénieurs informatiques seront agiles. Une stratégie de gouvernance restrictive peut impliquer davantage d’étapes manuelles, comme exiger d’un développeur de remplir un formulaire ou d’envoyer un e-mail à un membre de l’équipe de gouvernance pour créer manuellement une ressource. L’équipe de gouvernance a des capacités limitées et peut devenir un goulot d’étranglement. Résultat : en attendant que leurs ressources soient créées, les équipes de développement ne sont plus productives, ou les ressources inutiles entraînent une augmentation des coûts avant d’être supprimées.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous comprenez le concept de gouvernance des ressources cloud, poursuivez en découvrant comment l’accès aux ressources est géré dans Azure.

> [!div class="nextstepaction"]
> [En savoir plus sur l’accès aux ressources dans Azure](./resource-access-management.md)
