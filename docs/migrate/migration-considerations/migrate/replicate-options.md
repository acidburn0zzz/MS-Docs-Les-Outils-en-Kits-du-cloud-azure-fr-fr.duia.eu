---
title: Options de réplication
description: Un processus au sein d’une migration cloud qui se concentre sur les tâches de migration des charges de travail vers le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: bf798a816d799ba856d8ea20b999de1240ac5284
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802138"
---
# <a name="replication-options"></a>Options de réplication

Avant toute migration, vous devez vous assurer que les systèmes principaux sont sécurisés et qu’ils continueront à s’exécuter sans problème. Tout temps d’arrêt perturbe les utilisateurs ou les clients, et coûte du temps et de l’argent. La migration n’est pas aussi simple que la désactivation des machines virtuelles locales et leur copie sur Azure. Les outils de migration doivent prendre en compte la réplication synchrone ou asynchrone pour s’assurer que les systèmes actifs peuvent être copiés sur Azure sans temps d’arrêt. Surtout, les systèmes doivent être maintenus au même niveau que leurs équivalents locaux. Vous souhaiterez peut-être tester les ressources migrées dans des partitions isolées dans Azure pour vous assurer que les charges de travail fonctionnent comme prévu.

Le contenu du Framework de l’adoption du cloud suppose qu’Azure Migrate (ou Azure Site Recovery) est l’outil le plus approprié pour la réplication des ressources dans le cloud. Toutefois, d’autres options sont envisageables. Cet article présente ces options pour faciliter la prise de décisions.

## <a name="azure-site-recovery-also-known-as-azure-migrate"></a>Azure Site Recovery (également appelé Azure Migrate)

[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) orchestre et gère la récupération d’urgence pour les machines virtuelles Azure, les machines virtuelles locales et les serveurs physiques. Vous pouvez également utiliser Site Recovery pour gérer la migration de machines locales et d’autres fournisseurs de services cloud vers Azure. Répliquez des machines locales vers Azure ou des machines virtuelles Azure vers une région secondaire. Basculez ensuite la machine virtuelle du site principal vers le site secondaire, puis terminez le processus de migration. Grâce à Azure Site Recovery, vous pouvez réaliser différents scénarios de migration :

- **Migrer de l’environnement local vers Azure.** Migrez des machines virtuelles VMware, des machines virtuelles Hyper-V et des serveurs physiques locaux vers Azure. Pour ce faire, effectuez presque les mêmes étapes que pour une récupération d’urgence complète. Ne basculez simplement pas les machines virtuelles d’Azure vers le site local.
- **Migrer entre des régions Azure.** Migrez des machines virtuelles Azure d’une région Azure vers une autre. Une fois que la migration est terminée, configurez la récupération d’urgence des machines virtuelles Azure dans la région secondaire vers laquelle vous avez migré.
- **Migrer à partir d’un autre cloud vers Azure.** Vous pouvez migrer vos instances de calcul configurées sur d’autres fournisseurs de cloud vers des machines virtuelles Azure. Site Recovery gère ces instances de la même façon que les serveurs physiques lors de la migration.

![Azure Site Recovery](../../../_images/migrate/asr-replication-image.png)
*Azure Site Recovery déplaçant des ressources vers Azure ou d’autres clouds*

Une fois que vous avez évalué les infrastructures locale et cloud pour la migration, Azure Site Recovery contribue à votre stratégie de migration en répliquant des machines locales. En suivant les étapes simples ci-dessous, vous pouvez configurer la migration de machines virtuelles locales, de serveurs physiques et d’instances de machine virtuelle cloud vers Azure :

- Assurez-vous que la configuration requise est respectée.
- Préparez les ressources Azure.
- Préparez les instances de machine virtuelle locale ou de cloud pour la migration.
- Déployez un serveur de configuration.
- Activez la réplication des machines virtuelles.
- Testez le basculement pour vérifier que tout fonctionne bien.
- Exécutez un basculement unique vers Azure.

## <a name="azure-database-migration-service"></a>Azure Database Migration Service

Ce service aide à réduire la complexité de votre migration cloud en utilisant un seul service complet plutôt que plusieurs outils. [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview) est une solution fluide et de bout en bout qui permet de migrer des bases de données SQL Server locales vers le cloud. Il s’agit d’un service complètement managé conçu pour permettre les migrations transparentes de plusieurs sources de base de données vers des plateformes de données Azure avec un temps d’arrêt minimal. Il intègre certaines des fonctionnalités des outils et services existants, offrant ainsi aux clients une solution complète et hautement disponible.

Le service utilise l’Assistant Migration de données pour générer des rapports d’évaluation qui fournissent des suggestions concernant les modifications requises avant d’effectuer une migration. Libre à vous d’effectuer toute correction requise. Lorsque vous êtes prêt à commencer le processus de migration, Azure Database Migration Service effectue toutes les étapes associées. Vous pouvez lancer vos projets de migration et ne plus vous en occuper, car vous savez que le processus s’appuie sur les bonnes pratiques déterminées par Microsoft.

## <a name="next-steps"></a>Étapes suivantes

Une fois la réplication terminée, les [activités de préproduction](./stage.md) peuvent commencer.

> [!div class="nextstepaction"]
> [Activités de préproduction pendant une migration](./stage.md)
