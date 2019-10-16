---
title: Scénarios et exemples de gouvernance d’abonnements
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Fournit des exemples montrant comment implémenter la gestion des abonnements Azure pour des scénarios courants.
author: rdendtler
ms.author: rodend
ms.date: 01/03/2017
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.openlocfilehash: ffda6a8f11954895e934f310c1a53c95fb2e1351
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72378043"
---
# <a name="examples-of-implementing-azure-enterprise-scaffold"></a>Exemples d’implémentation d’une structure d’entreprise Azure

> [!NOTE]
> La structure d’entreprise Azure a été intégrée au framework d’adoption du cloud Microsoft. Le contenu de cet article est maintenant représenté dans la section [Prêt](../ready/index.md) du nouveau framework. Cet article sera déprécié début 2020. Pour commencer à utiliser le nouveau processus, reportez-vous à la [vue d’ensemble Prêt](../ready/index.md), à la [création de votre première zone d’accueil](../ready/azure-setup-guide/migration-landing-zone.md) et/ou aux [considérations relatives aux zones d’accueil](../ready/considerations/index.md).

Cet article fournit des exemples montrant comment une entreprise peut implémenter les recommandations pour une [structure d’entreprise Azure](./azure-scaffold.md). Elle utilise une société fictive nommée Contoso pour illustrer les bonnes pratiques pour des scénarios courants.

## <a name="background"></a>Arrière-plan

Contoso est une société présente dans le monde entier qui fournit des solutions de chaîne d’approvisionnement pour les clients de tous les domaines, d’un modèle Logiciel en tant que Service à un modèle de package déployé localement. Elle développe des logiciels dans le monde entier avec des centres de développement principaux en Inde, aux États-Unis et au Canada.

La partie ISV de la société est divisée en plusieurs unités commerciales indépendantes qui gèrent des produits dans une activité spécifique. Chaque unité commerciale a ses propres développeurs, chefs de produit et architectes.

La division Enterprise Technology Services (ETS) fournit une fonctionnalité informatique centralisée et gère plusieurs centres de données dans lesquels les divisions hébergent leurs applications. Outre la gestion des centres de données, l’organisation ETS fournit et gère la collaboration centralisée (par exemple, les e-mails et les sites web) et les services de téléphonie/réseau. Elle gère également les charges de travail côté client pour les divisions commerciales plus petites qui ne disposent pas de personnel d’exploitation.

Les personnes suivantes sont utilisées dans cet article :

- Dave est l’administrateur Azure ETS.
- Alice est la directrice du développement de la division Chaîne logistique Contoso.

Contoso doit créer une application de métier et une application destinée aux clients. Elle a décidé d’exécuter les applications dans Azure. Dave lit l’article [Gouvernance normative de l’abonnement](./azure-scaffold.md) et se prépare à appliquer les recommandations.

## <a name="scenario-1-line-of-business-application"></a>Scénario 1 : application métier

Contoso crée un système de gestion du code source (BitBucket) à utiliser par les développeurs dans le monde entier. L’application utilise IaaS (infrastructure as a service) pour l’hébergement et se compose de serveurs web et d’un serveur de base de données. Les développeurs accèdent aux serveurs dans leurs environnements de développement, mais ils n’ont pas besoin d’accéder aux serveurs dans Azure. Contoso ETS souhaite autoriser le propriétaire de l’application et l’équipe à gérer l’application. L’application est uniquement disponible sur le réseau d’entreprise de Contoso. Dave doit configurer l’abonnement pour cette application. L’abonnement hébergera également d’autres logiciels liés au développement à l’avenir.

### <a name="naming-standards-and-resource-groups"></a>Normes d’attribution de noms et groupes de ressources

Dave crée un abonnement pour prendre en charge des outils de développement qui sont communs à toutes les divisions. Dave doit pouvoir affecter des noms explicites pour l’abonnement et les groupes de ressources (pour l’application et les réseaux). Il crée l’abonnement et les groupes de ressources suivants :

| Item | Nom | Description |
| --- | --- | --- |
| Subscription |Contoso ETS DeveloperTools Production |Prend en charge des outils de développement courants |
| Resource group |bitbucket-prod-rg |Contient le serveur d’applications web et le serveur de base de données |
| Resource group |corenetworks-prod-rg |Contient les réseaux virtuels et la connexion à la passerelle de site à site |

### <a name="role-based-access-control"></a>Contrôle d’accès en fonction du rôle

Après avoir créé son abonnement, Dave veut s’assurer que les équipes et les propriétaires d’applications appropriés peuvent accéder à leurs ressources. Dave tient compte du fait que chaque équipe a des exigences différentes. Il utilise les groupes qui ont été synchronisés depuis l’annuaire Active Directory de Contoso local sur Azure Active Directory et fournit le niveau d’accès adapté aux équipes.

Dave attribue les rôles suivants pour l’abonnement :

| Role | Affecté à | Description |
| --- | --- | --- |
| [Propriétaire](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) |ID géré à partir de l’annuaire Active Directory local de Contoso |Cet ID est contrôlé avec un accès juste-à-temps (JIT) par le biais de l’outil de gestion des identités de Contoso et garantit que l’accès propriétaire à l’abonnement est entièrement audité |
| [Lecteur de sécurité](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#security-reader) |Service de gestion de la sécurité et des risques |Ce rôle permet aux utilisateurs de consulter l’Azure Security Center et l’état des ressources |
| [Contributeur de réseau](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#network-contributor) |Équipe réseau |Ce rôle permet à l’équipe réseau de Contoso de gérer la connexion VPN de site à site et les réseaux virtuels |
| *Rôle personnalisé* |Propriétaire de l’application |Dave crée un rôle qui permet de modifier les ressources au sein du groupe de ressources. Pour plus d’informations, consultez [Rôles personnalisés dans le contrôle d’accès en fonction du rôle (RBAC) Azure](https://docs.microsoft.com/azure/role-based-access-control/custom-roles). |

### <a name="policies"></a>Stratégies

Dave a les exigences suivantes pour la gestion des ressources dans l’abonnement :

- Les outils de développement assistant les développeurs dans le monde entier, il ne souhaite pas empêcher les utilisateurs de créer des ressources dans n’importe quelle région. Toutefois, il doit savoir où les ressources sont créées.
- Il doit surveiller les coûts. Par conséquent, il souhaite empêcher les propriétaires d’applications de créer des machines virtuelles inutiles et coûteuses.
- Étant donné que cette application sert aux développeurs de nombreuses divisions, il souhaite baliser chaque ressource avec la division et le propriétaire d’application. À l’aide de ces balises, ETS peut facturer les équipes appropriées.

Il crée les stratégies suivantes par le biais d’[Azure Policy](https://docs.microsoft.com/azure/azure-policy/azure-policy-introduction) :

| Champ | Résultat | Description |
| --- | --- | --- |
| location |audit |Auditer la création de ressources dans n’importe quelle région |
| Type |deny |Refuser la création de machines virtuelles de série G |
| tags |deny |Exiger la balise de propriétaire de l’application |
| tags |deny |Exiger la balise du centre de coût |
| tags |append |Ajouter le nom de la balise **BusinessUnit** et la valeur de la balise **ETS** à toutes les ressources |

### <a name="resource-tags"></a>Balises de ressource

Dave sait qu’il doit disposer d’informations spécifiques sur la facturation pour identifier le centre de coût pour l’implémentation du BitBucket. En outre, Dave souhaite connaître toutes les ressources qu’ETS possède.

Il ajoute les [balises](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) suivantes aux groupes de ressources et aux ressources.

| Nom de la balise | Valeur de la balise |
| --- | --- |
| ApplicationOwner |Le nom de la personne responsable de cette application |
| CostCenter |Le centre de coût du groupe qui paie pour la consommation d’Azure |
| BusinessUnit |**ETS** (la division associée à l’abonnement) |

### <a name="core-network"></a>Réseau principal

L’équipe Contoso ETS en charge de la gestion de la sécurité des informations et des risques passe en revue le plan de migration des applications dans Azure proposé par Dave. Elle veut s’assurer que l’application n’est pas exposée sur Internet. Dave a également des applications de développeur qui seront déplacées vers Azure à l’avenir. Ces applications nécessitent des interfaces publiques. Pour répondre à ces exigences, il fournit des réseaux virtuels internes et externes et un groupe de sécurité réseau pour limiter l’accès.

Il crée les ressources suivantes :

| Type de ressource | Nom | Description |
| --- | --- | --- |
| Réseau virtuel |internal-vnet |Utilisé avec l’application BitBucket et connecté au réseau d’entreprise de Contoso par le biais d’ExpressRoute. Un sous-réseau (`bitbucket`) fournit l’application avec un espace d’adresses IP spécifique |
| Réseau virtuel |external-vnet |Disponible pour des applications futures qui nécessitent des points de terminaison accessible au public |
| Groupe de sécurité réseau |bitbucket-nsg |Garantit que la surface d’attaque de cette charge de travail est réduite en autorisant des connexions uniquement sur le port 443 du sous-réseau sur lequel l’application réside (`bitbucket`) |

### <a name="resource-locks"></a>Verrous de ressources

Dave reconnaît que la connectivité du réseau d’entreprise de Contoso au réseau virtuel interne doit être protégée de tout script versatile ou de toute suppression accidentelle.

Il crée le [verrou de ressources suivant](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) :

| Type de verrou | Ressource | Description |
| --- | --- | --- |
| **CanNotDelete** |internal-vnet |Empêche les utilisateurs de supprimer le réseau virtuel ou des sous-réseaux, mais n’empêche pas l’ajout de nouveaux sous-réseaux |

### <a name="azure-automation"></a>Azure Automation

Dave n’a rien à automatiser pour cette application. Même s’il a créé un compte Azure Automation, il ne l’utilisera pas au cours des étapes initiales.

### <a name="azure-security-center"></a>Azure Security Center

Le service de gestion des services informatiques Contoso doit rapidement identifier et gérer les menaces. Il doit également comprendre les problèmes éventuels.

Pour répondre à ces exigences, Dave active [Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-intro) et fournit l’accès au rôle Lecteur de sécurité.

## <a name="scenario-2-customer-facing-app"></a>Scénario 2 : application destinée aux clients

La direction de l’entreprise dans la division Chaîne logistique a identifié différentes possibilités d’accroître l’engagement auprès des clients de Contoso à l’aide d’une carte de fidélité. L’équipe d’Alice doit créer cette application et décide qu’Azure augmente la capacité à répondre aux besoins métier. Alice travaille avec Dave d’ETS pour configurer deux abonnements pour le développement et le fonctionnement de cette application.

### <a name="azure-subscriptions"></a>Abonnements Azure

Dave se connecte à Azure Enterprise Portal et voit que le service Chaîne d’approvisionnement existe déjà. Toutefois, comme ce projet est le premier projet de développement de l’équipe en charge de la chaîne d’approvisionnement dans Azure, Dave détecte le besoin d’un nouveau compte pour l’équipe de développement d’Alice. Il crée le compte « R & D » pour son équipe et octroie l’accès à Alice. Alice se connecte au portail Azure et crée deux abonnements : l’un destiné aux serveurs de développement et l’autre dédié aux serveurs de production. Elle suit les normes d’affectation de noms précédemment établies lors de la création des abonnements suivants :

| Utilisation de l’abonnement | Nom |
| --- | --- |
| Développement |Contoso SupplyChain ResearchDevelopment LoyaltyCard Development |
| Production |Contoso SupplyChain Operations LoyaltyCard Production |

### <a name="policies"></a>Stratégies

Dave et Alice discutent de l’application et concluent que cette application sert uniquement aux clients dans la région Amérique du Nord. Alice et son équipe envisagent d’utiliser l’environnement de service d’application de d’Azure et SQL Azure pour créer l’application. Il se peut qu’ils doivent créer des machines virtuelles pendant le développement. Alice souhaite faire en sorte que les développeurs disposent des ressources dont ils ont besoin pour explorer et examiner les problèmes sans s’inclure dans ETS.

Pour **l’abonnement de développement**, ils créent la stratégie suivante :

| Champ | Résultat | Description |
| --- | --- | --- |
| location |audit |Auditer la création de ressources dans n’importe quelle région |

Elles ne limitent pas le type de référence SKU qu’un utilisateur peut créer pendant le développement et ne nécessitent pas de balises pour tout groupe de ressources ou toute ressource.

Pour **l’abonnement de production**, ils créent les stratégies suivantes :

| Champ | Résultat | Description |
| --- | --- | --- |
| location |deny |Interdire la création de toute ressource en dehors des centres de données des États-Unis |
| tags |deny |Exiger la balise de propriétaire de l’application |
| tags |deny |Exiger une balise de service |
| tags |append |Ajouter une balise pour chaque groupe de ressources qui indique l’environnement de production |

Elles ne limitent pas le type de référence SKU qu’un utilisateur peut créer en mode de production.

### <a name="resource-tags"></a>Balises de ressource

Dave sait qu’il doit disposer d’informations spécifiques pour identifier les départements d’entreprise approprié pour la facturation et la propriété. Il définit des balises de ressources pour les groupes de ressources et les ressources.

| Nom de la balise | Valeur de la balise |
| --- | --- |
| ApplicationOwner |Le nom de la personne responsable de cette application |
| department |Le centre de coût du groupe qui paie pour la consommation d’Azure |
| EnvironmentType |**Production** (même si l’abonnement inclut **Production** dans son nom, inclure cette balise permet de faciliter l’identification en cas de recherche de ressources dans le portail ou sur la facture) |

### <a name="core-networks"></a>Réseaux principaux

L’équipe Contoso ETS en charge de la gestion de la sécurité des informations et des risques passe en revue le plan de migration des applications dans Azure proposé par Dave. Elle veut s’assurer que l’application de la carte de fidélité est correctement isolée et protégée dans un réseau DMZ. Pour satisfaire cette exigence, Alice et Dave créent un réseau virtuel externe et un groupe de sécurité réseau pour isoler l’application de carte de fidélité du réseau d’entreprise de Contoso.

Pour **l’abonnement de développement**, ils créent :

| Type de ressource | Nom | Description |
| --- | --- | --- |
| Réseau virtuel |internal-vnet |Sert à l’environnement de développement de la carte de fidélité de Contoso et est connecté au réseau d’entreprise de Contoso par le biais d’ExpressRoute |

Pour **l’abonnement de production**, ils créent :

| Type de ressource | Nom | Description |
| --- | --- | --- |
| Réseau virtuel |external-vnet |Héberge l’application de carte de fidélité et n’est pas connecté directement à la connexion ExpressRoute de Contoso. Un code est envoyé par le biais du système de code source directement aux services PaaS. |
| Groupe de sécurité réseau |loyaltycard-nsg |Garantit que la surface d’attaque de cette charge de travail est réduite en autorisant uniquement les communications entrantes sur le port TCP 443. Contoso examine également une éventuelle protection supplémentaire par le biais d’un pare-feu d’applications web. |

### <a name="resource-locks"></a>Verrous de ressources

Dave et Alice discutent et décident d’ajouter des verrous de ressources sur certaines ressources clés dans l’environnement afin d’éviter une suppression accidentelle en cas de code errant de type push.

Ils créent le verrou suivant :

| Type de verrou | Ressource | Description |
| --- | --- | --- |
| **CanNotDelete** |external-vnet |Pour empêcher des personnes de supprimer le réseau virtuel ou des sous-réseaux. Le verrou n’empêche pas l’ajout de nouveaux sous-réseaux |

### <a name="azure-automation"></a>Azure Automation

Alice et son équipe de développement disposent de runbooks complets complète pour gérer l’environnement de cette application. Les runbooks permettent l’ajout ou la suppression de nœuds de l’application et d’autres tâches DevOps.

Pour utiliser ces runbooks, ils activent [Automation](https://docs.microsoft.com/azure/automation/automation-intro).

### <a name="azure-security-center"></a>Azure Security Center

Le service de gestion des services informatiques Contoso doit rapidement identifier et gérer les menaces. Il doit également comprendre les problèmes éventuels.

Pour répondre à ces exigences, Dave active l’Azure Security Center. Il garantit qu’Azure Security Center supervise les ressources et fournit un accès aux équipes DevOps et de sécurité.

## <a name="next-steps"></a>Étapes suivantes

- Pour en savoir plus sur la création de modèles Resource Manager, consultez la rubrique [Bonnes pratiques relatives à la création de modèles Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-template-best-practices).
