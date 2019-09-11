---
title: Répondre à la complexité de la migration de plusieurs régions géographiques
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Répondre à la complexité de la migration de plusieurs régions géographiques.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 3977618981212e2c0dc4dcd95ae14bf4dc773499
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905589"
---
# <a name="multiple-geographic-regions"></a>Zones géographiques multiples

Lorsque les entreprises opèrent dans plusieurs régions géographiques, une complexité supplémentaire peut être introduite dans les efforts de migration vers le cloud. Ces complexités se manifestent sous trois formes principales : la distribution de ressources, les profils d’accès utilisateur et les exigences de conformité. Avant de répondre aux complexités liées à plusieurs régions, il est important de comprendre l’ampleur de la complexité potentielle.

## <a name="general-scope-expansion"></a>Expansion de l’étendue générale

L’approche suivante peut vous aider à évaluer les défis potentiels et à établir un cours d’action général :

- Envisagez une implémentation plus robuste de la préparation et de la gouvernance.
- Inventoriez les zones géographiques affectées. Compilez une liste des régions et des pays qui sont affectés par la migration vers le cloud.
- Documentez les exigences de souveraineté des données : Les pays identifiés ont-ils des exigences de conformité qui régissent la souveraineté des données ?
- Documentez la base utilisateur : Les employés, partenaires ou clients dans le pays identifié seront-ils affectés par la migration vers le cloud ?
- Documentez les ressources et centres de données : Existe-t-il des ressources dans le pays identifié qui peuvent être incluses dans l’effort de migration ?

Alignez les modifications à travers le processus de migration pour traiter l’inventaire initial.

### <a name="documenting-complexity"></a>Documentation de la complexité

Le tableau suivant peut vous aider à documenter les résultats des étapes précédentes :

|Région  |Country  |Employés locaux  |Utilisateurs externes locaux  |Ressources ou centres de données locaux |Exigences de souveraineté des données  |
|---------|---------|---------|---------|---------|---------|
|Amérique du Nord     |États-Unis         |OUI         |Partenaires et clients         |OUI         |Non         |
|Amérique du Nord     |Canada         |Non         |Clients         |OUI         |OUI         |
|Europe     |Allemagne         |OUI         |Partenaires et clients         |Non - Réseau uniquement         |OUI         |
|Asie-Pacifique     |Corée du Sud         |OUI         |Partenaires         |OUI         |Non         |

<!-- markdownlint-disable MD026 -->

### <a name="why-is-data-sovereignty-relevant"></a>Pourquoi la souveraineté des données est-elle pertinente ?

Dans le monde entier, les organisations gouvernementales ont commencé à établir des exigences en matière de souveraineté des données, comme le Règlement général sur la protection des données (RGPD). Les exigences de conformité de cette nature requièrent souvent une localisation au sein d’une région spécifique ou même au sein d’un pays spécifique pour protéger ses citoyens. Dans certains cas, les données relatives aux clients, aux employés ou aux partenaires doivent être stockées sur une plateforme cloud au sein de la même région que l’utilisateur final.

La réponse à ce défi a été une motivation importante pour les entreprises qui opèrent à l’échelle mondiale. Pour respecter les exigences de conformité, certaines entreprises ont choisi de déployer des ressources informatiques dupliquées sur des fournisseurs de Cloud au sein de la région. Dans l’exemple de tableau ci-dessus, l’Allemagne est un bon exemple de ce scénario. Dans cet exemple, il existe des clients, des partenaires et des employés en Allemagne, mais pas de ressources informatiques existantes. Cette société peut choisir de déployer des ressources dans un centre de données dans la zone couverte par le RGPD, en utilisant potentiellement des centres de données d’Azure en Allemagne. La compréhension des données affectées par le RGPD aidera l’équipe chargée de l’adoption du cloud à comprendre la meilleure approche de migration dans ce cas.

### <a name="why-is-the-location-of-end-users-relevant"></a>Pourquoi l’emplacement des utilisateurs finaux est-il pertinent ?

Les entreprises qui prennent en charge des utilisateurs finaux dans plusieurs pays ont développé des solutions techniques pour traiter le trafic des utilisateurs finaux. Dans certains cas, cela implique la localisation des ressources. Dans d’autres scénarios, l’entreprise peut choisir de mettre en œuvre des solutions de réseau étendu globales pour gérer des bases d’utilisateurs disparates via des solutions axées sur le réseau. Dans les deux cas, la stratégie de migration peut être affectée par les profils d’utilisation de ces utilisateurs finaux disparates.

Étant donné que la société prend en charge les employés, les partenaires et les clients en Allemagne, mais qu’il n’y a actuellement pas de centres de données dans ce pays, il est probable que cette société mette en place une forme de solution de ligne de crédit pour acheminer le trafic vers les centres de données dans d’autres pays. Ce routage existant présente un risque significatif pour les performances perçues des applications migrées. L’injection de sauts supplémentaires dans un WAN global établi et réglé peut créer la perception d’applications sous-performantes après la migration. La recherche et la résolution de ces problèmes peuvent entraîner des retards importants pour un projet. Dans chacun des processus ci-dessous, des conseils sur la façon de résoudre cette complexité sont inclus dans les processus d’établissement des conditions préalables, d’évaluation, de migration et d’optimisation. Il est essentiel de comprendre les profils utilisateur dans chaque pays pour gérer correctement cette complexité.

### <a name="why-is-the-location-of-datacenters-relevant"></a>Pourquoi l’emplacement des centres de données est-il pertinent ?

L’emplacement des centres de données existants peut affecter une stratégie de migration. Voici quelques-uns des impacts les plus courants :

**Décisions relatives à l’architecture :** Le ciblage de la région/l’emplacement est l’une des premières étapes de la conception de la stratégie de migration. Cela est souvent influencé par l’emplacement des ressources existantes. En outre, les services cloud disponibles et le coût unitaire de ces services peuvent varier d’une région à l’autre. Ainsi, la compréhension de l’emplacement actuel et futur des ressources affecte les décisions d’architecture et peut également affecter les estimations de budget.

**Dépendances du centre de données :** En fonction des données du tableau ci-dessus, il est probable que des dépendances existent entre les différents centres de données dans le monde. Dans de nombreuses organisations qui opèrent sur ce type de mise à l’échelle, ces dépendances peuvent ne pas être documentées ou bien comprises. Les approches utilisées pour évaluer les profils utilisateur vous aideront à identifier certaines de ces dépendances. Toutefois, des étapes supplémentaires sont suggérées au cours du processus d’évaluation pour atténuer les risques associés à cette complexité.

## <a name="implementing-the-general-approach"></a>Implémentation de l’approche générale

Cette approche est pilotée par des informations quantifiables. Par conséquent, l’approche suivante suit un modèle piloté par les données pour répondre aux complexités de la migration globale.

## <a name="suggested-prerequisites"></a>Prérequis suggérés

Nous vous suggérons que l’équipe d’adoption cloud commence par la migration d’une charge de travail simple à l’aide du [Guide de migration Azure](../azure-migration-guide/index.md), avant d’essayer de s’attaquer à la mise à l’échelle mondiale. Cela permet à l’équipe de se familiariser avec le processus général de migration cloud avant de tenter un scénario de migration plus complexe.

Lorsque l’étendue d’une migration comprend plusieurs régions, les considérations suivantes relatives à la disponibilité doivent être évaluées par l’équipe d’adoption cloud :

- La souveraineté des données peut nécessiter la localisation de certaines ressources, mais il existe de nombreuses ressources qui peuvent ne pas être régies par ces contraintes de conformité. Des opérations telles que la journalisation, la création de rapports, le routage réseau, l’identité et d’autres services informatiques centraux peuvent être admissibles pour être hébergés en tant que services partagés sur plusieurs abonnements, voire dans plusieurs régions. Il est recommandé que l’équipe d’adoption cloud évalue un modèle de partage pour ces services, comme indiqué dans [l’architecture de référence pour une topologie hub-and-spoke avec des services partagés](/azure/architecture/reference-architectures/hybrid-networking/shared-services)
- Lors du déploiement de plusieurs instances d’environnements similaires, une fabrique d’environnement peut assurer la cohérence, améliorer la gouvernance et accélérer le déploiement. Le [parcours de gouvernance pour les grandes entreprises](../../governance/journeys/complex-enterprise/index.md) établit une approche qui crée une fabrique d’environnement qui évolue dans plusieurs régions.

Une fois que l’équipe est à l’aise avec l’approche de base et que la préparation est alignée, il existe quelques conditions préalables basées sur les données à prendre en compte :

- **Découverte générale :** Complétez le tableau de [documentation de la complexité](#documenting-complexity) ci-dessus.
- **Effectuez une analyse de profil utilisateur sur chaque pays affecté :** Il est important de comprendre le routage de l’utilisateur final général tôt lors du processus de migration. La modification des lignes d’emprunt globales et l’ajout de connexions comme ExpressRoute à un centre de données cloud peut nécessiter des mois de retards réseau. Résolvez cela aussi tôt que possible dans le processus.
- **Rationalisation initiale du patrimoine numérique :** Chaque fois que de la complexité est introduite dans une stratégie de migration, une rationalisation initiale doit être effectuée. Pour obtenir de l'aide, consultez l’aide sur la [rationalisation du patrimoine numérique](../../digital-estate/index.md).
  - **Exigences supplémentaires relatives au patrimoine :** Établissez des stratégies de marquage pour identifier les charges de travail affectées par les exigences de souveraineté des données. Les étiquettes requises doivent commencer par la rationalisation du patrimoine numérique et traverser les ressources migrées.
- **Évaluer un modèle hub-and-spoke :** Les systèmes distribués partagent souvent des dépendances communes. Ces dépendances peuvent souvent être traitées par le biais de l’implémentation d’un modèle hub-and-spoke. Bien qu’un modèle de ce type soit hors de portée pour le processus de migration, il doit être marqué pour tenir compte des itérations futures des [processus prêts](../../ready/index.md).
- **Définition de la priorité du backlog de migration :** Lorsque des modifications réseau sont nécessaires pour prendre en charge le déploiement de production d’une charge de travail qui prend en charge plusieurs régions, il est important que l’équipe de stratégie cloud effectue le suivi et la gestion des escalades relatives à ces modifications du réseau. Le niveau le plus élevé du support exécutif contribuera à l’accélération de la modification. Toutefois, l’impact le plus important est qu’il donne à l’équipe de stratégie la possibilité de modifier les priorités du backlog pour s’assurer que les charges de travail globales ne sont pas bloquées par les modifications du réseau. Ces charges de travail doivent être classées par ordre de priorité uniquement lorsque les modifications du réseau sont terminées.

Ces conditions préalables vous aideront à établir des processus qui peuvent résoudre cette complexité lors de l’exécution de la stratégie de migration.

## <a name="assess-process-changes"></a>Évaluer les changements de processus

Lors du traitement des complexités globales des utilisateurs et des ressources, il existe quelques activités clés qui doivent être ajoutées à l’évaluation des candidats à la migration. Chacune de ces modifications apporte de la clarté sur l’impact sur les utilisateurs et les ressources à l’échelle globale, par le biais d’une approche basée sur les données.

### <a name="suggested-action-during-the-assess-process"></a>Action suggérée pendant le processus d’évaluation

**Évaluer les dépendances entre les centres de données :** Les [outils de visualisation des dépendances d’Azure Migrate](/azure/migrate/concepts-dependency-visualization) peuvent vous aider à identifier les dépendances. L’utilisation de cet ensemble d’outils avant la migration est une bonne pratique générale. Toutefois, lors de la gestion de la complexité globale, cette étape devient indispensable pour le processus d’évaluation. Grâce au [regroupement des dépendances](/azure/migrate/how-to-create-group-machine-dependencies), la visualisation peut vous aider à identifier les adresses IP et les ports des ressources requises pour prendre en charge la charge de travail.

> [!IMPORTANT]
> Deux remarques importantes : Tout d’abord, un expert en matière de placement des ressources et des schémas d’adresses IP est nécessaire pour identifier les ressources qui résident dans un centre de données secondaire. Deuxièmement, il est important d’évaluer les dépendances et les clients en aval dans le visuel pour comprendre les dépendances bidirectionnelles.

**Identifier l’impact global sur les utilisateurs :** Les sorties de l’analyse du profil utilisateur prérequise doivent identifier toute charge de travail affectée par les profils utilisateur globaux. Lorsqu’un candidat à la migration se trouve dans la liste des charges de travail concernées, l’architecte qui prépare la migration doit consulter des experts en matière de mise en réseau et d’opérations pour valider les attentes en matière de routage et de performances du réseau. Au minimum, l’architecture doit inclure une connexion ExpressRoute entre le centre d’opérations réseau (NOC) le plus proche et Azure. [L’architecture de référence pour les connexions ExpressRoute](/azure/architecture/reference-architectures/hybrid-networking/expressroute) peut faciliter la configuration de la connexion nécessaire.

**Conception pour la conformité :** Les sorties de l’analyse du profil utilisateur prérequise doivent identifier toute charge de travail affectée par les exigences en matière de souveraineté des données. Pendant les activités d’architecture du processus d’évaluation, l’architecte affecté doit consulter des experts en matière de conformité pour comprendre les exigences en matière de migration/déploiement dans plusieurs régions. Ces exigences ont un impact important sur les stratégies de conception. Les architectures de référence pour les [applications web multirégion](/azure/architecture/reference-architectures/app-service-web-app/multi-region) et les [applications multirégion multiniveau](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server) peuvent aider à la conception.

> [!WARNING]
> Lorsque vous utilisez une des architectures de référence ci-dessus, il peut être nécessaire d’exclure des éléments de données spécifiques des processus de réplication pour respecter les exigences de souveraineté des données. Une étape supplémentaire est alors ajoutée au processus de promotion.

## <a name="migrate-process-changes"></a>Migrer les changements de processus

Lors de la migration d’une application qui doit être déployée dans plusieurs régions, l’équipe d’adoption cloud doit tenir compte de certaines considérations. Ces considérations comprennent la conception du coffre Azure Site Recovery, la conception du serveur de configuration/traitement, les conceptions de bande passante réseau et la synchronisation des données.

### <a name="suggested-action-during-the-migrate-process"></a>Action suggérée pendant le processus de migration

**Conception du coffre Azure Site Recovery :** Azure Site Recovery est l’outil suggéré pour la réplication native dans le cloud et la synchronisation des ressources numériques sur Azure. Site Recovery réplique les données relatives à la ressource dans un coffre Site Recovery, qui est lié à un abonnement spécifique dans une région spécifique et un centre de données Azure. Lors de la réplication de ressources dans une autre région, un deuxième coffre Site Recovery peut être nécessaire.

**Conception de serveur de configuration/traitement :** Site Recovery fonctionne avec une instance locale d’un serveur de configuration et de traitement, qui est liée à un seul coffre Site Recovery. Cela signifie qu’une deuxième instance de ces serveurs devra peut-être être installée dans le centre de données source pour faciliter la réplication.

**Conception de la bande passante réseau :** Pendant la réplication et la synchronisation continue, les données binaires sont déplacées sur le réseau du centre de données source vers le coffre Site Recovery dans le centre de données Azure cible. Ce processus consomme de la bande passante. La duplication de la charge de travail dans une deuxième région double la quantité de bande passante consommée. Lorsque la bande passante est limitée ou qu’une charge de travail implique une grande quantité de configuration ou de dérive de données, cela peut affecter le temps nécessaire pour effectuer la migration. Plus important encore, cela peut nuire à l’expérience des utilisateurs ou des applications qui dépendent toujours de la bande passante du centre de données source.

**Synchronisation des données :** Souvent, le plus gros drainage de la bande passante provient de la synchronisation de la plateforme de données. Comme défini dans les architectures de référence pour les [applications web multirégion](/azure/architecture/reference-architectures/app-service-web-app/multi-region) et les [applications multirégion multiniveau](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), la synchronisation des données est souvent nécessaire pour aligner les applications. S’il s’agit de l’état opérationnel souhaité de l’application, il peut être judicieux d’effectuer une synchronisation entre la plateforme de données source et chacune des plateformes cloud avant de migrer les ressources d’application et de niveau intermédiaire.
**Synchronisation des données :** Souvent, le plus gros drainage de la bande passante provient de la synchronisation de la plateforme de données. Comme défini dans les architectures de référence pour les [applications web multirégion](/azure/architecture/reference-architectures/app-service-web-app/multi-region) et les [applications multirégion multiniveau](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), la synchronisation des données est souvent nécessaire pour aligner les applications. S’il s’agit de l’état opérationnel souhaité de l’application, il peut être judicieux d’effectuer une synchronisation entre la plateforme de données source et chacune des plateformes cloud avant de migrer les ressources d’application et de niveau intermédiaire.

**Récupération d’urgence depuis Azure vers Azure :** Il existe une autre option qui peut réduire la complexité davantage. Si les approches par chronologie et synchronisation de données s’apparentent à un déploiement en deux étapes, la [récupération d’urgence depuis Azure vers Azure](/azure/site-recovery/azure-to-azure-architecture) peut être une solution acceptable. Dans ce scénario, la charge de travail est migrée vers le premier centre de données Azure à l’aide d’un seul coffre Site Recovery d’une conception de serveur de configuration ou de traitement. Une fois la charge de travail testée, elle peut être récupérée dans un deuxième centre de données Azure à partir des ressources migrées. Cette approche réduit l’impact sur les ressources du centre de code source et tire parti des vitesses de transfert plus rapides et des limites de bande passante élevées disponibles entre les centres de donnes Azure.

> [!NOTE]
> Cette approche peut augmenter le coût à long terme de la migration, car cela peut entraîner des frais de bande passante supplémentaires.

## <a name="optimize-and-promote-process-changes"></a>Changements aux processus d’optimisation et de promotion

Répondre à la complexité globale pendant l’optimisation et la promotion peut nécessiter des efforts dupliqués dans chacune des régions supplémentaires. Lorsqu’un déploiement unique est acceptable, il peut tout de même être nécessaire de dupliquer les tests d’entreprise et les plans de changement de l’entreprise.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Action suggérée pendant le processus d’optimisation et de promotion

**Optimisation pré-test :** Les tests d’automatisation initiaux peuvent identifier les opportunités d’optimisation potentielles, comme avec tout effort de migration. Dans le cas de charges de travail globales, il est important de tester la charge de travail dans chaque région de façon indépendante, car des modifications mineures de la configuration du réseau ou du centre de données Azure cible peuvent affecter les performances.

**Plan de changements dans l’entreprise :** Pour tout scénario de migration complexe, il est recommandé de créer un plan de changements dans l’entreprise pour garantir une communication claire au sujet des modifications apportées aux processus d’entreprise, aux expériences utilisateur et au timing des efforts requis pour intégrer les changements. Dans le cas d’efforts de migration globaux, le plan doit inclure des considérations pour les utilisateurs finaux dans chaque zone géographique affectée.

**Tests en entreprise :** Conjointement au plan de changements dans l’entreprise, des tests d’entreprise peuvent être nécessaires dans chaque région pour garantir les performances et le respect des modèles de routage réseau modifiés.

**Volées de promotion :** La promotion se produit souvent sous la forme d’une activité unique, ce qui permet de réacheminer le trafic de production vers les charges de travail migrées. En cas de publication internationale, il est recommandé de fournir la promotion par volées (ou regroupements prédéfinis d’utilisateurs). Cela permet à l’équipe de stratégie cloud et à l’équipe d’adoption cloud de mieux observer les performances et d’améliorer la prise en charge des utilisateurs dans chaque région. Les volées de promotion sont souvent contrôlées au niveau de la mise en réseau en modifiant le routage de plages d’adresses IP spécifiques des ressources de la charge de travail source vers les ressources qui viennent d’être migrées. Après la migration d’un regroupement spécifié d’utilisateurs finaux, le groupe suivant peut être redirigé.

**Optimisation des volées :** L’un des avantages des volées de promotion est qu’elles permettent d’obtenir des observations plus approfondies et d’optimiser l’optimisation des ressources déployées. Après une courte période d’utilisation en production par la première volée, il est suggéré d’affiner davantage les ressources migrées, lorsque cela est autorisé par les procédures d’exploitation informatique.

## <a name="next-steps"></a>Étapes suivantes

Un point de complexité distinct, souvent lié à plusieurs régions, est le besoin de préparer la migration de plusieurs [centres de données](./multiple-datacenters.md). Bien que de nature similaire, cette complexité concerne le volume de ressources à migrer lors du déplacement de plusieurs centres de données dans le cloud.

> [!div class="nextstepaction"]
> [Migration de plusieurs centres de données](./multiple-datacenters.md)
