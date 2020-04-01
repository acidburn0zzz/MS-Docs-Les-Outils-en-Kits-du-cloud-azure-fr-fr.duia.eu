---
title: Se préparer à la complexité de la gestion agile des changements
description: Utilisez le Cloud Adoption Framework pour Azure afin de préparer les architectes du cloud à participer à une conversation avec les gestionnaires de projet dans le but d’expliquer le concept de la gestion des changements.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 56c7d171d46813d7175e93759be10ce1423115b0
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80355169"
---
<!-- cSpell:ignore ITSM TOGAF -->

# <a name="prepare-for-technical-complexity-agile-change-management"></a>Se préparer à la complexité technique : gestion agile des changements

Lorsque l’ensemble d’un centre de données peut être mis hors service et recréé avec une seule ligne de code, les processus traditionnels éprouvent des difficultés à suivre le rythme. Les conseils fournis dans le cadre du Framework d’adoption du cloud s’appuient sur des pratiques telles que la gestion des services informatiques (ITSM), l’Open Group Architecture Framework (TOGAF) et d’autres. Toutefois, pour garantir l’agilité et la réactivité aux changements opérationnels, cette infrastructure façonnent ces pratiques de manière à s’adapter aux méthodologies agiles et aux approches DevOps.

Lors du passage à un modèle agile dans lequel l’accès est mis sur la flexibilité et l’itération, la complexité technique et la gestion des changements sont gérées différemment par rapport à un modèle traditionnel en cascade axé sur une série linéaire d’étapes de migration. Cet article décrit une approche de haut niveau de la gestion des changements dans le cadre d’un effort de migration basé sur l’agilité. À la fin de cet article, vous devriez avoir une compréhension générale des niveaux de gestion des changements et de la documentation connexe dans une approche de migration incrémentielle. Des formations et des décisions supplémentaires sont requises pour sélectionner et implémenter des pratiques agiles basées sur cette compréhension. L’objectif de cet article est de préparer les architectes cloud pour faciliter la conversation avec la gestion de projet afin d’expliquer le concept général de gestion des changements dans cette approche.

## <a name="address-technical-complexity"></a>Résoudre la complexité technique

Lors de la modification d’un système technique, la complexité et l’interdépendance introduisent un risque dans les plans de projet. Il en va de même pour les migrations cloud. Lors du déplacement de milliers&mdash;ou de dizaines de milliers&mdash;de ressources vers le cloud, ces risques sont amplifiés. La détection et le mappage de toutes les dépendances dans un patrimoine numérique important peuvent prendre des années. Peu d’entreprises peuvent tolérer un cycle d’analyse aussi long. Pour équilibrer la nécessité d’une analyse architecturale et d’une accélération des activités, le Framework d’adoption du cloud se concentre sur un modèle INVEST pour la gestion du backlog de produit. Les sections suivantes résument ce type de modèle.

## <a name="invest-in-workloads"></a>INVEST dans les charges de travail

Le terme _charge de travail_ apparaît dans l’ensemble du Framework d’adoption du cloud. Une charge de travail est une unité de fonctionnalités d’application qui peut être migrée vers le cloud. Il peut s’agir d’une application unique, de la couche d’une application ou de la collection d’une application. La définition est flexible et peut changer selon les différentes phases de la migration. Le Framework d’adoption du cloud utilise le terme _invest_ pour définir une charge de travail.

INVEST est un acronyme courant dans de nombreuses méthodologies agiles pour écrire des récits utilisateur ou des éléments de backlog de produit, qui sont tous deux des unités de sortie dans les outils de gestion de projet agile. L’unité mesurable de sortie dans une migration est une charge de travail migrée. Le Framework d’adoption du cloud modifie légèrement l’acronyme INVEST pour créer une construction permettant de définir des charges de travail :

- **Indépendante :** Une charge de travail ne doit pas avoir de dépendances inaccessibles. Pour qu’une charge de travail soit considérée comme migrée, toutes les dépendances doivent être accessibles et incluses dans l’effort de migration.
- **Négociable :** Une fois la détection supplémentaire effectuée, la définition d’une charge de travail change. Les architectes qui planifient la migration peuvent négocier des facteurs de dépendance. Parmi les exemples de points de négociation peuvent être inclus la préversion des fonctionnalités, la mise à disposition des fonctionnalités sur un réseau hybride ou le regroupement de toutes les dépendances dans une seule mise en production.
- **De valeur :** La valeur d’une charge de travail est mesurée par la capacité à fournir aux utilisateurs un accès à une charge de travail de production.
- **Estimable :** Les dépendances, les ressources, les temps de migration, les niveaux de performance et les coûts du cloud doivent tous être estimables et doivent être estimés avant la migration.
- **Petite :** L’objectif est de regrouper les charges de travail en un seul sprint. Toutefois, cela n’est pas toujours possible. Au lieu de cela, les équipes sont encouragées à planifier des sprints et des mises en production pour réduire le temps nécessaire pour déplacer une charge de travail en production.
- **Testable :** Il doit toujours y avoir un moyen défini de tester ou de valider l’achèvement de la migration d’une charge de travail.

Cet acronyme n’est pas destiné à servir de base à une adhérence rigide, mais doit aider à guider la définition du terme _charge de travail_.

## <a name="migration-backlog-aligning-business-priorities-and-timing"></a>Backlog de migration : Alignement des priorités de l’entreprise et du calendrier

Le backlog de migration vous permet de suivre votre portefeuille de niveau supérieur des charges de travail pouvant être migrées. Avant la migration, l’équipe de stratégie cloud et celle chargée de l’adoption du cloud sont encouragées à passer en revue le [patrimoine numérique](../../../digital-estate/index.md) actuel et à accepter une liste des charges de travail à migrer classées par ordre de priorité. Cette liste constitue la base du backlog initial de migration.

Initialement, il est peu probable que les charges de travail du backlog de migration répondent aux critères INVEST décrits dans la section précédente. Au lieu de cela, elles servent à regrouper logiquement des ressources à partir d’un inventaire initial en tant qu’espace réservé en vue d’une tâche future. Ces espaces réservés peuvent ne pas être techniquement exacts, mais ils servent de base pour la coordination avec l’entreprise.

![Relation entre les backlogs de migration, de mise en production et d’itération utilisés pendant le processus de migration](../../../_images/migrate/backlog-relationships.png)

*Les backlogs de migration, de mise en production et d’itération suivent différents niveaux d’activité pendant les processus de migration.*

Dans tout backlog de migration, l’équipe responsable de la gestion des changements doit s’efforcer d’obtenir les informations suivantes pour toute charge de travail dans le plan. Au minimum, ces données doivent être disponibles pour toutes les charges de travail classées par ordre de priorité pour la migration dans les deux ou trois mises en production suivantes.

### <a name="migration-backlog-data-points"></a>Points de données du backlog de migration

- **Impact commercial.** Compréhension de l’impact pour l’entreprise de l’absence de la chronologie attendue ou de la réduction des fonctionnalités pendant les fenêtres de gel.
- **Priorité relative de l’entreprise.** Liste classée par ordre de priorité des charges de travail en fonction des priorités de l’entreprise.
- **Propriétaire de l’entreprise**. Documenter le nom de la personne responsable de prendre des décisions d’affaires concernant cette charge de travail.
- **Propriétaire technique.** Documenter le nom de la personne responsable de prendre des décisions techniques relatives à cette charge de travail.
- **Chronologies attendues.** Moment où l’achèvement de la migration est planifié.
- **Gel de la charge de travail.** Délais d’exécution pendant lesquels la charge de travail ne doit pas être admissible pour une modification.
- **Nom de la charge de travail.**
- **Inventaire initial.** Toutes les ressources requises pour fournir les fonctionnalités de la charge de travail, notamment les machines virtuelles, les appliances informatiques, les données, les applications, les pipelines de déploiement et autres. Ces informations sont susceptibles d’être inexactes.

## <a name="release-backlog-aligning-business-change-and-technical-coordination"></a>Backlog de mise en production : Alignement des changements opérationnels et de la coordination technique

Dans le contexte d’une migration, une _mise en production_ est une activité qui déploie une ou plusieurs charges de travail en production. Une mise en production couvre généralement plusieurs itérations ou un travail technique. Toutefois, il s’agit d’une seule itération de changement opérationnel. Une fois qu’une ou plusieurs charges de travail ont été préparées pour leur promotion en production, une mise en production se produit. La décision d’empaqueter une mise en production est prise quand les charges de travail migrées représentent suffisamment de valeur commerciale pour justifier l’injection de modifications dans un environnement d’entreprise. Les mises en production sont exécutées conjointement avec un [plan des changements opérationnels](../optimize/business-change-plan.md), une fois les [tests d’entreprise](../optimize/business-test.md) terminés. L’équipe de stratégie cloud est responsable de la planification et de la surveillance de l’exécution d’une mise en production afin de s’assurer que les changements opérationnels souhaités sont publiés.

Un *backlog de mise en production* est le futur plan d’état qui définit une mise en production à venir. Le backlog de mise en production est le point pivot entre la gestion des changements opérationnels (*backlog de migration*) et la gestion des changements techniques (*backlog de sprint*). Un backlog de mise en production se compose d’une liste de charges de travail provenant du backlog de migration qui correspondent à un sous-ensemble spécifique de la réalisation des résultats de l’entreprise. La définition et la soumission d’un backlog de mise en production à l’équipe d’adoption du cloud servent de déclencheur pour une analyse approfondie et une planification de la migration. Une fois que l’équipe d’adoption du cloud a vérifié les détails techniques associés à une mise en production, elle peut choisir de valider cette dernière, en établissant une chronologie de mise en production basée sur les connaissances actuelles.

Étant donné le degré d’analyse requis pour valider une mise en production, l’équipe de stratégie cloud doit tenir à jour une liste en cours des deux à quatre mises en production suivantes. L’équipe doit également tenter de valider autant des informations suivantes que possible, avant de définir et de soumettre une mise en production. Une équipe disciplinée de stratégie cloud capable de gérer les quatre prochaines mises en production peut augmenter considérablement la cohérence et la précision des estimations de la chronologie des mises en production.

### <a name="release-backlog-data-points"></a>Points de données du backlog de mise en production

Un partenariat entre l’équipe de stratégie cloud et l’équipe d’adoption du cloud collabore à l’ajout des points de données suivants pour toutes les charges de travail dans le backlog de mise en production :

- **Inventaire affiné.** Validation des ressources requises devant être migrées. Souvent validées par le biais de journaux ou de données de surveillance au niveau de l’hôte, du réseau ou du système d’exploitation pour garantir une compréhension précise des dépendances du réseau et du matériel de chaque ressource dans le cadre de la charge standard.
- **Modèles d’utilisation.** Compréhension des modèles d’utilisation des utilisateurs finaux. Ces modèles incluent souvent une analyse de la distribution géographique des utilisateurs finaux, des itinéraires réseau, des pics d’utilisation saisonniers, des pics d’utilisation quotidiens/horaires et de la composition des utilisateurs finaux (intervalle versus externe).
- **Attentes en matière de niveau de performance.** Analyse des données de journal disponibles capturant le débit, les pages vues, les itinéraires réseau et d’autres données de performance nécessaires à la réplication de l’expérience de l’utilisateur final.
- **Dépendances.** Analyse du trafic et des modèles d’utilisation des applications pour identifier les dépendances de charge de travail supplémentaires, qui doivent être prises en compte dans le séquencement et la préparation de l’environnement. N’incluez pas de charge de travail dans une mise en production tant que l’un des critères suivants n’a pas été rempli :
  - Toutes les charges de travail dépendantes ont été migrées.
  - Les configurations de réseau et de sécurité ont été implémentées pour permettre à la charge de travail d’accéder à toutes les dépendances en fonction des attentes existantes en matière de niveau de performance.
- **Approche de migration souhaitée.** Au niveau du backlog de migration, l’effort de migration supposé est le seul facteur utilisé dans l’analyse. Par exemple, si le résultat opérationnel est une sortie d’un centre de données existant, toutes les migrations sont supposées être un scénario de réhébergement dans le backlog de migration. Dans le backlog de mise en production, l’équipe de stratégie cloud et l’équipe d’adoption du cloud doivent évaluer la valeur à long terme des fonctionnalités supplémentaires, de la modernisation et des investissements de développement continus pour déterminer si une approche plus moderne doit être impliquée.
- **Critères de test d’entreprise.** Une fois qu’une charge de travail a été ajoutée au backlog de migration, les critères de test doivent être approuvés mutuellement. Dans certains cas, les critères de test peuvent se limiter à un test de performances avec un groupe défini d’utilisateurs avancés. Toutefois, pour la validation statistique, un test de performances automatisé est souhaitable et doit être inclus. Souvent, l’instance existante de l’application n’a pas de fonctionnalités de test automatisé. Si cela s’avère être le cas, il n’est pas rare que les architectes cloud collaborent avec les utilisateurs avancés pour créer un test de charge en ligne de base sur la solution existante afin d’établir un point de référence à utiliser pendant la migration.

### <a name="release-backlog-cadence"></a>Cadence des backlogs de mise en production

Dans les migrations à maturité, les mises en production sont régulières. La rapidité de l’équipe d’adoption du cloud se normalise souvent, produisant une mise en production toutes les deux à quatre itérations (environ tous les un ou deux mois). Toutefois, il doit s’agir d’un résultat organique. La création artificielle de cadences de mise en production peut avoir un impact négatif sur la capacité de l’équipe d’adoption du cloud à atteindre un débit constant.

Pour stabiliser l’impact sur l’activité, l’équipe de stratégie cloud doit établir un processus mensuel de mise en production avec l’entreprise pour maintenir un dialogue régulier, mais elle doit également établir qu’il faudra attendre plusieurs mois avant qu’une cadence régulière de mise en production puisse être prédite.

## <a name="sprint-or-iteration-backlog-aligning-technical-change-and-effort"></a>Backlog de sprint ou d’itérations : Alignement des changements techniques et des efforts

Un *sprint*, ou *itération*, est une unité de travail cohérente et liée au temps. Dans le processus de migration, il est souvent mesuré en incréments de deux semaines. Toutefois, il n’est pas rare qu’il y ait des itérations d’une ou de quatre semaines. La création d’itérations liées au temps force des intervalles cohérents d’achèvement de l’effort et permet des ajustements plus fréquents aux plans, en fonction des nouveaux apprentissages. Pendant un sprint donné, il existe généralement des tâches pour l’évaluation, la migration et l’optimisation des charges de travail définies dans le backlog de migration. Ces unités de travail doivent être suivies et managées dans le même outil de gestion de projet que le backlog de migration et de mise en production afin de garantir la cohérence entre chaque niveau de gestion des changements.

Un *backlog de sprint*, ou *backlog d’itération*, se compose du travail technique à effectuer en un sprint ou une itération unique, traitant de la migration de ressources individuelles. Ce travail doit être dérivé de la liste des charges de travail en cours de migration. Lorsque vous utilisez des outils comme Azure DevOps (précédemment Visual Studio Online) pour la gestion de projet, les éléments de travail d’un sprint sont les enfants des éléments de backlog de produit dans un backlog de mise en production et les épopées dans un backlog de migration. Une telle relation parent-enfant permet d’assurer la clarté à tous les niveaux de la gestion des changements.

Au cours d’un sprint ou d’une itération unique, l’équipe d’adoption du cloud s’efforce de fournir la quantité de travail technique promise, menant à la migration d’une charge de travail définie. C’est le résultat final de la stratégie de gestion des changements. Une fois ces opérations terminées, vous pouvez tester ces efforts en validant la préparation à la production d’une charge de travail indexée dans le cloud.

### <a name="large-or-complex-sprint-structures"></a>Structures de sprint volumineuses ou complexes

Pour une petite migration avec une équipe de migration autonome, un seul sprint peut inclure les quatre phases d’une migration pour une seule charge de travail (*évaluer*, *migrer*, *optimiser* et *sécuriser et gérer*). Plus communément, chacun de ces processus est partagé par plusieurs équipes dans des éléments de travail distincts sur de nombreux sprints. En fonction du type d’effort, de l’échelle de l’effort et des rôles, ces sprints peuvent prendre plusieurs formes différentes.

- **Fabrique de migration.** Les migrations à grande échelle nécessitent parfois une approche qui ressemble à une fabrique dans le modèle d’exécution. Dans ce modèle, plusieurs équipes sont allouées à l’exécution d’un processus de migration spécifique (ou sous-ensemble du processus). Une fois l’opération terminée, la sortie du sprint d’une équipe remplit le backlog de l’équipe suivante. Il s’agit d’une approche efficace pour les migrations de réhébergement à grande échelle de nombreuses charges de travail potentielles impliquant des milliers de machines virtuelles passant par des phases d’évaluation, d’architecture, de correction et de migration. Toutefois, pour que cette approche fonctionne, un nouvel environnement homogène avec des processus rationalisés de gestion des changements et d’approbation est indispensable.
- **Vagues de migration.** Une autre approche qui fonctionne bien pour les migrations volumineuses est un modèle de vagues. Dans ce modèle, la division du travail n’est pas aussi claire. Les équipes se consacrent à l’exécution du processus de migration des charges de travail individuelles. Toutefois, la nature de chaque sprint change. Dans un sprint, l’équipe peut terminer des tâches d’évaluation et d’architecture. Dans un autre, elle peut terminer la tâche de migration. Dans encore un autre sprint, l’accent sera sur l’optimisation et la mise en production. Cette approche permet à une équipe centrale de rester alignée sur les charges de travail et de les suivre tout au long du processus. Lors de l’utilisation de cette approche, la diversité des qualifications et des changements de contexte peut réduire la vélocité potentielle de l’équipe, ce qui ralentit l’effort de migration. En outre, les obstacles au cours des cycles d’approbation peuvent entraîner des retards considérables. Il est important de conserver des options dans le backlog de mise en production pour maintenir l’équipe en mouvement pendant les périodes de blocage avec ce modèle. Il est également important d’effectuer une formation croisée des membres de l’équipe et de s’assurer que les ensembles de compétences s’alignent sur le thème de chaque sprint.

### <a name="sprint-backlog-data-points"></a>Points de données du backlog de sprint

Le résultat d’un sprint capture et documente les changements apportés à une charge de travail, fermant ainsi la boucle de gestion des changements. Quand c’est terminé, au minimum, les éléments suivants doivent être documentés. Tout au long de l’exécution d’un sprint, cette documentation doit être remplie en tandem avec les éléments de travail techniques.

- **Ressources déployées.** Toutes les ressources déployées dans le cloud pour héberger la charge de travail.
- **Correction.** Toute modification apportée aux ressources pour préparer la migration cloud.
- **Configuration.** Configuration choisie pour les ressources déployées, notamment les références aux scripts de configuration.
- **Modèle de déploiement.** Approche utilisée pour déployer la ressource dans le cloud, notamment les références à des scripts ou outils de déploiement.
- **Architecture.** Documentation de l’architecture déployée dans le cloud.
- **Métriques de performance.** Sortie des tests automatisés ou des tests d’entreprise effectués pour valider le niveau de performance au moment du déploiement.
- **Configuration ou exigences uniques.** Tout aspect unique du déploiement, de la configuration ou des exigences techniques nécessaires à l’exploitation de la charge de travail.
- **Approbation opérationnelle.** Approbation de la validation de la préparation opérationnelle par le propriétaire de l’application et le personnel des opérations informatiques chargés de gérer la charge de travail après le déploiement.
- **Approbation de l’architecture.** Approbation du propriétaire de la charge de travail et de l’équipe d’adoption du cloud pour valider les changements d’architecture requis pour héberger chaque ressource.

## <a name="next-steps"></a>Étapes suivantes

Une fois que les approches de gestion des changements ont été établies, il est temps de traiter le dernier prérequis : la [révision du backlog de migration](./migration-backlog-review.md)

> [!div class="nextstepaction"]
> [Révision du backlog de migration](./migration-backlog-review.md)
