---
title: Métriques d’accélération du déploiement, indicateurs et tolérance au risque
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Métriques d’accélération du déploiement, indicateurs et tolérance au risque
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5049b41abc03c5f59d0d750373b48a39b0638084
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031241"
---
# <a name="deployment-acceleration-metrics-indicators-and-risk-tolerance"></a>Métriques d’accélération du déploiement, indicateurs et tolérance au risque

Cet article vise à vous aider à quantifier la tolérance au risque de l’activité en lien avec l’accélération du déploiement. La définition de métriques et d’indicateurs vous aide à créer une étude de rentabilité pour investir dans la maturité de la discipline Accélération du déploiement.

## <a name="metrics"></a>Mesures

La discipline Accélération du déploiement se concentre sur les risques liés à la configuration, au déploiement, à la mise à jour et à la maintenance des ressources cloud. Les informations suivantes sont utiles lors de l’adoption de cette discipline de gouvernance cloud :

- **Échecs de déploiement :** Pourcentage de déploiements qui échouent ou qui débouchent sur des ressources mal configurées.
- **Temps de déploiement :** Il s’agit du temps nécessaire pour déployer des mises à jour sur un système existant.
- **Ressources non conformes :** Il s’agit du nombre ou du pourcentage de ressources non conformes avec les stratégies définies.

## <a name="risk-tolerance-indicators"></a>Indicateurs de tolérance au risque

Les risques liés à l’accélération du déploiement dépendent en grande partie du nombre et de la complexité des systèmes cloud qui sont déployés pour votre entreprise. Plus votre patrimoine cloud s’agrandit, plus le nombre de systèmes déployés et la fréquence de mise à jour de vos ressources cloud augmentent. Avec les dépendances entre les ressources, il est de plus en plus important de veiller à ce que les ressources soient correctement configurées et de concevoir des systèmes capables de résilience, particulièrement lorsqu’une ou plusieurs ressources subissent des temps d’arrêt imprévus.

<!-- "en-us" location is required for the URL below. -->

Envisagez d’adopter une culture organisationnelle de type DevOps ou [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) au tout début de votre parcours d’adoption du cloud. L’organisation informatique classique des entreprises sépare souvent les équipes chargées des opérations, de la sécurité et du développement. Bien souvent, ces équipes ne collaborent pas ou sont même hostiles les unes envers les autres. C’est en reconnaissant ces défis au tout début du processus et en intégrant les parties prenantes principales de chacune des équipes que vous pouvez favoriser l’agilité dans votre adoption du cloud, tout en gardant la main sur la sécurité et la gouvernance.

Collaborez avec votre équipe DevSecOps et les parties prenantes de l’entreprise pour identifier les [risques commerciaux](./business-risks.md) liés à la configuration, puis déterminez une ligne de base acceptable pour configurer la tolérance au risque. Cette section des instructions du Framework d’adoption du cloud fournit des exemples, mais les risques et les bases de référence détaillés pour votre entreprise ou vos déploiements risquent d’être différents.

Une fois que vous avez une base de référence, établissez des seuils minimaux représentant une augmentation inacceptable de vos risques identifiés. Ces seuils font office de déclencheurs lorsque vous devez prendre des mesures pour corriger ces risques. Voici quelques exemples montrant comment des métriques liées à la configuration, comme celles décrites ci-dessus, peuvent justifier un investissement accru dans la discipline Accélération du déploiement.

- **Déclencheurs relatifs aux dérives de configuration :** Lorsque les principaux composants système d’une entreprise subissent des changements de configuration inattendus, des défaillances lors du déploiement ou des mises à jour de système, l’entreprise doit investir dans la discipline Accélération du déploiement pour identifier les causes racine et définir les actions correctives.
- **Déclencheurs relatifs à la non-conformité :** Si le nombre de ressources non conformes dépasse un seuil défini (soit un nombre total de ressources ou un pourcentage), l’entreprise doit investir dans les améliorations de la discipline Accélération du déploiement pour garantir que la configuration des ressources reste conforme tout au long du cycle de vie des ressources en question.
- **Déclencheurs relatifs au calendrier du projet :** Si le temps de déploiement des ressources et des applications d’une entreprise dépasse souvent un seuil défini, l’entreprise doit investir dans ses processus Accélération du déploiement pour introduire des déploiements automatisés appliqués à la cohérence et à la prévisibilité, ou bien les améliorer. Les temps de déploiement qui sont mesurés en jours ou en semaines indiquent généralement qu’une stratégie Accélération du déploiement n’est pas optimale.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de gestion cloud ](./template.md), documenter les métriques et les indicateurs de tolérance correspondant au plan d’adoption du cloud actuel.

Considérez les exemples de stratégies d’accélération du déploiement comme des points de départ permettant de développer des stratégies qui répondent à des risques métier spécifiques, dans la continuité de vos plans d’adoption du cloud.

> [!div class="nextstepaction"]
> [Examiner les exemples de stratégies](./policy-statements.md)