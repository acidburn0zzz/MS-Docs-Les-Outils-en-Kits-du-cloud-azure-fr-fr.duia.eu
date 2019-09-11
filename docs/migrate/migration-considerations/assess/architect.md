---
title: Architecture de charges de travail avant la migration
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Architecture de charges de travail avant la migration
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d62b2f5957dc5cee19f462e3c7d74c85672eadfe
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70834783"
---
# <a name="architect-workloads-prior-to-migration"></a>Architecture de charges de travail avant la migration

Cet article développe le processus d’évaluation en examinant les activités associées à la définition de l’architecture d’une charge de travail dans une itération donnée. Comme nous l’avons vu dans l’article sur la [rationalisation incrémentielle](../../../digital-estate/rationalize.md), certaines hypothèses architecturales sont faites au cours de toute transformation d’entreprise nécessitant une migration. Cet article clarifie ces hypothèses, partage quelques obstacles qui peuvent être évités et identifie les opportunités d’accélérer la valeur métier en mettant à l’épreuve ces hypothèses. Ce modèle incrémentiel pour l’architecture permet aux équipes de se déplacer plus rapidement et d’obtenir des résultats métier plus tôt.

## <a name="architecture-assumptions-prior-to-migration"></a>Hypothèses d’architecture avant la migration

Les hypothèses suivantes sont typiques pour tout effort de migration :

- **IaaS.** Il est généralement supposé que la migration des charges de travail implique principalement le déplacement des machines virtuelles d’un centre de donnes physiques vers un centre de donnes cloud via une migration IaaS, nécessitant un minimum de redéveloppement ou de reconfiguration. C’est ce qu’on appelle une migration de type « Lift and Shift ». (Les exceptions suivent.)
- **Cohérence de l’architecture.** Les modifications apportées à l’architecture principale pendant une migration augmentent considérablement la complexité. Le débogage d’un système modifié sur une nouvelle plateforme introduit de nombreuses variables qui peuvent être difficiles à isoler. Pour cette raison, les charges de travail ne doivent subir que des modifications mineures pendant la migration, et les modifications doivent être minutieusement testées.
- **Test de mise hors service.** Les migrations et l’hébergement des ressources sont synonymes de dépenses opérationnelles et potentiellement de capital. On suppose que toutes les charges de travail en cours de migration ont été examinées pour valider l’utilisation continue. Le choix de mettre hors service des ressources inutilisées entraîne des économies immédiates.
- **Redimensionnement des ressources.** On suppose que peu de ressources locales utilisent entièrement les ressources allouées. Avant la migration, on suppose que les ressources seront redimensionnées pour s’adapter au mieux aux besoins d’utilisation réels.
- **Exigences de continuité et de reprise d’activité.** On suppose qu’un contrat SLA convenu pour la charge de travail a été négocié avec l’entreprise avant la planification des publications. Ces exigences sont susceptibles de produire des changements d’architecture mineurs.
- **Temps d’arrêt de la migration.** De même, les temps d’arrêt pour promouvoir la charge de travail en production peuvent avoir un effet néfaste sur l’entreprise. Parfois, les solutions qui doivent être migrées avec un temps d’arrêt minimal nécessitent des changements d’architecture. On suppose qu’une compréhension générale des exigences de temps d’arrêt a été établie avant la planification des publications.

## <a name="roadblocks-that-can-be-avoided"></a>Obstacles qui peuvent être évités

Les hypothèses triées pouvant créer des obstacles susceptibles de ralentir la progression ou d’entraîner des difficultés plus tard. Voici quelques-uns des obstacles à surveiller avant la publication :

- **Paiement de la dette technique.** Certaines charges de travail vieillissantes ont un montant élevé de dette technique. Cela peut entraîner des défis à long terme en augmentant les coûts d’hébergement avec n’importe quel fournisseur cloud. Lorsque la dette technique augmente de façon non naturelle les coûts d’hébergement, d’autres architectures doivent être évaluées.
- **Modèles de trafic utilisateur.** Les solutions existantes peuvent dépendre de modèles de routage réseau existants. Ces modèles peuvent ralentir considérablement les performances. En outre, l’introduction de nouvelles solutions de réseau étendu (WAN) hybrides peut prendre des semaines, voire des mois. Préparez-vous au début du processus d’architecture en tenant compte des modèles de trafic et des modifications apportées aux services d’infrastructure de base.

## <a name="accelerating-business-value"></a>Accélération de la valeur métier

Certains scénarios peuvent nécessiter une architecture différente de la stratégie de réhébergement IaaS supposée. Voici quelques exemples :

- Alternatives PaaS. Les déploiements PaaS peuvent réduire les coûts d’hébergement, et ils peuvent également réduire le temps nécessaire à la migration de certaines charges de travail. Pour obtenir la liste des approches qui peuvent tirer parti d’une conversion PaaS, consultez l'article sur [l’évaluation des ressources](./evaluate.md).
- Déploiements scriptés/DevOps. Si une charge de travail possède un déploiement DevOps existant ou d’autres formes de déploiement par script, le coût de la modification de ces scripts peut être inférieur au coût de la migration de la ressource.
- Efforts de correction. Les efforts de correction requis pour préparer une charge de travail pour la migration peuvent être importants. Dans certains cas, il est plus judicieux de moderniser la solution que de corriger les problèmes de compatibilité sous-jacents.

Dans chacun de ces scénarios, une autre architecture peut être la meilleure solution possible.

## <a name="next-steps"></a>Étapes suivantes

Une fois la nouvelle architecture définie, [des estimations de coût précises peuvent être calculées](./estimate.md).

> [!div class="nextstepaction"]
> [Estimer les coûts du cloud](./estimate.md)
