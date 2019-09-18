---
title: Établir des itérations et des plans de publication de versions
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Établir des itérations et des plans de publication de versions
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 0dbef36d3909f11c1616d2e44c63227959c4ff56
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70839175"
---
# <a name="establish-iterations-and-release-plans"></a>Établir des itérations et des plans de publication de versions

La méthodologie agile et les autres méthodologies itératives sont basées sur les concepts d’itérations et de versions. Cet article décrit l’affectation des itérations et des versions lors de la planification. Ces affectations régissent la visibilité des chronologies afin de faciliter les conversations entre les membres de l’équipe de stratégie cloud. Les affectations alignent également les tâches techniques de telle façon que l’équipe d’adoption du cloud pourra les gérer pendant l’implémentation.

## <a name="establish-iterations"></a>Établir des itérations

Dans une approche itérative de l’implémentation technique, vous planifiez des efforts techniques autour de blocs de temps récurrents. Les itérations correspondent généralement à des blocs de temps d’une à six semaines. Le consensus suggère que deux semaines représentent la durée d’itération moyenne pour la plupart des équipes d’adoption du cloud. Toutefois, le choix de la durée des itérations dépend du type d’effort technique, de la charge administrative et de la préférence de l’équipe.

Pour commencer à aligner les efforts sur une chronologie, nous vous suggérons de définir un ensemble d’itérations d’une durée de 6 à 12 mois.

## <a name="understand-velocity"></a>Comprendre la vélocité

L’alignement des efforts sur les itérations et les versions nécessite une bonne compréhension de la vélocité. La vélocité est la quantité de travail qui peut être effectuée dans une itération donnée quelconque. Au cours d’une planification précoce, la vélocité est une estimation. Après plusieurs itérations, la vélocité devient un indicateur très précieux des engagements que l’équipe peut prendre en toute confiance.

Vous pouvez mesurer la vélocité dans des termes abstraits tels que des points de récit (story points). Vous pouvez également la mesurer dans des termes plus tangibles, comme les heures. Pour la plupart des infrastructures itératives, nous vous recommandons d’utiliser des mesures abstraites pour éviter les défis en matière de précision et de perception. Les exemples de cet article représentent la vélocité en heures par sprint. Cette représentation permet de comprendre ce concept de façon plus globale.

**Exemple :** Une équipe d’adoption du cloud de cinq personnes s’est engagée pour des sprints de deux semaines. Compte tenu des obligations actuelles, telles que les réunions et d’autres processus, chaque membre de l’équipe peut consacrer régulièrement 20 heures par semaine à l’effort d’adoption. Pour cette équipe, l’estimation initiale de la vélocité est de 100 heures par sprint.

## <a name="iteration-planning"></a>Planification des itérations

Initialement, vous planifiez les itérations en évaluant les tâches techniques en fonction du backlog hiérarchisé. Les équipes d’adoption du cloud estiment l’effort nécessaire pour effectuer diverses tâches. Ces tâches sont ensuite affectées à la première itération disponible.

Pendant la planification des itérations, les équipes d’adoption du cloud valident et affinent les estimations. Elles procèdent ainsi jusqu’à ce qu’elles aient aligné toute la vélocité disponible sur les tâches spécifiques. Ce processus se poursuit pour chaque charge de travail hiérarchisée jusqu’à ce que tous les efforts soient alignés sur une itération prévue.

Dans ce processus, l’équipe valide les tâches affectées au sprint suivant. L’équipe met à jour ses estimations en fonction de la conversation de l’équipe sur chaque tâche. L’équipe ajoute alors chaque tâche estimée au sprint suivant jusqu’à ce que la vélocité disponible soit atteinte. Enfin, l’équipe estime des tâches supplémentaires et les ajoute à l’itération suivante. L’équipe effectue ces étapes jusqu’à ce que la vélocité de cette itération soit également épuisée.

Le processus précédent continue jusqu’à ce que toutes les tâches soient affectées à une itération.

**Exemple :** Partons de l’exemple précédent. Supposons que chaque migration de charge de travail nécessite 40 tâches. Supposons également que nous estimons que chaque tâche dure une heure en moyenne. L’estimation combinée est d’environ 40 heures par migration de charge de travail. Si ces estimations restent cohérentes pour les 10 charges de travail hiérarchisées, 400 heures seront nécessaires pour ces charges de travail.

La vélocité définie dans l’exemple précédent suggère que la migration des 10 premières charges de travail nécessitera quatre itérations, ce qui correspond à deux mois calendaires. La première itération se composera de 100 tâches qui entraîneront la migration de deux charges de travail. L’itération suivante, une collection similaire de 100 tâches, entraînera la migration de trois charges de travail.

> [!WARNING]
> Les nombres précédents de tâches et d’estimations sont utilisés à titre d’exemple uniquement. Les tâches techniques sont rarement aussi régulières. Vous ne devriez pas voir cet exemple comme un reflet de la durée nécessaire à la migration d’une charge de travail.

## <a name="release-planning"></a>Planification de la mise en production

Dans le cadre de l’adoption du cloud, une version est définie comme une collection de livrables qui fournit une valeur commerciale suffisante pour justifier le risque d’interrompre les processus d’entreprise.

La publication de modifications liées aux charges de travail dans un environnement de production génère certains changements dans les processus d’entreprise. Dans l’idéal, ces changements sont transparents et l’entreprise voit la valeur des modifications sans interruptions significatives du service. Toutefois, un risque d’interruption de l’activité accompagne toute modification et ne doit pas être pris à la légère.

Pour s’assurer qu’une modification est justifiée par son retour potentiel, l’équipe de stratégie cloud doit participer à la planification des versions. Une fois les tâches alignées sur les sprints, l’équipe peut déterminer une chronologie approximative du moment où chaque charge de travail sera prête pour la mise en production. L’équipe de stratégie cloud doit examiner le minutage de chaque publication de version. L’équipe identifie alors le point d’inflexion entre le risque et la valeur pour l’entreprise.

**Exemple :** En poursuivant l’exemple précédent, l’équipe de stratégie cloud a passé en revue le plan d’itération. Cet examen a permis d’identifier deux points de version. Pendant la deuxième itération, un total de cinq charges de travail sera prêt pour la migration. Ces cinq charges de travail fourniront une valeur commerciale significative et déclencheront la première publication de version. La publication de version suivante interviendra deux itérations plus tard, lorsque les cinq charges de travail suivantes seront prêtes pour la publication.

## <a name="assign-iteration-paths-and-tags"></a>Affecter des chemins d’itération et des étiquettes

Pour les clients qui gèrent des plans d’adoption du cloud dans Azure DevOps, les processus précédents sont reflétés en affectant un chemin d’itération à chaque tâche et chaque récit utilisateur. Nous vous recommandons également d’étiqueter chaque charge de travail avec une version spécifique. Cet étiquetage et cette affectation alimentent le remplissage automatique des rapports de chronologie.

## <a name="next-steps"></a>Étapes suivantes

[Estimez les chronologies](./timelines.md) pour communiquer correctement les attentes.

> [!div class="nextstepaction"]
> [Estimer les chronologies](./timelines.md)
