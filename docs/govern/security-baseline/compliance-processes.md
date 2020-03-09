---
title: Base de référence de la sécurité des processus de conformité à la stratégie
description: Découvrez dans le Framework d’adoption du cloud pour Azure une approche de création de processus qui vont dans le sens d’une discipline de gouvernance de base de référence des identités.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 85286fd741cfdc1201eb436f3327993ac0337875
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77707440"
---
# <a name="security-baseline-policy-compliance-processes"></a>Base de référence de la sécurité des processus de conformité à la stratégie

Cet article décrit les processus d’adhésion à la stratégie, qui gouvernent la [base de référence de la sécurité](./index.md). Pour être efficace, une gouvernance de sécurité du cloud implique plusieurs processus manuels récurrents qui visent à détecter les vulnérabilités et à imposer des stratégies de correction de ces risques de sécurité. De fait, l’équipe de gouvernance cloud ainsi que les équipes informatiques et métier des parties prenantes intéressées sont régulièrement sollicitées pour examiner et mettre à jour la stratégie, et veiller au respect de cette dernière. En outre, de nombreux processus de supervision et d’application continues peuvent être automatisés ou complétés par des outils afin de réduire la charge de gouvernance et accélérer la réponse en cas de manquement à la stratégie.

## <a name="planning-review-and-reporting-processes"></a>Processus de planification, de révision et de génération de rapports

Les outils de base de référence de la sécurité du cloud ne peuvent pas surpasser les processus et stratégies qu’ils appuient. Les éléments suivants représentent un ensemble d’exemples de processus généralement impliqués dans la discipline Base de référence de la sécurité. Ces exemples constituent des points de départ pour planifier les processus qui vous permettront de mettre à jour la stratégie de sécurité à mesure que l’entreprise évolue et selon les commentaires des équipes informatiques chargés d’implémenter les mesures de gouvernance.

**Évaluation des risques et planification initiales :** Dans le cadre de l’adoption initiale de la discipline de base de référence de la sécurité, identifiez vos principaux risques métier et tolérances liés à la sécurité du cloud. Utilisez ces informations pour débattre des techniques spécifiques avec les membres de vos équipes informatiques et de sécurité, puis développer un ensemble de stratégies de sécurité de base pour atténuer ces risques et ainsi établir votre stratégie de gouvernance initiale.

**Planification du déploiement :** Avant de déployer n’importe quelle charge de travail ou ressource, effectuez une révision de la sécurité afin d’identifier tout nouveau risque et de vous assurer que toutes les exigences de la stratégie d’accès et de sécurité des données sont respectées.

**Test de déploiement :** Dans le cadre du processus de déploiement de n’importe quelle charge de travail ou ressource, l’équipe de gouvernance cloud, en collaboration avec les équipes de sécurité de votre entreprise, sera responsable du passage en revue du déploiement pour valider la conformité à la stratégie de sécurité.

**Planification annuelle :** Tous les ans, effectuez une révision de haut niveau de la stratégie de base de référence de la sécurité des ressources. Étudiez les priorités de l’entreprise pour l’avenir et les stratégies d’adoption du cloud mises à jour afin d’identifier l’augmentation des risques potentiels ou d’autres besoins en sécurité émergents. Utilisez ce temps de révision annuelle pour examiner les dernières meilleures pratiques liées aux bases de référence de la sécurité et intégrez-les dans vos stratégies et processus de révision.

**Planification et révision trimestrielles :** Tous les trimestres, effectuez une révision des données d’audit de sécurité et des rapports d’incident afin d’identifier les modifications requises dans la stratégie de sécurité. Dans le cadre de ce processus, passez en revue les ressources de cybersécurité afin d’anticiper de manière proactive les nouvelles menaces et mettre à jour la stratégie, le cas échéant. Une fois l’examen terminé, assurez-vous de la conformité des mesures de conception à la stratégie mise à jour.

Ce processus de planification constitue également un moment idéal pour évaluer les lacunes des membres de votre équipe de gouvernance cloud en lien avec les risques, nouveaux ou changeants, associés à la sécurité. Invitez le personnel informatique concerné à participer aux révisions et à la planification en tant que conseillers techniques temporaires ou membres permanents de votre équipe.

**Apprentissage et formation :** Deux fois par mois, offrez des sessions de formation pour vous assurer que le personnel informatique et les développeurs connaissent les dernières exigences en matière de sécurité. Dans le cadre de ce processus, relisez et mettez à jour toute la documentation, les guides et les autres ressources de formation pour vous assurer qu’ils correspondent aux dernières instructions stratégiques de l’entreprise.

**Révisions d’audit et création de rapports mensuelles :** Tous les mois, effectuez un audit sur tous les déploiements cloud afin de garantir leur alignement continu sur la stratégie de sécurité. Examinez les activités de sécurité avec le personnel informatique, puis identifiez les problèmes de conformité qui n’ont pas encore été pris en charge par le processus d’application et de supervision continues. Cet examen produit un rapport pour l’équipe de la stratégie cloud et chaque équipe d’adoption du cloud afin de communiquer sur l’adhésion générale des parties prenantes à la stratégie. Le rapport est également conservé à des fins d’audit et juridiques.

## <a name="ongoing-monitoring-processes"></a>Processus de supervision continue

Votre stratégie de gouvernance de sécurité réussit si l’état actuel et passé de votre infrastructure cloud est clairement identifiable. Si vous ne pouvez pas analyser les mesures et données pertinentes au sujet de l’intégrité et de l’activité de vos ressources cloud, vous ne pourrez pas identifier les changements de risques ni détecter les violations de vos tolérances aux risques. Les processus de gouvernance continus décrits ci-dessus exigent que vous fournissiez des données de qualité afin d’être capable de modifier la stratégie pour protéger votre infrastructure au mieux face à l’évolution des menaces et des exigences en matière de sécurité.

Assurez-vous que vos équipes de sécurité et informatiques ont mis en place des systèmes de supervision automatisés pour votre infrastructure cloud recueillant les données de journaux d’activité pertinentes dont vous avez besoin pour évaluer les risques. Soyez proactif dans le cadre de la surveillance de ces systèmes afin d’assurer la détection et l’atténuation rapides des violations potentielles des stratégies, et assurez-vous que votre stratégie de supervision est conforme aux besoins en matière de sécurité.

## <a name="violation-triggers-and-enforcement-actions"></a>Déclencheurs relatifs aux violations et actions de mise en conformité

Comme le non-respect des règles de sécurité peut entraîner des erreurs critiques et une divulgation de données ainsi que des risques d’interruption de service, l’équipe de gouvernance cloud doit disposer d’une visibilité totale sur les violations graves des stratégies. Veillez à ce que le personnel informatique dispose de chemins d’escalade clairs pour signaler les problèmes de sécurité aux membres de l’équipe de gouvernance les mieux placés pour identifier et vérifier que les problèmes de stratégie sont atténués.

Lorsque des violations sont détectées, vous devez prendre des actions conformes à la stratégie dès que possible. Votre équipe informatique peut automatiser la plupart des déclencheurs relatifs aux violations à l’aide des outils présentés dans la [chaîne d’outils Base de référence de la sécurité pour Azure](./toolchain.md).

Les déclencheurs et mesures d’application ci-après fournissent des exemples auxquels vous pouvez vous référer lorsque vous planifiez d’utiliser les données de supervision pour résoudre les violations des stratégies :

- **Augmentation du nombre d’attaques détectées.** Si une ressource subit une augmentation de 25 % du nombre d’attaques par force brute ou DDoS, discutez avec le personnel du service de sécurité informatique et le propriétaire de la charge de travail pour déterminer les solutions. Suivez la résolution des problèmes et actualisez votre assistance si une révision de la stratégie est nécessaire pour prévenir d’autres incidents.
- **Données non classifiées détectées.** L’accès externe sera refusé à n’importe quelle source de données dont l’impact sur la confidentialité, la sécurité ou les activités n’aura pas été correctement classifié. Cet accès sera rétabli lorsque le propriétaire des données aura appliqué la classification et le niveau de protection des données appropriés.
- **Problème d’intégrité de la sécurité détecté.** Désactivez l’accès à toutes les machines virtuelles vulnérables, ou auxquelles des logiciels malveillants ont pu accéder, jusqu’à ce que des correctifs ou logiciels de sécurité appropriés soient installés. Mettez à jour les conseils stratégiques à prendre en compte pour chaque nouvelle menace détectée.
- **Vulnérabilité du réseau détectée.** L’accès à toute ressource non explicitement autorisée par les stratégies d’accès au réseau doit alerter le personnel informatique et de sécurité, ainsi que le propriétaire de la charge de travail concernée. Suivez la résolution des problèmes et actualisez votre assistance si une révision de la stratégie est nécessaire pour réduire les risques d’autres incidents.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de gestion cloud](./template.md), documentez les processus et les déclencheurs qui correspondent au plan d’adoption du cloud actuel.

Pour obtenir des conseils sur l’exécution des stratégies de gestion cloud en harmonie avec les plans d’adoption, consultez l’article sur l’amélioration de la discipline.

> [!div class="nextstepaction"]
> [Amélioration de la discipline Base de référence de la sécurité](./discipline-improvement.md)
