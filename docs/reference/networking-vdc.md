---
title: 'Centres de données virtuels : perspective réseau'
description: Découvrez comment créer un centre de données virtuel dans Azure.
author: tracsman
ms.author: jonor
ms.date: 06/12/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: e5729e592fe0e602d24e2e37831c782fada73128
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566687"
---
# <a name="virtual-datacenters-a-network-perspective"></a>Centres de données virtuels : perspective réseau

## <a name="overview"></a>Vue d'ensemble

La migration d’applications locales vers Azure permet aux organisations de bénéficier d’une infrastructure sécurisée et rentable, même si les applications sont migrées avec des changements minimes. Toutefois, pour tirer pleinement profit de l’agilité inhérente au cloud computing, les entreprises doivent faire évoluer leurs architectures de façon à exploiter au mieux les fonctionnalités d’Azure.

Microsoft Azure offre des services et une infrastructure hyperscale avec des fonctionnalités et une fiabilité de qualité professionnelle. De par les nombreuses options de connectivité hybride proposées, les clients peuvent accéder aux services et à l’infrastructure au moyen de l’Internet public ou d’une connexion Azure ExpressRoute privée. Les partenaires Microsoft offrent également des fonctionnalités améliorées en proposant des services de sécurité et des appliances virtuelles optimisées pour s’exécuter dans Azure.

Les clients peuvent choisir d’accéder à ces services cloud via Internet ou avec Azure ExpressRoute, qui fournit une connectivité réseau privée. La plateforme Microsoft Azure permet aux clients d’étendre leur infrastructure dans le cloud et de générer des architectures multiniveaux sans interruption. Les partenaires Microsoft offrent également des fonctionnalités améliorées en proposant des services de sécurité et des appliances virtuelles optimisées pour s’exécuter dans Azure.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-the-virtual-datacenter"></a>Qu’est-ce qu’un centre de données virtuel ?

À ses débuts, le cloud était essentiellement une plateforme destinée à l’hébergement des applications publiques. Petit à petit, les entreprises ont compris la valeur du cloud et ont commencé à migrer des applications métier internes vers le cloud. Ces types d’applications ont fait apparaître des considérations supplémentaires en matière de sécurité, de fiabilité, de performance et de coût, d’où la nécessité d’un mode de remise des services cloud plus flexible. De nouveaux services liés à l’infrastructure et au réseau ont donc vu le jour pour accroître le degré de flexibilité, ainsi que de nouvelles fonctionnalités de mise à l’échelle, de reprise d’activité après sinistre et autres.

Les solutions cloud ont d’abord été conçues pour héberger des applications uniques et relativement isolées dans le domaine public. Cette approche a donné de bons résultats pendant quelques années. Les avantages des solutions cloud sont ensuite devenus évidents, et plusieurs charges de travail à grande échelle ont été hébergées dans le cloud. Il s’est révélé crucial de résoudre les problèmes de sécurité, de fiabilité, de performances et de coûts des déploiements dans une ou plusieurs régions sur l’ensemble du cycle de vie du service cloud.

Le diagramme suivant de déploiement cloud montre un exemple de faille de sécurité, mis en surbrillance dans la zone rouge. La zone jaune indique qu’il est possible d’optimiser les appliances virtuelles réseau dans les charges de travail.

![0][0]

Un centre de données virtuel est un concept né de la nécessité de procéder à une mise à l’échelle pour gérer les charges de travail des entreprises, ainsi que de l’obligation de faire face aux problèmes induits par la prise en charge d’applications à grande échelle dans le cloud public.

Une implémentation de centre de données virtuel ne se résume pas simplement aux charges de travail d’application dans le cloud, mais englobe également le réseau, la sécurité, la gestion et l’infrastructure (par exemple, le DNS et les services d’annuaire). Plus une entreprise déplace de charges de travail vers Azure, plus il est important de réfléchir à l’infrastructure sous-jacente et aux objets dans lesquels ces charges de travail sont placées. Il convient d’envisager avec soin le mode de structuration des ressources afin d’éviter la prolifération de centaines d’« îlots de charge de travail » qui doivent être gérés séparément avec des flux de données, des modèles de sécurité et des problèmes de conformité indépendants.

Le concept de centre de données virtuel est un ensemble de suggestions et de bonnes pratiques conçues pour implémenter une collection d’entités distinctes mais liées, qui ont des fonctions, des fonctionnalités et une infrastructure communes. La visualisation de vos charges de travail à travers le centre de données virtuel vous permet d’alléger les coûts grâce aux économies d’échelle, à l’optimisation de la sécurité par le biais de la centralisation des composants et des flux de données, ainsi qu’à la simplification des opérations, de la gestion et des audits de conformité.

> [!NOTE]
> Il est important de comprendre qu’un centre de données virtuel **N’EST PAS** un produit Azure distinct, mais la combinaison de différentes fonctionnalités et capacités en vue de répondre précisément à vos exigences. Un centre de données virtuel est un moyen d’utiliser vos charges de travail et Azure pour optimiser vos ressources et capacités dans le cloud. Il constitue une approche modulaire permettant de créer des services informatiques dans Azure, tout en respectant les rôles et les responsabilités au sein de l’organisation.

Une implémentation de centre de données virtuel peut aider les entreprises à déplacer des charges de travail et des applications vers Azure dans les scénarios suivants :

- Héberger plusieurs charges de travail liées
- Migrer les charges de travail d’un environnement local vers Azure
- Implémenter les exigences de gestion partagée ou centralisée de la sécurité et des accès dans l’ensemble des charges de travail
- Combiner de manière appropriée Azure DevOps et la centralisation des services informatiques pour une grande entreprise

La clé permettant d’accéder aux avantages du centre de données virtuel repose sur l’utilisation d’une topologie réseau centralisée, de type « hub-and-spoke », avec un mélange de services et de fonctionnalités Azure :

- [Réseau virtuel Microsoft Azure][VNet]
- [Groupes de sécurité réseau][network-security-groups]
- [Peering de réseaux virtuels][VNetPeering]
- [Itinéraires définis par l’utilisateur][user-defined-routes]
- Identité Azure avec [contrôle d’accès en fonction du rôle (RBAC)][RBAC] et, éventuellement, les services [Pare-feu Azure][AzFW], [Azure DNS][DNS], [Azure Front Door][AFD] et [Azure Virtual WAN][vWAN].

## <a name="who-should-implement-a-virtual-datacenter"></a>Qui doit implémenter un centre de données virtuel ?

Tout client Azure ayant décidé d’adopter le cloud peut bénéficier des gains d’efficacité découlant de la configuration d’un ensemble de ressources mises en commun entre toutes les applications. En fonction de l’ampleur du projet, même les applications individuelles peuvent tirer parti des modèles et des composants utilisés pour générer une implémentation de centre de données virtuel.

Si votre organisation dispose d’équipes ou de services centralisés dédiés à l’informatique, au réseau, à la sécurité ou à la conformité, l’implémentation d’un centre de données virtuel peut faciliter l’application des points de stratégie, la répartition des tâches et garantir l’uniformité des composants communs sous-jacents tout en offrant aux équipes d’application le degré de liberté et de contrôle adapté à vos exigences.

Les organisations qui se tournent vers DevOps peuvent également utiliser les concepts du centre de données virtuel pour fournir des poches autorisées de ressources Azure et offrir l’assurance qu’elles disposent d’un contrôle total au sein de ce groupe (abonnement ou groupe de ressources dans un abonnement commun), tandis que les limites de réseau et de sécurité restent conformes aux définitions d’une stratégie centralisée dans un groupe de ressources et un réseau virtuel concentrateur.

<!-- markdownlint-enable MD026 -->

## <a name="considerations-for-implementing-a-virtual-datacenter"></a>Considérations relatives à l’implémentation d’un centre de données virtuel

Quand vous concevez l’implémentation d’un centre de données virtuel, vous devez prendre en compte plusieurs aspects cruciaux :

### <a name="identity-and-directory-service"></a>Services d’identité et d’annuaire

Les services d’identité et d’annuaire constituent un aspect clé de tous les centres de données, à la fois en local et dans le cloud. La notion d’identité est liée à tous les aspects des accès et des autorisations vis-à-vis des services au sein d’une implémentation de centre de données virtuel. Pour garantir que seuls les utilisateurs et processus autorisés auront accès à votre compte et à vos ressources Azure, Azure utilise plusieurs types d’informations d’identification pour l’authentification. Ces informations regroupent des mots de passe (pour l’accès au compte Azure), des clés de chiffrement, des signatures numériques et des certificats. [Azure Multi-Factor Authentication][multi-factor-authentication] est une couche de sécurité supplémentaire permettant d’accéder aux services Azure. Multi-Factor Authentication assure une authentification forte par le biais d’une série d’options de vérification simples (appel téléphonique, SMS ou notification d’application mobile) qui permet aux clients de choisir leur méthode préférée.

Toute grande entreprise doit définir un processus de gestion d’identité qui décrit la gestion des différentes identités, leur authentification, ainsi que les autorisations, rôles et privilèges dans leur implémentation d’un centre de données virtuel. Ce processus doit avoir pour fonction d’améliorer la sécurité et la productivité tout en minimisant les coûts, les temps d’arrêt et les tâches manuelles répétitives.

Les entreprises/organisations peuvent nécessiter une combinaison de services complexe pour différents métiers, et les employés assument fréquemment plusieurs rôles lorsqu’ils sont impliqués dans divers projets. Un centre de données virtuel requiert une coopération satisfaisante entre les différentes équipes, chacune dotée d’un rôle spécifique, afin de garantir le bon fonctionnement des systèmes avec une gouvernance adéquate. La matrice des responsabilités, des accès et des droits peut se révéler complexe. La gestion des identités dans le centre de données virtuel est implémentée par le biais d’[Azure Active Directory (Azure AD)][azure-ad] et du contrôle d’accès en fonction du rôle (RBAC).

Un service d’annuaire est une infrastructure d’informations partagée qui permet de localiser, de gérer, d’administrer et d’organiser les éléments et ressources réseau utilisés quotidiennement. Ces ressources peuvent inclure des volumes, des dossiers, des fichiers, des imprimantes, des utilisateurs, des groupes, des appareils et d’autres objets. Chacune des ressources du réseau est considérée comme un objet par le serveur d’annuaire. Les informations concernant une ressource sont stockées sous la forme d’une collection d’attributs associée à cette ressource ou à cet objet.

Tous les services professionnels Microsoft Online utilisent Azure Active Directory (Azure AD) pour l’authentification et les autres besoins d’identification. Azure Active Directory est une solution cloud complète et hautement disponible de gestion des identités et des accès qui associe des services d'annuaire principaux, une gouvernance avancée des identités et la gestion de l'accès aux applications. Il est possible d’intégrer Azure AD au service Active Directory local afin d’autoriser l’authentification unique pour toutes les applications cloud et hébergées localement. Les attributs utilisateur du service Active Directory local peuvent être automatiquement synchronisés avec Azure AD.

Il n’est pas nécessaire qu’un seul administrateur général affecte toutes les autorisations dans l’implémentation d’un centre de données virtuel. À la place, chaque service d’entreprise spécifique, groupe d’utilisateurs ou service dans le service d’annuaire peut disposer des autorisations nécessaires pour gérer ses propres ressources dans l’implémentation d’un centre de données virtuel. La structuration des autorisations doit être équilibrée. En effet, un nombre d’autorisations excessif risque de compromettre les performances, tandis que des autorisations insuffisantes ou trop flexibles sont susceptibles d’accroître les risques pour la sécurité. Le contrôle d’accès en fonction du rôle Azure (RBAC) contribue à résoudre ce problème en offrant une gestion affinée des accès aux ressources dans l’implémentation d’un centre de données virtuel.

#### <a name="security-infrastructure"></a>Infrastructure de sécurité

L’infrastructure de sécurité fait référence à la répartition du trafic dans le segment réseau virtuel spécifique l’implémentation d’un centre de données virtuel. Cette infrastructure spécifie la façon dont les flux d’entrée et de sortie sont contrôlés dans l’implémentation d’un centre de données virtuel. Azure repose sur une architecture multi-locataire qui empêche le trafic non autorisé et accidentel entre les déploiements au moyen de l’isolation VNET, de listes de contrôles d’accès (ACL), d’équilibreurs de charge, de filtres IP et de stratégies de flux de trafic. La traduction d’adresses réseau (NAT) sépare le trafic réseau interne du trafic externe.

La structure Azure alloue des ressources d’infrastructure aux charges de travail des locataires et gère les communications à destination et en provenance des machines virtuelles. L’hyperviseur Azure applique la séparation de mémoire et de processus entre les machines virtuelles, et route en toute sécurité le trafic réseau vers les locataires du système d’exploitation invité.

#### <a name="connectivity-to-the-cloud"></a>Connectivité avec le cloud

L’implémentation d’un centre de données virtuel nécessite une connectivité aux réseaux externes pour offrir des services aux clients, aux partenaires et aux utilisateurs internes. Il est donc nécessaire d’avoir une connectivité non seulement à Internet, mais aussi aux réseaux et centres de données locaux.

Les clients contrôlent les services ayant accès à l’Internet public et ceux accessibles à partir de l’Internet public via le [Pare-feu Azure][AzFW] ou d’autres types de NVA (appliance virtuelle réseau). Ils contrôlent également les stratégies de routage personnalisées à l’aide de [routes définies par l’utilisateur][user-defined-routes] ainsi que le filtrage réseau à l’aide de[ groupes de sécurité réseau][network-security-groups]. Nous recommandons de protéger également les ressources Internet via le service [Azure DDoS Protection Standard][DDoS].

Les entreprises peuvent avoir besoin de connecter leur implémentation de centre de données virtuel à des centres de données locaux ou à d’autres ressources. Cette connectivité entre Azure et les réseaux locaux est un aspect essentiel de la conception d’une architecture efficace. Pour créer cette interconnexion, les entreprises disposent de deux méthodes : transit par le biais d’Internet ou par des connexions directes privées.

Un [**réseau privé virtuel de site à site Azure**][VPN] est un service d’interconnexion sur Internet entre les réseaux locaux et une implémentation de centre de données virtuel, établi par l’intermédiaire de connexions chiffrées sécurisées (tunnels IPsec/IKE). La connexion site à site Azure est flexible et facile à créer et ne nécessite aucun approvisionnement supplémentaire, car toutes les connexions se connectent par le biais d’internet.

En cas de très nombreuses connexions VPN, le service réseau [**Azure Virtual WAN**][vWAN] offre une connectivité de branche à branche optimisée et automatisée par le biais d’Azure. Le WAN virtuel vous permet de vous connecter pour configurer des appareils de branche pour communiquer avec Azure. Vous pouvez effectuer cette connexion et cette configuration manuellement ou à l’aide d’appareils de fournisseurs favoris par le biais d’un partenaire Virtual WAN. L’utilisation d’appareils de fournisseurs favoris permet une utilisation facile, une simplification de la connectivité et une gestion de la configuration. Le tableau de bord intégré du WAN Azure fournit des informations de dépannage en temps réel qui peuvent vous faire gagner du temps et vous permettre d’afficher en toute simplicité la connectivité de site à site à grande échelle.

[**ExpressRoute**][ExR] est un service de connectivité Azure qui permet d’établir des connexions privées entre une implémentation de centre de données virtuel et n’importe quel réseau local. Les connexions ExpressRoute ne sont pas établies par l’intermédiaire du réseau public Internet et offrent un surcroît de sécurité et de fiabilité et des débits supérieurs (jusqu’à 10 Gbits/s), ainsi qu’une latence constante. ExpressRoute est utile pour les implémentations de centre de données virtuel, car les clients ExpressRoute peuvent bénéficier des règles de conformité associées aux connexions privées. Avec [ExpressRoute Direct][ExRD], vous pouvez vous connecter directement aux routeurs Microsoft à 100 Gbits/s pour les clients ayant des besoins en bande passante supérieurs.

Le déploiement de connexions ExpressRoute implique généralement la souscription d’un engagement auprès d’un fournisseur de services ExpressRoute. Les clients qui doivent être opérationnels rapidement commencent généralement par utiliser un VPN site à site pour établir la connectivité entre une implémentation de centre de données virtuel et les ressources locales, puis effectuent une migration vers une connexion ExpressRoute quand votre interconnexion physique avec votre fournisseur de services est établie.

#### <a name="connectivity-within-the-cloud"></a>*Connectivité au sein du cloud*

Les services de [VNET][VNet] et [VNET Peering][VNetPeering] sont les services de connectivité réseau de base au sein d’une implémentation de centre de données virtuel. Un VNET garantit une limite d’isolement naturelle pour les ressources du centre de données virtuel, et le VNET Peering permet l’intercommunication entre différents réseaux virtuels au sein de la même région Azure ou même de plusieurs régions. Le contrôle du trafic à l’intérieur d’un VNET et entre plusieurs VNET doit correspondre à un ensemble de règles de sécurité spécifiées par le biais des listes de contrôle d’accès ([groupes de sécurité réseau][network-security-groups]), d’[appliances virtuelles réseau][NVA] et de tables de routage personnalisées ([itinéraires définis par l’utilisateur][user-defined-routes]).

## <a name="virtual-datacenter-overview"></a>Vue d’ensemble du centre de données virtuel

### <a name="topology"></a>Topologie

*Hub-and-spoke* est un modèle permettant de concevoir la topologie réseau d’une implémentation de centre de données virtuel.

![1][1]

Comme illustré, deux types de conception Hub-and-spoke peuvent être utilisés dans Azure. Pour la communication, les ressources partagées et la stratégie de sécurité centralisée (« hub VNET » dans le diagramme), ou un type de réseau étendu virtuel (« Virtual WAN » dans le diagramme) pour les communications de branche à branche à grande échelle et de branche à Azure.

Un hub est la zone réseau centrale qui contrôle et inspecte le trafic d’entrée ou de sortie entre différentes zones : Internet, le réseau local et les spokes (rayons). La topologie hub-and-spoke offre au service informatique un moyen efficace d’appliquer des stratégies de sécurité à un emplacement central. Elle réduit également les risques de configuration incorrecte et d’exposition.

Le concentrateur contient généralement les composants de service communs consommés par les rayons. Voici des exemples de services centraux usuels :

- Infrastructure Windows Active Directory, nécessaire à l’authentification utilisateur des tiers qui souhaitent accéder aux charges de travail du rayon à partir de réseaux non approuvés. Elle inclut les services de fédération Active Directory (AD FS) associés.
- Service DNS destiné à résoudre le nommage pour la charge de travail dans les spokes et permettant d’accéder aux ressources locales et sur Internet si le service [Azure DNS][DNS] n’est pas utilisé.
- Infrastructure à clé publique (PKI) permettant d’implémenter l’authentification unique sur les charges de travail.
- Contrôle de flux du trafic TCP et UDP entre les zones du réseau à rayons et Internet.
- Contrôle de flux entre les rayons et les ressources locales.
- Si nécessaire, contrôle de flux entre un rayon et un autre.

Le cendre de données virtuel réduit le coût global au moyen de l’infrastructure de concentrateur partagée entre plusieurs rayons.

Le rôle de chaque rayon peut consister à héberger différents types de charges de travail. Les rayons offrent également une approche modulaire pour les déploiements renouvelables des mêmes charges de travail. C’est le cas, par exemple, des phases de développement et de test, de tests d’acceptation utilisateur, de préproduction et de production. Les rayons permettent également de séparer et d’activer différents groupes au sein de votre organisation. Les groupes Azure DevOps en sont un exemple. À l’intérieur d’un spoke, il est tout aussi possible de déployer une charge de travail de base que des charges de travail multiniveaux complexes avec un contrôle du trafic entre les différents niveaux.

#### <a name="subscription-limits-and-multiple-hubs"></a>Limites d’abonnement et concentrateurs multiples

Dans Azure, chacun des composants, quel qu’en soit le type, est déployé dans un abonnement Azure. L’isolement des composants Azure dans différents abonnements Azure peut satisfaire aux exigences de différents cœurs de métier, telles que la configuration de niveaux d’accès et d’autorisation différenciés.

Une implémentation de centre de données virtuel peut effectuer un scale-up pour atteindre un grand nombre de rayons ; toutefois, à l’instar de chaque système informatique, il existe des limites liées à la plateforme. Le déploiement d’un concentrateur est lié à un abonnement Azure spécifique, qui fait l’objet de restrictions et de limites, telles que le nombre maximal de VNET Peering (si vous souhaitez en savoir plus, veuillez consulter l’article [Abonnement Azure et limites, quotas et contraintes de service][limits]). Dans les cas où ces limites peuvent poser problème, il est possible de procéder à la montée en puissance de l’architecture en faisant évoluer un modèle hub-and-spoke unique vers un cluster constitué de plusieurs concentrateurs et rayons. Plusieurs concentrateurs situés dans une ou plusieurs régions Azure peuvent être interconnectés à l’aide de VNET Peering, d’ExpressRoute, de Virtual WAN ou d’un réseau VPN de site à site.

![2][2]

L’introduction de plusieurs hubs augmente les efforts liés au coût et à la gestion du système. Cela se justifie donc uniquement pour des raisons de scalabilité, pour étendre les limites du système ou à des fins de redondance ainsi que dans le cadre d’une réplication régionale, pour fournir un niveau de performance à l’utilisateur final ou une reprise d’activité. Dans les scénarios qui nécessitent plusieurs concentrateurs, ces derniers doivent tous, dans la mesure du possible, offrir le même ensemble de services afin d’en faciliter l’exploitation.

#### <a name="interconnection-between-spokes"></a>Interconnexion entre les rayons

Il est possible d’implémenter des charges de travail multiniveau complexes à l’intérieur d’un même rayon. Les configurations multiniveau peuvent être implémentées à l’aide de sous-réseaux (un pour chaque niveau) dans le même réseau virtuel, ainsi qu’au moyen d’un filtrage des flux par l’intermédiaire de groupes de sécurité réseau.

Un architecte peut vouloir déployer une charge de travail multiniveau sur plusieurs réseaux virtuels. Avec le peering de réseaux virtuels, vous pouvez connecter des rayons à d’autres rayons du même hub ou de hubs distincts. Ce scénario s’applique généralement aux cas où les serveurs de traitement d’application sont situés dans un même rayon ou réseau virtuel. La base de données est déployée sur un autre rayon ou réseau virtuel. Dans ce cas, il est facile d’interconnecter les rayons avec le peering de réseaux virtuels et d’éviter ainsi le transit par le hub. Toutefois, il convient d’étudier avec soin l’architecture et la sécurité pour vérifier que le contournement du hub n’élude pas de points de sécurité ou d’audit importants susceptibles d’exister uniquement dans le hub.

![3][3]

Il est également possible d’interconnecter des rayons à un rayon jouant le rôle de concentrateur. Cette approche crée une hiérarchie à deux niveaux : le spoke du niveau supérieur (niveau 0) devient le hub de spokes inférieurs (niveau 1) dans la hiérarchie. Les spokes d’une implémentation de centre de données virtuel doivent transférer le trafic vers le hub central pour que le trafic puisse atteindre sa destination sur le réseau local ou l’Internet public. Une architecture à deux niveaux de hubs introduit un routage complexe qui supprime les avantages d’une relation hub-and-spoke simple.

Bien qu’Azure autorise des topologies complexes, les deux principes fondamentaux du concept de centre de données virtuel sont la répétabilité et la simplicité. Pour réduire l’effort de gestion, la conception d’une topologie hub-and-spoke simple est l’architecture de référence que nous recommandons pour un centre de données virtuel.

### <a name="components"></a>Composants

Un centre de données virtuel est constitué de quatre types de composant de base : l’**infrastructure**, les **réseaux de périmètre**, les **charges de travail** et la **supervision**.

Chaque type de composant intègre plusieurs ressources et fonctionnalités Azure. Votre implémentation de centre de données virtuel est constituée d’instances de plusieurs types de composants et de diverses variantes du même type de composant. Par exemple, vous pouvez disposer de nombreuses instances de charge de travail distinctes, séparées de façon logique, qui représentent différentes applications. Utilisez ces différents types de composants et instances afin de générer le centre de données virtuel.

![4][4]

L’architecture conceptuelle de haut niveau du centre de données virtuel ci-dessus représente différents types de composants utilisés dans diverses zones de la topologie hub-and-spoke. Le diagramme illustre les composants d’infrastructure dans les différentes parties de l’architecture.

En général, une bonne pratique consiste à baser les droits d’accès et les privilèges sur un groupe. Utilisez des groupes, plutôt que des utilisateurs individuels, pour maintenir une gestion cohérente des stratégies d’accès entre les équipes et réduire les erreurs de configuration. L’attribution et la suppression d’utilisateurs dans les groupes appropriés facilitent l’actualisation continue des privilèges d’un utilisateur spécifique.

Chaque groupe de rôles doit avoir un préfixe unique pour ses noms. Ce préfixe permet d’identifier facilement le groupe associé à une charge de travail spécifique. Par exemple, une charge de travail hébergeant un service d’authentification peut être associée à des groupes appelés **AuthServiceNetOps**, **AuthServiceSecOps**, **AuthServiceDevOps** et **AuthServiceInfraOps**. Les rôles centralisés ou les rôles non associés à un service spécifique peuvent être précédés de **Corp**. Exemple : **CorpNetOps**.

De nombreuses organisations utilisent une variante des groupes ci-après pour procéder à une répartition générale des rôles :

- Le groupe du service informatique central, **Corp,** , détient les droits de propriété permettant de contrôler les composants d’infrastructure. Exemples : réseau et sécurité. Le groupe doit avoir le rôle de contributeur pour l’abonnement, le contrôle du hub et les droits de contributeur réseau sur les rayons. Les grandes organisations divisent souvent ces responsabilités de gestion entre plusieurs équipes. C’est le cas, par exemple, pour un groupe d’opérations réseau **CorpNetOps**, exclusivement axé sur le réseau, et pour un groupe d’opérations de sécurité **CorpSecOps**, responsable de la stratégie de pare-feu et de sécurité. Dans ce cas précis, il convient de créer deux groupes distincts pour l’attribution de ces rôles personnalisés.
- Le groupe de développement/test, **AppDevOps,** , est responsable du déploiement des charges de travail d’application ou de service. Ce groupe joue le rôle de contributeur de machine virtuelle pour les déploiements IaaS. Il peut également jouer un ou plusieurs rôles de contributeur PaaS. Si vous souhaitez en savoir plus, veuillez consulter [Rôles intégrés pour les ressources Azure][Roles]. Éventuellement, l’équipe de développement/test peut avoir besoin de visibilité sur les stratégies de sécurité (groupes de sécurité réseau) et les stratégies de routage (itinéraires définis par l’utilisateur) dans le hub ou un rayon spécifique. En plus du rôle de contributeur pour les charges de travail, ce groupe nécessite également le rôle de lecteur de réseau.
- Le groupe des opérations et de la maintenance, **CorpInfraOps** ou **AppInfraOps**, est chargé de gérer les charges de travail en production. Ce groupe doit être un contributeur d’abonnement sur les charges de travail dans tous les abonnement de production. Certaines organisations peuvent également déterminer si elles ont besoin d’un groupe supplémentaire de type équipe du support technique pour la prise en charge du processus d’escalade avec le rôle de contributeur d’abonnement en production ainsi que l’abonnement au hub central. Le groupe supplémentaire corrige les problèmes de configuration potentiels dans l’environnement de production.

Le centre de données virtuel est conçu de telle sorte que les groupes créés pour le groupe du service informatique central gérant le hub aient des groupes correspondants au niveau de la charge de travail. Outre la gestion des ressources du hub, le groupe du service informatique central peut contrôler l’accès externe et les autorisations de niveau supérieur sur l’abonnement. Les groupes de charge de travail peuvent également contrôler les ressources et les autorisations de leur réseau virtuel indépendamment du groupe du service informatique central.

Un centre de données virtuel est partitionné pour héberger de manière sécurisée plusieurs projets appartenant à différents métiers. Tous les projets nécessitent plusieurs environnements isolés (développement, test d’acceptation utilisateur (UAT), production). Les abonnements Azure distincts pour chacun de ces environnements assurent un isolement naturel.

![5][5]

Le diagramme précédent illustre la relation entre les projets, les utilisateurs et les groupes d’une organisation, et les environnements dans lesquels les composants Azure sont déployés.

Dans le contexte informatique, un environnement (ou niveau) désigne généralement un système dans lequel plusieurs applications sont déployées et exécutées. Les grandes entreprises utilisent un environnement de développement (dans lequel les modifications sont effectuées et testées) et un environnement de production (destiné aux utilisateurs finaux). Ces environnements sont séparés, le plus souvent par des environnements intermédiaires, afin d’autoriser l’échelonnement des phases de déploiement (lancement), de test et de restauration en cas de problème. Les architectures de déploiement varient sensiblement, mais le processus de base qui consiste à commencer par le niveau développement (DEV) et à terminer par le niveau production (PROD) reste généralement appliqué.

Une architecture communément employée pour ces types d’environnement multiniveau comprend les environnements Azure DevOps pour le développement et les tests, UAT pour la préproduction, et les environnements de production. Les organisations peuvent tirer profit d’un ou de plusieurs locataires Azure AD afin de définir l’accès et les droits pour ces environnements. Le diagramme précédent illustre un cas d’utilisation de deux locataires Azure AD distincts : l’un pour Azure DevOps et UAT, et l’autre exclusivement destiné à la production.

La présence de différents locataires Azure AD met en œuvre la séparation entre les environnements. Le même groupe d’utilisateurs, par exemple le groupe du service informatique central, doit s’authentifier à l’aide d’un URI distinct pour accéder à un autre locataire Azure AD et modifier les rôles ou autorisations des environnements Azure DevOps ou de production d’un projet. L’utilisation d’authentifications utilisateur distinctes pour accéder à différents environnements réduit les éventuelles interruptions et autres problèmes dus à des erreurs humaines.

#### <a name="component-type-infrastructure"></a>Type de composant : Infrastructure

Ce type de composant est l’endroit où réside la majeure partie de l’infrastructure sous-jacente. Il s’agit également du composant auquel vos équipes d’informatique centralisée, de sécurité et de conformité consacrent la majorité de leur temps.

![6][6]

Les composants d’infrastructure assurent une interconnexion pour les différents composants d’une implémentation de centre de données virtuel et sont présents à la fois dans le hub et dans les rayons. La responsabilité de la gestion et de la maintenance des composants d’infrastructure est généralement attribuée à l’équipe du service informatique central ou de la sécurité.

L’une des principales tâches de l’équipe d’infrastructure informatique consiste à garantir la cohérence des schémas d’adresse IP dans l’ensemble de l’entreprise. L’espace d’adressage IP privé attribué à une implémentation de centre de données virtuel doit être cohérent et NE PAS chevaucher les adresses IP privées affectées sur vos réseaux locaux.

Bien que la traduction d’adresses réseau (NAT) sur les routeurs de périphérie locaux ou dans les environnements Azure permette d’éviter les conflits d’adresses IP, elle ajoute de la complexité à vos composants d’infrastructure. L’une des finalités clés d’un centre de données virtuel étant de simplifier la gestion, l’utilisation du processus NAT pour gérer les problèmes liés aux adresses IP n’est pas recommandée.

Les composants d’infrastructure ont les fonctionnalités suivantes :

- [**Services d’identité et d’annuaire**][azure-ad]. L’accès à chaque type de ressource dans Azure est contrôlé par une identité stockée dans un service d’annuaire. Le service d’annuaire stocke non seulement la liste des utilisateurs, mais également les droits d’accès aux ressources dans un abonnement Azure spécifique. Ces services peuvent exister uniquement dans le cloud, ou être synchronisés avec l’identité locale stockée dans Active Directory.
- [**Réseau virtuel**][VPN]. Les réseaux virtuels sont l’un des principaux composants d’un centre de données virtuel et vous permettent de créer une limite d’isolation du trafic sur la plateforme Azure. Un réseau virtuel est constitué d’un ou de plusieurs segments de réseau virtuel, chacun étant doté d’un préfixe de réseau IP (sous-réseau) spécifique. Le réseau virtuel définit une zone de périmètre interne dans laquelle les machines virtuelles IaaS et les services PaaS peuvent établir des communications privées. Les machines virtuelles (et les services PaaS) figurant dans un réseau virtuel ne peuvent pas communiquer directement avec les machines virtuelles (et les services PaaS) d’un autre réseau virtuel, même si ces deux réseaux virtuels sont créés par le même client, dans le cadre du même abonnement. Cet isolement est une propriété critique qui garantit que les machines virtuelles et les communications du client restent privées dans un réseau virtuel.
- [**Itinéraires définis par l’utilisateur**][user-defined-routes]. Le routage du trafic dans un réseau virtuel repose par défaut sur la table de routage système. Un itinéraire défini par l’utilisateur est une table de routage personnalisée que les administrateurs réseau peuvent associer à un ou plusieurs sous-réseaux pour remplacer le comportement de la table de routage système et définir un chemin de communication au sein d’un réseau virtuel. L’existence d’itinéraires définis par l’utilisateur garantit que le trafic de sortie en provenance du rayon transite par des machines virtuelles personnalisées et des appliances virtuelles réseau, ainsi que des équilibreurs de charge spécifiques présents dans le hub et dans les rayons.
- [**Groupes de sécurité réseau**][network-security-groups]. Un groupe de sécurité réseau est une liste de règles de sécurité qui fait office de filtrage du trafic sur les sources IP, les destinations IP, les protocoles, les ports sources IP et les ports de destination IP. Le groupe de sécurité réseau peut être appliqué à un sous-réseau et/ou à une carte réseau virtuelle associée à une machine virtuelle Azure. Les groupes de sécurité réseau jouent un rôle essentiel dans l’implémentation d’un contrôle de flux approprié dans le hub et les rayons. Le niveau de sécurité offert par le groupe de sécurité réseau dépend des ports que vous ouvrez et du but dans lequel vous le faites. Les clients doivent appliquer des filtres supplémentaires par machine virtuelle avec des pare-feu basés sur l’hôte, tels qu’IPtables ou le Pare-feu Windows.
- [**DNS**][DNS]. La résolution de noms des ressources dans les réseaux virtuels d’une implémentation de centre de données virtuel est assurée par le biais de DNS. Azure fournit des services DNS pour la résolution de noms [publics][DNS] et [privés][PrivateDNS]. Les zones privées fournissent la résolution de noms au sein d’un réseau virtuel, ainsi qu’entre des réseaux virtuels. Vous pouvez avoir des zones privées entre plusieurs réseaux virtuels au sein de la même région, mais aussi entre plusieurs régions et abonnements. Pour la résolution publique, Azure DNS fournit un service d’hébergement pour les domaines DNS qui offre une résolution de noms à l’aide de l’infrastructure Microsoft Azure. En hébergeant vos domaines dans Azure, vous pouvez gérer vos enregistrements DNS avec les mêmes informations d’identification, les mêmes API, les mêmes outils et la même facturation que vos autres services Azure.
- [**Abonnement**][SubMgmt] et [**Gestion des groupes de ressources**][RGMgmt]. Un abonnement définit une limite naturelle permettant de créer plusieurs groupes de ressources dans Azure. Les ressources d’un abonnement sont regroupées dans des conteneurs logiques nommés groupes de ressources. Le groupe de ressources représente un groupe logique destiné à organiser les ressources d’une implémentation de centre de données virtuel.
- [**Contrôle d’accès en fonction du rôle (RBAC)** ][RBAC]. Le mécanisme RBAC permet de mapper un rôle organisationnel sur des droits d’accès à des ressources Azure spécifiques, ce qui vous donne la possibilité de restreindre les utilisateurs à un sous-ensemble d’actions. Avec RBAC, vous pouvez accorder l’accès en attribuant le rôle approprié à des utilisateurs, groupes et applications dans l’étendue adéquate. L’étendue d’une attribution de rôle peut être un abonnement Azure, un groupe de ressources ou une ressource unique. Le mécanisme RBAC autorise l’héritage des autorisations. Un rôle attribué à une étendue parent accorde également l’accès aux enfants qu’elle contient. RBAC vous permet de séparer les tâches et d’accorder aux utilisateurs uniquement les accès dont ils ont besoin pour accomplir leur travail. Par exemple, utilisez RBAC pour autoriser un employé à gérer les machines virtuelles d’un abonnement, et pour permettre à un autre employé de gérer les bases de données SQL au sein du même abonnement.
- [**VNET Peering**][VNetPeering]. La fonctionnalité fondamentale utilisée pour créer l’infrastructure du centre de données virtuel est VNET Peering, un mécanisme qui connecte deux réseaux virtuels de la même région par le biais du réseau du centre de données Azure, ou bien en utilisant la dorsale (backbone) mondiale de Azure entre plusieurs régions.

#### <a name="component-type-perimeter-networks"></a>Type de composant : Réseaux de périmètre

Les composants de type [Réseau de périmètre][DMZ] permettent d’établir une connectivité réseau entre les réseaux de vos centres de données locaux ou physiques ainsi qu’une connectivité à destination et en provenance d’Internet. Il s’agit également des composants auxquels vos équipes réseau et sécurité consacrent généralement la majorité de leur temps.

Les paquets entrants doivent transiter par les appliances de sécurité du hub avant d’atteindre les serveurs back-end dans les rayons. Exemples : pare-feu, systèmes de détection et de prévention d’intrusion. Avant de quitter le réseau, les paquets Internet des charges de travail doivent également transiter par les appliances de sécurité du réseau de périmètre. Les finalités de ce flux sont la mise en œuvre, l’inspection et l’audit des stratégies.

Les composants de type réseau de périmètre fournissent les fonctionnalités suivantes :

- [des réseaux virtuels][VNet], [des itinéraires définis par l’utilisateur][user-defined-routes] et [des groupes de sécurité réseau][network-security-groups]
- [Appliances virtuelles réseau][NVA]
- [Équilibrage de charge Azure][ALB]
- [Azure Application Gateway][AppGW] avec [pare-feu d'applications web (WAF)][AppGWWAF]
- [Adresses IP publiques][PIP]
- [Azure Front Door][AFD] avec [pare-feu d’applications web (WAF)][AFDWAF]
- [Pare-feu Azure][AzFW]

En règle générale, les équipes du service informatique central et de la sécurité sont chargées de la définition des exigences et du fonctionnement des réseaux de périmètre.

![7][7]

Le diagramme précédent illustre l’application de deux périmètres avec un accès à Internet et à un réseau local, ces deux périmètres résidant dans le hub DMZ. Dans le hub DMZ, le réseau de périmètre vers Internet peut monter en puissance pour prendre en charge une multitude d’applications métier, à l’aide de plusieurs batteries de pare-feu d’applications web (WAF) et de Pare-feu Azure. Le hub permet également une connectivité via un VPN ou ExpressRoute le cas échéant.

[**Réseaux virtuels**][VNet]. Le hub repose généralement sur un réseau virtuel comprenant plusieurs sous-réseaux pour héberger les différents types de service qui filtrent et inspectent le trafic à destination ou en provenance d’Internet via les instances NVA, WAF et Azure Application Gateway.

[**Itinéraires définis par l’utilisateur**][user-defined-routes] Ces itinéraires permettent aux clients de déployer des pare-feu, des systèmes de détection et de prévention d’intrusion et d’autres appliances virtuelles, et de router le trafic réseau à travers ces appliances de sécurité à des fins d’application de stratégies de limites de sécurité, d’audit et d’inspection. Les itinéraires définis par l’utilisateur peuvent être créés à la fois dans le hub et dans les rayons pour garantir que le trafic transite par des machines virtuelles personnalisées, des appliances virtuelles réseau et des équilibreurs de charge spécifiques utilisés par une implémentation de centre de données virtuel. Pour garantir que le trafic généré à partir de machines virtuelles figurant dans le rayon transite par les appliances virtuelles correctes, il convient de configurer un itinéraire défini par l’utilisateur dans les sous-réseaux du rayon en définissant l’adresse IP frontale de l’équilibreur de charge interne en tant que tronçon suivant. L’équilibreur de charge interne distribue le trafic interne vers les appliances virtuelles (pool principal d’équilibreur de charge).

Le [**Pare-feu Azure**][AzFW] est un service de sécurité réseau informatique managé qui protège vos ressources Réseau virtuel Azure. Il s’agit d’un service de pare-feu avec état intégral, doté d’une haute disponibilité intégrée et d’une scalabilité illimitée dans le cloud. Vous pouvez créer, appliquer et consigner des stratégies de connectivité réseau et d’application de façon centralisée entre les abonnements et les réseaux virtuels. Le service Pare-feu Azure utilise une adresse IP publique statique pour vos ressources de réseau virtuel. Il permet aux pare-feu externes d’identifier le trafic provenant de votre réseau virtuel. Le service est totalement intégré à Azure Monitor pour la journalisation et les analyses.

[**Appliances virtuelles réseau**][NVA]. Dans le hub, le réseau de périmètre disposant d’un accès à Internet est normalement géré via une instance de Pare-feu Azure, une batterie de pare-feu ou WAF (pare-feu d’applications web).

Les différents métiers utilisent habituellement de nombreuses applications web. Ces applications ont tendance à comporter diverses vulnérabilités face aux attaques potentielles. Les pare-feu d’applications web sont un type de produit particulier qui permet de détecter les attaques contre les applications web (HTTP/HTTPS) de façon plus approfondie qu’un pare-feu générique. Contrairement à la technologie de pare-feu classique, les WAF intègrent un ensemble de fonctionnalités spécifiques pour protéger les serveurs web internes contre les menaces.

Un pare-feu Azure ou NVA utilise un plan d’administration commune, avec un ensemble de règles de sécurité, pour non seulement protéger les charges de travail hébergées dans les rayons, mais aussi contrôler l’accès aux réseaux locaux. Le Pare-feu Azure dispose d’une fonctionnalité d’extensibilité intégrée, alors que les pare-feux NVA peuvent être manuellement mis à l’échelle derrière un équilibreur de charge. En règle générale, une batterie de pare-feu est équipée de logiciels moins spécialisés qu’un WAF, mais dispose d’un vaste champ d’application permettant de filtrer et d’inspecter n’importe quel type de trafic en entrée et en sortie. Si une approche NVA est appliquée, les pare-feu peuvent être trouvés et déployés à partir de la Place de marché Azure.

Utilisez un ensemble de pare-feu Azure (ou NVA) pour le trafic provenant d’Internet, et un autre ensemble pour le trafic émanant du niveau local. L’utilisation d’un seul ensemble de pare-feu pour ces deux types de trafics réseau constitue un risque pour la sécurité, car elle n’offre aucun périmètre de sécurité entre les deux. L’utilisation de couches distinctes de pare-feu simplifie la vérification des règles de sécurité et permet d’identifier clairement les règles auxquelles correspondent les différentes demandes réseau entrantes.

Nous vous recommandons d’utiliser un ensemble d’instances de Pare-feu Azure, ou NVA, pour le trafic provenant d’Internet. Utilisez-en un autre pour le trafic local. L’utilisation d’un seul ensemble de pare-feu pour ces deux types de trafic réseau constitue un risque pour la sécurité, car elle n’offre aucun périmètre de sécurité entre les deux. L’utilisation de couches de pare-feu distinctes simplifie la vérification des règles de sécurité et permet d’identifier clairement les règles auxquelles correspondent les différentes requêtes réseau entrantes.

[**Azure Load Balancer**][ALB] offre un service haute disponibilité de couche 4 (TCP/UDP), qui peut distribuer le trafic entrant entre des instances de service définies dans un jeu à charge équilibrée. Le trafic envoyé à l’équilibreur de charge à partir de points de terminaison frontaux (points de terminaison IP publics ou privés) peut être redistribué avec ou sans traduction d’adresses à un ensemble d’un pool d’adresses IP principal (par exemple, des appliances virtuelles réseau ou des machines virtuelles).

Azure Load Balancer peut également analyser à l’aide de sondes l’intégrité des différentes instances de serveur ; si l’une des instances ne répond pas à une sonde, l’équilibreur de charge arrête d’envoyer le trafic à l’instance défaillante correspondante. Dans le centre de données virtuel, un équilibreur de charge externe est déployé sur le hub et les rayons. Dans le hub, l’équilibreur de charge est utilisé pour router efficacement le trafic vers des services dans les rayons. Dans ces derniers, les équilibreurs de charge sont utilisés pour gérer le trafic des applications.

[Azure Front Door (AFD)][AFD] est une plateforme d’accélération d’applications web scalable à haute disponibilité, intégrant un équilibreur de charge HTTP global, la protection d’application et le réseau de distribution de contenu. En s’exécutant dans plus de 100 emplacements au niveau de la périphérie du réseau global de Microsoft, AFD vous permet de générer et de faire fonctionner votre application web dynamique et votre contenu statique. Vous pouvez aussi effectuer un scale-out de ces derniers. AFD fournit à votre application des performances d’utilisateur final très élevées, l’automatisation de la maintenance de région/d’horodatage unifiée, l’automatisation de la continuité d’activité et de la reprise d’activité, des informations client/utilisateur unifiées, ainsi que des insights sur la mise en cache et les services. La plateforme offre des SLA relatifs aux performances, à la fiabilité et au support, des certifications de conformité et des pratiques de sécurité vérifiables, dont le développement, la mise en œuvre et la prise en charge sont effectués de manière native par Azure.

[**Application Gateway**][AppGW] Microsoft Azure Application Gateway est une appliance virtuelle dédiée qui intègre Application Delivery Controller (ADC) en tant que service, offrant ainsi diverses fonctionnalités d’équilibrage de charge de couche 7 pour votre application. Cette appliance vous permet d’optimiser la productivité de la batterie de serveurs Web en déchargeant une terminaison SSL nécessitant de nombreuses ressources du processeur vers la passerelle Application Gateway. Elle fournit également d’autres fonctionnalités de routage de couche 7, notamment la distribution en tourniquet (round robin) du trafic entrant, l’affinité de session basée sur les cookies, le routage basé sur le chemin d’accès de l’URL et la possibilité d’héberger plusieurs sites web derrière une seule passerelle Application Gateway. Un pare-feu d’applications web (WAF) est également intégré à la référence SKU Application Gateway WAF. Cette référence SKU protège les applications web contre les vulnérabilités et les codes malveillants exploitant une faille de sécurité les plus courants sur le web. La passerelle Application Gateway peut être configurée en tant que passerelle internet, passerelle interne uniquement ou une combinaison des deux.

[**Adresses IP publiques**][PIP]. Avec certaines fonctionnalités Azure, vous pouvez associer des points de terminaison de service à une adresse IP publique, pour que votre ressource soit accessible à partir d’Internet. Ce point de terminaison utilise NAT (traduction d’adresses réseau) pour router le trafic vers l’adresse et le port internes sur le réseau virtuel Azure. Il s’agit du principal chemin d’accès pour que le trafic externe passe dans le réseau virtuel. Vous pouvez configurer des adresses IP publiques pour déterminer le type de trafic passé ainsi que la façon dont la traduction s’opère sur le réseau virtuel et son emplacement précis.

Le service [**Azure DDoS Protection Standard**][DDoS] fournit des fonctionnalités d’atténuation supplémentaires par rapport au niveau de service [De base][DDoS] qui sont destinées spécifiquement aux ressources de réseau virtuel Azure. Le service DDoS Protection Standard est facile à activer et ne nécessite aucun changement de l’application. Les stratégies de protection sont paramétrées par le biais d’algorithmes de surveillance du trafic et d’apprentissage automatique dédiés. Ces stratégies sont appliquées aux adresses IP publiques associées aux ressources déployées sur des réseaux virtuels. Exemples : instances Azure Load Balancer, Azure Application Gateway et Azure Service Fabric. Les données de télémétrie en temps réel sont disponibles par le biais d’affichages Azure Monitor pendant une attaque et à des fins d’historique. Vous pouvez ajouter une protection de la couche Application via le pare-feu d’applications web Azure Application Gateway. La protection est assurée pour les adresses IP publiques IPv4 Azure.

#### <a name="component-type-monitoring"></a>Type de composant : Surveillance

Les composants de surveillance offrent une vue d’ensemble de tous les autres types de composants et génèrent des alertes concernant ces derniers. Toutes les équipes doivent avoir accès à la surveillance des composants et services qui leur sont accessibles. Si vous disposez d’équipes des opérations ou d’un support technique centralisé, ils doivent disposer d’un accès intégré aux données fournies par ces composants.

Azure propose différents types de service de journalisation et de supervision pour effectuer le suivi du comportement des ressources hébergées par Azure. La gouvernance et le contrôle des charges de travail dans Azure reposent non seulement sur la collecte des données de journalisation, mais également sur le déclenchement d’actions en fonction d’événements signalés spécifiques.

[**Azure Monitor**][Monitor]. Azure comprend plusieurs services qui effectuent individuellement un rôle ou une tâche spécifique dans l’espace d’analyse. Ensemble, ces services fournissent une solution complète pour la collecte, l’analyse et l’action sur les données de télémétrie de votre application et des ressources Azure qui les prennent en charge. Ces services peuvent aussi surveiller les ressources locales critiques afin de fournir un environnement de surveillance hybride. Comprendre les outils et les données disponibles est la première étape du développement d’une stratégie de surveillance complète pour votre application.

Il existe deux principaux types de journaux d’activité dans Azure :

- Le [Journal d’activité Azure][ActLog], auparavant connu sous le nom de **Journaux d’activité des opérations**, fournit un aperçu des opérations effectuées sur les ressources de l’abonnement Azure. Ces journaux d’activité signalent les événements de plan de contrôle relatifs à vos abonnements. Chaque ressource Azure génère des journaux d’audit.

- Les [journaux de diagnostic Azure Monitor][DiagLog] sont des journaux d’activité générés par une ressource qui fournit des données fréquentes et détaillées sur le fonctionnement de cette ressource. Le contenu de ces journaux d’activité varie en fonction du type de ressource.

![9][9]

Nous vous conseillons de suivre les journaux des groupes de sécurité réseau, en tenant particulièrement compte des informations suivantes :

- Les [journaux des événements][nsg-log] fournissent des informations sur les règles des groupes de sécurité réseau appliquées aux machines virtuelles et aux rôles d’instance en fonction de l’adresse MAC.
- Les [journaux d’activité de compteur][nsg-log] indiquent le nombre d’exécutions de chaque règle de groupe de sécurité réseau pour refuser ou autoriser le trafic.

Tous les journaux d’activité peuvent être stockés dans des comptes de stockage Azure à des fins d’audit, d’analyse statique ou de sauvegarde. Quand vous stockez les journaux d’activité dans un compte de stockage Azure, les clients peuvent utiliser différents types de framework pour récupérer, préparer, analyser et visualiser ces données afin de signaler l’état et l’intégrité des ressources cloud.

Les grandes entreprises doivent avoir acquis au préalable un framework standard pour la supervision des systèmes locaux. Ils peuvent étendre ce framework pour intégrer les journaux d’activité générés par les déploiements cloud. Avec [Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-queries), les organisations peuvent conserver l’ensemble de la journalisation dans le cloud. Log Analytics est implémenté en tant que service cloud. Il peut donc être opérationnel rapidement, avec un investissement minimal dans les services d’infrastructure. Log Analytics s’intègre également aux composants System Center, tels que System Center Operations Manager, pour étendre au cloud vos investissements de gestion existants.

Log Analytics est un service dans Azure conçu pour faciliter la collecte, la mise en corrélation, la recherche et l’exploitation des données de journalisation et de performances générées par les systèmes d’exploitation, les applications et les composants cloud d’infrastructure. Ce composant vous offre des informations opérationnelles en temps réel à l’aide d’une fonction de recherche intégrée et de tableaux de bord personnalisés, qui vous permettent d’analyser tous les enregistrements de l’ensemble de vos charges de travail dans votre implémentation de centre de données virtuel.

[Azure Network Watcher][NetWatch] fournit des outils permettant d’effectuer une supervision et des diagnostics, d’afficher les métriques et d’activer ou de désactiver les journaux d’activité des ressources d’un réseau virtuel Azure. Il s’agit d’un service multifacette qui permet d’accéder aux fonctionnalités suivantes et à bien d’autres encore :

- Superviser la communication entre une machine virtuelle et un point de terminaison
- Afficher les ressources se trouvant sur un réseau virtuel et leurs relations
- Diagnostiquer les problèmes de filtrage du trafic réseau à destination ou en provenance d’une machine virtuelle
- Diagnostiquer les problèmes de routage réseau d’une machine virtuelle
- Diagnostiquer les connexions sortantes d’une machine virtuelle
- Capturer les paquets à destination et en provenance d’une machine virtuelle
- Diagnostiquer les problèmes liés à une passerelle de réseau virtuel Azure et aux connexions
- Déterminer les latences relatives entre les régions Azure et les fournisseurs de services Internet
- Afficher les règles de sécurité d’une interface réseau
- Afficher les métriques réseau
- Analyser le trafic à destination ou en provenance d’un groupe de sécurité réseau
- Afficher les journaux de diagnostic des ressources réseau

La solution [Network Performance Monitor][NPM] dans Operations Management Suite peut fournir des informations détaillées sur le réseau, de bout en bout. Ces informations incluent une seule vue de vos réseaux Azure et de vos réseaux locaux. La solution dispose de fonctionnalités de supervision spécifiques pour ExpressRoute et les services publics.

#### <a name="component-type-workloads"></a>Type de composant : Charges de travail

Les composants de type charge de travail désignent l’emplacement où résident vos applications et services proprement dits. Il s’agit également du composant auquel vos équipes de développement d’applications consacrent la majorité de leur temps.

Les possibilités de charge de travail sont illimitées. Voici quelques-uns des innombrables types de charges de travail possibles :

**Applications métier internes :** Les applications métiers sont des applications informatiques cruciales pour le fonctionnement continu d’une entreprise. Les applications métiers présentent certaines caractéristiques en commun :

- **Interactives par nature :** Une fois que vous avez entré des données, des résultats ou des rapports sont retournés.
- **Pilotées par les données :** Charges de travail gourmandes en données avec accès fréquent aux bases de données ou à d’autres types de stockage.
- **Intégrées :** Charges de travail offrant une intégration avec d’autres systèmes au sein ou en dehors de l’organisation.

**Sites web destinés aux clients (accessibles par Internet ou en interne) :** La plupart des applications qui interagissent avec Internet sont des sites web. Azure permet d’exécuter un site web sur une machine virtuelle IaaS ou à partir d’un site [Azure Web Apps][WebApps] (PaaS). Azure Web Apps prend en charge l’intégration à des réseaux virtuels permettant le déploiement des applications web dans la zone réseau d’un rayon. Les sites web internes n’ont pas besoin d’exposer un point de terminaison Internet public, car les ressources sont accessibles par le biais d’adresses routables non-Internet privées à partir du réseau virtuel privé.

**Big Data et Analytics :** En cas de scale-up lié à un volume de données très important, il peut arriver que le scale-up des bases de données ne s’effectue pas correctement. La technologie Hadoop offre un système permettant d’exécuter des requêtes distribuées en parallèle sur un grand nombre de nœuds. Les clients ont la possibilité d’exécuter des charges de travail de données dans des machines virtuelles IaaS ou PaaS ([HDInsight][HDI]). HDInsight prend en charge le déploiement dans un réseau virtuel basé sur l’emplacement et peut être déployé sur un cluster dans un rayon du centre de données virtuel.

**Événements et messagerie :** [Azure Event Hubs][EventHubs] est un service d’ingestion de télémétrie hyperscale qui collecte, transforme et stocke des millions d’événements. En tant que plateforme de streaming distribuée, il offre une faible latence et une durée de rétention configurable vous permettant d’ingérer des quantités massives de données de télémétrie dans Azure et de lire les données de plusieurs applications. Le service Event Hubs prend en charge le traitement de pipelines en temps réel et par lots sur le même flux.

Vous pouvez implémenter un service de messagerie cloud à haut niveau de fiabilité entre applications et services via [Azure Service Bus][ServiceBus]. Il offre une messagerie répartie asynchrone entre le client et le serveur, une messagerie FIFO (premier entré, premier sorti) structurée ainsi que des fonctionnalités de publication et d’abonnement.

![10][10]

### <a name="make-a-virtual-datacenter-highly-available-multiple-virtual-datacenters"></a>Rendre un centre de données virtuel hautement disponible : plusieurs centres de données virtuels

Jusqu’à présent, cet article s’est concentré sur la conception d’un seul centre de données virtuel en décrivant l’architecture et les composants de base qui contribuent à la résilience. Les fonctionnalités Azure telles que l’équilibreur de charge Azure, les appliances virtuelles réseau, les groupes à haute disponibilité, les groupes identiques et divers autres mécanismes contribuent à l’obtention d’un système qui vous permet d’assurer des niveaux de SLA élevés dans vos services de production.

Toutefois, étant donné qu’un seul centre de données virtuel est généralement implémenté dans une même région, il peut être vulnérable à des pannes majeures qui affectent la totalité de cette région. Les clients qui nécessitent des contrats SLA de haut niveau doivent protéger leurs services en déployant le même projet dans au moins deux implémentations de centres de données virtuels placés dans des régions distinctes.

En plus de la question des contrats SLA, il existe divers scénarios courants dans lesquels il est judicieux de déployer plusieurs implémentations de centres de données virtuels :

- Présence régionale ou mondiale
- Récupération d’urgence.
- Mécanisme de redirection du trafic entre des centres de données

#### <a name="regionalglobal-presence"></a>Présence régionale/mondiale

Les centres de données Azure sont présents dans de nombreuses régions du monde. Quand ils sélectionnent plusieurs centres de données Azure, les clients doivent considérer deux facteurs associés : les distances géographiques et la latence. Pour offrir la meilleure expérience utilisateur possible, évaluez la distance géographique entre les implémentations de centres de données virtuels ainsi que la distance entre chaque implémentation de centre de données virtuel et les utilisateurs finaux.

La région où sont hébergées les implémentations de centres de données virtuels doit respecter les exigences réglementaires établies par la juridiction dont relève votre organisation.

#### <a name="disaster-recovery"></a>Récupération d'urgence

La conception d’un plan de reprise d’activité dépend des types de charges de travail et de la possibilité de synchroniser l’état de ces charges de travail entre différentes implémentations de centres de données virtuels. Dans l’idéal, la plupart des clients souhaitent un mécanisme de basculement rapide, ce qui peut nécessiter une synchronisation des données d’application entre les déploiements exécutant plusieurs implémentations de centres de données virtuels. Toutefois, quand vous concevez des plans de reprise d’activité, il est important de savoir que la plupart des applications sont sensibles à la latence qui peut découler de la synchronisation de ces données.

La synchronisation et la supervision des pulsations des applications dans différentes implémentations de centres de données virtuels obligent les applications à communiquer sur le réseau. Deux implémentations dans des régions distinctes peuvent être connectées :

- VNET Peering : ce type de service peut se connecter à des hubs dans différentes régions.
- Peering privé ExpressRoute lorsque les hubs dans chaque implémentation de centre de données virtuel sont connectés au même circuit ExpressRoute.
- Plusieurs circuits ExpressRoute connectés au moyen de votre dorsale d’entreprise et de vos différentes implémentations de centres de données virtuels connectés aux circuits ExpressRoute.
- Connexions VPN site à site entre la zone hub de vos implémentations de centres de données virtuels dans chaque région Azure.

Les connexions VNET Peering et ExpressRoute constituent généralement le type privilégié de connectivité réseau en raison de la bande passante plus importante et des niveaux de latence constants lors du transit à travers la dorsale de Microsoft.

Nous recommandons aux clients d’exécuter des tests de qualification de réseau pour vérifier la latence et la bande passante de ces connexions et pour déterminer si la réplication synchrone ou asynchrone des données est appropriée. Il est également important d’évaluer ces résultats au vu de l’objectif de délai de récupération (RTO).

#### <a name="disaster-recovery-diverting-traffic-from-one-region-to-another"></a>Reprise d’activité : redirection du trafic d’une région à une autre

[Azure Traffic Manager][traffic-manager] vérifie périodiquement l’intégrité du service des points de terminaison publics dans différentes implémentations de centres de données virtuels et, en cas de défaillance de ces points de terminaison, route automatiquement le trafic vers le centre de données virtuel secondaire à l’aide du système DNS (Domain Name System).

Étant donné qu’il utilise DNS, Traffic Manager ne fonctionne que sur les points de terminaison publics Azure. Le service est généralement utilisé pour contrôler ou rediriger le trafic vers Machines virtuelles Azure et Web Apps dans l’instance saine d’une implémentation de centre de données virtuel. Traffic Manager est résilient même en cas de défaillance de la totalité d’une région Azure et peut contrôler la distribution du trafic utilisateur pour les points de terminaison de service dans différents centres de données virtuels en fonction de plusieurs critères. Citons par exemple l’échec d’un service dans une implémentation de centre de données virtuel spécifique ou la sélection de l’implémentation de centre de données virtuel présentant la latence réseau la plus faible.

### <a name="summary"></a>Résumé

Un centre de données virtuel est une approche relative à la migration d’un centre de données qui permet de créer une architecture scalable dans Azure qui optimise l’utilisation des ressources cloud, réduit les coûts et simplifie la gouvernance du système. Un centre de données virtuel repose sur une topologie réseau de type « hub-and-spoke » qui fournit les services partagés communs dans le hub et autorise des applications/charges de travail spécifiques dans les rayons. Le centre de données virtuel respecte également la structure des rôles d’une entreprise, où collaborent différents services (équipes informatique centrale, DevOps, opérations et maintenance, etc.) tout en exerçant leur rôle spécifique. Un centre de données virtuel répond aux exigences d’une migration lift-and-shift, mais offre également de nombreux avantages pour les déploiements de cloud natifs.

## <a name="references"></a>Références

Ce document a abordé les fonctionnalités ci-après. Pour plus d’informations, cliquez sur les liens correspondants.

<!-- markdownlint-disable MD033 -->

|Fonctionnalités réseau|Équilibrage de la charge.|Connectivité|
|-|-|-|
|[Réseaux virtuels Azure][VNet]</br>[Groupes de sécurité réseau][network-security-groups]</br>[Journaux des groupes de sécurité réseau][nsg-log]</br>[Itinéraires définis par l’utilisateur][user-defined-routes]</br>[Appliances virtuelles réseau][NVA]</br>[Adresses IP publiques][PIP]</br>[Service de protection DDoS Azure][DDoS]</br>[Pare-feu Azure][AzFW]</br>[DNS Azure][DNS]|[Azure Front Door][AFD]</br>[Azure Load Balancer (L3)][ALB]</br>[Application Gateway (L7)][AppGW]</br>[Adresse IP de pare-feu d’application web][WAF]</br>[Azure Traffic Manager][traffic-manager]</br></br></br></br></br> |[Peering de réseaux virtuels][VNetPeering]</br>[Réseau privé virtuel][VPN]</br>[Virtual WAN][vWAN]</br>[ExpressRoute][ExR]</br>[ExpressRoute Direct][ExRD]</br></br></br></br></br>

|Identité</br>|Surveillance</br>|Bonnes pratiques</br>|
|-|-|-|
|[Azure Active Directory][azure-ad]</br>[Azure Multi-Factor Authentication][multi-factor-authentication]</br>[Contrôle d’accès en fonction du rôle][RBAC]</br>[Rôles Azure AD par défaut][Roles]</br></br></br> |[Network Watcher][NetWatch]</br>[Azure Monitor][Monitor]</br>[Journaux d’activité][ActLog]</br>[Journaux de diagnostic][DiagLog]</br>[Microsoft Operations Management Suite][OMS]</br>[Analyseur de performances réseau][NPM]|[Meilleures pratiques en matières de réseaux de périmètre][DMZ]</br>[Gestion des abonnements][SubMgmt]</br>[Gestion des groupes de ressources][RGMgmt]</br>[Limites d’abonnement Azure][limits] </br></br></br>|

|Autres services Azure|
|-|
|[Azure Web Apps][WebApps]</br>[HDInsight (Hadoop)][HDI]</br>[Hubs d'événements][EventHubs]</br>[Service Bus][ServiceBus]|

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Étapes suivantes

- Explorez [VNET Peering][VNetPeering], la technologie sous-jacente des conceptions hub-and-spoke (réseau en étoile) de centre de données virtuel.
- Implémentez [Azure AD][azure-ad] pour bien démarrer avec l’exploration de [RBAC][RBAC].
- Développez un modèle de gestion des abonnements et des ressources ainsi qu’un modèle RBAC pour répondre à la structure, aux exigences et aux stratégies de votre organisation. L’activité la plus importante est la planification. Dans la mesure du possible, planifiez les réorganisations, les fusions, les nouvelles gammes de produits et les autres points à prendre en compte.

<!-- images -->

[0]: ../_images/vdc/networking-redundant-equipment.png "Exemples de chevauchement de composants"
[1]: ../_images/vdc/networking-vdc-high-level.png "Exemple général de modèle hub-and-spoke dans une implémentation de centre de données virtuel"
[2]: ../_images/vdc/networking-hub-spokes-cluster.png "Cluster de concentrateurs et de rayons"
[3]: ../_images/vdc/networking-spoke-to-spoke.png "Rayon à rayon"
[4]: ../_images/vdc/networking-vdc-block-level-diagram.png "Diagramme de niveau bloc d’une implémentation de centre de données virtuel"
[5]: ../_images/vdc/networking-users-groups-subscriptions.png "Utilisateurs, groupes, abonnements et projets"
[6]: ../_images/vdc/networking-infrastructure-high-level.png "Diagramme d’infrastructure de haut niveau"
[7]: ../_images/vdc/networking-high-level-perimeter-networks.png "Diagramme d’infrastructure de haut niveau"
[8]: ../_images/vdc/networking-vnet-peering-perimeter-networks.png "Peering de réseaux virtuels et réseaux de périmètre"
[9]: ../_images/vdc/networking-high-level-diagram-monitoring.png "Diagramme de surveillance de haut niveau"
[10]: ../_images/vdc/networking-high-level-workloads.png "Diagramme de charge de travail de haut niveau"

<!-- links -->

[limits]: https://docs.microsoft.com/azure/azure-subscription-service-limits
[Roles]: https://docs.microsoft.com/azure/role-based-access-control/built-in-roles
[VNet]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview
[network-security-groups]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg
[DNS]: https://docs.microsoft.com/azure/dns/dns-overview
[PrivateDNS]: https://docs.microsoft.com/azure/dns/private-dns-overview
[VNetPeering]: https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview
[RBAC]: https://docs.microsoft.com/azure/role-based-access-control/overview
[multi-factor-authentication]: https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication
[azure-ad]: https://docs.microsoft.com/azure/active-directory/active-directory-whatis
[VPN]: https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: https://docs.microsoft.com/azure/expressroute/expressroute-introduction
[ExRD]: https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about
[vWAN]: https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about
[NVA]: https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: https://docs.microsoft.com/azure/firewall/overview
[SubMgmt]: /azure/architecture/cloud-adoption/appendix/azure-scaffold
[RGMgmt]: https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview
[DMZ]: https://docs.microsoft.com/azure/best-practices-network-security
[ALB]: https://docs.microsoft.com/azure/load-balancer/load-balancer-overview
[DDoS]: https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview
[PIP]: https://docs.microsoft.com/azure/virtual-network/virtual-network-public-ip-address
[AFD]: https://docs.microsoft.com/azure/frontdoor/front-door-overview
[AFDWAF]: https://docs.microsoft.com/azure/frontdoor/waf-overview
[AppGW]: https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction
[AppGWWAF]: https://docs.microsoft.com/azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/
[ActLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-activity-logs
[DiagLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[nsg-log]: https://docs.microsoft.com/azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview
[NPM]: https://docs.microsoft.com/azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: https://docs.microsoft.com/azure/app-service/
[HDI]: https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs
[ServiceBus]: https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview
[traffic-manager]: https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview
