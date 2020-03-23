---
title: Réplication et processus de migration
description: Découvrez le rôle que joue la réplication dans le processus de migration, ainsi que la façon de planifier les prérequis et les risques associés aux activités de réplication.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 31930cfef32d4a02b3892405e2c5b462e0039566
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79312776"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-role-does-replication-play-in-the-migration-process"></a>Quel rôle la réplication joue-t-elle dans le processus de migration ?

Les centres de données locaux sont remplis de ressources physiques telles que des serveurs, des appareils et des périphériques réseau. Toutefois, chaque serveur n’est qu’un interpréteur de commandes physique. La valeur réelle provient des fichiers binaires exécutés sur le serveur. Les applications et les données sont l’objectif du centre de données. Ce sont les binaires principaux à migrer. Pour alimenter ces applications et banques de données, nous avons d’autres ressources numériques et sources binaires, comme les systèmes d’exploitation, les itinéraires réseau, les fichiers et les protocoles de sécurité.

La réplication est le principal moteur des efforts de migration. Il s’agit du processus de copie d’une version à un point dans le temps de divers binaires. Les instantanés binaires sont ensuite copiés vers une nouvelle plateforme et déployés sur un nouveau matériel, dans le cadre d'un processus appelé *amorçage*. Lorsqu’elle est exécutée correctement, la copie amorcée du fichier binaire doit se comporter de la même façon que le binaire d’origine sur l’ancien matériel. Toutefois, cette capture instantanée du fichier binaire est immédiatement obsolète et mal alignée avec la source d’origine. Pour que le nouveau binaire et l’ancien restent alignés, un processus appelé *synchronisation* met continuellement à jour la copie stockée dans la nouvelle plateforme. La synchronisation se poursuit jusqu’à ce que la ressource soit promue en fonction du modèle de promotion choisi. À ce stade, la synchronisation est interrompue.

## <a name="required-prerequisites-to-replication"></a>Conditions préalables requises pour la réplication

Avant la réplication, la *nouvelle plateforme* et le nouveau matériel doivent être préparés pour recevoir les copies binaires. L’article concernant les [prérequis](../prerequisites/index.md) présente les conditions minimales requises pour créer une plateforme sécurisée, robuste et hautes performances en vue de recevoir les réplicas binaires.

Les *binaires sources* doivent également être préparés pour la réplication et la synchronisation. Les articles sur l’évaluation, l’architecture et la correction traitent chacun des actions nécessaires pour s’assurer que le fichier binaire source est prêt pour la réplication et la synchronisation.

Une *chaîne d’outils* qui s’aligne sur la nouvelle plateforme et les binaires source doit être implémentée pour exécuter et gérer les processus de réplication et de synchronisation. L’article sur les [options de réplication](./replicate-options.md) décrit les différents outils qui peuvent contribuer à une migration vers Azure.

## <a name="replication-risks---physics-of-replication"></a>Risques de réplication : Physique de la réplication

Lors de la planification de la réplication d’une source binaire vers une nouvelle destination, il existe quelques lois fondamentales à prendre sérieusement en compte lors de la planification et de l’exécution.

- **La vitesse de la lumière.** Lors du déplacement de volumes importants de données, la fibre est toujours l’option la plus rapide. Malheureusement, ces câbles peuvent uniquement déplacer des données à deux tiers de la vitesse de la lumière. Cela signifie qu’il n’existe aucune méthode pour une réplication instantanée ou illimitée des données.
- **La vitesse du pipeline WAN.** Plus la vitesse de déplacement des données est importante, plus la bande passante de liaison montante est importante, ce qui définit le volume de données par seconde qui peuvent être transférées sur le réseau étendu (WAN) existant d’une entreprise vers le centre de données cible.
- **La vitesse du développement WAN.** Si les budgets le permettent, de la bande passante supplémentaire peut être ajoutée à la solution de réseau étendu (WAN) d’une entreprise. Toutefois, il peut falloir des semaines ou des mois pour approvisionner, configurer et intégrer des connexions sur fibre supplémentaires.
- **La vitesse des disques.** Si les données peuvent se déplacer plus rapidement et qu’il n’y a pas de limite à la bande passante entre le fichier binaire source et la destination cible, les lois de la physique restent un facteur limitant. Les données peuvent seulement être répliquées aussi rapidement qu’elles peuvent être lues à partir des disques source. La lecture de chaque disque en rotation dans un centre de données prend du temps.
- **La vitesse des calculs humains.** Les disques et la lumière sont plus rapides que les processus de réflexion humaine. Lorsqu’un groupe d’êtres humains est requis pour collaborer et prendre des décisions, les résultats seront encore plus lents. La réplication ne peut jamais surmonter les retards liés à l’intelligence humaine.

Chacune de ces lois de la physique présente les risques suivants qui affectent généralement les plans de migration :

- **Temps de la réplication.** Les outils de réplication avancés ne peuvent pas surmonter les lois de base de la physique &mdash; la réplication demande du temps et de la bande passante. Les plans doivent inclure des chronologies réalistes qui reflètent la durée nécessaire à la réplication des fichiers binaires. *La bande passante totale disponible pour la migration* est la quantité de bande passante en amont, mesurée en mégabits par seconde (Mbits/s) ou en gigabits par seconde (Gbits/s), qui n’est pas consommée par d’autres besoins métier de plus haute priorité. *Le stockage total de la migration* est l’espace disque total, mesuré en gigaoctets ou en téraoctets, requis pour stocker une capture instantanée de toutes les ressources à migrer. Une estimation initiale du temps peut être calculée en divisant le *stockage total de la migration* par la *bande passante totale disponible pour la migration*. Notez la conversion des bits en octets. Reportez-vous à l’entrée suivante, « Effet cumulatif de la dérive des disques », pour un calcul plus précis du temps.
- **Effet cumulatif de la dérive des disques.** Du point de réplication à la promotion d’une ressource en production, les fichiers binaires source et de destination doivent rester synchronisés. La *dérive* des binaires consomme davantage de bande passante, car toutes les modifications apportées au fichier binaire doivent être répliquées de façon récurrente. Pendant la synchronisation, toutes les dérives binaires doivent être incluses dans le calcul de l’espace de stockage total de la migration. Plus il faut de temps pour promouvoir une ressource en production, plus la dérive cumulée se produit souvent. Plus le nombre de ressources en cours de synchronisation est grand, plus la bande passante utilisée est importante. Chaque fois qu’une ressource supplémentaire est maintenue dans un état de synchronisation, un peu plus de la bande passante totale disponible pour la migration est perdue.
- **Temps pour les changements dans l’entreprise.** Comme mentionné dans l’entrée précédente, « Effet cumulatif de la dérive des disques », le temps de synchronisation a un effet négatif cumulatif sur la vitesse de la migration. La définition des priorités du backlog de migration et la préparation avancée pour le [plan de changements dans l’entreprise](../optimize/business-change-plan.md) sont essentielles à la rapidité de la migration. Le test le plus important de l’alignement commercial et technique pendant un effort de migration est le rythme de la promotion. Plus vite une ressource peut être promue en production, plus la dérive du disque et son impact sur la bande passante est faible, et plus le temps pouvant être alloué à la réplication de la charge de travail suivante est long.

## <a name="next-steps"></a>Étapes suivantes

Une fois la réplication terminée, les [activités de préproduction](./stage.md) peuvent commencer.

> [!div class="nextstepaction"]
> [Activités de préproduction pendant une migration](./stage.md)
