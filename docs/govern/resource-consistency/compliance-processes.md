---
title: Processus de conformité à la stratégie de cohérence des ressources
description: Processus de conformité à la stratégie de cohérence des ressources
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 7fbb2d7b121c011005c4f900bf66cafb8977ffeb
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76805980"
---
# <a name="resource-consistency-policy-compliance-processes"></a>Processus de conformité à la stratégie de cohérence des ressources

Cet article décrit les processus d’adhésion à la stratégie, qui gouvernent la [cohérence des ressources](./index.md). Une gouvernance efficace de la cohérence des ressources cloud commence par des processus manuels récurrents. Ces processus ont été conçus pour identifier l’inefficacité opérationnelle, améliorer la gestion des ressources déployées, et garantir un minimum d’interruptions pour les charges de travail critiques. Ces processus manuels sont complétés par la supervision, l’automatisation et des outils afin de réduire la surcharge de gouvernance et de permettre de répondre plus rapidement aux écarts à la stratégie.

## <a name="planning-review-and-reporting-processes"></a>Processus de planification, de révision et de génération de rapports

Les plateformes cloud offrent tout un ensemble d’outils et de fonctionnalités de gestion que vous pouvez utiliser pour organiser, approvisionner, mettre à l’échelle et minimiser les temps d’arrêt. L’utilisation de ces outils afin de structurer et d’exécuter vos déploiements cloud de manière efficace et de minimiser les risques potentiels demande de faire appel à des processus et stratégies réfléchis. En parallèle, vous devrez travailler en étroite collaboration avec les équipes en charge des opérations informatiques et les parties prenantes de l’entreprise.

Les éléments suivants représentent un ensemble d’exemples de processus généralement impliqués dans la discipline Cohérence des ressources. Ces exemples constituent des points de départ pour planifier les processus qui vous permettront de mettre à jour la stratégie de cohérence des ressources à mesure que l’entreprise évolue et selon les commentaires des équipes informatiques chargés d’implémenter les mesures de gouvernance.

**Évaluation des risques et planification initiales :** Dans le cadre de l’adoption initiale de la discipline Cohérence des ressources, identifiez vos principaux risques métier et tolérances liés aux opérations et à la gestion informatique. Utilisez ces informations pour parler des risques techniques spécifiques avec les membres de vos équipes informatiques et les propriétaires de charge de travail. Vous pourrez ainsi développer un ensemble de bases de référence pour les stratégies Cohérence des ressources, afin de réduire les risques et d’établir votre stratégie de gouvernance initiale.

**Planification du déploiement :** Avant de déployer une ressource, effectuez un examen afin d’identifier les éventuels nouveaux risques opérationnels. Définissez les exigences en termes de ressources et les modèles de demande attendus. Identifiez également les besoins en évolutivité et les opportunités potentielles d’optimisation de l’utilisation. Vérifiez aussi que des plans de sauvegarde et de récupération sont en place.

**Test de déploiement :** Dans le cadre du processus de déploiement, l’équipe de gouvernance cloud, en collaboration avec les équipes en charge des opérations cloud, est tenue de passer en revue le déploiement pour valider la conformité à la stratégie Cohérence des ressources.

**Planification annuelle :** Tous les ans, effectuez une révision de haut niveau de la stratégie Cohérence des ressources. Étudiez les plans d’expansion de l’entreprise ou ses priorités pour l’avenir, puis mettez à jour les stratégies d’adoption du cloud afin d’identifier l’augmentation des risques potentiels ou d’autres besoins émergents pour la Cohérence des ressources. Utilisez ce temps de révision annuelle pour examiner les dernières meilleures pratiques liées à la Cohérence des ressources cloud. Puis intégrez ces pratiques dans vos stratégies et processus de révision.

**Planification et révision trimestrielles :** Tous les trimestres, effectuez une révision des données opérationnelles et des rapports d’incident afin d’identifier les modifications requises dans la stratégie Cohérence des ressources. Dans le cadre de ce processus, observez les changements d’utilisation et de performances des ressources, afin d’identifier les augmentations et diminutions requises en termes d’allocation des ressources. Par ailleurs, identifiez les charges de travail ou ressources qui peuvent être mises hors service.

Ce processus de planification constitue également un moment idéal pour évaluer les lacunes des membres de votre équipe de gouvernance cloud en lien avec les risques, nouveaux ou évolutifs, liés à la Cohérence des ressources en tant que discipline. Invitez le personnel informatique concerné à participer aux révisions et à la planification en tant que conseillers techniques temporaires ou membres permanents de votre équipe.

**Apprentissage et formation :** Deux fois par mois, offrez des sessions de formation pour vous assurer que le personnel informatique et les développeurs connaissent les dernières exigences et recommandations pour la stratégie Cohérence des ressources. Dans le cadre de ce processus, relisez et mettez à jour toute la documentation et les autres ressources de formation pour vous assurer qu’elles correspondent aux dernières instructions stratégiques de l’entreprise.

**Révisions d’audit et création de rapports mensuelles :** Tous les mois, effectuez un audit sur tous les déploiements cloud afin de garantir leur alignement continu sur la stratégie Cohérence des ressources. Examinez les activités associées à la stratégie avec le personnel informatique, puis identifiez les problèmes de conformité qui n’ont pas encore été pris en charge par le processus d’application et de supervision continues. Le résultat de cette révision est un rapport pour l’équipe de la stratégie cloud et chaque équipe d’adoption du cloud afin de communiquer sur les performances et l’adhésion générales vis-à-vis de la stratégie. Le rapport est également conservé à des fins d’audit et juridiques.

## <a name="ongoing-monitoring-processes"></a>Processus de supervision continue

Votre stratégie de gouvernance Cohérence des ressources réussit si l’état actuel et passé de votre infrastructure cloud est clairement identifiable. Si vous ne pouvez pas analyser les mesures et données pertinentes au sujet de l’intégrité et de l’activité de votre environnement cloud, vous ne pourrez pas identifier les changements de risques ni détecter les violations de vos tolérances aux risques. Les processus de gouvernance continue indiqués ci-dessus nécessitent des données de qualité pour s’assurer que la stratégie peut être modifiée. De cette manière, vous pouvez optimiser l’utilisation des ressources cloud et améliorer les performances globales des charges de travail hébergées sur le cloud.

Assurez-vous que vos équipes informatiques ont implémenté des systèmes de supervision automatisés pour votre infrastructure cloud recueillant les données de journaux d’activité pertinentes dont vous avez besoin pour évaluer les risques. Soyez proactif dans le cadre de la supervision de ces systèmes afin d’assurer la détection et l’atténuation rapides des violations potentielles des stratégies, et assurez-vous que votre stratégie de supervision est conforme à vos besoins opérationnels.

## <a name="violation-triggers-and-enforcement-actions"></a>Déclencheurs relatifs aux violations et actions de mise en conformité

Étant donné que la conformité à la stratégie Cohérence des ressources peut entraîner une interruption de service critique ou des risques de dépassements de coût significatifs, l’équipe de gouvernance cloud doit bénéficier d’une grande visibilité sur les incidents de non-conformité. Veillez à ce que le personnel informatique dispose de procédures d’escalade claires pour signaler ces problèmes aux membres de l’équipe de gouvernance les mieux placés pour identifier et vérifier que les problèmes de stratégie sont atténués une fois détectés.

Lorsque des violations sont détectées, vous devez prendre des actions conformes à la stratégie dès que possible. Votre équipe informatique peut automatiser la plupart des déclencheurs relatifs aux violations à l’aide des outils présentés dans la [chaîne d’outils Cohérence des ressources pour Azure](./toolchain.md).

Les déclencheurs et mesures d’application ci-après fournissent des exemples auxquels vous pouvez vous référer lorsque vous planifiez d’utiliser les données de supervision pour résoudre les violations des stratégies :

- **Ressource sur-provisionnée détectée.** Les ressources détectées qui utilisent moins de 60 % de la capacité de la mémoire ou de l’UC doivent automatiquement descendre en puissance ou déprovisionner les ressources pour réduire les coûts.
- **Ressource sous-provisionnée détectée.** Les ressources détectées qui utilisent plus de 80 % de la capacité de la mémoire ou de l’UC doivent automatiquement monter en puissance ou approvisionner des ressources supplémentaires afin d’augmenter la capacité.
- **Création de ressources sans catégorie.** Toute requête demandant la création d’une ressource sans les balises Meta requises sera automatiquement rejetée.
- **Panne de ressource critique détectée.** Le personnel informatique est informé de toutes les pannes détectées sur des ressources critiques. Si la panne ne peut pas être résolue immédiatement, le personnel fait remonter le problème aux propriétaires de la charge de travail et à l’équipe de gouvernance cloud. L’équipe de gouvernance cloud effectue un suivi du problème jusqu’à obtenir des instructions de résolution et de mise à jour si la révision de la stratégie est nécessaire pour empêcher l’apparition de futurs incidents.
- **Dérives de configuration.** Des alertes doivent être déclenchées dès lors que des ressources non conformes aux bases de référence établies sont détectées, et ces ressources doivent être corrigées automatiquement à l’aide d’outils de gestion de configuration comme Azure Automation, Chef, Puppet, Ansible, etc.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de gestion cloud](./template.md), documentez les processus et les déclencheurs qui correspondent au plan d’adoption du cloud actuel.

Pour obtenir des conseils sur l’exécution des stratégies de gestion cloud en harmonie avec les plans d’adoption, consultez l’article sur l’amélioration de la discipline.

> [!div class="nextstepaction"]
> [Amélioration de la discipline Cohérence des ressources](./discipline-improvement.md)
