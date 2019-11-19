---
title: 'Guide de gouvernance pour les entreprises standard : Amélioration multicloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guide de gouvernance pour les entreprises standard : Amélioration multicloud'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 10097c550ba160c41add31e27d0813c175f5e26a
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566232"
---
# <a name="standard-enterprise-governance-guide-multicloud-improvement"></a>Guide de gouvernance pour les entreprises standard : Amélioration multicloud

Cet article fait progresser le scénario en ajoutant des contrôles à l’adoption multi-cloud.

## <a name="advancing-the-narrative"></a>Développement du scénario

Microsoft est conscient du fait que les clients peuvent adopter plusieurs clouds pour des raisons bien spécifiques. C’est également le cas du client fictif dont nous allons parler dans ce guide. Parallèlement au parcours d’adoption d’Azure, la réussite de l’entreprise l’a amenée à acquérir une autre entreprise, petite mais complémentaire. Cette entreprise exécute toutes ses opérations informatiques sur un fournisseur de cloud différent.

Cet article décrit les changements observés suite à l’intégration de la nouvelle organisation. Pour ce scénario, nous partons du principe que cette entreprise a atteint toutes les itérations de gouvernance décrites dans ce guide de gouvernance.

### <a name="changes-in-the-current-state"></a>Modifications apportées à l’état actuel

Dans la phase précédente de ce scénario, l’entreprise avait commencé à envoyer activement des applications de production vers le cloud via des pipelines CI/CD.

Depuis, certains changements ont eu lieu et ceux-ci vont avoir un impact sur la gouvernance :

- L’identité est contrôlée par une instance locale d’Active Directory. L’identité hybride est facilitée grâce à la réplication vers Azure Active Directory.
- Les opérations informatiques ou opérations cloud sont principalement gérées par Azure Monitor et les autres automatisations associées.
- La récupération d'urgence et la continuité de l’activité sont contrôlées par des instances Azure Vault.
- Azure Security Center est utilisé pour superviser les attaques et les violations de sécurité.
- Azure Security Center et Azure Monitor sont tous les deux utilisés pour superviser la gouvernance du cloud.
- Azure Blueprints, Azure Policy et des groupes d’administration Azure sont utilisés pour automatiser la conformité à la stratégie.

### <a name="incrementally-improve-the-future-state"></a>Améliorer progressivement l’état futur

L’objectif est d’intégrer l’entreprise ayant fait l’objet de l’acquisition aux opérations existantes, dans la mesure du possible.

## <a name="changes-in-tangible-risks"></a>Modifications apportées aux risques tangibles

**Coût d’acquisition de l’entreprise :** d’après les estimations, l’acquisition de la nouvelle entreprise est rentabilisée dans cinq ans environ. En raison de la durée de rentabilisation relativement longue, le conseil d’administration souhaite contrôler autant que possible les coûts d’acquisition. Il existe un risque de conflit entre le contrôle des coûts et l’intégration technique.

Ce risque métier peut s’associer à quelques risques techniques :

- La migration vers le cloud peut générer des coûts d’acquisition supplémentaires.
- Le nouvel environnement peut ne pas être correctement gouverné, ce qui pourrait engendrer un non-respect de la stratégie.

## <a name="incremental-improvement-of-the-policy-statements"></a>Amélioration incrémentielle des instructions de stratégie

Les modifications suivantes apportées à la stratégie contribueront à traiter les nouveaux risques et à guider l’implémentation :

- Toutes les ressources dans un cloud secondaire doivent être surveillées à l’aide des outils existants de surveillance de la sécurité et de gestion opérationnelle.
- Toutes les unités d’organisation doivent être intégrées dans le fournisseur d’identité existant.
- Le fournisseur d’identité principal doit régir l’authentification des ressources dans le cloud secondaire.

## <a name="incremental-improvement-of-governance-practices"></a>Amélioration incrémentielle des pratiques de gouvernance

Cette section de l’article va modifier la conception du MVP de gouvernance, afin d’inclure de nouvelles stratégies Azure ainsi qu’une implémentation d’Azure Cost Management. Ensemble, ces modifications de la conception permettront de répondre aux nouvelles instructions de la stratégie d’entreprise.

1. Connectez les réseaux. Cette étape est effectuée par les équipes de mise en réseau et de sécurité informatique, en collaboration avec l’équipe de gouvernance cloud. L’ajout d’une connexion d’un fournisseur MPLS/de ligne allouée au nouveau cloud intègrera les réseaux. L’ajout de configurations de pare-feu et de tables de routage contrôlera l’accès et le trafic entre les environnements.
2. Consolidez les fournisseurs d’identité. En fonction des charges de travail hébergées dans le cloud secondaire, diverses options sont proposées pour consolider le fournisseur d’identité. Voici quelques exemples :
    1. Pour les applications qui utilisent l’authentification OAuth2, les utilisateurs Active Directory dans le cloud secondaire peuvent simplement être répliqués sur le locataire Azure AD existant. Grâce à cela, tous les utilisateurs peuvent être authentifiés dans le locataire.
    2. D’un autre côté, la fédération permet aux unités d’organisation de circuler dans Active Directory local, puis dans l’instance Azure AD.
3. Ajoutez des ressources à Azure Site Recovery.
    1. Dès le départ, Azure Site Recovery a été conçu en tant qu’outil hybride ou multicloud.
    2. Les machines virtuelles dans le cloud secondaire peuvent être en mesure d’être protégées par les mêmes processus Azure Site Recovery utilisés pour protéger les ressources locales.
4. Ajoutez des ressources à Azure Cost Management.
    1. Dès le départ, Azure Cost Management a été conçu en tant qu’outil multicloud.
    2. Les machines virtuelles dans le cloud secondaire peuvent être compatibles avec Azure Cost Management pour certains fournisseurs cloud. Des frais supplémentaires peuvent s’appliquer.
5. Ajoutez des ressources à Azure Monitor.
    1. Dès son lancement, Azure Monitor a été conçu en tant qu’outil cloud hybride.
    2. Les machines virtuelles dans le cloud secondaire peuvent être compatibles avec les agents Azure Monitor, ce qui leur permet d’être incluses dans Azure Monitor pour la supervision opérationnelle.
6. Adoptez des outils de mise en œuvre de la gouvernance.
    1. La mise en œuvre de la gouvernance est spécifique au cloud.
    2. À l’inverse, les stratégies d’entreprise établies dans le guide de gouvernance ne le sont pas. Bien que l’implémentation puisse varier d’un cloud à l’autre, les stratégies peuvent être appliquées au fournisseur secondaire.

L’adoption multicloud doit se limiter au périmètre nécessaire, défini selon les besoins techniques ou des exigences métier spécifiques. Plus elle s’étend, plus la complexité et les risques de sécurité s’alourdissent.

## <a name="conclusion"></a>Conclusion

Cette série d’articles décrit le développement incrémental des bonnes pratiques de gouvernance, conformément aux expériences de cette entreprise fictive. En commençant doucement mais avec des bases solides, l’entreprise a pu rapidement évoluer tout en appliquant la bonne quantité de gouvernance au bon moment. Le MVP en lui-même n’a pas protégé le client. En fait, il a créé les bases permettant de gérer les risques et d’ajouter de la protection. À partir de là, des couches de gouvernance ont été appliquées pour traiter les risques tangibles. Le parcours présenté ici n’est pas conforme à 100 % avec les expériences d’un lecteur. Il doit plutôt être considéré comme un modèle pour la gouvernance incrémentielle. Il est conseillé au lecteur d’adapter ces meilleures pratiques à ses propres contraintes et exigences de gouvernance.
