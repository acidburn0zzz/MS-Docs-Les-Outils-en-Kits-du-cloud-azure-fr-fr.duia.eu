---
title: Exemples de résultats comptables
description: Utilisez le Cloud Adoption Framework pour Azure afin de percevoir les résultats opérationnels dans le contexte d’une transformation cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 374fe7d5aee3a2277f3bd8c6188f132756e538a1
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83815359"
---
# <a name="examples-of-fiscal-outcomes"></a>Exemples de résultats comptables

Au niveau le plus haut, les discussions en matière de comptabilité portent sur trois concepts de base :

- **Chiffre d’affaires :** L’entreprise gagnera-t-elle plus d’argent suite à la vente de biens ou de services ?
- **Coût :** Est-ce que moins d’argent sera consacré à la création, au marketing, à la vente ou à la livraison de biens ou de services ?
- **Bénéfices :** Bien que rares, certaines transformations peuvent à la fois augmenter le chiffre d’affaires et réduire les coûts. Il s’agit d’un résultat bénéficiaire.

Le reste de cet article explique ces résultats comptables dans le contexte d’une transformation cloud.

> [!NOTE]
> Les exemples suivants sont basés sur des hypothèses et ne doivent pas être considérés comme une garantie de retour lors de l’adoption d’une stratégie cloud.

## <a name="revenue-outcomes"></a>Résultats en termes de chiffre d’affaires

### <a name="new-revenue-streams"></a>Nouveaux flux de revenus

Le cloud permet de créer des opportunités pour fournir de nouveaux produits à des clients ou fournir des produits existants d’une nouvelle façon. Les nouveaux flux de revenus sont une source d’innovation, d’entrepreneuriat et de motivation pour de nombreuses personnes dans le monde des affaires. Toutefois, ils sont aussi sources d’échec et sont perçus par un grand nombre d’entreprises comme un grand risque. Les résultats corrélés au chiffre d’affaires proposés par le service informatique sont généralement mal accueillis. Pour renforcer la crédibilité de ces revenus, établissez un partenariat avec un chef d’entreprise reconnu pour ses innovations. Une validation du flux de revenus tôt dans le processus permet à l’entreprise d’éviter les obstacles.

- **Exemple :** Une société vend des livres depuis plus de cent ans. Un employé de la société réalise que le contenu des livres peut être distribué par voie électronique. Il crée un appareil qui peut être vendu dans la librairie et qui permet de les télécharger directement, et ainsi de générer _x euros_ par les nouvelles ventes.

### <a name="revenue-increases"></a>Augmentation du chiffre d’affaires

D’une portée mondiale et numérique, le cloud permet aux entreprises d’augmenter le chiffre d’affaires des flux de revenus existants. Il arrive souvent que ce type de résultat provienne d’un alignement avec la direction des ventes ou du marketing.

- **Exemple :** Une entreprise qui commercialise des appareils pourrait en vendre plus si les vendeurs pouvaient accéder de façon sécurisée au catalogue numérique et aux niveaux des stocks de l’entreprise. Malheureusement, ces données se trouvent seulement dans le système ERP de l’entreprise, qui est accessible uniquement via un appareil connecté au réseau. La création d’un service frontal pour s’interfacer avec l’ERP en exposant la liste du catalogue et les niveaux des stocks non sensibles à une application dans le cloud permettrait aux vendeurs d’accéder aux données dont ils ont besoin tandis qu’ils se trouvent sur site chez un client. L’extension d’Active Directory localement avec Azure Active Directory (Azure AD) et l’intégration des accès en fonction du rôle dans l’application permettraient à l’entreprise de garantir la sécurisation des données. Ce projet simple pourrait avoir un impact de _x %_ sur le chiffre d’affaires d’une ligne de produits existante.

### <a name="profit-increases"></a>Augmentation des bénéfices

Il est rare qu’un même effort augmente les revenus et réduit les coûts simultanément. Néanmoins, quand cela se produit, alignez les résultats d’un ou plusieurs des revenus générés sur l’un ou plusieurs des coûts générés pour communiquer le résultat souhaité.

## <a name="cost-outcomes"></a>Résultats en termes de coûts

### <a name="cost-reduction"></a>Réduction des coûts

Le cloud computing peut réduire les dépenses d’investissement liées à l’achat de matériel et de logiciel, à la configuration des centres de données, au fonctionnement des centres de données sur site, etc. Les coûts des racks de serveurs, l’alimentation électrique permanente pour le fonctionnement et le refroidissement, et les experts en informatique pour la gestion de l’infrastructure s’additionnent rapidement. L’arrêt d’un centre de données peut réduire les engagements en matière de dépenses d’investissement. Ceci est communément appelé « getting out of the data center business » (Sortie de l’activité des centres de données). La réduction des coûts est généralement mesurée en euros dans le budget courant, qui peut couvrir de une à cinq années, selon la façon dont le directeur financier gère les finances.

- **Exemple no 1 :** Le centre de données d’une entreprise consomme un pourcentage important du budget informatique annuel. Le département informatique choisit d’effectuer une migration cloud et de transformer les ressources de ce centre de données vers des solutions IaaS (Infrastructure as a Service), ce qui génère une réduction des coûts de trois ans.
- **Exemple no 2 :** Une société de portefeuille a récemment acquis une nouvelle entreprise. Dans le cadre de l’acquisition, les termes du contrat indiquent que la nouvelle entité doit être supprimée des centres de données dans les six mois. Si cela n’est pas fait, une pénalité de 1 million d’euros par mois en découle au profit de la société de portefeuille. Le déplacement des ressources numériques vers le cloud dans le cadre d’une migration cloud pourrait permettre une mise hors service rapide des anciennes ressources.
- **Exemple no 3 :** Une société qui s’occupe de la gestion des impôts sur le revenu de particuliers réalise 70 pour cent de son chiffre d’affaires annuel au cours des trois premiers mois de l’année. Le reste de l’année, son important investissement dans l’informatique est relativement peu utilisé. Une migration cloud permettrait au département informatique de déployer la capacité de traitement/hébergement nécessaire pour ces trois mois. Pendant les 9 mois restants, les coûts IaaS pourraient être considérablement réduits en diminuant la surface du système informatique.

<!-- docsTest:ignore "Ryan Sorensen" "Director of Application Development and Enterprise Architecture" 1M -->
<!-- cSpell:ignore Coverdell Coverdell's Sorensen -->

### <a name="example-coverdell"></a>Exemple : Coverdell

Coverdell modernise son infrastructure afin de réaliser des économies de coûts avec Azure. La décision de Coverdell d’investir dans Azure et d’unifier son réseau de sites web, ses applications, ses données et son infrastructure au sein de cet environnement a permis de réaliser davantage d’économies que ce que la société attendait. La migration vers un environnement entièrement Azure a diminué de 54 000 euros les coûts mensuels pour les services de colocation. Avec son infrastructure nouvelle et unifiée, Coverdell s’attend à économiser environ 1 million d’euros au cours des deux à trois prochaines années.

> « L’accès à l’ensemble des technologies Azure ouvre la porte à des solutions scalables, faciles à implémenter et avec une haute disponibilité, qui se révèlent être rentables. Ainsi, nos architectes peuvent être bien plus créatifs dans les solutions qu’ils fournissent. »
>
> Ryan Sorensen
>
> Directeur du développement des applications et de l’architecture d’entreprise
>
> Coverdell

### <a name="cost-avoidance"></a>Évitement des coûts

La mise hors service des centres de données peut également permettre une suppression des coûts, car elle permet d’éviter les cycles d’actualisation ultérieurs. Un cycle de renouvellement est un processus consistant à acheter de nouveaux matériels et logiciels pour remplacer des systèmes locaux vieillissants. Dans Azure, le matériel et le système d’exploitation sont maintenus, corrigés et actualisés régulièrement sans coût supplémentaire pour les clients. Ceci permet à un directeur financier d’éliminer certaines dépenses planifiées futures dans les prévisions financières à long terme. La suppression des coûts se mesure en euros. Elle diffère de la réduction des coûts en cela qu’elle est centrée sur un budget futur qui n’a pas encore été entièrement approuvé.

- **Exemple :** Le centre de données d’une entreprise doit faire l’objet d’un renouvellement de bail dans six mois. Le centre de données est en service depuis huit ans. Il y a quatre ans, tous les serveurs ont été actualisés et virtualisés, ce qui a coûté des millions d’euros à l’entreprise. L’année prochaine, l’entreprise prévoit d’actualiser à nouveau le matériel et les logiciels. La migration des ressources de ce centre de données dans le cadre d’une migration cloud permettrait une suppression de coûts, en éliminant l’actualisation planifiée du budget prévu pour l’année prochaine. Elle pourrait également produire une réduction des coûts en réduisant ou en éliminant les coûts liés à la location des locaux.

### <a name="capital-expenses-and-operating-expenses"></a>Dépenses d’investissement et dépenses d’exploitation

Avant d’aborder les coûts, il est important de comprendre les deux options de coût principales : les dépenses d’investissement et les dépenses d’exploitation.

Les termes suivants vous aideront à comprendre les différences entre les dépenses d’investissement et les dépenses d’exploitation au cours des discussions commerciales sur un projet de transformation.

- Un **investissement** est de l’argent et des actifs appartenant à une entreprise, destiné à contribuer à un objectif particulier, comme augmenter la capacité d’un serveur ou créer une application.
- Les **dépenses d’investissement** produisent des avantages sur une longue période. Ces dépenses sont généralement non récurrentes et aboutissent à l’acquisition de ressources permanentes. La création d’une application peut être qualifiée de dépense d’investissement.
- Les **dépenses d’exploitation** sont des dépenses normales de fonctionnement de l’entreprise. La consommation de services cloud dans un modèle de paiement à l’utilisation peut être qualifiée de dépense d’exploitation.
- Les **actifs** sont des ressources économiques qui peuvent être détenues ou contrôlées pour produire de la valeur. Des serveurs, des lacs de données et des applications peuvent tous être considérés comme des actifs.
- La **dépréciation** correspond à la diminution de la valeur d’un actif au fil du temps. Plus pertinente pour les conversations sur les dépenses d’investissement et les dépenses d’exploitation, la dépréciation est la façon dont les coûts d’un actif sont alloués entre les périodes auxquelles il est utilisé. Par exemple, si vous créez une application cette année, mais que sa durée d’utilisation moyenne prévue est de cinq ans (comme pour la plupart des applications), le coût de l’équipe de développement et des outils nécessaires pour créer et déployer la base de code serait amorti uniformément sur cinq années.
- La **valorisation** est le processus d’estimation de la valeur d’une entreprise. Dans la plupart des secteurs d’activité, la valorisation est basée sur la capacité de l’entreprise à générer du chiffre d’affaires et du bénéfice, tout en respectant les coûts d’exploitation nécessaires pour créer les biens qui sont à l’origine de ce chiffre d’affaires. Dans certains secteurs tels que la distribution ou dans certains types de transactions tels que le capital investissement, les actifs et la dépréciation peuvent jouer un rôle important dans la valorisation de la société.

Il y a fort à parier que différents dirigeants, y compris le responsable des investissements, discutent de la meilleure utilisation du capital pour développer la société dans la direction voulue. Donner au responsable des investissements le moyen de convertir des discussions sur les dépenses d’investissement litigieuses en objectifs comptables clairs de dépenses d’exploitation peut être un résultat intéressant par lui-même. Dans de nombreux secteurs, les directeurs financiers recherchent activement des moyens pour mieux associer des chiffrages comptables au coût des biens vendus.

Cependant, avant d’associer des parcours de transformation à ce type de conversion des dépenses d’investissement en dépenses d’exploitation, il est judicieux de rencontrer des membres des équipes de la direction financière ou informatique pour déterminer quelle structure de coûts l’entreprise préfère. Dans certaines organisations, la réduction des dépenses d’investissement en faveur des dépenses d’exploitation engendre des réticences. Comme mentionné plus haut, cette approche est adoptée parfois dans les sociétés de distribution, de portefeuille ou de capital investissement, qui accordent une valeur plus importante aux modèles traditionnels de comptabilisation des actifs, lesquels accordent une valeur minime à l’informatique. Vous pouvez aussi le voir dans les organisations qui ont eu dans le passé des expériences négatives lorsqu’elles externalisent leur service informatique ou d’autres fonctions.

Si un modèle de dépenses d’exploitation est souhaitable, l’exemple suivant peut être un résultat viable pour l’entreprise :

- **Exemple :** Le centre de données de l'entreprise se déprécie de _x euros_ par an pour les trois prochaines années. Il est prévu que _y euros_ seront nécessaires pour actualiser le matériel au cours des prochaines années. Nous pouvons convertir les dépenses d'investissement en un modèle de dépenses d'exploitation à un coût uniforme de _z euros_ par mois, ce qui permet une meilleure gestion et un meilleur contrôle des coûts d'exploitation de la technologie.

## <a name="next-steps"></a>Étapes suivantes

Apprenez-en davantage sur les [résultats au niveau de l’agilité](./agility-outcomes.md).

> [!div class="nextstepaction"]
> [Résultats au niveau de l’agilité](./agility-outcomes.md)
