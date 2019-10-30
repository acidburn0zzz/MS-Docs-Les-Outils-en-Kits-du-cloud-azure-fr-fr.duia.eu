---
title: Opérations de plateforme - Gestion cloud et opérations
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Opérations de plateforme - Gestion cloud et opérations
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: ca62f35c059e185850bb47045fa0edef7be1d223
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683594"
---
# <a name="platform-operations-in-cloud-management"></a>Opérations de plateforme en gestion cloud

Une base de référence de gestion cloud comprenant l’[inventaire et la visibilité](./inventory.md), la [conformité opérationnelle](./operational-compliance.md) et la [protection et la récupération](./protect.md) peut fournir un niveau de gestion cloud suffisant pour la plupart des charges de travail d’un portefeuille informatique. Toutefois, cela suffit rarement pour l’intégralité du portefeuille. Cet article s’appuie sur les opérations de portefeuille, qui correspondent le plus souvent à l’étape d’après dans la gestion cloud.

Une étude rapide des ressources du portefeuille informatique met en évidence les éléments qui se répètent dans les charges de travail prises en charge. Ces charges de travail comprennent plusieurs plateformes courantes. En fonction des décisions d’ordre technique qui ont été prises au sein de l’entreprise, ces plateformes peuvent être très différentes. Pour certaines organisations, il y aura une forte dépendance envers SQL Server, Oracle ou d’autres plateformes de données open source. Dans d’autres organisations, les points communs se trouvent au niveau des plateformes d’hébergement des machines virtuelles ou des conteneurs. D’autres encore peuvent avoir une dépendance commune aux applications ou aux systèmes ERP, tels que SAP, Oracle, etc.

La connaissance de ces points communs permet à l’équipe de gestion cloud de se spécialiser dans des niveaux supérieurs de prise en charge pour les plateformes prioritaires.

## <a name="establish-a-service-catalog"></a>Établir un catalogue de services

L’objectif des opérations de plateforme est de créer des solutions fiables et reproductibles qui peuvent être utilisées par une équipe d’adoption cloud afin de fournir une plateforme proposant un niveau d’engagement plus élevé. Cet engagement peut réduire la probabilité ou la fréquence des temps d’arrêt, ce qui améliore la fiabilité. L’engagement peut également réduire la quantité de données perdues ou la durée de récupération en cas de défaillance du système. Cet engagement comprend souvent des opérations centralisées en cours pour prendre en charge la plateforme.

À mesure que l’équipe de gestion cloud établit de plus hauts niveaux de gestion et de spécialisation des opérations pour certaines plateformes, ces plateformes sont régulièrement ajoutées à un catalogue de services. Ce catalogue de services permet le déploiement en libre-service des plateformes dans une configuration précise, qui respecte les opérations de plateforme en cours. Lors des discussions concernant l’alignement des activités, les équipes de gestion cloud et de stratégie cloud peuvent proposer des solutions de catalogue de services afin d’améliorer la fiabilité, la durée de fonctionnement et la récupération dans le cadre d’un processus contrôlé et reproductible.

Pour informations, certaines organisations appellent « liste approuvée » la première version du catalogue de services. La principale différence réside dans le fait qu’un catalogue de services est fourni avec les engagements opérationnels en cours du Cloud Center of Excellence. Une « liste approuvée » est similaire en ce sens qu’elle fournit une liste pré-approuvée de solutions que l’équipe peut utiliser dans le cloud. Toutefois, les applications de « liste approuvée » ne présentent généralement pas d’avantages opérationnels. Comme avec l’informatique centralisée et le Cloud Center of Excellence (CCoE), la différence se situe au niveau de priorités. Un catalogue de services suppose une bonne intention, mais il fournit une barrière de sécurité au niveau des opérations, de la gouvernance et de la sécurité, ce qui accélère l’innovation. Une « liste approuvée » entrave l’innovation tant que les barrières des opérations, de la conformité et de la sécurité ne sont pas franchies pour une solution. Ces deux solutions sont viables, mais elles nécessitent que l’entreprise prenne des décisions subtiles concernant les priorités, afin d’investir davantage dans l’innovation ou la conformité.

### <a name="building-the-service-catalog"></a>Création du catalogue de services

La gestion cloud est rarement efficace pour fournir un catalogue de services dans un silo. La création d’un catalogue adéquat nécessite un partenariat entre l’informatique centralisée et le Cloud Center of Excellence (CCoE). Cette approche est généralement plus efficace lorsqu’une organisation informatique atteint un niveau de maturité CCoE, même si elle peut être implémentée plus tôt.

Lors de la création du catalogue de services dans un modèle CCoE, l’équipe de plateforme cloud crée la plateforme à l’état souhaité. Les équipes chargées de la gouvernance et de la sécurité cloud valident la gouvernance et la conformité au sein du déploiement. L’équipe de gestion cloud établit des opérations en cours pour cette plateforme. L’équipe chargée de l’automatisation cloud crée un package pour la plateforme afin de permettre un déploiement scalable et reproductible.

Une fois la plateforme mise en package, l’équipe de gestion cloud peut ajouter le package au catalogue de services. À partir de là, l’équipe d’adoption cloud peut tirer parti de ce package ou d’autres packages inclus dans le catalogue pendant le déploiement. Une fois la solution mise en production, l’entreprise bénéficie des avantages supplémentaires que présente la gestion opérationnelle améliorée, ainsi que du potentiel de la réduction des interruptions de service.

> [!NOTE]
> La création d’un catalogue de services nécessite beaucoup d’efforts et de temps pour plusieurs équipes. L’utilisation du catalogue de services ou de la liste verte comme mécanismes de passerelle ralentit l’innovation. Lorsque l’innovation est une priorité, les catalogues de services doivent être développés parallèlement aux autres efforts d’adoption.

## <a name="defining-your-own-platform-operations"></a>Définition de vos propres opérations de plateforme

Les outils et processus de gestion peuvent améliorer les opérations de plateforme. Mais souvent, cela ne suffit pas pour atteindre l’état souhaité de stabilité et de fiabilité. Les véritables opérations de plateforme nécessitent que l’on se concentre sur les principes de qualité de l’architecture. Quand une plateforme justifie un investissement plus important au niveau des opérations, les cinq principes suivants doivent être pris en compte avant que la plateforme ne fasse partie d’un catalogue de services :

1. Scalabilité : Capacité d’un système à traiter une charge accrue.
2. Disponibilité : Durée pendant laquelle le système est fonctionnel et opérationnel.
3. Résilience : Capacité d’un système à récupérer après des défaillances et à continuer de fonctionner.
4. Gestion : Processus d’opérations assurant l’exécution d’un système en production.
5. Sécurité : Protection des applications et des données contre les menaces.

Le [Centre des architectures Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) fournit une méthode permettant de vérifier si les charges de travail suivent ces principes, en vue d’améliorer les opérations globales. Ces principes peuvent être appliqués aussi bien aux opérations de plateforme qu’aux opérations de charge de travail.

## <a name="getting-started-with-specific-platforms"></a>Bien démarrer avec les plateformes spécifiques

Chez les clients Azure classiques, les plateformes suivantes sont courantes et peuvent facilement justifier un investissement dans les opérations de plateforme. Les équipes de gestion cloud ont tendance à commencer par ces opérations lorsqu’elles créent des exigences d’opérations de plateforme ou un catalogue de services complet.

### <a name="paas-data-operations"></a>Opérations de données PaaS

Les données constituent souvent la première plateforme qui garantit les investissements en opérations de plateforme. Lorsque les données sont hébergées dans un environnement PaaS (Platform as a service), les parties prenantes de l’entreprise ont tendance à demander un RPO relativement bas afin de réduire la perte de données. Selon la nature de l’application, elles peuvent également demander une réduction du RTO. Dans les deux cas, l’architecture qui prend en charge les solutions de données PaaS peut facilement permettre un niveau accru de prise en charge de la gestion.

Dans la plupart des scénarios, le coût d’amélioration des engagements de gestion est facilement justifié, même pour les applications qui ne sont pas stratégiques. Cette amélioration des opérations de plateforme est si courante que de nombreuses équipes de gestion cloud la voient plus comme une base de référence améliorée que comme une véritable amélioration des opérations de plateforme.

### <a name="iaas-data-operations"></a>Opérations de données IaaS

Lorsque les données sont hébergées dans une solution IaaS, l’effort d’amélioration du RTO et du RPO peut être beaucoup plus élevé. Pourtant, les parties prenantes de l’entreprise souhaitant obtenir de meilleurs engagements de gestion sont rarement affectées par le choix entre une solution PaaS et une solution IaaS. Parfois, la connaissance des différences fondamentales d’architecture peut amener l’entreprise à exiger des solutions PaaS ou des engagements qui correspondent aux solutions PaaS disponibles. La modernisation des plateformes de données IaaS doit être considérée comme une première étape dans les opérations de plateforme.

Lorsque la modernisation n’est pas possible, les équipes de gestion cloud donnent généralement la priorité aux plateformes de données IaaS, en les considérant comme le premier service obligatoire du catalogue de services. Lorsque l’entreprise a le choix entre les serveurs de données autonomes et les solutions de données en cluster haute disponibilité, les discussions concernant les engagements sont grandement facilitées. Une connaissance de base des améliorations opérationnelles et de l’augmentation des coûts va aider l’entreprise à prendre la meilleure décision en ce qui concerne les processus métiers et la prise en charge des charges de travail.

### <a name="other-common-platform-operations"></a>Autres opérations de plateforme courantes

En plus des plateformes de données, les hôtes de machines virtuelles constituent souvent une plateforme commune pour les améliorations d’opérations. La plupart du temps, les équipes de gestion cloud et de plateforme cloud investissent dans l’amélioration des hôtes VMWare ou des solutions de conteneur afin d’améliorer la stabilité et la fiabilité des hôtes qui prennent en charge les machines virtuelles, qui elles, alimentent les charges de travail. Le fait d’exécuter des opérations appropriées sur un hôte ou un conteneur peut améliorer le RPO/RTO de plusieurs charges de travail. Cette approche permet de créer des engagements métier améliorés, mais elle répartit l’investissement. Ensemble, les engagements améliorés et les coûts réduits facilitent grandement la justification des améliorations apportées à la gestion cloud et aux opérations de plateforme.

## <a name="next-steps"></a>Étapes suivantes

Parallèlement aux améliorations apportées aux opérations de plateforme, les équipes de gestion cloud se concentreront également sur l’amélioration des [opérations de charge de travail](./workload.md) pour les 20 % (ou moins) de charges de travail de production.

> [!div class="nextstepaction"]
> [Améliorer les opérations de charge de travail](./workload.md)
