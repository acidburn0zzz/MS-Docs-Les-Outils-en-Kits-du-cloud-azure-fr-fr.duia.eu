---
title: Appliquer des principes de conception et des opérations avancées
description: Appliquer des principes de conception et des opérations avancées
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 16762a0eae366c3bf1cd578faaf52df60e6c97b1
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807680"
---
# <a name="apply-design-principles-and-advanced-operations"></a>Appliquer des principes de conception et des opérations avancées

Les trois premières disciplines de gestion cloud décrivent une base de référence de gestion. Au minimum, une base de référence de gestion doit inclure un engagement métier standard afin de réduire au maximum les interruptions d’activité et d’accélérer la récupération en cas d’interruption du service. La plupart des bases de référence de gestion se concentrent sur le maintien de l’inventaire et de la visibilité, de la conformité opérationnelle, ainsi que de la protection et de la récupération.

L’objectif d’une base de référence de gestion est de créer une offre cohérente fournissant un niveau minimal d’engagement métier pour toutes les charges de travail prises en charge. Cette base de référence d’offres de gestion reproductibles communes permet à l’équipe de fournir une gestion opérationnelle hautement optimisée, avec une déviation minime. Toutefois, cette offre standard peut ne pas fournir un engagement suffisant pour l’entreprise.

Le diagramme de la section suivante illustre trois façons d’aller au-delà de la ligne de base de gestion.

La base de référence de gestion doit respecter l’engagement minimal dont ont besoin 80 % des charges de travail les moins critiques du portefeuille. La base de référence ne doit pas être appliquée à des charges de travail critiques pour la mission. Elle ne doit pas non plus être appliquée aux plateformes partagées entre les charges de travail. Celles-ci nécessitent qu’une attention particulière soit portée aux principes de conception et aux opérations avancées.

## <a name="advanced-operations-options"></a>Options des opérations avancées

Nous suggérons trois moyens d’améliorer les engagements métier au-delà de la base de référence de gestion, comme illustré dans le diagramme suivant :

![Opérations avancées](../_images/manage/beyond-the-baseline.png)

## <a name="enhanced-management-baseline"></a>Base de référence de gestion améliorée

Comme l’indique le guide de gestion Azure, une base de référence de gestion améliorée utilise des outils cloud natifs pour améliorer la durée de fonctionnement et réduire le temps de récupération. Les améliorations sont significatives, mais un peu moins qu’avec une spécialisation de charge de travail ou de plateforme. L’avantage d’une base de référence de gestion améliorée est la réduction tout aussi importante du coût et du temps d’implémentation.

## <a name="management-specialization"></a>Spécialisation de gestion

Certains aspects des opérations de charge de travail et de plateforme peuvent nécessiter la modification des principes de conception et d’architecture. Ces modifications peuvent prendre du temps et entraîner des frais d’exploitation accrus. Pour réduire le nombre de charges de travail nécessitant de tels investissements, une base de référence de gestion améliorée peut représenter une amélioration suffisante pour l’engagement métier.

Pour les charges de travail qui nécessitent un investissement plus élevé pour répondre à un engagement métier, la spécialisation des opérations est essentielle.

## <a name="areas-of-management-specialization"></a>Domaines de spécialisation de la gestion

Il existe deux domaines de spécialisation :

- **Spécialisation de plateforme :** Investir dans les opérations en cours d’une plateforme partagée, en répartissant l’investissement entre plusieurs charges de travail.
- **Spécialisation de charge de travail :** Investir dans les opérations en cours d’une charge de travail spécifique. Généralement réservée aux charges de travail critiques.

### <a name="central-it-or-cloud-center-of-excellence-ccoe"></a>Informatique centralisée ou centre d’excellence du cloud (CCoE)

Le choix entre une spécialisation de plateforme et une spécialisation de charge de travail est basé sur la criticité et l’impact de chaque charge de travail. Toutefois, ces choix reflètent également une décision culturelle plus large qui consiste à choisir entre les modèles organisationnels Informatique centralisée et CCoE.

La spécialisation de charge de travail entraîne souvent un changement culturel. L’informatique traditionnelle et l’informatique centralisée créent toutes les deux des processus qui peuvent aider à grande échelle. La prise en charge de la mise à l’échelle est plus facilement réalisable pour les services reproductibles présents dans une base de référence de gestion, une base de référence améliorée ou même des opérations de plateforme. La spécialisation de charge de travail fait rarement l’objet d’une mise à l’échelle. En raison de cette absence de mise à l’échelle, il est plus difficile pour une organisation appliquant l’informatique centralisée de fournir la prise en charge nécessaire sans atteindre les limites organisationnelles concernant la mise à l’échelle.

Le modèle CCoE permet une mise à l’échelle par le biais d’une délégation délibérée de la responsabilité et d’une centralisation sélective. La spécialisation de charge de travail tend à mieux s’aligner sur l’approche de responsabilité déléguée d’un CCoE.

L’exemple suivant présente l’alignement naturel des rôles dans un CCoE :

- L’équipe de plateforme cloud participe à la création de plateformes communes que partagent plusieurs équipes d’adoption cloud.
- L’équipe d’automatisation cloud étend ces plateformes sous la forme de ressources déployables dans un catalogue de services.
- La gestion cloud fournit la base de référence de gestion de manière centralisée et prend en charge l’utilisation du catalogue de services.
- Toutefois, l’unité commerciale (une équipe DevOps ou d’adoption cloud, par exemple) est responsable des opérations quotidiennes de la charge de travail, du pipeline ou des performances.

Comme lors de l’alignement des domaines de gestion, les modèles Informatique centralisée et CCoE peuvent généralement fournir une spécialisation de plateforme, avec un changement culturel minime. L’application de la spécialisation de charge de travail peut être un peu plus complexe pour les équipes appliquant l’informatique centralisée.

## <a name="management-specialization-processes"></a>Processus de spécialisation de la gestion

Pour chaque spécialisation, le processus en quatre étapes suivant est fourni sous la forme d’une méthode disciplinée et itérative. Cette méthode nécessite un partenariat avec des experts en adoption cloud, en plateformes cloud, en automatisation cloud et en gestion cloud afin de créer une boucle de commentaires viable et informée.

- **Améliorer la conception du système :** Améliorez la conception des systèmes communs (plateformes) ou des charges de travail spécifiques pour réduire efficacement les interruptions.
- **Automatiser la correction :** Certaines améliorations ne sont pas rentables. Dans ce cas, il peut être plus judicieux d’automatiser la correction et de réduire l’impact des interruptions.
- **Mettre à l’échelle la solution :** Lorsque la conception des systèmes et la correction automatisée sont améliorées, vous pouvez mettre ces modifications à l’échelle dans l’environnement via le catalogue de services.
- **Amélioration continue :** Vous pouvez utiliser divers outils de supervision pour découvrir les améliorations incrémentielles qui peuvent être apportées dans la prochaine étape de la conception du système, de l’automatisation et de la mise à l’échelle.

### <a name="improve-system-design"></a>Améliorer la conception du système

L’amélioration de la conception du système constitue l’approche la plus efficace pour améliorer les opérations de toutes les plateformes communes. Les améliorations de la conception du système peuvent augmenter la stabilité et diminuer les interruptions d’activité. La conception de systèmes individuels n’entre pas dans le cadre du Framework d’adoption cloud. En complément de celui-ci, Azure Architecture Framework fournit les bonnes pratiques permettant d’améliorer la résilience et la conception d’un système spécifique. Vous pouvez appliquer ces améliorations à la conception système d’une plateforme ou d’une charge de travail.

Azure Architecture Framework se concentre sur l’amélioration par le biais des cinq principes de la conception système :

- **Scalabilité :** Mise à l’échelle des ressources de plateforme communes pour gérer une charge accrue.
- **Disponibilité :** Diminution des interruptions d’activité par l’amélioration du potentiel de disponibilité.
- **Résilience :** Amélioration du temps de récupération pour réduire la durée des interruptions.
- **Sécurité :** Protection des applications et des données contre les menaces externes.
- **Gestion :** Processus d’opérations propres aux ressources de plateforme communes.

La plupart des interruptions d’activité correspondent à une certaine forme de dette technique ou de défaillance dans l’architecture. Pour les déploiements existants, les améliorations de la conception système peuvent être vues comme le paiement d’une dette technique existante. Pour les nouveaux déploiements, les améliorations de la conception système peuvent être vues comme l’évitement d’une dette technique. La section suivante, « Correction automatisée », vous permet de résoudre les éventuelles dettes techniques qui ne peuvent pas ou ne doivent pas être résolues.

En savoir plus sur [Azure Architecture Framework](https://docs.microsoft.com/azure/architecture/guide/pillars) pour améliorer la conception du système. Une fois que la conception de votre système se sera améliorée, revenez à cet article pour trouver de nouvelles opportunités d’améliorer et de faire évoluer ces améliorations dans votre environnement.

### <a name="automated-remediation"></a>Correction automatisée

Certaines dettes techniques ne peuvent pas ou ne doivent pas être résolues. En effet, leur résolution peut être trop coûteuse. Elle peut être planifiée, mais sa durée de projet peut être longue. Il est possible que l’interruption d’activité n’ait pas un impact significatif sur l’entreprise ou que la priorité de l’entreprise soit de récupérer rapidement au lieu d’investir dans la résilience.

Lorsque la résolution de la dette technique n’est pas souhaitée, la correction automatisée est généralement le choix à faire. L’utilisation d’Azure Automation et d’Azure Monitor pour détecter les tendances et fournir une correction automatisée est l’approche la plus couramment utilisée pour la correction automatisée.

Pour obtenir des conseils sur la correction automatisée, consultez [Azure Automation et les alertes](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

### <a name="scale-the-solution-with-a-service-catalog"></a>Mettre à l’échelle la solution avec un catalogue de services

L’élément indispensable à la spécialisation de plateforme et aux opérations de plateforme est un catalogue de services bien géré. C’est ainsi que les améliorations apportées à la conception et à la correction des systèmes sont mises à l’échelle dans un environnement. L’équipe de plateforme cloud et l’équipe d’automatisation cloud s’associent pour créer des solutions reproductibles convenant aux plateformes les plus courantes dans n’importe quel environnement. Toutefois, si ces solutions ne sont pas exploitées de manière cohérente, la gestion cloud peut offrir un peu plus qu’une offre de base de référence.

Pour accroître l’adoption et réduire la charge de maintenance de toutes les plateformes optimisées, la plateforme doit être ajoutée à un catalogue de services. Chaque application du catalogue peut être déployée pour un usage interne via le catalogue de services ou en tant qu’offre de la Place de marché pour les utilisateurs externes.

Pour obtenir des informations sur la publication dans un catalogue de services, consultez la série concernant la [publication dans un catalogue de services](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app).

### <a name="continuous-improvement"></a>Amélioration continue

La spécialisation de plateforme et les opérations de plateforme dépendent de boucles de commentaires efficaces entre les équipes chargées de l’adoption, de la plateforme, de l’automatisation et de la gestion. Le fait de baser ces boucles de commentaires sur des données permet à chaque équipe de prendre des décisions éclairées. Pour que les opérations de plateforme puissent respecter leurs engagements métier à long terme, il est important de tirer parti des insights propres à la plateforme centralisée. Étant donné que les conteneurs et SQL Server sont les plateformes gérées de manière centralisée qui sont les plus couramment utilisées, consultez les articles suivant, qui vous aideront à vous familiariser avec la collecte de données en vue d’une amélioration continue :

- [Performances du conteneur](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
- [Performances de la base de données PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
- [Performances de la base de données IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
