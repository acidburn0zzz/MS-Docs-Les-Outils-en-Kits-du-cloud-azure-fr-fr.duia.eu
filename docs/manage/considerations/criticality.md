---
title: Criticité pour l’entreprise en gestion cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin de comprendre la criticité de la charge de travail et d’éviter tout impact négatif sur le chiffre d’affaires et la rentabilité.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 2114b212718adb22b190f854de665e0d59fa50a4
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83398469"
---
# <a name="business-criticality-in-cloud-management"></a>Criticité pour l’entreprise en gestion cloud

Dans chaque entreprise, il existe un petit nombre de charges de travail qui sont trop importantes pour échouer. Ces charges de travail sont considérées comme stratégiques. Lorsque ces charges de travail connaissent des pannes ou une dégradation de leurs performances, l’impact négatif sur les revenus et la rentabilité se fait ressentir à tous les niveaux de l’entreprise.

À l’inverse, certaines charges de travail peuvent ne pas être utilisées pendant plusieurs mois. Il n’est bien sûr pas souhaitable que ces charges de travail connaissent des pannes ou une baisse des performances, toutefois, l’impact sera isolé et limité.

La première chose à faire avant de prendre des engagements mutuels en gestion cloud est de comprendre l’importance de chaque charge de travail du portefeuille informatique.
Le diagramme suivant présente un alignement courant entre l’échelle des états critiques à suivre et les engagements standard pris par l’entreprise.

![Criticité et alignement des niveaux de gestion](../../_images/manage/cloud-criticality-alignment.png)

## <a name="criticality-scale"></a>Échelle de criticité

Avant de procéder à l’alignement de l’état critique de l’entreprise, vous devez d’abord créer une échelle des états critiques. Le tableau suivant présente un exemple de mise à l’échelle à utiliser comme référence, ou modèle, pour créer votre propre échelle.

| Caractère critique | Affichage de l’entreprise |
| --------- | --------- |
| Intégration stratégique |  Affecte la mission de l’entreprise et peut affecter de façon notable les déclarations de pertes et profits d’entreprise. |
| Unité-critique | Impacte la mission d’une unité commerciale spécifique, ainsi que ses déclarations de pertes et profits. |
| Élevé | Peut ne pas entraver la mission, mais impacte les processus de haute importance. Les pertes mesurables peuvent être quantifiées en cas de panne. |
| Moyenne | L’impact sur les processus est probable. Les pertes sont faibles ou non mesurables, mais une atteinte de l’image de marque et des pertes en amont sont possibles. |
| Faible | L’impact sur les processus d’entreprise n’est pas mesurable. Aucune atteinte de l’image de marque ni pertes en amont ne sont probables. Un impact localisé concernant une seule équipe est probable. |
| Non pris en charge | Les propriétaires d’entreprise, les équipes et les processus associés à cette charge de travail ne peuvent pas justifier un investissement dans la gestion continue de la charge de travail. |

Il est courant pour les entreprises d’inclure des classifications d’état critique supplémentaires propres à leurs processus d’activité, verticaux ou métier spécifiques. Voici quelques exemples de classifications supplémentaires :

- **Critique pour la conformité :** Dans les secteurs très réglementés, certaines charges de travail peuvent être considérées comme critiques pour le maintien des exigences de conformité.
- **Critique pour la sécurité :** Certaines charges de travail peuvent ne pas être critiques pour la mission, mais des pannes peuvent entraîner une perte de données ou un accès non souhaité aux informations protégées.
- **Critique pour la sécurité physique :** Lorsque la vie ou la sécurité physique des employés et des clients est menacée pendant une panne, il peut être judicieux de classifier les charges de travail comme étant critiques pour la sécurité physique.

## <a name="importance-of-accurate-criticality"></a>Importance d’une criticité précise

Plus loin dans le processus d’adoption cloud, l’équipe de gestion cloud utilisera cette classification en vue de déterminer l’effort nécessaire pour atteindre les niveaux d’état critique alignés. Dans les environnements locaux, la gestion des opérations est souvent achetée de façon centralisée et traitée comme une charge métier nécessaire, avec peu ou pas de coûts d’exploitation supplémentaires. Dans le cloud, la gestion des opérations (comme pour tout avec le cloud) est achetée pour chacune des ressources, et elle est prise en compte dans les frais de fonctionnement mensuels.

Étant donné que dans le cloud le coût de la gestion des opérations est direct et évident, il est important d’aligner correctement les coûts sur les échelles d’état critique souhaitées.

## <a name="select-a-default-criticality"></a>Sélectionner une criticité par défaut

La révision initiale de chaque charge de travail du portefeuille peut prendre du temps. Pour garantir que cette tâche ne bloque pas la stratégie cloud dans son ensemble, il est préférable que vos équipes s’accordent sur l’état critique par défaut qu’il convient d’appliquer à toutes les charges de travail.

En fonction de la table de mise à l’échelle de l’état critique précédente, nous vous recommandons d’adopter un état critique _Moyen_ comme valeur par défaut. Cela permettra à votre équipe de stratégie cloud d’identifier rapidement les charges de travail qui nécessitent un niveau d’état critique plus élevé.

## <a name="use-the-template"></a>Utiliser le modèle

Les étapes suivantes s’appliquent si vous utilisez le [classeur de gestion des opérations](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) pour planifier la gestion cloud.

1. Enregistrez l’échelle des états critiques dans l’onglet **Mettre à l'échelle** du classeur.
2. Mettez à jour chaque charge de travail qui se trouve dans l’onglet _Exemple_ ou _Nettoyer le modèle_ pour refléter l’état critique par défaut indiqué dans la colonne _État critique_.
3. L’entreprise doit entrer les valeurs exactes pour voir les écarts qui existent par rapport à l’état critique par défaut.

## <a name="next-steps"></a>Étapes suivantes

Une fois que votre équipe a défini l’état critique de l’entreprise, vous pouvez [calculer et enregistrer l’impact commercial](./impact.md).

> [!div class="nextstepaction"]
> [Calculer et enregistrer l’impact commercial](./impact.md)
