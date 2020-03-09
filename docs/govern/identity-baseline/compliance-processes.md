---
title: Base de référence de l’identité des processus de conformité à la stratégie
description: Utilisez le Framework d’adoption du cloud pour Azure pour découvrir une approche de création de processus qui vont dans le sens d’une discipline de gouvernance de base de référence des identités.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ba23836fdcfcd8dee6f90707487142f755e525b8
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706981"
---
# <a name="identity-baseline-policy-compliance-processes"></a>Base de référence de l’identité des processus de conformité à la stratégie

Cet article décrit les processus d’adhésion à la stratégie, qui gouvernent la [base de référence de l’identité](./index.md). Une gouvernance efficace de l’identité commence par des processus manuels récurrents qui guident l’adoption et la révision des stratégies d’identité. De fait, l’équipe de gouvernance cloud ainsi que les équipes informatiques et métier des parties prenantes intéressées sont régulièrement sollicitées pour examiner et mettre à jour la stratégie, et veiller au respect de cette dernière. En outre, de nombreux processus de supervision et d’application continues peuvent être automatisés ou complétés par des outils afin de réduire la charge de gouvernance et accélérer la réponse en cas de manquement à la stratégie.

## <a name="planning-review-and-reporting-processes"></a>Processus de planification, de révision et de génération de rapports

Les outils de gestion des identités offrent des capacités et des fonctionnalités qui facilitent grandement la gestion des utilisateurs et le contrôle d’accès dans un déploiement cloud. Cependant, ils exigent également des processus et des stratégies bien pensés pour soutenir les objectifs de votre organisation. Les éléments suivants représentent un ensemble d’exemples de processus généralement impliqués dans la discipline Base de référence de l’identité. Ces exemples constituent des points de départ pour planifier les processus qui vous permettront de mettre à jour la stratégie d’identité à mesure que l’entreprise évolue et selon les commentaires des équipes informatiques chargés d’implémenter les mesures de gouvernance.

**Évaluation des risques et planification initiales :** Dans le cadre de l’adoption initiale de la discipline de base de référence de l’identité, identifiez vos principaux risques métier et tolérances liés à la gestion des identités du cloud. Utilisez ces informations pour débattre des techniques spécifiques avec les membres de vos équipes informatiques responsables de la gestion des services d’identité, puis développer un ensemble de stratégies de sécurité de base pour atténuer ces risques et ainsi établir votre stratégie de gouvernance initiale.

**Planification du déploiement :** Avant tout déploiement, passez en revue les besoins d’accès pour toutes les charges de travail et élaborez une stratégie de contrôle d’accès qui s’aligne sur la stratégie d’identité d’entreprise établie. Documenter tout écart entre les besoins et la stratégie actuelle afin de déterminer si des mises à jour de la stratégie sont nécessaires, et modifier la stratégie au besoin.

**Test de déploiement :** Dans le cadre du processus de déploiement, l’équipe de gouvernance cloud, en collaboration avec les équipes informatiques responsables des services d’identité, est tenue de passer en revue le déploiement pour valider la conformité à la stratégie d’identité.

**Planification annuelle :** Tous les ans, effectuez une révision de haut niveau de la stratégie de gestion des identités. Explorez les changements prévus dans l’environnement des services d’identité et les stratégies mises à jour d’adoption de l’informatique dans le cloud afin d’identifier les risques potentiels d’augmentation ou la nécessité de modifier les modèles actuels d’infrastructure d’identité. Utilisez ce temps de révision annuelle pour examiner les dernières meilleures pratiques liées aux bases de référence de la gestion des identités et intégrez-les dans vos stratégies et processus de révision.

**Planification trimestrielle :** Tous les trimestres, effectuez un examen général des données de vérification de l’identité et du contrôle d’accès, et rencontrez les équipes d’adoption cloud afin d’identifier tout nouveau risque potentiel, ou toute nouvelle exigence opérationnelle qui nécessiterait des mises à jour de la stratégie d’identité ou des changements dans la stratégie de contrôle d’accès.

Ce processus de planification constitue également un moment idéal pour évaluer les lacunes des membres de votre équipe de gouvernance cloud, en lien avec les risques, nouveaux ou changeants, associés à l’identité. Invitez le personnel informatique concerné à participer aux révisions et à la planification en tant que conseillers techniques temporaires ou membres permanents de votre équipe.

**Apprentissage et formation :** Deux fois par mois, offrez des sessions de formation pour vous assurer que le personnel informatique et les développeurs connaissent les dernières exigences en matière de stratégie d’identité. Dans le cadre de ce processus, relisez et mettez à jour toute la documentation, les guides et les autres ressources de formation pour vous assurer qu’ils correspondent aux dernières instructions stratégiques de l’entreprise.

**Révisions d’audit et création de rapports mensuelles :** Tous les mois, effectuez un audit sur tous les déploiements cloud afin de garantir leur alignement continu sur la stratégie d’identité. Profitez de cet examen pour vérifier l’accès des utilisateurs par rapport aux changements opérationnels afin de vous assurer que les utilisateurs ont un accès correct aux ressources cloud et que les stratégies d’accès telles que le contrôle d’accès en fonction du rôle (RBAC) sont suivies de façon cohérente. Identifiez tous les comptes privilégiés et documentez leur raison d’être. Cette procédure d’examen produit un rapport pour l’équipe de la stratégie cloud et pour chaque équipe d’adoption du cloud, afin de détailler l’adhésion générale des parties prenantes à la stratégie. Le rapport est également conservé à des fins d’audit et juridiques.

## <a name="processes-for-ongoing-monitoring"></a>Processus de surveillance continue

Votre stratégie de gouvernance d’identité réussit si l’état actuel et passé de vos systèmes d’identité est clairement identifiable. Si vous ne pouvez pas analyser les mesures et données pertinentes au sujet du déploiement de votre cloud, vous ne pourrez pas identifier les changements de risques ni détecter les violations de vos tolérances aux risques. Les processus de gouvernance en cours évoqués précédemment exigent des données de qualité pour s’assurer que la stratégie peut être modifiée afin de répondre à l’évolution des besoins de votre entreprise.

Assurez-vous que vos équipes informatiques ont implémenté des systèmes de supervision automatisés pour vos services d’identité recueillant les journaux d’activité et les informations d’audit dont vous avez besoin pour évaluer les risques. Soyez proactif dans le cadre de la surveillance de ces systèmes afin d’assurer la détection et l’atténuation rapides des violations potentielles des stratégies, et assurez-vous que tout changement apporté à votre infrastructure d’identité se reflète dans votre stratégie de surveillance.

## <a name="violation-triggers-and-enforcement-actions"></a>Déclencheurs relatifs aux violations et actions de mise en conformité

Les violations de la stratégie d’identité peuvent entraîner un accès non autorisé à des données sensibles et entraîner de graves perturbations des applications et des services essentiels à la mission. Lorsque des violations sont détectées, vous devez prendre des actions conformes à la stratégie dès que possible. Votre équipe informatique peut automatiser la plupart des déclencheurs relatifs aux violations à l’aide des outils présentés dans la [chaîne d’outils Base de référence d’identité](./toolchain.md).

Les déclencheurs et mesures d’application ci-après fournissent des exemples auxquels vous pouvez vous référer lorsque vous planifiez d’utiliser les données de supervision pour résoudre les violations des stratégies :

- **Activité suspecte détectée :** Les connexions d’utilisateurs détectées à partir d’adresses IP de proxy anonymes, d’emplacements inconnus ou de connexions successives à partir d’emplacements géographiques incroyablement éloignés peuvent indiquer une violation potentielle du compte ou une tentative d’accès malveillant. La connexion sera bloquée jusqu’à ce que l’identité de l’utilisateur puisse être vérifiée et le mot de passe réinitialisé.
- **Informations d’identification d’utilisateur divulguées :** Les comptes dont le nom d’utilisateur et le mot de passe ont été divulgués sur Internet seront désactivés jusqu’à ce que l’identité de l’utilisateur puisse être vérifiée et le mot de passe réinitialisé.
- **Contrôles d’accès insuffisants détectés :** Toute ressource protégée dont les restrictions d’accès ne répondent pas aux exigences de sécurité sera bloqué jusqu’à ce que la ressource soit mise en conformité.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de gestion cloud](./template.md), documentez les processus et les déclencheurs qui correspondent au plan d’adoption du cloud actuel.

Pour obtenir des conseils sur l’exécution des stratégies de gestion cloud en harmonie avec les plans d’adoption, consultez l’article sur l’amélioration de la discipline.

> [!div class="nextstepaction"]
> [Amélioration de la discipline Base de référence des identités](./discipline-improvement.md)
