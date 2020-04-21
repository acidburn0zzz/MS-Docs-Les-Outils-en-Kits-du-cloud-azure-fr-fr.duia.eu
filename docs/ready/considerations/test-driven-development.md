---
title: Développement piloté par les tests des zones d’atterrissage
description: Développement piloté par les tests des zones d’atterrissage
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 5693072eee18e0e3ee45bd3d3fd62d3a7de5795e
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81122014"
---
# <a name="test-driven-development-tdd-for-landing-zones"></a>Développement piloté par les tests (TDD) des zones d’atterrissage

Le développement piloté par les tests est un processus DevOps et de développement de logiciels courant qui améliore la qualité des nouvelles fonctionnalités et améliorations apportées à une solution basée sur du code. L’infrastructure basée sur le cloud et le code source sous-jacent peuvent utiliser ce processus pour garantir que les zones d’atterrissage répondent aux exigences principales et qu’elles sont de haute qualité. Ce processus est particulièrement utile lorsque des zones d’atterrissage sont en cours de développement et de refactorisation dans un effort de développement parallèle.

![Processus de développement piloté par les tests pour les zones d’atterrissage cloud](../../_images/ready/test-driven-development-process.png)

Dans le cloud, l’infrastructure est la sortie du code. Un code correctement structuré, testé et vérifié produit une zone d’atterrissage viable. Selon la [définition des zones d’atterrissage](../landing-zone/index.md), « Une zone atterrissage est un environnement permettant d’héberger vos charges de travail qui sont préprovisionnées par le biais de code. Elle comprend des fonctionnalités de base reposant sur un ensemble défini de services cloud et de bonnes pratiques **pour assurer votre réussite**. » Cet article décrit une approche permettant d’utiliser le développement piloté par les tests pour répondre à la dernière partie de cette définition, tout en répondant aux exigences de qualité, de sécurité, d’exploitation et de gouvernance.

Cette approche peut être utilisée pour répondre à des demandes de fonctionnalités simples pendant les premières phases de développement. Plus tard dans le cycle de vie de l’adoption du cloud, ce processus peut être utilisé pour répondre aux exigences de sécurité, d’exploitation, de gouvernance ou de conformité.

## <a name="definition-of-done"></a>Définition de Terminé

« Assurer la réussite » est une déclaration subjective. Cette déclaration fournit à l’équipe de plateforme cloud des informations qui sont peu actionnables pendant le développement de la zone d’atterrissage ou les efforts de refactorisation. Ce manque de clarté peut entraîner des attentes manquées et des vulnérabilités dans un environnement cloud. Avant la refactorisation ou le développement d’une zone d’atterrissage, l’équipe de la plateforme cloud doit faire de la clarté sur la « définition de terminé » pour chaque zone d’atterrissage.

La définition de Terminé est un contrat simple entre l’équipe de plateforme cloud et les autres équipes affectées. Ce contrat décrit les fonctionnalités ajoutées à la valeur attendue, qui doivent être incluses dans tout effort de développement de zone d’atterrissage. Souvent, la définition de Terminé est une liste de vérification, qui s’aligne sur le plan d’adoption du cloud à court terme. Dans les processus matures, les fonctionnalités attendues de la liste de vérification auront chacune leurs propres critères d’acceptation pour créer encore plus de clarté. Lorsque les fonctionnalités à valeur ajoutée remplissent chacune les critères d’acceptation, la zone d’atterrissage est suffisamment configurée pour permettre la réussite de la vague ou de la mise en œuvre de l’effort d’adoption en cours.

À mesure que les équipes adoptent des charges de travail et des fonctionnalités cloud supplémentaires, la définition de Terminé et des critères d’acceptation devient de plus en plus complexe.

## <a name="test-driven-development-cycle"></a>Cycle de développement piloté par les tests

Le cycle qui rend le développement piloté par les tests efficace est souvent appelé test rouge/vert. Dans cette approche, l’équipe de plateforme cloud commence par un test ayant échoué (test rouge) en fonction de la définition de Terminé et des critères d’acceptation définis. Pour chaque fonctionnalité ou critère d’acceptation, l’équipe de plateforme cloud exécuterait des tâches de développement jusqu’à ce que le test soit réussi (test vert). Un cycle de développement piloté par les tests (ou un test rouge/vert) répéterait les étapes de base de l’image et de la liste ci-dessous jusqu’à ce que la définition complète de Terminé puisse être satisfaite.

![Processus de développement piloté par les tests pour les zones d’atterrissage cloud](../../_images/ready/test-driven-development-process.png)

- **Créer un test :** Définissez un test pour valider que les critères d’acceptation pour une fonctionnalité spécifique à valeur ajoutée ont été satisfaits. Lorsque cela est possible, automatisez le test.
- **Tester la zone d’atterrissage :** Exécutez le nouveau test et les tests existants. Si la fonctionnalité requise n’a pas déjà été remplie par des efforts de développement antérieurs et n’est pas incluse dans l’offre du fournisseur cloud, le test doit échouer. L’exécution de tests existants vous permettra de vérifier que votre nouveau test ne réduit pas la fiabilité des fonctionnalités de la zone d’atterrissage fournies par le code existant.
- **Développer et refactoriser la zone d'atterrissage :** Ajoutez ou modifiez le code source pour satisfaire la fonctionnalité à valeur ajoutée demandée et améliorer la qualité générale de la base de code. Pour rencontrer au maximum l’esprit du développement piloté par les tests, l’équipe de la plateforme cloud n’ajouterait que du code pour répondre à la fonctionnalité demandée et rien de plus. En même temps, le maintien de la qualité et la maintenance du code sont un travail partagé. Lors de la réalisation de nouvelles demandes de fonctionnalités, l’équipe de la plateforme cloud doit chercher à améliorer le code en supprimant la duplication et en clarifiant le code. L’exécution de tests entre la création de code et la refactorisation du code source est fortement suggérée.
- **Déployer la zone d’atterrissage :** Une fois que le code source est capable de remplir la demande de fonctionnalité, déployez la zone d’atterrissage modifiée sur le fournisseur de cloud dans un environnement de test contrôlé ou de bac à sable (sandbox).
- **Tester la zone d’atterrissage :** Le nouveau test de la zone d’atterrissage doit confirmer que le nouveau code répond aux critères d’acceptation de la fonctionnalité demandée. Une fois tous les tests réussis, la fonctionnalité est considérée comme terminée et les critères d’acceptation sont considérés comme étant satisfaits.

Lorsque toutes les fonctionnalités à valeur ajoutée et les critères d'acceptation réussissent les tests associés, la zone d’atterrissage est prête à prendre en charge la vague suivante du plan d’adoption du cloud.

## <a name="simple-example-of-a-definition-of-done"></a>Exemple simple d’une définition de Terminé

Pour un effort de migration initial, la définition de Terminé peut être trop simple. Voici un exemple de l’un de ces exemples simplifiés à l’extrême.

- La zone d’atterrissage initiale sera utilisée pour héberger 10 charges de travail à des fins d’apprentissage initial. Ces charges de travail ne sont pas essentielles pour l’entreprise et n’ont pas accès aux données sensibles. À l’avenir, il est probable que ces charges de travail soient mises en production, mais leur caractère critique et sensible ne changera probablement pas. Pour prendre en charge ces charges de travail, l’équipe chargée de l’adoption du cloud doit respecter les critères suivants :

- Segmentation de réseau à aligner avec la conception de réseau proposée.
- Accès aux ressources de calcul, de stockage et de mise en réseau pour héberger les charges de travail alignées sur la découverte de domaine numérique
- Schéma d’attribution de noms et de marquage pour une utilisation plus simple.
- Cet environnement doit être traité comme une « zone démilitarisée (DMZ) » avec accès à l’Internet public
- Au cours des efforts d’adoption, l’équipe d’adoption du cloud souhaiterait un accès temporaire à l’environnement pour modifier les configurations de service.
- À des fins de sensibilisation uniquement : Avant la version de production, ces charges de travail nécessitent une intégration avec le fournisseur d’identité d’entreprise pour régir l’identité et l’accès en continu à des fins de gestion des opérations. C’est à ce moment que l’accès de l’équipe d’adoption du cloud doit être révoqué.

Le dernier point ci-dessus n’est pas une fonctionnalité ni un critère d’acceptation. Toutefois, il s’agit d’un indicateur selon lequel des expansions supplémentaires seront nécessaires et doivent être explorées par d’autres équipes de façon anticipée.

## <a name="additional-examples-of-a-definition-of-done"></a>Exemples supplémentaires d’une définition de Terminé

La méthodologie de gouvernance au sein du Cloud Adoption Framework fournit un parcours narratif à travers la maturité naturelle d’une équipe de gouvernance. Dans ce parcours, vous trouverez plusieurs exemples de « définition de Terminé » et de « critères d’acceptation », sous la forme de déclarations de stratégie.

- [Déclarations de stratégie initiales](../../govern/guides/complex/initial-corporate-policy.md#policy-statements) : Exemple de stratégies d’entreprise directrices et définition initiale de Terminé en fonction des exigences d’adoption aux premières étapes.
- [Expansion d’identité](../../govern/guides/complex/identity-baseline-improvement.md#incremental-improvement-of-the-policy-statements) : Exemple de stratégies d’entreprise directrices (« définition de Terminé ») pour répondre aux exigences de développement de la gestion des identités pour une zone d’atterrissage.
- [Expansion de sécurité](../../govern/guides/complex/security-baseline-improvement.md#incremental-improvement-of-the-policy-statements) : Exemple de stratégies d’entreprise directrices (« définition de Terminé ») pour répondre aux exigences de sécurité alignées sur le plan d’adoption du cloud de référence.
- [Expansion des opérations](../../govern/guides/complex/resource-consistency-improvement.md#incremental-improvement-of-the-policy-statements) : Exemple de stratégies d’entreprise directrices (« définition de Terminé ») pour répondre aux exigences de base de la gestion des opérations.
- [Expansion des coûts](../../govern/guides/complex/cost-management-improvement.md#changes-to-the-policy-statements) : Exemple de stratégies d’entreprise directrices (« définition de Terminé ») pour répondre aux exigences de la gestion des coûts.

Les exemples ci-dessus sont des exemples de base pour vous aider à développer une « définition de Terminé » pour vos zones d’atterrissage. Des exemples de stratégies supplémentaires sont disponibles sous chacune des [disciplines de la gouvernance cloud](../../govern/governance-disciplines.md).

## <a name="next-steps"></a>Étapes suivantes

Pour accélérer le développement piloté par les tests dans Azure, passez en revue les [fonctionnalités de développement piloté par les tests d’Azure](./azure-test-driven-development.md).

> [!div class="nextstepaction"]
> [Développement piloté par les tests dans Azure](./azure-test-driven-development.md)
