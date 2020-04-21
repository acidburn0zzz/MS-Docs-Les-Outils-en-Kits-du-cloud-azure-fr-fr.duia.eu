---
title: Amélioration de la discipline de gestion des coûts
description: Découvrez les tâches qu’une entreprise peut effectuer pour développer et faire évoluer sa discipline de gestion des coûts à chaque phase d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 02d76581a49f58358d624ded4add1af180964f16
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81120388"
---
# <a name="cost-management-discipline-improvement"></a>Amélioration de la discipline de gestion des coûts

La discipline Gestion des coûts vise à lever les principaux risques métier liés aux dépenses à engager pour l’hébergement des charges de travail cloud. Parmi les Cinq disciplines de la gouvernance cloud, la gestion des coûts est impliquée dans le contrôle des coûts et l’utilisation des ressources cloud dans l’optique de créer et maintenir un cycle de coûts planifié.

Cet article décrit les tâches que votre entreprise est susceptible d’effectuer pour développer et affiner la discipline de gestion des coûts. Ces tâches peuvent être divisées en phases de planification, de création, d’adoption et d’exploitation de l’implémentation d’une solution cloud. Les tâches sont ensuite répétées pour permettre le développement d’une [approche incrémentielle de la gouvernance cloud](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatre phases d’adoption](../../_images/govern/adoption-phases.png)

*Figure 1 - Phases d’adoption de l’approche incrémentielle de la gouvernance cloud.*

Un seul document ne peut pas prendre en compte les exigences de toutes les entreprises. Par conséquent, cet article présente des exemples d’activités minimales et potentielles suggérés pour chaque phase du processus de maturation de la gouvernance. L’objectif initial de ces activités est de vous aider à générer un [produit minimum viable (MVP) de stratégie](../guides/index.md#an-incremental-approach-to-cloud-governance) et à établir un framework pour une amélioration incrémentielle de la stratégie. Votre équipe de gouvernance cloud devra décider de la part d’investissement qu’elle est prête à consentir dans ces activités pour améliorer vos capacités de gouvernance en matière de gestion des coûts.

> [!CAUTION]
> Les activités minimales ou potentielles décrites dans cet article ne correspondent pas spécialement à des stratégies d’entreprise spécifiques ou à des exigences de conformité de tiers. Ces conseils visent à favoriser les échanges qui conduiront à un alignement des deux exigences avec un modèle de gouvernance cloud.

## <a name="planning-and-readiness"></a>Planification et préparation

Cette phase de maturité de la gouvernance comble le fossé entre les résultats opérationnels et les stratégies concrètes. Au cours de ce processus, l’équipe de direction définit des métriques spécifiques, les mappe au patrimoine numérique, et commence à planifier l’effort global de migration.

**Activités minimales suggérées :**

- Évaluer vos options de [chaîne d’outils de gestion des coûts](./toolchain.md).
- Élaborer un brouillon de recommandations relatives à l’architecture et distribuer ce document aux principales parties prenantes.
- Sensibiliser et impliquer les personnes et les équipes concernées par le développement des recommandations relatives à l’architecture.

**Activités potentielles :**

- Arrêter les décisions budgétaires qui vont dans le sens de votre stratégie cloud.
- Valider les métriques d’apprentissage que vous utilisez pour rendre compte de l’affectation réussie de fonds.
- Comprendre le modèle comptable cloud souhaité qui va déterminer la façon dont les coûts du cloud sont comptabilisés.
- Se familiariser avec le plan de gestion du patrimoine numérique et valider les attentes précises en matière de coûts.
- Évaluer les options d’achat pour déterminer s’il est préférable d’opter pour un paiement à l’utilisation ou pour un pré-engagement en souscrivant un Contrat Entreprise.
- Mettre en adéquation les objectifs de l’entreprise avec les budgets planifiés et ajuster éventuellement les plans budgétaires.
- Mettre au point un mécanisme de communication des objectifs et des décisions budgétaires pour notifier les parties prenantes techniques et opérationnelles à la fin de chaque cycle de coût.

## <a name="build-and-predeployment"></a>Génération et prédéploiement

Plusieurs conditions techniques et non techniques sont exigées pour migrer correctement un environnement. Ce processus porte essentiellement sur les décisions, la préparation et l’infrastructure qui sert de base à la migration.

**Activités minimales suggérées :**

- Implémenter votre [chaîne d’outils de gestions des coûts](./toolchain.md) en la déployant lors d’une phase de prédéploiement.
- Mettre à jour les recommandations relatives à l’architecture et distribuer le document aux principales parties prenantes.
- Élaborer une documentation et des ressources pédagogiques, des messages de sensibilisation, des incitations et d’autres programmes afin de favoriser l’adoption par les utilisateurs.
- Déterminer l’adéquation de vos exigences d’achats avec vos budgets et objectifs.

**Activités potentielles :**

- Calquer vos plans budgétaires sur la [stratégie d’abonnement](../../decision-guides/subscriptions/index.md) qui définit votre modèle de possession de base.
- Utilisez la [stratégie de cohérence des ressources](../../decision-guides/resource-consistency/index.md) pour appliquer les recommandations relatives à l’architecture et aux coûts dans le temps.
- Déterminer s’il existe des anomalies au niveau des coûts qui contrarient vos plans de migration et d’adoption.

## <a name="adopt-and-migrate"></a>Adoption et migration

La migration est un processus incrémentiel qui porte essentiellement sur le déplacement, le test et l’adoption d’applications ou de charges de travail dans un patrimoine numérique.

**Activités minimales suggérées :**

- Migrer votre [chaîne d’outils de gestion des coûts](./toolchain.md) du prédéploiement à la production.
- Mettre à jour les recommandations relatives à l’architecture et distribuer le document aux principales parties prenantes.
- Élaborer une documentation et des ressources pédagogiques, des messages de sensibilisation, des incitations et d’autres programmes afin de favoriser l’adoption par les utilisateurs.

**Activités potentielles :**

- Implémenter votre modèle comptable cloud.
- Veiller à ce que vos budgets reflètent vos dépenses réelles à chaque phase de mise en production et les ajuster si nécessaire.
- Surveiller les changements apportés aux plans budgétaires et les valider avec les parties prenantes si des approbations supplémentaires sont nécessaires.
- Mettez à jour les recommandations relatives à l’architecture en fonction des coûts réels.

## <a name="operate-and-post-implementation"></a>Exploitation et post-implémentation

Une fois la transformation terminée, la gouvernance et les opérations doivent perdurer tout au long du cycle de vie naturel d’une application ou d’une charge de travail. Cette phase de maturité de la gouvernance est centrée sur les activités qui interviennent généralement après l’implémentation de la solution et le début de stabilisation du cycle de transformation.

**Activités minimales suggérées :**

- Personnaliser votre [chaîne d’outils de gestion des coûts](./toolchain.md) en fonction de l’évolution des besoins de votre organisation en gestion de coûts.
- Envisager l’automatisation des notifications et des rapports à mesure que les dépenses réelles évoluent.
- Affiner les recommandations relatives à l’architecture pour orienter les futurs processus d’adoption.
- Sensibiliser régulièrement les équipes concernées pour assurer leur adhérence continue aux recommandations d’architecture.

**Activités potentielles :**

- Effectuer un examen opérationnel du cloud tous les trimestres et communiquer la valeur apportée à l’entreprise et les coûts associés.
- Ajuster les plans tous les trimestres en fonction de l’évolution des dépenses réelles.
- Déterminer si, d’un point de vue financier, les abonnements des divisions sont dans la lignée des comptes de résultats.
- Analyser les méthodes de communication de la valeur et des coûts aux parties prenantes une fois par mois.
- Remédier au problème des ressources sous-utilisées et déterminer s’il est intéressant de les conserver.
- Détecter les distorsions et les anomalies entre le plan et les dépenses réelles.
- Aider les équipes d’adoption du cloud et l’équipe de stratégie cloud à comprendre et à résoudre ces anomalies.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous comprenez le concept de gouvernance des coûts du cloud, passez en revue les [meilleures pratiques en matière de gestion des coûts](./best-practices.md) pour trouver des moyens de réduire vos dépenses globales.

> [!div class="nextstepaction"]
> [Meilleures pratiques en matière de gestion des coûts](./best-practices.md)
