---
title: 'Bien démarrer : Sécuriser l’environnement de l’entreprise'
description: Commencez à intégrer la sécurité à des points critiques au cours de vos efforts et opérations d’adoption du cloud.
author: JanetCThomas
ms.author: janet
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 100d5c327fb6e87f0a355f5305ff83ebb972b020
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83400760"
---
<!-- cSpell:ignore CISO passwordless -->

# <a name="get-started-implement-security-across-the-enterprise-environment"></a>Bien démarrer : Implémenter la sécurité dans l’environnement de l’entreprise

La sécurité permet aux entreprises de créer des garanties de confidentialité, d’intégrité et de disponibilité avec, comme objectif essentiel, de se protéger contre l’impact potentiel sur les opérations d’actes malveillants et involontaires internes et externes. Cette feuille de route décrit les principales étapes qui permettent d’atténuer ou d’éviter les risques métier liés aux attaques de cybersécurité en établissant rapidement des pratiques de sécurité essentielles dans le cloud et en intégrant la sécurité à votre processus d’adoption du cloud.

Les étapes décrites dans ce guide sont destinées à tous les rôles qui prennent en charge les garanties de sécurité des environnements cloud et des zones d’atterrissage. Cela inclut les priorités concernant l’atténuation des risques immédiate et des conseils sur la génération d’une stratégie de sécurité moderne, en mettant en œuvre l’approche et en l’exécutant sur cette stratégie.

Différents éléments du Cloud Adoption Framework sont inclus dans ce guide pratique :

![Bien démarrer avec la sécurité d’entreprise](../_images/get-started/security-map.png)

En suivant les étapes décrites dans ce guide, vous pouvez intégrer de la sécurité à des points critiques du processus afin d’éviter des obstacles dans l’adoption du cloud et de réduire l’interruption de l’activité ou des opérations.

Microsoft a créé des fonctionnalités et des ressources pour vous permettre d’implémenter plus rapidement ces conseils de sécurité sur Microsoft Azure (référencé tout au long de ce document). Ces ressources sont conçues pour vous aider à établir, superviser et appliquer la sécurité. Elles sont fréquemment mises à jour et révisées.

Le diagramme suivant illustre l’approche holistique recommandée par Microsoft pour l’utilisation des conseils de sécurité et des outils de la plateforme afin d’établir la visibilité et le contrôle de la sécurité sur vos ressources cloud dans Azure.

![Diagramme relatif à la sécurité](../_images/security/security-diagram.png)

Effectuez les étapes suivantes pour planifier et exécuter votre stratégie afin de sécuriser vos ressources cloud et d’utiliser le cloud en vue de moderniser les opérations de sécurité :

## <a name="step-1-establish-essential-security-practices"></a>Étape 1 : Établir des pratiques de sécurité essentielles

La sécurité dans le cloud commence par des pratiques fiables. Que vous opériez déjà dans le cloud ou que vous planifiiez de l’adopter ultérieurement, il est important d’établir rapidement des pratiques de sécurité essentielles.

En plus de respecter toutes les exigences de conformité réglementaire explicites, nous vous recommandons d’effectuer les étapes suivantes pour relever les principaux défis de sécurité auxquels la plupart des entreprises sont confrontées quand elles migrent vers le cloud.

**Livrables et conseils de prise en charge :**

- **Technique :** atténuez les principaux risques et augmentez la visibilité et le contrôle des ressources en activant l’authentification sans mot de passe ou multifacteur pour les administrateurs, et en activant la protection contre les menaces pour les ressources cloud.
  - [Authentification sans mot de passe ou multifacteur pour les administrateurs](https://docs.microsoft.com/azure/architecture/framework/security/critical-impact-accounts#passwordless-or-multi-factor-authentication-for-admins)
  - [Opérations de sécurité](https://docs.microsoft.com/azure/architecture/framework/security/security-operations) et [protection contre les menaces dans Azure Security Center](https://docs.microsoft.com/azure/security-center/threat-protection)
- **Processus :** activez des décisions de sécurité rapides et une amélioration continue en attribuant des rôles et des responsabilités de sécurité, et en établissant un processus de réponse aux incidents.
  - [Clarifier les axes de responsabilité](https://docs.microsoft.com/azure/architecture/framework/security/governance#clear-lines-of-responsibility), [Attribuer des privilèges pour assurer la gestion de l’environnement](https://docs.microsoft.com/azure/architecture/framework/security/governance#assign-privileges-for-managing-the-environment) et Mettre en œuvre le degré de sécurisation <!-- TODO: Improve this and add link to AAF article -->
  - Rôles et responsabilités de sécurité <!-- TODO: add link to bookmark -->
  - [Guide de référence sur les réponses aux incidents](https://aka.ms/irrg)
- **Personnes :** fournissez aux équipes de sécurité la formation, les outils et l’accès nécessaires pour déployer et fonctionner correctement pendant la transition vers l’environnement cloud.
  - **Sensibilisez tout le monde aux concepts** relatifs à l’évolution du cloud et de la sécurité du cloud :
    - [Évolution de l’environnement des menaces, des rôles et des stratégies numériques](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#evolution-of-threat-environment-roles--digital-strategies-2004)
    - [Transformation de la sécurité, des stratégies, des outils et des menaces](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#transformation-of-security-strategies-tools--threats-1513)
  - **Formez le personnel technique** aux détails techniques sur les fonctionnalités de sécurité du cloud pour les plateformes qu’il utilise. Microsoft fournit une [documentation complète sur la sécurité Azure](https://docs.microsoft.com/azure/security).
- **Décisions à long terme concernant l’architecture :** établissez des bases durables avec les bonnes décisions. Il est très difficile et très coûteux de les changer par la suite.
  - [Créer une stratégie de segmentation d’entreprise et aligner les architectures techniques dessus (segmentation du réseau, segmentation des identités, etc.)](https://docs.microsoft.com/azure/architecture/framework/security/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)
  - [Annuaire d’entreprise unique](https://docs.microsoft.com/azure/architecture/framework/security/identity#single-enterprise-directory)
  - [Stratégie d’authentification pour les services](https://docs.microsoft.com/azure/architecture/framework/security/applications-services#prefer-identity-authentication-over-keys)
  - [Stratégie d’attribution des autorisations](https://docs.microsoft.com/azure/architecture/framework/security/critical-impact-accounts#avoid-granular-and-custom-permissions)

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et de support technique |
| --- | --- |
| <li> Équipe de sécurité du cloud <br><br><br> | <li> Équipe de stratégie cloud <li> Équipe d’adoption du cloud <li> Centre d’excellence du cloud ou équipe informatique centrale |

Au cours de cette étape initiale, les équipes de gouvernance doivent également commencer à coordonner la création de bases de référence de sécurité qui peuvent être supervisées, gérées et appliquées dans les différents environnements. Vous trouverez des conseils supplémentaires sur cette création à l’étape 4 ci-dessous.

> [!NOTE]
> Chaque organisation doit définir ses propres normes minimales, car l’état du risque et la tolérance ultérieure à ce risque peuvent varier considérablement en fonction du secteur, de la culture et d’autres facteurs. Par exemple, une banque peut ne tolérer aucune atteinte éventuelle à sa réputation, même par une attaque mineure sur un système de test, où certaines organisations accepteraient volontiers le même risque s’il accélérait leur transformation numérique de trois à six mois.

## <a name="step-2-modernize-security-strategy"></a>Étape 2 : Moderniser une stratégie de sécurité

Une sécurité efficace dans le cloud exige une solide stratégie qui reflète l’environnement actuel des menaces et la nature de la plateforme cloud qui héberge les ressources de l’entreprise. Une stratégie claire améliore l’effort de toutes les équipes pour fournir un environnement cloud d’entreprise sécurisé et durable qui réduit le risque métier. La stratégie de sécurité doit permettre des résultats métiers définis, réduire le risque à un niveau acceptable et permettre aux employés d’être productifs.

Une stratégie de sécurité du cloud fournit des conseils clairs à toutes les équipes qui travaillent sur les technologies, les processus et la préparation des personnes à cette adoption. La stratégie doit indiquer l’architecture et les capacités techniques du cloud, guider l’architecture et les capacités de la sécurité, et influencer la formation et la sensibilisation des équipes.

**Livrables :**

L’étape relative à la stratégie doit aboutir à un document qui peut être facilement communiqué à de nombreuses parties prenantes au sein de l’organisation, ce qui inclut éventuellement des cadres de l’équipe dirigeante de l’organisation.

C’est pourquoi nous vous recommandons de capturer la stratégie dans une présentation pour faciliter la discussion et la mise à jour. Cela peut également être étayé avec un document, en fonction de la culture et des préférences.

- **Présentation de la stratégie :** vous pouvez avoir une présentation unique de la stratégie, ou choisir de créer également une version résumée pour les audiences des dirigeants.
  - **Présentation complète :** cela doit inclure l’ensemble complet des éléments de la stratégie de sécurité dans la présentation principale ou dans des diapositives de référence facultatives.
  - **Résumés pour l’équipe dirigeante :** versions à utiliser avec les cadres supérieurs et les membres du Conseil d’administration, et qui contiennent uniquement des éléments essentiels pertinents pour le poste qu’ils occupent, comme le goût du risque, les priorités majeures ou les risques acceptés.
- Vous pouvez enregistrer les motivations, les résultats et la justification métier dans le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).

**Bonnes pratiques pour la création d’une stratégie de sécurité :**

Les programmes réussis intègrent les éléments suivants dans leur processus de stratégie de sécurité :

- **Alignez-vous fidèlement sur la stratégie d’entreprise :** la charte de sécurité est destinée à protéger la valeur métier. Il est donc essentiel de converger tous les efforts de sécurité vers celle-ci et de minimiser le conflit interne.
  - **Créer une compréhension partagée :** des exigences métier, informatiques et de sécurité.
  - **Intégrez la sécurité tôt dans l’adoption du cloud :** pour éviter des crises de dernière minute dues à des risques évitables.
  - **Approche agile :** Pour établir immédiatement des exigences de sécurité minimales et améliorer en permanence les garanties de sécurité au fil du temps.
  - **Changement de culture de sécurité :** par le biais d’actions proactives intentionnelles de la Direction.

Pour plus d’informations, consultez [Transformations, états d’esprit et attentes](../strategy/define-security-strategy.md#transformations-mindsets-and-expectations).

- **Modernisez une stratégie de sécurité :** la stratégie de sécurité doit inclure des considérations sur tous les aspects de l’environnement de technologies modernes, du paysage actuel des menaces et des ressources de la communauté de sécurité.
  - **Adaptez-vous au modèle de responsabilité partagée** du cloud.
  - **Incluez tous les types de cloud et le multicloud.**
  - **Préférez les contrôles cloud natifs** pour éviter les frictions inutiles et dangereuses.
  - **Intégration de la communauté de sécurité :** pour suivre le rythme de l’évolution des attaquants.

**Ressources associées pour plus de contexte :**

- [Évolution de l’environnement des menaces, des rôles et des stratégies numériques](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#evolution-of-threat-environment-roles--digital-strategies-2004)
- [Transformation de la sécurité, des stratégies, des outils et des menaces](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#transformation-of-security-strategies-tools--threats-1513)
- Considérations relatives à la stratégie Cloud Adoption Framework :
  - [Moderniser votre stratégie de sécurité](../strategy/define-security-strategy.md#modernize-your-security-strategy)
  - [Résilience de la cybersécurité](../strategy/define-security-strategy.md#cybersecurity-resilience)
  - [Comment le cloud change les relations et les responsabilités de sécurité](../strategy/define-security-strategy.md#how-the-cloud-is-changing-security)

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et de support technique |
| --- | --- |
| <li> Équipe dirigeante chargée de la sécurité (responsable de la sécurité des systèmes d’information (CISO) ou équivalent) | <li> Équipe de stratégie cloud <li> Équipe de sécurité du cloud <li> Équipe d’adoption du cloud <li> Centre d’excellence du cloud ou équipe informatique centrale |

**Approbation de la stratégie :** l’équipe de direction et les responsables de l’entreprise ayant la responsabilité des résultats métier ou des risques métier des branches d’activité au sein de l’organisation (cela peut inclure le Conseil d’administration, en fonction de l’organisation).

## <a name="step-3-develop-a-security-plan"></a>Étape 3 : Développer un plan de sécurité

La planification fait appliquer la stratégie de sécurité en définissant les résultats, les étapes majeures, les chronologies et les propriétaires des tâches. Ce plan présente également les rôles et les responsabilités des équipes.

La planification de la sécurité et la planification de l’adoption du cloud ne doivent pas être effectuées de manière isolée. Il est essentiel d’inviter l’équipe de sécurité du cloud tôt dans les cycles de planification pour éviter une interruption du travail ou un risque accru en raison de problèmes de sécurité découverts trop tardivement. Une connaissance approfondie et une prise en compte de l’espace numérique, ainsi qu’un portefeuille informatique existant déjà pleinement intégré au processus de planification cloud contribuent à un fonctionnement optimal de la planification de la sécurité.

**Livrables :**

- **Plan de sécurité :** doit faire partie de la documentation de planification principale pour le cloud et peut être un document qui utilise le [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx), un jeu de diapositives détaillé, un fichier projet ou une combinaison de ces formats, en fonction de la taille, de la culture et des pratiques standard de l’organisation.

- Le plan de sécurité doit inclure tous les éléments suivants :

  - **Plan des fonctions de l’organisation :** les équipes savent ainsi comment les rôles et les responsabilités de sécurité actuels changeront avec la migration vers le cloud.
    - **Plan des compétences en sécurité** pour prendre en charge les membres de l’équipe quand ils parcourent les changements significatifs concernant les technologies, les rôles et les responsabilités.
  - **Feuille de route de l’architecture et des fonctionnalités de sécurité technique :** pour guider les équipes techniques.
  Microsoft fournit des architectures de référence et des fonctionnalités de technologie pour vous aider lors de la création de votre architecture et de votre feuille de route, notamment :
    - [Composants et modèle de référence Azure](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151) pour accélérer la planification et la conception des rôles de sécurité Azure.
      ![Modèle d’administration Azure](../_images/security/azure-administration-model.png)
      ![Modèle RBAC Azure](../_images/security/azure-rbac-model.png)
    - [Architecture de référence pour la cybersécurité Microsoft](https://aka.ms/mcra) afin de créer une architecture globale pour la cybersécurité pour une entreprise hybride incluant des ressources locales et cloud.
    - [Architecture de référence du centre des opérations de sécurité (SOC)](https://docs.microsoft.com/security/compass/security-operations-videos-and-decks#part-1-introduction---soc-learnings-strategies-and-technical-integration-2430) pour moderniser la détection des problèmes de sécurité, la réponse à y apporter et la récupération qui suit.
    - [Architecture de référence de l’accès utilisateur de confiance zéro](https://docs.microsoft.com/security/ciso-workshop/ciso-workshop-module-3#part-5-zero-trust-user-access-reference-architecture-842) pour moderniser l’architecture de contrôle d’accès pour la génération dans le cloud.
    - [Azure Security Center](https://docs.microsoft.com/azure/security-center/) et [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/) pour sécuriser des ressources cloud.
  - **Plan de sensibilisation et de formation à la sécurité :** toutes les équipes ont des connaissances de base critiques sur la sécurité.
  - **Marquage de la sensibilité des ressources :** pour désigner des ressources sensibles à l’aide d’une taxonomie alignée sur l’impact pour l’activité (créée conjointement par les parties prenantes, les équipes de sécurité et d’autres parties intéressées).

- **Adoptez un environnement hybride :** cela inclut les applications SaaS (Software as a Service), les environnements locaux et plusieurs fournisseurs de cloud IaaS (Infrastructure as a Service) et PaaS (Platform as a Service) (le cas échéant).
- **Mettez à jour le plan de cloud avec des changements de sécurité :** mettez à jour d’autres sections du plan d’adoption du cloud principal pour refléter les changements déclenchés par le plan de sécurité.

**Bonnes pratiques pour la planification de la sécurité :** votre plan de sécurité est généralement plus efficace si votre planification adopte l’approche suivante :

- **Adoption de la sécurité agile :** établissez des exigences de sécurité minimales et déplacez tous les éléments non critiques vers une liste hiérarchisée d’étapes suivantes.
Cela ne doit pas être un plan détaillé traditionnel de 3 à 5 ans, car le cloud et l’environnement des menaces changent trop rapidement pour que ce type de plan soit utile. Votre plan doit se concentrer sur le développement des étapes de début et l’état de fin :
  - **Gains rapides :** plan détaillé pour le futur immédiat visant à identifier les gains rapides et à commencer des initiatives à plus long terme qui auront un fort impact. Ce peut être pour 3 à 12 mois en fonction de la culture de l’organisation, des pratiques standard et d’autres facteurs.
  - **Vision claire** de l’état final souhaité pour guider le processus de planification de chaque équipe (dont l’aboutissement peut prendre plusieurs années).
- **Vaste partage du plan :** pour contribuer à la sensibilisation des parties prenantes, augmenter leurs commentaires et accroître leur engagement.
- **Atteindre les résultats stratégiques :** vérifiez que votre plan s’aligne sur les résultats stratégiques décrits dans la stratégie de sécurité et les atteint.
- **Propriété, responsabilité et échéances :** vérifiez que les propriétaires de chaque tâche sont identifiés et qu’ils sont validés pour accomplir cette tâche dans un délai spécifique.
- **Connectez-vous au côté humain de la sécurité :** pour recruter des personnes pendant cette transformation de durée et exprimer de nouvelles attentes de la façon suivante :
  - **Prise en charge active de la transformation des membres d’une équipe :** Avec une communication claire et un coaching sur :
    - Les compétences qu’ils doivent acquérir
    - La raison pour laquelle ils doivent les acquérir (et les avantages que cela présente)
    - La façon d’obtenir ces connaissances (et de fournir des ressources pour les aider à les acquérir).
  Ces informations peuvent être documentées à l’aide du [modèle de stratégie et de plan](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx) et vous pouvez utiliser la [formation en ligne Microsoft sur la sécurité](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction) pour faciliter la formation des membres de votre équipe.
  - **Rendez la sensibilisation à la sécurité attrayante :** pour permettre aux utilisateurs de se reconnaître réellement dans le rôle qu’ils jouent dans le maintien de la sécurité de l’organisation.
- **Passez en revue les enseignements et conseils de Microsoft :** Microsoft a publié des insights et des points de vue pour aider votre organisation à planifier sa transformation vers le cloud et une stratégie de sécurité moderne incluant des formations enregistrées, de la documentation, ainsi que les bonnes pratiques de sécurité et les normes recommandées.
  Pour obtenir des conseils techniques pour vous aider à créer votre plan et votre architecture, consultez la [documentation sur la sécurité de Microsoft](https://docs.microsoft.com/security).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et de support technique |
| --- | --- |
| <li> Équipe de sécurité du cloud | <li> Équipe de stratégie cloud <li> Équipe de gouvernance cloud <li> Toutes les équipes chargées des risques de votre organisation <li> Centre d’excellence du cloud ou équipe informatique centrale |

**Approbation du plan de sécurité :** Équipe dirigeante chargée de la sécurité (CISO ou équivalent).

## <a name="step-4-secure-new-workloads"></a>Étape 4 : Sécuriser les nouvelles charges de travail

Il est beaucoup plus facile de démarrer dans un état sécurisé que de réajuster la sécurité ultérieurement dans votre environnement. Nous vous recommandons vivement de commencer avec une configuration sécurisée pour garantir que les charges de travail sont migrées vers un environnement sécurisé, où elles sont également développées et testées.

Pendant l’implémentation de la [zone d’atterrissage](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/landing-zone), de nombreuses décisions peuvent affecter la sécurité et les profils de risque. L’équipe de sécurité du cloud doit passer en revue la configuration de la zone d’atterrissage pour garantir qu’elle répond aux normes et exigences de sécurité dans les bases de référence de sécurité de votre organisation.

**Livrables :**

- Vérifiez que les nouvelles zones d’atterrissage répondent aux exigences de conformité et de sécurité de l’organisation.

**Conseils pour la prise en charge de l’achèvement des livrables :**

- **Combinaison d’exigences existantes et de recommandations concernant le cloud :** commencez par les recommandations, puis adaptez-les aux exigences de sécurité qui vous sont propres. Nous avons fait face à des difficultés lors de la tentative d’application de normes et de stratégies locales existantes, car elles font souvent référence à des technologies ou des approches de sécurité obsolètes. Microsoft a publié des conseils pour vous permettre de créer vos bases de référence de sécurité :
  - [Normes de sécurité Azure pour la stratégie et l’architecture](https://docs.microsoft.com/security/compass/compass) : recommandations sur la stratégie et l’architecture pour déterminer la posture de sécurité de votre environnement.
  - [Benchmarks de sécurité Azure](https://docs.microsoft.com/azure/security/benchmarks/introduction) : recommandations de configuration spécifiques pour la sécurisation des environnements Azure.
  - [Formation sur les bases de référence de sécurité Azure](https://docs.microsoft.com/learn/modules/create-security-baselines).
- **Fournissez des garde-fous** : ils doivent avoir un audit et une application automatisés des stratégies. Pour ces nouveaux environnements, les équipes doivent faire en sorte d’auditer et d’appliquer les bases de référence de sécurité de votre organisation afin de réduire les mauvaises surprises concernant la sécurité pendant le développement, ainsi que l’intégration continue et le déploiement continu (CI/CD) des charges de travail.
Microsoft fournit plusieurs fonctionnalités natives dans Azure pour le permettre :
  - [Degré de sécurisation](https://docs.microsoft.com/azure/security-center/secure-score-security-controls) : évaluation notée de votre posture de sécurité Azure qui vous permet d’effectuer le suivi des processus et projets relatifs à la sécurité dans votre organisation.
  - [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) : Les architectes cloud et les groupes de l’équipe informatique centrale peuvent définir un ensemble reproductible de ressources Azure qui implémentent et respectent les normes, modèles et exigences d’une organisation.
  - [Azure Policy](https://docs.microsoft.com/azure/governance/policy/) : la base des fonctionnalités de contrôle et de visibilité utilisées par ces autres services. Azure Policy est intégré à [Azure Resource Manager (ARM)](https://docs.microsoft.com/azure/azure-resource-manager), ce qui vous permet d’auditer les changements et d’appliquer des stratégies à toutes les ressources dans Azure avant, pendant ou après leur création.
- [Améliorer les opérations de zone d’atterrissage](../ready/considerations/landing-zone-security.md) : utilisez les bonnes pratiques concernant l’amélioration de la sécurité au sein d’une zone d’atterrissage donnée.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes en charge et de support technique |
| --- | --- |
| <li> Équipe de sécurité du cloud | <li> Équipe d’adoption du cloud <li> Équipe de plateforme cloud <li> Équipe de stratégie cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou équipe informatique centrale |

## <a name="step-5-secure-existing-cloud-workloads"></a>Étape 5 : Sécuriser les charges de travail cloud existantes

De nombreuses organisations ont déjà déployé des ressources dans des environnements cloud d’entreprise qui n’appliquaient pas les bonnes pratiques concernant la sécurité, créant ainsi des risques métier accrus.

Après avoir vérifié que les nouvelles applications et zones d’atterrissage suivent les bonnes pratiques concernant la sécurité, vous devez vous efforcer de mettre à niveau les environnements existants avec les mêmes normes.

**Livrables :**

- Vérifiez que l’ensemble des environnements cloud et zones d’atterrissage existants répondent aux exigences de conformité et de sécurité de l’organisation.
- Testez la disponibilité opérationnelle des déploiements de production à l’aide de stratégies Base de référence de sécurité.
- Validez le respect des conseils de conception et des exigences de sécurité des bases de référence de sécurité.

**Conseils pour la prise en charge de l’achèvement des livrables :**

- Utilisez les mêmes bases de référence de sécurité que celles que vous avez créées à l’[étape 4](#step-4-secure-new-workloads) comme votre état idéal. Il se peut que vous deviez ajuster certains paramètres de stratégie pour uniquement les auditer au lieu de les appliquer.
- Équilibrez les risques opérationnels et les risques de sécurité. Étant donné que ces environnements peuvent héberger des systèmes de production qui activent des processus métier critiques, vous devrez peut-être implémenter des améliorations de sécurité de façon incrémentielle pour éviter les risques de temps d’arrêt opérationnels.
- Hiérarchisez la détection et la remédiation du risque de sécurité en fonction du caractère critique pour l’entreprise, en commençant par les charges de travail qui ont un fort impact métier si elles sont compromises et par les charges de travail présentant un niveau d’exposition aux risques élevé.

Pour plus d’informations, consultez [identifier et classer les applications critiques pour l’entreprise](https://docs.microsoft.com/azure/architecture/framework/security/applications-services?toc=/security/compass/toc.json&bc=/security/compass/breadcrumb/toc.json#identify-and-classify-business-critical-applications).

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe d’adoption du cloud | <li> Équipe d’adoption du cloud <li> Équipe de stratégie cloud <li> Équipe de sécurité du cloud <li> Équipe de gouvernance cloud <li> Centre d’excellence du cloud ou informatique centralisée |

## <a name="step-6-govern-to-manage-and-improve-security-posture"></a>Étape 6 : Gouverner pour gérer et améliorer la posture de sécurité

À l’instar de toutes les disciplines modernes, la sécurité est un processus itératif qui doit se concentrer sur l’amélioration continue. La posture de sécurité peut également décliner si les organisations ne maintiennent pas leur concentration dessus au fil du temps.

Une application cohérente des exigences de sécurité vient de disciplines de gouvernance et de solutions automatisées fiables. Une fois la ou les bases de référence de sécurité définies par l’équipe de sécurité du cloud, ces exigences doivent être auditées pour garantir qu’elles sont appliquées de manière cohérente à tous les environnements cloud (et qu’elles sont mises en application, le cas échéant).

**Livrables :**

- Vérifiez que les bases de référence de sécurité de l’organisation sont appliquées à tous les systèmes appropriés et que les anomalies sont auditées à l’aide d’un [degré de sécurisation](https://docs.microsoft.com/azure/security-center/secure-score-security-controls) ou d’un mécanisme similaire.
- Documentez les stratégies de base de référence de sécurité, les processus et les conseils de conception dans le [Modèle de discipline Base de référence de sécurité](../govern/security-baseline/template.md).

**Conseils pour la prise en charge de l’achèvement des livrables :**

- Utilisez les bases de référence de sécurité et les mêmes mécanismes d’audit que vous avez créés à l’[étape 4](#step-4-secure-new-workloads) comme composants techniques de supervision des bases de référence, complétés par des personnes et des contrôles de processus afin de garantir la cohérence.
- Vérifiez que toutes les charges de travail et ressources suivent les [conventions de nommage et de catégorisation](../ready/azure-best-practices/naming-and-tagging.md) appropriées et [appliquez les conventions de catégorisation à l’aide d’Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/govern-tags), en mettant l’accent sur les étiquettes liées à la « sensibilité des données ».
- Si vous débutez avec la gouvernance cloud, établissez des [stratégies de gouvernance, des processus et des disciplines](../govern/index.md) à l’aide de la méthodologie de gouvernance.

<!-- markdownlint-disable MD033 -->
<br>

| Équipe responsable | Équipes responsable et de support |
| --- | --- |
| <li> Équipe de gouvernance cloud | <li> Équipe de stratégie cloud <li> Équipe de sécurité du cloud <li> Centre d’excellence du cloud ou équipe informatique centrale |

## <a name="next-steps"></a>Étapes suivantes

Ces étapes vous guideront tout au long de l’implémentation de la stratégie, des contrôles, des processus, des compétences et de la culture appropriés nécessaires pour gérer de manière cohérente les risques de sécurité au sein de l’entreprise.
À mesure que vous poursuivez l’exploration du mode de fonctionnement de la sécurité du cloud, envisagez d’effectuer les étapes suivantes dans une build suivant ces conseils de démarrage.

- Passez en revue la [documentation sur la sécurité de Microsoft](https://docs.microsoft.com/security) qui fournit des conseils techniques permettant aux professionnels de la sécurité de concevoir une stratégie, une architecture et des feuilles de route classées par ordre de priorité concernant la cybersécurité, puis de les améliorer.
- Passez en revue les informations de sécurité pour les [contrôles de sécurité intégrés des services Azure](https://docs.microsoft.com/azure/security/fundamentals/security-controls).
- Passez en revue les outils et services de sécurité Azure dans [Services et technologies de sécurité disponibles sur Azure](https://docs.microsoft.com/azure/security/azure-security-services-technologies).
- Consultez le [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trustcenter/guidance/risk-assessment), car il contient de nombreux conseils, rapports et documents connexes qui peuvent vous aider à effectuer des évaluations des risques dans le cadre de vos processus de conformité réglementaire.
- Passez en revue les outils tiers disponibles pour répondre plus facilement à vos exigences de sécurité. Pour plus d’informations, consultez [Intégrer les solutions de sécurité dans Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-partner-integration).
