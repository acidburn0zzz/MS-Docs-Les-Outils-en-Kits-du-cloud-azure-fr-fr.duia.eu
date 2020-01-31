---
title: Corriger les ressources avant la migration
description: Corriger les ressources incompatibles avant la migration
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 23045cf48dd26400bbad07bbde927e29c3189f8d
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802104"
---
# <a name="remediate-assets-prior-to-migration"></a>Corriger les ressources avant la migration

Pendant le processus d’évaluation de la migration, l’équipe cherche à identifier les configurations qui rendraient une ressource incompatible avec le fournisseur de cloud choisi. La *correction* est un point de contrôle dans le processus de migration pour s’assurer que ces incompatibilités ont été résolues. Cet article présente quelques tâches de correction courantes à des fins de référence. Il établit également un processus squelette pour décider si la correction est un investissement judicieux.

## <a name="common-remediation-tasks"></a>Tâches de correction courantes

Dans tous les environnements d’entreprise existe une dette technique. Dans une certaine mesure, cela est sain et normal. Les décisions architecturales particulièrement adaptées à un environnement local peuvent ne pas convenir parfaitement à une plateforme cloud. Dans un cas comme dans l’autre, des tâches de correction courantes peuvent être nécessaires pour préparer les ressources à la migration. Voici quelques exemples :

- **Mises à niveau mineures de l’hôte.** Parfois, un hôte obsolète doit être mis à niveau avant la réplication.
- **Mises à niveau mineures du système d’exploitation invité.** Il est plus probable qu’un système d’exploitation ait besoin de correctifs ou de mises à niveau avant la réplication.
- **Modifications du SLA.** La sauvegarde et la récupération changent considérablement dans une plateforme cloud. Il est probable que les ressources nécessitent des modifications mineures de leurs processus de sauvegarde pour garantir le fonctionnement continu du cloud.
- **Migration PaaS.** Dans certains cas, le déploiement PaaS d’une structure de données ou d’une application peut être nécessaire pour accélérer le déploiement. Des modifications mineures peuvent être nécessaires pour préparer la solution au déploiement PaaS.
- **Modifications du code PaaS.** Il n’est pas rare que des applications personnalisées requièrent des modifications mineures du code pour être prêtes pour le modèle PaaS. Les exemples peuvent inclure des méthodes qui écrivent sur un disque local ou utilisent l’état de session en mémoire, entre autres.
- **Modifications de la configuration de l’application.** Les applications migrées peuvent nécessiter des modifications de variables, telles que les chemins d’accès réseau aux ressources dépendantes, les modifications de compte de service ou les mises à jour des adresses IP dépendantes.
- **Modifications mineures apportées aux chemins d’accès réseau.** Il peut être nécessaire de modifier les modèles de routage pour acheminer correctement le trafic utilisateur vers les nouvelles ressources.
    > [!NOTE]
    > Il ne s'agit pas d'un routage de production vers les nouvelles ressources, mais d'une configuration permettant un routage approprié vers les ressources en général.

## <a name="large-scale-remediation-tasks"></a>Tâches de correction à grande échelle

Lorsqu’un centre de données est correctement entretenu et mis à jour et qu’il reçoit les correctifs appropriés, il est peu probable qu’il soit nécessaire de le corriger. Les environnements riches en corrections tendent à être courants dans les grandes entreprises, les organisations qui ont subi une importante réduction des effectifs informatiques, certains environnements de services managés hérités et les environnements riches en acquisitions. Dans chacun de ces types d’environnements, la correction peut consommer une grande partie de l’effort de migration. Lorsque les tâches de correction suivantes apparaissent fréquemment et nuisent à la vitesse ou à la cohérence de la migration, il peut être judicieux de scinder la correction en un effort et une équipe parallèles (de la même façon que l’adoption du cloud et la gouvernance cloud s’exécutent en parallèle).

- **Mises à niveau fréquentes de l’hôte.** Quand un grand nombre d’hôtes doivent être mis à niveau pour terminer la migration d’une charge de travail, l’équipe de migration risque de subir des retards. Il peut être judicieux de libérer les applications concernées et de traiter les corrections avant d’inclure les applications concernées dans les mises en production planifiées.
- **Mise à niveau fréquente du système d’exploitation invité.** Les grandes entreprises ont généralement des serveurs s’exécutant sur des versions obsolètes de Linux ou Windows. Outre les risques de sécurité évidents liés à l’exploitation d’un système d’exploitation obsolète, il existe également des problèmes d’incompatibilité qui empêchent la migration des charges de travail concernées. Quand un grand nombre de machines virtuelles requièrent une correction du système d’exploitation, il peut être judicieux de répartir ces efforts dans une itération parallèle.
- **Modifications majeures du code.** Les applications personnalisées plus anciennes peuvent nécessiter beaucoup plus de modifications pour les préparer au déploiement PaaS. Dans ce cas, il peut être judicieux de les supprimer entièrement du backlog de migration et de les gérer dans un programme complètement séparé.

## <a name="decision-framework"></a>Infrastructure de décision

Bien qu’il soit facile de corriger des charges de travail plus petites, c’est l’une des raisons pour lesquelles il est recommandé de choisir une charge de travail plus petite pour votre migration initiale. Toutefois, à mesure que vos efforts de migration arrivent à maturité et que vous commencez à faire face à des charges de travail plus importantes, la correction peut s’avérer un processus long et coûteux. Par exemple, les efforts de correction pour une migration de Windows Server 2003 impliquant un pool de ressources de plus de 5 000 machines virtuelles peuvent retarder une migration de plusieurs mois. Lorsqu’une correction de cette envergure est requise, les questions suivantes peuvent aider à prendre des décisions :

- Toutes les charges de travail concernées par la correction ont-elles été identifiées et annotées dans le backlog de migration ?
- Pour les charges de travail qui ne sont pas concernées, une migration produira-t-elle un retour sur investissement (ROI) similaire ?
- Les ressources concernées peuvent-elles être corrigées en fonction de la chronologie de la migration d’origine ? Quel impact les changements de chronologie auraient-ils sur le ROI ?
- Est-il possible économiquement de corriger les ressources parallèlement aux efforts de migration ?
- Le personnel dispose-t-il d’une bande passante suffisante pour effectuer une correction et une migration ? Un partenaire devrait-il être engagé pour exécuter l’une ou l’autre des tâches ou les deux ?

Si ces questions ne débouchent pas sur des réponses favorables, il peut être judicieux d’envisager d’autres approches qui vont au-delà d’une stratégie de réhébergement IaaS de base :

- **Mise en conteneur.** Certaines ressources peuvent être hébergées dans un environnement en conteneur sans être corrigées. Cela peut produire des niveaux de performance peu favorables et ne résout pas les problèmes de sécurité ou de conformité.
- **Automatisation.** Selon les exigences de charge de travail et de correction, il peut être plus rentable de générer un script du déploiement sur les nouvelles ressources à l’aide d’une approche DevOps.
- **Régénération.** Lorsque les coûts de correction sont très élevés et que la valeur commerciale est tout aussi élevée, une charge de travail peut être une bonne candidate à la régénération ou à la réarchitecture.

## <a name="next-steps"></a>Étapes suivantes

Une fois la correction terminée, les [activités de réplication](./replicate.md) sont prêtes.

> [!div class="nextstepaction"]
> [Répliquer les ressources](./replicate.md)
