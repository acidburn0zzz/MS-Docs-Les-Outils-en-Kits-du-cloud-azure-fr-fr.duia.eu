---
title: Criticité pour l’entreprise - Gestion cloud et opérations
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criticité pour l’entreprise - Gestion cloud et opérations
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: be5cc97c7b42eb79f0ec9721376524dc2710e2c4
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683628"
---
# <a name="business-impact-in-cloud-management"></a>Impact commercial en gestion cloud

Supposez le meilleur, préparez-vous au pire. Dans le cadre de la gestion informatique, il est normal de supposer que les charges de travail nécessaires à la prise en charge des opérations métier seront disponibles et exécutées dans les limites convenues, en fonction de la criticité sélectionnée. Toutefois, pour gérer les investissements judicieusement, il est important de comprendre l’impact qu’une panne ou qu’une détérioration des performances peuvent avoir pour l’entreprise. Cette importance est illustrée dans le graphique suivant, qui montre l’impact commercial de potentielles interruptions de charges de travail, sur une échelle de valeur relative.

![Impact des interruptions](../../_images/manage/time-value-impact.png)

Pour obtenir une comparaison équitable de la façon dont les différentes charges de travail du portefeuille sont impactées, il est recommandé d’utiliser une métrique Temps/Valeur. La métrique Temps/Heure montre l’impact négatif d’une panne de charge de travail. En règle générale, cet impact est enregistré sous la forme d’une perte directe sur le chiffre d’affaires ou sur le chiffre d’affaires d’exploitation au cours d’une panne. Pour être plus précis, on calcule le montant des pertes de revenus pour une unité de temps. La métrique Temps/Valeur la plus courante est « l’impact par heure », qui mesure les pertes de revenus d’exploitation par heure de panne.

Il existe plusieurs méthodes pour calculer l’impact. Les options disponibles dans les sections suivantes peuvent être utilisées avec des résultats similaires. Il est important d’utiliser la même méthode pour chaque charge de travail lorsque vous calculez les pertes protégées d’un portefeuille.

## <a name="start-with-estimates"></a>Commencer par les estimations

Les modèles d’exploitation actuels peuvent compliquer la détermination d’un impact précis. Heureusement, peu de systèmes ont besoin d’un calcul des pertes extrêmement précis. Dans l’étape précédente sur la classification selon la criticité, il a été suggéré que toutes les charges de travail démarrent par défaut avec une « criticité moyenne ». Les charges de travail de criticité moyenne ont généralement un niveau standard de gestion, avec un impact relativement faible sur les coûts d’exploitation. C’est seulement lorsqu’une charge de travail nécessite des ressources de gestion opérationnelle supplémentaires qu’une analyse financière précise est nécessaire.

Pour toutes les charges de travail standardisées, l’impact sur l’activité est une variable de priorité lorsque vous récupérez vos systèmes pendant une panne. En dehors de ces situations assez rares, l’impact sur l’activité modifie très peu, voire pas du tout, la gestion des opérations. 

## <a name="calculating-time"></a>Calcul du temps

Selon la nature de la charge de travail, les pertes peuvent être calculées différemment. Pour les systèmes transactionnels à vitesse élevée, tel qu’une plateforme commerciale en temps réel, les pertes par milliseconde peuvent avoir une grande importance. Les systèmes moins fréquemment utilisés, tels que le système de gestion des paies, ne sont probablement pas utilisés toutes les heures. Si la fréquence d’utilisation est élevée ou faible, il est important de normaliser la variable Temps lorsque vous calculez l’impact financier.

## <a name="calculating-total-impact"></a>Calcul de l’impact total

Lorsque des investissements de gestion supplémentaires sont souhaités, la précision de l’impact sur l’activité devient plus importante. Les points suivants listent les méthodes de calcul des pertes, de la plus précise à la moins précise :

- **Pertes ajustées :** Si l’entreprise a connu un événement ayant entraîné des pertes très importantes, comme un ouragan ou autre catastrophe naturelle, il est probable qu’un expert en sinistres ait calculé les pertes réelles subies pendant la panne. Ces calculs sont basés sur les normes du secteur des assurances pour le calcul des pertes et la gestion des risques. L’utilisation des pertes ajustées pour le montant total des pertes dans un laps de temps spécifique peut amener à des projections très précises.

- **Pertes historiques :** Si l’environnement local a subi des interruptions historiques dues à l’instabilité de l’infrastructure, il peut être un peu plus difficile de calculer les pertes. Toutefois, les formules de l’expert peuvent toujours être utilisées en interne. Pour calculer les pertes historiques, comparez les deltas des ventes, du chiffre d’affaires brut et des coûts d’exploitation sur trois périodes : avant, pendant et après une panne. L’examen de ces deltas peut permettre d’identifier des pertes précises quand aucune autre donnée n’est disponible.

- **Calcul complet des pertes :** Si aucune donnée historique n’est disponible, une valeur de perte comparative peut être obtenue. Dans ce modèle, déterminez le chiffre d’affaires brut moyen par heure pour l’unité commerciale. Partir du principe qu’une panne totale du système correspond à une perte de 100 % du chiffre d’affaires ne reflète pas vraiment la réalité lorsque vous effectuez des prévisions concernant les investissements de prévention des pertes. Toutefois, vous pouvez partir de ce principe pour comparer grossièrement les impacts et définir la priorité des investissements.

Avant de faire des suppositions concernant le calcul des pertes, collaborez avec votre service financier afin de déterminer la meilleure méthode pour calculer les pertes potentielles associées à une panne de charge de travail.

## <a name="calculating-workload-impact"></a>Calcul de l’impact d’une charge de travail

Les données historiques permettant de calculer les pertes peuvent être suffisantes pour déterminer clairement l’impact de chaque charge de travail sur ces pertes. C’est lors de cette évaluation que le partenariat avec l’entreprise est absolument essentiel. Une fois qu’un impact total a été calculé, cet impact doit être attribué à chaque charge de travail. Cette distribution d’impact doit provenir des parties prenantes de l’entreprise, qui doivent s’accorder sur l’impact relatif et cumulatif de chaque charge de travail. En outre, l’équipe doit solliciter les commentaires des cadres de l’entreprise pour valider l’alignement. Malheureusement, le résultat final est à la fois objectif et subjectif. L’importance de cet exercice est qu’il montre la logique et les opinions des parties prenantes de l’entreprise qui doivent s’exprimer quant à l’allocation du budget.

## <a name="using-the-template"></a>Utilisation du modèle

Les étapes suivantes s’appliquent aux lecteurs qui utilisent le [classeur Operations Management](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) pour planifier la gestion cloud.

1. Chacune des charges de travail présentées sous les onglets « Example » ou « Clean Template » doit être mise à jour par l’entreprise avec l’impact « Temps/Valeur » de chaque charge de travail. Par défaut, l’impact Temps/Heure représente les pertes projetées par heure, qui sont associées à une panne de charge de travail.

## <a name="next-steps"></a>Étapes suivantes

Une fois l’impact défini, les [engagements peuvent être alignés](./commitment.md).

> [!div class="nextstepaction"]
> [Aligner les engagements de gestion sur l’activité](./commitment.md)
