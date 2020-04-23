---
title: Migration cloud
description: Découvrez comment établir les processus itératifs pour évaluer, migrer, optimiser, sécuriser et gérer les charges de travail que vous voulez migrer dans le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: migrate
layout: LandingPage
ms.openlocfilehash: b341996c45c4a0c5b7d8467419c3117f939afa20
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81120754"
---
# <a name="cloud-migration-in-the-cloud-adoption-framework"></a>Migration cloud dans le Framework d’adoption du cloud

Tout [plan d’adoption du cloud](../plan/index.md) à l’échelle de l’entreprise inclura des charges de travail qui ne justifient pas des investissements significatifs dans la création d’une nouvelle logique métier. Ces charges de travail peuvent être déplacées vers le cloud en suivant différentes approches : lift-and-shift, lift-and-optimize ou modernisation. Chacune de ces approches est considérée comme une migration. Les exercices suivants vous aident à établir les processus itératifs pour évaluer, migrer, optimiser, sécuriser et gérer ces charges de travail.

## <a name="getting-started"></a>Prise en main

Pour vous préparer à cette phase du cycle d’adoption du cloud, le framework recommande les exercices suivants :

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-migration-guide/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Migrer votre première charge de travail</h3>
Utilisez le Guide de migration d’Azure pour vous familiariser avec les outils Azure natifs et une approche de la migration.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-best-practices/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Scénarios de migration</h3>
Utilisez d’autres outils et approches de migration pour suivre d’autres scénarios de migration.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-best-practices/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Meilleures pratiques</h3>
Répondez aux besoins de migration courants via l’application de bonnes pratiques cohérentes.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./migration-considerations/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Améliorations de processus</h3>
La migration est une activité exigeant de nombreux processus. À mesure que les efforts de migration augmentent, utilisez ces améliorations des processus pour évaluer et faire évoluer différents aspects de la migration.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>
<!-- markdownlint-enable MD033 -->

Cette méthodologie et les étapes ci-dessus s’appuient sur les hypothèses suivantes :

- La méthodologie régissant les sprints de migration s’inscrit dans les vagues de migration ou les versions qui sont définies à l’aide des méthodologies de planification, préparation et adoption. Dans chaque sprint de migration, un lot de charges de travail est migré vers le cloud.
- Avant de migrer des charges de travail, au moins une [zone de destination](../ready/index.md) a été identifiée, configurée et déployée pour répondre aux besoins du plan d’adoption du cloud à court terme.
- La migration est généralement associée aux termes _lift and shift_ ou _réhébergement_. Cette méthodologie et les étapes ci-dessus sont basées sur la conviction qu’aucun centre de données et peu de charges de travail ne doivent être migrés selon une approche de réhébergement pure. Si de nombreuses charges de travail peuvent être réhébergées, les clients choisissent néanmoins plus souvent de moderniser des ressources spécifiques au sein de chaque charge de travail. Au cours de ce processus itératif, l’équilibre entre la rapidité et la modernisation est un point de discussion courant.

## <a name="migration-effort"></a>Effort de migration

L’effort nécessaire pour migrer des charges de travail est généralement divisé en trois phases : évaluation, déploiement et mise en production. Cette section du Cloud Adoption Framework enseigne aux lecteurs comment optimiser le retour de chaque phase requise pour migrer une charge de travail en production.

Dans une itération standard de deux semaines, une équipe de migration expérimentée peut effectuer ce processus pour 2 à 5 charges de travail de faible-moyenne complexité. Les charges de travail plus complexes telles que SAP peuvent nécessiter plusieurs itérations de deux semaines pour achever les trois phases de l’effort de migration. L’expérience et la complexité ont un impact significatif sur les chronologies et la vélocité de la migration.

![Effort de migration du Cloud Adoption Framework](../_images/migrate/methodology.png)

Les points suivants fournissent une vue d’ensemble des phases de ce processus (illustrées ci-dessus) :

- **Évaluer les charges de travail :** Évaluez les charges de travail pour estimer les coûts, la modernisation et les outils de déploiement. Ce processus se concentre sur la validation ou la remise en question des hypothèses formulées au cours de découvertes et d’évaluations précédentes en examinant de plus près les options de rationalisation. C’est également au cours de cette phase que les modèles et les dépendances des utilisateurs sont étudiés plus en détail pour vérifier que les charges de travail atteindront les objectifs techniques après la migration.
- **Déployer les charges de travail :** Une fois les charges de travail évaluées, les fonctionnalités existantes de ces charges de travail sont répliquées (ou améliorées) dans le cloud. Ceci peut impliquer un _lift-and-shift_ ou un _réhébergement_ dans le cloud. Mais le plus souvent au cours de cette phase, de nombreuses ressources prenant en charge ces charges de travail sont modernisées pour tirer parti des avantages du cloud.
- **Mettre en production les charges de travail :** Une fois les fonctionnalités répliquées dans le cloud, les charges de travail peuvent être testées, optimisées, documentées et mises en production pour les opérations en cours. Durant ce processus, il est essentiel de passer en revue les charges de travail migrées et de les transmettre aux équipes de gouvernance, de gestion des opérations et de sécurité pour assurer la prise en charge continue de ces charges de travail.

> [!NOTE]
> Dans certaines des premières itérations de l’effort de migration, il est courant de limiter l’étendue à une seule charge de travail. Cette approche maximise la rétention des compétences et donne à l’équipe plus de temps pour expérimenter et apprendre.
> [!NOTE]
> Lors de la création d’une fabrique de migration, certaines équipes peuvent choisir de répartir chacune des phases ci-dessus entre plusieurs équipes et/ou sprints. Cette approche peut améliorer la répétabilité et accélérer les efforts de migration.

## <a name="migration-waves"></a>Vagues de migration

Les itérations de migration confèrent une valeur technique en migrant les ressources et les charges de travail. Une vague de migration est la plus petite collection de charges de travail fournissant une valeur métier tangible et mesurable. Chaque itération doit se terminer dans un rapport détaillant les efforts techniques réalisés. Toutefois, les changements d’ordre métier et la planification stratégique se produisent généralement à un niveau légèrement supérieur. Au fur et à mesure que l’équipe d’adoption du cloud participe à l’effort de migration, l’équipe de stratégie cloud se concentre sur la planification des 1 à 2 vagues de migration suivantes. L’équipe de stratégie cloud suit également les progrès techniques sous la forme d’une métrique d’apprentissage pour mieux comprendre les chronologies associées à la réalisation de la valeur métier. À cet égard, les vagues de migration constituent l’approche itérative de gestion des changements pour faire le suivi des résultats métier, des personnes et des chronologies.

Comme indiqué dans le graphique de la section précédente, les processus se trouvant dans la [méthodologie de planification](../plan/index.md), la [méthodologie de préparation](../ready/index.md) et, dans certains cas, la [méthodologie de stratégie](../strategy/index.md) du Cloud Adoption Framework fournissent des conseils sur la planification et la gestion des vagues de migration. La gestion de ces vagues permet de hiérarchiser et de définir l’effort de migration à fournir par les équipes techniques.

## <a name="next-steps"></a>Étapes suivantes

Les étapes « Bien démarrer » ci-dessus ainsi que les instructions disponibles dans la méthodologie de migration vous aideront à développer des compétences pour améliorer l’exécution des processus au sein de chaque sprint de migration. Le [guide de migration Azure](./azure-migration-guide/index.md) est une série d’articles décrivant les outils et les approches les plus couramment utilisés durant votre première vague de migration.

> [!div class="nextstepaction"]
> [Guide de migration Azure](./azure-migration-guide/index.md)
