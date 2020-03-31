---
title: Introduction au guide de migration Azure
description: Utilisez le Framework d’adoption du cloud pour Azure pour découvrir comment migrer efficacement les services de votre organisation.
author: matticusau
ms.author: mlavery
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: e0cb1779836edce3571a081ae44794aeb8bc06b8
ms.sourcegitcommit: afe10f97fc0e0402a881fdfa55dadebd3aca75ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80432981"
---
# <a name="azure-migration-guide-before-you-start"></a>Guide de migration Azure : Avant de commencer

La [méthodologie Migrer dans le Framework d’adoption du cloud](../index.md) guide les lecteurs à travers un processus itératif permettant de migrer une seule charge de travail ou bien un petit ensemble de charges de travail par mise en production. Dans chaque itération, le processus Évaluer, Migrer, Optimiser et Promouvoir garantit que les charges de travail sont prêtes pour prendre en charge les demandes en production. Ce processus indépendant du cloud peut donc guider la migration vers n’importe quel fournisseur de cloud.

Le présent guide expose une version simplifiée de ce processus dans le contexte de la migration de votre environnement local vers **Azure**.

::: zone target="docs"

> [!TIP]
> Pour une expérience interactive, consultez ce guide dans le portail Azure. Accédez au [centre des guides de démarrage rapide Azure](https://portal.azure.com/?feature.quickstart=true#blade/Microsoft_Azure_Resources/QuickstartCenterBlade) dans le portail Azure, sélectionnez **Migrer votre environnement vers Azure** et suivez les instructions pas à pas.

::: zone-end

## <a name="migration-tools"></a>[Outils de migration](#tab/MigrationTools)

Ce guide est le chemin suggéré pour réaliser votre première migration vers Azure, car il vous montre la méthodologie et les outils cloud natifs les plus couramment employés durant une migration vers Azure. Ces outils sont présentés dans les pages suivantes :

> [!div class="checklist"]
>
> - **Évaluer l’adéquation technique de chaque charge de travail.** Validez la préparation technique et la capacité d’adaptation à la migration.
> - **Migrer vos services.** Procédez à la migration en répliquant les ressources locales sur Azure.
> - **Gérer les coûts et la facturation.** Apprenez à utiliser les outils nécessaires au contrôle des coûts dans Azure.
> - **Optimiser et promouvoir.** Optimisez les coûts par rapport aux performances avant de promouvoir votre charge de travail en production.
> - **Obtenir de l’aide.** Obtenez de l’aide et un support pendant les activités de votre migration ou post-migration.

Il est supposé qu’une zone d’accueil a déjà été déployée, en adéquation avec les bonnes pratiques indiquées dans la [méthodologie Préparer du Framework d’adoption du cloud](../../ready/index.md).

## <a name="when-to-use-this-guide"></a>[Quand utiliser ce guide](#tab/WhenToUseThisGuide)

Bien que les outils abordés dans ce guide prennent en charge un large éventail de scénarios de migration, ce guide se limite à un cadre d’une _complexité minimale_. Pour savoir si ce guide de migration est adapté à votre projet, déterminez si les conditions suivantes s’appliquent à votre situation :

- Les charges de travail prévues dans la migration initiale ne sont pas critiques et ne contiennent pas de données sensibles.
- Vous migrez un environnement homogène.
- Seules quelques divisions doivent être alignées pour effectuer la migration.
- Vous n’envisagez pas d’automatiser la migration entière.
- Vous migrez un petit nombre de serveurs.
- Le mappage des dépendances des composants à migrer est simple à définir.
- Votre secteur d’activité a une réglementation minimale pour cette migration.

Si l’une de ces conditions ne s’applique pas à votre situation, tournez-vous plutôt vers le [guide pour un cadre étendu](../expanded-scope/index.md). Nous vous recommandons également de demander une assistance auprès d’une de nos équipes ou d’un de nos partenaires Microsoft pour effectuer des migrations nécessitant le guide pour un cadre étendu. Les clients qui sont engagés avec Microsoft ou des partenaires certifiés réussissent mieux dans ces scénarios. Vous trouverez plus d’informations sur la demande d’assistance dans ce guide.

<!-- markdownlint-enable MD033 -->

::: zone target="docs"

Pour plus d'informations, consultez les pages suivantes :

- [Guide pour un cadre étendu](../expanded-scope/index.md)

::: zone-end
