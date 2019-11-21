---
title: Introduction au guide de migration Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment migrer efficacement les services de votre organisation vers Azure en suivant des instructions pas à pas.
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 9f27c7fca9a9a5bd2f5c38f78b8db2092b24d014
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251482"
---
::: zone target="docs"

# <a name="azure-migration-guide-before-you-start"></a>Guide de migration Azure : Avant de commencer

::: zone-end

::: zone target="chromeless"

# <a name="before-you-start"></a>Avant de commencer

::: zone-end

Avant de migrer des ressources vers Azure, vous devez choisir la méthode de migration et les fonctionnalités que vous allez utiliser pour gouverner et sécuriser votre environnement. Ce guide vous accompagne tout au long de ce processus de décision.

::: zone target="docs"

> [!TIP]
> Pour une expérience interactive, consultez ce guide dans le portail Azure. Accédez au [centre des guides de démarrage rapide Azure](https://portal.azure.com/?feature.quickstart=true#blade/Microsoft_Azure_Resources/QuickstartCenterBlade) dans le portail Azure, sélectionnez **Migrer votre environnement vers Azure** et suivez les instructions pas à pas.

::: zone-end

# <a name="overviewtaboverview"></a>[Vue d'ensemble](#tab/Overview)

Ce guide vous explique les bases de la migration des applications et des ressources de votre environnement local vers Azure. Il est conçu pour les étendues de migration avec une complexité minimale. Pour savoir si ce guide est adapté à votre migration, consultez l’onglet **Quand utiliser ce guide**.

Lorsque vous migrez vers Azure, vous pouvez migrer vos applications telles quelles à l’aide de solutions de machine virtuelle IaaS (connues sous le nom de migration de _réhébergement_ ou _lift-and-shift_), ou utiliser des services managés et autres fonctionnalités cloud natives pour moderniser vos applications. Pour plus d’informations sur le choix à faire, consultez **Options de migration**. Lorsque vous développez votre stratégie de migration, vous pouvez vous poser les questions suivantes :

- Mes applications à migrer vont-elles fonctionner dans le cloud ?
- Quelle est la meilleure stratégie (technologie, outils et migrations) pour mon application ? Pour plus d’informations, consultez le [guide de décision des outils de migration](../../decision-guides/migrate-decision-guide/index.md) du Framework d’adoption du cloud.
- Comment minimiser les temps d’arrêt pendant la migration ?
- Comment contrôler les coûts ?
- Comment suivre les coûts des ressources et les facturer sans faire d’erreur ?
- Comment m’assurer que nous restons conformes et respectons la réglementation ?
- Comment respecter les obligations légales en matière de souveraineté des données dans certains pays ?

Ce guide vous aide à répondre à ces questions. Il suggère les tâches et les fonctionnalités à prendre en compte lorsque vous vous préparez à déployer des ressources dans Azure, notamment :

> [!div class="checklist"]
>
> - **Configurer les prérequis.** Planifiez et préparez la migration.
> - **Évaluer votre équipement technique.** Validez la préparation technique et la capacité d’adaptation à la migration.
> - **Gérer les coûts et la facturation.** Examinez les coûts de vos ressources.
> - **Migrer vos services.** Effectuez la bonne migration.
> - **Organiser vos ressources.** Verrouillez les ressources critiques à votre système et identifiez les ressources pour en assurer le suivi.
> - **Optimiser et transformer.** Profitez de la post-migration pour passer en revue vos ressources.
> - **Sécuriser et gérer.** Vérifiez que votre environnement est sécurisé et correctement supervisé.
> - **Obtenir de l’aide.** Obtenez de l’aide et un support pendant les activités de votre migration ou post-migration.

::: zone target="docs"

Pour en savoir plus sur l’organisation et la structuration de vos abonnements, la gestion de vos ressources déployées et la conformité aux conditions de votre stratégie d’entreprise, consultez [Gouvernance dans Azure](https://docs.microsoft.com/azure/security/governance-in-azure).

::: zone-end

# <a name="when-to-use-this-guidetabwhentousethisguide"></a>[Quand utiliser ce guide](#tab/WhenToUseThisGuide)

Bien que les outils abordés dans ce guide prennent en charge un large éventail de scénarios de migration, ce guide se limite à un cadre d’une _complexité minimale_. Pour déterminer si ce guide de migration est adapté à votre projet, déterminez si les conditions suivantes s’appliquent à vous :

- Vous migrez un environnement homogène.
- Seules quelques divisions doivent être alignées pour effectuer la migration.
- Vous n’envisagez pas d’automatiser la migration entière.
- Vous migrez un petit nombre de serveurs.
- Le mappage des dépendances des composants à migrer est simple à définir.
- Votre secteur d’activité a une réglementation minimale pour cette migration.

Si l’une de ces conditions ne s’applique _pas_ à votre cas, tournez-vous plutôt vers le [guide pour un cadre étendu](../expanded-scope/index.md). Nous vous recommandons également de demander une assistance auprès d’une de nos équipes ou d’un de nos partenaires Microsoft pour effectuer des migrations nécessitant le guide pour un cadre étendu. Les clients qui sont engagés avec Microsoft ou des partenaires certifiés réussissent mieux dans ces scénarios. Vous trouverez plus d’informations sur la demande d’assistance dans ce guide.

<!-- markdownlint-enable MD033 -->

::: zone target="docs"

Pour plus d'informations, consultez les pages suivantes :

- [Guide pour un cadre étendu](../expanded-scope/index.md)

::: zone-end

# <a name="migration-optionstabmigrationoptions"></a>[Options de migration](#tab/MigrationOptions)

Vous pouvez effectuer une migration vers le cloud de plusieurs façons. Certaines sont mieux adaptées aux différents scénarios que d’autres. Lorsque vous déterminez comment migrer votre environnement, envisagez les options suivantes lors du choix d’une stratégie de migration :

- **Réhébergement :** Également appelé « lift-and-shift », le réhébergement déplace l’état actuel vers Azure en changeant très peu l’architecture globale.
- **Refactorisation :** Les options PaaS (Platform as a service) permettent de réduire les coûts d’exploitation associés à de nombreuses applications. Il peut être plus prudent de refactoriser légèrement une application pour qu’elle corresponde à un modèle PaaS. La refactorisation s’applique également au processus de développement d’applications, dans lequel du code est refactorisé pour permettre à une application de répondre à de nouvelles opportunités commerciales.
- **Réarchitecture :** Certaines applications vieillissantes ne sont pas compatibles avec les fournisseurs de cloud, en raison des décisions qui ont été prises concernant l’architecture lors de la conception de l’application. Dans ce cas, l’application aura peut-être besoin d’être réarchitecturée dans le cadre de la migration.
- **Regénération :** Dans certains scénarios, les changements nécessaires pour migrer une application peuvent être trop importants pour justifier un plus grand investissement, et la solution doit être regénérée.
- **Remplacement :** Les solutions sont généralement implémentées à l’aide de la technologie et des techniques les mieux adaptées sur le moment. Dans certains cas, les applications SaaS (software as a service) modernes peuvent fournir toutes les fonctionnalités fournies par l’application hébergée. Dans ces scénarios, une charge de travail peut avoir été planifiée pour un futur remplacement, qui du coup peut être ignorée dans le cadre de la migration.

::: zone target="chromeless"

Ces méthodes ne s’excluent pas mutuellement&mdash;par exemple, alors que la migration peut à la base utiliser un modèle de **réhébergement**, vous pouvez choisir d’implémenter une **refactorisation** ou une **réarchitecture** dans le cadre de la phase d’optimisation post-migration. Ce point est traité dans la section **Optimiser et transformer** de ce guide.

::: zone-end

::: zone target="docs"

Ces méthodes ne s’excluent pas mutuellement&mdash;par exemple, alors que la migration peut à la base utiliser un modèle de **réhébergement**, vous pouvez choisir d’implémenter une **refactorisation** ou une **réarchitecture** dans le cadre de la phase d’optimisation post-migration. Ce point est traité dans la section [Optimiser et transformer](./optimize-and-transform.md) de ce guide.

::: zone-end

![Infographie des options de migration](../../_images/migrate/migration-options.png)
