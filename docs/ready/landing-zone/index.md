---
title: Qu’est-ce qu’une zone d’accueil ?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez en quoi les zones d’accueil constituent les éléments constitutifs de tout environnement d’adoption du cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 6db16b50115f2ba145dd4980dc5d57867f438de7
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78228357"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-a-landing-zone"></a>Qu’est-ce qu’une zone d’accueil ?

L’infrastructure as code (IaC) est une transition naturelle durant la plupart des opérations d’adoption du cloud. Le déploiement de vos premières zones d’accueil dans le cloud est généralement le point de départ pour la transition vers la création d’un environnement Code First. Cet article vous aidera à bien comprendre le sens du terme _zone d’accueil_ et d’autres termes connexes.

## <a name="landing-zone-definition"></a>Définition de la zone d’accueil

Une zone d’accueil est l’élément constitutif de tout environnement d’adoption du cloud. Le terme _zone d’accueil_ fait référence à une construction logique qui capture tous les prérequis à l’adoption du cloud souhaitée.

**Étendue :** une zone d’accueil pleinement opérationnelle prend en compte toutes les ressources de plateforme requises pour répondre aux besoins d’adoption du client.

**Refactorisation :** une zone d’accueil pleinement opérationnelle est le livrable final de toutes les itérations de la méthodologie Préparer du Framework d’adoption du cloud. À chaque itération, le code base qui définit la zone d’accueil est refactorisé ou étendu. Après la refactorisation, la zone d’accueil peut être modifiée ou redéployée pour être adaptée à de nouveaux besoins d’adoption du cloud.

**Objectif :** la zone d’accueil est une approche qui vise à créer un ensemble commun d’implémentations de plateforme cohérentes. Ces implémentations cohérentes doivent être mises en place pour que vos applications puissent accéder aux composants dont elles auront besoin une fois déployées. Chaque itération de zone d’accueil doit donc être conçue et déployée en conformité avec les exigences du plan d’adoption du cloud et de la stratégie de conception des abonnements.

**Objectif principal :** la zone d’accueil a pour principal objectif de garantir que « l’ossature » requise est déjà en place quand une application arrive sur Azure.

## <a name="landing-zone-usage"></a>Utilisation des zones d’accueil

Les zones d’accueil ne sont pas obligatoirement différentes pour les environnements d’adoption IaaS et PaaS. Toutefois, les zones d’accueil sont spécialement conçues pour prendre en charge le plan d’adoption qui est conforme à la stratégie d’abonnement. La prise en charge du plan d’adoption peut nécessiter l’utilisation de plusieurs zones d’accueil avec une combinaison de composants requis.

L’objectif et l’étendue du plan d’adoption global du cloud définissent « l’ossature » requise. D’autres exigences en matière de gouvernance, de conformité, de sécurité et de gestion opérationnelle sont généralement ajoutées à l’étendue initiale des zones d’accueil. Durant les premières phases de l’adoption, les zones d’accueil peuvent nécessiter une « ossature » plus légère en raison des exigences définies et des risques acceptables.  Quand il y a plusieurs zones d’accueil, la pratique courante est que chaque zone d’accueil dépende des hubs qui fournissent les contrôles requis par le biais d’un modèle de services partagés.

## <a name="related-terms"></a>Termes connexes

- **Services partagés :** les charges de travail ont souvent des dépendances qu’elles partagent avec beaucoup de charges de travail différentes. L’approche des services partagés consiste à déplacer un grand nombre de ces dépendances communes vers une construction logique unique.

- **Modèle hub-and-spoke :** le modèle hub-and-spoke est l’une des implémentations de l’approche des services partagés. Dans ce modèle, le hub est une construction logique unique qui héberge tous les services partagés. Les zones d’accueil sont ensuite utilisées comme spokes à partir du hub, sur la base des dépendances communes.

- **Zone d’accueil indépendante :** certaines approches des zones d’accueil n’appellent pas spécifiquement un hub dédié. Cela est souvent le cas quand toutes les ressources de production (applications, données et machines virtuelles) dans le plan d’adoption du cloud peuvent être hébergées, gérées et gouvernées de manière sécurisée dans le même environnement.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer à utiliser des zones d’accueil, [choisissez votre première zone d’accueil](./first-landing-zone.md).

> [!div class="nextstepaction"]
> [Choisir votre première zone d’accueil](./first-landing-zone.md)
