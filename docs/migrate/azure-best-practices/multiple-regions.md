---
title: Guide de décision concernant les régions
description: Découvrez les régions dans lesquelles la plateforme cloud est disponible ainsi que les facteurs et caractéristiques susceptibles d’affecter vos sélections de régions Azure.
author: doodlemania2
ms.author: dermar
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 0445ba3048a7b16b792cd144c29d1643aefe0d09
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83815308"
---
# <a name="azure-regions"></a>Régions Azure

Azure est disponible dans de nombreuses régions du monde. Comme chaque [région Azure](https://azure.microsoft.com/global-infrastructure/regions) a un ensemble de caractéristiques spécifiques, le choix de la région à utiliser est extrêmement important.

1. **Services disponibles :** Les services déployés dans chaque région varient selon différents facteurs. La région que vous choisissez pour déployer votre charge de travail doit offrir le service souhaité. Pour plus d’informations sur les services disponibles dans chaque région, consultez [Disponibilité des produits par région](https://azure.microsoft.com/global-infrastructure/services).
1. **Capacité :** Chaque région présente une capacité maximale. Même si cette capacité est généralement peu perceptible pour l’utilisateur final, elle peut impacter les types d’abonnements disponibles, les types de services déployables par ces abonnements et les circonstances dans lesquelles ces déploiements sont possibles. Il s’agit d’un concept différent de celui des quotas d’abonnement. Si vous planifiez une migration massive de centres de données vers Azure, il peut être utile de consulter votre équipe de terrain ou administrateur de comptes Azure local pour vérifier que vous pouvez effectuer votre déploiement à l’échelle requise.
1. **Contraintes :** Certaines contraintes affectent le déploiement de services dans certaines régions. Par exemple, certaines régions sont disponibles uniquement en tant que destinations de sauvegarde ou de basculement. Les [exigences de souveraineté des données](https://azure.microsoft.com/global-infrastructure/geographies) représentent d’autres contraintes qu’il est important de noter.
1. **Souveraineté :** Certaines régions sont dédiées à des entités souveraines spécifiques. Même si toutes les régions sont des régions Azure, ces régions souveraines sont totalement isolées du reste d’Azure, elles ne sont pas nécessairement gérées par Microsoft et peuvent être limitées à certains types de clients. Ces régions souveraines sont les suivantes :
    1. [Azure Chine](https://azure.microsoft.com/global-infrastructure/china)
    1. [Azure Allemagne](https://azure.microsoft.com/global-infrastructure/germany) : dépréciée en faveur des régions Azure non souveraines standard en Allemagne
    1. [Azure US Government](https://azure.microsoft.com/global-infrastructure/government)
    1. Remarque : En [Australie](https://azure.microsoft.com/global-infrastructure/australia), deux régions sont gérées par Microsoft, mais sont fournies pour le gouvernement australien, ses clients et sous-traitants. Ainsi, elles impliquent des contraintes vis-à-vis des clients, de la même façon que les autres clouds souverains.

## <a name="operate-in-multiple-geographic-regions"></a>Opérer dans plusieurs régions géographiques

Les entreprises ayant des activités dans plusieurs régions géographiques bénéficient de la résilience dont elles ont besoin, mais font face à une complexité supplémentaire. Cette complexité se manifeste sous quatre formes principales :

- Distribution de ressources
- Profils d’accès utilisateur
- Exigences en matière de conformité
- Résilience régionale

En examinant ces formes de complexité de façon plus approfondie, vous comprendrez en quoi le choix de la région revêt une telle importance à l’égard de votre stratégie d’adoption du cloud dans sa globalité. Commençons par les considérations relatives au réseau.

## <a name="networking-considerations"></a>Mise en réseau - Éléments à prendre en compte

Tout déploiement cloud robuste nécessite un réseau bien étudié, tenant compte des régions Azure. Une fois que vous avez examiné les caractéristiques ci-dessus pour déterminer les régions de déploiement, le réseau doit être déployé. Si cet article n’a pas pour objet de fournir des informations réseau exhaustives, certaines considérations doivent faire l’objet d’une attention particulière :

- Les régions Azure sont déployées par paires. En cas de défaillance catastrophique affectant une région, une autre région faisant partie du même périmètre géopolitique est désignée comme région appairée. Envisagez le déploiement dans des régions appairées comme stratégie de résilience primaire et secondaire. Brésil Sud est une exception notable dont la région appairée est USA Centre Sud. Pour plus d’informations, consultez [Régions jumelées Azure](https://docs.microsoft.com/azure/best-practices-availability-paired-regions).

  - Stockage Azure prend en charge le [stockage géoredondant](https://docs.microsoft.com/azure/storage/common/storage-redundancy-grs) (GRS, Geographically Redundant Storage) : trois copies de vos données sont stockées dans votre région primaire et trois copies supplémentaires sont stockées dans la région appairée. Vous ne pouvez pas modifier le jumelage du stockage dans le cadre d’un stockage géoredondant.
  - Les services qui s’appuient sur le stockage géoredondant Azure peuvent tirer parti de cette fonctionnalité de région jumelée. La prise en charge de cette fonctionnalité doit alors être prévue aussi bien au niveau de vos applications qu’au niveau du réseau.
  - Si vous n’envisagez pas d’utiliser le stockage géoredondant pour satisfaire vos besoins en résilience régionale, n'utilisez pas la région jumelée comme région secondaire. En cas de défaillance régionale, les ressources seront soumises à une pression intense dans la région jumelée lors de leur migration. En utilisant un autre site pour la reprise d’activité, vous évitez cette pression et gagnez ainsi en rapidité lors de la reprise.
  > [!WARNING]
  > N’essayez pas d’utiliser le stockage géoredondant Azure pour la récupération ou les sauvegardes de machine virtuelle. Utilisez plutôt la [sauvegarde Azure](https://azure.microsoft.com/services/backup) et [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery) avec des [disques managés Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) pour assurer la résilience de vos charges de travail IaaS.

- Les services Sauvegarde Azure et Azure Site Recovery fonctionnent en tandem avec votre conception réseau pour mettre en œuvre la résilience régionale répondant à vos besoins en sauvegarde de données et d’IaaS. Assurez-vous que le réseau est optimisé pour que les transferts de données restent sur le segment principal de Microsoft et, dans la mesure du possible, utilisez [VNet Peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview). Certaines organisations de plus grande taille, effectuant des déploiements à l’échelle mondiale, peuvent privilégier [ExpressRoute Premium](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) pour router le trafic entre les régions, ce qui leur permet de réduire les frais liés aux sorties régionales.

- Les groupes de ressources Azure sont des constructions spécifiques aux régions. Toutefois, il est normal que les ressources d’un groupe de ressources s’étendent sur plusieurs régions. Dans ce contexte, il est important de savoir qu’en cas de défaillance régionale, les opérations du plan de contrôle sur un groupe de ressources échoueront dans la région affectée, même si les ressources situées dans d’autres régions (au sein de ce groupe de ressources) continuent de fonctionner. Ceci peut affecter à la fois la conception de votre réseau et celle de votre groupe de ressources.

- De nombreux services PaaS dans Azure prennent en charge les [points de terminaison de service](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) ou la [liaison privée](https://docs.microsoft.com/azure/private-link/private-link-overview). Ces deux solutions conditionnent fortement les considérations relatives au réseau quand vous étudiez la résilience régionale, la migration et la gouvernance.

- De nombreux services PaaS s’appuient sur leurs propres solutions de résilience régionale. Par exemple, Azure SQL Database et Azure Cosmos DB vous permettent d’effectuer facilement des réplications dans _x_ régions supplémentaires. Certains services, comme Azure DNS, n’ont aucune dépendance vis-à-vis de la région. Quand vous réfléchissez aux services que vous allez utiliser dans votre processus d’adoption, veillez à bien comprendre les fonctionnalités de basculement et les étapes de récupération potentiellement nécessaires pour chaque service Azure.

- En plus d’effectuer leurs déploiements dans plusieurs régions pour assurer la reprise d’activité, de nombreuses organisations choisissent un modèle de déploiement actif-actif de sorte qu’aucun basculement ne soit nécessaire. Cette approche présente des avantages supplémentaires, à savoir un équilibrage de charge global et un renforcement de la tolérance de panne et des performances réseau. Pour tirer parti de ce modèle, vos applications doivent prendre en charge l’exécution en mode actif-actif dans plusieurs régions.

> [!WARNING]
> Les régions Azure sont des constructions hautement disponibles, assorties de SLA appliqués aux services qui s’y exécutent. Toutefois, vous devez toujours éviter que vos applications stratégiques soient dépendantes d’une seule région. Soyez toujours prêt à une défaillance régionale et pratiquez les étapes de reprise d’activité et d’atténuation.

Après avoir étudié la topologie de réseau qui vous permettra de rester opérationnel, vous devrez documenter d’autres aspects et aligner les processus. L’approche suivante peut vous aider à évaluer les défis potentiels et à établir un cours d’action général :

- Envisagez une implémentation plus robuste de la préparation et de la gouvernance.
- Inventoriez les zones géographiques affectées. Dressez la liste des régions et des pays affectés.
- Documentez les exigences de souveraineté des données. Les pays identifiés ont-ils des exigences de conformité qui régissent la souveraineté des données ?
- Documentez la base utilisateur. Les employés, partenaires ou clients dans le pays identifié seront-ils affectés par la migration vers le cloud ?
- Documentez les ressources et centres de données. Existe-t-il des ressources dans le pays identifié qui peuvent être incluses dans l’effort de migration ?
- Documentez la disponibilité des références SKU et les exigences de basculement au niveau régional.

Alignez les modifications à travers le processus de migration pour traiter l’inventaire initial.

## <a name="document-complexity"></a>Documenter la complexité

Le tableau suivant peut vous aider à documenter les résultats des étapes précédentes :

| Région        | Country     | Employés locaux | Utilisateurs externes locaux   | Ressources ou centres de données locaux | Exigences de souveraineté des données |
|---------------|-------------|-----------------|------------------------|-----------------------------|-------------------------------|
| Amérique du Nord | États-Unis         | Oui             | Partenaires et clients | Oui                         | Non                            |
| Amérique du Nord | Canada      | Non              | Clients              | Oui                         | Oui                           |
| Europe        | Allemagne     | Oui             | Partenaires et clients | Non - Réseau uniquement           | Oui                           |
| Asie-Pacifique  | Corée du Sud | Oui             | Partenaires               | Oui                         | Non                            |

<!-- markdownlint-disable MD026 -->

## <a name="relevance-of-data-sovereignty"></a>Pertinence de la souveraineté des données

Dans le monde entier, les organisations gouvernementales ont commencé à établir des exigences en matière de souveraineté des données, comme le Règlement général sur la protection des données (RGPD). Les exigences de conformité de cette nature requièrent souvent une localisation au sein d’une région spécifique ou même au sein d’un pays spécifique pour protéger ses citoyens. Dans certains cas, les données relatives aux clients, aux employés ou aux partenaires doivent être stockées sur une plateforme cloud au sein de la même région que l’utilisateur final.

La réponse à ce défi a été une motivation importante pour les entreprises qui opèrent à l’échelle mondiale. Pour respecter les exigences de conformité, certaines entreprises ont choisi de déployer des ressources informatiques dupliquées sur des fournisseurs de Cloud au sein de la région. Dans le tableau ci-dessus, l’Allemagne est un bon exemple de ce scénario. Cet exemple comprend des clients, des partenaires et des employés en Allemagne, mais pas de ressources informatiques existantes. Cette société peut choisir de déployer des ressources dans un centre de données dans la zone couverte par le RGPD, en utilisant potentiellement des centres de données d’Azure en Allemagne. La compréhension des données affectées par le RGPD aidera l’équipe chargée de l’adoption du cloud à comprendre la meilleure approche de migration dans ce cas.

### <a name="why-is-the-location-of-end-users-relevant"></a>Pourquoi l’emplacement des utilisateurs finaux est-il pertinent ?

Les entreprises qui prennent en charge des utilisateurs finaux dans plusieurs pays ont développé des solutions techniques pour traiter le trafic des utilisateurs finaux. Dans certains cas, cela implique la localisation des ressources. Dans d’autres scénarios, l’entreprise peut choisir de mettre en œuvre des solutions de réseau étendu globales pour gérer des bases d’utilisateurs disparates via des solutions axées sur le réseau. Dans les deux cas, la stratégie de migration peut être affectée par les profils d’utilisation de ces utilisateurs finaux disparates.

Comme la société prend en charge les employés, les partenaires et les clients en Allemagne, mais qu’il n’y a actuellement pas de centre de données dans ce pays, il est probable que cette société mette en place une forme de solution de ligne de crédit pour router le trafic vers les centres de données d’autres pays. Ce routage existant présente un risque significatif pour les performances perçues des applications migrées. L’injection de sauts supplémentaires dans un WAN global établi et réglé peut créer la perception d’applications sous-performantes après la migration. La recherche et la résolution de ces problèmes peuvent entraîner des retards importants pour un projet. Dans chacun des processus ci-dessous, des conseils sur la façon de résoudre cette complexité sont inclus dans les processus d’établissement des conditions préalables, d’évaluation, de migration et d’optimisation. Il est essentiel de comprendre les profils utilisateur dans chaque pays pour gérer correctement cette complexité.

### <a name="why-is-the-location-of-datacenters-relevant"></a>Pourquoi l’emplacement des centres de données est-il pertinent ?

L’emplacement des centres de données existants peut affecter une stratégie de migration. Voici quelques-uns des impacts les plus courants :

**Décisions relatives à l’architecture :** Le ciblage de la région est l’une des premières étapes de la conception de la stratégie de migration. Cela est souvent influencé par l’emplacement des ressources existantes. En outre, les services cloud disponibles et le coût unitaire de ces services peuvent varier d’une région à l’autre. Ainsi, la compréhension de l’emplacement actuel et futur des ressources affecte les décisions d’architecture et peut également affecter les estimations de budget.

**Dépendances du centre de données :** En fonction des données du tableau ci-dessus, il est probable que des dépendances existent entre les différents centres de données dans le monde. Dans de nombreuses organisations qui opèrent sur ce type de mise à l’échelle, ces dépendances peuvent ne pas être documentées ou bien comprises. Les approches utilisées pour évaluer les profils utilisateur vous aideront à identifier certaines de ces dépendances. Toutefois, des étapes supplémentaires sont suggérées au cours du processus d’évaluation pour atténuer les risques associés à cette complexité.

## <a name="implementing-the-general-approach"></a>Implémentation de l’approche générale

Cette approche est pilotée par des informations quantifiables. Par conséquent, l’approche suivante suit un modèle piloté par les données pour répondre aux complexités de la migration globale.

Lorsque l’étendue d’une migration comprend plusieurs régions, les considérations suivantes relatives à la disponibilité doivent être évaluées par l’équipe d’adoption cloud :

- La souveraineté des données peut nécessiter la localisation de certaines ressources, mais il existe de nombreuses ressources qui peuvent ne pas être régies par ces contraintes de conformité. Des opérations telles que la journalisation, la création de rapports, le routage réseau, l’identité et d’autres services informatiques centraux peuvent être admissibles pour être hébergés en tant que services partagés sur plusieurs abonnements, voire dans plusieurs régions. L’équipe d’adoption cloud doit envisager d’utiliser un modèle de service partagé, comme indiqué dans l’[architecture de référence pour une topologie hub-and-spoke avec des services partagés](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services)
- Lors du déploiement de plusieurs instances d’environnements similaires, une fabrique d’environnement peut assurer la cohérence, améliorer la gouvernance et accélérer le déploiement. Le [guide de gouvernance pour les entreprises complexes](../../govern/guides/complex/index.md) établit une approche qui crée un environnement qui évolue dans plusieurs régions.

Une fois que l’équipe est à l’aise avec l’approche de référence et que la préparation est alignée, certains prérequis sont à prendre en compte :

- **Découverte générale :** Complétez le tableau de [documentation de la complexité](#document-complexity) ci-dessus.
- **Effectuez une analyse de profil utilisateur sur chaque pays affecté :** Il est important de comprendre le routage de l’utilisateur final général tôt lors du processus de migration. La modification des lignes d’emprunt globales et l’ajout de connexions comme ExpressRoute à un centre de données cloud peut nécessiter des mois de retards réseau. Résolvez cela aussi tôt que possible dans le processus.
- **Rationalisation initiale du patrimoine numérique :** Chaque fois que de la complexité est introduite dans une stratégie de migration, une rationalisation initiale doit être effectuée. Pour obtenir de l'aide, consultez l’aide sur la [rationalisation du patrimoine numérique](../../digital-estate/index.md).
  - **Exigences supplémentaires relatives au patrimoine :** Établissez des stratégies de marquage pour identifier les charges de travail affectées par les exigences de souveraineté des données. Les étiquettes requises doivent commencer par la rationalisation du patrimoine numérique et traverser les ressources migrées.
- **Évaluer un modèle hub-and-spoke :** Les systèmes distribués partagent souvent des dépendances communes. Ces dépendances peuvent souvent être traitées par le biais de l’implémentation d’un modèle hub-and-spoke. Bien qu’un modèle de ce type soit hors de portée pour le processus de migration, il doit être marqué pour tenir compte des itérations futures des [processus prêts](../../ready/index.md).
- **Définition de la priorité du backlog de migration :** Lorsque des modifications réseau sont nécessaires pour prendre en charge le déploiement de production d’une charge de travail qui prend en charge plusieurs régions, il est important que l’équipe de stratégie cloud effectue le suivi et la gestion des escalades relatives à ces modifications du réseau. Le niveau le plus élevé du support exécutif contribuera à l’accélération de la modification. Toutefois, l’impact le plus important est qu’il donne à l’équipe de stratégie la possibilité de modifier les priorités du backlog pour s’assurer que les charges de travail globales ne sont pas bloquées par les modifications du réseau. Ces charges de travail doivent être classées par ordre de priorité uniquement lorsque les modifications du réseau sont terminées.

Ces conditions préalables vous aideront à établir des processus qui peuvent résoudre cette complexité lors de l’exécution de la stratégie de migration.

## <a name="assess-process-changes"></a>Évaluer les changements de processus

Dans le cadre des complexités globales des utilisateurs et des ressources, quelques activités clés doivent être ajoutées à l’évaluation des candidats à la migration. Chacune de ces modifications apporte de la clarté sur l’impact sur les utilisateurs et les ressources à l’échelle globale, par le biais d’une approche basée sur les données.

### <a name="suggested-action-during-the-assess-process"></a>Action suggérée pendant le processus d’évaluation

**Évaluer les dépendances entre les centres de données :** Les [outils de visualisation des dépendances d’Azure Migrate](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization) peuvent vous aider à identifier les dépendances. L’utilisation de ces outils avant la migration est une bonne pratique. Dans le cadre de la complexité globale, cette étape devient indispensable pour le processus d’évaluation. Grâce au [regroupement des dépendances](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies), la visualisation peut vous aider à identifier les adresses IP et les ports des ressources requises pour prendre en charge la charge de travail.

> [!IMPORTANT]
> Deux remarques importantes : Tout d’abord, un expert en matière de placement des ressources et des schémas d’adresses IP est nécessaire pour identifier les ressources qui résident dans un centre de données secondaire. Deuxièmement, il est important d’évaluer les dépendances et les clients en aval dans le visuel pour comprendre les dépendances bidirectionnelles.

**Identifier l’impact global sur les utilisateurs :** Les sorties de l’analyse du profil utilisateur prérequise doivent identifier toute charge de travail affectée par les profils utilisateur globaux. Lorsqu’un candidat à la migration se trouve dans la liste des charges de travail concernées, l’architecte qui prépare la migration doit consulter des experts en matière de mise en réseau et d’opérations pour valider les attentes en matière de routage et de performances du réseau. Au minimum, l’architecture doit comprendre une connexion ExpressRoute entre le centre d’opérations réseau (NOC) le plus proche et Azure. [L’architecture de référence pour les connexions ExpressRoute](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/expressroute) peut faciliter la configuration de la connexion nécessaire.

**Conception pour la conformité :** Les sorties de l’analyse du profil utilisateur prérequise doivent identifier toute charge de travail affectée par les exigences en matière de souveraineté des données. Pendant les activités d’architecture du processus d’évaluation, l’architecte affecté doit consulter des experts en matière de conformité pour comprendre les exigences en matière de migration/déploiement dans plusieurs régions. Ces exigences ont un impact important sur les stratégies de conception. Les architectures de référence pour les [applications web multirégion](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/multi-region) et les [applications multirégion multiniveau](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/multi-region-sql-server) peuvent aider à la conception.

> [!WARNING]
> Lorsque vous utilisez une des architectures de référence ci-dessus, il peut être nécessaire d’exclure des éléments de données spécifiques des processus de réplication pour respecter les exigences de souveraineté des données. Une étape supplémentaire est alors ajoutée au processus de promotion.

## <a name="migrate-process-changes"></a>Migrer les changements de processus

Pour migrer une application qui doit être déployée dans plusieurs régions, l’équipe d’adoption cloud doit tenir compte de certaines considérations. Ces considérations comprennent la conception du coffre Azure Site Recovery, la conception du serveur de configuration/traitement, les conceptions de bande passante réseau et la synchronisation des données.

### <a name="suggested-action-during-the-migrate-process"></a>Action suggérée pendant le processus de migration

**Conception du coffre Azure Site Recovery :** Azure Site Recovery est l’outil suggéré pour la réplication native dans le cloud et la synchronisation des ressources numériques sur Azure. Site Recovery réplique les données relatives à la ressource dans un coffre Site Recovery, qui est lié à un abonnement spécifique dans une région spécifique et un centre de données Azure. Lors de la réplication de ressources dans une autre région, un deuxième coffre Site Recovery peut être nécessaire.

**Conception de serveur de configuration/traitement :** Site Recovery fonctionne avec une instance locale d’un serveur de configuration et de traitement, qui est liée à un seul coffre Site Recovery. Cela signifie qu’une deuxième instance de ces serveurs devra peut-être être installée dans le centre de données source pour faciliter la réplication.

**Conception de la bande passante réseau :** Pendant la réplication et la synchronisation continue, les données binaires sont déplacées sur le réseau du centre de données source vers le coffre Site Recovery dans le centre de données Azure cible. Ce processus consomme de la bande passante. La duplication de la charge de travail dans une deuxième région double la quantité de bande passante consommée. Lorsque la bande passante est limitée ou qu’une charge de travail implique une grande quantité de configuration ou de dérive de données, cela peut affecter le temps nécessaire pour effectuer la migration. Plus important encore, cela peut nuire à l’expérience des utilisateurs ou des applications qui dépendent toujours de la bande passante du centre de données source.

**Synchronisation des données :** Souvent, le plus gros drainage de la bande passante provient de la synchronisation de la plateforme de données. Comme défini dans les architectures de référence pour les [applications web multirégion](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/multi-region) et les [applications multirégion multiniveau](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), la synchronisation des données est souvent nécessaire pour aligner les applications. S’il s’agit de l’état opérationnel souhaité de l’application, il peut être judicieux d’effectuer une synchronisation entre la plateforme de données source et chacune des plateformes cloud avant de migrer les ressources d’application et de niveau intermédiaire.
**Synchronisation des données :** Souvent, le plus gros drainage de la bande passante provient de la synchronisation de la plateforme de données. Comme défini dans les architectures de référence pour les [applications web multirégion](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/multi-region) et les [applications multirégion multiniveau](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), la synchronisation des données est souvent nécessaire pour aligner les applications. S’il s’agit de l’état opérationnel souhaité de l’application, il peut être judicieux d’effectuer une synchronisation entre la plateforme de données source et chacune des plateformes cloud avant de migrer les ressources d’application et de niveau intermédiaire.

**Récupération d’urgence depuis Azure vers Azure :** Une autre option peut encore réduire la complexité. Si les approches par chronologie et synchronisation de données s’apparentent à un déploiement en deux étapes, la [récupération d’urgence depuis Azure vers Azure](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-architecture) peut être une solution acceptable. Dans ce scénario, la charge de travail est migrée vers le premier centre de données Azure à l’aide d’un seul coffre Site Recovery d’une conception de serveur de configuration ou de traitement. Une fois la charge de travail testée, elle peut être récupérée dans un deuxième centre de données Azure à partir des ressources migrées. Cette approche réduit l’impact sur les ressources du centre de code source et tire parti des vitesses de transfert plus rapides et des limites de bande passante élevées disponibles entre les centres de donnes Azure.

> [!NOTE]
> Cette approche peut augmenter le coût à long terme de la migration, car cela peut entraîner des frais de bande passante supplémentaires.

## <a name="optimize-and-promote-process-changes"></a>Changements aux processus d’optimisation et de promotion

Répondre à la complexité globale pendant l’optimisation et la promotion peut nécessiter des efforts dupliqués dans chacune des régions supplémentaires. Lorsqu’un déploiement unique est acceptable, il peut tout de même être nécessaire de dupliquer les tests d’entreprise et les plans de changement de l’entreprise.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Action suggérée pendant le processus d’optimisation et de promotion

**Optimisation pré-test :** Les tests d’automatisation initiaux peuvent identifier les opportunités d’optimisation potentielles, comme avec tout effort de migration. Dans le cas de charges de travail globales, il est important de tester la charge de travail dans chaque région de façon indépendante, car des modifications mineures de la configuration du réseau ou du centre de données Azure cible peuvent affecter les performances.

**Plan de changements dans l’entreprise :** Pour les scénarios de migration complexes, vous devez créer un plan de changements dans l’entreprise pour communiquer clairement sur les changements effectués dans les processus métier, les expériences utilisateur et sur la chronologie des efforts nécessaires pour intégrer les changements. Dans le cas d’efforts de migration globaux, le plan doit inclure des considérations pour les utilisateurs finaux dans chaque zone géographique affectée.

**Tests en entreprise :** Conjointement au plan de changements dans l’entreprise, des tests d’entreprise peuvent être nécessaires dans chaque région pour garantir les performances et le respect des modèles de routage réseau modifiés.

**Volées de promotion :** La promotion se produit souvent sous la forme d’une activité unique, ce qui permet de réacheminer le trafic de production vers les charges de travail migrées. En cas de publication internationale, la promotion doit être effectuée par volées (ou regroupements prédéfinis d’utilisateurs). Cela permet à l’équipe de stratégie cloud et à l’équipe d’adoption cloud de mieux observer les performances et d’améliorer la prise en charge des utilisateurs dans chaque région. Les volées de promotion sont souvent contrôlées au niveau de la mise en réseau en modifiant le routage de plages d’adresses IP spécifiques des ressources de la charge de travail source vers les ressources qui viennent d’être migrées. Après la migration d’un regroupement spécifié d’utilisateurs finaux, le groupe suivant peut être redirigé.

**Optimisation des volées :** L’un des avantages des volées de promotion est qu’elles permettent d’obtenir des observations plus approfondies et d’optimiser l’optimisation des ressources déployées. Après une courte période d’utilisation en production par la première volée, il est suggéré d’affiner davantage les ressources migrées, lorsque cela est autorisé par les procédures d’exploitation informatique.
