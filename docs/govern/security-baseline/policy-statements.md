---
title: Exemples d’instructions de stratégie de base de référence de la sécurité
description: Aidez-vous de ces exemples de déclarations de stratégie de base de référence de la sécurité pour élaborer des déclarations de stratégie qui répondent aux besoins de votre organisation.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: e3f2a6156d282e2db6fb8a7206251447f9e48f71
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219799"
---
# <a name="security-baseline-sample-policy-statements"></a>Exemples d’instructions de stratégie de base de référence de la sécurité

Les instructions de stratégie cloud individuelles sont des recommandations destinées à traiter des risques spécifiques identifiés lors de votre processus d’évaluation des risques. Ces instructions doivent fournir un bref récapitulatif des risques, ainsi que des plans établis pour les gérer. Chaque définition d’instruction doit inclure les informations suivantes :

- **Risque technique :** un récapitulatif du risque que cette stratégie gérera.
- **Instruction de stratégie :** Une explication succincte claire des exigences de la stratégie.
- **Options techniques :** Recommandations exploitables, spécifications ou autres conseils que des équipes informatiques et des développeurs peuvent utiliser lors de l’implémentation de la stratégie.

Les exemples d’énoncés de stratégie suivants traitent des risques courants liés à la sécurité. Ces énoncés sont des exemples que vous pouvez référencer lorsque vous rédigez des énoncés de stratégie pour répondre aux besoins de votre organisation. Ces exemples ne sont pas destinés à être normatifs, et il existe potentiellement plusieurs options de stratégie pour gérer chaque risque identifié. Travaillez en étroite collaboration avec les équipes métier, les équipes informatiques et de sécurité pour identifier les meilleures stratégies pour vos propres risques.

## <a name="asset-classification"></a>Classification des ressources

**Risque technique :** Les ressources qui ne sont pas correctement identifiées comme critiques ou qui impliquent des données sensibles peuvent ne pas se voir accorder une protection suffisante, ce qui conduit à des fuites de données ou des interruptions potentielles de l’activité.

**Instruction de stratégie :** Toutes les ressources déployées doivent être classées par criticité et par classification des données. Les classifications doivent être examinées par l’équipe de gouvernance cloud et le propriétaire de l’application avant le déploiement dans le cloud.

**Option de conception potentielle :** Établissez des [normes de balisage des ressources](../../decision-guides/resource-tagging/index.md) et vérifiez que le service informatique les applique systématiquement à toutes les ressources déployées à l’aide de [balises de ressources Azure](https://docs.microsoft.com/azure/azure-resource-manager/management/tag-resources).

## <a name="data-encryption"></a>Chiffrement des données

**Risque technique :** Il existe un risque d’exposition de données protégées pendant le stockage.

**Instruction de stratégie :** Toutes les données protégées doivent être chiffrées au repos.

**Option de conception potentielle :** Consultez l’article [Vue d’ensemble du chiffrement Azure](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview) pour voir comment le chiffrement des données au repos est effectué sur la plateforme Azure. Il convient également de prendre en considération d’autres contrôles comme ceux liés au chiffrement des données de compte et le contrôle sur le mode de modification des paramètres des comptes de stockage.

## <a name="network-isolation"></a>Isolement réseau

**Risque technique :** La connectivité entre des réseaux et des sous-réseaux de réseaux introduit des vulnérabilités potentielles qui peuvent entraîner des fuites de données ou une interruption de services critiques.

**Instruction de stratégie :** Les sous-réseaux de réseau qui contiennent des données protégées doivent être isolés de tous les autres sous-réseaux. Le trafic réseau entre des sous-réseaux de données protégées doit être audité régulièrement.

**Option de conception potentielle :** Dans Azure, l’isolement réseau et de sous-réseau est géré par le biais du [Réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="secure-external-access"></a>Sécuriser l’accès externe

**Risque technique :** Autoriser l’accès à des charges de travail à partir de l’Internet public introduit un risque d’intrusion entraînant une exposition non autorisée des données ou une interruption de l’activité.

**Instruction de stratégie :** Aucun sous-réseau contenant des données protégées ne doit pas être accessible directement par l’Internet public ou dans les centres de données. L’accès à ces sous-réseaux doit être routé via des sous-réseaux intermédiaires. Tous les accès à ces sous-réseaux doivent transiter par une solution de pare-feu capable d’effectuer des analyses des paquets et de bloquer des fonctions.

**Option de conception potentielle :** Dans Azure, sécurisez les points de terminaison publics en déployant une [zone DMZ entre l’Internet public et votre réseau basé sur le cloud](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz?toc=/azure/cloud-adoption-framework/toc.json&bc=/azure/cloud-adoption-framework/_bread/toc.json). Envisagez le déploiement, la configuration et l’automatisation du [pare-feu Azure](https://docs.microsoft.com/azure/firewall/overview).

## <a name="ddos-protection"></a>Protection DDoS

**Risque technique :** Les attaques par déni de service distribué (DDoS) peuvent entraîner une interruption de l’activité.

**Instruction de stratégie :** Déployez des mécanismes d’atténuation DDoS automatisés pour tous les points de terminaison réseau accessibles publiquement. Aucun site web public s’appuyant sur une IaaS ne doit être exposé sur Internet sans DDoS.

**Option de conception potentielle :** Utilisez [Azure DDoS Protection](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) Standard pour limiter les perturbations provoquées par les attaques DDoS.

## <a name="secure-on-premises-connectivity"></a>Sécuriser la connectivité locale

**Risque technique :** Le trafic non chiffré entre votre réseau cloud et local sur l’Internet public est vulnérable aux interceptions, ce qui introduit un risque d’exposition des données.

**Instruction de stratégie :** Toutes les connexions entre les réseaux locaux et cloud doivent s’effectuer via une connexion VPN chiffrée sécurisée ou une liaison WAN privée dédiée.

**Option de conception potentielle :** Dans Azure, utilisez un réseau VPN ExpressRoute ou Azure pour établir des connexions privées entre vos réseaux locaux et cloud.

## <a name="network-monitoring-and-enforcement"></a>Supervision et mise en œuvre du réseau

**Risque technique :** Les changements apportés à la configuration du réseau peuvent entraîner de nouvelles vulnérabilités et de nouveaux risques d’exposition des données.

**Instruction de stratégie :** Les outils de gouvernance doivent auditer et appliquer les exigences de configuration réseau définies par l’équipe de base de référence de la sécurité.

**Option de conception potentielle :** Dans Azure, l’activité réseau peut être supervisée à l’aide d’[Azure Network Watcher](https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview), tandis qu’[Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-network-recommendations) peut permettre d’identifier les failles de sécurité. Azure Policy vous permet de restreindre les ressources réseau et la stratégie de configuration des ressources en fonction des limites définies par l’équipe de sécurité.

## <a name="security-review"></a>Révision de sécurité

**Risque technique :** Au fil du temps, de nouvelles menaces de sécurité et de nouveaux types d’attaques émergent, augmentant le risque d’exposition ou d’interruption de vos ressources cloud.

**Instruction de stratégie :** Les tendances et les attaques potentielles susceptibles d’affecter les déploiements cloud doivent être régulièrement examinées par l’équipe de sécurité pour fournir des mises à jour aux outils de base de référence de sécurité utilisés dans le cloud.

**Option de conception potentielle :** Établissez une réunion de révision de sécurité régulière qui inclut les membres de l’équipe informatique et de gouvernance concernés. Passez en revue les données et métriques de sécurité existantes pour déterminer les lacunes des outils de stratégie et de base de référence de sécurité actuels, ainsi que pour mettre à jour la stratégie afin de corriger tous les nouveaux risques. Utilisez [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) et [Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-intro) pour obtenir des insights exploitables sur les menaces émergentes spécifiques à vos déploiements.

## <a name="next-steps"></a>Étapes suivantes

Utilisez les exemples mentionnés dans cet article comme point de départ pour développer des stratégies qui gèrent des risques de sécurité spécifiques, dans la continuité de vos plans d’adoption du cloud.

Pour commencer à développer vos propres instructions de stratégie personnalisées liées à la base de référence de la sécurité, téléchargez le [modèle de discipline de base de référence de la sécurité](./template.md).

Pour accélérer l’adoption de cette discipline, choisissez le [guide de gouvernance actionnable](../guides/index.md) correspondant le mieux à votre environnement. Modifiez ensuite la conception pour intégrer vos décisions spécifiques en matière de stratégie d’entreprise.

Sur la base des risques et de la tolérance, établissez un processus de gouvernance et de communication en lien avec l’adhésion à la stratégie Base de référence de sécurité.

> [!div class="nextstepaction"]
> [Établir des processus de conformité à la stratégie](./compliance-processes.md)
