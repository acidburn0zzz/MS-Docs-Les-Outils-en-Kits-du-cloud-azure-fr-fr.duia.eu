---
title: Impact commercial en gestion cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à déterminer et comprendre l’impact potentiel des pannes ou de la détérioration des performances sur votre entreprise.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: dc2c490850c47dfa92ec91d5133168b982b5c719
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83398482"
---
# <a name="business-impact-in-cloud-management"></a>Impact commercial en gestion cloud

Supposez le meilleur, préparez-vous au pire. Dans le cadre de la gestion informatique, il est normal de supposer que les charges de travail nécessaires à la prise en charge des opérations métier seront disponibles et exécutées dans les limites convenues, en fonction de l’état critique sélectionnée. Toutefois, pour gérer les investissements judicieusement, il est important de comprendre l’impact que peuvent avoir sur l’entreprise une panne ou une détérioration des performances. Cette importance est illustrée dans le graphique suivant, qui montre l’impact commercial de potentielles interruptions de charges de travail spécifiques, sur une échelle de valeur relative.

![Impact des interruptions](../../_images/manage/time-value-impact.png)

Pour obtenir une comparaison équitable de la façon dont les différentes charges de travail du portefeuille sont impactées, il est recommandé d’utiliser une métrique Temps/Valeur. La métrique Temps/Heure montre l’impact négatif d’une panne de charge de travail. En règle générale, cet impact est enregistré sous la forme d’une perte directe sur le chiffre d’affaires ou sur le chiffre d’affaires d’exploitation au cours d’une panne. Pour être plus précis, le montant des pertes de revenus pour une unité de temps est calculé. La métrique Temps/Valeur la plus courante est _Impact par heure_, qui mesure les pertes de revenus d’exploitation par heure de panne.

Plusieurs approches de calcul de l’impact peuvent être utilisées. Vous pouvez appliquer les options disponibles dans les sections suivantes pour obtenir des résultats similaires. Il est important d’utiliser la même approche pour chaque charge de travail lorsque vous calculez les pertes protégées d’un portefeuille.

## <a name="start-with-estimates"></a>Commencer par les estimations

Les modèles d’exploitation actuels peuvent compliquer la détermination d’un impact précis. Heureusement, peu de systèmes ont besoin d’un calcul des pertes extrêmement précis. Dans l’étape précédente, _Classifier l’état critique_, il a été suggéré que toutes les charges de travail démarrent par défaut avec un _état critique moyen_. Les charges de travail de l’état critique moyen reçoivent généralement un niveau standard de support de gestion, avec un impact relativement faible sur les coûts d’exploitation. C’est seulement lorsqu’une charge de travail nécessite des ressources de gestion opérationnelle supplémentaires qu’un impact financier précis est nécessaire.

Pour toutes les charges de travail standardisées, l’impact commercial est une variable de priorité lorsque vous récupérez vos systèmes pendant une panne. En dehors de ces situations assez rares, l’impact commercial modifie très peu, voire pas du tout, la gestion des opérations.

## <a name="calculate-time"></a>Calculer l’heure

Selon la nature de la charge de travail, les pertes sont calculées différemment. Pour les systèmes transactionnels à vitesse élevée, tel qu’une plateforme commerciale en temps réel, les pertes par milliseconde peuvent avoir une grande importance. Les systèmes moins fréquemment utilisés, tels que les données de paie, ne sont probablement pas utilisés toutes les heures. Si la fréquence d’utilisation est élevée ou faible, il est important de normaliser la variable Temps lorsque vous calculez l’impact financier.

## <a name="calculate-total-impact"></a>Calculer l’impact total

Lorsque vous souhaitez prendre en compte des investissements de gestion supplémentaires, la précision de l’impact sur l’activité devient plus importante. Les trois approches suivantes pour calculer les pertes sont classées de la plus précise à la moins précise :

- **Pertes ajustées :** Si l’entreprise a connu un événement ayant entraîné des pertes très importantes, comme un ouragan ou autre catastrophe naturelle, il est probable qu’un expert en sinistres ait calculé les pertes réelles subies pendant la panne. Ces calculs sont basés sur les normes du secteur des assurances pour le calcul des pertes et la gestion des risques. L’utilisation des pertes ajustées pour le montant total des pertes dans un laps de temps spécifique peut amener à des projections très précises.

- **Pertes historiques :** Si l’environnement local a subi des interruptions historiques dues à l’instabilité de l’infrastructure, il peut être un peu plus difficile de calculer les pertes. Vous pouvez cependant toujours appliquer les formules d’ajustement utilisées en interne. Pour calculer les pertes historiques, comparez les deltas des ventes, du chiffre d’affaires brut et des coûts d’exploitation sur trois délais d'exécution : avant, pendant et après une panne. L’examen de ces deltas peut permettre d’identifier des pertes précises quand aucune autre donnée n’est disponible.

- **Calcul complet des pertes :** Si aucune donnée historique n’est disponible, une valeur de perte comparative peut être dérivée. Dans ce modèle, déterminez le chiffre d’affaires brut moyen par heure pour l’unité commerciale. Lorsque vous projetez des investissements en matière d’élimination des pertes, il n’est pas juste de supposer qu’une panne système complète correspond à une perte de chiffre de 100 %. Toutefois, vous pouvez partir de ce principe pour comparer grossièrement les impacts et définir la priorité des investissements.

Avant de faire des suppositions concernant les pertes potentielles associées aux pannes de la charge de travail, il est conseillé de collaborer avec votre service financier afin de déterminer la meilleure méthode pour effectuer de tels calculs.

## <a name="calculate-workload-impact"></a>Calculer l’impact d’une charge de travail

Lorsque vous calculez des pertes en appliquant des données historiques, vous pouvez avoir suffisamment d’informations pour déterminer clairement la contribution de chaque charge de travail à ces pertes. C’est lors de cette évaluation que les partenariats au sein de l’entreprise sont absolument essentiels. Une fois qu’un impact total a été calculé, cet impact doit être attribué à chaque charge de travail. Cette distribution d’impact doit provenir des parties prenantes de l’entreprise, qui doivent s’accorder sur l’impact relatif et cumulatif de chaque charge de travail. En outre, l’équipe doit solliciter les commentaires des cadres de l’entreprise pour valider l’alignement. Le résultat final de tels commentaires est à la fois objectif et subjectif. L’importance de cet exercice est qu’il illustre la logique et les opinions des parties prenantes de l’entreprise qui doivent s’exprimer quant à l’allocation du budget.

## <a name="use-the-template"></a>Utiliser le modèle

Si vous utilisez le [classeur de gestion des operations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) pour planifier la gestion cloud, procéder comme suit :

- Chaque entreprise doit mettre à jour chacune des charges de travail présentées sous les onglets _Exemple_ et _Nettoyer le modèle_ avec *Impact Temps/Valeur* de chaque charge de travail. Par défaut, *Impact Temps/Valeur* représente les pertes projetées par heure, associées à une panne de charge de travail.

## <a name="next-steps"></a>Étapes suivantes

Une fois que l’entreprise a un impact défini, vous pouvez [aligner les engagements](./commitment.md).

> [!div class="nextstepaction"]
> [Aligner les engagements de gestion sur l’activité](./commitment.md)
