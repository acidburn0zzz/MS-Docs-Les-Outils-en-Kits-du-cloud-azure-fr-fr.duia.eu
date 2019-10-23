---
title: Vue d’ensemble de la migration d’ordinateurs mainframe
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migrez des applications d’environnements mainframe vers Azure, infrastructure fiable, hautement disponible et scalable pour les systèmes qui s’exécutent sur des ordinateurs mainframe.
author: njray
ms.author: v-nanra
ms.date: 12/27/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 88f844cb0a80971457beeb8814a109d70bb5d814
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547936"
---
# <a name="mainframe-migration-overview"></a>Vue d’ensemble de la migration d’ordinateurs mainframe

De nombreuses entreprises et organisations ont beaucoup à gagner lorsqu’elles migrent tout ou partie de leurs charges de travail, applications et bases de données mainframe vers le cloud. Azure offre des fonctionnalités de type mainframe à l’échelle du cloud, sans les inconvénients des ordinateurs mainframe.

En général, le terme mainframe désigne un système informatique volumineux, mais la majorité des ordinateurs mainframe actuellement déployés sont des serveurs IBM System Z ou des systèmes IBM compatibles avec les connecteurs et exécutant MVS, DOS, VSE, OS/390 ou z/OS. Les systèmes mainframe sont toujours utilisés dans de nombreux secteurs d’activité afin d’exécuter des systèmes d’informations vitales. Ils ont leur place dans des scénarios très spécifiques, tels que les grands environnements informatiques traitant de gros volumes de transactions.

La migration vers le cloud permet aux entreprises de moderniser leur infrastructure. Avec les services cloud, vous pouvez proposer des applications mainframe, et la valeur qu’elles offrent, sous forme de charge de travail dès que votre organisation en a besoin. De nombreuses charges de travail peuvent être transférées vers Azure suite à quelques modifications mineures du code (mettre à jour le nom des bases de données, par exemple). Vous pouvez migrer des charges de travail plus complexes à l’aide d’une approche en phases.

La plupart des entreprises classées au Fortune 500 exécutent déjà leurs charges de travail critiques sur Azure. Les avantages financiers significatifs qu’offre Azure motivent de nombreux projets de migration. En général, les entreprises commencent par migrer les charges de travail de développement et de test vers Azure, puis enchaînent avec les services DevOps, la messagerie et la récupération d’urgence en tant que service.

## <a name="intended-audience"></a>Public concerné

Ce guide s’adresse à vous si vous envisagez une migration ou l’ajout de services cloud optionnels à votre environnement informatique.

Ces conseils aident les organisations informatiques à se lancer dans la conversation de migration. Il se peut que vous connaissiez mieux Azure et les infrastructures basées sur le cloud que les ordinateurs mainframe. Ce guide commence donc par présenter le fonctionnement des ordinateurs mainframe avant d’aborder les différentes stratégies permettant d’identifier les éléments à migrer et les étapes de migration.

## <a name="mainframe-architecture"></a>Architecture mainframe

Les ordinateurs mainframe ont été conçus à la fin des années 1950 en tant que serveurs de montée en puissance pour exécuter un grand nombre de transactions en ligne et le traitement par lots. C’est pourquoi les ordinateurs mainframe disposent de logiciels pour les formulaires de transactions en ligne (parfois appelées les écrans verts) et de systèmes d’entrée/sortie hautes performances pour traiter des lots.

Les ordinateurs mainframe ont la réputation d’être extrêmement fiables et disponibles, et sont connus pour leur capacité à exécuter des transactions en ligne et des traitements par lots très volumineux. Une transaction provient d’un élément de traitement initié par une demande unique, généralement générée par un utilisateur sur un terminal. Les transactions peuvent également provenir de plusieurs sources, y compris des pages web, des stations de travail à distance et des applications dans d’autres systèmes d’information. Une transaction peut également être déclenchée automatiquement à une heure donnée, comme le montre l’illustration suivante.

![Composants d’une architecture mainframe IBM classique](../../_images/mainframe-migration/mainframe-architecture.png)

Une architecture mainframe IBM classique inclut généralement ces composants :

- **Systèmes frontaux :** Les utilisateurs peuvent initier des transactions à partir de terminaux, de pages web ou de stations de travail à distance. Les applications mainframe affichent souvent des interfaces utilisateur personnalisées qui peuvent être conservées après la migration vers Azure. Les émulateurs de terminaux sont toujours utilisés pour accéder aux applications mainframe. Ils sont également appelés des terminaux à écran vert.

- **Couche Application :** Les ordinateurs mainframe incluent généralement un système de contrôle des informations client (CICS), une suite de gestion des transactions majeure pour ordinateurs mainframe IBM z/OS (souvent utilisée avec IBM Information Management System, IMS) et un gestionnaire de transactions utilisant les messages. Les systèmes de traitement par lots gèrent les mises à jour de données à débit élevé pour de gros volumes d’enregistrements de compte.

- **Code :** Les langages de programmation utilisés par les ordinateurs mainframe incluent COBOL, Fortran, PL/I et Natural. Job control language (JCL) est utilisé pour travailler avec z/OS.

- **Couche Base de données :** Le système de gestion de base de données relationnelle (SGBDR) courant pour z/OS est IBM DD2. Il gère des structures de données appelées *dbspaces*, qui contiennent une ou plusieurs tables et sont affectées à des pools de stockage d’ensembles de données physiques appelés *dbextents*. Il existe deux composants majeurs des bases de données : le répertoire qui identifie les emplacements des données dans les pools de stockage et le journal qui contient un enregistrement des opérations effectuées sur la base de données. Différents formats de fichiers plats sont pris en charge pour les données. Le système DB2 pour z/OS utilise généralement des jeux de données avec la méthode VSAM (Virtual Storage Access Method) pour stocker les données.

- **Niveau Gestion :** Les ordinateurs mainframe IBM comportent des logiciels de planification tels que TWS-OPC, des outils de gestion des impressions et des sorties (comme CA-SAR et SPOOL) et un système de contrôle du code source. Le contrôle des accès sécurisé pour z/OS est géré par la fonctionnalité de contrôle des accès aux ressources (RACF). Un gestionnaire de bases de données fournit l’accès aux données dans la base de données et s’exécute dans sa propre partition dans un environnement z/OS.

- **Partition logique (LPAR) :** Les partitions logiques (LPAR) sont utilisées pour diviser les ressources de calcul. Un ordinateur mainframe physique est divisé en plusieurs partitions logiques.

- **z/OS :** Un système d’exploitation 64 bits est couramment utilisé pour les ordinateurs mainframe IBM.

Les systèmes IBM utilisent un moniteur transactionnel (comme CICS) pour effectuer le suivi de tous les aspects des transactions commerciales et les gérer. CICS gère le partage des ressources, l’intégrité des données et les priorités d’exécution. CICS autorise les utilisateurs, alloue les ressources et transmet les requêtes de base de données issues de l’application vers un gestionnaire de bases de données comme IBM DB2.

Pour une configuration plus précise, CICS est couramment utilisé avec IMS/TM (anciennement IMS/Data Communications ou IMS/DC). IMS a été conçu pour réduire la redondance des données en conservant une copie unique des données. Cet outil jour le rôle de moniteur transactionnel dans CICS en maintenant un état tout au long du processus et en enregistrant des fonctions d’entreprise dans un magasin de données.

## <a name="mainframe-operations"></a>Opérations mainframe

Voici quelques opérations mainframe classiques :

- **En ligne :** Les charges de travail incluent le traitement transactionnel, la gestion des bases de données et les connexions. Elles sont souvent implémentées à l’aide d’IBM DB2, de CICS et des connecteurs z/OS.

- **Par lots :** Les travaux sont exécutés sans intervention de l’utilisateur, et suivent généralement des intervalles réguliers (chaque matin, par exemple). Les traitements par lots peuvent être exécutés sur des systèmes Windows ou Linux à l’aide d’un émulateur JCL, tels les logiciels Micro Focus Enterprise Server ou BMC Control-M.

- **Job control language (JCL) :** JCL spécifie les ressources nécessaires pour traiter des tâches par lots. JCL communique ces informations à z/OS via un ensemble d’instructions de contrôle du travail. Le langage JCL de base contient six instructions types : JOB, ASSGN, DLBL, EXTENT, LIBDEF et EXEC. Un travail peut contenir plusieurs instructions EXEC (étapes), et chaque étape peut contenir plusieurs instructions LIBDEF, ASSGN, DLBL et EXTENT.

- **Chargement du programme initial :**  Cette opération fait référence au chargement d’une copie du système d’exploitation à partir d’un disque vers le stockage réel d’un processeur où elle est exécutée. Les chargements du programme initial sont utiles pour récupérer après les temps d’arrêt. Le chargement du programme initial correspond au démarrage du système d’exploitation sur les machines virtuelles Windows ou Linux.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Mythes et réalités](./myths-and-facts.md)
