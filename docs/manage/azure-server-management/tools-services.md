---
title: Outils et services de gestion de serveur Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Outils et services de gestion de serveur Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: dbb00a411eb7905ad557e1acdc2a98d4d03cff49
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221421"
---
# <a name="azure-server-management-tools-and-services"></a>Outils et services de gestion de serveur Azure

Comme décrit dans la [vue d’ensemble](./index.md) de cette section, la suite de services de gestion de serveur Azure couvre les sujets suivants :

- [Migrer](#migrate)
- [Sécuriser](#secure)
- [Protéger](#protect)
- [Surveiller](#monitor)
- [Configurer](#configure)
- [Gouverner](#govern)

Les sections suivantes décrivent en bref ces domaines de gestion et contiennent des liens vers du contenu détaillé sur les principaux services Azure qui les prennent en charge.

## <a name="migrate"></a>Migrer

Les services de migration peuvent vous aider à migrer vos charges de travail dans Azure. Pour une aide optimale, le service Azure Migrate commence par mesurer les performances du serveur local et évaluer l’aptitude à la migration. Une fois qu’Azure Migrate a terminé l’évaluation, vous pouvez utiliser [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) et [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview) pour migrer vos machines locales vers Azure.

## <a name="secure"></a>Sécuriser

[Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-intro) est une application de gestion de la sécurité complète. Grâce à son intégration à Security Center, vous pouvez rapidement évaluer l’état de conformité de la sécurité et des réglementations de votre environnement. Pour obtenir des instructions sur l’intégration de vos serveurs à Azure Security Center, consultez [Configurer les services de gestion Azure pour un abonnement](./onboard-at-scale.md#azure-security-center).

## <a name="protect"></a>Protéger

Pour protéger vos données, vous devez planifier la sauvegarde, la haute disponibilité, le chiffrement, l’autorisation et les problèmes opérationnels associés. Ces sujets étant largement traitées en ligne, nous allons nous concentrer sur la création d’un plan de continuité d’activité et reprise d’activité (BCDR). Nous inclurons des références vers de la documentation qui explique comment implémenter et déployer ce type de plan.

Quand vous créez des stratégies de protection des données, vous devez d’abord envisager de diviser vos applications de charge de travail en différents niveaux, car chaque niveau requiert généralement son propre plan de protection unique. Pour en savoir plus sur la conception d’applications qui doivent être résilientes, consultez [Conception d’applications résilientes pour Azure](https://docs.microsoft.com/azure/architecture/resiliency).

La protection des données la plus simple est la sauvegarde. Pour accélérer le processus de récupération en cas de perte du serveur, vous devez sauvegarder les données, mais également les configurations de serveur. La sauvegarde est un mécanisme efficace pour gérer une suppression accidentelle de données et les attaques de ransomware. [Sauvegarde Azure](https://docs.microsoft.com/azure/backup) peut vous aider à protéger vos données sur les serveurs exécutant Windows ou Linux locaux ou Azure. Pour plus d’informations sur les fonctionnalités de ce service et les guides pratiques, consultez la [documentation sur Sauvegarde Azure](https://docs.microsoft.com/azure/backup/backup-overview).

La récupération via la sauvegarde peut prendre beaucoup de temps. Le standard du secteur est généralement d’un jour. Si une charge de travail nécessite la continuité de l’activité en cas de défaillance matérielle ou de panne du centre de données, utilisez la réplication de données. [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) fournit une réplication continue de vos machines virtuelles, solution qui permet une perte de données minimale. Site Recovery prend également en charge plusieurs scénarios de réplication, tels que la réplication de machines virtuelles Azure entre deux régions Azure, entre des serveurs locaux et entre des sites locaux et Azure. Pour plus d’informations, consultez le [tableau complet de la réplication Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview#what-can-i-replicate).

Pour les données de votre serveur de fichiers, un autre service à prendre en compte est [Azure File Sync](https://docs.microsoft.com/azure/storage/files/storage-sync-files-planning). Ce service vous permet de centraliser les partages de fichiers de votre organisation dans Azure Files tout en préservant la flexibilité, le niveau de performance et la compatibilité d’un serveur de fichiers local. Pour utiliser ce service, suivez les instructions de déploiement d’Azure File Sync.

## <a name="monitor"></a>Surveiller

[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) fournit une vue de diverses ressources, telles que les applications, les conteneurs et les machines virtuelles. Il collecte également les données de plusieurs sources.

- Azure Monitor pour machines virtuelles ([insights](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview)) fournit une vue détaillée de l’intégrité des machines virtuelles, des tendances en matière de performances et des dépendances. Le service supervise l’intégrité du système d’exploitation de vos machines virtuelles Azure, de vos groupes de machines virtuelles identiques et des machines de votre environnement local.
- Log Analytics ([journaux d’activité](https://docs.microsoft.com/azure/azure-monitor/platform/data-collection#logs)) est une fonctionnalité d’Azure Monitor. Son rôle est central pour l’ensemble de la gestion Azure. Il sert de magasin de données pour l’analyse des journaux et pour de nombreux autres services Azure. Le langage de requête est riche et le moteur analytique fournit des informations sur le fonctionnement de vos applications et de vos ressources.
- Le [Journal d’activité Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) est également une fonctionnalité d’Azure Monitor. Il fournit un insight sur les événements de niveau abonnement qui se produisent dans Azure.

## <a name="configure"></a>Configuration

Plusieurs services appartiennent à cette catégorie. Ils peuvent vous aider à automatiser les tâches opérationnelles, à gérer les configurations des serveurs, à mesurer la conformité des mises à jour, à planifier les mises à jour et à détecter les modifications apportées à vos serveurs. Ces services sont essentiels à la prise en charge des opérations en cours.

- [Update Management](https://docs.microsoft.com/azure/automation/automation-update-management#viewing-update-assessments) automatise le déploiement des correctifs dans votre environnement, y compris le déploiement sur des instances de système d’exploitation qui s’exécutent en dehors d’Azure. Il prend en charge les systèmes d’exploitation Windows et Linux, et assure le suivi de la non-conformité et des principales vulnérabilités du système d’exploitation provoquées par des correctifs manquants.
- Les services [Change Tracking et Inventory](https://docs.microsoft.com/azure/automation/change-tracking) fournissent un insight sur les logiciels qui s’exécutent dans votre environnement et exposent toutes les modifications qui se sont produites.
- [Azure Automation](https://docs.microsoft.com/azure/automation/automation-intro) vous permet d’exécuter des scripts Python et PowerShell ou des runbooks pour automatiser des tâches dans votre environnement. Quand vous l’utilisez avec le [Runbook Worker hybride](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker), vous pouvez également étendre vos runbooks à vos ressources locales.
- [Azure Automation State Configuration](https://docs.microsoft.com/azure/automation/automation-dsc-overview) vous permet d’envoyer (push) des configurations DSC (Desired State Configuration) PowerShell directement à partir d’Azure. À son tour, DSC vous permet de superviser et de conserver les configurations de charge de travail et de système d’exploitation invité.

## <a name="govern"></a>Gouvernance

L’adoption du cloud et la migration vers ce dernier engendrent des défis de gestion et nécessitent un autre état d’esprit pour passer d’une charge de gestion opérationnelle à la supervision et à la gouvernance. Le Framework d’adoption du cloud pour Azure commence par la [gouvernance](../../govern/index.md). Il explique comment migrer vers le cloud, à quoi ressemble le parcours et qui doit être impliqué.

La conception de la gouvernance pour les organisations standard diffère souvent de la conception de la gouvernance pour les entreprises complexes. Pour en savoir plus sur les bonnes pratiques de gouvernance pour une organisation standard, consultez [Guide de gouvernance pour les entreprises standard](../../govern/guides/standard/index.md). Pour en savoir plus sur les bonnes pratiques de gouvernance pour une entreprise complexe, consultez [Guide de gouvernance pour les entreprises complexes](../../govern/guides/complex/index.md).

## <a name="billing-information"></a>Informations de facturation

Pour en savoir plus sur les tarifs des services de gestion Azure, consultez ces pages :

- [Azure Site Recovery](https://azure.microsoft.com/pricing/details/site-recovery)

- [Sauvegarde Azure](https://azure.microsoft.com/pricing/details/backup)

- [Azure Monitor](https://azure.microsoft.com/pricing/details/monitor)

- [Centre de sécurité Azure](https://azure.microsoft.com/pricing/details/security-center)

- [Service Azure Update Management](https://azure.microsoft.com/pricing/details/automation)

- [Services Azure Change Tracking et Inventory](https://azure.microsoft.com/pricing/details/automation)

- [Desired State Configuration](https://azure.microsoft.com/pricing/details/automation)

- [Service Azure Automation](https://azure.microsoft.com/pricing/details/automation)

- [Azure Policy](https://azure.microsoft.com/pricing/details/azure-policy)

- [Service Azure File Sync](https://azure.microsoft.com/pricing/details/storage/blobs)

> [!NOTE]
> La solution Azure Update Management est gratuite, mais il existe un coût réduit lié à l’ingestion des données. En règle générale, les 5 premiers Go par mois d’ingestion de données sont gratuits. Nous observons généralement que chaque machine utilise environ 25 Mo par mois. Ainsi, environ 200 machines par mois sont couvertes gratuitement. Pour chaque serveur supplémentaire, multipliez le nombre de serveurs supplémentaires par 25 Mo par mois. Multipliez le résultat par le coût de stockage pour la quantité totale de stockage nécessaire. [Les coûts de stockage sont disponibles ici](https://azure.microsoft.com/pricing/details/storage). Chaque serveur supplémentaire doit avoir un impact minime sur le coût.