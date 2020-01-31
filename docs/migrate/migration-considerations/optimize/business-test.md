---
title: Conseils pour les tests d’entreprise (UAT) pendant la migration
description: Un processus au sein d’une migration cloud qui se concentre sur les tâches de migration des charges de travail vers le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4c24ae176d3b8fc8ec4fa504ed406bc32a1c0ab3
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76801951"
---
# <a name="guidance-for-business-testing-uat-during-migration"></a>Conseils pour les tests d’entreprise (UAT) pendant la migration

Traditionnellement considérés comme une fonction informatique, les tests d’acceptation utilisateur (UAT) au cours d’une transformation métier peuvent être orchestrés uniquement par informatique. Toutefois, cette fonction est souvent exécutée plus efficacement en tant que fonction métier. Le service informatique prend ensuite en charge cette activité de l’entreprise en élaborant des plans de test et en facilitant et en automatisant les tests dans la mesure du possible. Bien que l’informatique puisse souvent se substituer aux tests, rien ne remplace l’observation directe des utilisateurs réels qui tentent de tirer parti d’une nouvelle solution dans le contexte d’un processus métier réel ou reproduit.

> [!NOTE]
> Lorsqu’ils sont disponibles, les tests automatisés sont un moyen bien plus efficace et efficient de tester un système. Toutefois, les migrations cloud sont souvent axées sur les systèmes hérités ou, du moins, sur des systèmes de production stables. Souvent, ces systèmes ne sont pas gérés par des tests automatisés complets et bien entretenus. Cet article suppose que ces tests ne sont pas disponibles au moment de la migration.

Après les tests automatisés, il y a les tests des changements apportés aux processus et aux technologies par les utilisateurs avancés. Les utilisateurs avancés sont les personnes qui exécutent généralement un processus réel nécessitant des interactions avec un outil technologique ou un ensemble d’outils. Ils peuvent être représentés par un client externe qui utilise un site d’e-commerce pour acquérir des biens ou des services. Les utilisateurs avancés peuvent également être représentés par un groupe d’employés qui exécutent un processus métier, tel qu’un centre d’appels qui traite les demandes de clients et enregistre leurs expériences.

L’objectif des tests d’entreprise est de solliciter la validation des utilisateurs avancés pour certifier que la nouvelle solution s’exécute conformément aux attentes et n’entrave pas les processus métier. Si cet objectif n’est pas respecté, le test d’entreprise sert de boucle de commentaires qui peut aider à définir pourquoi et comment la charge de travail ne répond pas aux attentes.

## <a name="business-activities-during-business-testing"></a>Activités commerciales pendant les tests d’entreprise

Lors des tests d’entreprise, la première itération est pilotée manuellement directement avec les clients. Il s’agit de la forme de boucle de commentaires la plus pure, mais aussi la plus chronophage.

- **Identifiez les utilisateurs avancés.** L’entreprise a généralement une meilleure compréhension des utilisateurs avancés qui sont les plus touchés par une modification technique.
- **Alignez et préparez les utilisateurs avancés.** Assurez-vous que les utilisateurs avancés comprennent les objectifs stratégiques, les résultats souhaités et les modifications attendues des processus métier. Préparez-les eux et leur structure de gestion au processus de test.
- **Participez à l’interprétation de la boucle de commentaires.** Aidez le personnel informatique à comprendre l’impact des différents points de commentaires des utilisateurs avancés.
- **Clarifiez le changement de processus.** Lorsque la transformation peut déclencher une modification des processus métier, signalez la modification et tous les impacts en aval.
- **Classez les commentaires par ordre de priorité.** Aidez l’équipe informatique à classer les commentaires par ordre de priorité en fonction de l’impact sur l’activité.

Parfois, le service informatique peut employer des analystes ou des propriétaires de produits qui peuvent agir en tant que mandataires pour les activités détaillées de test d’entreprise. Toutefois, la participation d’entreprises est fortement encouragée et est susceptible de produire des résultats métier favorables.

## <a name="it-activities-during-business-testing"></a>Activités informatiques pendant les tests d’entreprise

Le service informatique agit comme l’un des destinataires de la sortie des tests d’entreprise. Les boucles de commentaires exposées lors des tests d’entreprise deviennent finalement des éléments de travail qui définissent des modifications techniques ou des modifications de processus. En tant que destinataire, le service informatique doit contribuer à faciliter et à collecter les commentaires et à gérer les actions techniques qui en résultent. Voici quelques activités classiques que le service informatique effectue lors des tests d’entreprise :

- Fournir une structure et une logistique pour les tests d’entreprise.
- Faciliter les tests.
- Fournir un moyen et un processus pour enregistrer les commentaires.
- Aider l’entreprise à classer les commentaires par ordre de priorité et à les valider.
- Élaborer des plans pour donner suite aux modifications techniques.
- Identifier les tests automatisés existants qui pourraient rationaliser les tests effectués par les utilisateurs avancés.
- Pour les modifications susceptibles de nécessiter des déploiements ou des tests répétés, étudiez les processus de test, définissez des valeurs de référence et créez une automatisation afin de rationaliser les tests des utilisateurs avancés.

## <a name="next-steps"></a>Étapes suivantes

Conjointement avec les tests d’entreprise, [l’optimisation de ressources migrées](./optimize.md) peut améliorer les performances relatives aux charges de travail et aux coûts.

> [!div class="nextstepaction"]
> [Évaluer et redimensionner les ressources cloud](./optimize.md)
