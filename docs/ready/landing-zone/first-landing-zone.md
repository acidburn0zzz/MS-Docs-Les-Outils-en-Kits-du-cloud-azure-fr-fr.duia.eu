---
title: Considérations relatives aux zones d’accueil Azure
description: Découvrez en quoi les zones d’accueil constituent les éléments constitutifs de tout environnement d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 594f10968e45477895fcc5dcd1b2a95d16d7c861
ms.sourcegitcommit: 1a4b140f09bdaa141037c54a4a3b5577cda269db
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80392650"
---
# <a name="first-landing-zone"></a>Première zone d’accueil

L’infrastructure as code (IaC) est une transition naturelle durant la plupart des opérations d’adoption du cloud. Le déploiement de vos premières zones d’atterrissage dans le cloud est généralement la première étape du passage à un environnement basé sur le code. Cet article vous aidera à comprendre la notion de _zone d’atterrissage_ et à déterminer laquelle de ces zones est la mieux adaptée à vos besoins d’adoption.

## <a name="code-first-approach-to-landing-zones"></a>Méthode Code First pour les zones d’atterrissage

L’image suivante montre diverses options relatives aux zones d’atterrissage. Les options suivantes vous aideront à sélectionner une zone d’atterrissage adaptée dès aujourd’hui. Elles permettent également de prévoir vos futurs besoins concernant les zones d’atterrissage.

![Options des zones d’atterrissage](../../_images/ready/landing-zone-options.png)

R. Commencez par du code permettant de produire des zones d’atterrissage cohérentes et reproductibles. Si vous êtes à l’aise avec la refactorisation (ou l’affinage du code et de l’infrastructure) pendant votre apprentissage, commencez par une base de code légère, telle que le blueprint de zone d’atterrissage de migration Cloud Adoption Framework. Cette méthode accélère l’adoption et crée des opportunités d’apprentissage pratique. Toutefois, ce type de zone d’atterrissage initiale ne peut pas être utilisé pour les données sensibles ou les charges de travail stratégiques sans une refactorisation supplémentaire.

B. À mesure que l’adoption grandit et que les exigences sont plus clairement identifiées, les équipes chargées de l’adoption et des plateformes refactorisent les zones d’atterrissage en fonction de ce qu’elles apprennent. Le processus d’extension de vos zones d’atterrissage prépare les environnements à des exigences de conformité ou d’architecture plus complexes. L’article [Étendre la zone d’atterrissage](../considerations/index.md) fournit des guides de décision et des liens vers de bonnes pratiques pour vous guider dans vos efforts de refactorisation. L’extension de la zone d’atterrissage peut contribuer au respect des exigences concernant la sécurité, les opérations et la gouvernance.

C. Certains plans d’adoption du cloud sont régis par des exigences de conformité externes. Azure fournit quelques exemples de blueprints Azure qui vous permettront de répondre plus facilement à ces exigences. Certains de ces exemples peuvent être ajoutés à votre blueprint initial. D’autres exemples ont également une implémentation spécifique qui peut servir de première zone d’atterrissage.

D. Quand un partenaire fournit des services gérés continus ou s’il s’est engagé par contrat à fournir le plan d’adoption, il fournit généralement sa propre zone d’atterrissage. L’utilisation de la zone d’atterrissage d’un partenaire peut accélérer les efforts d’adoption et garantir la cohérence des exigences de gestion opérationnelle. Toutefois, pour garantir l’alignement, vous devez tenir compte de la gouvernance interne et des exigences de sécurité.

> [!NOTE]
> Avant de passer à une approche basée sur le code et la refactorisation, les lecteurs doivent se familiariser avec les [priorités en concurrence derrière cette décision](../../strategy/balance-competing-priorities.md#balance-during-ready). Quand vous choisissez une approche de zone d’atterrissage, vous devez bien comprendre l’équilibre nécessaire entre « Délai d’adoption » et « Opérations à long terme ».

## <a name="choosing-a-first-landing-zone"></a>Choix d’une première zone d’atterrissage

La sélection de la première zone d’atterrissage dépend d’un certain nombre de variables. Le tableau suivant comprend certaines options concernant les premières zones d’atterrissage, ainsi que des variables qui peuvent aider à la prise de décision.

| Zone d’atterrissage                                 | Expérience cloud  | Scale             | Heure de découverte | Prêt pour la production | Hybride             | Données sensibles     | Stratégique   | Conformité         |
|----------------------------------------------|-------------------|-------------------|----------------|------------------|--------------------|--------------------|--------------------|--------------------|
| [CAF Migrate](./migrate-landing-zone.md)     | Nouveau dans le cloud      | < 1 000 ressources    | 1 à 5 jours    | Étendue limitée -> | Extension nécessaire | Extension nécessaire | Extension nécessaire | Extension nécessaire |
| [CAF Terraform](./terraform-landing-zone.md) | Divers modèles | Divers modèles | 10 à 20 semaines | Étendue limitée -> | Modules disponibles  | Modules disponibles  | Modules disponibles  | Modules disponibles  |

Le tableau suivant présente les mêmes zones d’atterrissage, mais d’un point de vue légèrement différent, afin d’aider les décisions plus techniques.

| Zone d’atterrissage                                 | Hub                          | Spoke    | Modèle cloud | Technology      |
|----------------------------------------------|------------------------------|----------|-------------|-----------------|--|--|--|
| [CAF Migrate](./migrate-landing-zone.md)     | Refactorisation nécessaire            | Inclus | Azure uniquement  | Azure Blueprint |
| [CAF Terraform](./terraform-landing-zone.md) | Inclus dans le module VDC       | Inclus | Multicloud  | Terraform       |

## <a name="next-steps"></a>Étapes suivantes

Si vous n’êtes toujours pas sûr de la première zone d’atterrissage à choisir, nous vous recommandons de commencer par le [blueprint de zone d’atterrissage CAF Migrate](./migrate-landing-zone.md).

> [!div class="nextstepaction"]
> [Blueprint de zone d’atterrissage CAF Migrate](./migrate-landing-zone.md)
