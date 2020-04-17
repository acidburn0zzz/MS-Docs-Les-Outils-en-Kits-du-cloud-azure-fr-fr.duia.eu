---
title: Construction d’une organisation sensible aux coûts
description: Utilisez le Cloud Adoption Framework pour Azure afin de découvrir les bonnes pratiques liées à la création d’une organisation soucieuse des coûts.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.openlocfilehash: 714bd0d26a38a1ee3a3cb2bfc2d336d1ffd4f45c
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80428517"
---
# <a name="build-a-cost-conscious-organization"></a>Construire une organisation sensible aux coûts

Comme indiqué dans [Motivations : Pourquoi migrons-nous vers le cloud ?](../strategy/motivations.md), il existe, pour une entreprise, de nombreuses raisons d’adopter le cloud. Lorsque la réduction des coûts est une motivation majeure, il est important de créer une organisation sensible aux coûts.

Assurer une sensibilisation aux coûts n’est pas une activité ponctuelle. Comme d’autres sujets en lien avec l’adoption du cloud, il s’agit d’une activité itérative. Le diagramme suivant décrit ce processus en se concentrant sur trois activités interdépendantes : *visibilité*, *responsabilité financière* et *optimisation*. Ces processus s’exécutent au niveau macro et micro, que nous décrivons en détail dans cet article.

![Processus sensible aux coûts](../_images/ready/cost-optimization-process.png)
*Figure 1 : Structure de l’organisation sensible aux coûts.*

## <a name="general-cost-conscious-processes"></a>Processus sensibles aux coûts généraux

- **Visibilité :** Pour qu’une organisation soit sensible aux coûts, elle a besoin de visibilité sur ces coûts. La visibilité dans une organisation sensible aux coûts exige des rapports cohérents pour les équipes qui adoptent le cloud, les équipes financières qui gèrent les budgets et les équipes de management responsables des coûts. Cette visibilité est obtenue en établissant ce qui suit :
  - L’étendue des rapports appropriée.
  - L’organisation des ressources appropriée (groupes d’administration, groupes de ressources, abonnements).
  - Des stratégies de catégorisation claires.
  - Des contrôles d’accès appropriés (RBAC).

- **Responsabilité financière :** La responsabilité financière est aussi importante que la visibilité. La responsabilité financière commence par des budgets clairs dédiés aux efforts d’adoption. Ces budgets doivent être bien établis, clairement communiqués et basés sur des attentes réalistes. La responsabilité financière exige un processus itératif et une volonté de croissance pour atteindre son niveau adéquat.

- **Optimisation :** L’optimisation est l’action qui crée les réductions de coûts. Pendant l’optimisation, les allocations de ressources sont modifiées pour réduire le coût de prise en charge de différentes charges de travail. Ce processus nécessite une itération et une expérimentation. Chaque réduction de coût réduit les performances. Trouver le bon équilibre entre les attentes en matière de contrôle des coûts et de performances des utilisateurs finaux exige la contribution de plusieurs parties.

Les sections suivantes décrivent les rôles que l’*équipe de stratégie cloud*, l’*équipe d’adoption du cloud*, l’*équipe de gouvernance cloud* et le *centre d’excellence du cloud (CCoE)* jouent dans le développement d’une organisation sensible aux coûts.

## <a name="cloud-strategy-team"></a>Équipe de stratégie cloud

L’élaboration d’une sensibilisation aux coûts dans le cadre des efforts d’adoption du cloud commence au niveau du leadership. Pour être efficace à long terme, l’[équipe de stratégie cloud](./cloud-strategy.md) doit inclure un membre du service financier. Si votre structure financière inclut des directeurs commerciaux responsables du coût des solutions, ceux-ci doivent également être invités à rejoindre l’équipe. En plus des activités de base généralement affectées à l’équipe de stratégie cloud, tous les membres de cette équipe ont également les responsabilités suivantes :

- **Visibilité :** L’équipe de stratégie cloud et l’[équipe de gouvernance cloud](./cloud-governance.md) ont besoin de connaître les coûts réels des efforts d’adoption du cloud. Compte tenu du caractère dirigeant de cette équipe, elle doit avoir accès à plusieurs étendues de coût pour analyser les décisions liées aux dépenses. En règle générale, un dirigeant a besoin d’une visibilité sur les coûts totaux pour l’ensemble des « dépenses » liées au cloud. Mais en tant que membres actifs de l’équipe de stratégie cloud, l’équipe doit aussi être capable d’afficher les coûts par division ou par unité de facturation pour valider les [modèles de comptabilité cloud](../strategy/cloud-accounting.md) de type showback, chargeback ou autre.

- **Responsabilité financière :** Des budgets doivent être établis entre les équipes de stratégie cloud, de [gouvernance cloud](./cloud-governance.md) et d’[adoption du cloud](./cloud-adoption.md) en fonction des activités d’adoption attendues. Quand des écarts par rapport au budget se produisent, l’équipe de stratégie cloud et l’équipe de gouvernance cloud doivent s’associer pour déterminer rapidement la meilleure marche à suivre pour les corriger.

- **Optimisation :** Pendant les efforts d’optimisation, l’équipe de stratégie cloud peut représenter l’investissement et la valeur de retour de charges de travail spécifiques. Si une charge de travail a une valeur stratégique ou un impact financier sur l’entreprise, les efforts d’optimisation des coûts doivent être supervisés de près. S’il n’existe aucun impact stratégique sur l’organisation et aucun coût inhérent aux faibles performances d’une charge de travail, l’équipe de stratégie cloud peut approuver la suroptimisation. Pour prendre ces décisions, l’équipe doit être en mesure de voir les coûts par projet.

## <a name="cloud-adoption-team"></a>Équipe d’adoption du cloud

L’[équipe d’adoption du cloud](./cloud-adoption.md) est au centre de toutes les activités d’adoption. Ainsi, elle constitue la première ligne de défense contre les dépassements budgétaires. Cette équipe joue un rôle actif dans les trois phases de sensibilisation aux coûts.

- **Visibilité :**

  - **Prise de conscience :** Il est important pour l’équipe d’adoption du cloud d’avoir une visibilité sur les objectifs de réduction des coûts de l’effort. Se contenter d’affirmer que l’effort d’adoption du cloud va permettre de réduire les coûts est le meilleur moyen d’échouer. Une visibilité *spécifique* est importante. Par exemple, si l’objectif est de réduire le coût total de possession du centre de données de 3 % ou les frais d’exploitation annuels de 7 %, révélez ces cibles au plus tôt et distinctement.
  - **Données de télémétrie :** Cette équipe a besoin d’une visibilité sur l’impact de ses décisions. Au cours des activités de migration ou d’innovation, les décisions de cette équipe ont un effet direct sur les coûts et les performances. L’équipe a besoin d’équilibrer ces deux facteurs contradictoires. La supervision des performances et la supervision des coûts dont l’étendue se limite aux projets actifs de l’équipe sont importantes pour offrir la visibilité nécessaire.

- **Responsabilité financière :** L’équipe d’adoption du cloud a besoin de connaître tous les budgets prédéfinis associés à ses efforts d’adoption. Quand les coûts réels ne sont pas alignés sur le budget, il est possible de créer une responsabilité financière. Celle-ci ne revient pas à pénaliser l’équipe d’adoption pour avoir dépassé le budget, car l’excédent de budget peut être dû à des décisions prises par nécessité pour les performances. La responsabilité financière consiste plutôt à éduquer l’équipe sur les objectifs et la façon dont ses décisions affectent ces objectifs. De plus, la responsabilité financière implique de faciliter le dialogue pour que l’équipe puisse communiquer sur les décisions qui ont conduit au dépassement du budget. Si ces décisions vont à l’encontre des objectifs du projet, cet effort offre une bonne opportunité de collaborer avec l’équipe de stratégie cloud pour prendre de meilleures décisions.

- **Optimisation :** Cet effort est un acte d’équilibrage, car l’optimisation des ressources peut réduire les performances des charges de travail qu’elles prennent en charge. Parfois, les économies prévues ou budgétées ne peuvent pas être réalisées pour une charge de travail, car cette charge de travail ne s’effectue pas correctement avec les ressources budgétées. Dans ce cas, l’équipe d’adoption du cloud doit prendre des décisions judicieuses et signaler les changements à l’équipe de stratégie cloud et à l’équipe de gouvernance cloud afin que les budgets ou les décisions d’optimisation puissent être corrigés.

## <a name="cloud-governance-team"></a>Équipe de gouvernance cloud

En règle générale, l’[équipe de gouvernance cloud](./cloud-governance.md) est responsable de la gestion des coûts pour tout l’effort d’adoption du cloud. Comme indiqué dans la rubrique relative à la [discipline Gestion des coûts](../govern/cost-management/index.md) dans la méthodologie de gouvernance du Framework d’adoption du cloud, la gestion des coûts est la première des cinq disciplines de gouvernance cloud. Ces articles présentent une série de responsabilités plus profondes pour l’équipe de gouvernance cloud.

Cet effort se concentre sur les activités suivantes, liées au développement d’une organisation sensible aux coûts :

- **Visibilité :** L’équipe de gouvernance cloud travaille en tant que pair de l’équipe de stratégie cloud pour planifier des budgets d’adoption du cloud. Ces deux équipes collaborent également pour contrôler régulièrement les dépenses réelles. L’équipe de gouvernance cloud se charge de garantir la génération cohérente et fiable de rapports sur les coûts et de données de télémétrie.

- **Responsabilité financière :** Quand des écarts par rapport au budget se produisent, l’équipe de stratégie cloud et l’équipe de gouvernance cloud doivent s’associer pour déterminer rapidement la meilleure marche à suivre pour les corriger. En règle générale, l’équipe de gouvernance cloud se conforme à ces décisions. Parfois, l’action peut correspondre à une simple formation pour l’[équipe d’adoption du cloud](./cloud-adoption.md) concernée. L’équipe de gouvernance cloud peut également permettre d’optimiser les ressources déployées, de modifier les options de remise ou d’implémenter des options de contrôle des coûts automatisé comme le blocage du déploiement des ressources non planifiées.

- **Optimisation :** Une fois que les ressources ont migré vers le cloud ou y sont créées, vous pouvez utiliser des outils de supervision pour évaluer les performances et l’utilisation de ces ressources. Des données de supervision et de performances appropriées peuvent identifier les ressources à optimiser. L’équipe de gouvernance cloud se charge de veiller à ce que les outils de supervision et de création de rapports sur les coûts soient systématiquement déployés. Elle peut aussi aider les équipes d’adoption à identifier les opportunités d’optimisation en fonction des performances et des données de télémétrie sur les coûts.

## <a name="cloud-center-of-excellence"></a>Centre d’excellence de cloud

Bien qu’il ne soit généralement pas responsable de la gestion des coûts, le CCoE peut exercer un impact significatif sur les organisations sensibles aux coûts. De nombreuses décisions fondamentales en matière d’informatique ont des répercussions sur les coûts à grande échelle. Quand le CCoE joue son rôle, les coûts peuvent être réduits pour plusieurs efforts d’adoption du cloud.

- **Visibilité :** Tout groupe d’administration ou groupe de ressources qui héberge des ressources informatiques essentielles doit être visible par l’équipe du CCoE. L’équipe peut utiliser ces données pour créer des opportunités d’optimisation.

- **Responsabilité financière :** Bien qu’il ne soit généralement pas responsable des coûts, le CCoE peut se charger de créer des solutions reproductibles qui minimisent les coûts et optimisent les performances.

- **Optimisation :** Étant donné la visibilité du CCoE pour plusieurs déploiements, l’équipe se trouve dans une position idéale pour suggérer des conseils d’optimisation et aider les équipes d’adoption à mieux ajuster les ressources.

## <a name="next-steps"></a>Étapes suivantes

La pratique de ces responsabilités à chaque niveau de l’entreprise permet de construire une organisation sensible aux coûts. Pour commencer à suivre ces conseils, passez en revue l’[introduction à la préparation de l’organisation](./index.md) pour identifier les structures d’équipe appropriées.

> [!div class="nextstepaction"]
> [Identifier les structures d’équipe appropriées](./index.md)
