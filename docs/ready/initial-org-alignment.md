---
title: Alignement initial de l’organisation
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Fournit une vue d’ensemble de l’alignement initial de l’organisation.
author: alexbuckgit
ms.author: abuck
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: governance
ms.openlocfilehash: a3e819cdd726e3df6edb4cbe0c20a7d652fde152
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70834679"
---
# <a name="initial-organization-alignment"></a>Alignement initial de l’organisation

La **transformation numérique** vers le cloud computing implique de passer d’un fonctionnement local à un fonctionnement dans le cloud. Ce changement induit de nouvelles méthodes de gestion d’une entreprise. Par exemple, la transformation numérique implique de passer de dépenses en capital pour les logiciels et les matériels de centre de données à des dépenses d’exploitation pour l’utilisation des ressources cloud. Découvrons comment utiliser le [framework d’adoption du cloud Microsoft pour Azure](../index.md).

## <a name="the-digital-transformation-process"></a>Processus de transformation numérique

Pour réussir son adoption du cloud, une entreprise doit préparer son organisation, son personnel et ses processus à cette transformation numérique. Chaque structure organisationnelle d’entreprise étant différente, aucune approche en matière de préparation organisationnelle ne conviendra à tout le monde. Ce document décrit les principales étapes que votre entreprise peut suivre pour se préparer. Votre organisation devra prendre le temps d’élaborer un plan détaillé pour réaliser chacune des étapes répertoriées.

Voici le principal processus à suivre pour la transformation numérique :

1. Constituez une équipe de stratégie cloud. Cette équipe est responsable du pilotage de la transformation numérique. À ce stade, il est également important de constituer une équipe dédiée à la gouvernance et une équipe dédiée à la sécurité pour la transformation numérique.
2. Les membres de l’équipe de stratégie cloud apprennent ce qui est nouveau et différent au sujet des technologies cloud.
3. L’équipe de stratégie cloud prépare l’entreprise en créant l’analyse de cas pour la transformation numérique ; elle énumère tous les écarts actuels de la stratégie métier et détermine les principales solutions pour les supprimer.
4. Alignez les solutions principales avec des groupes métier. Identifiez les parties prenantes dans chaque groupe métier pour être en possession de la conception et de l’implémentation de chaque solution.
5. Adaptez les rôles, compétences et processus existants pour inclure des rôles, compétences et processus cloud.

<!--6. Develop processes for operating in the cloud to make solutions more robust in terms of availability, resiliency, and security.
1. Optimize solutions for performance, scalability, and cost efficiency.-->

## <a name="step-1-create-a-cloud-strategy-team"></a>Étape 1 : Constituer une équipe de stratégie cloud

La première étape de la transformation numérique de votre entreprise est de faire appel à des leaders métier de toute l’organisation pour constituer une équipe de stratégie cloud. Cette équipe rassemble des responsables métier issus des départements des finances, des infrastructures informatiques et des groupes d’applications. Ces équipes peuvent apporter leurs compétences pour la phase d’expérimentation et d’analyse cloud.

Par exemple, une équipe de stratégie cloud peut être pilotée par le directeur technique et être composée de membres de l’équipe d’architecture d’entreprise, du département de finance et d’informatique, de techniciens experts issus de divers groupes d’applications informatiques (ressources humaines, finance, etc.) et de responsables d’équipes de mise en réseau, de sécurité et d’infrastructure.

Il est également important de former deux autres équipes principales : une équipe dédiée à la gouvernance et une équipe dédiée à la sécurité. Ces équipes sont responsables de la conception, de l’implémentation et de l’audit en cours des stratégies de sécurité et de la gouvernance de l’entreprise. L’équipe dédiée à la gouvernance a besoin de membres ayant travaillé dans les domaines de la protection des ressources, de la gestion des coûts, de la stratégie de groupe et autres sujets associés. L’équipe dédiée à la sécurité requiert des membres qui connaissent bien les normes de sécurité actuelles du secteur, ainsi que les exigences de sécurité de l’entreprise.

![Équipe de stratégie cloud, avec les équipes de sécurité et de gouvernance](../_images/getting-started-overview-1.png)

L’équipe dédiée à la gouvernance est responsable de la conception et de l’implémentation du modèle de gouvernance de l’entreprise dans le cloud, ainsi que du déploiement et du maintien des ressources d’infrastructure partagée qui font partie de la transformation numérique. Ces ressources incluent les ressources cloud, logicielles et matérielles nécessaires pour connecter le réseau local au réseau virtuel dans le cloud.

L’équipe dédiée à la sécurité est responsable de la conception et de l’implémentation de la stratégie de sécurité de l’entreprise dans le cloud et collabore étroitement avec l’équipe dédiée à la gouvernance. L’équipe dédiée à la sécurité possède l’extension de la limite de sécurité du réseau local pour inclure le réseau virtuel dans le cloud. Cela peut consister à posséder et maintenir les pare-feu entrants et sortants sur le réseau virtuel cloud, ainsi qu’à garantir que la stratégie et les outils empêchent le déploiement des ressources non autorisées.

## <a name="step-2-learn-whats-new-in-the-cloud"></a>Étape 2 : Découvrir les nouveautés dans le cloud

L’étape suivante de la transformation numérique de votre entreprise implique que les membres de l’équipe de stratégie cloud apprennent comment la technologie cloud va changer la méthode de gestion de l’entreprise. Il s’agit de préparer et de planifier les changements qui vont affecter votre activité, votre personnel et vos technologies. Il est essentiel que les membres de l’équipe de stratégie cloud comprennent les nouveautés et les différences entre un environnement cloud et un environnement local.

![Les équipes chargées de la stratégie cloud, de la gouvernance et de la sécurité découvrent les meilleures pratiques d’utilisation du cloud.](../_images/getting-started-overview-2.png)

Pour comprendre le cloud, il faut commencer par se pencher sur le [fonctionnement d’Azure](../getting-started/what-is-azure.md) en général. Ensuite, étudiez les bases de [la gouvernance dans Azure](../governance/resource-consistency/what-is-governance.md) en préparation de la [compréhension de la gestion des accès aux ressources](../governance/resource-consistency/azure-resource-access.md).

Pour en apprendre davantage, l’équipe dédiée à la gouvernance doit passer en revue les guides de conception et les concepts dans la section sur la gouvernance de la table des matières. Les sections portant sur l’infrastructure et les charges de travail sont utiles pour en savoir plus sur les architectures et charges de travail classiques dans le cloud.

## <a name="step-3-identify-gaps-in-business-strategy"></a>Étape 3 : Identifier les écarts dans la stratégie métier

L’étape suivante s’adresse à l’équipe de stratégie cloud : elle doit énumérer les problèmes métier qui nécessitent une solution de transformation numérique. Par exemple, une entreprise peut avoir un centre de données local existant avec un matériel en fin de vie qui doit être remplacé. Dans un autre exemple, une entreprise peut rencontrer des difficultés pour commercialiser des fonctionnalités et services nouveaux et être en retard sur la concurrence. Ces écarts représentent les _objectifs_ de la transformation numérique de votre entreprise.

Ils peuvent être classés dans les catégories suivantes :

| Category | Description |
| --- | --- |
| la gestion des coûts ; | Représente un écart dans la façon dont l’entreprise paie pour la technologie. |
| Gouvernance | Représente un écart dans les processus utilisés par l’entreprise pour protéger ses ressources d’une utilisation incorrecte qui peut entraîner des surcoûts, des problèmes de sécurité ou des problèmes de conformité. |
| Conformité | Représente un écart dans la façon dont l’entreprise respecte ses processus et stratégies internes, ainsi que les normes, réglementations et lois externes. |
| Sécurité | Représente un écart dans la façon dont l’entreprise protège ses ressources de données et technologies des menaces externes. |
| Gouvernance des données | Représente un écart dans la façon dont une entreprise gère ses données, notamment les données client. Par exemple, le nouveau Règlement général sur la protection des données (RGPD) de l’Union européenne contient des exigences strictes en matière de protection des données client qui peuvent nécessiter de nouveaux matériels et logiciels. |

Une fois que votre entreprise a classé tous les écarts de stratégie métier dans ces catégories, l’étape suivante consiste à identifier une solution principale pour chaque problème.

Le tableau suivant fournit plusieurs exemples :

|Écart de stratégie métier|Catégorie &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;|Solution &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|-----|-----|-----|
| Des services actuellement hébergés en local rencontrent des problèmes de disponibilité, de résilience et d’extensibilité pendant les pics de demande, ce qui représente environ 10 % de l’utilisation. Des serveurs du centre de données local sont en fin de vie. Le département informatique de l’entreprise recommande l’achat de nouveaux matériels locaux pour le centre de données avec des spécifications pour gérer les pics de demande.| la gestion des coûts ; | Migrez les charges de travail locales existantes affectées vers des ressources évolutives dans le cloud, en payant uniquement pour l’utilisation. |
| Des réglementations et lois de gestion des données externes exigent que l’entreprise respecte un ensemble de contrôles standard qui nécessitent le chiffrement des données au repos, et donc de nouveaux matériels et logiciels. | Gouvernance des données | Migrez les données vers Azure Storage Service Encryption pour les données au repos. |
| Des services hébergés dans un centre de données local ont été confrontés à des attaques par déni de service distribué (DDoS) sur les services accessibles au public. Les attaques sont difficiles à atténuer et nécessitent de nouveaux matériels, logiciels et personnels de sécurité pour être traitées de manière efficace. | Sécurité | Migrez les services vers Azure et profitez de la protection DDoS Azure.|

Une fois tous les écarts de la stratégie métier énumérés et les solutions principales déterminées, classez la liste par ordre de priorité. Pour ce faire, vous pouvez aligner les écarts de la stratégie métier avec les objectifs à court et long termes de l’entreprise pour chaque catégorie. Par exemple, si l’entreprise a un objectif à court terme de réduction des dépenses informatiques des deux prochains trimestres, les écarts métiers dans la catégorie *Gestion des coûts* peuvent être classés par ordre de priorité en se basant sur les économies prévues associées à chacun des écarts.

À l’issue de ce processus, vous obtenez une liste classée des solutions principales alignées avec les catégories métier.

## <a name="step-4-align-high-level-solutions-with-business-groups-to-design-solutions"></a>Étape 4 : Aligner les solutions principales avec des groupes métier pour concevoir des solutions

Maintenant que les objectifs de la transformation numérique ont été énumérés, classés par ordre de priorité et que des solutions principales ont été proposées, l’étape suivante pour l’équipe de stratégie cloud consiste à aligner chaque solution principale avec les équipes d’implémentation et de conception de chaque groupe métier.

Les équipes récupèrent les listes classées par ordre de priorité et étudient une à une les solutions principales pour concevoir chaque solution. Le processus de conception implique la spécification d’une nouvelle infrastructure et de nouvelles charges de travail. Des modifications peuvent être appliquées aux rôles des personnes et aux processus qu’elles suivent. À ce stade, il est aussi important que chaque équipe de conception fasse appel aux équipes dédiées à la sécurité et à la gouvernance pour examiner chaque conception. Toutes les conceptions doivent respecter les stratégies et procédures définies par les équipes dédiées à la sécurité et à la gouvernance, et ces dernières doivent participer à l’approbation finale de chaque conception.

![L’équipe chargée de la stratégie cloud fournit des solutions de haut niveau aux équipes de conception et d’implémentation.](../_images/getting-started-overview-3.png)

La conception de chaque solution est une tâche non triviale. À mesure que les conceptions sont créées, elles doivent être considérées dans le contexte des autres conceptions de solution des autres équipes. Par exemple, si plusieurs des conceptions entraînent la migration de services et d’applications locaux existants vers le cloud, il peut s’avérer plus efficace de les regrouper et de concevoir une stratégie de migration globale. Dans un autre exemple, il peut être impossible de migrer certains services et applications locaux existants, et la solution pourrait être de les remplacer par un nouveau développement ou des services tiers. Dans ce cas, il peut être plus efficace de les regrouper et de déterminer de quelle façon ils se chevauchent pour identifier si un service tiers peut être utilisé pour plusieurs solutions.

Une fois la conception de la solution terminée, l’équipe passe à la phase d’implémentation de chaque conception. La phase d’implémentation de chaque conception de solution peut être effectuée via des processus de gestion de projets standard.

## <a name="step-5-adapt-existing-roles-skills-and-process-for-the-cloud"></a>Étape 5 : Adapter les rôles, compétences et processus existants pour le cloud

Lors de chaque phase de l’histoire du secteur informatique, les changements les plus notables sont souvent observés au niveau des rôles du personnel. Pendant la transition des mainframes au modèle client/serveur, le rôle de l’opérateur informatique a largement disparu, remplacé par celui de l’administrateur système. À l’arrivée de la virtualisation, la demande en personnel travaillant avec des serveurs physiques a diminué, remplacée par un besoin en spécialistes de la virtualisation. De même, à mesure que les institutions passent au cloud computing, les rôles vont probablement changer. Par exemple, les spécialistes de centres de données peuvent être remplacés par des analystes financiers du cloud. Même dans les cas où l’intitulé des postes informatiques n’a pas changé, les rôles de travail quotidien ont considérablement évolué.

Les membres du personnel informatique peuvent s’inquiéter quant à leur poste et rôle quand ils se rendent compte qu’un ensemble de compétences différent est nécessaire pour prendre en charge les solutions cloud. Mais les employés agiles qui découvrent et explorent les nouvelles technologies cloud n’ont pas à ressentir cette peur. Ils peuvent piloter l’adoption des services cloud et aider l’organisation à comprendre et appréhender les changements associés.

### <a name="capturing-concerns"></a>Recueil des préoccupations

Lors de la transformation numérique, chaque équipe doit recueillir les préoccupations que le personnel peut avoir. Au cours de cette opération, identifiez les aspects suivants :

- **Le type de préoccupation.** Par exemple, les employés peuvent être réfractaires aux changements apportés à leurs tâches suite à la transformation numérique.
- **L’impact de la préoccupation si elle n’est pas traitée.** Par exemple, le fait d’être réfractaire à la transformation numérique peut entraîner un ralentissement des employés pour effectuer les changements nécessaires.
- **Le domaine compétent pour traiter la préoccupation.** Par exemple, si les employés du département informatique sont réticents à acquérir de nouvelles compétences, le domaine des parties prenantes informatiques est le plus compétent pour traiter cette préoccupation. Identifier le domaine peut être simple pour certains problèmes, et dans ce genre de situation, vous avez peut-être besoin de faire remonter l’information à la direction.

### <a name="identify-gaps"></a>Identifier les écarts

Un autre aspect de l’étude des problèmes liés à la transformation numérique de votre entreprise est l’identification des **écarts**. Un écart est un rôle, une compétence ou un processus requis pour votre transformation numérique qui n’existe actuellement pas dans votre entreprise.

Commencez en énumérant les nouvelles responsabilités qui accompagnent la transformation numérique, en mettant l’accent sur les nouvelles responsabilités et les responsabilités actuelles à supprimer. Identifiez le domaine qui s’aligne sur chaque responsabilité. Pour les nouvelles responsabilités, déterminez à quel point elles sont alignées avec le domaine. Certaines responsabilités peuvent s’étendre sur plusieurs domaines, et cela représente une opportunité d’alignement meilleur qui doit être collectée en tant que préoccupation. Dans le cas où aucun domaine responsable ne peut être identifié, recueillez cela comme un écart.

Ensuite, identifiez les compétences nécessaires pour prendre en charge la responsabilité. Déterminez si votre entreprise possède des ressources existantes avec ces compétences. En l’absence de ressources existantes, déterminez quels programmes de formation ou recrutements sont nécessaires. Déterminez l’intervalle de temps durant lequel la responsabilité doit être prise pour respecter le calendrier de votre transformation numérique.

Enfin, identifiez les rôles qui mettront en pratique ces compétences. Certains de vos effectifs existants assureront une partie du rôle, et dans d’autres cas, un nouveau rôle pourra être nécessaire.

### <a name="partner-across-teams"></a>Collaborer avec les équipes

Les compétences nécessaires pour combler les écarts dans la transformation numérique de votre organisation ne se cantonneront généralement pas à un seul rôle, ni à un seul département. Les compétences ont des liens et des dépendances qui peuvent s’étendre à un ou plusieurs rôles, et ces rôles peuvent exister dans divers départements. Par exemple, un propriétaire de charge de travail peut avoir besoin qu’une personne ayant un rôle informatique approvisionne des ressources principales comme des groupes de ressources et des abonnements.

Ces dépendances représentent les nouveaux processus que votre organisation implémente pour gérer le flux de travail entre les rôles. Dans l’exemple ci-dessus, il existe différents types de processus pouvant prendre en charge la relation entre le propriétaire de la charge de travail et le rôle informatique. Par exemple, un outil de flux de travail peut être créé pour gérer le processus, ou un simple modèle d’e-mail peut être utilisé.

Suivez ces dépendances et notez les processus qui les prendront en charge, et indiquez si le processus existe actuellement ou non. Pour les processus qui nécessitent des outils, assurez-vous que la chronologie pour le déploiement de ceux-ci s’aligne sur la planification de la transformation numérique globale.

## <a name="next-steps"></a>Étapes suivantes

La transformation numérique est un processus itératif, et avec chaque itération, les équipes impliquées deviendront plus efficaces.

> [!div class="nextstepaction"]
> [Comprendre le fonctionnement d’Azure](../getting-started/what-is-azure.md)
