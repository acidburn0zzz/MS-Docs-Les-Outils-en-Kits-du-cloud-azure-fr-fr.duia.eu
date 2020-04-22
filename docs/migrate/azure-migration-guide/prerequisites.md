---
title: Prérequis pour migrer vers Azure
description: Utilisez le Cloud Adoption Framework pour Azure afin de comprendre comment vous préparer à la migration Azure et quels sont les prérequis nécessaires à la réussite d’un projet de migration.
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: a1c100c4c3c9a960867f0666853df742ecf68c3d
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80997585"
---
::: zone target="docs"

# <a name="prerequisites-for-migrating-to-azure"></a>Prérequis pour migrer vers Azure

::: zone-end

::: zone target="chromeless"

# <a name="prerequisites"></a>Prérequis

::: zone-end

Les ressources de cette section vous aideront à préparer votre environnement actuel pour la migration vers Azure.

# <a name="overview"></a>[Vue d'ensemble](#tab/Overview)

Les raisons d’une migration vers Azure incluent la suppression des risques associés au matériel hérité, la réduction des dépenses d’investissement, la libération d’espace dans un centre de données et la réalisation rapide du retour sur investissement (ROI).

- **Éliminer le matériel hérité.** Vous pouvez avoir des applications hébergées sur une infrastructure proche de la fin de son cycle de vie ou de sa prise en charge, que ce soit localement ou chez un fournisseur d’hébergement. La migration vers le cloud offre une solution intéressante à ce défi, car la possibilité de migrer « en l’état » permet à l’équipe de résoudre rapidement le défi actuel posé par le cycle de vie de l’infrastructure, puis de se concentrer sur une planification à long terme du cycle de vie des applications et l’optimisation dans le cloud.
- **Résoudre la fin de prise en charge pour les logiciels.** Vous pouvez avoir des applications qui dépendent d’autres logiciels ou systèmes d’exploitation proches de la fin de leur prise en charge. La migration vers Azure peut fournir des options de support étendu pour ces dépendances ou d’autres options de migration qui réduisent les besoins de refactorisation pour prendre en charge vos applications à l’avenir. Par exemple, consultez [Options de support étendu pour Windows Server 2008 et SQL Server 2008](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support).
- **Réduire les dépenses d’investissement.** L’hébergement de votre propre infrastructure de serveur nécessite un investissement considérable en matériel, logiciel, électricité et personnel. La migration vers une solution cloud permet de réduire considérablement les dépenses d’investissement. Pour obtenir les meilleures réductions en la matière, il peut être nécessaire de reconcevoir la solution. Toutefois, une migration « en l’état » est une bonne première étape.
- **Libérer de l’espace dans un centre de données.** Vous pouvez choisir Azure pour développer la capacité de votre centre de données. Pour ce faire, vous pouvez utiliser le cloud en tant qu’extension de vos fonctionnalités locales.
- **Réaliser rapidement un retour sur investissement.** Le retour sur investissement (ROI) est beaucoup plus facile avec les solutions cloud, car le modèle de paiement cloud offre une excellente compréhension de l’utilisation et encourage une culture de réalisation du ROI.

Chacun des scénarios ci-dessus peut être des points d’entrée pour étendre votre empreinte cloud à l’aide d’une autre méthodologie (réhébergement, refactorisation, réarchitecture, régénération ou remplacement).

## <a name="migration-characteristics"></a>Caractéristiques de la migration

Ce guide part du principe que, avant la migration, votre patrimoine numérique est constitué principalement d’une infrastructure hébergée localement et peut inclure des applications hébergées vitales pour l’entreprise. Après une migration réussie, votre patrimoine de données peut ressembler beaucoup à ce qu’il était en local, mais avec l’infrastructure hébergée dans les ressources cloud. À l’inverse, le patrimoine de données idéal est une variante de votre patrimoine de données actuel, car il comporte des aspects de votre infrastructure locale avec des composants qui ont été refactorisés pour optimiser la plateforme cloud et en tirer parti.

L’objectif de ce parcours de migration est d’atteindre les objectifs suivants :

- Correction de la fin de vie du matériel hérité.
- Réduction des dépenses d’investissement.
- Retour sur investissement.

> [!NOTE]
> Un autre avantage de cette migration est le modèle de prise en charge logicielle supplémentaire pour Windows 2008, Windows 2008 R2, SQL Server 2008 et SQL Server 2008 R2. Pour plus d'informations, consultez les pages suivantes :
>
> - [Windows Server 2008 et Windows Server 2008 R2](https://www.microsoft.com/cloud-platform/windows-server-2008).
> - [SQL Server 2008 et SQL Server 2008 R2](https://www.microsoft.com/sql-server/sql-server-2008).

# <a name="understand-migration-approaches"></a>[Comprendre les approches de migration](#tab/Approach)

La stratégie et les outils que vous utilisez pour migrer une application vers Azure dépendent en grande partie de vos motivations métier, exigences technologiques et chronologies. Ils nécessitent également une compréhension approfondie de la charge de travail et des ressources (infrastructure, applications et données) réelles en cours de migration.

Avant de déterminer votre stratégie de migration cloud, analysez les applications candidates pour identifier leur compatibilité avec les technologies d’hébergement cloud. Utilisez le [guide de décision sur les outils de migration](../../decision-guides/migrate-decision-guide/index.md) du Framework d’adoption du cloud pour vous aider à prendre en main ce processus.

Une migration axée sur IaaS, où les serveurs (avec leurs applications et données associées) sont réhébergés dans le cloud à l’aide de machines virtuelles, est souvent l’approche la plus simple pour déplacer des charges de travail vers le cloud. Cependant, pensez que la configuration, la sécurisation et la gestion correctes des machines virtuelles peut nécessiter plus de temps et d’expertise informatique que l’utilisation de services PaaS dans Azure. Si vous envisagez d’utiliser Machines virtuelles Microsoft Azure, tenez bien compte de l’effort de maintenance continue nécessaire pour corriger, mettre à jour et gérer votre environnement de machine virtuelle.

Lors de l’évaluation des charges de travail pour la migration, identifiez les applications qui ne nécessitent pas de modification importante pour s’exécuter à l’aide de technologies PaaS, telles qu’Azure App Service, ou d’orchestrateurs tels qu’Azure Kubernetes Service. Ces applications doivent être les premières candidates à la modernisation et à l’optimisation du cloud.

## <a name="learn-more"></a>En savoir plus

- [Guide de décision sur les outils de migration du Framework d’adoption du cloud](../../decision-guides/migrate-decision-guide/index.md)
- [Les 5 R de la rationalisation](../../digital-estate/5-rs-of-rationalization.md)

# <a name="planning-checklist"></a>[Check-list de planification](#tab/Checklist)

Avant de commencer une migration, vous devez remplir certains prérequis. Les détails exacts de ces activités varient en fonction de l’environnement en cours de migration. En règle générale, la check-list suivante s’applique :

> [!div class="checklist"]
>
> - **Identifier les parties prenantes :** Identifiez les personnes clés qui ont un rôle à jouer ou un intérêt dans le résultat de la migration.
> - **Identifier les jalons clés :** Pour planifier efficacement les chronologies de migration, identifiez les jalons clés à respecter.
> - **Identifier la stratégie de migration :** Déterminez lequel des 5 R de la rationalisation vous allez utiliser.
> - **Évaluer votre ajustement technique :** Validez la préparation technique et l’adéquation à la migration, et déterminez le niveau d’assistance dont vous pourriez avoir besoin de la part des partenaires externes ou du support Azure.
> - **Planification de la migration :** Effectuez l’évaluation et la planification détaillées nécessaires à la préparation de vos ressources (infrastructure, applications et données), ainsi que de l’infrastructure Azure pour la migration.
> - **Tester votre migration :** Validez votre plan de migration en effectuant une migration de test à portée limitée.
> - **Migrer vos services :** Effectuez la bonne migration.
> - **Après la migration :** Comprenez ce qui est requis après la migration de votre environnement vers Azure.

En supposant que vous choisissiez une approche de réhébergement pour la migration, les activités suivantes sont également pertinentes :

> [!div class="checklist"]
>
> - **Alignement de la gouvernance :** Un consensus a-t-il été atteint en ce qui concerne l’alignement de la gouvernance avec la base de la migration ?
> - **Réseau :** Une stratégie de réseau doit être sélectionnée et alignée sur les exigences de sécurité informatique.
> - **Identité :** Une stratégie d’identité hybride doit être alignée pour s’adapter au plan de gestion des identités et d’adoption du cloud.

::: zone target="docs"

<!-- markdownlint-disable MD024 -->

## <a name="learn-more"></a>En savoir plus

- [Les 5 R de la rationalisation](../../digital-estate/5-rs-of-rationalization.md)
- [Guide de décision sur les outils de migration](../../decision-guides/migrate-decision-guide/index.md)
- [Check-list de planification du Framework d’adoption du cloud](../migration-considerations/prerequisites/planning-checklist.md)

::: zone-end
