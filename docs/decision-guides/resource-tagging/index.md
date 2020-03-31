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
ms.openlocfilehash: cda5b1ee78dd3cf0a67fa6207835b52522e5405c
ms.sourcegitcommit: afe10f97fc0e0402a881fdfa55dadebd3aca75ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80431429"
---
<!-- cSpell:ignore catalogsearch northamerica jsmith contactalias catsearchowners businessprocess businessimpact revenueimpact -->

# <a name="resource-naming-and-tagging-decision-guide"></a>Guides de décision concernant le nommage et l’étiquetage des ressources

L’organisation des ressources cloud est l’une des tâches les plus importantes du service informatique, sauf si tous vos déploiements sont simples. L’organisation de vos ressources remplit trois objectifs principaux :

- **Gestion des ressources** : Votre équipe informatique devra trouver rapidement les ressources associées aux charges de travail, aux environnements, aux groupes de propriété ou autres informations importantes. L’organisation des ressources est essentielle à l’affectation des rôles organisationnels et aux autorisations d’accès pour la gestion des ressources.
- **Automatisation :** En plus de faciliter la gestion des ressources pour le personnel informatique, un bon modèle organisationnel vous permet de tirer parti de l’automatisation dans le cadre de la création de ressources, de la supervision des opérations et de la création de processus DevOps.
- **Comptabilité :** Pour informer les groupes métier de leur consommation de ressources cloud, le service informatique doit d’abord connaître les ressources qui sont utilisées par les charges de travail et les différentes équipes. Pour prendre en charge les approches telles que la facturation de type chargeback/showback, les ressources cloud doivent être organisées de manière à refléter leur propriété et leur utilisation.

## <a name="tagging-decision-guide"></a>Guide de décision concernant l’étiquetage

![Options d’étiquetage, de la moins complexe à la plus complexe, dans l’ordre des liens ci-dessous](../../_images/decision-guides/decision-guide-resource-tagging.png)

Passer à : [Conventions de nommage des bases de référence](#baseline-naming-conventions) | [Modèles d’étiquetage des ressources](#resource-tagging-patterns) | [En savoir plus](#learn-more)

Votre approche d’étiquetage peut être simple ou complexe, et mettre l’accent aussi bien sur l’aide apportée aux équipes informatique chargées de gérer les charges de travail cloud, que sur l’intégration des informations relatives à tous les aspects de l’entreprise.

Un étiquetage aligné sur le service informatique (comme l’étiquetage basé sur la charge de travail, la fonction ou l’environnement) permet de simplifier la supervision des ressources et de faciliter les décisions de gestion prises en fonction des besoins opérationnels.

L’étiquetage des schémas qui sont alignés sur l’entreprise (comme la comptabilité, la propriété d’entreprise ou la criticité) peut nécessiter plus de temps, notamment pour créer des standards d’étiquetage qui reflètent les intérêts métier, et pour conserver ces standards. Toutefois, le résultat de ce processus est un système d’étiquetage qui permet de mieux prendre en compte les coûts ainsi que la valeur des ressources informatiques de l’entreprise. Le fait d’associer la valeur métier d’une ressource à son coût d’exploitation est l’une des premières étapes permettant de modifier la façon dont votre organisation perçoit l’informatique en tant que centre de coûts.

## <a name="baseline-naming-conventions"></a>Conventions de nommage des bases de référence

Une convention de nommage standardisée constitue le point de départ de l’organisation de vos ressources hébergées dans le cloud. Un système de nommage correctement structuré vous permet d’identifier rapidement les ressources à des fins de gestion et de comptabilité. Si vous disposez déjà de conventions de nommage informatiques dans d’autres services de votre organisation, déterminez si les conventions de nommage cloud doivent s’aligner sur ces conventions ou si vous devez établir des standards distincts pour le cloud.

Notez également que les [exigences de nommage](../../ready/azure-best-practices/naming-and-tagging.md) varient selon le type de ressource Azure. Vos conventions de nommage doivent être compatibles avec ces exigences de nommage.

## <a name="resource-tagging-patterns"></a>Modèles d’étiquetage des ressources

Pour obtenir une organisation plus sophistiquée que celle fournie par une convention de nommage cohérente seule, les plateformes cloud permettent d’étiqueter les ressources.

Les *étiquettes* sont des éléments de métadonnées qui sont associés aux ressources. Les étiquettes sont constituées de paires de chaînes clé/valeur. Il vous revient de choisir les valeurs à inclure dans ces paires. Toutefois, l’application d’un ensemble cohérent d’étiquettes globales, faisant partie d’une stratégie de nommage et d’étiquetage complète, constitue un élément essentiel des stratégies globales de gouvernance.

Dans le cadre de votre processus de planification, aidez-vous des questions suivantes pour déterminer le type d’informations que doivent prendre en charge vos étiquettes de ressource :

- Vos stratégies de nommage et d’étiquetage doivent-elles être intégrées aux stratégies de nommage et aux stratégies organisationnelles qui existent dans votre organisation ?
- Allez-vous implémenter un système de comptabilité de type chargeback/showback ? Devez-vous associer des ressources à des informations de comptabilité pour des services, des groupes professionnels et des équipes en utilisant plus de détails que ne le permet une simple répartition au niveau de l’abonnement ?
- L’étiquetage doit-il présenter des informations telles que les exigences de conformité réglementaire pour une ressource ? Qu’en est-il des détails opérationnels tels que les exigences de disponibilité, la planification des mises à jour correctives et les exigences de sécurité ?
- D’après la stratégie informatique centralisée, de quelles étiquettes aurez-vous besoin pour toutes les ressources ? Quelles étiquettes sont facultatives ? Chaque équipe est-elle autorisée à implémenter ses propres schémas d’étiquetage personnalisés ?

Les modèles d’étiquetage courants listés ci-dessous montrent comment vous pouvez utiliser l’étiquetage pour organiser les ressources cloud. Ces modèles ne sont pas destinés à être exclusifs et peuvent être utilisés en parallèle, fournissant ainsi plusieurs façons d’organiser les ressources en fonction des besoins de votre entreprise.

<!-- markdownlint-disable MD033 -->

| Type d’étiquette | Exemples | Description |
|-----|-----|-----|
| Fonctionnelle            | app = catalogsearch1 <br/>tier = web <br/>webserver = apache<br/>env = prod <br/>env = staging <br/>env = dev                 | Permet d’attribuer une catégorie aux ressources par rapport à leur rôle au sein d’une charge de travail, à l’environnement dans lequel elles ont été déployées, ou par rapport à d’autres fonctionnalités ou détails opérationnels.                                 |
| classification ;        | confidentiality=private<br/>sla = 24hours                                 | Classifie une ressource selon son utilisation et les stratégies qui y sont appliquées                               |
| Comptabilité            | department = finance <br/>project = catalogsearch <br/>region = northamerica | Permet à la ressource d’être associée à des groupes d’une organisation à des fins de facturation |
| Partenariat           | owner = jsmith <br/>contactalias = catsearchowners<br/>stakeholders = user1;user2;user3<br/>                       | Fournit des informations sur la façon dont les utilisateurs (en dehors de l’équipe informatique) sont liés à la ressource ou affectés par celle-ci.                      |
| Objectif               | businessprocess=support<br/>businessimpact=moderate<br/>revenueimpact=high   | Aligne les ressources sur les fonctions métier pour mieux prendre en charge les décisions relatives aux investissements  |

<!-- markdownlint-enable MD033 -->

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations sur le nommage et l’étiquetage dans Azure, consultez :

- [Conventions d’affectation de noms pour les ressources Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming). Consultez ce guide afin de connaître les conventions de nommage recommandées pour les ressources Azure.
- [Organisation des ressources Azure à l’aide d’étiquettes](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags). Dans Azure, vous pouvez appliquer des étiquettes au niveau des groupes de ressources et au niveau des ressources, ce qui vous permet de choisir le niveau de granularité des rapports comptables en fonction des étiquettes appliquées.

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, l’étiquetage des ressources ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
