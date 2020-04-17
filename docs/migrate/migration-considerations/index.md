---
title: Modèle de migration du Framework d’adoption du cloud
description: Modèle de migration du Framework d’adoption du cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d238918580c2db808a82c52d67d837a055c033e9
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80432579"
---
# <a name="cloud-adoption-framework-migration-model"></a>Modèle de migration du Framework d’adoption du cloud

Cette section du Framework d’adoption du cloud explique les principes qui sous-tendent son modèle de migration. Dans la mesure du possible, ce contenu tente de conserver une position indépendante du fournisseur tout en vous guidant à travers les processus et les activités qui peuvent s’appliquer à toute migration vers le cloud, quel que soit le fournisseur cloud choisi.

## <a name="understand-migration-motivations"></a>Comprendre les motivations de la migration

La migration vers le cloud est un effort de gestion de portefeuille qui est adroitement déguisé en implémentation technique. Au cours du processus de migration, vous décidez de déplacer certaines ressources, d’investir dans d’autres et de retirer des ressources obsolètes ou inutilisées. Certaines ressources sont optimisées, refactorisées ou entièrement remplacées dans le cadre de ce processus. Chacune de ces décisions doit correspondre aux motivations qui sous-tendent votre migration vers le cloud. Les migrations les plus réussies vont également plus loin et alignent ces décisions sur les résultats opérationnels souhaités.

Le modèle de migration Framework d’adoption du cloud dépend de l’organisation par votre entreprise d’un processus de préparation à l’adoption du cloud. Veillez à passer en revue les conseils associés aux étapes [Planifier](../../strategy/index.md) et [Préparer](../../ready/index.md) du Framework d’adoption du cloud pour déterminer les facteurs opérationnels ou toute autre justification d’une migration vers le cloud, ainsi que toutes les tâches de planification ou de formation organisationnelle requises avant l’exécution d’un processus de migration à grande échelle.

> [!NOTE]
> Si la planification des activités est importante, un état d’esprit axé sur la croissance l’est tout autant. Parallèlement aux efforts de planification des activités plus vastes entrepris par l’équipe de stratégie cloud, il est suggéré que l’équipe d’adoption du cloud migre une première charge de travail comme préalable à des activités de migration à plus grande échelle. Cette migration initiale permettra à l’équipe d’acquérir une expérience pratique des problèmes techniques et opérationnels liés à une migration.

## <a name="envision-an-end-state"></a>Prévoir un état final

Il est important de vous faire une idée approximative de l’état final avant de commencer vos efforts de migration. Le diagramme ci-dessous montre un point de départ local de l’infrastructure, des applications et des données qui définissent votre *patrimoine numérique*. Au cours du processus de migration, ces ressources sont transférées au moyen de l’une des cinq stratégies de migration décrites dans [Les cinq R de la rationalisation](../../digital-estate/5-rs-of-rationalization.md).

![Infographie des options de migration](../../_images/migrate/migration-options.png)

Les efforts entrepris pour migrer et moderniser les charges de travail varient selon l’approche choisie. Ainsi, les migrations de _réhébergement_ (également appelé _lift and shift_) utilisent simplement des fonctionnalités IaaS (infrastructure as a service) ne nécessitant aucun changement au niveau du code et des applications. En revanche, la _refactorisation_ nécessite quelques changements minimes, tandis que la _réarchitecture_ exige la modification et l’extension du code et des fonctionnalités des applications afin de tirer parti des technologies cloud.

Les stratégies natives dans le cloud et les stratégies PaaS (platform as a service) *reconstruisent* des charges de travail locales à l’aide des offres de plateforme locales et de services gérés Azure. Les charges de travail ayant des offres équivalentes basées sur le cloud SaaS (software as a service) et entièrement gérées peuvent souvent être entièrement *remplacées* par ces services dans le cadre du processus de migration.

> [!NOTE]
> Durant la présentation publique du Framework d’adoption du cloud, cette section du framework met l’accent sur une stratégie de migration de réhébergement. Bien que les solutions PaaS et SaaS soient envisagées comme alternatives au besoin, la migration des charges de travail basées sur des machines virtuelles à l’aide de fonctionnalités IaaS constitue l’objectif premier.
>
> À l’avenir, d’autres sections et itérations de ce contenu développeront d’autres approches. Pour accéder à une discussion générale sur l’élargissement de l’étendue de votre migration afin d’inclure des stratégies de migration plus complexes, consultez l’article sur l’équilibrage du portefeuille.

## <a name="incremental-migration"></a>Migration incrémentielle

Le modèle de migration du Framework d’adoption du cloud est basé sur un processus de transformation incrémentielle dans le cloud. Il suppose que votre organisation commence par un effort initial de migration vers le cloud, à étendue limitée, que nous appelons communément la première charge de travail. Cet effort est étendu de manière itérative pour inclure davantage de charges de travail à mesure que vos équipes des opérations affinent et améliorent vos processus de migration.

Des outils de migration vers le cloud, comme [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview), peuvent migrer des centres de données entiers comprenant des dizaines de milliers de machines virtuelles. Toutefois, les activités commerciales et informatiques existantes peuvent rarement gérer un rythme de changement si soutenu. De nombreuses organisations divisent donc l’effort de migration en plusieurs itérations, chaque itération étant l’objet d’un déplacement d’une charge de travail (ou d’une collection de charges de travail).

Les principes sous-jacents à ce modèle incrémentiel sont basés sur l’exécution de processus et de prérequis référencés dans l’infographie suivante.

![Modèle de migration du Framework d’adoption du cloud](../../_images/migrate/methodology.png)

L’application cohérente de ces principes représente un objectif final pour vos processus de migration vers le cloud. Il ne s’agit en aucun cas d’un point de départ requis. À mesure que vos efforts de migration arrivent à maturité, reportez-vous aux instructions fournies dans cette section pour définir le processus le mieux adapté aux besoins de votre organisation.

## <a name="next-steps"></a>Étapes suivantes

Examinez les [prérequis pour la migration](./prerequisites/index.md) pour commencer à vous familiariser avec ce modèle.

> [!div class="nextstepaction"]
> [Prérequis pour la migration](./prerequisites/index.md)
