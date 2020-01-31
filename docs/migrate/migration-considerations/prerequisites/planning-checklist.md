---
title: Check-list de planification de l’environnement de migration
description: Valider la préparation de l’environnement avant la migration
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 2660c6f09924c907591c8c8635b943125d0ac9a1
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76801407"
---
# <a name="migration-environment-planning-checklist-validate-environmental-readiness-prior-to-migration"></a>Check-list de planification de l’environnement de migration : valider la préparation de l’environnement avant la migration

En première étape du processus de migration, vous devez créer l’environnement approprié dans le cloud pour recevoir, héberger et prendre en charge la migration des ressources. Cet article fournit une liste des éléments à valider dans l’environnement actuel avant la migration.

La check-list suivante s’aligne sur les instructions fournies dans la [section Prêt](../../../ready/index.md) du Framework d’adoption du cloud. Consultez cette section pour obtenir des instructions concernant l’exécution des éléments suivants.

## <a name="effort-type-assumption"></a>Hypothèse relative au type d’effort

Cet article et cette check-list adoptent une approche de _réhébergement_ ou de _transition cloud_ pour la migration cloud.

## <a name="governance-alignment"></a>Alignement de la gouvernance

La première décision, qui est aussi et la plus importante, concernant n’importe quel environnement prêt à la migration est le choix de l’alignement de la gouvernance. Un consensus a-t-il été atteint en ce qui concerne l’alignement de la gouvernance avec la base de la migration ? Au minimum, l’équipe chargée de l’adoption du cloud doit déterminer si cette migration est accueillie dans un seul environnement avec une gouvernance limitée, une fabrique d’environnements avec une gouvernance complète ou une variante intermédiaire. Pour plus d’options et de conseils sur l’alignement de la gouvernance, consultez l’article relatif à l’[alignement de la gouvernance et la conformité](../../expanded-scope/governance-or-compliance.md).

## <a name="cloud-readiness-implementation"></a>Implémentation de la préparation au cloud

Que vous choisissiez d’aligner votre migration initiale sur une stratégie de gouvernance du cloud plus large ou non, vous devez vous assurer que votre environnement de déploiement cloud est configuré de façon à prendre en charge vos charges de travail.

Si vous envisagez d’aligner votre migration sur une stratégie de gouvernance du cloud dès le départ, vous devez appliquer les [cinq disciplines de la gouvernance du cloud](../../../govern/governance-disciplines.md) pour vous aider à prendre des décisions éclairées en matière de stratégies, chaînes d’outils et mécanismes de mise en conformité. Cela permettra d’aligner votre environnement cloud sur les exigences globales de l’entreprise. Pour obtenir des exemples d’implémentation de ce modèle à l’aide des services Azure, consultez les [guides actionnables de conception de gouvernance](../../../govern/guides/index.md) du Framework d’adoption du cloud.

Si vos migrations initiales ne sont pas étroitement alignées sur une stratégie de gouvernance cloud plus large, les problèmes généraux liés à l’organisation, à l’accès et à la planification de l’infrastructure doivent tout de même être managés. Consultez le [guide de configuration Azure](../../../ready/azure-setup-guide/index.md) pour obtenir de l’aide concernant ces décisions en matière de préparation au cloud.

> [!CAUTION]
> Nous vous recommandons vivement de développer une stratégie de gouvernance pour tout ce qui va au-delà de la migration initiale de vos charges de travail.

Quel que soit votre niveau d’alignement de la gouvernance, vous devrez prendre des décisions concernant les sujets suivants.

### <a name="resource-organization"></a>Organisation des ressources

En fonction du choix d’alignement de la gouvernance, une approche de l’organisation et du déploiement des ressources doit être établie avant la migration.

### <a name="nomenclature"></a>Nomenclature

Une approche cohérente de dénomination des ressources ainsi que des schémas de nommage structurés doivent être établis avant la migration.

### <a name="resource-governance"></a>Gouvernance des ressources

Une décision concernant les outils de gouvernance des ressources doit être prise avant la migration. Les outils n’ont pas besoin d’être entièrement implémentés, mais une direction doit être choisie et testée. L’équipe de gouvernance cloud doit définir et exiger l’implémentation d’un produit minimum viable (MVP) pour les outils de gouvernance avant la migration.

## <a name="network"></a>Réseau

Vos charges de travail informatiques nécessitent la configuration de réseaux virtuels pour prendre en charge l’accès de l’administrateur et de l’utilisateur final. Selon les décisions prises concernant l’organisation et la gouvernance des ressources, vous devez sélectionner une approche réseau pour l’aligner sur les exigences de sécurité informatique. En outre, vos décisions en matière de réseau doivent être alignées sur toute contrainte de réseau hybride requise pour exécuter les charges de travail dans le backlog de migration et prendre en charge tout accès aux ressources hébergées localement.

## <a name="identity"></a>Identité

Les services d’identité informatiques sont un prérequis afin de proposer la gestion des identités et des accès (IAM) pour vos ressources cloud. Alignez votre stratégie de gestion des identités sur vos plans d’adoption du cloud avant de continuer. Par exemple, lors de la migration de ressources locales existantes, envisagez de favoriser une approche d’identité hybride à l’aide de la [synchronisation d’annuaires](../../../decision-guides/identity/index.md) pour autoriser un ensemble cohérent d’informations d’identification d’utilisateur dans vos environnements local et cloud pendant et après la migration.

## <a name="next-steps"></a>Étapes suivantes

Si l’environnement répond à la configuration minimale requise, il peut être considéré comme approuvé en ce qui concerne la préparation à la migration. La [complexité culturelle et la gestion des changements](./cultural-complexity.md) permettent d’aligner les rôles et les responsabilités afin de garantir des attentes appropriées lors de l’exécution du plan.

> [!div class="nextstepaction"]
> [Complexité culturelle et gestion des changements](./cultural-complexity.md)
