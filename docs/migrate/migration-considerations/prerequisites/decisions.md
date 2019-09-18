---
title: Décisions qui affectent les migrations
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Décisions importantes à prendre en ce qui concerne le processus de migration
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4bc84ad8bd2d0a0521399c1762585db6f9a5a6ab
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025412"
---
# <a name="decisions-that-affect-migrations"></a>Décisions qui affectent les migrations

Pendant la migration, plusieurs facteurs peuvent influencer les décisions et les activités d’exécution. Cet article explique le thème central de ces décisions et explore quelques questions qui traitent des principes de migration de cette section du guide du Framework d’adoption du cloud.

## <a name="business-outcomes"></a>Résultats métier

L’objectif de tout effort d’adoption peut avoir un impact significatif sur l’approche suggérée pour l’exécution.

- **Migration.** Les axes stratégiques d’entreprise urgents, la vitesse d’adoption ou les économies de coûts sont des exemples de résultats opérationnels. Ces résultats sont essentiels aux efforts visant à créer de la valeur commerciale à partir de changements transitifs dans les modèles informatiques ou d’exploitation. La section Migrer du Framework d’adoption du cloud se concentre principalement sur les résultats métier de la migration.
- **Innovation des applications.** L’amélioration de l’expérience client et la croissance des parts de marché sont des exemples de résultats incrémentiels. Les résultats proviennent d’une collection de modifications incrémentielles axées sur les besoins et les souhaits des clients actuels.
- **Innovation basée sur les données.** De nouveaux produits ou services, en particulier ceux qui sont alimentés par des données, sont des exemples de résultats perturbateurs. Ces résultats sont le résultat d’expérimentations et de prédictions qui utilisent des données pour perturber le statu quo sur le marché.

Aucune entreprise ne poursuivrait un seul de ces résultats. Sans opérations, il n’y a pas de client et vice versa. L’adoption du cloud n’est pas différente. Les entreprises s’efforcent généralement d’atteindre chacun de ces résultats, mais en essayant de vous concentrer simultanément sur chacun d’entre eux, vous risquez d’éparpiller vos efforts et de ralentir vos progrès sur le travail qui pourraient profiter le plus à vos besoins commerciaux.

Ce prérequis n’est pas une demande pour vous de choisir l’un de ces trois objectifs, mais plutôt d’aider vos équipes de stratégie cloud et d’adoption du cloud à établir un ensemble de priorités opérationnelles qui guideront l’exécution des trois à six prochains mois. Ces priorités sont définies en classant chacune des trois options détaillées de *la plus significative* à *la moins significative*, car elles se rapportent aux efforts auxquels cette équipe peut contribuer au cours d’un ou des deux trimestres suivants.

### <a name="acting-on-migration-outcomes"></a>Agir sur les résultats de la migration

Si les résultats opérationnels sont classés le plus haut dans la liste, cette section du Framework d’adoption du cloud fonctionnera correctement pour votre équipe. Dans cette section, il est supposé que vous devez classer par ordre de priorité la vitesse et les économies de coûts en tant qu’indicateurs de performance clés (KPI) primaires, auquel cas un modèle de migration vers l’adoption serait bien aligné avec les résultats. Un modèle axé sur la migration est essentiellement fondé sur la migration « lift-and-shift » des ressources Infrastructure as a service (IaaS) pour épuiser un centre de données et réaliser des économies. Dans ce type de modèle, une modernisation peut avoir lieu, mais elle constitue un objectif secondaire jusqu’à ce que la mission principale de la migration soit réalisée.

### <a name="acting-on-application-innovations"></a>Agir sur les innovations des applications

Si la part de marché et l’expérience client sont vos principaux moteurs, ce n’est peut-être pas la meilleure section du Framework d’adoption du cloud pour guider les efforts de vos équipes. L’innovation des applications nécessite un plan axé sur la modernisation et la transition des charges de travail, quelle que soit l’infrastructure sous-jacente. Dans ce cas, les instructions de cette section peuvent être utiles, mais elles ne constituent peut-être pas la meilleure approche pour guider les décisions fondamentales.

### <a name="acting-on-data-innovations"></a>Agir sur les innovations de données

Si les données, l’expérimentation, la recherche et le développement (R&D) ou les nouveaux produits sont votre priorité pour les six prochains mois, cette section du Framework d’adoption du cloud n’est peut-être pas la meilleure pour guider les efforts de vos équipes. Tout effort d’innovation des données peut tirer parti des conseils relatifs à la migration des données sources existantes. Toutefois, l’objectif plus large de cet effort est l’entrée et l’intégration de sources de données supplémentaires. L’élargissement de ces recommandations par des prédictions et de nouvelles expériences est bien plus importante que la migration des ressources IaaS.

## <a name="balancing-the-portfolio"></a>Équilibrage du portefeuille

Cette section du Framework d’adoption du cloud établit la théorie pour aider les lecteurs à comprendre les différentes approches pour traiter les changements dans un portefeuille équilibré. L’article sur [l’équilibrage du portefeuille](../../expanded-scope/balance-the-portfolio.md) est un exemple d’expansion d’étendue, conçu pour aider à donner suite à cette théorie.

## <a name="effort"></a>Effort

L’effort de migration peut varier considérablement en fonction de la taille et de la complexité des charges de travail impliquées. Une migration de charge de travail plus petite impliquant quelques centaines de machines virtuelles est un processus tactique qui peut être implémenté à l’aide d’outils automatisés tels qu’[Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-overview). À l’inverse, la migration de dizaines de milliers de charges de travail d’une grande entreprise nécessite un processus hautement stratégique et peut impliquer une refactorisation, une régénération et un remplacement importants des applications existantes intégrant des fonctionnalités PaaS (platform as a service) et SaaS (software as a service). [L’identification et l’équilibrage de l’étendue](../../expanded-scope/balance-the-portfolio.md) de vos migrations planifiées sont essentielles.

Avant de prendre des décisions susceptibles d’avoir un impact à long terme sur le programme de migration actuel, il est primordial de créer un consensus sur les décisions suivantes.

### <a name="effort-type"></a>Type d’effort

Dans toute migration d’envergure (> 250 machines virtuelles), les ressources sont migrées à l’aide de diverses options de transition, présentées dans les 5 R de la rationalisation : *réhébergement*, *refactorisation*, *réarchitecture*, *régénération* et *remplacement*.

Certaines charges de travail sont modernisées à l’aide d’ un processus de *régénération* ou de *réarchitecture*, créant ainsi des applications plus modernes avec de nouvelles capacités techniques et fonctionnalités. D’autres ressources passent par un processus de *refactorisation*, par exemple un déplacement vers des conteneurs ou d’autres approches opérationnelles et d’hébergement plus modernes qui ne modifient pas nécessairement le code base des solutions. En règle générale, les machines virtuelles et autres ressources mieux établies passent par un processus de *réhébergement*, en transférant ces ressources du centre de données vers le cloud. Certaines charges de travail peuvent potentiellement être migrées vers le cloud, mais doivent plutôt être *remplacées* par des services cloud basés sur les services (SaaS) qui répondent aux mêmes besoins métier, par exemple en utilisant Office 365 comme alternative à la migration des instances Exchange Server.

Dans la plupart des scénarios, un événement métier crée une fonction de forçage qui entraîne la migration temporaire d’un pourcentage élevé de ressources à l’aide du processus de *réhébergement*, suivie d’une transition secondaire plus importante à l’aide de l’une des autres stratégies de migration, une fois qu’elles se trouvent dans le cloud. Ce processus est communément appelé *transition cloud*.

Durant le processus de [rationalisation du patrimoine numérique](../../../digital-estate/calculate.md), ces types de décisions sont appliqués à chaque ressource à migrer. Toutefois, il convient pour l’instant de faire une hypothèse de base. Parmi les cinq stratégies de migration, laquelle est la plus adaptée aux objectifs stratégiques ou aux résultats métier qui motivent cet effort de migration ? Cette décision sert d’hypothèse directrice dans tout l’effort de migration.

### <a name="effort-scale"></a>Échelle de l’effort

L’échelle de la migration est la prochaine décision préalable importante. Les processus nécessaires à la migration de 1 000 ressources sont différents du processus requis pour déplacer 10 000 ressources. Avant de commencer l’effort de migration, il est important de répondre aux questions suivantes :

- **Combien de ressources prennent aujourd’hui en charge les charges de travail en cours de migration ?** Les ressources incluent des structures de données, des applications, des machines virtuelles et des appliances informatiques nécessaires. Il est recommandé de choisir une charge de travail relativement petite pour votre première candidate à la migration.
- **Parmi ces ressources, combien sont planifiées pour la migration ?** Il est courant qu’un pourcentage de ressources soit interrompu pendant un processus de migration, en raison de l’absence d’une dépendance soutenue de l’utilisateur final.
- **Quelles sont les estimations descendantes de l’échelle des ressources pouvant être migrées ?** Pour les charges de travail incluses pour la migration, estimez le nombre de ressources sous-jacentes, telles que les applications, les machines virtuelles, les sources de données et les appliances informatiques. Pour obtenir des conseils sur l’identification des ressources pertinentes, consultez la section [Patrimoine numérique](../../../digital-estate/index.md) du Framework d’adoption du cloud.

### <a name="effort-timing"></a>Calendrier de l’effort

Souvent, les migrations sont motivées par un événement métier attrayant qui est sensible au facteur temps. Par exemple, une motivation courante est la résiliation ou le renouvellement d’un contrat d’hébergement tiers. Bien qu’il existe de nombreux événements métier potentiels nécessitant une migration, ils partagent un point commun : une date de fin. Il est important de comprendre le calendrier de tout événement métier à venir, afin que les activités et la vélocité puissent être planifiées et validées correctement.

## <a name="recap"></a>Récapitulatif

Avant de continuer, documentez les hypothèses suivantes et partagez-les avec les équipes de stratégie cloud et d’adoption du cloud :

- Résultats métier.
- Rôles. Ceci sera documenté et affiné pour les processus *Évaluer*, *Migrer*, *Optimiser* et *Sécuriser et gérer* de la migration.
- Définition de Terminé. Ceci sera documenté et affiné séparément pour les processus *Évaluer*, *Migrer*, *Optimiser* et *Sécuriser et gérer* de la migration.
- Type d’effort.
- Échelle de l’effort.
- Calendrier de l’effort.

## <a name="next-steps"></a>Étapes suivantes

Une fois le processus compris par l’équipe, il est temps de passer en revue les prérequis techniques. La [check-list de planification de l’environnement de migration](./planning-checklist.md) permet de s’assurer que la base technique est prête pour la migration.

Une fois que le processus est compris par les membres de l’équipe, il est temps de passer en revue les prérequis techniques la [check-list de planification de la migration] permettra de s’assurer que la base technique est prête pour la migration.

> [!div class="nextstepaction"]
> [Vérifier la check-list de planification de la migration](./planning-checklist.md)
