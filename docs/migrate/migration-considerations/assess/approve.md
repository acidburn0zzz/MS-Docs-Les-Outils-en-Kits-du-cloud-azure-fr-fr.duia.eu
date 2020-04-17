---
title: Approuver les changements de l’architecture avant la migration
description: Apprenez à classifier les changements de l’architecture quand ils sont nécessaires et à établir des activités d’approbation appropriées.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d59f2d92f6777cd3210de715eb0de217fe9abce8
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80432918"
---
<!-- cSpell:ignore architected ITIL -->

# <a name="approve-architecture-changes-before-migration"></a>Approuver les changements de l’architecture avant la migration

Pendant le processus d’évaluation de la migration, chaque charge de travail est évaluée, conçue et estimée pour développer un plan d’état futur pour la charge de travail. Certaines charges de travail peuvent être migrées vers le cloud sans aucune modification de l’architecture. Maintenir la configuration et l’architecture locales peut réduire les risques et rationaliser le processus de migration. Malheureusement, toutes les applications ne peuvent pas s’exécuter dans le cloud sans modification de l’architecture. Lorsque des changements d’architecture sont requis, cet article peut vous aider à classer la modification et fournir des conseils sur les activités d’approbation appropriées.

## <a name="business-impact-and-approval"></a>Impact commercial et approbation

Pendant la migration, certains éléments sont susceptibles d’être modifiés d’une manière qui aura un impact sur l’entreprise. Bien que la modification ne puisse parfois pas être évitée, les surprises résultant de modifications non divulguées ou non documentées doivent l’être. Pour assurer la prise en charge des parties prenantes tout au long de l’effort de migration, il est important d’éviter les surprises. Prendre à défaut les propriétaires d’applications ou les parties prenantes d’entreprise peut ralentir ou arrêter un effort d’adoption du cloud.

Avant la migration, il est important de préparer le propriétaire de l’entreprise à laquelle appartient la charge de travail à toute modification susceptible d’influencer les processus métier, notamment les modifications apportées aux éléments ci-dessous :

- Contrats de niveau de service.
- Modèles d’accès ou les exigences de sécurité ayant un impact sur l’utilisateur final.
- Pratiques de conservation des données.
- Niveau de performance des applications de base.

Même s’il est possible de migrer une charge de travail avec un minimum de modifications, voire aucune, cela peut toujours avoir un impact sur l’activité. Les processus de réplication peuvent ralentir le niveau de performance des systèmes de production. Les modifications apportées à l’environnement en vue de la migration peuvent entraîner des limitations du niveau de performance du routage ou du réseau. De nombreux impacts supplémentaires peuvent résulter d’activités de réplication, de mise en lots ou de promotion.

Des activités d’approbation régulières permettent de réduire ou d’éviter les surprises suite à un changement ou à des impacts commerciaux découlant du niveau de performance. L’équipe d’adoption du cloud doit exécuter un processus d’approbation des modifications à la fin du processus d’évaluation, avant de commencer le processus de migration.

## <a name="existing-culture"></a>Culture existante

Vos équipes informatiques ont probablement des mécanismes existants pour gérer les changements impliquant vos ressources locales. En général, ces mécanismes sont régis par des processus de gestion des changements basés sur la bibliothèque ITIL (Information Technology Infrastructure Library). Dans de nombreuses migrations d’entreprise, ces processus impliquent un comité consultatif sur les modifications (CAB) qui est chargé de l’examen, de la documentation et de l’approbation de toutes les demandes de modification (RFC) relatives au service informatique.

Le CAB comprend généralement des experts de plusieurs équipes informatiques et métier, proposant une variété de perspectives et un examen détaillé de toutes les modifications liées au service informatique. Un processus d’approbation du CAB est un moyen éprouvé de réduire les risques et l’impact commercial des modifications impliquant des charges de travail stables managées par les opérations informatiques.

## <a name="technical-approval"></a>Approbation technique

L’état de préparation de l’organisation quant à l’approbation des modifications techniques est l’une des raisons les plus courantes de l’échec de la migration vers le cloud. Dans une plateforme cloud, il y a plus de projets bloqués par une série d’approbations techniques que par n’importe quel autre déficit. Préparer l’organisation à l’approbation des modifications techniques est une exigence importante pour la réussite de la migration. Voici quelques-unes des meilleures pratiques pour vous assurer que l’organisation est prête pour l’approbation technique.

### <a name="itil-change-advisory-board-challenges"></a>Défis relatifs au comité consultatif sur les modifications ITIL

Chaque approche de gestion des changements a son propre ensemble de contrôles et de processus d’approbation. La migration est une série de modifications continues qui commencent par un degré élevé d’ambiguïté et améliorent la clarté au cours de l’exécution. Par conséquent, la migration est mieux régie par les approches de gestion des changements basées sur l’agilité, avec l’équipe de stratégie cloud qui agit en tant que directeur de produit.

Toutefois, l’échelle et la fréquence des modifications au cours d’une migration cloud ne sont pas adaptées à la nature des processus ITIL. Les exigences relatives à une approbation du CAB peuvent compromettre la réussite d’une migration, en ralentissant ou en arrêtant l’effort. En outre, aux premiers stades de la migration, l’ambiguïté est grande et l’expertise en la matière tend à être faible. Pour les premières migrations ou mises en production de charges de travail, l’équipe d’adoption du cloud est souvent en mode d’apprentissage. Par conséquent, il peut être difficile pour l’équipe de fournir les types de données nécessaires pour obtenir une approbation du CAB.

Les meilleures pratiques suivantes peuvent aider le CAB à maintenir un certain niveau de confort pendant la migration sans devenir un bloqueur pénible.

### <a name="standardize-change"></a>Normalisation des modifications

Il est tentant pour une équipe d’adoption du cloud d’envisager des décisions architecturales détaillées pour chaque charge de travail migrée vers le cloud. Il est tout aussi tentant d’utiliser la migration cloud comme catalyseur pour refactoriser les décisions architecturales passées. Pour les organisations qui migrent quelques centaines de machines virtuelles ou quelques douzaines de charges de travail, les deux approches peuvent être correctement managées. Lors de la migration d’un centre de données composé d’au moins 1 000 ressources, chacune de ces approches est considérée comme un anti-modèle à haut risque qui réduit considérablement la probabilité de réussite. La modernisation, la refactorisation et la réarchitecture de chaque application nécessitent différents compétences et une grande variété de modifications, et ces tâches créent des dépendances sur les efforts humains à l’échelle. Chacune de ces dépendances introduit des risques dans l’effort de migration.

L’article sur [la rationalisation du patrimoine numérique](../../../digital-estate/rationalize.md) traite de l’impact sur l’agilité et le gain de temps des hypothèses de base lors de la rationalisation d’un patrimoine numérique. La modification standardisée présente un avantage supplémentaire. En choisissant une approche de rationalisation par défaut pour régir l’effort de migration, le comité consultatif cloud ou le directeur de produit peut examiner et approuver l’application d’une modification dans une longue liste de charges de travail. Cela réduit l’approbation technique de chaque charge de travail à celles qui nécessitent une modification d’architecture significative pour être compatible avec le cloud.

### <a name="clarify-expectations-and-roles-of-approvers"></a>Clarification des attentes et des rôles des approbateurs

Avant l’évaluation de la première charge de travail, l’équipe de stratégie cloud doit documenter et communiquer les attentes de toute personne impliquée dans l’approbation des modifications. Cette activité simple peut éviter des retards coûteux lorsque l’équipe d’adoption du cloud est entièrement engagée.

### <a name="seek-approval-early"></a>Demande précoce d’une approbation

Lorsque cela est possible, les modifications techniques doivent être détectées et documentées pendant le processus d’évaluation. Quels que soient les processus d’approbation, l’équipe d’adoption du cloud doit impliquer les approbateurs dès que possible. Plus l’approbation d’une modification peut commencer tôt, moins un processus d’approbation est susceptible de bloquer les activités de migration.

## <a name="next-steps"></a>Étapes suivantes

Avec l’aide de ces meilleures pratiques, il devrait être plus facile d’intégrer une approbation appropriée et à faible risque aux efforts de migration. Une fois les modifications de charge de travail approuvées, l’équipe d’adoption du cloud est prête à [migrer les charges de travail](../migrate/index.md).

> [!div class="nextstepaction"]
> [Migrer des charges de travail](../migrate/index.md)
