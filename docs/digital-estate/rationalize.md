---
title: Rationaliser le patrimoine numérique
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Évaluez vos ressources numériques pour déterminer la meilleure façon de les héberger dans le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: 17087228df93164a697b86c7c3934278a55bf91b
ms.sourcegitcommit: f7ec7828687f433ff8b69b91817cbec7b074662c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72915017"
---
# <a name="rationalize-the-digital-estate"></a>Rationaliser le patrimoine numérique

La rationalisation du cloud est le processus qui consiste à évaluer des ressources dans le but de déterminer la meilleure façon de les héberger dans le cloud. Une fois que vous avez déterminé une [approche](./approach.md) et compilé un [inventaire](./inventory.md), la rationalisation du cloud peut commencer. La rubrique [Rationalisation du cloud](./rationalize.md) traite des options de rationalisation les plus courantes.

## <a name="traditional-view-of-rationalization"></a>Considérations traditionnelles sur la rationalisation

La rationalisation est facile à comprendre lorsque vous visualisez le processus traditionnel de rationalisation sous la forme d’un arbre de décision complexe. Chaque ressource du patrimoine numérique est analysée par un processus qui aboutit à l’un des cinq résultats possibles (les cinq R). Ce processus fonctionne bien pour les petits patrimoines. Pour les gros patrimoines, en revanche, il n’est pas efficace et peut entraîner d’importants retards. Pour comprendre pourquoi, examinons de plus près ce processus. Ensuite, nous présenterons un modèle plus efficace.

**Inventaire :** Il est nécessaire d’effectuer un inventaire complet des ressources, y compris des applications, des logiciels, du matériel, des systèmes d’exploitation et des métriques de performances système, afin de réaliser une rationalisation complète à l’aide de modèles traditionnels.

**Analyse quantitative :** Dans l’arbre de décision, ce sont les questions quantitatives qui déterminent la première couche de décisions. Les questions courantes sont les suivantes : Cette ressource est-elle actuellement utilisée ? Si oui, est-elle correctement optimisée et dimensionnée ? Quelles sont les dépendances qui existent entre les ressources ? Ces questions sont essentielles à la classification de l’inventaire.

**Analyse qualitative :** L’ensemble de décisions suivant nécessite une intelligence humaine dans le but d’effectuer une analyse qualitative. Souvent, ces questions sont propres à la solution et peuvent uniquement être posées aux parties prenantes et aux utilisateurs avancés. Ces décisions retardent généralement le processus, ce qui ralentit considérablement les choses. Cette analyse nécessite généralement 40 à 80 heures de travail à temps plein par application.

Pour des conseils sur la création d’une liste de questions d’analyse qualitative, consultez [Approches de la planification du patrimoine numérique](./approach.md).

**Décision de rationalisation :** Une équipe de rationalisation expérimentée sait analyser les données qualitatives et quantitatives pour prendre des décisions éclairées. Malheureusement, de telles équipes coûtent cher à l’embauche ou nécessitent des mois de formation.

## <a name="rationalization-at-enterprise-scale"></a>Rationalisation de l’échelle de l’entreprise

Si ce processus paraît long et fastidieux pour un patrimoine numérique constitué de 50 machines virtuelles, imaginez l’effort nécessaire pour mener à bien la transformation de l’entreprise dans un environnement comprenant des milliers de machines virtuelles et des centaines d’applications. L’effort humain nécessaire peut facilement dépasser 1 500 heures de travail à temps plein et neuf mois de planification.

Même si la rationalisation complète constitue à la fois l’objectif final et un excellent moyen d’aller de l’avant, il est rare qu’elle génère un retour sur investissement important si l’on prend en compte le temps et l’énergie qui y ont été consacrés.

Lorsque la rationalisation est essentielle pour la prise de décisions financières, il est conseillé de faire appel à des entreprises spécialistes en rationalisation du cloud pour accélérer le processus. Cela dit, même dans ce cas, la rationalisation complète peut être fastidieuse et coûteuse, et peut retarder la transformation ou les résultats pour votre entreprise.

Le reste de cet article décrit une alternative, appelée « rationalisation incrémentielle ».

## <a name="incremental-rationalization"></a>Rationalisation incrémentielle

La rationalisation complète d’un gros patrimoine numérique implique des risques, et peut subir des retards en raison de sa complexité. L’approche incrémentielle part du principe que les décisions retardées permettent de répartir la charge de l’entreprise afin de réduire les risques de blocages. Avec le temps, cette approche crée un modèle organique permettant de développer les processus et l’expérience nécessaires pour prendre des décisions de rationalisation éclairées et efficaces.

### <a name="inventory-reduce-discovery-data-points"></a>Inventaire : Réduire le nombre de points de données de découverte

Très peu d’organisations consacrent le temps, l’énergie et les ressources nécessaires à un inventaire précis et en temps réel du patrimoine numérique complet. Les pertes, les vols, les cycles d’actualisation et l’intégration de nouveaux employés justifient souvent un suivi détaillé des ressources sur les appareils des utilisateurs finaux. Toutefois, le retour sur investissement associé au maintien d’un inventaire précis du serveur et des applications dans un centre de données local traditionnel, est souvent faible. La plupart des entreprises d’informatique ont des problèmes plus urgents que celui d’effectuer le suivi de l’utilisation des ressources au sein d’un centre de données.

Dans une transformation cloud, l’inventaire est directement lié aux coûts d’exploitation. Pour une bonne planification, vous devez disposer de données d’inventaire exactes. Malheureusement, les options d’analyse de l’environnement peuvent retarder les décisions de plusieurs semaines, voire de plusieurs mois. Heureusement, quelques astuces peuvent accélérer la collecte des données.

L’analyse basée sur l’agent est la source de retard la plus fréquemment citée. Les données robustes nécessaires à une rationalisation traditionnelle peuvent souvent uniquement être collectées en exécutant un agent sur chacune des ressources. Cette dépendance aux agents ralentit souvent la progression, car elle peut nécessiter les commentaires des équipes chargées de la sécurité, des opérations et de l’administration.

Dans un processus de rationalisation incrémentielle, vous pouvez utiliser une solution sans agent pour une découverte initiale visant à accélérer les premières décisions. Selon le niveau de complexité de l’environnement, une solution basée sur l’agent peut rester nécessaire. Toutefois, elle peut être supprimée du chemin critique vers le changement.

### <a name="quantitative-analysis-streamline-decisions"></a>Analyse quantitative : Simplifier la prise de décisions

Quelle que soit l’approche que vous choisissez pour la découverte de l’inventaire, l’analyse quantitative peut déboucher sur un certain nombre de décisions et d’hypothèses initiales. Cela est particulièrement vrai lorsque vous tentez d’identifier la première charge de travail ou lorsque l’objectif de la rationalisation est d’obtenir une comparaison générale des coûts. Dans un processus de rationalisation incrémentielle, l’équipe de stratégie cloud et l’équipe chargée de l’adoption du cloud limitent les [5 R de la rationalisation](./5-rs-of-rationalization.md) à deux décisions concises et appliquent uniquement ces facteurs quantitatifs, dans le but de simplifier l’analyse et de réduire la quantité de données initiales nécessaires au changement.

Par exemple, si une organisation est en cours de migration IaaS vers le cloud, vous pouvez supposer que la plupart des charges de travail seront mises hors service ou réhébergées.

### <a name="qualitative-analysis-temporary-assumptions"></a>Analyse qualitative : Hypothèses temporaires

En réduisant le nombre de résultats possibles, il est plus facile de prendre une première décision au sujet de l’état futur d’une ressource. Lorsque vous réduisez les options, vous réduisez aussi le nombre de questions posées à ce stade.

Par exemple, si les options sont limitées au réhébergement ou à la mise hors service, l’entreprise doit répondre à une seule question au cours de la rationalisation initiale, à savoir s’il faut mettre hors service la ressource.

« L’analyse indique qu’aucun utilisateur n’utilise activement cette ressource. Est-ce exact ou avons-nous négligé quelque chose ? » Il est généralement beaucoup plus facile de répondre à cette question binaire en effectuant une analyse qualitative.

Cette approche simplifiée produit des lignes de base, des plans financiers, une stratégie et une direction. Par la suite, chaque ressource fait l’objet d’une rationalisation et d’une analyse qualitative afin d’évaluer d’autres options. Toutes les hypothèses que vous poserez dans cette rationalisation initiale sont testées avant

## <a name="challenge-assumptions"></a>Remettre en question les hypothèses

Le résultat de la section précédente est une rationalisation approximative chargée d’hypothèses. À présent, il est temps de mettre à l’épreuve certaines de ces hypothèses.

### <a name="retire-assets"></a>Mettre hors service des ressources

Dans un environnement local traditionnel, il est rare que l’hébergement de ressources petites et peu utilisées ait un impact significatif sur les coûts annuels. À quelques exceptions près, les efforts en termes de temps de travail nécessaires à l’analyse et à la mise hors service des ressources compensent largement les économies que représentent la déconnexion et la mise hors service de ces ressources.

Toutefois, lorsque vous passez à un modèle de comptabilité dans le cloud, la mise hors service des ressources peut vous permettre de réaliser d’importantes économies au niveau des coûts d’exploitation annuels et des premiers efforts de migration.

Après l’analyse quantitative, il n’est pas rare que les organisations mettent hors service 20 % (voire plus) de leur patrimoine numérique. Nous vous recommandons d’effectuer une analyse qualitative plus approfondie avant une telle décision. Une fois la confirmation acquise, la mise hors service de ces ressources peut vous permettre d’atteindre pour la première fois un retour sur investissement dans le cadre de la migration vers le cloud. Dans de nombreux cas, c’est l’un des plus importants facteurs de réduction des coûts. Par conséquent, il est recommandé que l’équipe de stratégie cloud supervise la validation et la mise hors service des ressources parallèlement à la phase de développement du processus de migration, afin d’obtenir un retour sur investissement plus rapide.

### <a name="program-adjustments"></a>Ajustements du programme

Il est rare qu’une entreprise n’ait qu’une seule à transformer. Le choix entre la réduction des coûts, la croissance de l’activité et la génération de nouveaux flux de revenus implique de nombreuses décisions. Par conséquent, nous vous conseillons que l’équipe de stratégie cloud collabore avec le service informatique dans le but d’identifier les ressources qui nécessitent des efforts de transformation parallèles et qui ne relèvent pas de la transformation initiale.

Dans l’exemple de migration IaaS présenté dans cet article :

- Demandez à l’équipe DevOps d’identifier les ressources qui font déjà partie d’un déploiement automatisé et supprimez-les du plan de migration principal.

- Demandez à l’équipe chargée des données et à l’équipe Recherche et Développement d’identifier les ressources qui génèrent de nouveaux flux de revenus et supprimez-les du plan de migration principal.

Cette analyse qualitative axée sur le programme peut être exécutée rapidement et permet un alignement entre plusieurs backlogs de migration.

Vous devrez peut-être encore évaluer certaines ressources comme ressources de réhébergement pendant un certain temps. Vous pouvez procéder à une rationalisation après la migration initiale.

## <a name="select-the-first-workload"></a>Sélectionner la première charge de travail

L’implémentation de la première charge de travail est essentielle pour les tests et pour l’apprentissage. Il s’agit de votre première occasion de développer et de démontrer votre volonté de croissance.

### <a name="business-criteria"></a>Critères commerciaux

Afin de garantir la transparence au sein de l’entreprise, identifiez une charge de travail qui est prise en charge par un membre de l’équipe de stratégie cloud. De préférence, choisissez une charge de travail appartenant à une équipe qui est fortement motivée pour passer au cloud et pour laquelle cela représente un enjeu important.

### <a name="technical-criteria"></a>Critères techniques

Sélectionnez une charge de travail ayant le moins de dépendances possible et qui peut être déplacée sous la forme d’un petit groupe de ressources. Nous vous recommandons de sélectionner une charge de travail avec un chemin d’accès de test défini afin de faciliter la validation.

La première charge de travail est souvent déployée dans un environnement expérimental sans aucune fonctionnalité opérationnelle ou de gouvernance. Il est très important de sélectionner une charge de travail qui n’interagit pas avec des données sécurisées.

### <a name="qualitative-analysis"></a>Analyse qualitative

Les équipes chargées de l’adoption du cloud et l’équipe chargée de l’adoption du cloud peuvent collaborer pour analyser cette petite charge de travail. Cette collaboration génère une opportunité contrôlée pour créer et tester les critères de l’analyse qualitative. Les petites charges de travail permettent d’interroger les utilisateurs affectés dans le but d’effectuer une analyse qualitative détaillée en une semaine maximum. Pour connaître les facteurs courants d’analyse qualitative, consultez la cible de rationalisation correspondante dans les [5 R de la rationalisation](./5-rs-of-rationalization.md).

### <a name="migration"></a>Migration

Parallèlement à la rationalisation continue, l’équipe chargée de l’adoption du cloud peut commencer à effectuer la migration de la petite charge de travail afin de développer ses connaissances dans les domaines clés suivants :

- Renforcer ses compétences au sujet de la plateforme du fournisseur de cloud.
- Définir les services principaux (et les standards Azure) qui sont nécessaires à une vision à long terme.
- Mieux comprendre comment les opérations peuvent être amenées à évoluer lors de la transformation.
- Comprendre les risques commerciaux inhérents ainsi que la tolérance de l’entreprise à de tels risques
- Établir une ligne de base ou un produit minimum viable (MVP) pour la gouvernance, en fonction de la tolérance de l’entreprise aux risques inhérents

## <a name="release-planning"></a>Planification de la mise en production

Pendant que l’équipe chargée de l’adoption du cloud effectue la migration ou l’implémentation de la première charge de travail, l’équipe de stratégie cloud peut commencer à classer les applications et les charges de travail restantes selon leur priorité.

### <a name="power-of-10"></a>Puissance 10

L’approche de rationalisation traditionnelle vise à répondre à tous les besoins envisageables. Heureusement, le processus de transformation ne nécessite pas toujours un plan pour chaque application. Dans un modèle incrémentiel, la méthode Puissance 10 constitue un bon point de départ. Dans ce modèle, l’équipe de stratégie cloud sélectionne les 10 premières applications devant faire l’objet d’une migration. Ces dix charges de travail doivent être un mélange de charges de travail simples et complexes.

### <a name="build-the-first-backlogs"></a>Créer les premiers backlogs

Les équipes chargées de l’adoption du cloud et l’équipe de stratégie cloud peuvent collaborer sur l’analyse qualitative des 10 premières charges de travail. Cet effort crée le premier backlog de migration hiérarchisé ainsi que le premier backlog de mise en production hiérarchisé. Cette méthode permet aux équipes de reproduire cette approche et de disposer de suffisamment de temps pour créer un processus d’analyse qualitative adéquat.

### <a name="mature-the-process"></a>Confirmer le processus

Une fois que les deux équipes sont d’accord sur les critères d’analyse qualitative, l’évaluation peut devenir une tâche au sein de chaque itération. En général, deux ou trois mises en production sont nécessaires pour atteindre un consensus sur les critères d’évaluation.

Une fois que l’évaluation est déplacée vers les processus d’exécution incrémentielle de la migration, l’équipe chargée de l’adoption du cloud peut reproduire l’évaluation et l’architecture plus rapidement. À ce stade, l’équipe de stratégie cloud n’est plus impliquée, ce qui allège sa charge de travail. Elle peut également se concentrer sur la priorité des applications qui ne sont pas encore en production, ce qui permet un bon alignement sur les conditions fluctuantes du marché.

Toutes les applications classées par ordre de priorité ne seront pas prêtes pour la migration. L’ordre de priorité est susceptible de changer une analyse qualitative plus approfondie ayant mis en lumière des événements commerciaux et des dépendances nécessitant un chargement de priorité du backlog. Certaines mises en production peuvent regrouper un petit nombre de charges de travail. D’autres peuvent ne contenir qu’une seule charge de travail.

L’équipe chargée de l’adoption du cloud est susceptible d’exécuter les itérations qui ne produisent pas une migration complète de la charge de travail. Plus la charge de travail est petite, et moins elle a de dépendances, mieux adaptée elle sera à un sprint ou à une itération. Pour cette raison, nous vous recommandons que les quelques premières applications du backlog de mise en production soient petites et qu’elles aient peu de dépendances externes.

## <a name="end-state"></a>État final

Avec le temps, l’équipe chargée de l’adoption du cloud et l’équipe de stratégie cloud obtiendront ensemble une rationalisation complète de l’inventaire. Toutefois, l’approche incrémentielle permet aux équipes d’accélérer continuellement leur processus de rationalisation. Elle aide la transformation à générer des résultats commerciaux tangibles plus rapidement, sans un effort d’analyse initiale aussi important.

Dans certains cas, le modèle financier peut être trop strict pour permettre une décision sans effectuer de rationalisation supplémentaire. Dans ce cas, vous pouvez adopter une approche de rationalisation plus traditionnelle.

## <a name="next-steps"></a>Étapes suivantes

La rationalisation génère un backlog hiérarchisé comprenant toutes les ressources qui seront affectées par la transformation choisie. Ce backlog est maintenant prêt à servir de base pour les modèles de coûts des services cloud.

> [!div class="nextstepaction"]
> [Aligner les modèles de coûts sur le patrimoine numérique](./calculate.md)
