---
title: Sécurité des clusters et des applications
description: Apprenez-en davantage sur Kubernetes dans le Cloud Adoption Framework pour la sécurité des clusters et des applications.
author: sabbour
ms.author: asabbour
ms.topic: guide
ms.date: 03/20/2020
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 64a7f4097a75b54ef4f91b5889fa31fc3b98d61a
ms.sourcegitcommit: 1a4b140f09bdaa141037c54a4a3b5577cda269db
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80392745"
---
<!-- cSpell:ignore asabbour sabbour kured -->

# <a name="cluster-and-application-security"></a>Sécurité des clusters et des applications

Familiarisez-vous avec les principes de base de la sécurité de Kubernetes et passez en revue la configuration sécurisée des clusters et les conseils en matière de sécurité des applications.

## <a name="plan-train-and-proof"></a>Planifier, former et vérifier

Pour bien démarrer, la liste de contrôle et les ressources ci-dessous vous aideront à planifier les opérations de cluster et la sécurité. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Avez-vous examiné le modèle de sécurité et de menaces des clusters Kubernetes ?
> - Votre cluster est-il activé pour le contrôle d’accès en fonction du rôle ?

<!-- markdownlint-disable MD033 -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Familiarisez-vous avec le livre blanc sur les principes de base de la sécurité de Kubernetes.** Les objectifs principaux d’un environnement Kubernetes sécurisé consistent à s’assurer que les applications qu’il exécute sont protégées, que les problèmes de sécurité peuvent être identifiés et résolus rapidement, et que les futurs problèmes similaires seront évités. | [The Definitive Guide to Securing Kubernetes (whitepaper)](https://clouddamcdnprodep.azureedge.net/gdc/gdc8LXmoZ/original) (Guide de sécurisation de Kubernetes (livre blanc))     |
> | **Passez en revue la configuration du durcissement de la sécurité pour les nœuds de cluster.** Un système d’exploitation hôte à la sécurité durcie réduit la surface d’exposition aux attaques et permet de déployer des conteneurs en toute sécurité. | [Durcissement de la sécurité des hôtes de machines virtuelles AKS](https://docs.microsoft.com/azure/aks/security-hardened-vm-host-image)     |
> | **Configurez le contrôle d’accès en fonction du rôle (RBAC) pour le cluster.** Ce mécanisme de contrôle vous permet d’affecter à des utilisateurs ou à des groupes d’utilisateurs, l’autorisation d’accomplir des opérations, telles que la création ou la modification de ressources, ou encore l’affichage de journaux d’activité à partir de charges de travail d’applications en cours d’exécution. | [Présentation du contrôle d’accès en fonction du rôle (RBAC) dans Kubernetes (vidéo)](https://www.youtube.com/watch?v=G3R24JSlGjY&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=12) <br/> [Intégrer Azure AD à Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/azure-ad-integration) <br/> [Limiter l’accès au fichier de configuration de cluster](https://docs.microsoft.com/azure/aks/control-kubeconfig-access)   |

## <a name="deploy-to-production-and-apply-best-practices"></a>Déployer en production et appliquer les bonnes pratiques

Lors de la préparation de l’application pour la production, vous devez implémenter un ensemble minimal de bonnes pratiques. Utilisez la liste de contrôle ci-dessous à ce stade. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Avez-vous configuré des règles de sécurité réseau pour les communications entrantes, sortantes et entre les pods ?
> - Votre cluster est-il configuré pour appliquer automatiquement les mises à jour de sécurité de nœud ?
> - Exécutez-vous une solution d’analyse de la sécurité pour vos charges de travail de cluster et de conteneur ?

<!-- markdownlint-disable MD033 -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Contrôlez l’accès aux clusters à l’aide de l’appartenance à un groupe.** Configurez le contrôle d’accès en fonction du rôle de Kubernetes pour limiter l’accès aux ressources de cluster en fonction de l’identité ou de l’appartenance de groupe d’un utilisateur. | [Contrôler l’accès aux clusters à l’aide du contrôle d’accès en fonction du rôle et des groupes Azure AD](https://docs.microsoft.com/azure/aks/azure-ad-rbac)    |
> | **Créez une stratégie de gestion des secrets.** Déployez et gérez en toute sécurité des informations sensibles, telles que des mots de passe et des certificats, à l’aide de la gestion des secrets dans Kubernetes. | [Comprendre la gestion des secrets dans Kubernetes (vidéo)](https://www.youtube.com/watch?v=KmhM33j5WYk&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=10) |
> | **Sécurisez le trafic réseau entre les pods avec des stratégies réseau.** Appliquez le principe du privilège minimum pour contrôler le flux du trafic réseau entre les pods du cluster. | [Sécuriser le trafic entre les pods avec des stratégies réseau](https://docs.microsoft.com/azure/aks/use-network-policies) |
> | **Limitez l’accès au serveur d’API à l’aide d’adresses IP autorisées.** Améliorez la sécurité du cluster et réduisez la surface d’attaque en limitant l’accès au serveur d’API à un ensemble limité de plages d’adresses IP. | [Sécuriser l’accès au serveur d’API](https://docs.microsoft.com/azure/aks/api-server-authorized-ip-ranges) |
> | **Limitez le trafic de sortie du cluster.** Découvrez les ports et adresses à autoriser pour limiter le trafic de sortie du cluster. Vous pouvez utiliser le Pare-feu Azure ou une appliance de pare-feu tierce pour sécuriser votre trafic de sortie et définir ces ports et adresses requis. | [Contrôler le trafic de sortie pour les nœuds de cluster dans AKS](https://docs.microsoft.com/azure/aks/limit-egress-traffic) |
> | **Sécurisez le trafic avec un pare-feu d’applications web (WAF).** Tirez parti d’Azure Application Gateway comme contrôleur d’entrée pour les clusters Kubernetes.  | [Configurer Azure Application Gateway comme contrôleur d’entrée](https://docs.microsoft.com/azure/application-gateway/ingress-controller-overview)    |
> | **Appliquez des mises à jour de sécurité et de noyau aux nœuds Worker.** Familiarisez-vous avec l’expérience de mise à jour des nœuds AKS Pour protéger vos clusters, les mises à jour de sécurité sont appliquées automatiquement aux nœuds Linux dans AKS. Ces mises à jour incluent des correctifs de sécurité ou des mises à jour du noyau. Certaines de ces mises à jour nécessitent un redémarrage du nœud pour terminer le processus. | [Utiliser kured afin de redémarrer automatiquement les nœuds pour appliquer les mises à jour](https://docs.microsoft.com/azure/aks/node-updates-kured) |
> | **Configurez une solution d’analyse de conteneur et de cluster.** Analysez les conteneurs envoyés dans Azure Container Registry et obtenez une visibilité accrue des nœuds de cluster, du trafic cloud et des contrôles de sécurité. | [Intégration d’Azure Container Registry avec Security Center](https://docs.microsoft.com/azure/security-center/azure-container-registry-integration) <br/> [Intégration d’Azure Kubernetes Service à Security Center](https://docs.microsoft.com/azure/security-center/azure-kubernetes-service-integration)  |

## <a name="optimize-and-scale"></a>Optimiser et mettre à l’échelle

Maintenant que l’application est en production, comment faire pour optimiser votre workflow et préparer votre application et votre équipe pour la mise à l’échelle ? Utilisez la liste de contrôle d’optimisation et de mise à l’échelle pour vous préparer. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Pouvez-vous appliquer des stratégies de gouvernance et de cluster à grande échelle ?

<!-- markdownlint-disable MD033 -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Appliquez des stratégies de gouvernance du cluster.** Appliquez une mise en œuvre et une protection à grande échelle sur vos clusters, de manière centralisée et cohérente. | [Contrôler les déploiements avec Azure Policy](https://docs.microsoft.com/azure/governance/policy/concepts/rego-for-aks)    |
> | **Faites permuter régulièrement les certificats de cluster.** Kubernetes utilise des certificats pour l’authentification avec un grand nombre de ses composants. Vous souhaiterez peut-être permuter régulièrement ces certificats pour des raisons de sécurité ou de stratégie. | [Effectuer une rotation des certificats dans Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/certificate-rotation)    |
