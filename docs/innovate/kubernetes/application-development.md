---
title: Développement et déploiement d’applications
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment utiliser Kubernetes dans le Cloud Adoption Framework pour le développement et l’architecture d’applications.
author: sabbour
ms.author: asabbour
ms.topic: guide
ms.date: 03/20/2020
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 54d1af4e3f4c0669548638451544de9c6678481a
ms.sourcegitcommit: 25cd1b3f218d0644f911737a6d5fd259461b2458
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80226703"
---
# <a name="application-development-and-deployment"></a>Développement et déploiement d’applications

Examinez les modèles et les pratiques de développement d’applications, configurez les pipelines DevOps et implémentez les bonnes pratiques SRE (Site Reliability Engineering).

## <a name="plan-train-and-proof"></a>Planifier, former et vérifier

Pour bien démarrer, la liste de contrôle et les ressources ci-dessous vous aideront à planifier le développement et le déploiement de vos applications. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Avez-vous préparé votre environnement de développement et configuré le workflow ?
> - Comment allez-vous structurer le dossier du projet pour prendre en charge le développement d’applications Kubernetes ?
> - Avez-vous identifié les exigences en matière d’état, de configuration et de stockage de votre application ?

<!-- markdownlint-disable MD033 -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle | Ressources |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Préparer votre environnement de développement** Configurez votre environnement avec les outils dont vous avez besoin pour créer des conteneurs et configurer votre workflow de développement. | [Utilisation de Docker dans Visual Studio Code](https://code.visualstudio.com/docs/azure/docker) <br/>[Utilisation&nbsp;de&nbsp;Kubernetes&nbsp;dans&nbsp;Visual&nbsp;Studio Code](https://code.visualstudio.com/docs/azure/kubernetes) <br/> [Présentation d’Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about) |
> | **Conteneurisez votre application.** Familiarisez-vous avec l’expérience de développement Kubernetes de bout en bout, notamment la génération de modèles automatique d’application, les workflows de boucle interne, les frameworks de gestion d’applications, les pipelines CI/CD, l’agrégation de journaux, la supervision et les métriques d’application. | [Conteneuriser vos applications avec Docker et Kubernetes (livre électronique)](https://azure.microsoft.com/resources/containerize-your-apps-with-docker-and-kubernetes) <br/> [Expérience de développement Kubernetes de bout en bout sur Azure (webinaire)](https://info.microsoft.com/AU-AzureApp-WBNR-FY20-11Nov-12-ContainerizeYourApplicationswithKubernetesonAzure-SRDEM10557_LP02OnDemandRegistration-ForminBody.html) |
> | **Passez en revue les scénarios Kubernetes courants.** Kubernetes est souvent considéré comme une plateforme pour la diffusion de microservices, mais il s’agit de nos jours d’une plateforme beaucoup plus large. Regardez cette vidéo pour en savoir plus sur les scénarios Kubernetes courants, tels que le workflow et l’analytique par lot.    | [Scénarios&nbsp;courants&nbsp;d’&nbsp;utilisation de &nbsp;Kubernetes&nbsp;(vidéo)](https://www.youtube.com/watch?v=zd8vYhrFXp4&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=7) |
> | **Préparez votre application pour Kubernetes.** Préparez la disposition de votre système de fichiers d’application pour Kubernetes et planifiez des mises en production hebdomadaires ou quotidiennes. Découvrez comment le processus de déploiement Kubernetes permet d’effectuer des mises à niveau fiables et sans temps d’arrêt. | [Conception et disposition de projet pour des applications Kubernetes réussies (webinaire)](https://info.microsoft.com/ww-OnDemandRegistration-successful-kubernetes-applications-webinar.html) <br/> [Fonctionnement des déploiements Kubernetes (vidéo)](https://www.youtube.com/watch?v=mNK14yXIZF4&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=3) </br> [Suivre un atelier AKS](https://aka.ms/learn/aksworkshop) |
> | **Gérez le stockage d’application.** Veillez à bien comprendre les besoins en matière de performances des pods et les méthodes pour y accéder afin de fournir les options de stockage appropriées. Vous devez également planifier des méthodes pour sauvegarder et tester le processus de restauration pour le stockage attaché. | [Notions de base des applications avec état dans Kubernetes (vidéo)](https://www.youtube.com/watch?v=GieXzb91I40&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=9) <br/> [État et données dans les applications Docker](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/docker-application-state-data) <br/>[Options de stockage dans Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/operator-best-practices-storage) |
> | **Gérez les secrets d’application.** Ne stockez pas les informations d’identification dans le code de votre application. Vous devez utiliser un coffre de clés pour stocker et récupérer les clés et les informations d’identification.  | [Fonctionnement de Kubernetes et de la gestion de la configuration (vidéo)](https://www.youtube.com/watch?v=vRcQOZLnKUk&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=11) <br/> [Comprendre la gestion des secrets dans Kubernetes (vidéo)](https://www.youtube.com/watch?v=KmhM33j5WYk&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=10) <br/>[Utilisation d’Azure Key Vault avec Kubernetes](https://github.com/Azure/kubernetes-keyvault-flexvol) <br/>[Utiliser l’identité Pod pour s’authentifier et accéder aux ressources Azure](https://github.com/Azure/aad-pod-identity) |

## <a name="deploy-to-production-and-apply-best-practices"></a>Déployer en production et appliquer les bonnes pratiques

Lors de la préparation de l’application pour la production, vous devez implémenter un ensemble minimal de bonnes pratiques. Utilisez la liste de contrôle ci-dessous à ce stade. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Pouvez-vous superviser tous les aspects de votre application ?
> - Avez-vous défini des besoins en ressources pour votre application ? Qu’en est-il des exigences de mise à l’échelle ?
> - Pouvez-vous déployer de nouvelles versions de l’application sans affecter les systèmes de production ?

<!-- -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources                                                                                                     |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Configurez des contrôles d’intégrité de préparation et d’activité.** Kubernetes utilise des contrôles de préparation et d’activité pour savoir quand votre application est prête à recevoir le trafic et quand elle doit être redémarrée. Si vous ne définissez pas ces contrôles, Kubernetes ne pourra pas déterminer si votre application est opérationnelle.   | [Liveness and readiness checks](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes) (Contrôles de préparation et d’activité) |
> | **Configurez la journalisation, la supervision de l’application et les alertes.** La supervision de vos conteneurs est cruciale, particulièrement lorsque vous exécutez un cluster de production à grande échelle, avec plusieurs applications.  La méthode de journalisation recommandée pour les applications conteneurisées consiste à écrire dans les flux de sortie standard (stdout) et d’erreur standard (stderr).   | [Logging in Kubernetes](https://kubernetes.io/docs/concepts/cluster-administration/logging) (Journalisation dans Kubernetes) <br/> [Bien démarrer avec la supervision et les alertes pour Kubernetes (vidéo)](https://www.youtube.com/watch?v=W7aN_z-cyUw&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=16) <br/> [Azure Monitor pour conteneurs](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview) <br/> [Activer et consulter les journaux d'activité du nœud principal Kubernetes dans Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/view-master-logs)  <br/> [Afficher les journaux, métriques de pod et événements Kubernetes en temps réel](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-livedata-overview) |
> | **Définissez les besoins en ressources pour l’application.** L’un des principaux moyens de gérer les ressources de calcul au sein d’un cluster Kubernetes consiste à utiliser des requêtes et des limites de pod. Ces requêtes et limites indiquent au planificateur Kubernetes quelles ressources de calcul attribuer à un pod.     | [Définir&nbsp;les&nbsp;requêtes&nbsp;et&nbsp;limites&nbsp;de ressources de pod](https://docs.microsoft.com/azure/aks/developer-best-practices-resource-management) |
> | **Configurez les exigences de mise à l’échelle des applications.** Kubernetes prend en charge la mise à l’échelle horizontale automatique des pods pour ajuster le nombre de pods dans un déploiement en fonction de l’utilisation du processeur ou d’autres métriques. Pour que vous puissiez utiliser le programme de mise à l’échelle automatique, tous les conteneurs de vos pods doivent avoir des requêtes et limites de processeur définies.    | [Configurer le programme de mise à l’échelle automatique horizontale de pod](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale#autoscale-pods) |
> | **Déployez des applications à l’aide de DevOps et d’un pipeline automatisé.**  L’automatisation complète de toutes les étapes entre la validation du code et le déploiement de production permet aux équipes de se concentrer sur la création du code, et élimine la surcharge et le risque d’erreur humaine lors des étapes banales et manuelles. Le déploiement de nouveau code est plus rapide et moins risqué, ce qui aide les équipes à devenir plus agiles, plus productives et plus confiantes quant à leur code en cours d’exécution.    | [Faire évoluer vos activités DevOps](https://docs.microsoft.com/learn/paths/evolve-your-devops-practices) <br/> [Configuration d’un pipeline de build Kubernetes (vidéo)](https://www.youtube.com/watch?v=5irsAdKoEBU&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=6) <br/> [Centre de déploiement pour Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/deployment-center-launcher) <br/> [GitHub Actions pour un déploiement sur Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/kubernetes-action) <br/>  [CI/CD vers Azure Kubernetes Service avec Jenkins](https://docs.microsoft.com/azure/aks/jenkins-continuous-deployment) |

## <a name="optimize-and-scale"></a>Optimiser et mettre à l’échelle

Maintenant que l’application est en production, comment faire pour optimiser votre workflow et préparer votre application et votre équipe pour la mise à l’échelle ? Utilisez la liste de contrôle d’optimisation et de mise à l’échelle pour vous préparer. Vous devez pouvoir répondre à ces questions :

> [!div class="checklist"]
>
> - Les préoccupations intersectorielles sont-elles abstraites de votre application ?
> - Êtes-vous en mesure de maintenir la fiabilité du système et des applications, tout en continuant à itérer sur de nouvelles fonctionnalités et versions ?

<!-- -->

> [!div class="tdCol2BreakAll"]
>
> | Liste de contrôle  | Ressources                                                                                                     |
> |------------------------------------------------------------------|-----------------------------------------------------------------|
> | **Déployez une passerelle API.** Une passerelle API sert de porte d’entrée pour les microservices, dissocie les clients de vos microservices, ajoute une couche de sécurité supplémentaire et réduit la complexité de vos microservices en supprimant la charge liée à la gestion des préoccupations intersectorielles.     | [Utiliser Gestion des API Azure avec des microservices déployés dans Azure Kubernetes Service](https://docs.microsoft.com/azure/api-management/api-management-kubernetes) |
> | **Déployez un maillage de services.** Un maillage de services offre des fonctionnalités axées sur les aspects suivants : gestion du trafic, résilience, stratégie, sécurité, identité forte et observabilité des charges de travail. Votre application est dissociée de ces fonctionnalités opérationnelles, qui sont déplacées par le maillage de services hors de la couche Application, au niveau de la couche Infrastructure.     | [Fonctionnement&nbsp;des&nbsp;maillages&nbsp;de&nbsp;services&nbsp;dans Kubernetes&nbsp;(vidéo)](https://www.youtube.com/watch?v=izVWk7rYqWI&list=PLLasX02E8BPCrIhFrc_ZiINhbRkYMKdPT&index=15&t=0s) <br/> [En savoir plus sur les maillages de services](https://docs.microsoft.com/azure/aks/servicemesh-about) <br/> [Utiliser Istio avec Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/servicemesh-istio-about) <br/> [Utiliser Linkerd avec Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/servicemesh-linkerd-about) <br/> [Utiliser Consul avec Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/servicemesh-consul-about) |
> | **Implémentez des pratiques d’ingénierie de fiabilité de site.**  L’ingénierie de fiabilité de site est une approche éprouvée destinée à maintenir la fiabilité des systèmes et des applications cruciaux tout en effectuant des itérations à la vitesse demandée par la place de marché.   | [Introduction à l’ingénierie de fiabilité de site (SRE)](https://docs.microsoft.com/learn/modules/intro-to-site-reliability-engineering) <br/> [DevOps chez Microsoft : ingénierie de fiabilité de site pour les jeux en streaming](https://azure.microsoft.com/resources/devops-at-microsoft-game-streaming-sre) |
