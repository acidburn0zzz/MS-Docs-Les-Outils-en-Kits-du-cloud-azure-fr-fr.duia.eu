---
title: Migration cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Contenu d’introduction à la migration cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 1bf9497684c1043d23eec48b1ab5d5f1f12ef752
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70837999"
---
# <a name="cloud-migration-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Migration cloud dans le Framework d’adoption du cloud Microsoft pour Azure

La migration cloud est le processus de déplacement de ressources numériques existantes vers une plateforme cloud. Avec cette approche, les ressources existantes sont répliquées vers le cloud avec des modifications minimales. Une fois qu’une application ou une charge de travail devient opérationnelle dans le cloud, les utilisateurs sont transférés de la solution existante vers la solution cloud. La migration cloud est un moyen d’équilibrer efficacement un portefeuille cloud. Cette approche est souvent la plus agile et la plus rapide à court terme. À l’inverse, certains avantages du cloud peuvent ne pas être effectifs avec cette approche tant que d’autres modifications ne sont pas apportées. Les grandes entreprises et les PME utilisent cette approche pour accélérer le rythme du changement, éviter les dépenses d’investissement planifiées et réduire les coûts d’exploitation courants.

## <a name="cloud-migration-guidance"></a>Guide de migration cloud

Les instructions de cette section du Framework d’adoption du cloud visent deux objectifs :

- Proposer des guides de migration immédiatement actionnables qui illustrent des expériences communes rencontrées par les clients. Chaque guide encapsule le processus et les outils nécessaires à la réussite d’un effort de migration vers le cloud. Par définition, les conseils de conception sont propres à Azure. Toutes les autres recommandations figurant dans ces guides peuvent être appliquées dans le cadre d’une approche indépendante du cloud ou multicloud.
- Aider les lecteurs à créer des plans de migration personnalisés capables de satisfaire plusieurs des besoins de l’entreprise, notamment la migration de plusieurs clouds publics grâce à des instructions détaillées sur le développement de processus, rôles et responsabilités, et des contrôles de gestion des changements.

Ce contenu s’adresse à l’équipe d’adoption cloud. Il peut également servir aux architectes du cloud qui cherchent à développer des fondements solides pour la migration vers le cloud.

## <a name="intended-audience"></a>Public concerné

Le guide du Framework d’adoption du cloud touche l’activité, la technologie et la culture des entreprises. Cette section a un impact significatif sur les propriétaires d’applications, le personnel de gestion des changements (comme le bureau de gestion des projets et le personnel de gestion agile) et les dirigeants des départements financiers et métier, ainsi que l’équipe d’adoption cloud. Plusieurs dépendances sont à noter entre ces acteurs et nécessitent une approche facilitante de la part des architectes du cloud qui font usage de ce guide. Il se peut que la facilitation entre les équipes découle d’une action ponctuelle, mais dans certains cas, elle requiert des interactions récurrentes entre les acteurs.

L’architecte du cloud joue le rôle de facilitateur et de leader d’opinion pour rassembler tous ces publics. Le contenu figurant dans cette collection de guides est conçu pour aider l’architecte cloud à adapter les discussions en fonction des publics et ainsi prendre les décisions nécessaires. La transformation métier rendue possible par le cloud dépend des conseils donnés par le rôle Architecte cloud aux équipes métier et informatiques.

**Spécialisation Architecte du cloud dans cette section :** Chaque section du Framework d’adoption du cloud représente une spécialisation ou une variante différente du rôle de l’architecte cloud. Cette section est destinée aux architectes cloud avec une expertise sur l’environnement local existant et la manière dont cela affecte les options de migration.

**Séparation des tâches :** Dans de nombreuses entreprises, la séparation des tâches existe pour limiter l’accès aux systèmes de production ou aux segments de l’environnement de l’entreprise. Dans ce cas, le processus de migration devient plus complexe. Dans certains cas, ces rôles et responsabilités peuvent nécessiter plusieurs architectes cloud pour couvrir l’ensemble du processus de migration.

**Options de partenariat** Sur chacun de ces processus, les équipes apprennent de nouvelles compétences et approches en matière d’exécution technique. Le développement des compétences techniques entre les membres de l’équipe existante est une option lors de l’exécution. Embauche de personnel supplémentaire. Un partenariat avec des tiers peut souvent fournir une accélération et des réductions des risques significatives. Les [options de partenariat](./migration-considerations/assess/partnership-options.md) peuvent vous aider à prendre des décisions pour choisir l’option de partenariat la plus appropriée.

## <a name="next-steps"></a>Étapes suivantes

Pour les lecteurs qui souhaitent suivre ce guide du début à la fin, ce contenu les aidera à développer une stratégie de migration vers le cloud fiable. Les différentes instructions guident le lecteur à travers la théorie et la mise en pratique de cette stratégie.

Dans un premier temps, il est recommandé aux lecteurs d’étudier le [guide de migration Azure](./azure-migration-guide/index.md) pour comprendre l’ensemble standard d’outils et d’approches nécessaires à la migration dans un cas d’usage courant. Par la suite, les recommandations de base peuvent être étendues pour répondre aux besoins des lecteurs grâce aux [scénarios de migration complexes](./expanded-scope/index.md), aux [pratiques recommandées pour la migration](./azure-best-practices/index.md) et aux [considérations relatives à la migration](./migration-considerations/index.md).

> [!div class="nextstepaction"]
> [Guide de migration Azure](./azure-migration-guide/index.md)
