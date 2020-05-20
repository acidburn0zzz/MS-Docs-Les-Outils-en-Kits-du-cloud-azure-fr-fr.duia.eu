---
title: Évaluation des coûts et dimensionnement des charges de travail migrées vers Azure
description: Utilisez le Cloud Adoption Framework pour Azure afin de découvrir les bonnes pratiques en matière d’évaluation des coûts et de dimensionnement des charges de travail migrées vers Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: adc74b83bf3da456e657d890a06ba6b1bcf516ed
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83401241"
---
<!-- docsTest:ignore ARO -->

# <a name="best-practices-for-costing-and-sizing-workloads-migrated-to-azure"></a>Meilleures pratiques pour l’évaluation des coûts et le dimensionnement des charges de travail migrées vers Azure

Lorsque vous planifiez et concevez la migration, le fait de mettre l’accent sur les coûts garantit la réussite à long terme de votre migration vers Azure. Au cours d’un projet de migration, il est essentiel que toutes les équipes (telles que les équipes des finances, de gestion et de développement d’applications) comprennent les coûts associés.

- Avant la migration, vous devez absolument estimer les dépenses liées à la migration, avec une ligne de base pour les objectifs budgétaires mensuels, trimestriels et annuels. Cela est essentiel à votre réussite.
- Après la migration, vous devez optimiser les coûts, surveiller en permanence les charges de travail et planifier des modèles d’utilisation future. Les ressources migrées peuvent représenter d’abord un certain type de charge de travail, mais évoluer en un autre type au fil du temps, selon l’utilisation, les coûts et l’évolution des besoins de l’entreprise.

Cet article décrit les meilleures pratiques pour l’évaluation des coûts et le dimensionnement avant et après la migration.

> [!IMPORTANT]
> Les meilleures pratiques et opinions décrites dans cet article sont basées sur la plateforme Azure et les fonctionnalités disponibles au moment de la rédaction. Les fonctionnalités et les capacités changent au fil du temps. Il est possible que certaines recommandations ne s’appliquent pas à votre déploiement. Par conséquent, sélectionnez celles qui vous conviennent.

## <a name="before-migration"></a>Avant la migration

Avant de déplacer vos charges de travail vers le cloud, estimez le coût mensuel de leur exécution dans Azure. La gestion proactive des coûts liés au cloud vous permet de respecter votre budget de charges d’exploitation. Si le budget est limité, tenez-en compte avant la migration. Envisagez de convertir les charges de travail aux technologies serverless Azure, le cas échéant, pour réduire les coûts.

Les meilleures pratiques décrites dans cette section vous aident à estimer les coûts, effectuer un dimensionnement adéquat pour les machines virtuelles et le stockage, utiliser les avantages d’Azure Hybrid, utiliser des machines virtuelles réservées et estimer les dépenses cloud pour les abonnements.

## <a name="best-practice-estimate-monthly-workload-costs"></a>Bonne pratique : estimer les coûts mensuels de la charge de travail

Pour prévoir votre facture mensuelle pour les charges de travail migrées, vous pouvez utiliser plusieurs outils.

<!-- TODO: Change "input costs" -->
- **Calculatrice de prix Azure :** Sélectionnez les produits que vous souhaitez estimer, par exemple les machines virtuelles et le stockage, puis entrez les coûts dans la calculatrice pour créer une estimation.

 ![Calculatrice de prix Azure](./media/migrate-best-practices-costs/pricing.png) _Calculatrice de prix Azure_

- **Azure Migrate :** Pour estimer les coûts, vous devez passer en revue et considérer toutes les ressources requises pour exécuter vos charges de travail dans Azure. Pour obtenir ces données, vous créez l’inventaire de vos ressources, y compris les serveurs, les machines virtuelles, les bases de données et le stockage. Vous pouvez utiliser Azure Migrate pour collecter ces informations.

- Azure Migrate détecte et évalue votre environnement local afin de fournir un inventaire.
- Azure Migrate peut mapper et afficher des dépendances entre les machines virtuelles pour vous donner une vision complète.
- Une évaluation Azure Migrate contient le coût estimé.
  - Coûts de calcul : selon la taille de machine virtuelle Azure recommandée lorsque vous créez une évaluation, Azure Migrate utilise les API de facturation Azure pour calculer l’estimation des coûts mensuels de machine virtuelle. Cette estimation tient compte du système d’exploitation, de Software Assurance, des instances réservées, de la durée de fonctionnement de machine virtuelle, de l’emplacement et des paramètres de devise. Elle agrège le coût de toutes les machines virtuelle incluses dans l’évaluation pour calculer le coût de calcul mensuel total.
  - Coût de stockage : Azure Migrate calcule le coût de stockage mensuel total en additionnant le coût de stockage de toutes les machines virtuelles incluses dans l’évaluation. Vous calculez le coût de stockage mensuel d’une machine en additionnant le coût mensuel de tous les disques qui lui sont attachés.

    ![Azure Migrate](./media/migrate-best-practices-costs/assess.png)
    _Évaluation Azure Migrate_

**En savoir plus :**

- [Utiliser](https://azure.microsoft.com/pricing/calculator) la calculatrice de prix Azure.
- [Obtenir une vue d’ensemble](https://docs.microsoft.com/azure/migrate/migrate-services-overview) d’Azure Migrate.
- [En savoir plus](https://docs.microsoft.com/azure/migrate/concepts-assessment-calculation) sur les évaluations Azure Migrate.
- [En savoir plus](https://docs.microsoft.com/azure/dms/dms-overview) sur Azure Database Migration Service.

## <a name="best-practice-right-size-vms"></a>Bonne pratique : redimensionner des machines virtuelles

Vous avez le choix entre différentes options lorsque vous déployez des machines virtuelles Azure pour prendre en charge les charges de travail. Chaque type de machine virtuelle possède des fonctionnalités spécifiques et différentes combinaisons d’UC, mémoire et disques. Les machines virtuelles sont regroupées comme indiqué ci-dessous :

| **Type** | **Détails** | **Utilisation** |
| --- | --- | --- |
| **Usage général** | Ratio processeur/mémoire équilibré. | Convient pour le test et le développement, les bases de données de petite à moyenne taille et les serveurs web au volume de trafic faible à moyen. |
| **Optimisé pour le calcul** | Ratio processeur/mémoire élevé. | Convient pour les serveurs web au trafic de moyen volume, les appliances réseau, les processus de traitement par lots et les serveurs d’applications. |
| **Optimisé pour la mémoire** | Ratio mémoire/processeur élevé. | Convient pour les bases de données relationnelles, les caches de taille moyenne à grande et l’analytique en mémoire. |
| **Optimisé pour le stockage** | Débit de disque et E/S élevés. | Convient pour les bases de données NoSQL, SQL et Big Data. |
| **Optimisé pour le GPU** | Machines virtuelles spécialisées. Un ou plusieurs GPU. | Retouche vidéo et graphique avancée. |
| **Hautes performances** | Processeur plus rapide et plus puissant. Machines virtuelles avec interfaces réseau haut débit en option (RDMA) | Applications hautes performances critiques. |

- Il est important de comprendre les différences de prix entre ces machines virtuelles et les effets à long terme sur le budget.
- Chaque type est associé à plusieurs gammes de machines virtuelles.
- En outre, lorsque vous sélectionnez une machine virtuelle dans une gamme, vous pouvez uniquement mettre à l’échelle la machine virtuelle au sein de cette gamme. Par exemple, un modèle DSv2\_2 peut évoluer en DSv2\_4, mais pas vers une autre gamme, comme Fsv2\_2.

**En savoir plus :**

- [Apprenez-en plus](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) sur les types de machines virtuelles et leur dimensionnement, et adaptez leur taille à leur type.
- [Planifiez](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs) le dimensionnement des machines virtuelles.
- [Examinez](https://docs.microsoft.com/azure/migrate/contoso-migration-assessment) un exemple d’évaluation de la société fictive Contoso.

## <a name="best-practice-select-the-right-storage"></a>Bonne pratique : sélectionner le stockage approprié

Le paramétrage et la gestion de stockage local (SAN ou NAS) et des réseaux qui les prennent en charge peuvent s’avérer coûteux et fastidieux. Les données (de stockage) de fichier sont généralement migrées vers le cloud pour simplifier les tâches opérationnelles et de gestion. Microsoft fournit plusieurs options pour déplacer des données vers Azure, et vous devez prendre des décisions concernant ces options. Choisir le type de stockage approprié pour les données de votre entreprise peut vous faire économiser plusieurs milliers d’euros chaque mois. Tenez compte des points suivants :

- Les données auxquelles vous n’accédez pas souvent et qui ne sont pas vitales pour l’entreprise ne doivent pas forcément être placées sur le stockage le plus coûteux.
- À l’inverse, les données critiques pour l’entreprise doivent se trouver sur les options de stockage de niveau supérieur.
- Lors de la planification de la migration, effectuez un inventaire des données et classez-les par ordre d’importance, afin de les mapper vers le stockage le plus approprié. Tenez compte du budget et des coûts, ainsi que des performances. Le coût ne doit pas nécessairement être le principal facteur de prise de décision. L’option la moins coûteuse peut exposer la charge de travail à des pertes de performances et à moins de disponibilité.

### <a name="storage-data-types"></a>Types de données de stockage

Azure fournit différents types de données de stockage.

<!-- markdownlint-disable MD033 -->

| **Type de données** | **Détails** | **Utilisation** |
| --- | --- |  --- |
| **Objets blob** | Optimisé pour stocker de grandes quantités d’objets non structurées, comme des données texte ou binaires. <br><br> | Accéder aux données depuis n’importe où via HTTP/HTTPS. | Utiliser cette option pour les scénarios d’accès aléatoire et de diffusion en continu. Par exemple, pour envoyer des images et des documents directement vers un navigateur, diffusez la vidéo et l’audio, et stockez les données de récupération d’urgence et de sauvegarde. |
| **Fichiers** | Partages de fichiers managés accessibles via SMB 3.0 | Utiliser lors de la migration des partages de fichiers locaux et pour fournir plusieurs connexions/accès aux données de fichiers. |
| **Disques** | Basé sur les objets blob de pages. <br><br> Type de disque (vitesse) : Standard (HDD ou SSD) ou Premium (SSD). <br><br> Gestion des disques : Non managé (vous gérez les paramètres de disque et le stockage) ou managé (vous sélectionnez le type de disque et Azure gère le disque pour vous). | Utiliser des disques Premium pour les machines virtuelles. Utiliser des disques managés pour la gestion simple et la mise à l’échelle. |
| **Files d’attente** | Stocker et récupérer un grand nombre de messages accessibles via des appels authentifiés (HTTP ou HTTPS) | Connecter des composants d’application à la file d’attente asynchrone des messages. |
| **Tables** | Tables de stockage. | Désormais inclus dans l’API Table d’Azure Cosmos DB. |

<!--markdownlint-enable MD033 -->

### <a name="access-tiers"></a>Niveaux d’accès

Le stockage Azure propose différentes options permettant d’accéder aux données d’objets blob de blocs. En sélectionnant le niveau d’accès approprié, vous pouvez stocker vos données d’objets blob de blocs de manière plus économique.

<!-- markdownlint-disable MD033 -->

| **Type** | **Détails** | **Utilisation** |
| --- | --- | --- |
| **Chaud** | Stockage plus cher que Froid. Frais d’accès inférieurs à Froid. <br><br> Niveau par défaut. | Pour les données en cours d’utilisation qui sont fréquemment sollicitées. |
| **Froid** | Stockage moins cher que Chaud. Frais d’accès supérieurs à Chaud. <br><br> Stockage minimal de 30 jours. | Stockage à court terme : les données sont disponibles mais sollicitées rarement. |
| **Archive** | Utilisé pour les objets blob de blocs. <br><br> Option la plus économique pour le stockage. L’accès aux données est plus cher que les options Chaud et Froid. | Pour les données qui peuvent tolérer plusieurs heures de latence de récupération et restent dans le niveau pendant au moins 180 jours. |

<!--markdownlint-enable MD033 -->

### <a name="storage-account-types"></a>Types de comptes de stockage

Azure fournit différents types de comptes de stockage et niveaux de performances.

<!-- markdownlint-disable MD033 -->

| **Type de compte** | **Détails** | **Utilisation** |
| --- | --- | --- |
| **Usage général v2 Standard** | Prend en charge les objets blob (blocs, page, ajout), fichiers, disques, files d’attente et tables. <br><br> Prend en charge les niveaux d’accès Chaud, Froid et Archive. ZRS est pris en charge. | Utiliser pour la plupart des scénarios et des types de données. Les comptes de stockage standard peuvent être basés sur HHD ou SSD. |
| **Usage général v2 Premium** | Prend en charge les données de stockage d’objets blob (objets blob de pages). Prend en charge les niveaux d’accès Chaud, Froid et Archive. ZRS est pris en charge. <br><br> Stocké sur disque SSD. | Recommandation de Microsoft pour toutes les machines virtuelles. |
| **Usage général v1** | La hiérarchisation des accès n’est pas prise en charge. ZRS n’est pas pris en charge. | Utiliser si les applications ont besoin du modèle de déploiement Azure Classic. |
| **Objet blob** | Compte de stockage spécialisé pour le stockage des objets non structurés. Fournit des objets blob de blocs et d’ajout uniquement (aucun service stockage sur fichier, file d’attente, table ou disque). Fournit les mêmes durabilité, disponibilité, évolutivité et performances que l’usage général v2. | Dans ces comptes, vous ne pouvez pas stocker d’objets blob de pages et donc pas de fichiers VHD. Vous pouvez définir le niveau d’accès sur Chaud ou Froid. |

<!--markdownlint-enable MD033 -->

### <a name="storage-redundancy-options"></a>Options de redondance de stockage

Les comptes de stockage peuvent utiliser différents types de redondance pour la résilience et la haute disponibilité.

| **Type** | **Détails** | **Utilisation** |
| --- | --- | --- |
| **Stockage localement redondant (LRS)** | Protège contre une panne locale grâce à une réplication, au sein d’une unité de stockage unique, vers un domaine de mise à jour et un domaine d'erreur distincts. Conserve plusieurs copies de vos données dans un centre de données. Offre une durabilité des objets d’au moins 99,999999999 % (9 « neuf ») sur une année donnée. | Envisagez cette option si votre application stocke les données qui peuvent être recréées facilement. |
| **Stockage redondant interzone (ZRS)** | Protège contre une panne du centre de données grâce à une réplication sur trois clusters de stockage dans une même région. Chaque cluster de stockage est séparé physiquement des autres et se trouve dans sa propre zone de disponibilité. Fournit une durabilité d’au minimum 99,9999999999 % (12 « neuf ») pour les objets sur une année donnée, en conservant plusieurs copies de vos données dans plusieurs centres de données ou régions. | Envisagez cette option si vous avez besoin de cohérence, de durabilité et de haute disponibilité. Vous ne serez peut-être pas à l’abri d’un sinistre régional, lorsque plusieurs zones sont affectées définitivement. |
| **Stockage géo-redondant (GRS)** | Protège contre une panne dans l’ensemble de la région en répliquant les données vers une région secondaire à des centaines de kilomètres de la région principale. Offre une durabilité des objets d’au moins 99,99999999999999 % (16 « neuf ») sur une année donnée. | Les données de réplica ne sont disponibles que si Microsoft lance un basculement vers la région secondaire. En cas de basculement, les accès en lecture et écriture sont disponibles. |
| **Stockage géo-redondant avec accès en lecture (RA-GRS)** | Semblable à GRS. Offre une durabilité des objets d’au moins 99,99999999999999 % (16 « neuf ») sur une année donnée. | Fournit une disponibilité de lecture de 99,99 % en autorisant l’accès en lecture à partir de la région secondaire utilisée pour GRS. |

**En savoir plus :**

- [Passez en revue](https://azure.microsoft.com/pricing/details/storage) la tarification du stockage Azure.
- [Apprenez-en plus](https://docs.microsoft.com/azure/storage/common/storage-import-export-service) sur Azure Import/Export pour la migration de grandes quantités de données vers des fichiers et des objets blob Azure.
- [Comparez](https://docs.microsoft.com/azure/storage/common/storage-decide-blobs-files-disks) les types de données pour le stockage sur disque, les objets blobs et le fichiers.
- [Apprenez-en plus](https://docs.microsoft.com/azure/storage/blobs/storage-blob-storage-tiers) sur les niveaux d’accès.
- [Passez en revue](https://docs.microsoft.com/azure/storage/common/storage-account-overview) les différents types de comptes de stockage.
- En savoir plus sur la [redondance du stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-redundancy), y compris LRS, ZRS, GRS et GRS en lecture seule.
- Apprenez-en plus sur [Azure Files](https://docs.microsoft.com/azure/storage/files/storage-files-introduction).

## <a name="best-practice-take-advantage-of-azure-hybrid-benefits"></a>Bonne pratique : Tirer parti des avantages d’Azure Hybrid

Grâce à des années d’investissements logiciels dans des systèmes tels que Windows Server et SQL Server, Microsoft est dans une position unique pour offrir aux clients de la valeur ajoutée dans le cloud, avec de grosses remises que les autres fournisseurs de cloud ne peuvent pas nécessairement proposer.

Un portefeuille de produits Azure/locaux Microsoft intégrés génère des avantages compétitifs et de coût. Si vous disposez actuellement d’un système d’exploitation ou d’autres licences de logiciels via Software Assurance (SA), vous pouvez utilisez ces licences dans le cloud avec Azure Hybrid Benefit.

**En savoir plus :**

- [Essayez](https://azure.microsoft.com/pricing/hybrid-benefit) la calculatrice des économies réalisées avec Azure Hybrid Benefit.
- [Apprenez-en plus](https://azure.microsoft.com/pricing/hybrid-benefit) sur Hybrid Benefit pour Windows Server.
- [Passez en revue](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-pricing-guidance) la tarification conseillée des machines virtuelles SQL Server Azure.

## <a name="best-practice-use-reserved-vm-instances"></a>Bonne pratique : utiliser des instances de machines virtuelles réservées

La plupart des plateformes cloud sont configurées avec un paiement à l’utilisation. Ce modèle présente des inconvénients, étant donné que vous ne connaissez pas nécessairement à l’avance les charges de travail dynamiques. Lorsque vous spécifiez des intentions claires pour une charge de travail, vous contribuez à la planification de l’infrastructure.

Avec des instances de machines virtuelles réservées Azure, vous prépayez l’instance de machine virtuelle pour une durée de un à trois ans.

- Cet acompte s’accompagne d’une remise sur les ressources que vous utilisez.
- Vous pouvez réduire sensiblement les coûts de machine virtuelle, de calcul de base de données SQL, d’Azure Cosmos DB ou d’autres ressources, jusqu’à hauteur de 72 % sur les tarifs des paiements à l’utilisation.
- Les réservations permettent de bénéficier d’une remise sur la facturation et n’ont aucune incidence sur l’état de runtime de vos ressources.
- Vous pouvez annuler des instances réservées.

![Instances réservées](./media/migrate-best-practices-costs/reserve.png)
_Machines virtuelles réservées Azure_

**En savoir plus :**

- Apprenez-en plus sur les [réservations Azure](https://docs.microsoft.com/azure/cost-management-billing/reservations/save-compute-costs-reservations).
- Lisez la [FAQ sur les instances réservées Azure](https://azure.microsoft.com/pricing/reserved-vm-instances/#faq).
- Passez en revue la [tarification conseillée des machines virtuelles SQL Server Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-pricing-guidance).

## <a name="best-practice-aggregate-cloud-spend-across-subscriptions"></a>Bonne pratique : agréger les dépenses cloud des abonnements

Il est inévitable, à terme, d’avoir plusieurs abonnements Azure. Par exemple, vous aurez peut-être besoin d’un abonnement supplémentaire pour séparer les limites de développement et de production, ou votre plateforme peut exiger un abonnement distinct pour chaque client. La possibilité d’agréger les rapports de données de tous les abonnements sur une plateforme unique est une fonctionnalité très utile.

Pour ce faire, vous pouvez utiliser les API Azure Cost Management. Ensuite, après l’agrégation des données dans une source unique (comme Azure SQL), vous pouvez utiliser des outils tels que Power BI pour exposer les données agrégées. Vous pouvez créer des rapports d’abonnements agrégés et des rapports granulaires. Par exemple, pour les utilisateurs qui ont besoin d’informations proactives de gestion des coûts, vous pouvez créer des vues spécifiques pour les coûts en fonction du service, du groupe de ressources ou d’autres informations. Vous n’avez pas besoin de leur accorder un accès total aux données de facturation Azure.

**En savoir plus :**

- [Obtenez une vue d’ensemble](https://docs.microsoft.com/azure/billing/billing-consumption-api-overview) de l’API Azure Consumption.
- [Apprenez-en plus](https://docs.microsoft.com/power-bi/desktop-connect-azure-consumption-insights) sur la connexion à Azure Consumption Insights dans Power BI Desktop.
- [Apprenez à gérer](https://docs.microsoft.com/azure/billing/billing-manage-access) l’accès aux informations de facturation pour Azure à l’aide du contrôle d’accès en fonction du rôle (RBAC).

## <a name="after-migration"></a>Après la migration

Après une migration réussie de vos charges de travail et quelques semaines de collecte des données de consommation, vous aurez une idée claire du coût des ressources.

- En analysant les données, vous pouvez commencer à déterminer une ligne budgétaire de base pour les ressources et les groupes de ressources Azure.
- Ensuite, sachant comment votre budget cloud est dépensé, vous pouvez chercher comment réduire vos coûts.

Les meilleures pratiques de cette section incluent l’utilisation d’Azure Cost Management pour la budgétisation et l’analyse des coûts, la surveillance des ressources, la mise en œuvre des budgets de groupe de ressources, ainsi que l’optimisation de la surveillance, du stockage et des machines virtuelles.

## <a name="best-practice-use-azure-cost-management"></a>Bonne pratique : utiliser Azure Cost Management

Microsoft propose Azure Cost Management pour vous aider à suivre vos dépenses :

- Il vous aide à surveiller et à contrôler les dépenses Azure, et à optimiser l’utilisation des ressources.
- Il passe en revue l’ensemble de l’abonnement et toutes les ressources associées, et émet des recommandations.
- Il fournit une API complète, pour intégrer des outils externes et des systèmes financiers pour les rapports.
- Il suit l’utilisation des ressources et gère les coûts liés au cloud dans une vue unifiée.
- Il fournit des insights financiers et opérationnels enrichis pour vous aider à prendre des décisions avisées.

Dans Cost Management, vous pouvez :

- **Créer un budget :** Créez un budget pour garantir la responsabilité financière.
  - Vous pouvez tenir compte des services que vous consommez ou vous abonner pour une période spécifique (mensuelle, trimestrielle, annuelle) et une étendue (abonnements/groupes de ressources). Par exemple, vous pouvez créer un budget d’abonnement Azure pour un mois, un trimestre ou un an.
    - Une fois que vous avez créé un budget, il est indiqué dans l’analyse des coûts. La visualisation de votre budget par rapport aux dépenses actuelles est une des premières étapes nécessaires lors de l’analyse de vos coûts et dépenses.
  - Des notifications par e-mail peuvent être envoyées lorsque les seuils budgétaires sont atteints.
  - Vous pouvez exporter les données de gestion des coûts dans le stockage Azure, à des fins d’analyse.

    ![Budget Cost Management](./media/migrate-best-practices-costs/budget.png)
    _Budget Azure Cost Management_

- **Réaliser une analyse des coûts :** Obtenez une analyse des coûts pour explorer et examiner vos coûts organisationnels, afin de comprendre comment les coûts sont accumulés et d’identifier les tendances de dépenses.
  - L’analyse des coûts est accessible aux utilisateurs EA.
  - Vous pouvez afficher les données d’analyse des coûts pour différentes étendues, notamment par service, compte, abonnement ou groupe de ressources.
  - Vous pouvez obtenir une analyse des coûts qui montre le coût total pour le mois en cours et les coûts quotidiens cumulés.

    ![Analyse d’Azure Cost Management](./media/migrate-best-practices-costs/analysis.png)
    _Figure : Analyse d’Azure Cost Management_
- **Obtenir des recommandations :** Obtenez des recommandations d’Advisor, pour savoir comment optimiser et améliorer l’efficacité.

**En savoir plus :**

- Obtenez une vue d’ensemble d’[Azure Cost Management](https://docs.microsoft.com/azure/cost-management-billing/cost-management-billing-overview).
- Apprenez à [optimiser votre investissement dans le cloud avec Azure Cost Management](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-best-practices).
- Apprenez à [utiliser les rapports Azure Cost Management](https://docs.microsoft.com/azure/cost-management/use-reports).
- Obtenez un [tutoriel sur l’optimisation des coûts à partir de recommandations](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations).
- Examinez l’[API Azure Consumption](https://docs.microsoft.com/rest/api/consumption/budgets).

## <a name="best-practice-monitor-resource-utilization"></a>Bonne pratique : surveiller l’utilisation des ressources

Dans Azure, vous payez pour ce que vous utilisez, lorsque les ressources sont consommées, et vous ne payez pas lorsqu’elles ne le sont pas. Pour les machines virtuelles, la facturation a lieu lorsqu’une machine virtuelle est allouée, et vous n’êtes pas facturé une fois que la machine virtuelle est libérée. Dans cet esprit, vous devez surveiller les machines virtuelles en cours d’utilisation et vérifiez que leur dimensionnement.

- Évaluez en permanence vos charges de travail de machine virtuelle pour déterminer les lignes de base.
- Par exemple, si votre charge de travail est utilisée principalement du lundi au vendredi, de 8 h 00 à 18 h 00, mais rarement en dehors de ces heures, vous pouvez rétrograder les machines virtuelles en dehors des heures de pointe. Cela implique éventuellement de modifier la taille des machines virtuelles ou d’utiliser des groupes de machines virtuelles identiques pour adapter automatiquement le dimensionnement.
- Certaines entreprises « mettent en veille » les machines virtuelles en les programmant selon un calendrier qui spécifie quand elles doivent être disponibles et quand elles ne sont pas nécessaires.
- Outre les machines virtuelles, vous devez surveiller d’autres ressources réseau, telles qu’ExpressRoute et les passerelles de réseau virtuel pour veiller à ce que leur utilisation soit adaptée.
- Vous pouvez surveiller l’utilisation des machines virtuelles à l’aide d’outils Microsoft, tels qu’Azure Cost Management, Azure Monitor et Azure Advisor. Des outils tiers sont également disponibles.

**En savoir plus :**

- Obtenez une vue d’ensemble d’[Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) et d’[Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview).
- [Obtenez](https://docs.microsoft.com/azure/advisor/advisor-cost-recommendations) des recommandations sur les coûts de la part d’Advisor.
- [Découvrez comment [optimiser les coûts à partir des recommandations](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations) et [éviter les frais imprévus](https://docs.microsoft.com/azure/billing/billing-getting-started).
- En savoir plus sur le [kit d’outils Azure Resource Optimization (ARO)](https://github.com/azure/azure-quickstart-templates/tree/master/azure-resource-optimization-toolkit).

## <a name="best-practice-implement-resource-group-budgets"></a>Bonne pratique : implémenter des budgets de groupe de ressources

Souvent, les groupes de ressources sont utilisés pour représenter des limites de coût. Avec ce modèle d’utilisation, l’équipe Azure continue d’innover et d’améliorer ses offres pour suivre et analyser les dépenses à différents niveaux, y compris la possibilité de créer des budgets pour les ressources et les groupes de ressources.

- Un budget de groupe de ressources vous permet de suivre les coûts associés à un groupe de ressources.
- Vous pouvez déclencher des alertes et exécuter un large éventail de playbooks lorsque le budget est atteint ou dépassé.

**En savoir plus :**

- [Apprenez à gérer](https://docs.microsoft.com/azure/billing/billing-cost-management-budget-scenario) les coûts avec Azure Budgets.
- [Suivez un tutoriel](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets) pour créer et gérer un budget Azure.

## <a name="best-practice-optimize-azure-monitor-retention"></a>Bonne pratique : optimiser la rétention d’Azure Monitor

Lorsque vous déplacez des ressources dans Azure et activez la journalisation des diagnostics, vous générez un gros volume de données de journal. En général, ces données de journal d’activité sont envoyées à un compte de stockage mappé avec un espace de travail Log Analytics.

- Plus la période de rétention de données de journal est longue, plus vous aurez de données.
- Toutes les données de journal ne sont pas identiques, et certaines ressources génèrent plus de données de journal que d’autres.
- En raison des réglementations et de la conformité, il est probable que vous devrez conserver les données de journal de certaines ressources plus longtemps que d’autres.
- Vous devez trouver le bon équilibre entre l’optimisation des coûts de stockage de journal et la rétention des données de journal dont vous avez besoin.
- Nous vous recommandons d’évaluer et de configurer la journalisation immédiatement après une migration, afin de ne pas gaspiller de l’argent en conservant des journaux d’activité sans importance.

**En savoir plus :**

- [Apprenez-en plus sur](https://docs.microsoft.com/azure/azure-monitor/platform/usage-estimated-costs) la surveillance de l’utilisation et l’estimation des coûts.

## <a name="best-practice-optimize-storage"></a>Bonne pratique : optimiser le stockage

Si vous avez suivi les meilleures pratiques pour la sélection du stockage avant la migration, vous en constatez probablement les bénéfices. Toutefois, il peut exister des coûts de stockage supplémentaires que vous pouvez toujours optimiser. Au fil du temps, les objets blob et les fichiers deviennent obsolètes. Des données peuvent ne plus être utilisées, mais les exigences réglementaires vous obligent parfois à les conserver pendant un certain temps. Par conséquent, vous n’avez pas forcément à les placer dans le stockage hautes performances que vous avez utilisé pour la migration d’origine.

L’identification des données périmées et leur déplacement vers des zones de stockage plus économiques peuvent avoir un impact considérable sur votre budget de stockage mensuel et vous permettre de faire des économies. Azure offre de nombreux moyens pour vous aider à identifier et à stocker ces données périmées.

- Tirez parti des niveaux d’accès pour le stockage à usage général v2, avec le déplacement des données moins importantes du niveau Chaud vers les niveaux Froid et Archivé.
- Utilisez StorSimple pour déplacer des données périmées en fonction de stratégies personnalisées.

**En savoir plus :**

- [Apprenez-en plus](https://docs.microsoft.com/azure/storage/blobs/storage-blob-storage-tiers) sur les niveaux d’accès.
- [Obtenez une vue d’ensemble](https://docs.microsoft.com/azure/azure-monitor/overview) de StorSimple et de la [tarification StorSimple](https://azure.microsoft.com/pricing/details/storsimple).

## <a name="best-practice-automate-vm-optimization"></a>Bonne pratique : automatiser l’optimisation des machines virtuelles

L’objectif ultime de l’exécution d’une machine virtuelle dans le cloud consiste à optimiser l’UC, la mémoire et le disque qu’elle utilise. Si vous découvrez des machines virtuelles qui ne sont pas optimisées ou pas souvent utilisées, il est judicieux de les arrêter ou de réduire l’échelle en utilisant des groupes de machines virtuelles identiques.

Vous pouvez optimiser une machine virtuelle avec Azure Automation, des groupes de machines virtuelles identiques, l’arrêt automatique et des solutions tierces ou scriptées.

**En savoir plus :**

- [Découvrez comment](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-vertical-scale-reprovision) utiliser la mise à l’échelle automatique verticale.
- [Planifiez](https://azure.microsoft.com/updates/azure-devtest-labs-schedule-vm-auto-start) un démarrage automatique de machine virtuelle.
- [Découvrez comment](https://docs.microsoft.com/azure/automation/automation-solution-vm-management) démarrer ou arrêter des machines virtuelles hors des heures d’activité dans Azure Automation.
- Obtenez des informations supplémentaires sur [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) et le [kit d’outils Azure Resource Optimization (ARO)](https://github.com/azure/azure-quickstart-templates/tree/master/azure-resource-optimization-toolkit).

## <a name="best-practices-use-logic-apps-and-runbooks-with-budgets-api"></a>Meilleure pratique : utiliser des applications logiques et des runbooks avec l’API Budgets

Azure fournit une API REST qui a accès à vos informations de facturation client.

- Vous pouvez utiliser l’API Budgets pour intégrer des systèmes externes et des flux de travail déclenchés par les mesures que vous générez à partir des données de l’API.
- Vous pouvez extraire les données d’utilisation et de ressources dans vos outils d’analyse de données préférés.
- Les API d’utilisation des ressources Azure et RateCard peuvent vous aider à prévoir vos coûts avec précision et à les gérer.
- Les API sont implémentées en tant que fournisseur de ressources et incluses dans les API exposées par Azure Resource Manager.
- L’API Budgets peut être intégrée à Azure Logic Apps et aux runbooks.

**En savoir plus :**

- [Apprenez-en plus](https://docs.microsoft.com/rest/api/consumption/budgets) sur l’API Budget.
- [Obtenez des informations](https://docs.microsoft.com/azure/billing/billing-usage-rate-card-overview) dans l’utilisation d’Azure avec l’API de facturation.

## <a name="best-practice-implement-serverless-technologies"></a>Bonne pratique : implémenter des technologies serverless

Les charges de travail de machine virtuelle sont souvent migrées « en l’état » afin d’éviter les temps d’arrêt. Souvent les machines virtuelles peuvent héberger des tâches intermittentes, à exécution rapide ou très lente. Par exemple, des machines virtuelles qui exécutent des tâches planifiées, comme un planificateur de tâches Windows ou des scripts PowerShell. Lorsque ces tâches ne sont pas en cours d’exécution, vous absorbez néanmoins les coûts de machine virtuelle et de stockage sur disque.

Après la migration, suite à un examen approfondi de ces types de tâches, vous pouvez envisager de les migrer vers des technologies serverless, comme les travaux Azure Batch ou Azure Functions. Avec cette solution, vous n’avez plus besoin de gérer et de maintenir les machines virtuelles, ce qui vous permet de réaliser des économies supplémentaires.

**En savoir plus :**

- En savoir plus sur [Azure Functions](https://azure.microsoft.com/services/functions).
- En savoir plus sur [Azure Batch](https://azure.microsoft.com/services/batch).

## <a name="next-steps"></a>Étapes suivantes

Passez en revue d’autres meilleures pratiques :

- [Meilleures pratiques](./migrate-best-practices-security-management.md) relatives à la sécurité et à la gestion après la migration.
- [Meilleures pratiques](./migrate-best-practices-networking.md) relatives au réseau après la migration.
