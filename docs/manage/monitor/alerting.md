---
title: 'Guide de supervision du cloud : Génération d’alertes'
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à déterminer quand utiliser Azure Monitor ou System Center Operations Manager dans Microsoft Azure.
author: MGoedtel
ms.author: magoedte
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 0f9c71ec1ee9ce258def9abb297e89567399aeb9
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83400811"
---
<!-- cSpell:ignore kusto multiresource multisignal -->

# <a name="cloud-monitoring-guide-alerting"></a>Guide de supervision du cloud : Génération d’alertes

Pendant des années, les organisations informatiques ont rencontré des difficultés pour combattre la lassitude liée aux alertes créées par les outils de supervision déployés dans l’entreprise. De nombreux systèmes génèrent un grand volume d’alertes souvent considérées comme non significatives, tandis que d’autres sont pertinentes, mais sont négligées ou ignorées. En conséquence, les opérations assurées par le département informatique et les développeurs ont eu du mal à respecter la qualité de niveau de service promise aux clients internes ou externes. Il est essentiel de comprendre l’état de votre infrastructure et de vos applications pour en garantir la fiabilité. Vous devez identifier les causes rapidement de façon à minimiser la dégradation et les interruptions du service, ou pour réduire l’effet ou le nombre d’incidents.

## <a name="successful-alerting-strategy"></a>Stratégie d’alerte réussie

*On ne peut pas régler un problème quand on ne sait pas qu’il existe.*

Déclencher des alertes sur ce qui est important est critique. Ceci est sous-entendu par la collecte et la mesure des métriques et des journaux appropriés. Vous avez également besoin d’un outil de supervision capable de stocker, d’agréger, de visualiser, d’analyser et de produire une réponse automatique quand certaines conditions sont remplies. Vous pouvez améliorer l’observabilité de vos services et de vos applications seulement si vous comprenez pleinement leur composition. Vous mappez cette composition dans une configuration de supervision détaillée à appliquer par la plateforme de supervision. Cette configuration inclut les états de défaillance prévisibles (les symptômes qui ne sont pas la cause de la défaillance) pour lesquels les alertes sont justifiées.

Tenez compte des principes suivants pour déterminer si un symptôme est un candidat approprié pour une alerte :

- **Est-il important ?** Le problème est-il symptomatique d’un problème réel ou d’un problème influençant l’intégrité globale de l’application ? Par exemple, une utilisation élevée du processeur sur la ressource est-elle une préoccupation ? Un autre exemple est celui d’une requête SQL particulière s’exécutant sur une instance de base de données SQL sur cette ressource et entraînant une forte utilisation du processeur pendant une période prolongée. Comme la condition d’utilisation du processeur est un problème réel, vous devez alerter sur celui-ci. Mais vous n’avez pas besoin d’en informer l’équipe, car cela ne sert à rien d’indiquer la cause première du problème. Alerte et notifier à propos du problème d’utilisation du processus de requête SQL est à la fois pertinent et exploitable.
- **Est-ce urgent ?** Le problème est-il réel et nécessite-t-il une attention de façon urgente ? Si oui, l’équipe responsable doit être immédiatement notifiée.
- **Vos clients sont-ils affectés ?** Les utilisateurs du service ou de l’application sont-ils affectés suite au problème ?
- **D’autres systèmes dépendants sont-ils affectés ?** Existe-t-il des alertes provenant de dépendances qui sont interdépendantes et qui peuvent éventuellement être corrélées pour éviter de notifier différentes équipes sur le même problème ?

Posez-vous ces questions quand vous développez initialement une configuration de supervision. Testez et validez les hypothèses dans un environnement hors production, puis déployez-les en production. Les configurations de supervision sont dérivées de modes de défaillance connus, de résultats des tests de défaillances simulées et de l’expérience de différents membres de l’équipe.

Après la publication de votre configuration de supervision, vous pouvez en apprendre beaucoup sur ce qui fonctionne et sur ce qui ne fonctionne pas. Examinez les volumes élevés d’alertes, les problèmes non signalés par la supervision mais remarqués par les utilisateurs finaux, ainsi que les meilleures actions qui ont été entreprises dans le cadre de cette évaluation. Identifiez les changements à implémenter pour améliorer la fourniture des services dans le cadre d’un processus continu d’amélioration de la supervision. Il ne s’agit pas seulement de l’évaluation des alertes inutiles ou des alertes manquées, mais également de l’efficacité de la supervision de la charge de travail. Cela concerne l’efficacité de vos stratégies d’alerte, de vos processus et de votre culture globale pour déterminer si vous vous améliorez.

System Center Operations Manager et Azure Monitor prennent tous deux en charge les alertes basées sur des seuils statiques ou même sur des seuils dynamiques, et les actions configurées pour ces alertes. Les alertes par e-mail, par SMS et par appels vocaux pour des notifications simples en sont des exemples. Ces deux services prennent également en charge l’intégration de la gestion des services informatiques (ITSM), afin d’automatiser la création d’enregistrements d’incidents et de remonter les problèmes à l’équipe de support appropriée ou à tout autre système de gestion des alertes utilisant un webhook.

Quand c’est possible, vous pouvez utiliser un des nombreux services permettant d’automatiser les actions de récupération. Il s’agit notamment de System Center Orchestrator, d’Azure Automation, d’Azure Logic Apps ou de la mise à l’échelle automatique dans le cas de charges de travail élastiques. Si envoyer des notifications aux équipes responsables est l’action la plus courante pour les alertes, automatiser les actions correctives peut également être approprié. Cette automatisation peut aider à rationaliser l’ensemble du processus de gestion des incidents. L’automatisation de ces tâches de récupération peut également réduire le risque d’une erreur humaine.

## <a name="azure-monitor-alerting"></a>Alertes Azure Monitor

Si vous utilisez Azure Monitor exclusivement, suivez ces instructions lorsque vous prenez en compte la vitesse, le coût et le volume de stockage.

En fonction des fonctionnalités et de la configuration utilisées, vous pouvez stocker les données de supervision dans l’un des six référentiels :

- **Base de données des métriques Azure Monitor :** Base de données de séries chronologiques utilisée principalement pour les métriques de la plateforme Azure Monitor, mais les données des métriques d’Application Insights y sont également reflétées. Les informations entrées dans cette base de données ont les délais d’alerte les plus rapides.

- **Magasin des journaux Application Insights :** Base de données qui stocke la plupart des données de télémétrie d’Application Insights sous forme de journaux.

- **Magasin des journaux Azure Monitor :** Magasin principal pour les données des journaux Azure. D’autres outils peuvent y envoyer des données, qui peuvent être analysées dans les journaux Azure Monitor. En raison des opérations d’ingestion et d’indexation, les requêtes sur les alertes des journaux ont une latence plus élevée. Cette latence est généralement de 5 à 10 minutes, mais elle peut être plus élevée dans certaines circonstances.

- **Magasin des journaux d’activité :** Utilisé pour tous les événements des journaux d’activités et d’intégrité du service. Les alertes dédiées sont possibles. Contient les événements de niveau abonnement qui se produisent sur les objets de votre abonnement, tels qu’ils sont vus de l’extérieur de ces objets. Par exemple, quand une stratégie est définie, ou en cas d’accès ou de suppression d’une ressource.

- **Stockage Azure :** Stockage universel pris en charge par Diagnostics Azure et d’autres outils de supervision. Il s’agit d’une option à bas coût pour la conservation à long terme de la télémétrie de supervision. Les alertes ne sont pas prises en charge à partir des données stockées dans ce service.

- **Event Hubs :** Généralement utilisé pour diffuser en continu des données dans des outils de supervision ou ITSM locaux ou d’autres partenaires.

Azure Monitor possède quatre types d’alertes, toutes globalement liées au référentiel où les données sont stockées :

- [Alerte de métrique](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric) : Alerte sur les données de la base de données des métriques Azure Monitor. Les alertes sont déclenchées quand une valeur supervisée dépasse un seuil défini par l’utilisateur, puis quand elle revient à un état « normal ».

- [Alerte de requête sur un journal](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-log-query) : Disponible pour les alertes sur le contenu des magasins de journaux Application Insights ou Azure. Elle peut également alerter en fonction de requêtes portant sur plusieurs espaces de travail.

- [Alerte de journal d’activité](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-activity-log) : Alerte sur les éléments du magasin de journaux d’activités, à l’exception des données de Service Health.

- [Alerte Service Health](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-activity-log-service-notifications) : Type spécial d’alerte utilisé seulement pour les problèmes Service Health provenant du magasin de journaux d’activité, comme les pannes et la maintenance planifiée à venir. Notez que ce type d’alerte est configuré via [Azure Service Health](https://docs.microsoft.com/azure/service-health/service-health-overview), un service associé à Azure Monitor.

### <a name="enable-alerting-through-partner-tools"></a>Activer les alertes via des outils partenaires

Si vous utilisez une solution d’alertes externes, routez autant que possible via Azure Event Hubs, le chemin le plus rapide pour sortir d’Azure Monitor. Vous devrez payer pour l’ingestion dans le hub d’événements. Si le coût est un problème et que la rapidité ne l’est pas, vous pouvez utiliser Stockage Azure comme alternative moins coûteuse. Vérifiez simplement que vos outils de supervision ou ITSM peuvent lire dans Stockage Azure pour extraire les données.

Azure Monitor prend en charge l’intégration à d’autres plateformes de supervision et à des logiciels ITSM comme ServiceNow. Vous pouvez utiliser les alertes Azure et néanmoins déclencher des actions en dehors d’Azure, si votre processus de gestion des incidents ou DevOps l’exige. Si vous voulez alerter dans Azure Monitor et automatiser la réponse, vous pouvez lancer des actions automatisées avec Azure Functions, Azure Logic Apps ou Azure Automation, selon votre scénario et vos exigences.

### <a name="specialized-azure-monitoring-offerings"></a>Offres de supervision Azure spécialisées

En général, les [solutions de gestion](https://docs.microsoft.com/azure/azure-monitor/insights/solutions-inventory) stockent leurs données dans le magasin de journaux Azure. Les deux exceptions sont Azure Monitor pour machines virtuelles et Azure Monitor pour conteneurs. Le tableau suivant décrit l’expérience des alertes basée sur le type de données particulier et sur l’emplacement où il est stocké.

| Solution | Type de données | Comportement des alertes |
|---| ---| --- |
| Azure Monitor pour des conteneurs | Les données des performances moyennes calculées à partir des nœuds et des pods sont écrites dans le magasin de métriques. | Créez des alertes de métrique si vous voulez être alerté en fonction de la variation des performances d’utilisation mesurées et agrégées sur une période donnée. |
| | Les données de performances calculées qui utilisent des centiles provenant de nœuds, de contrôleurs, de conteneurs et de pods sont écrites dans le magasin de journaux. Les journaux de conteneur et les informations d’inventaire sont également écrits dans le magasin de journaux. | Créez des alertes de requête de journal si vous voulez être alerté en fonction de la variation de l’utilisation mesurée des clusters et des conteneurs. Les alertes de requête de journal peuvent également être configurées en fonction des nombres de phases de pods et des nombres de nœuds d’état. |
Azure Monitor pour machines virtuelles | Les critères d’intégrité sont des métriques écrites dans le magasin de métriques. | Des alertes sont générées quand l’état d’intégrité passe d’une condition saine à une condition non saine. Cette alerte prend seulement en charge les groupes d’actions configurés pour envoyer des notifications par SMS ou par e-mail. |
| | Les données du journal de performances du système d’exploitation de mappage et invité sont écrites dans le magasin de journaux. | Créez des alertes de requête de journal. |

<!-- docsTest:ignore "speed driven by cost" -->

### <a name="fastest-speed-driven-by-cost"></a>Vitesse la plus rapide pilotée par le coût

La latence est une des décisions les plus critiques nécessitant des alertes et la résolution rapide des problèmes affectant votre service. Si vous avez besoin d’alertes en quasi temps réel dans les cinq minutes, évaluez d’abord si vous avez ou si vous pouvez recevoir des alertes sur vos données de télémétrie là où elles sont stockées par défaut. En général, cette stratégie est également l’option la moins chère, car l’outil que vous utilisez envoie déjà ses données à cet emplacement.

Cela dit, quelques nuances importantes sont à considérer pour cette règle.

La **télémétrie du système d’exploitation invité** parvient au système selon différentes voies.

- Le moyen le plus rapide d’alerter sur ces données est de les importer en tant que métriques personnalisées. Pour cela, utilisez l’extension Diagnostics Azure, puis utilisez une alerte de métrique. Cependant, les métriques personnalisées sont actuellement en préversion et sont [plus coûteuses que les autres options](https://azure.microsoft.com/pricing/details/monitor).

- La méthode la plus économique, mais la plus lente consiste à les envoyer au magasin Kusto des journaux Azure. L’exécution de l’agent Log Analytics sur la machine virtuelle est la meilleure façon d’obtenir toutes les données de métriques et de journaux du système d’exploitation invité dans ce magasin.

- Vous pouvez envoyer aux deux magasins en exécutant à la fois l’extension et l’agent sur la même machine virtuelle. Vous pouvez ensuite alerter rapidement, mais également utiliser les données du système d’exploitation invité dans le cadre de recherches plus complexes quand vous les combinez à d’autres données de télémétrie.

**Importation de données à partir d’un emplacement local :** Si vous essayez d’interroger et de superviser des machines s’exécutant dans Azure et en local, vous pouvez utiliser l’agent Log Analytics pour collecter les données du système d’exploitation invité. Vous pouvez ensuite utiliser une fonctionnalité appelée [journaux vers métriques](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric-logs) afin de transférer ces métriques dans le magasin de métriques. Cette méthode ignore une partie du processus d’ingestion dans le magasin de journaux Azure, et les données sont donc disponibles plus tôt dans la base de données de métriques.

### <a name="minimize-alerts"></a>Minimiser les alertes

Si vous utilisez une solution comme Azure Monitor pour machines virtuelles et trouvez que les critères d’intégrité par défaut qui supervisent l’utilisation des performances sont acceptables, ne créez pas d’alertes de recherche de journal ou de métrique basées sur les mêmes compteurs de performance et qui se recouperaient.

Si vous n’utilisez pas Azure Monitor pour machines virtuelles, créez des alertes et gérez les notifications plus facilement en explorant les fonctionnalités suivantes :

> [!NOTE]
> Ces fonctionnalités s’appliquent seulement aux alertes de métriques, c’est-à-dire aux alertes basées sur les données envoyées à la base de données de métriques d’Azure Monitor. Elles ne s’appliquent pas aux autres types d’alertes. Comme mentionné précédemment, l’objectif principal des alertes de métrique est la rapidité. Si obtenir une alerte en moins de cinq minutes n’est pas votre préoccupation principale, vous pouvez utiliser à la place une alerte de requête de journal.

- [Seuils dynamiques](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-dynamic-thresholds) : Les seuils dynamiques examinent l’activité de la ressource sur une période de temps donnée et créent des seuils supérieurs et inférieurs de « comportement normal ». Quand la métrique supervisée se passe en dehors de ces seuils, vous recevez une alerte.

- [Alertes multisignaux](https://azure.microsoft.com/blog/monitor-at-scale-in-azure-monitor-with-multi-resource-metric-alerts) : Vous pouvez créer une alerte de métrique qui utilise la combinaison de deux entrées différentes provenant de deux types de ressources différents. Par exemple, si vous voulez déclencher une alerte quand l’utilisation du processeur d’une machine virtuelle dépasse 90 % et que le nombre de messages dans une certaine file d’attente Azure Service Bus qui alimente cette machine virtuelle dépasse une certaine quantité, vous pouvez le faire sans créer de requête de journal. Cette fonctionnalité ne fonctionne que pour deux signaux. Si vous avez une requête plus complexe, alimentez vos données de métriques dans le magasin de journaux d’Azure Monitor et utilisez une requête de journal.

- [Alertes multiressources](https://azure.microsoft.com/blog/monitor-at-scale-in-azure-monitor-with-multi-resource-metric-alerts) : Azure Monitor permet qu’une même règle d’alerte de métrique s’applique à toutes les ressources de machine virtuelle. Cette fonctionnalité peut vous faire gagner du temps, car vous n’avez pas besoin de créer des alertes individuelles pour chaque machine virtuelle. La tarification pour ce type d’alerte est la même. Si vous avez créé 50 alertes pour la supervision de l’utilisation du processeur pour 50 machines virtuelles ou bien une alerte qui supervise l’utilisation du processeur pour toutes ces 50 machines virtuelles, cela vous coûte le même prix. Vous pouvez également utiliser ces types d’alertes en combinaison avec des seuils dynamiques.

Utilisées ensemble, ces fonctionnalités permettent de gagner du temps en minimisant les notifications d’alerte et la gestion des alertes sous-jacentes.

### <a name="limits-on-alerts"></a>Limites sur les alertes

Veuillez noter les [limites sur le nombre d’alertes que vous pouvez créer](https://docs.microsoft.com/azure/azure-resource-manager/management/azure-subscription-service-limits#azure-monitor-limits). Vous pouvez faire augmenter certaines limites (mais pas toutes) en appelant le support technique.

### <a name="best-query-experience"></a>Meilleure expérience des requêtes

Si vous recherchez des tendances dans toutes vos données, il est logique d’importer toutes vos données dans les journaux Azure, à moins qu’elles ne se trouvent déjà dans Application Insights. Vous pouvez créer des requêtes sur les deux espaces de travail : il n’est donc pas nécessaire de déplacer les données entre ceux-ci. Vous pouvez également importer le journal d’activité et les données de Service Health dans votre espace de travail Log Analytics. Cette ingestion et ce stockage vous sont facturés, mais vous récupérez toutes vos données à un même emplacement où vous pouvez effectuer des analyses et des interrogations. Cette approche vous donne également la possibilité de créer des conditions de requête complexes et des alertes sur celles-ci.
