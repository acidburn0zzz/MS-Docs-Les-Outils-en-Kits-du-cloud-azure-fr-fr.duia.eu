---
title: 'Centre de données virtuel : perspective réseau'
description: Utilisez le Cloud Adoption Framework pour Azure pour savoir comment utiliser Azure afin d'étendre en toute transparence votre infrastructure dans le cloud et de créer des architectures à plusieurs niveaux.
author: tracsman
ms.author: jonor
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: reference
manager: rossort
ms.custom: virtual-network
ms.openlocfilehash: c27ab20e703ae8ef37fcfba1a2d3f4585d2832da
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219391"
---
<!-- docsTest:disable -->
<!-- cSpell:ignore tracsman jonor rossort NVAs iptables WAFs DDOS ITSM LLAP anycast vwan -->

# <a name="the-virtual-datacenter-a-network-perspective"></a>Centre de données virtuel : perspective réseau

Les applications migrées à partir d’un emplacement local tirent parti de l’infrastructure économique sécurisée d’Azure, même avec un minimum de modifications d’application. Cela étant, les entreprises sont invitées à adapter leurs architectures pour améliorer l’agilité et tirer parti des fonctionnalités d’Azure.

Microsoft Azure offre des services et une infrastructure hyperscale avec des fonctionnalités et une fiabilité de qualité professionnelle. De par les nombreuses options de connectivité hybride proposées, les clients peuvent accéder aux services et à l’infrastructure au moyen d'Internet ou d’une connexion réseau privée. Les partenaires Microsoft peuvent également offrir des fonctionnalités améliorées en proposant des services de sécurité et des appliances virtuelles optimisées pour s’exécuter dans Azure.

Les clients peuvent étendre leur infrastructure dans le cloud et créer des architectures multiniveaux en toute transparence.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-a-virtual-datacenter"></a>Qu’est-ce qu’un centre de données virtuel ?

Le cloud a débuté en tant que plateforme destiné à héberger des applications publiques. Petit à petit, les entreprises ont compris la valeur du cloud et ont commencé à migrer des applications métier internes. Ces applications ont fait apparaître des considérations supplémentaires en matière de sécurité, de fiabilité, de performance et de coût impliquant plus de flexibilité en termes de prestation de services cloud. De nouveaux services liés à l’infrastructure et au réseau ont vu le jour pour accroître cette flexibilité et de nouvelles fonctionnalités de mise à l’échelle élastique, de reprise d’activité après sinistre et autres, ont été proposées.

Dans un premier temps, les solutions cloud été conçues pour héberger des applications uniques et relativement isolées dans le domaine public. Cette approche a donné de bons résultats pendant quelques années. Les avantages des solutions cloud sont ensuite devenus évidents, et plusieurs charges de travail à grande échelle ont été hébergées dans le cloud. Il s’est révélé crucial de résoudre les problèmes de sécurité, de fiabilité, de performances et de coûts des déploiements dans une ou plusieurs régions sur l’ensemble du cycle de vie du service cloud.

Dans l’exemple de diagramme de déploiement cloud ci-dessous, la zone rouge met en évidence une faille de sécurité. La zone jaune indique la possibilité d’optimiser les appliances virtuelles réseau dans les charges de travail.

![0][0]

Les centres de données virtuels offrent aux charges de travail d'entreprise la mise à l’échelle dont elles ont besoin. Cette mise à l’échelle doit relever les défis liés à l’exécution d’applications à grande échelle dans le cloud public.

Une implémentation de centre de données virtuel (VDC) s'étend au-delà des charges de travail d’application dans le cloud. Elle offre notamment une infrastructure de réseau, de sécurité et de gestion comme les services DNS et Active Directory. À mesure que les entreprises migrent de nouvelles charges de travail vers Azure, elles doivent réfléchir à l’infrastructure et aux objets qui prennent en charge ces charges de travail. Structurer avec soin les ressources permet d'éviter la prolifération de centaines d’îlots de charge de travail gérés séparément, avec des flux de données, des modèles de sécurité et des problèmes de conformité indépendants.

Le concept de centre de données virtuel fournit des recommandations et des conceptions de haut niveau à des fins d'implémentation d’une collection d’entités distinctes mais liées. Ces entités présentent souvent des fonctionnalités et une infrastructure de prise en charge communes. La visualisation de vos charges de travail sous forme de centre de données virtuel vous permet d’alléger les coûts grâce aux économies d’échelle, à l’optimisation de la sécurité par le biais de la centralisation des composants et des flux de données, ainsi qu’à la simplification des opérations, de la gestion et des audits de conformité.

> [!NOTE]
> Un centre de données virtuel n'est **pas** un service Azure spécifique. Il combine plusieurs fonctionnalités Azure pour répondre à vos besoins. Un centre de données virtuel est un moyen d’utiliser vos charges de travail et Azure pour optimiser vos ressources et fonctionnalités dans le cloud. Il offre une approche modulaire permettant de fournir des services informatiques dans Azure, tout en respectant les rôles et les responsabilités au sein de l’organisation.

Un centre de données virtuel aide les entreprises à déployer des charges de travail et des applications vers Azure dans les scénarios suivants :

- Héberger plusieurs charges de travail liées
- Migrer les charges de travail d’un environnement local vers Azure
- Implémenter les exigences de gestion partagée ou centralisée de la sécurité et des accès dans l’ensemble des charges de travail
- Combiner de manière appropriée DevOps et la centralisation des services informatiques pour une grande entreprise

## <a name="who-should-implement-a-virtual-datacenter"></a>Qui doit implémenter un centre de données virtuel ?

Tout client ayant décidé d’adopter Azure peut tirer parti de l'efficacité découlant de la configuration d’un ensemble de ressources mises en commun par toutes les applications. En fonction de la taille du projet, même les applications individuelles peuvent s'appuyer sur les modèles et les composants utilisés pour générer une implémentation de centre de données virtuel.

Certaines organisations disposent d'équipes ou de services centralisés pour l’informatique, la mise en réseau, la sécurité ou la conformité. L’implémentation d’un centre de données virtuel peut faciliter l'application de points de stratégie, séparer les responsabilités et garantir la cohérence des composants communs sous-jacents. Les équipes d’application conservent la liberté et le contrôle dont elles ont besoin.

Les organisations qui suivent une approche DevOps peuvent également utiliser les concepts de centre de données virtuel pour fournir des poches autorisées de ressources Azure. Cette méthode offre aux groupes DevOps l’assurance qu’ils disposent d’un contrôle total au sein de ce groupe, au niveau de l'abonnement ou dans les groupes de ressources d'un abonnement commun. Dans le même temps, les limites relatives au réseau et à la sécurité restent conformes à la définition d’une stratégie centralisée dans un réseau de hubs et un groupe de ressources gérée de manière centralisée.

## <a name="considerations-for-implementing-a-virtual-datacenter"></a>Considérations relatives à l’implémentation d’un centre de données virtuel

Lors de la conception d’un centre de données virtuel, prenez en compte les points cruciaux suivants :

### <a name="identity-and-directory-service"></a>Services d’identité et d’annuaire

Les services d’identité et d’annuaire constituent des fonctionnalités clés des centres de données locaux et dans le cloud. La notion d’identité couvre tous les aspects des accès et des autorisations vis-à-vis des services au sein d’une implémentation de centre de données virtuel. Pour garantir que seuls les utilisateurs et processus autorisés auront accès à vos ressources Azure, Azure utilise plusieurs types d’informations d’identification pour l’authentification, mots de passe de compte, clés de chiffrement, signatures numériques et certificats notamment. [Azure Multi-Factor Authentication][multi-factor-authentication] offre une couche de sécurité supplémentaire pour accéder aux services Azure moyennant une authentification forte avec diverses options de vérification simples (appel téléphonique, SMS ou notification d’application mobile) permettant aux clients de choisir leur méthode préférée.

Toute grande entreprise doit définir un processus de gestion d’identité qui décrit la gestion des différentes identités, leur authentification, ainsi que les autorisations, rôles et privilèges au sein du centre de données virtuel. Ce processus doit avoir pour fonction d’améliorer la sécurité et la productivité tout en réduisant les coûts, les temps d’arrêt et les tâches manuelles répétitives.

Les entreprises/organisations peuvent nécessiter une combinaison de services complexe pour différents métiers, et les employés assument fréquemment plusieurs rôles lorsqu’ils sont impliqués dans divers projets. Le VDC nécessite une coopération satisfaisante entre les différentes équipes, chacune ayant un rôle spécifique, afin de garantir le bon fonctionnement des systèmes avec une gouvernance adéquate. La matrice des responsabilités, des accès et des droits peut se révéler complexe. La gestion des identités dans le centre de données virtuel est implémentée par le biais d’[Azure Active Directory (Azure AD)][azure-ad] et du contrôle d’accès en fonction du rôle (RBAC).

Un service d’annuaire est une infrastructure d’informations partagée qui permet de localiser, de gérer, d’administrer et d’organiser les éléments et ressources réseau utilisés quotidiennement. Ces ressources peuvent inclure des volumes, des dossiers, des fichiers, des imprimantes, des utilisateurs, des groupes, des appareils et d’autres objets. Chacune des ressources du réseau est considérée comme un objet par le serveur d’annuaire. Les informations concernant une ressource sont stockées sous la forme d’une collection d’attributs associée à cette ressource ou à cet objet.

Tous les services professionnels Microsoft Online utilisent Azure Active Directory (Azure AD) pour l’authentification et les autres besoins d’identification. Azure Active Directory est une solution cloud complète et hautement disponible de gestion des identités et des accès qui associe des services d'annuaire principaux, une gouvernance avancée des identités et la gestion de l'accès aux applications. Il est possible d’intégrer Azure AD au service Active Directory local afin d’autoriser l’authentification unique pour toutes les applications cloud et hébergées localement. Les attributs utilisateur du service Active Directory local peuvent être automatiquement synchronisés avec Azure AD.

Il n’est pas nécessaire qu’un seul administrateur général affecte toutes les autorisations dans une implémentation de VDC. À la place, chaque service d’entreprise spécifique, groupe d’utilisateurs ou service dans le service d’annuaire peut disposer des autorisations nécessaires pour gérer ses propres ressources dans une implémentation de VDC. La structuration des autorisations doit être équilibrée. En effet, un nombre d’autorisations excessif risque de compromettre les performances, tandis que des autorisations insuffisantes ou trop flexibles sont susceptibles d’accroître les risques pour la sécurité. Le contrôle d’accès en fonction du rôle Azure (RBAC) contribue à résoudre ce problème en offrant une gestion affinée des accès aux ressources dans une implémentation de centre de données virtuel.

### <a name="security-infrastructure"></a>Infrastructure de sécurité

L’infrastructure de sécurité fait référence à la répartition du trafic dans le segment réseau virtuel spécifique d’une implémentation de VDC. Cette infrastructure spécifie la manière dont les flux d’entrée et de sortie sont contrôlés dans une implémentation de centre de données virtuel. Azure repose sur une architecture multi-locataire qui empêche le trafic non autorisé et accidentel entre les déploiements au moyen de l’isolation du réseau virtuel, de listes de contrôles d’accès, d’équilibreurs de charge, de filtres IP et de stratégies de flux de trafic. La traduction d’adresses réseau (NAT) sépare le trafic réseau interne du trafic externe.

La structure Azure alloue des ressources d’infrastructure aux charges de travail des locataires et gère les communications à destination et en provenance des machines virtuelles. L’hyperviseur Azure applique la séparation de mémoire et de processus entre les machines virtuelles, et route en toute sécurité le trafic réseau vers les locataires du système d’exploitation invité.

### <a name="connectivity-to-the-cloud"></a>Connectivité avec le cloud

Un centre de données virtuel nécessite une connectivité aux réseaux externes pour offrir des services aux clients, aux partenaires ou aux utilisateurs internes. Il est donc nécessaire d’avoir une connectivité non seulement à Internet, mais aussi aux réseaux et centres de données locaux.

Les clients contrôlent les différents accès vers et depuis les services à partir de l’Internet public. Ces accès sont contrôlés via le [Pare-feu Azure][AzFW] ou d’autres types de NVA (appliance virtuelle réseau). Ils contrôlent également les stratégies de routage personnalisées à l’aide de [routes définies par l’utilisateur][UDR] ainsi que le filtrage réseau à l’aide de[ groupes de sécurité réseau][NSG]. Nous recommandons de protéger également les ressources Internet via le service [Azure DDoS Protection Standard][DDoS].

Les entreprises peuvent avoir besoin de connecter leur centre de données virtuel à des centres de données locaux ou à d’autres ressources. Cette connectivité entre Azure et les réseaux locaux est un aspect essentiel de la conception d’une architecture efficace. Pour créer cette interconnexion, les entreprises disposent de deux méthodes : transit par le biais d’Internet ou par des connexions directes privées.

Un [VPN de site à site Azure][VPN] connecte des réseaux locaux à votre centre de données virtuel dans Azure. Le lien est établi via des connexions chiffrées sécurisées (tunnels IPsec). Les connexions VPN de site à site Azure sont flexibles, rapides à créer et n'impliquent généralement pas l'achat de matériel supplémentaire. S'appuyant sur les protocoles standard de l’industrie, la plupart des périphériques réseau actuels peuvent créer des connexions VPN à Azure via Internet ou des chemins de connectivité existants.

[ExpressRoute][ExR] permet des connexions privées entre votre centre de données virtuel et tous les réseaux locaux. Les connexions ExpressRoute ne sont pas établies par l’intermédiaire du réseau public Internet et offrent un surcroît de sécurité et de fiabilité et des débits supérieurs (jusqu’à 100 Gbits/s), ainsi qu’une latence constante. ExpressRoute offre les avantages des règles de conformité associées aux connexions privées. Avec [ExpressRoute Direct][ExRD], vous pouvez vous connecter directement aux routeurs Microsoft à 10 ou 100 Gbits/s.

Le déploiement de connexions ExpressRoute implique généralement la souscription d’un engagement auprès d’un fournisseur de services ExpressRoute (à l'exception d'ExpressRoute Direct). Les clients qui doivent être opérationnels rapidement commencent généralement par utiliser un VPN site à site pour établir la connectivité entre un centre de données virtuel et des ressources locales. Une fois votre l’interconnexion physique avec le fournisseur de services achevée, migrez la connectivité vers votre connexion ExpressRoute.

En cas de très nombreuses connexions VPN ou ExpressRoute, le service réseau [Azure Virtual WAN][virtual-wan] offre une connectivité de branche à branche optimisée et automatisée par le biais d’Azure. Le WAN virtuel vous permet de vous connecter et de configurer des appareils de branche pour communiquer avec Azure. Vous pouvez effectuer cette connexion et cette configuration manuellement ou à l’aide d’appareils de fournisseurs favoris par le biais d’un partenaire Virtual WAN. L’utilisation d’appareils de fournisseurs favoris permet une utilisation facile, une simplification de la connectivité et une gestion de la configuration. Le tableau de bord intégré du WAN Azure fournit des informations de dépannage en temps réel qui peuvent vous faire gagner du temps et vous permettre d’afficher en toute simplicité la connectivité de site à site à grande échelle. Virtual WAN fournit également des services de sécurité avec Pare-feu Azure et Firewall Manager (en option) dans votre hub Virtual WAN.

### <a name="connectivity-within-the-cloud"></a>Connectivité au sein du cloud

Les [réseaux virtuels Azure][virtual-network] et le [peering de réseaux virtuels][virtual-network-peering] sont les composants réseau de base d'un centre de données virtuel. Un réseau virtuel garantit une limite d’isolement pour les ressources de centre de données virtuel. Le peering permet l’intercommunication entre différents réseaux virtuels au sein de la même région Azure, entre les régions, voire entre les réseaux dans différents abonnements. À l’intérieur et entre les réseaux virtuels, les flux de trafic peuvent être contrôlés moyennant des règles de sécurité spécifiées dans des [groupes de sécurité réseau][NSG], des stratégies de pare-feu ([Pare-feu Azure][AzFW] ou[appliances virtuelles réseau][NVA]) et des [itinéraires définis par l’utilisateur][UDR] personnalisés.

Les réseaux virtuels sont également des points d’ancrage à des fins d'intégration de produits Azure de type plateforme en tant que service (PaaS) comme [Stockage Azure][Storage], [Azure SQL][SQL] et d’autres services publics intégrés dotés de points de terminaison publics. Les [points de terminaison de service][ServiceEndpoints] et [Azure Private Link][PrivateLink] vous permettent d'intégrer vos services publics à votre réseau privé. Vous pouvez même rendre vos services publics privés, tout en bénéficiant des avantages des services PaaS gérés par Azure.

## <a name="virtual-datacenter-overview"></a>Vue d’ensemble du centre de données virtuel

### <a name="topologies"></a>Topologies

Un centre de données virtuel peut être créé à l’aide de l’une de ces topologies de haut niveau, en fonction de vos besoins et exigences de mise à l’échelle :

Dans une topologie _plate_, toutes les ressources sont déployées dans un même réseau virtuel. Les sous-réseaux permettent le contrôle et la ségrégation des flux.

![11][11]

Dans une topologie _maillée_, le peering de réseaux virtuels connecte tous les réseaux virtuels directement entre eux.

![12][12]

Une topologie _hub-and-spoke peering_ convient parfaitement aux applications distribuées et aux équipes dotées de responsabilités déléguées.

![13][13]

Une topologie _Azure Virtual WAN_ peut prendre en charge les scénarios de bureaux distants à grande échelle et les services WAN globaux.

![14][14]

Les topologies hub-and-spoke peering et Azure Virtual WAN relèvent toutes deux d'une conception hub-and-spoke optimale en termes de communication, de ressources partagées et de stratégie de sécurité centralisée. Les hubs reposent sur un hub de peering de réseaux virtuels (désigné par `Hub Virtual Network` dans le diagramme) ou d’un hub Virtual WAN (désigné par `Azure Virtual WAN` dans le diagramme). Azure Virtual WAN est conçu pour les communications de branche à branche et de branche à Azure à grande échelle, ou pour éviter la complexité découlant de la création de tous les composants individuellement dans un hub de peering de réseaux virtuels. Dans certains cas, il vous faudra peut-être imposer une conception de hub de peering de réseaux virtuels, si des appliances virtuelles réseau sont requises dans le hub, par exemple.

Dans ces deux topologies Hub and Spoke, le hub correspond à la zone réseau centrale qui contrôle et inspecte le trafic entre différentes zones : Internet, le réseau local et les rayons. La topologie hub-and-spoke aide le service informatique à appliquer de manière centralisée les stratégies de sécurité. Elle réduit également les risques de configuration incorrecte et d’exposition.

Le concentrateur contient généralement les composants de service communs consommés par les rayons. Voici des exemples de services centraux usuels :

- Infrastructure Windows Active Directory, nécessaire à l’authentification utilisateur des tiers qui souhaitent accéder aux charges de travail du rayon à partir de réseaux non approuvés. Elle inclut les services de fédération Active Directory (AD FS) associés.
- Un service DNS (Distributed Name System) destiné à résoudre le nommage pour la charge de travail dans les rayons et permettant d’accéder aux ressources locales et sur Internet si le service [Azure DNS][DNS] n’est pas utilisé.
- Infrastructure à clé publique (PKI) permettant d’implémenter l’authentification unique sur les charges de travail.
- Contrôle de flux du trafic TCP et UDP entre les zones du réseau à rayons et Internet.
- Contrôle de flux entre les rayons et les ressources locales.
- Si nécessaire, contrôle de flux entre un rayon et un autre.

Un centre de données virtuel réduit le coût global au moyen de l’infrastructure de hub partagé entre plusieurs rayons.

Le rôle de chaque rayon peut consister à héberger différents types de charges de travail. Les rayons offrent également une approche modulaire pour les déploiements renouvelables des mêmes charges de travail. C’est le cas, par exemple, des phases de développement et de test, de tests d’acceptation utilisateur, de préproduction et de production. Les rayons permettent également de séparer et d’activer différents groupes au sein de votre organisation. Les groupes DevOps en sont un exemple. À l’intérieur d’un spoke, il est tout aussi possible de déployer une charge de travail de base que des charges de travail multiniveaux complexes avec un contrôle du trafic entre les différents niveaux.

### <a name="subscription-limits-and-multiple-hubs"></a>Limites d’abonnement et concentrateurs multiples

> [!IMPORTANT]
> Selon la taille de vos déploiements Azure, une stratégie à plusieurs hubs peut s'avérer nécessaire. Lorsque vous concevez votre stratégie hub-and-spoke, posez-vous les questions suivantes : cette conception peut-elle être mise à l'échelle pour prendre en charge plusieurs régions ? Il est nettement préférable de planifier une conception capable d'évoluer et de ne pas devoir y recourir que l'inverse.
>
> Le moment où procéder à une mise à l'échelle vers un hub secondaire (ou plus) dépend de plusieurs facteurs, reposant généralement sur les limites inhérentes à la mise à l'échelle. Lors d'une conception avec mise à l'échelle, veillez à examiner les [limites][limits] en termes d'abonnement, de réseau virtuel et de machine virtuelle.

Dans Azure, chacun des composants, quel qu’en soit le type, est déployé dans un abonnement Azure. L’isolement des composants Azure dans différents abonnements Azure peut satisfaire aux exigences de différents métiers, telles que la configuration de niveaux différenciés d’accès et d’autorisation.

Une implémentation de centre de données virtuel peut effectuer un scale-up pour atteindre un grand nombre de rayons ; toutefois, à l’instar de chaque système informatique, il existe des limites liées à la plateforme. Le déploiement du hub est lié à un abonnement Azure spécifique, qui comporte des restrictions et des limites (par exemple, un nombre maximum de peering de réseaux virtuels). Pour plus d’informations, consultez [Abonnement Azure et limites, quotas et contraintes de service][limits].) Dans les cas où ces limites peuvent poser problème, il est possible de procéder à la montée en puissance de l’architecture en faisant évoluer un modèle hub-and-spoke unique vers un cluster constitué de plusieurs concentrateurs et rayons. Plusieurs hubs dans une ou plusieurs régions Azure peuvent être connectés à l’aide du peering de réseaux virtuels, d’ExpressRoute, de Virtual WAN ou d’un VPN site à site.

![2][2]

L’introduction de plusieurs hubs augmente les efforts liés au coût et à la gestion du système. Cela se justifie uniquement en raison de l’extensibilité, les limites système, la redondance et la réplication régionale pour le niveau de performance des utilisateurs ou la récupération d’urgence. Dans les scénarios qui nécessitent plusieurs concentrateurs, ces derniers doivent tous, dans la mesure du possible, offrir le même ensemble de services afin d’en faciliter l’exploitation.

### <a name="interconnection-between-spokes"></a>Interconnexion entre les rayons

Il est possible d’implémenter des charges de travail multiniveau complexes à l’intérieur d’un même rayon ou d'une conception de réseau à plat. Les configurations multiniveau peuvent être implémentées à l’aide de sous-réseaux, un pour chaque niveau, ou d'applications dans le même réseau virtuel. Le contrôle et le filtrage du trafic s’effectuent à l’aide des groupes de sécurité réseau et des itinéraires définis par l’utilisateur.

Un architecte peut vouloir déployer une charge de travail multiniveau sur plusieurs réseaux virtuels. Avec le peering de réseaux virtuels, vous pouvez connecter des rayons à d’autres rayons du même hub ou de hubs distincts. Ce scénario s’applique généralement aux cas où les serveurs de traitement d’application sont situés dans un même rayon ou réseau virtuel. La base de données est déployée sur un autre rayon ou réseau virtuel. Dans ce cas, il est facile d’interconnecter les rayons avec le peering de réseaux virtuels et ce faisant, d’éviter le transit via le hub. Toutefois, il convient d’étudier avec soin l’architecture et la sécurité pour vérifier que le contournement du hub n’élude pas de points de sécurité ou d’audit importants susceptibles d’exister uniquement dans le hub.

![3][3]

Il est également possible d’interconnecter des rayons à un rayon jouant le rôle de concentrateur. Cette approche crée une hiérarchie à deux niveaux : le spoke du niveau supérieur (niveau 0) devient le hub de spokes inférieurs (niveau 1) dans la hiérarchie. Les rayons d’une implémentation de centre de données virtuel doivent transférer le trafic vers le hub central pour que le trafic puisse atteindre sa destination sur le réseau local ou l’Internet public. Une architecture à deux niveaux de hubs introduit un routage complexe qui supprime les avantages d’une relation hub-and-spoke simple.

Bien qu’Azure autorise des topologies complexes, les deux principes fondamentaux du concept de VDC sont la répétabilité et la simplicité. Pour réduire l’effort de gestion, la conception d’une topologie hub-and-spoke simple est l’architecture de référence que nous recommandons pour un VDC.

### <a name="components"></a>Components

Le centre de données virtuel est constitué de quatre types de composant de base : l’**infrastructure**, les **réseaux de périmètre**, les **charges de travail** et la **supervision**.

Chaque type de composant intègre plusieurs ressources et fonctionnalités Azure. Votre implémentation de VDC est constituée d’instances de plusieurs types de composants et de diverses variantes du même type de composant. Par exemple, vous pouvez disposer de nombreuses instances de charge de travail distinctes, séparées de façon logique, qui représentent différentes applications. Utilisez ces différents types de composants et instances afin de générer le VDC.

![4][4]

L’architecture conceptuelle de haut niveau du VDC ci-dessus représente différents types de composants utilisés dans diverses zones de la topologie hub-and-spoke. Le diagramme illustre les composants d’infrastructure dans les différentes parties de l’architecture.

En général, une bonne pratique consiste à baser les droits d’accès et les privilèges sur un groupe. Utilisez des groupes, plutôt que des utilisateurs individuels, pour maintenir une gestion cohérente des stratégies d’accès entre les équipes et réduire les erreurs de configuration. L’attribution et la suppression d’utilisateurs dans les groupes appropriés facilitent l’actualisation continue des privilèges d’un utilisateur spécifique.

Chaque groupe de rôles doit avoir un préfixe unique pour ses noms. Ce préfixe permet d’identifier facilement le groupe associé à une charge de travail spécifique. Par exemple, une charge de travail hébergeant un service d’authentification peut être associée à des groupes appelés **AuthServiceNetOps**, **AuthServiceSecOps**, **AuthServiceDevOps** et **AuthServiceInfraOps**. Les rôles centralisés ou les rôles non associés à un service spécifique peuvent être précédés de **Corp**. Exemple : **CorpNetOps**.

De nombreuses organisations utilisent une variante des groupes ci-après pour procéder à une répartition générale des rôles :

- Le groupe du service informatique central, **Corp,** , détient les droits de propriété permettant de contrôler les composants d’infrastructure. Exemples : réseau et sécurité. Le groupe doit avoir le rôle de contributeur pour l’abonnement, le contrôle du hub et les droits de contributeur réseau sur les rayons. Les grandes organisations divisent souvent ces responsabilités de gestion entre plusieurs équipes. C’est le cas, par exemple, pour un groupe d’opérations réseau **CorpNetOps**, exclusivement axé sur le réseau, et pour un groupe d’opérations de sécurité **CorpSecOps**, responsable de la stratégie de pare-feu et de sécurité. Dans ce cas précis, il convient de créer deux groupes distincts pour l’attribution de ces rôles personnalisés.
- Le groupe de développement/test, **AppDevOps,** , est responsable du déploiement des charges de travail d’application ou de service. Ce groupe joue le rôle de contributeur de machine virtuelle pour les déploiements IaaS. Il peut également jouer un ou plusieurs rôles de contributeur PaaS. Si vous souhaitez en savoir plus, veuillez consulter [Rôles intégrés pour les ressources Azure][Roles]. Éventuellement, l’équipe de développement/test peut avoir besoin de visibilité sur les stratégies de sécurité (groupes de sécurité réseau) et les stratégies de routage (itinéraires définis par l’utilisateur) dans le hub ou un rayon spécifique. En plus du rôle de contributeur pour les charges de travail, ce groupe nécessite également le rôle de lecteur de réseau.
- Le groupe des opérations et de la maintenance, **CorpInfraOps** ou **AppInfraOps**, est chargé de gérer les charges de travail en production. Ce groupe doit être un contributeur d’abonnement sur les charges de travail dans tous les abonnement de production. Certaines organisations peuvent également déterminer si elles ont besoin d’un groupe supplémentaire de type équipe du support technique pour la prise en charge du processus d’escalade avec le rôle de contributeur d’abonnement en production ainsi que l’abonnement au hub central. Le groupe supplémentaire corrige les problèmes de configuration potentiels dans l’environnement de production.

Le centre de données virtuel est conçu de telle sorte que les groupes créés pour les groupes du service informatique central gérant le hub disposent des groupes correspondants au niveau de la charge de travail. En plus de la gestion des ressources de hub, seuls les groupes du service informatique central peuvent contrôler l’accès externe et les autorisations de niveau supérieur sur l’abonnement. Les groupes de charge de travail peuvent également contrôler les ressources et les autorisations de leur réseau virtuel indépendamment du groupe du service informatique central.

Le centre de données virtuel est partitionné pour héberger de manière sécurisée plusieurs projets appartenant à différents métiers. Tous les projets nécessitent plusieurs environnements isolés (développement, test d’acceptation utilisateur (UAT) et production). Les abonnements Azure distincts pour chacun de ces environnements peuvent assurer un isolement naturel.

![5][5]

Le diagramme précédent illustre la relation entre les projets, les utilisateurs et les groupes d’une organisation, et les environnements dans lesquels les composants Azure sont déployés.

Dans le contexte informatique, un environnement (ou niveau) désigne généralement un système dans lequel plusieurs applications sont déployées et exécutées. Les grandes entreprises utilisent un environnement de développement (dans lequel les modifications sont effectuées et testées) et un environnement de production (destiné aux utilisateurs finaux). Ces environnements sont séparés, le plus souvent par des environnements intermédiaires, afin d’autoriser l’échelonnement des phases de déploiement (lancement), de test et de restauration en cas de problème. Les architectures de déploiement varient sensiblement, mais le processus de base qui consiste à commencer par le niveau développement (DEV) et à terminer par le niveau production (PROD) reste généralement appliqué.

Une architecture communément employée pour ces types d’environnement multiniveau comprend les environnements DevOps pour le développement et les tests, UAT pour la préproduction, et les environnements de production. Les organisations peuvent utiliser un ou plusieurs locataires Azure AD afin de définir l’accès et les droits pour ces environnements. Le diagramme précédent illustre un cas d’utilisation de deux locataires Azure AD distincts : l’un pour DevOps et UAT, et l’autre exclusivement destiné à la production.

La présence de différents locataires Azure AD met en œuvre la séparation entre les environnements. Le même groupe d’utilisateurs, par exemple le groupe du service informatique central, doit s’authentifier à l’aide d’un URI distinct pour accéder à un autre locataire Azure AD et modifier les rôles ou autorisations des environnements DevOps ou de production d’un projet. L’utilisation d’authentifications utilisateur distinctes pour accéder à différents environnements réduit les éventuelles interruptions et autres problèmes dus à des erreurs humaines.

#### <a name="component-type-infrastructure"></a>Type de composant : Infrastructure

Ce type de composant est l’endroit où réside la majeure partie de l’infrastructure sous-jacente. Il s’agit également du composant auquel vos équipes d’informatique centralisée, de sécurité et de conformité consacrent la majorité de leur temps.

![6][6]

Les composants d’infrastructure assurent une interconnexion pour les différents composants d’une implémentation de VDC et sont présents à la fois dans le hub et dans les rayons. La responsabilité de la gestion et de la maintenance des composants d’infrastructure est généralement attribuée à l’équipe du service informatique central ou de la sécurité.

L’une des principales tâches de l’équipe d’infrastructure informatique consiste à garantir la cohérence des schémas d’adresse IP dans l’ensemble de l’entreprise. L’espace d’adressage IP privé attribué à une implémentation de VDC doit être cohérent et NE PAS chevaucher les adresses IP privées affectées sur vos réseaux locaux.

Bien que la traduction d’adresses réseau (NAT) sur les routeurs de périphérie locaux ou dans les environnements Azure permette d’éviter les conflits d’adresses IP, elle ajoute de la complexité à vos composants d’infrastructure. L’une des finalités clés d’un centre de données virtuel étant de simplifier la gestion, l’utilisation du processus NAT pour gérer les problèmes liés aux adresses IP, bien que relevant d'une solution valide, n’est pas recommandée.

Les composants d’infrastructure ont les fonctionnalités suivantes :

- [Services d’identité et d’annuaire][azure-ad]. L’accès à chaque type de ressource dans Azure est contrôlé par une identité stockée dans un service d’annuaire. Le service d’annuaire stocke non seulement la liste des utilisateurs, mais également les droits d’accès aux ressources dans un abonnement Azure spécifique. Ces services peuvent exister uniquement dans le cloud, ou être synchronisés avec l’identité locale stockée dans Active Directory.
- [Réseau virtuel][virtual-network]. Les réseaux virtuels sont l’un des principaux composants d’un centre de données virtuel et vous permettent de créer une limite d’isolation du trafic sur la plateforme Azure. Un réseau virtuel est constitué d’un ou de plusieurs segments de réseau virtuel, chacun étant doté d’un préfixe de réseau IP (sous-réseau, IPv4 ou double pile IPv4/IPv6) spécifique. Le réseau virtuel définit une zone de périmètre interne dans laquelle les machines virtuelles IaaS et les services PaaS peuvent établir des communications privées. Les machines virtuelles (et les services PaaS) figurant dans un réseau virtuel ne peuvent pas communiquer directement avec les machines virtuelles (et les services PaaS) d’un autre réseau virtuel, même si ces deux réseaux virtuels sont créés par le même client, dans le cadre du même abonnement. Cet isolement est une propriété critique qui garantit que les machines virtuelles et les communications du client restent privées dans un réseau virtuel. Si souhaitez une connectivité entre réseaux, les fonctionnalités suivantes décrivent comment procéder.
- [Appairage de réseaux virtuels][virtual-network-peering]. La fonctionnalité fondamentale utilisée pour créer l’infrastructure d’un centre de données virtuel est le peering de réseaux virtuels, qui connecte deux réseaux virtuels de la même région par le biais du réseau du centre de données Azure, ou en utilisant la dorsale principale mondiale d'Azure entre plusieurs régions.
- [Points de terminaison de service de réseau virtuel][ServiceEndpoints]. Les points de terminaison de service étendent l’espace d’adressage privé de votre réseau virtuel pour inclure votre espace PaaS. Les points de terminaison étendent également l’identité de votre réseau virtuel aux services Azure via une connexion directe. Les points de terminaison permettent de sécuriser vos ressources critiques du service Azure pour vos réseaux virtuels uniquement.
- [Private Link][PrivateLink]. Azure Private Link vous permet d’accéder aux services PaaS Azure (par exemple [Stockage Azure][Storage], [Azure Cosmos DB][cosmos-db] et [Azure SQL Database][SQL]) ainsi qu’aux services de partenaires ou de clients hébergés par Azure sur un point de terminaison privé dans votre réseau virtuel. Le trafic entre votre réseau virtuel et le service transite par le réseau principal de Microsoft, éliminant ainsi toute exposition à l’Internet public. Vous pouvez également créer votre propre [service Private Link][PrivateLinkSvc] dans votre réseau virtuel et le distribuer en privé à vos clients. L’expérience de configuration et de consommation à l’aide du service Liaison privée Azure est cohérente entre les services PaaS Azure, appartenant au client et de partenaires partagés.
- [Itinéraires définis par l’utilisateur][UDR]. Le routage du trafic dans un réseau virtuel repose par défaut sur la table de routage système. Un itinéraire défini par l’utilisateur est une table de routage personnalisée que les administrateurs réseau peuvent associer à un ou plusieurs sous-réseaux pour remplacer le comportement de la table de routage système et définir un chemin de communication au sein d’un réseau virtuel. L’existence d’itinéraires définis par l’utilisateur garantit que le trafic de sortie en provenance du rayon transite par des machines virtuelles personnalisées et des appliances virtuelles réseau, ainsi que des équilibreurs de charge spécifiques présents dans le hub et dans les rayons.
- [Groupes de sécurité réseau][NSG]. Un groupe de sécurité réseau est une liste de règles de sécurité qui fait office de filtrage du trafic sur les sources IP, les destinations IP, les protocoles, les ports sources IP et les ports de destination IP (également appelés couche 4 cinq-tuple). Le groupe de sécurité réseau peut être appliqué à un sous-réseau et/ou à une carte réseau virtuelle associée à une machine virtuelle Azure. Les groupes de sécurité réseau jouent un rôle essentiel dans l’implémentation d’un contrôle de flux approprié dans le hub et les rayons. Le niveau de sécurité offert par le groupe de sécurité réseau dépend des ports que vous ouvrez et du but dans lequel vous le faites. Les clients doivent appliquer des filtres supplémentaires par machine virtuelle avec des pare-feu basés sur l’hôte, par exemple iptables ou le Pare-feu Windows.
- [DNS (Domain Name System)][DNS]. DNS fournit la résolution de noms pour les ressources d'un centre de données virtuel. Azure fournit des services DNS pour la résolution de noms [publics][DNS] et [privés][PrivateDNS]. Les zones privées fournissent la résolution de noms au sein d’un réseau virtuel, ainsi qu’entre des réseaux virtuels. Vous pouvez avoir des zones privées entre plusieurs réseaux virtuels au sein de la même région, mais aussi entre plusieurs régions et abonnements. Pour la résolution publique, Azure DNS fournit un service d’hébergement pour les domaines DNS qui offre une résolution de noms à l’aide de l’infrastructure Microsoft Azure. En hébergeant vos domaines dans Azure, vous pouvez gérer vos enregistrements DNS avec les mêmes informations d’identification, les mêmes API, les mêmes outils et la même facturation que vos autres services Azure.
- [Groupe d'administration][MgmtGrp], [abonnement](../ready/azure-best-practices/scale-subscriptions.md) et [gestion des groupes de ressources][RGMgmt]. Un abonnement définit une limite naturelle permettant de créer plusieurs groupes de ressources dans Azure. Cette séparation peut être destinée à la fonction, la ségrégation des rôles ou la facturation. Les ressources d’un abonnement sont regroupées dans des conteneurs logiques nommés groupes de ressources. Le groupe de ressources représente un groupe logique destiné à organiser les ressources d'un centre de données virtuel. Si votre organisation dispose de plusieurs abonnements, vous pouvez avoir besoin d’un moyen de gérer efficacement l’accès, les stratégies et la conformité de ces abonnements. Les groupes d’administration Azure fournissent un niveau d’étendue au-delà des abonnements. Vous organisez les abonnements en conteneurs connus sous le nom de groupes d’administration et vous appliquez vos conditions de gouvernance aux groupes d’administration. Tous les abonnements d’un groupe d’administration héritent automatiquement des conditions appliquées à ce groupe d’administration. Pour afficher ces trois fonctionnalités dans une vue hiérarchique, consultez [Organisation de vos ressources](../ready/azure-setup-guide/organize-resources.md) dans Cloud Adoption Framework.
- [Contrôle d’accès en fonction du rôle (RBAC)][RBAC]. RBAC peut mapper des rôles organisationnels et des droits d’accès à des ressources Azure spécifiques, ce qui vous donne la possibilité de restreindre les utilisateurs à un sous-ensemble d’actions. Si vous synchronisez Azure Active Directory avec une instance Active Directory locale, vous pouvez utiliser les mêmes groupes Active Directory dans Azure que ceux utilisés localement. Avec RBAC, vous pouvez accorder l’accès en attribuant le rôle approprié à des utilisateurs, groupes et applications dans l’étendue adéquate. L’étendue d’une attribution de rôle peut être un abonnement Azure, un groupe de ressources ou une ressource unique. Le mécanisme RBAC autorise l’héritage des autorisations. Un rôle attribué à une étendue parent accorde également l’accès aux enfants qu’elle contient. RBAC vous permet de séparer les tâches et d’accorder aux utilisateurs uniquement les accès dont ils ont besoin pour accomplir leur travail. Par exemple, un employé peut gérer les machines virtuelles dans un abonnement, et un autre les bases de données SQL Server au sein du même abonnement.

#### <a name="component-type-perimeter-networks"></a>Type de composant : Réseaux de périmètre

Les composants d'un réseau de périmètre (parfois appelé réseau DMZ) connectent les réseaux de vos centres de données locaux ou physiques, et établissent une connectivité Internet. En général, le périmètre requiert beaucoup de temps de la part de vos équipes réseau et sécurité.

Les paquets entrants doivent transiter par les appliances de sécurité du hub avant d’atteindre les serveurs et les services principaux dans les rayons. Exemples : pare-feu, systèmes de détection et de prévention d’intrusion. Avant de quitter le réseau, les paquets Internet des charges de travail doivent également transiter par les appliances de sécurité du réseau de périmètre. Ce flux permet la mise en œuvre, l’inspection et l’audit des stratégies.

Les composants réseau du périmètre sont les suivants :

- [des réseaux virtuels][virtual-network], [des itinéraires définis par l’utilisateur][UDR] et [des groupes de sécurité réseau][NSG]
- [Appliances virtuelles réseau][NVA]
- [Équilibrage de charge Azure][ALB]
- [Azure Application Gateway][AppGW] avec [pare-feu d'applications web (WAF)][AppGWWAF]
- [Adresses IP publiques][PIP]
- [Azure Front Door][azure-front-door] avec [pare-feu d’applications web (WAF)][AFDWAF]
- [Pare-feu Azure][AzFW] et [Azure Firewall Manager][AzFWMgr]
- [Protection DDos standard][DDoS]

En règle générale, les équipes du service informatique central et de la sécurité sont chargées de la définition des exigences et du fonctionnement des réseaux de périmètre.

![7][7]

Le diagramme précédent illustre l’application de deux périmètres avec un accès à Internet et à un réseau local, ces deux périmètres résidant dans le hub DMZ. Dans le hub DMZ, le réseau de périmètre vers Internet peut monter en puissance pour prendre en charge de nombreuses applications métier, à l’aide de plusieurs batteries de pare-feu d’applications web (WAF) et de Pare-feu Azure. Le hub permet également une connectivité locale via un VPN ou ExpressRoute le cas échéant.

> [!NOTE]
> Comme l'illustre le diagramme précédent, dans le « Hub DMZ », un grand nombre des fonctionnalités suivantes peuvent être regroupées dans un hub Azure Virtual WAN (par exemple, les réseaux virtuels, les itinéraires définis par l’utilisateur, les groupes de sécurité réseau, les passerelles VPN, les passerelles ExpressRoute, les équilibreurs de charge Azure, Pare-feu Azure et DDoS) L’utilisation de hubs Azure Virtual WAN permet de considérablement faciliter la création du réseau virtuel hub, et dès lors du centre de données virtuel, Azure se chargeant de la complexité d’ingénierie lorsque vous déployez un hub Azure Virtual WAN.

[Réseaux virtuels][virtual-network]. Le hub repose généralement sur un réseau virtuel comprenant plusieurs sous-réseaux pour héberger les différents types de service qui filtrent et inspectent le trafic à destination ou en provenance d’Internet via les instances Pare-feu Azure, NVA, WAF et Azure Application Gateway.

[Itinéraires définis par l’utilisateur][UDR] Ces itinéraires permettent aux clients de déployer des pare-feu, des systèmes de détection et de prévention d’intrusion et d’autres appliances virtuelles, et de router le trafic réseau à travers ces appliances de sécurité à des fins d’application de stratégies de limites de sécurité, d’audit et d’inspection. Les itinéraires définis par l’utilisateur peuvent être créés à la fois dans le hub et dans les rayons pour garantir que le trafic transite par des machines virtuelles personnalisées, des appliances virtuelles réseau et des équilibreurs de charge spécifiques utilisés par une implémentation de centre de données virtuel. Pour garantir que le trafic généré à partir de machines virtuelles figurant dans le rayon transite par les appliances virtuelles correctes, il convient de configurer un itinéraire défini par l’utilisateur dans les sous-réseaux du rayon en définissant l’adresse IP frontale de l’équilibreur de charge interne en tant que tronçon suivant. L’équilibreur de charge interne distribue le trafic interne vers les appliances virtuelles (pool principal d’équilibreur de charge).

[Pare-feu Azure][AzFW] est un service de sécurité réseau managé qui protège vos ressources Réseau virtuel Azure. Il s’agit d’un pare-feu managé, doté d’une haute disponibilité et d’une extensibilité illimitée dans le cloud. Vous pouvez créer, appliquer et consigner des stratégies de connectivité réseau et d’application de façon centralisée entre les abonnements et les réseaux virtuels. Le service Pare-feu Azure utilise une adresse IP publique statique pour vos ressources de réseau virtuel. Il permet aux pare-feu externes d’identifier le trafic provenant de votre réseau virtuel. Le service est totalement intégré à Azure Monitor pour la journalisation et les analyses.

Si vous utilisez la topologie Azure Virtual WAN, [Azure Firewall Manager][AzFWMgr] est un service de gestion de la sécurité qui fournit une stratégie de sécurité centralisée et la gestion des itinéraires pour les périmètres de sécurité basés sur le cloud. Il fonctionne avec le hub Azure Virtual WAN, ressource managée par Microsoft qui vous permet de créer facilement des architectures hub-and-spoke. Lorsque des stratégies de sécurité et de routage sont associées à un hub, on parle de hub virtuel sécurisé.

[Appliances virtuelles réseau][NVA]. Dans le hub, le réseau de périmètre disposant d’un accès à Internet est normalement géré via une instance de Pare-feu Azure, une batterie de pare-feu ou WAF (pare-feu d’applications web).

Les différents cœurs de métier utilisent généralement de nombreuses applications web qui sont susceptibles de présenter diverses vulnérabilités et d’être exposées à des codes malveillants exploitant une faille de sécurité. Les pare-feu d’applications web sont un type de produit particulier qui permet de détecter les attaques contre les applications web (HTTP/HTTPS) de façon plus approfondie qu’un pare-feu générique. Contrairement à la technologie de pare-feu classique, les WAF intègrent un ensemble de fonctionnalités spécifiques pour protéger les serveurs web internes contre les menaces.

Un pare-feu Azure ou NVA utilise un plan d’administration commune, avec un ensemble de règles de sécurité, pour non seulement protéger les charges de travail hébergées dans les rayons, mais aussi contrôler l’accès aux réseaux locaux. Le Pare-feu Azure dispose d’une fonctionnalité d’extensibilité intégrée, alors que les pare-feux NVA peuvent être manuellement mis à l’échelle derrière un équilibreur de charge. En règle générale, une batterie de pare-feu est équipée de logiciels moins spécialisés qu’un WAF, mais dispose d’un vaste champ d’application permettant de filtrer et d’inspecter n’importe quel type de trafic en entrée et en sortie. Si une approche NVA est appliquée, vous pouvez trouver et déployer les pare-feu à partir de la Place de marché Azure.

Nous vous recommandons d’utiliser un ensemble d’instances de Pare-feu Azure, ou NVA, pour le trafic provenant d’Internet. Utilisez-en un autre pour le trafic local. L’utilisation d’un seul ensemble de pare-feu pour ces deux types de trafic réseau constitue un risque pour la sécurité, car elle n’offre aucun périmètre de sécurité entre les deux. L’utilisation de couches de pare-feu distinctes simplifie la vérification des règles de sécurité et permet d’identifier clairement les règles auxquelles correspondent les différentes requêtes réseau entrantes.

[Azure Load Balancer][ALB] offre un service haute disponibilité de couche 4 (TCP/UDP), qui peut distribuer le trafic entrant entre des instances de service définies dans un jeu à charge équilibrée. Le trafic envoyé à l’équilibreur de charge à partir de points de terminaison frontaux (points de terminaison IP publics ou privés) peut être redistribué avec ou sans traduction d’adresses à un ensemble d’un pool d’adresses IP principal (par exemple, des appliances virtuelles réseau ou des machines virtuelles).

Azure Load Balancer peut également analyser à l’aide de sondes l’intégrité des différentes instances de serveur ; si l’une des instances ne répond pas à une sonde, l’équilibreur de charge arrête d’envoyer le trafic à l’instance défaillante correspondante. Dans le centre de données virtuel, un équilibreur de charge externe est déployé sur le hub et les rayons. Dans le hub, l’équilibreur de charge est utilisé pour router efficacement le trafic vers les instances de pare-feu, et dans les rayons, les équilibreurs de charge sont utilisés pour gérer le trafic des applications.

[Azure Front Door (AFD)][azure-front-door] est une plateforme d’accélération d’applications web scalable à haute disponibilité, intégrant un équilibreur de charge HTTP global, la protection d’application et le réseau de distribution de contenu. En s’exécutant dans plus de 100 emplacements au niveau de la périphérie du réseau global de Microsoft, AFD vous permet de générer et de faire fonctionner votre application web dynamique et votre contenu statique. Vous pouvez aussi effectuer un scale-out de ces derniers. AFD fournit à votre application des performances d’utilisateur final très élevées, l’automatisation de la maintenance de région/d’horodatage unifiée, l’automatisation de la continuité d’activité et de la reprise d’activité, des informations client/utilisateur unifiées, ainsi que des insights sur la mise en cache et les services. La plateforme offre ce qui suit :
    - performance, fiabilité et prise en charge des contrats de niveau de service (SLA).
    - Certifications de conformité.
    - Pratiques de sécurité vérifiables développées, exploitées et prises en charge en mode natif par Azure.
Azure Front Door fournit aussi un pare-feu d'applications web (WAF) qui protège les applications web contre les vulnérabilités et failles de sécurité.

[Azure Application Gateway][AppGW] est une appliance virtuelle dédiée qui propose un contrôleur managé de livraison d’applications. Elle offre diverses fonctionnalités d’équilibrage de charge de couche 7 pour votre application. Cette appliance vous permet d’optimiser les performances de la batterie de serveurs Web en déchargeant une terminaison SSL nécessitant de nombreuses ressources du processeur vers la passerelle Application Gateway. Elle fournit également d’autres fonctionnalités de routage de couche 7, notamment la distribution en tourniquet (round-robin) du trafic entrant, l’affinité de session basée sur les cookies, le routage basé sur le chemin d’accès de l’URL et la possibilité d’héberger plusieurs sites web derrière une seule passerelle d’application. Un pare-feu d’applications web (WAF) est également intégré à la référence SKU Application Gateway WAF. Cette référence SKU protège les applications web contre les vulnérabilités et les codes malveillants exploitant une faille de sécurité les plus courants sur le web. La passerelle Application Gateway peut être configurée en tant que passerelle internet, passerelle interne uniquement ou une combinaison des deux.

[IP publiques][PIP]. Avec certaines fonctionnalités Azure, vous pouvez associer des points de terminaison de service à une adresse IP publique, pour que votre ressource soit accessible depuis Internet. Ce point de terminaison utilise NAT pour router le trafic vers l’adresse et le port internes sur le réseau virtuel dans Azure. Il s’agit du principal chemin d’accès pour que le trafic externe passe dans le réseau virtuel. Vous pouvez configurer des adresses IP publiques pour déterminer le type de trafic passé ainsi que la façon dont la traduction s’opère sur le réseau virtuel et son emplacement précis.

Le service [Azure DDoS Protection Standard][DDoS] fournit des fonctionnalités d’atténuation supplémentaires par rapport au niveau de [service De base][DDoS] qui sont destinées spécifiquement aux ressources de réseau virtuel Azure. Le service DDoS Protection Standard est facile à activer et ne nécessite aucun changement de l’application. Les stratégies de protection sont paramétrées par le biais d’algorithmes de surveillance du trafic et d’apprentissage automatique dédiés. Ces stratégies sont appliquées aux adresses IP publiques associées aux ressources déployées sur des réseaux virtuels. Exemples : instances Azure Load Balancer, Azure Application Gateway et Azure Service Fabric. Les journaux générés par le système en quasi-temps réel sont disponibles par le biais d’affichages Azure Monitor pendant une attaque et à des fins d’historique. Vous pouvez ajouter une protection de la couche Application via le pare-feu d’applications web Azure Application Gateway. La protection est assurée pour les adresses IP publiques IPv4 et IPv6 Azure.

La topologie hub-and-spoke utilise le peering de réseaux virtuels et les itinéraires définis par l’utilisateur pour acheminer correctement le trafic.

![8][8]

Dans le diagramme, l’itinéraire défini par l’utilisateur permet de s'assurer que le trafic transite du rayon vers le pare-feu avant de passer en local via la passerelle ExpressRoute (si la stratégie de pare-feu permet un tel flux).

#### <a name="component-type-monitoring"></a>Type de composant : Surveillance

Les [composants de surveillance][MonitorOverview] offrent une vue d’ensemble de tous les autres types de composants et génèrent des alertes concernant ces derniers. Toutes les équipes doivent avoir accès à la surveillance des composants et services qui leur sont accessibles. Si vous disposez d’équipes des opérations ou d’un support technique centralisé, ils doivent disposer d’un accès intégré aux données fournies par ces composants.

Azure propose différents types de service de journalisation et de supervision pour effectuer le suivi du comportement des ressources hébergées par Azure. La gouvernance et le contrôle des charges de travail dans Azure reposent non seulement sur la collecte des données de journalisation, mais également sur le déclenchement d’actions en fonction d’événements signalés spécifiques.

[Azure Monitor][AzureMonitor]. Azure comprend plusieurs services qui effectuent individuellement un rôle ou une tâche spécifique dans l’espace d’analyse. Ensemble, ces services fournissent une solution complète pour la collecte, l’analyse et l’action sur les journaux générés par le système de vos applications et des ressources Azure qui les prennent en charge. Ces services peuvent aussi surveiller les ressources locales critiques afin de fournir un environnement de surveillance hybride. Comprendre les outils et les données disponibles est la première étape du développement d’une stratégie de surveillance complète pour vos applications.

Il existe deux types de journaux de base dans Azure Monitor :

- Les [métriques][Metrics] sont des valeurs numériques décrivant un aspect d’un système à un moment précis dans le temps. Elles sont légères et capables de prendre en charge des scénarios en quasi-temps réel. Pour de nombreuses ressources Azure, vous verrez les données collectées par Azure Monitor directement sur la page Vue d’ensemble correspondante sur le portail Azure. À titre d'exemple, jetez un œil à toutes les machines virtuelles pour voir plusieurs graphiques affichant les métriques de performances. Sélectionnez l’un des graphiques pour ouvrir les données dans Metrics Explorer sur le portail Azure, ce qui vous permet de représenter les valeurs de plusieurs métriques dans un graphique au fil du temps. Vous pouvez afficher les graphiques de manière interactive ou les épingler au tableau de bord pour les voir avec d’autres visualisations.

- Les [journaux d’activité][Logs] contiennent différents types de données organisées en enregistrements, avec différents jeux de propriétés pour chaque type. Les événements et traces sont stockés sous forme de journaux avec les données de performances, et tous peuvent être combinés à des fins d'analyse. Les données de journal collectées par Azure Monitor peuvent être analysées à l’aide de requêtes qui permettent de récupérer, consolider et analyser rapidement les données collectées. Les journaux sont stockés et interrogés à partir de [Log Analytics][LogAnalytics]. Vous pouvez créer et tester des requêtes à l’aide de Log Analytics dans le portail Azure, avant d’analyser directement les données à l’aide de ces outils ou d’enregistrer les requêtes pour les utiliser pour les visualisations ou les règles d’alerte.

![9][9]

Azure Monitor peut recueillir des données de diverses sources. Vous pouvez envisager de surveiller les données de vos applications sous forme de niveaux allant de votre application à la plateforme elle-même, en passant par le système d’exploitation et les services sur lesquels s’appuie votre application. Azure Monitor collecte des données à partir de chacun des niveaux suivants :

- **Données de surveillance de l’application :** données concernant les performances et la fonctionnalité du code que vous avez écrit, quelle que soit la plateforme.
- Données de surveillance du système d’exploitation invité : données concernant le système d’exploitation sur lequel votre application est exécutée. Ce système d'exploitation peut s'exécuter dans Azure, un autre cloud ou un système local.
- **Données de surveillance des ressources Azure :** données sur le fonctionnement d’une ressource Azure.
- **Données de surveillance de l’abonnement Azure :** données concernant le fonctionnement et la gestion d’un abonnement Azure, mais aussi données concernant l’intégrité et le fonctionnement d’Azure.
- **Données de surveillance du locataire Azure :** données concernant le fonctionnement des services Azure au niveau du locataire, tels qu’Azure Active Directory.
- **Sources personnalisées :** Les journaux envoyés à partir de sources locales peuvent également être inclus. Il peut notamment s'agir d'événements de serveur local ou de sortie syslog de périphérique réseau.

La supervision des données est utile uniquement si elle permet d’augmenter votre visibilité sur le fonctionnement de votre environnement informatique. Azure Monitor inclut plusieurs fonctionnalités et outils qui fournissent des informations importantes sur vos applications et d’autres ressources dont elles dépendent. La supervision des solutions et des fonctionnalités telles qu’Application Insights et Azure Monitor pour les conteneurs fournit des insights détaillés sur les différents aspects de votre application et les services Azure spécifiques.

Les solutions de supervision dans Azure Monitor sont des jeux de logique empaquetés qui fournissent des informations détaillées pour une application ou un service spécifique. Elles incluent une logique de collecte des données de surveillance pour l’application ou le service, des requêtes permettant d’analyser ces données et des vues pour la visualisation. Microsoft et ses partenaires proposent des solutions de supervision qui assurent la supervision de divers services Azure et d’autres applications.

Avec toutes ces données enrichies collectées, il est important de prendre des mesures proactives sur les événements survenant dans votre environnement et où les seules requêtes manuelles ne suffisent pas. Dans Azure Monitor, les alertes vous avertissent de manière proactive en cas de condition critique, et sont susceptibles d’essayer de prendre des mesures correctives. Les règles d’alerte basées sur les métriques émettent des alertes en quasi-temps réel à partir de valeurs numériques, alors que les règles basées sur les journaux d’activité acceptent une logique complexe sur des données issues de différentes sources. Les règles d’alerte dans Azure Monitor utilisent des groupes d’actions, qui contiennent des ensembles uniques de destinataires et d’actions pouvant être partagés entre plusieurs règles. Selon vos besoins, les groupes d’actions peuvent effectuer des actions telles que l’utilisation de webhooks entraînant des alertes pour démarrer des actions externes ou s'intégrer à vos outils ITSM.

Azure Monitor permet également de créer des tableaux de bord personnalisés. Les tableaux de bord Azure vous permettent de combiner différents genres de données, y compris les métriques et les journaux d’activité, dans un même volet dans le portail Azure. Si vous le souhaitez, vous pouvez partager le tableau de bord avec d’autres utilisateurs d’Azure. Les éléments d’Azure Monitor peuvent être ajoutés à un tableau de bord Azure en plus de la sortie de n’importe quelle requête de journal ou graphique de métriques. Par exemple, vous pouvez créer un tableau de bord qui combine des vignettes affichant un graphique de métriques, un tableau de journaux d’activité, un graphique d’utilisation provenant d’Application Insights et la sortie d’une requête de journal d’activité.

Enfin, les données Azure Monitor constituent une source native pour Power BI. Power BI est un service d’analyse métier qui fournit des visualisations interactives d’une large gamme de sources de données. Il constitue un moyen efficace de mettre les données à disposition d’autres personnes à l'intérieur comme à l'extérieur de votre organisation. Vous pouvez configurer Power BI pour importer automatiquement les données de journal à partir d’Azure Monitor afin de tirer parti de ces visualisations supplémentaires.

[Azure Network Watcher][NetWatch] fournit des outils permettant d’effectuer une supervision et des diagnostics, d’afficher les métriques et d’activer ou de désactiver les journaux d’activité des ressources d’un réseau virtuel dans Azure. Il s’agit d’un service multifacette qui permet d’accéder aux fonctionnalités suivantes et à bien d’autres encore :

- Superviser la communication entre une machine virtuelle et un point de terminaison
- Afficher les ressources se trouvant sur un réseau virtuel et leurs relations
- Diagnostiquer les problèmes de filtrage du trafic réseau à destination ou en provenance d’une machine virtuelle
- Diagnostiquer les problèmes de routage réseau d’une machine virtuelle
- Diagnostiquer les connexions sortantes d’une machine virtuelle
- Capturer les paquets à destination et en provenance d’une machine virtuelle
- Diagnostiquer les problèmes liés à une passerelle de réseau virtuel et aux connexions.
- Déterminer les latences relatives entre les régions Azure et les fournisseurs de services Internet
- Afficher les règles de sécurité d’une interface réseau
- Afficher les métriques réseau
- Analyser le trafic à destination ou en provenance d’un groupe de sécurité réseau
- Afficher les journaux de diagnostic des ressources réseau

#### <a name="component-type-workloads"></a>Type de composant : Charges de travail

Les composants de type charge de travail désignent l’emplacement où résident vos applications et services proprement dits. Il s’agit du composant auquel vos équipes de développement d’applications consacrent la majorité de leur temps.

Les possibilités de charge de travail sont illimitées. Voici quelques-uns des innombrables types de charges de travail possibles :

**Applications internes :** Les applications métier sont essentielles pour les opérations d’entreprise. Ces applications présentent certaines caractéristiques en commun :

- **Interactives :** Une fois que vous avez entré des données, des résultats ou des rapports sont retournés.
- **Pilotées par les données :** Elles utilisent les données de manière intensive et accèdent fréquemment aux bases de données ou à d’autres types de stockage.
- **Intégrées :** Elles assurent une intégration avec d’autres systèmes au sein ou en dehors de l’organisation.

**Sites web destinés aux clients (accessibles sur Internet ou en interne) :** La plupart des applications Internet sont des sites web. Azure peut exécuter un site web via une machine virtuelle IaaS ou un site [Azure Web Apps][WebApps] (PaaS). Azure Web Apps s’intègre aux réseaux virtuels pour déployer des applications web dans une zone de réseau du rayon. Les sites web internes n’ont pas besoin d’exposer un point de terminaison Internet public, car les ressources sont accessibles par le biais d’adresses routables non-Internet privées à partir du réseau virtuel privé.

**Analytique du Big Data :** Lorsque les données doivent faire l'objet d'un scale-up pour des volumes plus importants, les bases de données relationnelles peuvent ne pas fonctionner correctement en raison de la charge extrême ou de la nature non structurée des données. [Azure HDInsight][HDInsight] est un service cloud d’analyse managé, complet et open source pour les entreprises. Vous pouvez utiliser des infrastructures open source telles que Hadoop, Apache Spark, Apache Hive, LLAP, Apache Kafka, Apache Storm. R. HDInsight prend en charge le déploiement dans un réseau virtuel basé sur l’emplacement et peut être déployé sur un cluster dans un rayon du centre de données virtuel.

**Événements et messagerie :** [Azure Event Hubs][EventHubs] est une plateforme de streaming de Big Data et un service d’ingestion d’événements. Il peut recevoir et traiter des millions d’événements par seconde. Il offre une faible latence et une durée de rétention configurable vous permettant d’ingérer des quantités massives de données dans Azure et de les lire à partir de plusieurs applications. Le service prend en charge le traitement de pipelines en temps réel et par lots sur un même flux.

Vous pouvez implémenter un service de messagerie cloud à haut niveau de fiabilité entre applications et services via [Azure Service Bus][ServiceBus]. Il offre une messagerie répartie asynchrone entre le client et le serveur, une messagerie FIFO (premier entré, premier sorti) structurée ainsi que des fonctionnalités de publication et d’abonnement.

![10][10]

Ces exemples vous permettent de créer des types de charges de travail dans Azure (des applications web et aux applications SQL de base en passant par l'IoT, le Big Data, le Machine Learning, l'IA et bien plus).

### <a name="highly-availability-multiple-virtual-datacenters"></a>Haute disponibilité : plusieurs centres de données virtuels

Jusqu’à présent, cet article s’est concentré sur la conception d’un seul centre de données virtuel en décrivant les architectures et les composants de base qui contribuent à la résilience. Les fonctionnalités Azure telles que l’équilibreur de charge Azure, les appliances virtuelles réseau, les zones de disponibilité, les groupes de disponibilité, les groupes identiques vous permettent d'assurer des niveaux de contrat de niveau de service élevés dans vos services de production.

Toutefois, étant donné qu’un centre de données virtuel est généralement implémenté dans une même région, il peut être vulnérable à des pannes qui affectent la totalité de la région. Les clients qui nécessitent une haute disponibilité doivent protéger leurs services en déployant le même projet dans au moins deux implémentations de centre de données virtuel déployées dans des régions distinctes.

En plus des questions liées aux contrats SLA, plusieurs scénarios courants tirent parti de l’exécution de différents centres de données virtuels :

- Présence régionale ou mondiale de vos utilisateurs finaux ou partenaires.
- Exigences de récupération d’urgence.
- Mécanisme de redirection du trafic entre des centres de données à des fins d'équilibrage de charge et de performances

#### <a name="regionalglobal-presence"></a>Présence régionale/mondiale

Les centres de données Azure sont présents dans de nombreuses régions du monde. Lorsque vous sélectionnez plusieurs centres de données Azure, prenez en compte deux facteurs associés : les distances géographiques et la latence. Pour optimiser l’expérience utilisateur, évaluez la distance entre chaque centre de données virtuel, de même que la distance entre chaque centre de données virtuel et les utilisateurs finaux.

Une région Azure hébergeant votre centre de données virtuel doit respecter les exigences réglementaires de la juridiction dont relève votre organisation.

#### <a name="disaster-recovery"></a>Récupération d'urgence

La conception d’un plan de reprise d’activité dépend des types de charges de travail et de la possibilité de synchroniser l’état de ces charges de travail entre différentes implémentations de centre de données virtuel. Dans l’idéal, la plupart des clients souhaitent un mécanisme de basculement rapide, ce qui peut nécessiter une synchronisation des données d’application entre les déploiements s'exécutant dans plusieurs implémentations de centre de données virtuel. Toutefois, quand vous concevez des plans de reprise d’activité, il est important de savoir que la plupart des applications sont sensibles à la latence qui peut découler de la synchronisation de ces données.

La synchronisation et la supervision des pulsations des applications dans différentes implémentations de VDC obligent les applications à communiquer sur le réseau. Plusieurs implémentations de centre de données virtuel dans des régions distinctes peuvent être connectées comme suit :

- Communication hub à hub intégrée aux hubs Azure Virtual WAN dans les régions du même Virtual WAN.
- Peering de réseaux virtuels pour connecter des hubs dans différentes régions.
- Peering privé ExpressRoute lorsque les hubs de chaque implémentation de centre de données virtuel sont connectés au même circuit ExpressRoute.
- Plusieurs circuits ExpressRoute connectés au moyen de votre dorsale d’entreprise et de vos différentes implémentations de centre de données virtuel connectées aux circuits ExpressRoute.
- Connexions VPN site à site entre la zone hub de vos implémentations de centre de données virtuel dans chaque région Azure.

Les hubs Virtual WAN, le peering de réseaux virtuels ou les connexions ExpressRoute constituent généralement le type privilégié de connectivité réseau en raison de la bande passante plus importante et des niveaux de latence constants lors de la transmission via la dorsale de Microsoft.

Réalisez des tests de qualification de réseau pour vérifier la latence et la bande passante de ces connexions et pour déterminer si la réplication synchrone ou asynchrone des données est appropriée. Il est également important d’évaluer ces résultats au vu de l’objectif de délai de récupération (RTO).

#### <a name="disaster-recovery-diverting-traffic-from-one-region-to-another"></a>Reprise d’activité : redirection du trafic d’une région à une autre

[Azure Traffic Manager][azure-traffic-manager] et [Azure Front Door][azure-front-door] vérifient périodiquement l’intégrité du service des points de terminaison d'écoute dans différentes implémentations de centre de données virtuel et, en cas de défaillance de ces points de terminaison, routent automatiquement le trafic vers le centre de données virtuel le plus proche. Traffic Manager utilise les mesures utilisateur en temps réel et le DNS pour acheminer les utilisateurs vers le centre de données virtuel le plus proche (ou le suivant en cas de défaillance). Azure Front Door est un proxy inverse de plus de 100 sites de réseau principal Microsoft, qui utilise anycast pour acheminer les utilisateurs vers le point de terminaison d’écoute le plus proche.

### <a name="summary"></a>Résumé

Un centre de données virtuel est une approche relative à la migration d’un centre de données permettant de créer une architecture évolutive qui optimise l’utilisation des ressources Azure, réduit les coûts et simplifie la gouvernance du système. Le centre de données virtuel est généralement basé sur les topologies de réseau hub-and-spoke (à l’aide du peering de réseaux virtuels ou de hubs Virtual WAN). Les services partagés communs fournis dans le hub, de même que les applications et charges de travail spécifiques, sont déployés dans les rayons. Le centre de données virtuel respecte également la structure des rôles d’une entreprise, où collaborent différents services (équipes informatique centrale, DevOps, opérations et maintenance, etc.) tout en exerçant leur rôle spécifique. Le centre de données virtuel prend en charge la migration des charges de travail locales existantes vers Azure, mais offre aussi de nombreux avantages en termes de déploiements natifs cloud.

## <a name="references"></a>References

Apprenez-en davantage sur les fonctionnalités Azure présentées dans ce document.

<!-- markdownlint-disable MD033 -->

| Fonctionnalités réseau | Équilibrage de la charge. | Connectivité |
| --- | --- | --- |
| [Réseaux virtuels Azure][virtual-network] <br> [Groupes de sécurité réseau][NSG] <br> [Points de terminaison de service][ServiceEndpoints] <br> [Liaison privée][PrivateLink] <br> [Itinéraires définis par l’utilisateur][UDR] <br> [Appliances virtuelles réseau][NVA] <br> [Adresses IP publiques][PIP] <br> [DNS Azure][DNS] | [Azure Front Door][azure-front-door] <br> [Azure Load Balancer (L4)][ALB] <br> [Application Gateway (L7)][AppGW] <br> [Azure Traffic Manager][azure-traffic-manager] <br><br><br><br><br> | [Peering de réseaux virtuels][virtual-network-peering] <br> [Réseau privé virtuel][VPN] <br> [Virtual WAN][virtual-wan] <br> [ExpressRoute][ExR] <br> [ExpressRoute Direct][ExRD] <br><br><br><br><br> |

| Identité | Surveillance | Bonnes pratiques |
| --- | --- | --- |
| [Azure Active Directory][azure-ad] <br>[Azure Multi-Factor Authentication][multi-factor-authentication] <br> [Contrôle d’accès en fonction du rôle][RBAC] <br> [Rôles Azure AD par défaut][Roles] <br><br><br> | [Network Watcher][NetWatch] <br> [Azure Monitor][MonitorOverview] <br> [Log Analytics][LogAnalytics] <br> | [Groupe d’administration][MgmtGrp] <br> [Gestion des abonnements](../ready/azure-best-practices/scale-subscriptions.md) <br> [Gestion des groupes de ressources][RGMgmt] <br> [Limites d’abonnement Azure][limits] <br><br><br> |

Sécurité | Autres services Azure | |
|-|-|-|
| [Pare-feu Azure][AzFW] <br> [Firewall Manager][AzFWMgr] <br> [Application Gateway - WAF][AppGWWAF] <br> [Front Door - WAF][AFDWAF] <br> [Service de protection DDoS Azure][DDoS] <br> | [Stockage Azure][Storage] <br> [Azure SQL][SQL] <br> [Azure Web Apps][WebApps] <br> [Cosmos DB][cosmos-db] <br> [HDInsight][HDInsight] | [Hubs d'événements][EventHubs] <br> [Service Bus][ServiceBus] <br> [Azure IoT][IoT] <br> [Azure Machine Learning][machine-learning] |

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Étapes suivantes

- Apprenez-en davantage sur le [peering de réseaux virtuels][virtual-network-peering], la technologie principale des topologies hub-and-spoke.
- Implémentez [Azure Active Directory][azure-ad] pour utiliser le [contrôle d’accès en fonction du rôle][RBAC].
- Développez un modèle de gestion des abonnements et des ressources utilisant le contrôle d’accès en fonction du rôle et répondant aux exigences de la structure, ainsi qu'aux stratégies de votre organisation. L’activité la plus importante est la planification. Analysez la manière dont les réorganisations, les fusions, les nouvelles gammes de produits, entre autres considérations, affectent vos modèles initiaux afin de garantir une mise à l’échelle adaptée aux besoins et au développement futurs.

<!-- images -->

[0]: ../_images/vdc/networking-vdc-redundant.png "Exemples de chevauchement de composants"
<!-- _1_ >: ../_images/vdc/networking-vdc-high-level.png "Example of hub and spoke VDC" -->
[2]: ../_images/vdc/networking-vdc-cluster.png "Cluster de concentrateurs et de rayons"
[3]: ../_images/vdc/networking-vdc-spoke-to-spoke.png "Rayon à rayon"
[4]: ../_images/vdc/networking-vdc-block-level-diagram.png "Diagramme de niveau bloc du centre de données virtuel"
[5]: ../_images/vdc/networking-vdc-users-groups-subscriptions.png "Utilisateurs, groupes, abonnements et projets"
[6]: ../_images/vdc/networking-vdc-infrastructure.png "Diagramme d’infrastructure"
[7]: ../_images/vdc/networking-vdc-perimeter.png "Diagramme d’infrastructure"
[8]: ../_images/vdc/networking-vdc-perimeter-peering.png "Peering de réseaux virtuels et réseaux de périmètre"
[9]: ../_images/vdc/networking-vdc-monitoring.png "Diagramme d’Azure Monitor"
[10]: ../_images/vdc/networking-vdc-workloads.png "Diagramme des charges de travail"
[11]: ../_images/vdc/networking-vdc-brief-flat.png "Exemple de réseau plat"
[12]: ../_images/vdc/networking-vdc-brief-mesh.png "Exemple de réseau maillé"
[13]: ../_images/vdc/networking-vdc-brief-hub.png "Exemple de centre de données virtuel hub-and-spoke"
[14]: ../_images/vdc/networking-vdc-brief-vwan.png "Exemple de centre de données virtuel Virtual WAN"

<!-- links -->

[limits]: https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits
[Roles]: https://docs.microsoft.com/azure/role-based-access-control/built-in-roles
[virtual-network]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview
[NSG]: https://docs.microsoft.com/azure/virtual-network/security-overview
[PrivateLink]: https://docs.microsoft.com/azure/private-link/private-link-overview
[PrivateLinkSvc]: https://docs.microsoft.com/azure/private-link/private-link-service-overview
[ServiceEndpoints]: https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview
[DNS]: https://docs.microsoft.com/azure/dns/dns-overview
[PrivateDNS]: https://docs.microsoft.com/azure/dns/private-dns-overview
[virtual-network-peering]: https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview
[UDR]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview
[RBAC]: https://docs.microsoft.com/azure/role-based-access-control/overview
[multi-factor-authentication]: https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks
[azure-ad]: https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis
[VPN]: https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: https://docs.microsoft.com/azure/expressroute/expressroute-introduction
[ExRD]: https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about
[virtual-wan]: https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about
[NVA]: https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: https://docs.microsoft.com/azure/firewall/overview
[AzFWMgr]: https://docs.microsoft.com/azure/firewall-manager/overview
[MgmtGrp]: https://docs.microsoft.com/azure/governance/management-groups/overview
[RGMgmt]: https://docs.microsoft.com/azure/azure-resource-manager/management/manage-resource-groups-portal#what-is-a-resource-group
[ALB]: https://docs.microsoft.com/azure/load-balancer/load-balancer-overview
[DDoS]: https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview
[PIP]: https://docs.microsoft.com/azure/virtual-network/virtual-network-public-ip-address
[azure-front-door]: https://docs.microsoft.com/azure/frontdoor/front-door-overview
[AFDWAF]: https://docs.microsoft.com/azure/web-application-firewall/afds/afds-overview
[AppGW]: https://docs.microsoft.com/azure/application-gateway/overview
[AppGWWAF]: https://docs.microsoft.com/azure/web-application-firewall/ag/ag-overview
[MonitorOverview]: https://docs.microsoft.com/azure/networking/networking-overview#monitor
[AzureMonitor]: https://docs.microsoft.com/azure/azure-monitor/overview
[Metrics]: https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics
[Logs]: https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-logs
[LogAnalytics]: https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal
[NetWatch]: https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: https://docs.microsoft.com/azure/app-service/
[HDInsight]: https://docs.microsoft.com/azure/hdinsight/hdinsight-overview
[EventHubs]: https://docs.microsoft.com/azure/event-hubs/event-hubs-about
[ServiceBus]: https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview
[azure-traffic-manager]: https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview
[Storage]: https://docs.microsoft.com/azure/storage/common/storage-introduction
[SQL]: https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview
[cosmos-db]: https://docs.microsoft.com/azure/cosmos-db/introduction
[IoT]: https://docs.microsoft.com/azure/iot-fundamentals/iot-introduction
[machine-learning]: https://docs.microsoft.com/azure/machine-learning/overview-what-is-azure-ml
