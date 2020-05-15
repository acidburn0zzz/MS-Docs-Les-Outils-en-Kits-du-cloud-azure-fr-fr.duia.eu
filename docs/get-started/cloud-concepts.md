---
title: "Bien démarrer : Documenter les décisions d'alignement de base"
description: Identifiez et documentez les décisions initiales nécessaires au parcours d'adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 0c59a383f47629dd16cd81bc6865812fcaca4679
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230585"
---
<!-- docsTest:ignore CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template -->

# <a name="get-started-understand-and-document-foundational-alignment-decisions"></a>Bien démarrer : Identifier et documenter les décisions d'alignement de base

Le parcours d'adoption du cloud peut offrir de nombreux avantages commerciaux, techniques et organisationnels par le biais de différents parcours. Indépendamment de ce que vous souhaitez accomplir, si votre parcours implique le cloud, certaines décisions initiales doivent être comprises par les différentes équipes impliquées. À mesure que vous parcourez ce guide, notez ces décisions à l'aide du [modèle de décision initiale](https://raw.githubusercontent.com/microsoft/cloudadoptionframework/master/references/initial-decisions-checklist.docx) pour intégrer rapidement les membres de l'équipe qui participent au cycle de vie global de l'adoption du cloud.

> [!NOTE]
> En cliquant sur l'une des étapes ci-dessous, vous accéderez à la table des matières du Cloud Adoption Framework et aux concepts de base qui seront ultérieurement utilisés pour aider l'équipe à appliquer les conseils associés. Marquez cette page pour revenir souvent à cette check-list.

## <a name="step-1-understand-how-azure-works"></a>Étape 1 : Comprendre le fonctionnement d'Azure

Si vous avez choisi Azure comme fournisseur de cloud pour prendre en charge votre parcours d'adoption du cloud, il est important de comprendre [comment Azure fonctionne](./what-is-azure.md).

**Équipes impliquées, livrables et conseils de prise en charge :**

Une compréhension du fonctionnement de base d'Azure est indispensable pour toutes les personnes impliquées dans le cycle de vie de l'adoption du cloud.

## <a name="step-2-understand-initial-azure-concepts"></a>Étape 2 : Comprendre les concepts initiaux d'Azure

Azure repose sur un ensemble de [concepts de base](../ready/considerations/fundamental-concepts.md) qu'il est indispensable de connaître pour mener une conversation approfondie sur la stratégie technique, car elle est spécifiquement liée aux implémentations Azure.

**Équipes impliquées, livrables et conseils de prise en charge :**

Une compréhension des termes et définitions des concepts de base est indispensable pour toutes les personnes impliquées dans l'implémentation Azure de la stratégie technologique.

## <a name="step-3-review-the-portfolio"></a>Étape 3 : Examiner le portefeuille

Quel que soit le fournisseur de cloud choisi, toutes les décisions relatives à l'environnement et à l'hébergement dans le cloud reposent sur l'identification du portefeuille global de charges de travail. Le Cloud Adoption Framework comprend quelques outils d'identification et d'évaluation du portefeuille.

**Livrables :**

- Notez l'emplacement, l'état et la personne responsable de la documentation du portefeuille dans le [modèle de décision initiale](https://raw.githubusercontent.com/microsoft/cloudadoptionframework/master/references/initial-decisions-checklist.docx).

**Conseils relatifs aux livrables :**

- Les [concepts de base](../ready/considerations/fundamental-concepts.md) vous aident à appréhender les sujets clés d'Azure avant d'entamer votre adoption du cloud.
- Le [classeur de gestion des opérations](https://raw.githubusercontent.com/microsoft/cloudadoptionframework/master/manage/opsmanagementworkbook.xlsx) et l'approche d'alignement métier vous aident à identifier les charges de travail et les ressources qui ont été transférées à une équipe chargée des opérations cloud.
- Le [plan d'adoption du cloud](../plan/plan-intro.md) fournit un backlog des charges de travail et des ressources destinées à être adoptées dans le cloud.
- L'[analyse du patrimoine numérique](../digital-estate/approach.md) est une approche qui permet de documenter les charges de travail et les ressources existantes destinées à être adoptées dans le cloud. Dans Azure, le patrimoine numérique est particulièrement bien représenté dans un outil appelé [Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-support-matrix).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> Il incombe à l'équipe chargée de la stratégie cloud de définir un mode de visualisation du portefeuille. | <li> Plusieurs équipes utiliseront les conseils suivants pour créer ces vues. Toutes les personnes impliquées dans l'adoption du cloud devront savoir où trouver la vue du portefeuille pour étayer leurs décisions plus tard dans le processus. |

## <a name="step-4-define-portfolio-hierarchy-depth-to-align-the-portfolio"></a>Étape 4 : Définir la profondeur de la hiérarchie de portefeuille pour aligner le portefeuille

L'hébergement des ressources et des charges de travail dans le cloud peut être simple. Par exemple, une charge de travail et ses ressources de prise en charge. Pour d'autres clients, la stratégie d'adoption du cloud peut inclure des milliers de charges de travail et bien plus de ressources de prise en charge. La hiérarchie de portefeuille définit des noms communs pour chacun des niveaux hiérarchiques afin de créer un langage commun à l'organisation, quel que soit le fournisseur de cloud.

**Livrables :**

- Notez les besoins hiérarchiques pertinents dans le [modèle de décision initiale](https://raw.githubusercontent.com/microsoft/cloudadoptionframework/master/references/initial-decisions-checklist.docx).

**Conseils relatifs aux livrables :**

- Identifiez les niveaux de la [hiérarchie de portefeuille](../reference/fundamental-concepts/hosting-hierarchy.md) pour aligner les termes de base.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> L'équipe de gouvernance cloud est chargée de définir, d'appliquer et d'automatiser la hiérarchie de portefeuille afin de façonner la stratégie de l'entreprise dans le cloud. | <li> Toutes les personnes impliquées dans la stratégie technique d'adoption du cloud doivent connaître la hiérarchie de portefeuille et les niveaux hiérarchiques utilisés aujourd'hui. |

## <a name="step-5-establish-a-naming-and-tagging-standard-across-the-portfolio"></a>Étape 5 : Établir une norme de dénomination et d'étiquetage dans l'ensemble du portefeuille

Toutes les charges de travail et ressources existantes doivent être nommées et étiquetées conformément à la norme de dénomination et d'étiquetage. Ces normes doivent être documentées et disponibles comme référence pour tous les membres de l'équipe. Dans la mesure du possible, les normes doivent également être automatiquement appliquées pour garantir des exigences d'étiquetage minimales.

**Livrables :**

- Notez l'emplacement, l'état et la personne responsable du classeur des normes de dénomination et d'étiquetage dans le [modèle de décision initiale](https://raw.githubusercontent.com/microsoft/cloudadoptionframework/master/references/initial-decisions-checklist.docx).

**Conseils relatifs aux livrables :**

- Créez une [norme de dénomination et d'étiquetage](../ready/azure-best-practices/naming-and-tagging.md).
- Renseignez le [classeur de suivi des conventions de dénomination et d'étiquetage](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx) pour suivre les décisions.
- [Passez en revue et mettez à jour les étiquettes existantes dans Azure](https://docs.microsoft.com/azure/azure-resource-manager/management/tag-resources).
- [Appliquez des stratégies d'étiquetage dans Azure](https://docs.microsoft.com/azure/azure-resource-manager/management/tag-policies).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> L'équipe de gouvernance cloud est chargée de définir, d'appliquer et d'automatiser les normes de dénomination et d'étiquetage afin d'assurer la cohérence au sein du portefeuille. | <li> Toutes les personnes impliquées dans la stratégie technique d'adoption du cloud doivent connaître les normes de dénomination et d'étiquetage avant le déploiement dans le cloud. |

## <a name="step-6-create-a-resource-organization-design-to-implement-the-portfolio-hierarchy"></a>Étape 6 : Créer une conception d'organisation des ressources pour implémenter la hiérarchie de portefeuille

Pour assurer un alignement cohérent avec les décisions relatives à la hiérarchie de portefeuille, il est important de créer une conception pour l'organisation des ressources. Celle-ci alignera les outils organisationnels du fournisseur de cloud sur la hiérarchie de portefeuille requise pour prendre en charge votre plan d'adoption du cloud. Cette conception guidera l'implémentation en précisant quelles ressources peuvent être déployées dans des limites spécifiques au sein des environnements cloud.

**Livrables :**

- Mappez les produits Azure avec le niveau aligné de la hiérarchie de portefeuille dans le [modèle de décision initiale](https://raw.githubusercontent.com/microsoft/cloudadoptionframework/master/references/initial-decisions-checklist.docx).

**Conseils relatifs aux livrables :**

- Découvrez comment les [produits Azure prennent en charge la hiérarchie de portefeuille](../reference/fundamental-concepts/hierarchy-azure-tools.md).
- Passez en revue les abonnements existants pour les aligner sur la hiérarchie de portefeuille choisie.

Élaborez une stratégie d'abonnement :

- Commencez avec [deux abonnements par conception](../ready/azure-best-practices/initial-subscriptions.md).
  - Ajoutez des conceptions d'abonnement de base pour prendre en compte les besoins courants de l'entreprise, comme les services partagés ou les abonnements de type bac à sable.
- [Gérez les abonnements multiples](../ready/azure-best-practices/organize-subscriptions.md) car des abonnements supplémentaires sont nécessaires pour prendre en charge le plan d'adoption du cloud.
- Établissez des [limites claires basée sur la hiérarchie de portefeuille](../reference/fundamental-concepts/hierarchy-azure-tools.md#organizing-the-hierarchy-in-azure).
- Si nécessaire, [déplacez des ressources et groupes de ressources entre les abonnements](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription) pour respecter la stratégie de l'organisation.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> L'équipe de gouvernance cloud est chargée de définir, d'implémenter et d'automatiser la conception de l'organisation des ressources dans l'ensemble du portefeuille. | <li> Toutes les personnes impliquées dans la stratégie technique pour l'adoption du cloud doivent s'être familiarisées avec la conception de l'organisation des ressources avant le déploiement dans le cloud. |

## <a name="step-7-map-capabilities-teams-and-raci-to-fundamental-concepts"></a>Étape 7 : Adapter les capacités, les équipes et le modèle RACI aux concepts de base

La complexité de la hiérarchie de portefeuille permettra d'informer les structures organisationnelles et les méthodologies pour guider les activités quotidiennes des différentes équipes.

**Livrables :**

- Suivez les guides de prise en main pour un alignement organisationnel basé sur ces concepts de base.

<!-- docsTest:ignore Get Align -->

**Conseils relatifs aux livrables :**

- Utilisez les étapes précédentes comme guide pour évaluer les [conseils de responsabilité vis-à-vis de la hiérarchie de portefeuille](../reference/fundamental-concepts/hosting-hierarchy.md#hierarchy-accountability-and-guidance) afin de déterminer les capacités éventuelles à fournir par des organisations dédiées ou des équipes virtuelles.
- Utilisez [Bien démarrer : Aligner votre organisation](./org-alignment.md) pour appliquer les conseils de responsabilité vis-à-vis de la hiérarchie de portefeuille au diagramme RACI.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et équipes de soutien |
| --- | --- |
| <li> L'équipe chargée de la stratégie du cloud est responsable de l'alignement des structures organisationnelles virtuelles ou dédiées afin de garantir le succès du cycle de vie global de l'adoption du cloud. | <li> Toutes les personnes impliquées dans le cycle de vie de l'adoption du cloud doivent s'être familiarisées avec l'alignement des personnes et des niveaux de responsabilité. |

## <a name="whats-next"></a>Étapes suivantes

Tirez parti de cet ensemble de concepts de base grâce à la série de guides de prise en main de cette section du Cloud Adoption Framework.

> [!div class="nextstepaction"]
> [Appliquer les concepts de base à d'autres guides de prise en main](./index.md)
