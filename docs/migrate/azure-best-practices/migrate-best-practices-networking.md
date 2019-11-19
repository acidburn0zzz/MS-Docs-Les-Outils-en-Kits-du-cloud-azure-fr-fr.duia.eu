---
title: Meilleures pratiques de configuration du réseau pour les charges de travail migrées vers Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Après une migration vers Azure, adoptez les meilleures pratiques pour apprendre à configurer le réseau pour vos charges de travail migrées.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: df31cb73ec601c52f0f925d09a56f0af7aaf1513
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565223"
---
# <a name="best-practices-to-set-up-networking-for-workloads-migrated-to-azure"></a>Meilleures pratiques de configuration du réseau pour les charges de travail migrées vers Azure

Lorsque vous envisagez et concevez un projet de migration, l’une des étapes les plus importantes, au-delà de la migration proprement dite, réside dans la conception et l’implémentation du réseau Azure. Cet article décrit les meilleures pratiques pour la mise en réseau lors d’une migration vers des implémentations IaaS et PaaS dans Azure.

> [!IMPORTANT]
> Les meilleures pratiques et opinions décrites dans cet article sont basées sur la plateforme Azure et les fonctionnalités disponibles au moment de la rédaction. Les fonctionnalités et les capacités changent au fil du temps. Il est possible que certaines recommandations ne s’appliquent pas à votre déploiement. Par conséquent, choisissez celles qui vous conviennent.

## <a name="design-virtual-networks"></a>Concevoir des réseaux virtuels

Azure fournit des réseaux virtuels (VNet) :

- Les ressources Azure communiquent entre elles en privé, directement et en toute sécurité via des réseaux virtuels.
- Vous pouvez configurer des connexions au point de terminaison sur des réseaux virtuels pour les machines virtuelles et les services qui requièrent une communication Internet.
- Il s’agit d’un isolement logique du cloud Azure dédié à votre abonnement.
- Vous pouvez implémenter plusieurs réseaux virtuels au sein de chaque abonnement et chaque région Azure.
- Chaque réseau virtuel est isolé des autres réseaux virtuels.
- Les réseaux virtuels peuvent contenir les adresses IP privées et publiques définies dans [RFC 1918](https://tools.ietf.org/html/rfc1918), exprimées en notation CIDR. Les adresses IP publiques spécifiées dans l’espace d’adressage d’un réseau virtuel ne sont pas directement accessibles à partir d’Internet.
- Les réseaux virtuels peuvent se connecter entre eux sur la base d’un peering de réseaux virtuels. Les réseaux virtuels connectés peuvent se trouver dans des régions identiques ou différentes. Par conséquent, les ressources d’un réseau virtuel peuvent se connecter aux ressources d’autres réseaux virtuels.
- Par défaut, les itinéraires Azure se chargent de l’acheminement entre les sous-réseaux d’un réseau virtuel, les réseaux virtuels connectés, les réseaux locaux et Internet.

Lorsque vous planifiez votre topologie de réseau virtuel, vous devez penser à la manière d’organiser les espaces d’adressage IP, d’implémenter un réseau hub-and-spoke, de segmenter les réseaux virtuels en sous-réseaux, de configurer le serveur DNS et d’implémenter les zones de disponibilité Azure.

## <a name="best-practice-plan-ip-addressing"></a>Meilleure pratique : Planifier l’adressage IP

Lorsque vous créez des réseaux virtuels dans le cadre de votre migration, il est important de planifier l’espace d’adressage IP de vos réseaux virtuels.

- Pour chaque réseau virtuel, vous devez attribuer un espace d’adressage qui ne dépasse pas une plage CIDR de /16. Les réseaux virtuels permettent d’utiliser 65 536 adresses IP, et le fait d’affecter un préfixe inférieur à /16 entraînerait une perte d’adresses IP. Il est important de ne pas gaspiller les adresses IP, même si elles se trouvent dans les plages privées définies par la RFC 1918.
- L’espace d’adressage de réseaux virtuels ne doit pas chevaucher les plages du réseau local.
- La traduction d’adresses réseau (NAT) ne doit pas être utilisée.
- Le chevauchement des adresses peut être à l’origine de problèmes de connexion aux réseaux et de dysfonctionnement du routage. Si des réseaux se chevauchent, vous devez reconcevoir le réseau ou utiliser la traduction d’adresses réseau (NAT).

**En savoir plus :**

- [Consultez une présentation](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) des réseaux virtuels Azure.
- [Lisez](https://docs.microsoft.com/azure/virtual-network/virtual-networks-faq) la FAQ relative à la mise en réseau.
- [Découvrez](https://docs.microsoft.com/azure/azure-subscription-service-limits?toc=%2fazure%2fvirtual-network%2ftoc.json#networking-limits) les limites de la mise en réseau.

## <a name="best-practice-implement-a-hub-and-spoke-network-topology"></a>Meilleure pratique : Implémenter une topologie de réseau hub-and-spoke

Une topologie de réseau hub-and-spoke isole des charges de travail tout en partageant des services tels que l’identité et la sécurité.

- Le hub est un réseau virtuel Azure qui agit comme point central de connectivité.
- Les spokes sont des réseaux virtuels qui se connectent au réseau virtuel du hub à l’aide d’un peering.
- Les services partagés sont déployés dans le hub, tandis que les charges de travail individuelles sont déployées en tant que rayons.

Tenez compte des éléments suivants :

- L’implémentation d’une topologie hub-and-spoke dans Azure permet de centraliser les services communs, tels que les connexions à des réseaux locaux, les pare-feu et l’isolation entre les réseaux virtuels. Le réseau virtuel du hub fournit un point central de connectivité aux réseaux locaux et offre un emplacement pour héberger des services utilisés par les charges de travail qui sont hébergées dans les réseaux virtuels spokes.
- La configuration hub-and-spoke est généralement utilisée par les grandes entreprises. Les réseaux plus modestes peuvent envisager une conception plus simple pour économiser sur les coûts et la complexité.
- Les réseaux virtuels spokes peuvent servir à isoler les charges de travail, chaque spoke étant géré séparément des autres spokes. Chaque charge de travail peut inclure plusieurs niveaux, avec plusieurs sous-réseaux connectés à l’aide d’équilibreurs de charge Azure.
- Les réseaux virtuels hub-and-spoke peuvent être implémentés dans des groupes de ressources différents, voire dans des abonnements différents. Quand vous appairez des réseaux virtuels de différents abonnements, les abonnements peuvent être associés au même locataire Azure Active Directory (Azure AD) ou à un locataire différent. Cela permet de décentraliser la gestion de chaque charge de travail, tout en partageant les services gérés dans le réseau hub.

![Gestion des changements](./media/migrate-best-practices-networking/hub-spoke.png)
*Topologie hub-and-spoke*

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/hub-spoke) sur la topologie hub-and-spoke.
- Obtenir des recommandations de réseau pour l’exécution de machines virtuelles [Windows](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/windows-vm) et [Linux](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/linux-vm) dans Azure.
- [En savoir plus](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) sur le peering de réseaux virtuels.

## <a name="best-practice-design-subnets"></a>Meilleure pratique : conception des sous-réseaux

Pour garantir une forme d’isolation à l’intérieur d’un réseau virtuel, vous devez le segmenter en un ou plusieurs sous-réseaux et allouer une partie de l’espace d’adressage du réseau virtuel à chaque sous-réseau.

- Vous pouvez créer plusieurs sous-réseaux au sein de chaque réseau virtuel.
- Par défaut, Azure achemine le trafic réseau entre tous les sous-réseaux dans un réseau virtuel.
- Vos décisions en matière de sous-réseau dépendent de vos exigences techniques et organisationnelles.
- Vous devez utiliser la notation CIDR pour créer des sous-réseaux.
- Lorsque vous décidez de la plage réseau de vos sous-réseaux, sachez qu’Azure conserve les cinq adresses IP de chaque sous-réseau qui ne peuvent pas être utilisées. Par exemple, si vous créez le plus petit sous-réseau disponible, soit /29 (avec huit adresses IP), Azure conservera cinq adresses ; autrement dit, vous ne disposerez que de trois adresses utilisables que vous pourrez assigner aux hôtes sur le sous-réseau.
- Dans la plupart des cas, il est recommandé d’utiliser /28 comme le plus petit sous-réseau.

**Exemple :**

Le tableau présente un exemple de réseau virtuel avec un espace d’adressage de 10.245.16.0/20 segmenté en sous-réseaux, dans le cadre d’une migration planifiée.

**Sous-réseau** | **CIDR** | **Adresses** | **Utilisation**
--- | --- | --- | ---
DEV-FE-EUS2 | 10.245.16.0/22 | 1019 | Machines virtuelles frontales/de couche web
DEV-APP-EUS2 | 10.245.20.0/22 | 1019 | Machines virtuelles de niveau application
DEV-DB-EUS2 | 10.245.24.0/23 | 507 | Machines virtuelles de base de données

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm#segmentation) sur la conception des sous-réseaux.
- [Découvrez comment](https://docs.microsoft.com/azure/migrate/contoso-migration-infrastructure) une société fictive (Contoso) a préparé son infrastructure réseau en vue d’une migration.

## <a name="best-practice-set-up-a-dns-server"></a>Meilleure pratique : sélection d’un serveur DNS

Azure ajoute par défaut un serveur DNS lorsque vous déployez un réseau virtuel. Cela vous permet de créer des réseaux virtuels et de déployer des ressources rapidement. Toutefois, ce serveur DNS fournit uniquement des services aux ressources qui se trouvent sur ce réseau virtuel. Si vous souhaitez connecter plusieurs réseaux virtuels entre eux, ou vous connecter à un serveur local à partir de réseaux virtuels, vous avez besoin de fonctionnalités de résolution de noms supplémentaires. Par exemple, vous devrez peut-être utiliser Active Directory pour résoudre les noms DNS entre des réseaux virtuels. Pour ce faire, vous devez déployer votre propre serveur DNS personnalisé dans Azure.

- Les serveurs DNS d’un réseau virtuel peuvent transférer des requêtes DNS vers le programme de résolution récursive dans Azure. Cela vous permet de résoudre les noms d’hôte au sein de ce réseau virtuel. Par exemple, un contrôleur de domaine exécuté dans Azure peut répondre aux requêtes DNS concernant ses propres domaines et transférer toutes les autres requêtes vers Azure.
- Le transfert DNS permet aux machines virtuelles de voir vos ressources locales (par le biais du contrôleur de domaine) et les noms d’hôte fournis par Azure (à l’aide du redirecteur). Les programmes de résolution récursive d’Azure sont accessibles via l’adresse IP virtuelle 168.63.129.16.
- Le transfert DNS permet aussi la résolution DNS entre réseaux virtuels et permet à vos ordinateurs locaux de résoudre les noms d’hôte fournis par Azure.
  - Pour résoudre le nom d’hôte d’une machine virtuelle, la machine virtuelle du serveur DNS doit résider dans le même réseau virtuel et être configurée pour rediriger les requêtes de nom d’hôte vers Azure.
  - Comme le suffixe DNS est différent dans chaque réseau virtuel, vous pouvez utiliser des règles de redirection conditionnelles pour envoyer les requêtes DNS au réseau virtuel approprié en vue de la résolution.
- Lorsque vous utilisez vos propres serveurs DNS, vous pouvez spécifier plusieurs serveurs DNS pour chaque réseau virtuel. Vous pouvez également spécifier plusieurs serveurs DNS par interface réseau (pour Azure Resource Manager) ou par service cloud (pour le modèle de déploiement classique).
- Les serveurs DNS spécifiés pour une interface réseau ou un service cloud ont la priorité sur les serveurs DNS spécifiés pour le réseau virtuel.
- Dans le modèle de déploiement Azure Resource Manager, vous pouvez spécifier des serveurs DNS pour un réseau virtuel et une interface réseau, mais la meilleure pratique consiste à utiliser le paramètre uniquement sur les réseaux virtuels.

    ![Serveurs DNS](./media/migrate-best-practices-networking/dns2.png) *Serveurs DNS pour un réseau virtuel*

**En savoir plus :**

- [En savoir plus sur](https://docs.microsoft.com/azure/migrate/contoso-migration-infrastructure) la résolution de noms lorsque vous utilisez votre propre serveur DNS.
- [En savoir plus sur](../../ready/azure-best-practices/naming-and-tagging.md) les règles et restrictions d’affectation de noms DNS.

## <a name="best-practice-set-up-availability-zones"></a>Meilleure pratique : Configurer des zones de disponibilité

Les zones de disponibilité augmentent la haute disponibilité de manière à protéger les applications et les données contre les défaillances de centre de données.

- Les Zones de disponibilité sont des emplacements physiques uniques au sein d’une région Azure.
- Chaque zone de disponibilité est composée d’un ou de plusieurs centres de données équipés d’une alimentation, d’un système de refroidissement et d’un réseau indépendants.
- Pour garantir la résilience, un minimum de trois zones distinctes sont activées dans toutes les régions.
- La séparation physique des zones de disponibilité dans une région protège les applications et les données des défaillances dans le centre de données.
- Les services redondants interzone répliquent vos applications et données entre des zones de disponibilité pour les protéger contre des points uniques de panne. - - Avec les zones de disponibilité, Azure propose des contrats de niveau de service qui garantissent une disponibilité des machines virtuelles de 99,99 %.

    ![Zone de disponibilité](./media/migrate-best-practices-networking/availability-zone.png) *Zone de disponibilité*

- Vous pouvez planifier et générer une haute disponibilité dans votre architecture de migration par la colocalisation de vos ressources de calcul, de stockage, de mise en réseau et de données dans une zone et une réplication de ces ressources dans d’autres zones. Les services Azure qui prennent en charge les zones de disponibilité sont classés en deux catégories :
  - Services zonaux : vous associez une ressource à une zone spécifique. Par exemple, machines virtuelles, disques managés, adresses IP.
  - Services redondants interzone : la ressource est automatiquement répliquée sur plusieurs zones. Par exemple, stockage redondant interzone, Azure SQL Database.
- Vous pouvez déployer une charge Azure standard équilibrée avec les charges de travail sur Internet ou les couches applicatives, pour assurer une tolérance de panne zonale.

    ![Équilibreur de charge](./media/migrate-best-practices-networking/load-balancer.png) *Équilibreur de charge*

**En savoir plus :**

- [Obtenir une vue d’ensemble](https://docs.microsoft.com/azure/availability-zones/az-overview) des zones de disponibilité.

## <a name="design-hybrid-cloud-networking"></a>Conception d’une mise en réseau de cloud hybride

Pour une migration réussie, il est essentiel de connecter les réseaux d’entreprise locaux à Azure. Ceci permet de créer une connexion permanente, appelée réseau de cloud hybride, dans laquelle les services sont fournis aux utilisateurs de l’entreprise depuis le cloud Azure. Il existe deux manières de créer ce type de réseau :

- **VPN de site à site :** la connexion de site à site est établie entre votre appareil VPN local compatible et une passerelle VPN Azure déployée dans un réseau virtuel. Les ressources locales autorisées peuvent alors accéder aux réseaux virtuels. Les communications de site à site sont envoyées via un tunnel chiffré sur Internet.
- **Azure ExpressRoute :** la connexion Azure ExpressRoute est établie entre votre réseau local et Azure via un partenaire ExpressRoute. Cette connexion est privée et le trafic ne passe par Internet.

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/vpn) sur la mise en réseau de cloud hybride.

## <a name="best-practice-implement-a-highly-available-site-to-site-vpn"></a>Meilleure pratique : implémentation d’un VPN de site à site à haute disponibilité

Pour implémenter un VPN de site à site, vous devez configurer une passerelle VPN dans Azure.

- Une passerelle VPN est un type spécifique de passerelle de réseau virtuel qui est utilisé pour envoyer du trafic chiffré entre un réseau virtuel Azure et un emplacement local via l’Internet public.
- Vous pouvez également utiliser des passerelles VPN pour envoyer du trafic chiffré entre les réseaux virtuels Azure sur le réseau Microsoft.
- Un réseau virtuel ne peut posséder qu’une seule passerelle VPN.
- Vous pouvez créer plusieurs connexions à la même passerelle VPN. Lorsque vous créez plusieurs connexions, tous les tunnels VPN partagent la bande passante de passerelle disponible.
- Chaque passerelle VPN Azure comprend deux instances dans une configuration de type actif / passif.
  - En cas de maintenance planifiée ou d’interruption non planifiée au niveau de l’instance active, l’instance de secours prend automatiquement le relais et reprend la connexion site à site ou la connexion entre deux réseaux virtuels.
  - Le basculement entraîne une brève interruption.
  - Dans le cadre d’une maintenance planifiée, la connectivité doit être restaurée dans les 10 à 15 secondes.
  - En cas de problèmes non planifiés, la récupération de la connexion est plus longue et peut atteindre 1 min 30 sec dans le pire des cas.
  - Les connexions client VPN point à site (P2S) à la passerelle seront interrompues et les utilisateurs devront se reconnecter à partir des ordinateurs clients.

Lorsque vous configurez un VPN de site à site, procédez comme suit :

- Vous avez besoin d’un réseau virtuel dont la plage d’adresses ne se chevauche pas avec le réseau local auquel se connecte le VPN.
- Vous devez créer un sous-réseau de passerelle dans le réseau.
- Vous devez créer une passerelle VPN, spécifier le type de passerelle (VPN) et indiquer si la passerelle est basée sur un routage ou sur une stratégie. Un VPN basé sur un routage est recommandé pour sa capacité et sa durabilité.
- Vous devez créer une passerelle de réseau local en local et configurer votre appareil VPN local.
- Vous devez créer une connexion de VPN de site à site de basculement entre la passerelle de réseau virtuel et l’appareil en local. L’utilisation d’un VPN basé sur un routage autorise les connexions actif/passif ou actif/actif vers Azure. Un VPN basé sur un routage prend également en charge simultanément les connexions site à site (depuis n’importe quel ordinateur) et point à site (depuis un seul ordinateur).
- Vous devez spécifier la référence SKU de la passerelle que vous souhaitez utiliser. Cela dépendra de vos besoins en charges de travail, de vos débits, de vos fonctionnalités et de vos contrats de niveau de service.
- Le protocole BGP (Border Gateway Protocol) est une fonctionnalité en option que vous pouvez utiliser avec Azure ExpressRoute et avec vos passerelles VPN basées sur un routage pour propager vos itinéraires BGP locaux sur vos réseaux virtuels.

![VPN](./media/migrate-best-practices-networking/vpn.png)
*VPN site à site*

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices) sur les appareils VPN locaux compatibles.
- [Obtenir une vue d’ensemble](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) des passerelles VPN.
- [En savoir plus](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable) sur les connexions VPN hautement disponibles.
- [En savoir plus](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-plan-design) sur la planification et la conception d’une passerelle VPN.
- [En savoir plus](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings#gwsku) sur les paramètres de la passerelle VPN.
- [En savoir plus](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#gwsku) sur les références SKU de passerelle.
- [En savoir plus](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-bgp-overview) sur la configuration de BGP avec les passerelles VPN Azure.

### <a name="best-practice-configure-a-gateway-for-vpn-gateways"></a>Meilleure pratique : configuration d’une passerelle pour les passerelles VPN

Lorsque vous créez une passerelle VPN dans Azure, vous devez utiliser un sous-réseau spécial nommé GatewaySubnet. Lorsque vous créez ce sous-réseau, tenez compte de ces meilleures pratiques :

- La longueur du préfixe du sous-réseau de passerelle peut avoir une longueur de préfixe maximale de 29 (par exemple, 10.119.255.248/29). Il est actuellement recommandé d’utiliser une longueur de préfixe de 27 (par exemple, 10.119.255.224/27).
- Lorsque vous définissez l’espace d’adressage du sous-réseau de passerelles, utilisez la toute dernière partie de l’espace d’adressage des réseaux virtuels.
- Lorsque vous utilisez Azure GatewaySubnet, ne déployez jamais vos machines virtuelles ou d’autres appareils tels qu’Application Gateway sur le sous-réseau de passerelles.
- N’affectez pas de groupe de sécurité réseau (NSG) à ce sous-réseau. Cela entraînerait une interruption de la passerelle.

**En savoir plus :**

- [Utilisez cet outil](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) pour déterminer votre espace d’adressage IP.

## <a name="best-practice-implement-azure-virtual-wan-for-branch-offices"></a>Meilleure pratique : implémentation d’Azure Virtual WAN pour les succursales

Dans le cas de plusieurs connexions VPN, le service réseau Azure Virtual WAN offre une connectivité de branche à branche optimisée et automatisée via Azure.

- Virtual WAN vous permet de vous connecter et de configurer des appareils de branche pour communiquer avec Azure. Cela peut se faire manuellement ou à l’aide d’appareils de fournisseur de votre choix via un Virtual WAN partenaire.
- L’utilisation d’appareils de fournisseur permet une utilisation facile, une meilleure connectivité et une bonne gestion de la configuration.
- Le tableau de bord intégré du WAN Azure fournit des informations de dépannage en temps réel qui peuvent vous faire gagner du temps et vous permettre de suivre en toute simplicité la connectivité de site à site à grande échelle.

**En savoir plus :** 
[En savoir plus](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about) sur Azure Virtual WAN.

### <a name="best-practice-implement-expressroute-for-mission-critical-connections"></a>Meilleure pratique : Implémentation d’ExpressRoute pour les connexions stratégiques

Le service Azure ExpressRoute étend votre infrastructure locale dans le cloud Microsoft en créant des connexions privées entre le centre de données virtuel Azure et des réseaux locaux.

- Les connexions ExpressRoute peuvent être établies sur un réseau universel (VPN IP), sur un réseau Ethernet point à point, ou via un fournisseur de connectivité. Elles ne transitent pas par l’Internet public.
- Les connexions ExpressRoute offrent une sécurité, une fiabilité et des vitesses supérieures (allant jusqu’à 10 Gbits/s), avec une latence constante.
- Le service ExpressRoute se révèle d’une grande utilité pour les centres de données virtuels, car les clients ExpressRoute peuvent bénéficier des règles de conformité associées aux connexions privées.
- Avec ExpressRoute Direct, vous pouvez vous connecter directement aux routeurs Microsoft à 100 Gbits/s si vous avez besoin d’une plus grande quantité de bande passante.
- ExpressRoute utilise le protocole BGP pour échanger des itinéraires entre des réseaux locaux, les instances Azure et les adresses publiques Microsoft.

Le déploiement de connexions ExpressRoute implique généralement la souscription d’un engagement auprès d’un fournisseur de services ExpressRoute. Pour un démarrage rapide, il convient généralement d’utiliser d’abord un VPN site à site pour établir la connectivité entre le centre de données virtuel et les ressources locales, puis d’effectuer une migration vers une connexion ExpressRoute lorsqu’une interconnexion physique avec votre fournisseur de services est établie.

**En savoir plus :**

- [Lire une présentation](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) d’ExpressRoute.
- [En savoir plus](https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about) sur ExpressRoute Direct.

### <a name="best-practice-optimize-expressroute-routing-with-bgp-communities"></a>Meilleure pratique : optimisation du routage ExpressRoute avec les communautés BGP

En présence de plusieurs circuits ExpressRoute, vous pouvez vous connecter à Microsoft par le biais de plusieurs chemins d’accès. Par conséquent, le routage peut ne pas être optimal et votre trafic peut emprunter un chemin d’accès plus long pour atteindre Microsoft ; Microsoft peut faire de même pour atteindre votre réseau. Plus le chemin d’accès réseau est long, plus la latence est élevée. La latence a un impact direct sur les performances d’application ainsi que sur l’expérience utilisateur.

**Exemple :**

Examinons un exemple :

- Vous disposez de deux bureaux aux États-Unis, un à Los Angeles et un à New York.
- Vos bureaux sont connectés sur un réseau étendu, qui peut être votre propre réseau principal ou le VPN IP de votre fournisseur de services.
- Vous avez deux circuits ExpressRoute également connectés sur le réseau étendu, l’un dans USA Ouest et l’autre dans USA Est. Vous avez bien évidemment deux chemins d’accès pour vous connecter au réseau Microsoft.

**Problème :**

Imaginez à présent que vous déployiez un service Azure (par exemple, Azure App Service) dans les régions USA Ouest et USA Est.

- Vous souhaitez que les utilisateurs de chaque bureau puissent accéder aux services Azure les plus proches pour bénéficier d’une expérience optimale.
- Vous voulez donc connecter les utilisateurs de Los Angeles à la région Azure USA Ouest et les utilisateurs de New York à la région Azure USA Est.
- Cela fonctionne pour les utilisateurs de la côte Est, mais pas pour ceux résidant sur la côte Ouest. Le problème est le suivant :
  - Sur chaque circuit ExpressRoute, nous publions les préfixes dans la région Azure USA Est (23.100.0.0/16) et dans la région Azure USA Ouest (13.100.0.0/16).
  - Sans connaître le préfixe associé à chaque région, les préfixes ne sont pas traités de manière différente.
  - Votre réseau WAN peut supposer que les deux préfixes sont plus proches de la région USA Est que de la région USA Ouest, et donc acheminer les utilisateurs des deux bureaux vers le circuit ExpressRoute de la région USA Est, ce qui influence négativement l’expérience des utilisateurs du bureau de Los Angeles.

![VPN](./media/migrate-best-practices-networking/bgp1.png)
*Connexion non optimisée par les communautés BGP*

**Solution :**

Pour optimiser le routage pour les utilisateurs des deux bureaux, vous devez savoir faire la différence entre le préfixe de la région Azure USA Ouest et celui de la région Azure USA Est. Vous pouvez encoder ces informations à l’aide des valeurs de communauté BGP.

- Vous affectez une valeur de communauté BGP unique à chaque région Azure. Par exemple, 12076:51004 pour USA Est et 12076:51006 pour USA Ouest.
- Maintenant que vous savez quel préfixe est associé à chaque région Azure, vous pouvez configurer un circuit ExpressRoute préférentiel.
- Étant donné que vous utilisez le protocole BGP pour échanger des informations de routage, vous pouvez utiliser les préférences locales du protocole BGP pour influencer le routage.
- Dans notre exemple, vous pouvez affecter, dans la région USA Ouest, une valeur de préférence locale supérieure à celle de la région USA Est (13.100.0.0/16) et vice-versa dans la région USA Est (23.100.0.0/16).
- Avec cette configuration, dès lors que les deux chemins d’accès à Microsoft sont disponibles, les utilisateurs de Los Angeles se connecteront à la région Azure USA Ouest à l’aide du circuit de l’ouest, et les utilisateurs de New York se connecteront à la région Azure USA Est à l’aide du circuit de l’est. Le routage est optimisé des deux côtés.

![VPN](./media/migrate-best-practices-networking/bgp2.png)
*Connexion optimisée par les communautés BGP*

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/expressroute/expressroute-optimize-routing) sur l’optimisation du routage.

## <a name="secure-vnets"></a>Réseaux virtuels sécurisés

Microsoft partage avec vous la responsabilité de la sécurisation des réseaux virtuels. Microsoft fournit de nombreuses fonctionnalités de mise en réseau, ainsi que des services conçus pour aider à sécuriser les ressources. Lorsque vous concevez la sécurité de réseaux virtuels, vous devez respecter les meilleures pratiques qui comprennent notamment l’implémentation d’un réseau de périmètre, l’utilisation de groupes de sécurité et de filtrage, la sécurisation de l’accès aux ressources et aux adresses IP, ou encore l’implémentation d’un mécanisme de protection contre les attaques.

**En savoir plus :**

- [Obtenir une vue d’ensemble](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices) sur les meilleures pratiques pour la sécurité réseau.
- [Découvrez comment](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm#security) concevoir des réseaux sécurisés.

## <a name="best-practice-implement-an-azure-perimeter-network"></a>Meilleure pratique : implémentation d’un réseau de périmètre Azure

Bien que Microsoft investisse fortement dans la protection de l’infrastructure cloud, vous devez également protéger vos services cloud et vos groupes de ressources. Une approche multicouche de la sécurité constitue la meilleure défense. La mise en place d’un réseau de périmètre constitue une partie importante de cette stratégie de défense.

- Un réseau de périmètre protège les ressources réseau internes d’un réseau non approuvé.
- Il représente la couche la plus éloignée exposée à Internet. Il se situe généralement entre Internet et l’infrastructure d’entreprise, avec généralement une certaine forme de protection des deux côtés.
- Dans une topologie de réseau d’entreprise classique, l’infrastructure centrale est puissamment fortifiée sur les périmètres, avec plusieurs couches d’appareils de sécurité. La limite de chaque couche se compose d’appareils et de points d’application de stratégies.
- Chaque couche peut comprendre une combinaison de solutions de sécurité réseau comprenant des pare-feu, la prévention DoS (Denial of Service), des systèmes IDS (détection d’intrusion) / IPS (protection contre les intrusions) et des appareils VPN.
- L’application de stratégies sur le réseau de périmètre peut prendre la forme de stratégies de pare-feu, de listes de contrôle d’accès (ACL) ou de routage spécifique.
- Puisque le trafic entrant arrive par Internet, il est intercepté et géré par diverses solutions de défense afin de bloquer les attaques et le trafic dangereux, tout en autorisant les demandes légitimes d’accès au réseau.
- Le trafic entrant peut être directement acheminé vers les ressources du réseau de périmètre. La ressource du réseau de périmètre peut ensuite communiquer davantage avec les autres ressources du réseau, en autorisant le trafic dans le réseau après validation.

La figure suivante montre un exemple de réseau de périmètre à sous-réseau unique dans un réseau d’entreprise, avec deux limites de sécurité.

![VPN](./media/migrate-best-practices-networking/perimeter.png)
*Déploiement d’un réseau de périmètre*

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) sur le déploiement d’un réseau de périmètre entre Azure et votre centre de données local.

## <a name="best-practice-filter-vnet-traffic-with-nsgs"></a>Meilleure pratique : filtrage du trafic de réseau virtuel avec des groupes de sécurité réseau

Les groupes de sécurité réseau (NSG) contiennent plusieurs règles de sécurité entrantes et sortantes qui filtrent le trafic entre des ressources. Le filtrage peut se faire par source et par adresse IP de destination, par port et par protocole.

- Les groupes de sécurité réseau contiennent des règles de sécurité qui autorisent ou refusent le trafic réseau entrant ou sortant en direction/à partir des différents types de ressources Azure. Pour chaque règle, vous pouvez spécifier la source et la destination, le port et le protocole.
- Les règles des groupes de sécurité réseau sont évaluées par priorité selon un tuple à cinq éléments (source, port source, destination, port de destination et protocole) pour autoriser ou refuser le trafic.
- Un enregistrement de flux est créé pour les connexions existantes. La communication est autorisée ou refusée en fonction de l’état de connexion de l’enregistrement de flux.
- Un enregistrement de flux permet de configurer un groupe de sécurité réseau avec état. Par exemple, si vous spécifiez une règle de sécurité sortante vers n’importe quelle adresse sur le port 80, il n’est pas nécessaire d’indiquer une règle de sécurité entrante pour la réponse au trafic sortant. Vous devez uniquement spécifier une règle de sécurité entrante si la communication est établie en externe.
- Le contraire est également vrai. Si le trafic entrant est autorisé sur un port, vous n’avez pas lieu de spécifier une règle de sécurité sortante pour répondre au trafic sur ce port.
- Les connexions existantes ne sont pas interrompues quand vous supprimez une règle de sécurité ayant activé le flux. Les flux de trafic sont interrompus quand les connexions sont arrêtées et qu’aucun trafic ne transite dans un sens ou dans l’autre pendant au moins quelques minutes.
- Lorsque vous créez des groupes de sécurité réseau, créez-en aussi peu que possible, mais autant que nécessaire.

### <a name="best-practice-secure-northsouth-and-eastwest-traffic"></a>Meilleure pratique : sécurisation du trafic nord/sud et est/ouest

Pour sécuriser des réseaux virtuels, il est important de prendre en compte les vecteurs d’attaque.

- L’utilisation seule de groupes de sécurité réseau simplifie votre environnement, mais sécurise uniquement le trafic sur votre sous-réseau. C’est ce que l’on appelle le trafic nord/sud.
- Le trafic entre des machines virtuelles sur le même sous-réseau est appelé « trafic est/ouest ».
- Il est important d’utiliser les deux formes de protection, de sorte que si un pirate parvient à accéder au trafic de l’extérieur, il puisse être intercepté lorsqu’il tente de se connecter à des ordinateurs situés dans le même sous-réseau.

### <a name="use-service-tags-on-nsgs"></a>Utiliser des balises de service sur les groupes de sécurité réseau

Une balise de service représente un groupe de préfixes d’adresses IP. L’utilisation d’une balise de service permet de réduire la complexité associée à la création de règles de groupes de sécurité réseau.

- Vous pouvez utiliser des balises de service à la place des adresses IP spécifiques lorsque vous créez des règles.
- Microsoft gère les préfixes d’adresse associés à une balise de service et met à jour automatiquement la balise de service quand les adresses changent.
- Vous ne pouvez pas créer votre propre balise de service, ni spécifier les adresses IP incluses dans une balise.

Les balises de service permettent d’automatiser l’attribution d’une règle à des groupes de services Azure. Par exemple, si vous souhaitez autoriser un sous-réseau de réseau virtuel dans lequel des serveurs web accèdent à une base de données Azure SQL, vous pouvez créer une règle de trafic sortant sur le port 1433 et utiliser la balise de service **Sql**.

- Cette balise **Sql** désigne les préfixes d’adresses des services Azure SQL Database et Azure SQL Data Warehouse.
- Si vous spécifiez **Sql** comme valeur, le trafic vers Sql est autorisé ou refusé.
- Si vous souhaitez uniquement autoriser l’accès à Sql dans une **région** spécifique, vous pouvez préciser cette région. Par exemple, si vous souhaitez autoriser l’accès à Azure SQL Database uniquement dans la région USA Est, vous pouvez spécifier **Sql.EastUS** comme balise de service.
- La balise représente le service, mais pas des instances du service. Par exemple, la balise représente le service Azure SQL Database, mais pas une base de données ou un serveur SQL spécifique.
- Tous les préfixes d’adresse représentés par cette balise sont également représentés par la balise **Internet**.

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/virtual-network/security-overview) sur les groupes de sécurité réseau.
- [En savoir plus](https://docs.microsoft.com/azure/virtual-network/security-overview#service-tags) sur les balises de service disponibles pour les groupes de sécurité réseau.

## <a name="best-practice-use-application-security-groups"></a>Meilleure pratique : utilisation de groupes de sécurité d’application

Les groupes de sécurité d’application vous permettent de configurer la sécurité réseau comme le prolongement naturel d’une structure d’application.

- Vous pouvez regrouper des machines virtuelles et définir des stratégies de sécurité réseau basés sur des groupes de sécurité d’application.
- Les groupes de sécurité d’application vous permettent de réutiliser votre stratégie de sécurité à grande échelle, sans maintenance manuelle d’adresses IP explicites.
- Les groupes de sécurité réseau gèrent la complexité des adresses IP explicites et plusieurs ensembles de règles, ce qui vous permet de vous concentrer sur la logique métier.

**Exemple :**

![Groupe de sécurité d’application](./media/migrate-best-practices-networking/asg.png)
*Exemple de groupe de sécurité d’application*

**Interface réseau** | **Groupe de sécurité d’application**
--- | ---
NIC1 | AsgWeb
NIC2 | AsgWeb
NIC3 | AsgLogic
NIC4 | AsgDb

- Dans notre exemple, chaque interface réseau appartient à un seul groupe de sécurité d’application, mais une interface peut en réalité appartenir à plusieurs groupes, dans les limites imposées par Azure.
- Aucune de ces interfaces réseau ne dispose d’un groupe de sécurité réseau associé. NSG1 est associé aux deux sous-réseaux et contient les règles suivantes.

<!--markdownlint-disable MD033 -->

**Nom de la règle** | **Objectif** | **Détails**
--- | --- | ---
Allow-HTTP-Inbound-Internet | Autoriser le trafic internet vers les serveurs web. Le trafic entrant à partir d’internet est refusé par la règle de sécurité par défaut DenyAllInbound, donc aucune règle supplémentaire n’est nécessaire pour les groupes de sécurité d’application AsgLogic ou AsgDb. | Priorité : 100<br/><br/> Source : Internet<br/><br/> Port source : *<br/><br/> Destination : AsgWeb<br/><br/> Port de destination : 80<br/><br/> Protocole : TCP<br/><br/> Accès : Autoriser.
Deny-Database-All | Étant donné que la règle de sécurité par défaut AllowVNetInBound autorise toutes les communications entre les ressources dans le même réseau virtuel, cette règle est nécessaire pour refuser le trafic à partir de toutes les ressources. | Priorité : 120<br/><br/> Source : *<br/><br/> Port source : *<br/><br/> Destination : AsgDb<br/><br/> Port de destination : 1433<br/><br/> Protocole : Tous<br/><br/> Accès : Refuser.
Allow-Database-BusinessLogic | Autoriser le trafic du groupe de sécurité d’application AsgLogic vers le groupe de sécurité d’application AsgDb. La priorité de cette règle est supérieure à la règle Deny-Database-All et est traitée en premier, c’est pourquoi le trafic en provenance du groupe de sécurité d’application AsgLogic est autorisé et tout autre trafic est bloqué. | Priorité : 110<br/><br/> Source : AsgLogic<br/><br/> Port source : *<br/><br/> Destination : AsgDb<br/><br/> Port de destination : 1433<br/><br/> Protocole : TCP<br/><br/> Accès : Autoriser.

<!--markdownlint-enable MD033 -->

- Les règles spécifiant un groupe de sécurité d’application en tant que source ou destination sont appliquées uniquement aux interfaces réseau qui sont membres du groupe de sécurité d’application. Si l’interface réseau n’est pas membre d’un groupe de sécurité d’application, la règle n’est pas appliquée à l’interface réseau, même si le groupe de sécurité réseau est associé au sous-réseau.

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/virtual-network/security-overview#application-security-groups) sur les groupes de sécurité d’application.

### <a name="best-practice-secure-access-to-paas-using-vnet-service-endpoints"></a>Meilleure pratique : sécurisation de l’accès aux services PaaS à l’aide de points de terminaison de service de réseau virtuel

Les points de terminaison de service de réseau virtuel étendent l’espace d’adressage IP et l’identité de votre réseau virtuel au service via une connexion directe.

- Les points de terminaison permettent de sécuriser les ressources critiques du service Azure pour vos réseaux virtuels uniquement. Le trafic à partir de votre réseau virtuel vers le service Azure reste toujours sur le réseau principal de Microsoft Azure.
- L’espace d’adressage privé VNet peut se recouper et ne permet donc pas d’identifier de façon unique le trafic en provenance d’un réseau virtuel.
- Une fois les points de terminaison de service activés dans votre réseau virtuel, vous pouvez sécuriser les ressources du service Azure en ajoutant une règle de réseau virtuel aux ressources du service. Ainsi, votre sécurité est améliorée grâce à la suppression complète de l’accès Internet public aux ressources et à l’autorisation du trafic uniquement à partir de votre réseau virtuel.

![Points de terminaison de service](./media/migrate-best-practices-networking/endpoint.png)
*Points de terminaison de service*

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) sur les points de terminaison de service de réseau virtuel.

## <a name="best-practice-control-public-ip-addresses"></a>Meilleure pratique : contrôle des adresses IP publiques

Les adresses IP publiques dans Azure peuvent être associées à des machines virtuelles, à des équilibreurs de charge, à des passerelles d’application et à des passerelles VPN.

- Les adresses IP publiques permettent aux ressources Internet de communiquer avec les ressources Azure et aux ressources Azure de communiquer avec Internet.
- Les adresses IP publiques sont créées avec une référence SKU de base ou standard, qui présentent plusieurs différences. Les références SKU standard peut être affectées à n’importe quel service, mais elles sont généralement configurées sur des machines virtuelles, des équilibreurs de charge et des passerelles d’application.
- Il est important de noter que, dans le cas d’une adresse IP publique de base, aucun groupe de sécurité réseau n’est configuré automatiquement. Vous devez configurer votre propre groupe et affecter des règles pour en contrôler l’accès. Les adresses IP standard se voient attribuer par défaut un groupe de sécurité réseau et des règles.
- Les meilleures pratiques consistent à ne pas configurer de machines virtuelles avec une adresse IP publique.
  - Si vous avez besoin d’un port ouvert, utilisez de préférence les ports dédiés aux services web, tels que les ports 80 ou 443.
  - L’accès aux ports de gestion à distance standard tels que SSH (22) et RDP (3389) doit être refusé, de même que tous les autres ports, à l’aide de groupes de sécurité réseau.
- L’idéal est de placer les machines virtuelles derrière un équilibreur de charge Azure ou une passerelle d’application. Si vous avez par la suite besoin d’un accès aux ports de gestion à distance, vous pouvez utiliser un accès juste-à-temps via Azure Security Center.

**En savoir plus :**

- [Adresses IP publiques dans Azure](https://docs.microsoft.com/azure/virtual-network/virtual-network-ip-addresses-overview-arm#public-ip-addresses)
- [Gérer l’accès juste-à-temps aux machines virtuelles](https://docs.microsoft.com/azure/security-center/security-center-just-in-time)

## <a name="take-advantage-of-azure-security-features-for-networking"></a>Tirer parti des fonctionnalités de sécurité Azure pour la mise en réseau

Azure propose des fonctionnalités de sécurité de plateforme simples d’utilisation, qui fournissent des moyens efficaces de contrer les attaques réseau courantes. Parmi ces fonctionnalités, citons le Pare-feu Azure, le pare-feu d’applications web et Network Watcher.

## <a name="best-practice-deploy-azure-firewall"></a>Meilleure pratique : déploiement du Pare-feu Azure

Pare-feu Azure est un service de sécurité réseau informatique et managé qui protège vos ressources de réseau virtuel. Il s’agit d’un pare-feu managé avec état intégral, doté d’une haute disponibilité intégrée et d’une extensibilité illimitée dans le cloud.

![Points de terminaison de service](./media/migrate-best-practices-networking/firewall.png)
*Pare-feu Azure*

- Le Pare-feu Azure peut créer, appliquer et consigner des stratégies de connectivité réseau et d’application de façon centralisée entre les abonnements et les réseaux virtuels.
- Le Pare-feu Azure utilise une adresse IP publique statique pour vos ressources de réseau virtuel, ce qui permet aux pare-feu situés à l’extérieur d’identifier le trafic provenant de votre réseau virtuel.
- Le Pare-feu Azure est totalement intégré à Azure Monitor pour la journalisation et les analyses.
- Lors de la création de règles de Pare-feu Azure, il est recommandé d’utiliser les balises FQDN pour créer des règles.
  - Une balise FQDN représente un groupe de noms de domaine complets (FQDN) associés à des services Microsoft bien connus.
  - Vous pouvez utiliser une balise FQDN pour autoriser le trafic sortant requis via votre pare-feu.
- Par exemple, pour autoriser manuellement le trafic Windows Update via votre pare-feu, vous devez créer plusieurs règles d’application. Les balises FQDN vous permettent de créer une règle d’application et d’inclure la balise Windows Update. Avec cette règle en place, le trafic réseau acheminé vers les points de terminaison Microsoft Windows Update peut traverser votre pare-feu.

**En savoir plus :**

- [Obtenir une vue d’ensemble](https://docs.microsoft.com/azure/firewall/overview) du Pare-feu Azure.
- [En savoir plus](https://docs.microsoft.com/azure/firewall/fqdn-tags) sur les balises FQDN.

## <a name="best-practice-deploy-a-web-application-firewall-waf"></a>Meilleure pratique : Déployer un pare-feu d’applications web (WAF)

Les applications Web sont de plus en plus la cible d’attaques malveillantes qui exploitent des vulnérabilités connues. L’injection de code SQL et les attaques de script site à site (XSS) sont des exemples d’attaques courantes. Empêcher ces attaques dans le code d’application peut se révéler difficile et nécessiter une maintenance rigoureuse, des mises à jour correctives ainsi que la surveillance au niveau de plusieurs couches de la topologie de l’application. Un pare-feu d’applications web centralisé facilite grandement la gestion de la sécurité et permet aux administrateurs de l’application de se protéger contre les menaces ou les intrusions. Un pare-feu d’applications web peut réagir plus rapidement à une menace de sécurité en corrigeant des vulnérabilités connues dans un emplacement central plutôt que de sécuriser individuellement les applications web. Les passerelles d’application existantes peuvent être facilement converties en une passerelle d’application avec un pare-feu d’applications web.

Le pare-feu d’applications web (WAF) est une fonctionnalité d’Azure Application Gateway.

- WAF protège de manière centralisée vos applications web contre les vulnérabilités et exploits courants.
- Cette fonctionnalité assure une protection sans modifier le code principal.
- Elle peut protéger plusieurs applications web en même temps derrière une passerelle d’application.
- WAF est intégré avec Azure Security Center.
- Vous pouvez personnaliser les règles de pare-feu d’applications Web et les groupes de règles en fonction des besoins de votre application.
- Il est recommandé d’utiliser un WAF devant une application accessible sur le web, y compris les applications hébergées sur des machines virtuelles Azure ou utilisées comme Azure App Service.

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/application-gateway/waf-overview) sur le pare-feu d’applications web.
- [En savoir plus](https://docs.microsoft.com/azure/application-gateway/application-gateway-waf-configuration) sur les limites et exclusions du pare-feu d’applications web.

## <a name="best-practice-implement-azure-network-watcher"></a>Meilleure pratique : implémentation d’Azure Network Watcher

Azure Network Watcher fournit des outils permettant de surveiller les ressources et les communications dans un réseau virtuel Azure. Par exemple, vous pouvez surveiller les communications entre une machine virtuelle et un point de terminaison (une autre machine virtuelle ou un FQDN, par exemple), afficher les ressources et leurs relations dans un réseau virtuel, ou diagnostiquer des problèmes de trafic réseau.

![Network Watcher](./media/migrate-best-practices-networking/network-watcher.png)
*Network Watcher*

- Network Watcher vous permet de superviser et diagnostiquer les problèmes réseau sans vous connecter à vos machines virtuelles.
- Vous pouvez déclencher la capture de paquets en définissant des alertes et bénéficiez d’un accès à des informations en temps réel sur le niveau de performance au niveau du paquet. Quand vous identifiez un problème, vous pouvez l’examiner en détail.
- Il est recommandé d’utiliser Network Watcher pour passer en revue les journaux de flux NSG.
  - Les journaux de flux NSG de Network Watcher permettent d’afficher des informations sur le trafic IP entrant et sortant via un groupe de sécurité réseau.
  - Ces journaux de flux sont écrits au format JSON.
  - Ils affichent les flux entrants et sortants en fonction de la règle, la carte réseau à laquelle le flux s’applique, des informations à 5 tuples sur le flux (IP source/de destination, port source/de destination, protocole), ainsi que l’autorisation ou le refus du trafic.

**En savoir plus :**

- [Obtenir une vue d’ensemble](https://docs.microsoft.com/azure/network-watcher) de Network Watcher.
- [En savoir plus](https://docs.microsoft.com/azure/network-watcher/network-watcher-nsg-flow-logging-overview) sur les journaux de flux du groupe de sécurité réseau.

## <a name="use-partner-tools-in-the-azure-marketplace"></a>Utiliser des outils partenaires dans la Place de marché Azure

Pour les topologies de réseau plus complexes, vous pouvez utiliser des produits de sécurité proposés par des partenaires de Microsoft, et notamment des appliances virtuelles réseau (NVA).

- Une NVA est une machine virtuelle qui exécute une fonction réseau, telle qu’un pare-feu, l’optimisation du WAN ou une autre fonction réseau.
- Les NVA renforcent la sécurité et les fonctions réseau du réseau virtuel. Elles peuvent être déployées pour différentes applications : les pare-feu à haute disponibilité, la prévention d’intrusion, la détection d’intrusion, les pare-feu d’applications web (WAF), l’optimisation WAN, le routage, l’équilibrage de charge, le VPN, la gestion des certificats, Active Directory et l’authentification multifacteur.
- Les appliances virtuelles réseau sont disponibles auprès de nombreux fournisseurs sur la  [Place de marché Azure](https://azuremarketplace.microsoft.com).

## <a name="best-practice-implement-firewalls-and-nvas-in-hub-networks"></a>Meilleure pratique : implémentation de pare-feu et d’appliances virtuelles réseau dans des réseaux hub

Dans le hub, le réseau de périmètre (disposant d’un accès à Internet) est normalement managé par le biais d’un pare-feu Azure, une batterie de pare-feu ou des pare-feu d’applications web (WAF). Voici un comparatif :

<!--markdownlint-disable MD033 -->

**Type de pare-feu** | **Détails**
--- | ---
WAF | Les applications web sont courantes et ont tendance à être sujettes à des vulnérabilités et à des attaques potentielles.<br/><br/> Les WAF sont conçues pour détecter les attaques contre les applications web (HTTP/HTTPS), d’une manière plus précise qu’avec un pare-feu générique.<br/><br/> Contrairement à la technologie de pare-feu classique, les WAF intègrent un ensemble de fonctionnalités spécifiques pour protéger les serveurs web internes contre les menaces.
Pare-feu Azure | Comme les batteries de pare-feu NVA, le Pare-feu Azure utilise un mécanisme d’administration commune et un ensemble de règles de sécurité pour protéger les charges de travail hébergées dans les réseaux spoke et pour contrôler l’accès aux réseaux locaux.<br/><br/> Le Pare-feu Azure dispose d’une extensibilité intégrée.
Pare-feu NVA | Comme le Pare-feu Azure, les batteries de pare-feu NVA utilisent un mécanisme d’administration commune et un ensemble de règles de sécurité pour protéger les charges de travail hébergées dans les réseaux spoke, et pour contrôler l’accès aux réseaux locaux.<br/><br/> Les pare-feu NVA peuvent être mis à l’échelle manuellement derrière un équilibreur de charge.<br/><br/> Bien qu’une batterie de pare-feu soit équipée de logiciels moins spécialisés qu’un WAF, elle dispose d’un plus vaste champ d’application permettant de filtrer et d’inspecter n’importe quel type de trafic en entrée et en sortie.<br/><br/> Les pare-feu NVA sont disponibles sur la Place de marché Azure.

<!--markdownlint-enable MD033 -->

Nous vous recommandons d’utiliser un ensemble de Pare-feu Azure (ou d’appliances virtuelles réseau) pour le trafic provenant d’Internet, et un autre ensemble pour le trafic émanant du niveau local.

- L’utilisation d’un seul ensemble de pare-feu pour ces deux types de trafics réseau constitue un risque pour la sécurité, car elle n’offre aucun périmètre de sécurité entre les deux.
- L’utilisation de couches de pare-feu distinctes simplifie la vérification des règles de sécurité et permet d’identifier clairement les règles auxquelles correspondent les différentes requêtes réseau entrantes.

**En savoir plus :**

- [En savoir plus](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) sur l’utilisation d’appliances virtuelles réseau dans un réseau virtuel Azure.

## <a name="next-steps"></a>Étapes suivantes

Passez en revue d’autres meilleures pratiques :

- [Meilleures pratiques](./migrate-best-practices-security-management.md) relatives à la sécurité et à la gestion après la migration.
- [Meilleures pratiques](./migrate-best-practices-costs.md) relatives à la gestion des coûts après la migration.
