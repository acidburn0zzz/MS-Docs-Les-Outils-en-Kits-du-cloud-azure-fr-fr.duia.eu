---
title: Passer en revue vos options de calcul
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Passer en revue vos options de calcul pour les charges de travail Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: dbdabb6edc425ea3c70706313d2357323d2a523c
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73561877"
---
# <a name="review-your-compute-options"></a>Passer en revue vos options de calcul

La détermination des exigences de calcul pour l’hébergement de vos charges de travail est un facteur clé lorsque vous vous préparez à votre adoption du cloud. Les produits et services de calcul d’Azure prennent en charge un large éventail de scénarios et de fonctionnalités pour le calcul des charges de travail. La façon dont vous configurez votre environnement de zone d’accueil pour prendre en charge vos exigences de calcul dépend des exigences techniques, métier et de gouvernance de votre charge de travail.

## <a name="identify-compute-services-requirements"></a>Identifier les conditions requises pour les services de calcul

Dans le cadre de l’évaluation et de la préparation de votre zone d’accueil, vous devez identifier les ressources de calcul que votre zone d’accueil doit prendre en charge. Ce processus implique l’évaluation de l’ensemble des applications et services qui composent vos charges de travail afin de déterminer leurs exigences en matière de calcul et d’hébergement. Une fois que vous avez identifié et documenté les exigences, vous pouvez créer des stratégies pour votre zone d’accueil afin de contrôler les types de ressources autorisés en fonction des besoins de votre charge de travail.

Pour chaque application ou service que vous allez déployer dans votre environnement de zone d’accueil, utilisez l’arbre de décision suivant comme point de départ pour vous aider à déterminer vos exigences en matière de services de calcul :

![Arbre de décision pour les services de calcul Azure](../../_images/ready/compute-decision-tree.png)

> [!NOTE]
> En savoir plus sur l’évaluation des options de calcul pour l’ensemble de vos applications et services dans le [guide de l’architecture des applications Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-overview).

### <a name="key-questions"></a>Questions clés

Répondez aux questions suivantes sur vos charges de travail pour vous aider à prendre des décisions en vous basant sur l’arbre de décision des services de calcul Azure :

- **Créez-vous des applications et des services en ligne, ou effectuez-vous une migration à partir de charges de travail locales existantes ?** Le développement de nouvelles applications dans le cadre de vos efforts d’adoption du cloud vous permet de tirer pleinement parti des technologies d’hébergement cloud modernes dès la phase de conception.
- **Si vous migrez des charges de travail existantes, pouvez-vous tirer parti des technologies cloud modernes ?** La migration des charges de travail locales nécessite une analyse : Pouvez-vous facilement optimiser les applications et services existants pour tirer parti des technologies cloud modernes, ou est-ce qu’une approche de type _lift-and-shift_ fonctionnera mieux pour vos charges de travail?
- **Vos applications ou services peuvent-ils tirer parti des conteneurs ?** Si vos applications sont de bons candidats pour l’hébergement en conteneur, vous pouvez tirer parti de l’efficacité, de l’extensibilité et des fonctionnalités d’orchestration des ressources fournies par les [Azure Container Services](https://azure.microsoft.com/product-categories/containers). Les services de [stockage sur disque Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) et [Azure Files](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) peuvent être utilisés pour le stockage persistant des applications en conteneur.
- **Vos applications sont-elles basées sur le web ou sur des API, et utilisent-elles PHP, ASP.NET, Node.js ou des technologies similaires ?** Les applications web peuvent être déployées sur des instances [Azure App Service](https://docs.microsoft.com/azure/app-service/overview) gérées, de sorte que vous n’avez pas besoin de gérer des machines virtuelles à des fins d’hébergement.
- **Aurez-vous besoin d’un contrôle total sur le système d’exploitation et l’environnement d’hébergement de votre charge de travail ?** Si vous avez besoin de contrôler l’environnement d’hébergement, y compris le système d’exploitation, les disques, les logiciels exécutés localement et d’autres configurations, vous pouvez utiliser des [machines virtuelles Azure](https://azure.microsoft.com/services/virtual-machines) pour héberger vos applications et services. Outre le choix de la taille des machines virtuelles et des niveaux de performances, vos décisions en matière de stockage sur disque virtuel affectent les performances et les contrats SLA liés à vos charges de travail IaaS. Pour plus d'informations, consultez la documentation du [stockage sur disque Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview).
- **Votre charge de travail implique-t-elle des fonctionnalités HPC (calcul haute performance) ?** [Azure Batch](https://docs.microsoft.com/azure/batch/batch-technical-overview) fournit la planification des tâches et la mise à l'échelle automatique des ressources de calcul sous forme de plateforme en tant que service. L'exécution d'applications parallèles et HPC à grande échelle dans le cloud s'en trouve ainsi facilitée.
- **Vos applications utiliseront-elles une architecture de microservices ?** Les applications qui utilisent une architecture basée sur les microservices peuvent tirer parti de plusieurs technologies de calcul optimisées. Les charges de travail autonomes basées sur les événements peuvent utiliser [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) pour créer des applications évolutives et sans serveur qui n’ont pas besoin d’une infrastructure. Pour les applications qui nécessitent davantage de contrôle sur l’environnement dans lequel les microservices s’exécutent, vous pouvez utiliser des services de conteneur comme [Azure Container Instances](https://docs.microsoft.com/azure/container-instances/container-instances-overview), [Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/intro-kubernetes) et [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).

> [!NOTE]
> La plupart des services de calcul Azure sont utilisés en association avec le stockage Azure. Consultez le [guide de décisions pour le stockage](./storage-options.md) pour vos décisions relatives au stockage.

## <a name="common-compute-scenarios"></a>Scénarios de calcul courants

Le tableau suivant illustre quelques scénarios d’utilisation courants et les services de calcul recommandés pour les gérer :

| **Scénario** | **Service de calcul** |
| --- | --- |
| Je dois provisionner des machines virtuelles Linux et Windows en quelques secondes avec les configurations de mon choix. | [Machines virtuelles Azure](https://azure.microsoft.com/services/virtual-machines) |
| Je dois obtenir une haute disponibilité par mise à l’échelle automatique pour créer des milliers de machines virtuelles en quelques minutes. | [Groupes de machines virtuelles identiques](https://azure.microsoft.com/services/virtual-machine-scale-sets) |
| Je veux simplifier le déploiement, la gestion et les opérations de Kubernetes. | [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service) |
| Je dois accélérer le développement d’applications avec une architecture Serverless orientée événements. | [Azure Functions](https://azure.microsoft.com/services/functions) |
| Je dois développer des microservices et orchestrer des conteneurs sur Windows et Linux. | [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric) |
| Je veux créer rapidement des applications cloud pour le web et les appareils mobiles avec une plateforme entièrement managée. | [Azure App Service](https://azure.microsoft.com/services/app-service) |
| Je veux conteneuriser des applications et exécuter facilement des conteneurs avec une seule commande. | [Azure Container Instances](https://azure.microsoft.com/services/container-instances) |
| Je dois planifier des travaux à l’échelle du cloud et gestion du calcul avec la possibilité de mise à l’échelle à hauteur de dizaines, centaines ou milliers de machines virtuelles. | [Azure Batch](https://azure.microsoft.com/services/batch) |
| Je dois créer des API et applications cloud hautement disponibles et scalables qui peuvent m’aider à me concentrer sur les applications plutôt que sur le matériel. | [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services) |

## <a name="regional-availability"></a>Disponibilité régionale

Azure vous permet d’offrir des services à l’échelle dont vous avez besoin pour atteindre vos clients et partenaires,  _où qu’ils soient_. Un facteur clé dans la planification de votre déploiement cloud consiste à déterminer la région Azure qui hébergera vos ressources de charge de travail.

Certaines options de calcul, telles qu’Azure App Service, sont généralement disponibles dans la plupart des régions Azure. Toutefois, certains services de calcul sont pris en charge uniquement dans des régions spécifiques. Certains types de machines virtuelles et leurs types de stockage associés ont une disponibilité régionale limitée. Avant de choisir les régions dans lesquelles vous allez déployer vos ressources de calcul, nous vous recommandons de consulter la [page Régions](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=azure-vmware-cloudsimple,cloud-services,batch,container-instances,app-service,service-fabric,functions,kubernetes-service,virtual-machine-scale-sets,virtual-machines)  pour vérifier l’état le plus récent de la disponibilité régionale.

Pour en savoir plus sur l’infrastructure globale Azure, consultez la  [page Régions Azure](https://azure.microsoft.com/global-infrastructure/regions). Vous pouvez également afficher  [les produits disponibles par région](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=all) pour obtenir des détails spécifiques sur les services globaux disponibles dans chaque région Azure.

## <a name="data-residency-and-compliance-requirements"></a>Conditions de résidence et de conformité des données

Des exigences légales et contractuelles relatives au stockage de données s’appliquent souvent à vos charges de travail. Ces exigences peuvent varier en fonction de l’emplacement de votre organisation, de la juridiction du stockage et du traitement des fichiers et des données, et de votre secteur d’activité. Les composants des obligations de données à prendre en compte incluent la classification des données, l’emplacement des données et les responsabilités respectives pour la protection des données dans le cadre du modèle de responsabilité partagée. De nombreuses solutions de calcul dépendent des ressources de stockage liées. Cette exigence peut également influencer vos décisions de calcul. Pour obtenir de l’aide sur la compréhension de ces exigences, consultez le livre blanc  [Assurer la conformité de la résidence et de la sécurité des données avec Azure](https://azure.microsoft.com/resources/achieving-compliant-data-residency-and-security-with-azure).

Une partie de vos efforts de conformité peut inclure le contrôle de l’emplacement physique de vos ressources de calcul. Les régions Azure sont organisées en groupes appelés zones géographiques. Une  [zone géographique Azure](https://azure.microsoft.com/global-infrastructure/geographies)  garantit que les exigences de résidence, de souveraineté, de conformité et de résilience des données sont respectées dans les limites géographiques et politiques. Si vos charges de travail sont soumises à une souveraineté des données ou à d’autres exigences de conformité, vous devez déployer vos ressources de stockage dans des régions dans une zone géographique Azure conforme.

## <a name="establish-controls-for-compute-services"></a>Établir des contrôles pour les services de calcul

Lorsque vous préparez votre environnement de zone d’accueil, vous pouvez établir des contrôles qui limitent les ressources que chaque utilisateur peut déployer. Les contrôles peuvent vous aider à gérer les coûts et à limiter les risques de sécurité, tout en permettant aux développeurs et aux équipes informatiques de déployer et de configurer les ressources nécessaires pour prendre en charge vos charges de travail.

Après avoir identifié et documenté les exigences de votre zone d’accueil, vous pouvez utiliser [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) pour contrôler les ressources de calcul que vous autorisez les utilisateurs à créer. Les contrôles peuvent prendre la forme [d’autorisations ou de refus de création de types de ressources de calcul](https://docs.microsoft.com/azure/governance/policy/samples/allowed-resource-types). Par exemple, vous pouvez limiter les utilisateurs à la création de ressources Azure App Service ou Azure Functions uniquement. Vous pouvez également utiliser une stratégie pour contrôler les options autorisées lors de la création d’une ressource, comme la [restriction des références SKU de machine virtuelle qui peuvent être approvisionnées](https://docs.microsoft.com/azure/governance/policy/samples/allowed-skus-storage) ou [l’autorisation d’images de machine virtuelle spécifiques uniquement](https://docs.microsoft.com/azure/governance/policy/samples/allowed-custom-images).

Les stratégies peuvent être étendues à des ressources, des groupes de ressources, des abonnements et des groupes d’administration. Vous pouvez inclure vos stratégies dans les définitions d’[Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints/overview) et les appliquer à plusieurs reprises à l’ensemble de votre parc cloud.
