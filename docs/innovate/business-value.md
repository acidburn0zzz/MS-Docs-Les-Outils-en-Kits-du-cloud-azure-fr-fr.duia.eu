---
title: Créer un consensus autour de la valeur métier de l’innovation cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Apprenez à créer un consensus autour de la valeur métier de l’innovation cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 643da95396a4983c2642fabcf21340264d0cd1c9
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683341"
---
# <a name="building-consensus-on-the-business-value-of-innovation"></a>Création d’un consensus autour de la valeur métier de l’innovation

La première étape du développement d’une innovation consiste à identifier la manière dont elle produira une valeur métier. Cet exercice inclut une série de questions qui soulignent à quel point il est important de consacrer plus de temps à la définition de la valeur métier.

## <a name="qualifying-questions"></a>Questions de qualification

Avant de développer une solution (locale ou dans le cloud), vérifiez vos critères de valeur métier :

1. Quel besoin client défini cherchons-nous à satisfaire avec cette solution ?
2. Quelles sont les opportunités créées par cette solution pour l’entreprise ?
3. Quels résultats opérationnels cette solution permet-elle d’obtenir ?
4. Quelles motivations de l’entreprise cette solution satisfait-elle ?

Si les réponses à ces quatre questions sont bien documentées, vous n’avez peut-être pas besoin de suivre le reste de cet exercice. Heureusement, cette documentation peut être facilement testée. Pour tester la documentation et votre alignement général, organisez deux courtes réunions : l’une avec les parties prenantes de l’entreprise, l’autre avec l’équipe de développement impliquée. Posez les quatre questions ci-dessus au cours des deux réunions et comparez les résultats.

> [!NOTE]
> La documentation existante **ne doit pas** être partagée avec l’une ou l’autre des équipes avant la réunion. Si un véritable alignement existe, les hypothèses directrices doivent être mentionnées (ou, mieux encore, clairement énoncées) par les membres de chaque groupe.

> [!WARNING]
> Ne facilitez pas la réunion. Il s’agit d’un test d’alignement et non d’un exercice de création d’alignement. Au début de la réunion, assurez-vous que les participants connaissent son objectif, à savoir tester l’alignement directionnel par rapport aux accords existants établis au sein de l’équipe. Déterminez uniquement une limite de temps. Imposez jusqu’à cinq minutes par question et chronométrez chacune d’elles. Clôturez chaque question en cinq minutes, même si les participants ne s’accordent pas sur une réponse.

Si les réponses présentent un alignement directionnel mais reflètent les différents langages et intérêts de chaque groupe, considérez que l’exercice a réussi. Vous êtes prêt à passer au développement de la solution.

Si une ou deux réponses présentent un alignement directionnel, considérez que vos efforts portent leurs fruits. Vous présentez déjà un meilleur alignement que la plupart des organisations. Moyennant un investissement léger mais continu en matière d’alignement, votre réussite devrait se concrétiser prochainement. Consultez chacune des sections suivantes. Elles offrent des idées qui vous permettront peut-être de renforcer l’alignement.

Si l’une des équipes ne parvient pas à répondre aux quatre questions en trente minutes, alors l’alignement et les efforts à venir auront certainement un impact considérable sur ce travail et sur d’autres travaux. Soyez attentif à chacune des sections suivantes.

## <a name="address-the-big-picture-first"></a>Commencer par aborder les choses sous une perspective globale

Le framework d’adoption du cloud suit une voie prescrite : stratégie, planification, préparation et adoption. L’innovation cloud s’inscrit dans la phase d’adoption de ce processus. Quand les réponses aux questions 3 et 4 ci-dessus (résultats et motivations) ne sont pas correctement alignées, cela signifie qu’un élément a été manqué au cours de la phase de stratégie du cycle de vie d’adoption du cloud. Certains des scénarios suivants sont susceptibles de se présenter.

- **Opportunité d’alignement :** quand les parties prenantes de l’entreprise ne peuvent pas s’accorder sur les motivations et les résultats opérationnels liés à un effort d’innovation cloud, cela révèle une problématique plus importante. Les exercices de la [phase de stratégie cloud](../strategy/index.md) peuvent aider à développer l’alignement entre les parties prenantes de l’entreprise. En outre, il est fortement recommandé à ces parties prenantes de former une [équipe de stratégie cloud](../organize/cloud-strategy.md) se réunissant régulièrement.

- **Opportunité de communication :** quand l’équipe de développement ne peut pas s’accorder sur les motivations et les résultats opérationnels, cela peut indiquer des lacunes en termes de communication stratégique. L’examen de la stratégie cloud avec l’équipe d’adoption du cloud peut vous permettre d’éliminer rapidement cet obstacle. Plusieurs semaines après cet examen, l’équipe doit se prêter une nouvelle fois à l’exercice sur les questions de qualification.

- **Opportunité de définition des priorités :** une stratégie cloud représente essentiellement une hypothèse au niveau de la direction. Les meilleures stratégies cloud sont ouvertes aux itérations et aux commentaires. Si les deux équipes comprennent la stratégie mais ne parviennent toujours pas à aligner véritablement les réponses à ces questions, il se peut que les priorités ne soient pas correctement alignées. Une session avec l’équipe d’adoption du cloud et l’équipe de stratégie cloud peut aider les deux groupes dans leurs efforts. Au cours de cette session, l’équipe d’adoption du cloud partage ses réponses alignées sur les questions relatives à la perspective globale. Une conversation entre l’équipe d’adoption du cloud et l’équipe de stratégie cloud peut alors mettre en évidence les opportunités d’amélioration de l’alignement des priorités.

Ces opportunités relatives à la perspective globale révèlent souvent des moyens d’améliorer l’alignement de cette solution sur la stratégie cloud. Cet exercice aboutit souvent aux deux résultats suivants :

- Ces conversations peuvent permettre d’améliorer la stratégie cloud et la représentation de ce besoin critique du client. Ce changement peut renforcer le soutien de l’équipe par la direction.
- En revanche, cette conversation peut montrer qu’il est plus pertinent d’investir dans une autre solution pour l’équipe d’adoption du cloud. Dans ce cas, envisagez de migrer cette solution avant de continuer à investir dans l’innovation. Cela peut également indiquer qu’une approche basée sur les développeurs citoyens est nécessaire pour tester la valeur métier en premier. Dans les deux cas, cela permet à l’équipe d’éviter un lourd investissement offrant des retours commerciaux limités.

## <a name="address-solution-alignment"></a>Améliorer l’alignement de la solution

Il est relativement courant que les réponses aux questions 1 et 2 (besoin du client et opportunité commerciale) ne soient pas correctement alignées, particulièrement au cours des premières phases de conceptualisation et de développement. De nombreuses équipes de développement peinent à trouver l’équilibre entre une définition excessive et insuffisante. Dans le cadre du framework d’adoption du cloud, les approches « lean » telles que les boucles de rétroaction développer-mesurer-apprendre sont présentées comme le meilleur moyen de répondre à ces questions. La liste suivante présente les opportunités et les approches permettant de créer un alignement.

- **Opportunité d’hypothèse :** souvent, différentes parties prenantes et équipes de développement présentent des attentes excessives vis-à-vis d’une solution. Cela indique que l’hypothèse est trop vague. Suivez l’aide sur la façon de [développer une solution en faisant preuve d’empathie vis-à-vis du client](./considerations/build.md) pour élaborer une hypothèse plus claire.
- **Opportunité de développement :** quand les équipes ne sont pas correctement alignées en raison d’un désaccord sur la façon de répondre au besoin du client, cela indique généralement que l’équipe est [retardée par un spike technique prématuré](./considerations/build.md#reduce-complexity-and-delay-technical-spikes). Pour que l’équipe reste concentrée sur le client, commencez la première itération et développez un petit MVP pour traiter une partie de l’hypothèse. Pour plus d’informations sur la façon d’aider l’équipe à avancer, consultez [Développement d’inventions numériques](./considerations/invention.md).
- **Opportunité de formation :** quand l’une des équipes n’est pas correctement alignée parce qu’elle a besoin de spécifications techniques approfondies et de spécifications fonctionnelles étendues, cela révèle une opportunité de formation aux méthodologies agiles. Quand la culture de l’équipe n’est pas prête pour les processus agiles, il peut être difficile d’innover et de suivre le rythme du marché. Pour connaître les ressources de formation sur l’approche DevOps et les pratiques agiles, consultez :
  - [Faire évoluer vos activités DevOps](https://docs.microsoft.com/learn/paths/evolve-your-devops-practices)
  - [Générer des applications avec Azure DevOps](https://docs.microsoft.com/learn/paths/build-applications-with-azure-devops)
  - [Déployer des applications avec Azure DevOps](https://docs.microsoft.com/learn/paths/deploy-applications-with-azure-devops/)

L’utilisation de cette méthodologie et des outils de gestion de backlog dans chaque section indiquée ci-dessus peut aider à aligner la solution.

## <a name="next-steps"></a>Étapes suivantes

Une fois que la proposition de valeur métier est correctement alignée et communiquée, il est temps de commencer à développer votre solution. Pour obtenir de l’aide sur les étapes suivantes, revenez aux [exercices sur l’innovation](./index.md).

> [!div class="nextstepaction"]
> [Revenir aux exercices sur l’innovation en vue des étapes suivantes](./index.md)
