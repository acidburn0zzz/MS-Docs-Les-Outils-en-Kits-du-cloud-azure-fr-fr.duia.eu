---
title: Structure d’entreprise Azure
description: La structure d’entreprise Azure devient le Framework d’adoption du cloud Microsoft pour Azure. Apprenez à répondre au besoin de gouvernance et à l’équilibrer avec le besoin d’agilité.
author: rdendtler
ms.author: rodend
ms.date: 09/22/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
ROBOTS: NOINDEX
ms.openlocfilehash: c545f147ba374fe1150573b060c600269eb628b1
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79311606"
---
<!-- cSpell:ignore rodend subscope ITSM Hashi -->

# <a name="azure-enterprise-scaffold-prescriptive-subscription-governance"></a>Structure d’entreprise Azure : Gouvernance normative de l’abonnement

> [!NOTE]
> La structure d’entreprise Azure a été intégrée au framework d’adoption du cloud Microsoft. Le contenu de cet article est maintenant représenté dans la section [Prêt](../ready/index.md) du nouveau framework. Cet article sera déprécié début 2020. Pour commencer à utiliser le nouveau processus, reportez-vous à la [Vue d’ensemble Prêt](../ready/index.md), à la [création de votre première zone d’atterrissage](../ready/landing-zone/migrate-landing-zone.md) et aux [considérations relatives aux zones d’atterrissage](../ready/considerations/index.md).

Les entreprises adoptent de plus en plus le cloud public en raison de son agilité et de la flexibilité. Elles s’appuient sur les points forts du cloud pour générer des revenus et optimiser l’utilisation des ressources dans le cadre de leur activité. Microsoft Azure offre une multitude de services et de fonctionnalités que les entreprises assemblent comme des modules pour gérer un large éventail de charges de travail et d’applications.

Décider d’utiliser Microsoft Azure n’est que la première étape pour bénéficier de l’avantage du cloud. La deuxième étape consiste à comprendre comment l’entreprise peut utiliser Azure efficacement et identifier les fonctionnalités de base qui doivent être présentes pour répondre à certaines questions comme :

- « Je suis inquiet au sujet de la souveraineté des données ; comment puis-je m’assurer que mes données et systèmes répondent à notre réglementation ? »
- « Comment savoir ce que chaque ressource prend en charge afin de les comptabiliser et de les facturer avec exactitude ? »
- « Je veux m’assurer que tout ce que nous déployons ou faisons dans le cloud public le soit d’abord dans un souci de sécurité ; comment faire pour faciliter cela ? »

La perspective d’un abonnement vide sans garde-fou est décourageante. Elle peut même vous décourager de migrer vers Azure.

Cet article offre aux techniciens un point de départ qui leur permettra de répondre aux besoins de gouvernance et de les mettre en balance avec les besoins d’agilité. Il présente le concept d’une structure d’entreprise qui guide les organisations dans l’implémentation et la gestion sécurisées de leurs environnements Azure. Il fixe le cadre pour développer des contrôles efficaces et efficients.

## <a name="need-for-governance"></a>Besoin de gouvernance

Lors de la migration vers Azure, vous devez prendre en compte la gouvernance assez tôt pour garantir une utilisation efficace du cloud au sein de l’entreprise. Hélas, compte tenu du temps et de la bureaucratie que nécessite la création d’un système de gouvernance complet, certaines divisions en appellent directement à des fournisseurs sans passer par le service informatique de l’entreprise. Cette approche peut exposer l’entreprise à des risques si les ressources ne sont pas gérées correctement. Les caractéristiques du cloud public (agilité, flexibilité et tarifs basés sur la consommation) sont importantes pour les groupes professionnels qui doivent répondre rapidement aux demandes des clients (internes et externes). Mais le service informatique de l’entreprise doit s’assurer que les données et les systèmes sont efficacement protégés.

Dans la construction, la structure sert de fondations. La structure trace les grandes lignes et fournit des points d’ancrage pour le montage de systèmes plus permanents. Une structure d’entreprise revient au même : il s’agit d’un ensemble de contrôles flexibles et de fonctionnalités Azure qui fournissent la structure de l’environnement et des points d’ancrage pour les services basés sur le cloud public. Elle fournit aux constructeurs (groupes informatiques et commerciaux) une assise pour créer et lier de nouveaux services en gardant à l’esprit la rapidité de livraison.

Elle est basée sur des pratiques que nous avons développées au cours de nos nombreuses collaborations avec des clients de tailles diverses. Nous comptons parmi ces clients aussi bien des petites entreprises développant des solutions dans le cloud que de grandes multinationales et des éditeurs de logiciels indépendants qui migrent des charges de travail et développent des solutions cloud natives. La structure d’entreprise a été spécialement conçue pour offrir une flexibilité permettant de prendre en charge les charges de travail informatiques traditionnelles et les charges de travail agiles, comme quand les développeurs créent des applications SaaS (software as a service) basées sur les fonctionnalités de la plateforme Azure.

La structure d’entreprise peut constituer le fondement de chaque nouvel abonnement dans Azure. Elle permet aux administrateurs de s’assurer que les charges de travail répondent à la configuration requise minimale en matière de gouvernance d’une organisation sans empêcher les groupes professionnels et les développeurs d’atteindre rapidement leurs objectifs. Notre expérience montre qu’elle a pour effet non pas d’empêcher la croissance du cloud public, mais de l’accélérer considérablement.

> [!NOTE]
> Microsoft a publié en préversion une nouvelle fonctionnalité appelée [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) qui vous permet d’empaqueter, gérer et déployer images, modèles, stratégies et autres scripts courants dans les abonnements et les groupes d’administration. Cette fonctionnalité est le trait d’union entre l’objectif de la structure en tant que modèle de référence et le déploiement de ce modèle dans votre organisation.
>
L’illustration suivante présente les composants de la structure. Celle-ci est basée sur un plan solide de la hiérarchie de gestion et des abonnements. Les piliers en sont des stratégies Resource Manager et des normes d’affectation de noms fortes. Le reste de la structure est constitué des fonctionnalités Azure de base qui habilitent et connectent un environnement sécurisé et facile à gérer.

![Structure d’entreprise](../_images/reference/scaffold-v2.png)

## <a name="define-your-hierarchy"></a>Définition de votre hiérarchie

La structure a pour assise la hiérarchie et la relation de l’Accord de Mise en Œuvre Entreprise Azure à travers les abonnements et les groupes de ressources. L’Accord de Mise en Œuvre Entreprise définit la forme et l’utilisation des services Azure au sein de votre entreprise d’un point de vue conceptuel. Dans le cadre du Contrat Entreprise, vous pouvez subdiviser l’environnement en services, en comptes, en abonnements et en groupes de ressources à l’image de la structure de votre organisation.

![Hierarchy](../_images/reference/agreement.png)

Un abonnement Azure est l’unité de base contenant toutes les ressources. Il définit aussi plusieurs limites au sein d’Azure, comme le nombre de cœurs, de réseaux virtuels et d’autres ressources. Les groupes de ressources servent à affiner le modèle d’abonnement et permettent un regroupement plus naturel des ressources.

Chaque entreprise est différente et la hiérarchie représentée dans l’illustration ci-dessus autorise une grande flexibilité quant à la façon dont Azure est organisé au sein de votre entreprise. La modélisation de votre hiérarchie en fonction des besoins de votre entreprise en matière de facturation, de gestion des ressources et d’accès à celles-ci constitue la première et la plus importante des décisions à prendre au moment de se lancer dans le cloud public.

### <a name="departments-and-accounts"></a>Services et comptes

Les trois modèles courants pour les inscriptions Azure sont :

- Le modèle **fonctionnel** :

  ![Le modèle fonctionnel](../_images/reference/functional.png)

- Le modèle **division** :

  ![Le modèle division](../_images/reference/business.png)

- Le modèle **géographique** :

  ![Le modèle géographique](../_images/reference/geographic.png)

Bien que chacun de ces modèles ait sa place, le modèle **division** est de plus en plus adopté pour sa souplesse quand il s’agit de modéliser le modèle de coût d’une organisation et de représenter l’étendue du contrôle. Le groupe Microsoft Core Engineering and Operations a créé un sous-ensemble efficace du modèle **division** (niveaux **Fédéral**, **État** et **Local**). Pour plus d’informations, consultez [Organisation des abonnements et des groupes de ressources dans l’entreprise](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/azure-best-practices/scaling-subscriptions).

### <a name="azure-management-groups"></a>Groupes d’administration Azure

Microsoft propose à présent une autre façon de modéliser votre hiérarchie : [Groupes d’administration Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview). Les groupes d’administration sont bien plus flexibles que les services et les comptes. Ils peuvent s’imbriquer sur six niveaux au maximum. Les groupes d’administration vous permettent de créer une hiérarchie distincte de votre hiérarchie de facturation, seulement dans une optique de gestion efficace des ressources. Les groupes d’administration permettent de reproduire une hiérarchie de facturation et c’est ce par quoi les entreprises commencent souvent. Toutefois, l’intérêt des groupes d’administration est de les utiliser pour modéliser votre organisation, en regroupant les abonnements associés (quel que soit leur emplacement dans la hiérarchie de facturation) et en attribuant des rôles, stratégies et initiatives communs. Voici quelques exemples :

- **Production et hors production.** Certaines entreprises créent des groupes d’administration pour identifier leurs abonnements production et hors production. Les groupes d’administration permettent à ces clients de gérer plus facilement les rôles et les stratégies. Par exemple, un abonnement hors production peut permettre aux développeurs de bénéficier d’un accès « contributeur » tandis qu’un abonnement production leur permet seulement un accès « lecteur ».
- **Services internes et services externes.** Les entreprises ont souvent des besoins, des stratégies et des rôles différents pour les services internes et les services destinés aux clients.

Des groupes d’administration bien conçus constituent, avec une stratégie et des initiatives Azure, l’élément central d’une gouvernance efficace d’Azure.

### <a name="subscriptions"></a>Abonnements

Quand vous êtes amené à prendre des décisions concernant vos services et comptes (ou groupes d’administration), votre objectif premier est de diviser votre environnement Azure à l’image de votre organisation. Or, vos décisions les plus importantes sont celles qui ont trait aux abonnements ; elles ont un impact sur la sécurité, la scalabilité et la facturation. De nombreuses organisations se servent des modèles suivants de guides :

- **Application/Service :** Les abonnements représentent une application ou un service (portefeuille d’applications).
- **Cycle de vie :** Les abonnements représentent le cycle de vie d’un service, par exemple Production ou Développement.
- **Service :** Les abonnements représentent les services de l’organisation.

Les deux premiers modèles sont les plus couramment utilisés et sont fortement recommandés. L’approche Cycle de vie convient pour la plupart des organisations. Dans ce cas, la recommandation générale consiste à utiliser les deux abonnements de base, `Production` et `Nonproduction`, puis à utiliser les groupes de ressources permettant de séparer davantage les environnements.

### <a name="resource-groups"></a>Groupes de ressources

Azure Resource Manager vous permet de placer les ressources dans des groupes explicites pour la gestion, la facturation ou l’affinité naturelle. Les groupes de ressources sont des conteneurs de ressources qui ont un cycle de vie commun ou partagent un attribut tel que « tous les serveurs SQL » ou « Application A ».

Les groupes de ressources ne peuvent pas être imbriqués et les ressources ne peuvent appartenir qu’à un seul groupe de ressources. Certaines actions peuvent agir sur toutes les ressources contenues dans un groupe de ressources. Par exemple, la suppression d’un groupe de ressources supprime toutes les ressources du groupe de ressources. Comme pour les abonnements, il existe des modèles communs quand il s’agit de créer des groupes de ressources, qui vont des charges de travail « Informatique traditionnelle » aux charges de travail de type « Informatique agile » :

- Les charges de travail de type « informatique traditionnelle » sont généralement regroupées par éléments au sein du même cycle de vie, par exemple en tant qu’application. Le regroupement par application permet de gestion des applications individuelles.
- Les charges de travail de type « agile » ont tendance à se concentrer sur les applications cloud pour les clients externes. Les groupes de ressources reflètent souvent les couches de déploiement (comme les couches Web et Application) et de gestion.

> [!NOTE]
> Comprendre votre charge de travail vous aide à développer une stratégie de groupe de ressources. Ces modèles peuvent être combinés et associés. Par exemple, la présence d’un groupe de ressources de services partagés dans le même abonnement que les groupe de ressources « Agile ».

## <a name="naming-standards"></a>Normes d’attribution de noms

Le premier pilier de la structure est une norme d’attribution de noms cohérente. Des normes d’attribution de noms bien conçues vous permettent d’identifier des ressources dans le portail, sur une facture et dans des scripts. Vous disposez déjà probablement de conventions d’attribution de noms pour l’infrastructure locale. Lorsque vous ajoutez Azure à votre environnement, vous devez étendre ces normes d’attribution de noms à vos ressources Azure.

> [!TIP]
> Pour les conventions de dénomination :
>
> - Passez en revue et adoptez autant que possible les [modèles et pratiques recommandées](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming). Ces recommandations vous aident à choisir une norme d’attribution de noms explicite et fournissent de nombreux exemples.
> - Utilisation de stratégies Resource Manager pour appliquer des normes de nommage.
>
> Ne perdez pas de vue qu’il est difficile de changer les noms par la suite et que les quelques minutes passées ici vous éviterons des problèmes plus tard.

Vos normes d’affectation de noms doivent viser les ressources les plus utilisées et recherchées. Par exemple, tous les groupes de ressources doivent suivre une norme bien définie par souci de clarté.

### <a name="resource-tags"></a>Balises de ressource

Les balises de ressource sont en parfaite adéquation avec les normes d’affectation de noms. Plus vous ajoutez des ressources aux abonnement, plus il est important de les classer logiquement pour les besoins de la facturation, de la gestion et de l’exploitation. Pour plus d’informations, consultez [Organisation des ressources Azure à l’aide de balises](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

> [!IMPORTANT]
> Les balises peuvent contenir des informations personnelles et être visées par les dispositions du RGPD. Planifiez soigneusement la gestion de vos balises. Si vous recherchez des informations générales sur le RGPD, consultez la section RGPD du [Portail d’approbation de services](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

Au-delà de la facturation et de la gestion, les balises sont utilisées de diverses manières. Elles sont souvent employées dans le cadre de l’automation (consultez la section ultérieure). Cet aspect doit être pris en considération en amont au risque de provoquer des conflits. Nous vous recommandons d’identifier toutes les balises courantes au niveau de l’entreprise (par exemple, ApplicationOwner, CostCenter) et de les appliquer systématiquement au moment de déployer les ressources à l’aide de l’automatisation.

## <a name="azure-policy-and-initiatives"></a>Stratégie et initiatives Azure

Le deuxième pilier de la structure consiste à utiliser une [stratégie et des initiatives Azure](https://docs.microsoft.com/azure/azure-policy/azure-policy-introduction) pour gérer les risques en appliquant des règles (avec des effets) sur les ressources et les services de vos abonnements. Les initiatives Azure sont des collections de stratégies visant à atteindre un objectif unique. Des stratégies et des initiatives sont alors affectées à une étendue de ressources pour commencer la mise en œuvre de ces stratégies.

Les stratégies et initiatives sont encore plus efficaces quand elles sont associées aux groupes d’administration mentionnés précédemment. Les groupes d’administration permettent d’affecter une initiative ou une stratégie à tout un ensemble d’abonnements.

### <a name="common-uses-of-resource-manager-policies"></a>Utilisations courantes de stratégies Resource Manager

Les stratégies et initiatives représentent un outil puissant dans le kit de ressources Azure. Les stratégies permettent aux entreprises de fournir des contrôles pour les charges de travail de type « Informatique traditionnelle » et ainsi d’apporter aux applications métier la stabilité dont elles ont besoin tout en autorisant aussi les charges de travail de type « Agile ». Cela permet, par exemple, de développer des applications client sans exposer l’entreprise à des risques supplémentaires. Les modèles les plus courants pour les stratégies sont les suivants :

- **Conformité géographique et souveraineté des données.** Azure dispose d’une liste de régions dans le monde qui ne cesse de s’allonger. Les entreprises doivent souvent faire en sorte que les ressources situées dans une étendue spécifique restent dans une région géographique pour répondre à des exigences réglementaires.
- **Éviter une exposition publique des serveurs.** Azure Policy peut interdire le déploiement de certains types de ressources. Il est courant de créer une stratégie pour interdire la création d’une adresse IP publique dans une étendue spécifique et ainsi éviter d’exposer involontairement un serveur sur Internet.
- **Gestion des coûts et métadonnées.** Les balises de ressource sont souvent utilisées pour ajouter des données de facturation importantes aux ressources et groupes de ressources comme CostCenter, Owner, etc. Ces balises sont extrêmement utiles pour une facturation et une gestion des ressources précises. Les stratégies peuvent imposer l’application de balises de ressource à toutes les ressources déployées, ce qui en facilite la gestion.

### <a name="common-uses-of-initiatives"></a>Usages courants des initiatives

Les initiatives offrent aux entreprises la possibilité de regrouper des stratégies logiques et de les suivre comme une entité unique. Les initiatives aident l’entreprise à mieux répondre aux besoins des charges de travail agiles et traditionnelles. Les usages courants des initiatives incluent :

- **Habilitation de la supervision dans Azure Security Center.** Il s’agit d’une initiative par défaut dans Azure Policy qui illustre parfaitement ce qu’est une initiative. Elle habilite les stratégies qui identifient les bases de données SQL non chiffrées, les vulnérabilités des machines virtuelles et des besoins plus courants liés à la sécurité.
- **Initiative propre à la réglementation.** Les entreprises regroupent souvent les stratégies courantes dans une exigence réglementaire (comme HIPAA) de sorte que les contrôles et la conformité vis-à-vis de ces contrôles soient suivis avec efficacité.
- **Types de ressources et références SKU.** La création d’une initiative qui limite les types de ressources et les références SKU pouvant être déployés peut aider à contrôler les coûts et à garantir à votre organisation qu’elle déploie uniquement des ressources que votre équipe peut prendre en charge compte tenu de ses compétences et de ses procédures.

> [!TIP]
> Nous vous recommandons de toujours utiliser des définitions d’initiative plutôt que des définitions de stratégie. Après avoir affecté une initiative à une étendue, comme un abonnement ou un groupe d’administration, vous pouvez facilement ajouter une autre stratégie à l’initiative sans avoir à modifier les affectations. Il est ainsi bien plus facile de comprendre ce qui est appliqué et de suivre la conformité.

### <a name="policy-and-initiative-assignments"></a>Affectations de stratégies et d’initiatives

Après avoir créé des stratégies et les avoir regroupées sous forme d’initiatives logiques, vous devez affecter la stratégie à une étendue, qu’il s’agisse d’un groupe d’administration, d’un abonnement ou même d’un groupe de ressources. Les affectations vous permettent aussi d’exclure une sous-étendue de l’affectation d’une stratégie. Par exemple, si vous interdisez la création d’adresses IP publiques au sein d’un abonnement, vous pouvez créer une affectation en excluant un groupe de ressources connecté à votre zone DMZ protégée.

Vous trouverez dans ce dépôt [GitHub](https://github.com/Azure/azure-policy) plusieurs exemples de stratégies qui montrent comment une stratégie et des initiatives peuvent être appliquées à diverses ressources dans Azure.

## <a name="identity-and-access-management"></a>Gestion de l’identité et de l’accès

Quand vous vous lancez dans le cloud public, vous devez en premier lieu vous poser les questions suivantes : « qui doit avoir accès aux ressources ? » et « comment contrôler cet accès ? ». Le contrôle de l’accès au portail Azure et aux ressources qu’il contient s’avère essentiel pour la sécurité à long terme de vos ressources dans le cloud.

Pour sécuriser l’accès à vos ressources, vous devez configurer d’abord votre fournisseur d’identité, puis les rôles et l’accès. Azure Active Directory (Azure AD), connecté à votre instance Active Directory locale, est la pierre angulaire d’Azure Identity. Ceci dit, Azure AD n’est *pas* la même chose qu’Active Directory local et il est important de comprendre ce qu’est un locataire Azure AD et le rapport avec votre abonnement Azure. Consultez les [informations](../govern/resource-consistency/resource-access-management.md) disponibles pour acquérir des bases solides sur Azure AD et Active Directory local. Pour connecter et synchroniser votre instance Active Directory à Azure AD, installez et configurez l’[outil Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) localement.

![Schéma de l’architecture AD](../_images/reference/ad-architecture.png)

Quand Azure a été initialement lancé, les contrôles d’accès à un abonnement étaient élémentaires : Administrateur ou coadministrateur. L’accès à un abonnement dans le modèle classique impliquait l’accès à toutes les ressources dans le portail. Ce manque de contrôle précis a conduit à une prolifération d’abonnements afin de fournir un niveau de contrôle d’accès raisonnable pour une inscription Azure. Cette prolifération d’abonnements n’est plus nécessaire. Le contrôle d’accès en fonction du rôle (RBAC) vous permet d’affecter les utilisateurs à des rôles standard qui offrent un accès courant, tel que « propriétaire », « collaborateur » ou « lecteur ». Vous pouvez même créer vos propres rôles.

Lorsque vous implémentez l’accès en fonction du rôle, vous avez tout intérêt à suivre les recommandations suivantes :

- Veillez sur l’administrateur/coadministrateur d’un abonnement, car ces rôles ont des autorisations étendues. Seul le propriétaire de l’abonnement doit être ajouté comme coadministrateur s’il doit gérer des déploiements Azure Classic.
- Utilisez des groupes d’administration pour attribuer des [rôles](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview#management-group-access) dans plusieurs abonnements et éviter d’avoir à les gérer au niveau de l’abonnement.
- Ajoutez des utilisateurs Azure à un groupe (par exemple, les propriétaires de l’application X) dans Active Directory. Utilisez le groupe synchronisé pour affecter aux membres de groupes les droits nécessaires pour gérer le groupe de ressources contenant l’application.
- Suivez le principe de l’octroi des **privilèges minimum** nécessaires pour exécuter le travail prévu.

> [!IMPORTANT]
>Envisagez d’utiliser les fonctionnalités [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure), Azure [Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted) et l’[accès conditionnel](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) pour améliorer la sécurité et la visibilité des actions d’administration dans vos abonnements Azure. Ces fonctionnalités sont celles d’une licence Azure AD Premium valide (selon le cas) et visent à mieux sécuriser et gérer votre identité. Azure AD PIM permet un accès administratif « juste-à-temps » avec le workflow d’approbation, ainsi qu’un audit complet des activations et des activités d’administrateur. Azure Multi-Factor Authentication est une autre fonctionnalité critique qui permet une vérification en deux étapes pour se connecter au portail Azure. En l’associant aux contrôles d’accès conditionnel, vous pouvez gérer efficacement vos risques de compromission.

L’une des meilleures stratégies d’atténuation des risques que vous puissiez adopter et qui devrait être considérée comme obligatoire pour chaque déploiement consiste à planifier et à préparer vos contrôles d’identité et d’accès et à suivre les bonnes pratiques de gestion des identités Azure ([lien](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices)).

## <a name="security"></a>Sécurité

Les inquiétudes vis-à-vis de la sécurité constituent traditionnellement l’un des principaux obstacles à l’adoption du cloud. Les gestionnaires du risque informatique et les services de sécurité ont besoin de vérifier que les ressources dans Azure sont protégées et sécurisées par défaut. Azure fournit des fonctionnalités que vous pouvez utiliser pour protéger les ressources tout en détectant et en éliminant les menaces visant ces ressources.

### <a name="azure-security-center"></a>Azure Security Center

Outre des fonctionnalités de protection avancée contre les menaces, [Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-intro) offre une vue unifiée de l’état de la sécurité des ressources dans votre environnement. Azure Security Center est une plateforme ouverte qui permet aux partenaires de Microsoft de créer des logiciels qui s’y connectent et améliorent ses fonctionnalités. Les fonctionnalités de base d’Azure Security Center (niveau gratuit) évaluent votre sécurité et vous donnent des conseils pour l’améliorer. Aux niveaux payants, vous bénéficiez d’autres fonctionnalités appréciables comme l’accès administrateur juste-à-temps et les contrôles d’application adaptatifs (mise en liste verte).

> [!TIP]
>Azure Security Center est un outil puissant régulièrement amélioré avec de nouvelles fonctionnalités que vous pouvez utiliser pour détecter les menaces et protéger votre entreprise. Il est vivement recommandé de toujours activer Azure Security Center.

### <a name="locks-for-azure-resources"></a>Verrous pour les ressources Azure

Plus votre organisation ajoute des services de base aux abonnements, plus il est important d’éviter une interruption de service. Une interruption courante se produit quand un script ou un outil s’exécutant dans un abonnement Azure supprime involontairement une ressource. Les [verrous](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) limitent les opérations sur les ressources importantes, dont la modification ou la suppression aurait un impact significatif. Vous pouvez appliquer des verrous à des abonnements, à des groupes de ressources ou à des ressources individuelles. Appliquez des verrous aux ressources fondamentales, comme les réseaux virtuels, les passerelles, les groupes de sécurité réseau et les comptes de stockage de clés.

### <a name="secure-devops-kit-for-azure"></a>Kit DevOps sécurisé pour Azure

Le kit DevOps sécurisé pour Azure (AzSK) est une collection de scripts, d’outils, d’extensions et de fonctionnalités d’automatisation qui a été créée à l’origine par la propre équipe informatique de Microsoft et [publiée en open source via GitHub ](https://github.com/azsk/devopskit-docs). AzSK répond aux besoins de sécurité de bout en bout des abonnements et des ressources pour les équipes qui ont recours à une automatisation étendue et qui intègrent graduellement la sécurité dans des flux de travail DevOps natifs, favorisant ainsi la sécurisation des tâches DevOps dans les six domaines suivants :

- Sécurisation de l’abonnement
- Sécurisation du développement
- Intégration de la sécurité dans CI/CD
- Assurance continue
- Alertes et supervision
- Gouvernance des risques du cloud

![Diagramme général du kit DevOps sécurisé pour Azure](../_images/reference/secure-devops-kit.png)

AzSK est un ensemble complet d’outils, de scripts et d’informations qui représentent une partie importante d’un plan de gouvernance Azure complet. Il est essentiel de l’incorporer dans votre structure de façon à aider votre organisation à atteindre ses objectifs de gestion des risques.

### <a name="azure-update-management"></a>Azure Update Management

L’une des mesures clés que vous pouvez prendre pour assurer la sécurité de votre environnement est de veiller à ce que vos serveurs soient corrigés avec les dernières mises à jour. Bien que de nombreux outils permettent d’assurer cette tâche, Azure met à disposition la solution [Azure Update Management](https://docs.microsoft.com/azure/automation/automation-update-management) pour gérer l’identification et le déploiement des correctifs critiques du système d’exploitation. Cette solution utilise Azure Automation, qui est abordé dans la section [Automatiser](#automate), plus loin dans ce guide.

## <a name="monitor-and-alerts"></a>Supervision et génération d’alertes

La collecte et l’analyse des données de télémétrie, qui donnent des indications sur les activités, les performances, l’intégrité et la disponibilité des services que vous utilisez dans tous vos abonnements Azure, sont essentielles à la gestion proactive de vos applications et de votre infrastructure et représentent une nécessité incontournable pour chaque abonnement Azure. Chaque service Azure émet des données de télémétrie qui prennent la forme de journaux d’activité, de métriques et de journaux de diagnostic.

- Les **journaux d’activité** décrivent toutes les opérations effectuées sur les ressources de vos abonnements.
- Les **métriques** sont des informations numériques émises par une ressource qui décrivent les performances et l’intégrité de cette ressource.
- Les **journaux de diagnostic** sont émis par un service Azure et fournissent des informations complètes et fréquentes sur le fonctionnement de ce service.

Ces informations peuvent être consultées et traitées à plusieurs niveaux et sont constamment améliorées. Azure propose des fonctionnalités **partagées**, **basiques** et **approfondies** destinées à superviser les ressources Azure via les services présentés dans le schéma ci-dessous.

![Surveillance](../_images/reference/monitoring.png)

### <a name="shared-capabilities"></a>Fonctionnalités partagées

- **Alertes :** Vous pouvez collecter chaque journal, événement et métrique auprès des ressources Azure, mais s’il n’est pas possible d’être notifié de l’existence de conditions et d’actions critiques, ces données peuvent uniquement être utilisées à des fins historiques et forensiques. Les alertes Azure vous notifient de façon proactive de l’existence de conditions que vous définissez dans toutes vos applications et votre infrastructure. Vous créez des règles d’alerte pour les journaux d’activité, les événements et les métriques qui utilisent des groupes d’actions afin de notifier des ensembles de destinataires. Les groupes d’actions permettent aussi d’automatiser les corrections en utilisant des actions externes comme des webhooks pour exécuter des runbooks Azure Automation et Azure Functions.

- **Tableaux de bord :** Les tableaux de bord vous permettent d’agréger les vues de supervision et de combiner les données dans l’ensemble des ressources et des abonnements pour vous donner un aperçu de la télémétrie des ressources Azure à l’échelle de l’entreprise. Vous pouvez créer et configurer vos propres vues et les partager avec d’autres utilisateurs. Par exemple, vous pouvez créer un tableau de bord constitué de plusieurs vignettes pour les différents administrateurs de base de données afin de fournir des informations dans tous les services de base de données Azure, notamment Azure SQL DB, Azure DDB pour PostgreSQL et Azure DB pour MySQL.

- **Metrics Explorer :** Les métriques sont des valeurs numériques générées par les ressources Azure (comme % CPU ou E/S de disque) qui fournissent des insights sur le fonctionnement et les performances de vos ressources. À l’aide de Metrics Explorer, vous pouvez définir et envoyer les métriques qui vous intéressent à Log Analytics à des fins d’agrégation et d’analyse.

### <a name="core-monitoring"></a>Analyse principale

- **Azure Monitor :** Azure Monitor est le service de plateforme principal qui fournit une seule source de supervision des ressources Azure. L’interface Azure Monitor du portail Azure offre un point d’accès centralisé à toutes les fonctionnalités de supervision d’Azure, notamment aux fonctionnalités de supervision approfondies d’Application Insights, de Log Analytics, de la supervision réseau, des solutions de gestion et de Service Map. Avec Azure Monitor, vous pouvez visualiser, interroger, router, archiver et agir sur les métriques et les journaux issus des ressources Azure à l’échelle de votre domaine cloud. En plus du portail, vous pouvez récupérer les données par l’intermédiaire des applets de commande PowerShell Monitor, de l’interface de ligne de commande multiplateforme ou des API REST Azure Monitor.

- **Azure Advisor :** Azure Advisor supervise constamment les données de télémétrie de tous vos abonnements et environnements. Il fournit des suggestions sur les bonnes pratiques permettant d’optimiser vos ressources Azure pour faire des économies et améliorer les performances, la sécurité et la disponibilité des ressources qui composent vos applications.

- **Service Health :** Azure Service Health identifie les problèmes liés aux services Azure qui peuvent affecter vos applications et vous aide à définir des fenêtres de maintenance planifiées.

- **Journal d’activité :** Le journal d’activité décrit toutes les opérations effectuées sur les ressources de vos abonnements. Il fournit une piste d’audit pour déterminer le « quoi », « qui, » et « quand » des opérations de création, de mise à jour et de suppression des ressources. Les événements du journal d’activité sont stockés dans la plateforme et peuvent faire l’objet d’une requête pendant 90 jours. Vous pouvez intégrer les journaux d’activité à Log Analytics sur des périodes de conservation plus longues et pour des interrogations et analyses plus approfondies sur diverses ressources.

### <a name="deep-application-monitoring"></a>Analyse approfondie des applications

- **Application Insights :** Application Insights vous permet de collecter des données de télémétrie propres à des applications, et de superviser les performances, la disponibilité et l’utilisation de ces applications dans le cloud ou localement en instrumentant votre application avec des SDK pris en charge pour plusieurs langages, dont .NET, JavaScript, JAVA, Node.js, Ruby et Python. Les événements Application Insights sont intégrés dans le même magasin de données Log Analytics qui prend en charge la supervision de l’infrastructure et de la sécurité pour vous permettre de mettre en corrélation et d’agréger les événements dans le temps via un langage de requête élaboré.

### <a name="deep-infrastructure-monitoring"></a>Analyse approfondie des infrastructures

- **Log Analytics :** Log Analytics joue un rôle central dans la supervision Azure en collectant des données de télémétrie et d’autres données auprès de diverses sources et en fournissant un langage de requête et un moteur d’analytique qui vous donnent des insights sur le fonctionnement de vos applications et ressources. Vous pouvez interagir directement avec les données Log Analytics par le biais de recherches rapides dans les journaux et les vues, ou utiliser les outils d’analyse dans d’autres services Azure qui stockent leurs données dans Log Analytics, comme Application Insights ou Azure Security Center.

- **Supervision réseau :** Les services de supervision réseau d’Azure vous permettent d’obtenir des insights sur le flux de trafic, les performances, la sécurité, la connectivité et les goulots d’étranglement du réseau. Une conception réseau bien planifiée doit inclure la configuration des services de supervision réseau comme Network Watcher et le Moniteur ExpressRoute.

- **Solutions de gestion :** Les solutions de gestion sont des jeux empaquetés de logique, d’insights et de requêtes Log Analytics prédéfinies pour une application ou un service. Elles utilisent Log Analytics comme base de stockage et d’analyse des données d’événement. La supervision des conteneurs et l’analytique Azure SQL Database sont des exemples de solutions de gestion.

- **Service Map :** Service Map offre une vue graphique de vos composants d’infrastructure, de leurs processus et de leurs interdépendances vis-à-vis d’autres ordinateurs et processus externes. Il intègre des événements, des données de performance et des solutions de gestion dans Log Analytics.

> [!TIP]
> Avant de créer des alertes individuelles, créez et tenez à jour un ensemble de groupes d’actions partagés qui puisse être utilisé dans toutes les alertes Azure. Vous pourrez ainsi gérer de façon centralisée le cycle de vie de vos listes de destinataires, les méthodes de remise de notifications (e-mail, numéros de téléphone SMS) et les webhooks ciblant des actions externes (runbooks Azure Automation, Azure Functions et Logic Apps, ITSM).

## <a name="cost-management"></a>la gestion des coûts ;

Un des changements majeurs auxquels vous serez confronté en passant d’un cloud local au cloud public est le passage de dépenses d’investissement (acheter du matériel) à des dépenses d’exploitation (payer pour le service que vous utilisez). Cette transition nécessite également une gestion plus précise de vos coûts. L’avantage du cloud est que vous pouvez agir foncièrement et positivement sur le coût d’un service que vous utilisez, simplement en l’arrêtant ou en le redimensionnant quand vous n’en avez pas besoin. La gestion délibérée des coûts dans le cloud est une meilleure pratique à laquelle les clients expérimentés s’adonnent quotidiennement.

Microsoft fournit plusieurs outils pour visualiser, suivre et gérer les coûts. Nous vous proposons aussi un ensemble complet d’API pour vous permettre de personnaliser la gestion des coûts et de l’intégrer à vos propres outils et tableaux de bord. Ces outils sont plus ou moins regroupés dans les fonctionnalités du portail Azure et des fonctionnalités externes.

### <a name="azure-portal-capabilities"></a>Fonctionnalités du portail Azure

Il s’agit d’outils destinés à fournir des informations instantanées sur les coûts et à vous permettre de pendre des mesures.

- **Coût des ressources d’abonnement :** Située dans le portail, la vue [Analyse des coûts Azure](https://docs.microsoft.com/azure/cost-management/overview) vous donne un aperçu rapide de vos coûts ainsi que des informations sur les dépenses quotidiennes par ressource ou groupe de ressources.
- **Azure Cost Management :** Ce produit est le résultat du rachat de Cloudyn par Microsoft. Il vous permet de gérer et d’analyser vos dépenses Azure et ce que vous dépensez auprès d’autres fournisseurs de clouds publics. Il existe des niveaux gratuits et payants, offrant un grande quantité de fonctionnalités, comme indiqué dans la [présentation](https://docs.microsoft.com/azure/cost-management/overview).
- **Budgets et groupes d’actions Azure :** Jusqu’à récemment, la détermination du coût d’un service et les réponses à y apporter étaient un exercice plutôt manuel. Avec l’introduction des budgets Azure et des API correspondantes, il est maintenant possible de créer des actions (comme dans [cet exemple](https://channel9.msdn.com/Shows/Azure-Friday/Managing-costs-with-the-Azure-Budgets-API-and-Action-Groups)) quand les coûts atteignent un seuil. Par exemple, arrêter un groupe de ressources de « test » dès qu’il atteint 100 % de son budget ou [autre exemple].
- **Azure Advisor** : connaître le coût d’un service est une chose, savoir exploiter ces informations en est une autre. [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) vous fait des suggestions quant aux mesures à prendre pour réaliser des économies, améliorer la fiabilité ou même accroître la sécurité.

### <a name="external-cost-management-tools"></a>Outils de gestion des coûts externes

- **Power BI Azure Consumption Insights :** Vous souhaitez créer vos propres visualisations pour votre organisation ? Dans ce cas, le pack de contenu Azure Consumption Insights pour Power BI est l’outil qu’il vous faut. Avec ce pack de contenu et Power BI, vous pouvez créer des visualisations personnalisées de façon à représenter votre organisation, à effectuer une analyse plus approfondie des coûts et à ajouter d’autres sources de données pour enrichir ces visualisations.

- **API de consommation :** Les [API de consommation](https://docs.microsoft.com/rest/api/consumption) vous donnent un accès programmatique à des données de coûts et d’utilisation, ainsi qu’à des informations sur les budgets, les instances réservées et les coûts de place de marché. Seuls les Accord de Mise en Œuvre Entreprise et certains abonnements directs web ont accès à ces API. Cependant, celles-ci vous permettent d’intégrer vos données de coûts dans vos propres outils et entrepôts de données. Vous pouvez également [accéder à ces API par le biais d’Azure CLI](https://docs.microsoft.com/cli/azure/consumption?view=azure-cli-latest).

Les clients qui sont des utilisateurs chevronnés du cloud suivent certaines meilleures pratiques :

- **Supervision active des coûts.** Les organisations qui ont une certaine expérience d’Azure supervisent constamment les coûts et prennent des mesures quand cela s’avère nécessaire. Certaines organisations emploient même des personnes pour effectuer des analyses et suggérer des changements dans l’utilisation, des postes qui sont largement rentabilisés la première fois qu’elles découvrent qu’un cluster HDInsight inutilisé s’exécute depuis des mois.
- **Utilisation d’instances de machines virtuelles réservées.** Un autre principe clé pour gérer les coûts dans le cloud est d’utiliser l’outil adéquat. Si vous avez une machine virtuelle IaaS qui doit rester active 24h/24, 7j/7, vous pouvez réalisez des économies significatives en utilisant une instance de machine virtuelle réservée. Trouver le bon équilibre entre automatiser l’arrêt des machines virtuelles et utiliser des instances réservées demande de l’expérience et de l’analyse.
- **Utilisation efficace de l’automatisation.** De nombreuses charges de travail n’ont pas besoin d’être exécutées tous les jours. Rien que le fait de désactiver une machine virtuelle pendant quatre heures tous les jours peut réduire vos coûts de 15 %. L’automation est vite rentabilisée.
- **Utilisation d’étiquettes de ressource pour une meilleure visibilité.** Comme indiqué ailleurs dans ce document, l’utilisation d’étiquettes de ressource permet de mieux analyser les coûts.

La gestion des coûts est une discipline essentielle à une exécution efficace et efficiente d’un cloud public. Les entreprises qui réussissent sont celles qui parviennent à maîtriser leurs coûts et à les aligner sur leur demande effective, pas celles qui achètent trop et qui espèrent que la demande viendra.

## <a name="automate"></a>Automatisation

Parmi les organisations qui font appel à des fournisseurs de cloud, ce qui distingue celles qui sont matures des autres est le niveau d’automation qu’elles incorporent. L’automation est un processus sans fin et un domaine dans lequel votre organisation doit investir du temps et des ressources à mesure qu’elle migre dans le cloud. L’automatisation permet notamment un déploiement cohérent des ressources (en lien direct avec un autre concept de structure de base, Modèles et DevOps) en vue de corriger les problèmes. L’automation est le « tissu conjonctif » de la structure Azure qui relie chacune des parties entre elles.

Plusieurs outils peuvent vous aider à générer cette fonctionnalité, notamment des outils internes comme Azure Automation, Event Grid et Azure CLI, mais aussi un nombre important d’outils tiers comme Terraform, Jenkins, Chef et Puppet. Les outils d’automatisation de base incluent Azure Automation, Event Grid et Azure Cloud Shell.

- **Azure Automation** est une fonctionnalité cloud qui vous permet de créer des runbooks (dans PowerShell ou Python) et d’automatiser les processus, de configurer les ressources et même d’appliquer des correctifs. [Azure Automation](https://docs.microsoft.com/azure/automation/automation-intro) propose un ensemble complet de fonctionnalités multiplateformes qui sont indispensables à votre déploiement, mais elles sont trop nombreuses pour être présentées ici en détail.
- **Event Grid** est un système de routage d’événements complètement managé qui vous permet de réagir aux événements qui se produisent dans votre environnement Azure. Si Azure Automation est le tissu conjonctif des organisations cloud matures, [Event Grid](https://docs.microsoft.com/azure/event-grid) est le tissu conjonctif d’une automatisation efficace. Avec Event Grid, vous pouvez créer une action serverless simple pour envoyer un e-mail à un administrateur chaque fois qu’une ressource est créée et journaliser cette ressource dans une base de données. Ce même Event Grid peut envoyer une notification quand une ressource est supprimée et supprimer l’élément de la base de données.
- **Azure Cloud Shell** est un [interpréteur de commandes](https://docs.microsoft.com/azure/cloud-shell/overview) interactif basé sur navigateur qui permet de gérer les ressources dans Azure. Il fournit un environnement complet pour PowerShell ou Bash qui se lance si nécessaire (et est géré automatiquement), si bien que vous disposez d’un environnement cohérent à partir duquel exécuter vos scripts. Azure Cloud Shell vous donne accès à d’autres outils clés (déjà installés) pour automatiser votre environnement, notamment [Azure CLI](https://docs.microsoft.com/cli/azure/get-started-with-azure-cli?view=azure-cli-latest), [Terraform](https://docs.microsoft.com/azure/virtual-machines/linux/terraform-install-configure) et une liste croissante d’autres [outils](https://azure.microsoft.com/updates/cloud-shell-new-cli-tools-and-font-size-selection) destinés à gérer conteneurs, bases de données (sqlcmd) et bien plus encore.

L’automatisation est une tâche à temps plein qui deviendra rapidement l’une des tâches opérationnelles les plus importantes au sein de votre équipe cloud. Les organisations qui misent en priorité sur l’automation sont celles qui tirent le meilleur parti d’Azure :

- **Gestion des coûts :** Recherche active d’opportunités et création d’automatisation pour redimensionner les ressources, effectuer un scale-up ou un scale-down et désactiver les ressources non utilisées.
- **Flexibilité opérationnelle :** En utilisant l’automatisation (avec des modèles et DevOps), vous bénéficiez d’un niveau de répétabilité qui accroît la disponibilité, améliore la sécurité et permet à votre équipe de se concentrer sur la résolution des problèmes métier.

## <a name="templates-and-devops"></a>Modèles et DevOps

Comme nous l’avons souligné dans la section Automatiser, votre objectif en tant qu’organisation doit être de provisionner les ressources à l’aide de scripts et de modèles sous contrôle de code source et de limiter la configuration interactive de vos environnements. Cette approche d’« infrastructure en tant que code » couplée à un processus DevOps rigoureux pour le déploiement continu peut assurer la cohérence et réduire la dérive dans vos environnements. Pratiquement toutes les ressources Azure peuvent être déployées à l’aide de [modèles JSON Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-template-deploy) en combinaison avec PowerShell ou l’interface CLI multiplateforme d’Azure et des outils comme Terraform de HashiCorp (qui bénéficie d’une prise en charge de premier ordre et qui est intégré avec Azure Cloud Shell).

Certains articles comme [Bonnes pratiques pour utiliser des modèles Azure Resource Manager](https://blogs.msdn.microsoft.com/mvpawardprogram/2018/05/01/azure-resource-manager) font un excellent exposé sur les bonnes pratiques et les enseignements tirés de la mise en œuvre d’une approche DevOps sur des modèles Azure Resource Manager avec la chaîne d’outils [Azure DevOps](https://docs.microsoft.com/azure/devops/user-guide/?view=vsts). Prenez le temps de développer un ensemble de modèles en fonction des besoins spécifiques de votre organisation, ainsi que des pipelines de livraison continue avec les chaînes d’outils DevOps (comme Azure DevOps, Jenkins, Bamboo, TeamCity et Concourse), en particulier pour vos environnements de production et d’assurance qualité. Il existe une grande bibliothèque de [modèles de démarrage rapide Azure](https://github.com/Azure/azure-quickstart-templates) sur GitHub qui peuvent vous servir de point de départ pour les modèles, et vous pouvez rapidement créer des pipelines de livraison basés sur le cloud avec Azure DevOps.

En guise de bonne pratique pour les abonnements de production ou les groupes de ressources, votre objectif doit être d’utiliser la sécurité RBAC pour interdire les utilisateurs interactifs par défaut et d’utiliser des pipelines de livraison continue automatisés basés sur des principaux de service pour provisionner toutes les ressources et livrer tout le code d’application. Aucun administrateur ou développeur ne doit toucher au portail Azure pour configurer les ressources de manière interactive. Ce niveau de DevOps demande un effort concerté et utilise tous les concepts de la structure Azure. Par ailleurs, il fournit un environnement cohérent et plus sécurisé qui répondra aux besoins de votre organisation à mesure qu’elle se développera.

> [!TIP]
> Pour concevoir et développer des modèles Azure Resource Manager complexes, utilisez des [modèles liés](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-linked-templates) de façon à organiser et à refactoriser les relations de ressources complexes à partir de fichiers JSON monolithiques. Cela vous permettra de gérer les ressources individuellement et vos modèles gagneront en lisibilité, testabilité et réutilisabilité.

Azure est un fournisseur de cloud hyperscale. Tandis que votre organisation passe de l’utilisation de serveurs locaux à celle du cloud, avoir recours aux mêmes concepts que ceux utilisés par les fournisseurs de cloud et les applications SaaS lui permet de répondre à ses besoins avec beaucoup plus d’efficacité.

## <a name="core-network"></a>Réseau principal

La composante finale du modèle de référence de structure Azure est essentielle à la façon dont votre organisation accède à Azure de manière sécurisée. L’accès aux ressources peut être interne (dans le réseau de l’entreprise) ou externe (par le biais d’internet). Il est facile pour les utilisateurs de votre organisation de placer par inadvertance des ressources au mauvais endroit et de potentiellement les exposer à un accès malveillant. Comme pour les appareils locaux, les entreprises doivent ajouter des contrôles appropriés pour s’assurer que les utilisateurs d’Azure prennent les bonnes décisions. Pour la gouvernance de l’abonnement, nous identifions des ressources principales qui fournissent le contrôle d’accès de base. Les ressources principales sont constituées des éléments suivants :

- Les **réseaux virtuels** sont des objets Conteneur de sous-réseaux. Bien qu’ils ne soient pas strictement nécessaires, ils sont souvent utilisés lors de la connexion d’applications à des ressources d’entreprise internes.
- Les **routes définies par l’utilisateur** vous permettent de manipuler la table de routage au sein d’un sous-réseau, ce qui vous permet d’envoyer le trafic par l’intermédiaire d’une appliance virtuelle réseau ou à une passerelle distante sur un réseau virtuel appairé.
- L’**appairage de réseaux virtuels** vous permet de connecter plusieurs réseaux virtuels Azure sans interruption, de créer des conceptions Hub and Spoke plus complexes ou des réseaux de services partagés.
- **Points de terminaison de service.** Par le passé, les services PaaS s’appuyaient sur différentes méthodes pour sécuriser l’accès aux ressources des réseaux virtuels. Les points de terminaison de service vous permettent de sécuriser l’accès aux services PaaS activés à partir de points de terminaison connectés **uniquement**, ce qui améliore la sécurité globale.
- Les **groupes de sécurité** constituent un ensemble complet de règles qui vous permettent d’autoriser ou de refuser le trafic entrant et sortant dans les ressources Azure. Les [groupes de sécurité](https://docs.microsoft.com/azure/virtual-network/security-overview) sont constitués de règles de sécurité, qui peuvent être enrichies avec des **balises de service** (qui définissent des services Azure courants comme Azure Key Vault ou Azure SQL Database) et des **groupes de sécurité d’application** (qui définissent la structure d’application, comme les serveurs web ou les serveurs d’applications).

> [!TIP]
> Vous pouvez utiliser des balises de service et des groupes de sécurité d’application dans vos groupes de sécurité réseau non seulement pour améliorer la lisibilité de vos règles (ce qui est essentiel pour en comprendre l’impact), mais aussi pour permettre une micro-segmentation efficace au sein d’un sous-réseau plus vaste, ce qui réduit la prolifération et améliore la flexibilité.

### <a name="azure-virtual-datacenter"></a>Centre de données virtuel Azure

Azure met à disposition les fonctionnalités internes et tierces de notre vaste réseau de partenaires qui vous permettent d’avoir une posture de sécurité efficace. Plus important encore, Microsoft communique des bonnes pratiques et des recommandations via le [centre de données virtuel Azure](./networking-vdc.md). Quand vous passez d’une charge de travail unique à plusieurs charges de travail qui utilisent des fonctionnalités hybrides, les recommandations du centre de données virtuel vous indiquent comment mettre en place un réseau flexible capable de croître en même temps que vos charges de travail Azure.

## <a name="next-steps"></a>Étapes suivantes

La gouvernance est essentielle au succès d’Azure. Cet article vise l’implémentation technique d’une structure d’entreprise, mais traite uniquement de processus plus larges et de relations entre les composants. La gouvernance de stratégies s’applique du haut vers le bas et dépend des objectifs de l’entreprise. Naturellement, la création d’un modèle de gouvernance pour Azure inclut des représentants du service informatique. Mais, plus important encore, elle doit également intégrer des responsables de groupes professionnels et de la gestion des risques et de la sécurité. Au final, une structure d’entreprise consiste à limiter les risques métier afin de faciliter la mission et la poursuite des objectifs d’une organisation.

Maintenant que vous connaissez mieux la gouvernance des abonnements, il est temps pour voir ces recommandations dans la pratique. Pour plus d’informations, consultez [Bonnes pratiques de préparation pour Azure](../ready/azure-best-practices/index.md).
