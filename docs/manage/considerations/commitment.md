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
ms.openlocfilehash: 7e7618163b15d17eab51571779e573dd9acb726e
ms.sourcegitcommit: 73dbedf580951f25bf4b5544b83451cb075b1fa1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72805822"
---
# <a name="business-commitment-in-cloud-management"></a>Engagement commercial dans la gestion cloud

La définition d’un engagement commercial est un exercice d’équilibrage des priorités. L’objectif est d’aligner le niveau adéquat de gestion opérationnelle sur un coût de fonctionnement acceptable. Cet équilibrage requiert quelques points de données et calculs, présentés dans les sections suivantes.

![Équilibrer les coûts et la résilience](../../_images/manage/business-commitment-scale.png)

Les engagements en matière de stabilité métier (par résilience technique ou autres impacts de contrats SLA) constituent une décision de justification métier. Pour la plupart des charges de travail dans un environnement, un niveau de base en gestion cloud est suffisant. Pour les autres, une augmentation des coûts de 2 à 4 fois supérieure des coûts se justifie facilement en raison de l’impact potentiel des interruptions de l’entreprise. Les articles précédents de cette série aident à comprendre la classification et l’impact des interruptions sur diverses charges de travail. Cet article vous aidera à calculer les retours. Comme indiqué dans l’image suivante, à chaque niveau de la gestion du cloud, il existe des points d’inflexion où le coût peut augmenter plus rapidement que la résilience. Ces points d’inflexion vous invitent à prendre des décisions commerciales détaillées et des engagements commerciaux.

## <a name="determining-a-proper-commitment-with-the-business"></a>Détermination d’un engagement adéquat avec l’entreprise

Pour chaque charge de travail du portefeuille, l’équipe des opérations cloud et l’équipe de stratégie cloud doivent s’aligner sur le niveau de gestion fourni directement par l’équipe d’exploitation du cloud.

Les aspects clés à respecter lors de l’établissement d’un engagement avec l’entreprise sont les suivants :

- Conditions requises pour les opérations informatiques
- Responsabilité de gestion
- Location cloud
- Facteurs de coût souple
- ROI pour éviter les pertes
- Valider un niveau d’administration

Le reste de cet article décrit chacun de ces critères pour vous aider à prendre une décision.

## <a name="it-operations-prerequisites"></a>Conditions requises pour les opérations informatiques

Le [Guide de gestion Azure](../azure-management-guide/index.md) présente les outils de gestion disponibles dans Azure. Avant de parvenir à un engagement envers l’entreprise, le département informatique doit déterminer une ligne de base de gestion standard acceptable à appliquer à toutes les charges de travail gérées. Il calcule ensuite un coût de gestion standard pour chacune des charges de travail gérées dans le portefeuille informatique, en fonction du nombre de cœurs de processeur, de l’espace disque et d’autres variables relatives aux ressources. Il évalue également un contrat SLA composite pour chaque charge de travail selon l’architecture.

> [!TIP]
> Les équipes d’exploitation informatique utilisent souvent une durée de fonctionnement minimale de 99,9% par défaut pour le contrat SLA composite initial. Ils peuvent également choisir de normaliser les coûts de gestion en fonction de la charge de travail moyenne, en particulier pour les solutions ayant des besoins minimaux en journalisation et en stockage. La moyenne des coûts de quelques charges de travail de gravité moyenne peut constituer un point de départ pour les conversations initiales.

> [!TIP]
> Pour les lecteurs qui utilisent le classeur [Gestion des opérations](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) pour planifier la gestion cloud, les champs de gestion des opérations doivent être mis à jour pour refléter ces conditions préalables. Ces champs incluent le niveau d’engagement, le contrat SLA composite et le coût mensuel. Le coût mensuel doit représenter le coût des outils de gestion opérationnelle ajoutés sur une base mensuelle.

La ligne de base de la gestion des opérations servira de point de départ à valider dans chacune des sections suivantes.

## <a name="management-responsibility"></a>Responsabilité de gestion

Dans un environnement local traditionnel, le coût de la gestion de l’environnement est généralement considéré comme un coût irrécupérable détenu par les opérations informatiques. Dans le cloud, la gestion est une décision intentionnelle avec un impact budgétaire direct. Les coûts de chaque fonction de gestion peuvent être plus directement attribués à chaque charge de travail déployée dans le cloud. Cette approche permet un meilleur contrôle, mais elle crée une exigence pour les équipes d’exploitation cloud et les équipes de stratégie cloud pour s’engager en premier lieu à un accord concernant les responsabilités.

Les organisations peuvent également choisir de [sous-traiter certaines de leurs fonctions de gestion en cours avec un fournisseur de services](https://www.microsoft.com/cloud-adoption-framework-offers?ot=manage). Ces fournisseurs de services peuvent utiliser [Azure Lighthouse](https://azure.com/lighthouse) pour offrir aux organisations une plus grande précision et un meilleur contrôle dans l’octroi de l’accès à leurs ressources, ainsi qu’une meilleure transparence des actions effectuées par les fournisseurs de services.

**Responsabilité déléguée** : Étant donné qu’il n’est pas nécessaire de centraliser et de prévoir une surcharge de gestion opérationnelle, les opérations informatiques de nombreuses organisations envisagent de nouvelles approches. L’une des approches courantes est appelée responsabilité déléguée. Dans un modèle de centre d’excellence cloud, les opérations de plateforme et l’automatisation de plateforme fournissent des outils de gestion libre-service qui peuvent être exploités par les équipes d’exploitation, indépendamment d’une équipe centrale des opérations informatiques. Cette approche offre aux parties prenantes de l’entreprise un contrôle total sur les budgets liés à la gestion. Il permet également au centre d’excellence cloud de s’assurer qu’un nombre minimum de rambardes est correctement implémenté. Dans ce modèle, l’informatique agit comme un courtier et un guide pour aider l’entreprise à prendre des décisions judicieuses. Les opérations métier supervisent les opérations quotidiennes des charges de travail dépendantes.

**Responsabilité centralisée** : Les exigences de conformité, la complexité technique et certains modèles de service partagés peuvent nécessiter un modèle informatique central. Dans ce modèle, l’IT continue de gérer les responsabilités de gestion des opérations. Par conséquent, la conception environnementale, les contrôles de gestion et les outils de gouvernance peuvent être gérés et contrôlés de manière centralisée, ce qui limite le rôle des parties prenantes dans le cadre des engagements de gestion. Toutefois, le coût et la visibilité de l’architecture des approches du cloud facilitent grandement la communication des coûts et du niveau de gestion pour chaque charge de travail.

**Modèle mixte :** La classification est au cœur d’un modèle mixte aux responsabilités de gestion. Les entreprises qui se trouvent au milieu d’une transformation d’un environnement local vers le cloud peuvent nécessiter un modèle d’exploitation local en premier pendant un certain temps. D’autres sociétés qui ont des exigences strictes en matière de conformité ou qui dépendent de contrats à long terme avec des fournisseurs sous-traitants peuvent nécessiter un modèle d’exploitation centralisé. Malgré ces types de contraintes, les entreprises ont besoin d’innover. Lorsque l’innovation rapide doit croître, au milieu d’un modèle de responsabilité informatique centralisée, la classification et un modèle mixte peuvent fournir un équilibre. Dans cette approche, l’informatique centrale fournit un modèle d’exploitation centralisé pour toutes les charges de travail stratégiques ou qui contiennent des informations sensibles. Toutefois, toutes les autres classifications de charge de travail peuvent être placées dans un environnement cloud conçu pour les responsabilités déléguées. L’approche de responsabilité centralisée fait office de modèle d’exploitation général. L’entreprise a ensuite la possibilité de tirer parti d’un modèle d’exploitation spécialisé, en fonction du niveau de support et de sensibilité requis.

La première étape est la validation d’une approche de responsabilité, qui met en forme les engagements suivants.

**Quelle organisation sera responsable de la gestion des opérations quotidiennes pour cette charge de travail ?**

## <a name="cloud-tenancy"></a>Location cloud

Pour la plupart des entreprises, la gestion est plus facile lorsque toutes les ressources résident dans un seul locataire. Toutefois, certaines organisations peuvent avoir besoin de gérer plusieurs locataires. L’article sur la [centralisation des opérations de gestion avec Azure Lighthouse](../centralize-operations.md) fournit quelques exemples où les entreprises peuvent nécessiter des environnements Azure multilocataires.

**Cette charge de travail se trouve-t-elle dans un seul locataire Azure, avec toutes les autres charges de travail ?**

## <a name="soft-cost-factors"></a>Facteurs de coût souple

La section suivante de cet article décrit une approche des retours comparatifs associés aux niveaux de processus et d’outils de gestion. À la fin de cette section, chaque charge de travail analysée mesure le coût de la gestion par rapport à l’impact prévu des interruptions de l’entreprise. Cette approche offre un moyen relativement facile de comprendre si l’investissement dans des approches de gestion plus riche est justifié.

Avant d’exécuter les nombres, il est important d’examiner les facteurs de coût souple. Les facteurs de coût souple génèrent un retour, mais ce retour est difficile à mesurer par le biais d’économies directes qui seraient visibles dans une déclaration de bénéfices et de pertes. Les facteurs de coût souple sont importants, car ils peuvent indiquer un besoin d’investir dans un niveau de gestion élevé.

Voici quelques exemples de ces facteurs :

- Utilisation quotidienne par le conseil ou le CEO.
- Utilisation d’une charge de travail par les _x%_ des meilleurs clients qui ont un impact accru sur les revenus ailleurs.
- Impact sur la satisfaction des employés.

Le point de données suivant requis pour faire un engagement est une liste de facteurs de coût souple. Ils n’ont pas besoin d’être documentés à ce niveau, mais la partie prenante de l’entreprise doit être consciente de l’importance de ces facteurs et de leur exclusion des calculs suivants.

## <a name="calculate-loss-avoidance-roi"></a>Calculer le ROI pour éviter les pertes

Lors du calcul du retour relatif sur les coûts de gestion des opérations, l’équipe informatique chargée des opérations cloud doit remplir les conditions préalables ci-dessus et effectuer un niveau minimal de gestion pour toutes les charges de travail.

Le prochain engagement à effectuer est l’acceptation par l’entreprise des coûts associés à l’offre gérée par référence.

**L’entreprise est-elle d’accord pour investir dans l’offre de base pour répondre aux normes minimales des opérations cloud ?**

Si l’entreprise n’accepte pas ce niveau de gestion, une solution doit être conçue pour permettre à l’entreprise de continuer, sans affecter de manière significative les opérations cloud d’autres charges de travail.

Si l’entreprise souhaite un niveau supérieur au niveau standard, le reste de cette section vous aidera à valider cet investissement et les retours associés (sous forme de prévention des pertes).

### <a name="increased-levels-of-management-design-principles-and-service-catalog"></a>Augmentation des niveaux de gestion : Principes de conception et catalogue de services

Pour les solutions gérées, plusieurs principes de conception et solutions de modèles peuvent être appliqués en plus de la ligne de base de gestion. Chacun des principes de conception en matière de fiabilité et de résilience augmente le coût d’exploitation de la charge de travail. Pour permettre aux professionnels de l’informatique et aux entreprises de s’accorder sur ces engagements supplémentaires, il est important de comprendre les pertes potentielles qui peuvent être évitées par le biais de ces investissements accrus.

Les calculs suivants vous guideront dans les formules pour mieux comprendre la comparaison entre les pertes et les investissements de gestion accrus. Pour obtenir des conseils sur le calcul du coût d’une gestion accrue, consultez les articles sur l’[automatisation de la charge de travail](./workload.md) et l’[automation de la plateforme](./platform.md).

> [!TIP]
> Pour les lecteurs qui utilisent le classeur [Gestion des opérations](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) pour planifier la gestion cloud, les champs de gestion des opérations doivent être mis à jour pour refléter chaque conversation. Ces champs incluent le niveau d’engagement, le contrat SLA composite et le coût mensuel. Le coût mensuel doit représenter le coût des outils de gestion opérationnelle ajoutés sur une base mensuelle. Une fois mis à jour, ces champs mettent à jour les formules ROI et chacun des champs suivants.

### <a name="estimate-outage-hours-per-year"></a>Estimation de l’interruption (heures par année)

Le « contrat SLA composite » est le contrat de niveau de service basé sur le déploiement de chaque ressource de la charge de travail. Ce champ indique « Estimation de l’interruption » (marquée Est. interruption*** dans le classeur). Pour estimer l’interruption en heures par année sans utiliser le classeur, appliquez la formule suivante :

**Estimation de l’interruption = (1 - Pourcentage SLA composite) /* Nombre d’heures dans une année**

Dans le classeur, la valeur par défaut utilisée est de 8 760 heures par an.

### <a name="standard-loss-impact"></a>Impact sur la perte standard

L’impact sur la perte standard (intitulé « Impact standard » dans le classeur) prévoit l’impact financier de toute interruption, en supposant que la prédiction « Estimation de l’interruption » est exacte. Pour calculer cette prévision sans utiliser le classeur, appliquez la formule suivante :

**Impact standard = Estimation de l’interruption @ trois 9 du temps d’activité /* Impact Durée/Valeur**

Cela sert de base pour le coût, si les parties prenantes de l’entreprise choisissent d’investir dans un niveau de gestion plus élevé.

### <a name="composite-sla-impact"></a>Impact du contrat SLA composite

L’impact sur le contrat SLA composite (intitulé « Impact de niveau d’engagement » dans le classeur) fournit un impact fiscal mis à jour, en fonction des modifications apportées au contrat SLA de temps d’activité. Cela vous permet de comparer l’impact financier projeté des deux options. Pour calculer cet impact prévu sans la feuille de calcul, appliquez la formule suivante.

**Impact du contrat SLA composite = Estimation de l’interruption /* Impact Durée/Valeur**

La valeur représente les pertes potentielles à éviter par le niveau d’engagement modifié et le nouveau contrat SLA composite.

### <a name="comparison-basis"></a>Base de comparaison

La base de comparaison évalue l’impact standard et l’impact du contrat SLA composite pour déterminer lequel est le plus approprié dans la colonne de retour.

### <a name="return-on-loss-avoidance"></a>Retour sur prévention des pertes

Si le coût de la gestion d’une charge de travail dépasse les pertes potentielles, l’investissement proposé dans la gestion cloud peut ne pas être fructueux. Pour comparer le « retour sur prévention des pertes », consultez la colonne intitulée « ROI annuel**** ». Pour calculer cette colonne vous-même, utilisez la formule suivante :

**Retour sur prévention des pertes = (Base de comparaison - (Coût mensuel /* 12)) // (Coût mensuel/* 12))**

À moins qu’il n’y ait d’autres facteurs de coût logiciel à prendre en compte, cette comparaison peut rapidement suggérer s’il y a un investissement plus approfondi dans les opérations cloud, la résilience, la fiabilité ou d’autres domaines.

## <a name="validate-the-commitment"></a>Valider l’engagement

À ce stade du processus, des engagements ont été pris : la responsabilité centralisée ou déléguée, la location Azure et le niveau d’engagement.
Chaque engagement doit être validé et documenté pour s’assurer que l’équipe d’exploitation du cloud, l’équipe de stratégie cloud et les parties prenantes de l’entreprise sont en accord avec cet engagement pour gérer la charge de travail.

## <a name="next-steps"></a>Étapes suivantes

Une fois les engagements effectués, les équipes d’exploitation responsables peuvent commencer la configuration de la charge de travail en question. Pour commencer, évaluez les différentes approches d’[inventaire et de visibilité](./inventory.md).

> [!div class="nextstepaction"]
> [Options d’inventaire et de visibilité](./inventory.md)
