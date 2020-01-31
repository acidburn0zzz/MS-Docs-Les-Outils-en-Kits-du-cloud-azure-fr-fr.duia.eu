---
title: Plusieurs centres de données
description: Plusieurs centres de données
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 9156df0b76f6edf1d249d5d724e0a5d0f4fd8e15
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76803073"
---
# <a name="multiple-datacenters"></a>Plusieurs centres de données

L’étendue d’une migration implique souvent la transition de plusieurs centres de données. Les conseils suivants élargiront la portée du [guide de migration Azure](../azure-migration-guide/index.md) pour traiter plusieurs centres de données.

## <a name="general-scope-expansion"></a>Expansion de l’étendue générale

La majeure partie de cet effort nécessaire dans le cadre de cette expansion de l’étendue se produit au cours des processus de détermination des prérequis, d’évaluation et d’optimisation d’une migration.

## <a name="suggested-prerequisites"></a>Prérequis suggérés

Avant de commencer la migration, vous devez créer des épopées dans l’outil de gestion de projet pour représenter chaque centre de données à migrer. Il est ensuite important de comprendre les résultats et les motivations métier qui justifient cette migration. Ces motivations peuvent être utilisées pour classer par ordre de priorité la liste des épopées (ou centres de données). Par exemple, si la migration est motivée par un désir de quitter les centres de données avant le renouvellement des baux, chaque épopée sera alors classée par ordre de priorité en fonction de la date de renouvellement du bail.

Dans chaque épopée, les charges de travail à évaluer et à migrer sont managées en tant que fonctionnalités. Chaque ressource de cette charge de travail est managée en tant que récit utilisateur. Le travail nécessaire pour évaluer, migrer, optimiser, promouvoir, sécuriser et gérer chaque ressource est représenté sous la forme de tâches pour chaque ressource.

Les sprints ou les itérations consistent alors en une série de tâches requises pour migrer les ressources et les récits utilisateur validés par l’équipe d’adoption du cloud. Les mises en production comportent alors une ou plusieurs charges de travail ou fonctionnalités à promouvoir en production.

## <a name="assess-process-changes"></a>Évaluer les changements de processus

La modification la plus importante du processus d’évaluation, lors de l’extension de l’étendue pour traiter plusieurs centres de données, est liée à l’enregistrement et à la hiérarchisation précis des charges de travail et des dépendances entre les centres de données.

### <a name="suggested-action-during-the-assess-process"></a>Action suggérée pendant le processus d’évaluation

**Évaluer les dépendances entre les centres de données :** Les [outils de visualisation des dépendances d’Azure Migrate](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization) peuvent vous aider à identifier les dépendances. L’utilisation de cet ensemble d’outils avant la migration est une bonne pratique générale. Toutefois, lors de la gestion de la complexité globale, cette étape devient indispensable pour le processus d’évaluation. Grâce au [regroupement des dépendances](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies), la visualisation peut vous aider à identifier les adresses IP et les ports des ressources requises pour prendre en charge la charge de travail.

> [!IMPORTANT]
> Deux remarques importantes : Tout d’abord, un expert en matière de placement des ressources et des schémas d’adresses IP est nécessaire pour identifier les ressources qui résident dans un centre de données secondaire. Deuxièmement, il est important d’évaluer les dépendances et les clients en aval dans le visuel pour comprendre les dépendances bidirectionnelles.

## <a name="migrate-process-changes"></a>Migrer les changements de processus

La migration de plusieurs centres de données est similaire à la consolidation des centres de données. Après la migration, le cloud devient l’unique solution de centre de données pour de multiple ressources. L’extension de l’étendue la plus probable au cours du processus de migration est la validation et l’alignement des adresses IP.

### <a name="suggested-action-during-the-migrate-process"></a>Action suggérée pendant le processus de migration

Les activités suivantes ont une incidence importante sur la réussite d’une migration vers le cloud :

- **Évaluer les conflits réseau :** Lors de la consolidation de centres de données en un seul fournisseur de services cloud, il est probable de créer des conflits réseau, DNS ou autres. Pendant la migration, il est important de tester les conflits afin d’éviter les interruptions des systèmes de production hébergés dans le cloud.
- **Mettre à jour les tables de routage :** Souvent, les modifications apportées aux tables de routage sont requises lors de la consolidation de réseaux ou de centres de données.

## <a name="optimize-and-promote-process-changes"></a>Changements aux processus d’optimisation et de promotion

Pendant l’optimisation, des tests supplémentaires peuvent être nécessaires.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Action suggérée pendant le processus d’optimisation et de promotion

Avant la promotion, il est important de fournir des niveaux supplémentaires de test pendant cette expansion de l’étendue. Lors du test, il est important de tester le routage ou d’autres conflits réseau. En outre, il est important d’isoler l’application déployée et de la retester pour vérifier que toutes les dépendances ont été migrées vers le cloud. Dans ce cas, l’isolation consiste à séparer l’environnement déployé des réseaux de production. Cela permet ainsi d’intercepter des ressources négligées qui sont toujours en cours d’exécution localement.

## <a name="secure-and-manage-process-changes"></a>Changements aux processus de sécurisation et de gestion

Les processus de sécurisation et de gestion devraient rester inchangés par cette expansion de l’étendue.

## <a name="next-steps"></a>Étapes suivantes

Revenez à la [check-list d’expansion d’étendue](./index.md) pour vous assurer que votre méthode de migration est entièrement alignée.

> [!div class="nextstepaction"]
> [Check-list d’expansion d’étendue](./index.md)
