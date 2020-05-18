---
title: Chronologies d’un plan d’adoption du cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à évaluer les chronologies en fonction de votre plan d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: e5407f2f78942d22c5fa07b277f600d5440ddc04
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83214019"
---
# <a name="timelines-in-a-cloud-adoption-plan"></a>Chronologies d’un plan d’adoption du cloud

Dans l’article précédent de cette série, les charges de travail et les tâches étaient attribuées aux [mises en production et aux itérations](./iteration-paths.md). Ces attributions alimentent les estimations de chronologie dans cet article.

Les structures de répartition du travail sont couramment utilisées dans les outils de gestion de projets séquentiels. Elles représentent la façon dont les tâches dépendantes sont effectuées dans le temps. De telles structures fonctionnent bien lorsque les tâches sont séquentielles par nature. Les interdépendances des tâches dans l’adoption du cloud rendent ces structures difficiles à gérer. Pour combler cette lacune, vous pouvez estimer les chronologies en fonction des attributions de chemin d’itération en masquant la complexité.

## <a name="estimate-timelines"></a>Estimer les chronologies

Pour développer une chronologie, commencez par les mises en production. Les objectifs de cette mise en production créent une date cible pour tout impact métier. Les itérations facilitent l’alignement de ces mises en production avec des durées spécifiques.

Si des jalons plus granulaires sont requis dans la chronologie, utilisez l’attribution d’itérations pour indiquer des jalons. Pour effectuer cette attribution, supposez que la dernière instance d’une tâche liée à la charge de travail peut servir de jalon final. Les équipes marquent généralement la tâche finale comme un jalon.

Quel que soit le niveau de granularité, utilisez le dernier jour de l’itération comme date pour chaque jalon. Cela lie l’achèvement de l’adoption de la charge de travail à une date spécifique. Vous pouvez suivre la date dans une feuille de calcul ou un outil de gestion de projets séquentiel tel que Microsoft Project.

## <a name="delivery-plans-in-azure-devops"></a>Plans de livraison dans Azure DevOps

<!-- docsTest:ignore "Microsoft Delivery Plans" -->

Si vous utilisez Azure DevOps pour gérer votre plan d’adoption du cloud, envisagez d’avoir recours à [l’extension Plans de livraison Microsoft](https://marketplace.visualstudio.com/items?itemname=ms.vss-plans). Cette extension permet de créer rapidement une représentation visuelle de la chronologie basée sur les attributions d’itération et de mise en production.
