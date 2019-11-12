---
title: Guide de décision sur la journalisation et création de rapports
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Découvrez les principaux services pour les migrations Azure : journalisation, création de rapports et supervision.'
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: b772eddfce65fa7a2ce4d67e36b1cc0f82e47ac5
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564875"
---
# <a name="logging-and-reporting-decision-guide"></a>Guide de décision sur la journalisation et création de rapports

Toutes les organisations ont besoin de mécanismes leur permettant d’avertir les équipes informatiques en cas de problèmes de performances, de temps de fonctionnement et de sécurité avant qu’ils ne s’aggravent. Une stratégie de supervision efficace vous permet d’analyser les performances individuelles des composants qui constituent vos charges de travail et votre infrastructure réseau. Dans le cas d’une migration de cloud public, il est essentiel d’intégrer la journalisation et la création de rapports à vos systèmes de supervision existants, et d’informer le personnel informatique approprié des événements et métriques importants. De cette manière, vous vous assurez que votre organisation atteint ses objectifs de conformité en termes de temps de fonctionnement, de sécurité et de stratégies.

![Traçage des options de journalisation, de création de rapports et de supervision de la moins complexe à la plus complexe, dans l’ordre des liens ci-dessous](../../_images/decision-guides/decision-guide-logging-and-reporting.png)

Passer à : [Planification de votre infrastructure de supervision](#plan-your-monitoring-infrastructure) | [Cloud natif](#cloud-native) | [Extension locale](#on-premises-extension) | [Agrégation de passerelle](#gateway-aggregation) | [Supervision hybride (locale)](#hybrid-monitoring-on-premises) | [Supervision hybride (basée sur le cloud)](#hybrid-monitoring-cloud-based) | [Multicloud](#multicloud) | [En savoir plus](#learn-more)

Lorsque vous déterminez une stratégie de journalisation et de création de rapports cloud, le point d’inflexion se base principalement sur les investissements que votre organisation a déjà faits dans les processus opérationnels et, dans une certaine mesure, sur les exigences à prendre en charge dans une stratégie multicloud.

Il existe plusieurs façons de journaliser et de créer des rapports sur les activités dans le cloud. Le cloud natif et la journalisation centralisée sont deux options de service managé courantes, qui sont basées sur la conception de l’abonnement et le nombre d’abonnements.

## <a name="plan-your-monitoring-infrastructure"></a>Planifier votre infrastructure de supervision

Lors de la planification de votre déploiement, vous devez penser à l’emplacement où seront stockées vos données de journalisation, et à la manière dont vous intégrerez les rapports et les services de supervision basés sur le cloud à vos processus et outils existants.

| Question | Cloud natif | Extension locale | Supervision hybride | Agrégation de passerelle |
|-----|-----|-----|-----|-----|
| Vous disposez déjà d’une infrastructure de supervision locale ? | Non | OUI | OUI |  Non |
| Avez-vous des exigences qui empêchent le stockage des données de journal dans des emplacements de stockage externes ? | Non | OUI | Non | Non |
| Avez-vous besoin d’intégrer la supervision cloud à des systèmes locaux ? | Non | Non | OUI | Non |
Avez-vous besoin de traiter ou filtrer les données de télémétrie avant de les envoyer à vos systèmes de supervision ? | Non | Non | Non | OUI |

### <a name="cloud-native"></a>Cloud natif

Si votre organisation ne dispose pas à l’heure actuelle de systèmes de création de rapports et de journalisation établis, ou si votre déploiement planifié n’a pas besoin d’être intégré à des systèmes de supervision locaux existants ou externes, le plus simple est d’opter pour une solution SaaS cloud native, telle que [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview).

Dans ce scénario, toutes les données de journal sont enregistrées et stockées dans le cloud, tandis que les outils de journalisation et création de rapports, qui traitent les informations et les mettent en évidence auprès de l’équipe informatique, sont fournis par la plateforme Azure et Azure Monitor.

Les solutions de journalisation personnalisées basées sur Azure Monitor peuvent être implémentées ad hoc pour chaque abonnement ou charge de travail, dans des déploiements plus petits ou expérimentaux. Par ailleurs, elles sont organisées de manière centralisée afin de superviser les données de journal de tout votre patrimoine cloud.

**Conditions nécessaires pour le cloud natif :** Les conditions suivantes sont nécessaires à l’utilisation d’un système de création de rapports et de journalisation cloud natif :

- Vous n’avez pas besoin d’intégrer les données de journal de vos charges de travail cloud dans vos systèmes locaux existants.
- Vous n’utilisez pas vos systèmes de création de rapports basés sur le cloud pour superviser les systèmes locaux.

### <a name="on-premises-extension"></a>Extension locale

L’utilisation de solutions de journalisation et de création de rapports cloud, telles que Azure Monitor, peut nécessiter un effort important de redéveloppement pour les applications et les services devant faire l’objet d’une migration vers le cloud. Dans ce cas, il peut être judicieux d’autoriser les charges de travail à continuer d’envoyer des données de télémétrie aux systèmes locaux existants.

Pour que cette approche soit possible, vos ressources cloud doivent être en mesure de communiquer directement avec vos systèmes locaux via un [réseau hybride](../software-defined-network/hybrid.md) et des [services de domaine hébergés dans le cloud](../identity/index.md#cloud-hosted-domain-services). Une fois cela mis en place, le réseau virtuel cloud fonctionne comme une extension de l’environnement local. Par conséquent, vos charges de travail hébergées sur le cloud peuvent communiquer directement avec votre système de création de rapports et de journalisation local.

Cette approche s’appuie sur les investissements que vous avez déjà faits dans les outils de supervision, et modifie de manière limitée les applications et services déployés sur le cloud. Cette approche est souvent la plus rapide pour prendre en charge la supervision lors d’une migration de type lift-and-shift. En revanche, elle ne permet pas de capturer les données de journal produites par les ressources PaaS et SaaS basées sur le cloud. De même, elle omet tous les journaux liés aux machines virtuelles et générés par la plateforme cloud en elle-même, comme l’état des machines virtuelles. Par conséquent, ce modèle doit servir de solution temporaire en attendant qu’une solution de supervision hybride plus complète soit implémentée.

Conditions s’appliquant uniquement aux scénarios en local :

- Vous devez conserver vos données de journal uniquement dans votre environnement local, que ce soit en raison d’exigences techniques ou d’exigences stratégiques ou réglementaires.
- Vos systèmes locaux ne prennent pas en charge les solutions de journalisation et création de rapports hybrides ni les solutions d’agrégation de passerelle.
- Vos applications basées sur le cloud peuvent envoyer la télémétrie directement à vos systèmes de journalisation et agents de supervision locaux. Ces derniers effectuent un envoi local, qui peut être déployé sur les machines virtuelles de charge de travail.
- Vos charges de travail ne sont pas dépendantes de services PaaS ou SaaS, qui nécessitent une journalisation et une création de rapports basées sur le cloud.

### <a name="gateway-aggregation"></a>Agrégation de passerelle

Si la quantité de données de télémétrie basées sur le cloud est importante ou si les systèmes de supervision locaux existants ont besoin de modifier les données de journal avant de pouvoir les traiter, un service d’[agrégation de passerelle](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation) de données journal peut être nécessaire.

Un service de passerelle est déployé sur votre fournisseur de cloud. Ensuite, les applications et les services appropriés sont configurés de manière à ce qu’ils envoient les données de télémétrie à la passerelle au lieu du système de journalisation par défaut. Suite à cela, la passerelle peut traiter les données : elle agrège des données, les combine et les formate selon les besoins avant de les envoyer à votre système de supervision qui les ingère et les analyse.

En outre, une passerelle peut être utilisée pour agréger et prétraiter des liaisons de données de télémétrie pour les systèmes cloud natifs et hybrides.

Postulats concernant l’agrégation de passerelle :

- Vous vous attendez à des niveaux élevés de données de télémétrie provenant de vos services et applications basés sur le cloud.
- Vous devez formater ou optimiser vos données de télémétrie avant de les envoyer à vos systèmes de supervision.
- Vos systèmes de supervision disposent d’API ou d’autres mécanismes disponibles pour ingérer les données de journal après leur traitement par la passerelle.

### <a name="hybrid-monitoring-on-premises"></a>Supervision hybride (locale)

Une solution de supervision hybride combine les données de journal de vos ressources locales et cloud. De cette manière, elle peut vous fournir une vue intégrée de l’état opérationnel de votre parc informatique.

Si vous avez déjà investi dans des systèmes de supervision locaux qu’il serait difficile ou coûteux de remplacer, vous pouvez intégrer la télémétrie de vos charges de travail cloud à vos solutions de supervision locales existantes. Dans un système de supervision local hybride, les données de télémétrie locales continuent d’utiliser le système de supervision local existant. Les données de télémétrie basées sur le cloud peuvent être directement envoyées au système de supervision local, ou elles peuvent être envoyées à Azure Monitor, puis compilées et ingérées par le système local à intervalles réguliers.

**Conditions nécessaires à la supervision hybride locale :** Les postulats suivants sont admis lorsque l’on utilise un système de création de rapports et de journalisation local pour la supervision hybride :

- Vous devez utiliser des systèmes de création de rapports locaux existants pour superviser les charges de travail cloud.
- Vous devez rester propriétaire des données de journal locales.
- Vos systèmes de gestion locaux disposent d’API ou d’autres mécanismes disponibles pour ingérer les données de journal venant de systèmes basés sur le cloud.

> [!TIP]
> Étant donné la nature itérative de la migration cloud, il est possible de passer d’une supervision cloud native et locale à une approche hybride partielle à mesure qu’avance l’intégration des ressources et des services basés sur le cloud dans votre parc informatique.

### <a name="hybrid-monitoring-cloud-based"></a>Supervision hybride (basée sur le cloud)

Si vous n’avez pas un besoin essentiel de maintenir un système de supervision local, ou si vous voulez remplacer les systèmes de supervision locaux par une solution centralisée basée sur le cloud, vous pouvez également choisir d’intégrer des données de journal locales à Azure Monitor, afin de fournir un système de supervision centralisée basée sur le cloud.

Ce scénario est une mise en miroir de l’approche centralisée locale : les charges de travail basées sur le cloud envoient des données de télémétrie directement à Azure Monitor, tandis que les applications et les services locaux envoient des données de télémétrie directement à Azure Monitor ou agrègent les données localement pour qu’elles soient ingérées par Azure Monitor à intervalles réguliers. Azure Monitor vous sert ensuite de système principal de création de rapports et de supervision pour l’ensemble de votre parc informatique.

Postulats concernant la supervision hybride basée sur le cloud : Les postulats suivants sont admis lorsque l’on utilise un système de création de rapports et de journalisation basé sur le cloud pour la supervision hybride :

- Vous n’êtes pas dépendant des systèmes de supervision locaux existants.
- Vos charges de travail n’imposent pas d’exigences stratégiques ou réglementaires quant au stockage des données de journal en local.
- Vos systèmes de supervision basés sur le cloud disposent d’API ou d’autres mécanismes disponibles pour ingérer les données de journal venant de services et d’applications locaux.

### <a name="multicloud"></a>Multicloud

L’intégration des capacités de journalisation et de création de rapports sur l’ensemble d’une plateforme multi-cloud peut être compliquée. Les services offerts d’une plateforme à une autre ne sont pas directement comparables, et les capacités de journalisation et de télémétrie fournies par ces services sont également différentes.
La prise en charge de la journalisation multicloud nécessite souvent d’avoir recours à des services de passerelle. Ces derniers traitent les données de journal et les convertissent en un format courant, avant de les envoyer à une solution de journalisation hybride.

## <a name="learn-more"></a>En savoir plus

[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) est le service de supervision et de création de rapports par défaut pour Azure. Elle fournit :

- Une plateforme unifiée servant à collecter la télémétrie d’application, la télémétrie d’hôte (par exemple, les machines virtuelles), les métriques de conteneur, les métriques de plateforme Azure et les journaux des événements.
- Visualisation, requêtes, alertes et outils d’analyse. Ce service peut fournir des insights sur les machines virtuelles, les systèmes d’exploitation invités, les réseaux virtuels et les événements d’application de charge de travail.
- Les [API REST](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-rest-api-walkthrough) pour l’intégration à des services externes et pour l’automatisation des services de supervision et d’alerte
- [Intégration](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-partners) avec de nombreux fournisseurs tiers connus.

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, la journalisation et la création de rapports ne représentent qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
