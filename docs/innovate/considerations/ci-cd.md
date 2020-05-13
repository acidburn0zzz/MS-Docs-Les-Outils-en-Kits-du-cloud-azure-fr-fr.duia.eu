---
title: Favoriser l’adoption avec l’invention numérique
description: Utilisez le modèle de maturité de la méthodologie d’innovation pour réduire les points de friction qui ralentissent l’adoption, tout en maintenant les bonnes pratiques en place.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 54a2892ed657c08ee6c984798a61c1ff10716257
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219748"
---
<!-- cSpell:ignore deprioritize -->

# <a name="empower-adoption"></a>Favoriser l’adoption

Le test ultime de l’innovation est la réaction du client à votre invention. L’hypothèse est-elle avérée ? Les clients utilisent-ils la solution ? Est-elle mise à l’échelle pour répondre aux besoins du pourcentage d’utilisateurs souhaité ? Plus important encore, les utilisateurs continuent-ils de revenir ? Aucune de ces questions ne peut être posée tant que la solution de produit minimum viable (MVP) n’a pas été déployée. Dans cet article, nous allons nous concentrer sur la discipline de la favorisation de l’adoption.

## <a name="reduce-friction-that-affects-adoption"></a>Réduire les frictions qui affectent l’adoption

Il existe quelques problématiques clés pour l’adoption qui peuvent être réduites en combinant des technologies et des processus. Pour les lecteurs connaissant les processus d’intégration continue (CI) et de déploiement continu (CD), ou les processus DevOps, ce qui suit leur sera familier. Cet article établit un point de départ pour les équipes d’adoption du cloud, qui alimente les boucles d’innovation et de feeback. Dans le futur, ce point de départ peut passer à des approches CI/CD ou DevOps plus robustes, à mesure que les produits et les équipes gagnent en maturité.

Comme précisé dans [Mesure de l’impact client](./measure.md), la validation positive de toute hypothèse requiert une itération et une détermination. Vous échouerez plus souvent que vous ne réussirez au cours de n’importe quel cycle d’innovation. Ceci est normal. Toutefois, lorsqu’un besoin du client, l’hypothèse et la solution sont alignés à grande échelle, le monde change rapidement. Cet article vise à réduire les [pics techniques](./build.md#reduce-complexity-and-delay-technical-spikes) qui ralentissent l’innovation, tout en garantissant que quelques bonnes pratiques solides sont en place. Cela permet à l’équipe de se préparer au succès, tout en répondant aux besoins actuels des clients.

## <a name="empower-adoption-the-maturity-model"></a>Favoriser l’adoption : le modèle de maturité

L’objectif principal de la [méthodologie d’innovation](./index.md) consiste à créer des partenariats avec les clients et à accélérer les boucles de commentaires, ce qui entraînera des innovations sur le marché. L’image et les sections qui suivent décrivent les implémentations initiales qui prendront en charge la méthodologie.

![Favoriser l’adoption : le modèle de maturité](../../_images/innovate/empower-adoption-maturity.png)

- [Solution partagée](#shared-solution) : établissez un dépôt centralisé pour tous les aspects de la solution.
- [Boucles de commentaires](#feedback-loops) : Assurez-vous que les boucles de rétroaction peuvent être gérées de manière cohérente au fil des itérations.
- [Intégration continue](#continuous-integration) : développez et consolidez régulièrement la solution.
- [Test fiable](#reliable-testing) : Validez la qualité de la solution et les modifications attendues pour garantir la fiabilité de vos métriques de test.
- [Déploiement de la solution](#solution-deployment) : Déployez des solutions pour que l’équipe puisse partager rapidement les modifications avec les clients.
- [Mesure intégrée](#integrated-measurements) : ajoutez des métriques d’apprentissage à la boucle de rétroaction pour une analyse claire par l’ensemble de l’équipe.

Pour réduire les pics techniques, supposez que la maturité sera initialement faible pour chacun de ces principes. Toutefois, vous pouvez préparer les outils et les processus qui peuvent être mis à l’échelle à mesure que ces opérations deviennent plus précises. Dans Azure, [GitHub](https://guides.github.com) et [Azure DevOps](https://docs.microsoft.com/azure/devops) permettent aux petites équipes de rencontrer peu de problèmes lors de leur prise en main. Ces équipes peuvent croître pour inclure jusqu’à plusieurs milliers de développeurs travaillant sur des solutions de mise à l’échelle et qui testent des centaines d’hypothèses d’utilisateurs. Le reste de cet article illustre l’approche « prévoir grand, commencer petit » pour favoriser l’adoption sur chacun de ces principes.

## <a name="shared-solution"></a>Solution partagée

Comme précisé dans [Mesure de l’impact client](./measure.md), la validation positive de toute hypothèse requiert une itération et une détermination. Vous échouerez plus souvent que vous ne réussirez au cours de n’importe quel cycle d’innovation. Ceci est normal. Toutefois, lorsqu’un besoin du client, l’hypothèse et la solution sont alignés à grande échelle, le monde change rapidement.

Quand vous effectuez la mise à l’échelle de l’innovation, il n’existe pas d’outil plus précieux qu’une base de code partagée pour la solution. Malheureusement, il n’existe aucun moyen de prédire quelle itération ou MVP constituera la combinaison gagnante. C’est pourquoi il n’est jamais trop tôt pour établir un dépôt ou une base de code partagé. Il s’agit du [pic technique](./build.md#reduce-complexity-and-delay-technical-spikes) qui ne doit jamais être retardé. Au fur et à mesure que l’équipe itère au sein de plusieurs solutions MVP, un référentiel partagé permet de faciliter la collaboration et le développement accéléré. Lorsque les modifications apportées ralentissent les métriques d’apprentissage, la contrôle de version vous de restaurer une version antérieure et plus efficace de la solution.

[GitHub](https://guides.github.com) est l’outil de gestion de dépôts de code le plus utilisé. Il vous permet de créer un dépôt de code partagé en quelques étapes. Vous pouvez également utiliser la fonctionnalité [Azure Repos](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops) d’Azure DevOps pour créer un dépôt [Git](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) ou [Team Foundation](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc).

## <a name="feedback-loops"></a>Boucles de rétroaction

Le secret pour créer des partenariats avec les clients au cours des cycles d’innovation consiste à intégrer le client à la solution. Cela est accompli, en partie, en [mesurant l’impact sur les clients](./measure.md). Cela nécessite de discuter et d’effectuer des tests directs avec le client. Les deux génèrent des commentaires qui doivent être gérés efficacement.

Chaque commentaire constitue une solution potentielle aux besoins des clients. Plus important encore, tous les commentaires d’un client constituent une opportunité d’améliorer le partenariat. Si des commentaires sont intégrés à une solution MVP, félicitez le client. Même si les commentaires ne sont pas exploitables, le simple fait d’être transparent avec la décision de déclasser les commentaires démontre une [mentalité de croissance](./learn.md#growth-mindset) et une volonté [d’apprendre en permanence](./learn.md#continuous-learning).

[Azure DevOps](https://docs.microsoft.com/azure/devops) comprend des moyens de [demander, fournir et gérer des commentaires](https://docs.microsoft.com/azure/devops/project/feedback). Chacun de ces outils centralise les commentaires afin que l’équipe puisse effectuer des actions et fournir un suivi dans le service d’une boucle de commentaires transparente.

## <a name="continuous-integration"></a>Intégration continue

À mesure que l’adoption est mise à l’échelle et qu’une hypothèse se rapproche de la véritable innovation, le nombre de petites hypothèses à tester augmente rapidement. Pour obtenir des boucles de commentaires précises et des processus d’adoption sans heurts, il est important que chacune de ces hypothèses soit intégrée à l’hypothèse principale sous-jacente à l’innovation et la soutiennent. Cela signifie que vous devez aussi agir rapidement pour innover et vous développer, ce qui nécessite que plusieurs développeurs testent des variantes de l’hypothèse principale. Pour des efforts de développement de phase ultérieurs, il peut être nécessaire que plusieurs équipes de développeurs créent une solution partagée. L’intégration continue est la première étape vers la gestion de toutes les parties mobiles.

Dans l’intégration continue, les modifications du code sont fréquemment fusionnées dans la branche principale. Les processus de génération et de test automatisés garantissent que le code de la branche principale est toujours de qualité production. Cela garantit que les développeurs travaillent ensemble pour développer des solutions partagées qui proposent des boucles de commentaires précises et fiables.

Azure DevOps et [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines) permettent d’assurer une intégration continue en quelques étapes dans GitHub ou divers autres référentiels.
Apprenez-en plus sur l’[intégration continue](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-integration) ou découvrez le [labo pratique](https://www.azuredevopslabs.com/labs/azuredevops/continuousintegration). Il existe également des architectures de solution permettant d’accélérer la création de vos [pipelines CI/CD avec Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="reliable-testing"></a>Test fiable

Les défauts de toute solution peuvent créer des faux positifs ou des faux négatifs. Des erreurs inattendues peuvent facilement entraîner une mauvaise interprétation des métriques d’adoption des utilisateurs. Elles peuvent également entraîner des commentaires négatifs des clients qui ne représentent pas précisément le test de votre hypothèse.

Lors des premières itérations d’une solution MVP, vous pouvez vous attendre à rencontrer des erreurs. Les utilisateurs précoces peuvent d’ailleurs les trouver attrayants. Dans les premières versions, les tests d’acceptation seront habituellement inexistants. Toutefois, l’un des aspects de la création avec empathie est la validation des besoins et de l’hypothèse. Les deux peuvent être effectuées par le biais de tests unitaires au niveau du code et de tests d’acceptation manuels avant le déploiement. Ensemble, elles fournissent un niveau de fiabilité lors des tests. Vous devez vous efforcer d’automatiser une série bien définie de tests de génération, de tests unitaires et de tests d’acceptation. Celles-ci garantissent des mesures fiables relatives à des ajustements plus granulaires de l’hypothèse et de la solution obtenue.

La fonctionnalité [Azure Test Plans](https://docs.microsoft.com/azure/devops/test/track-test-status?view=azure-devops) fournit des outils permettant de développer et d’exécuter des plans de test pendant l’exécution des tests manuels ou automatisés.

## <a name="solution-deployment"></a>Déploiement de la solution

L’aspect le plus important de la favorisation de l’adoption est probablement la possibilité de contrôler la publication d’une solution aux clients. En fournissant un pipeline libre-service ou automatisé pour publier une solution pour les clients, vous accélérez la boucle de commentaires. En permettant aux clients d’interagir rapidement avec les modifications de la solution, vous invitez le client à prendre part au processus. Cette approche déclenche également des tests plus rapides des hypothèses, réduisant ainsi les hypothèses et les rechargements potentiels.

Il existe plusieurs méthodes pour le déploiement de solutions. Les éléments suivants représentent les trois plus courantes :

- Le **déploiement continu** est l’approche la plus avancée, car il déploie automatiquement les modifications de code en production. Pour des équipes matures qui testent des hypothèses matures, le déploiement continu peut être extrêmement précieux.
- Lors des premières phases de développement, la **livraison continue** peut être plus appropriée. Dans la livraison continue, toute modification du code est automatiquement déployée dans un environnement de type production. Les développeurs, les décideurs d’entreprise et d’autres membres de l’équipe peuvent utiliser cet environnement pour vérifier que leur travail est prêt pour la production. Vous pouvez également utiliser cette méthode pour tester une hypothèse avec des clients, sans affecter les activités commerciales en cours.
- Le **déploiement manuel** est l’approche la moins sophistiquée pour la gestion des versions. Comme son nom l’indique, un membre de l’équipe déploie manuellement les modifications de code les plus récentes. Cette approche est sujette aux erreurs, n’est pas fiable et est considérée comme un anti-modèle par la plupart des ingénieurs chevronnés.

Lors de la première itération d’une solution MVP, le déploiement manuel est courant, malgré l’évaluation précédente. Lorsque la solution est extrêmement fluide et que les commentaires des clients sont inconnus, il est important de réinitialiser l’ensemble de la solution (ou même l’hypothèse principale). Voici la règle générale pour le déploiement manuel : aucune preuve du client, aucune automatisation du déploiement.

Investir trop tôt peut entraîner une perte de temps. Plus important encore, cela peut créer des dépendances sur le pipeline de mise en production qui rend l’équipe plus résistante à un pivot précoce. Après les premières itérations ou lorsque les commentaires des clients suggèrent une réussite potentielle, un modèle de déploiement plus avancé doit être rapidement adopté.

À tout moment de la validation des hypothèses, Azure DevOps et [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines) offrent des fonctionnalités de livraison continue et de déploiement continu. En savoir plus sur la [livraison continue](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-delivery), ou consultez le [laboratoire pratique](https://www.azuredevopslabs.com/labs/azuredevops/continuousdeployment). Les architectures de solution peuvent aussi accélérer la création de vos [pipelines CI/CD avec Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="integrated-measurements"></a>Mesures intégrées

En [mesurant l’impact client](./measure.md), il est important de comprendre comment les clients réagissent aux modifications apportées à la solution. Ces données, appelées _télémétrie_, fournissent des insights sur les actions effectuées par un utilisateur (ou un groupe d’utilisateurs) lors de l’utilisation de la solution. À partir de ces données, il est facile d’obtenir une validation quantitative de l’hypothèse. Ces métriques peuvent ensuite être utilisées pour ajuster la solution et générer des informations plus précises. Ces modifications plus subtiles permettent de faire passer la solution initiale dans les itérations suivantes, ce qui permet au final de répéter l’adoption à grande échelle.

Dans Azure, [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) fournit les outils et l’interface permettant de collecter et d’examiner les données de l’expérience client. Vous pouvez appliquer ces observations et insights pour affiner le backlog à l’aide d'[Azure Boards](https://docs.microsoft.com/azure/devops/boards).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous maîtrisez les outils et les processus nécessaires pour favoriser l’adoption, il est temps d’examiner une discipline d’innovation plus avancée, l’[interaction avec les appareils](./devices.md). Cette discipline peut aider à réduire les obstacles entre les expériences physiques et numériques, rendant votre solution encore plus facile à adopter.

> [!div class="nextstepaction"]
> [Interagir avec les appareils](./devices.md)
