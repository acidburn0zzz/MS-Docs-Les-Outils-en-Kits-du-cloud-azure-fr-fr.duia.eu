---
title: Hiérarchiser et définir les charges de travail pour l’adoption du cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à hiérarchiser et définir les charges de travail pour un plan d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 9f374bbe149e132fde4c44a8c0ecd9246615bac0
ms.sourcegitcommit: 388e32dd4861039149c846c926c0e9230cf28ae3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79140618"
---
# <a name="prioritize-and-define-workloads-for-a-cloud-adoption-plan"></a>Hiérarchiser et définir les charges de travail pour un plan d’adoption du cloud

L’établissement de priorités claires et exploitables est l’un des secrets de la réussite de l’adoption du cloud. Il est naturel d’être tenté de consacrer du temps à définir toutes les charges de travail qui pourraient potentiellement être affectées lors de l’adoption du cloud. Toutefois, cela s’avère contreproductif, notamment au début du processus d’adoption.

Au lieu de cela, nous vous recommandons de confier à votre équipe la tâche de hiérarchiser et documenter minutieusement les 10 premières charges de travail. Une fois que l’implémentation du plan d’adoption a commencé, l’équipe peut établir la liste des 10 charges de travail suivantes de plus haute priorité. Cette approche fournit suffisamment d’informations pour planifier les itérations suivantes.

La limitation du plan à 10 charges de travail favorise l’agilité et l’alignement des priorités à mesure que les critères métier évoluent. Cette approche donne également de l’espace à l’équipe d’adoption du cloud pour apprendre et affiner ses estimations. Plus important encore, elle abolit l’usage d’une planification approfondie, tel un obstacle à des changements opérationnels efficaces.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-a-workload"></a>Qu’est-ce qu’une charge de travail ?

Dans le contexte d’une adoption du cloud, une charge de travail est un ensemble de ressources informatiques (serveurs, machines virtuelles, applications, données ou appliances) qui soutiennent collectivement un processus défini. Les charges de travail peuvent soutenir plusieurs processus. Elles peuvent également dépendre d’autres ressources partagées ou plateformes étendues. Toutefois, une charge de travail doit avoir des limites définies en ce qui concerne les ressources et les processus qui en dépendent. Souvent, il est possible de visualiser les charges de travail en surveillant le trafic réseau entre les ressources informatiques.

## <a name="prerequisites"></a>Prérequis

Les entrées stratégiques de la liste des prérequis facilitent grandement les tâches suivantes. Pour obtenir de l’aide sur la collecte des données présentées dans cet article, passez en revue les [prérequis](./prerequisites.md).

## <a name="initial-workload-prioritization"></a>Hiérarchisation initiale des charges de travail

Au cours du processus de [rationalisation incrémentielle](../digital-estate/rationalize.md), votre équipe doit s’accorder sur une approche de type « puissance de 10 », qui est constituée de 10 charges de travail prioritaires. Ces charges de travail servent de limite initiale pour la planification de l’adoption.

Si vous décidez qu’une rationalisation du patrimoine numérique n’est pas nécessaire, nous recommandons aux équipes d’adoption du cloud et à l’équipe de stratégie cloud de convenir d’une liste de 10 applications qui serviront d’objectif initial de la migration. Nous vous recommandons de faire en sorte que ces 10 charges de travail comptent des charges de travail simples (moins de 10 ressources dans un déploiement autonome) et des charges de travail plus complexes. Ces 10 charges de travail commenceront le processus de hiérarchisation des charges de travail.

> [!NOTE]
> L’approche de type « puissance de 10 » sert de limite initiale pour la planification, afin de concentrer énergie et investissement dans une première phase d’analyse. Toutefois, l’analyse et la définition des charges de travail peuvent entraîner des modifications dans la liste des charges de travail prioritaires.

## <a name="add-workloads-to-your-cloud-adoption-plan"></a>Ajouter des charges de travail à votre plan d’adoption du cloud

Dans l’article précédent, [Plan d’adoption du cloud et Azure DevOps](./template.md), vous avez créé un plan d’adoption du cloud dans Azure DevOps.

Vous pouvez à présent représenter les charges de travail de la liste « Puissance de 10 » dans votre plan d’adoption du cloud. Le moyen le plus simple pour cela consiste à effectuer des modifications en bloc dans Microsoft Excel. Pour préparer votre station de travail pour des modifications en bloc, consultez [Ajouter ou modifier en bloc des éléments de travail avec Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

L’étape 5 de cet article vous indique de sélectionner **Liste d’entrée**. Au lieu de cela, sélectionnez **Liste de requête**. Ensuite, dans la liste déroulante **Sélectionner une requête**, sélectionnez la requête **Workload Template** (Modèle de charge de travail). Cette requête charge tous les efforts liés à la migration d’une charge de travail unique dans votre feuille de calcul.

Une fois que les éléments de travail du modèle de charge de travail ont été chargés, procédez comme suit pour commencer à ajouter de nouvelles charges de travail :

1. Copiez tous les éléments qui ont l’étiquette **Workload Template** (Modèle de charge de travail) dans la colonne la plus à droite.
2. Collez les lignes copiées sous la dernière ligne de la table.
3. Remplacez la cellule de titre de la nouvelle fonctionnalité de **Workload Template** (Modèle de charge de travail) par le nom de votre nouvelle charge de travail.
4. Collez la nouvelle cellule de nom de la charge de travail dans la colonne d’étiquettes pour toutes les lignes sous la nouvelle fonctionnalité. Veillez à ne pas modifier les étiquettes ni le nom des lignes associées à la véritable fonctionnalité **Workload Template** (Modèle de charge de travail). Vous aurez besoin de ces éléments de travail lorsque vous ajouterez la charge de travail suivante au plan d’adoption du cloud.
5. Passez directement à l’étape 8 des instructions de modification en bloc pour publier la feuille de calcul. Cette étape crée tous les éléments de travail requis pour migrer votre charge de travail.

Répétez les étapes 1 à 5 pour chacune des charges de travail de la liste « Puissance de 10 ».

## <a name="define-workloads"></a>Définir les charges de travail

Une fois que les priorités initiales ont été définies et que les charges de travail ont été ajoutées au plan, chaque charge de travail peut être définie via une analyse qualitative plus poussée. Avant d’inclure une charge de travail quelconque dans le plan d’adoption du cloud, essayez de fournir les points de données suivants pour chaque charge de travail.

### <a name="business-inputs"></a>Entrées opérationnelles

| Point de données | Description | Entrée |
|---|---|---|
| Nom de la charge de travail | Comment s’appelle cette charge de travail ? |         |
| Description de la charge de travail | En une phrase, que fait cette charge de travail ? |         |
| Motivations de l’adoption | Quelles sont les motivations de l’adoption du cloud qui sont affectées par cette charge de travail ? |         |
| Sponsor principal | Parmi les parties prenantes affectées, qui est le sponsor principal qui demande les motivations ci-dessus ? |         |
| Unité commerciale | Quelle unité commerciale est responsable du coût de cette charge de travail ? |         |
| Processus métier | Quels sont les processus métier qui seront affectés par les changements apportés à la charge de travail ? |         |
| Équipes commerciales | Quelles équipes commerciales seront affectées par les changements ? |         |
| Parties prenantes de l’entreprise | Existe-t-il des dirigeants dont l’activité sera affectée par les changements ? |         |
| Résultats métier | Comment l’entreprise mesurera-t-elle la réussite de cet effort ? |         |
| Mesures | Quelles métriques seront utilisées pour effectuer le suivi de la réussite ? |         |
| Conformité | Existe-t-il des exigences de conformité tierces pour cette charge de travail ? |         |
| Propriétaires d'applications | Qui est responsable de l’impact commercial des applications associées à cette charge de travail ? |         |
| Périodes de gel des activités | Y a-t-il des périodes pendant lesquelles l’entreprise n’autorisera pas les changements ? |         |
| Zones géographiques | Des zones géographiques sont-elles affectées par cette charge de travail ? |         |

### <a name="technical-inputs"></a>Entrées techniques

| Point de données | Description | Entrée |
|---|---|---|
| Approche d’adoption | Cette adoption est-elle candidate à une migration ou à une innovation ? |         |
| Chef des opérations d’application | Listez les parties responsables des performances et de la disponibilité de cette charge de travail. |         |
| Contrats SLA | Listez les contrats de niveau de service (exigences RTO/RPO). |         |
| Caractère critique | Listez l’importance actuelle de l’application. |         |
| Classification des données | Établissez le classement de la sensibilité des données. |         |
| Zones géographiques d’exploitation | Listez les zones géographiques dans lesquelles la charge de travail est ou doit être hébergée. |         |
| Applications | Spécifiez la liste initiale ou le nombre initial des applications incluses dans cette charge de travail. |         |
| Machines virtuelles | Spécifiez la liste initiale ou le nombre initial des machines virtuelles et des serveurs inclus dans la charge de travail. |         |
| Sources de données | Spécifiez la liste initiale ou le nombre initial des sources de données incluses dans la charge de travail. |         |
| Les dépendances | répertorie toutes les dépendances de ressources non incluses dans la charge de travail. |         |
| Zones géographiques du trafic utilisateur | Listez les zones géographiques qui ont un volume important de trafic utilisateur. |         |

## <a name="confirm-priorities"></a>Confirmer les priorités

Sur la base des données assemblées, l’équipe de stratégie cloud et l’équipe d’adoption du cloud doivent se réunir pour réévaluer les priorités. La clarification des points de données de l’entreprise peut entraîner des modifications des priorités. La complexité ou des dépendances techniques peuvent entraîner des modifications liées aux affectations de personnel, aux chronologies ou au séquencement des efforts techniques.

Après examen des données, les deux équipes doivent être en mesure de confirmer les priorités qui en résultent. Cet ensemble de priorités documentées, validées et confirmées constitue le backlog d’adoption du cloud classé par ordre de priorité.

## <a name="next-steps"></a>Étapes suivantes

Pour toute charge de travail figurant dans le backlog d’adoption du cloud classé par ordre de priorité, l’équipe est maintenant prête à [aligner des ressources](./assets.md).

> [!div class="nextstepaction"]
> [Aligner des ressources pour les charges de travail hiérarchisées](./assets.md)
