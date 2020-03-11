---
title: Guide de décision pour la cohérence des ressources
description: Découvrez l’importance de la cohérence des ressources de votre patrimoine cloud et les facteurs qui déterminent les exigences en matière de cohérence des ressources.
author: doodlemania2
ms.author: dermar
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: bb84d0f7ce6c29d52b1aebb54a456634cb942182
ms.sourcegitcommit: 58ea417a7df3318e3d1a76d3807cc4e7e3976f52
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78892393"
---
# <a name="resource-consistency-decision-guide"></a>Guide de décision pour la cohérence des ressources

La [conception d’abonnement](../subscriptions/index.md) Azure définit la façon dont vous organisez vos ressources cloud par rapport à la structure globale de votre organisation, à vos méthodes de comptabilité et à vos besoins de charge de travail. En plus de ce niveau de structure, pour répondre à vos besoins de stratégie de gouvernance organisationnelle dans l’ensemble de votre patrimoine cloud, vous devez organiser, déployer et gérer des ressources au sein d’un abonnement de manière cohérente.

![Traçage des options d’application de la stratégie de la moins complexe à la plus complexe, dans l’ordre des liens ci-dessous](../../_images/decision-guides/decision-guide-resource-consistency.png)

Passer à : [Regroupement de base](#basic-grouping) | [Cohérence de déploiement](#deployment-consistency) | [Cohérence de stratégie](#policy-consistency) | [Cohérence hiérarchique](#hierarchical-consistency) | [Cohérence automatisée](#automated-consistency)

Les décisions concernant le niveau des exigences de cohérence des ressources de votre patrimoine cloud sont principalement motivées par les facteurs suivants : la taille du patrimoine numérique après la migration, les besoins métier ou environnementaux qui ne s’intègrent pas parfaitement à vos approches de conception d’abonnement existantes, ou la nécessité de renforcer la gouvernance au fil du temps après le déploiement des ressources.

La cohérence du déploiement, du regroupement et de la gestion des ressources cloud devient plus importante à mesure que ces facteurs gagnent en importance. Pour atteindre des niveaux plus avancés de cohérence des ressources dans le but de répondre aux besoins croissants, vous devez fournir un effort plus grand au niveau de l’automatisation, des outils et de l’application de la cohérence, ce qui implique plus de temps passé sur la gestion des changements et le suivi.

## <a name="basic-grouping"></a>Regroupement de base

Dans Azure, les [groupes de ressources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) sont un mécanisme d’organisation des ressources de base permettant de regrouper logiquement les ressources dans un abonnement.

Les groupes de ressources servent de conteneurs pour les ressources ayant un cycle de vie commun ainsi que des contraintes de gestion partagées telles que les exigences en matière de stratégie ou de contrôle d’accès en fonction du rôle (RBAC). Les groupes de ressources ne peuvent pas être imbriqués et les ressources ne peuvent appartenir qu’à un seul groupe de ressources. Toutes les actions du plan de contrôle agissent sur l’ensemble des ressources contenues dans un groupe de ressources. Par exemple, la suppression d’un groupe de ressources supprime également toutes les ressources dans ce groupe. Pour déterminer le modèle à privilégier pour la gestion des groupes de ressources, il convient de se poser les questions suivantes :

1. Les contenus du groupe de ressources sont-ils développés ensemble ?
1. Les contenus du groupe de ressources sont-ils gérés, mis à jour et supervisés ensemble et par les mêmes personnes ou équipes ?
1. Les contenus du groupe de ressources sont-ils mis hors service ensemble ?

Si vous avez répondu _non_ à l’une ou plusieurs de ces questions, vous devez placer la ressource en question ailleurs, dans un autre groupe de ressources.

> [!IMPORTANT]
> Les groupes de ressources sont également spécifiques à la région. Toutefois, il arrive fréquemment que des ressources se trouvent dans des régions différentes au sein du même groupe de ressources, car elles sont gérées ensemble comme décrit ci-dessus. Pour plus d’informations sur la sélection des régions, consultez [Plusieurs régions](../../migrate/azure-best-practices/multiple-regions.md).

## <a name="deployment-consistency"></a>Cohérence du déploiement

S’appuyant sur le mécanisme de regroupement des ressources de base, la plateforme Azure offre un système permettant d’utiliser des modèles de déploiement de vos ressources dans l’environnement cloud. Vous pouvez utiliser des modèles pour créer une organisation et des conventions de nommage cohérentes lors du déploiement des charges de travail, en appliquant ces aspects de la conception du déploiement et de la gestion de vos ressources.

Les [modèles Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/template-deployment-overview) vous permettent de déployer vos ressources de façon répétée et cohérente en utilisant une configuration prédéterminée et une structure de groupes de ressources. Les modèles Resource Manager vous aident à définir un ensemble de standards qui serviront de base à vos déploiements.

Par exemple, vous pouvez disposer d’un modèle standard pour déployer une charge de travail de serveur web qui contient deux machines virtuelles en tant que serveurs web combinés à un équilibreur de charge qui répartit le trafic entre les serveurs. Vous pouvez ensuite réutiliser ce modèle pour créer un groupe de machines virtuelles structurellement identiques et un équilibreur de charge chaque fois que ce type de charge de travail est nécessaire. Il vous suffit ensuite de modifier le nom du déploiement et les adresses IP concernées.

Vous pouvez également déployer ces modèles par programmation et les intégrer à vos systèmes CI/CD.

## <a name="policy-consistency"></a>Stratégie de cohérence

Pour s’assurer que les stratégies de gouvernance sont appliquées lors de la création des ressources, une partie de la conception du regroupement des ressources implique l’utilisation d’une configuration commune lors du déploiement des ressources.

En combinant des groupes de ressources et des modèles Resource Manager standardisés, vous pouvez appliquer des standards pour les paramètres requis dans un déploiement et les règles [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) appliquées à chaque ressource ou groupe de ressources.

Par exemple, l’une de vos exigences est que toutes les machines virtuelles déployées dans votre abonnement doivent se connecter à un sous-réseau commun géré par votre équipe informatique centrale. Vous pouvez créer un modèle standard pour le déploiement des machines virtuelles de charge de travail afin de créer un groupe de ressources distinct pour la charge de travail et y déployer les machines virtuelles nécessaires. Ce groupe de ressources disposerait d’une règle de stratégie permettant uniquement de joindre les interfaces réseau du groupe de ressources au sous-réseau partagé.

La section [Application de stratégie](../policy-enforcement/index.md) fournit une discussion approfondie sur la mise en œuvre de vos décisions stratégiques dans le cadre d’un déploiement cloud.

## <a name="hierarchical-consistency"></a>Cohérence hiérarchique

Les groupes de ressources vous permettent de prendre en charge des niveaux hiérarchiques supplémentaires au sein de l’abonnement de votre organisation, en appliquant les règles Azure Policy et les contrôles d’accès au niveau d’un groupe de ressources. Toutefois, à mesure que grandit votre patrimoine cloud, vous aurez peut-être des besoins de gouvernance multiabonnements plus complexes que ceux pouvant être satisfaits par la hiérarchie Entreprise/Service/Compte/Abonnement du Contrat Entreprise Azure.

Les [groupes d’administration Azure](https://docs.microsoft.com/azure/governance/management-groups) vous permettent d’organiser les abonnements dans des structures organisationnelles plus sophistiquées en les regroupant dans une hiérarchie distincte de celle du Contrat Entreprise. Cette autre hiérarchie vous permet d’appliquer des mécanismes d’application des stratégies et de contrôle de l’accès dans plusieurs abonnements à la fois et dans les ressources qu’ils contiennent. Les hiérarchies des groupes d’administration peuvent être utilisées pour associer les abonnements de votre patrimoine cloud à des opérations ou à des besoins de gouvernance métier. Pour plus d’informations, consultez le [Guide de décision concernant les abonnements](../subscriptions/index.md).

## <a name="automated-consistency"></a>Cohérence automatisée

Pour les grands déploiements cloud, la gouvernance mondiale devient à la fois plus importante et plus complexe. Il est essentiel d’appliquer et de faire respecter automatiquement les exigences de gouvernance lors du déploiement des ressources, ainsi que de répondre aux exigences mises à jour pour les déploiements existants.

[Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) donnent les moyens aux organisations de supporter la gouvernance globale des vastes domaines cloud dans Azure. Les blueprints vont au-delà des fonctionnalités fournies par les modèles standard Azure Resource Manager pour créer des orchestrations de déploiement complètes capables de déployer des ressources et d’appliquer des règles de stratégie. Les blueprints prennent en charge la gestion de versions, et permettent de mettre à jour tous les abonnements où le blueprint a été utilisé et de bloquer les abonnements déployés pour éviter la création et la modification non autorisées des ressources.

Ces packages de déploiement permettent aux équipes informatiques et de développement de déployer rapidement de nouvelles charges de travail et des ressources réseau conformes à l’évolution des exigences des stratégies de l’entreprise. Les blueprints peuvent également être intégrés dans les pipelines de CI/CD afin d’appliquer les normes de gouvernance révisées aux déploiements au fur et à mesure de leur mise à jour.

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, la cohérence des ressources ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
