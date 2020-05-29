---
title: Suivi et alertes liés aux changements critiques
description: Activez le suivi et les alertes liés aux changements critiques dans votre environnement hybride avec les services Change Tracking et Inventory d’Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 1fa20d37c5cc7813220ff5862743f3179f4aefcd
ms.sourcegitcommit: bd9872320b71245d4e9a359823be685e0f4047c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83861512"
---
<!-- cSpell:ignore HKEY kusto -->

# <a name="enable-tracking-and-alerting-for-critical-changes"></a>Activer le suivi et les alertes pour les changements critiques

Les services Change Tracking et Inventory d’Azure fournissent des alertes sur l’état de la configuration de votre environnement hybride et sur les modifications apportées à cet environnement. Ils peuvent faire des rapports sur les modifications de fichiers, de services, de logiciels et de registres critiques susceptibles d’affecter vos serveurs déployés.

Par défaut, le service d’inventaire Azure Automation ne supervise pas les fichiers ou les paramètres de registre. La solution fournit une liste de clés de Registre que nous vous recommandons de superviser. Pour voir cette liste, accédez à votre compte Automation sur le portail Azure, puis sélectionnez **Inventorier** > **Modifier les paramètres**.

![Capture d’écran de l’affichage de l’inventaire Azure Automation dans le portail Azure](./media/change-tracking1.png)

Pour plus d’informations sur chaque clé de Registre, consultez [Suivi des modifications des clés de Registre](https://docs.microsoft.com/azure/automation/automation-change-tracking#registry-key-change-tracking). Sélectionnez une clé quelconque à évaluer, puis activez-la. Le paramétrage s’applique à toutes les machines virtuelles activées dans l’espace de travail actuel.

Vous pouvez également utiliser le service pour assurer le suivi des modifications de fichiers critiques. Par exemple, vous pouvez suivre le fichier C:\windows\system32\drivers\etc\hosts, car le système d’exploitation l’utilise pour mapper les noms d’hôte à des adresses IP. Les modifications apportées à ce fichier peuvent entraîner des problèmes de connectivité ou rediriger le trafic vers des sites web dangereux.

Pour activer le suivi du contenu du fichier hosts, suivez les étapes décrites dans [Activer le suivi de contenu de fichier](https://docs.microsoft.com/azure/automation/change-tracking-file-contents#enable-file-content-tracking).

Vous pouvez également ajouter une alerte en cas de modifications des fichiers que vous suivez. Par exemple, imaginons que vous souhaitiez définir une alerte pour les modifications du fichier hosts. Sélectionnez **Log Analytics** sur la barre de commandes, ou Log Search pour l’espace de travail Log Analytics lié. Dans Log Analytics, utilisez la requête suivante pour rechercher des modifications apportées au fichier hosts :

  ```kusto
  ConfigurationChange | where FieldsChanged contains "FileContentChecksum" and FileSystemPath contains "hosts"
  ```

![Capture d’écran de l’éditeur de requête Log Analytics dans le portail Azure](./media/change-tracking2.png)

Cette requête recherche les changements apportés au contenu des fichiers dont le chemin contient le mot « hosts ». Vous pouvez également rechercher un fichier spécifique en changeant le paramètre du chemin. (Par exemple, `FileSystemPath ==  "c:\\windows\\system32\\drivers\\etc\\hosts"`.)
  
Une fois que la requête a retourné les résultats, sélectionnez **Nouvelle règle d’alerte** pour ouvrir l’éditeur de règles d’alerte. Vous pouvez également accéder à cet éditeur via Azure Monitor dans le portail Azure.

Dans l’éditeur de règles d’alerte, passez en revue la requête et changez la logique d’alerte, si nécessaire. Dans ce cas, nous voulons que l’alerte soit déclenchée si des modifications sont détectées sur n’importe quelle machine de l’environnement.

![Capture d’écran de l’éditeur de règles d’alerte Log Analytics dans le portail Azure](./media/change-tracking3.png)

Une fois que vous avez défini la logique de condition, vous pouvez attribuer des groupes d’actions pour répondre à l’alerte. Dans cet exemple, quand l’alerte est déclenchée, des e-mails sont envoyés et un ticket ITSM est créé. Vous pouvez entreprendre de nombreuses autres actions utiles, telles que le déclenchement d’une fonction Azure, d’un runbook Azure Automation, d’un webhook ou d’une application logique.

![Capture d’écran de l’exemple de récapitulatif de règles d’alerte dans le portail Azure](./media/change-tracking4.png)

Une fois que vous avez défini tous les paramètres et la logique, appliquez l’alerte à l’environnement.

## <a name="tracking-and-alerting-examples"></a>Exemples de suivi et d’alerte

Cette section présente d’autres scénarios courants de suivi et d’alerte que vous voulez peut-être utiliser.

### <a name="driver-file-changed"></a>Fichier de pilote modifié

Utilisez la requête suivante pour détecter si des fichiers de pilote sont changés, ajoutés ou supprimés. C’est utile pour le suivi des modifications apportées aux fichiers système critiques.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Files" and FileSystemPath contains " c:\\windows\\system32\\drivers\\"
  ```

### <a name="specific-service-stopped"></a>Service spécifique arrêté

Utilisez la requête suivante pour suivre les modifications apportées aux services critiques pour le système.

  ```kusto
  ConfigurationChange | where SvcState == "Stopped" and SvcName contains "w3svc"
  ```

### <a name="new-software-installed"></a>Nouveau logiciel installé

Utilisez la requête suivante pour les environnements devant verrouiller des configurations logicielles.

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Software" and ChangeCategory == "Added"
  ```

### <a name="specific-software-version-is-or-isnt-installed-on-a-machine"></a>Une version du logiciel spécifique est ou n’est pas installée sur une machine

Utilisez la requête suivante pour évaluer la sécurité. Cette requête référence `ConfigurationData`, qui contient les journaux d’activité pour Inventory et indique le dernier état de configuration rapportée, pas les modifications.

  ```kusto
  ConfigurationData | where SoftwareName contains "Monitoring Agent" and CurrentVersion != "8.0.11081.0"
  ```

### <a name="known-dll-changed-through-the-registry"></a>DLL connue changée par le biais du registre

Utilisez la requête suivante pour détecter les modifications apportées à des clés de Registre bien connues.

  ```kusto
  ConfigurationChange | where RegistryKey == "HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Control\\Session Manager\\KnownDlls"
  ```

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment Azure Automation [crée des planifications de mise à jour](./update-schedules.md) afin de gérer les mises à jour de vos serveurs.

> [!div class="nextstepaction"]
> [Créer des planifications de mise à jour](./update-schedules.md)
