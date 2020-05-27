---
title: Stratégies de migration d’applications mainframe
description: Découvrez les stratégies permettant de réhéberger, mettre hors service, regénérer ou remplacer les applications à migrer d’environnements mainframe vers Azure.
author: njray
ms.author: v-nanra
ms.date: 12/26/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: eb599b892e5cb3e898faf84fb1bd8b65b8d9d03b
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83815070"
---
<!-- cSpell:ignore njray nanra Attunity Codit DRDA ISAM ISQL LPARS VSAM ODBC JDBC GDGs REXX TIP dbextents Raincode Tmax -->

# <a name="mainframe-application-migration"></a>Migration d’applications d’un environnement mainframe

Quand elles entreprennent de migrer des applications d’un environnement mainframe vers Azure, la plupart des équipes informatiques adoptent une approche pragmatique : elles réutilisent le maximum de ressources possible, puis elles débutent un déploiement échelonné où certaines applications sont réécrites ou remplacées.

La migration d’applications engage généralement une ou plusieurs des stratégies suivantes :

- **Réhébergement :** vous pouvez déplacer le code, les programmes et les applications existants de l’environnement mainframe, et ensuite recompiler le code à exécuter dans un émulateur de mainframe qui est hébergé dans une instance cloud. En règle générale, avec cette approche, vous commencez par déplacer les applications vers un émulateur dans le cloud, puis vous migrez la base de données vers une base de données dans le cloud. Cette approche nécessite certaines opérations d’ingénierie et de refactorisation ainsi que des conversions de données et de fichiers.

    Vous pouvez aussi faire appel à un fournisseur d’hébergement traditionnel. L’un des avantages majeurs du cloud est l’externalisation de la gestion de l’infrastructure. Vous pouvez trouver un fournisseur de centre de données qui hébergera vos charges de travail de mainframe pour vous. Ce modèle peut vous faire gagner du temps, réduire votre dépendance à l’égard des fournisseurs et diminuer vos coûts intermédiaires.

- **Mise hors service :** toutes les applications devenues inutiles doivent être mises hors service avant la migration.

- **Regénération :** certaines organisations choisissent de réécrire entièrement les programmes à l’aide de techniques modernes. Cette approche est moins courante que l’approche lift-and-shift, car elle s’avère plus chère et plus complexe. Après ce type de migration, il est souvent judicieux de commencer à remplacer des modules et du code en s’aidant de moteurs de transformation de code.

- **Remplacement :** cette approche remplace les fonctionnalités du mainframe par des options équivalentes dans le cloud. SaaS (software as a service) est une option disponible : elle utilise une solution créée spécifiquement pour répondre à un besoin de l’entreprise, comme la finance, les ressources humaines, la fabrication ou la planification des ressources métier. En outre, il existe maintenant de nombreuses applications métier capables de résoudre des problématiques qui étaient auparavant gérées par des solutions mainframe personnalisées.

Vous devez commencer par planifier les charges de travail que vous souhaitez migrer en priorité, puis déterminer les prérequis pour déplacer les ressources associées (applications, bases de code hérité et bases de données).

## <a name="mainframe-emulation-in-azure"></a>Émulation de mainframe dans Azure

Les services cloud Azure peuvent émuler des environnements mainframe traditionnels, ce qui vous permet de réutiliser des applications et du code mainframe existants. Les composants serveur communs que vous pouvez émuler incluent les systèmes de traitement transactionnel en ligne (OLTP), de traitement par lots et d’ingestion des données.

### <a name="oltp-systems"></a>Systèmes OLTP

Beaucoup d’environnements mainframe comprennent des systèmes OLTP qui traitent des milliers ou des millions de mises à jour pour le compte d’innombrables utilisateurs. Ces applications utilisent souvent des logiciels de traitement transactionnel et de gestion des formulaires/de l’écran, tels qu’un système de contrôle des informations client (CICS), des systèmes de gestion des informations (IMS) et un processeur d’interface de terminal (TIP).

Quand des applications OLTP sont migrées vers Azure, des émulateurs pour les moniteurs transactionnels (TP) de mainframe peuvent s’exécuter en tant qu’IaaS sur des machines virtuelles Azure. La fonctionnalité de saisie de formulaires et de gestion de l’écran peut également être implémentée par des serveurs web. Il est possible de combiner cette approche avec des API de base de données, comme ADO (ActiveX Data Objects), ODBC (Open Database Connectivity) et JDBC (Java Database Connectivity) pour l’accès aux données et les transactions.

### <a name="time-constrained-batch-updates"></a>Mises à jour par lots avec des contraintes de temps

Beaucoup de systèmes mainframe effectuent mensuellement ou annuellement les mises à jour de millions d’enregistrements de compte, en particulier ceux utilisés dans les banques, les compagnies d’assurance et les organismes publics. Les ordinateurs mainframe gèrent ces types de charges de travail en offrant des systèmes de gestion des données à haut débit. Les traitements par lots sur ces ordinateurs s’effectuent généralement en série par nature et leur performance dépend du débit IOPS (entrées/sorties par seconde) assuré par le mainframe principal.

Les environnements de traitement par lots dans le cloud utilisent le calcul parallèle et des réseaux à haut débit pour améliorer les performances. Azure propose plusieurs options de calcul, de stockage et de mise en réseau qui vous aident à optimiser les performances du traitement par lots.

### <a name="data-ingestion-systems"></a>Systèmes d’ingestion des données

Les ordinateurs mainframe ingèrent de grandes quantités de données qui leur sont transmises pour traitement par les solutions des services commerciaux, financiers, de fabrication, etc. Avec Azure, vous pouvez utiliser des utilitaires en ligne de commande simples, comme [AzCopy](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy), pour copier des données vers et depuis l’emplacement de stockage. Vous pouvez également utiliser le service [Azure Data Factory](https://docs.microsoft.com/azure/data-factory/introduction), qui ingère des données provenant de magasins de données disparates pour vous permettre de créer et planifier des workflows basés sur des données.

En plus des environnements d’émulation, Azure fournit des services PaaS (platform as a service) et d’analytique qui contribuent à optimiser les environnements mainframe existants.

## <a name="migrate-oltp-workloads-to-azure"></a>Migrer des charges de travail OLTP vers Azure

L’approche lift-and-shift est l’option sans code qui vous permet de migrer rapidement des applications existantes vers Azure. Chaque application est migrée en l’état, ce qui offre les avantages du cloud sans les risques ni les coûts liés aux modifications de code. Cette approche est possible quand vous utilisez un émulateur pour les moniteurs TP de mainframe sur Azure.

Les moniteurs TP sont proposés par différents fournisseurs et s’exécutent sur des machines virtuelles, une option IaaS (infrastructure as a service) disponible sur Azure. Les diagrammes suivants avant/après illustrent la migration d’une application en ligne adossée au système SGBD IBM DB2 sur un ordinateur mainframe IBM z/OS. Le système DB2 pour z/OS utilise des fichiers VSAM (Virtual Storage Access Method) pour stocker les données et des fichiers plats ISAM (Indexed Sequential Access Method). Cette architecture utilise également le système CICS pour la supervision des transactions.

![Migration « lift-and-shift » d’un environnement mainframe vers Azure à l’aide d’un logiciel d’émulation](../../_images/mainframe-migration/mainframe-vs-azure.png)

Sur Azure, les environnements d’émulation sont utilisés pour exécuter le gestionnaire TP et les traitements par lots basés sur JCL. Dans la couche Données, DB2 est remplacé par [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), mais il est également possible d’utiliser Microsoft SQL Server, DB2 LUW ou Oracle Database. Un émulateur prend en charge IMS, VSAM et SEQ. Les outils de gestion du système mainframe sont remplacés par des services Azure et par des logiciels d’autres fournisseurs, qui s’exécutent sur des machines virtuelles.

La fonctionnalité de saisie de formulaires et de gestion de l’écran est généralement implémentée par des serveurs web, éventuellement combinés avec des API de base de données, comme ADO, ODBC et JDBC pour l’accès aux données et les transactions. Le choix exact des composants IaaS Azure à utiliser dépend de votre système d’exploitation. Par exemple :

- Machines virtuelles Windows : Internet Information Server (IIS), avec ASP.NET pour la gestion de l’écran et la logique métier. Utilisez ADO.NET pour les transactions et l’accès aux données.

- Machines virtuelles Linux : serveurs d’applications basés sur Java, par exemple, Apache Tomcat pour la gestion de l’écran et les fonctionnalités métier basées sur Java. Utilisez JDBC pour les transactions et l’accès aux données.

## <a name="migrate-batch-workloads-to-azure"></a>Migrer des charges de travail par lots vers Azure

Les opérations par lots dans Azure diffèrent de l’environnement de traitement par lots classique sur les ordinateurs mainframe. Les traitements par lots sur ces ordinateurs s’effectuent généralement en série par nature et leur performance dépend du débit IOPS assuré par le mainframe principal. Les environnements de traitement par lots dans le cloud utilisent le calcul parallèle et des réseaux à haut débit pour améliorer les performances.

Pour optimiser les performances des traitements par lots à l’aide d’Azure, vous pouvez utiliser les options de [calcul](https://docs.microsoft.com/azure/virtual-machines/windows/overview), de [stockage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction), de [mise en réseau](https://azure.microsoft.com/blog/maximize-your-vm-s-performance-with-accelerated-networking-now-generally-available-for-both-windows-and-linux) et de [supervision](https://docs.microsoft.com/azure/azure-monitor/overview) comme suit.

### <a name="compute"></a>Calcul

Utilisez :

- Utilisez des machines virtuelles avec la fréquence d’horloge la plus élevée. Les applications mainframe sont souvent monothread et les processeurs mainframe ont une fréquence d’horloge très élevée.

- Utilisez des machines virtuelles avec une grande capacité de mémoire pour permettre la mise en cache des données et des applications des zones de travail.

- Utilisez des machines virtuelles avec des processeurs virtuels à très haute densité pour tirer pleinement parti du traitement multithread, si l’application prend en charge les threads multiples.

- Utilisez le traitement parallèle (Azure facilite le scale-out pour ce type de traitement) afin d’augmenter la puissance de calcul disponible au moment d’un traitement par lots.

### <a name="storage"></a>Stockage

Utilisez :

- Utilisez [Azure SSD Premium](https://docs.microsoft.com/azure/virtual-machines/windows/premium-storage) ou [Azure SSD Ultra](https://docs.microsoft.com/azure/virtual-machines/windows/disks-ultra-ssd) pour bénéficier d’un débit IOPS maximal.

- Utilisez l’entrelacement sur plusieurs disques pour augmenter le débit IOPS par taille de stockage.

- Partitionnez le stockage afin de répartir les E/S entre plusieurs dispositifs de stockage Azure.

### <a name="networking"></a>Mise en réseau

- Activez l’[accélération réseau Azure](https://docs.microsoft.com/azure/virtual-network/create-vm-accelerated-networking-powershell) pour réduire la latence.

### <a name="monitoring"></a>Surveillance

- Utilisez des outils d’analyse, [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview), [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) et les journaux Azure afin d’aider les administrateurs à analyser les surcharges de performances liées aux traitements par lots et à éliminer les goulots d’étranglement.

## <a name="migrate-development-environments"></a>Migrer des environnements de développement

Les architectures distribuées du cloud s’appuient sur différents ensembles d’outils de développement qui offrent les avantages des pratiques et des langages de programmation modernes. Pour faciliter cette transition, vous pouvez utiliser un environnement de développement avec d’autres outils conçus pour émuler les environnements IBM z/OS. La liste suivante présente les options proposées par Microsoft et d’autres fournisseurs :

| Composant        | Options Azure                                                                                                                                  |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| z/OS             | Windows, Linux ou UNIX                                                                                                                      |
| CICS             | Services Azure proposés par Micro Focus, Oracle, GT Software (Fujitsu), TmaxSoft, Raincode et NTT Data, ou réécriture à l’aide de Kubernetes |
| IMS              | Services Azure proposés par Micro Focus et Oracle                                                                                  |
| Assembler        | Services Azure proposés par Raincode et TmaxSoft ; ou COBOL, C ou Java, ou mappage aux fonctions du système d’exploitation               |
| JCL              | JCL, PowerShell ou autres outils de script                                                                                                   |
| COBOL            | COBOL, C ou Java                                                                                                                            |
| Natural          | Naturel, COBOL, C ou Java                                                                                                                  |
| FORTRAN et PL/I | FORTRAN, PL/I, COBOL, C ou Java                                                                                                           |
| REXX et PL/I    | REXX, PowerShell ou autres outils de script                                                                                                  |

## <a name="migrate-databases-and-data"></a>Migrer des données et des bases de données

La migration d’application implique généralement le réhébergement de la couche Données. Vous pouvez migrer facilement des bases de données SQL Server, open source et d’autres bases de données relationnelles vers des solutions entièrement managées sur Azure, comme [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), [Azure Database pour PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview) et [Azure Database pour MySQL](https://docs.microsoft.com/azure/mysql/overview) avec [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview).

Par exemple, vous pouvez effectuer la migration si la couche Données de mainframe utilise :

- IBM DB2 ou une base de données IMS. Utilisez Azure SQL Database, SQL Server, DB2 LUW ou Oracle Database sur Azure.

- Des fichiers VSAM et autres fichiers plats. Utilisez des fichiers plats ISAM (Indexed Sequential Access Method) pour Azure SQL, SQL Server, DB2 LUW ou Oracle.

- Des groupes de données de génération (GDG). Migrez vers des fichiers sur Azure qui utilisent une convention de nommage et des extensions de nom de fichier offrant les mêmes fonctionnalités que les GDG.

La couche Données IBM comprend plusieurs composants clés que vous devez également migrer. Par exemple, quand vous migrez une base de données, vous migrez en même temps une collection de données stockées dans des pools, chacun d’eux contenant des dbextents, qui sont des jeux de données VSAM z/OS. Votre migration doit inclure le répertoire qui identifie les emplacements des données dans les pools de stockage. De plus, votre plan de migration doit prendre en compte le journal de base de données, qui contient un enregistrement des opérations effectuées sur la base de données. Une base de données peut avoir un, deux (double ou autre) ou quatre journaux (doubles et autres).

La migration de la base de données inclut également les composants ci-dessous :

- **Gestionnaire de base de données :** il fournit l’accès aux données dans la base de données. Le gestionnaire de base de données s’exécute dans sa propre partition dans un environnement z/OS.
- **Demandeur d’applications :** il accepte les demandes des applications avant de les passer à un serveur d’applications.
- **Adaptateur de ressources en ligne :** il inclut les composants du demandeur d’applications à utiliser dans les transactions CICS.
- **Adaptateur de ressources par lots :** il implémente les composants du demandeur d’applications pour les applications par lots dans z/OS.
- **Interactive SQL (ISQL) :** il s’exécute comme une interface et une application CICS pour permettre aux utilisateurs d’entrer des instructions SQL ou des commandes d’opérateur.
- **Application CICS :** elle s’exécute sous le contrôle de CICS, en utilisant les sources de données et les ressources disponibles dans CICS.
- **Application par lots :** elle exécute un processus logique sans communication interactive avec les utilisateurs pour produire des mises à jour de données en bloc ou générer des rapports à partir d’une base de données, par exemple.

## <a name="optimize-scale-and-throughput-for-azure"></a>Optimiser la mise à l’échelle et le débit pour Azure

D’une manière générale, les systèmes mainframe montent en puissance tandis que le cloud monte en charge. Pour optimiser la mise à l’échelle et le débit des applications de style mainframe qui s’exécutent sur Azure, il est important de bien comprendre de quelle façon les systèmes mainframe peuvent séparer et isoler les applications. Un système mainframe z/OS utilise une fonctionnalité de partitions logiques appelée LPAR pour isoler et gérer les ressources dont a besoin une application spécifique sur une instance unique.

Par exemple, un système mainframe peut utiliser une partition logique (LPAR) pour une région CICS et les programmes COBOL associés, et une partition LPAR séparée pour DB2. Des partitions LPAR supplémentaires sont souvent utilisées pour les environnements de développement, de test et de préproduction.

Sur Azure, il est plus courant d’utiliser des machines virtuelles séparées à la place. Une architecture Azure déploie généralement des machines virtuelles pour la couche Application, un groupe séparé de machines virtuelles pour la couche Données, un autre groupe pour le développement, et ainsi de suite. Chaque niveau de traitement peut alors être optimisé en déployant le type de machines virtuelles et de fonctionnalités le plus adapté à l’environnement existant.

De plus, chaque niveau peut fournir des services de reprise d’activité après sinistre. Par exemple, les machines virtuelles de base de données et de production peuvent nécessiter une reprise d’activité à chaud, alors que les machines virtuelles de développement et de test prennent en charge une reprise d’activité à froid.

La figure suivante illustre un déploiement Azure possible avec un site principal et un site secondaire. Dans le site principal, les machines virtuelles de test, de préproduction et de production sont déployées avec une haute disponibilité. Le site secondaire est utilisé pour la sauvegarde et pour la reprise d’activité après sinistre.

![Déploiement Azure possible avec un site principal et un site secondaire](../../_images/mainframe-migration/migration-backup-dr.png)

## <a name="perform-a-staged-mainframe-to-azure"></a>Effectuer une migration intermédiaire de l’ordinateur mainframe vers Azure

Le processus de déplacement des solutions d’un ordinateur mainframe vers Azure peut comprendre une migration _intermédiaire_, qui consiste à déplacer certaines applications en priorité et à conserver les applications restantes sur l’ordinateur mainframe de façon temporaire ou permanente. Cette approche nécessite généralement des systèmes qui permettent aux applications et aux bases de données d’interagir entre l’ordinateur mainframe et Azure.

Un scénario courant consiste à déplacer une application vers Azure, mais en conservant sur l’ordinateur mainframe toutes les données dont a besoin l’application. Un logiciel spécifique est utilisé pour que les applications sur Azure puissent accéder aux données à partir de l’ordinateur mainframe. Heureusement, il existe un large éventail de solutions qui permettent l’intégration entre Azure et les environnements mainframe existants, la prise en charge de scénarios hybrides et la migration progressive. Les partenaires Microsoft, les éditeurs de logiciels indépendants et les intégrateurs système peuvent vous aider dans votre démarche.

[Microsoft Host Integration Server](https://docs.microsoft.com/host-integration-server) est l’une des solutions disponibles. Elle fournit l’architecture de base de données relationnelle distribuée (DRDA) requise par les applications dans Azure pour accéder aux données dans DB2 conservées sur l’ordinateur mainframe. Il existe d’autres options pour l’intégration entre les environnements mainframe et Azure, parmi lesquelles les solutions fournies par IBM, Attunity et Codit, entre autres, ainsi que des solutions open source.

## <a name="partner-solutions"></a>Solutions de partenaires

Si vous envisagez d’effectuer une migration de mainframe, le réseau de partenaires est là pour vous aider.

Azure fournit une infrastructure fiable, hautement disponible et évolutive pour les systèmes qui s’exécutent sur des ordinateurs mainframe. Certaines charges de travail peuvent être migrées assez facilement. D’autres charges de travail qui dépendent de logiciels système hérités, tels que CICS et IMS, peuvent être réhébergées à l’aide de solutions de partenaires, en attendant d’être migrées progressivement vers Azure. Quel que soit votre choix, Microsoft et ses partenaires sont à votre disposition pour vous aider à optimiser votre environnement pour Azure tout en maintenant le même niveau de fonctionnalités logicielles de votre système mainframe existant.

<!-- docsTest:ignore "IBM DB2 pureScale" -->

## <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez les ressources suivantes :

- [Prise en main d’Azure](https://docs.microsoft.com/azure)

- [Déployer IBM DB2 pureScale sur Azure](https://azure.microsoft.com/resources/deploy-ibm-db2-purescale-on-azure)

- [Documentation Host Integration Server](https://docs.microsoft.com/host-integration-server)
