---
title: Guide de décision concernant le SDN (Software Defined Networking)
description: Utilisez le Cloud Adoption Framework pour Azure pour découvrir comment le SDN (Software Defined Networking) permet de mettre en place un réseau virtualisé géré de manière centralisée par logiciel.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 4fa9f16a2636cf5e8f1340bf51ae39e8db3198b0
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708731"
---
# <a name="software-defined-networking-decision-guide"></a>Guide de décision concernant le SDN (Software Defined Networking)

La mise en réseau définie par logiciel (ou SDN, pour Software Defined Networking) est une architecture réseau conçue pour permettre une fonctionnalité réseau virtualisée qui peut être gérée, configurée et modifiée de manière centralisée par logiciel. Le SDN permet la création de réseaux cloud utilisant les équivalents virtualisés des routeurs physiques, pare-feux et autres appareils réseau utilisés dans des réseaux locaux. Le SDN est essentiel pour la création de réseaux virtuels sécurisés sur les plateformes de cloud public comme Azure.

## <a name="networking-decision-guide"></a>Guide de décision concernant la mise en réseau

![Options de mise en réseau, de la moins complexe à la plus complexe, dans l’ordre des liens ci-dessous](../../_images/decision-guides/decision-guide-software-defined-network.png)

Passer à : [PaaS uniquement](./paas-only.md) | [Natif cloud](./cloud-native.md) | [Zone DMZ cloud](./cloud-dmz.md) [Hybride](./hybrid.md) | [Modèle hub-and-spoke](./hub-spoke.md) | [En savoir plus](#learn-more)

Le SDN fournit plusieurs options avec différents degrés de complexité et de tarification. Le guide de découverte ci-dessus fournit une référence pour personnaliser rapidement ces options afin de s’aligner au mieux sur des stratégies commerciales et technologiques spécifiques.

Le point d’inflexion de ce guide dépend de plusieurs décisions clés que votre équipe de stratégie cloud a prises avant de prendre des décisions sur l’architecture réseau. Les plus importantes sont les décisions concernant votre [définition du patrimoine numérique](../../digital-estate/index.md) et votre [conception de l’abonnement](../subscriptions/index.md) (ce qui peut également nécessiter des données provenant de décisions prises dans le cadre de votre comptabilité cloud et de vos stratégies sur les marchés mondiaux).

Les petits déploiements inférieurs à 1 000 VM dans une seule région sont moins susceptibles d’être fortement affectés par ce point d’inflexion. Inversement, des efforts d’adoption importants avec plus de 1 000 machines virtuelles, de multiples unités commerciales ou de multiples marchés géopolitiques pourraient être considérablement affectés par votre décision SDN et ce point d’inflexion clé.

## <a name="choose-the-right-virtual-networking-architectures"></a>Choisir les bonnes architectures de réseaux virtuels

Cette section développe le guide de décision pour vous aider à choisir les bonnes architectures de réseau virtuel.

Il existe de nombreuses façons de mettre en œuvre les technologies SDN pour créer des réseaux virtuels cloud. La façon dont vous structurez les réseaux virtuels utilisés dans votre migration et la façon dont ces réseaux interagissent avec votre infrastructure informatique existante dépendra d’une combinaison des exigences en matière de charge de travail et de gouvernance.

Lors de la planification de l’architecture de réseau virtuel ou de la combinaison d’architectures à prendre en compte lors de la planification de votre migration vers le Cloud, prenez en compte les questions suivantes pour déterminer ce qui convient à votre entreprise :

| Question | PaaS uniquement | Cloud natif | Zone DMZ cloud | Hybride | Hub-and-spoke |
|-----|-----|-----|-----|-----|-----|
| Votre charge de travail utilisera-t-elle uniquement les services PaaS ? Ses besoins en capacités réseau seront-ils supérieurs à celles fournies par les services eux-mêmes ? | Oui | Non | Non | Non | Non |
| Votre charge de travail nécessite-t-elle une intégration avec des applications sur site ? | Non | Non | Oui | Oui | Oui |
| Avez-vous établi des stratégies de sécurité avancées et une connectivité sécurisée entre vos locaux et vos réseaux cloud ? | Non | Non | Non | Oui | Oui |
| Votre charge de travail nécessite-t-elle des services d’authentification non pris en charge par les services d’identité cloud, ou avez-vous besoin d’un accès direct aux contrôleurs de domaine locaux ? | Non | Non | Non | Oui | Oui |
| Devrez-vous déployer et gérer un grand nombre de machines virtuelles et de charges de travail ? | Non | Non | Non | Non | Oui |
| Devrez-vous fournir une gestion centralisée et une connectivité locale tout en déléguant le contrôle des ressources à des équipes de travail individuelles ? | Non | Non | Non | Non | Oui |

## <a name="virtual-networking-architectures"></a>Architectures de réseaux virtuels

En savoir plus sur les principales architectures réseau définies par le logiciel :

- **[PaaS uniquement](./paas-only.md) :** La plupart des produits PaaS (Platform as a Service) prennent en charge un ensemble limité de fonctions réseau intégrées et peuvent ne pas nécessiter un réseau à définition logicielle explicitement défini pour répondre aux besoins de charge de travail.
- **[Natif cloud](./cloud-native.md) :** Une architecture native cloud gère les charges de travail basées sur le cloud, au moyen de réseaux virtuels reposant sur les fonctionnalités réseau à définition logicielle par défaut de la plateforme cloud, sans avoir recours à des ressources locales ou externes.
- **[Zone DMZ cloud](./cloud-dmz.md) :** Prend en charge une connectivité limitée entre votre réseau local et votre réseau cloud, sécurisée par l’implémentation d’une zone démilitarisée contrôlant étroitement le trafic entre les deux environnements.
- **[Hybride](./hybrid.md) :** L’architecture de réseau cloud hybride permet aux réseaux virtuels d’environnements cloud approuvés d’accéder à vos ressources locales, et vice versa.
- **[Hub-and-spoke](./hub-spoke.md) :** L’architecture hub-and-spoke vous permet de gérer de manière centralisée la connectivité externe et les services partagés, d’isoler les charges de travail individuelles et de surmonter les limites d’abonnement potentielles.

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations sur le SDN (Software-Defined Networking) dans Azure, consultez :

- [Réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) : sur Azure, la capacité fondamentale du SDN est fournie par un réseau virtuel Azure, qui agit comme un cloud analogue aux réseaux physiques locaux. Les réseaux virtuels servent également de limite d’isolement par défaut entre les ressources de la plate-forme.
- [Meilleures pratiques Azure pour la sécurité réseau](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices). suggestions de l’équipe Azure Security sur la façon de configurer vos réseaux virtuels pour minimiser les vulnérabilités de sécurité.

## <a name="next-steps"></a>Étapes suivantes

Le réseau à définition logicielle n’est qu’un des composants de l’infrastructure centrale nécessitant des décisions architecturales lors d’un processus d’adoption cloud. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
