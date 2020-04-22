---
title: Commencer par les zones d’atterrissage à l’échelle de l’entreprise
description: Commencer par les zones d’atterrissage à l’échelle de l’entreprise
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 683385356d94400c8b29e55d019870c18eeda863
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81122038"
---
# <a name="start-with-enterprise-scale-landing-zones"></a>Commencer par les zones d’atterrissage à l’échelle de l’entreprise

Il n’est pas toujours judicieux pour une équipe de plateforme Cloud d’avoir l’approche « Démarrer petit et développer ». Les équipes ont travaillé pendant des années dans les limites de l’environnement local existant de l'entreprise pour atteindre l’état de maturité actuel en matière de sécurité, d’opérations et de gouvernance. Il faudra du temps pour reproduire les processus, les outils et les architectures souhaités en fonction des nouvelles contraintes d’un environnement cloud. Pour accélérer ce processus d’apprentissage, un point de départ légèrement différent est requis. Si l’on compare l’image ci-dessous avec les [conseils de refactorisation précoce de cette méthodologie](../landing-zone/refactor.md), le changement fondamental réside dans le point de départ, qui est maintenant plus complexe comme décrit plus loin dans cet article.

![Illustration de la refactorisation de la zone d’atterrissage, décrit dans la section suivante de cet article](../../_images/ready/refactor-enterprise-scale.png)

<!-- markdownlint-disable MD026 -->

## <a name="qualifiers-should-i-start-with-enterprise-scale"></a>Qualificateurs : Dois-je commencer avec la mise à l’échelle de l’entreprise ?

Pour la plupart des modèles d’adoption, une approche « Démarrer petit et développer » est préférable, car elle permet à l’équipe d’apprendre à partir d’expériences réelles. Pour les entreprises qui correspondent aux références de cet article, une approche plus robuste est nécessaire.

### <a name="scale-and-speed"></a>Mise à l’échelle et vitesse

Lorsque l’équipe d’adoption a pour objectif à moyen terme (dans les 24 mois) d’héberger plus de 1 000 ressources (applications, infrastructure ou données) dans le cloud, l’apprentissage par des approches pratiques n’est pas suffisant. De multiples critères devront être prédéfinis pour assurer la vitesse et l’échelle de déploiement nécessaires à une grande entreprise.

### <a name="security-compliance-and-culture"></a>Sécurité, conformité et culture

Pour diverses raisons métier, il peut être nécessaire de mettre en place une zone d’atterrissage et une architecture de services partagés d’entreprise préalablement à toute adoption du cloud. La nécessité de disposer d’une solution de zone d’atterrissage à l’échelle de l'entreprise peut être évidente pour les sociétés dont les activités sont construites autour de données sensibles et d’architectures complexes et interdépendantes. Elle peut également être évidente pour les entreprises ayant besoin d’environnements cloud qui répondent à des exigences strictes de tiers avant d’utiliser le cloud. Les entreprises qui s’appuient sur des modèles de contrôle informatique centralisé profondément enracinés peuvent également avoir besoin d’une architecture qui commence par un contrôle centralisé des processus pour répondre aux exigences de contrôle des modifications.

### <a name="all-in-on-the-cloud"></a>Cent pour cent cloud

Le plus souvent, le choix d’une zone d’atterrissage à l’échelle de l’entreprise est motivé par le souhait de migrer l’ensemble des ressources et des processus dans le cloud. Cela peut être dû à l’arrêt d’un centre de donnes ou à un déplacement massif en vue d’améliorer l’agilité de l’entreprise. Quel que soit le pilote, cette décision d’entreprise exige généralement la mise à l’échelle et la rapidité d’adoption. Cette combinaison de demandes fait qu’il est difficile de prendre le temps nécessaire pour apprendre et se préparer à l’hébergement de données sensibles et critiques dans le cloud.

### <a name="skill-requirements"></a>Compétences requises

Une action à l’échelle de l’entreprise implique que l’équipe de la plateforme cloud dispose de budgets qui concernent l’ensemble de l’entreprise. Ce qualificateur part du principe que l’équipe a des compétences cloud plus approfondies que la plupart des autres sociétés. Ces compétences peuvent avoir été acquises lors de l’adoption du cloud à plus petite échelle au sein de l’entreprise. Vous pouvez également ajouter des compétences en attirant du personnel expérimenté ou en travaillant avec des partenaires très expérimentés. Dans les deux cas, les compétences suivantes seront nécessaires pour commencer à l’échelle de l’entreprise.

Compétences suggérées :

- Connaissances approfondies sur l’architecture du fournisseur de services cloud choisi.
- Expérience pratique étendue avec les approches Infrastructure as code basées sur le cloud.
- Bonne connaissance de GitHub ou d’autres référentiels de code source, y compris les stratégies de branchement et de demande de tirage.
- Expérience pratique des déploiements automatisés du code source vers le fournisseur de services cloud.

Si ces compétences ne sont pas disponibles au sein de l’équipe de la plateforme cloud (par le biais du personnel, des partenaires ou d’autres mécanismes de support), une approche « Démarrer petit et développer » est susceptible de préparer plus rapidement l’entreprise grâce des résultats de meilleure qualité. Une telle approche permet d’acquérir des compétences moins coûteuses au sein de l’équipe existante.

## <a name="start-with-an-enterprise-scale-landing-zones"></a>Commencer par une ou des zones d’atterrissage à l’échelle de l’entreprise

Microsoft investit depuis longtemps dans des outils et des approches permettant aux clients de développer et de gérer plus aisément des zones d’atterrissage à l’échelle de l'entreprise. Au cours des dernières années, cet investissement a abouti à des conseils et des outils sur Azure. Cette approche continue et peut entraîner des mises à jour régulières de la présente section.

![Illustration de refactorisation de la zone d’atterrissage](../../_images/ready/refactor-enterprise-scale.png)

Chacun des modèles suivants fournit aux clients une zone d’atterrissage initiale à l’échelle de l'entreprise, y compris des modèles d’infrastructure :

- [Services partagés ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-shared)
- [Charge de travail App Service Environment/SQL Database ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-ase-sql-workload)
- [Gouvernance de UK Official et de UK NHS](https://docs.microsoft.com/azure/governance/blueprints/samples/ukofficial)

Les exemples supplémentaires de l’[article sur les exemples de blueprints Azure](https://docs.microsoft.com/azure/governance/blueprints/samples) peuvent être utilisés en tant que test « Rouge/Vert » pour les zones d’atterrissage à l’échelle de l’entreprise. L’application de ces blueprints permet de garantir qu’un environnement répond aux normes de conformité avant son adoption. Cette approche est ensuite particulièrement utile pour valider les zones d’atterrissage tierces ou partenaires avant d’adopter le cloud :

## <a name="next-steps"></a>Étapes suivantes

Choisissez l’un des plans de zone d’atterrissage à l’échelle de l’entreprise.
Vous pouvez alors vous fonder les mêmes instructions de l’approche [Démarrer petit et développer](./index.md) pour étendre vos zones d’atterrissage à l’échelle de l’entreprise en fonction de vos besoins.

> [!div class="nextstepaction"]
> [Reprenez les conseils de l’approche « Démarrer petit et développer » en utilisant votre zone d’atterrissage à l’échelle de l’entreprise comme source initiale](./index.md)
