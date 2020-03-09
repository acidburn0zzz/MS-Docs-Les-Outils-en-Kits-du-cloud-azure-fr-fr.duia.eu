---
title: Mettre à l’échelle une migration vers Azure
description: Découvrez comment Contoso mène à bien une migration à l’échelle vers Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/08/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: c4d5e151d5ea4badd3c6c5fab25f4a6be9ee60c5
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78222826"
---
# <a name="scale-a-migration-to-azure"></a>Mettre à l’échelle une migration vers Azure

Cet article montre comment la société fictive Contoso réalise une migration à l’échelle vers Azure. Elle réfléchit à la façon planifier et d’effectuer une migration de plus de 3 000 charges de travail, 8 000 bases de données et plus de 10 000 machines virtuelles.

## <a name="business-drivers"></a>Axes stratégiques

L’équipe informatique a travaillé en étroite collaboration avec des partenaires commerciaux pour comprendre le résultat qu’ils souhaitent obtenir avec cette migration :

- **Répondre à la croissance de l’entreprise.** Contoso étant en pleine croissance, son infrastructure et ses systèmes locaux sont soumis à une charge importante.
- **Gagner en efficacité.** Contoso doit supprimer les procédures inutiles et rationaliser les processus pour les développeurs et les utilisateurs. L’entreprise a besoin d’une informatique rapide et doit éviter de perdre du temps ou d’argent en répondant plus rapidement aux exigences des clients.
- **Gagner en agilité.** le service informatique de Contoso doit être plus réactif face aux besoins de l’entreprise. Elle doit être en mesure de réagir plus rapidement que l’évolution du marché pour réussir dans une économie mondiale. L’informatique ne doit pas devenir une entrave à l’activité.
- **Mise à l’échelle** À mesure que l’entreprise croît, l’informatique de Contoso doit fournir des systèmes capables de croître au même rythme.
- **Améliorer les modèles de coûts.** Contoso souhaite réduire les besoins en fonds propres dans le budget informatique. Contoso souhaite utiliser les capacités du cloud pour mettre à l’échelle et réduire les besoins en matériel coûteux.
- **Réduire les coûts de licences.** Contoso souhaite réduire les coûts liés au cloud.

## <a name="migration-goals"></a>Objectifs de la migration

L’équipe cloud de Contoso a épinglé les objectifs de cette migration. Ces objectifs ont été utilisés pour déterminer la meilleure méthode de migration.

**Configuration requise** | **Détails**
--- | ---
**Migrer rapidement vers le cloud** | Contoso souhaite déplacer les applications et les machines virtuelles dans Azure aussi vite que possible.
**Compiler un inventaire complet** | Contoso souhaite dresser un inventaire complet des applications, des bases de données et des machines virtuelles présentes dans l’organisation.
**Évaluer et classifier les applications** | Contoso souhaite tirer pleinement parti du cloud. Par défaut, Contoso considère que tous les services s’exécuteront en tant que PaaS. IaaS sera utilisé quand PaaS ne conviendra pas.
**Former et migrer vers DevOps** | Contoso souhaite passer à un modèle DevOps. Contoso prévoit de former les équipes à Azure et DevOps et de les réorganiser selon les besoins.

Après avoir défini les objectifs et les contraintes, Contoso examine l’encombrement informatique et identifie le processus de migration.

## <a name="current-deployment"></a>Déploiement actuel

Après avoir planifié et configuré une [infrastructure Azure](./contoso-migration-infrastructure.md) et effectué différentes preuves de concepts (POC) sur les combinaisons de migration détaillées dans le tableau ci-dessus, la société Contoso est prête à se lancer dans une migration complète vers Azure à l’échelle. Voici ce que Contoso souhaite migrer.

<!--markdownlint-disable MD033 -->

**Item** | **Volume** | **Détails**
--- | --- | ---
**Charges de travail** | Plus de 3 000 applications | Les applications s’exécutent sur des machines virtuelles.<br/><br/>  Les applications sont basées sur Windows, SQL, des systèmes d’exploitation open source et LAMP.
**Bases de données** | Autour de 8 500 | Les bases de données utilisées sont SQL Server, MySQL et PostgreSQL.
**Machines virtuelles** | Plus de 35 000 | Les machines virtuelles s’exécutent sur des hôtes VMware et sont gérées par des serveurs vCenter.

<!--markdownlint-enable MD033 -->

## <a name="migration-process"></a>Processus de migration

Après avoir défini les axes stratégiques et les objectifs de migration, Contoso envisage un processus de migration à quatre volets :

- **Phase 1 : Évaluer.** Identifier les ressources actuelles et déterminer si elles se prêtent à une migration vers Azure.
- **Phase 2 : Migrer.** Déplacer les ressources vers Azure. La façon dont les applications et les objets seront déplacés vers Azure dépendra des applications elles-mêmes et des objectifs de l’entreprise.
- **Phase 3 : Optimiser.** Après avoir déplacé les ressources vers Azure, Contoso doit les améliorer et les rationnaliser pour en optimiser les performances et l’efficacité.
- **Phase 4 : Sécuriser et gérer.** Maintenant que tout est en place, Contoso tire parti de la sécurité Azure, des ressources et des services de gestion pour régir, sécuriser et superviser ses applications cloud dans Azure.

Ces phases ne sont pas conduites partout de façon simultanée à dans l’organisation. Chaque projet de migration de Contoso se trouve à une étape différente du processus d’évaluation et de migration. L’optimisation, la sécurité et la gestion sont des tâches qui se répéteront dans le temps.

## <a name="phase-1-assess"></a>Phase 1 : Évaluer

Contoso lance le processus en détectant et en évaluant les applications, les données et l’infrastructure locales. Voici ce que fera Contoso :

- Contoso doit détecter les applications, mapper les dépendances entre les applications et établir l’ordre et la priorité de migration.
- Au cours de l’évaluation, Contoso prévoit d’établir un inventaire complet des applications et des ressources. Parallèlement au nouvel inventaire, Contoso utilisera et mettra à jour la base de données de gestion de configuration (CMDB) existante, ainsi que le catalogue de services.
  - La base de données CMDB contient les configurations techniques des applications Contoso.
  - Le catalogue de services rassemble les détails opérationnels des applications, notamment les partenaires commerciaux associés et les contrats de niveau de service (SLA).

### <a name="discover-apps"></a>Détecter les applications

Contoso exécute des milliers d’applications sur divers types de serveurs. Outre la base de données CMDB et le catalogue de services, Contoso a besoin d’outils de détection et d’évaluation.

- Les outils doivent fournir un mécanisme capable d’alimenter le processus de migration en données d’évaluation.
- Les outils d’évaluation doivent fournir des données qui permettent d’établir un inventaire intelligent des ressources physiques et virtuelles de Contoso. Les données doivent inclure des informations de profil et des métriques de performances.
- À l’issue de la détection, Contoso doit disposer d’un inventaire complet des ressources et des métadonnées associées. Cet inventaire servira à définir le plan de migration.

### <a name="identify-classifications"></a>Identifier les classifications

Contoso identifie certaines catégories communes pour classifier les ressources dans l’inventaire. Ces classifications sont essentielles aux décisions que va prendre Contoso pour la migration. La liste de classifications aide à établir les priorités de migration et à identifier les problèmes complexes.

**Catégorie** | **Valeur attribuée** | **Détails**
--- | --- | ---
Groupe de l’entreprise | Liste des noms de groupes de l’entreprise | Quel est le groupe en charge de l’élément d’inventaire ?
Candidat à une preuve de concept | O/N | L’application peut-elle être utilisée comme preuve de concept ou précurseur pour la migration vers le cloud ?
Dette technique | Aucune/Légère/Lourde | L’élément d’inventaire est-il en cours d’exécution ou utilise-t-il un produit, une plateforme ou un système d’exploitation dont le support n’est plus assuré ?
Implications pour le pare-feu | O/N | L’application communique-t-elle avec Internet/trafic extérieur ?  S’intègre-t-elle à un pare-feu ?
Problèmes de sécurité | O/N | Existe-t-il des problèmes de sécurité connus au niveau de l’application ?  L’application utilise-t-elle des données non chiffrées ou des plateformes obsolètes ?

### <a name="discover-app-dependencies"></a>Détecter les dépendances des applications

Dans le cadre du processus d’évaluation, Contoso doit déterminer où s’exécutent les applications et identifier les dépendances et les connexions entre les serveurs d’applications. Contoso mappe l’environnement en étapes.

1. Dans un premier temps, Contoso cherche à déterminer comment les serveurs et les machines se mappent aux applications, emplacements réseau et groupes individuels.
2. Ces informations permettent à Contoso d’identifier clairement les applications qui ont peu de dépendances et qui peuvent être migrées rapidement.
3. Contoso peut se servir du mappage pour identifier les dépendances et les communications plus complexes entre les serveurs d’applications. Contoso peut ensuite regrouper logiquement ces serveurs pour représenter les applications, puis élaborer une stratégie de migration en fonction de ces groupes.

Une fois le mappage terminé, Contoso peut vérifier que tous les composants d’application sont identifiés et pris en compte au moment d’établir le plan de migration.

![Mappage des dépendances](./media/contoso-migration-scale/dependency-map.png)

### <a name="evaluate-apps"></a>Évaluer les applications

Dans la dernière étape du processus de détection et d’évaluation, Contoso peut évaluer les résultats de l’évaluation et du mappage pour trouver le moyen de migrer chaque application du catalogue de services.

Pour bien représenter ce processus d’évaluation, elle ajoute quelques classifications supplémentaires à l’inventaire.

**Catégorie** | **Valeur attribuée** | **Détails**
--- | --- | ---
Groupe de l’entreprise | Liste des noms de groupes de l’entreprise | Quel est le groupe en charge de l’élément d’inventaire ?
Candidat à une preuve de concept | O/N | L’application peut-elle être utilisée comme preuve de concept ou précurseur pour la migration vers le cloud ?
Dette technique | Aucune/Légère/Lourde | L’élément d’inventaire est-il en cours d’exécution ou utilise-t-il un produit, une plateforme ou un système d’exploitation dont le support n’est plus assuré ?
Implications pour le pare-feu | O/N | L’application communique-t-elle avec Internet/trafic extérieur ?  S’intègre-t-elle à un pare-feu ?
Problèmes de sécurité | O/N | Existe-t-il des problèmes de sécurité connus au niveau de l’application ?  L’application utilise-t-elle des données non chiffrées ou des plateformes obsolètes ?
Stratégie de migration | Réhébergement/Refactorisation/Réarchitecture/Regénération | De quel type de migration l’application a-t-elle besoin ? Comment l’application sera-t-elle déployée dans Azure ? [Plus d’informations](./contoso-migration-overview.md#migration-patterns)
Complexité technique | 1-5 | Quel est le degré de complexité de la migration ? Cette valeur doit être définie par l’équipe DevOps de Contoso et par les partenaires compétents.
Caractère critique pour l’entreprise | 1-5 | Quelle importance l’application a-t-elle pour l’entreprise ? Par exemple, une note de 1 pourra être attribuée à une application utilisée par un petit groupe de travail et une note de 5 à une application critique utilisée dans toute l’organisation. Cette note influencera le niveau de priorité de sa migration.
Priorité de migration | 1/2/3 | Quelle est la priorité de migration de l’application ?
Risque de migration | 1-5 | Qu’est le niveau de risque pour la migration de l’application ? L’équipe DevOps de Contoso et les partenaires compétents doivent se mettre d’accord sur cette valeur.

### <a name="figure-out-costs"></a>Déterminer les coûts

Pour déterminer les coûts et les économies potentielles de la migration vers Azure, Contoso peut se servir de la [Calculatrice du coût total de possession (TCO)](https://azure.microsoft.com/pricing/tco/calculator) pour calculer le coût TCO pour Azure et le comparer à celui d’un déploiement sur site équivalent.

### <a name="identify-assessment-tools"></a>Identifier les outils d’évaluation

Contoso choisit l’outil qui lui permettra de détecter, évaluer et établir l’inventaire. Contoso recense un ensemble d’outils et de services Azure, d’outils et de scripts natifs et d’outils de partenaires. En particulier, Contoso souhaite savoir comment utiliser Azure Migrate pour effectuer une évaluation précise.

#### <a name="azure-migrate"></a>Azure Migrate

Le service Azure Migrate permet de détecter et d’évaluer les machines virtuelles VMware locales en vue de préparer une migration vers Azure. Voici les actions qu’effectue Azure Migrate :

1. Découvrir : Détecter les machines virtuelles VMware locales.
    - Azure Migrate prend en charge la détection à partir de plusieurs serveurs vCenter (en série) et peut exécuter des détections dans différents projets Azure Migrate.
    - Azure Migrate assure la détection au moyen d’une machine virtuelle VMware exécutant Migrate Collector. Le même collecteur peut détecter les machines virtuelles sur différents serveurs vCenter et envoyer des données à différents projets.
2. Évaluation de l’état de préparation : Évaluez si les machines locales se prêtent à une exécution dans Azure. L’évaluation comprend les éléments suivants :
    - Recommandations de taille : Obtenez des suggestions de taille pour les machines virtuelles Azure, en fonction de l’historique des performances des machines virtuelles locales.
    - Coûts mensuels estimés : obtenez les coûts estimés pour l’exécution de machines locales dans Azure.
3. Identifier les dépendances : Visualisez les dépendances des ordinateurs locaux pour créer des groupes d’ordinateurs optimaux pour l’évaluation et la migration.

![Azure Migrate](./media/contoso-migration-scale/azure-migrate.png)

##### <a name="migrate-at-scale"></a>Migrer à l’échelle

Contoso doit utiliser Azure Migrate correctement en raison de l’échelle de cette migration.

- Avec Azure Migrate, Contoso procèdera à une évaluation application par application. Azure Migrate retournera ainsi les données au portail Azure en temps voulu.
- Les administrateurs de Contoso se documentent sur la façon d’effectuer un [déploiement à l’échelle avec Azure Migrate](https://docs.microsoft.com/azure/migrate/how-to-scale-assessment).
- Contoso prend note des limites d’Azure Migrate résumées dans le tableau suivant.

**Action** | **Limite**
--- | ---
Création d’un projet Azure Migrate | 10 000 machines virtuelles
Découverte | 10 000 machines virtuelles
Évaluation | 10 000 machines virtuelles

Contoso prévoit d’utiliser Azure Migrate de la façon suivante :

- Dans vCenter, Contoso organisera les machines virtuelles dans des dossiers. Cela facilitera le travail des équipes qui pourront axer l’évaluation sur les machines virtuelles d’un dossier spécifique.
- Azure Migrate utilise Azure Service Map pour évaluer les dépendances entre les machines. Pour cela, des agents doivent être installés sur les machines virtuelles à évaluer.
  - Contoso utilisera des scripts automatisés pour installer les agents Windows ou Linux nécessaires.
  - En utilisant des scripts, Contoso pourra envoyer (push) l’installation aux machines virtuelles situées dans un dossier vCenter.

#### <a name="database-tools"></a>Outils de base de données

Outre Azure Migrate, Contoso cherchera à utiliser des outils spécialement conçus pour l’évaluation des bases de données. Des outils comme l’[Assistant Migration de données](https://docs.microsoft.com/sql/dma/dma-overview?view=sql-server-2017) l’aideront à évaluer les bases de données SQL Server en vue de la migration.

Avec l’Assistant Migration de données, Contoso pourra déterminer si les bases de données locales sont compatibles avec les différentes solutions de base de données Azure, comme Azure SQL Database, SQL Server s’exécutant sur une machine virtuelle Azure IaaS et Azure SQL Managed Instance.

En plus d’Azure Database Migration Service, Contoso dispose d’autres scripts pour détecter et répertorier les bases de données SQL Server. Ceux-ci se trouvent dans le dépôt GitHub.

#### <a name="partner-assessment-tools"></a>Outils d’évaluation des partenaires

Plusieurs autres outils de partenaires peuvent être utiles à Contoso pour évaluer l’environnement local en vue de la migration vers Azure. [En savoir plus](https://azure.microsoft.com/migration/partners) sur les partenaires de migration Azure.

## <a name="phase-2-migrate"></a>Phase 2 : Migrer

Maintenant que l’évaluation est terminée, Contoso doit identifier les outils qui lui permettront de déplacer ses applications, données et infrastructure vers Azure.

### <a name="migration-strategies"></a>Stratégies de migration

Contoso a le choix entre quatre stratégies de migration globales.

<!--markdownlint-disable MD033 -->

**Stratégie** | **Détails** | **Utilisation**
--- | --- | ---
**Réhébergement** | Souvent appelée migration _lift-and-shift_, cette option sans code permet de migrer rapidement les applications existantes vers Azure.<br/><br/> Les applications sont migrées en l’état, avec les avantages du cloud et sans les risques ou les coûts associés aux modifications de code. | Contoso peut réhéberger les applications moins stratégiques, qui ne nécessitent pas de modifications de code.
**Refactorisation** | Également appelée « repackaging », cette stratégie demande peu de modifications du code ou de la configuration de l’application pour connecter cette dernière à Azure PaaS et tirer le meilleur parti des capacités du cloud. | Contoso peut refactoriser les applications stratégiques afin qu’elles conservent les mêmes fonctionnalités de base, mais en les déplaçant pour qu’elles s’exécutent sur une plateforme Azure telle qu’Azure App Service.<br/><br/> Cela demande peu de modifications de code.<br/><br/> En revanche, Contoso devra assurer la maintenance d’une plateforme de machines virtuelles, car elle ne sera pas gérée par Microsoft.
**Réarchitecture** | Cette stratégie consiste à modifier ou à étendre la base de code d’une application de façon à optimiser son architecture et ainsi profiter des fonctionnalités du cloud et de la mise à l’échelle.<br/><br/> Elle permet d’en faire une application moderne dotée d’une architecture résiliente, hautement scalable et déployable de façon indépendante.<br/><br/> Les services Azure peuvent accélérer le processus, mettre à l’échelle les applications en toute confiance et gérer ces dernières en toute simplicité.
**Recréation** | Cette stratégie consiste à regénérer entièrement une application à l’aide de technologies cloud natives.<br/><br/> La plateforme Azure en tant que service (PaaS) propose un environnement complet de développement et de déploiement dans le cloud. Elle élimine en partie le coût et la complexité des licences logicielles et évite d’avoir à recourir à une infrastructure applicative sous-jacente, à des intergiciels (middleware) et à d’autres ressources. | Contoso peut réécrire entièrement les applications critiques pour tirer parti des technologies cloud comme l’informatique serverless ou les microservices.<br/><br/> Contoso gérera les applications et les services qu’elle développe et Azure gérera tout le reste.

<!--markdownlint-enable MD033 -->

Les données doivent aussi être prises en considération, surtout au vu du volume des bases de données de Contoso. L’approche par défaut de la société consiste à utiliser des services PaaS comme Azure SQL Database pour tirer pleinement parti des fonctionnalités du cloud. En déplaçant ses bases de données vers un service PaaS, Contoso n’aura qu’à gérer les données, laissant ainsi le soin à Microsoft de gérer la plateforme sous-jacente.

### <a name="evaluate-migration-tools"></a>Évaluer les outils de migration

Contoso utilise essentiellement une paire de services et d’outils Azure pour la migration :

- [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) : Orchestre la récupération d’urgence et migre les machines virtuelles locales vers Azure.
- [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview) : Migre les bases de données locales comme SQL Server, MySQL et Oracle vers Azure.

#### <a name="azure-site-recovery"></a>Azure Site Recovery

Azure Site Recovery est le service Azure de base quand il s’agit d’orchestrer la récupération d’urgence et la migration au sein d’Azure et des sites locaux vers Azure.

1. Site Recovery autorise et orchestre la réplication de vos sites locaux vers Azure.
2. Dès lors que la réplication est configurée et qu’elle s’exécute, les machines locales peuvent être basculées vers Azure, ce qui marque la fin de la migration.

Contoso avait déjà [réalisé une preuve de concept](./contoso-migration-rehost-vm.md) pour voir si Site Recovery pouvait les aider à migrer vers le cloud.

##### <a name="use-site-recovery-at-scale"></a>Utiliser Site Recovery à l’échelle

Contoso envisage d’effectuer plusieurs migrations lift-and-shift. Pour s’assurer que cela fonctionne, Site Recovery exécutera une réplication par lots d’environ 100 machines virtuelles à la fois. Pour savoir comment cela fonctionne, Contoso a besoin de planifier la capacité pour la migration Site Recovery proposée.

- Contoso doit collecter des informations sur ses volumes de trafic. En particulier :
  - Contoso doit déterminer le taux de modification des machines virtuelles à répliquer.
  - Contoso doit aussi tenir compte de la connectivité réseau du site local à Azure.
- Face aux exigences de capacité et de volume, les équipes doivent allouer suffisamment de bande passante, compte tenu du taux de modification quotidien des données des machines virtuelles en question, pour atteindre son objectif de point de récupération (RPO).
- Enfin, elles doivent déterminer le nombre de serveurs qu’il faudra pour exécuter les composants Site Recovery nécessaires au déploiement.

###### <a name="gather-on-premises-information"></a>Collecter les informations locales

Contoso peut utiliser l’outil [Planificateur de déploiement Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-deployment-planner) pour effectuer ces étapes :

- Contoso peut utiliser cet outil pour profiler à distance les machines virtuelles sans aucune répercussion sur l’environnement de production. Cela permet de cerner les besoins en bande passante et stockage pour la réplication et le basculement.
- Contoso peut exécuter l’outil sans installer de composants Site Recovery en local.
- L’outil collecte des informations sur les machines virtuelles compatibles et incompatibles, le nombre de disques par machine virtuelle et l’activité des données par disque. De même, il identifie les besoins en bande passante réseau, ainsi que l’infrastructure Azure nécessaires au succès de la réplication et du basculement.
- Contoso doit veiller à exécuter l’outil de planification sur des ordinateurs Windows Server qui ont la configuration minimale requise pour le serveur de configuration Site Recovery. Le serveur de configuration est un ordinateur Site Recovery qui est nécessaire à la réplication des machines virtuelles VMware locales.

###### <a name="identify-site-recovery-requirements"></a>Identifier la configuration requise pour Site Recovery

Outre la réplication des machines virtuelles, Site Recovery a besoin de plusieurs composants pour la migration de VMware.

<!--markdownlint-disable MD033 -->

**Composant** | **Détails**
--- | ---
**Serveur de configuration** | Généralement une machine virtuelle VMware configurée à l’aide d’un modèle OVF.<br/><br/> Le composant de serveur de configuration coordonne la communication entre les ordinateurs locaux et Azure, et gère la réplication des données.
**Serveur de traitement** | Installé par défaut sur le serveur de configuration.<br/><br/> Le composant serveur de processus reçoit les données de réplication, les optimise grâce à la mise en cache, la compression et le chiffrement, puis les envoie à Stockage Azure.<br/><br/> De plus, le serveur de processus installe le service Mobilité d’Azure Site Recovery sur les machines virtuelles que vous voulez répliquer, et effectue une découverte automatique sur les machines locales.<br/><br/> Les déploiements mis à l’échelle ont besoin d’autres serveurs de processus autonomes pour gérer les importants volumes de trafic de réplication.
**Service Mobilité** | L’agent Service Mobilité est installé sur chaque machine virtuelle VMware destinée à être migrée avec Site Recovery.

<!--markdownlint-enable MD033 -->

Contoso doit savoir comment déployer ces composants en tenant compte des considérations de capacité.

<!--markdownlint-disable MD033 -->

**Composant** | **Besoins en capacité**
--- | ---
**Taux de modification quotidien maximal** | Un seul serveur de processus peut prendre en charge un taux de modification quotidien maximal de 2 To. Sachant qu’une machine virtuelle ne peut utiliser qu’un seul serveur de processus, le taux quotidien maximal de modification de données pris en charge pour une machine virtuelle répliquée est de 2 To.
**Débit maximal** | Un compte standard Stockage Azure peut gérer au maximum 20 000 demandes par seconde, et les opérations d’entrée/sortie par seconde (IOPS) sur une machine virtuelle en cours de réplication doivent se situer dans cette limite. Par exemple, si une machine virtuelle dispose de 5 disques et que chaque disque génère 120 IOPS (taille de 8 Ko) sur la machine virtuelle, la limite de 500 IOPS sur le disque Azure est respectée.<br/><br/> Notez que le nombre de comptes de stockage nécessaires est égal au nombre total d’IOPS de la machine source divisé par 20 000. Un ordinateur répliqué ne peut appartenir qu’à un seul compte de stockage dans Azure.
**Serveur de configuration** | D’après son estimation de réplication de 100 à 200 machines virtuelles et des [exigences de dimensionnement du serveur de configuration](https://docs.microsoft.com/azure/site-recovery/site-recovery-plan-capacity-vmware#size-recommendations-for-the-configuration-server-and-inbuilt-process-server), les équipes Contoso estiment qu’elles ont besoin d’un ordinateur serveur de configuration avec les capacités suivantes :<br/><br/> Processeur : 16 processeurs virtuels (2 sockets &#215; 8 cœurs de 2,5 GHz)<br/><br/> Mémoire : 32 Go<br/><br/> Disque cache : 1 To<br/><br/> Taux de modification des données : 1 To à 2 To.<br/><br/> En plus des exigences de dimensionnement, Contoso devra vérifier que l’emplacement du serveur de configuration est optimal, à savoir sur le même réseau et le même segment de réseau local que les machines virtuelles qui seront migrées.
**Serveur de traitement** | Contoso prévoit de déployer un serveur de processus dédié autonome capable de répliquer entre 100 et 200 machines virtuelles :<br/><br/> Processeur : 16 processeurs virtuels (2 sockets &#215; 8 cœurs de 2,5 GHz)<br/><br/> Mémoire : 32 Go<br/><br/> Disque cache : 1 To<br/><br/> Taux de modification des données : 1 To à 2 To.<br/><br/> Le serveur de processus sera fortement sollicité et doit donc se trouver sur un hôte ESXi capable de gérer les E/S disque, le trafic réseau et l’UC nécessaires à la réplication. Pour cela, Contoso examinera s’il y a lieu d’utiliser un hôte dédié.
**Mise en réseau** | Après avoir examiné l’infrastructure VPN de site à site actuelle, Contoso a décidé d’implémenter Azure ExpressRoute. Cette implémentation est cruciale, car elle permettra de réduire la latence et d’améliorer la bande passante pour la région Azure primaire de Contoso (USA Est 2).<br/><br/> **Surveillance :** Contoso devra superviser attentivement les flux de données en provenance du serveur de processus. Si les données surchargent la bande passante réseau, Contoso envisagera de [limiter la bande passante du serveur de processus](https://docs.microsoft.com/azure/site-recovery/site-recovery-plan-capacity-vmware#control-network-bandwidth).
**Azure Storage** | Pour la migration, Contoso doit identifier le type et le nombre appropriés de comptes Stockage Azure cibles. Site Recovery réplique les données de machine virtuelle dans le stockage Azure.<br/><br/> Site Recovery peut répliquer dans des comptes de stockage Standard ou Premium (SSD).<br/><br/> Pour prendre une décision concernant le stockage, Contoso doit examiner les [limites de stockage](https://docs.microsoft.com/azure/virtual-machines/windows/disks-types) et tenir compte des perspectives de croissance et d’utilisation dans le temps. Compte tenu de la vitesse et de la priorité des migrations, Contoso a décidé d’utiliser des SSD Premium.<br/><br/>
Contoso a décidé d’utiliser des disques managés pour toutes les machines virtuelles déployées dans Azure. Le nombre d’opérations d’entrée/sortie par seconde (IOPS) dictera le type de disque qui sera utilisé : Standard (HDD ou SSD) ou Premium (SSD).<br/><br/>

<!--markdownlint-enable MD033 -->

#### <a name="azure-database-migration-service"></a>Azure Database Migration Service

Azure Database Migration Service (DMS) est un service complètement managé permettant des migrations sans interruption de plusieurs sources de base de données vers des plateformes de données Azure avec un temps d’arrêt minimum.

- DMS intègre les fonctionnalités d’outils et de services existants. Il s’appuie sur l’Assistant Migration de données pour générer des rapports d’évaluation qui émettent des recommandations concernant la compatibilité des bases de données et les modifications nécessaires.
- DMS utilise un processus de migration simple et auto-guidé, dont l’évaluation intelligente aide à résoudre les problèmes potentiels avant la migration.
- DMS permet une migration à l’échelle de plusieurs sources vers la base de données Azure cible.
- DMS assure une prise en charge de SQL Server, de la version 2005 à la version 2017.

DMS n’est pas le seul outil de migration de base de données Microsoft. Une comparaison des outils et des services peut être consultée [ici](https://blogs.msdn.microsoft.com/datamigration/2017/10/13/differentiating-microsofts-database-migration-tools-and-services).

##### <a name="use-dms-at-scale"></a>Utiliser DMS à l’échelle

Contoso prévoit d’utiliser DMS au moment de migrer à partir de SQL Server.

- Pendant la phase d’approvisionnement de DMS, Contoso doit le dimensionner correctement et le configurer de façon à optimiser le niveau de performance des migration de données. Contoso sélectionnera l’option « Niveau critique pour l’entreprise avec 4 vCores », permettant ainsi au service de tirer parti de plusieurs processeurs virtuels pour la parallélisation et de transferts de données plus rapides.

    ![Mise à l’échelle de DMS](./media/contoso-migration-scale/dms.png)

- Une autre tactique de mise à l’échelle pour Contoso consiste à faire provisoirement monter en puissance l’instance cible Azure SQL ou Base de données MySQL vers la référence SKU de niveau Premium pendant la migration de données. Cela permet de réduire la limitation de base de données qui peut avoir une incidence sur les activités de transfert de données quand des références SKU de niveau inférieur sont utilisées.

##### <a name="use-other-tools"></a>Utiliser d’autres outils

Outre DMS, Contoso peut utiliser d’autres outils et services pour identifier les informations des machines virtuelles.

- Elle dispose de scripts qui facilitent les migrations manuelles. Ceux-ci sont disponibles dans le dépôt GitHub.
- Différents [outils de partenaires](https://azure.microsoft.com/migration/partners) peuvent aussi être utilisés pour la migration.

## <a name="phase-3-optimize"></a>Phase 3 : Optimiser

Après avoir déplacé les ressources vers Azure, Contoso doit les simplifier pour améliorer les performances et optimiser le retour sur investissement à l’aide d’outils de gestion des coûts. Étant donné qu’Azure est un service facturé à l’utilisation, il est essentiel pour Contoso de comprendre le fonctionnement des systèmes et de vérifier qu’ils sont correctement dimensionnés.

### <a name="azure-cost-management"></a>Gestion des coûts Azure

Pour exploiter au mieux son investissement cloud, Contoso entend tirer parti de l’outil gratuit Azure Cost Management.

- Cette solution sous licence conçue par Cloudyn, filiale de Microsoft, permet à Contoso de gérer ses dépenses cloud avec précision et en toute transparence. Cette solution propose des outils pour surveiller, répartir et réduire les coûts liés au cloud.
- Azure Cost Management fournit des rapports de tableau de bord simples qui facilitent la répartition des coûts, la rétrofacturation et la facturation interne.
- Azure Cost Management permet d’optimiser les dépenses cloud en identifiant les ressources sous-utilisées, ce qui permettra à Contoso de les gérer et de les ajuster.
- [En savoir plus](https://docs.microsoft.com/azure/cost-management/overview) sur Azure Cost Management.

![la gestion des coûts ;](./media/contoso-migration-scale/cost-management.png)

### <a name="native-tools"></a>Outils natifs

Contoso prévoit aussi d’utiliser des scripts pour localiser les ressources non utilisées.

- Pendant les migrations de grande ampleur, il est fréquent qu’il reste des reliquats de données, comme des disques durs virtuels (VHD), qui occasionnent des frais sans pour autant être utiles à l’entreprise. Les scripts sont disponibles dans le dépôt GitHub.
- Contoso entend tirer parti du travail réalisé par le service informatique de Microsoft et envisage d’implémenter le kit d’optimisation des ressources Azure (ARO).
- Contoso peut déployer un compte Azure Automation avec des runbooks et des planifications préconfigurés dans son abonnement et commencer à faire des économies. L’optimisation des ressources Azure se produit automatiquement dans un abonnement dès lors qu’une planification est activée ou créée, et l’optimisation s’étend aux nouvelles ressources.
- Ces fonctionnalités d’automation décentralisées permettent de réduire les coûts. Voici quelques fonctionnalités :
  - Mise en veille automatique des machines virtuelles Azure faiblement actives.
  - Mise en veille et sortie de veille programmées des machines virtuelles Azure.
  - Mise en veille et sortie de veille programmées des machines virtuelles Azure par ordre croissant et décroissant à l’aide de balises Azure.
  - Suppression en bloc de groupes de ressources à la demande.
- Démarrez avec le kit de ressources ARO dans ce [dépôt GitHub](https://github.com/Azure/azure-quickstart-templates/tree/master/azure-resource-optimization-toolkit).

### <a name="partner-optimization-tools"></a>Outils d’optimisation de partenaires

Il est possible d’utiliser des outils de partenaires comme [Hanu](https://hanu.com/insight) et [Scalr]( https://www.scalr.com/cost-optimization).

## <a name="phase-4-secure-and-manage"></a>Phase 4 : Sécuriser et gérer

Au cours de cette phase, Contoso utilise les ressources de sécurité et de gestion Azure pour régir, sécuriser et superviser les applications cloud dans Azure. Ces ressources permettent d’utiliser les produits disponibles sur le portail Azure dans un environnement sécurisé et bien géré. Contoso commence à utiliser ces services pendant la migration et profite de la prise en charge hybride d’Azure pour continuer à en utiliser certains pour une expérience cohérente à l’échelle du cloud hybride.

### <a name="security"></a>Sécurité

Contoso prévoit de s’appuyer sur Azure Security Center pour bénéficier de fonctionnalités unifiées de gestion de la sécurité et de protection avancée contre les menaces dans vos charges de travail cloud hybrides.

- Security Center offre une visibilité et un contrôle intégraux sur la sécurité des applications cloud dans Azure.
- Contoso peut ainsi détecter rapidement les menaces et prendre les mesures nécessaires pour y répondre, et réduire les risques de sécurité en activant la protection adaptative contre les menaces.

[En savoir plus](https://azure.microsoft.com/services/security-center) sur Security Center.

### <a name="monitoring"></a>Surveillance

Contoso a besoin d’une visibilité sur l’intégrité et les performances des applications, de l’infrastructure et des données nouvellement migrées et s’exécutant désormais dans Azure. Contoso utilisera les outils de supervision cloud Azure intégrés comme Azure Monitor, l’espace de travail Log Analytics et Application Insights.

- Grâce à ces outils, Contoso pourra facilement collecter des données provenant de sources et bénéficier d’insights détaillés. Par exemple, Contoso peut mesurer l’utilisation de l’UC, de la mémoire et du disque des machines virtuelles, afficher les dépendances des applications et du réseau au niveau des diverses machines virtuelles et suivre les performances des applications.
- Contoso se servira de ces outils de supervision du cloud pour prendre des mesures et s’intégrer à des solutions de service.
- [En savoir plus](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview) sur la supervision Azure.

### <a name="business-continuity-and-disaster-recovery"></a>Continuité d’activité et reprise d’activité

Contoso aura besoin d’une stratégie de continuité d’activité et de reprise d’activité (BCDR) pour ses ressources Azure.

- Azure propose des [fonctionnalités BCDR intégrées](https://docs.microsoft.com/azure/architecture/resiliency/disaster-recovery-azure-applications) destinées à assurer la sécurité des données et le bon fonctionnement des applications et des services.
- En plus des fonctionnalités intégrées, la société Contoso tient à s’assurer qu’elle pourra récupérer après une défaillance, éviter les interruptions d’activité coûteuses, répondre aux objectifs de conformité et protéger les données contre les ransomwares et les erreurs humaines. Pour ce faire :
  - Contoso prévoit de déployer la solution économique Sauvegarde Microsoft Azure pour sauvegarder les ressources Azure. Comme cette solution est intégrée, Contoso pourra configurer des sauvegardes cloud en quelques étapes simples.
  - Contoso configurera la récupération d’urgence pour les machines virtuelles Azure à l’aide d’Azure Site Recovery de façon à assurer la réplication, le basculement et la restauration automatique entre les régions Azure spécifiées. Les applications qui s’exécutent sur les machines virtuelles Azure seront ainsi assurées de rester disponibles dans la région secondaire choisie par Contoso au cas où une panne surviendrait dans la région primaire. [Plus d’informations](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

## <a name="conclusion"></a>Conclusion

Dans cet article, la société Contoso a établi des plans pour effectuer une migration Azure à l’échelle. Elle a divisé le processus de migration en quatre étapes, à savoir : évaluation, migration, optimisation, puis sécurité et gestion une fois la migration terminée. S’il est particulièrement important d’envisager un projet de migration dans son ensemble, le processus migration des systèmes d’une organisation doit être décomposé sous forme de classifications et de numéros qui font sens pour l’entreprise. En évaluant les données et en appliquant des classifications, le projet peut être décomposé en une série de migrations de plus petite taille, qui peuvent s’exécuter rapidement et en toute sécurité. La somme de ces petites migrations se transforme rapidement et avec succès en une migration d’envergure vers Azure.
