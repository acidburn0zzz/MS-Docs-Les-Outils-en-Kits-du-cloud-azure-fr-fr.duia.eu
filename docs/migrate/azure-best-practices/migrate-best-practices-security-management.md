---
title: Sécurisation et gestion des charges de travail migrées vers Azure
description: Utilisez le Cloud Adoption Framework pour Azure afin de découvrir les bonnes pratiques d’utilisation, de gestion et de sécurisation de vos charges de travail migrées.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d61816b0140c36aa405025358a43068201bcad03
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79311929"
---
# <a name="best-practices-for-securing-and-managing-workloads-migrated-to-azure"></a>Meilleures pratiques pour la sécurisation et la gestion des charges de travail migrées vers Azure

Lorsque vous planifiez et concevez la migration, en plus de penser à la migration elle-même, vous devez considérer votre modèle de sécurité et de gestion dans Azure après la migration. Cet article décrit la planification et les meilleures pratiques pour la sécurisation de votre déploiement Azure après la migration, et pour les tâches en cours afin de maintenir votre déploiement à un niveau optimal.

> [!IMPORTANT]
> Les meilleures pratiques et opinions décrites dans cet article sont basées sur la plateforme Azure et les fonctionnalités disponibles au moment de la rédaction. Les fonctionnalités et les capacités changent au fil du temps.

## <a name="secure-migrated-workloads"></a>Sécuriser les charges de travail migrées

Après la migration, la tâche la plus critique consiste à protéger les charges de travail migrées des menaces internes et externes. Ces meilleures pratiques vous aideront à le faire :

- [Utiliser Azure Security Center](#best-practice-follow-azure-security-center-recommendations) : Découvrez comment utiliser la supervision, les évaluations et les recommandations fournies par Azure Security Center.
- [Chiffrer vos données](#best-practice-encrypt-data) : Obtenez les meilleures pratiques pour chiffrer vos données dans Azure.
- [Configurer un logiciel anti-programme malveillant](#best-practice-protect-vms-with-antimalware) : Protégez vos machines virtuelles contre les attaques et logiciels malveillants.
- [Sécuriser les applications web](#best-practice-secure-web-apps) : Protégez les informations sensibles dans les applications web migrées.
- [Réviser les abonnements](#best-practice-review-subscriptions-and-resource-permissions) : Vérifiez qui peut accéder à vos abonnements et ressources Azure après la migration.
- [Utiliser les journaux d’activité](#best-practice-review-audit-and-security-logs) : Passez en revue vos journaux d’activité d’audit et de sécurité Azure régulièrement.
- [Réviser les autres fonctionnalités de sécurité](#best-practice-evaluate-other-security-features) : Comprenez et évaluez les fonctionnalités de sécurité avancées d’Azure.

## <a name="best-practice-follow-azure-security-center-recommendations"></a>Bonne pratique : Suivre les recommandations d’Azure Security Center

Microsoft fait tout son possible pour que les administrateurs locataires Azure disposent des informations nécessaires pour activer les fonctionnalités de sécurité qui protègent les charges de travail contre les attaques. Azure Security Center fournit la gestion de la sécurité unifiée. Depuis le Security Center, vous pouvez appliquer des stratégies de sécurité sur l’ensemble des charges de travail, limiter l’exposition aux menaces, détecter et répondre aux attaques. Security Center analyse les ressources et les configurations des locataires Azure et émet des recommandations en matière de sécurité, notamment :

- **Gestion de stratégie centralisée :** Assurez la conformité aux exigences de sécurité obligatoires ou de votre société en gérant de façon centralisée les stratégies de sécurité dans toutes vos charges de travail cloud hybrides.
- **Évaluation continue de la sécurité :** Supervisez la posture de sécurité des machines, réseaux, services de stockage et de données, et des applications pour découvrir d’éventuels problèmes de sécurité.
- **Recommandations exploitables :** Corrigez les failles de sécurité avant qu’elles ne puissent être exploitées par des attaquants avec des recommandations de sécurité exploitables et classées par ordre de priorité.
- **Alertes et incidents classés par ordre de priorité :** Concentrez-vous en premier lieu sur les menaces les plus importantes avec les incidents et alertes de sécurité classés par ordre de priorité.

En plus des évaluations et des recommandations, Azure Security Center offre un d’autres fonctionnalités de sécurité qui peuvent être activées pour des ressources spécifiques.

- **Accès juste-à-temps (JIT).** Réduisez votre surface d’attaque réseau grâce à un accès contrôlé et juste à temps aux ports de gestion sur les machines virtuelles Azure.
  - Si le port RDP 3389 de vos machines virtuelles est ouvert sur Internet, celles-ci sont exposés à l’activité continue d’acteurs malveillants. Les adresses IP Azure sont bien connues et les pirates les sondent continuellement pour détecter les attaques sur les ports 3389 ouverts.
  - JIT utilise des groupes de sécurité réseau (NSG) et des règles entrantes qui limitent la durée d’ouverture d’un port spécifique.
  - Alors que l’option juste à temps est activée, Security Center vérifie qu’un utilisateur dispose des droits d’accès en écriture du contrôle d’accès en fonction du rôle (RBAC) pour une machine virtuelle. En outre, définissez des règles sur la façon dont les utilisateurs peuvent se connecter aux machines virtuelles. Si les autorisations sont correctes, une requête d’accès est approuvée et Security Center configure les Groupes de sécurité réseau (NSG) afin d’autoriser le trafic entrant vers les ports sélectionnés pendant la durée que vous spécifiez. Les groupe de sécurité réseau retournent à leur état antérieur à l’expiration du délai.
- **Contrôles d’application adaptative.** Protégez les machines virtuelles contre les attaques et logiciels malveillants en déterminant, dans une liste verte dynamique d’applications, quelles applications s’exécutent sur elles.
  - Les contrôles d’application adaptatifs vous permettent de placer des applications en liste verte et d’empêcher les utilisateurs ou administrateurs malhonnêtes d’installer des applications logicielles non approuvées ou en cours d’approbation sur vos machines virtuelles.
    - Vous pouvez bloquer ou alerter les tentatives d’exécution d’applications malveillantes, éviter les applications indésirables ou malveillantes et garantir la conformité avec la stratégie de sécurité de sécurité des applications de votre organisation.
- **Monitoring d’intégrité de fichier.** Garantissez l’intégrité des fichiers s’exécutant sur les machines virtuelles.
  - Des problèmes de machines virtuelles peuvent se produire indépendamment de l’installation de logiciels. La modification d’un fichier système peut également entraîner une défaillance de la machine virtuelle ou une dégradation des performances. Le Monitoring d’intégrité de fichier examine les fichiers système et les paramètres du registre pour détecter les modifications et vous avertit si quelque chose est mis à jour.
  - Security Center recommande les fichiers à surveiller.

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/security-center/security-center-intro) sur Azure Security Center.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/security-center/security-center-just-in-time) sur l’accès aux machines virtuelles juste-à-temps.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/security-center/security-center-adaptive-application) sur l’activation des contrôles d’applications adaptatifs.
- [Prise en main](https://docs.microsoft.com/azure/security-center/security-center-file-integrity-monitoring) du Monitoring d’intégrité de fichier.

## <a name="best-practice-encrypt-data"></a>Bonne pratique : Chiffrer les données

Le chiffrement est une partie importante des pratiques de sécurité d’Azure. S’assurer que le cryptage est activé à tous les niveaux évite que les parties non autorisées accèdent aux données sensibles, notamment les données en transit et au repos.

### <a name="encryption-for-iaas"></a>Chiffrement pour IaaS

- **Machines virtuelles :** Pour les machines virtuelles, vous pouvez utiliser Azure Disk Encryption pour chiffrer vos disques de machines virtuelles Windows et Linux IaaS.
  - Le chiffrement de disque tire parti de BitLocker pour Windows et DM-Crypt pour Linux pour le chiffrement de volume pour le système d’exploitation et les disques de données.
  - Vous pouvez utiliser une clé de chiffrement créée par Azure, ou fournir vos propres clés de chiffrement, sauvegardées dans Azure Key Vault.
  - Avec la fonctionnalité Chiffrement de disque, les données de machine virtuelle IaaS sont sécurisées au repos (sur le disque) et pendant le démarrage de la machine virtuelle.
    - Azure Security Center vous envoie une alerte dès lors que certaines de vos machines virtuelles ne sont pas chiffrées.
- **Stockage :** Protégez les données au repos stockées dans Stockage Azure.
  - Les données stockées dans les comptes de stockage Azure peuvent être chiffrées à l’aide de clés AES générées par Microsoft et conformes à la norme FIPS 140-2 ; vous pouvez également utiliser vos propres clés.
  - Storage Service Encryption est activé pour tous les comptes de stockage nouveaux et existants et ne peut pas être désactivé.

### <a name="encryption-for-paas"></a>Chiffrement pour PaaS

Contrairement à IaaS où vous gérez vos propres machines virtuelles et votre infrastructure, dans un modèle PaaS, la plate-forme et l’infrastructure sont gérées par le fournisseur, ce qui vous permet de vous concentrer sur la logique et les capacités des applications centrales. Avec autant de types de service PaaS différents, chaque service est évalué individuellement pour des raisons de sécurité. À titre d’exemple, voyons comment nous pourrions activer le chiffrement pour Azure SQL Database.

- **Always Encrypted :** L’assistant Always Encrypted de SQL Server Management Studio permet de protéger les données au repos.
  - Vous créez une clé Always Encrypted pour chiffrer des données de colonne individuelle.
  - Les clés Always Encrypted peuvent être stockées sous forme chiffrée dans les métadonnées de la base de données ou stockées dans des magasins de clés sécurisés, tels qu’Azure Key Vault.
  - Des changements seront probablement nécessaires dans l’application pour que cette fonctionnalité puisse être utilisée.
- **Transparent Data Encryption (TDE) :** Protégez la base de données Azure SQL Database à l’aide du chiffrement et du déchiffrement en temps réel de la base de données, des sauvegardes associées et des fichiers journaux de transactions au repos.
  - TDE permet aux activités de chiffrement d’avoir lieu sans modification au niveau de la couche applicative.
  - TDE peut utiliser les clés de chiffrement fournies par Microsoft ou vous pouvez fournir vos propres clés en utilisant le support Bring Your Own Key.

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/security/azure-security-disk-encryption-overview) sur Azure Disk Encryption pour machines virtuelles Iaas.
- [Activez](https://docs.microsoft.com/azure/security/azure-security-disk-encryption-windows) le chiffrement pour les machines virtuelles IaaS Windows.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) sur Azure Storage Service Encryption pour les données au repos.
- [Lisez](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) une présentation d’Always Encrypted.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-azure-sql?view=sql-server-2017) sur TDE pour Azure SQL Database.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql) sur TDE avec Service Bring Your Own Key (BYOK).

## <a name="best-practice-protect-vms-with-antimalware"></a>Bonne pratique : Protéger les machines virtuelles avec un logiciel anti-programme malveillant

En particulier, les anciennes machines virtuelles migrées Azure peuvent ne pas disposer du niveau approprié de logiciel anti-programme malveillant installé. Azure fournit une solution de point de terminaison gratuite qui aide à protéger les machines virtuelles contre les virus, les logiciels espions et autres logiciels malveillants.

- Microsoft Antimalware pour Azure produit des alertes lorsqu’un logiciel malveillant ou indésirable connu tente de s’installer.
- Il s’agit d’une solution d’agent unique qui fonctionne en arrière-plan sans intervention humaine.
- Dans Azure Security Center, vous pouvez facilement identifier les machines virtuelles qui ne disposent pas d’une protection des points de terminaison, et installer Microsoft Antimalware si nécessaire.

![Logiciel anti-programme malveillant pour machines virtuelles](./media/migrate-best-practices-security-management/antimalware.png)
*Logiciel anti-programme malveillant pour machines virtuelles*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/security/azure-security-antimalware) sur Microsoft Antimalware.

## <a name="best-practice-secure-web-apps"></a>Bonne pratique : Sécuriser les applications web

Les applications web migrées sont confrontées à quelques problèmes :

- La plupart des applications web héritées ont tendance à contenir des informations sensibles dans les fichiers de configuration. Les fichiers contenant de telles informations peuvent présenter des problèmes de sécurité lorsque les applications sont sauvegardées, ou lorsque le code de l’application est vérifié dans le cadre ou hors du contrôle source.
- De plus, lorsque vous migrez des applications web résidant dans une machine virtuelle, vous déplacez probablement cette machine d’un environnement réseau et protégé par un pare-feu local vers un environnement accessible sur Internet. Veillez à mettre en place une solution qui fait le même travail que vos ressources de protection locales.

Azure propose quelques solutions :

- **Azure Key Vault :** Aujourd’hui, les développeurs d’applications web prennent des mesures pour s’assurer que les informations sensibles de ces fichiers ne sont pas divulguées. Une méthode pour sécuriser les informations est de les extraire des fichiers et de les placer dans un Azure Key Vault.
  - Vous pouvez utiliser un coffre de clés pour centraliser le stockage des secrets d’application et contrôler leur distribution. Cela évite d’avoir à stocker les informations de sécurité dans les fichiers d’application.
  - Les applications peuvent sécuriser l’accès aux informations dans le coffre à l’aide des URI sans avoir besoin de code personnalisé.
  - Azure Key Vault vous permet de verrouiller l’accès via les contrôles de sécurité Azure et d’implémenter de manière transparente les « clés propagées ». Microsoft ne voit ni n’extrait vos données.
- **Environnement App Service :** Si une application que vous migrez a besoin d’une protection supplémentaire, vous pouvez envisager d’ajouter un App Service Environment et un pare-feu d’applications pour protéger les ressources d’application.
  - Azure App Service Environment fournit un environnement entièrement isolé et dédié dans lequel exécuter des applications Azure App Service, notamment des applications Web Windows et Linux, des conteneurs Docker, des Mobile Apps et des fonctions.
  - Cela est utile pour les applications à très grande échelle, qui nécessitent une isolation et un accès réseau sécurisé ou qui sollicitent fortement la mémoire.
- **Pare-feu d’application web :** Une fonctionnalité d’Azure Application Gateway qui fournit une protection centralisée pour les applications web.
  - Il protège les applications web sans nécessiter de modifications du code principal.
  - Il protège plusieurs applications web derrière une passerelle d’application.
  - Un pare-feu d’applications web peut être supervisé à l’aide d’Azure Monitor et il est intégré à Azure Security Center.

![Sécuriser les applications web](./media/migrate-best-practices-security-management/web-apps.png)
*Azure Key Vault*

**En savoir plus :**

- [Consultez une vue d’ensemble](https://docs.microsoft.com/azure/key-vault/key-vault-overview) sur Azure Key Vault.
- [En savoir plus](https://docs.microsoft.com/azure/application-gateway/waf-overview) sur le pare-feu d’application web.
- [Consultez une vue d’ensemble](https://docs.microsoft.com/azure/app-service/environment/intro) sur les environnements App Service.
- [Découvrez comment](https://docs.microsoft.com/azure/key-vault/tutorial-web-application-keyvault) configurer une application web pour lire les secrets de Key Vault.
- [En savoir plus](https://docs.microsoft.com/azure/application-gateway/waf-overview) sur le pare-feu d’application web.

## <a name="best-practice-review-subscriptions-and-resource-permissions"></a>Bonne pratique : Examiner les abonnements et les autorisations de ressources

Lorsque vous migrez et exécutez vos charges de travail dans Azure, le personnel ayant accès aux charges de travail se déplace. Votre équipe de sécurité doit examiner régulièrement l’accès à vos groupes de locataires et de ressources Azure. Azure propose des offres pour la gestion des identités et la sécurité du contrôle d’accès, y compris le contrôle d’accès en fonction du rôle (RBAC) pour fournir des autorisations d’accès aux ressources Azure.

- RBAC attribue des autorisations d’accès aux principaux de sécurité. Les principaux de sécurité représentent les utilisateurs, les groupes (ensemble d’utilisateurs), les principaux de service (identité utilisée par les applications et les services) et les identités managées (identité Azure Active Directory managée automatiquement par Azure).
- La fonctionnalité RBAC peut assigner des rôles aux principaux de sécurité, tels que le propriétaire, le contributeur et le lecteur, et assigner des définitions de rôles (ensemble d’autorisations) qui définissent les opérations pouvent être effectuées par les rôles.
- La fonctionnalité RBAC peut aussi établir une étendue qui définit les limites d’un rôle. L’étendue peut être définie à plusieurs niveaux, notamment un groupe d’administration, un abonnement, un groupe de ressources ou une ressource.
- Veillez à ce que les administrateurs avec accès Azure ne puissent accéder qu’aux ressources que vous voulez autoriser. Si les rôles prédéfinis dans Azure ne sont pas assez précis, vous pouvez créer des rôles personnalisés pour séparer et limiter les autorisations d’accès.

![Contrôle d’accès](./media/migrate-best-practices-security-management/subscription.png)
*Contrôle d’accès - IAM*

**En savoir plus :**

- [À propos de](https://docs.microsoft.com/azure/role-based-access-control/overview) RBAC.
- [Découvrez](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) comment gérer les accès à l’aide du contrôle d’accès en fonction du rôle et du portail Azure.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/role-based-access-control/custom-roles) sur les rôles personnalisés.

## <a name="best-practice-review-audit-and-security-logs"></a>Bonne pratique : Réviser les journaux d’activité d’audit et de sécurité

Azure Active Directory (Azure AD) fournit les journaux d’activité qui apparaissent dans Azure Monitor. Les journaux d’activité de bord capturent les opérations effectuées dans la location Azure, le moment où elles ont eu lieu et qui les a effectuées.

- Les journaux d’audit présentent l’historique des tâches dans le locataire. Les journaux d’activité de connexion indiquent qui a effectué les tâches.
- L’accès aux rapports de sécurité dépend de votre licence Azure AD. Avec la licence Gratuit et De base , vous obtenez la liste d’utilisateurs et de connexions à risque. Dans les éditions Premium 1 et Premium 2, vous obtenez des informations sur les événements sous-jacents.
- Vous pouvez maintenant acheminer les journaux d’activité vers divers points de terminaison pour une rétention à long terme et l’analyse des données.
- Prenez l’habitude d’examiner les journaux d’activité ou d’intégrer vos outils de gestion des informations et des événements de sécurité (SIEM) pour examiner automatiquement les anomalies. Si vous n’utilisez pas Premium 1 ou 2, vous devrez effectuer un grand nombre d’analyses vous-même ou utiliser votre système SIEM. L’analyse comprend la recherche de connexions et d’événements à risque, ainsi que d’autres modèles d’attaques d’utilisateurs.

![Utilisateurs et groupes](./media/migrate-best-practices-security-management/azure-ad.png)
*Utilisateurs et utilisateurs Azure AD*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor) sur les journaux d’activité Azure AD dans Azure Monitor.
- [Découvrez comment](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-audit-logs) contrôler les rapports d’activité sur le portail Azure.

## <a name="best-practice-evaluate-other-security-features"></a>Bonne pratique : Évaluer d’autres fonctionnalités de sécurité

Azure offre d’autres fonctionnalités de sécurité qui proposent des options de sécurité avancées. Certaines de ces meilleures pratiques nécessitent des licences supplémentaires et des options premium.

- **Implémenter les unités administratives (AU) d’Azure AD.** Déléguer des tâches administratives au personnel du support peut s’avérer délicat par un simple contrôle d’accès de base Azure. L’attribution d’accès au personnel du support en vue d’administrer tous les groupes Azure AD n’est peut-être pas l’approche idéale pour la sécurité de l’organisation. L’utilisation d’AU vous permet de séparer les ressources Azure dans des conteneurs de la même manière que les unités d’organisation (OU) locales. Pour utiliser AU, l’administrateur de l’UA doit posséder une licence AD Azure Premium. [Plus d’informations](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-administrative-units)
- **Utiliser l’authentification multifacteur.** Si vous possédez une licence premium Azure AD, vous pouvez activer et appliquer l’authentification multifacteur sur vos comptes d’administrateur. L’hameçonnage est le moyen le plus courant de compromettre l’identité des comptes. Une fois qu’une personne malveillante possède des informations d’identification de compte d’administration, rien ne l’empêche d’entreprendre des actions de grande envergure, telles que la suppression de tous vos groupes de ressources. Vous pouvez établir l’authentification multifacteur de plusieurs façons, y compris par e-mail, application d’authentification ou message texte sur téléphone. En tant qu’administrateur, vous pouvez choisir l’option la moins intrusive. La fonctionnalité d’authentification multifacteur s’intègre à l’analyse des menaces et aux stratégies d’accès conditionnel pour exiger aléatoirement une réponse à un défi d’authentification multifacteur. Apprenez-en davantage sur les [conseils de sécurité](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices) et sur la [configuration](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices) de l’authentification multifacteur (MFA).
- **Implémenter l’accès conditionnel.** Dans la plupart des petites et moyennes entreprises, les administrateurs Azure et l’équipe du support technique sont probablement situés dans une même région géographique. Dans ce cas, la plupart des connexions proviendront des mêmes zones. Si les adresses IP de ces emplacements sont assez statiques, il est logique que vous ne puissiez pas voir les connexions administrateur si vous vous trouvez à l’extérieur de ces zones. Même dans le cas où une personne malveillante distante compromet les informations d’identification d’un administrateur, vous pouvez implémenter des fonctionnalités de sécurité telles que l’accès conditionnel associé à la fonctionnalité d’authentification multifacteur pour empêcher la connexion depuis des emplacements distants ou depuis des emplacements usurpés à l’aide d’adresses IP aléatoires. [Apprenez-en davantage](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)sur l’accès conditionnel, et [révisez les meilleures pratiques](https://docs.microsoft.com/azure/active-directory/conditional-access/best-practices) pour l’accès conditionnel dans Azure AD.
- **Révisez les autorisations pour les applications d’entreprise.** Au fil du temps, les administrateurs sélectionnent les liens Microsoft et tiers sans connaître l’impact de ceux-ci sur l’organisation. Les liens peuvent afficher des écrans de consentement qui attribuent des autorisations aux applications Azure et peuvent fournir un accès en lecture des données Azure AD, voire un accès complet en gestion de l’ensemble de votre abonnement Azure. Vous devez régulièrement passer en revue les applications pour lesquelles vos administrateurs et utilisateurs ont autorisé l’accès aux ressources Azure. Assurez-vous que ces applications n’ont que les autorisations nécessaires. De plus, tous les trimestres ou tous les semestres, vous pouvez envoyer un email aux utilisateurs avec un lien vers les pages d’application afin qu’ils sachent à quelles applications ils ont attribué l’accès à leurs données d’organisation. [Apprenez-en plus](https://docs.microsoft.com/azure/active-directory/manage-apps/application-types) sur les types d’applications et sur la [façon de contrôler](https://docs.microsoft.com/azure/active-directory/manage-apps/remove-user-or-group-access-portal) les affectations d’applications dans Azure AD.

## <a name="managed-migrated-workloads"></a>Charges de travail migrées gérées

Dans cette section, nous recommandons d’adopter quelques bonnes pratiques pour la gestion d’Azure, notamment :

- [Gérer les ressources](#best-practice-name-resource-groups) : Meilleures pratiques pour les groupes de ressources et les ressources Azure, y compris le nommage intelligent, la prévention de la suppression accidentelle, la gestion des autorisations des ressources et le balisage efficace des ressources.
- [Utiliser des blueprints](#best-practice-implement-blueprints) : Consultez une vue d’ensemble rapide sur l’utilisation des blueprints pour construire et administrer vos environnements de déploiement.
- [Réviser les architectures](#best-practice-review-azure-reference-architectures) : Passez en revue les exemples d’architectures Azure pour en tirer des leçons lorsque vous construisez vos déploiements après la migration.
- [Configurer les groupes d’administration](#best-practice-manage-resources-with-azure-management-groups) : Si vous avez plusieurs abonnements, vous pouvez les regrouper dans des groupes d’administration et appliquer les paramètres de gouvernance à ces groupes.
- [Configurer les stratégies d’accès](#best-practice-deploy-azure-policy) : Appliquez les stratégies de conformité à vos ressources Azure.
- [Implémenter une stratégie BCDR](#best-practice-implement-a-bcdr-strategy) : Élaborez une stratégie de continuité d’activité et reprise d’activité (BCDR) pour assurer la sécurité des données, la résilience de votre environnement et la disponibilité des ressources en cas de panne.
- [Gérer les machines virtuelles](#best-practice-use-managed-disks-and-availability-sets) : Rassemblez les machines virtuelles en groupes de disponibilité pour la résilience et la haute disponibilité. Utilisez des disques managés pour faciliter la gestion des disques et du stockage des machines virtuelles.
- [Superviser l’utilisation des ressources](#best-practice-monitor-resource-usage-and-performance) : Activez la journalisation des diagnostics pour les ressources Azure, créez des alertes et des playbooks pour un dépannage proactif, et utilisez le tableau de bord Azure pour obtenir un affichage unifié sur l’état d’intégrité et le statut de votre déploiement.
- [Gérer les mises à jour et le support technique](#best-practice-manage-updates) : Comprendre votre plan de support Azure et la façon de le mettre en œuvre, d’obtenir les meilleures pratiques pour maintenir à jour les machines virtuelles et de mettre en place des processus pour la gestion des changements.

## <a name="best-practice-name-resource-groups"></a>Bonne pratique : Groupes de ressources de nom

Afin d’améliorer la productivité et l’efficacité, assurez-vous que vos groupes de ressources ont des noms significatifs que les administrateurs et les membres de l’équipe du support technique peuvent facilement reconnaître et utiliser.

- Nous vous recommandons de suivre les conventions d’affectation de noms Azure.
- Si vous synchronisez votre Active Directory local avec Azure AD à l’aide d’Azure AD Connect, pensez à faire correspondre les noms des groupes de sécurité locaux aux noms des groupes de ressources dans Azure.

![Dénomination](./media/migrate-best-practices-security-management/naming.png)
*Dénomination de groupe de ressources*

**En savoir plus :**

- [Apprenez-en](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) plus sur les conventions d’affectation de noms.

## <a name="best-practice-implement-delete-locks-for-resource-groups"></a>Bonne pratique : Implémenter les verrous de suppression pour les groupes de ressources

La dernière chose dont vous pouvez vous passer est qu’un groupe de ressources disparaisse parce qu’il a été supprimé accidentellement. Nous vous recommandons d’implémenter des verrous de suppression pour que cela ne se produise pas.

![Supprimer des verrous](./media/migrate-best-practices-security-management/locks.png)
*Supprimer des verrous*

**En savoir plus :**

- [Découvrez comment](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) verrouiller les ressources pour empêcher les modifications inattendues.

## <a name="best-practice-understand-resource-access-permissions"></a>Bonne pratique : Comprendre les autorisations d’accès aux ressources

Un propriétaire d’abonnement a accès à tous les groupes de ressources et ressources de votre abonnement.

- Ajoutez des personnes avec parcimonie à cette affectation précieuse. Il est important de comprendre les ramifications de ces types d’autorisations pour assurer la sécurité et la stabilité de votre environnement.
- Assurez-vous de placer les ressources dans des groupes de ressources appropriés :
  - Associez les ressources ayant un cycle de vie similaire. Idéalement, vous ne devriez pas avoir besoin de déplacer une ressource lorsque vous devez supprimer un groupe de ressources complet.
  - Les ressources qui prennent en charge une fonction ou une charge de travail doivent être regroupées pour simplifier leur gestion.

**En savoir plus :**

- [Découvrez](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise) comment organiser les abonnements et les groupes de ressources.

## <a name="best-practice-tag-resources-effectively"></a>Bonne pratique : Baliser des ressources efficacement

Il est fréquent que l’utilisation d’un seul nom de groupe de ressources lié aux ressources ne permette de fournir suffisamment de métadonnées pour une mise en œuvre efficace de mécanismes, tels que la facturation interne ou la gestion au sein d’un abonnement.

- Dans le cadre des meilleures pratiques, vous devez utiliser les balises Azure pour ajouter des métadonnées utiles qui peuvent être interrogées et faire l’objet de rapports.
- Les balises permettent d’organiser logiquement les ressources avec les propriétés que vous définissez. Les balises peuvent être appliquées à des groupes de ressources ou des ressources directement.
- Les balises peuvent être appliquées à un groupe de ressources ou des ressources individuelles. Les balises figurant dans un groupe de ressources ne sont pas héritées par les ressources qui le composent.
- Vous pouvez automatiser le balisage à l’aide de PowerShell ou d’Azure Automation, ou baliser des groupes et ressources individuels. -Approche de balisage ou approche de libre-service. Si vous avez mis en place un système de gestion des changements et des requêtes, vous pouvez facilement utiliser les informations contenues dans la requête HTTP pour remplir les étiquettes de ressources spécifiques à votre entreprise.

![Balisage](./media/migrate-best-practices-security-management/tagging.png)
*Balisage*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) sur le balisage et les limitations des balises.
- [Révisez](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags#powershell) les exemples PowerShell et de l’interface de ligne de commande pour configurer le balisage et pour appliquer les balises d’un groupe de ressources à ses ressources.
- [Consultez](https://www.azurefieldnotes.com/2016/07/18/azure-resource-tagging-best-practices) les meilleures pratiques du balisage Azure.

## <a name="best-practice-implement-blueprints"></a>Bonne pratique : Implémenter des blueprints

À l’instar d’un plan, « blueprint » en anglais, qui permet aux ingénieurs et architectes de décrire les paramètres de conception d’un projet, Azure Blueprint permet aux architectes cloud et aux groupes de l’informatique centrale de définir un ensemble reproductible de ressources Azure qui implémentent et respectent les normes, modèles et exigences d’une organisation. En utilisant Azure Blueprints, les équipes de développement peuvent rapidement construire et créer de nouveaux environnements qui répondent aux exigences de conformité organisationnelle et qui ont un ensemble de composants intégrés, tels que la mise en réseau, visant à accélérer le développement et la livraison.

- Utilisez des blueprints pour orchestrer le déploiement des groupes de ressources, des modèles Azure Resource Manager et des affectations de rôles et de stratégies.
- Les blueprints sont stockés dans une base de données Azure Cosmos distribuée de façon globale. Les objets Blueprint sont répliqués dans plusieurs régions Azure. La réplication offre une faible latence, une haute disponibilité et un accès cohérent au blueprint, quelle que soit la région dans laquelle un blueprint déploie les ressources.

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/governance/blueprints/overview) sur les blueprints.
- [Révisez](https://azure.microsoft.com/blog/customizing-azure-blueprints-to-accelerate-ai-in-healthcare) un exemple de blueprint utilisé pour accélérer l’IA dans le secteur de la santé.

## <a name="best-practice-review-azure-reference-architectures"></a>Bonne pratique : Réviser les architectures de référence Azure

Construire des charges de travail sécurisées, évolutives et gérables dans Azure peut s’avérer décourageant. Avec les changements continus, il peut être difficile de suivre les différentes fonctionnalités pour un environnement optimal. Il peut être utile d’avoir une référence pour en tirer des leçons lors de la conception et de la migration de vos charges de travail. Azure et ses partenaires Azure ont construit plusieurs exemples d’architectures de référence pour différents types d’environnements. Ces exemples sont conçus pour vous fournir des idées dont vous pouvez tirer des leçons et sur lesquelles vous pouvez vous appuyer.

Les architectures de référence sont organisées par scénario. Elles contiennent les meilleures pratiques et des conseils sur la gestion, la disponibilité, l’évolutivité et la sécurité.
Azure App Service Environment fournit un environnement entièrement isolé et dédié dans lequel exécuter des applications Azure App Service, notamment des applications Web Windows et Linux, des conteneurs Docker, des Mobile Apps et des fonctions. App Service ajoute la puissance d’Azure à votre application grâce à la sécurité, l’équilibrage de charge, la mise à l’échelle automatique et la gestion automatisée. Vous pouvez également bénéficier de ses fonctionnalités DevOps, notamment le déploiement continu à partir d’Azure DevOps et GitHub, la gestion des packages, les environnements intermédiaires et les certificats SSL. App Service est utile pour les applications qui ont besoin d’une isolation et d’un accès réseau sécurisé, et pour celles qui utilisent de grandes quantités de mémoire et d’autres ressources qui ont besoin d’être mises à l’échelle.

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/architecture/reference-architectures) sur les architectures de référence Azure.
- [Révisez](https://docs.microsoft.com/azure/architecture/example-scenario) les exemples de scénarios Azure

## <a name="best-practice-manage-resources-with-azure-management-groups"></a>Bonne pratique : Gérer les ressources avec les groupes d’administration Azure

Si votre organisation dispose de plusieurs abonnements, vous avez besoin de gérer l’accès, les stratégies et la conformité de ceux-ci. Les groupes d’administration Azure fournissent un niveau d’étendue au-delà des abonnements.

- Vous organisez les abonnements en conteneurs appelés groupes d’administration et vous leur appliquez des conditions de gouvernance.
- Tous les abonnements d’un groupe d’administration héritent automatiquement des conditions du groupe d’administration.
- Les groupes d’administration fournissent une gestion de qualité professionnelle à grande échelle, quel que soit le type de vos abonnements.
- Par exemple, vous pouvez appliquer une stratégie de groupe de gestion qui limite les régions dans lesquelles les machines virtuelles peuvent être créées. Une telle stratégie s’applique alors à tous les groupes d’administration, abonnements et ressources sous ce groupe d’administration.
- Vous pouvez créer une structure flexible de groupes d’administration et d’abonnements pour organiser vos ressources dans une hiérarchie à des fins de stratégie unifiée et de gestion de l’accès.

Le diagramme suivant montre un exemple de création d’une hiérarchie pour la gouvernance à l’aide des groupes d’administration.

![Groupes d’administration](./media/migrate-best-practices-security-management/management-groups.png)
*Groupes d’administration*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/governance/management-groups/index) sur l’organisation de ressources en groupes d’administration.

## <a name="best-practice-deploy-azure-policy"></a>Bonne pratique : Déployer Azure Policy

Azure Policy est un service d’Azure que vous utilisez pour créer, affecter et gérer des stratégies.

- Les stratégies appliquent différentes règles et effets sur vos ressources, qui restent donc conformes aux normes et aux contrats de niveau de service de l’entreprise.
- Azure Policy évalue vos ressources en analysant celles qui ne sont pas conformes avec vos stratégies.
- Par exemple, vous pouvez créer une stratégie qui n’autorise qu’une taille de SKU spécifique pour les machines virtuelles dans votre environnement. Azure Policy évalue ce paramètre lors de la création et de la mise à jour des ressources, ainsi que lors de l’analyse des ressources existantes.
- Azure fournit des stratégies intégrées que vous pouvez assigner ou que vous pouvez créer vous-même.

![Azure Policy](./media/migrate-best-practices-security-management/policy.png)
*Azure Policy*

**En savoir plus :**

- [Consultez une vue d’ensemble](https://docs.microsoft.com/azure/governance/policy/overview) d’Azure Policy.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage) sur la création et la gestion des stratégies pour appliquer la conformité.

## <a name="best-practice-implement-a-bcdr-strategy"></a>Bonne pratique : Implémenter une stratégie BCDR

La planification de la continuité d’activité et reprise d’activité (BCDR) est un exercice essentiel que vous devez effectuer dans le cadre du processus de planification de la migration vers Azure. En termes juridiques, votre contrat peut comporter une clause de force majeure qui excuse les obligations dues à une force plus importante comme les ouragans ou les tremblements de terre. Cependant, vous devez faire en sorte que les services continuent de fonctionner et de se rétablir au besoin en cas d’urgence. Votre capacité à le faire peut faire ou défaire l’avenir de votre entreprise.

D’une manière générale, votre stratégie BCDR doit prendre en compte ce qui suit :

- **Sauvegarde de données :** Comment sécuriser vos données afin de pouvoir les récupérer facilement en cas de panne.
- **Récupération d’urgence :** Comment assurer la résilience et la disponibilité de vos applications.

### <a name="set-up-bcdr"></a>Configurer la continuité d’activité et reprise d’activité

Lorsque vous migrez vers Azure, il est important de comprendre que bien que la plate-forme Azure offre ces capacités de résilience intégrées, vous devez concevoir votre déploiement Azure pour tirer parti des fonctionnalités et des services Azure qui offrent une haute disponibilité, une récupération d’urgence et une sauvegarde.

- Votre solution BCDR dépendra des objectifs de votre entreprise et de votre stratégie de déploiement Azure. Les déploiements Infrastructure as a Service (IaaS) et Platform as a Service (PaaS) posent des problèmes différents à la continuité d’activité et reprise d’activité.
- Une fois en place, vos solutions BCDR doivent être testées régulièrement pour vérifier que votre stratégie reste viable.

### <a name="back-up-an-iaas-deployment"></a>Sauvegarder un déploiement IaaS

Dans la plupart des cas, une charge de travail locale est supprimée après la migration, et votre stratégie de sauvegarde des données sur site doit être étendue ou remplacée. Si vous migrez l’ensemble de votre centre de données vers Azure, vous devrez concevoir et implémenter une solution de sauvegarde complète utilisant les technologies Azure ou des solutions intégrées tierces.

Pour les charges de travail exécutées sur des machines virtuelles Azure IaaS, pensez à ces solutions de sauvegarde :

- **Sauvegarde Azure :** Fournit des sauvegardes cohérentes avec les applications pour les machines virtuelles Azure Linux et Windows.
- **Captures instantanées du stockage :** Prend des captures instantanées du stockage blob.

#### <a name="azure-backup"></a>Sauvegarde Azure

Sauvegarde Azure crée des points de récupération de données enregistrés dans le stockage Azure. Sauvegarde Azure peut sauvegarder les disques de machine virtuelle Azure Files (en préversion). Azure Files fournit des partages de fichiers dans le cloud, qui sont accessibles via SMB.

Vous pouvez utiliser Sauvegarde Azure pour sauvegarder les machines virtuelles de plusieurs façons.

- **Sauvegarde directe à partir des paramètres de machine virtuelle.** Vous pouvez sauvegarder des machines virtuelles avec Sauvegarde Azure directement depuis les options de machine virtuelle dans le portail Azure. Vous pouvez sauvegarder la machine virtuelle une fois par jour et restaurer le disque de machine virtuelle si nécessaire. Azure Backup prend des captures instantanées de données (VSS), aucun agent n’est installé sur la machine virtuelle.
- **Sauvegarde directe dans un coffre Recovery Services.** Vous pouvez sauvegarder vos machines virtuelles IaaS en déployant un coffre Azure Backup Recovery Services. Cela fournit un emplacement unique pour le suivi et la gestion des sauvegardes, ainsi que des options de sauvegarde et de restauration précises. La sauvegarde s’effectue jusqu’à trois fois par jour, au niveau des fichiers/dossiers. Elle n’est pas compatible avec les applications, et Linux n’est pas pris en charge. Installez l’agent Microsoft Azure Recovery Services (MARS) sur chaque machine virtuelle que vous souhaitez sauvegarder à l’aide de cette méthode.
- **Protéger la machine virtuelle dans Azure Backup Server.** Serveur de sauvegarde Azure est fourni gratuitement avec Sauvegarde Azure. La machine virtuelle est sauvegardée dans le serveur de sauvegarde Azure. Vous sauvegardez ensuite le serveur de sauvegarde Azure dans un coffre-fort sur Azure. La sauvegarde est compatible avec les applications, avec une granularité totale sur les sauvegardes fréquentes et la rétention. Vous pouvez sauvegarder au niveau de l’application, par exemple en sauvegardant SQL Server ou SharePoint.

Pour des raisons de sécurité, Azure Backup chiffre les données en transit à l’aide d’AES 256 et les envoie à Azure via HTTPS. Les données sauvegardées au repos dans Azure sont chiffrées en utilisant [Storage Service Encryption (SSE)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption?toc=/azure/storage/queues/toc.json), et les données pour la transmission et le stockage.

![Sauvegarde Azure](./media/migrate-best-practices-security-management/iaas-backup.png)
*Sauvegarde Azure*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup) sur les différents types de sauvegardes.
- [Planifiez une infrastructure de sauvegarde](https://docs.microsoft.com/azure/backup/backup-azure-vms-introduction) pour les machines virtuelles Azure.

#### <a name="storage-snapshots"></a>Captures instantanées du stockage

Les machines virtuelles Azure sont stockés en tant qu’objets blob de pages dans Stockage Azure.

- Les instantanés capturent l’état de l’objet blob à un instant précis.
- Comme méthode de sauvegarde alternative pour les disques Azure VM, vous pouvez effectuer une capture instantanée des blobs de stockage et les copier sur un autre compte de stockage.
- Vous pouvez copier un blob entier ou utiliser une copie de capture instantanée incrémentielle pour ne copier que les modifications delta et réduire l’espace de stockage.
- Par mesure de précaution supplémentaire, vous pouvez activer la suppression en douceur des comptes de stockage blob. Lorsque cette fonction est activée, un blob supprimé est marqué pour suppression mais n’est pas immédiatement purgé. Pendant la période temporaire, le blob peut être restauré.

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) sur le Stockage Blob Azure.
- [Apprenez-en](https://docs.microsoft.com/azure/storage/blobs/storage-blob-snapshots) davantage sur la création d’un instantané d’objet blob.
- [Passez en revue un exemple de scénario](https://azure.microsoft.com/blog/microsoft-azure-block-blob-storage-backup) pour la sauvegarde de stockage d’objets blob.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete) sur la suppression réversible.
- [Reprise d’activité après sinistre et basculement forcé (préversion) dans Stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-disaster-recovery-guidance?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)

#### <a name="third-party-backup"></a>Sauvegarde tierce

De plus, vous pouvez utiliser des solutions tierces pour sauvegarder les machines virtuelles et les conteneurs de stockage Azure vers le stockage local ou d’autres fournisseurs de cloud. [Apprenez-en davantage](https://azuremarketplace.microsoft.com/marketplace/apps?search=backup&page=1) sur les solutions de sauvegarde dans Azure Marketplace.

### <a name="set-up-disaster-recovery-for-iaas-apps"></a>Configurer la récupération après sinistre pour les applications IaaS

En plus de protéger les données, la planification de la continuité d’activité et reprise d’activité doit déterminer le moyen d’assurer la disponibilité des applications et des charges de travail en cas d’incident. Pour les charges de travail exécutées sur des machines virtuelles Azure IaaS et le stockage Azure, pensez à ces solutions :

#### <a name="azure-site-recovery"></a>Azure Site Recovery

Azure Site Recovery est le principal service Azure assurant que les machines virtuelles Azure peuvent être mises en ligne et que les applications de celles-ci sont disponibles en cas de panne.

Site Recovery réplique des machines virtuelles d’une région primaire à une région secondaire Azure. En cas de sinistre, vous basculerez vers les machines virtuelles de la région primaire et continuez à y accéder normalement dans la région secondaire. Lorsque les opérations reviennent à la normale, vous pouvez faire basculer les machines virtuelles vers la région primaire.

![Azure Site Recovery](./media/migrate-best-practices-security-management/site-recovery.png)
*Site Recovery*

**En savoir plus :**

- [Révisez](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-disaster-recovery-guidance) les scénarios de récupération d’urgence des machines virtuelles Azure.
- [Découvrez comment](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-replicate-after-migration) configurer la récupération d’urgence pour une machine virtuelle Azure après la migration.

## <a name="best-practice-use-managed-disks-and-availability-sets"></a>Bonne pratique : Utiliser des disques managés et des groupes à haute disponibilité

Azure utilise des groupes à haute disponibilité pour regrouper logiquement les machines virtuelles et pour isoler les machines virtuelles d’un groupe d’autres ressources. Les machines virtuelles d’un groupe à haute disponibilité sont réparties sur plusieurs domaines d’erreur avec des sous-systèmes distincts, ce qui assure une protection contre les pannes locales. Les machines virtuelles sont aussi réparties sur plusieurs domaines de mise à jour, ce qui évite un redémarrage simultané de toutes les machines virtuelles du groupe.

Les disques managés Azure simplifient la gestion des disques pour les machines virtuelles Azure en gérant les comptes de stockage associés aux disques de machines virtuelles.

- Utilisez des disques managés dans la mesure du possible. Vous avez simplement à spécifier le type de stockage à utiliser et la taille de disque dont vous avez besoin, et Azure crée et gère le disque à votre place.
- Vous pouvez convertir des disques existants en disques managés.
- Vous devez créer des machines virtuelles dans des groupes à haute disponibilité pour la résilience et la haute disponibilité. Quand des arrêts planifiés ou imprévus surviennent, les groupes à haute disponibilité garantissent qu’au moins une de vos machines virtuelles du groupe reste disponible.

![Disques managés](./media/migrate-best-practices-security-management/managed-disks.png)
*Disques managés*

**En savoir plus :**

- [Consultez une vue d’ensemble](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) sur les disques managés.
- [Découvrez comment](https://docs.microsoft.com/azure/virtual-machines/windows/convert-unmanaged-to-managed-disks) convertir des disques en disques managés.
- [Découvrez comment](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability) gérer la disponibilité des machines virtuelles Windows dans Azure.

## <a name="best-practice-monitor-resource-usage-and-performance"></a>Bonne pratique : Superviser l’utilisation des ressources et les performances

Vous avez peut-être déplacé vos charges de travail vers Azure pour ses immenses capacités de mise à l’échelle. Cependant, le déplacement de votre charge de travail ne signifie pas qu’Azure implémentera automatiquement la mise à l’échelle. Par exemple :

- Si votre organisation de marketing envoie une nouvelle publicité télévisée qui génère 300 % plus de trafic, cela pourrait causer des problèmes de disponibilité du site. Votre charge de travail nouvellement migrée pourrait atteindre les limites attribuées et tomber en panne.
- Un autre exemple pourrait être une attaque de déni de service distribué (DDoS) sur votre charge de travail migrée. Dans ce cas, il se peut que vous ne souhaitiez pas effectuer de mise à l’échelle, mais plutôt empêcher la source des attaques d’atteindre vos ressources.

Ces deux cas ont des résolutions différentes, mais, pour chacun d’eux, vous devez avoir une idée de ce qui se passe avec l’utilisation et la surveillance des performances.

- Azure Monitor peut aider à faire émerger ces métriques, et fournir une réponse avec des alertes, une mise à l’échelle automatique, des hubs d’événements, des applications logiques et plus encore.
- En plus de la supervision Azure, vous pouvez intégrer votre application SIEM tierce partie afin de superviser les journaux d’activité Azure pour les événements d’audit et de performance.

![Azure Monitor](./media/migrate-best-practices-security-management/monitor.png)
*Azure Monitor*

**En savoir plus :**

- [Découvrez](https://docs.microsoft.com/azure/azure-monitor/overview) Azure Monitor.
- [Adoptez les meilleures pratiques](https://docs.microsoft.com/azure/architecture/best-practices/monitoring) pour l’analyse et les diagnostics.
- [Découvrez](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling) la mise à l’échelle automatique.
- [Découvrez comment](https://docs.microsoft.com/azure/security-center/security-center-export-data-to-siem) router les données Azure vers un outil SIEM.

## <a name="best-practice-enable-diagnostic-logging"></a>Bonne pratique : Activer la journalisation des diagnostics

Les ressources Azure génèrent un bon nombre de métriques de journalisation et de données de télémétrie.

- Par défaut, la journalisation des diagnostics n’est pas activée pour la plupart des types de ressources.
- En activant la journalisation des diagnostics sur l’ensemble de vos ressources, vous pouvez interroger les données de journalisation et créer des alertes et des playbooks basés sur celles-ci.
- Lorsque vous activez l’enregistrement de diagnostic, chaque ressource possède un ensemble spécifique de catégories. Vous sélectionnez une ou plusieurs catégories de journalisation et un emplacement pour les données de journalisation. Les journaux d’activité peuvent être envoyés à un compte de stockage, à un Event Hub ou à Azure Monitor.

![Journalisation des diagnostics](./media/migrate-best-practices-security-management/diagnostics.png)
*Journalisation des diagnostics*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs) sur la collecte et l’utilisation des données de journal.
- [Découvrez les opérations prises en charge](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-diagnostic-logs-schema) pour la journalisation des diagnostics.

## <a name="best-practice-set-up-alerts-and-playbooks"></a>Bonne pratique : Configurer les alertes et les playbooks

Alors que la journalisation des diagnostics est activée pour les ressources Azure, vous pouvez commencer à utiliser les données de journalisation pour créer des alertes personnalisées.

- Les alertes vous avertissent de façon proactive lorsque des conditions sont détectées dans vos données de surveillance. Vous pouvez alors résoudre les problèmes avant que les utilisateurs du système ne s’en aperçoivent. Vous pouvez définir des alertes sur des éléments, tels que les valeurs de métriques, les requêtes de recherche dans les journaux, les événements du journal d’activité, l’état d’intégrité de la plateforme et la disponibilité du site Web.
- Lorsque des alertes sont déclenchées, vous pouvez exécuter un Playbook d’application logique. Un playbook vous aide à automatiser et orchestrer une réponse à une alerte spécifique. Les playbooks sont basés sur Azure Logic Apps. Vous pouvez utiliser les modèles d’application logique pour créer des playbooks ou créer les vôtres.
- Par exemple, vous pouvez créer une alerte qui se déclenche lorsqu’une analyse de port se produit dans un groupe de sécurité réseau. Vous pouvez configurer un playbook qui exécute et verrouille l’adresse IP de l’origine de l’analyse.
- Un autre exemple pourrait être une application avec une fuite de mémoire. Lorsque l’utilisation de la mémoire atteint un certain point, un playbook peut recycler le processus.

![Alertes](./media/migrate-best-practices-security-management/alerts.png)
*Alertes*

**En savoir plus :**

- [Découvrez-en plus sur](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-alerts) les alertes.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/security-center/security-center-playbooks) sur les playbooks de sécurité qui répondent aux alertes Security Center.

## <a name="best-practice-use-the-azure-dashboard"></a>Bonne pratique : Utiliser le tableau de bord Azure

Le portail Azure est une seule console unifiée qui permet de créer, gérer et surveiller tout, de simples applications web à des applications de cloud complexes. Il comprend un tableau de bord personnalisable et des options d’accessibilité.

- Vous pouvez créer plusieurs tableaux de bord et les partager avec d’autres personnes ayant accès à vos abonnements Azure.
- Avec ce modèle partagé, votre équipe dispose d’une visibilité sur l’environnement Azure, ce qui lui permet d’être proactive dans la gestion des systèmes dans le cloud.

![Tableau de bord Azure](./media/migrate-best-practices-security-management/dashboard.png)
*Tableau de bord Azure*

**En savoir plus :**

- [Découvrez comment](https://docs.microsoft.com/azure/azure-portal/azure-portal-dashboards) créer un tableau de bord.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/azure-portal/azure-portal-dashboards-structure) sur la structure de tableau de bord.

## <a name="best-practice-understand-support-plans"></a>Bonne pratique : Comprendre les plans de support

À un moment donné, vous devrez collaborer avec votre personnel de soutien ou le personnel du support technique Microsoft. Il est essentiel de disposer d’un ensemble de stratégies et de procédures de support lors de scénarios, tels que la récupération d’urgence. De plus, vos administrateurs et votre personnel de support doivent être formés à l’implémentation de ces stratégies.

- Dans le cas peu probable où un problème de service Azure aurait un impact sur votre charge de travail, les administrateurs devraient savoir comment soumettre un ticket de support à Microsoft de la manière la plus appropriée et efficace.
- Familiarisez-vous avec les différents plans de support offerts pour Azure. Cela va des temps de réponse dédiés aux instances Développeur, au support Premier avec un temps de réponse inférieur à 15 minutes.

![Plans de support](./media/migrate-best-practices-security-management/support.png)
*Plans de support*

**En savoir plus :**

- [Consultez une vue d’ensemble](https://azure.microsoft.com/support/options) des plans de support Azure.
- [Apprenez-en davantage](https://azure.microsoft.com/support/legal/sla) sur les contrats de niveau de service (SLA).

## <a name="best-practice-manage-updates"></a>Bonne pratique : Gérer les mises à jour

Le maintien à jour des machines virtuelles Azure avec les dernières mises à jour du système d’exploitation et du logiciel est une tâche énorme. La capacité de faire émerger toutes les machines virtuelles, de déterminer les mises à jour dont elles ont besoin et d’envoyer (push) automatiquement ces mises à jour est extrêmement utile.

- Vous pouvez utiliser Update Management dans Azure Automation pour gérer les mises à jour du système d’exploitation de vos machines Windows et Linux déployées dans Azure, localement ou dans d’autres fournisseurs cloud.
- Utilisez Update Management pour évaluer rapidement l’état des mises à jour disponibles sur tous les ordinateurs d’agent et gérer l’installation des mises à jour.
- Vous pouvez activer Update Management pour les machines virtuelles directement depuis un compte Azure Automation. Vous pouvez également mettre à jour une même machine virtuelle depuis la page Machine virtuelle du portail Azure.
- De plus, les machines virtuelles Azure peuvent être inscrites avec System Center Configuration Manager. Vous pouvez ensuite migrer la charge de travail Configuration Manager vers Azure et effectuer des rapports et des mises à jour logicielles à partir d’une même interface web.

![Mises à jour de la machine virtuelle](./media/migrate-best-practices-security-management/updates.png)
*Mises à jour*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/automation/automation-update-management) sur la gestion des mises à jour dans Azure.
- [Découvrez comment](https://docs.microsoft.com/azure/automation/oms-solution-updatemgmt-sccmintegration) intégrer System Center Configuration Manager à Update Management.
- [Forum Aux Questions](https://docs.microsoft.com/sccm/core/understand/configuration-manager-on-azure) (FAQ) relatif à Configuration Manager dans Azure.

## <a name="implement-a-change-management-process"></a>Implémenter un processus de gestion des changements

Comme pour tout système de production, tout type de changement peut avoir un impact sur votre environnement. Un processus de gestion des changements qui exige que des requêtes soient soumises afin d’apporter des changements aux systèmes de production est un ajout précieux dans votre environnement migré.

- Vous pouvez établir des cadres de meilleures pratiques pour la gestion des changements afin de sensibiliser les administrateurs et le personnel de support.
- Vous pouvez utiliser Azure Automation pour vous aider dans la gestion de la configuration et le suivi des changements dans le cadre de vos flux de travail migrés.
- Lors de la mise en application du processus de gestion des changements, vous pouvez utiliser les journaux d’audit pour lier les journaux d’activité des modifications Azure aux demandes de modification existantes (ou non). Ainsi, si vous voyez une modification apportée sans demande de modification correspondante, vous pouvez rechercher la cause du problème dans le processus.

Azure possède une solution Suivi des modifications dans Azure Automation :

- La solution suit les modifications apportées aux logiciels et fichiers Windows et Linux, aux clés de Registre Windows, aux services Windows et aux démons Linux.
- Les modifications apportées sur les serveurs supervisés sont envoyées au service Azure Monitor dans le cloud pour traitement.
- La logique est appliquée aux données reçues et le service cloud enregistre les données.
- Dans le tableau de bord de suivi des modifications, vous pouvez facilement voir les modifications apportées à votre infrastructure de serveur.

![Gestion des changements](./media/migrate-best-practices-security-management/change.png)
*Gestion des changements*

**En savoir plus :**

- [Apprenez-en davantage](https://docs.microsoft.com/azure/automation/automation-change-tracking) sur le Suivi des modifications.
- [Apprenez-en davantage](https://docs.microsoft.com/azure/automation/automation-intro) sur les fonctionnalités d’Azure Automation.

## <a name="next-steps"></a>Étapes suivantes

Passez en revue d’autres meilleures pratiques :

- [Meilleures pratiques](./migrate-best-practices-networking.md) relatives au réseau après la migration.
- [Meilleures pratiques](./migrate-best-practices-costs.md) relatives à la gestion des coûts après la migration.
