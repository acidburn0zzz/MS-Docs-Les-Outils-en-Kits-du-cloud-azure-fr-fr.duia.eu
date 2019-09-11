---
title: Capacité réseau dépassée
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Les besoins en stockage dépassent la capacité réseau lors d’une migration.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: eb6a5adeac25293539edd5d97c816fad2865345c
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70836703"
---
# <a name="storage-requirements-exceed-network-capacity-during-a-migration-effort"></a>Les besoins en stockage dépassent la capacité réseau lors d’une migration

Lors d’une migration cloud, les ressources sont répliquées et synchronisées sur le réseau entre le centre de données existant et le cloud. Il n’est pas rare que les exigences de taille des données existantes de différentes charges de travail dépassent la capacité du réseau. Dans ce type de scénario, le processus de migration peut être radicalement ralenti ou, dans certains cas, complètement interrompu. Le guide qui suit étendra la portée du [guide de migration Azure](../azure-migration-guide/index.md) pour fournir une solution qui permet de contourner les limitations du réseau.

## <a name="general-scope-expansion"></a>Expansion de l’étendue générale

La majeure partie de cet effort nécessaire dans le cadre de cette expansion de l’étendue se produit au cours des processus de détermination des conditions préalables, d’évaluation et de migration.

## <a name="suggested-prerequisites"></a>Conditions préalables suggérées

**Valider les risques liés à la capacité du réseau :** [La rationalisation du patrimoine numérique](../../digital-estate/rationalize.md) est un prérequis fortement recommandé, en particulier s’il existe des problèmes de surcharge de la capacité réseau disponible. Lors de la rationalisation du patrimoine numérique, un [inventaire des ressources numériques](../../digital-estate/inventory.md) est collecté. Cet inventaire doit inclure les exigences de stockage existantes dans le patrimoine numérique. Comme indiqué dans [Risques de réplication : Physique de la réplication](../migration-considerations/migrate/replicate.md#replication-risks---physics-of-replication), cet inventaire peut être utilisé pour estimer la **taille totale des données de migration**, qui peut être comparée à la **bande passante de migration disponible** totale. Si cette comparaison n’est pas alignée avec le **temps nécessaire pour les changements dans l’entreprise**, cet article peut vous aider à accélérer la migration, en réduisant le temps nécessaire à la migration du centre de données.

**Transfert hors connexion de banques de données indépendantes :** Le diagramme ci-dessous présente des exemples de transferts de données en ligne et hors ligne avec Azure Data Box. Ces approches peuvent être utilisées pour envoyer des volumes importants de données vers le cloud avant la migration de la charge de travail. Dans un transfert de données hors connexion, les données source sont copiées sur une Azure Data Box, qui est ensuite physiquement livrée à Microsoft pour le transfert dans un compte de stockage Azure en tant que fichier ou objet blob. Ce processus peut être utilisé pour envoyer des données qui ne sont pas directement liées à une charge de travail spécifique, avant d’autres efforts de migration. Cela réduit la quantité de données qui doivent être expédiées sur le réseau, afin d’effectuer une migration respectant les contraintes réseau.

Cette approche peut être utilisée pour transférer des données HDFS, des sauvegardes, des archives, des serveurs de fichiers, des applications, etc. Les conseils techniques existants expliquent comment utiliser cette approche pour transférer des données à partir [d’un magasin HDFS](/azure/storage/blobs/data-lake-storage-migrate-on-premises-hdfs-cluster), de disques à l’aide de [SMB](/azure/databox/data-box-deploy-copy-data), [NFS](/azure/databox/data-box-deploy-copy-data-via-nfs), [REST](/azure/databox/data-box-deploy-copy-data-via-rest), ou du [service de copie de données](/azure/databox/data-box-deploy-copy-data-via-copy-service) vers Data Box.

Il existe également des [solutions de partenaires tiers](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) qui utilisent Azure Data Box pour une migration « Seed and Feed », où un volume important de données est déplacé lors d’un transfert hors connexion, mais est ensuite synchronisé à une échelle plus faible sur le réseau.

![Transferts de données en ligne et hors connexion avec Azure Data Box](../../_images/migration/databox.png)

## <a name="assess-process-changes"></a>Évaluer les changements de processus

Si les besoins de stockage d’une charge de travail (ou plusieurs) dépassent la capacité du réseau, vous pouvez toujours utiliser une Azure Data Box pour un transfert de données hors connexion.

La position générale de Microsoft est que la transmission réseau est l’approche conseillée, sauf si le réseau n’est pas disponible. Cette suggestion est due à la vitesse de transfert. Le transfert de données sur le réseau (même lorsque la bande passante est limitée) est généralement plus rapide que l’expédition physique de la même quantité de données à l’aide d’un mécanisme de transfert hors connexion, comme Data Box.

Si la connectivité à Azure est disponible, une analyse doit être effectuée avant d’utiliser Data Box, surtout si la migration de la charge de travail est sensible au temps. Data Box est recommandé uniquement lorsque le temps de transfert des données nécessaires dépasse le temps requis pour remplir, expédier et restaurer les données à l’aide de Data Box.

### <a name="suggested-action-during-the-assess-process"></a>Action suggérée pendant le processus d’évaluation

**Analyse de la capacité du réseau :** Lorsque les exigences de transfert de données liées aux charges de travail sont exposées à un risque de dépassement de la capacité du réseau, l’équipe d’adoption cloud ajoute une tâche d’analyse supplémentaire au processus d’évaluation, appelée analyse de la capacité du réseau. Au cours de cette analyse, un membre de l’équipe possédant une expertise en matière de réseau local et de connectivité réseau estime la quantité de capacité réseau disponible et le temps requis pour le transfert des données. Cette capacité disponible est alors comparée aux besoins de stockage de toutes les ressources à migrer pour la version actuelle. Si les besoins en matière de stockage dépassent la bande passante disponible, les ressources prenant en charge la charge de travail sont sélectionnées pour le transfert hors connexion.

> [!IMPORTANT]
> À la fin de l’analyse, le plan de version devra peut-être être mis à jour pour refléter le temps nécessaire à l’envoi, à la restauration et à la synchronisation des ressources à transférer hors connexion.

**Analyse de dérive :** Chaque ressource à transférer hors connexion doit être analysée pour déterminer la dérive du stockage et de la configuration. La dérive du stockage correspond à la quantité de modifications dans le stockage sous-jacent au fil du temps. La dérive de la configuration porte sur les modifications dans la configuration de la ressource au fil du temps. Du moment où le stockage est copié au moment où la ressource est promue en production, toute dérive peut être perdue. Si cette dérive doit être reflétée dans la ressource migrée, une forme de synchronisation est nécessaire entre la ressource locale et la ressource migrée. Elle doit être signalée pour être prise en compte lors de l’exécution de la migration.

## <a name="migrate-process-changes"></a>Migrer les changements de processus

Lorsque vous utilisez des mécanismes de transfert hors connexion, les [processus de réplication](../migration-considerations/migrate/replicate.md) ne sont probablement pas nécessaires. Toutefois, [des processus de synchronisation](../migration-considerations/migrate/replicate.md) peuvent toujours être requis. La compréhension des résultats de l’analyse de dérive effectuée au cours du processus d’évaluation informe les tâches requises lors de la migration, si une ressource est transférée hors connexion.

### <a name="suggested-action-during-the-migrate-process"></a>Action suggérée pendant le processus de migration

**Copie du stockage :** Cette approche peut être utilisée pour transférer des données HDFS, des sauvegardes, des archives, des serveurs de fichiers, des applications, etc. Les conseils techniques existants expliquent comment utiliser cette approche pour transférer des données à partir [d’un magasin HDFS](/azure/storage/blobs/data-lake-storage-migrate-on-premises-hdfs-cluster), de disques à l’aide de [SMB](/azure/databox/data-box-deploy-copy-data), [NFS](/azure/databox/data-box-deploy-copy-data-via-nfs), [REST](/azure/databox/data-box-deploy-copy-data-via-rest), ou du [service de copie de données](/azure/databox/data-box-deploy-copy-data-via-copy-service) vers Data Box.

Il existe également des [solutions de partenaires tiers](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) qui utilisent Azure Data Box pour une migration « Seed and Sync », où un volume important de données est déplacé lors d’un transfert hors connexion, mais est ensuite synchronisé à une échelle plus faible sur le réseau.

**Expédition de l’appareil :** Une fois les données copiées, l’appareil peut être [expédié à Microsoft](/azure/databox/data-box-deploy-picked-up). Une fois les données reçues et importées, elles sont disponibles dans un compte de stockage Azure.

**Restauration de la ressource :** [Vérifiez que les données](/azure/databox/data-box-deploy-picked-up#verify-data-upload-to-azure) sont disponibles dans le compte de stockage. Une fois vérifiées, les données peuvent être utilisées en tant qu’objets blob ou dans Azure Files. Si les données sont un fichier VHD/VHDX, le fichier peut être converti en disques managés. Ces disques managés peuvent ensuite être utilisés pour instancier une machine virtuelle, ce qui crée un réplica de la ressource locale d’origine.

**Synchronisation :** Si la synchronisation de la dérive est requise pour une ressource migrée, une des [solutions de partenaires tiers](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) peut être utilisée pour synchroniser les fichiers jusqu’à ce que la ressource soit restaurée.

## <a name="optimize-and-promote-process-changes"></a>Changements aux processus d’optimisation et de promotion

Les activités d’optimisation ne sont pas susceptibles d’être affectées par cette modification de l’étendue.

## <a name="secure-and-manage-process-changes"></a>Changements aux processus de sécurisation et de gestion

Les activités de sécurisation et de gestion ne sont pas susceptibles d’être affectées par cette modification de l’étendue.

## <a name="next-steps"></a>Étapes suivantes

Revenez à la [liste de vérification d’expansion d’étendue](./index.md) pour vous assurer que votre méthode de migration est entièrement alignée.

> [!div class="nextstepaction"]
> [Liste de contrôle d’expansion d’étendue](./index.md)
