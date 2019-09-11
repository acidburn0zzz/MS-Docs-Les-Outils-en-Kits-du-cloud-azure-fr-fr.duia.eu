---
title: Guide de décision concernant l’identité
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment utiliser l’identité comme un service principal lors des migrations vers Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 2e1ba47201285559be784fafe6b39bdbde0c35ed
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70817075"
---
# <a name="identity-decision-guide"></a>Guide de décision concernant l’identité

Dans tous les environnements (local, hybride ou cloud uniquement), le service informatique doit contrôler les administrateurs, les utilisateurs et les groupes qui ont accès aux ressources. Les services de gestion des identités et des accès (IAM) vous permettent de gérer le contrôle des accès dans le cloud.

![Options d’identité, de la moins complexe à la plus complexe, dans l’ordre des liens ci-dessous](../../_images/discovery-guides/discovery-guide-identity.png)

Passer à : [Déterminer les exigences d’intégration des identités](#determine-identity-integration-requirements) | [Base de référence cloud](#cloud-baseline) | [Synchronisation des annuaires](#directory-synchronization) | [Services de domaines hébergés dans le cloud](#cloud-hosted-domain-services) | [Active Directory Federation Services](#active-directory-federation-services) | [En savoir plus](#learn-more)

Plusieurs options sont disponibles pour gérer les identités dans un environnement cloud. Ces options varient au niveau du coût et de la complexité. Le niveau d’intégration requis avec votre infrastructure d’identité sur site existante est un facteur clé dans la structuration de vos services d’identité cloud.

Dans Azure, Azure Active Directory (Azure AD) fournit un niveau basique de gestion des identités et de contrôle d’accès aux ressources cloud. Toutefois, si l’infrastructure Active Directory de votre organisation présente une structure en forêt complexe ou des unités d’organisation personnalisées, il se peut que vos charges de travail basées sur le cloud nécessitent la synchronisation des annuaires avec Azure AD pour bénéficier d’un ensemble cohérent d’identités, de groupes et de rôles sur tous vos environnements locaux et cloud. En outre, pour garantir la prise en charge des applications qui dépendent de mécanismes d’authentification hérités, il se peut que vous deviez déployer Active Directory Domain Services (AD DS) dans le cloud.

La gestion des identités basée sur le cloud est un processus itératif. Pour un premier déploiement, il se peut que vous souhaitiez débuter par une solution cloud native comprenant un petit ensemble d’utilisateurs et de rôles correspondants. À mesure qu’avance votre migration, vous devrez intégrer votre solution de gestion des identités à l’aide de la synchronisation d’annuaire, ou ajouter des services de domaine dans le cadre de vos déploiements cloud. Réétudiez votre stratégie d’identité dans chaque itération du processus de migration.

## <a name="determine-identity-integration-requirements"></a>Déterminer les exigences d’intégration des identités

| Question | Base de référence cloud | Synchronisation de répertoires | Services de domaines hébergés dans le cloud | Services de fédération Active Directory (AD FS) |
|------|------|------|------|------|
| À l’heure actuelle, vous manque-t-il un service d’annuaire local ? | OUI | Non | Non | Non |
| Vos charges de travail doivent-elles utiliser un ensemble commun d’utilisateurs et de groupes dans l’environnement cloud et l’environnement local ? | Non | OUI | Non | Non |
| Vos charges de travail dépendent-elles des mécanismes d’authentification hérités, tels NTLM ou Kerberos ? | Non | Non | OUI | OUI |
| Avez-vous besoin de l’authentification unique auprès de plusieurs fournisseurs d’identité ? | Non | Non | Non | OUI |

Dans le cadre de la planification de votre migration vers Azure, vous devez déterminer la meilleure méthode pour intégrer votre gestion des identités et les services d’identité cloud. Les paragraphes suivants illustrent des scénarios d’intégration courants.

### <a name="cloud-baseline"></a>Base de référence cloud

Azure AD est le système natif de gestion des identités et des accès (IAM) qui permet d’accorder aux utilisateurs et aux groupes un accès aux fonctionnalités de gestion de la plateforme Azure. Si votre organisation ne dispose pas d’une solution locale de gestion des identités suffisante et si vous prévoyez d’effectuer la migration de charges de travail afin qu’elles soient compatibles avec les mécanismes d’authentification basés sur le cloud, vous devez créer votre infrastructure d’identité en vous basant sur Azure AD.

**Conditions nécessaires pour la base de référence cloud** : L’utilisation d’une infrastructure d’identité cloud native (uniquement) implique les hypothèses suivantes :

- Vos ressources basées sur le cloud ne peuvent présenter aucune dépendance avec les services d’annuaire locaux ni les serveurs Active Directory, ou bien les charges de travail doivent être modifiées pour supprimer ces dépendances.
- Les charges de travail d’application ou de service qui sont en cours de migration doivent prendre en charge les mécanismes d’authentification compatibles avec Azure AD ou bien elles peuvent être modifiées facilement pour les prendre en charge. Azure AD s’appuie sur des mécanismes d’authentification Internet (SAML, OAuth et OpenID Connect, par exemple). Il se peut que les charges de travail existantes qui dépendent de méthodes d’authentification héritées, et qui utilisent des protocoles tels que NTLM ou Kerberos, doivent être refactorisées avant la migration vers le cloud, à l’aide du modèle de base de référence cloud.

> [!TIP]
> En effectuant la migration complète de vos services d’identité vers Azure AD, vous éliminez le besoin de maintenir votre propre infrastructure d’identité et vous simplifiez considérablement votre gestion informatique.
>
> Toutefois, Azure AD ne peut pas remplacer entièrement une infrastructure Active Directory locale traditionnelle. Il se peut que les fonctionnalités d’annuaire (méthodes d’authentification héritées, gestion des ordinateurs ou stratégies de groupe, par exemple) ne soient pas disponibles si vous ne déployez pas les outils et les services nécessaires dans le cloud.
>
> Si vous avez besoin d’intégrer vos identités ou vos services de domaine locaux à vos déploiements cloud, consultez la section ci-dessous concernant la synchronisation d’annuaires et les modèles de services de domaine hébergés dans le cloud.

### <a name="directory-synchronization"></a>Synchronisation de répertoires

Pour les organisations qui disposent déjà d’une infrastructure Active Directory locale, la synchronisation d’annuaires est souvent la meilleure solution pour conserver la gestion des accès et des utilisateurs existante tout en bénéficiant des capacités IAM nécessaires pour gérer les ressources cloud. Ce processus permet de dupliquer en continu les informations d’annuaire entre Azure AD et les services d’annuaire locaux. Ainsi, les utilisateurs peuvent utiliser les mêmes informations d’identification, la même identité, les mêmes rôles et les mêmes autorisations dans l’ensemble de votre organisation.

Remarque : Les organisations qui ont adopté Office 365 ont peut-être déjà implémenté [la synchronisation d’annuaires](/office365/enterprise/set-up-directory-synchronization) entre leur infrastructure locale Active Directory et Azure Active Directory.

**Conditions nécessaires à la synchronisation d’annuaires** : L’utilisation d’une solution d’identité synchronisée implique les hypothèses suivantes :

- Vous devez maintenir un ensemble commun de comptes utilisateur et de groupes entre le cloud et votre infrastructure informatique locale.
- Vos services d’identité locaux prennent en charge la réplication avec Azure AD.

> [!TIP]
> Toutes les charges de travail basées sur le cloud et dépendantes de mécanismes d’authentification hérités qui sont fournis par les serveurs Active Directory locaux, et qui ne sont pas pris en charge par Azure AD, doivent rester connectées aux services de domaine locaux ou aux serveurs virtuels dans l’environnement cloud qui fournit ces services. L’utilisation de services d’identité locaux introduit également des dépendances de connectivité entre les réseaux cloud et locaux.

### <a name="cloud-hosted-domain-services"></a>Services de domaines hébergés dans le cloud

Si vous disposez de charges de travail qui dépendent d’authentification par revendication à l’aide de protocoles hérités (Kerberos ou NTLM, par exemple), et qu’il est impossible de refactoriser ces charges de travail pour accepter des protocoles d’authentification modernes (tels que SAML, OAuth et OpenID Connect), vous devrez peut-être migrer certains de vos services de domaine vers le cloud dans le cadre de votre déploiement cloud.

Ce modèle implique le déploiement de machines virtuelles exécutant Active Directory sur vos réseaux virtuels basés sur le cloud, afin de fournir Active Directory Domain Services (AD DS) aux ressources du cloud. Les applications et les services existants qui font l’objet d’une migration vers votre réseau cloud doivent pouvoir utiliser ces serveurs d’annuaires hébergés dans le cloud sans nécessiter de modifications importantes.

Il se peut que vos services de domaine et de répertoires existants soient toujours utilisés dans votre environnement local. Dans ce scénario, nous vous recommandons d’utiliser également la synchronisation d’annuaires pour fournir un ensemble d’utilisateurs et de rôles commun dans les environnements cloud et local.

**Conditions nécessaires pour les services de domaines hébergés dans le cloud** : L’exécution d’une migration de répertoire implique les hypothèses suivantes :

- Vos charges de travail dépendent de l’authentification par revendication à l’aide de protocoles tels que Kerberos ou NTLM.
- Vos machines virtuelles de charge de travail doivent être jointes au domaine afin d’assurer la gestion ou l’application des objectifs stratégiques de groupe Active Directory.

> [!TIP]
> La migration de répertoire associée à des services de domaine hébergés dans le cloud offre une grande souplesse lors de la migration des charges de travail existantes. Toutefois, l’hébergement de machines virtuelles dans votre réseau virtuel cloud (pour fournir ces services) augmente la complexité de vos tâches d’administration informatique. Au fur et à mesure que votre expérience de migration cloud gagne en maturité, examinez les besoins de maintenance à long terme associés à l’hébergement de ces serveurs. Déterminez si la refactorisation des charges de travail existantes pour les rendre compatibles avec les fournisseurs d’identité cloud (comme Azure Active Directory) peut réduire les besoins de ces serveurs hébergés dans le cloud.

### <a name="active-directory-federation-services"></a>Services de fédération Active Directory (AD FS)

La fédération des identités établit des relations d’approbation entre plusieurs systèmes de gestion des identités afin de permettre l’authentification et des fonctionnalités d’autorisation communes. Vous pouvez ensuite prendre en charge les fonctionnalités d’authentification unique sur plusieurs domaines dans votre organisation ou les systèmes d’identité gérés par vos clients ou partenaires commerciaux.

Azure AD prend en charge la fédération de domaines Active Directory locaux à l’aide d’[Active Directory Federation Services](/azure/active-directory/hybrid/how-to-connect-fed-whatis) (AD FS). Consultez l’architecture de référence [Extension d’AD FS vers Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adfs) pour en savoir plus sur l’implémentation dans Azure.

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations sur les services d’identité dans Azure, consultez :

- [Azure AD](https://azure.microsoft.com/services/active-directory). Azure AD fournit un service d’identité basé sur le cloud. Il vous permet de gérer l’accès à vos ressources Azure et de contrôler la gestion des identités, l’inscription des appareils, l’approvisionnement des utilisateurs, le contrôle de l’accès aux applications et la protection des données.
- [Azure AD Connect](/azure/active-directory/hybrid/whatis-hybrid-identity). L’outil Azure AD Connect vous permet de connecter des instances Azure AD avec vos solutions de gestion des identités existantes, en autorisant la synchronisation de votre répertoire existant avec le cloud.
- [Contrôle d’accès en fonction du rôle](/azure/role-based-access-control/overview) (RBAC). Azure AD fournit le contrôle des accès en fonction du rôle pour gérer efficacement et en toute sécurité l’accès aux ressources dans le plan de gestion. Les travaux et les responsabilités sont classés par rôle, et les utilisateurs sont assignés à ces rôles. Le RBAC vous permet de contrôler les utilisateurs qui ont accès à une ressource, ainsi que les actions qu’ils peuvent effectuer sur cette ressource.
- [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure) (PIM). PIM réduit le temps d’exposition des privilèges d’accès aux ressources et augmente votre visibilité en matière d’utilisation grâce à des rapports et des alertes. PIM autorise les utilisateurs à utiliser ces privilèges uniquement pendant une période précise (juste-à-temps (JIT)), ou en leur attribuant des privilèges pour une plus courte durée après laquelle ces privilèges sont automatiquement révoqués.
- [Intégrer des domaines Active Directory locaux avec Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad). Cette architecture de référence fournit un exemple de synchronisation d’annuaires entre des domaines Active Directory locaux et Azure AD.
- [Étendre Active Directory Domain Services (AD DS) à Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adds-extend-domain). Cette architecture de référence fournit un exemple de déploiement de serveurs AD DS pour étendre les services de domaine aux ressources basées sur le cloud.
- [Étendre les services de fédération Active Directory (AD FS) à Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adfs). Cette architecture de référence configure Active Directory Federation Services (ADFS) afin d’effectuer l’authentification fédérée et l’autorisation auprès de votre répertoire Azure AD.

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, l’identité ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
