---
title: Migration cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migration cloud dans le Framework d’adoption du cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: migrate
layout: LandingPage
ms.openlocfilehash: c112c1d340de944502ac16159977ffa12b5b095d
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72378260"
---
# <a name="cloud-migration-in-the-cloud-adoption-framework"></a>Migration cloud dans le Framework d’adoption du cloud

Tout [plan d’adoption du cloud](../plan/index.md) à l’échelle de l’entreprise inclura des charges de travail qui ne justifient pas des investissements significatifs dans la création d’une nouvelle logique métier. Ces charges de travail peuvent être déplacées vers le cloud en suivant différentes approches : lift-and-shift, lift-and-optimize ou modernisation. Chacune de ces approches est considérée comme une migration. Les exercices suivants vous aident à établir les processus itératifs pour évaluer, migrer, optimiser, sécuriser et gérer ces charges de travail.

## <a name="getting-started"></a>Prise en main

Pour vous préparer à cette phase du cycle d’adoption du cloud, le framework suggère les cinq exercices suivants :

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-migration-guide/prerequisites.md?tabs=Checklist">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Prérequis pour la migration</h3>
Vérifiez que la zone d’accueil a été déployée et qu’elle est prête à héberger les premières charges de travail qui seront migrées vers Azure. Si vous n’avez pas encore créé de stratégie d’adoption du cloud et de plan d’adoption du cloud, vérifiez que ces deux efforts sont en cours.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-migration-guide/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Migrer votre première charge de travail</h3>
Utilisez le guide de migration Azure pour vous aider à migrer votre première charge de travail. Cela vous aidera à vous familiariser avec les outils et approches nécessaires à la mise à l’échelle des efforts d’adoption.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./expanded-scope/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Scénarios de migration étendue</h3>
Tirez parti de la liste de vérification d’étendue supplémentaire pour identifier les scénarios qui nécessiteraient des modifications de votre future architecture d’état, des processus de migration, des configurations de zones d’accueil ou des décisions en matière d’outils de migration.
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
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Bonnes pratiques</h3>
Validez toutes les modifications par rapport à la section sur les bonnes pratiques, afin de garantir l’implémentation correcte des approches de migration spécifiques liées aux charges de travail/à l’architecture ou de l’étendue supplémentaire.
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
                                <img alt="" src="../_images/icons/5.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Améliorations du processus</h3>
La migration est une activité exigeant de nombreux processus. À mesure que les efforts de migration augmentent, utilisez la section sur les considérations relatives à la migration pour évaluer et faire évoluer divers aspects de votre processus.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>
<!-- markdownlint-enable MD033 -->

## <a name="iterative-migration-process"></a>Processus itératif de migration

La migration vers le cloud se compose essentiellement de quatre phases simples : évaluer, migrer, optimiser, et sécuriser et gérer. Cette section du Framework d’adoption du cloud explique comment optimiser les résultats de chaque phase du processus et aligner ces phases avec votre plan d’adoption du cloud. Le graphique suivant illustre ces phases dans une approche itérative :

![Modèle de migration du Framework d’adoption du cloud](../_images/operational-transformation-migrate.png)

## <a name="creating-a-balanced-cloud-portfolio"></a>Création d’un portefeuille cloud équilibré

Tout portefeuille technologique équilibré est constitué d’un mélange de ressources dans différents états. La mise hors service est planifiée pour certaines applications et celles-ci font donc l’objet d’un support minimal. D’autres applications ou ressources font l’objet d’un support de l’ordre de la simple maintenance, mais les fonctionnalités de ces solutions sont stables. Pour des processus métier plus récents, les conditions changeantes du marché vont probablement pousser à une amélioration ou à une modernisation en continu des fonctionnalités. Quand des opportunités de générer de nouveaux flux de revenus se présentent, de nouvelles applications ou ressources sont introduites dans l’environnement. À chaque étape du cycle de vie d’une ressource, l’impact d’un investissement sur le chiffre d’affaires et sur les bénéfices va changer. Plus la phase du cycle de vie est tardive, moins il est probable qu’une nouvelle fonctionnalité ou un travail de modernisation va générer un fort retour sur investissement.

Le cloud fournit différents mécanismes d’adoption, chacun avec des degrés similaires d’investissement et de retour. La création d’applications cloud natives peut considérablement réduire les dépenses d’exploitation. Une fois qu’une application cloud native est publiée, l’itération du développement de nouvelles fonctionnalités et solutions peut être plus rapide. La modernisation d’une application peut procurer des avantages similaires en supprimant les contraintes héritées de l’existant associées aux modèles de développement locaux. Malheureusement, ces deux approches sont fastidieuses et dépendent de la taille, des compétences et de l’expérience des équipes de développement des logiciels. Souvent, les développeurs ne sont pas là où ils voudraient être : les personnes avec les compétences et le talent nécessaires pour moderniser des applications préféreraient créer de nouvelles applications. Dans un marché contraint par les ressources humaines, les projets de modernisation à grande échelle peuvent être impactés négativement par la satisfaction et le talent des employés. Dans un portefeuille équilibré, cette approche doit être réservée aux applications qui recevraient des améliorations significatives des fonctionnalités si elles restaient locales.

## <a name="envision-an-end-state"></a>Prévoir un état final

Un parcours efficace a besoin d’une destination cible. Élaborez une vision globale de l’état final avant d’entreprendre la première étape. Cette infographie présente un point de départ constitué d’applications, de données et d’une infrastructure existantes, qui définit l’existant numérique. Pendant le processus de migration, chaque ressource subit une transition via une des options figurant à droite.

## <a name="migration-implementation"></a>Implémentation de la migration

Ces articles décrivent deux parcours, chacun avec un objectif similaire: migrer un pourcentage important des ressources existantes vers Azure. Cependant, les résultats métier et l’état actuel vont influencer considérablement les processus nécessaires pour y arriver. Ces écarts subtils aboutissent à des deux approches radicalement différentes pour atteindre un état final similaire.

![Modèle de migration du Framework d’adoption du cloud](../_images/operational-transformation-migrate.png)

Pour guider une exécution incrémentielle pendant la transition vers l’état final, ce modèle sépare la migration selon deux aspects.

**Préparation de la migration :** Établir un backlog approximatif de la migration principalement basé sur l’état actuel et sur les résultats souhaités.

- **Résultats métier :** Les objectifs métier principaux pilotant cette migration.
- **Estimation de l’existant numérique** : Une estimation approximative du nombre et de la condition des charges de travail à migrer.
- **Rôles et responsabilités :** Une définition claire de la structure de l’équipe, de la séparation des responsabilités et des exigences quant aux accès.
- **Exigences de la gestion du changement :** La cadence, les processus et la documentation nécessaires pour passer en revue et approuver les changements.

Ces entrées initiales déterminent le backlog de la migration. Le résultat du backlog de la migration est une liste hiérarchisée des applications à migrer vers le cloud. Cette liste détermine l’exécution du processus de migration cloud. Au fil du temps, elle va aussi augmenter pour inclure une grande partie de la documentation nécessaire pour gérer le changement.

**Processus de migration :** Chaque activité de la migration cloud est contenue dans un des processus suivants, car elle concerne le backlog de la migration.

- **Évaluer :** Évaluer une ressource existante et établir un plan pour la migration de la ressource.
- **Migrer :** Répliquer la fonctionnalité d’une ressource dans le cloud.
- **Optimiser :** Équilibrer les performances, le coût, les accès et la capacité opérationnelle d’une ressource cloud.
- **Sécuriser et gérer :** Vérifier qu’une ressource cloud est prête pour les opérations courantes.

Les informations collectées pendant le développement d’un backlog de migration déterminent la complexité et le niveau du travail nécessaire au sein du processus de migration cloud lors de chaque itération et pour chaque version de la fonctionnalité.

## <a name="transition-to-the-end-state"></a>Transition vers l’état final

L’objectif est d’une migration vers le cloud sans heurts et en partie automatisée. Le processus de migration utilise les outils fournis par un fournisseur cloud pour répliquer et organiser rapidement les ressources dans le cloud. Après vérification, une simple modification du réseau redirige les utilisateurs vers la solution cloud. Pour de nombreux cas d’usage, la technologie pour atteindre cet objectif est largement disponible. Des exemples de cas montrent la rapidité avec laquelle 10 000 machines virtuelles peuvent être répliquées dans Azure.

Cependant, une approche incrémentielle de la migration reste nécessaire. Dans la plupart des environnements, la longue liste des machines virtuelles à migrer doit être décomposée en unités de travail plus petites pour que la migration réussisse. De nombreux facteurs limitent le nombre de machines virtuelles qui peuvent être migrées au cours d’une période donnée. La vitesse du trafic réseau sortant est une des quelques limites techniques ; la plupart des limites sont imposées par la capacité de l’entreprise à valider et à s’adapter aux changements.

L’approche incrémentielle de la migration du Framework d’adoption du cloud facilite la création d’un plan incrémentiel qui reflète et documente les limitations techniques et culturelles. L’objectif de ce modèle est de maximiser la rapidité de la migration tout en minimisant la surcharge de travail pour le département informatique et pour l’entreprise. Vous trouverez ci-après deux exemples d’exécution d’une migration incrémentielle basée sur le backlog de la migration.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./azure-migration-guide/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guide de migration Azure</h3>
                        <p><b>Résumé :</b> Ce client migre moins de 1 000 machines virtuelles. Moins de dix applications supportées sont détenues par un propriétaire d’application qui ne fait pas partie de l’organisation informatique. Les applications restantes, les machines virtuelles et les données associées sont détenues et supportées par les membres de l’équipe d’adoption du cloud. Les membres de l’équipe d’adoption du cloud ont un accès d’administration aux environnements de production dans le centre de données existant.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./expanded-scope/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guide pour un scénario complexe</h3>
                        <p><b>Résumé :</b> La migration de ce client présente une certaine complexité en raison du métier, de la culture et de la technologie. Ce guide présente plusieurs défis liés à cette complexité spécifique et les moyens de les relever.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

Ces deux parcours représentent deux expériences extrêmes de clients qui investissent dans la migration cloud. Pour la plupart des entreprises, ces deux scénarios s’entremêlent. Après avoir examiné les parcours, utilisez le modèle de migration du Framework d’adoption du cloud pour amorcer la conversation de la migration et modifier les parcours de référence pour qu’ils répondent mieux à vos besoins.

## <a name="next-steps"></a>Étapes suivantes

Choisissez l’un de ces parcours :

> [!div class="nextstepaction"]
> [Guide de migration Azure](./azure-migration-guide/index.md)
>
> [Guide avec étendue développée](./expanded-scope/index.md)
