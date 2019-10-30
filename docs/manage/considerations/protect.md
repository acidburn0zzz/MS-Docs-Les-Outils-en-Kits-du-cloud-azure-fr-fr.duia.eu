---
title: Protéger et récupérer – Gestion et opérations du cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Protéger et récupérer – Gestion et opérations du cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 2e055cb6105b9424259d2b8e86bdde7d64798479
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682451"
---
# <a name="protect-and-recover-in-cloud-management"></a>Protéger et récupérer dans la gestion cloud

Une fois que les exigences relatives à [l’inventaire et à la visibilité](./inventory.md) ainsi qu’à la [conformité opérationnelle](./operational-compliance.md) ont été satisfaites, les équipes de gestion du cloud peuvent se tourner vers l’avenir et se préparer à l’éventualité d’une panne de la charge de travail. Lors de la planification de la gestion du cloud, l’équipe doit partir de l’hypothèse qu’une opération échouera.

Aucune solution technique ne peut offrir constamment un contrat SLA dont la durée de fonctionnement est de 100 %. Les solutions aux architectures les plus redondantes affirment fournir une durée de fonctionnement de « six 9 », soit de 99,9999 %. Cependant, même une solution à « six 9 » tombe en panne pendant 31,6 secondes dans une année donnée. Malheureusement, il est rare que des solutions justifient l’investissement opérationnel important et continu nécessaire pour atteindre « six 9 » de durée de fonctionnement.

La préparation d’une panne permet à l’équipe de détecter les défaillances plus tôt et de récupérer plus rapidement. Cette discipline est axée sur les étapes suivantes qui surviennent après la défaillance d’un système. Comment protéger les charges de travail afin qu’elles puissent être récupérées rapidement en cas de panne.

## <a name="translating-protection-and-recovery-conversations"></a>Traduction des conversations de protection et de récupération

Les charges de travail qui alimentent les opérations d’entreprise sont constituées d’applications, de données, de machines virtuelles et d’autres ressources. Chacune de ces ressources peut nécessiter une approche différente de la protection et de la récupération. L’aspect important de cette discipline est d’établir un engagement cohérent dans le cadre de la ligne de base relative à la gestion, afin de fournir un point de départ au cours des discussions commerciales.

Au minimum, chaque ressource prenant en charge une charge de travail donnée doit avoir une approche de base avec un engagement clair concernant la vitesse de récupération (objectifs de délai de récupération ou RTO) et le risque de perte de données (objectifs de point de récupération ou RPO).

### <a name="recovery-time-objectives-rto"></a>Objectifs de délai de récupération (RTO)

En cas de sinistre, le RTO est le laps de temps nécessaire pour récupérer un système donné à son état précédant l’incident. Pour chaque charge de travail, cela inclut le temps requis pour restaurer les fonctionnalités minimales nécessaires pour les machines virtuelles et les applications. Il comprend également le temps nécessaire pour restaurer les données requises par les applications.

En termes commerciaux, le RTO représente la durée pendant laquelle le processus d’entreprise sera hors service. Pour les charges de travail stratégiques, cette variable doit être relativement faible, ce qui permet une reprise rapide des processus d’entreprise. Pour les charges de travail de priorité plus basse, un niveau standard de RTO peut ne pas avoir d’impact notable sur le niveau de performance de l’entreprise.

La ligne de base relative à la gestion doit établir un objectif de délai de récupération standard pour les charges de travail non stratégiques. L’entreprise peut ensuite utiliser cette ligne de base pour justifier des investissements supplémentaires en matière de délais de récupération.

### <a name="recovery-point-objectives-rpo"></a>Objectifs de point de récupération (RPO)

Dans la plupart des systèmes de gestion du cloud, les données sont capturées et stockées régulièrement grâce à une certaine forme de protection des données. Le point de récupération désigne la dernière fois que les données ont été capturées. En cas de défaillance d’un système, celui-ci peut être restauré uniquement au point de récupération le plus récent.

Si un système a un objectif de point de récupération mesuré en heures ou en jours, une défaillance du système entraînerait la perte de données pour ces heures ou jours entre le dernier point de récupération et la panne. Un RPO d’un jour entraînerait théoriquement la perte de toutes les transactions dans la journée précédant la défaillance.

Pour les systèmes stratégiques, un RPO mesuré en minutes ou en secondes peut être plus approprié pour éviter une perte de revenus. Toutefois, un RPO plus court entraîne généralement une augmentation des coûts de gestion globaux.

Une ligne de base relative à la gestion doit se concentrer sur le RPO acceptable le plus long pour réduire les coûts. L’équipe de gestion du cloud peut alors augmenter le RPO de plateformes ou de charges de travail spécifiques, ce qui justifie davantage d’investissements.

## <a name="protect-and-recover-workloads"></a>Protéger et récupérer des charges de travail

La plupart des charges de travail dans un environnement informatique prennent en charge un processus d’entreprise ou technique très petit. Les systèmes qui n’ont pas d’impact systémique sur les opérations d’entreprise ne justifient souvent pas les investissements accrus nécessaires à la récupération rapide ou à la réduction de la perte de données. L’établissement d’une ligne de base permet à l’entreprise de comprendre clairement quel niveau de support relatif à la récupération peut être offert à un tarif cohérent et facile à gérer. Cela aide les parties prenantes de l’entreprise à déterminer la valeur d’un investissement accru en matière de récupération.

Pour la plupart des équipes de gestion du cloud, une ligne de base améliorée avec des engagements RPO/RTO spécifiques pour différentes ressources offre la voie la plus favorable aux engagements commerciaux réciproques. Les sections suivantes décrivent quelques lignes de base améliorées courantes qui permettent à l’entreprise d’ajouter facilement des fonctionnalités de protection et de récupération par le biais d’un processus reproductible.

### <a name="protect-and-recover-data"></a>Protection et récupération des données

Les données constituent sans doute la ressource la plus précieuse dans l’économie numérique. La possibilité de protéger et de récupérer des données de manière plus efficace est la ligne de base améliorée la plus courante. Pour les données qui alimentent une charge de travail en production, la perte de données peut être directement comparée à la perte de revenus ou de rentabilité. Il est généralement recommandé que les équipes de gestion du cloud offrent un niveau de ligne de base relative à la gestion améliorée qui prend en charge les plateformes de données courantes.

Avant d’implémenter des opérations de plateforme, il est courant pour les équipes de gestion du cloud de prendre en charge des opérations améliorées pour une plateforme de données PaaS. Par exemple, il est facile pour une équipe de gestion du cloud d’imposer une plus grande fréquence de sauvegarde ou de réplication multirégionale pour les solutions Azure SQL ou Cosmo DB. De cette façon, l’équipe de développement peut facilement améliorer le RPO en modernisant simplement ses plateformes de données.

Ce raisonnement sera revu plus en détail dans le cadre de la [discipline des opérations relatives aux plateformes](./platform.md).

### <a name="protect-and-recover-vms"></a>Protection et récupération des machines virtuelles

La plupart des charges de travail dépendent dans une certaine mesure des machines virtuelles. Ces machines virtuelles hébergent différents aspects de la solution. Pour que la charge de travail prenne en charge un processus d’entreprise après une défaillance du système, un certain nombre de ces machines virtuelles doivent être récupérées rapidement.

Chaque minute de temps d’arrêt de ces machines virtuelles peut s’assimiler à une perte de revenus ou à une rentabilité réduite. Lorsque le temps d’arrêt des machines virtuelles a un impact direct sur le rendement budgétaire de l’entreprise, le RTO est très important. Les machines virtuelles peuvent être récupérées plus rapidement grâce à la réplication sur un site secondaire et à la récupération automatisée. Ce modèle est appelé « mode de récupération à chaud/tiède ». Au plus haut niveau de récupération, les machines virtuelles peuvent être répliquées sur un site secondaire entièrement fonctionnel. Cette approche plus coûteuse est appelée mode de récupération à chaud ou à haute disponibilité.

Chacun des modèles ci-dessus réduit l’objectif de délai de récupération, ce qui permet de restaurer plus rapidement les capacités des processus d’entreprise. Toutefois, chaque modèle entraîne également des coûts de gestion cloud considérablement accrus.

Ce raisonnement sera revu plus en détail dans le cadre de la [discipline des opérations relatives aux charges de travail](./workload.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois que ce composant de la ligne de base relative à la gestion a été atteint, l’équipe peut anticiper les pannes afin de les éviter en exécutant des [opérations relatives aux plateformes](./platform.md) et des [opérations relatives aux charges de travail](./workload.md).

> [!div class="nextstepaction"]
> [Opérations relatives aux plateformes](./platform.md)
> [Opérations relatives aux charges de travail](./workload.md)
