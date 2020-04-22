---
title: Développement piloté par les tests des zones d’atterrissage dans Azure
description: Développement piloté par les tests des zones d’atterrissage dans Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: de56ab7dca0a769272777118836bc9ee93058002
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81122058"
---
# <a name="test-driven-development-tdd-for-landing-zones-in-azure"></a>Développement piloté par les tests des zones d’atterrissage dans Azure

Comme indiqué dans l’article précédent sur le [développement piloté par les tests pour les zones d’atterrissage](./test-driven-development.md), les cycles TDD commencent par un test qui valide les critères d’acceptation d’une fonctionnalité spécifique requise pour fournir le plan d’adoption du cloud. Le développement ou la refactorisation de la zone d’atterrissage peut ensuite être testée pour s’assurer que les critères d’acceptation ont été respectés. Cet article décrit un chaîne d’outils cloud natifs dans Azure pour automatiser les cycles de développement pilotés par les tests.

## <a name="azure-tools-to-support-landing-zone-tdd-cycles"></a>Outils Azure pour la prise en charge des cycles TDD de la zone d’atterrissage

![Outils de développement piloté par les tests dans Azure](../../_images/ready/azure-tdd-tools.png)

La chaîne d’outils des produits et services de gouvernance Azure natif peut facilement être intégrée dans un développement piloté par des tests pour la création de zones d’atterrissage. Chacun de ces outils sert un objectif spécifique, facilitant le développement, le test et le déploiement de votre zone d'atterrissage en conformité avec les cycles TDD.

## <a name="microsoft-provided-test-and-deployment-templates-to-accelerate-tdd"></a>Modèles de test et de déploiement fournis par Microsoft pour accélérer le développement piloté par les tests (TDD)

Microsoft fournit les exemples suivants à des fins de gouvernance. Toutefois, chacun peut être utilisé comme un test ou une série de tests dans un cycle de développement piloté par les tests pour les zones d’atterrissage. Vous trouverez des informations complémentaires sur chaque outil dans la section suivante.

- Azure Blueprints fournit plusieurs [exemples de blueprints](https://docs.microsoft.com/azure/governance/blueprints/samples), qui incluent des stratégies de test et de modèles pour le déploiement. Ces exemples de blueprints permettent d’accélérer les efforts de développement, de déploiement et de test dans les cycles TDD.
- Azure Policy comprend également des [initiatives de stratégie intégrées](https://docs.microsoft.com/azure/governance/policy/samples/built-in-initiatives), qui peuvent être utilisées pour tester et appliquer la définition complète de traitement terminé pour une zone d’atterrissage. Azure Policy comprend des [définitions de stratégie intégrées](https://docs.microsoft.com/azure/governance/policy/samples/built-in-policies) qui peuvent répondre à des critères d’acceptation individuels dans la définition de traitement terminé.
- Azure Graph comprend des [exemples de requêtes](https://docs.microsoft.com/azure/governance/resource-graph/samples/advanced) avancés, qui peuvent être utilisés pour comprendre comment les charges de travail sont déployées dans une zone de destination dans le cadre de scénarios de test avancés.
- Les [modèles de démarrage rapide Azure](https://azure.microsoft.com/resources/templates) fournissent des modèles de code source pour vous aider à accélérer le déploiement de la zone d’atterrissage et de la charge de travail.

Chacun des exemples ci-dessus peut être utilisé en tant qu’outils pour accélérer les cycles TDD. Ces exemples s’exécutent sur les outils de gouvernance dans les sections suivantes, qui permettent aux équipes de plateforme cloud de créer leur propre code source et leur propres tests.

## <a name="azure-governance-tools-that-can-accelerate-tdd-cycles"></a>Outils de gouvernance Azure permettant d’accélérer les cycles TDD

[Azure Policy](https://docs.microsoft.com/azure/governance/policy) : Azure Policy peut fournir des fonctionnalités automatiques de détection, de protection et de résolution dans les cas où les déploiements et les tentatives de déploiement s’écartent des stratégies de gouvernance. Toutefois, Azure Policy fournit également le mécanisme principal pour tester les critères d’acceptation dans votre « définition de traitement terminé ». Dans un cycle TDD, une définition de stratégie peut être créée pour tester un seul critère d’acceptation. De même, tous les critères d’acceptation peuvent être ajoutés à une initiative de stratégie affectée à l’abonnement entier. Cette approche fournit un mécanisme pour les « tests rouges » avant la modification de la zone de destination. Une fois que la zone d’atterrissage est conforme à la définition de traitement terminé, elle peut être utilisée pour appliquer les critères de test afin d’éviter les modifications de code qui provoqueraient l’échec du test dans les versions ultérieures.

[Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints) : Azure Blueprint regroupe des stratégies et d’autres outils de déploiement dans un package répétable pouvant être affecté à plusieurs zones d’atterrissage. Les plans s’avèrent utiles lorsque plusieurs efforts d’adoption partagent des définitions communes de traitement terminé que vous pouvez mettre à jour au fil du temps. Cela peut également faciliter le déploiement lors du développement et de la refactorisation ultérieurs des zones d’atterrissage.

[Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph) : Le langage de requête de Resource Graph permet de créer des tests pilotés par les données en fonction des informations sur les ressources déployées dans une zone d’atterrissage. Plus loin dans le plan d’adoption, cet outil peut également définir des tests complexes basés sur les interactions entre les ressources de la charge de travail et l’environnement cloud sous-jacent.

[Modèles Microsoft Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/templates/overview) : Ces modèles fournissent le code source principal pour tous les environnements déployés dans Azure. Lorsque vous utilisez des outils tiers, tels que Terraform, pour développer du code source qui déploie une zone d’atterrissage, les outils génèrent ses propres modèles. Ces modèles sont ensuite envoyés au Azure Resource Manager.

[Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/management/overview) : Resource Manager fournit une plateforme cohérente pour les fonctions de création et de déploiement. Cette plateforme gère le déploiement d’une zone de destination à partir du code source.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer à refactoriser votre première zone d’atterrissage, évaluez les [Considérations générales relatives aux zones d’atterrissage](./basic-considerations.md).

> [!div class="nextstepaction"]
> [Considérations générales relatives aux zones d’atterrissage](./basic-considerations.md)
