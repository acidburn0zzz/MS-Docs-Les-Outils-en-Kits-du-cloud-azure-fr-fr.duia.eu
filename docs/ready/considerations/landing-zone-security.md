---
title: Améliorer la sécurité des zones d’atterrissage
description: Améliorer la sécurité des zones d’atterrissage
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: be340d1566fce58012cd63c6efc90fd2e0636260
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81122018"
---
<!-- cSpell:ignore SIEM -->

# <a name="improve-landing-zone-security"></a>Améliorer la sécurité des zones d’atterrissage

Lorsque les charges de travail, ou la zone d’atterrissage dans laquelle elles sont hébergées, requièrent un accès à des données sensibles ou à des systèmes critiques, il est important de protéger les données et les ressources. L’amélioration de la sécurité de la zone d’atterrissage s’appuie sur une [approche de développement pilotée par les tests pour les zones d’atterrissage](./test-driven-development.md), qui consiste à développer ou refactoriser la zone d’atterrissage afin de tenir compte des exigences de sécurité accrues.

## <a name="landing-zone-security-best-practices"></a>Meilleures pratiques de sécurité pour la zone d’atterrissage

La liste suivante d’architectures de référence et de meilleures pratiques contient des exemples de méthodes pour améliorer la sécurité de la zone d’atterrissage :

- [Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-get-started?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) : Intégrer un abonnement à Security Center.
- [Azure Sentinel](https://docs.microsoft.com/azure/sentinel/quickstart-onboard?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) : Onboard Azure Sentinel est une solution de type **SIEM (Security Information and Event Management)** et **SOAR (Security Orchestrated Automated Response)** .
- [Sécurité des limites du réseau](../../reference/networking-vdc.md) : Plusieurs modèles de référence pour le développement d’un réseau, de la même façon que la limite réseau est sécurisée dans un centre de données.
- [Architecture réseau sécurisée](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) : Architecture de référence pour l’implémentation d’une zone démilitarisée et d’une architecture réseau sécurisée.
- [Gestion des identités et contrôle des accès](https://docs.microsoft.com/azure/security/fundamentals/identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) : Série de meilleures pratiques pour l’implémentation de l’identité et de l’accès pour sécuriser une zone d’atterrissage dans Azure.
- [Meilleures pratiques en matière de sécurité réseau](https://docs.microsoft.com/azure/security/fundamentals/network-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) : Fournit d’autres meilleures pratiques pour sécuriser le réseau.
- La [sécurité opérationnelle](https://docs.microsoft.com/azure/security/fundamentals/operational-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) fournit les meilleures pratiques pour l’amélioration de la sécurité opérationnelle dans Azure.
- [Base de référence de sécurité](../../govern/guides/complex/security-baseline-improvement.md#incremental-improvement-of-the-best-practices) : Exemple de développement d’une base de référence de sécurité basée sur la gouvernance pour appliquer les conditions de sécurité.

## <a name="test-driven-development-cycle"></a>Cycle de développement piloté par les tests

Avant de commencer à apporter des améliorations à la sécurité, il est important de comprendre la « définition de terminé » et tous les « critères d’acceptation ». Pour plus d’informations, consultez les articles sur [le développement piloté par test des zones d’atterrissage](./test-driven-development.md) et [le développement piloté par les tests dans Azure](./azure-test-driven-development.md).

![Processus de développement piloté par les tests pour les zones d’atterrissage cloud](../../_images/ready/test-driven-development-process.png)

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [améliorer les opérations de zone d’atterrissage](./landing-zone-operations.md) pour prendre en charge les applications critiques.

> [!div class="nextstepaction"]
> [Améliorer les opérations de zone d’atterrissage](./landing-zone-operations.md)
