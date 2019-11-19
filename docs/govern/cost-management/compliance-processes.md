---
title: Processus de conformité à la stratégie Gestion des coûts
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processus de conformité à la stratégie Gestion des coûts
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: eb3bfc584e3c3f86e39918495fe7e0d313f13e55
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564718"
---
# <a name="cost-management-policy-compliance-processes"></a>Processus de conformité à la stratégie Gestion des coûts

Cet article présente une approche permettant de créer des processus qui appuient une discipline de gouvernance [Gestion des coûts](./index.md). Pour être efficace, une gouvernance des coûts du cloud implique plusieurs processus manuels récurrents qui visent à entrer en conformité avec la stratégie. De fait, l’équipe de gouvernance cloud et les parties prenantes intéressées sont régulièrement sollicitées afin de passer en revue et mettre à jour la stratégie et veiller au respect de cette dernière. En outre, de nombreux processus de supervision et d’application continues peuvent être automatisés ou complétés par des outils afin de réduire la charge de gouvernance et accélérer la réponse en cas de manquement à la stratégie.

## <a name="planning-review-and-reporting-processes"></a>Processus de planification, de révision et de génération de rapports

Les outils de gestion des coûts du cloud ne peuvent pas surpasser les processus et stratégies qu’ils appuient. Les éléments suivants représentent un ensemble d’exemples de processus généralement impliqués dans la discipline Gestion des coûts. Ces exemples constituent des points de départ pour planifier les processus qui vous permettront de mettre à jour la stratégie de coûts en continu, à mesure que l’entreprise évolue et selon les commentaires des équipes commerciales qui doivent respecter les conseils de gouvernance des coûts.

**Évaluation des risques et planification initiales :** Dans le cadre de l’adoption initiale de la discipline Gestion des coûts, identifiez vos principaux risques métier et tolérances liés aux coûts du cloud. Utilisez ces informations pour débattre du budget et des risques liés aux coûts avec les membres de vos équipes commerciales, puis développer un ensemble de stratégies de base pour atténuer ces risques et ainsi établir votre stratégie de gouvernance initiale.

**Planification du déploiement :** Avant le déploiement d’une ressource, prévoyez un budget en fonction de l’allocation cloud prévue. Assurez-vous de documenter les informations relatives à la propriété et à la comptabilité dans le cadre du déploiement.

**Planification annuelle :** Une fois par an, effectuez une analyse cumulative sur toutes les ressources qui sont déployées et celles dont le déploiement est prévu. Définissez les budgets en fonction des unités commerciales, des départements, des équipes ou des autres services concernés pour favoriser l’adoption en libre-service. Veillez à ce que le responsable de chaque unité de facturation connaisse le montant du budget et sache effectuer le suivi des dépenses.

Il est temps de procéder à un engagement ou un achat préalable pour optimiser votre remise. Nous vous conseillons d’aligner votre budget annuel avec l’année fiscale de votre fournisseur de cloud afin de bénéficier au maximum des réductions de fin d’année.

**Planification trimestrielle :** Une fois par trimestre, examinez les budgets avec chaque responsable d’unité de facturation afin d’aligner les prévisions aux dépenses réelles. Si vous constatez des modifications au plan initial ou des dépenses inattendues, ajustez et réallouez le budget.

Ce processus de planification trimestriel constitue également un moment idéal pour évaluer les lacunes des membres de votre équipe de gouvernance cloud en lien avec les plans de l’entreprise actuels ou futurs. Invitez le personnel concerné et les propriétaires des charges de travail à participer aux révisions et à la planification en tant que conseillers temporaires ou membres permanents de votre équipe.

**Apprentissage et formation :** Deux fois par mois, offrez des sessions de formation pour vous assurer que le personnel commercial et informatique connaît les dernières exigences stratégiques Gestion des coûts. Dans le cadre de ce processus, relisez et mettez à jour toute la documentation, les guides et les autres ressources de formation pour vous assurer qu’ils correspondent aux dernières instructions stratégiques de l’entreprise.

**Génération de rapports mensuels :** Une fois par mois, comparez les dépenses réelles avec vos prévisions. Signalez tout écart inattendu aux responsables de la facturation.

Ces processus de base permettent d’ajuster les dépenses et d’établir les fondements de la discipline Gestion des coûts.

## <a name="processes-for-ongoing-monitoring"></a>Processus de surveillance continue

La réussite des stratégies de gouvernance Gestion des coûts dépend du degré de visibilité sur les dépenses de cloud passées, en cours et prévues. Si vous ne pouvez pas analyser les mesures et données pertinentes au sujet de vos coûts existants, vous ne pourrez pas identifier les changements de risques ni détecter les violations de vos tolérances aux risques. Les processus de gouvernance continus décrits ci-dessus exigent que vous fournissiez des données de qualité afin d’être capable de modifier la stratégie pour protéger votre infrastructure au mieux face à l’évolution des besoins métiers et l’utilisation du cloud.

Assurez-vous que vos équipes informatiques ont implémenté des systèmes automatisés pour surveiller vos dépenses et votre utilisation du cloud, et identifier les écarts inattendus par rapport aux prévisions de coûts. Mettez en place des systèmes de rapports et d’alertes pour garantir une détection et une atténuation rapides des potentielles violations de stratégie.

## <a name="compliance-violation-triggers-and-enforcement-actions"></a>Déclencheurs relatifs aux violations de conformité et actions de mise en conformité

Lorsque des violations sont détectées, vous devez prendre des actions de mise en conformité vis-à-vis de la stratégie. Vous pouvez automatiser la plupart des déclencheurs relatifs aux violations à l’aide des outils présentés dans la [chaîne d’outils Gestion des coûts pour Azure](./toolchain.md).

Voici quelques exemples de déclencheurs :

- **Écarts de budget mensuel :** Lorsque l’écart entre les dépenses mensuelles réelles et les prévisions dépasse 20 %, discutez-en avec le responsable de l’unité de facturation. Mettez-vous d’accord sur des résolutions et des modifications à apporter aux prévisions.
- **Rythme d’adoption :** Tout écart de niveau d’abonnement supérieur à 20 % déclenche une révision avec le responsable de l’unité de facturation. Mettez-vous d’accord sur des résolutions et des modifications à apporter aux prévisions.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de gestion cloud ](./template.md), documentez les processus et les déclencheurs qui correspondent au plan d’adoption du cloud actuel.

Pour obtenir des conseils sur l’exécution des stratégies de gestion cloud en harmonie avec les plans d’adoption, consultez l’article sur l’amélioration de la discipline Gestion des coûts.

> [!div class="nextstepaction"]
> [Amélioration de la discipline Gestion des coûts](./discipline-improvement.md)
