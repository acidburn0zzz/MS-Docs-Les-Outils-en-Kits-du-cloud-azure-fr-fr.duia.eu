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
ms.openlocfilehash: c57152b92826539a236227636ee115c19bd70e7a
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565747"
---
# <a name="build-consensus-on-the-business-value-of-innovation"></a>Créer un consensus autour de la valeur métier de l’innovation

La première étape du développement d’une innovation consiste à identifier la manière dont elle peut créer une valeur métier. Dans cet exercice, vous répondez à une série de questions qui mettent en avant l’importance du temps investi dans la définition de la valeur métier de votre organisation.

## <a name="qualifying-questions"></a>Questions de qualification

Avant de développer une solution (locale ou dans le cloud), validez vos critères de valeur métier en répondant aux questions suivantes :

1. À quel besoin client défini cherchez-vous à répondre avec cette solution ?
1. Quelles sont les opportunités créées par cette solution pour votre entreprise ?
1. Quels résultats opérationnels cette solution permet-elle d’obtenir ?
1. À quelles motivations de votre entreprise cette solution répond-elle ?

Si les réponses à ces quatre questions sont bien documentées, vous n’avez peut-être pas besoin de faire le reste de cet exercice. Heureusement, vous pouvez facilement tester n’importe quelle documentation. Organisez deux réunions courtes pour tester la documentation et l’alignement interne de votre organisation. Invitez les parties prenantes de l’entreprise à participer à une réunion et organisez une réunion distincte avec l’équipe de développement engagée. Posez les quatre questions ci-dessus à chaque groupe, puis comparez les résultats.

> [!NOTE]
> La documentation existante **ne doit pas** être partagée avec l’une ou l’autre des équipes avant la réunion. Si un véritable alignement existe, les hypothèses directrices doivent être mentionnées, voire clairement énoncées, par les membres de chaque groupe.

<!-- -->

> [!WARNING]
> Ne facilitez pas la réunion. Ce test permet de déterminer l’alignement ; ce n’est pas un exercice de création d’alignement. Au début de la réunion, rappelez aux participants que l’objectif est de tester l’alignement directionnel sur les accords existants au sein de l’équipe. Ne consacrez pas plus de cinq minutes à chaque question. Utilisez un minuteur et passez à la question suivante au bout de cinq minutes, même si les participants ne se sont pas mis d’accord sur une réponse.

Tenez compte des différentes langues et des intérêts de chaque groupe. Si les réponses du test confirment un alignement directionnel, vous pouvez considérer que cet exercice est réussi. Vous êtes prêt à passer au développement de la solution.

Si une ou deux réponses présentent un alignement directionnel, considérez que vos efforts portent leurs fruits. Votre alignement est déjà meilleur que celui de la plupart des organisations. Moyennant un investissement modéré mais continu en matière d’alignement, votre réussite devrait se concrétiser prochainement. Consultez chacune des sections suivantes. Elles offrent des idées qui vous permettront peut-être de renforcer l’alignement.

Si l’une des équipes ne parvient pas à répondre aux quatre questions en 30 minutes, il est probable que l’alignement et les considérations des sections ci-dessous auront un impact significatif sur ce travail et sur d’autres travaux. Soyez attentif à chacune des sections suivantes.

## <a name="address-the-big-picture-first"></a>Commencer par aborder les choses sous une perspective globale

Le framework d’adoption du cloud doit suivre une procédure comprenant les phases suivantes : stratégie, planification, préparation et adoption. L’innovation cloud s’inscrit dans la phase d’adoption de ce processus. Les réponses aux [questions de qualification](#qualifying-questions) trois et quatre concernent les résultats et les motivations. Si ces réponses ne sont pas cohérentes, ceci indique que votre organisation a manqué quelque chose pendant la phase de stratégie du cycle de vie d’adoption du cloud. Certains des scénarios suivants sont susceptibles de se présenter.

- **Opportunité d’alignement :** quand les parties prenantes de l’entreprise ne peuvent pas s’accorder sur les motivations et les résultats opérationnels liés à un effort d’innovation cloud, cela révèle une problématique plus importante. Les exercices de la [phase de stratégie cloud](../strategy/index.md) peuvent aider à développer l’alignement entre les parties prenantes de l’entreprise. En outre, il est fortement recommandé à ces parties prenantes de former une [équipe de stratégie cloud](../organize/cloud-strategy.md) se réunissant régulièrement.

- **Opportunité de communication :** quand l’équipe de développement ne peut pas s’accorder sur les motivations et les résultats opérationnels, cela peut indiquer des lacunes en termes de communication stratégique. Vous pouvez résoudre rapidement ce problème en examinant la stratégie de cloud avec l’équipe d’adoption du cloud. Plusieurs semaines après cet examen, l’équipe doit se prêter une nouvelle fois à l’exercice sur les questions de qualification.

- **Opportunité de définition des priorités :** une stratégie cloud représente essentiellement une hypothèse au niveau de la direction. Les meilleures stratégies cloud sont ouvertes aux itérations et aux commentaires. Si les deux équipes comprennent la stratégie, mais ne parviennent toujours pas à aligner véritablement les réponses à ces questions, il se peut que les priorités ne soient pas correctement alignées. Organisez une session avec l’équipe d’adoption du cloud et l’équipe de stratégie cloud. Cette session peut soutenir les efforts des deux groupes. L’équipe d’adoption du cloud commence par partager ses réponses alignées aux questions de qualification. Une conversation entre l’équipe d’adoption du cloud et l’équipe de stratégie cloud peut alors mettre en évidence les opportunités d’amélioration de l’alignement des priorités.

Ces opportunités relatives à la perspective globale révèlent souvent des moyens d’améliorer l’alignement de la solution innovante sur la stratégie cloud. Cet exercice aboutit souvent aux deux résultats suivants :

- Ces conversations peuvent aider votre équipe à améliorer la stratégie de cloud de votre organisation et à mieux répondre aux besoins importants des clients. Ce changement peut renforcer le soutien de votre équipe par la direction.
- À l’inverse, ces entretiens peuvent montrer que votre équipe d’adoption du cloud devrait s’investir dans une solution différente. Dans ce cas, envisagez de migrer cette solution avant de continuer à investir dans l’innovation. Sinon, ces entretiens peuvent indiquer que vous adoptez une approche développeur citoyenne pour tester d’abord la valeur métier. Dans les deux cas, ils permettent à votre équipe d’éviter un gros investissement au rendement limité pour l’entreprise.

## <a name="address-solution-alignment"></a>Améliorer l’alignement de la solution

Il n’est pas rare que les réponses aux questions une et deux ne coïncident pas. Pendant les premières étapes de conceptualisation et de développement, les besoins du client et les opportunités commerciales divergent souvent. De nombreuses équipes de développement peinent à trouver un équilibre entre une définition excessive et insuffisante. Le framework d’adoption du cloud recommande des approches « lean » telles que les boucles de rétroaction développer-mesurer-apprendre pour répondre à ces questions. La liste suivante présente les opportunités et les approches permettant de créer un alignement.

- **Opportunité d’hypothèse :** souvent, différentes parties prenantes et équipes de développement présentent des attentes excessives vis-à-vis d’une solution. Des attentes peu réalistes peuvent être un signe que l’hypothèse est trop vague. Suivez les conseils pour [développer une solution en faisant preuve d’empathie vis-à-vis du client](./considerations/build.md) afin d’élaborer une hypothèse plus claire.
- **Opportunité de développement :** il est possible que les équipes soient mal alignées parce qu’elles ne sont pas d’accord sur la façon de répondre aux besoins du client. Ce désaccord indique généralement que l’équipe est [retardée par un pic d’évolution technique prématuré](./considerations/build.md#reduce-complexity-and-delay-technical-spikes). Pour que l’équipe reste concentrée sur le client, commencez la première itération et développez un petit produit minimum viable (MVP) pour traiter une partie de l’hypothèse. Pour plus d’informations sur la façon d’aider l’équipe à avancer, consultez [Développer des inventions numériques](./considerations/invention.md).
- **Opportunité de formation :** L’une ou l’autre équipe peut être mal alignée parce qu’elle doit satisfaire à des exigences techniques approfondies et à des exigences fonctionnelles étendues. Ceci peut aboutir à une opportunité de formation aux méthodologies agiles. Quand la culture de l’équipe n’est pas prête pour les processus agiles, innover et suivre le rythme du marché peut représenter un défi.  Pour connaître les ressources de formation sur l’approche DevOps et les pratiques agiles, consultez :
  - [Faire évoluer vos activités DevOps](https://docs.microsoft.com/learn/paths/evolve-your-devops-practices)
  - [Générer des applications avec Azure DevOps](https://docs.microsoft.com/learn/paths/build-applications-with-azure-devops)
  - [Déployer des applications avec Azure DevOps](https://docs.microsoft.com/learn/paths/deploy-applications-with-azure-devops)

Le suivi de la méthodologie et des outils de gestion du backlog dans chaque section de cet article peut aider à aligner la solution.

## <a name="next-steps"></a>Étapes suivantes

Après avoir aligné et communiqué votre proposition de valeur métier, vous pouvez commencer à développer votre solution.
> [!div class="nextstepaction"]
> [Revenir aux exercices sur l’innovation en vue des étapes suivantes](./index.md)
