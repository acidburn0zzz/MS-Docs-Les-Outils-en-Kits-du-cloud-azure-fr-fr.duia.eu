---
title: Opérations de plateforme en gestion cloud
description: Développez une compréhension de la dépendance au sein de votre organisation pour les opérations de plateforme courantes dans la gestion cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: d9c493436196a8cf95453d1822dfa43df0fa6b5c
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83755986"
---
# <a name="platform-operations-in-cloud-management"></a>Opérations de plateforme en gestion cloud

Une base de référence de gestion cloud qui comprend [l’inventaire et la visibilité](./inventory.md), [la conformité opérationnelle](./operational-compliance.md) et [la protection et la récupération](./protect.md) fournit dans certains cas un niveau de gestion cloud suffisant pour la plupart des charges de travail d’un portefeuille informatique. Toutefois, elle suffit rarement pour l’intégralité du portefeuille. Cet article s’appuie sur les opérations de portefeuille, qui correspondent le plus souvent à l’étape d’après dans la gestion cloud.

Une étude rapide des ressources du portefeuille informatique met en évidence des motifs dans les charges de travail prises en charge. Ces charges de travail comprennent des plateformes courantes. En fonction des décisions techniques qui ont été prises au sein de l’entreprise, ces plateformes peuvent être très différentes.

Certaines organisations présentent une forte dépendance envers SQL Server, Oracle ou d’autres plateformes de données open source. Dans d’autres, les points communs se trouvent au niveau des plateformes d’hébergement des machines virtuelles ou des conteneurs. D’autres encore peuvent avoir une dépendance commune à des applications ou à des systèmes ERP (Enterprise Resource Planning) comme SAP ou Oracle.

En prenant connaissance de ces similitudes, l’équipe de gestion cloud peut se spécialiser dans des niveaux supérieurs de prise en charge de ces plateformes prioritaires.

## <a name="establish-a-service-catalog"></a>Établir un catalogue de services

L’objectif des opérations de plateforme est de créer des solutions fiables et reproductibles, utilisables par une équipe d’adoption du cloud dans le but de proposer une plateforme qui offre un niveau d’engagement supérieur. Cet engagement est susceptible de réduire la probabilité ou la fréquence des temps d’arrêt, ce qui améliore la fiabilité. En cas de défaillance du système, il peut également limiter la quantité de données perdues et le délai de récupération. Il comprend souvent des opérations centralisées et régulières qui viennent soutenir la plateforme.

À mesure que l’équipe de gestion cloud établit de plus hauts niveaux de gestion et de spécialisation des opérations pour certaines plateformes, ces plateformes sont régulièrement ajoutées à un catalogue de services. Le catalogue de services permet le déploiement en libre-service des plateformes dans une configuration précise, qui respecte les opérations de plateforme en cours. Lors des discussions concernant l’alignement des activités, les équipes de gestion cloud et de stratégie cloud peuvent proposer des solutions de catalogue de services afin d’améliorer les engagements de fiabilité, de durée de fonctionnement et de récupération de l’entreprise dans le cadre d’un processus contrôlé et reproductible.

Pour information, certaines organisations appellent _liste approuvée_ la première version du catalogue de services. La principale différence réside dans le fait qu’un catalogue de services s’accompagne des engagements opérationnels permanents du Cloud Center of Excellence (CCoE). Une liste approuvée est similaire en ce qu’elle constitue une liste préapprouvée de solutions qu’une équipe peut utiliser dans le cloud. Toutefois, il n’y a en général pas d’avantages opérationnels associés aux applications d’une liste approuvée.

Comme avec l’informatique centralisée et le Cloud Center of Excellence (CCoE), la différence se situe au niveau de priorités. Un catalogue de services suppose une bonne intention, mais il fournit une barrière de sécurité au niveau des opérations, de la gouvernance et de la sécurité, ce qui accélère l’innovation. Une liste approuvée entrave l’innovation tant que les portes des opérations, de la conformité et de la sécurité ne sont pas franchies pour une solution donnée. Les deux solutions sont viables, mais elles obligent l’entreprise à prendre des décisions subtiles concernant les priorités, afin d’investir davantage dans l’innovation ou bien dans la conformité.

### <a name="build-the-service-catalog"></a>Créer le catalogue de services

La gestion cloud est rarement efficace pour fournir un catalogue de services dans un silo. Un partenariat est nécessaire au sein de l’informatique centralisée ou du CCoE pour développer un catalogue adéquat. Cette approche est généralement plus efficace lorsqu’une organisation informatique atteint un niveau de maturité CCoE, même si elle peut être implémentée plus tôt.

En cas de création du catalogue de services dans un modèle CCoE, l’équipe chargée des plateformes cloud élabore la plateforme à l’état souhaité. Les équipes chargées de la gouvernance et de la sécurité cloud valident la gouvernance et la conformité au sein du déploiement. L’équipe de gestion cloud établit des opérations en cours pour cette plateforme. L’équipe chargée de l’automatisation cloud crée un package pour la plateforme afin de permettre un déploiement scalable et reproductible.

Une fois la plateforme mise en package, l’équipe de gestion cloud peut l’ajouter au catalogue de services. L’équipe d’adoption du cloud peut alors utiliser le package ou d’autres packages du catalogue pendant le déploiement. Une fois la solution mise en production, l’entreprise bénéficie des avantages supplémentaires que présentent l’amélioration de la gestion opérationnelle et la potentielle réduction des interruptions de l’activité.

> [!NOTE]
> La création d’un catalogue de services nécessite beaucoup d’efforts et de temps pour plusieurs équipes. Le recours au catalogue de services ou à la liste approuvée comme mécanismes de porte a pour effet de ralentir l’innovation. Lorsque l’innovation est une priorité, les catalogues de services doivent être développés parallèlement aux autres efforts d’adoption.

## <a name="define-your-own-platform-operations"></a>Définir ses propres opérations de plateforme

Bien que les outils et les processus de gestion puissent contribuer à améliorer les opérations de plateforme, ils restent souvent insuffisants pour atteindre les états de stabilité et de fiabilité souhaités. De véritables opérations de plateforme exigent de se concentrer sur les piliers de la qualité de l’architecture. Quand une plateforme justifie un investissement plus important au niveau des opérations, les cinq principes suivants doivent être pris en compte avant que la plateforme ne fasse partie d’un catalogue de services :

- **Scalabilité :** Capacité d’un système à traiter une charge accrue.
- **Disponibilité :** Pourcentage de temps pendant lequel le système est fonctionnel et opérationnel.
- **Résilience :** Capacité d’un système à récupérer après des défaillances et à continuer de fonctionner.
- **Gestion :** Processus opérationnels assurant l’exécution d’un système en production.
- **Sécurité :** Protection des applications et des données contre les menaces.

Le [Microsoft Azure Well-Architected Framework](https://docs.microsoft.com/azure/architecture/guide/pillars) fournit une méthode permettant de vérifier si les charges de travail suivent ces principes, en vue d'améliorer les opérations globales. Ces principes peuvent être appliqués aussi bien aux opérations de plateforme qu’aux opérations de charge de travail.

## <a name="get-started-with-specific-platforms"></a>Bien démarrer avec des plateformes spécifiques

Les plateformes abordées dans les sections suivantes, courantes chez les clients Azure classiques, peuvent facilement justifier un investissement dans les opérations de plateforme. Les équipes de gestion cloud ont tendance à commencer par ces plateformes lorsqu’elles élaborent des exigences d’opérations de plateforme ou un catalogue de services complet.

### <a name="paas-data-operations"></a>Opérations de données PaaS

Les données constituent souvent la première plateforme qui garantit les investissements en opérations de plateforme. Lorsque les données sont hébergées dans un environnement PaaS (Platform as a service), les parties prenantes de l’entreprise ont tendance à demander un objectif de point de récupération (RPO) relativement bas afin de réduire la perte de données. Selon la nature de l’application, elles peuvent également requérir une réduction de l’objectif de temps de récupération (RTO). Dans les deux cas, l’architecture des solutions de données PaaS peut facilement permettre un niveau accru de soutien à la gestion.

Dans la plupart des scénarios, le coût d’amélioration des engagements de gestion est facilement justifié, même pour les applications non stratégiques. Cette amélioration des opérations de plateforme est si courante que de nombreuses équipes de gestion cloud la voient plus comme une base de référence améliorée que comme un véritable perfectionnement des opérations de plateforme.

### <a name="iaas-data-operations"></a>Opérations de données IaaS

Lorsque les données sont hébergées dans une solution IaaS (Infrastructure as a service) classique, l’effort d’amélioration du RPO et du RTO peut se révéler beaucoup plus conséquent. Pourtant, la volonté des parties prenantes de l’entreprise d’atteindre de meilleurs engagements de gestion est rarement affectée par le choix entre une solution PaaS et une solution IaaS. En fait, le fait de prendre connaissance des différences fondamentales d’architecture peut amener l’entreprise à exiger des solutions PaaS ou des engagements qui correspondent aux caractéristiques des solutions PaaS. La modernisation des plateformes de données IaaS doit être considérée comme une première étape dans les opérations de plateforme.

Lorsque la modernisation n’est pas possible, les équipes de gestion cloud donnent généralement la priorité aux plateformes de données IaaS, en les considérant comme le premier service obligatoire du catalogue de services. Lorsque l’entreprise a le choix entre des serveurs de données autonomes et des solutions de données en cluster haute disponibilité, l’animation des discussions concernant ses engagements s’en trouve grandement facilitée. Une fois familiarisée avec les améliorations opérationnelles et l’augmentation des coûts, l’entreprise aura toutes les clés en main pour prendre la meilleure décision en ce qui concerne les processus d’entreprise et les charges de travail associées.

### <a name="other-common-platform-operations"></a>Autres opérations de plateforme courantes

En plus des plateformes de données, les hôtes de machines virtuelles constituent souvent une plateforme commune pour les améliorations d’opérations. La plupart du temps, les équipes chargées de la gestion cloud et des plateformes cloud investissent dans l’amélioration des hôtes VMware ou des solutions de conteneur. Ces investissements peuvent améliorer la stabilité et la fiabilité des hôtes qui gèrent les machines virtuelles, qui elles font tourner les charges de travail. Le bon fonctionnement d’un hôte ou d’un conteneur est susceptible d’améliorer le RPO ou le RTO de plusieurs charges de travail. Cette approche permet de créer des engagements métier améliorés, mais elle répartit l’investissement. Le perfectionnement des engagements comme la réduction des coûts facilitent grandement la justification des améliorations apportées à la gestion cloud et aux opérations de plateforme.

## <a name="next-steps"></a>Étapes suivantes

Parallèlement à l’amélioration des opérations de plateforme, les équipes de gestion cloud se concentrent sur le perfectionnement des [opérations de charge de travail](./workload.md) des premiers 20 % (ou moins) parmi les meilleures charges de travail de production.

> [!div class="nextstepaction"]
> [Améliorer les opérations de charge de travail](./workload.md)
