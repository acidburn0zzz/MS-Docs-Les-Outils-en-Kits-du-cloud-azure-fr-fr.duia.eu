---
title: Topologie de réseau hub-and-spoke
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Topologie de réseau hub-and-spoke
author: tracsman
ms.author: jonor
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: 48f73d7c7f2e7f3bba8183464c786a3e0744807c
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905487"
---
# <a name="hub-and-spoke-network-topology"></a>Topologie de réseau hub-and-spoke

*Hub-and-spoke* est un modèle de réseau visant à gérer de manière plus efficace les besoins de communication ou de sécurité courants. Il permet également d’éviter les limitations des abonnements Azure. Ce modèle répond aux préoccupations suivantes :

- **Réduction des coûts et amélioration de la gestion**. En centralisant les services qui peuvent être partagés par plusieurs charges de travail (comme les appliances virtuelles réseau et les serveurs DNS) en un seul endroit, le service informatique est capable de réduire les ressources et efforts de gestion redondants.
- **Dépassement des limites des abonnements**. Pour exécuter les charges de travail informatiques volumineuses, il se peut que vous ayez besoin d’utiliser davantage de ressources que le quota autorisé par un abonnement Azure unique. (Voir les [limites d’abonnement][Limits].) Vous avez la possibilité de dépasser ces limites en appairant des réseaux virtuels de charge de travail issus de différents abonnements à un hub central.
- **Séparation des problèmes**. Vous pouvez déployer des charges de travail individuelles entre les équipes informatiques centrales et celles dédiées aux charges de travail.

Les patrimoines cloud plus petits pourraient ne pas bénéficier de la structure et des capacités ajoutées offertes par ce modèle. Toutefois, il est préférable d’adopter une architecture de mise en réseau hub-and-spoke en cas d’efforts plus important d’adoption cloud et d’une des préoccupations mentionnées précédemment.

> [!NOTE]
> Le site Architectures de référence Azure contient des exemples de modèles que vous pouvez utiliser comme base pour l’implémentation de vos propres réseaux hub-and-spoke :
>
> - [Implémenter une topologie de réseau hub-and-spoke dans Azure](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
> - [Implémenter une topologie de réseau hub-and-spoke avec des services partagés dans Azure](/azure/architecture/reference-architectures/hybrid-networking/shared-services)

## <a name="overview"></a>Vue d'ensemble

![Exemples de topologie de réseau hub-and-spoke][1]

Comme indiqué dans le diagramme, Azure prend en charge deux types de conception hub-and-spoke. Il prend en charge la communication, les ressources partagées et la stratégie de sécurité centralisée (« hub de réseau virtuel » dans le diagramme), ou un type de réseau étendu virtuel (« Virtual WAN » dans le diagramme) pour les communications de branche à branche à grande échelle et de branche à Azure.

Un hub est une zone réseau centrale qui contrôle et inspecte le trafic d’entrée ou de sortie entre les zones : Internet, le réseau local et des spokes. La topologie hub-and-spoke offre à votre service informatique un moyen efficace d’appliquer des stratégies de sécurité à un emplacement central. Elle réduit également les risques de configuration incorrecte et d’exposition.

Le hub contient souvent les composants de service courants que les spokes consomment. Voici des exemples de services centraux usuels :

- Infrastructure Windows Server Active Directory, nécessaire à l’authentification utilisateur des tiers qui souhaitent accéder aux charges de travail du spoke à partir de réseaux non approuvés. Elle inclut les services de fédération Active Directory (AD FS) associés.
- Service DNS destiné à résoudre le nommage pour la charge de travail dans les spokes et permettant d’accéder aux ressources locales et sur Internet si le service [Azure DNS][DNS] n’est pas utilisé.
- Infrastructure à clé publique (PKI) permettant d’implémenter l’authentification unique sur les charges de travail.
- Contrôle de flux du trafic TCP et UDP entre les zones du réseau à rayons et Internet.
- Contrôle de flux entre les rayons et les ressources locales.
- Si nécessaire, contrôle de flux entre un rayon et un autre.

Vous pouvez réduire la redondance, simplifier la gestion et réduire le coût global en utilisant l’infrastructure de hub partagé pour prendre en charge plusieurs spokes.

Le rôle de chaque rayon peut consister à héberger différents types de charges de travail. Les rayons offrent également une approche modulaire pour les déploiements renouvelables des mêmes charges de travail. C’est le cas, par exemple, des phases de développement et de test, de tests d’acceptation utilisateur, de préproduction et de production.

Les rayons permettent également de séparer et d’activer différents groupes au sein de votre organisation. Les groupes Azure DevOps en sont un exemple. À l’intérieur d’un spoke, il est tout aussi possible de déployer une charge de travail de base que des charges de travail multiniveaux complexes avec un contrôle du trafic entre les différents niveaux.

## <a name="subscription-limits-and-multiple-hubs"></a>Limites d’abonnement et concentrateurs multiples

Dans Azure, chacun des composants, quel qu’en soit le type, est déployé dans un abonnement Azure. L’isolement des composants Azure dans différents abonnements Azure peut satisfaire aux exigences de différents métiers, telles que la configuration de niveaux différenciés d’accès et d’autorisation.

Une implémentation hub-and-spoke unique peut évoluer en un grand nombre de spokes. Mais comme pour tout système informatique, les plateformes ont des limites. Le déploiement du hub est lié à un abonnement Azure spécifique, qui comporte des restrictions et des limites. (Le nombre maximal de Peerings de réseaux virtuels est un bon exemple. Pour plus d’informations, consultez [Abonnement Azure et limites, quotas et contraintes de service][Limits].)

Dans les cas où ces limites peuvent poser problème, vous pouvez procéder à la montée en puissance de l’architecture en faisant évoluer un modèle hub-and-spoke unique vers un cluster constitué de plusieurs hubs et spokes. Vous pouvez interconnecter plusieurs hubs dans une ou plusieurs régions Azure à l’aide du Peering de réseaux virtuels, d’Azure ExpressRoute, d’un WAN virtuel ou d’un VPN site à site.

![Cluster de hubs et de spokes][2]

L’introduction de plusieurs hubs augmente les frais généraux liés au coût et à la gestion du système. Cela se justifie uniquement par l’extensibilité, les limites système, la redondance et la réplication régionale pour le niveau de performance des utilisateurs ou la récupération d’urgence. Dans les scénarios qui nécessitent plusieurs hubs, ces derniers doivent tous, dans la mesure du possible, offrir le même ensemble de services afin d’en faciliter l’exploitation.

## <a name="interconnection-between-spokes"></a>Interconnexion entre les rayons

Il est possible d’implémenter des charges de travail multiniveaux complexes dans un même spoke. Vous pouvez implémenter des configurations multiniveaux à l’aide de sous-réseaux (un pour chaque niveau) dans le même réseau virtuel et en utilisant des groupes de sécurité réseau pour filtrer les flux.

Un architecte peut vouloir déployer une charge de travail multiniveau sur plusieurs réseaux virtuels. Avec le Peering de réseaux virtuels, vous pouvez connecter des spokes à d’autres spokes du même hub ou de hubs distincts.

Ce scénario s’applique généralement aux cas où les serveurs de traitement d’application sont situés dans un même spoke ou réseau virtuel. La base de données est déployée sur un autre spoke ou réseau virtuel. Dans ce cas, il est facile d’interconnecter les spokes grâce au Peering de réseaux virtuels et d’éviter le transit par le hub. La solution est d’étudier avec soin l’architecture et la sécurité pour vérifier que le contournement du hub n’élude pas de points de sécurité ou d’audit importants susceptibles d’exister uniquement dans le hub.

![Spokes se connectant entre eux et un hub][3]

Il est également possible d’interconnecter des rayons à un rayon jouant le rôle de concentrateur. Cette approche crée une hiérarchie à deux niveaux : le spoke du niveau supérieur (niveau 0) devient le hub de spokes inférieurs (niveau 1) dans la hiérarchie. Les spokes d’une implémentation hub-and-spoke doivent transférer le trafic vers le hub central pour que le trafic puisse atteindre sa destination sur le réseau local ou l’Internet public. Une architecture à deux niveaux de hubs introduit un routage complexe qui supprime les avantages d’une relation hub-and-spoke simple.

<!-- images -->

[0]: ./images/network-redundant-equipment.png "Exemples de chevauchement de composants"
[1]: ./images/network-hub-spoke-high-level.png "Exemple de haut niveau de hub-and-spoke"
[2]: ./images/network-hub-spokes-cluster.png "Cluster de concentrateurs et de rayons"
[3]: ./images/network-spoke-to-spoke.png "Rayon à rayon"
[4]: ./images/network-hub-spoke-block-level-diagram.png "Diagramme au niveau des blocs du hub-and-spoke"
[5]: ./images/network-users-groups-subsciptions.png "Utilisateurs, groupes, abonnements et projets"
[6]: ./images/network-infrastructure-high-level.png "Diagramme d’infrastructure de haut niveau"
[7]: ./images/network-highlevel-perimeter-networks.png "Diagramme d’infrastructure de haut niveau"
[8]: ./images/network-vnet-peering-perimeter-neworks.png "Peering de réseaux virtuels et réseaux de périmètre"
[9]: ./images/network-high-level-diagram-monitoring.png "Diagramme de surveillance de haut niveau"
[10]: ./images/network-high-level-workloads.png "Diagramme de charge de travail de haut niveau"

<!-- links -->

[Limits]: /azure/azure-subscription-service-limits
[Roles]: /azure/role-based-access-control/built-in-roles
[VNet]: /azure/virtual-network/virtual-networks-overview
[network-security-groups]: /azure/virtual-network/virtual-networks-nsg
[DNS]: /azure/dns/dns-overview
[PrivateDNS]: /azure/dns/private-dns-overview
[VNetPeering]: /azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: /azure/virtual-network/virtual-networks-udr-overview
[RBAC]: /azure/role-based-access-control/overview
[azure-ad]: /azure/active-directory/active-directory-whatis
[VPN]: /azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: /azure/expressroute/expressroute-introduction
[ExRD]: /azure/expressroute/expressroute-erdirect-about
[vWAN]: /azure/virtual-wan/virtual-wan-about
[NVA]: /azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: /azure/firewall/overview
[SubMgmt]: /azure/architecture/cloud-adoption/appendix/azure-scaffold
[RGMgmt]: /azure/azure-resource-manager/resource-group-overview
[DMZ]: /azure/best-practices-network-security
[ALB]: /azure/load-balancer/load-balancer-overview
[PIP]: /azure/virtual-network/resource-groups-networking#public-ip-address
[AFD]: /azure/frontdoor/front-door-overview
[AppGW]: /azure/application-gateway/application-gateway-introduction
[WAF]: /azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: /azure/monitoring-and-diagnostics/
[ActLog]: /azure/monitoring-and-diagnostics/monitoring-overview-activity-logs
[DiagLog]: /azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[nsg-log]: /azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: /azure/operations-management-suite/operations-management-suite-overview
[NPM]: /azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: /azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: /azure/app-service/
[HDI]: /azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: /azure/event-hubs/event-hubs-what-is-event-hubs
[ServiceBus]: /azure/service-bus-messaging/service-bus-messaging-overview
[traffic-manager]: /azure/traffic-manager/traffic-manager-overview