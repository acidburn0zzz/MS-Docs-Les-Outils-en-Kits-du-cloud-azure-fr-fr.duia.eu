---
title: Comprendre la base de référence de la sécurité cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez la base de référence de la sécurité cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: dfb7969d19017c003ef961c18e87b8cb110ccd4e
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71032491"
---
# <a name="understand-the-cloud-security-baseline"></a>Comprendre la base de référence de la sécurité cloud

Cet article d’introduction présente le thème général de la base de référence de la sécurité, qui repose sur les [cinq disciplines de la gouvernance cloud](../governance-disciplines.md) pour établir un cadre de gouvernance. Des informations plus détaillées sur la sécurité du cloud sont disponibles dans le [cloud approuvé d’Azure](https://azure.microsoft.com/overview/trusted-cloud). Des approches pour améliorer l’état de sécurité de vos organisations sont disponibles dans le [catalogue des services de sécurité cloud](https://www.microsoft.com/security/information-protection).

> [!NOTE]
> Cet article n’a pas été conçu pour fournir le contexte nécessaire au lecteur pour qu’il puisse implémenter une stratégie de sécurité. Il cherche uniquement à familiariser le lecteur au sujet.

## <a name="cloud-security"></a>Sécurité cloud

La sécurité cloud est une extension des pratiques traditionnelles destinées à protéger les informations. La sécurité informatique traditionnelle englobe les stratégies et contrôles permettant de surveiller la sécurité des ordinateurs, la sécurité du réseau, la protection des données, l’utilisation des informations, etc. Ces mêmes stratégies et contrôles sont nécessaires dans le cloud. Pendant la transformation cloud, il est impératif que le responsable de la sécurité des systèmes soit activement impliqué et qu’il comprenne le paysage cloud, afin de s’assurer que les stratégies informatiques héritées sont mappées à des niveaux de contrôle corrects dans le cloud.

Toute stratégie de sécurité cloud doit au moins prendre en compte les points suivants :

- **Classification des données.** Une classification correcte des données est nécessaire pour comprendre toutes les sources de données privées, protégées ou hautement confidentielles. Elle vous aide à gérer les risques pendant la planification.
- **Planification d’un scénario de cloud hybride.** Comprendre comment les réseaux locaux hérités se connecteront au cloud aide le chef de la sécurité des systèmes à identifier et éliminer les risques.
- **Planification des attaques et des erreurs.** Durant les premiers mois d’une transformation, l’équipe apprendra tout en faisant des erreurs. Commencez par des déploiements avec peu de risques et hautement restreints pour apprendre en toute sécurité.
- **Hiérarchisation de la confidentialité.** Pendant la transformation, toute l’équipe doit mettre la vie privée des clients et des employés au cœur de ses préoccupations. Dans le cloud, vos données sont protégées. Toutefois, l’équipe doit faire particulièrement attention lorsqu’elle s’occupe de données sensibles.

## <a name="protecting-data-and-privacy"></a>Protection des données et de la confidentialité

Pour les organisations du monde entier, que ce soit pour les gouvernements, les organismes à but non lucratif ou les entreprises, le cloud computing est désormais un composant essentiel de la stratégie informatique. Les services cloud permettent aux organisations de toutes tailles de bénéficier d’un stockage de données quasiment illimité, tout en leur évitant d’avoir à acheter, entretenir et mettre à jour leurs propres réseaux et systèmes informatiques. Microsoft et d’autres fournisseurs de cloud offrent une infrastructure informatique, une plateforme et un service SaaS (software as a service), qui permettent aux clients de faire évoluer à la hausse ou à la baisse rapidement, et de ne payer que pour la puissance informatique et le stockage qu’ils utilisent.

Toutefois, si les organisations continuent de profiter des avantages des services cloud (plus de choix, d’agilité et de flexibilité, stimulation de l’efficacité, et réduction des coûts informatiques), elles doivent également se rendre compte que l’introduction des services cloud nuit à la confidentialité, la sécurité et la conformité. Microsoft s’est efforcé de proposer des offres cloud non seulement évolutives, fiables et gérables, mais également capables d’assurer la protection et l’utilisation des données client de manière transparente.

La sécurité est un composant essentiel dans la protection robuste des données, pour tous les environnements informatiques en ligne. Toutefois, la sécurité à elle toute seule n’est pas suffisante. La volonté des clients et des entreprises à utiliser un produit de cloud computing en particulier dépend également de la capacité du client ou de l’entreprise à croire que la confidentialité de leurs informations sera préservée par ce produit, et que leurs données seront uniquement utilisées conformément à leurs attentes. Apprenez-en davantage sur l’approche de Microsoft en matière de [protection des données et confidentialité dans le cloud ](https://go.microsoft.com/fwlink/?LinkId=808242&clcid=0x409).

## <a name="risk-mitigation"></a>Atténuation des risques

Les deux risques principaux dans un centre de données peuvent provenir de deux sources différentes : le vieillissement des systèmes et les erreurs humaines. Lors de la définition d’une stratégie de sécurité informatique, le minimum est de se protéger contre ces deux risques. Et c’est exactement la même chose dans le cloud. Voici quelques exemples de contrôles que vous pouvez mettre en place pour résoudre les risques et renforcer votre stratégie de sécurité cloud.

- **Systèmes hérités :** Beaucoup de composants dans les centres de données locaux sont des logiciels, du matériel et des processus antérieurs aux risques de sécurité actuels. Si possible, corrigez, remplacez ou retirez ces systèmes lors d’une transformation cloud. Bien sûr, ce n’est pas toujours possible. Si les systèmes hérités restent en production dans une solution hybride, il est important que ces systèmes soient inventoriés et pris en compte lors de la conception d’un centre de données virtuel. Ainsi, l’équipe de conception peut éliminer ou contrôler l’accès à ces systèmes à partir du cloud.
- **Contrôles et processus de sécurité informatique :** Au minimum, les équipes de conception cloud doivent être informées des processus et contrôles de sécurité informatique existants, afin de les transférer dans le cloud. Dans un scénario idéal, un membre de l’équipe de sécurité informatique est formé en cyber-sécurité, et fait également partie (en tant que membre) des équipes de conception et d’implémentation.
- **Supervision et audit :** Lors de la conception des processus et des outils de gouvernance, assurez-vous que les solutions de supervision et d’audit prennent en compte les risques et les violations de sécurité.

> [!NOTE]
> **Divulgation de la dette technique :** Ce sujet ne dispose pas de prochaines étapes exploitables. D’autres articles aborderont ce sujet plus tard. Des informations plus détaillées sur la sécurité du cloud sont disponibles dans le [cloud approuvé d’Azure](https://azure.microsoft.com/overview/trusted-cloud). Des approches pour améliorer l’état de sécurité de vos organisations sont disponibles dans le [catalogue des services de sécurité cloud](https://www.microsoft.com/security/information-protection).
