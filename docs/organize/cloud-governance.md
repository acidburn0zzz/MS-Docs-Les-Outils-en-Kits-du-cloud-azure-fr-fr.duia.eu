---
title: Compétences de gouvernance cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Décrit la mise en place des compétences de gouvernance cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 33942811554556b1f67dc6515a8c679b09bfa983
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224009"
---
# <a name="cloud-governance-capabilities"></a>Compétences de gouvernance cloud

Tout type de changement entraîne de nouveaux risques. Les compétences de gouvernance cloud permettent d’évaluer et de gérer correctement les risques et la tolérance aux risques. Cette compétence garantit une identification correcte des risques que l’entreprise ne peut pas tolérer. Les personnes qui fournissent cette compétence peuvent alors convertir les risques en stratégies de gouvernance d’entreprise. Les stratégies de gouvernance sont alors exécutées par le biais de disciplines définies que les membres du personnel qui fournissent des compétences de gouvernance cloud mettent en application.

## <a name="possible-sources-for-this-capability"></a>Sources possibles pour cette compétence

Selon les résultats souhaités par l’entreprise, les aptitudes nécessaires pour fournir des compétences complètes de gouvernance cloud peuvent être fournies par les services suivants :

- Gouvernance informatique
- Architecture d’entreprise
- Opérations informatiques
- Infrastructure informatique
- Mise en réseau
- Identité
- Virtualisation
- Continuité de l’activité/Reprise d’activité
- Propriétaires d’applications au sein du service informatique

La compétence de gouvernance cloud identifie les risques liés aux mises en production actuelles et futures. Cette compétence est observée dans les efforts d’évaluation des risques, de compréhension des impacts potentiels et de prise de décisions concernant la tolérance aux risques. Ce faisant, des plans peuvent rapidement être mis à jour pour refléter les besoins en constante évolution de la [capacité d’adoption du cloud](./cloud-adoption.md).

## <a name="key-responsibilities"></a>Responsabilités principales

La principale fonction d’une compétence de gouvernance cloud est d’équilibrer les forces opposées de transformation et d’atténuation des risques. De plus, la gouvernance cloud veille à ce que l’[adoption du cloud](./cloud-adoption.md) ait connaissance des recommandations liées à la classification et l’architecture des données et ressources qui régissent toutes les approches d’adoption. L’équipe va aussi travailler avec le [centre d’excellence du cloud](./cloud-center-of-excellence.md) pour appliquer des approches automatisées à la gouvernance des environnements cloud.

Ces tâches sont généralement exécutées tous les mois par la compétence de gouvernance cloud.

**Tâches de planification précoces :**

- Comprendre les [risques métier](../govern/policy-compliance/risk-tolerance.md) introduits par le plan
- Représenter la [tolérance aux risques de l’entreprise](../govern/policy-compliance/risk-tolerance.md)
- Faciliter la création d’un [MVP de gouvernance](../govern/guides/index.md)

**Tâches mensuelles suivies :**

- Comprendre les [risques métier](../govern/policy-compliance/risk-tolerance.md) introduits à chaque mise en production
- Représenter la [tolérance aux risques de l’entreprise](../govern/policy-compliance/risk-tolerance.md)
- Faciliter l’amélioration incrémentielle des [exigences de stratégie et de conformité](../govern/policy-compliance/index.md)

## <a name="meeting-cadence"></a>Cadence des réunions

La compétence de gouvernance cloud est généralement assurée par une équipe de travail. Le temps qu’y consacre chaque membre d’équipe représente un important pourcentage de son emploi du temps quotidien. Les contributions ne sont pas limitées aux réunions et aux cycles de commentaires.

## <a name="additional-participants"></a>Participants supplémentaires

Voici les participants qui prennent fréquemment part aux activités de gouvernance cloud :

- Les cadres intermédiaires et les contributeurs directs qui occupent des rôles clés, désignés pour représenter l’entreprise, aident dans l’évaluation des tolérances aux risques.
- Les compétences de gouvernance cloud sont souvent une extension de la [compétence de stratégie cloud](./cloud-strategy.md). De la même façon que les dirigeants sont censés participer aux compétences de stratégie cloud, leurs collaborateurs direct sont censés participer aux activités de gouvernance cloud.
- Les employés de l’entreprise membres de la division qui travaillent en étroite collaboration avec la direction doivent être en mesure de prendre des décisions concernant les risques d’entreprise et techniques.
- Les employés du service informatique et du service de la sécurité des informations qui comprennent les aspects techniques de la transformation cloud peuvent être sollicités ponctuellement au lieu d’assurer constamment les compétences de gouvernance cloud.

## <a name="maturation-of-cloud-governance-capability"></a>Maturation de la compétence de gouvernance cloud

Certaines grandes organisations ont des équipes dédiées existantes qui se concentrent sur la gouvernance informatique. Ces équipes sont spécialisées dans la gestion des risques de tout le portefeuille informatique par le biais de méthodologies comme ITIL ou ITSM. Lorsque ces équipes existent, les modèles de maturité suivants peuvent être rapidement accélérés. En revanche, l’équipe de gouvernance informatique est encouragée à examiner le modèle de gouvernance cloud pour comprendre comment la gouvernance évolue légèrement vers le cloud. Consultez notamment les articles sur l’[extension de la stratégie d’entreprise vers le cloud](../govern/corporate-policy.md) et les [cinq disciplines de gouvernance cloud](../govern/governance-disciplines.md).

**Aucune gouvernance :** Il est courant pour les organisations d’adopter le cloud sans établir clairement de plans de gouvernance. Très vite, des préoccupations liées à la sécurité, au coût, à l’échelle et aux opérations commencent à déclencher des conversations sur le besoin d’un modèle de gouvernance et de personnes pour s’occuper des processus associés à ce modèle. Aborder ces sujets avant qu’ils ne deviennent des préoccupations s’avère toujours une démarche préliminaire utile pour éviter l’antimodèle « aucune gouvernance ». La section sur la [définition d’une stratégie d’entreprise](../govern/corporate-policy.md) peut faciliter ces conversations.

**Gouvernance bloquée :** Quand les préoccupations liées à la sécurité, au coût, à l’échelle et aux opérations ne sont pas considérées, les projets et les objectifs de l’entreprise ont tendance à bloquer. Un manque de gouvernance appropriée génère de la peur, de l’incertitude et des doutes parmi les parties prenantes et les ingénieurs. Mettez-y fin tout de suite en prenant des mesures précoces. Les deux guides de gouvernance définis dans le Framework d’adoption du cloud peuvent vous aider à démarrer modestement, puis à définir des stratégies de limitation initiales afin de réduire l’incertitude et d’affiner la gouvernance au fil du temps. Choisissez entre le [guide pour entreprise complexe](../govern/guides/complex/index.md) ou le [guide pour entreprise standard](../govern/guides/standard/index.md).

**Gouvernance volontaire :** Il y a des personnes volontaires dans toutes les entreprises. Ces cœurs vaillants sont toujours prêts à se jeter à l’eau pour aider leur équipe à tirer des leçons de ses erreurs. C’est souvent comme cela que commence la gouvernance, particulièrement dans les petites entreprises. Ces courageux consacrent du temps à résoudre les problèmes et poussent les équipes d’adoption du cloud vers un ensemble bien géré et cohérent de bonnes pratiques.

Les efforts de ces personnes valent bien mieux que les scénarios « aucune gouvernance » ou « gouvernance bloquée ». Même si ces efforts sont louables, cette approche ne doit pas être confondue avec la gouvernance. Une véritable gouvernance nécessite bien plus qu’un soutien sporadique pour être cohérente, laquelle cohérence constitue l’objectif de toute bonne approche de gouvernance. Les conseils données dans les [cinq disciplines de gouvernance cloud](../govern/governance-disciplines.md) permettent de développer cette discipline.

**Dépositaire du cloud :** Cette dénomination est devenue une fierté pour de nombreux architectes cloud spécialisés dans la gouvernance des premiers stades. Quand des pratiques de gouvernance se mettent en place, les résultats ont l’air similaires à ceux qu’obtiennent des volontaires. Toutefois, il existe une différence fondamentale. Un dépositaire du cloud a un plan à l’esprit. À ce stade de maturité, l’équipe consacre du temps à corriger les erreurs faites par les architectes cloud qui l’ont précédé. Toutefois, le dépositaire du cloud adapte cet effort à une [stratégie d’entreprise](../govern/corporate-policy.md) bien structurée. Il utilise aussi des outils d’automatisation de gouvernance, comme ceux décrits dans le [MVP de gouvernance](../govern/guides/complex/index.md).

Une autre différence fondamentale entre un dépositaire du cloud et un volontaire est le soutien du supérieur hiérarchique. Le volontaire fait des heures supplémentaires par rapport à ce qui est attendu de lui parce qu’il a envie d’apprendre et de faire. Le dépositaire du cloud est soutenu par sa direction pour réduire ses tâches quotidiennes afin de veiller à ce que du temps soit régulièrement alloué et investi pour l’amélioration de la gouvernance cloud.

**Gardien du cloud :** À mesure que les pratiques de gouvernance se consolident et sont acceptées par les équipes d’adoption du cloud, le rôle des architectes cloud spécialisés dans la gouvernance change un peu, de même que le rôle de l’équipe de gouvernance cloud. En règle générale, les pratiques les plus éprouvées attirent l’attention d’autres experts capables de renforcer les protections fournies par les implémentations de gouvernance.

Si cette différence est subtile, il s’agit néanmoins d’une distinction importante lors de l’élaboration d’une culture informatique centrée sur la gouvernance. Un gardien du cloud s’occupe de la remise en ordre rendue nécessaire par les actions innovantes des architectes cloud, et les deux rôles engendrent naturellement des frictions et ont des objectifs opposés. Un gardien du cloud aide à conserver le cloud sécurisé, afin que d’autres architectes cloud puissent effectuer les migrations plus rapidement, avec moins de désordres.

Les gardiens du cloud commencent à utiliser des approches de gouvernance plus avancées pour accélérer le déploiement de la plateforme et aider les équipes à répondre librement à leurs besoins environnementaux, pour une adoption plus rapide. Des exemples de ces fonctions plus avancées s’illustrent dans les améliorations incrémentielles apportées au MVP de gouvernance, comme l’[amélioration de la base de référence de sécurité](../govern/guides/complex/security-baseline-improvement.md).

**Accélérateurs cloud :** Les gardiens et les dépositaires du cloud récoltent naturellement des scripts et des automatisations qui accélèrent le déploiement des environnements, des plateformes, voire même des composants de diverses applications. L’organisation et le partage de ces scripts en plus des responsabilités de gouvernance centralisées développent un degré élevé de respect pour ces architectes au sein du service informatique.

Ces praticiens de la gouvernance qui partagent ouvertement leurs scripts organisés facilitent la livraison rapide de projets technologiques et l’incorporation de la gouvernance dans l’architecture des charges de travail. Cette influence sur les charges de travail et la prise en charge de bons modèles de conception élèvent les accélérateurs cloud à un niveau supérieur de spécialisation de gouvernance.

**Gouvernance globale :** Quand les organisations dépendent de besoins informatiques globalement dispersés, des écarts significatifs dans les opérations et la gouvernance peuvent apparaître dans les différentes zones géographiques. Les besoins de division et même les exigences de souveraineté des données locales peuvent entraîner des interférences entre les bonnes pratiques de gouvernance et les opérations nécessaires. Dans ces scénarios, un modèle de gouvernance hiérarchisé permet une cohérence viable minimale et une gouvernance localisée. L’article sur les [multiples couches de gouvernance](../govern/guides/complex/multiple-layers-of-governance.md) fournit plus d’insights sur l’atteinte de ce niveau de maturité.

Chaque entreprise est unique, il en va de même pour ses besoins en matière de gouvernance. Choisissez le niveau de maturité adapté à votre organisation et utilisez le Framework d’adoption du cloud pour sélectionner les pratiques, les processus et les outils qui vont vous aider à y parvenir.

## <a name="next-steps"></a>Étapes suivantes

Au fur et à mesure que la gouvernance cloud mûrit, les équipes sont en mesure d’adopter le cloud selon un rythme encore plus rapide. Les efforts continus en matière d’adoption du cloud ont tendance à faire mûrir les opérations informatiques. Cette maturation peut aussi nécessiter le développement de [compétences d’opérations cloud](./cloud-operations.md).

> [!div class="nextstepaction"]
> [Développer des compétences d’opérations cloud](./cloud-operations.md)
