---
title: Qu’est-ce que la comptabilité cloud ?
description: Explication du concept de comptabilité cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 008958e0542a52f022bbf2ba3183fbfb8c78b9ee
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806813"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-cloud-accounting"></a>Qu’est-ce que la comptabilité cloud ?

Le cloud change la façon dont les coûts sont comptabilisés par le service informatique, comme indiqué dans la section [Création d’un modèle financier pour la transformation cloud](./financial-models.md). Il est plus facile de prendre en charge différents modèles de comptabilité informatique en raison de la façon dont le cloud alloue les coûts. Il est donc important de comprendre comment comptabiliser les coûts du cloud avant d’entamer un parcours de transformation cloud. Cet article décrit les modèles de comptabilité cloud les plus courants pour l’informatique.

## <a name="traditional-it-accounting-cost-center-model"></a>Comptabilité informatique classique (modèle de centre de coûts)

Il est souvent juste de considérer l’informatique comme un centre de coûts. Dans le modèle de comptabilité informatique classique, l’informatique consolide le pouvoir d’achat de toutes les ressources informatiques. Comme nous l’avons souligné dans l’article sur les [modèles financiers](./financial-models.md), la consolidation du pouvoir d’achat peut inclure les licences logicielles, les frais récurrents des licences CRM, l’achat de postes de travail pour les employés ainsi que d’autres coûts importants.

Quand l’informatique sert de centre de coûts, sa valeur est largement perçue sous l’angle de la gestion des approvisionnements. En raison de cette perception, il est difficile pour le conseil d’administration ou les autres dirigeants de comprendre la véritable valeur de l’informatique. Les coûts d’approvisionnement tendent à fausser la perception de l’informatique en l’emportant sur toute autre valeur ajoutée par l’organisation. Cette vision explique pourquoi l’informatique est souvent associée aux responsabilités du directeur financier ou du directeur de l’exploitation. Cette perception de l’informatique est limitée, voire réductrice.

## <a name="central-it-accounting-profit-center-model"></a>Comptabilité du service informatique central (modèle de centre de profits)

Pour dépasser la vision de centre de coûts de l’informatique, certains DSI (directeurs des systèmes d’information) ont opté pour un modèle de comptabilité du service informatique central. Dans ce type de modèle, l’informatique est traitée comme une unité commerciale concurrente et en tant qu’homologue des unités commerciales génératrices de revenus. Dans certains cas, ce modèle peut être entièrement logique. Par exemple, certaines organisations ont une division des services informatiques professionnels qui génère un flux de revenus. Bien souvent, les modèles du service informatique central ne génèrent pas de revenus significatifs, ce qui rend leur justification difficile.

Quel que soit le modèle de revenus, les modèles de comptabilité du service informatique central sont uniques en raison de la manière dont l’unité informatique comptabilise les coûts. Dans un modèle informatique classique, l’équipe informatique enregistre les coûts et les paie à partir de fonds partagés, par exemple un compte d’opérations de maintenance ou un compte de pertes et profits dédié.

Dans un modèle de comptabilité du service informatique central, l’équipe informatique recense les services fournis pour comptabiliser les frais généraux, les frais de gestion et les autres dépenses estimées. Elle facture ensuite les unités commerciales concurrentes pour les services recensés. Dans ce modèle, le DSI est censé gérer le P&L (pertes et profits) associé à la vente de ces services. Cela peut entraîner une inflation des coûts informatiques ainsi que des conflits entre le service informatique central et les unités commerciales, en particulier quand le service informatique doit réduire les coûts ou quand il ne respecte pas les SLA (contrats de niveau de service) convenus. En période de changement de technologie ou de marché, l’introduction d’une nouvelle technologie perturbe le P&L du service informatique central, ce qui rend la transformation difficile.

## <a name="chargeback"></a>Facturation interne

L’une des premières étapes usuelles pour changer la réputation de l’informatique en tant que centre de coûts consiste à implémenter un modèle de comptabilité par facturation interne. Ce modèle est particulièrement répandu dans les petites entreprises ou les organisations informatiques très efficaces. Dans le modèle basé sur la facturation interne, tous les coûts informatiques associés à une unité commerciale spécifique sont traités comme des dépenses d’exploitation au sein du budget de cette unité. Cette pratique réduit les effets de coûts cumulés sur l’informatique, ce qui permet aux valeurs métier d’être mieux visibles.

Dans un modèle local hérité, la facturation interne est difficile à effectuer, car une personne doit encore assumer les importantes dépenses en capital ainsi que l’amortissement. La conversion continue des dépenses en capital en dépenses d’exploitation associées à l’utilisation est un exercice comptable difficile. Cette difficulté est l’une des principales raisons de la création du modèle de comptabilité informatique classique et du modèle de comptabilité du service informatique central. Le modèle des dépenses d’exploitation de la comptabilité cloud est quasiment indispensable si vous souhaitez fournir un modèle de facturation interne de manière efficace.

Toutefois, vous ne devez pas implémenter ce modèle sans prendre en compte ses implications. Voici quelques conséquences spécifiques à un modèle de facturation interne :

- La facturation interne entraîne une réduction massive du budget informatique global. Pour les organisations informatiques inefficaces ou nécessitant de nombreuses compétences techniques complexes dans les domaines de l’exploitation ou de la maintenance, ce modèle peut exposer les dépenses de manière non saine.
- La perte de contrôle est une conséquence courante. Dans des environnements hautement politiques, la facturation interne peut entraîner une perte de contrôle et la réallocation des équipes de l’entreprise. Cela peut entraîner une perte d’efficacité importante et réduire la capacité du service informatique à respecter de manière cohérente les SLA (contrats de niveau de service) ou les exigences des projets.
- La difficulté à comptabiliser les services partagés est une autre conséquence courante. Si l’organisation s’est développée grâce à des acquisitions, ce qui implique qu’elle a une dette technique, il est probable qu’un pourcentage élevé de services partagés doit être maintenu pour que tous les systèmes continuent à fonctionner efficacement.

Les transformations cloud incluent des solutions à ces conséquences et à d’autres conséquences associées à un modèle de facturation interne. Mais chacune de ces solutions inclut des dépenses d’implémentation et des dépenses d’exploitation. Le DSI et le directeur financier doivent évaluer soigneusement les avantages et les inconvénients d’un modèle de facturation interne avant d’envisager ce dernier.

## <a name="showback-or-awareness-back"></a>Facturation interne ou récupération des données de facturation

Pour les grandes entreprises, un modèle de récupération des données de facturation est une première étape plus sûre dans la transition du centre de coûts au centre de valeurs. Ce modèle n’affecte pas la comptabilité financière. En fait, les P&L de chaque organisation ne changent pas. Le plus grand changement a lieu au niveau de l’état d’esprit et de la prise de conscience. Dans un modèle de récupération des données de facturation, le service informatique gère le pouvoir d’achat centralisé et consolidé en tant qu’agent pour l’entreprise. Dans les rapports renvoyés à l’entreprise, le service informatique attribue tous les coûts directs à l’unité commerciale concernée, ce qui permet de réduire le budget perçu directement consommé par le service informatique. Le service informatique planifie également les budgets en fonction des besoins des unités commerciales associées, ce qui permet au service informatique de comptabiliser plus précisément les coûts associés aux initiatives purement informatiques.

Ce modèle offre un équilibre entre un véritable modèle de facturation interne et des modèles plus classiques de comptabilité informatique.

## <a name="impact-of-cloud-accounting-models"></a>Impact des modèles de comptabilité cloud

Le choix des modèles de comptabilité est crucial dans la conception du système. Le choix du modèle de comptabilité peut affecter les stratégies d’abonnement, les standards de nommage, les standards d’étiquetage ainsi que les conceptions de stratégie et de blueprint.

Une fois que vous avez vu avec l’entreprise les décisions à prendre concernant le modèle de comptabilité cloud et les [marchés mondiaux](./global-markets.md), vous avez suffisamment d’informations pour [développer une fondation Azure](../ready/index.md).

> [!div class="nextstepaction"]
> [Développer une fondation Azure](../ready/index.md)
