---
title: Métriques et indicateurs de tolérance au risque dans la discipline Gestion des coûts
description: Utilisez le Framework d’adoption du cloud pour Azure pour quantifier les métriques et les indicateurs de tolérance au risque pour la gestion des coûts la gouvernance cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: abaa95421c8e6acdec724f40e5b0e1cd30b7babf
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83815053"
---
# <a name="risk-tolerance-metrics-and-indicators-in-the-cost-management-discipline"></a>Métriques et indicateurs de tolérance au risque dans la discipline Gestion des coûts

Apprenez à quantifier la tolérance aux risques de l’entreprise associée à la discipline Gestion des coûts. La définition de mesures et d’indicateurs vous aide à créer une étude de rentabilité pour investir dans la maturité de cette discipline.

## <a name="metrics"></a>Mesures

La gestion des coûts met généralement l’accent sur les mesures liées aux coûts. Dans le cadre de votre analyse des risques, vous aurez besoin de collecter des données relatives à vos dépenses actuelles et planifiées liées aux charges de travail cloud afin de déterminer le niveau de risque auquel vous êtes exposé et l’importance des investissements dans votre discipline de gestion des coûts pour vos déploiements cloud planifiés.

Voici quelques exemples de métriques utiles que vous devez rassembler pour mieux évaluer la tolérance aux risques dans la discipline Gestion des coûts :

- **Dépenses annuelles :** Coût annuel total des services fournis par un fournisseur de services cloud.
- **Dépenses mensuelles :** Coût mensuel total des services fournis par un fournisseur de services cloud.
- **Ratio du prévisionnel par rapport au réel :** Ratio de comparaison des dépenses prévues et des dépenses réelles (mensuelles ou annuelles).
- **Rapport de rythme d’adoption (mois par mois) :** Pourcentage du delta dans les coûts du cloud d’un mois à l’autre.
- **Coûts cumulés :** Total de dépenses quotidiennes cumulées, à partir du début du mois.
- **Tendances des dépenses :** Tendance des dépenses par rapport au budget.

## <a name="risk-tolerance-indicators"></a>Indicateurs de tolérance au risque

Au cours des déploiements précoces à petite échelle, tels que le développement/les tests ou les premières charges de travail expérimentales, Cost Management est susceptible de présenter un risque relativement faible. À mesure que des ressources sont déployées, le risque augmente et la tolérance au risque de l’entreprise est susceptible de diminuer. De plus, à mesure que les équipes d’adoption du cloud ont la possibilité de configurer ou de déployer des ressources dans le cloud, le risque augmente et la tolérance diminue. À l’inverse, le développement d’une discipline Cost Management nécessite des collaborateurs de la phase d’adoption du cloud pour le déploiement des technologies plus innovantes.

Lors des premières étapes de l’adoption du cloud, vous collaborez avec votre entreprise pour déterminer une base de référence de tolérance au risque. Une fois que vous disposez d’une base de référence, vous devez déterminer les critères qui déclenchent un investissement dans la discipline Cost Management. Ces critères seront probablement différents pour chaque organisation.

Après avoir identifié les [risques métier](./business-risks.md), vous collaborez avec votre entreprise pour définir les bancs d’essai permettant d’identifier les déclencheurs d’augmentation potentielle de ces risques. Voici quelques exemples de mesures, telles que celles mentionnées ci-dessus, par rapport à votre tolérance aux risques de référence pour inciter votre entreprise à investir davantage dans Cost Management.

- **Engagement justifié (cas le plus courant) :** Entreprise qui s’engage à dépenser _n 000 000 €_ cette année dans des services de fournisseur cloud. Elle a besoin d’une discipline Cost Management pour veiller à ne pas dépasser ses objectifs de dépenses de plus de 20 % et à utiliser au moins 90 % de son budget.
- **Déclencheur de pourcentage :** Entreprise dont les dépenses cloud sont stables pour ses systèmes de production. En cas de hausse de plus _x pour cent_, une discipline Cost Management est un investissement judicieux.
- **Déclencheur de surapprovisionnement :** Entreprise qui considère ses solutions déployées sont suraprovisionnées. Cost Management est un investissement prioritaire tant que l’entreprise ne démontre pas que le provisionnement des ressources est parfaitement adapté à l’utilisation de celles-ci.
- **Déclencheur de dépense mensuelle :** Des dépenses mensuelles de plus de _n 000 €_ constituent un coût important pour une entreprise. Si les dépenses dépassent ce montant au cours d’un mois donné, l’entreprise doit investir dans Cost Management.
- **Déclencheur de dépense annuelle :** Entreprise disposant d’un budget informatique de R&D qui permet de dépenser _n 000 €_ par an pour l’expérimentation cloud. L'entreprise peut exécuter des charges de travail de production dans le cloud, mais le déclencheur est toujours considéré comme une solution expérimentale si le budget ne dépasse pas ce montant. Si le budget est dépassé, il doit être traité comme un investissement de production, ce qui oblige à gérer étroitement les dépenses.
- **Frais d’exploitation indésirables (rare) :** Une entreprise refuse de subir des dépenses d'exploitation et a besoin de disposer de contrôles de gestion des coûts avant de déployer une charge de travail de développement/de test.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de stratégie de gestion des coûts](./template.md), documenter les métriques et les indicateurs de tolérance correspondant au plan d’adoption du cloud actuel.

Considérez les exemples de stratégies de Gestion des coûts comme des points de départ permettant de développer vos propres stratégies qui répondent à des risques métier spécifiques, dans la continuité de vos plans d’adoption du cloud.

> [!div class="nextstepaction"]
> [Examiner les exemples de stratégies](./policy-statements.md)
