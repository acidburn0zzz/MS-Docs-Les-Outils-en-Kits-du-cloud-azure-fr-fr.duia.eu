---
title: Guide de préparation de la sécurité cloud CISO
description: Découvrez comment préparer le responsable de la sécurité des systèmes d’information (CISO) à la transformation du cloud et à la gouvernance incrémentielle.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: dc82f4d8ad21bcbb9d36b00fbdad1f91d6d4ec2c
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80356942"
---
<!-- cSpell:ignore CISO -->

# <a name="ciso-cloud-readiness-guide"></a>Guide de préparation au cloud pour un Chef de la sécurité des systèmes d’information

Recommandations de Microsoft comme le fait que le Framework d’adoption du cloud n’est pas en mesure de déterminer ou de guider les contraintes de sécurité uniques des milliers d’entreprises prises en charge par cette documentation. Lors de la migration vers le cloud, le rôle du Responsable de la sécurité des systèmes d’information ou du Bureau de la sécurité des systèmes d’information (CISO) n’est pas supplanté par les technologies cloud. Bien au contraire, le Chef de la sécurité des systèmes d’information (CISO) et le bureau du CISO s’enracinent et s’intègrent davantage. Ce guide part du principe que le lecteur est familiarisé avec les processus CISO et qu’il cherche à moderniser ces processus pour permettre la transformation cloud.

L’adoption du cloud active des services qui n’étaient pas souvent considérés dans les environnements informatiques traditionnels. Les déploiements en libre-service ou automatisés sont couramment exécutés par des équipes de développement d’applications ou d’autres équipes informatiques qui ne sont généralement pas en phase avec le déploiement de production. Dans certaines organisations, les composantes métier disposent également de fonctionnalités libre-service. Cela peut entraîner de nouvelles exigences de sécurité qui n’étaient pas nécessaires dans le monde local. La sécurité centralisée est plus difficile. La sécurité devient souvent une responsabilité partagée entre la culture d’entreprise et la culture informatique. Cet article peut aider un Chef de la sécurité des systèmes d’information (CISO) à se préparer à cette approche et à s’engager dans la gouvernance incrémentielle.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-a-ciso-prepare-for-the-cloud"></a>Comment un chef de la sécurité des systèmes d’information peut se préparer au cloud ?

Comme la plupart des stratégies, les stratégies de sécurité et de gouvernance dans une organisation ont tendance à se développer naturellement. Quand des incidents de sécurité se produisent, une stratégie est créée afin d’informer les utilisateurs et de réduire la probabilité d’incidents qui se répètent. Bien que naturelle, cette approche crée un encombrement des stratégies et des dépendances techniques. Les parcours de transformation cloud créent une opportunité unique de moderniser et de réinitialiser des stratégies. Lors de la préparation d’un parcours de transformation, le CISO peut créer une valeur immédiate et mesurable en agissant comme partie prenante principale dans une [révision de stratégie](./cloud-policy-review.md).

Dans une révision de ce type, le rôle du CISO est de créer un équilibre sécurisé entre les contraintes de la stratégie/conformité existantes et la posture de sécurité améliorée des fournisseurs de cloud. Cette progression peut être mesurée de différentes façons. Elle est souvent mesurée en nombre de stratégies de sécurité qui peuvent être déchargées de manière sécurisée vers le fournisseur de cloud.

**Transfert des risques de sécurité :** Comme les services sont déplacés vers des modèles d’hébergement IaaS (Infrastructure as a Service), l’entreprise supporte un risque moins direct concernant le provisionnement matériel. Le risque n’est pas supprimé. Au lieu de cela, il est transféré au fournisseur cloud. Si l’approche d’un fournisseur cloud pour le provisionnement matériel fournit le même niveau d’atténuation des risques, dans un processus renouvelable sécurisé, le risque de l’exécution du provisionnement matériel est supprimé du domaine de responsabilité de l’équipe informatique de l’entreprise et transféré au fournisseur de cloud. Cela réduit le risque de sécurité global que l’équipe informatique d’une entreprise est chargée de gérer, même si le risque proprement dit soit toujours être suivi et vérifié régulièrement.

À mesure que les solutions continuent à « remonter la pile » pour incorporer des modèles PaaS (Platform as a Service) ou SaaS (Software as a Service), des risques supplémentaires peuvent être évités ou transférés. Quand le risque est déplacé de manière sécurisée vers un fournisseur cloud, le coût de l’exécution, de la supervision et de l’application de stratégies de sécurité ou d’autres stratégies de conformité peut également être réduit de manière sécurisée.

**Esprit de croissance :** Le changement peut être effrayant aussi bien pour l’entreprise que pour les implémenteurs techniques. Quand le CISO mène un changement d’esprit de croissance dans une organisation, nous avons constaté que ces craintes naturelles sont remplacées par un intérêt accru pour la sécurité et la conformité aux stratégies. Approcher une [révision de stratégie](./cloud-policy-review.md), un parcours de transformation ou des révisions d’implémentations simples avec un esprit de croissance permet à l’équipe de migrer rapidement, mais pas au prix d’un profil de risque équitable et gérable.

## <a name="resources-for-the-chief-information-security-officer"></a>Ressources pour le Chef de la sécurité des systèmes d’information

Une connaissance du cloud est essentielle pour approcher une [révision de stratégie](./cloud-policy-review.md) avec un esprit de croissance. Les ressources suivantes peuvent aider le CISO à mieux comprendre la posture de sécurité de la plateforme Azure de Microsoft.

Ressources de la plateforme de sécurité :

- [Cycle de vie de développement de sécurité, audits internes](https://www.microsoft.com/sdl)
- [Formation obligatoire sur les mesures de sécurité, vérifications de la formation](https://downloads.cloudsecurityalliance.org/star/self-assessment/StandardResponsetoRequestforInformationWindowsAzureSecurityPrivacy.docx)
- [Test de pénétration, détection d’intrusion, DDoS, audits et journalisation](https://www.microsoft.com/trustcenter/Security/AuditingAndLogging)
- [Centre de données ultramoderne](https://www.microsoft.com/cloud-platform/global-datacenters), sécurité physique, [réseau sécurisé](https://docs.microsoft.com/azure/security/security-network-overview)
- [Réponse de Microsoft Azure aux problèmes de sécurité dans le cloud (PDF)](https://aka.ms/SecurityResponsePaper)

Confidentialité et contrôles :

- [Gérer vos données tout le temps](https://www.microsoft.com/trustcenter/Privacy/You-own-your-data)
- [Contrôler l’emplacement des données](https://www.microsoft.com/trustcenter/Privacy/Where-your-data-is-located)
- [Fournir l’accès aux données selon vos conditions](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Réponse à l’application de la législation](https://www.microsoft.com/trustcenter/Privacy/Responding-to-govt-agency-requests-for-customer-data)
- [Normes de confidentialité strictes](https://www.microsoft.com/TrustCenter/Privacy/We-set-and-adhere-to-stringent-standards)

Conformité :

- [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trustcenter/default.aspx)
- [Hub des contrôles communs](https://www.microsoft.com/trustcenter/Common-Controls-Hub)
- [Liste de points à vérifier en matière de services cloud](https://www.microsoft.com/trustcenter/Compliance/Due-Diligence-Checklist)
- [Conformité par service, emplacement et secteur](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

Transparence :

- [Comment Microsoft sécurise les données client dans les services Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Comment Microsoft gère l’emplacement des données dans les services Azure](https://azuredatacentermap.azurewebsites.net)
- [Qui dans Microsoft peut accéder à vos données dans quelles conditions](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Comment Microsoft sécurise les données client dans les services Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Passer en revue la certification des services Azure, hub de transparence](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

## <a name="next-steps"></a>Étapes suivantes

La première étape pour prendre des mesures dans toute stratégie de gouvernance est une [révision de stratégie](./cloud-policy-review.md). La rubrique relative à la [stratégie et à la conformité](./index.md) peut être un guide utile pendant votre révision de stratégie.

> [!div class="nextstepaction"]
> [Se préparer pour une révision de stratégie](./cloud-policy-review.md)
