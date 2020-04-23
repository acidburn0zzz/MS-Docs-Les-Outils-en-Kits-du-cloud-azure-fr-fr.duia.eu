---
title: Valider les hypothèses d’évaluation avant la migration
description: Découvrez comment valider les hypothèses d’évaluation avant de commencer la migration vers le cloud à l’aide du Cloud Adoption Framework pour Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: cc095a1751e945ca18763757582a6cd27b65d72a
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81119763"
---
# <a name="assess-workloads-and-validate-assumptions-before-migration"></a>Évaluer les charges de travail et valider les hypothèses avant la migration

Bon nombre de vos charges de travail existantes sont des candidates idéales pour la migration vers le cloud, mais toutes les ressources ne sont pas compatibles avec les plateformes cloud et certaines charges de travail ne tirent aucun profit de l’hébergement dans le cloud. La [planification du patrimoine numérique](../../../digital-estate/index.md) vous permet de générer un [backlog de migration](../prerequisites/technical-complexity.md#migration-backlog-aligning-business-priorities-and-timing) global des charges de travail potentielles à migrer. Toutefois, cet effort de planification est global. Il s’appuie sur des hypothèses formulées par l’équipe de stratégie cloud et n’explore pas en profondeur les considérations techniques.

Par conséquent, avant de migrer une charge de travail vers le cloud, il est important d’évaluer l’adéquation des ressources individuelles associées à cette charge de travail pour déterminer si elles sont aptes à être migrées. Au cours de cette évaluation, votre équipe d’adoption du cloud doit évaluer la compatibilité technique, l’architecture nécessaire, les attentes en matière de performances/dimensionnement ainsi que les dépendances, pour garantir que la charge de travail migrée peut être déployée efficacement dans le cloud.

*Évaluer* est la première des quatre activités incrémentielles qui ont lieu dans une itération. Comme indiqué dans l’article des prérequis traitant [de la complexité technique et de la gestion des changements](../prerequisites/technical-complexity.md), vous devez décider à l’avance de la manière dont cette phase doit être exécutée. Déterminez en particulier si les évaluations seront effectuées par l’équipe d’adoption du cloud durant le même sprint que l’effort de migration réel. Sinon, décidez si un modèle de type « vague » ou « usine » sera utilisé pour effectuer les évaluations dans une itération séparée. Si certains membres n’ont pas de connaissances élémentaires sur ces processus, il peut être judicieux de revisiter la section sur les [prérequis](../prerequisites/index.md).

## <a name="objective"></a>Objectif

L’objectif est d’évaluer un candidat à la migration en examinant la charge de travail, les ressources associées et les dépendances avant la migration.

## <a name="definition-of-done"></a>Définition de « *terminé* »

Ce processus est terminé quand les tâches suivantes ont été accomplies pour chaque candidat à la migration :

- Définition du passage de l’emplacement local au cloud, notamment la sélection de l’approche concernant la promotion de la charge de travail en vue de son utilisation en production.
- Exécution de l’ensemble des approbations, changements, estimations de coûts ou processus de validation nécessaires pour permettre à l’équipe d’adoption du cloud d’effectuer la migration.

## <a name="accountability-during-assessment"></a>Responsabilité de l’évaluation

L’équipe d’adoption du cloud est responsable de l’ensemble du processus d’évaluation. Cependant, les membres de l’équipe de stratégie cloud ont quelques responsabilités qui sont listées dans la section suivante.

## <a name="responsibilities-during-assessment"></a>Obligations liées à l’évaluation

En plus de la responsabilité d’ensemble, certaines actions doivent être affectées directement à un individu ou à un groupe. Voici quelques-unes des activités qui doivent être confiées à des parties responsables :

- **Priorité de l’entreprise.** L’équipe comprend le but de la migration de cette charge de travail, notamment tout impact prévu sur l’entreprise.
  - Un membre de l’équipe de stratégie cloud doit assumer la responsabilité finale de cette activité, sous la direction de l’équipe d’adoption du cloud.
- **Alignement des parties prenantes.** L’équipe aligne les attentes et les priorités avec les parties prenantes internes, identifiant ainsi les critères de réussite de la migration. À quoi ressemble une migration réussie ?
- **Rationalisation optimisée.** Les hypothèses initiales sont évaluées par rapport à la rationalisation. Une [approche de rationalisation](../../../digital-estate/rationalize.md) différente doit-elle être utilisée pour la migration de cette charge de travail spécifique ?
- **Décisions de modernisation.** Quelle que soit la décision de rationalisation, les diverses ressources dans la charge de travail doivent-elles être modernisées pour utiliser des solutions PaaS ?
- **Coût.** Le coût de l’architecture cible a été estimé et le budget global ajusté.
- **Prise en charge de la migration.** L’équipe a décidé de la manière dont le travail technique de la migration sera effectué, notamment pour déterminer qui du partenaire ou de Microsoft sera chargé du support.
- **Évaluation.** La charge de travail est évaluée pour déterminer sa compatibilité et ses dépendances.
  - Cette activité doit être confiée à un expert en la matière qui connaît bien l’architecture et les opérations de la charge de travail candidate.
- **Architecte.** L’équipe a convenu de l’architecture finale pour la charge de travail migrée.
- **Outils de migration.** Selon les approches de modernisation et d’architecture, différents outils de migration sont disponibles pour automatiser la migration. Avec l’architecture proposée, cette migration utilisera-t-elle les [outils de migration](../../../decision-guides/migrate-decision-guide/index.md) les plus adaptés ?
- **Alignement du backlog.** L’équipe d’adoption du cloud passe en revue les exigences et s’engage à migrer la charge de travail candidate. Après l’engagement, le backlog des versions et celui des itérations doivent être mis à jour en conséquence.
- **Structure de répartition du travail ou rétroplanning.** L’équipe établit un calendrier des principales étapes afin d’identifier les objectifs de finalisation des processus de planification, d’implémentation et d’examen.
- **Approbation finale.** Tous les approbateurs nécessaires ont examiné le plan et ont approuvé l’approche en matière de migration de la ressource.
  - Pour éviter les surprises plus tard dans le processus, au moins un représentant de l’entreprise doit être impliqué dans le processus d’approbation.

> [!CAUTION]
> Cette liste complète de responsabilités et d’actions peut prendre en charge des migrations vastes et complexes impliquant plusieurs rôles avec différents niveaux de responsabilité et nécessitant un processus d’approbation détaillé. Les efforts de migration moins intenses et plus simples peuvent ne pas nécessiter l’ensemble des rôles et des actions décrits ici. Pour distinguer les activités qui ajoutent de la valeur de celles qui ne sont pas nécessaires, vos équipes d’adoption du cloud et de stratégie cloud doivent utiliser ce processus complet dans le cadre de votre première migration de charge de travail. Une fois la charge de travail vérifiée et testée, l’équipe peut évaluer ce processus et choisir les actions à utiliser par la suite.

## <a name="next-steps"></a>Étapes suivantes

Grâce aux connaissances générales que vous venez d’acquérir sur le processus d’évaluation, vous pouvez à présent [classifier les charges de travail](./classify.md).

> [!div class="nextstepaction"]
> [Classifier les charges de travail](./classify.md)
