---
title: Évaluer les options de votre réseau
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Évaluer les options de votre réseau pour les charges de travail Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: e75c0386b8d66d6a8d65c047c138a4b24483cd23
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73243344"
---
# <a name="review-your-network-options"></a>Évaluer les options de votre réseau

La conception et l’implémentation des fonctionnalités de mise en réseau Azure sont un élément essentiel de vos efforts d’adoption du cloud. Vous devez prendre des décisions en matière de conception réseau pour prendre en charge correctement les charges de travail et les services qui seront hébergés dans le cloud. Les produits et services de mise en réseau Azure prennent en charge un large éventail de fonctionnalités de mise en réseau. La façon dont vous structurez ces services et les architectures de mise en réseau que vous choisissez dépend des exigences en matière de charge de travail, de gouvernance et de connectivité de votre organisation.

## <a name="identify-workload-networking-requirements"></a>Identifier les exigences réseau pour les charges de travail

Dans le cadre de l’évaluation et de la préparation de votre zone d’accueil, vous devez identifier les fonctionnalités réseau que votre zone d’accueil doit prendre en charge. Ce processus implique l’évaluation de l’ensemble des applications et services qui composent vos charges de travail afin de déterminer leurs exigences en matière de contrôle de réseau et de connectivité. Une fois que vous avez identifié et documenté les exigences, vous pouvez créer des stratégies pour votre zone d’accueil afin de contrôler les ressources réseau autorisées et la configuration en fonction des besoins de votre charge de travail.

Pour chaque application ou service que vous allez déployer dans votre environnement de zone d’accueil, utilisez l’arbre de décision suivant comme point de départ pour vous aider à déterminer les outils ou services de mise en réseau à utiliser :

![Arbre de décision des services de mise en réseau Azure](../../_images/ready/network-decision-tree.png)

### <a name="key-questions"></a>Questions clés

Répondez aux questions suivantes sur vos charges de travail pour vous aider à prendre des décisions en vous basant sur l’arbre de décision des services de mise en réseau Azure :

- **Vos charges de travail nécessitent-elles un réseau virtuel ?** Les types de ressources PaaS (Platform as a service) gérés utilisent les fonctionnalités réseau de la plateforme sous-jacente, qui ne nécessitent pas toujours un réseau virtuel. Si vos charges de travail n’ont pas besoin de fonctionnalités de mise en réseau avancées et que vous n’avez pas besoin de déployer des ressources d’infrastructure en tant que service (IaaS), les [fonctionnalités de mise en réseau natives par défaut fournies par les ressources PaaS](../../decision-guides/software-defined-network/paas-only.md) peuvent répondre à vos exigences de connectivité de charge de travail et de gestion du trafic.
- **Vos charges de travail nécessitent-elles une connectivité entre les réseaux virtuels et votre centre de données local ?** Azure propose deux solutions pour l’établissement de fonctionnalités de réseau hybride : La passerelle VPN Azure et Azure ExpressRoute. La [passerelle VPN Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) connecte vos réseaux locaux à Azure via des VPN (réseaux privés virtuels) de site à site, un peu comme si vous configuriez une succursale distante et que vous vous y connectiez. La passerelle VPN a une bande passante maximale de 1,25 Gbits/s. [Azure ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) offre une meilleure fiabilité et une plus faible latence en utilisant une connexion privée entre Azure et votre infrastructure locale. Les options de bande passante pour ExpressRoute sont comprises entre 50 Mbits/s et 100 Gbit/s.
- **Devrez-vous inspecter et auditer le trafic sortant à l’aide de périphériques réseau locaux ?** Pour les charges de travail cloud natives, vous pouvez utiliser un [pare-feu Azure](https://docs.microsoft.com/azure/firewall/overview) ou des [appliances virtuelles réseau tierces](https://azure.microsoft.com/solutions/network-appliances) hébergées dans le cloud pour inspecter et auditer le trafic entrant ou sortant de l’Internet public. Toutefois, de nombreuses stratégies de sécurité informatique d’entreprise exigent que le trafic sortant lié à Internet passe par des appareils gérés de manière centralisée dans l’environnement local de l’organisation. Le [tunneling forcé](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview) prend en charge ces scénarios. Tous les services gérés ne prennent pas en charge le tunneling forcé. Des services et fonctionnalités comme [App Service Environment dans Azure App Service](https://docs.microsoft.com/azure/app-service/environment/intro), la [gestion des API Azure](https://docs.microsoft.com/azure/api-management/api-management-key-concepts), [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/intro-kubernetes), les [instances gérées d’Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index), [Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/what-is-azure-databricks) et [Azure HDInsight](https://docs.microsoft.com/azure/hdinsight) prennent en charge cette configuration lors du déploiement du service ou de la fonctionnalité au sein d’un réseau virtuel.
- **Devrez-vous connecter plusieurs réseaux virtuels ?** Vous pouvez utiliser le [peering de réseaux virtuels](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) pour connecter plusieurs instances d’un [réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview). Le peering peut prendre en charge les connexions entre abonnements et régions. Pour les scénarios dans lesquels vous fournissez des services partagés entre plusieurs abonnements ou devez gérer un grand nombre de peerings réseau, envisagez d’adopter une [architecture de mise en réseau hub-and-spoke](../../decision-guides/software-defined-network/hub-spoke.md) ou d’utiliser [Azure Virtual WAN](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about). Le peering de réseaux virtuels offre une connectivité uniquement entre deux réseaux appairés. Par défaut, il ne fournit pas de connectivité transitive sur plusieurs peerings.
- **Vos charges de travail seront-elles accessibles via Internet ?** Azure fournit des services conçus pour vous aider à gérer et sécuriser l’accès externe à vos applications et services :
  - [Pare-feu Azure](https://docs.microsoft.com/azure/firewall/overview)
  - [Appliances réseau](https://azure.microsoft.com/solutions/network-appliances)
  - [Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
  - [Application Gateway Azure](https://docs.microsoft.com/azure/application-gateway)
  - [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)
- **Devrez-vous prendre en charge la gestion DNS personnalisée ?** [Azure DNS](https://docs.microsoft.com/azure/dns/dns-overview) est un service d’hébergement pour les domaines DNS. Azure DNS offre une résolution de noms à l’aide de l’infrastructure Azure. Si vos charges de travail requièrent une résolution de noms au-delà des fonctionnalités fournies par Azure DNS, vous devrez peut-être déployer des solutions supplémentaires. Si vos charges de travail requièrent également des services [Active Directory](https://docs.microsoft.com/azure/active-directory-domain-services/overview), envisagez d’utiliser Azure Active Directory Domain Services pour améliorer les fonctionnalités de d’Azure DNS. Pour obtenir davantage de fonctionnalités, vous pouvez également [déployer des machines virtuelles IaaS personnalisées](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances) pour répondre à vos besoins.

## <a name="common-networking-scenarios"></a>Scénarios de mise en réseau courants

La mise en réseau Azure est composée de plusieurs produits et services qui fournissent différentes fonctionnalités de mise en réseau. Dans le cadre de votre processus de conception réseau, vous pouvez comparer vos exigences de charge de travail aux scénarios de mise en réseau dans le tableau suivant pour identifier les outils ou services Azure que vous pouvez utiliser pour fournir ces fonctionnalités de mise en réseau :

<!-- markdownlint-disable MD033 -->

| **Scénario** | **Produit ou service de mise en réseau** |
| --- | --- |
| J’ai besoin de l’infrastructure réseau pour tout connecter, des machines virtuelles aux connexions VPN entrantes. | [Réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network) |
| Je dois équilibrer les connexions entrantes et sortantes et les demandes envoyées à mes applications ou services. | [Équilibrage de charge Azure](https://docs.microsoft.com/azure/load-balancer) |
| Je veux optimiser la distribution partir des batteries de serveurs d’applications tout en augmentant la sécurité des applications avec un pare-feu d’applications web. | [Application Gateway Azure](https://docs.microsoft.com/azure/application-gateway) <br/>[Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor) |
| Je dois utiliser Internet en toute sécurité pour accéder aux réseaux virtuels Azure avec des passerelles VPN hautes performances. | [Passerelle VPN Azure](https://docs.microsoft.com/azure/vpn-gateway) |
| J’ai besoin de réponses DNS ultra-rapides et d’une ultra haute disponibilité pour tous mes besoins en matière de domaine. | [DNS Azure](https://docs.microsoft.com/azure/dns) |
| Je dois accélérer la distribution de contenu à large bande passante aux clients du monde entier, des applications et du contenu stocké à la vidéo en streaming. | [Azure Content Delivery Network](https://docs.microsoft.com/azure/cdn) |
| Je dois protéger mes applications Azure contre les attaques DDoS. | [Azure DDoS Protection](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) |
| Je dois distribuer le trafic de manière optimale aux services dans les régions Azure du monde entier, tout en offrant une disponibilité et une adaptabilité élevées. | [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager)<br/>[Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor) |
| Je dois ajouter une connectivité réseau privée pour accéder aux services cloud Microsoft à partir de mes réseaux d’entreprise, comme s’ils se trouvaient en local et résidaient dans mon propre centre de données. | [Azure ExpressRoute](https://docs.microsoft.com/azure/expressroute) |
| Je veux surveiller et diagnostiquer les conditions au niveau d’un réseau. | [Azure Network Watcher](https://docs.microsoft.com/azure/network-watcher) |
| J’ai besoin de fonctionnalités de pare-feu natives, avec une haute disponibilité et une extensibilité cloud illimitée intégrées, et sans aucune maintenance. | [Pare-feu Azure](https://docs.microsoft.com/azure/firewall) |
| Je dois connecter des bureaux, des emplacements de vente et des sites en toute sécurité. | [Azure Virtual WAN](https://docs.microsoft.com/azure/virtual-wan) |
| J’ai besoin d’un point de livraison évolutif et à sécurité augmentée pour des applications web globales basées sur les microservices. | [Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor) |

<!-- markdownlint-enable MD033 -->

## <a name="choose-a-networking-architecture"></a>Choisir une architecture réseau

Après avoir identifié les services de mise en réseau Azure dont vous avez besoin pour prendre en charge vos charges de travail, vous devez également concevoir l’architecture qui associe ces services afin de fournir l’infrastructure réseau cloud de votre zone d’accueil. Le [Guide de décision concernant le SDN (Software Defined Networking)](../../decision-guides/software-defined-network/index.md) fournit des détails sur certains des modèles d’architecture réseau les plus courants utilisés sur Azure.

Le tableau suivant récapitule les principaux scénarios pris en charge par ces modèles :

| **Scénario** | **Architecture réseau suggérée**
| --- | --- |
| Toutes les charges de travail hébergées dans Azure et déployées sur votre zone d’accueil sont entièrement basées sur PaaS, ne nécessitent pas de réseau virtuel et ne font pas partie d’un effort d’adoption du cloud plus étendu qui inclut des ressources IaaS. | [PaaS uniquement](../../decision-guides/software-defined-network/paas-only.md) |
| Vos charges de travail hébergées par Azure déploient des ressources IaaS telles que des machines virtuelles ou nécessitent un réseau virtuel, mais ne nécessitent pas de connectivité à votre environnement local. | [Cloud natif](../../decision-guides/software-defined-network/cloud-native.md) |
| Vos charges de travail hébergées dans Azure nécessitent un accès limité aux ressources locales, mais vous devez traiter les connexions au cloud comme non approuvées. | [Zone DMZ cloud](../../decision-guides/software-defined-network/cloud-dmz.md) |
| Vos charges de travail hébergées dans Azure nécessitent un accès limité aux ressources locales, et vous envisagez d’implémenter des stratégies de sécurité matures et une connectivité sécurisée entre le cloud et votre environnement local. | [Hybride](../../decision-guides/software-defined-network/hybrid.md) |
| Vous devez déployer et gérer un grand nombre de machines virtuelles et de charges de travail , tout en dépassant les [limites d’abonnement Azure](https://docs.microsoft.com/azure/azure-subscription-service-limits), vous devez partager des services entre les abonnements, ou vous avez besoin d’une structure plus segmentée pour la séparation en fonction du rôle, de l’application ou des autorisations. | [Hub-and-spoke](../../decision-guides/software-defined-network/hub-spoke.md) |
| Vous avez de nombreuses filiales qui doivent se connecter les unes aux autres et à Azure. | [Azure Virtual WAN](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about) |

### <a name="azure-virtual-datacenter"></a>Centre de données virtuel Azure

En plus de l’utilisation de l’un de ces modèles d’architecture, si le groupe informatique de votre entreprise gère de grands environnements cloud, vous pouvez consulter les [conseils relatifs au centre de données virtuel Azure](../../reference/vdc.md) lors de la conception de votre infrastructure cloud basée sur Azure. Le centre de données virtuel Azure offre une approche combinée de mise en réseau, de sécurité, de gestion et d’infrastructure si votre organisation respecte les critères suivants :

- Votre entreprise est soumise à des exigences de conformité réglementaire nécessitant des capacités centralisées de surveillance et d’audit.
- Votre parc cloud regroupe plus de 10 000 machines virtuelles IaaS ou une mise à l’échelle équivalente de services PaaS.
- Vous devez mettre en place des capacités de déploiement agiles pour les charges de travail afin de soutenir les équipes de développement et d’exploitation, tout en maintenant la conformité des stratégies et de la gouvernance ainsi qu’un contrôle informatique central sur les services de base.
- Votre activité s’appuie sur une plate-forme complexe qui nécessite une expertise approfondie dans un domaine (par exemple, la finance, le pétrole et le gaz, ou la fabrication).
- Vos stratégies de gouvernance informatique existantes exigent une parité plus étroite avec les fonctionnalités existantes, même pendant la phase initiale d’adoption.

## <a name="follow-azure-networking-best-practices"></a>Suivre les meilleures pratiques de mise en réseau Azure

Dans le cadre de votre processus de conception réseau, consultez les articles suivants :

- [Planification des réseaux virtuels](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez comment planifier des réseaux virtuels selon vos besoins en isolation, connectivité et emplacements.
- [Meilleures pratiques Azure pour la sécurité réseau](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Découvrez les meilleures pratiques Azure qui peuvent vous aider à améliorer la sécurité de votre réseau.
- [Meilleures pratiques pour la mise en réseau lorsque vous migrez des charges de travail vers Azure](https://docs.microsoft.com/azure/migrate/migrate-best-practices-networking?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Obtenez des conseils supplémentaires sur la façon d’implémenter la mise en réseau Azure pour prendre en charge les charges de travail IaaS et PaaS.
