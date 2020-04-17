---
title: Exemples de déclarations de stratégie Base de référence des identités
description: Utilisez le Framework d’adoption du cloud pour Azure pour obtenir des exemples de déclarations de stratégie de base de référence des identités qui peuvent vous aider à élaborer des déclarations de stratégie.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: c3543299d323c8be6bf7ee88d6e9205c307e24f9
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80997435"
---
# <a name="identity-baseline-sample-policy-statements"></a>Exemples de déclarations de stratégie Base de référence des identités

Les instructions de stratégie cloud individuelles sont des recommandations destinées à traiter des risques spécifiques identifiés lors de votre processus d’évaluation des risques. Ces instructions doivent fournir un bref récapitulatif des risques, ainsi que des plans établis pour les gérer. Chaque définition d’instruction doit inclure les informations suivantes :

- **Risque technique :** un récapitulatif du risque que cette stratégie gérera.
- **Instruction de stratégie :** Une explication succincte claire des exigences de la stratégie.
- **Options de conception :** Recommandations exploitables, spécifications ou autres conseils que des équipes informatiques et des développeurs peuvent utiliser lors de l’implémentation de la stratégie.

Les exemples d’instructions de stratégie suivants traitent des risques courants liés à l’identité. Ces énoncés sont des exemples que vous pouvez référencer lorsque vous rédigez des énoncés de stratégie pour répondre aux besoins de votre organisation. Ces exemples ne sont pas destinés à être normatifs, et il existe potentiellement plusieurs options de stratégie pour gérer chaque risque identifié. Travaillez en étroite collaboration avec les équipes métier et les équipes informatiques pour identifier les meilleures stratégies pour vos propres risques.

## <a name="lack-of-access-controls"></a>Absence de contrôles d'accès

**Risque technique :** des paramètres de contrôle d’accès insuffisants ou ad hoc peuvent introduire un risque d’accès non autorisé à des ressources sensibles ou stratégiques.

**Instruction de stratégie :** Toutes les ressources déployées dans le cloud doivent être contrôlées à l’aide d’identités et de rôles approuvés par les stratégies de gouvernance en vigueur.

**Options de conception potentielles** : l'[Accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) est le mécanisme de contrôle d'accès par défaut dans Azure.

## <a name="overprovisioned-access"></a>Accès surapprovisionné

**Risque technique :** les utilisateurs et les groupes qui contrôlent des ressources situées au-delà de leur domaine de responsabilité peuvent provoquer des modifications non autorisées conduisant à des pannes ou à des vulnérabilités en matière de sécurité.

**Instruction de stratégie :** les stratégies suivantes seront implémentées :

- Un modèle d’accès à privilège minimum sera appliqué à toutes les ressources impliquées dans des applications stratégiques ou des données protégées.
- Les autorisations élevées doivent rester une exception, et toute exception de ce type doit être communiquée à l’équipe de gouvernance cloud. Les exceptions seront régulièrement vérifiées.

**Options de conception potentielles** : consultez les [Meilleures pratiques d’Azure Identity Management](https://docs.microsoft.com/azure/security/fundamentals/identity-management-best-practices) pour implémenter une stratégie de contrôle d’accès en fonction du rôle (RBAC) qui restreint l’accès selon les principes [à savoir](https://wikipedia.org/wiki/Need_to_know) et [sécurité à privilège minimum](https://wikipedia.org/wiki/Principle_of_least_privilege).

## <a name="lack-of-shared-management-accounts-between-on-premises-and-the-cloud"></a>Absence de comptes de gestion partagés entre l'infrastructure locale et le cloud

**Risque technique :** Les membres du personnel de gestion ou d’administration informatique qui possèdent un compte au sein de votre infrastructure Active Directory locale peuvent ne pas disposer d’un accès suffisant aux ressources cloud et ne pas pouvoir résoudre efficacement les problèmes opérationnels ou de sécurité.

**Instruction de stratégie :** Tous les groupes de l’infrastructure Active Directory locale qui disposent de privilèges élevés doivent être mappés vers un rôle RBAC approuvé.

**Options de conception potentielles** : implémentez une solution d’identité hybride entre votre infrastructure Azure Active Directory basée sur le cloud et votre infrastructure Active Directory locale, et ajoutez les groupes locaux requis aux rôles RBAC nécessaires pour leur permettre d’accomplir leur travail.

## <a name="weak-authentication-mechanisms"></a>Mécanismes d'authentification faibles

**Risque technique :** lorsque les systèmes de gestion des identités utilisent des méthodes d'authentification des utilisateurs qui ne sont pas suffisamment sécurisées (combinaisons utilisateur/mot de passe de base, par exemple), les mots de passe peuvent être compromis ou piratés, ce qui représente un risque majeur d'accès non autorisé aux systèmes cloud sécurisés.

**Instruction de stratégie :** tous les comptes sont tenus de se connecter aux ressources sécurisées à l’aide d’une méthode d’authentification multifacteur.

**Options de conception potentielles** : pour Azure Active Directory, implémentez [Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) dans le cadre de votre processus d'autorisation utilisateur.

## <a name="isolated-identity-providers"></a>Fournisseurs d'identité isolés

**Risque technique :** des fournisseurs d'identité incompatibles peuvent empêcher le partage de ressources ou de services avec des clients ou d'autres partenaires commerciaux.

**Instruction de stratégie :** Le déploiement des applications nécessitant une authentification des clients doit utiliser un fournisseur d'identité approuvé compatible avec le fournisseur d'identité principal pour les utilisateurs internes.

**Options de conception potentielles** : implémentez une [fédération avec Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-fed) entre vos fournisseurs d’identité interne et client ou utilisez [Azure Active Directory B2B](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b).

## <a name="identity-reviews"></a>Révisions des identités

**Risque technique :** à mesure que l’activité évolue, l’ajout de nouveaux déploiements dans le cloud ou l’apparition d’autres problèmes de sécurité peut accroître les risques d’accès non autorisé à des ressources sécurisées.

**Instruction de stratégie :** les processus de gouvernance cloud doivent inclure des révisions trimestrielles avec les équipes de gestion des indentés. L'objectif est d'identifier les modèles d'utilisation ou les acteurs malveillants devant être bloqués par la configuration des ressources cloud.

**Options de conception potentielles** : tous les trimestres, organisez une réunion destinée à la révision de la sécurité avec les membres de l'équipe de gouvernance et le personnel informatique chargé de la gestion des services d'identité. Passez en revue les données et les métriques de sécurité existantes pour déterminer les lacunes de la stratégie et des outils de gestion des identités actuels, ainsi que pour mettre à jour la stratégie afin de limiter les nouveaux risques éventuels.

## <a name="next-steps"></a>Étapes suivantes

Utilisez les exemples mentionnés dans cet article comme point de départ pour développer des stratégies qui répondent à des risques métier spécifiques, dans la continuité de vos plans d’adoption du cloud.

Pour commencer à développer vos déclarations de stratégie personnalisées pour la Base de référence des identités, téléchargez le [modèle Base de référence des identités](./template.md).

Pour accélérer l’adoption de cette discipline, choisissez le [guide de gouvernance actionnable](../guides/index.md) correspondant le mieux à votre environnement. Modifiez ensuite la conception pour intégrer vos décisions spécifiques en matière de stratégie d’entreprise.

Sur la base des risques et de la tolérance, établissez un processus de gouvernance et de communication en lien avec l’adhésion à la stratégie Base de référence des identités.

> [!div class="nextstepaction"]
> [Établir des processus de conformité à la stratégie](./compliance-processes.md)
