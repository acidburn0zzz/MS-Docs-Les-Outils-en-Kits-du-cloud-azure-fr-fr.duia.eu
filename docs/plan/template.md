---
title: Déployer le plan d’adoption du cloud dans Azure DevOps
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Déployer le modèle de plan d’adoption du cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 91c1433f300efc3950cb54852a00b5020a992e8f
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70839159"
---
# <a name="cloud-adoption-plan-and-azure-devops"></a>Plan d’adoption du cloud et Azure DevOps

Azure DevOps est l’ensemble des outils basés sur le cloud pour les clients Azure qui gèrent des projets itératifs. Il comprend également des outils permettant de gérer les pipelines de déploiement et d’autres aspects importants de DevOps. 

Dans cet article, vous allez apprendre à déployer rapidement un backlog sur Azure DevOps en utilisant un modèle de plan d’adoption du cloud. Ce modèle aligne les efforts d’adoption du cloud sur un processus standardisé basé sur les recommandations fournies dans le Framework d’adoption du cloud.

## <a name="create-your-cloud-adoption-plan"></a>Créer votre plan d’adoption du cloud

Pour déployer le plan d’adoption du cloud, ouvrez [Azure DevOps Demo Generator](https://aka.ms/adopt/plan/generator). Cet outil déploie le modèle sur votre locataire Azure DevOps. L’utilisation de cet outil nécessite les étapes suivantes :

1. Vérifiez que le champ **Modèle sélectionné** est défini sur **Plan d’adoption du cloud**. Si ce n’est pas le cas, sélectionnez **Choisir un modèle** pour choisir le modèle approprié.
2. Sélectionnez votre organisation Azure DevOps dans la zone de liste déroulante **Sélectionner une organisation**.
3. Entrez un nom pour votre nouveau projet. Le plan d’adoption du cloud aura ce nom lorsqu’il sera déployé sur votre locataire Azure DevOps.
4. Sélectionnez **Créer un projet** pour créer un projet sur votre locataire, en fonction du modèle de plan. Une barre de progression affiche la progression vers le déploiement du projet.
5. Une fois le déploiement terminé, sélectionnez **Accéder au projet** pour afficher votre nouveau projet.

Une fois que votre projet a été créé, poursuivez la lecture de cette série d’articles pour voir comment modifier le modèle pour l’aligner sur votre plan d’adoption du cloud.

Pour obtenir de l’aide et des conseils supplémentaires sur cet outil, consultez [Azure DevOps Services Demo Generator](https://docs.microsoft.com/azure/devops/demo-gen/?toc=%2Fazure%2Fdevops%2Fdemo-gen%2Ftoc.json&bc=%2Fazure%2Fdevops%2Fdemo-gen%2Fbreadcrumb%2Ftoc.json&view=azure-devops).

## <a name="bulk-edit-the-cloud-adoption-plan"></a>Modifier en bloc le plan d’adoption du cloud

Une fois le projet de plan déployé, vous pouvez utiliser Microsoft Excel pour le modifier. Il est beaucoup plus facile de créer des charges de travail ou des ressources dans le plan en utilisant Excel qu’en utilisant le navigateur Azure DevOps.

Pour préparer votre station de travail pour des modifications en bloc, consultez [Ajouter ou modifier en bloc des éléments de travail avec Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="use-the-cloud-adoption-plan"></a>Utiliser le plan d’adoption du cloud

Le plan d’adoption du cloud organise les activités par type d’activité :

- **Épopées** : Une *épopée* représente une phase globale du cycle de vie d’adoption du cloud.
- **Fonctionnalités** : Les fonctionnalités permettent d’organiser des objectifs spécifiques au sein de chaque phase. Par exemple, la migration d’une charge de travail spécifique est une fonctionnalité.
- **Récits utilisateur** : Les récits utilisateur regroupent le travail en collections logiques d’activités basées sur un objectif spécifique.
- **Tâches** : Les tâches correspondent au véritable travail à effectuer.

Sur chaque couche, les activités sont ensuite séquencées en fonction des dépendances. Les activités sont liées à des articles fournis dans le Framework d’adoption du cloud pour clarifier l’objectif ou la tâche en cours.

La vue la plus claire du plan d’adoption du cloud provient de la vue du backlog **Épopées**. Pour obtenir de l’aide afin d’accéder à la vue du backlog **Épopées**, consultez l'article sur l’[affichage d’un backlog](https://docs.microsoft.com/azure/devops/boards/backlogs/define-features-epics?view=azure-devops#view-a-backlog-or-portfolio-backlog). Dans cette vue, il est facile de planifier et de gérer le travail requis pour effectuer la phase actuelle du cycle de vie d’adoption.

> [!NOTE]
> L’état actuel du plan d’adoption du cloud porte essentiellement sur les efforts de migration. Les tâches liées à la gouvernance, à l’innovation et aux opérations doivent être renseignées manuellement.

## <a name="align-the-cloud-adoption-plan"></a>Aligner le plan d’adoption du cloud

Les pages de présentation des phases de planification et de stratégie du cycle de vie d’adoption du cloud font toutes référence au document [Cloud Adoption Framework strategy and planning template](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) (Modèle de planification et de stratégie du Framework d’adoption du cloud). Ce modèle organise les décisions et les points de données qui aligneront le modèle de plan d’adoption du cloud avec vos plans spécifiques d’adoption. Si vous ne l’avez pas déjà fait, vous souhaiterez peut-être effectuer les exercices relatifs à la [stratégie](../business-strategy/index.md) et à la [planification](../plan/index.md) avant d’aligner votre nouveau projet.

Les articles suivants prennent en charge l’alignement du plan d’adoption du cloud :

- [Charges de travail](./workloads.md) : Alignez les fonctionnalités dans l’épopée de migration cloud pour capturer chaque charge de travail à migrer ou à moderniser. Ajoutez et modifiez ces fonctionnalités pour capturer l’effort de migration de vos 10 charges de travail les plus importantes.
- [Ressources](./assets.md) : Chaque ressource (machine virtuelle, application ou données) est représentée par les récits utilisateur sous chaque charge de travail. Ajoutez et modifiez ces récits utilisateur pour les aligner sur votre patrimoine numérique.
- [Rationalisation](./review-rationalization.md) : À mesure que les charges de travail sont définies, les hypothèses initiales relatives à chaque charge de travail peuvent être testées. Cela peut entraîner des modifications des tâches sous chaque ressource.
- [Créer des plans de publication de versions](./iteration-paths.md) : Les chemins d’itération établissent des plans de publication de versions en alignant les efforts avec différentes versions et itérations.
- [Établir des chronologies](./timelines.md) : La définition de dates de début et de fin pour chaque itération crée une chronologie pour gérer le projet global.

Ces cinq articles vous aident pour chacune des tâches d’alignement requises à commencer à gérer vos efforts d’adoption. L’étape suivante vous place dans le contexte d’un exercice d’alignement.

## <a name="next-steps"></a>Étapes suivantes

Commencez à aligner votre projet de plan en [définissant et hiérarchisant les charges de travail](./workloads.md).

> [!div class="nextstepaction"]
> [Définir et hiérarchiser les charges de travail](./workloads.md)
