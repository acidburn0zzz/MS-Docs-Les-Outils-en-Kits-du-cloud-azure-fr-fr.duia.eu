---
title: 'Gouvernance pour les entreprises standard : Améliorer la discipline de gestion des coûts'
description: Utilisez le Framework d’adoption du cloud pour Azure pour savoir comment ajouter des contrôles de coût à un produit minimum viable (MVP, minimum viable product) de gouvernance.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 3d0a4e06a2aaa21f191130b937790408abf16952
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80434292"
---
# <a name="standard-enterprise-guide-improve-the-cost-management-discipline"></a>Guide pour les entreprises standard : Améliorer la discipline Gestion des coûts

Cet article fait progresser le scénario en ajoutant des contrôles de coûts au MVP de gouvernance.

## <a name="advancing-the-narrative"></a>Développement du scénario

L'adoption a dépassé l'indicateur de tolérance des coûts défini dans le MVP de la gouvernance. Il s'agit d'une bonne chose car cela correspond aux migrations entreprises depuis le centre de données de récupération d'urgence. L’augmentation des dépenses justifie désormais un investissement en temps de la part de l’équipe de gouvernance cloud.

### <a name="changes-in-the-current-state"></a>Modifications apportées à l’état actuel

Lors de la phase précédente de ce scénario, le service informatique avait mis hors service 100 % du centre de données de récupération d'urgence. Les équipes de développement d'applications et BI étaient prêtes pour le trafic de production.

Depuis, certains changements ont eu lieu et ceux-ci vont avoir un impact sur la gouvernance :

- L'équipe de migration a commencé à migrer les machines virtuelles hors du centre de données de production.
- Les équipes de développement d'applications envoient (push) activement les applications de production vers le cloud par le biais de pipelines CI/CD. Ces applications peuvent s'adapter de manière réactive aux demandes des utilisateurs.
- L’équipe décisionnelle du service informatique a fourni plusieurs outils d’analyse prédictive dans le cloud. Les volumes de données agrégées dans le cloud continuent de croître.
- Cette croissance va dans le sens des engagements pris en matière de résultats opérationnels. En revanche, les coûts ont commencé à s'envoler. Les projections budgétaires augmentent plus rapidement que prévu. Le directeur financier a besoin de revoir les approches en matière de gestion des coûts.

### <a name="incrementally-improve-the-future-state"></a>Améliorer progressivement l’état futur

Des fonctionnalités de contrôle des coûts et de création de rapports doivent être ajoutées à la solution cloud. Le service informatique fait toujours office de chambre de compensation des coûts. Cela signifie que les achats informatiques continuent à financer les services cloud. Les rapports devraient cependant lier les frais d’exploitation directs aux fonctions qui absorbent les coûts du cloud. Ce modèle est appelé « Show Back » en termes de comptabilité cloud.

Les modifications apportées aux états actuel et futur exposent à de nouveaux risques qui nécessiteront de nouvelles instructions de stratégie.

## <a name="changes-in-tangible-risks"></a>Modifications apportées aux risques tangibles

**Contrôle du budget :** les fonctionnalités en libre-service risquent de générer des coûts excessifs et inattendus sur la nouvelle plateforme. Des processus de gouvernance permettant de surveiller les coûts et d’atténuer les risques permanents liés à ceux-ci doivent être en place pour garantir un alignement continu avec le budget prévu.

Ce risque métier peut s’associer à quelques risques techniques :

- Les coûts réels peuvent dépasser le plan.
- Les conditions métier évoluent. Dans ce cas, il peut arriver qu’une fonction métier utilise plus de services cloud que prévu, ce qui se traduit par des anomalies en termes de dépenses. Ces dépenses supplémentaires risquent alors d'être considérées comme des dépassements, par opposition à un ajustement nécessaire du plan.
- Les systèmes peuvent être surapprovisionnés et, par conséquent, générer des dépenses excessives.

## <a name="incremental-improvement-of-the-policy-statements"></a>Amélioration incrémentielle des instructions de stratégie

Les modifications suivantes apportées à la stratégie contribueront à traiter les nouveaux risques et à guider l’implémentation.

- Chaque semaine, l'équipe de gouvernance doit s'assurer que tous les coûts liés au cloud sont conformes au plan. Chaque mois, des rapports sur les écarts entre les coûts du cloud et ceux prévus par le plan doivent être remis aux responsables informatiques et au département financier. Chaque mois, toutes les mises à jour des coûts liés au cloud et prévus par le plan doivent être révisées par les responsables informatiques et le département financier.
- Tous les coûts doivent être affectés à une fonction opérationnelle à des fins de responsabilisation.
- Les ressources du cloud doivent être contrôlées en permanence afin de déceler les possibilités d'optimisation.
- Les outils de gouvernance cloud doivent limiter les options de taille des ressources à une liste approuvée de configurations. Les outils doivent garantir que toutes les ressources peuvent être détectées et suivies par la solution de supervision des coûts.
- Lors de la planification du déploiement, toutes les ressources cloud requises associées à l’hébergement de charges de travail de production doivent être documentées. Cette documentation permettra d'affiner les budgets et de préparer une automatisation supplémentaire pour éviter l'utilisation d'options plus coûteuses. Au cours de ce processus, il convient d'envisager l'adoption de différents outils de remise proposés par le fournisseur de cloud, tels que des instances réservées ou des réductions sur le coût des licences.
- Tous les propriétaires d’applications sont tenus de suivre une formation sur les pratiques d’optimisation des charges de travail afin de mieux contrôler les coûts liés au cloud.

## <a name="incremental-improvement-of-the-best-practices"></a>Amélioration incrémentielle des bonnes pratiques

Cette section de l’article va modifier la conception du MVP de gouvernance, afin d’inclure de nouvelles stratégies Azure ainsi qu’une implémentation d’Azure Cost Management. Ensemble, ces deux modifications de la conception permettront de répondre aux nouvelles instructions de la stratégie d’entreprise.

1. Implémentez Azure Cost Management.
    1. Établissez la bonne étendue d'accès pour l'aligner sur le modèle d'abonnement et la discipline de cohérence des ressources. Un alignement sur le MVP de gouvernance défini dans les articles précédents nécessitera un accès à l’**étendue Compte d’inscription** pour l’équipe de gouvernance cloud qui exécutera le reporting de haut niveau. D'autres équipes extérieures à la gouvernance pourront avoir besoin d'un accès à l'**étendue Groupe de ressources**.
    1. Établissez un budget dans Azure Cost Management.
    1. Consultez les recommandations initiales et agissez en fonction. Prévoyez un processus récurrent pour le reporting.
    1. Configurez et exécutez la fonctionnalité de génération de rapports initiaux et récurrents d’Azure Cost Management.
2. Mettre à jour Azure Policy
    1. Vérifiez les valeurs de balisage, de groupe de gestion, d'abonnement et de groupe de ressources pour identifier tout écart.
    1. Définissez des options de taille pour les références SKU, afin de limiter les déploiements aux références SKU répertoriées dans la documentation de planification du déploiement.

## <a name="conclusion"></a>Conclusion

L’ajout de ces processus et modifications au MVP de gouvernance permet de traiter de nombreux risques associés à la gouvernance des coûts. Ensemble, ils fournissent la visibilité, la responsabilisation et l’optimisation nécessaires pour contrôler les coûts.

## <a name="next-steps"></a>Étapes suivantes

À mesure que l’adoption du cloud se poursuit et offre davantage de valeur aux activités métier, les risques et les besoins en matière de gouvernance du cloud changent également. Pour l’entreprise fictive de ce guide, l’étape suivante consiste à utiliser cet investissement en gouvernance pour gérer plusieurs clouds.

> [!div class="nextstepaction"]
> [Évolution multicloud](./multicloud-improvement.md)
