---
title: Guides de décision concernant le nommage et l’étiquetage des ressources
description: Découvrez les approches et options de nommage et d’étiquetage lors de l’organisation de ressources cloud dans le cadre du Cloud Adoption Framework pour Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 638f8dad1d7f284104765b28fe53561d98e02b56
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83399817"
---
<!-- cSpell:ignore catalogsearch northamerica jsmith contactalias catsearchowners businessprocess businessimpact revenueimpact -->

# <a name="resource-naming-and-tagging-decision-guide"></a>Guides de décision concernant le nommage et l’étiquetage des ressources

L’organisation des ressources cloud est une tâche cruciale pour le service informatique, sauf si tous vos déploiements sont simples. Organisez vos ressources en respectant les conventions de nommage et d’étiquetage, pour les raisons suivantes :

- **Gestion des ressources** : Votre équipe informatique devra localiser rapidement les ressources associées à des charges de travail, environnements ou groupes de propriété spécifiques ou à d’autres informations importantes. L’organisation des ressources est essentielle à l’affectation des rôles organisationnels et aux autorisations d’accès pour la gestion des ressources.
- **Gestion et optimisation des coûts :** Pour informer les groupes métier de leur consommation de ressources cloud, le service informatique doit d’abord connaître les ressources et les charges de travail utilisées par chaque équipe. Les rubriques suivantes sont prises en charge par des étiquettes liées aux coûts :

  - [Modèles de comptabilité cloud](../../strategy/cloud-accounting.md)
  - [Calculs du retour sur investissement](../../strategy/financial-models.md#return-on-investment)
  - [Suivi des coûts](../../ready/azure-best-practices/track-costs.md)
  - [Budgets](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json)
  - [Alertes](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-alerts-monitor-usage-spending?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json)
  - [Suivi des dépenses récurrentes et création de rapports](../../govern/cost-management/compliance-processes.md)
  - [Optimisations après implémentation](../../govern/cost-management/discipline-improvement.md#operate-and-post-implementation)
  - [Tactiques d’optimisation des coûts](../../govern/guides/complex/cost-management-improvement.md#incremental-improvement-of-the-best-practices)
- **Gestion des opérations :** La visibilité pour l’équipe de gestion des opérations concernant les engagements métier et les contrats SLA est un aspect important des opérations en cours. Pour assurer la bonne gestion des opérations, il est nécessaire d’étiqueter la [criticité](../../manage/considerations/criticality.md).
- **Sécurité :** La classification des données et de l’impact sur la sécurité est un point de données vital pour l’équipe quand des violations ou d’autres problèmes de sécurité émergent. Pour opérer de manière sécurisée, vous devez [classifier les données](../../govern/policy-compliance/data-classification.md) avec des étiquettes.
- **Gouvernance et conformité réglementaire :** Le fait de maintenir la cohérence entre les ressources permet d’identifier tout écart par rapport aux stratégies convenues. Cet [article de fondation de la gouvernance](../../govern/guides/complex/prescriptive-guidance.md#resource-tagging) montre comment l’un des modèles ci-dessous peut vous être utile lors du déploiement de pratiques de gouvernance. Des modèles similaires sont disponibles pour évaluer la conformité réglementaire à l’aide d’étiquettes.
- **Automatisation :** En plus de faciliter la gestion des ressources pour le personnel informatique, un bon modèle organisationnel vous permet de tirer parti de l’automatisation dans le cadre de la création de ressources, de la supervision des opérations et de la création de processus DevOps.
- **Optimisation des charges de travail :** L’étiquetage peut vous aider à identifier des modèles et à résoudre des problèmes d’ordre général. Il peut également vous aider à identifier les ressources nécessaires pour prendre en charge une seule charge de travail. L’étiquetage de toutes les ressources associées à chaque charge de travail vous permet d’analyser plus en profondeur vos charges de travail stratégiques et de prendre des décisions architecturales éclairées.

## <a name="tagging-decision-guide"></a>Guide de décision concernant l’étiquetage

![Options d’étiquetage, de la moins complexe à la plus complexe, dans l’ordre des liens ci-dessous](../../_images/decision-guides/decision-guide-resource-tagging.png)

Passer à : [Conventions de nommage des bases de référence](#baseline-naming-conventions) | [Modèles d’étiquetage des ressources](#resource-tagging-patterns) | [En savoir plus](#learn-more)

Votre approche d’étiquetage peut être simple ou complexe, et mettre l’accent aussi bien sur l’aide apportée aux équipes informatique chargées de gérer les charges de travail cloud, que sur l’intégration des informations relatives à tous les aspects de l’entreprise.

Un étiquetage aligné sur le service informatique (comme l’étiquetage basé sur la charge de travail, l’application, la fonction ou l’environnement) permet de simplifier la supervision des ressources et de faciliter les décisions de gestion prises en fonction des besoins opérationnels.

L’étiquetage des schémas qui sont alignés sur l’entreprise (comme la comptabilité, la propriété d’entreprise ou la criticité) peut nécessiter plus de temps, notamment pour créer des standards d’étiquetage qui reflètent les intérêts métier, et pour conserver ces standards. Toutefois, le résultat de ce processus est un système d’étiquetage qui permet de mieux prendre en compte les coûts ainsi que la valeur des ressources informatiques de l’entreprise. Le fait d’associer la valeur métier d’une ressource à son coût d’exploitation est l’une des premières étapes permettant de modifier la façon dont votre organisation perçoit l’informatique en tant que centre de coûts.

## <a name="baseline-naming-conventions"></a>Conventions de nommage des bases de référence

Une convention de nommage standardisée constitue le point de départ de l’organisation de vos ressources hébergées dans le cloud. Un système de nommage correctement structuré vous permet d’identifier rapidement les ressources à des fins de gestion et de comptabilité. Si vous disposez déjà de conventions de nommage informatiques dans d’autres services de votre organisation, déterminez si les conventions de nommage cloud doivent s’aligner sur ces conventions ou si vous devez établir des standards distincts pour le cloud.

> [!NOTE]
> Les [règles et restrictions en matière de nommage](https://docs.microsoft.com/azure/azure-resource-manager/management/resource-name-rules) varient en fonction des ressources Azure. Vos conventions de nommage doivent respecter ces règles.

## <a name="resource-tagging-patterns"></a>Modèles d’étiquetage des ressources

Pour obtenir une organisation plus sophistiquée que celle fournie par une convention de nommage cohérente seule, les plateformes cloud permettent d’étiqueter les ressources.

Les étiquettes sont des éléments de métadonnées attachés aux ressources. Les étiquettes sont constituées de paires de chaînes clé/valeur. Il vous revient de choisir les valeurs à inclure dans ces paires. Toutefois, l’application d’un ensemble cohérent d’étiquettes globales, faisant partie d’une stratégie de nommage et d’étiquetage complète, constitue un élément essentiel des stratégies globales de gouvernance.

Dans le cadre de votre processus de planification, aidez-vous des questions suivantes pour déterminer le type d’informations que doivent prendre en charge vos étiquettes de ressource :

- Vos stratégies de nommage et d’étiquetage doivent-elles être intégrées aux stratégies de nommage et aux stratégies organisationnelles qui existent dans votre organisation ?
- Allez-vous implémenter un système de comptabilité de type chargeback/showback ? Devez-vous associer des ressources à des informations de comptabilité pour des services, des groupes professionnels et des équipes en utilisant plus de détails que ne le permet une simple répartition au niveau de l’abonnement ?
- L’étiquetage doit-il présenter des informations telles que les exigences de conformité réglementaire pour une ressource ? Qu’en est-il des détails opérationnels tels que les exigences de disponibilité, la planification des mises à jour correctives et les exigences de sécurité ?
- D’après la stratégie informatique centralisée, de quelles étiquettes aurez-vous besoin pour toutes les ressources ? Quelles étiquettes sont facultatives ? Chaque équipe est-elle autorisée à implémenter ses propres schémas d’étiquetage personnalisés ?

Les modèles d’étiquetage courants listés ci-dessous montrent comment vous pouvez utiliser l’étiquetage pour organiser les ressources cloud. Ces modèles ne sont pas destinés à être exclusifs et peuvent être utilisés en parallèle, fournissant ainsi plusieurs façons d’organiser les ressources en fonction des besoins de votre entreprise.

<!-- markdownlint-disable MD033 -->
<!-- docsTest:disable -->

| Type d’étiquette | Exemples | Description |
|-----|-----|-----|
| Fonctionnelle | app&nbsp;=&nbsp;catalogsearch1 <br> tier&nbsp;=&nbsp;web <br> webserver&nbsp;=&nbsp;apache <br> env&nbsp;=&nbsp;prod <br> env&nbsp;=&nbsp;staging <br> env&nbsp;=&nbsp;dev | Permet d’attribuer une catégorie aux ressources par rapport à leur rôle au sein d’une charge de travail, à l’environnement dans lequel elles ont été déployées, ou par rapport à d’autres fonctionnalités ou détails opérationnels. |
| classification ; | confidentiality&nbsp;=&nbsp;private <br> SLA&nbsp;=&nbsp;24hours | Classifie une ressource selon son utilisation et les stratégies qui y sont appliquées. |
| Comptabilité | department&nbsp;=&nbsp;finance <br> program&nbsp;=&nbsp;business-initiative <br> region&nbsp;=&nbsp;northamerica | Permet à une ressource d’être associée à des groupes d’une organisation à des fins de facturation. |
| Partenariat | owner&nbsp;=&nbsp;jsmith <br> contactalias&nbsp;=&nbsp;catsearchowners <br> stakeholders&nbsp;=&nbsp;user1;user2;user3 | Fournit des informations sur la façon dont les utilisateurs (en dehors de l’équipe informatique) sont liés à la ressource ou affectés par celle-ci. |
| Objectif | businessprocess&nbsp;=&nbsp;support <br> businessimpact&nbsp;=&nbsp;moderate <br> revenueimpact&nbsp;=&nbsp;high | Aligne les ressources sur les fonctions métier pour mieux prendre en charge les décisions relatives aux investissements. |

<!-- docsTest:enable -->
<!-- markdownlint-enable MD033 -->

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations sur le nommage et l’étiquetage dans Azure, consultez :

- [Conventions d’affectation de noms pour les ressources Azure](../../ready/azure-best-practices/naming-and-tagging.md). Consultez ce guide afin de connaître les conventions de nommage recommandées pour les ressources Azure.
- [Utiliser des étiquettes pour organiser vos ressources Azure et votre hiérarchie de gestion](https://docs.microsoft.com/azure/azure-resource-manager/management/tag-resources). Dans Azure, vous pouvez appliquer des étiquettes au niveau des groupes de ressources et au niveau des ressources, ce qui vous permet de choisir le niveau de granularité des rapports comptables en fonction des étiquettes appliquées.

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, l’étiquetage des ressources ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
