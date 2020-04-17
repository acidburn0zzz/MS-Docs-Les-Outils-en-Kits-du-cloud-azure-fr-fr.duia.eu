---
title: Désactiver les ressources hors service
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à désactiver correctement les ressources mises hors service avec une interruption minimale des activités.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ef890dce11530f30a0863ab9a51dcc3832125e24
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80432332"
---
# <a name="decommission-retired-assets"></a>Désactiver les ressources hors service

Une fois la charge de travail promue en production, les ressources qui hébergeaient auparavant la charge de travail de production ne sont plus nécessaires pour prendre en charge les opérations de l’entreprise. À ce stade, les ressources plus anciennes sont considérées mises hors service. Les ressources mises hors service peuvent ensuite être désactivées, ce qui réduit les coûts d’exploitation. La désactivation d’une ressource peut être aussi simple que de mettre la ressource hors tension et de la supprimer de manière responsable. Malheureusement, la désactivation des ressources peut parfois avoir des conséquences indésirables. Les instructions suivantes peuvent vous aider à désactiver correctement les ressources mises hors service, avec des interruptions d’activité minimes.

## <a name="cost-savings-realization"></a>Réalisation d’économies sur les coûts

Lorsque les économies sur les coûts sont la motivation principale d’une migration, la désactivation est une étape importante. Jusqu’à ce qu’une ressource soit désactivée, elle continue à consommer de la puissance, des capacités de prise en charge de l’environnement et d’autres ressources qui augmentent les coûts. Une fois la ressource désactivé, les économies sur les coûts peuvent commencer à être réalisées.

## <a name="continued-monitoring"></a>Surveillance continue

Après la promotion d’une charge de travail migrée, les ressources à mettre hors service doivent continuer à être surveillées pour vérifier qu’aucun autre trafic de production n’est acheminé vers les mauvaises ressources.

## <a name="testing-windows-and-dependency-validation"></a>Fenêtres de test et validation des dépendances

Même avec la meilleure planification, les charges de travail de production peuvent encore contenir des dépendances à l’égard de ressources supposées mises hors service. Dans de tels cas, la désactivation d’une ressource mise hors service peut entraîner des défaillances système inattendues. Par conséquent, l’arrêt de toute ressource doit être traité avec la même rigueur qu’une activité de maintenance du système. Des fenêtres appropriées de test et d’interruption doivent être établies pour faciliter l’arrêt de la ressource.

## <a name="holding-period-and-data-validation"></a>Période de conservation et validation des données

Il n’est pas rare que les migrations manquent de données pendant les processus de réplication. Cela est particulièrement vrai pour les données plus anciennes qui ne sont pas utilisées régulièrement. Une fois qu’une ressource mise hors service a été désactivée, il est toujours prudent de conserver la ressource pendant un certain temps pour servir de sauvegarde temporaire des données. Les entreprises doivent prévoir un délai d’au moins 30 jours de conservation et de test avant de détruire les ressources mises hors service.

## <a name="next-steps"></a>Étapes suivantes

Une fois les ressources mises hors service désactivées, la migration est terminée. Cela crée une bonne occasion d’améliorer le processus de migration, et une [rétrospective](./retrospective.md) permet à l’équipe d’adoption du cloud d’examiner la mise en production dans un effort d’apprentissage et d’amélioration.

> [!div class="nextstepaction"]
> [Rétrospective](./retrospective.md)
