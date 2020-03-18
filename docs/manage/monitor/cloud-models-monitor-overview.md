---
title: Stratégie de supervision pour les modèles de déploiement cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin de savoir quelle stratégie de supervision utiliser pour la gestion cloud.
author: MGoedtel
ms.author: magoedte
ms.date: 10/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 3b6434937816255269bda41c422099a07a25f5bc
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78341825"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guide de supervision du cloud : Stratégie de supervision pour les modèles de déploiement cloud

Cet article inclut notre stratégie de supervision recommandée pour chacun des modèles de déploiement cloud, en fonction des critères suivants :

- Vous devez conserver votre engagement envers Operations Manager ou une autre plateforme de supervision de l’entreprise, en raison de l’intégration à vos processus, vos connaissances et votre expertise en matière d’exploitation informatique, ou parce que certaines fonctionnalités ne sont pas encore disponibles dans Azure Monitor.
- Vous devez superviser des charges de travail à la fois localement et dans le cloud public, ou seulement dans le cloud.
- Votre stratégie de migration cloud comprend la modernisation des opérations informatiques, et la migration vers nos services et solutions de supervision cloud.
- Vous pouvez avoir des systèmes critiques en « air gap » ou physiquement isolés, hébergés dans un cloud privé ou sur du matériel physique, et ces systèmes doivent être supervisés.

Notre stratégie comprend la supervision de l'infrastructure (charges de travail de calcul, de stockage et de serveur), des applications (utilisateur final, exceptions et client) et des ressources réseau. Elle offre une perspective de supervision complète et orientée service.

## <a name="azure-cloud-monitoring"></a>Supervision du cloud Azure

Azure Monitor est le service de plateforme natif Azure qui fournit une source de supervision unique des ressources Azure. Il est conçu pour les solutions cloud :

- basées sur Azure ;
- qui prennent en charge une fonctionnalité métier basée sur des charges de travail de machine virtuelle, ou sur des architectures complexes utilisant des microservices et d'autres ressources de plateforme.

Il supervise toutes les couches de la pile, en commençant par les services de locataire, comme Azure Active Directory Domain Services, ainsi que les événements de niveau abonnement et l'intégrité des services Azure.

Il supervise également les ressources de l'infrastructure, comme les machines virtuelles, le stockage et les ressources réseau. Au niveau de la couche supérieure, il supervise votre application.

Grâce à la supervision de chacune de ces dépendances et à la collecte des bons signaux que chacune peut émettre, vous pouvez observer les applications et disposez de l'infrastructure clé dont vous avez besoin.

Le tableau suivant résume l'approche recommandée pour superviser chaque couche de la pile :

<!-- markdownlint-disable MD033 -->

Couche | Ressource | Étendue | Méthode
---|---|---|----
Application | Application web exécutée sur une plateforme .NET, .NET Core, Java, JavaScript et Node.js, sur machine virtuelle Azure, Azure App Services, Azure Service Fabric, Azure Functions et Azure Cloud Services. | Supervisez une application web active pour automatiquement détecter les anomalies de performances, identifier les exceptions et les problèmes du code et collecter des analytiques sur le comportement des utilisateurs. |  Azure Monitor (Application Insights).
Ressources Azure - Platform as a service (PaaS) | Services Azure Database (par exemple, SQL ou MySQL). | Métriques de performances Azure Database pour SQL. | Active la journalisation des diagnostics pour la transmission en continu des données SQL vers les journaux d'Azure Monitor.
Ressources Azure - Infrastructure as a service (IaaS) | 1. Stockage Azure<br/> 2. Azure Application Gateway<br/> 3. Groupes de sécurité réseau<br/> 4. Azure Traffic Manager<br/> 5. Machines virtuelles Azure<br/> 6. Azure Kubernetes Service/Azure Container Instances | 1. Capacité, disponibilité et performances.<br/> 2. Performances et journaux de diagnostic (activité, accès, performances et pare-feu).<br/> 3. Supervise les événements quand des règles sont appliquées, et le compteur de règles indiquant combien de fois une règle est appliquée pour refuser ou pour autoriser.<br/> 4. Supervise la disponibilité de l’état des points de terminaison.<br/> 5. Supervise la capacité, la disponibilité et les performances dans le système d'exploitation d'une machine virtuelle invitée. Mappez les dépendances d’applications hébergées sur chaque machine virtuelle, notamment la visibilité des connexions réseau actives entre les serveurs, la latence des connexions entrantes et sortantes et les ports d’une architecture connectée à TCP.<br/> 6. Supervise la capacité, la disponibilité et les performances des charges de travail s’exécutant sur des conteneurs et des instances de conteneur. | 1. Métriques de stockage pour Stockage Blob.<br/> 2. Active la journalisation des diagnostics et configure la transmission en continu vers les journaux d'Azure Monitor.<br/> 3. Active la journalisation des diagnostics des groupes de sécurité réseau et configure la transmission en continu vers les journaux d'Azure Monitor.<br/> 4. Active la journalisation des diagnostics des points de terminaison Traffic Manager et configure la transmission en continu vers les journaux d'Azure Monitor.<br/> 5. Active Azure Monitor pour machines virtuelles.<br/> 6. Active Azure Monitor pour conteneurs.
Réseau | Communication entre votre machine virtuelle et un ou plusieurs points de terminaison (une autre machine virtuelle, un nom de domaine complet, un URI ou une adresse IPv4). | Supervise l’accessibilité, la latence et les changements de topologie réseau qui se produisent entre la machine virtuelle et le point de terminaison. | Azure Network Watcher.
Abonnement Azure | Intégrité des services Azure et intégrité des ressources de base. | <li> Actions d’administration effectuées sur un service ou une ressource.<br/><li> L’intégrité du service pour un service Azure se trouve dans un état dégradé ou indisponible.<br/><li> Problèmes d’intégrité détectés avec une ressource Azure du point de vue du service Azure.<br/><li> Opérations effectuées avec la mise à l’échelle automatique Azure indiquant un échec ou une exception. <br/><li> Opérations effectuées avec Azure Policy indiquant qu’une action autorisée ou refusée s’est produite.<br/><li> Enregistrement des alertes générées par Azure Security Center. | Fourni dans le journal d’activité pour la supervision et les alertes avec Azure Resource Manager.
Client Azure | Azure Active Directory || Active la journalisation des diagnostics et configure la transmission en continu vers les journaux d'Azure Monitor.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Supervision d’un cloud hybride

Pour de nombreuses organisations, la transition vers le cloud doit être abordée progressivement, le modèle de cloud hybride étant généralement la première étape du parcours. Vous devez soigneusement sélectionner le sous-ensemble d'applications et d'infrastructure approprié pour entamer votre migration, tout en évitant les interruptions de votre activité. Toutefois, étant donné que nous offrons deux plateformes de supervision qui prennent en charge ce modèle cloud, les décideurs informatiques peuvent ne pas savoir quel est le meilleur choix pour prendre en charge leurs objectifs métiers et opérationnels.

Dans cette section, nous allons aborder cette incertitude en examinant différents facteurs et en offrant des éléments de compréhension qui permettront de déterminer la plateforme à prendre en compte.

Gardez à l'esprit les aspects techniques clés suivants :

- Vous devez collecter des données à partir des ressources Azure qui prennent en charge la charge de travail, puis les transférer vers vos outils existants ou ceux du fournisseur de services managés.

- Vous devez maintenir votre investissement actuel envers System Center Operations Manager et le configurer pour superviser les ressources IaaS et PaaS exécutées dans Azure. Le cas échéant, dans la mesure où vous supervisez deux environnements aux caractéristiques différentes, en fonction de vos besoins, vous devez déterminer comment l'intégration à Azure Monitor prend en charge votre stratégie.

- Dans le cadre de votre stratégie de modernisation visant à une simplification avec un seul outil pour réduire les coûts et la complexité, vous devez vous engager envers Azure Monitor pour la supervision des ressources dans Azure et sur votre réseau d'entreprise.

Le tableau suivant résume les conditions requises qu’Azure Monitor et que System Center Operations Manager prennent en charge avec la supervision du modèle de cloud hybride en fonction d’un ensemble commun de critères.

<!-- markdownlint-disable MD033 -->

|Condition requise | Azure Monitor | Operations Manager |
|:--|:---|:---|
|Exigences de l’infrastructure | Non | Oui<br> Nécessite au minimum un serveur d’administration et un serveur SQL Server hébergeant la base de données opérationnelle et la base de données de l’entrepôt de données pour les rapports. La complexité s'accentue lorsque la haute disponibilité et la récupération d'urgence sont requises, de même qu'en présence de machines réparties sur plusieurs sites, de systèmes non fiables et d'autres considérations de conception complexes.|
|Connectivité limitée - Pas d’Internet<br> ni de réseau isolé | Non | Oui |
|Connectivité limitée - Accès contrôlé à Internet | Oui | Oui |
|Connectivité limitée - Déconnexion fréquente | Oui | Oui |
|Analyse du fonctionnement configurable | Non | Oui |
| Test de disponibilité des applications web (réseau isolé) | Oui, avec des limitations<br> Azure Monitor a une prise en charge limitée dans ce domaine et nécessite des exceptions de pare-feu personnalisées. | Oui |
| Test de disponibilité des applications web (distribuées dans le monde entier) | Non | Oui |
|Superviser les charges de travail de machine virtuelle | Oui, avec des limitations<br> Peut collecter les journaux d’erreurs IIS et SQL Server, les événements Windows et les compteurs de performances. Requiert la création de visualisations, d’alertes et de requêtes personnalisées. | Oui<br> Prend en charge la supervision de la plupart des charges de travail serveur avec les packs d’administration disponibles. Nécessite l’agent Windows Log Analytics ou l’agent Operations Manager sur la machine virtuelle, qui rend compte au groupe d’administration sur le réseau d’entreprise.|
|Superviser Azure IaaS | Oui | Oui<br> Prend en charge la supervision de la majeure partie de l’infrastructure du réseau d’entreprise. Suit l’état de disponibilité, les métriques et les alertes pour les machines virtuelles Azure, SQL et le stockage via le pack d’administration Azure.|
|Superviser Azure PaaS | Oui | Oui, avec des limitations<br> En fonction de ce qui est pris en charge dans le pack d’administration Azure. |
|Supervision des services Azure | Oui<br> | Oui<br> Bien qu'aucune supervision native de l'intégrité des services Azure ne soit aujourd'hui fournie via un pack d'administration, vous pouvez créer des workflows personnalisés pour interroger les alertes d'intégrité des services Azure. Utilisez l’API REST Azure pour recevoir des alertes via vos notifications existantes.|
|Supervision des applications web modernes | Oui | Non |
|Supervision des applications web héritées | Oui, les limitations dépendent du kit de développement logiciel (SDK)<br> Prend en charge la supervision des versions antérieures des applications web .NET et Java. | Oui, avec des limitations |
|Superviser des conteneurs Azure Kubernetes Service | Oui | Non |
|Superviser des conteneurs Docker ou Windows | Oui | Non |
|Analyse des performances réseau | Oui | Oui, avec des limitations<br> Prend en charge les vérifications de disponibilité et collecte des statistiques de base à partir des périphériques réseau à l'aide du protocole SNMP (Simple Network Management Protocol) du réseau d'entreprise.|
|Analyse de données interactive | Oui | Non<br> S’appuie sur des rapports prédéfinis ou personnalisés de SQL Server Reporting Services, des solutions de visualisation de tiers ou une implémentation de Power BI personnalisée. L’entrepôt de données Operations Manager présente des limitations de performances et de mise à l’échelle. S'intègre aux journaux Azure Monitor comme alternative aux exigences d'agrégation de données. L'intégration s'effectue en configurant le connecteur Log Analytics.|
|Diagnostics de bout en bout, analyse de la cause racine et résolution des problèmes en temps opportun | Oui | Oui, avec des limitations<br> Prend en charge les diagnostics de bout en bout et la résolution des problèmes uniquement pour l’infrastructure et les applications locales. Utilise d’autres composants System Center ou des solutions de partenaires.|
|Visualisations interactives (tableaux de bord) | Oui | Oui, avec des limitations<br> Fournit des tableaux de bord essentiels avec la console Web HTML5 ou une expérience avancée de solutions partenaires, telles que Squared Up et Savision. |
|Intégration avec les outils IT ou DevOps | Oui | Oui, avec des limitations |

<!-- markdownlint-enable MD033 -->

### <a name="collect-and-stream-monitoring-data-to-third-party-or-on-premises-tools"></a>Collecter et diffuser en continu des données de supervision vers des outils tiers ou locaux

Pour collecter les métriques et les journaux des ressources d'infrastructure et de plateforme Azure, vous devez activer les journaux de diagnostic Azure de ces ressources. En outre, avec les machines virtuelles Azure, vous pouvez collecter les métriques et les journaux du système d'exploitation invité en activant l'extension Diagnostics Azure. Pour transférer les données de diagnostic émises par vos ressources Azure vers vos outils locaux ou votre fournisseur de services managés, configurez [Event Hubs](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-stream-event-hubs) de manière à leur transmettre les données en continu.

### <a name="monitor-with-system-center-operations-manager"></a>Superviser avec System Center Operations Manager

Bien que System Center Operations Manager ait été initialement conçu comme une solution locale de supervision des applications, des charges de travail et des composants d’infrastructure exécutés dans votre environnement informatique, il a évolué pour inclure des fonctionnalités de supervision cloud. Il s'intègre à Azure, Office 365 et Amazon Web Services (AWS). Il peut superviser tous ces environnements grâce à des packs d'administration conçus et mis à jour pour les prendre en charge.  

Pour les clients qui ont beaucoup investi dans Operations Manager afin de bénéficier d'une supervision complète étroitement intégrée à leurs processus et outils de gestion des services informatiques, ou pour les clients qui découvrent Azure, il est compréhensible de se poser les questions suivantes :

- Operations Manager peut-il continuer à fournir de la valeur, et est-il pertinent pour l'entreprise ?
- Les fonctionnalités d'Operations Manager en font-elles le bon choix pour notre service informatique ?
- Est-ce que l’intégration d’Operations Manager avec Azure Monitor fournit la solution de supervision économique et complète dont nous avons besoin ?

Si vous avez déjà investi dans Operations Manager, vous n'avez pas besoin de vous concentrer sur la planification d'une migration pour le remplacer immédiatement. Avec Azure ou d'autres fournisseurs de services cloud qui existent en tant qu'extension de votre propre réseau local, Operations Manager peut superviser les machines virtuelles invitées et les ressources Azure comme si elles se trouvaient sur votre réseau d'entreprise. Cette approche nécessite une connexion réseau fiable entre votre réseau et le réseau virtuel Azure, celui-ci devant également disposer d'une bande passante suffisante.

Pour superviser les charges de travail exécutées dans Azure, vous avez besoin de ce qui suit :

- Le [pack d'administration Azure](https://www.microsoft.com/download/details.aspx?id=50013). Celui-ci collecte les métriques de performances émises par les services Azure, telles que les rôles web et worker, les tests de disponibilité Application Insights (tests web), Azure Service Bus, etc. Le pack d’administration utilise l’API REST Azure pour superviser la disponibilité et les performances de ces ressources. Selon les types de services Azure, le pack d’administration ne contient pas toujours de métriques ou de moniteurs prédéfinis, mais vous pouvez toujours les superviser via les relations définies dans le pack d’administration Azure pour les services découverts.

- Le [pack d'administration Azure SQL Database ](https://www.microsoft.com/download/details.aspx?id=38829) pour superviser la disponibilité et les performances des bases de données SQL Azure et des serveurs Azure SQL Database à l'aide de l'API REST Azure et des requêtes T-SQL aux vues système SQL Server.

- Pour superviser le système d'exploitation invité et les charges de travail exécutées sur la machine virtuelle, par exemple SQL Server, IIS ou Apache Tomcat, vous devez télécharger et importer le pack d'administration qui prend en charge l'application, le service et le système d'exploitation.

La connaissance est définie dans le pack d’administration, qui décrit comment superviser les dépendances et les composants individuels. Les deux packs d'administration Azure nécessitent l'exécution d'un ensemble d'étapes de configuration dans Azure et Operations Manager avant de pouvoir commencer à superviser ces ressources.

Au niveau de l’application, Operations Manager offre des fonctionnalités de supervision des performances des applications de base pour certaines versions héritées de .NET et Java. Si certaines applications de votre environnement de cloud hybride fonctionnent en mode hors connexion ou isolé du réseau, de sorte qu'elles ne peuvent pas communiquer avec un service cloud public, Operations Manager Application Performance Monitoring (APM) peut être une option viable pour certains scénarios limités. Pour les applications non exécutées sur des plateformes héritées, mais hébergées localement et dans un cloud public qui permet la communication avec Azure via un pare-feu (directement ou via un proxy), utilisez Azure Monitor Application Insights. Ce service offre une supervision approfondie au niveau du code, avec une prise en charge de première classe pour ASP.NET, ASP.NET Core, Java, JavaScript et Node.js.

Pour toute application web accessible en externe, vous devez activer un type de transaction synthétique appelé [supervision de la disponibilité]( https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability). Il est important de savoir si votre application ou un point de terminaison HTTP/HTTPS critique sur lequel votre application s'appuie est disponible et réactif. Avec la supervision de la disponibilité d'Application Insights, vous pouvez effectuer des tests à partir de plusieurs centres de données Azure et fournir des insights sur l'intégrité de votre application d'un point de vue global.

Même si Operations Manager est en mesure de superviser les ressources hébergées dans Azure, l'inclusion d'Azure Monitor présente différents avantages, car ses forces compensent les limitations d'Operations Manager et peuvent constituer une base solide pour prendre en charge une migration éventuelle à partir de celui-ci. Nous allons examiner chacun de ces avantages et inconvénients, en vous recommandant d'inclure Azure Monitor dans votre stratégie de supervision hybride.  

#### <a name="disadvantages-of-using-operations-manager-by-itself"></a>Inconvénients liés à l'utilisation d'Operations Manager seul

- L'analyse des données de supervision dans Operations Manager s'effectue généralement à l'aide de vues prédéfinies fournies par des packs d'administration accessibles à partir de la console, de rapports SQL Server Reporting Services (SSRS) ou de vues personnalisées créées par les utilisateurs finaux. L’analyse ad hoc des données n’est pas prête à l’emploi. La fonctionnalité de création de rapports d'Operations Manager est rigide. L'entrepôt de données qui assure la conservation à long terme des données de supervision n'évolue pas ou ne fonctionne pas bien. Et des connaissances en matière de rédaction d'instructions T-SQL, de développement de solution Power BI ou d'utilisation de solutions tierces sont nécessaires pour satisfaire les exigences des différents membres du service informatique.

- La fonctionnalité d'alerte d'Operations Manager ne prend pas en charge les expressions complexes ou n'inclut pas la logique de corrélation. Pour réduire le bruit, les alertes sont regroupées afin de mettre leurs relations en évidence et d'identifier leurs causes.

#### <a name="advantages-of-using-operations-manager-with-azure-monitor"></a>Avantages de l'utilisation d'Operations Manager avec Azure Monitor

- Azure Monitor permet de contourner les limites d'Operations Manager. Il complète la base de données de l'entrepôt de données Operations Manager en collectant des données de performances et de journaux importantes. Azure Monitor offre une meilleure analyse, de meilleures performances (lors de l'interrogation de gros volumes de données) et une meilleure conservation des données par rapport à l'entrepôt de données Operations Manager.

  Le langage de requête Azure Monitor vous permet de créer des requêtes beaucoup plus complexes et sophistiquées. Vous pouvez exécuter des requêtes sur plusieurs téraoctets de données en quelques secondes. Vous pouvez transformer rapidement vos données en graphiques en secteurs, en graphiques temporels et dans de nombreuses autres visualisations. Pour analyser ces données, vous n'êtes plus contraint d'utiliser des rapports Operations Manager basés sur SQL Server Reporting Services, des requêtes SQL personnalisées ou d'autres solutions de contournement.

- Vous pouvez améliorer l'expérience d'alerte en implémentant la solution Alerts Management d'Azure Monitor. Les alertes générées dans le groupe d'administration Operations Manager peuvent être transférées vers l'espace de travail Log Analytics d'Azure Monitor. Vous pouvez configurer l'abonnement responsable du transfert des alertes d'Operations Manager vers les journaux Azure Monitor pour ne transférer que certaines alertes. Par exemple, vous pouvez transférer uniquement les alertes qui répondent à vos critères d’interrogation en support de la gestion des problèmes pour les tendances et l’examen de la cause racine des défaillances ou des problèmes, dans un emplacement unique. En outre, vous pouvez mettre en corrélation d’autres données de journal à partir d’Application Insights ou d’autres sources, pour obtenir des insights qui contribuent à améliorer l’expérience utilisateur, à augmenter la durée de fonctionnement et à réduire le temps de résolution des incidents.

- Vous pouvez superviser l'infrastructure et les applications cloud natives à partir d'une architecture simple ou multiniveau dans Azure, et vous pouvez utiliser Operations Manager pour superviser l'infrastructure locale. Cette supervision inclut une ou plusieurs machines virtuelles, plusieurs machines virtuelles placées dans un groupe à haute disponibilité ou un groupe de machines virtuelles identiques, ou une application en conteneur déployée sur Azure Kubernetes Service (AKS) et exécutée sur des conteneurs Windows Server ou Linux.

- Vous pouvez utiliser la solution System Center Operations Manager Health Check pour évaluer de façon proactive et à intervalles réguliers l'intégrité de votre groupe d'administration System Center Operations Manager et les risques liés à celui-ci. Cette solution peut remplacer ou compléter toute fonctionnalité personnalisée que vous avez ajoutée à votre groupe d'administration.

- Grâce à la fonctionnalité Carte d'Azure Monitor pour machines virtuelles, vous pouvez superviser les métriques de connectivité standard à partir des connexions réseau entre vos machines virtuelles Azure et vos machines virtuelles locales. Ces métriques incluent le temps de réponse, le nombre de requêtes par minute, le débit du trafic et les liens. Vous pouvez identifier les connexions ayant échoué, résoudre les problèmes, effectuer la validation de la migration et l’analyse de la sécurité et vérifier l’architecture globale du service. La fonctionnalité de mappage peut découvrir automatiquement les composants d’application sur les systèmes Windows et Linux et mapper la communication entre les services. Cette automatisation vous permet d'identifier les connexions et les dépendances que vous n'aviez pas prises en compte, de planifier et de valider la migration vers Azure, et de réduire au minimum les spéculations lors de la résolution des incidents.

- À l'aide de Network Performance Monitor, vous pouvez superviser la connectivité réseau entre :
  - Votre réseau d’entreprise et Azure.
  - Les applications multicouches stratégiques et les microservices.
  - Les emplacements des utilisateurs et les applications web (HTTP/HTTPS).

Cette stratégie offre une visibilité de la couche réseau, sans recourir à SNMP. Elle peut également présenter, sur une carte topologique interactive, la topologie tronçon par tronçon des itinéraires entre le point de terminaison source et le point de terminaison de destination. Il est préférable d'essayer d'obtenir le même résultat avec la supervision du réseau dans Operations Manager, ou avec d'autres outils de supervision du réseau actuellement utilisés dans votre environnement.

### <a name="monitor-with-azure-monitor"></a>Surveiller avec Azure Monitor

Bien que la migration vers le cloud présente de nombreux défis, elle comporte également un certain nombre d'opportunités. Elle permet à votre organisation de migrer à partir d'un ou plusieurs outils de supervision d'entreprise locaux pour réduire les dépenses d'investissement et les coûts d'exploitation, ainsi que pour tirer parti des avantages d'une plateforme de supervision cloud telle qu'Azure Monitor à l'échelle du cloud. Examinez vos besoins en matière de supervision et d'alertes, la configuration des outils de supervision existants, et les charges de travail qui migrent vers le cloud. Une fois votre plan finalisé, configurez Azure Monitor.

- Supervisez l'infrastructure et les applications hybrides, à partir d'une architecture simple ou multiniveau dans laquelle les composants sont hébergés entre Azure, d'autres fournisseurs de services cloud et votre réseau d'entreprise. Les composants peuvent inclure une ou plusieurs machines virtuelles, plusieurs machines virtuelles placées dans un groupe à haute disponibilité ou un groupe de machines virtuelles identiques, ou une application en conteneur déployée sur Azure Kubernetes Service (AKS) et exécutée sur des conteneurs Windows Server ou Linux.

- Activez Azure Monitor pour machines virtuelles, Azure Monitor pour conteneurs et Application Insights afin de détecter et de diagnostiquer les problèmes entre l’infrastructure et les applications. Pour une analyse et une corrélation plus approfondies des données collectées à partir des différents composants ou dépendances sur lesquels repose l'application, vous devez utiliser les journaux Azure Monitor.

- Créez des alertes intelligentes qui s’appliquent à un ensemble principal d’applications et de composants de service, réduisez le bruit d’alerte avec des seuils dynamiques pour les signaux complexes et utilisez l’agrégation d’alertes basée sur les algorithmes Machine Learning pour identifier rapidement le problème.

- Définissez une bibliothèque de requêtes et de tableaux de bord pour répondre aux exigences des différents membres du service informatique.

- Définissez les normes et les méthodes relatives à la supervision des différentes ressources hybrides et cloud, une base de référence de supervision pour chaque ressource, des seuils d'alerte, etc.  

- Configurez le contrôle d'accès en fonction du rôle (RBAC) afin de n'accorder aux utilisateurs et aux groupes que le type d'accès dont ils ont besoin pour superviser les données des ressources dont ils sont responsables.

- Incluez l'automatisation et le libre-service pour permettre à chaque équipe de créer, d'activer et de paramétrer ses configurations de supervision et d'alerte selon les besoins.

## <a name="private-cloud-monitoring"></a>Supervision d’un cloud privé

Vous pouvez effectuer une supervision complète d’Azure Stack avec System Center Operations Manager. Plus précisément, vous pouvez superviser les charges de travail exécutées dans le locataire, le niveau des ressources sur les machines virtuelles, et l'infrastructure qui héberge Azure Stack (serveurs physiques et commutateurs réseau).

Vous pouvez également effectuer une supervision complète avec une combinaison de [fonctionnalités de supervision d'infrastructure](https://docs.microsoft.com/azure/azure-stack/azure-stack-monitor-health) incluses dans Azure Stack. Ces fonctionnalités vous permettent de voir l’intégrité et les alertes pour une région Azure Stack et le [service Azure Monitor](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-metrics-azure-data) dans Azure Stack, ce qui fournit des métriques et des journaux de l’infrastructure à un niveau de base pour la plupart des services.

Si vous avez déjà investi dans Operations Manager, utilisez le pack d’administration Azure Stack pour superviser la disponibilité et l’état d’intégrité des déploiements Azure Stack, notamment les régions, les fournisseurs de ressources, les mises à jour, les exécutions de mises à jour, les unités d’échelle, les nœuds d’unité, les rôles d’infrastructure et leurs instances (entités logiques constituées des ressources matérielles). Ce pack d’administration utilise les API REST du fournisseur de ressources d’intégrité et de mise à jour pour communiquer avec Azure Stack. Pour superviser des serveurs physiques et des périphériques de stockage, utilisez le pack d’administration des fournisseurs OEM (par exemple fourni par Lenovo, Hewlett Packard ou Dell). Operations Manager peut superviser les commutateurs réseau en mode natif pour collecter des statistiques de base à l'aide du protocole SNMP. La supervision des charges de travail du locataire est possible avec le pack d’administration Azure en suivant deux étapes de base. Configurez l’abonnement que vous voulez superviser, puis ajoutez les moniteurs pour cet abonnement.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Collecte des données appropriées](./data-collection.md)
