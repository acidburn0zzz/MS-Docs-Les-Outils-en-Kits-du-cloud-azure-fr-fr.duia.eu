---
title: Présentation des fonctions de gouvernance cloud
description: Découvrez la fonction d’une équipe chargée de la gouvernance cloud, notamment la source, l’étendue et le livrable.
author: JanetCThomas
ms.author: janet
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.topic: conceptual
ms.date: 04/20/2020
ms.openlocfilehash: 1ccda999eb0327f7694374b0589321ca0965f1c2
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83215753"
---
<!-- docsTest:ignore IS -->

# <a name="cloud-governance-functions"></a>Fonctions de gouvernance cloud

Une équipe chargée de la gouvernance cloud garantit que les risques et la tolérance aux risques sont évalués et gérés correctement. Elle assure la bonne identification des risques que l’entreprise ne peut pas tolérer. Les membres de cette équipe convertissent les risques en gestion des stratégies d’entreprise.

Selon les résultats opérationnels souhaités, les compétences nécessaires pour assurer des fonctions complètes de gouvernance cloud peuvent être les suivantes :

- Gouvernance informatique
- Architecture d’entreprise
- Sécurité
- Opérations informatiques
- Infrastructure informatique
- Mise en réseau
- Identité
- Virtualisation
- Continuité d’activité et reprise d’activité
- Propriétaires d’applications au sein du service informatique
- Propriétaires financiers

Ces fonctions de référence aident à identifier les risques liés aux versions actuelles et futures. Ces efforts permettent d’évaluer les risques, de comprendre les impacts potentiels et de prendre des décisions concernant la tolérance aux risques. En parallèle, mettez rapidement à jour les plans pour refléter l’évolution des besoins de [l’équipe chargée de la migration cloud](./cloud-migration.md).

## <a name="preparation"></a>Préparation

- Consultez la [méthodologie Gouvernance](../govern/index.md).
- Effectuez [l’évaluation benchmark de gouvernance](../govern/benchmark.md).
- [Présentation de la sécurité dans Azure](https://docs.microsoft.com/learn/modules/intro-to-security-in-azure) : Découvrez les concepts de base pour protéger votre infrastructure et vos données dans le cloud. Prenez connaissance des responsabilités qui vous incombent et de ce qu’Azure gère pour vous.
- Découvrez comment travailler avec plusieurs groupes pour [gérer les coûts](../organize/cost-conscious-organization.md).

## <a name="minimum-scope"></a>Étendue minimale

- Identifiez les [risques métier](../govern/policy-compliance/risk-tolerance.md) introduits par le plan.
- Représentez la [tolérance aux risques de l’entreprise](../govern/policy-compliance/risk-tolerance.md).
- Participez à la création d’un [MVP de gouvernance](../govern/guides/index.md).

Impliquez les participants suivants dans les activités de gouvernance cloud :

- Les cadres intermédiaires et les contributeurs directs qui occupent des rôles clés doivent représenter l’entreprise et aider à évaluer les tolérances aux risques.
- Les fonctions de gouvernance cloud sont assurées par une extension de [l’équipe chargée de la stratégie cloud](./cloud-strategy.md). De même que le DSI et les dirigeants sont censés participer aux fonctions de stratégie cloud, il est attendu de leurs collaborateurs directs qu’ils prennent part aux activités de gouvernance cloud.
- Les employés de l’entreprise membres de la division qui travaillent en étroite collaboration avec la direction doivent être en mesure de prendre des décisions concernant les risques d’entreprise et techniques.
- Les employés des technologies de l’information et de la sécurité des informations qui comprennent les aspects techniques de la transformation cloud peuvent être sollicités à tour de rôle au lieu d’assurer en permanence les fonctions de gouvernance cloud.

## <a name="deliverable"></a>Livrable

La mission de gouvernance cloud consiste à équilibrer les forces opposées de transformation et d’atténuation des risques. De plus, la gouvernance cloud garantit que [l’équipe chargée de la migration cloud](./cloud-migration.md) a connaissance de la classification des données et des ressources, ainsi que des recommandations d’architecture qui régissent l’adoption. Les professionnels ou les équipes chargés de la gouvernance collaborent également avec le [centre d’excellence cloud](../organize/cloud-center-of-excellence.md) pour appliquer des approches automatisées de la gouvernance des environnements cloud.

**Tâches mensuelles en cours :**

- Identifiez les [risques métier](../govern/policy-compliance/risk-tolerance.md) introduits à chaque mise en production.
- Représentez la [tolérance aux risques de l’entreprise](../govern/policy-compliance/risk-tolerance.md).
- Facilitez l’amélioration incrémentielle des [exigences de stratégie et de conformité](../govern/policy-compliance/index.md).

**Cadence des réunions :**

Le temps consacré par chaque membre de l’équipe chargée de la gouvernance cloud représente une part importante de son emploi du temps quotidien. Les contributions ne sont pas limitées aux réunions et aux cycles de commentaires.

## <a name="out-of-scope"></a>Hors propos

Au fil de l’adoption, l’équipe chargée de la gouvernance cloud risque d’avoir du mal à suivre le rythme des innovations. C’est particulièrement vrai dans les environnements comportant des exigences élevées en matière de conformité, d’exploitation ou de sécurité. Si c’est votre cas, vous pouvez déléguer une partie des responsabilités à une équipe informatique existante pour réduire l’étendue des attributions de l’équipe chargée de la gouvernance.

## <a name="next-steps"></a>Étapes suivantes

Certaines grandes organisations disposent d’équipes dédiées qui se concentrent sur la gouvernance informatique. Ces équipes sont spécialisées dans la gestion des risques de tout le portefeuille informatique. Lorsque ces équipes existent, les modèles de maturité suivants peuvent être rapidement accélérés. En revanche, l’équipe de gouvernance informatique est encouragée à examiner le modèle de gouvernance cloud pour comprendre comment la gouvernance évolue légèrement vers le cloud. Citons deux articles essentiels, sur l’extension de la stratégie d’entreprise dans le cloud et les cinq disciplines de gouvernance cloud.
Aucune gouvernance : Il est courant pour les organisations d’adopter le cloud sans établir clairement de plans de gouvernance. Très vite, des préoccupations liées à la sécurité, au coût, à l’échelle et aux opérations commencent à déclencher des conversations sur le besoin d’un modèle de gouvernance et de personnes pour s’occuper des processus associés à ce modèle. Aborder ces sujets avant qu’ils ne deviennent des préoccupations s’avère toujours une démarche préliminaire utile pour éviter l’antimodèle « aucune gouvernance ». La section sur la définition d’une stratégie d’entreprise peut faciliter ces conversations.

**Gouvernance bloquée :** Quand les préoccupations liées à la sécurité, au coût, à l’échelle et aux opérations ne sont pas considérées, les projets et les objectifs de l’entreprise ont tendance à bloquer. Un manque de gouvernance appropriée génère de la peur, de l’incertitude et des doutes parmi les parties prenantes et les ingénieurs. Mettez-y fin tout de suite en prenant des mesures précoces. Les deux guides de gouvernance définis dans le Framework d’adoption du cloud peuvent vous aider à démarrer modestement, puis à définir des stratégies de limitation initiales afin de réduire l’incertitude et d’affiner la gouvernance au fil du temps. Choisissez entre le guide pour entreprise complexe et le guide pour entreprise standard.

**Gouvernance volontaire :** Il y a des personnes volontaires dans toutes les entreprises. Ces cœurs vaillants sont toujours prêts à se jeter à l’eau pour aider leur équipe à tirer des leçons de ses erreurs. C’est souvent comme cela que commence la gouvernance, particulièrement dans les petites entreprises. Ces courageux consacrent du temps à résoudre les problèmes et poussent les équipes d’adoption du cloud vers un ensemble bien géré et cohérent de bonnes pratiques.

Les efforts de ces personnes valent bien mieux que les scénarios « aucune gouvernance » ou « gouvernance bloquée ». Même si ces efforts sont louables, cette approche ne doit pas être confondue avec la gouvernance. Une véritable gouvernance nécessite bien plus qu’un soutien sporadique pour être cohérente, laquelle cohérence constitue l’objectif de toute bonne approche de gouvernance. Les instructions données dans les cinq disciplines de gouvernance cloud permettent de développer cette discipline.

**Dépositaire du cloud :** Cette dénomination est devenue une fierté pour de nombreux architectes cloud spécialisés dans la gouvernance des premiers stades. Quand des pratiques de gouvernance se mettent en place, les résultats ont l’air similaires à ceux qu’obtiennent des volontaires. Toutefois, il existe une différence fondamentale. Un dépositaire du cloud a un plan à l’esprit. À ce stade de maturité, l’équipe consacre du temps à corriger les erreurs faites par les architectes cloud qui l’ont précédé. Toutefois, l’opérateur du cloud adapte cet effort à une stratégie d’entreprise bien structurée. Il utilise aussi des outils de gouvernance, comme ceux qui sont décrits dans le MVP de gouvernance.

Une autre différence fondamentale entre un dépositaire du cloud et un volontaire est le soutien du supérieur hiérarchique. Le volontaire fait des heures supplémentaires par rapport à ce qui est attendu de lui parce qu’il a envie d’apprendre et de faire. Le dépositaire du cloud est soutenu par sa direction pour réduire ses tâches quotidiennes afin de veiller à ce que du temps soit régulièrement alloué et investi pour l’amélioration de la gouvernance cloud.

**Gardien du cloud :** À mesure que les pratiques de gouvernance se consolident et sont acceptées par les équipes d’adoption du cloud, le rôle des architectes cloud spécialisés dans la gouvernance change un peu, de même que le rôle de l’équipe de gouvernance cloud. En règle générale, les pratiques les plus éprouvées attirent l’attention d’autres experts capables de renforcer les protections fournies par les implémentations de gouvernance.

Si cette différence est subtile, il s’agit néanmoins d’une distinction importante lors de l’élaboration d’une culture informatique centrée sur la gouvernance. Un gardien du cloud s’occupe de la remise en ordre rendue nécessaire par les actions innovantes des architectes cloud, et les deux rôles engendrent naturellement des frictions et ont des objectifs opposés. Un gardien du cloud aide à conserver le cloud sécurisé, afin que d’autres architectes cloud puissent effectuer les migrations plus rapidement, avec moins de désordres.
Les gardiens du cloud commencent à utiliser des approches de gouvernance plus avancées pour accélérer le déploiement de la plateforme et aider les équipes à répondre librement à leurs besoins environnementaux, pour une adoption plus rapide. Des exemples de ces fonctions plus avancées sont présentés dans les améliorations incrémentielles apportées au MVP de gouvernance, comme l’amélioration de la base de référence de sécurité.

**Accélérateurs cloud :** Les gardiens et les opérateurs du cloud récoltent naturellement des scripts et des outils de gouvernance qui accélèrent le déploiement des environnements, des plateformes ou même des composants de diverses applications. L’organisation et le partage de ces scripts en plus des responsabilités de gouvernance centralisées développent un degré élevé de respect pour ces architectes au sein du service informatique.

Ces praticiens de la gouvernance qui partagent ouvertement leurs scripts organisés facilitent la livraison rapide de projets technologiques et l’incorporation de la gouvernance dans l’architecture des charges de travail. Cette influence sur les charges de travail et la prise en charge de bons modèles de conception élèvent les accélérateurs cloud à un niveau supérieur de spécialisation de gouvernance.

**Gouvernance globale :** Quand les organisations dépendent de besoins informatiques globalement dispersés, des écarts significatifs dans les opérations et la gouvernance peuvent apparaître dans les différentes zones géographiques. Les besoins de division et même les exigences de souveraineté des données locales peuvent entraîner des interférences entre les bonnes pratiques de gouvernance et les opérations nécessaires. Dans ces scénarios, un modèle de gouvernance hiérarchisé permet une cohérence viable minimale et une gouvernance localisée. L’article sur les couches multiples de gouvernance fournit plus d’insights sur ce niveau de maturité.

Chaque entreprise est unique, il en va de même pour ses besoins en matière de gouvernance. Choisissez le niveau de maturité adapté à votre organisation et utilisez le Framework d’adoption du cloud pour sélectionner les pratiques, les processus et les outils qui vont vous aider à y parvenir.

Plus la gouvernance cloud mûrit, plus vite les équipes sont en mesure d’adopter le cloud. Les efforts continus en matière d’adoption du cloud ont tendance à faire mûrir les opérations informatiques. Développez une équipe chargée de l’exploitation du cloud ou collaborez étroitement avec elle pour intégrer la gouvernance au développement opérationnel.

Découvrez comment mettre en place une [équipe chargée de la gouvernance cloud](../get-started/team/cloud-governance.md) ou une [équipe chargée de l’exploitation du cloud](../get-started/team/cloud-operations.md).

Une fois que vous avez établi une [base de gouvernance cloud initiale](../govern/initial-foundation.md), appliquez ces meilleures pratiques dans [Améliorations de la base de gouvernance](../govern/foundation-improvements.md) pour anticiper votre plan d’adoption et éviter les risques.
