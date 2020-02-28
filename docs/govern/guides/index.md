---
title: Guides de gouvernance cloud
description: Consultez les guides de gouvernance cloud qui illustrent les bonnes pratiques à suivre pour traiter n’importe quel scénario de gouvernance de manière incrémentielle.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 51f24653998ab3cd4cf7fd043b487e4d7c1ccc5b
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77709224"
---
# <a name="cloud-governance-guides"></a>Guides de gouvernance cloud

Les guides de gouvernance actionnables de cette section illustrent l’approche incrémentielle du modèle de gouvernance du Framework d’adoption du cloud, basée sur la [méthodologie de gouvernance](../methodology.md) décrite précédemment. Vous pouvez établir une approche agile de la gouvernance cloud capable d’évoluer pour répondre aux besoins de n’importe quel scénario de gouvernance cloud.

## <a name="review-and-adopt-cloud-governance-best-practices"></a>Découvrir et adopter les meilleures pratiques en matière de gouvernance cloud

Pour commencer votre parcours d’adoption du cloud, choisissez un des guides de gouvernance suivants. Chaque guide décrit une série de bonnes pratiques qui reposent sur un ensemble d’expériences client fictives. Pour les lecteurs qui ne connaissent pas l’approche incrémentielle du modèle de gouvernance du Framework d’adoption du cloud, il est recommandé de lire d’abord l’introduction générale à la théorie de la gouvernance ci-dessous, avant de choisir un des ensembles de bonnes pratiques.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./standard/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guide de gouvernance standard</h3>
                        <p>Guide pour la plupart des organisations basées sur le modèle à deux abonnements recommandé, conçu pour les déploiements dans plusieurs régions, mais sans englober les clouds publics et souverains/gouvernementaux.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./complex/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guide de gouvernance pour les entreprises complexes</h3>
                        <p>Guide pour les entreprises qui sont gérées par plusieurs unités commerciales informatiques indépendantes ou qui englobent des clouds publics et souverains/gouvernementaux.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="an-incremental-approach-to-cloud-governance"></a>Approche incrémentielle de la gouvernance cloud

## <a name="choose-a-governance-guide"></a>Choisir un guide de gouvernance

Les différents guides montrent comment implémenter un MVP de gouvernance. Ensuite, chaque guide indique comment l’équipe de gouvernance cloud peut travailler au-devant des équipes chargées de l’adoption du cloud en tant que partenaire, afin d’accélérer le passage au cloud. Le modèle de gouvernance du Framework d’adoption du cloud guide l’application de la gouvernance, depuis les éléments de base jusqu’aux améliorations et évolutions postérieures.

Pour entamer un parcours de gouvernance, choisissez l’une des deux options ci-dessous. Les options s’appuient sur des expériences client synthétisées. Les titres évoquent la complexité de l’entreprise pour faciliter votre navigation. Toutefois, il se peut que la décision du lecteur soit plus complexe. Les tableaux suivants dressent la liste des différences entre ces deux options :

> [!WARNING]
> Un point de départ de gouvernance plus robuste peut être nécessaire. Dans ce cas, examinez l’approche [Centre de données virtuel Azure](#azure-virtual-datacenter) décrite brièvement [ci-dessous](#azure-virtual-datacenter). Cette approche est généralement conseillée lors d’un projet d’adoption à l’échelle de l’entreprise, en particulier si ce projet dépasse 10 000 ressources. C’est également la meilleure option pour les scénarios de gouvernance complexes lorsqu’une des conditions suivantes est requise : exigences de conformité étendues de la part de tiers, expertise approfondie du domaine, ou parité avec des stratégies de gouvernance et des exigences de conformité informatique éprouvées.

<!-- markdownlint-disable MD028 -->

> [!NOTE]
> Il est peu probable que les guides correspondent totalement à votre situation. Choisissez le guide qui s’en rapproche le plus et utilisez-le comme point de départ. Tout au long du guide, vous trouverez des informations supplémentaires afin de vous aider à personnaliser vos décisions et ainsi satisfaire certains critères spécifiques.

### <a name="business-characteristics"></a>Caractéristiques de l’entreprise

| Caractéristique | Organisation standard | Entreprise complexe |
|---|---|---|
| Zone (pays ou région géopolitique) | Les clients ou le personnel se trouvent majoritairement dans une seule zone. | Les clients ou le personnel sont répartis sur plusieurs zones ou nécessitent des clouds souverains. |
| Unités commerciales affectées | Unités commerciales partageant une infrastructure informatique commune | Plusieurs unités commerciales qui ne partagent pas une infrastructure informatique commune |
| Budget informatique | Budget informatique unique | Budget alloué à différentes unités commerciales et monnaies locales |
| Investissements informatiques | Les frais liés aux dépenses d’investissement sont planifiés annuellement et couvrent généralement uniquement la maintenance de base. | Les frais liés aux dépenses d’investissement sont planifiés annuellement et incluent souvent la maintenance ainsi qu’un cycle de renouvellement de trois à cinq ans. |

### <a name="current-state-before-adopting-cloud-governance"></a>État actuel avant l’adoption de la gouvernance cloud

| State | Entreprise standard | Entreprise complexe |
|---|---|---|
| Centre de données ou fournisseurs d’hébergement tiers | Moins de cinq centres de données | Plus de cinq centres de données |
| Mise en réseau | Aucun réseau étendu ou 1&ndash;2 fournisseurs de réseau étendu | Réseau complexe ou réseau étendu global |
| Identité | Forêt unique et domaine unique. | Complexe, forêts et domaines multiples. |

### <a name="desired-future-state-after-incremental-improvement-of-cloud-governance"></a>État futur souhaité après une amélioration incrémentielle de la gouvernance cloud

| State | Organisation standard | Entreprise complexe |
|---|---|---|
| Gestion des coûts – comptabilité cloud | Modèle de récupération des données de facturation. Facturation informatique centralisée. | Modèle de rétrofacturation. La facturation peut être répartie en fonction de l’approvisionnement informatique. |
| Ligne de base de sécurité – données protégées | Données financières de l’entreprise et adresse IP. Données client limitées. Aucune exigence en matière de conformité des tiers. | Plusieurs ensembles de données financières et personnelles des clients. Conformité des tiers à envisager. |

## <a name="azure-virtual-datacenter"></a>Centre de données virtuel Azure

Le centre de données virtuel Azure est une approche permettant de tirer le meilleur parti des capacités de la plateforme cloud Azure tout en garantissant la sécurité de l’entreprise et les exigences de gouvernance.

Par rapport à des environnements locaux traditionnels, Azure permet aux équipes de développement des charges de travail et leurs partenaires commerciaux de tirer parti de l’agilité de déploiement accrue qu’offrent les plateformes cloud. Toutefois, à mesure que vos efforts d’adoption du cloud s’intensifient pour inclure des charges de travail et des données stratégiques, cette agilité peut entrer en conflit avec les exigences de sécurité et de conformité de l’entreprise, établies par vos équipes informatiques. Cela est particulièrement vrai pour les grandes entreprises qui doivent respecter des obligations réglementaires et de gouvernance complexes existantes.

L’approche Centre de données virtuel Azure vise à répondre à ces préoccupations en amont du cycle d’adoption en fournissant des modèles, des architectures de référence, des exemples d'artefacts d’automatisation ainsi que des conseils pour faciliter un équilibre entre les exigences de gouvernance des développeurs et des équipes informatiques pendant les efforts d’adoption du cloud en entreprise. Au cœur de cette approche se trouve le concept même d’un centre de données virtuel : l’implémentation de limites d’isolation autour de votre infrastructure cloud par l’application de contrôles d’accès et de sécurité, de stratégies réseau et de surveillance de la conformité.

Un centre de données virtuel peut être considéré comme votre propre cloud isolé au sein de la plate-forme Azure, intégrant les processus de gestion, les exigences réglementaires et les processus de sécurité requis par vos stratégies de gouvernance. À l’intérieur de cette frontière virtuelle, le Centre de données virtuel Azure offre des exemples de modèles pour déployer des charges de travail tout en assurant une conformité cohérente, et fournit des conseils de base sur l’implémentation de la séparation des rôles et des responsabilités d’une organisation dans le cloud.

### <a name="azure-virtual-datacenter-assumptions"></a>Hypothèses du centre de données virtuel Azure

Même si des équipes restreintes peuvent bénéficier des modèles et des suggestions du Centre de données virtuel Azure, cette approche est conçue pour guider les services informatiques d’entreprise qui gèrent de grands environnements cloud. Les entreprises qui répondent aux critères suivants devraient suivre les recommandations du Centre de données virtuel Azure lors de la conception de leur infrastructure cloud basée sur Azure :

- Votre entreprise est soumise à des exigences de conformité réglementaire nécessitant des capacités centralisées de surveillance et d’audit.
- Vous devez maintenir une conformité commune aux stratégies et à la gouvernance et un contrôle informatique central sur les principaux services.
- Votre secteur dépend d’une plateforme complexe qui nécessite des contrôles complexes et une expertise approfondie du domaine pour gouverner la plateforme. C’est le plus courant dans les grandes entreprises des secteurs de la finance, du pétrole ou de l’industrie.
- Vos stratégies de gouvernance informatique existantes exigent une parité plus étroite avec les fonctionnalités existantes, même pendant la phase initiale d’adoption.

Pour plus d’informations, consultez la section [Centre de données virtuel Azure](../../reference/vdc.md) du Framework d’adoption cloud.

## <a name="next-steps"></a>Étapes suivantes

Choisissez un de ces guides :

> [!div class="nextstepaction"]
> [Guide de gouvernance pour les entreprises standard](./standard/index.md)
>
> [Guide de gouvernance pour les entreprises complexes](./complex/index.md)
