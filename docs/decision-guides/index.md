---
title: Guides de décision en matière d'architecture
description: Utilisez ces modèles de composants d’infrastructure de déploiement cloud de base pour prendre en charge vos scénarios de déploiement cloud spécifiques.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 9552ba8b168e79f247916ae86f8e7721282baddb
ms.sourcegitcommit: 388e32dd4861039149c846c926c0e9230cf28ae3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79140233"
---
# <a name="architectural-decision-guides"></a>Guides de décision en matière d'architecture

Les guides de décision en matière d’architecture du framework d'adoption du cloud décrivent les modèles qui permettent de formuler des recommandations de conception de gouvernance cloud. Chaque guide de décision se concentre sur un composant d’infrastructure des déploiements cloud et liste les schémas et modèles pouvant prendre en charge des scénarios de déploiement cloud spécifiques.

Lorsque vous commencez à établir la gouvernance cloud de votre organisation, des parcours de gouvernance actionnables fournissent une feuille de route de référence. Cela étant, ces parcours reposent sur des hypothèses en termes d’exigences et de priorités, qui ne reflètent pas systématiquement celles de votre organisation.

Ces guides de décision complètent les exemples de parcours de gouvernance en proposant d'autres modèles pour vous permettre d'aligner les choix de conception architecturale faits dans les exemples de recommandations de conception avec vos propres exigences.

## <a name="decision-guidance-categories"></a>Catégories de recommandations de décision

Chacune des catégories suivantes représente une technologie de base de tout déploiement dans le cloud. Les exemples de parcours de gouvernance prennent des décisions de conception liées à ces technologies, en fonction des besoins des entreprises exemples, et certaines de ces décisions peuvent ne pas correspondre aux propres besoins de votre organisation. Les sections suivantes traitent des options alternatives pour chacune de ces catégories, ce qui vous permet de choisir un schéma ou un modèle plus adapté à vos besoins.

[Abonnements](./subscriptions/index.md) : Planifiez la conception d'abonnement et la structure de compte de votre déploiement dans le cloud pour répondre aux fonctionnalités de votre organisation en termes de propriété, de facturation et de gestion.

[Identité](./identity/index.md) : Intégrez des services d’identité basés sur le cloud à vos ressources d’identité existantes pour prendre en charge les autorisations et le contrôle d’accès au sein de votre environnement informatique.

[Application de stratégies](./policy-enforcement/index.md) : Définissez et appliquez des règles de stratégie d’entreprise pour les ressources et charges de travail déployées dans le cloud qui s’alignent sur vos besoins de gouvernance.

[Cohérence des ressources](./resource-consistency/index.md) : Vérifiez que le déploiement et l'organisation de vos ressources cloud s'alignent en termes de gestion des ressources et d'exigences de stratégie.

[Identification des ressources](./resource-tagging/index.md) : Organisez vos ressources cloud de manière à ce qu’elles prennent en charge les modèles de facturation, les approches en matière de comptabilité cloud, le management, et qu’elles optimisent l’utilisation des ressources et les coûts. L'identification des ressources requiert un schéma d'attribution de noms et de métadonnées cohérent et bien organisé.

[SDN (Software Defined Network)](./software-defined-network/index.md) : Déployez des charges de travail sécurisées dans le cloud moyennant le déploiement rapide et la modification des fonctionnalités de mise en réseau virtualisées. Les réseaux à définition logicielle peuvent prendre en charge des workflows agiles, isoler des ressources et intégrer des systèmes basés sur le cloud à votre infrastructure informatique existante.

[Chiffrement](./encryption/index.md) : Sécurisez vos données sensibles à l’aide du chiffrement pour se conformer aux exigences de stratégie de sécurité et de conformité de votre entreprise.

[Journalisation et création de rapports](./logging-and-reporting/index.md) : Surveillez les données de journal générées par les ressources cloud. L’analyse des données vous renseigne sur l’intégrité des opérations, de la maintenance et du statut de conformité des charges de travail.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment les abonnements et les comptes servent de base à un déploiement dans le cloud.

> [!div class="nextstepaction"]
> [Conception des abonnements](./subscriptions/index.md)
