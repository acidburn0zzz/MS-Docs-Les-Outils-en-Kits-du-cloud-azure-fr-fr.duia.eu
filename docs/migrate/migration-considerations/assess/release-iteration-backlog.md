---
title: Itération et backlog de version
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Génération d’une itération et d’un backlog de version
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d2dddb4893a2781da38969949972fa516e32b46c
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025401"
---
# <a name="manage-change-in-an-incremental-migration-effort"></a>Gérer les modifications dans un effort de migration incrémentiel

Cet article part du principe que les processus de migration sont incrémentiels par nature, s’exécutant parallèlement au [processus régi](../../../govern/index.md). Toutefois, le même guide peut être utilisé pour remplir les tâches initiales dans une structure de répartition du travail pour les approches de gestion des changements en cascade traditionnelles.

## <a name="release-backlog"></a>Backlog de version

Un *backlog de version* est constitué d’une série de ressources (machines virtuelles, bases de données, fichiers et applications) qui doivent être migrées avant qu’une charge de travail puisse être publiée pour une utilisation en production dans le cloud. Au cours de chaque itération, l’équipe d’adoption cloud documente et évalue les efforts requis pour déplacer chaque ressource vers le cloud. Consultez la section « Backlog d’itération » qui suit.

## <a name="iteration-backlog"></a>Backlog d’itération

Un *backlog d’itération* est une liste détaillée des tâches requises pour migrer un nombre spécifique de ressources de l’espace numérique existant vers le cloud. Les entrées de cette liste sont souvent stockées dans un outil de gestion agile, comme Azure DevOps, en tant qu’éléments de travail.

Avant de commencer la première itération, l’équipe d’adoption cloud spécifie une durée d’itération, généralement de deux à quatre semaines. Ce créneau de temps est important pour créer une période de début et de fin pour chaque ensemble d’activités validées. La gestion de la cohérence des fenêtres d’exécution simplifie la mesure de la vélocité (le rythme de la migration) et l’alignement avec les besoins en constante évolution de l’entreprise.

Avant chaque itération, l’équipe examine le backlog de version, en estimant l’effort et les priorités des ressources à migrer. Elle s’engage ensuite à fournir un nombre spécifique de migrations convenues. Une fois que l’équipe d’adoption cloud consent à ce chiffre, la liste des activités devient le *backlog d’itération actuel*.

Au cours de chaque itération, les membres de l’équipe travaillent en tant qu’équipe auto-organisationnelle pour respecter les engagements dans le backlog d’itération actuel.

## <a name="next-steps"></a>Étapes suivantes

Une fois qu’un backlog d’itération est défini et accepté par l’équipe d’adoption cloud, les [approbations de gestion des changements](./approve.md) peuvent être finalisées.

> [!div class="nextstepaction"]
> [Approuver les changements de l’architecture avant la migration](./approve.md)
