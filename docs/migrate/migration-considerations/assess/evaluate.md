---
title: Évaluer la préparation des charges de travail
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Un processus au sein d’une migration cloud qui se concentre sur les tâches de migration des charges de travail vers le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7df4792fda1436d822108dc20d422e6912a0709f
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74159880"
---
# <a name="evaluate-workload-readiness"></a>Évaluer la préparation des charges de travail

Cette activité est axée sur l’évaluation de la préparation d’une charge de travail à migrer vers le cloud. Au cours de cette activité, l’équipe d’adoption du cloud vérifie que toutes les ressources et les dépendances associées sont compatibles avec le modèle de déploiement et le fournisseur de cloud choisis. Au cours du processus, l’équipe documente les efforts requis pour [corriger](../migrate/remediate.md) les problèmes de compatibilité.

## <a name="evaluation-assumptions"></a>Hypothèses d’évaluation

La plupart du contenu traitant des principes du Framework d’adoption du cloud est indépendant des services cloud. Toutefois, le processus d’évaluation de la préparation doit être en grande partie spécifique à chaque plateforme cloud. Les instructions suivantes supposent que vous avez l’intention de migrer vers Azure. Elles supposent également l’utilisation d’Azure Migrate (également appelé Azure Site Recovery) pour les [activités de réplication](../migrate/replicate.md). Pour en savoir plus sur d’autres outils, consultez [Options de réplication](../migrate/replicate-options.md).

Cet article ne capture pas toutes les activités d’évaluation possibles. Il est supposé que chaque environnement et résultat métier dicteront des exigences spécifiques. Pour accélérer la création de ces exigences, le reste de cet article partage quelques activités d’évaluation courantes liées à l’évaluation des [infrastructures](#common-infrastructure-evaluation-activities), des [bases de données](#common-database-evaluation-activities) et des [réseaux](#common-network-evaluation-activities).

## <a name="common-infrastructure-evaluation-activities"></a>Activités courantes d’évaluation des infrastructures

- Configuration requise pour VMware : [Étudiez la configuration requise d’Azure Site Recovery pour VMware](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix).
- Configuration requise pour Hyper-V : [Étudiez la configuration requise d’Azure Site Recovery pour Hyper-V](https://docs.microsoft.com/azure/site-recovery/hyper-v-azure-support-matrix).

Veillez à documenter toutes les incohérences dans la configuration de l’hôte, la configuration des machines virtuelles répliquées, les exigences de stockage ou la configuration réseau.

## <a name="common-database-evaluation-activities"></a>Activités courantes d’évaluation des bases de données

- Documentez les objectifs de point de récupération et les objectifs de temps de récupération du déploiement de base de données actuel. Ceux-ci sont utilisés dans les [activités d’architecture](./architect.md) pour faciliter la prise de décision.
- Documentez toute exigence relative à la configuration de haute disponibilité. Pour plus d’informations sur la configuration requise pour SQL Server, consultez le [guide des solutions de haute disponibilité SQL Server](https://docs.microsoft.com/sql/sql-server/failover-clusters/high-availability-solutions-sql-server).
- Évaluez la compatibilité PaaS. Le [guide de migration des données Azure](https://datamigration.microsoft.com) mappe des bases de données locales à des solutions PaaS Azure compatibles, telles que [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) ou [Azure DB](https://docs.microsoft.com/azure/sql-database) pour [MySQL](https://docs.microsoft.com/azure/mysql), [PostgreSQL](https://docs.microsoft.com/azure/postgresql) ou [MariaDB](https://docs.microsoft.com/azure/mariadb).
- Lorsque la compatibilité PaaS est une option sans que cela nécessite de correction, consultez l’équipe responsable des [activités d’architecture](./architect.md). Les migrations PaaS peuvent produire des gains de temps et des réductions importantes dans le coût total de possession (TCO) de la plupart des solutions cloud.
- Lorsque la compatibilité PaaS est une option, mais qu’une correction est requise, consultez les équipes responsables des [activités d’architecture](./architect.md) et des [activités de correction](../migrate/remediate.md). Dans de nombreux scénarios, les avantages des migrations PaaS pour les solutions de base de données peuvent l’emporter sur l’augmentation du temps de correction.
- Documentez la taille et le taux de change de chaque base de données à migrer.
- Lorsque cela est possible, documentez toutes les applications ou autres ressources qui appellent chaque base de données.

> [!NOTE]
> La synchronisation de toute ressource consomme de la bande passante pendant les processus de réplication. Un piège très courant consiste à ignorer la consommation de bande passante requise pour maintenir la synchronisation des ressources entre le point de réplication et la mise en production. Les bases de données sont des consommatrices courantes de bande passante pendant les cycles de mise en production, et les bases de données avec des empreintes de stockage importantes ou un taux de change élevé sont particulièrement préoccupantes. Envisagez une approche de réplication de la structure de données, avec des mises à jour contrôlées avant les tests d’acceptation utilisateur (UAT) et la mise en production. Dans de tels scénarios, les alternatives aux Azure Site Recovery peuvent être plus appropriées. Pour plus d’informations, consultez le [guide de migration des données Azure](https://datamigration.microsoft.com).

## <a name="common-network-evaluation-activities"></a>Activités courantes d’évaluation des bases de données

- Calculez le stockage total de toutes les machines virtuelles à répliquer pendant les itérations menant à une mise en production.
- Calculez le taux de dérive ou de change du stockage pour toutes les machines virtuelles à répliquer pendant les itérations menant à une mise en production.
- Calculez les exigences en bande passante nécessaires pour chaque itération en additionnant le stockage total et la dérive.
- Calculez la bande passante inutilisée disponible sur le réseau actuel pour valider l’alignement par itération.
- Documentez la bande passante nécessaire pour atteindre la vélocité de migration prévue. Si une correction est requise pour fournir la bande passante nécessaire, avertissez l’équipe responsable des [activités de correction](../migrate/remediate.md).

> [!NOTE]
> Le stockage total influence directement les exigences en bande passante lors de la réplication initiale. Toutefois, la dérive du stockage se poursuit du point de réplication jusqu’à la mise en production. Cela signifie que la dérive a un effet cumulatif sur la bande passante disponible.

## <a name="next-steps"></a>Étapes suivantes

Une fois l’évaluation d’un système terminée, les sorties alimentent le développement d’une nouvelle [architecture cloud](./architect.md).

> [!div class="nextstepaction"]
> [Architecture de charges de travail avant la migration](./architect.md)
