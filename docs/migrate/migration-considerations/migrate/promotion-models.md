---
title: 'Modèles de promotion : single-step (étape unique), staged (étapes intermédiaires) ou flight (vol)'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Comprendre l’impact de la promotion sur les activités de migration
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 690c871ab18bef96a5a1738de90a216ca5b8df90
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564618"
---
# <a name="promotion-models-single-step-staged-or-flight"></a>Modèles de promotion : single-step (étape unique), staged (étapes intermédiaires) ou flight (vol)

La migration des charges de travail est souvent traitée comme une activité unique. En réalité, il s’agit d’une collection d’activités plus petites qui facilitent le déplacement d’une ressource numérique vers le cloud. L’une des dernières activités d’une migration est la promotion d’une ressource en production. La promotion est le moment où le système de production change pour les utilisateurs finaux. Il peut souvent être aussi simple que de modifier le routage réseau et de rediriger les utilisateurs finaux vers la nouvelle ressource de production. La promotion est également le moment où les opérations informatiques ou cloud changent l’objectif des processus de gestion opérationnelle du système de production précédent vers les nouveaux systèmes de production.

Il existe plusieurs modèles de promotion. Cet article décrit trois des modèles les plus courants utilisés dans les migrations cloud. Le choix d’un modèle de promotion modifie les activités observées dans les processus de migration et d’optimisation. Par conséquent, le modèle de promotion doit être décidé tôt dans une mise en production.

## <a name="impact-of-promotion-model-on-migrate-and-optimize-activities"></a>Impact du modèle de promotion sur la migration et l’optimisation des activités

Dans chacun des modèles de promotion suivants, l’outil de migration choisi réplique et prépare les ressources qui composent une charge de travail. Après la mise en lots, chaque modèle traite la ressource un peu différemment.

- **Promotion à étape unique.** Dans un modèle de promotion *à étape unique*, la mise en lots sert également de processus de promotion. Une fois toutes les ressources mises en lots, le trafic des utilisateurs finaux est redirigé et la mise en lots passe en production. Dans ce cas, la promotion fait partie du processus de migration. Il s’agit du modèle de migration le plus rapide. Toutefois, cette approche rend plus difficile l’intégration d’activités robustes de test ou d’optimisation. En outre, ce type de modèle suppose que l’équipe de migration a accès à l’environnement de mise en lots et de production, ce qui compromet les exigences de séparation des tâches dans certains environnements.
  > [!NOTE]
  >La table des matières de ce site répertorie l’activité de promotion dans le cadre du processus d’optimisation. Dans un modèle à étape unique, la promotion se produit pendant le processus de migration. Lors de l’utilisation de ce modèle, les rôles et les responsabilités doivent être mis à jour en conséquence.
- **Intermédiaire.** Dans un modèle de promotion *intermédiaire*, la charge de travail est considérée comme migrée après avoir la mise en lots, mais elle n’est pas encore promue. Avant la promotion, la charge de travail migrée subit une série de tests de performances, de tests métier et de modifications d’optimisation. Elle est ensuite promue à une date ultérieure conjointement à un plan de test d’entreprise. Cette approche améliore l’équilibre entre les coûts et le niveau de performance, tout en facilitant l’obtention de la validation d’activité.
- **En vol.** Le modèle de promotion *en vol* combine les modèles à étape unique et intermédiaire. Dans un modèle en vol, les ressources de la charge de travail sont traitées comme une production après le passage en mise en lots. Après une période condensée de tests automatisés, le trafic de production est acheminé vers la charge de travail. Toutefois, il s’agit d’un sous-ensemble du trafic. Ce trafic fait office de premier vol de production et de test. Partant du principe que la charge de travail s’effectue du point de vue du niveau de performance et des fonctionnalités, le trafic supplémentaire est migré. Une fois que tout le trafic de production a été déplacé vers les nouvelles ressources, la charge de travail est considérée comme entièrement promue.

Le modèle de promotion choisi a un impact sur la séquence des activités à effectuer. Cela influence également les rôles et responsabilités de l’équipe d’adoption du cloud. Cela peut même avoir un impact sur la composition d’un ou de plusieurs sprints.

## <a name="single-step-promotion"></a>Promotion à étape unique

Ce modèle utilise des outils d’automatisation de la migration pour répliquer, mettre en lots et promouvoir des ressources. Les ressources sont répliquées dans un environnement intermédiaire contenu et contrôlé par l’outil de migration. Une fois que toutes les ressources ont été répliquées, l’outil peut exécuter un processus automatisé pour promouvoir les ressources dans l’abonnement choisi en une seule étape. Dans l’environnement intermédiaire, l’outil continue de répliquer la ressource, ce qui réduit la perte de données entre les deux environnements. Après la promotion d’une ressource, la liaison entre le système source et le système répliqué est interrompue. Dans cette approche, si des modifications supplémentaires se produisent dans les systèmes sources initiaux, les modifications sont perdues.

**Avantages.** Les aspects positifs de cette approche sont les suivants :

- Ce modèle introduit une modification moins importante dans les systèmes cibles.
- Une réplication continue réduit la perte de données.
- Si une mise en lots échoue, elle peut rapidement être supprimée et répétée.
- La réplication et des tests de mise en lots répétés permettent un processus incrémentiel de script et de test.

**Inconvénients.** Les aspects négatifs de cette approche sont les suivants :

- Les ressources mises en lots dans le bac à sable isolé des outils ne permettent pas de tester des modèles complexes.
- Pendant la réplication, l’outil de migration consomme de la bande passante dans le centre de données local. La mise en lots d’un grand volume de ressources sur une longue période a un impact exponentiel sur la bande passante disponible, nuisant au processus de migration et perturbant potentiellement le niveau de performance des charges de travail de production dans l’environnement local.

## <a name="staged-promotion"></a>Promotion intermédiaire

Dans ce modèle, le bac à sable intermédiaire géré par l’outil de migration est utilisé à des fins de test limité. Les ressources répliquées sont ensuite déployées dans l’environnement cloud, qui sert d’environnement intermédiaire étendu. Les ressources migrées s’exécutent dans le cloud, tandis que les ressources supplémentaires sont répliquées, mises en lots et migrées. Lorsque des charges de travail complètes deviennent disponibles, des tests plus riches sont lancés. Lorsque toutes les ressources associées à un abonnement ont été migrées, l’abonnement et toutes les charges de travail hébergées sont promus en production. Dans ce scénario, aucune modification n’est apportée aux charges de travail au cours du processus de promotion. Au lieu de cela, les modifications tendent à se trouver au niveau des couches du réseau et des identités, acheminant les utilisateurs vers le nouvel environnement et révoquant l’accès de l’équipe d’adoption du cloud.

**Avantages.** Les aspects positifs de cette approche sont les suivants :

- Ce modèle fournit des possibilités de test d’entreprise plus précis.
- La charge de travail peut être étudiée de plus près pour optimiser le niveau de performance et le coût des ressources.
- Un grand nombre de ressources peuvent être répliquées dans des contraintes de temps et de bande passante similaires.

**Inconvénients.** Les aspects négatifs de cette approche sont les suivants :

- L’outil de migration choisi ne peut pas faciliter la réplication continue après la migration.
- Un moyen secondaire de réplication des données est nécessaire pour synchroniser les plateformes de données pendant le délai d’exécution intermédiaire.

## <a name="flight-promotion"></a>Promotion en vol

Ce modèle est similaire au modèle de promotion intermédiaire. Toutefois, il existe une différence fondamentale. Lorsque l’abonnement est prêt pour la promotion, le routage des utilisateurs finaux se produit pendant des mises en lots ou des vols. À chaque vol, des utilisateurs supplémentaires sont redirigés vers les systèmes de production.

**Avantages.** Les aspects positifs de cette approche sont les suivants :

- Ce modèle atténue les risques associés à une activité importante de migration ou de promotion. Les erreurs dans la solution migrée peuvent être identifiées avec moins d’impact sur les processus métier.
- Il permet de surveiller les demandes relatives au niveau de performance des charges de travail dans l’environnement cloud pendant une durée prolongée, ce qui améliore la précision des décisions de dimensionnement des ressources.
- De grands nombres de ressources peuvent être répliquées dans des contraintes de temps et de bande passante similaires.

**Inconvénients.** Les aspects négatifs de cette approche sont les suivants :

- L’outil de migration choisi ne peut pas faciliter la réplication continue après la migration.
- Un moyen secondaire de réplication des données est nécessaire pour synchroniser les plateformes de données pendant le délai d’exécution intermédiaire.

## <a name="next-steps"></a>Étapes suivantes

Une fois qu’un modèle de promotion est défini et accepté par l’équipe d’adoption du cloud, la [correction des ressources](./remediate.md) peut commencer.

> [!div class="nextstepaction"]
> [Corriger les ressources avant la migration](./remediate.md)
