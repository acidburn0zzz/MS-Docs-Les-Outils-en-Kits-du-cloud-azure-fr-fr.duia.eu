---
title: Qu’est-ce qu’une zone d’accueil ?
description: Découvrez en quoi les zones d’accueil constituent les éléments constitutifs de tout environnement d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: de1fef059841fe013163f822c9188b7ed5b64a29
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83755698"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-a-landing-zone"></a>Qu’est-ce qu’une zone d’accueil ?

L’infrastructure en tant que code (IaC) est une exigence commune pour la plupart des opérations d’adoption du cloud. Le passage à la création d’un environnement axé sur le code peut ajouter une courbe d’apprentissage pour les membres de l’équipe et nécessiter des modifications de certains aspects des opérations, de la sécurité, de la gouvernance et de la conformité. Le déploiement de zones d’atterrissage discrètes sur mesure permet d’aplatir ces courbes et de laisser l’équipe poursuivre ses plans d’adoption. Cet article définit le sens du terme _zone d’accueil_ et d’autres termes connexes. D’autres articles de cette série vous guideront dans la création de zones d’atterrissage.

## <a name="prerequisite-to-landing-zone-deployment"></a>Prérequis au déploiement d’une zone d’atterrissage

Avant de définir des zones d’atterrissage, il est important de comprendre un terme connexe : _fondation de plateforme_. Dans n’importe quel environnement (cloud, local ou hybride), vous trouverez un ensemble _d’utilitaires de fondation_ qui soutiennent toutes les différentes charges de travail. L’entreprise a besoin des charges de travail pour fonctionner. L’informatique a besoin de ces utilitaires fondamentaux pour gérer, régir et sécuriser le _portefeuille_ complet de charges de travail. Pour plus d’informations sur ces termes et la façon dont ils sont liés, consultez [Hiérarchie du portefeuille](../../reference/fundamental-concepts/hosting-hierarchy.md).

**Fondation de plateforme :** Avant de déployer des zones d’atterrissage, des contrôles centralisés pour l’identité, la sécurité, les opérations, la conformité et la gouvernance sont supposés être fournis à la zone d’atterrissage à partir d’une _fondation de plateforme_ partagée qui prend en charge toutes les charges de travail de cette plateforme cloud spécifique. Toutes les charges de travail au sein de chaque zone d’atterrissage sont régies par ces contrôles centraux pour établir une base de référence cohérente sur les _piliers de l’architecture partagée_, à savoir la sécurité, la fiabilité, les performances, les coûts et les opérations cloud.

**Séparation des responsabilités :** Il doit y avoir une séparation claire des responsabilités entre le travail focalisé sur la charge de travail qui se déroule au sein d’une zone d’atterrissage et l’exploitation des utilitaires qui sont gérés en dehors de la zone d’atterrissage. Cette séparation des responsabilités garantit une gouvernance et une conformité appropriées. Elle garantit également que chaque équipe discute et considère toutes les exceptions à la stratégie d’entreprise pour éviter la création prématurée de solutions de contournement qui pourraient compromettre votre environnement.

> [!CAUTION]
> La séparation des responsabilités ne doit pas décourager les équipes à utiliser cette bonne pratique uniquement sur la base actuelle de l’allocation du personnel ou des structures d’équipe. Lors de l’adoption précoce du cloud, une équipe d’adoption unique peut conserver temporairement toutes les responsabilités liées à l’adoption de la technologie cloud et à la gouvernance, la sécurité et les opérations pour un petit nombre de charges de travail. Si le plan à terme comprend la séparation des responsabilités, voire l’isolation des tâches, cette approche est toujours la bonne pratique recommandée.

**Responsabilités partagées :** La _fondation de plateforme_ fournit des contrôles centralisés pour régir la plateforme cloud. Il existe toujours une responsabilité partagée entre tous les membres de l’équipe pour prendre en compte les exigences en matière d’identité, de sécurité, d’exploitation, de conformité et de gouvernance. Avant d’adopter une technologie dans une zone d’atterrissage, vous devez comprendre quels sont les utilitaires fournis par la _fondation de plateforme_ et ce que vous devrez implémenter dans la zone d’atterrissage pour assumer vos responsabilités partagées.

> [!IMPORTANT]
> Les développeurs et les architectes qui déploient des solutions au sein d’une zone d’atterrissage peuvent se référer à [Microsoft Azure Well-Architected Framework](https://docs.microsoft.com/azure/architecture/framework/) pour incorporer et développer ces piliers d’architecture partagée lors de la conception, de la construction ou de la prise en charge des charges de travail qui s’exécutent dans une zone d’atterrissage.

## <a name="landing-zone-definition"></a>Définition de la zone d’accueil

Une _zone d’atterrissage_ est un segment d’un environnement cloud qui a été préconfiguré par code et qui est dédié à la prise en charge **d’une ou de plusieurs charges de travail**. Les zones d’atterrissage fournissent un accès à des outils et des contrôles fondamentaux qui en font un endroit propice à l’innovation et à la création de nouvelles charges de travail dans le cloud ou à la migration de charges de travail existantes vers le cloud. Les zones d’atterrissage utilisent des ensembles définis de services cloud et des meilleures pratiques pour vous aider à réussir.

Plus précisément, une zone atterrissage est l’élément constitutif de tout environnement d’adoption du cloud. Le terme _zone d’atterrissage_ fait référence à une construction logique qui permet aux charges de travail de coexister sur une _fondation de plateforme_. Ensemble, les zones d’atterrissage et la fondation de plateforme capturent tout ce qui doit être en place et prêt pour permettre l’adoption du cloud dans le portefeuille informatique.

**Étendue :** Une zone d’atterrissage pleinement opérationnelle prend en compte tous les utilitaires de plateforme requis pour répondre aux besoins d’adoption du client.

**Refactorisation :** une zone d’accueil pleinement opérationnelle est le livrable final de toutes les itérations de la méthodologie Préparer du Framework d’adoption du cloud. À chaque itération, le code base qui définit la zone d’accueil est refactorisé ou étendu. Après la refactorisation, la zone d’accueil peut être modifiée ou redéployée pour être adaptée à de nouveaux besoins d’adoption du cloud.

**Objectif :** L’objectif de l’approche de zone d’atterrissage est de créer un ensemble commun d’implémentations de plateforme cohérentes qui permettent aux équipes d’adoption de s’appuyer sur une _fondation de plateforme_ gérée de manière centralisée. Ces implémentations cohérentes doivent être mises en place pour que vos applications puissent accéder aux composants dont elles auront besoin une fois déployées. Chaque itération de zone d’accueil doit donc être conçue et déployée en conformité avec les exigences du plan d’adoption du cloud et de la stratégie de conception des abonnements.

**Objectif principal :** La zone d’accueil a pour principal objectif de garantir que « l’ossature » requise ou autres utilitaires sont déjà en place quand une application arrive dans le cloud.

**Avantages :** Ensemble, les zones d’atterrissage et la fondation de plateforme commune créent une cohérence dans les _piliers de l’architecture partagée_, à savoir la sécurité, la fiabilité, les performances, les coûts et les opérations cloud. Cette combinaison réduit également la charge requise pour maintenir les opérations, la gouvernance et la conformité dans le portefeuille informatique. À mesure que les exigences d’adoption évoluent, les zones d’atterrissage réduisent la refactorisation et le déploiement requis pour adapter vos besoins d’adoption.

## <a name="landing-zone-usage"></a>Utilisation des zones d’accueil

Les zones d’accueil ne sont pas obligatoirement différentes pour les environnements d’adoption IaaS et PaaS. Toutefois, les zones d’accueil sont spécialement conçues pour prendre en charge le plan d’adoption qui est conforme à la stratégie d’abonnement. La prise en charge du plan d’adoption peut nécessiter l’utilisation de plusieurs zones d’accueil avec une combinaison de composants requis.

L’objectif et l’étendue du plan d’adoption global du cloud définissent « l’ossature » requise. D’autres exigences en matière de gouvernance, de conformité, de sécurité et de gestion opérationnelle sont généralement ajoutées à l’étendue initiale des zones d’accueil. Durant les premières phases de l’adoption, les zones d’accueil peuvent nécessiter une « ossature » plus légère en raison des exigences définies et des risques acceptables. Quand il y a plusieurs zones d’accueil, la pratique courante est que chaque zone d’accueil dépende des hubs qui fournissent les contrôles requis par le biais d’un modèle de services partagés.

## <a name="decentralized-operations"></a>Opérations décentralisées

Dans certaines organisations décentralisées, les conceptions d’adoption exigent des équipes de charge de travail qui sont **seules responsables** de l’implémentation et de l’exploitation de chaque charge de travail isolée, y compris la sécurité, la gouvernance, la gestion des opérations et d’autres fonctions. Pour ces équipes, une charge de travail peut avoir son propre environnement séparé, sans dépendances vis-à-vis d’une fondation de plateforme. Ces environnements spécifiques à la charge de travail ont des implémentations de sécurité, de fiabilité, de performances, de coûts et de cloud incohérentes. Par conséquent, ils ne doivent pas être désignés comme des zones d’atterrissage. Ces équipes doivent rechercher des conseils dans [Microsoft Azure Well-Architected Framework](https://docs.microsoft.com/azure/architecture/framework/) afin de concevoir, générer et optimiser chaque charge de travail de manière indépendante.

> [!IMPORTANT]
> Similaire mais différent : au début du cycle de vie de l’adoption du cloud, les petites équipes peuvent fonctionner comme des organisations décentralisées par nécessité. Si ces équipes sont décentralisées à cause des circonstances (par opposition à la décentralisation volontaire), il est toujours recommandé de suivre la meilleure pratique de zone d'atterrissage.

## <a name="portfolio-hierarchy"></a>Hiérarchie du portefeuille

Les zones d’atterrissage représentent une couche de l’ensemble de la hiérarchie du portefeuille, comme décrit dans les conditions préalables. L’existence de zones d’atterrissage est un indicateur qui permet à l’entreprise de prendre en charge un portefeuille plus large, avec l’aide de différentes équipes de prise en charge, de processus et d’une _fondation de plateforme_ centralisée. Pour plus d’informations sur la façon dont les zones d’atterrissage s’intègrent à la conception de portefeuille à plus grande échelle, consultez l’article sur la [Hiérarchie du portefeuille](../../reference/fundamental-concepts/hosting-hierarchy.md). Pour plus d’informations sur les produits dans Azure pouvant être utilisés pour gérer les différentes couches de la hiérarchie du portefeuille, consultez [Prise en charge de la hiérarchie Azure](../../reference/fundamental-concepts/hierarchy-azure-tools.md).

## <a name="next-steps"></a>Étapes suivantes

Avant d’établir votre première zone d’atterrissage, il est important de comprendre les [principes de refactorisation](./refactor.md) qui guident cette approche.

> [!div class="nextstepaction"]
> [Refactoriser des zones d’atterrissage](./refactor.md)
