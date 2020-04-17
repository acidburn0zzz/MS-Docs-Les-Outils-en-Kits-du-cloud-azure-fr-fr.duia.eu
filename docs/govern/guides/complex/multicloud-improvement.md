---
title: 'Gouvernance pour les entreprises complexes : Amélioration multicloud'
description: Utilisez Cloud Adoption Framework pour Azure afin d’en savoir plus sur l’utilisation de plusieurs clouds et sur la façon d’intégrer des organisations multiclouds pour les entreprises complexes.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 7fa026a06f2f42fda09783a29554e2a6c4797fcd
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80434416"
---
<!-- cSpell:ignore MPLS -->

# <a name="governance-guide-for-complex-enterprises-multicloud-improvement"></a>Guide de gouvernance pour les entreprises complexes : Amélioration multicloud

## <a name="advancing-the-narrative"></a>Développement du scénario

Microsoft est conscient du fait que les clients peuvent adopter plusieurs clouds pour des raisons bien spécifiques. C’est également le cas de l’entreprise fictive dont nous allons parler dans ce guide. Parallèlement au parcours d’adoption d’Azure, la réussite de l’entreprise l’a amenée à acquérir une autre entreprise, petite mais complémentaire. Cette entreprise exécute toutes ses opérations informatiques sur un fournisseur de cloud différent.

Cet article décrit les changements observés suite à l’intégration de la nouvelle organisation. Pour ce scénario, nous partons du principe que cette entreprise a atteint toutes les itérations de gouvernance décrites dans ce guide de gouvernance.

### <a name="changes-in-the-current-state"></a>Modifications apportées à l’état actuel

Dans la phase précédente de ce scénario, l’entreprise avait commencé à implémenter des contrôles de coûts et des fonctionnalités de surveillance des coûts dès lors que les dépenses cloud commençaient à faire partie des frais d’exploitation courants de l’entreprise.

Depuis, certains changements ont eu lieu et ceux-ci vont avoir un impact sur la gouvernance :

- L’identité est contrôlée par une instance locale d’Active Directory. L’identité hybride est facilitée grâce à la réplication vers Azure Active Directory.
- Les opérations informatiques ou opérations cloud sont principalement gérées par Azure Monitor et les autres fonctionnalités d’automatisation associées.
- La continuité d’activité et reprise d’activité (BCDR) sont contrôlées par des instances Azure Vault.
- Azure Security Center est utilisé pour superviser les attaques et les violations de sécurité.
- Azure Security Center et Azure Monitor sont tous les deux utilisés pour superviser la gouvernance du cloud.
- Azure Blueprints, Azure Policy et des groupes d’administration sont utilisés pour automatiser la conformité à la stratégie.

### <a name="incrementally-improve-the-future-state"></a>Améliorer progressivement l’état futur

L’objectif est d’intégrer l’entreprise ayant fait l’objet de l’acquisition aux opérations existantes, dans la mesure du possible.

## <a name="changes-in-tangible-risks"></a>Modifications apportées aux risques tangibles

**Coût d’acquisition de l’entreprise :** d’après les estimations, l’acquisition de la nouvelle entreprise est rentabilisée dans cinq ans environ. En raison de la durée de rentabilisation relativement longue, le conseil d’administration souhaite contrôler autant que possible les coûts d’acquisition. Il existe un risque de conflit entre le contrôle des coûts et l’intégration technique.

Ce risque métier peut s’associer à quelques risques techniques :

- La migration cloud risque de générer des coûts d’acquisition supplémentaires.
- En outre, le nouvel environnement risque de ne pas être correctement gouverné ou de provoquer des violations de stratégie.

## <a name="incremental-improvement-of-the-policy-statements"></a>Amélioration incrémentielle des instructions de stratégie

Les modifications suivantes apportées à la stratégie contribueront à traiter les nouveaux risques et à guider l’implémentation.

- Toutes les ressources dans un cloud secondaire doivent être surveillées à l’aide des outils existants de surveillance de la sécurité et de gestion opérationnelle.
- Toutes les unités d’organisation doivent être intégrées dans le fournisseur d’identité existant.
- Le fournisseur d’identité principal doit régir l’authentification des ressources dans le cloud secondaire.

## <a name="incremental-improvement-of-the-best-practices"></a>Amélioration incrémentielle des bonnes pratiques

Cette section de l’article améliore la conception du MVP de gouvernance, afin d’inclure de nouvelles stratégies Azure ainsi qu’une implémentation d’Azure Cost Management. Ensemble, ces deux modifications de la conception permettront de répondre aux nouvelles instructions de la stratégie d’entreprise.

1. Connectez les réseaux. Cette tâche est exécutée par les équipes responsables de la sécurité informatique et de la mise en réseau, et prise en charge par la gouvernance.
    1. L’ajout d’une connexion depuis un fournisseur MPLS ou un fournisseur de ligne allouée au nouveau cloud intégrera les réseaux. L’ajout de configurations de pare-feu et de tables de routage contrôlera l’accès et le trafic entre les environnements.
2. Consolidez les fournisseurs d’identité. En fonction des charges de travail hébergées dans le cloud secondaire, diverses options sont proposées pour consolider le fournisseur d’identité. Voici quelques exemples :
    1. Pour les applications qui utilisent l’authentification OAuth2, les utilisateurs Active Directory dans le cloud secondaire peuvent simplement être répliqués vers le locataire Azure AD existant.
    2. De l’autre côté, la fédération entre les deux fournisseurs d’identité locaux permettrait aux utilisateurs des nouveaux domaines Active Directory d’être répliqués sur Azure.
3. Ajoutez des ressources à Azure Site Recovery.
    1. Dès le départ, Azure Site Recovery a été conçu en tant qu’outil hybride et multicloud.
    2. Les machines virtuelles dans le cloud secondaire peuvent être protégées par les mêmes processus Azure Site Recovery utilisés pour protéger les ressources locales.
4. Ajoutez des ressources à Azure Cost Management.
    1. Dès le départ, Azure Cost Management a été conçu en tant qu’outil multicloud.
    2. Les machines virtuelles dans le cloud secondaire peuvent être compatibles avec Azure Cost Management pour certains fournisseurs cloud. Des frais supplémentaires peuvent s’appliquer.
5. Ajoutez des ressources à Azure Monitor.
    1. Dès le départ, Azure Monitor a été conçu en tant qu’outil cloud hybride.
    2. Les machines virtuelles dans le cloud secondaire peuvent être compatibles avec les agents Azure Monitor, ce qui leur permet d’être incluses dans Azure Monitor pour la surveillance opérationnelle.
6. Outils de mise en œuvre de la gouvernance.
    1. La mise en œuvre de la gouvernance est spécifique au cloud.
    2. À l’inverse, les stratégies d’entreprise établies dans le guide de gouvernance ne le sont pas. Bien que l’implémentation puisse varier d’un cloud à l’autre, les instructions de stratégie peuvent être appliquées au fournisseur secondaire.

L’adoption multicloud doit se limiter au périmètre nécessaire, défini selon les besoins techniques ou des exigences métier spécifiques. Plus elle s’étend, plus la complexité et les risques de sécurité s’alourdissent.

## <a name="next-steps"></a>Étapes suivantes

Dans de nombreuses grandes entreprises, les Cinq disciplines de la gouvernance cloud peuvent représenter des freins à l’adoption. L’article suivant présente une réflexion supplémentaire quant à la façon de transformer la gouvernance en sport collectif, afin de garantir la réussite à long terme dans le cloud.

> [!div class="nextstepaction"]
> [Couches de gouvernance multiples](./multiple-layers-of-governance.md)
