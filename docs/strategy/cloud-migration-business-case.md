---
title: Justification métier de la migration cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à développer une justification métier de la migration cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 28762d3540124b40bd3db4d7bd431033a1c25b5f
ms.sourcegitcommit: 26caeb6b7f4e14df30bf16727d0b1b3d63b9c0c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78337973"
---
# <a name="build-a-business-justification-for-cloud-migration"></a>Créer une justification professionnelle pour la migration vers le cloud

Les migrations cloud peuvent rapidement générer un retour sur investissement (ROI), grâce aux efforts de transformation du cloud. Toutefois, le développement d’une justification métier claire avec des coûts et des rendements concrets et pertinents peut s’avérer un processus complexe. Cet article va vous aider à réfléchir aux données dont vous avez besoin pour créer un modèle financier aligné sur les résultats d’une migration cloud. Avant toute chose, nous allons dissiper quelques mythes autour de la migration cloud afin d’éviter à votre organisation de commettre certaines erreurs courantes.

## <a name="dispelling-cloud-migration-myths"></a>Démystification de la migration cloud

**Mythe : Le cloud est toujours moins cher.** Il est communément admis qu’exploiter un centre de données dans le cloud revient toujours moins cher que de l’exploiter localement. Bien que cette hypothèse soit généralement vraie, ce n’est pas toujours le cas. Parfois, les coûts opérationnels du cloud sont plus élevés. Ces coûts plus élevés sont souvent liés à une mauvaise gouvernance, des architectures système inadéquates, une duplication des processus, des configurations système atypiques ou des charges de personnel plus importantes. Heureusement, vous pouvez atténuer un bon nombre de ces problèmes pour obtenir un ROI (retour sur investissement) rapide. Suivre l’aide fournie dans [Générer la justification métier](#build-the-business-justification) peut vous aider à détecter et à éviter ces alignements incorrects. Le fait de dissiper les autres mythes décrits ici peut également vous aider.

**Mythe : Tout doit être placé dans le cloud.** En fait, certains axes stratégiques peuvent vous amener à choisir une solution hybride. Avant de finaliser un modèle d’affaires, il est judicieux d’effectuer une première analyse quantitative, comme cela est expliqué dans les [articles consacrés au patrimoine numérique](../digital-estate/5-rs-of-rationalization.md). Pour plus d’informations sur les différents facteurs quantitatifs impliqués dans la rationalisation, consultez [Les 5 R de la rationalisation](../digital-estate/5-rs-of-rationalization.md). Chaque approche utilise des données d’inventaire faciles à obtenir ainsi qu’une brève analyse quantitative pour identifier les charges de travail ou les applications susceptibles de présenter des coûts plus élevés dans le cloud. Ces approches peuvent également identifier les dépendances ou les modèles de trafic qui nécessitent une solution hybride.

**Mythe : La mise en miroir de mon environnement local va m’aider à faire des économies dans le cloud.** Durant la planification du patrimoine numérique, il n’est pas rare que les entreprises détectent une sous-utilisation des fonctionnalités supérieure à 50 % de l’environnement provisionné. Si les ressources sont provisionnées dans le cloud pour correspondre au provisionnement actuel, il est difficile d’effectuer des économies. Réduisez éventuellement la taille des ressources déployées pour les aligner sur les modèles d’utilisation plutôt que sur les modèles de provisionnement.

**Mythe : Les coûts des serveurs impactent les analyses de rentabilisation de la migration cloud.** Parfois, cette hypothèse est vraie. Certaines entreprises jugent qu’il est important de réduire leurs dépenses d’investissement actuelles pour les serveurs. Mais cela dépend de plusieurs facteurs. Les entreprises dont le cycle de renouvellement du matériel est compris entre cinq et huit ans ont peu de chances d’obtenir des retours sur investissement rapides de leur migration cloud. Celles qui ont des cycles de renouvellement standards ou fixes peuvent atteindre un seuil de rentabilité rapidement. Dans les deux cas, d’autres dépenses peuvent être les déclencheurs financiers qui justifient la migration. Voici quelques exemples de coûts généralement négligés quand les entreprises adoptent une vision des coûts axée uniquement sur les serveurs ou uniquement sur les machines virtuelles :

- Les coûts des logiciels de virtualisation, des serveurs et des middlewares (intergiciels) peuvent être considérables. Les fournisseurs de cloud éliminent certains de ces coûts. Les programmes [Azure Hybrid Benefit](https://azure.microsoft.com/pricing/hybrid-benefit/#services) et [Réservations](https://azure.microsoft.com/reservations) sont deux exemples de fournisseur de cloud qui permettent de réduire les coûts de virtualisation.
- Les pertes financières dues à des pannes peuvent rapidement dépasser les coûts matériels ou logiciels. Si votre centre de données actuel est instable, travaillez avec l’entreprise pour quantifier l’impact des interruptions de service au niveau des coûts d’opportunité ou des coûts d’exploitation réels.
- Les coûts environnementaux peuvent également être importants. Pour une famille américaine moyenne, le logement représente le plus gros investissement et le poste de dépense le plus élevé dans le budget. Il en va souvent de même pour les centres de données. Les coûts immobiliers, d’équipement et d’énergie représentent une bonne part des coûts locaux. Une fois que les centres de données sont mis hors service, ces installations peuvent être reconverties, ou votre entreprise peut éventuellement se libérer entièrement de ces coûts.

**Mythe : Un modèle de dépenses d’exploitation est préférable à un modèle de dépenses en capital.** Comme cela est expliqué dans l’article sur les [résultats financiers](./business-outcomes/fiscal-outcomes.md), un modèle de dépenses d’exploitation peut être une bonne chose. Toutefois, certaines industries ont une vision négative des dépenses d’exploitation. Voici quelques exemples susceptibles de déclencher une intégration plus étroite avec les unités comptables et commerciales en ce qui concerne la conversation relative aux dépenses d’exploitation :

- Quand une entreprise considère les immobilisations comme un facteur d’évaluation, les réductions des dépenses en capital peuvent être perçues comme un résultat négatif. Bien qu’il ne s’agisse pas d’un standard universel, ce sentiment est le plus souvent observé dans les secteurs de la vente au détail, de la fabrication et de la construction.
- Une société de capital-investissement ou une société qui recherche un afflux de capitaux peut considérer l’augmentation des dépenses d’exploitation comme un résultat négatif.
- Si une entreprise se concentre principalement sur l’amélioration des marges commerciales ou sur la réduction du COGS (coût des produits vendus), les dépenses d’exploitation peuvent être perçues comme un résultat négatif.

Les entreprises ont tendance à percevoir les dépenses d’exploitation de manière plus favorable que les dépenses en capital. Par exemple, cette approche peut convenir aux entreprises qui cherchent à améliorer leurs flux de trésorerie, à réduire leurs dépenses d’investissement en capital ou à réduire leurs actifs.

Avant de fournir une justification métier axée sur la conversion des dépenses en capital en dépenses d’exploitation, déterminez ce qui convient le mieux à votre entreprise. La comptabilité et les achats peuvent souvent vous aider à aligner le message sur les objectifs financiers.

**Mythe : Migrer vers le cloud est aussi simple que d’appuyer sur un bouton.** Une migration est une transformation technique qui s’effectue manuellement. Dans votre justification, en particulier pour les facteurs temps, prenez en compte les aspects suivants qui peuvent allonger le processus de migration des ressources :

- **Limitations de bande passante :** la quantité de bande passante entre le centre de données actuel et le fournisseur de cloud détermine les chronologies durant la migration.
- **Chronologies des tests :** tester les applications auprès de l’entreprise pour valider leur disponibilité et leur niveau de performance peut prendre du temps. Il est donc primordial de planifier les processus de test en accord avec les utilisateurs décisionnaires.
- **Chronologies de la migration :** le temps et les efforts nécessaires pour implémenter la migration peuvent augmenter les coûts et causer des retards. L’allocation d’employés ou de partenaires contractuels peut également retarder le processus. La planification doit tenir compte de ces allocations.

L’adoption du cloud peut être ralentie par des obstacles techniques et culturels. Quand le temps est un facteur important de la justification, la planification est la meilleure mesure d’atténuation. Durant la planification, deux approches peuvent vous aider à atténuer les risques liés aux chronologies :

- Investissez le temps et l’énergie nécessaires pour bien comprendre les contraintes techniques liées à l’adoption. Bien que la pression liée au projet de migration puisse être élevée, il est important de prendre en compte des chronologies d’exécution réalistes.
- Si des obstacles culturels ou humains surviennent, ils ont un plus grand impact que les contraintes techniques. L’adoption du cloud engendre des changements, qui sont nécessaires pour parvenir à la transformation souhaitée. Malheureusement, les gens craignent parfois le changement et peuvent avoir besoin d’un soutien supplémentaire pour s’adapter à la planification. Identifiez les principaux membres de l’équipe qui s’opposent au changement, et impliquez-les en amont.

Pour anticiper et atténuer au maximum les risques liés aux chronologies, préparez les parties prenantes décisionnaires en leur présentant une solide justification avec les bénéfices et les résultats pour l’entreprise. Aidez ces parties prenantes à comprendre la nature des changements qui vont accompagner la transformation. Soyez clair et établissez des objectifs réalistes dès le début. Si des personnes ou des technologies ralentissent le processus, il sera plus facile d’obtenir le soutien de la direction.

## <a name="build-the-business-justification"></a>Élaboration de la justification métier

Le processus suivant définit une approche possible pour élaborer la justification d’une migration cloud. Pour plus d’informations sur les calculs et les termes financiers, consultez l’article sur les [modèles financiers](./financial-models.md).

D’un point de vue général, la formule utilisée pour la justification est simple. Toutefois, les points de données exacts nécessaires au remplissage de la formule peuvent être difficiles à déterminer. Au niveau de base, la justification métier se concentre sur le ROI (retour sur investissement) associé à la proposition de changement technique. La formule générique pour le retour sur investissement est :

![ROI est égal à (gain lié à l’investissement moins coût de l’investissement) divisé par coût de l’investissement](../_images/strategy/formula-roi.png)

Nous pouvons décomposer cette équation afin d’obtenir une vue spécifique à la migration des formules pour les variables d’entrée à droite de l’équation. Les sections suivantes de cet article présentent différents points à prendre en compte.

## <a name="migration-specific-initial-investment"></a>Investissement initial pour la migration

- Les fournisseurs de cloud comme Azure proposent des outils de calcul pour estimer le montant des investissements dans le cloud. La [calculatrice de prix Azure](https://azure.microsoft.com/pricing) en est un exemple.
- Certains fournisseurs de cloud proposent également des calculatrices du delta des coûts. La [calculatrice du TCO (coût total de possession) Azure](https://azure.com/tco) en est un exemple.
- Pour des structures de coûts plus détaillées, effectuez plutôt une [planification du patrimoine numérique](../digital-estate/index.md).
- Estimez le coût de la migration.
- Estimez le coût des besoins de formation. [Microsoft Learn](https://docs.microsoft.com/learn) peut être une solution pour atténuer ces coûts.
- Dans certaines entreprises, le temps investi par les membres d’équipes existants est éventuellement à inclure dans les coûts initiaux. Pour obtenir des conseils, consultez le service financier.
- Discutez des coûts supplémentaires ou des coûts cachés éventuels avec le service financier pour faire valider votre estimation.

## <a name="migration-specific-revenue-deltas"></a>Écarts de revenus liés à la migration

Cet aspect est souvent négligé par les stratèges qui créent une justification métier de la migration. Dans certains domaines, le cloud peut réduire les coûts. Toutefois, l’objectif final de toute transformation est d’améliorer les résultats à long terme. Tenez compte des répercussions en aval pour comprendre comment améliorer les revenus à long terme. Quelles seront les nouvelles technologies disponibles pour votre entreprise après la migration et qui ne peuvent pas être utilisées aujourd’hui ? Quels projets ou objectifs de l’entreprise sont bloqués en raison de dépendances sur des technologies héritées ? Quels sont les programmes en suspens qui sont en attente de dépenses en capital élevées pour la technologie ?

Une fois que vous avez étudié les opportunités offertes par le cloud, travaillez avec l’entreprise pour calculer les hausses de revenus envisageables grâce à ces opportunités.

## <a name="migration-specific-cost-deltas"></a>Écarts de coûts liés à la migration

Calculez les nouveaux coûts estimés après la migration proposée. Consultez l’article sur les [modèles financiers](./financial-models.md) pour plus d’informations sur les types de delta des coûts. Les fournisseurs de cloud proposent souvent des outils permettant de calculer le delta des coûts. La [calculatrice du TCO (coût total de possession) Azure](https://azure.com/tco) en est un exemple.

Autres exemples de coûts pouvant être réduits par une migration cloud :

- Arrêt ou réduction du centre de données (coûts environnementaux)
- Réduction de la consommation d’énergie (coûts environnementaux)
- Arrêt du rack (récupération des ressources physiques)
- Non-renouvellement du matériel (évitement des coûts)
- Non-renouvellement des logiciels (réduction des coûts opérationnels ou évitement des coûts)
- Consolidation fournisseur (réduction des coûts opérationnels et réduction potentielle des coûts accessoires)

## <a name="when-roi-results-are-surprising"></a>Quand les résultats de retour sur investissement ne sont pas ceux escomptés

Si le ROI d’une migration cloud ne correspond pas à vos attentes, vous pouvez revoir les mythes courants listés au début de cet article.

Toutefois, il est important de comprendre qu’une réduction des coûts n’est pas toujours possible. Certaines applications ont un coût opérationnel plus élevé dans le cloud qu’en local. Elles peuvent donc largement biaiser les résultats dans une analyse.

Quand le ROI est inférieur à 20 %, effectuez une [planification du patrimoine numérique](../digital-estate/index.md) en accordant une attention particulière à la [rationalisation](../digital-estate/rationalize.md). Durant l’analyse quantitative, passez en revue chaque application pour rechercher les charges de travail qui faussent les résultats. Il peut s’avérer judicieux de supprimer ces charges de travail de la planification. Si des données d’utilisation sont disponibles, essayez de réduire la taille des machines virtuelles en fonction de l’utilisation réelle.

Si le retour sur investissement n’est toujours pas suffisant, travaillez en collaboration avec votre représentant commercial Microsoft ou [demandez de l’aide à un partenaire expérimenté](https://azure.microsoft.com/migration/support).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer un modèle financier pour la transformation cloud](./financial-models.md)
