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
ms.openlocfilehash: 290fcf7093f128c1415bbf960d65074d12490ae1
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683642"
---
# <a name="business-criticality-in-cloud-management"></a>Criticité pour l’entreprise en gestion cloud

Dans chaque entreprise, il existe un petit nombre de charges de travail qui sont trop importantes pour échouer. Lorsque ces charges de travail connaissent une panne ou une dégradation de leurs performances, l’impact négatif sur les revenus et la rentabilité se fait ressentir à tous les niveaux de l’entreprise. Ces charges de travail sont considérées comme critiques.

À l’inverse, certaines charges de travail peuvent ne pas être utilisées pendant plusieurs mois. Il n’est bien sûr pas souhaitable que ces charges de travail connaissent des pannes ou une baisse des performances, toutefois, l’impact sera isolé et limité.

La première chose à faire avant de prendre des engagements mutuels en gestion cloud est de comprendre l’importance de chaque charge de travail du portefeuille informatique.
L’image ci-dessous présente un alignement courant entre l’échelle de criticité à suivre et les engagements standard pris par l’entreprise.

![Criticité et alignement des niveaux de gestion](../../_images/manage/cloud-criticality-alignment.png)

## <a name="criticality-scale"></a>Échelle de criticité

Avant de procéder à l’alignement de la criticité, vous devez d’abord créer une échelle de criticité. Vous trouverez ci-dessous un exemple d’échelle qui peut être utilisé comme référence, ou comme modèle pour créer votre propre échelle.

|Caractère critique  |Impact sur l’entreprise  |
|---------|---------|
|Critique pour la mission|Impacte la mission de l’entreprise et peut avoir un impact notable sur ses pertes et profits.|
|Critique pour l’unité|Impacte la mission d’une unité commerciale, ainsi que ses pertes et profits.|
|Élevé|Peut ne pas entraver la mission, mais impacte les processus de haute importance. Les pertes mesurables peuvent être quantifiées en cas de panne.|
|Moyenne|L’impact sur les processus est probable. Les pertes sont faibles ou non mesurables, mais une atteinte de l’image de marque et des pertes en amont sont possibles.|
|Faible|L’impact sur les processus métier est mesurable. Aucune atteinte de l’image de marque ni pertes en amont ne sont probables. Un impact localisé (concernant une seule équipe) est probable.|
|Non pris en charge|Les propriétaires d’entreprise, les équipes et les processus associés à cette charge de travail ne peuvent pas justifier un investissement dans la gestion continue de la charge de travail.|

Il est courant pour les entreprises d’inclure des classifications de criticité supplémentaires propres à un secteur d’activité, à une verticale ou à un processus métier. Voici quelques exemples de classifications supplémentaires :

- **Critique pour la conformité :** Dans les secteurs très réglementés, certaines charges de travail peuvent être considérées comme critiques pour le maintien de la conformité.
- **Critique pour la sécurité :** Certaines charges de travail peuvent ne pas être critiques pour la mission, mais des pannes peuvent entraîner une perte de données ou un accès non souhaité aux informations protégées.
- **Critique pour la sécurité physique :** Lorsque la vie ou la sécurité physique des employés et des clients est menacée pendant une panne, il peut être judicieux de classifier les charges de travail comme étant critiques pour la sécurité physique.

## <a name="importance-of-accurate-criticality"></a>Importance d’une criticité précise

Plus loin dans ce processus, l’équipe de gestion cloud utilisera cette classification en vue de déterminer l’effort nécessaire pour atteindre les niveaux de criticité alignés. Dans les environnements locaux, la gestion des opérations est souvent achetée de façon centralisée et traitée comme une charge métier nécessaire, avec peu ou pas de coûts d’exploitation supplémentaires. Dans le cloud, la gestion des opérations (comme pour tout avec le cloud) est achetée pour chacune des ressources, et elle est prise en compte dans les frais de fonctionnement mensuels.

Étant donné que dans le cloud le coût de la gestion des opérations est direct et évident, il est important d’aligner correctement les coûts sur les échelles de criticité souhaitées.

## <a name="select-a-default-criticality"></a>Sélectionner une criticité par défaut

La révision initiale de chaque charge de travail du portefeuille peut prendre du temps. Pour garantir que cette tâche ne bloque pas la stratégie cloud dans son ensemble, il est préférable que le service informatique et l’entreprise s’accordent sur la criticité par défaut qu’il convient d’appliquer à toutes les charges de travail.

En fonction de l’échelle de criticité ci-dessus, il est recommandé d’utiliser la criticité « Moyenne » par défaut. Cela permettra à l’équipe de stratégie cloud d’identifier rapidement les charges de travail qui nécessitent un niveau de criticité plus élevé.

## <a name="using-the-template"></a>Utilisation du modèle

Les étapes suivantes s’appliquent aux lecteurs qui utilisent le [classeur Operations Management](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) pour planifier la gestion cloud.

1. Vous pouvez enregistrer l’échelle de criticité dans l’onglet Scale du classeur.
2. Chaque charge de travail qui se trouve sous l’onglet « Example » ou « Clean Template » doit être mise à jour pour refléter la criticité par défaut indiquée dans la colonne « Criticality ».
3. Les valeurs exactes doivent être entrées par l’entreprise pour voir les écarts qui existent par rapport à la criticité par défaut.

## <a name="next-steps"></a>Étapes suivantes

Une fois la criticité définie, [calculez puis enregistrez l’impact commercial](./impact.md).

> [!div class="nextstepaction"]
> [Calculer et enregistrer l’impact commercial](./impact.md)