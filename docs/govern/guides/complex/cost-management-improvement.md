---
title: 'Gouvernance pour les entreprises complexes : Améliorer la discipline de gestion des coûts'
description: Utilisez le Framework d’adoption du cloud pour Azure pour savoir comment ajouter des contrôles de coût à un produit minimum viable (MVP, minimum viable product) de gouvernance.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: b44f153c9e14f1425aa3bb1374c60243c9a3c326
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77709037"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-cost-management-discipline"></a>Guide de gouvernance pour les entreprises complexes : Améliorer la discipline Gestion des coûts

Cet article fait progresser le scénario en ajoutant des contrôles de coûts au produit minimum viable (MVP) de gouvernance.

## <a name="advancing-the-narrative"></a>Développement du scénario

L’adoption a dépassé l’indicateur de tolérance défini dans le produit minimum viable pour la gouvernance. L’augmentation des dépenses justifie désormais un investissement en temps de la part de l’équipe de gouvernance cloud pour superviser et contrôler les modèles de dépenses.

Véritable moteur de l’innovation, le département informatique n’est plus uniquement considéré comme un centre de coûts. L’organisation informatique apportant de plus en plus de valeur, le directeur des services d’information et le directeur financier décident qu’il est temps de faire évoluer le rôle du département informatique dans l’entreprise. Parmi les modifications à mettre en œuvre, le directeur financier souhaite tester une méthode de facturation directe des opérations cloud pour la succursale canadienne de l’une des unités commerciales. L’un des deux centres de données mis hors service hébergeait exclusivement des ressources pour les opérations canadiennes de cette unité commerciale. Dans ce modèle, la succursale canadienne de l’unité commerciale sera facturée directement pour les frais d’exploitation associés aux ressources hébergées. Ce modèle permet aux équipes informatiques de se concentrer sur la création de valeur pour l’entreprise plutôt que sur la gestion des dépenses des autres. Toutefois, avant d’entreprendre cette transition, des outils de gestion des coûts doivent être en place.

### <a name="changes-in-the-current-state"></a>Modifications apportées à l’état actuel

Dans la phase précédente de ce scénario, l’équipe informatique déplaçait les charges de travail de production avec des données protégées dans Azure.

Depuis, certains changements ont eu lieu et ceux-ci vont avoir un impact sur la gouvernance :

- 5 000 ressources ont été supprimées des deux centres de données marqués d’un indicateur de mise hors service. Les équipes responsables de la sécurité informatique et des achats procèdent maintenant au déprovisionnement des ressources physiques restantes.
- Les équipes de développement d’applications ont implémenté des pipelines CI/CD pour déployer quelques applications cloud natives, ce qui impacte grandement l’expérience des clients.
- L’équipe Business Intelligence a créé des processus d’agrégation, de collecte, d’insights et de prédiction qui génèrent des avantages tangibles pour les opérations métier. Ces prédictions encouragent désormais la création de nouveaux produits et services.

### <a name="incrementally-improve-the-future-state"></a>Améliorer progressivement l’état futur

Des fonctionnalités de contrôle des coûts et de création de rapports doivent être ajoutées à la solution cloud. Les rapports devraient lier les frais d’exploitation directs aux fonctions qui absorbent les coûts du cloud. Générer des rapports supplémentaires peut permettre à l’équipe informatique de surveiller les dépenses et de proposer des conseils techniques sur la gestion des coûts. Pour la succursale canadienne, le département sera facturé directement.

## <a name="changes-in-risk"></a>Changements au niveau des risques

**Contrôle du budget :** les fonctionnalités en libre-service risquent de générer des coûts excessifs et inattendus sur la nouvelle plateforme. Des processus de gouvernance permettant de surveiller les coûts et d’atténuer les risques permanents liés à ceux-ci doivent être en place pour garantir un alignement continu avec le budget prévu.

Ce risque métier peut s’associer à quelques risques techniques :

- Les coûts réels risquent de dépasser ceux prévus initialement dans le plan.
- Les conditions métier évoluent. Dans ce cas, il peut arriver qu’une fonction métier utilise plus de services cloud que prévu, ce qui se traduit par des anomalies en termes de dépenses. Ces coûts supplémentaires risquent d’être considérés comme des dépassements plutôt que comme des ajustements du plan. En cas de réussite, l’expérience canadienne doit vous aider à traiter ce risque.
- Les systèmes risquent d’être surapprovisionnés, ce qui entraîne des dépenses excessives.

## <a name="changes-to-the-policy-statements"></a>Modifications apportées aux instructions de stratégie

Les modifications suivantes apportées à la stratégie contribueront à traiter les nouveaux risques et à guider l’implémentation.

- Chaque semaine, l’équipe de gouvernance cloud doit s’assurer que tous les coûts liés au cloud sont conformes au plan. Chaque mois, des rapports sur les écarts entre les coûts du cloud et ceux prévus par le plan doivent être remis aux responsables informatiques et au département financier. Chaque mois, toutes les mises à jour des coûts liés au cloud et prévus par le plan doivent être révisées par les responsables informatiques et le département financier.
- Tous les coûts doivent être affectés à une fonction opérationnelle à des fins de responsabilisation.
- Les ressources du cloud doivent être contrôlées en permanence afin de déceler les possibilités d'optimisation.
- Les outils de gouvernance cloud doivent limiter les options de taille des ressources à une liste approuvée de configurations. Les outils doivent garantir que toutes les ressources peuvent être détectées et suivies par la solution de supervision des coûts.
- Lors de la planification du déploiement, toutes les ressources cloud requises associées à l’hébergement de charges de travail de production doivent être documentées. Cette documentation permettra d’affiner les budgets et de préparer des outils d’automatisation supplémentaires pour éviter l’utilisation d’options plus coûteuses. Au cours de ce processus, il convient d’envisager l’adoption de différents outils de remise proposés par le fournisseur de cloud, tels que des instances réservées ou des réductions sur le coût des licences.
- Tous les propriétaires d’applications sont tenus de suivre une formation sur les pratiques d’optimisation des charges de travail afin de mieux contrôler les coûts liés au cloud.

## <a name="incremental-improvement-of-the-best-practices"></a>Amélioration incrémentielle des bonnes pratiques

Cette section de l’article va améliorer la conception du MVP de gouvernance, afin d’inclure de nouvelles stratégies Azure et une implémentation d’Azure Cost Management. Ensemble, ces deux modifications de la conception permettront de répondre aux nouvelles instructions de la stratégie d’entreprise.

1. Apportez des modifications au portail Microsoft Azure Enterprise Portal pour facturer le déploiement canadien à l’administrateur du département.
2. Implémentez Azure Cost Management.
    1. Définissez le niveau d’étendue d’accès approprié en fonction du modèle d’abonnement et du modèle de regroupement des ressources. En partant d’un alignement sur le MPV de gouvernance défini dans les articles précédents, un accès à **l’étendue Compte d’inscription** est nécessaire pour l’équipe de gouvernance cloud qui exécutera la génération de rapports de haut niveau. D’autres équipes en dehors de la gouvernance, comme l’équipe canadienne responsable des achats, auront besoin d’un accès à **l’étendue Groupe de ressources**.
    2. Établissez un budget dans Azure Cost Management.
    3. Consultez les recommandations initiales et agissez en fonction. Il est recommandé d’avoir un processus récurrent pour prendre en charge le processus de génération de rapports.
    4. Configurez et exécutez la fonctionnalité de génération de rapports initiaux et récurrents d’Azure Cost Management.
3. Mettez à jour Azure Policy.
    1. Auditez les valeurs de marquage, de groupe de gestion, d’abonnement et de groupe de ressources pour identifier tout écart.
    2. Définissez des options de taille pour les références SKU, afin de limiter les déploiements aux références SKU répertoriées dans la documentation de planification du déploiement.

## <a name="conclusion"></a>Conclusion

L’ajout des processus et modifications susmentionnées au MVP de gouvernance permet de traiter de nombreux risques associés à la gouvernance des coûts. Ensemble, ils fournissent la visibilité, la responsabilisation et l’optimisation nécessaires pour contrôler les coûts.

## <a name="next-steps"></a>Étapes suivantes

À mesure que l’adoption du cloud croît et offre davantage de valeur aux activités métier, les risques et les besoins en matière de gouvernance du cloud changent aussi. Pour cette entreprise fictive, l’étape suivante consiste à utiliser cet investissement en termes de gouvernance pour gérer plusieurs clouds.

> [!div class="nextstepaction"]
> [Amélioration multicloud](./multicloud-improvement.md)
