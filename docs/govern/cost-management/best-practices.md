---
title: Coûts et dimensionnement des ressources Azure
description: Utilisez le Cloud Adoption Framework pour Azure afin de découvrir les bonnes pratiques en matière d’évaluation des coûts et de dimensionnement des ressources dans Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 237ec750ddc8be3614d686c325458f12e9b0f5d9
ms.sourcegitcommit: bd9872320b71245d4e9a359823be685e0f4047c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83862362"
---
<!-- docsTest:ignore ARO -->

# <a name="best-practices-for-costing-and-sizing-resources-hosted-in-azure"></a>Meilleures pratiques pour le calcul des coûts et le dimensionnement des ressources hébergées dans Azure

Même si la gouvernance est un élément important, la gestion des coûts est un thème récurrent au niveau de l’entreprise. En optimisant et en gérant les coûts, vous pouvez garantir la réussite à long terme de votre environnement Azure. Il est essentiel que toutes les équipes (telles que les équipes des finances, de gestion et de développement des applications) comprennent les coûts associés et les réexaminent régulièrement.

> [!IMPORTANT]
> Les meilleures pratiques et opinions décrites dans cet article sont basées sur les fonctionnalités de la plateforme et du service disponibles dans Azure au moment de la rédaction. Les fonctionnalités et les capacités changent au fil du temps. Toutes les recommandations ne s’appliquent pas à votre déploiement et vous devez donc choisir ce qui convient le mieux à votre situation.

## <a name="best-practices-by-team-and-accountability"></a>Meilleures pratiques par équipe et responsabilité

Au sein de l'entreprise, la gestion des coûts relève d'une fonction de gouvernance et d'exploitation cloud. En matière de gestion des coûts, toutes les décisions entraînent une modification des ressources prenant en charge une charge de travail. Lorsque ces modifications ont un impact sur l’architecture d’une charge de travail, des considérations supplémentaires s'imposent pour réduire l’impact sur les utilisateurs finaux et les fonctions commerciales. L’équipe d’adoption cloud qui a configuré ou développé cette charge de travail sera probablement responsable de mener à bien ces types de modifications.

- **La catégorisation est essentielle à toute la gouvernance.** Assurez-vous que toutes les charges de travail et toutes les ressources suivent des [conventions d’attribution de noms et de balisage appropriées](../../ready/azure-best-practices/naming-and-tagging.md) et [appliquez les conventions de catégorisation à l’aide d’Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/govern-tags).
- **Identifiez les opportunités de taille adaptée.** Passez en revue l’utilisation actuelle des ressources et les exigences en matière de performances dans l’environnement.
- **Redimensionner :** Modifiez chaque ressource pour utiliser la plus petite instance ou référence SKU capable de prendre en charge les exigences de performances de chaque ressource.
- **Mise à l’échelle horizontale ou verticale.** L’utilisation de plusieurs petites instances peut offrir un parcours de mise à l’échelle plus simple qu’avec une seule instance de plus grande taille. Cela permet l’automatisation de la mise à l’échelle, qui favorise l’optimisation des coûts.

## <a name="operational-cost-management-best-practices"></a>Meilleures pratiques en matière de gestion des coûts opérationnels

Les meilleures pratiques suivantes sont généralement mises en œuvre par un membre de l'équipe de gouvernance ou des opérations cloud, conformément aux processus de mise à jour corrective et autres processus de maintenance planifiés. Ces meilleures pratiques s'articulent autour de conseils pratiques présentés plus loin dans cet article.

- **La catégorisation est essentielle à toute la gouvernance :** Assurez-vous que toutes les charges de travail et toutes les ressources suivent des [conventions d’attribution de noms et de balisage appropriées](../../ready/azure-best-practices/naming-and-tagging.md) et [appliquez les conventions de catégorisation à l’aide d’Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/govern-tags).
- **Identifiez les opportunités de taille adaptée :** Passez en revue l’utilisation actuelle des ressources et les exigences en matière de performances de l’environnement pour identifier les ressources sous-exploitées pendant un certain laps de temps (généralement plus de 90 jours).
- **Adapter les références SKU approvisionnées :** Modifiez la ressource sous-exploitée pour utiliser la plus petite instance ou référence SKU capable de prendre en charge les exigences de performances de chaque ressource.
- **Arrêt automatique pour les machines virtuelles :** Lorsqu’une machine virtuelle n’est pas utilisée de façon constante, envisagez son arrêt automatique. La machine virtuelle ne sera pas supprimée ni désaffectée, mais elle cessera de consommer des coûts de calcul et de mémoire jusqu’à ce qu’elle soit redémarrée.
- **Arrêt automatique de toutes les ressources hors production :** Si une machine virtuelle relève d’un environnement hors production, environnement de développement notamment, établissez une stratégie d’arrêt automatique pour réduire les coûts non utilisés. Dans la mesure du possible, utilisez Azure DevTest Labs pour proposer des options en libre-service et permettre aux développeurs d'être responsables des coûts.
- **Arrêter et désactiver les ressources non utilisées :** Oui, nous le disons bien deux fois. Si une ressource n’a pas été utilisée pendant plus de 90 jours et n’a pas d’exigence claire d’activité, désactivez-la. Plus important encore, si une machine a été arrêtée pendant plus de 90 jours, déprovisionnez et supprimez cette ressource. Vérifiez que toutes les stratégies de conservation des données sont respectées grâce à des mécanismes de sauvegarde ou autres.
- **Nettoyer les disques orphelins :** Supprimez le stockage inutilisé, en particulier le stockage des machines virtuelles qui n’est plus attaché aux machines virtuelles.
- **Adapter la redondance :** Si la ressource ne nécessite pas un haut degré de redondance, supprimez le stockage géoredondant.
- **Ajuster les paramètres de mise à l’échelle automatique :** Le surveillance opérationnelle permet de révéler les modèles d'utilisation de différentes ressources. Lorsque ces modèles d’utilisation sont mappés aux paramètres utilisés pour piloter les comportements de mise à l’échelle automatique, il est courant pour l’équipe des opérations d’ajuster les paramètres de mise à l’échelle automatique afin de répondre à la demande saisonnière et/ou aux modifications apportées aux allocations de budget. Consultez les meilleures pratiques en matière de gestion des coûts de charge de travail pour prendre connaissance de précautions importantes.

## <a name="workload-cost-management-best-practices"></a>Meilleures pratiques en matière de gestion des coûts de charge de travail

Avant de procéder à des modifications architecturales, consultez le responsable technique de la charge de travail. Pour faciliter l'examen de la charge de travail, utilisez [Microsoft Azure Well-Architected Review](https://docs.microsoft.com/assessments/?id=azure-architecture-review) et [Microsoft Azure Well-Architected Framework](https://docs.microsoft.com/azure/architecture/framework) afin de d'orienter les décisions liées aux types de modifications architecturales suivants.

- **Azure App Service.** Vérifiez les exigences de production pour les plans App Service Premium. À défaut de comprendre les besoins de l’entreprise pour une charge de travail et la configuration des ressources sous-jacentes, il est difficile de déterminer si un niveau de service Premium est nécessaire.
- **Mise à l’échelle horizontale ou verticale.** L’utilisation de plusieurs petites instances peut offrir un parcours de mise à l’échelle plus simple qu’avec une seule instance de plus grande taille. Cela permet l’automatisation de la mise à l’échelle, qui favorise l’optimisation des coûts. Avant de procéder à la mise à l'échelle horizontale d'une charge de travail, l'équipe technique doit vérifier que l'application est idempotente. Dans un premier temps, la l'échelle horizontale peut nécessiter des modifications en termes de code et de configuration des différentes couches de l’application.
- **Mise à l’échelle automatique.** Activez la mise à l’échelle automatique sur tous les services d’application pour autoriser un plus petit nombre de machines virtuelles facilement extensibles. L’activation de la mise à l’échelle automatique répond à la même exigence idempotente, ce qui requiert une compréhension de l’architecture de la charge de travail. Avant toute modification opérationnelle liée à la mise à l'échelle horizontale ou à la mise à l'échelle automatique, l'équipe d'adoption doit approuver la charge de travail et les ressources sous-jacentes.
- **Implémenter des technologies serverless :** Les charges de travail de machine virtuelle sont souvent migrées « en l’état » afin d’éviter les temps d’arrêt. Souvent les machines virtuelles peuvent héberger des tâches intermittentes, à exécution rapide ou très lente. Par exemple, des machines virtuelles qui exécutent des tâches planifiées, comme un planificateur de tâches Windows ou des scripts PowerShell. Lorsque ces tâches ne sont pas en cours d’exécution, vous absorbez néanmoins les coûts de machine virtuelle et de stockage sur disque. Après la migration, envisagez de réorganiser les couches de la charge de travail sur des technologies serverless comme Azure Functions ou Azure Batch.

## <a name="actionable-best-practices"></a>Bonnes pratiques à utiliser

Le reste de cet article présente des exemples tactiques de meilleures pratiques opérationnelles qu’une équipe de gouvernance ou d'opérations cloud peut suivre afin d'optimiser les coûts au sein de l’entreprise.

## <a name="before-adoption"></a>Avant l’adoption

Avant de déplacer vos charges de travail vers le cloud, estimez le coût mensuel de leur exécution dans Azure. La gestion proactive des coûts liés au cloud vous permet de respecter votre budget de charges d’exploitation. Les meilleures pratiques de cette section vous aident à estimer les coûts et à effectuer le dimensionnement adapté pour les machines virtuelles et le stockage avant de déployer une charge de travail dans le cloud.

## <a name="best-practice-estimate-monthly-workload-costs"></a>Bonne pratique : estimer les coûts mensuels de la charge de travail

Pour prévoir votre facture mensuelle pour les ressources Azure, vous pouvez utiliser différents outils.

<!-- TODO: Change "input costs" -->
- **Calculatrice de prix Azure :** Sélectionnez les produits que vous souhaitez estimer, par exemple les machines virtuelles et le stockage, puis entrez les coûts dans la calculatrice pour créer une estimation.

    ![Calculatrice de prix Azure](../../migrate/azure-best-practices/media/migrate-best-practices-costs/pricing.png) _Calculatrice de prix Azure_

- **Azure Migrate :** Pour estimer les coûts, vous devez passer en revue et considérer toutes les ressources requises pour exécuter vos charges de travail dans Azure. Pour obtenir ces données, vous créez l’inventaire de vos ressources, y compris les serveurs, les machines virtuelles, les bases de données et le stockage. Vous pouvez utiliser Azure Migrate pour collecter ces informations.
  - Azure Migrate détecte et évalue votre environnement local afin de fournir un inventaire.
  - Azure Migrate peut mapper et afficher des dépendances entre les machines virtuelles pour vous donner une vision complète.
  - Une évaluation Azure Migrate contient le coût estimé.
    - **Calcul des coûts :** selon la taille de machine virtuelle Azure recommandée lorsque vous créez une évaluation, Azure Migrate utilise les API de facturation Azure pour calculer l’estimation des coûts mensuels de machine virtuelle. Cette estimation tient compte du système d’exploitation, de Software Assurance, des instances réservées, de la durée de fonctionnement de machine virtuelle, de l’emplacement et des paramètres de devise. Elle agrège le coût de toutes les machines virtuelle incluses dans l’évaluation pour calculer le coût de calcul mensuel total.
    - **Coût de stockage :** Azure Migrate calcule le coût de stockage mensuel total en additionnant le coût de stockage de toutes les machines virtuelles incluses dans l’évaluation. Vous calculez le coût de stockage mensuel d’une machine en additionnant le coût mensuel de tous les disques qui lui sont attachés.

    ![Azure Migrate](../../migrate/azure-best-practices/media/migrate-best-practices-costs/assess.png)
    _Évaluation Azure Migrate_

**En savoir plus :**

- Utiliser la [calculatrice de tarification Azure](https://azure.microsoft.com/pricing/calculator).
- Consultez la [vue d’ensemble d’Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview).
- En savoir plus sur les [évaluations Azure Migrate](https://docs.microsoft.com/azure/migrate/concepts-assessment-calculation).
- En savoir plus sur [Azure Database Migration Service](https://docs.microsoft.com/azure/dms/dms-overview).

## <a name="best-practice-right-size-vms"></a>Bonne pratique : redimensionner des machines virtuelles

Vous avez le choix entre différentes options lorsque vous déployez des machines virtuelles Azure pour prendre en charge les charges de travail. Chaque type de machine virtuelle possède des fonctionnalités spécifiques et différentes combinaisons d’UC, mémoire et disques. Les machines virtuelles sont regroupées comme indiqué ci-dessous :

| Type | Détails | Utilisation |
|---|---|---|
| **À usage général** | Ratio processeur/mémoire équilibré. | Convient pour le test et le développement, les bases de données de petite à moyenne taille. | Serveurs web de trafic faible à moyen. |
| **Optimisé pour le calcul** | Ratio processeur/mémoire élevé. | Convient pour les serveurs web au trafic de moyen volume, les appliances réseau, les processus de traitement par lots et les serveurs d’applications. |
| **Optimisé pour la mémoire** | Ratio mémoire/processeur élevé. | Convient pour les bases de données relationnelles, les caches de taille moyenne à grande et l’analytique en mémoire. |
| **Optimisé pour le stockage** | Débit de disque et E/S élevés. | Convient pour les bases de données NoSQL, SQL et Big Data. |
| **Optimisé pour le GPU** | Machines virtuelles spécialisées. Un ou plusieurs GPU. | Retouche vidéo et graphique avancée. |
| **Hautes performances** | Processeur plus rapide et plus puissant. Machines virtuelles avec interfaces réseau haut débit en option (RDMA). | Applications hautes performances critiques. |

- Il est important de comprendre les différences de prix entre ces machines virtuelles et les effets à long terme sur le budget.
- Chaque type est associé à plusieurs gammes de machines virtuelles.
- En outre, lorsque vous sélectionnez une machine virtuelle dans une gamme, vous pouvez uniquement mettre à l’échelle la machine virtuelle au sein de cette gamme. Par exemple, un modèle DSv2\_2 peut évoluer en DSv2\_4, mais pas vers une autre gamme, comme Fsv2\_2.

**En savoir plus :**

- En savoir plus sur les [types de machines virtuelles](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) et leur dimensionnement, et adaptez leur taille à leur type.
- Planifiez le [dimensionnement des machines virtuelles](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs).
- Examinez un [exemple d’évaluation de la société fictive Contoso](../../plan/contoso-migration-assessment.md).

## <a name="best-practice-select-the-right-storage"></a>Bonne pratique : sélectionner le stockage approprié

Le paramétrage et la gestion de stockage local (SAN ou NAS) et des réseaux qui les prennent en charge peuvent s’avérer coûteux et fastidieux. Les données (de stockage) de fichier sont généralement migrées vers le cloud pour simplifier les tâches opérationnelles et de gestion. Microsoft fournit plusieurs options pour déplacer des données vers Azure, et vous devez prendre des décisions concernant ces options. Choisir le type de stockage approprié pour les données de votre entreprise peut vous faire économiser plusieurs milliers d’euros chaque mois. Tenez compte des points suivants :

- Les données auxquelles vous n’accédez pas souvent et qui ne sont pas vitales pour l’entreprise ne doivent pas forcément être placées sur le stockage le plus coûteux.
- À l’inverse, les données critiques pour l’entreprise doivent se trouver sur les options de stockage de niveau supérieur.
- Lors de la planification de l’adoption, effectuez un inventaire des données et classez-les par ordre d’importance, afin de les mapper vers le stockage le plus approprié. Tenez compte du budget et des coûts, ainsi que des performances. Le coût ne doit pas nécessairement être le principal facteur de prise de décision. L’option la moins coûteuse peut exposer la charge de travail à des pertes de performances et à moins de disponibilité.

### <a name="storage-data-types"></a>Types de données de stockage

Azure fournit différents types de données de stockage.

<!-- markdownlint-disable MD033 -->

| Type de données | Détails | Usage |
| ---|---|---|
| **Objets blob** | Optimisé pour stocker de grandes quantités d’objets non structurées, comme des données texte ou binaires. | Accéder aux données depuis n’importe où via HTTP/HTTPS. <br><br> Utiliser cette option pour les scénarios d’accès aléatoire et de diffusion en continu. Par exemple, pour envoyer des images et des documents directement vers un navigateur, diffusez la vidéo et l’audio, et stockez les données de récupération d’urgence et de sauvegarde. |
| **Fichiers** | Partages de fichiers managés accessibles via SMB 3.0. | Utiliser lors de la migration des partages de fichiers locaux et pour fournir plusieurs connexions/accès aux données de fichiers. |
| **Disques** | Basé sur les objets blob de pages. <br><br> Type de disque (vitesse) : HDD Standard, SSD Standard, SSD Premium ou ultra disques. <br><br> Gestion du disque : non managé (vous gérez les paramètres de disque et le stockage) ou managé (vous sélectionnez le type de disque et Azure gère le disque pour vous). | Utiliser des disques Premium pour les machines virtuelles. Utiliser des disques managés pour la gestion simple et la mise à l’échelle. |
| **Files d’attente** | Stocker et récupérer un grand nombre de messages accessibles via des appels authentifiés (HTTP ou HTTPS). | Connecter des composants d’application à la file d’attente asynchrone des messages. |
| **Tables** | Tables de stockage. | Désormais inclus dans l’API Table d’Azure Cosmos DB. |

<!--markdownlint-enable MD033 -->

### <a name="access-tiers"></a>Niveaux d’accès

Le stockage Azure propose différentes options permettant d’accéder aux données d’objets blob de blocs. En sélectionnant le niveau d’accès approprié, vous pouvez stocker vos données d’objets blob de blocs de manière plus économique.

<!-- markdownlint-disable MD033 -->

| Niveau d’accès | Détails | Usage |
| --- | --- | --- |
| **Chaud** | Coûts de stockage supérieurs, coûts d'accès et de transaction inférieurs <br><br> Il s’agit du niveau d’accès par défaut. | Pour les données en cours d’utilisation qui sont fréquemment sollicitées. |
| **Froid** | Coûts de stockage inférieurs, coûts d'accès et de transaction supérieurs. <br><br> Stockage minimal de 30 jours. | Stockage à court terme : les données sont disponibles mais sollicitées rarement. |
| **Archive** | Utilisé pour les objets blob de blocs. <br><br> Option la plus économique pour le stockage. Coûts de stockage les plus faibles, coûts d'accès et de transaction les plus élevés. | Utilisez pour des données qui peuvent tolérer plusieurs heures de latence de récupération et restent dans le niveau archive pendant au moins 180 jours. |

<!--markdownlint-enable MD033 -->

### <a name="storage-account-types"></a>Types de comptes de stockage

Azure fournit différents types de comptes de stockage et niveaux de performances.

<!-- markdownlint-disable MD033 -->

| Type de compte | Détails | Usage |
| --- | --- | --- |
| **Comptes de stockage à usage général v2 Standard** | Prend en charge les objets blob (blocs, page, ajout), fichiers, disques, files d’attente et tables. <br><br> Prend en charge les niveaux d’accès Chaud, Froid et Archive. Le stockage redondant interzone (ZRS) est pris en charge. | Utiliser pour la plupart des scénarios et des types de données. Les comptes de stockage standard peuvent être basés sur HHD ou SSD. |
| **Comptes de stockage à usage général v2 Premium** | Prend en charge les données de stockage d’objets blob (objets blob de pages). Prend en charge les niveaux d’accès Chaud, Froid et Archive. ZRS est pris en charge. <br><br> Stocké sur disque SSD. | Recommandation de Microsoft pour toutes les machines virtuelles. |
| **Usage général v1** | La hiérarchisation des accès n’est pas prise en charge. ZRS n’est pas pris en charge. | Utiliser si les applications ont besoin du modèle de déploiement Azure Classic. |
| **Objet blob** | Compte de stockage spécialisé pour le stockage des objets non structurés. Fournit des objets blob de blocs et d’ajout uniquement (aucun service stockage sur fichier, file d’attente, table ou disque). Fournit les mêmes durabilité, disponibilité, évolutivité et performances que l’usage général v2. | Dans ces comptes, vous ne pouvez pas stocker d’objets blob de pages et donc pas de fichiers VHD. Vous pouvez définir le niveau d’accès sur Chaud ou Froid. |

<!--markdownlint-enable MD033 -->

### <a name="storage-redundancy-options"></a>Options de redondance de stockage

Les comptes de stockage peuvent utiliser différents types de redondance pour la résilience et la haute disponibilité.

| Type | Détails | Usage |
| --- | --- | --- |
| **Stockage localement redondant (LRS)** | Protège contre une panne locale grâce à une réplication, au sein d’une unité de stockage unique, vers un domaine de mise à jour et un domaine d'erreur distincts. Conserve plusieurs copies de vos données dans un centre de données. Offre une durabilité des objets d’au moins 99,999999999 % (9 « neuf ») sur une année donnée. | Envisagez cette option si votre application stocke les données qui peuvent être recréées facilement. |
| **Stockage redondant interzone (ZRS)** | Protège contre une panne du centre de données grâce à une réplication sur trois clusters de stockage dans une même région. Chaque cluster de stockage est séparé physiquement des autres et se trouve dans sa propre zone de disponibilité. Fournit une durabilité d’au minimum 99,9999999999 % (12 « neuf ») pour les objets sur une année donnée, en conservant plusieurs copies de vos données dans plusieurs centres de données ou régions. | Envisagez cette option si vous avez besoin de cohérence, de durabilité et de haute disponibilité. Vous ne serez peut-être pas à l’abri d’un sinistre régional, lorsque plusieurs zones sont affectées définitivement. |
| **Stockage géo-redondant (GRS)** | Protège contre une panne dans l’ensemble de la région en répliquant les données vers une région secondaire à des centaines de kilomètres de la région principale. Offre une durabilité des objets d’au moins 99,99999999999999 % (16 « neuf ») sur une année donnée. | Les données de réplica ne sont disponibles que si Microsoft lance un basculement vers la région secondaire. En cas de basculement, les accès en lecture et écriture sont disponibles. |
| **Stockage géo-redondant avec accès en lecture (RA-GRS)** | Semblable à GRS. Offre une durabilité des objets d’au moins 99,99999999999999 % (16 « neuf ») sur une année donnée. | Fournit une disponibilité de lecture de 99,99 % en autorisant l’accès en lecture à partir de la région secondaire utilisée pour GRS. |

**En savoir plus :**

- Consultez la [tarification Stockage Azure](https://azure.microsoft.com/pricing/details/storage).
- Apprenez à utiliser le [service Azure Import/Export](https://docs.microsoft.com/azure/storage/common/storage-import-export-service) pour importer de manière sécurisée de grandes quantités de données dans le Stockage Blob Azure et dans Azure Files.
- Comparez les [types de données pour le stockage sur disque, les objets blobs et les fichiers](https://docs.microsoft.com/azure/storage/common/storage-introduction).
- Apprenez-en plus sur les [niveaux d’accès](https://docs.microsoft.com/azure/storage/blobs/storage-blob-storage-tiers).
- Passez en revue les [différents types de comptes de stockage](https://docs.microsoft.com/azure/storage/common/storage-account-overview).
- En savoir plus sur la [redondance du stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-redundancy), y compris LRS, ZRS, GRS et GRS en lecture seule.
- Apprenez-en plus sur [Azure Files](https://docs.microsoft.com/azure/storage/files/storage-files-introduction).

## <a name="after-adoption"></a>Après l’adoption

Avant l’adoption, les prévisions de coût dépendent des décisions prises par les propriétaires des charges de travail et l’équipe d’adoption du cloud. Tandis que l’équipe de gouvernance peut contribuer à influencer ces décisions, il est probable qu’il y ait peu d’actions à entreprendre pour cette équipe de gouvernance.

Une fois que les ressources sont en production, les données peuvent être agrégées et les tendances analysées au niveau de l’environnement. Ces données aident l’équipe de gouvernance à prendre des décisions de dimensionnement et d’utilisation de façon indépendante, en fonction de modèles d’utilisation réels et de l’architecture actuelle.

- Analysez les données pour déterminer une base de référence budgétaire pour les ressources et les groupes de ressources Azure.
- Identifiez les modèles d’utilisation qui vous permettront de réduire la taille des ressources et/ou l’arrêt/la suspension de ressources pour réduire encore davantage vos coûts.

Les meilleures pratiques de cette section incluent les avantages d’Azure Hybrid et des machines virtuelles réservées, la réduction des dépenses cloud dans les abonnements, l’utilisation d’Azure Cost Management pour la budgétisation et l’analyse des coûts, la surveillance des ressources, la mise en œuvre des budgets de groupe de ressources, ainsi que l’optimisation de la surveillance, du stockage et des machines virtuelles.

## <a name="best-practice-take-advantage-of-azure-hybrid-benefit"></a>Bonne pratique : Tirer parti des avantages d’Azure Hybrid

Grâce à des années d’investissements logiciels dans des systèmes tels que Windows Server et SQL Server, Microsoft est dans une position unique pour offrir aux clients de la valeur ajoutée dans le cloud, avec de grosses remises que les autres fournisseurs de cloud ne peuvent pas nécessairement proposer.

Un portefeuille de produits Azure/locaux Microsoft intégrés génère des avantages compétitifs et de coût. Si vous disposez actuellement d’un système d’exploitation ou d’autres licences de logiciels via Software Assurance (SA), vous pouvez utiliser ces licences dans le cloud avec Azure Hybrid Benefit.

**En savoir plus :**

- [Essayez](https://azure.microsoft.com/pricing/hybrid-benefit) la calculatrice des économies réalisées avec Azure Hybrid Benefit.
- Apprenez-en plus sur [Azure Hybrid Benefit pour Windows Server](https://azure.microsoft.com/pricing/hybrid-benefit).
- Passez en revue la [tarification conseillée des machines virtuelles SQL Server Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-pricing-guidance).

## <a name="best-practice-use-reserved-vm-instances"></a>Bonne pratique : utiliser des instances de machines virtuelles réservées

La plupart des plateformes cloud sont configurées avec un paiement à l’utilisation. Ce modèle présente des inconvénients, étant donné que vous ne connaissez pas nécessairement à l’avance les charges de travail dynamiques. Lorsque vous spécifiez des intentions claires pour une charge de travail, vous contribuez à la planification de l’infrastructure.

Avec des instances de machines virtuelles réservées Azure, vous prépayez l’instance de machine virtuelle pour une durée de un à trois ans.

- Cet acompte s’accompagne d’une remise sur les ressources que vous utilisez.
- Vous pouvez réduire sensiblement les coûts de machine virtuelle, de calcul de base de données SQL, d’Azure Cosmos DB ou d’autres ressources, jusqu’à hauteur de 72 % sur les tarifs des paiements à l’utilisation.
- Les réservations permettent de bénéficier d’une remise sur la facturation et n’ont aucune incidence sur l’état de runtime de vos ressources.
- Vous pouvez annuler des instances réservées.

![Instances réservées](../../migrate/azure-best-practices/media/migrate-best-practices-costs/reserve.png)
_Figure 1 : Machines virtuelles réservées Azure._

**En savoir plus :**

- Apprenez-en plus sur les [réservations Azure](https://docs.microsoft.com/azure/cost-management-billing/reservations/save-compute-costs-reservations).
- Lisez la [FAQ sur les instances réservées Azure](https://azure.microsoft.com/pricing/reserved-vm-instances/#faq).
- Passez en revue la [tarification conseillée des machines virtuelles SQL Server Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-pricing-guidance).

## <a name="best-practice-aggregate-cloud-spend-across-subscriptions"></a>Bonne pratique : agréger les dépenses cloud des abonnements

Il est inévitable, à terme, d’avoir plusieurs abonnements Azure. Par exemple, vous aurez peut-être besoin d’un abonnement supplémentaire pour séparer les limites de développement et de production, ou votre plateforme peut exiger un abonnement distinct pour chaque client. La possibilité d’agréger les rapports de données de tous les abonnements sur une plateforme unique est une fonctionnalité très utile.

Pour ce faire, vous pouvez utiliser les API Azure Cost Management. Ensuite, après l’agrégation des données dans une source unique (comme Azure SQL), vous pouvez utiliser des outils tels que Power BI pour exposer les données agrégées. Vous pouvez créer des rapports d’abonnements agrégés et des rapports granulaires. Par exemple, pour les utilisateurs qui ont besoin d’informations proactives de gestion des coûts, vous pouvez créer des vues spécifiques pour les coûts en fonction du service, du groupe de ressources ou d’autres informations. Vous n’avez pas besoin de leur accorder un accès total aux données de facturation Azure.

**En savoir plus :**

- Lisez la [Présentation des API Azure Consumption](https://docs.microsoft.com/azure/billing/billing-consumption-api-overview).
- Apprenez-en plus sur la [connexion à Azure Consumption Insights dans Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-connect-azure-consumption-insights).
- Apprenez à [gérer l'accès aux informations de facturation pour Azure à l'aide du contrôle d'accès en fonction du rôle (RBAC)](https://docs.microsoft.com/azure/billing/billing-manage-access).

## <a name="best-practice-monitor-resource-utilization"></a>Bonne pratique : surveiller l’utilisation des ressources

Dans Azure, vous payez pour ce que vous utilisez, lorsque les ressources sont consommées, et vous ne payez pas lorsqu’elles ne le sont pas. Pour les machines virtuelles, la facturation a lieu lorsqu’une machine virtuelle est allouée, et vous n’êtes pas facturé une fois que la machine virtuelle est libérée. Dans cet esprit, vous devez surveiller les machines virtuelles en cours d’utilisation et vérifiez que leur dimensionnement.

- Évaluez en permanence vos charges de travail de machine virtuelle pour déterminer les lignes de base.
- Par exemple, si votre charge de travail est utilisée principalement du lundi au vendredi, de 8 h 00 à 18 h 00, mais rarement en dehors de ces heures, vous pouvez rétrograder les machines virtuelles en dehors des heures de pointe. Cela implique éventuellement de modifier la taille des machines virtuelles ou d’utiliser des groupes de machines virtuelles identiques pour adapter automatiquement le dimensionnement.
- Certaines entreprises « mettent en veille » les machines virtuelles en les programmant selon un calendrier qui spécifie quand elles doivent être disponibles et quand elles ne sont pas nécessaires.
- Outre les machines virtuelles, vous devez surveiller d’autres ressources réseau, telles qu’ExpressRoute et les passerelles de réseau virtuel pour veiller à ce que leur utilisation soit adaptée.
- Vous pouvez surveiller l’utilisation des machines virtuelles à l’aide d’outils Microsoft, tels qu’Azure Cost Management, Azure Monitor et Azure Advisor. Des outils tiers sont également disponibles.

**En savoir plus :**

- Lisez les présentations d'[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) et d'[Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview).
- Bénéficiez de [recommandations sur les coûts d'Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-cost-recommendations).
- Découvrez comment [optimiser les coûts à partir des recommandations](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations) et [éviter les frais imprévus](https://docs.microsoft.com/azure/billing/billing-getting-started).
- En savoir plus sur le [kit d’outils Azure Resource Optimization (ARO)](https://github.com/azure/azure-quickstart-templates/tree/master/azure-resource-optimization-toolkit).

## <a name="best-practice-reduce-nonproduction-costs"></a>Bonne pratique : Réduire les coûts hors production

Les environnements de développement, de test et d’assurance qualité (AQ) sont nécessaires pendant les cycles de développement. Malheureusement, il est courant que ces environnements restent provisionnés longtemps après leur dernière utilisation. Une révision régulière des environnements hors production inutilisés peut avoir un impact immédiat sur les coûts.

En outre, envisagez une réduction générale des coûts pour tous les environnements hors production :

- Réduisez les ressources hors production pour utiliser des machines virtuelles de série B à faible coût et un stockage standard.
- Appliquez des stratégies Azure pour exiger des réductions de coût au niveau des ressources pour toutes les ressources hors production.

**En savoir plus :**

- [Utilisez des balises](https://docs.microsoft.com/azure/azure-resource-manager/management/tag-resources) pour identifier les ressources de développement, de test ou d’assurance qualité à redimensionner ou à arrêter.
- [L’arrêt automatique des machines virtuelles](https://docs.microsoft.com/azure/cost-management-billing/manage/getting-started#consider-cost-cutting-features-like-auto-shutdown-for-vms) définit une heure d’arrêt pour les machines virtuelles la nuit. Cette fonctionnalité arrête les machines virtuelles hors production toutes les nuits, ce qui oblige les développeurs à les redémarrer lorsqu'ils sont prêts à reprendre le travail de développement.
- Encouragez les équipes de développement à utiliser [Azure DevTest Labs](https://docs.microsoft.com/azure/lab-services/devtest-lab-overview) pour établir leurs propres approches de contrôle des coûts et éviter l’impact du temps d’arrêt automatique standard de l’étape précédente.

## <a name="best-practice-use-azure-cost-management"></a>Bonne pratique : utiliser Azure Cost Management

Microsoft propose Azure Cost Management pour vous aider à suivre vos dépenses :

- Il vous aide à surveiller et à contrôler les dépenses Azure, et à optimiser l’utilisation des ressources.
- Il passe en revue l’ensemble de l’abonnement et toutes les ressources associées, et émet des recommandations.
- Il fournit une API complète, pour intégrer les outils externes et les systèmes financiers pour les rapports.
- Il suit l’utilisation des ressources et gère les coûts liés au cloud dans une vue unifiée.
- Il fournit des insights financiers et opérationnels enrichis pour vous aider à prendre des décisions avisées.

Dans Azure Cost Management, vous pouvez :

- **Créer un budget :** Créez un budget pour garantir la responsabilité financière.
  - Vous pouvez tenir compte des services que vous consommez ou vous abonner pour une période spécifique (mensuelle, trimestrielle, annuelle) et une étendue (abonnements/groupes de ressources). Par exemple, vous pouvez créer un budget d’abonnement Azure pour un mois, un trimestre ou un an.
    - Une fois que vous avez créé un budget, il est indiqué dans l’analyse des coûts. La visualisation de votre budget par rapport aux dépenses actuelles est une des premières étapes nécessaires lors de l’analyse de vos coûts et dépenses.
  - Des notifications par e-mail peuvent être envoyées lorsque les seuils budgétaires sont atteints.
  - Vous pouvez exporter les données de gestion des coûts dans le stockage Azure, à des fins d’analyse.

    ![Afficher les budgets dans Azure Cost Management](../../migrate/azure-best-practices/media/migrate-best-practices-costs/budget.png)
    _Budget Azure Cost Management_

- **Réaliser une analyse des coûts :** Obtenez une analyse des coûts pour explorer et examiner vos coûts organisationnels, afin de comprendre comment les coûts sont accumulés et d’identifier les tendances de dépenses.
  - L’analyse des coûts est accessible aux utilisateurs EA.
  - Vous pouvez voir les données d’analyse des coûts pour différentes étendues, notamment par service, compte, abonnement ou groupe de ressources.
  - Vous pouvez obtenir une analyse des coûts qui montre le coût total pour le mois en cours et les coûts quotidiens cumulés.

    ![Analyse d’Azure Cost Management](../../migrate/azure-best-practices/media/migrate-best-practices-costs/analysis.png)
    _Figure : Analyse d’Azure Cost Management._

- **Obtenir des recommandations :** Obtenez des recommandations d’Advisor, pour savoir comment optimiser et améliorer l’efficacité.

**En savoir plus :**

- Lisez la [Présentation d'Azure Cost Management](https://docs.microsoft.com/azure/cost-management/overview).
- Apprenez à [optimiser votre investissement dans le cloud avec Azure Cost Management](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-best-practices).
- Apprenez à [utiliser les rapports Azure Cost Management](https://docs.microsoft.com/azure/cost-management/use-reports).
- Consultez un tutoriel consacré à l'[optimisation des coûts à partir de recommandations](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations).
- Passez en revue les [API Azure Consumption](https://docs.microsoft.com/rest/api/consumption/budgets).

## <a name="best-practice-implement-resource-group-budgets"></a>Bonne pratique : implémenter des budgets de groupe de ressources

Souvent, les groupes de ressources sont utilisés pour représenter des limites de coût. Avec ce modèle d’utilisation, l’équipe Azure continue d’innover et d’améliorer ses offres pour suivre et analyser les dépenses à différents niveaux, y compris la possibilité de créer des budgets pour les ressources et les groupes de ressources.

- Un budget de groupe de ressources vous permet de suivre les coûts associés à un groupe de ressources.
- Vous pouvez déclencher des alertes et exécuter un large éventail de playbooks lorsque le budget est atteint ou dépassé.

**En savoir plus :**

- Apprenez à [gérer les coûts avec Azure Budgets](https://docs.microsoft.com/azure/billing/billing-cost-management-budget-scenario).
- Consultez un tutoriel portant sur [la création et la gestion d'un budget Azure](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets).

## <a name="best-practice-review-azure-advisor-recommendations"></a>Bonne pratique : Examiner les recommandations Azure Advisor

Les recommandations de coûts d’Azure Advisor identifient les opportunités de réduction des coûts Lorsque les budgets paraissent élevés ou que l’utilisation semble faible, utilisez ce rapport pour identifier rapidement des opportunités de réduction des coûts.

**En savoir plus :**

- [Examinez les recommandations d’Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-cost-recommendations) pour prendre des mesures immédiates.

## <a name="best-practice-optimize-azure-monitor-retention"></a>Bonne pratique : optimiser la rétention d’Azure Monitor

Lorsque vous déplacez des ressources dans Azure et activez la journalisation des diagnostics, vous générez un gros volume de données de journal. En général, ces données de journal d’activité sont envoyées à un compte de stockage mappé avec un espace de travail Log Analytics.

- Plus la période de rétention de données de journal est longue, plus vous aurez de données.
- Toutes les données de journal ne sont pas identiques, et certaines ressources génèrent plus de données de journal que d’autres.
- En raison des réglementations et de la conformité, il est probable que vous devrez conserver les données de journal de certaines ressources plus longtemps que d’autres.
- Vous devez trouver le bon équilibre entre l’optimisation des coûts de stockage de journal et la rétention des données de journal dont vous avez besoin.
- Nous vous recommandons d’évaluer et de configurer la journalisation immédiatement après une migration, afin de ne pas gaspiller de l’argent en conservant des journaux d’activité sans importance.

**En savoir plus :**

- Apprenez-en plus sur la [surveillance de l'utilisation et l'estimation des coûts](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-usage-and-estimated-costs).

## <a name="best-practice-optimize-storage"></a>Bonne pratique : optimiser le stockage

Si vous avez suivi les meilleures pratiques pour la sélection du stockage avant l'adoption, vous en constatez probablement les bénéfices. Vous pouvez probablement optimiser d'autres coûts de stockage. Au fil du temps, les objets blob et les fichiers deviennent obsolètes. Des données peuvent ne plus être utilisées, mais les exigences réglementaires vous obligent parfois à les conserver pendant un certain temps. Par conséquent, vous n’avez pas forcément à les placer dans le stockage hautes performances que vous avez utilisé pour l’adoption d’origine.

L’identification des données périmées et leur déplacement vers des zones de stockage plus économiques peuvent avoir un impact considérable sur votre budget de stockage mensuel et vous permettre de faire des économies. Azure offre de nombreux moyens pour vous aider à identifier et à stocker ces données périmées.

- Tirez parti des niveaux d’accès pour le stockage à usage général v2, en déplaçant des données moins importantes du niveau Chaud vers les niveaux Froid et Archivé.
- Utilisez StorSimple pour déplacer des données périmées en fonction de stratégies personnalisées.

**En savoir plus :**

- Apprenez-en plus sur les [niveaux d’accès](https://docs.microsoft.com/azure/storage/blobs/storage-blob-storage-tiers).
- Lisez la [Présentation de StorSimple](https://docs.microsoft.com/azure/azure-monitor/overview).
- Passez en revue la [Tarification de StorSimple](https://azure.microsoft.com/pricing/details/storsimple).

## <a name="best-practice-automate-vm-optimization"></a>Bonne pratique : automatiser l’optimisation des machines virtuelles

L’objectif ultime de l’exécution d’une machine virtuelle dans le cloud consiste à optimiser l’UC, la mémoire et le disque qu’elle utilise. Si vous découvrez des machines virtuelles qui ne sont pas optimisées ou pas souvent utilisées, il est judicieux de les arrêter ou de réduire l’échelle en utilisant des groupes de machines virtuelles identiques.

Vous pouvez optimiser une machine virtuelle avec Azure Automation, des groupes de machines virtuelles identiques, l’arrêt automatique et des solutions tierces ou scriptées.

**En savoir plus :**

- Découvrez-en plus sur la [mise à l'échelle automatique verticale](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-vertical-scale-reprovision).
- Passez en revue [Azure DevTest Labs : Planifier le démarrage automatique d'une machine virtuelle](https://azure.microsoft.com/updates/azure-devtest-labs-schedule-vm-auto-start).
- Apprenez à [démarrer ou arrêter des machines virtuelles en dehors des heures d'activité dans Azure Automation](https://docs.microsoft.com/azure/automation/automation-solution-vm-management).
- Obtenez des informations supplémentaires sur [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) et le [kit d’outils Azure Resource Optimization (ARO)](https://github.com/azure/azure-quickstart-templates/tree/master/azure-resource-optimization-toolkit).

## <a name="best-practice-use-logic-apps-and-runbooks-with-budgets-api"></a>Bonne pratique : utiliser des applications logiques et des runbooks avec l’API Budgets

Azure fournit une API REST qui peut accéder à vos informations de facturation client.

- Vous pouvez utiliser l’API Budgets pour intégrer des systèmes externes et des flux de travail déclenchés par les mesures que vous générez à partir des données de l’API.
- Vous pouvez extraire les données d’utilisation et de ressources dans vos outils d’analyse de données préférés.
- Le API d’utilisation des ressources Azure et l’API de tarification des ressources Azure peuvent vous aider à prévoir et à gérer vos coûts avec précision.
- Les API sont implémentées en tant que fournisseur de ressources et incluses dans les API exposées par Azure Resource Manager.
- L’API Budgets peut être intégrée à Azure Logic Apps et aux runbooks Azure Automation.

**En savoir plus :**

- Apprenez-en plus sur l’[API Budget](https://docs.microsoft.com/rest/api/consumption/budgets).
- [Obtenez des informations](https://docs.microsoft.com/azure/billing/billing-usage-rate-card-overview) dans l’utilisation d’Azure avec les API Facturation Azure.

## <a name="next-steps"></a>Étapes suivantes

Si vous maîtrisez les meilleures pratiques, examinez la [chaîne d’outils Cost Management](./toolchain.md) pour identifier les outils et fonctionnalités Azure qui vous aideront à exécuter ces meilleures pratiques.

> [!div class="nextstepaction"]
> [Chaîne d’outils de gestion des coûts pour Azure](./toolchain.md)
