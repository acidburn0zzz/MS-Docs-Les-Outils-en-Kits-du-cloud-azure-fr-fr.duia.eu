---
title: Activer le suivi et les alertes pour les changements critiques
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Activer le suivi et les alertes pour les changements critiques
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 93449f754e3908e092fa64c55ad62fc604b4ba5b
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031312"
---
# <a name="enable-tracking-and-alerting-for-critical-changes"></a>Activer le suivi et les alertes pour les changements critiques

Les services Change Tracking et Inventory d’Azure fournissent des alertes sur l’état de la configuration de votre environnement hybride et sur les modifications apportées à cet environnement. Vous pouvez superviser les modifications de fichiers, de services, de logiciels et de registres critiques susceptibles d’affecter vos serveurs déployés.

Par défaut, le service d’inventaire Azure Automation ne supervise pas les fichiers ou les paramètres de registre. La solution fournit une liste de clés de Registre que nous vous recommandons de superviser. Pour voir cette liste, accédez à votre compte Automation dans le portail Azure, puis sélectionnez **Inventorier** > **Modifier les paramètres** :

![Capture d’écran de l’affichage de l’inventaire Azure Automation dans le portail Azure](./media/change-tracking1.png)

Pour plus d’informations sur chaque clé de Registre, consultez [Suivi des modifications des clés de Registre](https://docs.microsoft.com/azure/automation/automation-change-tracking#registry-key-change-tracking). Vous pouvez évaluer, puis activer chaque clé en la sélectionnant. Le paramétrage s’applique à toutes les machines virtuelles activées dans l’espace de travail actuel.

Vous pouvez également effectuer le suivi des modifications de fichiers critiques. Par exemple, vous pouvez suivre le fichier C:\windows\system32\drivers\etc\hosts, car le système d’exploitation l’utilise pour mapper les noms d’hôte à des adresses IP. Toute modification apportée à ce fichier peut entraîner des problèmes de connectivité ou rediriger le trafic vers des sites web dangereux.

Pour activer le suivi du contenu du fichier hosts, suivez les étapes décrites dans [Activer le suivi de contenu de fichier](https://docs.microsoft.com/azure/automation/change-tracking-file-contents#enable-file-content-tracking).

Vous pouvez également ajouter une alerte pour les modifications apportées aux fichiers que vous suivez. Par exemple, imaginons que vous souhaitiez définir une alerte pour les modifications apportées au fichier hosts. Commencez par accéder à log Analytics en sélectionnant **Log Analytics** dans la barre de commandes ou en ouvrant Recherche dans les journaux pour l’espace de travail Log Analytics lié. Une fois que vous êtes dans Log Analytics, recherchez les modifications de contenu apportées au fichier hosts à l’aide de la requête suivante :

```kusto
ConfigurationChange | where FieldsChanged contains "FileContentChecksum" and FileSystemPath contains "hosts"
```

![Capture d’écran de l’éditeur de requête Log Analytics dans le portail Azure](./media/change-tracking2.png)

Cette requête recherche les modifications apportées au contenu des fichiers dont le chemin d’accès contient le mot « hosts ». Vous pouvez également rechercher un fichier spécifique en changeant le paramètre du chemin. (Par exemple, `FileSystemPath ==  "c:\\windows\\system32\\drivers\\etc\\hosts"`.)
  
Une fois que la requête a retourné les résultats, sélectionnez **Nouvelle règle d’alerte** pour ouvrir l’éditeur de règles d’alerte. Vous pouvez également accéder à cet éditeur via Azure Monitor dans le portail Azure.

Dans l’éditeur de règles d’alerte, passez en revue la requête et changez la logique d’alerte, si nécessaire. Dans ce cas, nous voulons que l’alerte soit déclenchée si des modifications sont détectées sur n’importe quelle machine de l’environnement.

![Capture d’écran de l’éditeur de règles d’alerte Log Analytics dans le portail Azure](./media/change-tracking3.png)

Une fois que vous avez défini la logique de condition, vous pouvez attribuer des groupes d’actions pour répondre à l’alerte. Dans cet exemple, quand l’alerte est déclenchée, des e-mails sont envoyés et un ticket ITSM est créé. Vous pouvez entreprendre de nombreuses autres actions utiles, telles que le déclenchement d’une fonction Azure, d’un runbook Azure Automation, d’un webhook ou d’une application logique.

![Capture d’écran de l’exemple de récapitulatif de règles d’alerte dans le portail Azure](./media/change-tracking4.png)

Une fois que vous avez défini tous les paramètres et la logique, appliquez l’alerte à l’environnement.

## <a name="more-tracking-and-alerting-examples"></a>Autres exemples de suivi et d’alerte

Voici d’autres scénarios courants de suivi et d’alerte que vous pouvez envisager :

### <a name="driver-file-changed"></a>Fichier de pilote modifié

Détecte si des fichiers de pilote sont changés, ajoutés ou supprimés. Utile pour le suivi des modifications apportées aux fichiers système critiques

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Files" and FileSystemPath contains " c:\\windows\\system32\\drivers\\"
  ```

### <a name="specific-service-stopped"></a>Service spécifique arrêté

Utile pour le suivi des modifications apportées aux services critiques du système

  ```kusto
  ConfigurationChange | where SvcState == "Stopped" and SvcName contains "w3svc"
  ```

### <a name="new-software-installed"></a>Nouveau logiciel installé

Utile pour les environnements devant verrouiller des configurations logicielles

  ```kusto
  ConfigurationChange | where ConfigChangeType == "Software" and ChangeCategory == "Added"
  ```

### <a name="specific-software-version-is-or-isnt-installed-on-a-machine"></a>Une version du logiciel spécifique est ou n’est pas installée sur une machine

Utile pour évaluer la sécurité. Notez que cette requête référence `ConfigurationData`, qui contient les journaux d’activité pour Inventory et signale le dernier état de configuration rapportée, pas les modifications.

  ```kusto
  ConfigurationData | where SoftwareName contains "Monitoring Agent" and CurrentVersion != "8.0.11081.0"
  ```

### <a name="known-dll-changed-through-registry"></a>DLL connue changée par le biais du registre

Utile pour détecter les modifications apportées aux clés de Registre connues.

  ```kusto
  ConfigurationChange | where RegistryKey == "HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Control\\Session Manager\\KnownDlls"
  ```

## <a name="next-steps"></a>Étapes suivantes

Apprenez à gérer les mises à jour de vos serveurs en [créant des planifications de mise à jour](./update-schedules.md) avec Azure Automation.

> [!div class="nextstepaction"]
> [Créer des planifications de mise à jour](./update-schedules.md)
