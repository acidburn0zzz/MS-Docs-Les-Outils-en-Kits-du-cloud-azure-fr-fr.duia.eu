---
title: Motivations et risques commerciaux dans la discipline Accélération du déploiement
description: Utilisez le Framework d’adoption du cloud pour Azure pour comprendre les risques métier liés à la discipline d’accélération du déploiement, qui peut être utilisée dans la stratégie de gouvernance.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 1a2c1f53e5559c9ca161cad5b68266f0cd1ff83d
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83755018"
---
# <a name="motivations-and-business-risks-in-the-deployment-acceleration-discipline"></a>Motivations et risques commerciaux dans la discipline Accélération du déploiement

Cet article décrit les raisons pour lesquelles les clients adoptent une discipline d'accélération du déploiement dans le cadre d’une stratégie de gouvernance cloud. Des exemples sur les risques métier conduisant à la rédaction d’instructions de stratégie sont également présentés.

<!-- markdownlint-disable MD026 -->

## <a name="relevance"></a>Pertinence

Les systèmes locaux sont souvent déployés à l’aide d'images de référence ou de scripts d’installation. Une configuration supplémentaire est généralement requise, ce qui peut impliquer plusieurs étapes, voire une intervention humaine. Ces processus manuels sont sujets aux erreurs et entraînent souvent une « dérive de configuration », nécessitant des tâches de dépannage et de correction chronophages.

La plupart des ressources Azure peuvent être déployées et configurées manuellement via le portail Azure. Cette approche peut couvrir vos besoins si vous n'avez que quelques ressources à gérer. À mesure que votre patrimoine cloud se développe, votre organisation doit intégrer une automatisation dans ses processus de déploiement pour éviter toute dérive de configuration des ressources cloud ou d’autres problèmes introduits par les processus manuels. L’adoption d’une approche DevOps ou [DevSecOps](https://www.microsoft.com/devsecops) est souvent le meilleur moyen de gérer vos déploiements au fur et à mesure que vos efforts d’adoption du cloud évoluent.

Un plan d'accélération du déploiement robuste permet de veiller à ce que vos ressources cloud soient déployées, mises à jour et configurées de façon correcte et cohérente, et qu'elles le restent. La maturité de votre stratégie d’accélération du déploiement peut également constituer un facteur important de votre [stratégie de gestion des coûts](../cost-management/index.md). L’approvisionnement et la configuration automatiques de vos ressources cloud vous permettent de descendre en puissance ou de libérer des ressources lorsque la demande est faible ou limitée dans le temps, de manière à ne payer que les ressources dont vous avez besoin.

## <a name="business-risk"></a>Risque métier

La discipline d’accélération du déploiement tente de résoudre les risques métier suivants. Lors de l'adoption du cloud, surveillez la pertinence des points ci-dessous :

- **Interruption de service :** L'absence de processus de déploiement prévisibles et reproductibles ou des modifications non gérées des configurations système peuvent perturber les opérations normales et entraîner une perte de productivité ou d'activité.
- **Surcoûts :** Des modifications inattendues ayant trait à la configuration des ressources système peuvent rendre plus difficile l'identification de la cause racine des problèmes, et augmenter ainsi les coûts de développement, d'exploitation et de maintenance.
- **Manque d’efficacité organisationnelle :** Les barrières entre les équipes de développement, d’exploitation et de sécurité peuvent poser de nombreux problèmes en termes d'adoption efficace des technologies de cloud et de développement d’un modèle de gouvernance du cloud unifié.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de discipline Accélération du déploiement](./template.md), documentez les risques métier susceptibles d’être introduits par le plan d’adoption du cloud actuel.

Une fois tous les risques métier réalistes appréhendés, l’étape suivante consiste à documenter la tolérance de l’activité aux risques, ainsi que les indicateurs et métriques clés permettant de surveiller cette tolérance.

> [!div class="nextstepaction"]
> [Métriques, indicateurs et tolérance au risque](./metrics-tolerance.md)
