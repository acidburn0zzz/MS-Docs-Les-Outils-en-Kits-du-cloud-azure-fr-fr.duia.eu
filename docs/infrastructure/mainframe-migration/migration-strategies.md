---
title: Migrer des applications de mainframes vers Azure
description: Obtenez des conseils techniques pour passer d’une plateforme mainframe aux capacités de stockage et de calcul hyperscale d’Azure dans un environnement à haute disponibilité.
author: njray
ms.author: v-nanra
ms.date: 12/26/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: a693decfa8e2178069b005c129fa30188c577f2c
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83398800"
---
<!-- cSpell:ignore njray nanra vCPUs Proliant Sysplex IPLs DASDs LPARs ISPF Panvalet -->

# <a name="make-the-switch-from-mainframes-to-azure"></a>Assurer la transition d’ordinateurs mainframe vers Azure

Plateforme alternative permettant l’exécution d’applications mainframe classiques, Azure offre des capacités de stockage et de calcul hyperscale dans un environnement à haute disponibilité. Vous bénéficiez de la valeur et de l’agilité d’une plateforme cloud moderne sans les coûts associés à un environnement mainframe.

Cette section fournit des recommandations techniques pour assurer la transition d’une plateforme mainframe vers Azure.

![Ordinateur mainframe et Azure](../../_images/mainframe-migration/make-the-switch.png)

<!-- docsTest:ignore "vs. vCPUs" -->

## <a name="mips-and-vcpus"></a>MIPS et processeurs virtuels

Il n’existe pas de formule de mappage universelle qui permette de déterminer le nombre de processeurs virtuels nécessaires pour exécuter des charges de travail mainframe. Cependant, la métrique MIPS (million d’instructions par seconde) est souvent mappée en processeurs virtuels sur Azure. La métrique MIPS mesure la puissance de calcul globale d’un ordinateur mainframe en fournissant une valeur constante du nombre de cycles par seconde pour une machine donnée.

Si les besoins d’une petite organisation peuvent être inférieurs à 500 MIPS, une grande organisation aura généralement besoin de plus de 5 000 MIPS. Si l’on considère qu’un MIPS coûte 1 000 dollars, une grande organisation devra donc dépenser environ 5 millions de dollars par an pour déployer une infrastructure de 5 000 MIPS. Le coût estimé annuel d’un déploiement Azure type de cette envergure représente environ un dixième du coût d’une infrastructure MIPS. Pour plus de détails, consultez le tableau 4 du livre blanc intitulé [Demystifying Mainframe-to-Azure Migration](https://azure.microsoft.com/resources/demystifying-mainframe-to-azure-migration).

Un calcul précis des MIPS ramené en nombre de processeurs virtuels avec Azure dépend du type de processeur virtuel et de la charge de travail que vous exécutez. Cependant, certaines études comparatives constituent une bonne base pour estimer le nombre et le type de processeurs virtuels dont vous aurez besoin. Dernièrement, un benchmark HPE zREF est arrivé aux estimations suivantes :

- 288 MIPS par cœur Intel s’exécutant sur des serveurs HP Proliant pour des travaux (CICS) en ligne.

- 170 MIPS par cœur Intel pour des programmes de traitement par lots COBOL.

Ce guide donne une estimation de 200 MIPS par processeur virtuel pour le traitement en ligne et de 100 MIPS par processeur virtuel pour le traitement par lots.

> [!NOTE]
> Ces estimations sont susceptibles d’évoluer à mesure que de nouvelles séries de machines virtuelles sont mises à disposition dans Azure.

## <a name="high-availability-and-failover"></a>Haute disponibilité et basculement

Les systèmes mainframe offrent souvent un taux de disponibilité à cinq 9 (99,999 %) quand le couplage mainframe et Parallel Sysplex sont utilisés. Pourtant, les opérateurs système ont toujours besoin de prévoir des temps d’arrêt pour la maintenance et les chargements de programmes initiaux. Le taux de disponibilité réel est proche de deux ou trois 9, similaire aux serveurs Intel haut de gamme.

Par comparaison, Azure s’engage à travers des contrats de niveau de service (SLA) sur une disponibilité par défaut à plusieurs 9, optimisée par la réplication locale ou géographique des services.

Azure offre des garanties de disponibilité supplémentaires en répliquant les données à partir de plusieurs dispositifs de stockage, que ce soit localement ou dans d’autres régions géographiques. En cas de défaillance sur Azure, les ressources de calcul peuvent accéder aux données répliquées au niveau local ou régional.

Si vous utilisez des ressources PaaS (« platform as a service ») Azure, comme [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) et [Azure Cosmos Database](https://docs.microsoft.com/azure/cosmos-db/introduction), Azure peut gérer automatiquement les basculements. Si vous utilisez Azure IaaS (infrastructure as a service), le basculement s’appuie sur des fonctionnalités système spécifiques, comme les fonctionnalités SQL Server Always On, des instances de clustering de basculement et des groupes de disponibilité.

## <a name="scalability"></a>Extensibilité

En règle générale, les ordinateurs mainframe procèdent à un scale-up, tandis que les environnements cloud procèdent à un scale-out. Le scale-out des ordinateurs mainframe est possible moyennant une fonctionnalité de couplage, mais les coûts élevés en matériel et stockage font du scale-out une opération onéreuse sur un ordinateur mainframe.

La fonctionnalité de couplage effectue un calcul fortement couplé, alors que les fonctionnalités de scale-out d’Azure le sont faiblement. Le cloud peut procéder à un scale-up ou un scale-down pour répondre aux besoins spécifiques des utilisateurs. La puissance de calcul, le stockage et les services sont alors mis à l’échelle à la demande selon un modèle de facturation basée sur l’utilisation.

## <a name="backup-and-recovery"></a>Sauvegarde et récupération

Les clients dotés d’un ordinateur mainframe gèrent généralement des sites de récupération d’urgence ou font appel à un fournisseur de services mainframe indépendant pour les situations d’urgence. La synchronisation avec un site de récupération d’urgence s’effectue habituellement via des copies de données hors connexion. Dans les deux cas, les coûts sont élevés.

La géoredondance automatisée est également disponible via la fonctionnalité de couplage mainframe. Cette approche est coûteuse et est généralement réservée aux systèmes stratégiques. En revanche, Azure propose des options de [sauvegarde](https://docs.microsoft.com/azure/backup/backup-overview), de [récupération](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) et de [redondance](https://docs.microsoft.com/azure/storage/common/storage-redundancy) économiques et faciles à implémenter au niveau local ou régional ou via la géoredondance.

## <a name="storage"></a>Stockage

Pour bien comprendre le fonctionnement des ordinateurs mainframe, il convient de démêler plusieurs termes qui se chevauchent. Par exemple, le stockage central, la mémoire réelle, le stockage réel et le stockage principal renvoient tous à un dispositif de stockage relié directement au processeur mainframe.

Le matériel mainframe se compose de processeurs et de bien d’autres dispositifs, notamment des dispositifs de stockage à accès direct (DASD), des lecteurs de bande magnétique et plusieurs types de consoles utilisateur. Les bandes et les dispositifs DASD sont utilisés par les fonctions système et les programmes utilisateur.

Il existe différents types de dispositif de stockage physique pour les ordinateurs mainframe, à savoir :

- **Stockage central :** situé directement sur le processeur mainframe, il est aussi connu sous le nom de processeur ou de stockage réel.
- **Stockage auxiliaire :** indépendant de l’ordinateur mainframe, ce type de stockage englobe le stockage sur dispositif DASD et est également appelé stockage de pagination.

Le cloud offre tout un choix d’options flexibles et scalables, et vous ne paierez que les options dont vous avez besoin. [Stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction) offre un magasin d’objets hautement scalable pour les objets de données, un service de système de fichiers pour le cloud, un magasin de messagerie fiable et un magasin NoSQL. Les machines virtuelles bénéficient d’un stockage sur disque sécurisé et persistant grâce à des disques managés et non managés.

## <a name="mainframe-development-and-testing"></a>Développement et test sur ordinateur mainframe

L’un des principaux éléments moteurs des projets de migration d’ordinateur mainframe est l’aspect changeant du développement d’applications. Les organisations souhaitent un environnement de développement plus agile et plus réactif aux besoins métier.

En général, les ordinateurs mainframe disposent de partitions logiques distinctes (LPAR) pour le développement et le test, par exemple QA et LPAR intermédiaires. Les solutions de développement mainframe se composent de compilateurs (COBOL, PL/I, Assembler) et d’éditeurs. La solution la plus répandue est ISPF (Interactive System Productivity Facility). Elle est conçue pour le système d’exploitation z/OS qui s’exécute sur des ordinateurs mainframe IBM. On peut également citer RPF (ROSCOE Programming Facility) et les outils Computer Associates que sont CA Librarian et CA-Panvalet.

Sachant qu’il existe des compilateurs et des environnements d’émulation pour les plateformes x86, le développement et le test font le plus souvent partie des premières charges de travail à être migrées d’un ordinateur mainframe vers Azure. La disponibilité et l’utilisation généralisée d’[outils DevOps dans Azure](https://azure.microsoft.com/solutions/devops) ont pour effet d’accélérer la migration des environnements de développement et de test.

Dès que vous aurez développé et testé une solution sur Azure et qu’elle sera prête à être déployée sur l’ordinateur mainframe, vous devrez copier le code sur l’ordinateur mainframe et le compiler sur ce dernier.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Migration d’applications mainframe](./application-strategies.md)
