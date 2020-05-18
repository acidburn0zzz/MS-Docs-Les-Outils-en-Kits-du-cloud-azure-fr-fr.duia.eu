---
title: Fonction de gestion des identités et des clés dans le cloud
description: Comprendre la fonction de gestion des identités et des clés dans le cloud.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: b23cc2be9398a3512de95b5e2312b30764de8695
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230257"
---
# <a name="function-of-identity-and-key-management-in-the-cloud"></a>Fonction de gestion des identités et des clés dans le cloud

L’objectif principal d’une équipe de sécurité travaillant à la gestion des identités est d’assurer l’authentification et l’autorisation des êtres humains, des services, des appareils et des applications. La gestion des clés et des certifications offre une distribution et un accès sécurisés au éléments de clé pour les opérations de chiffrement (qui soutiennent souvent des résultats similaires à la gestion des identités).

## <a name="modernization"></a>Modernisation

La modernisation de l’identité des données et de la gestion des clés est façonnée par les facteurs suivants :

- Les disciplines de gestion des identités et des clés, ainsi que des certifications se rapprochent car elles fournissent toutes deux des garanties d’authentification et d’autorisation pour permettre des communications sécurisées.
- Des contrôles d’identité émergent en tant que périmètre de sécurité principal pour les applications cloud.
- L’authentification basée sur des clés pour des services cloud est remplacée par la gestion des identités en raison de la difficulté de stocker et de fournir de façon sécurisée un accès à ces clés.
- Il est essentiel de transmettre les leçons positives tirées des architectures d’identité locales, telles que l’identité unique, l’authentification unique (SSO) et l’intégration d’application native.
- Il est essentiel d’éviter des erreurs courantes des architectures locales qui les compliquent souvent à l’extrême, rendant le support difficile et facilitant les attaques. Ces erreurs sont les suivantes :
  - Prolifération des groupes et des unités d’organisation (UO).
  - Prolifération des annuaires tiers et des systèmes de gestion des identités.
  - Absence de clarté en lien avec la normalisation et la propriété de la stratégie d’identité d’application.
- Les attaques par vol d’informations d’identification continuent d’avoir un impact élevé et de constituer une menace hautement probable à atténuer.
- Les comptes de service et les comptes d’application restent un défi majeur, mais deviennent plus faciles à résoudre. Les équipes en charge de la gestion des identités doivent adopter activement les fonctionnalités cloud qui commencent à résoudre ces problèmes, comme les [identités managées Azure AD](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).

## <a name="team-composition-and-key-relationships"></a>Composition d’équipe et relations clés

Les équipes en charge de la gestion des identités et des clés doivent établir des relations fortes avec les rôles suivants :

- Architecture et opérations informatiques
- Architecture et opérations de sécurité
- Équipes chargées du développement
- Équipes chargées de la sécurité des données
- Équipes chargées de la confidentialité
- Équipes juridiques
- Équipes de gestion de la conformité et des risques

## <a name="next-steps"></a>Étapes suivantes

Examinez la fonction de [sécurité d’infrastructure et de point de terminaison](./cloud-security-infrastructure-endpoint.md).
