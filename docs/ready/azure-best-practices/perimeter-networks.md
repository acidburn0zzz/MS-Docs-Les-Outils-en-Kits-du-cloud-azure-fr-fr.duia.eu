---
title: Réseaux de périmètre
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à configurer Azure de manière efficace pour votre organisation.
author: tracsman
ms.author: jonor
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: cbf77bad65753d219e3a0a53f300aee3690b001d
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093243"
---
<!-- cSpell:ignore tracsman jonor rossort NVAs WAFs -->

# <a name="perimeter-networks"></a>Réseaux de périmètre

Les [réseaux de périmètre][perimeter-network] permettent d’établir une connectivité sécurisée entre vos réseaux cloud et les réseaux de vos centres de données locaux ou physiques, ainsi qu’une connectivité à destination et en provenance d’Internet. Ils sont également appelés zones démilitarisées (DMZ).

Pour que les réseaux de périmètre soient efficaces, les paquets entrants doivent circuler via des appliances de sécurité hébergées dans des sous-réseaux sécurisés avant d’atteindre les serveurs principaux. Par exemple, le pare-feu, les systèmes de détection d’intrusion (IDS) et les systèmes de prévention d’intrusion (IPS). Avant de quitter le réseau, les paquets Internet de charges de travail doivent également transiter par les appliances de sécurité du réseau de périmètre. Les finalités de ce flux sont la mise en œuvre, l’inspection et l’audit des stratégies.

Les réseaux de périmètre utilisent les fonctionnalités et services Azure suivants :

- [des réseaux virtuels][virtual-networks], [des itinéraires définis par l’utilisateur][user-defined-routes] et [des groupes de sécurité réseau][network-security-groups]
- [Appliances virtuelles réseau (NVA)][NVA]
- [Équilibrage de charge Azure][ALB]
- [Azure Application Gateway][AppGW] et [WAF (pare-feu d’applications web)][AppGWWAF]
- [Adresses IP publiques][PIP]
- [Azure Front Door][AFD] avec [pare-feu d’applications web][AFDWAF]
- [Pare-feu Azure][AzFW]

> [!NOTE]
> Les architectures de référence Azure fournissent des exemples de modèles que vous pouvez utiliser pour implémenter vos propres réseaux de périmètre :
>
> - [Implémenter une zone DMZ entre Azure et votre centre de données local](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid)
> - [Implémenter une zone DMZ entre Azure et Internet](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

En règle générale, votre équipe centrale d’informatique et de sécurité est responsable de la définition des conditions requises pour le fonctionnement de vos réseaux de périmètre.

![Exemple de topologie de réseau hub-and-spoke](../../_images/azure-best-practices/network-high-level-perimeter-networks.png)

Le diagramme ci-dessus montre un exemple de [topologie de réseau hub-and-spoke](./hub-spoke-network-topology.md), qui implémente l’application de deux périmètres avec un accès à Internet et à un réseau local. Les deux périmètres résident dans le hub DMZ. Dans le hub DMZ, le réseau de périmètre vers Internet peut monter en puissance pour permettre la prise en charge d’un grand nombre de métiers (LOB) à l’aide de plusieurs batteries d’instances WAF et de Pare-feu Azure qui contribuent à protéger les réseaux virtuels spoke. Le hub permet également une connectivité via un VPN ou Azure ExpressRoute le cas échéant.

## <a name="virtual-networks"></a>Réseaux virtuels

Les réseaux de périmètre reposent généralement sur un [réseau virtuel][virtual-networks] comprenant plusieurs sous-réseaux pour héberger les différents types de services qui filtrent et inspectent le trafic à destination ou en provenance d’Internet via les instances NVA, WAF et Azure Application Gateway.

## <a name="user-defined-routes"></a>Itinéraires définis par l’utilisateur

À l’aide d’[itinéraires définis par l’utilisateur][user-defined-routes], les clients peuvent déployer des pare-feu, des systèmes de détection ou de prévention d’intrusion ainsi que d’autres appliances virtuelles. Ils peuvent router le trafic via ces appliances de sécurité pour garantir la mise en œuvre, l’audit et l’inspection des stratégies relatives aux limites de sécurité. Des itinéraires définis par l’utilisateur peuvent être créés pour garantir que le trafic transite par les machines virtuelles personnalisées, les instances NVA et les équilibreurs de charge spécifiés.

Dans un exemple de réseau hub and spoke, garantir que le trafic généré par les machines virtuelles qui résident dans le spoke passe par les appliances virtuelles appropriées dans le hub nécessite un itinéraire défini par l’utilisateur dans les sous-réseaux du spoke. Cet itinéraire définit l’adresse IP frontale de l’équilibreur de charge interne en tant que prochain tronçon. L’équilibreur de charge interne distribue le trafic interne vers les appliances virtuelles (pool principal d’équilibreur de charge).

## <a name="azure-firewall"></a>Pare-feu Azure

[Pare-feu Azure][AzFW] est un service informatique managé qui aide à protéger vos ressources de réseau virtuel Azure. Il s’agit d’un pare-feu managé avec état intégral, doté d’une haute disponibilité intégrée et d’une extensibilité illimitée dans le cloud. Vous pouvez créer, appliquer et consigner des stratégies de connectivité réseau et d’application de façon centralisée entre les abonnements et les réseaux virtuels.

Le service Pare-feu Azure utilise une adresse IP publique statique pour vos ressources de réseau virtuel. Il permet aux pare-feu externes d’identifier le trafic provenant de votre réseau virtuel. Le service est interopérable avec Azure Monitor pour l’enregistrement et les analyses.

## <a name="network-virtual-appliances"></a>Appliances virtuelles réseau

Les réseaux de périmètre disposant d’un accès à Internet sont généralement managés par le biais d’une instance de Pare-feu Azure, une batterie de pare-feu ou des [pare-feu d’applications web][AFDWAF].

Les différents métiers utilisent habituellement de nombreuses applications web. Ces applications ont tendance à comporter diverses vulnérabilités face aux attaques potentielles. Un pare-feu d’applications web détecte les attaques contre les applications web (HTTP/HTTPS) de façon plus approfondie qu’un pare-feu générique. Contrairement à la technologie de pare-feu classique, les pare-feu d’applications web intègrent un ensemble de fonctionnalités spécifiques pour aider à protéger les serveurs web internes contre les menaces.

Une instance de Pare-feu Azure et un pare-feu d’[appliance virtuelle réseau][NVA] utilisent un plan d’administration commun avec un ensemble de règles de sécurité pour aider à protéger les charges de travail hébergées dans les spokes et à contrôler l’accès aux réseaux locaux. Le Pare-feu Azure dispose d’une extensibilité intégrée, alors que les pare-feu NVA peuvent être manuellement mis à l’échelle derrière un équilibreur de charge.

Une batterie de pare-feu est généralement équipée de logiciels moins spécialisés qu’un WAF, mais dispose d’un champ d’application plus vaste permettant de filtrer et d’inspecter n’importe quel type de trafic en entrée et en sortie. Si vous utilisez une approche NVA, vous pouvez rechercher et déployer le logiciel à partir de la Place de marché Azure.

Utilisez un ensemble d’instances de Pare-feu Azure (ou NVA) pour le trafic provenant d’Internet et un autre ensemble pour le trafic émanant du niveau local. L’utilisation d’un seul ensemble de pare-feu pour ces deux types de trafic constitue un risque pour la sécurité, car elle n’offre aucun périmètre de sécurité entre les deux. L’utilisation de couches de pare-feu distinctes simplifie la vérification des règles de sécurité et permet d’identifier clairement les règles auxquelles correspondent les différentes requêtes réseau entrantes.

## <a name="azure-load-balancer"></a>Azure Load Balancer

[Azure Load Balancer][ALB] offre un service haute disponibilité de couche 4 (TCP/UDP), qui peut distribuer le trafic entrant entre des instances de service définies dans un jeu à charge équilibrée. Le trafic envoyé à l’équilibreur de charge à partir de points de terminaison frontaux (points de terminaison IP publics ou privés) peut être redistribué avec ou sans traduction d’adresses à un pool d’adresses IP principales (par exemple, des appliances virtuelles réseau ou des machines virtuelles).

Azure Load Balancer peut également tester l’intégrité des différentes instances de serveur. Quand une instance ne répond pas au probe, l’équilibreur de charge cesse d’envoyer du trafic à l’instance non saine.

En guise d’exemple d’utilisation d’une topologie de réseau hub and spoke, vous pouvez déployer un équilibreur de charge externe sur le hub et les spokes. Dans le hub, l’équilibreur de charge achemine efficacement le trafic vers les services des spokes. Dans les spokes, les équilibreurs de charge gèrent le trafic des applications.

## <a name="azure-front-door-service"></a>Azure Front Door Service

[Azure Front Door Service][AFD] est une plateforme d’accélération d’applications web évolutive et à haute disponibilité et un équilibreur de charge HTTPS mondial de Microsoft. Vous pouvez utiliser Azure Front Door Service pour générer, exécuter et effectuer un scale-out de vos applications web dynamiques et de votre contenu statique. Il s’exécute dans plus de 100 emplacements en périphérie du réseau mondial de Microsoft.

Azure Front Door Service fournit à votre application l’automatisation de la maintenance de région/d’horodatage unifiée, l’automatisation de la continuité d’activité et de la reprise d’activité, des informations client/utilisateur unifiées, une mise en cache, ainsi que des insights sur les services. La plateforme offre des SLA en matière de niveau de performance, de fiabilité et de prise en charge. Elle offre également des certifications de conformité et des pratiques de sécurité vérifiables, dont le développement, le fonctionnement et la prise en charge sont effectués de manière native par Azure.

## <a name="application-gateway"></a>Application Gateway

[Azure Application Gateway][AppGW] est une appliance virtuelle dédiée qui propose un contrôleur managé de livraison d’applications (ADC). Elle offre diverses fonctionnalités d’équilibrage de charge de couche 7 pour votre application.

Application Gateway vous permet d’optimiser la productivité de la batterie de serveurs web en déchargeant une terminaison SSL gourmande en ressources de l’UC vers la passerelle de l’application. Elle fournit également d’autres fonctionnalités de routage de couche 7, notamment la distribution en tourniquet (round-robin) du trafic entrant, l’affinité de session basée sur les cookies, le routage basé sur le chemin d’accès de l’URL et la possibilité d’héberger plusieurs sites web derrière une seule passerelle d’application.

La référence SKU du WAF de la passerelle d’application comprend un pare-feu d’applications web. Cette référence SKU protège les applications web contre les vulnérabilités et les codes malveillants exploitant une faille de sécurité les plus courants sur le web. Vous pouvez configurer Application Gateway en tant que passerelle accessible sur Internet, passerelle interne uniquement ou une combinaison des deux.

## <a name="public-ips"></a>Adresses IP publiques

Avec certaines fonctionnalités Azure, vous pouvez associer des points de terminaison de service à une adresse [IP publique][PIP], pour que votre ressource soit accessible à partir d’Internet. Ce point de terminaison utilise NAT (traduction d’adresses réseau) pour router le trafic vers l’adresse et le port internes sur le réseau virtuel Azure. Il s’agit du principal chemin d’accès pour que le trafic externe passe dans le réseau virtuel. Vous pouvez configurer des adresses IP publiques pour déterminer le type de trafic transmis, ainsi que la façon dont la traduction s’opère sur le réseau virtuel et son emplacement précis.

## <a name="azure-ddos-protection-standard"></a>Service Protection DDos Standard Azure

Le service [Azure DDoS Protection Standard][DDoS] fournit des fonctionnalités d’atténuation supplémentaires par rapport au niveau de [service De base][DDoS] qui sont destinées spécifiquement aux ressources de réseau virtuel Azure. Le service DDoS Protection Standard est facile à activer et ne nécessite aucun changement de l’application.

Vous pouvez paramétrer les stratégies de protection par le biais d’algorithmes de surveillance du trafic et d’apprentissage automatique dédiés. Ces stratégies sont appliquées aux adresses IP publiques associées aux ressources déployées sur des réseaux virtuels. Exemples : instances Azure Load Balancer, Azure Application Gateway et Azure Service Fabric.

Les données de télémétrie en temps réel sont disponibles par le biais d’affichages Azure Monitor pendant une attaque et à des fins d’historique. Vous pouvez ajouter une protection de la couche application à l’aide du pare-feu d’applications web dans Azure Application Gateway. La protection est assurée pour les adresses IP publiques IPv4 Azure.

<!-- links -->

[virtual-networks]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview
[network-security-groups]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg
[user-defined-routes]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview
[NVA]: https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: https://docs.microsoft.com/azure/firewall/overview
[perimeter-network]: https://docs.microsoft.com/azure/best-practices-network-security
[ALB]: https://docs.microsoft.com/azure/load-balancer/load-balancer-overview
[DDoS]: https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview
[PIP]: https://docs.microsoft.com/azure/virtual-network/virtual-network-public-ip-address
[AFD]: https://docs.microsoft.com/azure/frontdoor/front-door-overview
[AFDWAF]: https://docs.microsoft.com/azure/frontdoor/waf-overview
[AppGW]: https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction
[AppGWWAF]: https://docs.microsoft.com/azure/application-gateway/application-gateway-web-application-firewall-overview
