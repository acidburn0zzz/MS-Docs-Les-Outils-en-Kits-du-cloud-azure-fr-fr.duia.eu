---
title: Refactorisation des zones d’atterrissage
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processus de refactorisation des zones d’atterrissage
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 8e1576afb56afd79a1028658609dc62c25775f75
ms.sourcegitcommit: 7660521b631ea092fb805df9c9d28ad3024287ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83621588"
---
# <a name="refactor-landing-zones"></a>Refactorisation des zones d’atterrissage

La zone d’atterrissage est un environnement permettant d’héberger vos charges de travail, **qui sont préprovisionnées par le biais de code**. Étant donné que l’infrastructure de zone d’atterrissage est définie dans le code, elle peut être refactorisée comme n’importe quel autre code base. La refactorisation est un processus qui consiste à modifier ou à restructurer le code source afin d’optimiser le résultat de ce code sans changer son rôle ou sa fonction principale.

La méthodologie Ready utilise le concept de refactorisation pour accélérer la migration et supprimer les points de blocage courants. Les étapes de la présentation Ready décrivent un processus qui commence par un modèle de zone d’atterrissage prédéfini qui correspond le mieux à votre fonction d’hébergement. Ensuite, refactorisez le code source ou faites-y des ajouts pour étendre la capacité des zones d’atterrissage à fournir cette fonction avec une sécurité, des opérations ou une gouvernance améliorées. L’image suivante illustre le concept de refactorisation.

![Illustration de la refactorisation de la zone d’atterrissage, décrit dans la section suivante de cet article](../../_images/ready/refactor.png)

## <a name="common-blockers"></a>Points de blocage courants

Lorsque les clients adoptent le cloud, les considérations relatives aux zones d’atterrissage représentent le point de blocage le plus courant pour l’adoption et les résultats liés au cloud. Les clients ont tendance pencher vers l’un des deux points de blocage suivants. La plupart du temps, les équipes penchent vers l’un de ces deux points de blocage, ce qui entraîne des blocages culturels qui compliquent l’adoption.

Les deux points de blocage principaux prennent racine dans une seule et même conviction, à savoir que l’environnement cloud et les centres de centres existants doivent être en parité ou presque au niveau des fonctionnalités des opérations, de la gouvernance et de la sécurité. Il s’agit d’un objectif à long terme. La difficulté vient cependant de l’équilibre délicat entre le moment où vous atteignez cet objectif et la rapidité nécessaire pour délivrer des résultats métier.

### <a name="blocker-acting-too-soon"></a>Point de blocage : Action trop précoce

Il a fallu des années et des efforts importants pour atteindre le niveau actuel de sécurité, de gouvernance et d’opérations dans les centres de données actuels. Il a également fallu des observations, des formations et une certaine personnalisation pour répondre aux contraintes uniques de cet environnement. La réplication des mêmes procédures et configurations prend du temps. Atteindre 100 % dans la parité des fonctionnalités peut également entraîner des performances médiocres de l’environnement qui s’exécute dans le cloud. Cette approche par parité est généralement synonyme de surcoûts non planifiés significatifs dans l’environnement cloud. N’essayez pas d’appliquer les exigences actuelles en matière d’état à un environnement futur comme jalon précoce. Une telle approche s’avère rarement rentable.

![Point de blocage courant : Action trop précoce](../../_images/ready/blocker-act-too-soon.png)

Dans l’image ci-dessus, le client a un objectif de 100 charges de travail dans le cloud. Pour y parvenir, il déploiera probablement sa première charge de travail. Puis les 10 premières charges de travail, avant qu’il ne soit prêt à mettre une de ces charges de travail en production. Enfin, il atteindra l’objectif du plan d’adoption et disposera d’un portefeuille robuste dans le cloud. Cependant, la croix rouge dans l’image indique le point où les clients sont généralement bloqués. Si vous attendez un alignement à 100 %, vous pouvez retarder la première charge de travail de plusieurs semaines ou plusieurs mois, voire plusieurs années.

### <a name="blocker-acting-too-late"></a>Point de blocage : Action trop tardive

En revanche, une action trop tardive peut avoir des conséquences importantes à long terme sur la réussite de l’adoption du cloud. Si l’équipe attend d’atteindre la parité des fonctionnalités pour terminer son travail d’adoption, elle rencontrera des obstacles inutiles et aura besoin de nombreuses interventions de sa hiérarchie pour que les efforts soient maintenus.

![Point de blocage courant : Action trop tardive](../../_images/ready/blocker-act-too-late.png)

Comme pour une action trop précoce, dans cette image, le client attend trop longtemps que les zones d’atterrissage soient prêtes. En attendant trop longtemps, le client sera obligé de limiter le volume de refactorisation et d’expansion qu’il peut effectuer dans l’environnement. Ces contraintes limitent sa capacité à assurer la suite du test.

### <a name="finding-balance"></a>Trouver le juste équilibre

Pour éviter ces points de blocage, nous suggérons une approche itérative basée sur un plan d’adoption du cloud bien structuré, qui optimise les opportunités d’apprentissage et réduit le temps de mise en œuvre. La refactorisation et les efforts en parallèle sont des éléments critiques de cette approche.

> [!WARNING]
> Les équipes d’adoption qui ont pour objectif à moyen terme (dans les 24 mois) d’**héberger plus de 1 000 ressources (applications, infrastructure ou ressources de données) dans le cloud** sont très peu susceptibles de parvenir à leurs fins en adoptant l’approche par refactorisation. La courbe d’apprentissage est trop abrupte et les délais trop serrés pour une approche organique de la transmission des compétences. Un point de départ plus complet nécessitant moins de personnalisation sera une meilleure voie d’accès pour atteindre vos objectifs. Vos partenaires de mise en œuvre seront probablement en mesure de vous guider vers une meilleure approche.

Le reste de cet article se concentre sur certaines contraintes clés qui peuvent favoriser l’approche par refactorisation tout en en minimisant les risques.

## <a name="theory"></a>Théorie

Le concept de refactorisation d’une zone d’atterrissage est simple en théorie, mais requiert des garde-fous bien définis. Le concept illustré ci-dessus présente le schéma de base comme suit. Quand vous êtes prêt à créer votre première zone d’atterrissage, commencez par une zone d’atterrissage initiale définie via un modèle. Une fois cette zone d’atterrissage déployée, utilisez les arbres de décision dans les articles suivants sous « Développer votre zone d’atterrissage » de cette série d’articles (voir la table des matières) pour refactoriser et faite des ajouts à votre zone d’atterrissage initiale. Répétez les arbres de décision et la refactorisation jusqu’à ce que vous disposiez d’un environnement d’entreprise conforme aux exigences de vos équipes de sécurité, d’exploitation et de gouvernance.

## <a name="development-approach"></a>Approche de développement

L’avantage d’une approche basée sur la refactorisation est la possibilité de créer des chemins d’itération parallèles pour le développement. L’image ci-dessous fournit un exemple de deux chemins d’itération parallèles : adoption du cloud et plateforme cloud. Ces deux chemins progressent à leur propre rythme, avec un risque minime de se convertir en point de blocage venant perturber les activités de ces deux équipes. L’alignement sur le plan d’adoption et les garde-fous de refactorisation constituent un ensemble d’accords sur les jalons, ce qui définit des dépendances d’état claires pour le futur.

![Itération parallèle de la zone d’atterrissage](../../_images/ready/iterations.png)

Dans les exemples de chemins d’itération ci-dessus, l’équipe chargée de l’adoption du cloud migre son portefeuille de 100 charges de travail vers le cloud. En parallèle, l’équipe de la plateforme cloud s’est concentrée sur le plan d’adoption du cloud afin de s’assurer que l’environnement soit prêt pour ces charges de travail.

Dans cet exemple, les itérations planifiées s’exécutent comme suit :

- L’équipe de la plateforme cloud initie le travail en déployant une zone d’atterrissage initiale. Cette zone d’atterrissage permet à l’équipe d’adoption du cloud de déployer et commencer à tester la première charge de travail.
- Pour préparer le prochain déploiement suivant de 10 charges de travail par l’équipe d’adoption du cloud, l’équipe de la plateforme cloud travaille à la refactorisation et à l’ajout d’un environnement connecté, en traitant le cloud comme une zone démilitarisée (DMZ).
- Pour que l’équipe d’adoption puisse mettre sa première charge de travail en production, l’équipe de sécurité doit examiner les conditions de sécurité. Tandis que l’équipe d’adoption déploie ses 10 premières charges de travail, l’équipe de la plateforme avance pour définir et implémenter les exigences de sécurité.
- Au moment de la mise en production de la première charge de travail, les deux équipes doivent avoir en appris suffisamment pour pouvoir préparer un modèle de service partagé à long terme. La centralisation des architectures de service principal aidera à aligner les objectifs de l’équipe de gouvernance et de l’équipe d’exploitation. La centralisation des services de base aide l’équipe d’adoption dans la mise à l’échelle et la mise en production des prochaines vagues de charges de travail de production.
- Lorsque l’équipe approche de l’objectif de migration de 100 charges de travail, elle commence sa transformation en une équipe d’excellence de collaboration cloud excellence et sert de modèle d’équipe.

La configuration d’un environnement d’entreprise peut prendre du temps. Cette approche n’élimine pas ce besoin. Cette approche est au contraire conçue pour supprimer les points de blocage précoces et susciter des opportunités d’apprentissage conjoint pour les équipes de plateforme et d’adoption.

## <a name="landing-zone-refactoring-guardrails"></a>Garde-fous de refactorisation de la zone d’atterrissage

Tous les modèles de zone d’atterrissage initiaux présentent des limitations. Les garde-fous ou les stratégies appliqués lors de la refactorisation doivent refléter ces limitations. Avant de commencer le processus de refactorisation des zones d’atterrissage, il est important de comprendre les exigences à long terme du plan d’adoption du cloud et la classification des charges de travail candidates en fonction des limitations initiales du modèle.

En guise d’exemple de garde-fous de refactorisation, comparons l’approche de développement de l’exemple précédent et le plan de zone d’atterrissage de la migration CAF.

- Selon les [détails des hypothèses du plan de la zone d’atterrissage pour la migration CAF](./migrate-landing-zone.md#assumptions), cette zone d’atterrissage initiale n’est pas conçue pour les charges de travail sensibles ou stratégiques. Ces fonctionnalités devront être ajoutées par le biais de la refactorisation.
- Dans cet exemple, supposons que le portefeuille de 100 charges de travail nécessite des fonctionnalités d’hébergement de données critiques et sensibles.

Pour répondre au mieux à ces deux exigences, l’équipe chargée de l’adoption et l’équipe plateforme travaillent dans les conditions suivantes :

- L’équipe chargée de l’adoption du cloud définira en priorité les charges de travail de production qui n’ont pas accès à des données sensibles et qui ne sont pas considérées comme critiques.
- Avant la mise en production, l’équipe de sécurité et l’équipe d’exploitation valideront l’alignement sur la stratégie précédente.
- L’équipe de la plateforme cloud collaborera avec les équipes de sécurité et de gouvernance pour implémenter une base de référence en matière de sécurité. Une fois que l’équipe de sécurité approuve l’implémentation, l’équipe d’adoption est autorisée à migrer les charges de travail qui ont accès à certaines données sensibles.
- L’équipe de la plateforme cloud travaille en collaboration avec l’équipe d’exploitation pour implémenter une base de référence en matière de gestion. Une fois que l’équipe d’exploitation approuve l’implémentation, l’équipe d’adoption reçoit l’autorisation de migrer les charges de travail plus critiques.

Dans cet exemple, le jeu de conditions définies permet à l’équipe d’adoption de commencer ses efforts de migration. Il permet également à l’équipe responsable de la plateforme de définir ses interactions avec les autres équipes dans le cadre de la création d’un environnement d’entreprise sur le long terme.

## <a name="meeting-long-term-requirements-while-refactoring"></a>Faire face aux exigences à long terme pendant la refactorisation

La section de la méthodologie Ready sur l’extension de votre zone d’atterrissage vous aidera à faire la transition vers les exigences à long terme. À mesure que l’équipe d’adoption du cloud progresse dans son plan d’adoption, la section liée au développement de votre zone d’atterrissage vous fournit des conseils pour prendre des décisions et effectuer la refactorisation conformément aux changements dans les besoins des différentes équipes.

![Itération parallèle de la zone d’atterrissage](../../_images/ready/refactor-methodologies.png)

Chaque sous-section de la partie liée au « développement de votre zone d’atterrissage » correspond à l’un des ajouts décrits dans l’image ci-dessus. Au-delà de ces expansions de base, certaines méthodologies plus approfondies (comme Govern ou Manage) de ce framework vous aideront à aller au-delà des modifications de base de la zone d’atterrissage pour mettre en place des disciplines à long terme.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer un processus de refactorisation, [choisissez votre première zone d’atterrissage](./first-landing-zone.md).

> [!div class="nextstepaction"]
> [Choisir votre première zone d’accueil](./first-landing-zone.md)
