---
title: Déclarations de stratégie de cohérence des ressources
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Déclarations de stratégie de cohérence des ressources
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 654ec56f2196af4d16b3e19a47ae117b9936b38f
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031118"
---
# <a name="resource-consistency-sample-policy-statements"></a>Déclarations de stratégie de cohérence des ressources

Les déclarations de stratégie cloud individuelles sont des recommandations destinées à traiter des risques spécifiques identifiés lors de votre processus d'évaluation des risques. Ces instructions doivent fournir un bref récapitulatif des risques, ainsi que des plans établis pour les gérer. Chaque définition d’instruction doit inclure les informations suivantes :

- **Risque technique :** un récapitulatif du risque que cette stratégie gérera.
- **Instruction de stratégie :** Une explication succincte claire des exigences de la stratégie.
- **Options de conception :** Recommandations exploitables, spécifications ou autres conseils que des équipes informatiques et des développeurs peuvent utiliser lors de l’implémentation de la stratégie.

Les exemples d’instructions de stratégie suivants traitent des risques commerciaux courants liés à la cohérence des ressources. Ces instructions sont des exemples que vous pouvez référencer lorsque vous rédigez des instructions de stratégie pour répondre aux besoins de votre organisation. Ces exemples ne sont pas destinés à être normatifs, et il existe potentiellement plusieurs options de stratégie pour gérer chaque risque identifié. Travaillez en étroite collaboration avec les équipes métier et informatiques pour identifier les meilleures stratégies pour votre ensemble de risques unique.

## <a name="tagging"></a>Marquage

**Risque technique :** Sans marquage approprié des métadonnées associées aux ressources déployées, les opérations informatiques ne peuvent pas hiérarchiser la prise en charge ou l’optimisation des ressources selon le contrat SLA requis, l'importance pour les opérations de l’entreprise ou les coûts d'exploitation. Cela peut entraîner une mauvaise allocation des ressources informatiques, ainsi que de possibles retards en termes de résolution des incidents.

**Instruction de stratégie :** les stratégies suivantes seront implémentées :

- Les ressources déployées doivent être étiquetées avec les valeurs suivantes :
  - Coût
  - Importance
  - Contrat SLA
  - Environnement
- Les outils de gouvernance doivent valider le marquage associé aux coûts, à la criticité, aux SLA, aux applications et aux environnements. Toutes les valeurs doivent être alignées avec les valeurs prédéfinies gérées par l’équipe de gouvernance.

**Options de conception potentielles** : Dans Azure, les [balises de métadonnées de nom-valeur standard](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) sont prises en charge pour la plupart des types de ressources. [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) est utilisé pour appliquer des balises spécifiques lors de la création de ressources.

## <a name="ungoverned-subscriptions"></a>Abonnements non régis

**Risque technique :** La création arbitraire d'abonnements et de groupes d’administration peut générer des sections isolées au sein de votre parc cloud, sections auxquelles les stratégies de gouvernance ne seront pas correctement appliquées.

**Instruction de stratégie :** La création de nouveaux abonnements ou de groupes d’administration pour les applications critiques ou les données protégées nécessite un examen par l’équipe de gouvernance du cloud. Les changements approuvés seront intégrés dans une affectation de blueprint appropriée.

**Options de conception potentielles** : Réservez l’accès administratif aux [groupes d’administration Azure](https://docs.microsoft.com/azure/governance/management-groups) de votre organisation aux seuls membres approuvés de l'équipe de gouvernance en charge de la création de l’abonnement et du processus de contrôle d’accès.

## <a name="manage-updates-to-virtual-machines"></a>Gérer les mises à jour des machines virtuelles

**Risque technique :** Les machines virtuelles (VM) ne disposant pas des dernières mises à jour et derniers correctifs logiciels peuvent faire l'objet de problèmes de sécurité ou de performances susceptibles d'entraîner des interruptions de service.

**Instruction de stratégie :** Les outils de gouvernance doivent veiller à ce que les mises à jour automatiques soient activées sur toutes les machines virtuelles déployées. Les violations doivent être examinées avec les équipes de gestion opérationnelle et corrigées conformément aux stratégies d’exploitation. Les ressources qui ne sont pas mises à jour automatiquement doivent être incluses dans les processus détenus par l’équipe responsable des opérations informatiques.

**Options de conception potentielles** : Les machines virtuelles hébergées sur Azure peuvent faire l'objet d'une gestion cohérente des mises à jour à l'aide de la [solution Update Management dans Azure Automation](https://docs.microsoft.com/azure/automation/automation-update-management).

## <a name="deployment-compliance"></a>Conformité du déploiement

**Risque technique :** Des scripts de déploiement et outils d’automatisation non vérifiés par l’équipe de gouvernance cloud peuvent donner lieu à des déploiements de ressources contraires à la stratégie.

**Instruction de stratégie :** les stratégies suivantes seront implémentées :

- Les outils de déploiement doivent être approuvés par l’équipe de gouvernance cloud pour s’assurer de la gouvernance en continu des ressources déployées.
- Les scripts de déploiement doivent être conservés dans un référentiel central, accessible par l’équipe de gouvernance cloud pour effectuer des audits et révisions périodiques.

**Options de conception potentielles** : Une utilisation cohérente d'[Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints) pour gérer les déploiements automatisés permet des déploiements cohérents des ressources Azure, respectant les normes et stratégies de gouvernance de votre organisation.

## <a name="monitoring"></a>Surveillance

**Risque technique :** Incorrectement implémentée ou instrumentée, la surveillance peut empêcher la détection de problèmes d’intégrité liés aux charges de travail ou autres violations des stratégies.

**Instruction de stratégie :** les stratégies suivantes seront implémentées :

- Les outils de gouvernance doivent vérifier que toutes les ressources associés aux applications critiques ou aux données protégées sont incluses dans la surveillance pour l’optimisation et l’épuisement des ressources.
- Les outils de gouvernance doivent valider que le niveau approprié de données de journalisation est collecté pour toutes les applications critiques ou données protégées.

**Options de conception potentielles** : [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) est le service de surveillance par défaut dans Azure, et une surveillance cohérente peut être appliquée via [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints) lors du déploiement de ressources.

## <a name="disaster-recovery"></a>Récupération d'urgence

**Risque technique :** La défaillance, la suppression ou la corruption de ressources peut entraîner une interruption des applications ou services stratégiques, ainsi qu'une perte de données sensibles.

**Instruction de stratégie :** Toutes les applications stratégiques et données protégées doivent s'accompagner de solutions de sauvegarde et de récupération mises en œuvre pour limiter l'impact des pannes et défaillances système sur l'entreprise.

**Options de conception potentielles** : Le service [Azure Site Recovery] propose des fonctionnalités de sauvegarde, de récupération et de réplication conçues pour limiter la durée des pannes dans des scénarios BCDR (continuité d'activité et reprise d'activité).

## <a name="next-steps"></a>Étapes suivantes

Utilisez les exemples mentionnés dans cet article comme point de départ pour développer des stratégies qui répondent à des risques métier spécifiques, dans la continuité de vos plans d'adoption du cloud.

Pour commencer à développer vos déclarations de stratégie personnalisées liées à la cohérence des ressources, téléchargez le [modèle Cohérence des ressources](./template.md).

Pour accélérer l’adoption de cette discipline, choisissez le [guide de gouvernance exploitable](../guides/index.md) correspondant le mieux à votre environnement. Modifiez ensuite la conception pour intégrer vos décisions spécifiques en matière de stratégie d’entreprise.

Sur la base des risques et de la tolérance, établir un processus de gouvernance et de communication en lien avec l’adhésion à la stratégie Cohérence des ressources.

> [!div class="nextstepaction"]
> [Établir des processus de conformité à la stratégie](./compliance-processes.md)