---
title: Guide de supervision du cloud - Stratégie de supervision pour les modèles de déploiement cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Choisir quand utiliser Azure Monitor ou System Center Operations Manager dans Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 10/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 5988cbb16e47a603af85eac97078b7dc0a00e295
ms.sourcegitcommit: d37c4443e9acaa381ea74ee3fc50e3b99f13f22a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72001889"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guide de supervision du cloud : Stratégie de supervision pour les modèles de déploiement cloud

Cet article inclut notre stratégie de supervision recommandée pour chacun des modèles de déploiement cloud, en fonction des critères suivants :

- Vous avez besoin de conserver votre engagement envers Operations Manager ou une autre plateforme de supervision de l’entreprise, en raison de l’intégration à vos processus, vos connaissances et votre expertise en matière d’exploitation informatique, ou certaines fonctionnalités ne sont pas encore disponibles dans Azure Monitor.
- Vous devez superviser des charges de travail locales et dans le cloud public, ou seulement dans le cloud.
- Votre stratégie de migration cloud comprend la modernisation des opérations informatiques, et la migration vers nos services et solutions de supervision cloud.
- Vous pouvez avoir des systèmes critiques en « air gap » ou physiquement isolés, hébergés dans un cloud privé ou sur du matériel physique, et qui doivent être supervisés.

Notre stratégie comprend la supervision de l’infrastructure (charges de travail de calcul, de stockage et de serveur), des applications (utilisateur final, exceptions et client) et des ressources réseau, pour offrir une perspective de supervision complète et orientée service.

## <a name="azure-cloud-monitoring"></a>Supervision du cloud Azure

Azure Monitor est le service de plateforme natif Azure qui fournit une source de supervision unique des ressources Azure. Il est conçu pour les solutions cloud basées sur Azure et qui prennent en charge une fonctionnalité métier basée sur des charges de travail de machine virtuelle, ou sur des architectures complexes utilisant des microservices et d’autres ressources de plateforme. Il supervise toutes les couches de la pile, en commençant par les services de locataire, comme Azure Active Directory Domain Services, et les événements de niveau abonnement et l’intégrité des services Azure. Il supervise également les ressources de l’infrastructure, comme les machines virtuelles, le stockage et les ressources réseau, et, au niveau de la couche supérieure, votre application. La supervision de chacune de ces dépendances et la collecte des bons signaux que chacune peut émettre, permet l’observabilité des applications et vous donne l’infrastructure clé dont vous avez besoin.

Le tableau suivant récapitule l’approche recommandée pour superviser chaque couche de la pile.

<!-- markdownlint-disable MD033 -->

Couche | Ressource | Étendue | Méthode
---|---|---|----
Application | Application web s’exécutant sur une plateforme .NET, .NET Core, Java, JavaScript et Node.js sur une machine virtuelle Azure, Azure App Services, Azure Service Fabric, Azure Functions et Azure Cloud Services | Supervisez une application web active pour automatiquement détecter les anomalies de performances, identifier les exceptions et les problèmes du code et collecter des analytiques sur le comportement des utilisateurs. |  Azure Monitor (Application Insights)
Ressources Azure - PaaS | 1. Services Azure Database (par exemple SQL ou MySQL) | 1. Métriques de performances Azure Database pour SQL. | 1. Active la journalisation des diagnostics pour le streaming des données SQL vers les journaux d’Azure Monitor.
Ressources Azure - IaaS | 1. Stockage Azure<br/> 2. Azure Application Gateway<br/> 3. Groupes de sécurité réseau<br/> 4. Azure Traffic Manager<br/> 5. Machine virtuelle<br/> 6. Azure Kubernetes Service/Azure Container Instances | 1. Capacité, disponibilité et performances.<br/> 2. Performances et journaux de diagnostics (activité, accès, performances et pare-feu).<br/> 3. Supervise les événements quand des règles sont appliquées, et le compteur de règles indiquant combien de fois une règle est appliquée pour refuser ou pour autoriser.<br/> 4. Supervise la disponibilité de l’état des points de terminaison.<br/> 5. Supervisez la capacité, la disponibilité et les performances dans le système d’exploitation de machine virtuelle invité. Mappez les dépendances d’applications hébergées sur chaque machine virtuelle, notamment la visibilité des connexions réseau actives entre les serveurs, la latence des connexions entrantes et sortantes et les ports d’une architecture connectée à TCP.<br/> 6. Supervise la capacité, la disponibilité et les performances des charges de travail s’exécutant sur des conteneurs et des instances de conteneur. | 1. Métriques de stockage pour Stockage Blob.<br/> 2. Active la journalisation des diagnostics et configure le streaming vers les journaux d’Azure Monitor.<br/> 3. Active la journalisation des diagnostics des groupes de sécurité réseau et configure le streaming vers les journaux d’Azure Monitor.<br/> 4. Active la journalisation des diagnostics des points de terminaison Traffic Manager et configure le streaming vers les journaux d’Azure Monitor.<br/> 5. Activer Azure Monitor pour machines virtuelles<br/> 6. Activez Azure Monitor pour conteneurs.
Réseau| Communication entre votre machine virtuelle et un ou plusieurs points de terminaison (une autre machine virtuelle, un nom de domaine complet, un URI ou une adresse IPv4). | Supervise l’accessibilité, la latence et les changements de topologie réseau qui se produisent entre la machine virtuelle et le point de terminaison. | Azure Network Watcher
Abonnement Azure | Intégrité des services Azure et intégrité des ressources de base | <li> Actions d’administration effectuées sur un service ou une ressource.<br/><li> L’intégrité du service pour un service Azure se trouve dans un état dégradé ou indisponible.<br/><li> Problèmes d’intégrité détectés avec une ressource Azure du point de vue du service Azure.<br/><li> Opérations effectuées avec la mise à l’échelle automatique Azure indiquant un échec ou une exception. <br/><li> Opérations effectuées avec Azure Policy indiquant qu’une action autorisée ou refusée s’est produite.<br/><li> Enregistrement des alertes générées par Azure Security Center. |Fourni dans le journal d’activité pour la supervision et les alertes avec Azure Resource Manager.
Client Azure|Azure Active Directory || Active la journalisation des diagnostics et configure le streaming vers les journaux d’Azure Monitor.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Supervision d’un cloud hybride

Pour de nombreuses organisations, le cloud doit être adopté progressivement et le modèle de cloud hybride est la première étape la plus courante du parcours. Vous devez soigneusement sélectionner le sous-ensemble approprié d’applications et l’infrastructure pour commencer votre migration tout en évitant les interruptions de votre activité. Toutefois, étant donné que nous offrons deux plateformes de supervision qui prennent en charge ce modèle cloud, les décideurs informatiques ne savent plus très bien quel est le meilleur choix pour prendre en charge leurs objectifs métiers et opérationnels. Nous allons examiner plusieurs facteurs pour résoudre cette incertitude et vous fournir une compréhension de la plateforme à choisir.

Voici quelques-uns des principaux aspects techniques à prendre en compte :

* Vous devez collecter des données à partir des ressources Azure qui prennent en charge la charge de travail, puis les transférer vers vos outils existants ou ceux du fournisseur de services managés.

* Vous devez maintenir votre investissement actuel dans System Center Operations Manager et le configurer pour superviser les ressources IaaS et PaaS s’exécutant dans Azure. Le cas échéant, étant donné que vous supervisez deux environnements ayant des caractéristiques différentes, en fonction de vos besoins, vous déterminez que l’intégration avec Azure Monitor prend en charge votre stratégie.

* Dans le cadre de votre stratégie de modernisation visant à une simplification avec un seul outil pour réduire les coûts et la complexité, vous vous engagez envers Azure Monitor pour la supervision des ressources dans Azure et sur votre réseau d’entreprise.

Le tableau suivant résume les conditions requises qu’Azure Monitor et que System Center Operations Manager prennent en charge avec la supervision du modèle de cloud hybride en fonction d’un ensemble commun de critères.

|Prérequis | Azure Monitor | Operations Manager |
|:--|:---|:---|
|Exigences de l’infrastructure | **Non** | **Oui**<br> Nécessite au minimum un serveur d’administration et un serveur SQL Server hébergeant la base de données opérationnelle et la base de données de l’entrepôt de données associée. Devient plus complexe lorsque la haute disponibilité et la reprise d’activité après sinistre sont nécessaires, des ordinateurs dans plusieurs sites, des systèmes non approuvés et d’autres considérations de conception complexes.|
|Connectivité limitée - Pas d’Internet<br> ni de réseau isolé | **Non** | **Oui** | 
|Connectivité limitée - Accès contrôlé à Internet | **Oui** | **Oui** |
|Connectivité limitée - Déconnexion fréquente | **Oui** | **Oui** |
|Analyse du fonctionnement configurable | **Non** | **Oui** |
| Test de disponibilité des applications web (réseau isolé) | **Oui, avec des limitations**<br> Azure Monitor a une prise en charge limitée dans ce domaine et nécessite des exceptions de pare-feu personnalisées. | **Oui** | 
| Test de disponibilité des applications web (distribuées dans le monde entier) | **Non** | **Oui** |
|Superviser les charges de travail de machine virtuelle | **Oui, avec des limitations**<br> Peut collecter les journaux d’erreurs IIS et SQL Server, les événements Windows et les compteurs de performances. Requiert la création de visualisations, d’alertes et de requêtes personnalisées. | **Oui**<br> Prend en charge la supervision de la plupart des charges de travail serveur avec les packs d’administration disponibles. Nécessite l’agent Windows Log Analytics ou l’agent Operations Manager sur la machine virtuelle, qui rend compte au groupe d’administration sur le réseau d’entreprise.|
|Superviser Azure IaaS | **Oui** | **Oui**<br> Prend en charge la supervision de la majeure partie de l’infrastructure du réseau d’entreprise. Suit l’état de disponibilité, les métriques et les alertes pour les machines virtuelles Azure, SQL et le stockage via le pack d’administration Azure.|
|Superviser Azure PaaS | **Oui** | **Oui, avec des limitations**<br> En fonction de ce qui est pris en charge dans le pack d’administration Azure. | 
|Supervision des services Azure | **Oui**<br> | **Oui**<br> Bien qu’il n’y ait pas de supervision native de l’intégrité des services Azure fournie aujourd’hui via un pack d’administration, vous pouvez créer des workflows personnalisés pour interroger les alertes d’intégrité des services Azure. Utilisez l’API REST Azure pour recevoir des alertes via vos notifications existantes.|
|Supervision des applications web modernes | **Oui** | **Non** |
|Supervision des applications web héritées | **Oui, les limitations dépendent du SDK**<br> Prend en charge la supervision des versions antérieures des applications web .NET et Java. | **Oui, avec des limitations** |
|Superviser des conteneurs Azure Kubernetes Service | **Oui** | **Non** |
|Superviser des conteneurs Docker/Windows | **Oui** | **Non** | 
|Analyse des performances réseau | **Oui** | **Oui, avec des limitations**<br> Prend en charge les vérifications de disponibilité et collecte des statistiques de base à partir des périphériques réseau à l’aide du protocole SNMP du réseau d’entreprise.|
|Analyse de données interactive | **Oui** | **Non**<br> S’appuie sur les des rapports prédéfinis ou personnalisés SQL Server Reporting Services, des solutions de visualisation tierces ou une implémentation de Power BI personnalisée. L’entrepôt de données Operations Manager présente des limitations de performances et de mise à l’échelle. S’intègre avec les journaux Azure Monitor comme alternative aux exigences d’agrégation de données. L’intégration est possible en configurant le connecteur Log Analytics.| 
|Diagnostics de bout en bout, analyse de la cause racine et résolution des problèmes en temps opportun | **Oui** | **Oui, avec des limitations**<br> Prend en charge les diagnostics de bout en bout et la résolution des problèmes uniquement pour l’infrastructure et les applications locales. Utilise d’autres composants System Center ou des solutions de partenaires.|
|Visualisations interactives (tableaux de bord) | **Oui** | **Oui, avec des limitations**<br> Fournit des tableaux de bord essentiels avec la console web HTLM5 ou une expérience avancée à partir des solutions de partenaires, telles que Squared Up et Savision. |
|Intégration avec les outils IT/DevOps | **Oui** | **Oui, avec des limitations** |

### <a name="collect-and-stream-monitoring-data-to-third-party-or-on-premises-tools"></a>Collecter et diffuser en continu des données de supervision vers des outils tiers ou locaux

Pour collecter des métriques et journaux à partir des ressources d’infrastructure et de plateforme Azure, vous devez activer les journaux de diagnostic Azure pour ces ressources. En outre, avec des machines virtuelles Azure, vous pouvez collecter des métriques et journaux du système d’exploitation invité en activant l’extension Diagnostics Azure. Pour transférer les données de diagnostic émises à partir de vos ressources Azure vers vos outils locaux ou votre fournisseur de services managés, configurez [Event Hubs](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-stream-event-hubs) pour diffuser les données vers ces derniers. 

### <a name="monitor-with-system-center-operations-manager"></a>Superviser avec System Center Operations Manager

Alors que System Center Operations Manager a été initialement conçu comme une solution locale pour superviser les applications, les charges de travail et l’infrastructure en cours d’exécution dans votre environnement informatique, il a évolué pour inclure des fonctionnalités de supervision cloud et s’intègre à Azure, Office 365 et Amazon Web Services (AWS). Il peut superviser ces divers environnements avec des packs d’administration conçus et mis à jour pour les prendre en charge.  

Pour les clients qui ont réalisé des investissements significatifs dans Operations Manager pour bénéficier d’une supervision complète étroitement intégrée à leurs processus et outils de gestion des services informatiques, ou aux clients qui découvrent Azure, il est compréhensible de se poser les questions suivantes :

* Operations Manager peut-il continuer à fournir de la valeur et est-il pertinent pour l’entreprise ?

* Les fonctionnalités d’Operations Manager en font-elles le bon choix pour notre service informatique ?

* Est-ce que l’intégration d’Operations Manager avec Azure Monitor fournit la solution de supervision économique et complète dont nous avons besoin ? 

Si vous avez déjà investi dans Operations Manager, vous n’avez pas besoin de vous concentrer sur la planification d’une migration pour le remplacer immédiatement. Avec Azure ou d’autres fournisseurs de cloud existant en tant qu’extension de votre propre réseau local, Operations Manager peut superviser les machines virtuelles invitées et les ressources Azure comme si elles se trouvaient sur votre réseau d’entreprise. Pour cela, vous devez disposer d’une connexion réseau fiable entre votre réseau et le réseau virtuel Azure disposant d’une bande passante suffisante. 

Pour superviser les charges de travail en cours d’exécution dans Azure, vous avez besoin des éléments suivants :

* Le [pack d’administration Azure](https://www.microsoft.com/download/details.aspx?id=50013) pour collecter les métriques de performances émises par les services Azure, telles que les rôles web et worker, les tests de disponibilité Application Insights (tests web), Service Bus, etc. Le pack d’administration utilise l’API REST Azure pour superviser la disponibilité et les performances de ces ressources. Certains types de service Azure n’ont pas de métriques ni de moniteurs prédéfinis dans le pack d’administration, mais ils peuvent toujours être supervisés via les relations définies dans le pack d’administration Azure pour les services détectés.

* Le [pack d’administration Azure SQL Database ](https://www.microsoft.com/download/details.aspx?id=38829) pour superviser la disponibilité et les performances des bases de données SQL Azure et des serveurs Azure SQL Database à l’aide de l’API REST Azure et des requêtes T-SQL pour les vues système SQL Server.

* Pour superviser le système d’exploitation invité et les charges de travail en cours d’exécution sur la machine virtuelle, par exemple SQL Server, IIS ou Apache Tomcat, vous devez télécharger et importer le pack d’administration qui prend en charge l’application, le service et le système d’exploitation.

La connaissance est définie dans le pack d’administration, qui décrit comment superviser les dépendances et les composants individuels. Les deux packs d’administration Azure nécessitent l’exécution d’un ensemble d’étapes de configuration dans Azure et Operations Manager pour commencer à superviser ces ressources. 

Au niveau de l’application, Operations Manager offre des fonctionnalités de supervision des performances des applications de base pour certaines versions héritées de .NET et Java. Si certaines applications au sein de votre environnement de cloud hybride fonctionnent en mode hors connexion ou isolé du réseau, de sorte qu’elles ne peuvent pas communiquer avec un service cloud public, Operations Manager Application Performance Monitoring (APM) peut être une option viable pour certains scénarios limités. Pour les applications qui ne s’exécutent pas sur des plateformes héritées, hébergées localement et dans un cloud public qui autorise la communication via un pare-feu (directe ou via un proxy) vers Azure, utilisez Azure Monitor Application Insights. Cela offre une supervision détaillée au niveau du code, avec une prise en charge de première classe pour ASP.NET, ASP.NET Core, Java, JavaScript et Node.js.

Pour toute application web qui peut être atteinte en externe, vous devez activer un type de transactions synthétiques nommées [supervision de la disponibilité]( https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability). Il est important de savoir si votre application ou un point de terminaison HTTP/HTTPS critique sur lequel votre application s’appuie est disponible et réactif. La supervision de la disponibilité Application Insights vous permet d’exécuter des tests à partir de plusieurs centres de données Azure et de fournir des insights sur l’intégrité de votre application d’un point de vue global.

Si Operations Manager est en mesure de superviser les ressources hébergées dans Azure, il existe plusieurs avantages à l’inclusion d’Azure Monitor, car ses forces compensent les limitations d’Operations Manager et constituent une base solide pour prendre en charge la migration éventuelle à partir de celui-ci. Nous examinerons chacun d’entre eux avec notre recommandation pour inclure Azure Monitor dans votre stratégie de supervision hybride.  

#### <a name="disadvantage-of-using-operations-manager-by-itself"></a>Inconvénient de l’utilisation d’Operations Manager par lui-même

1. L’analyse des données de supervision dans Operations Manager est généralement effectuée à l’aide de vues prédéfinies dans les packs d’administration accessibles à partir de la console, de rapports SQL Server Reporting Services (SSRS) ou de vues personnalisées créées par l’utilisateur final. L’analyse ad hoc des données n’est pas possible de façon native. La création de rapports Operations Manager est rigide, l’entrepôt de données qui fournit la conservation à long terme des données de supervision ne s’adapte pas ou ne fonctionne pas correctement, et l’expertise dans l’écriture d’instructions T-SQL, le développement d’une solution Power BI ou l’utilisation de solutions tierces est requise pour prendre en charge les prérequis pour les différentes « personas » du service informatique. 

2. La génération d’alertes dans Operations Manager ne prend pas en charge les expressions complexes et inclut la logique de corrélation dans un effort pour réduire le bruit d’alerte et les alertes de groupe afin d’illustrer la relation entre eux afin de faciliter l’identification de la cause racine du problème. 

#### <a name="advantage-of-operations-manager--azure-monitor"></a>Avantage d’Operations Manager + Azure Monitor

1. Les journaux Azure Monitor sont la solution pour contourner les limitations d’Operations Manager. Ils complètent la base de données de l’entrepôt de données Operations Manager pour collecter des données de journalisation et de performances importantes. Azure Monitor offre une meilleure analytique, de meilleures performances lors de l’interrogation de gros volumes de données et une meilleure conservation des données par rapport à l’entrepôt de données Operations Manager. Son langage de requête vous permet de créer des requêtes plus complexes et sophistiquées, avec la possibilité d’exécuter des requêtes sur plusieurs téraoctets de données en quelques secondes. Vous pouvez transformer rapidement vos données en graphiques en secteurs, en graphiques temporels et dans de nombreuses autres visualisations. Vous n’êtes plus obligé de travailler avec des rapports dans Operations Manager basés sur SQL Server Reporting Services, des requêtes SQL personnalisées ou d’autres solutions de contournement pour analyser ces données.

2. Offrez une expérience d’alerte améliorée grâce à l’implémentation de la solution Alerts Management d’Azure Monitor. Les alertes générées dans le groupe d’administration Operations Manager peuvent être transférées vers l’espace de travail Azure Monitor Log Analytics. Vous pouvez configurer l’abonnement responsable du transfert des alertes d’Operations Manager aux journaux Azure Monitor pour transférer uniquement certaines alertes. Par exemple, vous pouvez transférer uniquement les alertes qui répondent à vos critères d’interrogation en support de la gestion des problèmes pour les tendances et l’examen de la cause racine des défaillances ou des problèmes, dans un emplacement unique. En outre, vous pouvez mettre en corrélation d’autres données de journal à partir d’Application Insights ou d’autres sources, pour obtenir des insights qui contribuent à améliorer l’expérience utilisateur, à augmenter la durée de fonctionnement et à réduire le temps de résolution des incidents.

3. Supervisez l’infrastructure et les applications cloud natives à partir d’une architecture simple ou multiniveau dans Azure et utilisez Operations Manager pour superviser l’infrastructure locale. Cela inclut une ou plusieurs machines virtuelles, plusieurs machines virtuelles placées dans un groupe à haute disponibilité ou un groupe de machines virtuelles identiques, ou une application en conteneur déployée sur Azure Kubernetes Service (AKS) s’exécutant sur des conteneurs Windows Server ou Linux.

4. Utilisez la solution System Center Operations Manager Health Check pour évaluer de façon proactive les risques et l’intégrité de votre groupe d’administration System Center Operations Manager à intervalles réguliers. Cela peut remplacer ou compléter les fonctionnalités personnalisées que vous avez ajoutées à votre groupe d’administration.

5. Grâce à la fonctionnalité de mappage d’Azure Monitor pour machines virtuelles, vous pouvez superviser les métriques de connectivité standard à partir de connexions réseau entre vos machines virtuelles Azure et les machines virtuelles locales. Ces métriques incluent le temps de réponse, le nombre de requêtes par minute, le débit du trafic et les liens. Vous pouvez identifier les connexions ayant échoué, résoudre les problèmes, effectuer la validation de la migration et l’analyse de la sécurité et vérifier l’architecture globale du service. La fonctionnalité de mappage peut découvrir automatiquement les composants d’application sur les systèmes Windows et Linux et mapper la communication entre les services. Cela vous permet d’identifier les connexions et les dépendances que vous n’avez pas pris en compte, de planifier et de valider la migration vers Azure et de réduire au minimum les spéculations lors de la résolution des incidents.

6. À l’aide de Network Performance Monitor, surveillez la connectivité réseau entre :

   - Votre réseau d’entreprise et Azure.

   - Les applications multicouches critiques et les microservices.

   - Les emplacements des utilisateurs et les applications web (HTTP/HTTPS).

   Cette stratégie offre une visibilité de la couche réseau, sans recourir à SNMP. Elle peut également être présente dans une carte topologique interactive, la topologie tronçon par tronçon des itinéraires entre le point de terminaison source et le point de terminaison de destination. Il est préférable d’essayer d’obtenir le même résultat avec la supervision du réseau dans Operations Manager, ou d’autres outils de supervision du réseau actuellement utilisés dans votre environnement.

### <a name="monitor-with-azure-monitor"></a>Surveiller avec Azure Monitor

Alors qu’une migration vers le cloud présente de nombreux défis, elle inclut également un certain nombre d’opportunités. Elle permet à votre organisation de migrer à partir d’un ou de plusieurs outils de supervision d’entreprise locaux pour réduire les dépenses d’investissement et les coûts d’exploitation, et également tirer parti des avantages d’une plateforme de supervision cloud telle qu’Azure Monitor à l’échelle du cloud. Examinez vos exigences en matière de supervision et d’alertes, la configuration des outils de supervision existants, les charges de travail qui migrent vers le cloud, puis, une fois votre plan finalisé, configurez Azure Monitor. 

- Supervisez l’infrastructure et les applications hybrides, à partir d’une architecture simple ou multiniveau où les composants sont hébergés entre Azure, d’autres fournisseurs de cloud et votre réseau d’entreprise. Cela inclut une ou plusieurs machines virtuelles, plusieurs machines virtuelles placées dans un groupe à haute disponibilité ou un groupe de machines virtuelles identiques, ou une application en conteneur déployée sur Azure Kubernetes Service (AKS) s’exécutant sur des conteneurs Windows Server ou Linux. 

- Activez Azure Monitor pour machines virtuelles, Azure Monitor pour conteneurs et Application Insights afin de détecter et de diagnostiquer les problèmes entre l’infrastructure et les applications. Pour une analyse plus approfondie et une corrélation des données collectées à partir des différents composants ou dépendances prenant en charge l’application, vous devez utiliser les journaux Azure Monitor.

- Créez des alertes intelligentes qui peuvent s’appliquer à un ensemble principal d’applications et de composants de service, réduisez le bruit d’alerte avec des seuils dynamiques pour les signaux complexes et utilisez l’agrégation d’alertes basée sur les algorithmes Machine Learning pour identifier rapidement le problème.

 - Définissez une bibliothèque de requêtes et de tableaux de bord pour prendre en charge les spécifications pour les différentes « personas » du service informatique.

- Définissez des standards et des méthodes pour l’activation de la supervision des différentes ressources hybrides et cloud, une référence de base de la supervision pour chaque ressource, des seuils d’alerte, etc.  

- Configurez le contrôle d’accès en fonction du rôle (RBAC). Vous pouvez ainsi accorder aux utilisateurs et aux groupes uniquement le type d’accès dont ils ont besoin pour travailler avec les données de supervision des ressources dont ils sont responsables. 

- Incluez l’automatisation et le libre-service pour permettre à chaque équipe de créer, d’activer et de paramétrer ses configurations de supervision et d’alerte selon les besoins. 

## <a name="private-cloud-monitoring"></a>Supervision d’un cloud privé

Vous pouvez effectuer une supervision complète d’Azure Stack avec System Center Operations Manager. Plus précisément, vous pouvez superviser les charges de travail qui s’exécutent dans le locataire, le niveau des ressources sur les machines virtuelles et l’infrastructure qui héberge Azure Stack (serveurs physiques et commutateurs réseau). Vous pouvez également effectuer une supervision complète avec une combinaison de [fonctionnalités de supervision d’infrastructure](/azure/azure-stack/azure-stack-monitor-health) incluses dans Azure Stack. Ces fonctionnalités vous permettent de voir l’intégrité et les alertes pour une région Azure Stack et le [service Azure Monitor](/azure/azure-stack/user/azure-stack-metrics-azure-data) dans Azure Stack, ce qui fournit des métriques et des journaux de l’infrastructure à un niveau de base pour la plupart des services.

Si vous avez déjà investi dans Operations Manager, utilisez le pack d’administration Azure Stack pour superviser la disponibilité et l’état d’intégrité des déploiements Azure Stack. Ceci inclut les régions, les fournisseurs de ressources, les mises à jour, les exécutions des mises à jour, les unités d’échelle, les nœuds d’unité, les rôles d’infrastructure et leurs instances (entités logiques constituées des ressources matérielles). Il utilise les API REST du fournisseur de ressources d’intégrité et de mise à jour pour communiquer avec Azure Stack. Pour superviser des serveurs physiques et des périphériques de stockage, utilisez le pack d’administration des fournisseurs OEM (par exemple fourni par Lenovo, Hewlett Packard ou Dell). Operations Manager peut superviser nativement les commutateurs réseau pour collecter des statistiques en utilisant le protocole SNMP. La supervision des charges de travail du locataire est possible avec le pack d’administration Azure en suivant deux étapes de base. Configurez l’abonnement que vous voulez superviser, puis ajoutez les moniteurs pour cet abonnement.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Collecte des données appropriées](./data-collection.md)
