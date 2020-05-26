---
title: Exécution d’une migration
description: Obtenez une vue d’ensemble des articles qui expliquent les différentes activités qui peuvent être impliquées dans la migration d’une charge de travail dans Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ce653ab8c37eb4e034647cb8022adaf391f1949f
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83815342"
---
# <a name="deploy-workloads"></a>Déployer les charges de travail

Une fois les charges de travail évaluées, elles peuvent être déployées dans le cloud ou placées en préproduction en vue de leur mise en production. Cette série d’articles explique les différentes activités qui peuvent être impliquées dans cette phase de l’effort de migration.

## <a name="objective"></a>Objectif

L’objectif d’une migration consiste à migrer une charge de travail unique vers le cloud.

## <a name="definition-of-_done_"></a>Définition de « _terminé_ »

La phase de migration est terminée quand une charge de travail, comprenant toutes les ressources nécessaires à son fonctionnement, est en préproduction et est prête à être testée dans le cloud. Durant le processus d’optimisation, la charge de travail est préparée en vue de son utilisation en production.

Cette définition de « _terminé_ » peut varier en fonction des processus de test et de publication. Le prochain article de cette série traite du [choix d’un modèle de promotion](./promotion-models.md) et peut vous aider à déterminer le meilleur moment de promouvoir une charge de travail migrée en vue d’une utilisation en production.

## <a name="accountability-during-migration"></a>Responsabilité de la migration

La responsabilité de l’ensemble du processus de migration revient à l’équipe d’adoption du cloud. Cependant, les membres de l’équipe de stratégie cloud ont quelques responsabilités qui sont listées dans la section suivante.

## <a name="responsibilities-during-migration"></a>Obligations liées à la migration

En plus de la responsabilité d’ensemble, certaines actions doivent être affectées directement à un individu ou à un groupe. Voici quelques-unes des activités qui doivent être confiées à des parties responsables :

- **Correction.** Résolvez tous les problèmes de compatibilité empêchant la migration de la charge de travail vers le cloud.
  - Comme indiqué dans l’article des prérequis traitant [de la complexité technique et de la gestion des changements](../prerequisites/technical-complexity.md), vous devez décider à l’avance de la manière dont cette activité doit être exécutée. Déterminez en particulier si la correction sera effectuée par l’équipe d’adoption du cloud durant le même sprint que l’effort de migration réel. Sinon, décidez si un modèle de type « vague » ou « usine » sera utilisé pour effectuer la correction dans une itération séparée. Si certains membres n’ont pas de connaissances élémentaires sur ces processus, il peut être judicieux de revisiter la section sur les [prérequis](../prerequisites/index.md).
- **Réplication.** Créez une copie de chaque ressource dans le cloud pour synchroniser les machines virtuelles, les données et les applications avec les ressources dans le cloud.
  - Selon le modèle de promotion, différents outils peuvent être nécessaires pour mener à bien cette activité.
- **Préproduction.** Une fois toutes les ressources d’une charge de travail répliquées et vérifiées, vous pouvez mettre la charge de travail en préproduction pour réaliser des tests d’entreprise et exécuter un plan des changements dans l’entreprise.

## <a name="next-steps"></a>Étapes suivantes

Grâce aux connaissances générales que vous venez d’acquérir sur le processus de migration, vous pouvez à présent [choisir un modèle de promotion](./promotion-models.md).

> [!div class="nextstepaction"]
> [Choisir un modèle de promotion](./promotion-models.md)
