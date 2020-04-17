---
title: Prérequis pour la migration
description: Découvrez les prérequis qui vous aideront à préparer la migration vers le cloud, et qui vous permettront d’éviter les échecs de migration les plus courants.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ddbd2374cea98d08760e53eba885171aa854ed17
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80429024"
---
# <a name="prerequisites-for-migration"></a>Prérequis pour la migration

Avant de commencer les migrations, vous devez préparer votre _environnement_ cible de migration pour les changements à venir. Dans ce cas, l’environnement fait référence à la base technique dans le cloud. L’environnement fait également référence à l’environnement d’entreprise et à l’état d’esprit menant à la migration. De même, l’environnement inclut la culture des équipes exécutant les changements et de celles recevant la sortie. Le manque de préparation à ces changements est la raison la plus courante de l’échec des migrations. Cette série d’articles vous guide tout au long des prérequis suggérés pour préparer l’environnement.

## <a name="objective"></a>Objectif

L’objectif est de vérifier l’état de préparation des parties métier, culturelle et technique de l’entreprise avant le lancement d’un plan de migration itératif.

## <a name="review-business-drivers"></a>Passer en revue les facteurs opérationnels

Avant de lancer une migration vers le cloud, passez en revue les conseils associés aux étapes [Planifier](../../../strategy/index.md) et [Préparer](../../../ready/index.md) du Framework d’adoption du cloud pour vérifier que votre organisation est disposée à participer aux processus d’adoption du cloud et de migration vers le cloud. Examinez en particulier les impératifs de l’entreprise et les résultats attendus qui sous-tendent la migration :

- [Prise en main : Migrer](../../../getting-started/migrate.md)
- [Pourquoi migrons-nous vers le cloud ?](../../../strategy/motivations.md)

## <a name="definition-of-done"></a>Définition de « *terminé* »

Les prérequis sont terminés quand les conditions suivantes sont satisfaites :

- **État de préparation de la partie métier.** L’équipe de stratégie cloud a défini et hiérarchisé un backlog général de la migration représentant la partie du patrimoine numérique à migrer au cours des deux ou trois prochaines mises en production. Les équipes de stratégie cloud et d’adoption du cloud ont convenu d’une stratégie initiale pour gérer le changement.
- **État de préparation de la partie culturelle.** Les rôles, responsabilités et attentes de l’équipe d’adoption du cloud, de l’équipe de stratégie cloud et des utilisateurs affectés ont fait l’objet d’un accord quant aux charges de travail à migrer au cours des deux ou trois prochaines mises en production.
- **État de préparation de la partie technique.** La zone d’accueil (ou espace d’hébergement alloué dans le cloud) qui recevra les ressources migrées répond à la configuration minimale requise pour héberger la première charge de travail migrée.

> [!CAUTION]
> La préparation est essentielle à la réussite d’une migration. Cependant, une préparation excessive peut conduire à une *paralysie de l’analyse*, où trop de temps consacré à la planification peut sérieusement retarder un effort de migration. Les processus et prérequis définis dans cette section sont destinés à vous aider à prendre des décisions, mais veillez à ce qu’ils ne vous empêchent pas de faire des progrès significatifs.
>
> Choisissez une charge de travail relativement simple pour votre migration initiale. Utilisez les processus décrits dans cette section pour planifier et implémenter cette première migration. Ce premier effort de migration va rapidement démontrer les principes du cloud à votre équipe et les forcer à se familiariser avec son fonctionnement. À mesure que votre équipe acquiert de l’expérience, intégrez ces enseignements lors de migrations plus vastes et plus complexes.

## <a name="accountability-during-prerequisites"></a>Responsabilité des prérequis

Deux équipes sont responsables des tâches de préparation en vue du respect des prérequis :

- **Équipe de stratégie cloud :** Cette équipe est chargée d’identifier et de hiérarchiser les deux ou trois premières charges de travail susceptibles d’être candidates à la migration.
- **Équipe d’adoption du cloud :** Cette équipe est chargée de valider l’état de préparation de l’environnement technique et la faisabilité de la migration des charges de travail proposées.

Un seul membre de chaque équipe doit être identifié comme responsable de chacune des trois définitions des déclarations « terminé » dans la section précédente.

## <a name="responsibilities-during-prerequisites"></a>Obligations durant les prérequis

En plus de la responsabilité d’ensemble, certaines actions doivent être affectées directement à un individu ou à un groupe. Voici quelques-unes de ces obligations qui ont une incidence sur ces activités :

- **Définition des priorités métier.** Prenez des décisions concernant les charges de travail à migrer et les contraintes de temps générales. Pour plus d’informations, passez en revue les [motivations qui poussent une entreprise à migrer vers le cloud](../../../strategy/motivations.md).
- **État de préparation de la gestion des changements.** Établissez et communiquez le plan de suivi des changements techniques pendant la migration.
- **Alignement avec les utilisateurs professionnels.** Établissez un plan visant à prédisposer la communauté des utilisateurs professionnels à l’exécution de la migration.
- **Inventaire et analyse du patrimoine numérique.** Exécutez les outils nécessaires pour inventorier et analyser le patrimoine numérique. Pour plus d’informations, consultez la discussion portant sur le [patrimoine numérique](../../../digital-estate/index.md) dans le Framework d’adoption du cloud.
- **État de préparation du cloud.** Évaluez l’environnement de déploiement cible pour vérifier qu’il est conforme aux exigences des premières charges de travail candidates. Pour plus d’informations, consultez le [guide de configuration Azure](../../../ready/azure-setup-guide/index.md).

Les articles restants de cette série vous aident à respecter chacune de ces obligations.

## <a name="next-steps"></a>Étapes suivantes

Grâce aux connaissances générales que vous venez d’acquérir sur les prérequis, vous pouvez à présent [prendre les premières décisions en matière de migration](./decisions.md).

> [!div class="nextstepaction"]
> [Premières décisions en matière de migration](./decisions.md)
