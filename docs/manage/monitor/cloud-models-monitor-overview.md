---
title: Guide de supervision du cloud - Stratégie de supervision pour les modèles de déploiement cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Choisir quand utiliser Azure Monitor ou System Center Operations Manager dans Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: badf03f3616de8e6612221282aa24996f0b6e8f8
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221131"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guide de supervision du cloud : Stratégie de supervision pour les modèles de déploiement cloud

Cet article inclut notre stratégie de supervision recommandée pour chacun des modèles de déploiement cloud, en fonction des critères suivants :

- Vous avez besoin d’un engagement permanent pour Operations Manager ou d’une autre plateforme de supervision d’entreprise. Ceci est dû à l’intégration à vos processus, vos connaissances et votre expertise en matière d’exploitation informatique, ou au fait que certaines fonctionnalités ne sont pas encore disponibles dans Azure Monitor.
- Vous devez superviser des charges de travail locales et dans le cloud public, ou seulement dans le cloud.
- Votre stratégie de migration cloud comprend la modernisation des opérations informatiques, et la migration vers nos services et solutions de supervision cloud.
- Vous pouvez avoir des systèmes critiques en « air gap » ou physiquement isolés, hébergés dans un cloud privé ou sur du matériel physique, et qui doivent être supervisés.

Notre stratégie comprend la supervision de l’infrastructure (charges de travail de calcul, de stockage et de serveur), des applications (utilisateur final, exceptions et client) et des ressources réseau, pour offrir une perspective de supervision complète et orientée service.

## <a name="azure-cloud-monitoring"></a>Supervision du cloud Azure

Azure Monitor est le service de plateforme qui fournit une source unique d’analyse des ressources Azure. Il est conçu pour les solutions cloud basées sur Azure et qui prennent en charge une fonctionnalité métier basée sur des charges de travail de machine virtuelle, ou sur des architectures complexes utilisant des microservices et d’autres ressources de plateforme. Il supervise toutes les couches de la pile, en commençant par les services de locataire, comme Azure Active Directory Domain Services, et les événements de niveau abonnement et l’intégrité des services Azure. Il supervise également les ressources de l’infrastructure, comme les machines virtuelles, le stockage et les ressources réseau, et, au niveau de la couche supérieure, votre application. La supervision de chacune de ces dépendances et la collecte des bons signaux que chacune peut émettre, permet l’observabilité des applications et vous donne l’infrastructure clé dont vous avez besoin.

Le tableau suivant récapitule l’approche recommandée pour superviser chaque couche de la pile.

<!-- markdownlint-disable MD033 -->

Couche | Ressource | Étendue | Méthode
---|---|---|----
Application | Application web s’exécutant sur une plateforme .NET, .NET Core, Java, JavaScript et Node.js sur une machine virtuelle Azure, Azure App Services, Azure Service Fabric, Azure Functions et Azure Cloud Services | Supervise une application web en direct pour détecter automatiquement les anomalies de performances, identifier les exceptions et les problèmes du code, et collecter la télémétrie d’utilisabilité. |  Application Insights
Containers | Azure Kubernetes Service/Azure Container Instances | Supervise la capacité, la disponibilité et les performances des charges de travail s’exécutant sur des conteneurs et des instances de conteneur. | Azure Monitor pour des conteneurs
Système d’exploitation invité | Système d’exploitation de machine virtuelle Linux et Windows | Supervise la capacité, la disponibilité et les performances. Mappe les dépendances hébergées sur chaque machine virtuelle, notamment la visibilité des connexions réseau actives entre les serveurs, la latence des connexions entrantes et sortantes, et les ports sur n’importe quelle architecture connectée à TCP. | Azure Monitor pour machines virtuelles
Ressources Azure - PaaS | Services Azure Database (par exemple SQL ou MySQL) | Métriques de performances Azure Database pour SQL. | Active la journalisation des diagnostics pour le streaming des données SQL vers les journaux d’Azure Monitor.
Ressources Azure - IaaS | 1. Stockage Azure<br/> 2. Azure Application Gateway<br/> 3. Azure Key Vault<br/> 4. Groupes de sécurité réseau<br/> 5. Azure Traffic Manager | 1. Capacité, disponibilité et performances.<br/> 2. Performances et journaux de diagnostics (activité, accès, performances et pare-feu).<br/> 3. Supervise comment, quand et qui accède à vos coffres de clés.<br/> 4. Supervise les événements quand des règles sont appliquées, et le compteur de règles indiquant combien de fois une règle est appliquée pour refuser ou pour autoriser.<br/>5. Supervise la disponibilité de l’état des points de terminaison. | 1. Métriques de stockage pour Stockage Blob.<br/> 2. Active la journalisation des diagnostics et configure le streaming vers les journaux d’Azure Monitor.<br/> 3. Active la journalisation des diagnostics et configure le streaming vers les journaux d’Azure Monitor, puis active la [solution Azure Key Vault Analytics](https://docs.microsoft.com/azure/azure-monitor/insights/azure-key-vault). <br/> 4. Active la journalisation des diagnostics des groupes de sécurité réseau et configure le streaming vers les journaux d’Azure Monitor.<br/> 5. Active la journalisation des diagnostics des points de terminaison Traffic Manager et configure le streaming vers les journaux d’Azure Monitor.
Réseau| Communication entre votre machine virtuelle et un ou plusieurs points de terminaison (une autre machine virtuelle, un nom de domaine complet, un URI ou une adresse IPv4). | Supervise l’accessibilité, la latence et les changements de topologie réseau qui se produisent entre la machine virtuelle et le point de terminaison. | Azure Network Watcher
Abonnement Azure | Intégrité des services Azure et intégrité des ressources de base | <li> Actions d’administration effectuées sur un service ou une ressource.<br/><li> L’intégrité du service pour un service Azure se trouve dans un état dégradé ou indisponible.<br/><li> Problèmes d’intégrité détectés avec une ressource Azure du point de vue du service Azure.<br/><li> Opérations effectuées avec la mise à l’échelle automatique Azure indiquant un échec ou une exception. <br/><li> Opérations effectuées avec Azure Policy indiquant qu’une action autorisée ou refusée s’est produite.<br/><li> Enregistrement des alertes générées par Azure Security Center. |Fourni dans le journal d’activité pour la supervision et les alertes avec Azure Resource Manager.
Client Azure|Azure Active Directory || Active la journalisation des diagnostics et configure le streaming vers les journaux d’Azure Monitor.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Supervision d’un cloud hybride

Cette section est actuellement en cours de développement et fournira un ensemble complet de recommandations destinées à répondre à votre intérêt pour ce modèle de cloud. Elle sera bientôt disponible.  

## <a name="private-cloud-monitoring"></a>Supervision d’un cloud privé

Vous pouvez effectuer une supervision complète d’Azure Stack avec System Center Operations Manager. Plus précisément, vous pouvez superviser les charges de travail qui s’exécutent dans le locataire, le niveau des ressources sur les machines virtuelles et l’infrastructure qui héberge Azure Stack (serveurs physiques et commutateurs réseau). Vous pouvez également effectuer une supervision complète avec une combinaison de [fonctionnalités de supervision d’infrastructure](https://docs.microsoft.com/azure/azure-stack/azure-stack-monitor-health) incluses dans Azure Stack. Ces fonctionnalités vous permettent de voir l’intégrité et les alertes pour une région Azure Stack et le [service Azure Monitor](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-metrics-azure-data) dans Azure Stack, ce qui fournit des métriques et des journaux de l’infrastructure à un niveau de base pour la plupart des services.

Si vous avez déjà investi dans Operations Manager, utilisez le pack d’administration Azure Stack pour superviser la disponibilité et l’état d’intégrité des déploiements Azure Stack. Ceci inclut les régions, les fournisseurs de ressources, les mises à jour, les exécutions des mises à jour, les unités d’échelle, les nœuds d’unité, les rôles d’infrastructure et leurs instances (entités logiques constituées des ressources matérielles). Il utilise les API REST du fournisseur de ressources d’intégrité et de mise à jour pour communiquer avec Azure Stack. Pour superviser des serveurs physiques et des périphériques de stockage, utilisez le pack d’administration des fournisseurs OEM (par exemple fourni par Lenovo, Hewlett Packard ou Dell). Operations Manager peut superviser nativement les commutateurs réseau pour collecter des statistiques en utilisant le protocole SNMP. La supervision des charges de travail du locataire est possible avec le pack d’administration Azure en suivant deux étapes de base. Configurez l’abonnement que vous voulez superviser, puis ajoutez les moniteurs pour cet abonnement.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Collecte des données appropriées](./data-collection.md)
