---
title: Commencer un parcours de migration vers le cloud dans Azure
description: Obtenez des recommandations complètes pour transférer des charges de travail d’application héritées dans le cloud à l’aide de technologies cloud innovantes.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: ef04a867614c6597268269421ef1d341f5252f3b
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78223976"
---
# <a name="begin-a-cloud-migration-journey-in-azure"></a>Commencer un parcours de migration vers le cloud dans Azure

Utilisez Microsoft Cloud Adoption Framework pour Azure afin d’entamer un parcours de migration cloud. Ce framework fournit une aide complète sur la transition des charges de travail d’application héritées à l’aide de technologies novatrices basées sur le cloud.

## <a name="executive-summary"></a>Résumé

Cloud Adoption Framework aide les clients à effectuer un parcours d’adoption simplifié dans le cloud. Ce framework contient des informations détaillées qui couvrent un parcours d’adoption du cloud de bout en bout, en commençant par les résultats opérationnels ciblés, puis en alignant la préparation et l’évaluation du cloud à l’aide d’objectifs stratégiques clairement définis. Ces résultats sont obtenus via un chemin défini pour l’adoption du cloud. Avec l’adoption basée sur la migration, le chemin défini se concentre principalement sur la migration des charges de travail locales vers le cloud. Parfois, ce parcours comprend la modernisation des charges de travail pour augmenter le retour sur investissement de l’effort de migration.

Ce framework est principalement conçu pour les architectes cloud et les équipes de stratégie cloud qui dirigent les efforts d’adoption du cloud. Cependant, de nombreuses sujets contenus dans ce framework présentent un intérêt pour d’autres rôles au sein de l’entreprise et des services informatiques. Les architectes cloud servent souvent de facilitateurs pour faire participer chacun des rôles pertinents. Ce récapitulatif est conçu pour préparer les différents rôles avant de faciliter les conversations.

> [!NOTE]
> Cette aide est en préversion publique. La terminologie, les approches et l’aide fournies sont minutieusement testées par les clients, les partenaires et les équipes Microsoft au cours de cette préversion. Ainsi, la table des matières et l’aide peuvent changer légèrement au fil du temps.

## <a name="motivations"></a>Motivations

Les migrations cloud peuvent aider les entreprises à atteindre leurs résultats opérationnels souhaités. Une communication claire sur les motivations, les axes stratégiques et la mesure du succès sont des fondements importants pour la prise de décisions judicieuses tout au long des efforts de migration cloud. Le tableau suivant classe les motivations qui permettent de faciliter cette conversation. Il est supposé que la plupart des entreprises ont des motivations pour chaque classification. L’objectif de ce tableau n’est pas de limiter les résultats, mais de faciliter la hiérarchisation des motivations et des objectifs globaux :

<!-- markdownlint-disable MD033 -->

|Événements métier critiques | Motivations de la migration | Motivations de l’innovation |
|---------|---------|---------|
| Sortie du centre de données<br/><br/>Fusions, acquisitions ou cessions<br/><br/>Réductions des dépenses d’investissement<br/><br/>Fin de la prise en charge de technologies stratégiques<br/><br/>Réponse aux changements liés à la conformité réglementaire<br/><br/>Répondre aux nouvelles exigences liées à la souveraineté des données<br/><br/>Réduire les interruptions et améliorer la stabilité informatique|Réduction des coûts<br/><br/>Réduction de la complexité liée aux fournisseurs ou aux contraintes techniques<br/><br/>Optimisation des opérations internes<br/><br/>Augmenter la réactivité de l’entreprise<br/><br/>Se préparer à de nouvelles fonctionnalités techniques<br/><br/>Mettre à l’échelle pour répondre aux besoins du marché<br/><br/>Mettre à l’échelle pour répondre aux besoins d’une région ou du marché|Se préparer à de nouvelles fonctionnalités techniques<br/><br/>Créer des fonctionnalités techniques<br/><br/>Moderniser la posture et les contrôles de sécurité<br/><br/>Mettre à l’échelle pour répondre aux besoins d’une région ou du marché<br/><br/>Améliorer les expériences client et les engagements<br/><br/>Transformer des produits ou services<br/><br/>Proposer de nouveaux produits ou services sur le marché|

<!-- markdownlint-enable MD033 -->

Quand la priorité absolue est de réagir à des événements métier critiques, il est important de procéder à une [implémentation cloud](#cloud-implementation) de manière précoce, souvent en parallèle avec les efforts de stratégie et de planification. L’adoption d’une telle approche nécessite un état d’esprit axé sur la croissance et une volonté d’améliorer de manière itérative les processus, sur la base des enseignements tirés en direct.

Quand les motivations relatives à la migration constituent une priorité, [la stratégie et la planification](#cloud-strategy-and-planning) jouent un rôle essentiel au début du processus. Toutefois, il est vivement recommandé d’[implémenter](#cloud-implementation) la première charge de travail parallèlement à la planification pour aider l’équipe à comprendre et à planifier les courbes d’apprentissage associées au cloud.

Quand les motivations relatives à l’innovation représentent la priorité la plus élevée, la stratégie et la planification nécessitent des investissements supplémentaires au début du processus pour garantir l’équilibre du portefeuille et un alignement judicieux de l’investissement effectué pendant l’implémentation cloud. Pour plus d’informations sur les motivations liées à l’innovation, consultez [Comprendre le parcours d’innovation](./innovate.md).

Si tous les participants sont préparés à l’effort de migration en ayant conscience des motivations, cela permet de garantir des décisions plus judicieuses. La méthodologie de migration suivante montre comment Microsoft suggère aux clients de guider ces décisions selon une méthodologie cohérente.

## <a name="migration-approach"></a>Approche de migration

Cloud Adoption Framework établit une construction générale basée sur les concepts de planification, de préparation et d’adoption pour regrouper les types d’effort nécessaires à une adoption du cloud. Ce récapitulatif s’appuie sur ce flux général afin d’établir des processus itératifs permettant de regrouper les efforts d’optimisation lift-and-shift et les efforts de modernisation en une seule approche pour toutes les activités de migration cloud.

Cette approche comporte deux méthodologies ou domaines prioritaires : Stratégie/planification cloud et implémentation cloud. La [motivation](#motivations) ou le résultat opérationnel souhaité pour une migration cloud détermine souvent l’investissement qu’une équipe doit fournir dans [la stratégie et la planification](#cloud-strategy-and-planning) ainsi que dans l’[implémentation](#cloud-implementation). Ces motivations peuvent également influencer les décisions pour une exécution séquentielle ou parallèle.

## <a name="cloud-implementation"></a>Implémentation cloud

L’implémentation cloud est un processus itératif destiné à migrer et à moderniser le patrimoine numérique, en harmonie avec les résultats opérationnels ciblés et les contrôles de gestion des changements. À chaque itération, les charges de travail sont migrées ou modernisées en fonction de la stratégie et de la planification. Les décisions relatives aux modèles IaaS, PaaS ou hybrides sont prises pendant la phase d’évaluation de la [méthodologie de migration](../migrate/index.md) pour optimiser le contrôle et l’exécution. Ces décisions détermineront les outils qui seront utilisés à chaque itération de la phase de migration d’une même méthodologie. Ce modèle peut être utilisé avec une stratégie et une planification minimales. Cependant, pour garantir les meilleurs retours opérationnels, les services informatiques et l’entreprise doivent s’aligner sur une stratégie et un plan clairs afin de guider les activités d’implémentation.

![Méthodologie d’implémentation cloud du Framework d’adoption du cloud](../_images/operational-transformation-migrate.png)

L’objectif de cet effort est la migration ou la modernisation des charges de travail. Une charge de travail est une collection d’infrastructures, d’applications et de données qui prend collectivement en charge un objectif métier commun ou l’exécution d’un processus métier commun. Les exemples de charges de travail peuvent inclure des éléments tels qu’une application métier, une solution de paie RH, une solution CRM, un workflow d’approbation de document financier ou une solution pour le décisionnel. Les charges de travail peuvent également inclure des ressources techniques partagées, par exemple un entrepôt de données qui prend en charge plusieurs autres solutions. Dans certains cas, une charge de travail peut être représentée par une seule ressource, par exemple un serveur, une application ou une plateforme de données autonome.

Les migrations cloud sont souvent considérées comme un seul projet au sein d’un programme plus vaste visant à simplifier les opérations informatiques, leurs coûts ou leur complexité. La méthodologie de l’implémentation cloud permet d’aligner les efforts techniques d’une série de migrations de charges de travail sur les valeurs métier plus générales décrites dans la stratégie et la planification cloud.

**Bien démarrer :** Pour bien démarrer avec une implémentation cloud, le [Guide de migration Azure](../migrate/azure-migration-guide/index.md) et le [Guide de configuration Azure](../ready/azure-setup-guide/index.md) décrivent les outils et processus généraux nécessaires à la réussite d’une implémentation cloud. La migration de votre première charge de travail à l’aide de ces guides va aider l’équipe à surmonter les courbes d’apprentissage initiales au début du processus de planification. Vous devez ensuite prendre en compte la [liste de contrôle d’étendue supplémentaire](../migrate/expanded-scope/index.md), les [bonnes pratiques de la migration](../migrate/azure-best-practices/index.md) ainsi que les [considérations relatives à la migration](../migrate/migration-considerations/index.md) pour aligner l’aide de base de référence aux contraintes, processus, structures d’équipe et objectifs uniques de votre effort.

## <a name="cloud-strategy-and-planning"></a>Stratégie et planification cloud

La stratégie et la planification cloud correspondent à une méthodologie qui met l’accent sur l’alignement des résultats opérationnels, des priorités et des contraintes de l’entreprise pour établir une stratégie et un plan de migration clairs. Le plan (ou backlog de migration) qui en résulte décrit l’approche de la migration et de la modernisation dans le portefeuille informatique, qui peut couvrir des centres de données entiers, plusieurs charges de travail ou diverses collections d’infrastructures, d’applications et de données. Une gestion appropriée du portefeuille informatique tout au long des efforts d’implémentation cloud permet d’obtenir les résultats opérationnels souhaités.

![Vue d’ensemble du Framework d’adoption du cloud](../_images/caf-overview.png)

**Bien démarrer :** Le reste de cet article prépare le lecteur à l’application appropriée de la méthodologie relative à la stratégie et la planification cloud du Framework d’adoption du cloud. Il présente également des ressources et des liens supplémentaires qui peuvent aider le lecteur à adopter cette approche pour guider les efforts d’implémentation cloud.

### <a name="methodology-explained"></a>Méthodologie expliquée

La méthodologie relative à la stratégie et la planification cloud du Framework d’adoption du cloud repose sur une approche incrémentielle de l’implémentation cloud qui s’aligne sur les stratégies technologiques agiles, une maturité culturelle basée sur le désir de croissance et les stratégies axées sur les résultats opérationnels. Cette méthodologie comprend les composants généraux suivants qui guident l’implémentation de chaque stratégie.

Comme illustré dans l’image ci-dessus, ce framework aligne les décisions stratégiques sur un petit nombre de processus contenus, qui fonctionnent dans un modèle itératif. Bien qu’ils soient décrits dans un document linéaire, chacun des processus suivants est censé arriver à maturité parallèlement aux itérations de l’implémentation cloud. Les liens de chaque processus vont permettre de définir l’état final et les moyens d’évoluer vers l’état final souhaité :

- **[Planification](../strategy/index.md) :** Quand l’implémentation technique est alignée sur des objectifs stratégiques clairs, il est beaucoup plus facile de mesurer et d’aligner la réussite de ces objectifs sur plusieurs efforts d’implémentation cloud, quelles que soient les décisions techniques.
- **[Prêt](../ready/index.md) :** La préparation de l’entreprise, de la culture, des personnes et de l’environnement aux changements à venir contribue au succès de chaque effort et accélère les projets d’implémentation et de changement.
- **Adoption :** Veillez à l’implémentation appropriée des changements souhaités dans l’ensemble des processus informatiques et métier pour obtenir les résultats opérationnels attendus.
  - **[Migration](../migrate/index.md) :** Exécution itérative de la [méthodologie d’implémentation cloud](#cloud-implementation) conformément au processus testé d’évaluation, de migration, d’optimisation et de sécurisation et de gestion pour créer un processus reproductible de migration des charges de travail.
  - **[Innovation](../innovate/index.md) :** Valorisez la valeur commerciale grâce à des activités d’innovation qui déverrouillent de nouvelles compétences techniques et des capacités métier étendues.
- **[Gouverner](../govern/index.md) :** Alignez la stratégie de l’entreprise sur les risques tangibles, en les atténuant par des outils de gouvernance de stratégie, de processus et cloud.
- **[Gérer](../manage/index.md) :** Développez les opérations informatiques pour vérifier que les solutions cloud peuvent être exploitées via des processus sécurisés et rentables à l’aide d’outils d’exploitation modernes axés principalement sur le cloud.
- **[Organiser](../organize/index.md) :** aligner les personnes et les équipes pour fournir des opérations et une adoption appropriées en matière de cloud.

Tout au long de cette expérience de migration, ce framework est utilisé pour lever les ambiguïtés, gérer les changements et guider les diverses équipes interfonctionnelles à atteindre les résultats opérationnels souhaités.

### <a name="common-cultural-changes-resulting-from-adherence-to-this-methodology"></a>Changements culturels courants résultant de l’adhésion à cette méthodologie

L’effort nécessaire pour atteindre les résultats opérationnels souhaités peut déclencher de légers changements dans la culture des services informatiques, la sécurité et, dans une certaine mesure, la culture de l’entreprise. Voici quelques changements culturels courants observés dans ce processus :

- Les équipes informatique et de sécurité vont probablement adopter de nouvelles compétences pour prendre en charge les charges de travail dans le cloud.
- L’exécution d’une migration cloud encourage les approches itératives ou agiles.
- L’inclusion de la gouvernance cloud a également tendance à inspirer les approches DevOps.
- La création d’une équipe de stratégie cloud peut conduire à une intégration plus étroite entre les dirigeants de l’entreprise et les responsables informatiques.
- Collectivement, ces changements tendent à aboutir à une plus grande agilité de l’entreprise et informatique.

Le changement culturel n’est pas un objectif de la migration cloud ou du Framework d’adoption du cloud. Toutefois, il s’agit d’un résultat couramment rencontré.
Les changements culturels ne sont pas directement guidés. À la place, des changements subtils au niveau de la culture sont incorporés dans des suggestions d’amélioration de processus et des conseils d’approche.

### <a name="common-technical-efforts-associated-with-this-methodology"></a>Efforts techniques courants associés à cette méthodologie

Durant l’implémentation de la stratégie et de la planification cloud, l’équipe informatique consacre une grande partie de son temps à la migration des ressources numériques existantes vers le cloud. Au cours de cet effort, des changements minimes du code sont attendus, mais ils peuvent souvent se limiter à des changements de configuration. Dans de nombreux cas, une justification métier solide peut être apportée à la modernisation dans le cadre de la migration cloud.

### <a name="common-workload-examples"></a>Exemples de charges de travail courantes

La stratégie et la planification cloud ciblent souvent une vaste collection de charges de travail et d’applications. Dans le portefeuille, les types d’application ou de charge de travail courants sont généralement migrés. Voici quelques exemples :

- applications métier ;
- Applications destinées aux clients
- Applications tierces
- Plateformes d’analytique données
- Solutions distribuées mondialement
- Solutions hautement scalables

### <a name="common-technologies-migrated"></a>Technologies courantes migrées

Les technologies migrées vers le cloud se développent constamment au fur et à mesure que les fournisseurs de cloud ajoutent de nouvelles fonctionnalités. Voici quelques exemples de technologies couramment rencontrées dans le cadre d’un effort de migration :

- Windows et SQL Server
- Bases de données Linux et OSS (open source)
- Bases de données non structurées et NoSQL
- SAP sur Azure
- Analytics (Data Warehouse, Data Lake)

## <a name="next-steps-lifecycle-solution"></a>Étapes suivantes : Solution de cycle de vie

Le Framework d’adoption du cloud est une solution de cycle de vie. Il est conçu pour aider les lecteurs qui commencent tout juste leur parcours de migration ainsi que ceux qui sont profondément engagés dans celui-ci. Ainsi, le contenu est très spécifique au contexte et à l’audience. Les étapes suivantes sont mieux alignées sur le processus général que le lecteur souhaite améliorer.

> [!div class="nextstepaction"]
> [Stratégie](../strategy/index.md)
>
> [Planification](../plan/index.md)
>
> [Prête](../ready/index.md)
>
> [Migrer](../migrate/index.md)
>
> [Innovation](../innovate/index.md)
>
> [Gouvernance](../govern/index.md)
>
> [Gérer](../manage/index.md)
>
> [Organiser](../organize/index.md)
