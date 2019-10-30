---
title: Capacités informatiques centrales
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: En savoir plus sur la formation des fonctionnalités de l’informatique centralisée.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: d1d59b105dd6d75b0c5b5ed12d711473fd4995c8
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549120"
---
# <a name="central-it-capabilities"></a>Fonctionnalités de l’informatique centralisée

Dans le cadre de l’adoption du cloud, les capacités de gouvernance cloud ne sont pas suffisantes pour régir les efforts d’adoption. Lorsque l’adoption est progressive, les équipes ont tendance à développer de façon biologique les compétences et les processus qui devaient être prêts pour le cloud au fil du temps.

Toutefois, lorsqu’une équipe chargée de l’adoption du cloud tire parti du cloud pour obtenir un résultat métier élevé, l’adoption progressive est rare. La réussite génère la réussite. Cela est également vrai pour l’adoption du cloud, mais cela se produit à l’échelle du cloud. Lorsque l’adoption du cloud s’étend d’une équipe à plusieurs équipes dans un laps de temps relativement bref, une prise en charge supplémentaire du personnel informatique existant est nécessaire. Toutefois, ces membres du personnel peuvent manquer de la formation et de l’expérience nécessaires à la prise en charge du cloud à l’aide des outils informatiques cloud natifs. Cela conduit souvent à la formation d’une équipe d’informatique centralisée qui régit le cloud.

> [!CAUTION]
> Bien qu’il s’agisse d’une étape de maturité courante, elle peut présenter un risque élevé d’adoption, bloquant potentiellement l’innovation et les efforts de migration, en l’absence de gestion efficace. Consultez la section Risque ci-dessous pour savoir comment atténuer le risque que la centralisation devienne un antimodèle culturel.

## <a name="possible-sources-for-central-it-expertise"></a>Sources possibles pour l’expertise informatique centralisée

Les compétences nécessaires pour fournir des fonctionnalités d’informatique centralisée peuvent être fournies par :

- Une équipe informatique centralisée existante
- Des architectes d’entreprise
- Opérations informatiques
- Gouvernance informatique
- Infrastructure informatique
- Mise en réseau
- Identité
- Virtualisation
- Continuité d’activité et reprise d’activité
- Propriétaires d’applications au sein du service informatique

> [!WARNING]
> L’informatique centralisée doit être appliquée uniquement dans le cloud lorsque la livraison existante en local est basée sur un modèle d’informatique centralisée. Si le modèle local actuel est basé sur un contrôle délégué, envisagez une approche Cloud Center of Excellence (CCoE) qui offre une alternative plus compatible.

## <a name="key-responsibilities"></a>Responsabilités principales

Adaptez les pratiques informatiques existantes pour garantir l’adoption des environnements bien gérés et bien régis dans le cloud.

Les tâches suivantes sont généralement exécutées régulièrement :

### <a name="strategic-tasks"></a>Tâches stratégiques

- Révision :
  - [résultats métier](../strategy/business-outcomes/index.md)
  - [modèles financiers](../strategy/financial-models.md)
  - [motivations en faveur de l’adoption du cloud](../strategy/motivations.md)
  - [risques métier](../govern/policy-compliance/risk-tolerance.md)
  - [rationalisation du patrimoine numérique](../digital-estate/index.md)
- Surveillez les plans d’adoption et la progression par rapport au [backlog de migration classé par ordre de priorité](../migrate/migration-considerations/assess/release-iteration-backlog.md).
- Identifiez et hiérarchisez les modifications de plateforme requises pour prendre en charge le backlog de migration.
- Servez de couche intermédiaire ou de traduction entre les besoins en matière d’adoption du cloud et les équipes informatiques existantes.
- Faites appel aux équipes informatiques existantes pour accélérer les fonctionnalités de la plateforme et encourager l’adoption.

### <a name="technical-tasks"></a>Tâches techniques

- Créez et gérez la plateforme cloud pour prendre en charge les solutions.
- Définissez et implémentez l’architecture de la plateforme.
- Exploitez et gérez la plateforme cloud.
- Améliorez continuellement la plateforme.
- Suivez les nouvelles innovations de la plateforme cloud.
- Ajoutez de nouvelles fonctionnalités cloud pour prendre en charge la création de valeurs métier.
- Suggérer des solutions en libre-service.
- Vérifiez que les solutions respectent les exigences de gouvernance/conformité existantes.
- Créez et validez le déploiement de l’architecture de la plateforme.
- Passez en revue les plans de mise en production pour les sources de nouvelles opportunités d’automatisation.

## <a name="meeting-cadence"></a>Cadence des réunions

L’expertise informatique centrale provient généralement d’une équipe de travail. Attendez-vous à ce que les participants valident la plupart de leurs planifications quotidiennes dans le cadre des efforts d’alignement. Les contributions ne sont pas limitées aux réunions et aux cycles de retours d’expérience.

## <a name="central-it-risks"></a>Risques liés à l’informatique centralisée

Chacune des fonctionnalités cloud et des phases de maturité de l’organisation sont précédées du mot « cloud ». L’informatique centralisée est la seule exception. L’informatique centralisée est devenue prédominante lorsque toutes les ressources informatiques pouvaient être hébergées dans peu de sites, gérées par un petit nombre d’équipes et contrôlées via une seule plateforme de gestion des opérations. Les pratiques commerciales mondiales et l’économie numérique ont largement réduit les instances de ces environnements managés de manière centralisée.

Dans le monde informatique moderne, les ressources sont distribuées dans le monde entier. Les responsabilités sont déléguées. La gestion des opérations est assurée par un mélange de personnel interne, de fournisseurs de services managés et de fournisseurs de services cloud. Dans l’économie numérique, les pratiques de gestion informatique sont transférées vers un modèle libre-service et de contrôle délégué avec des barrières de sécurité claires pour appliquer la gouvernance. L’informatique centralisée peut être un contributeur important à l’adoption du cloud en devenant un courtier cloud et un partenaire pour l’innovation et l’agilité métier.

L’informatique centralisée en tant que fonction est bien positionnée pour obtenir des connaissances et des pratiques précieuses à partir des modèles locaux existants et appliquer ces pratiques à la livraison cloud. Toutefois, ce processus nécessite des modifications. De nouveaux processus, de nouvelles compétences et de nouveaux outils sont nécessaires pour prendre en charge l’adoption du cloud à grande échelle. Lorsque l’informatique centralisée s’adapte, elle devient un partenaire important dans le cadre des efforts d’adoption du cloud. Toutefois, si l’informatique centralisée ne s’adapte pas au cloud ou tente d’utiliser le cloud comme catalyseur pour des contrôles étroits, elle devient rapidement un bloqueur de l’adoption, de l’innovation et de la migration.

Les mesures de ce risque sont la vitesse et la flexibilité. Le cloud simplifie l’adoption rapide de nouvelles technologies. Quand de nouvelles fonctionnalités cloud peuvent être déployées en quelques minutes, mais que les révisions de l’informatique centralisée ajoutent des semaines ou des mois au processus de déploiement, ces processus centralisés deviennent un obstacle majeur au succès de l’entreprise. Lorsque vous rencontrez cet indicateur, envisagez d’autres stratégies de livraison informatique.

### <a name="exceptions"></a>Exceptions

De nombreux secteurs requièrent un respect strict de la conformité tierce. Certaines exigences de conformité exigent toujours un contrôle informatique centralisé. La mise en œuvre de ces mesures de conformité peut ajouter du temps aux processus de déploiement, en particulier pour les nouvelles technologies qui n’ont pas été utilisées à grande échelle. Dans ces scénarios, attendez-vous à des retards de déploiement au cours des premières phases d’adoption. Des situations similaires existent pour les entreprises qui gèrent des données client sensibles, mais peuvent ne pas être régies par une exigence de conformité tierce.

### <a name="operating-within-the-exceptions"></a>Exploitation malgré les exceptions

Lorsque des processus informatiques centralisés sont requis et que ces processus créent des points de contrôle appropriés en adoptant de nouvelles technologies, ces points de contrôle d’innovation peuvent toujours être gérés rapidement. Les exigences de gouvernance et de conformité sont conçues pour protéger les éléments sensibles, et non pour tout protéger. Le cloud fournit des mécanismes simples pour l’acquisition et le déploiement de ressources isolées tout en maintenant une barrière de sécurité adaptée.

Une équipe informatique centralisée mature maintient les protections nécessaires, mais négocie des pratiques qui encouragent toujours l’innovation. La démonstration de ce niveau de maturité dépend de la classification et de l’isolation appropriées des ressources.

### <a name="example-narrative-of-operating-within-exceptions-to-empower-adoption"></a>Exemple narratif de l’exploitation malgré les exceptions pour encourager l’adoption

Cet exemple narratif illustre l’approche adoptée par une équipe informatique centralisée mature pour encourager l’adoption.

La société Contoso, LLC a adopté un modèle d’informatique centralisée pour la prise en charge des ressources cloud de l’entreprise. Pour fournir ce modèle, elle a implémenté des contrôles étroits pour différents services partagés tels que les connexions réseau entrantes. Cela a permis de réduire l’exposition de son environnement cloud et de fournir un appareil unique de « basculement » pour bloquer tout le trafic en cas de violation. Sa stratégie Base de référence de la sécurité indique que tout le trafic entrant doit traverser un appareil partagé géré par l’équipe informatique centralisée.

Toutefois, l’une de ses équipes d’adoption du cloud requiert à présent un environnement avec une connexion réseau d’entrée dédiée et spécialement configurée pour tirer parti d’une technologie cloud spécifique. Une équipe informatique centralisée immature pourrait simplement refuser la demande et donner la priorité aux processus existants et non aux besoins d’adoption. L’équipe informatique centralisée de Contoso fonctionne différemment. Elle a rapidement identifié une solution simple en quatre parties à ce dilemme : classification, négociation, isolation et automatisation.

**Classification :** Étant donné que l’équipe chargée de l’adoption du cloud gérait les premières étapes de création d’une nouvelle solution et n’avait pas de données sensibles ou de besoins en support stratégique, les ressources de l’environnement étaient classées comme étant à faible risque et non critiques. Une classification efficace est un signe de maturité dans l’informatique centralisée. La classification de l’ensemble des ressources et des environnements permet d’obtenir des stratégies plus claires.

**Négociation :** La classification seule n’est pas suffisante. Des services partagés ont été implémentés pour exploiter de manière cohérente des ressources sensibles et stratégiques. La modification des règles compromettrait les stratégies de gouvernance et de conformité conçues pour les ressources qui nécessitent une protection accrue. L’adoption ne peut pas se produire au détriment de la stabilité, de la sécurité ou de la gouvernance. Cela a conduit à une négociation avec l’équipe d’adoption pour répondre à des questions spécifiques. Une équipe DevOps dirigée par l’entreprise sera-t-elle en mesure de fournir la gestion des opérations pour cet environnement ? Cette solution nécessite-t-elle un accès direct à d’autres ressources internes ? Si l’équipe chargée de l’adoption du cloud est à l’aise avec ces compromis, le trafic d’entrée peut être possible.

**Isolation :** Étant donné que l’entreprise peut fournir sa propre gestion des opérations en cours et que la solution n’est pas dépendante du trafic direct vers d’autres ressources internes, elle peut être coordonnée dans un nouvel abonnement. Cet abonnement est également ajouté à un nœud distinct de la nouvelle hiérarchie des groupes d’administration.

**Automatisation :** Un autre signe de maturité au sein de cette équipe est son principe d’automatisation. L’équipe utilise Azure Policy pour automatiser l’application des stratégies. Elle utilise également Azure Blueprints pour automatiser le déploiement des composants de plateforme courants et appliquer l’adhésion à la ligne de base d’identité définie. Pour cet abonnement et d’autres abonnements du nouveau groupe d’administration, les stratégies et les modèles sont légèrement différents. Les stratégies bloquant la bande passante d’entrée ont été levées. Elles ont été remplacées par des exigences pour router le trafic via l’abonnement aux services partagés, comme le trafic entrant, afin d’appliquer l’isolation du trafic. Étant donné que les outils de gestion des opérations en local ne peuvent pas accéder à cet abonnement, les agents associés à cet outil ne sont plus nécessaires. Toutes les autres barrières de sécurité de gouvernance requises par d’autres abonnements dans la hiérarchie des groupes d’administration sont toujours appliquées, garantissant ainsi une protection suffisante.

L’approche créative mature de l’équipe informatique centralisée de Contoso a fourni une solution qui ne compromet pas la gouvernance ni la conformité, mais encourage toujours l’adoption. Cette approche de répartition plutôt que de détention des approches cloud natives pour l’informatique centralisée est la première étape vers la création d’un véritable centre cloud d’excellence (CCoE). L’adoption de cette approche pour faire évoluer rapidement les stratégies existantes permet de faire appel à un contrôle centralisé si nécessaire et à des barrières de sécurité de la gouvernance quand une plus grande flexibilité est acceptable. L’équilibrage de ces deux considérations réduit les risques associés à l’informatique centralisée dans le cloud.

## <a name="next-steps"></a>Étapes suivantes

À mesure que l’informatique centralisée prend de la maturité dans le cloud, l’étape de maturité suivante est généralement un couplage plus souple des [opérations cloud](./cloud-operations.md). La disponibilité d’outils de gestion cloud natifs pour les opérations cloud et de coûts d’exploitation réduits pour les solutions PaaS-First mène souvent au fait que les équipes commerciales (ou plus précisément, les équipes DevOps au sein de l’entreprise) prennent la responsabilité des opérations cloud.

> [!div class="nextstepaction"]
> [Capacité des opérations cloud](./cloud-operations.md)
