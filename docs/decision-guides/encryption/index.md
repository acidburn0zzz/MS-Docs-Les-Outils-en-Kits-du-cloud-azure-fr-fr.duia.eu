---
title: Guide de décision concernant le chiffrement
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment utiliser le chiffrement comme un service principal lors des migrations vers Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 27a86947bdcf240f3ea469db10c94b3f63ccb1e8
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564891"
---
# <a name="encryption-decision-guide"></a>Guide de décision concernant le chiffrement

Le chiffrement des données permet de les protéger de tout accès non autorisé. Une stratégie de chiffrement correctement implémentée fournit des couches de sécurité supplémentaires pour vos charges de travail basées sur le cloud, et les protège des pirates et autres utilisateurs non autorisés, aussi bien externes qu’internes à votre organisation et à vos réseaux.

Passer à : [Gestion des clés](#key-management) | [Chiffrement des données](#data-encryption) | [En savoir plus](#learn-more)

La stratégie de chiffrement cloud se concentre sur la stratégie d’entreprise et sur les exigences de conformité. Le chiffrement des ressources est souhaitable. D’ailleurs, dans de nombreux services Azure, tels que le stockage Azure et Azure SQL Database, le chiffrement est activé par défaut. Toutefois, le chiffrement entraîne une augmentation de la latence et de l’utilisation globale des ressources.

Pour les charges de travail exigeantes, il est essentiel de trouver le bon équilibre entre performances et chiffrement, ainsi que de déterminer comment chiffrer les données et le trafic. Le coût et la complexité des mécanismes de chiffrement peuvent varier. En outre, les exigences techniques et stratégiques peuvent influencer vos décisions concernant la façon dont le chiffrement est appliqué et la façon dont les clés et les secrets critiques sont stockés et gérés.

Lorsque vous planifiez une stratégie de chiffrement, la stratégie d’entreprise et les exigences de conformité tierces constituent les principaux éléments à prendre en compte. Azure propose plusieurs mécanismes standards capables de répondre aux exigences courantes concernant le chiffrement des données qui sont au repos ou en transit. Toutefois, pour les stratégies et les exigences de conformité qui demandent un contrôle plus strict, telles que la gestion standardisée des clés et des secrets, le chiffrement des données en cours d’utilisation ou le chiffrement de certaines données, vous devrez probablement implémenter une stratégie de chiffrement plus sophistiquée afin de répondre à ces exigences.

## <a name="key-management"></a>Gestion des clés

Le chiffrement des données dans le cloud nécessite un stockage, une gestion et une utilisation sécurisés des clés de chiffrement. Un système de gestion des clés est essentiel pour que votre organisation puisse créer, stocker et gérer les clés de chiffrement, ainsi que les chaînes de connexion et les mots de passe importants, et autres informations confidentielles de type informatique.

Les systèmes modernes de gestion des clés comme Azure Key Vault prennent en charge le stockage et la gestion des clés protégées par logiciel à des fins de tests et de développement, ainsi que des clés protégées par module de sécurité matériel, pour une protection maximale des charges de travail de production ou des données sensibles.

Si vous planifiez une migration vers le cloud, le tableau suivant peut vous aider à choisir comment stocker et gérer les clés de chiffrement, les certificats et les secrets qui sont critiques pour la création de déploiements cloud sécurisés et faciles à gérer :

| Question | Cloud natif | Bring Your Own Key (BYOK) | Hold Your Own Key |
|---------------------------------------------------------------------------------------------------------------------------------------|--------------|--------|-------------|
| Manque-t-il un système centralisé de gestion des secrets et des clés à votre organisation ?                                                                    | OUI          | Non     | Non          |
| Devrez-vous restreindre la création de clés et de secrets sur les appareils locaux lors de l’utilisation de ces clés dans le cloud ? | Non           | OUI    | Non          |
| Votre organisation a-t-elle mis en place des règles ou des stratégies qui empêchent le stockage hors site des clés ?                | Non           | Non     | OUI         |

### <a name="cloud-native"></a>Cloud natif

Avec la gestion native des clés dans le cloud, l’ensemble des clés et des secrets sont générés, gérés et stockés dans un coffre du cloud, tel qu’Azure Key Vault. Cette approche simplifie de nombreuses tâches informatiques liées à la gestion des clés, comme la sauvegarde, le stockage ou le renouvellement des clés.

L’utilisation d’un système natif de gestion des clés dans le cloud suppose que :

- Vous faites confiance à la solution cloud de gestion des clés pour créer, gérer et héberger les secrets et les clés de votre organisation.
- Vous avez activé l’ensemble des applications et des services locaux qui ont besoin des services de chiffrement ou des secrets pour accéder au système de gestion des clés dans le cloud.

### <a name="bring-your-own-key"></a>Bring Your Own Key (BYOK)

Avec une approche de type Bring Your Own Key, vous générez des clés sur du matériel HSM dédié au sein de votre environnement local, puis vous transférez ces clés de manière sécurisée vers un système de gestion basé sur le cloud tel qu’Azure Key Vault en vue de les utiliser avec vos ressources hébergées dans le cloud.

**Conditions nécessaires à l’approche Bring Your Own Key :** La génération de clés locales et leur utilisation avec un système de gestion des clés basé sur le cloud supposent que :

- Vous faites confiance à l’infrastructure sous-jacente de sécurité et de contrôle d’accès de la plateforme cloud pour héberger et utiliser vos clés et vos secrets.
- Vos applications et vos services hébergés dans le cloud peuvent accéder aux clés et aux secrets, et les utiliser de manière fiable et sécurisée.
- Vous êtes obligé, par une stratégie réglementaire ou organisationnelle, de créer et de gérer les secrets et les clés de votre organisation localement.

### <a name="on-premises-hold-your-own-key"></a>Locale (Hold Your Own Key, HYOK)

Dans certains scénarios, une stratégie réglementaire ou des raisons techniques peuvent vous empêcher de stocker les clés dans un système de gestion des clés basé sur le cloud. Dans ce cas, vous devez générer des clés sur du matériel local, les stocker et les gérer à l’aide d’un système de gestion des clés local, et provisionner un mécanisme pour permettre aux ressources cloud d’accéder à ces clés à des fins de chiffrement. Notez que l’approche HYOK (Hold Your Own Key) peut ne pas être compatible avec tous les services Azure.

**Conditions nécessaires à la gestion locale des clés :** L’utilisation d’un système local de gestion des clés dans le cloud suppose que :

- Vous êtes obligé, par une stratégie réglementaire ou organisationnelle, de créer, de gérer et d’héberger les secrets et les clés de votre organisation localement.
- L’ensemble des applications et des services locaux qui ont besoin des services de chiffrement ou des secrets sont en mesure d’accéder au système local de gestion des clés.

## <a name="data-encryption"></a>Chiffrement des données

Lorsque vous planifiez votre stratégie de chiffrement, prenez en compte plusieurs états de données différents avec des besoins de chiffrement différents :

| État des données | Données |
|-----|-----|
| Données en transit | Trafic réseau interne, connexions Internet, connexions entre centres de données ou réseaux virtuels |
| Données au repos    | Bases de données, fichiers, disques virtuels, stockage PaaS |
| Données en cours d’utilisation     | Données chargées dans la mémoire RAM ou dans les caches processeur |

### <a name="data-in-transit"></a>Données en transit

Les données en transit sont des données qui sont déplacées d’une ressource interne à une autre, d’un centre de données à un autre, vers des réseaux externes ou sur Internet.

Le chiffrement des données en transit est généralement obtenu en exigeant les protocoles SSL/TLS pour le trafic. Le trafic qui transite entre vos ressources hébergées dans le cloud et un réseau externe ou l’Internet public doit toujours être chiffré. Par défaut, les ressources PaaS appliquent également un chiffrement SSL/TLS pour le trafic. Il revient à l’équipe chargée de l’adoption du cloud ainsi qu’au propriétaire de la charge de travail d’appliquer ou non le chiffrement du trafic entre les ressources IaaS hébergées sur vos réseaux virtuels. Un tel chiffrement est généralement recommandé.

**Conditions nécessaires au chiffrement des données en transit** : L’implémentation correcte des stratégies de chiffrement des données en transit suppose que :

- Tous les points de terminaison accessibles publiquement dans votre environnement cloud communiquent avec l’Internet public via les protocoles SSL/TLS.
- Vous utilisez des protocoles VPN chiffrés lorsque vous connectez des réseaux cloud à un réseau local ou autre réseau externe via l’Internet public.
- Vous utilisez un VPN ou une autre appliance de chiffrement locale associée au VPN virtuel correspondant ou à une appliance de chiffrement déployée sur votre réseau cloud, lorsque vous connectez des réseaux cloud à des réseaux locaux ou autres réseaux externes à l’aide d’une connexion WAN dédiée, telle qu’une connexion ExpressRoute.
- Vous chiffrez tout le trafic entre les ressources de votre réseau virtuel si vous disposez de données sensibles qui ne doivent pas être incluses dans les journaux d’activité de trafic ou autres rapports de diagnostics que le personnel informatique peut consulter.

### <a name="data-at-rest"></a>Données au repos

Les données au repos correspondent aux données qui ne sont ni déplacées ni traitées, y compris des fichiers, des bases de données, des disques de machine virtuelle, des comptes de stockage PaaS ou autres ressources similaires. Le chiffrement des données stockées protège les appareils virtuels contre tout accès non autorisé provenant d’une intrusion réseau externe, d’utilisateurs internes non autorisés ou de publications accidentelles.

Les ressources de stockage PaaS et de base de données appliquent généralement le chiffrement par défaut. Les ressources IaaS peuvent être sécurisées en chiffrant les données au niveau du disque virtuel ou en chiffrant l’intégralité du compte de stockage qui héberge vos disques virtuels. Toutes ces ressources peuvent utiliser des clés qui sont gérées par Microsoft ou par le client et stockées dans Azure Key Vault.

Le chiffrement des données au repos englobe également des techniques plus avancées de chiffrement des bases de données, comme le chiffrement au niveau des colonnes et des lignes, qui permet de contrôler plus précisément les données à sécuriser.

Ce sont vos exigences globales concernant les stratégies et la conformité, la sensibilité des données stockées ainsi que les exigences de performances de vos charges de travail qui déterminent quelles ressources doivent être chiffrées.

### <a name="assumptions-about-encrypting-data-at-rest"></a>Hypothèses relatives au chiffrement des données au repos

Le chiffrement des données au repos suppose que :

- Vous stockez des données qui ne sont pas destinées à une utilisation publique.
- Vos charges de travail peuvent accepter la latence supplémentaire liée au chiffrement du disque.

### <a name="data-in-use"></a>Données en cours d’utilisation

Le chiffrement des données en cours d’utilisation implique la sécurisation des données dans un stockage non permanent, comme le cache RAM ou le cache processeur. Il implique également l’utilisation de technologies telles que le chiffrement de l’intégralité de la mémoire, et de technologies d’enclave, telles qu’Intel Secure Guard Extensions (SGX). Cela comprend également des techniques de chiffrement, telles que le chiffrement homomorphe, qui peut être utilisé pour créer des environnements d’exécution sécurisés et approuvés.

**Conditions nécessaires au chiffrement des données en cours d’utilisation** : Le chiffrement des données en cours d’utilisation suppose que :

- Vous êtes obligé de séparer la propriété des données de la plateforme cloud sous-jacente de façon permanente, même au niveau de la RAM et du processeur.

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations sur le chiffrement et la gestion des clés dans Azure, consultez :

- [Vue d’ensemble du chiffrement Azure](https://docs.microsoft.com/azure/security/security-azure-encryption-overview). Description détaillée de la façon dont Azure utilise le chiffrement pour sécuriser les données au repos et les données en transit.
- [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-overview). Key Vault est le principal système de gestion des clés qui permet de stocker et de gérer des clés de chiffrement, des secrets et des certificats dans Azure.
- [Bonnes pratiques relatives au chiffrement et à la sécurité des données dans Azure](https://docs.microsoft.com/azure/security/azure-security-data-encryption-best-practices). Rubrique concernant les bonnes pratiques relatives au chiffrement et à la sécurité des données dans Azure.
- [Informatique confidentielle dans Azure](https://azure.microsoft.com/solutions/confidential-compute). L’informatique confidentielle d’Azure fournit des outils et des technologies pour créer des environnements d’exécution approuvés ou d’autres mécanismes de chiffrement permettant de sécuriser les données en cours d’utilisation.

## <a name="next-steps"></a>Étapes suivantes

Lors d’un processus d’adoption cloud, le chiffrement ne représente qu’une partie des composants d’infrastructure qui nécessitent des décisions architecturales. Consultez la [vue d’ensemble sur les guides de décision](../index.md) pour en savoir plus sur les autres schémas et modèles utilisés lors des décisions de conception pour d’autres types d’infrastructure.

> [!div class="nextstepaction"]
> [Guides de décision concernant l’architecture](../index.md)
