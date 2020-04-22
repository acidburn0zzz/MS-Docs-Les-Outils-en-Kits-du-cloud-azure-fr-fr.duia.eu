---
title: Conception et opérations de cluster
description: Apprenez-en davantage sur Kubernetes dans le Cloud Adoption Framework pour la conception et les opérations de cluster.
author: sabbour
ms.author: asabbour
ms.date: 12/16/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 594b8ae3ce7949c3289d9a81ac9870889a5dba98
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80527177"
---
<!-- cSpell:ignore asabbour sabbour autoscaler PDBs -->

# <a name="cluster-design-and-operations"></a>Conception et opérations de cluster

Identifiez la configuration du cluster et la conception du réseau. Garantissez la scalabilité future en automatisant le provisionnement de l’infrastructure. Assurez une haute disponibilité en planifiant la continuité d’activité et la reprise d’activité.

## <a name="plan-train-and-proof"></a>Planifier, former et vérifier

Pour bien démarrer, la liste de contrôle et les ressources ci-dessous vous aideront à planifier la conception du cluster. Vous devez pouvoir répondre à ces questions :

<!-- markdownlint-disable MD033 -->

> [!div class="checklist"]
>
> - Avez-vous identifié les exigences en matière de conception réseau pour votre cluster ?
> - Avez-vous des charges de travail avec des exigences différentes ? Combien de pools de nœuds allez-vous utiliser ?

<!-- -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Identifiez les considérations relatives à la conception réseau.** Familiarisez-vous avec les considérations relatives à la conception du réseau de clusters, comparez les modèles de réseau et choisissez le plug-in de mise en réseau Kubernetes adapté à vos besoins.    | [Kubenet et Azure Container Networking Interface (CNI)](https://docs.microsoft.com/azure/aks/concepts-network#azure-virtual-networks) <br/> [Utiliser la mise en réseau kubenet avec vos propres plages d’adresses IP dans Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/configure-kubenet) <br/> [Configurer un réseau Azure CNI dans AKS (Azure Kubernetes Service)](https://docs.microsoft.com/azure/aks/configure-azure-cni) <br/> [Conception d’un réseau sécurisé pour un cluster AKS](https://github.com/Azure/sg-aks-workshop/blob/master/cluster-design/NetworkDesign.md)|
> | **Créez plusieurs pools de nœuds.** Pour prendre en charge les applications qui ont des exigences de calcul ou de stockage différentes, vous pouvez éventuellement configurer votre cluster avec plusieurs pools de nœuds. Par exemple, utilisez des pools de nœuds supplémentaires afin de fournir des GPU pour les applications nécessitant beaucoup de ressources système ou d’accéder à un stockage SSD hautes performances.   | [Créer et gérer plusieurs pools de nœuds pour un cluster dans Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/use-multiple-node-pools) |
> | **Déterminez les exigences en matière de disponibilité.** Pour offrir un niveau de disponibilité plus élevé à vos applications, les clusters peuvent être répartis sur plusieurs zones de disponibilité. Ces zones représentent des centres de données physiquement séparés au sein d’une région donnée. Quand les composants du cluster sont répartis sur plusieurs zones, votre cluster est capable de tolérer une défaillance dans l’une de ces zones. Vos applications et vos opérations de gestion restent disponibles même si un centre de données complet rencontre un problème.   | [Créer un cluster Azure Kubernetes Service (AKS) qui utilise des zones de disponibilité](https://docs.microsoft.com/azure/aks/availability-zones) |

## <a name="go-to-production-and-apply-best-practices"></a>Basculer en production et appliquer les bonnes pratiques

Lors de la préparation de l’application pour la production, vous devez implémenter un ensemble minimal de bonnes pratiques. Utilisez la liste de contrôle ci-dessous à ce stade. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Êtes-vous en mesure de redéployer en toute confiance l’infrastructure de cluster ?
> - Avez-vous appliqué des quotas de ressources ?

<!-- -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources                                                                                                     |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Automatisez le provisionnement des clusters.** Avec l’infrastructure en tant que code, vous pouvez automatiser le provisionnement de l’infrastructure afin d’offrir une plus grande résilience pendant les sinistres et gagner en agilité pour redéployer rapidement l’infrastructure en fonction des besoins.     | [Créer un cluster Kubernetes avec Azure Kubernetes Service et Terraform](https://docs.microsoft.com/azure/terraform/terraform-create-k8s-cluster-with-tf-and-aks)|
> | **Planifiez la disponibilité à l’aide de budgets de perturbation de pod.** Pour assurer la disponibilité des applications, définissez des budgets de perturbation de pod afin de vous assurer qu’un nombre minimal de pods est disponible dans le cluster pendant les défaillances matérielles ou les mises à niveau de cluster. | [Planifier la disponibilité à l’aide de budgets de perturbation de pod](https://docs.microsoft.com/azure/aks/operator-best-practices-scheduler#plan-for-availability-using-pod-disruption-budgets)  |
> | **Appliquez des quotas de ressources sur les espaces de noms.** Planifiez et appliquez des quotas de ressources au niveau de l’espace de noms. Vous pouvez définir des quotas sur les ressources de calcul, les ressources de stockage et le nombre d’objets.| [Appliquer des quotas de ressources](https://docs.microsoft.com/azure/aks/operator-best-practices-scheduler#enforce-resource-quotas)  |

## <a name="optimize-and-scale"></a>Optimiser et mettre à l’échelle

Maintenant que l’application est en production, comment faire pour optimiser votre workflow et préparer votre application et votre équipe pour la mise à l’échelle ? Utilisez la liste de contrôle d’optimisation et de mise à l’échelle pour vous préparer. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Avez-vous un plan relatif à la continuité d’activité et à la reprise d’activité ?
> - Votre cluster peut-il être mis à l’échelle pour répondre aux demandes applicatives ?
> - Pouvez-vous superviser l’intégrité de votre cluster et de votre application, et recevoir des alertes ?

<!-- -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Mettez automatiquement à l’échelle un cluster pour répondre aux demandes applicatives.** Pour suivre le rythme des demandes de l’application, vous devrez peut-être ajuster le nombre de nœuds qui exécutent vos charges de travail automatiquement à l’aide du programme de mise à l’échelle automatique de cluster. | [Configurer le programme de mise à l’échelle automatique de cluster Kubernetes](https://docs.microsoft.com/azure/aks/cluster-autoscaler)    |
> | **Planifiez la continuité d’activité et la reprise d’activité.** Planifiez le déploiement multirégion, créez un plan de migration de stockage, et activez la géoréplication pour les images conteneur. | [Meilleures pratiques pour les déploiements dans les régions](https://docs.microsoft.com/azure/aks/operator-best-practices-multi-region)  <br/> [Géoréplication Azure Container Registry](https://docs.microsoft.com/azure/container-registry/container-registry-geo-replication)  |
> | **Configurez la supervision et le dépannage à grande échelle.** Configurez les alertes et la supervision des applications dans Kubernetes. Découvrez la configuration par défaut, comment intégrer des métriques plus sophistiquées, et comment ajouter vos propres fonctions personnalisées de supervision et d’alerte pour faire fonctionner votre application de manière fiable. | [Bien démarrer avec la supervision et les alertes pour Kubernetes (vidéo)](https://www.youtube.com/watch?v=W7aN_z-cyUw&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=16) <br/> [Configurer des alertes à l’aide d’Azure Monitor pour les conteneurs](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview) <br/> [Examiner les journaux de diagnostic pour les composants principaux](https://docs.microsoft.com/azure/aks/view-master-logs) <br/> [Diagnostics Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/concepts-diagnostics)    |
