---
title: Amélioration de la discipline Accélération du déploiement
description: Découvrez les tâches qu’une entreprise peut effectuer pour développer et faire évoluer sa discipline d’accélération du déploiement dans chaque phase d’adoption du cloud.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 835614ca30fc4fc5ca3e617e920f46aa4039cd8b
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83220360"
---
# <a name="deployment-acceleration-discipline-improvement"></a>Amélioration de la discipline Accélération du déploiement

La discipline Accélération du déploiement se concentre sur l’élaboration de stratégies qui garantissent que les ressources sont déployées et configurées de façon cohérente et répétée, et qu’elles restent conformes tout au long de leur cycle de vie. Au sein des cinq disciplines de la gouvernance cloud, la discipline Accélération du déploiement inclut des décisions en matière d’automatisation du déploiement, de contrôle du code source des artefacts du déploiement, de surveillance des ressources déployées pour maintenir l’état désiré et d’audit des problèmes de conformité.

Cet article décrit certaines tâches potentielles que votre entreprise peut entreprendre pour mieux développer et faire mûrir la discipline Accélération du déploiement. Ces tâches peuvent être décomposées en phases de planification, de construction, d’adoption et d’exploitation de l’implémentation d’une solution cloud, qui sont ensuite répétées pour permettre le développement d’une [approche incrémentielle de la gouvernance cloud](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatre phases d’adoption](../../_images/govern/adoption-phases.png)

_Figure 1 : Phases d’adoption de l’approche incrémentielle de la gouvernance cloud._

Il est impossible pour un même document de prendre en compte les exigences de toutes les organisations. Par conséquent, cet article présente des exemples d’activités minimales et potentielles suggérés pour chaque phase du processus de maturation de la gouvernance. L’objectif initial de ces activités est de vous aider à générer un [produit minimum viable (MVP) de stratégie](../guides/index.md#an-incremental-approach-to-cloud-governance) et à établir un framework pour une amélioration incrémentielle de la stratégie. Votre équipe de gouvernance cloud devra décider combien investir dans ces activités pour améliorer vos fonctionnalités de discipline de ligne de base des identités.

> [!CAUTION]
> Les activités minimales ou potentielles décrites dans cet article ne correspondent pas spécialement à des stratégies d’entreprise spécifiques ou à des exigences de conformité de tiers. Ces conseils visent à favoriser les échanges qui conduiront à un alignement des deux exigences avec un modèle de gouvernance cloud.

## <a name="planning-and-readiness"></a>Planification et préparation

Cette phase de maturité de la gouvernance comble le fossé entre les résultats opérationnels et les stratégies concrètes. Au cours de ce processus, l’équipe de direction définit des métriques spécifiques, les mappe au patrimoine numérique, et commence à planifier l’effort global de migration.

**Activités minimales suggérées :**

- Évaluez vos options de [chaîne d’outils d’accélération du déploiement](./toolchain.md) et implémentez une stratégie hybride appropriée pour votre organisation.
- Élaborer un brouillon de recommandations relatives à l’architecture et distribuer ce document aux principales parties prenantes.
- Formez et impliquez les personnes et les équipes concernées par le développement des instructions relatives à l'architecture.
- Formez le personnel informatique et les équipes de développement pour qu’elles comprennent les stratégies et les principes DevSecOps, ainsi que l’importance des déploiements intégralement automatisés dans la discipline Accélération du déploiement.

**Activités potentielles :**

- Définissez les rôles et attributions qui régiront la discipline Accélération du déploiement dans le cloud.

## <a name="build-and-predeployment"></a>Génération et prédéploiement

**Activités minimales suggérées :**

- Pour les nouvelles applications cloud, introduisez au tout début du processus de développement des déploiements intégralement automatisés. Cet investissement permettra d’améliorer la fiabilité de vos processus de tests, tout en garantissant la cohérence dans l’ensemble de vos environnements de production, QA et de développement.
- Stockez tous les artefacts du déploiement (modèles de déploiement ou scripts de configuration) à l’aide d’une plateforme de contrôle de code source telles que GitHub ou Azure DevOps.
- Stockez tous les secrets, mots de passe, certificats et chaînes de connexion dans [Azure Key Vault](https://docs.microsoft.com/azure/key-vault).
- Envisagez de procéder à un test pilote avant d’implémenter votre [chaîne d’outils d’accélération du déploiement](./toolchain.md), pour vous assurer que vos déploiements sont bien rationalisés. Tenez compte des commentaires reçus lors des tests pilotes pendant la phase de prédéploiement et répétez si nécessaire.
- Évaluez l’architecture logique et physique de vos applications, et identifiez les opportunités d’automatisation du déploiement des ressources d’application ou d’améliorations de parties de l’architecture avec d’autres ressources cloud.
- Mettez à jour le document d’instructions relatives à l’architecture pour inclure des plans de déploiement et d’adoption par les utilisateurs, puis distribuez-le aux principales parties prenantes.
- Continuez de former les personnes et les équipes les plus concernées par les instructions relatives à l’architecture.

**Activités potentielles :**

- Définissez un pipeline de déploiement continu et d’intégration continue pour gérer en intégralité les versions des mises à jour de vos applications via vos environnements de production, QA et de développement.

## <a name="adopt-and-migrate"></a>Adoption et migration

La migration est un processus incrémentiel qui porte essentiellement sur le déplacement, le test et l’adoption d’applications ou de charges de travail dans un patrimoine numérique.

**Activités minimales suggérées :**

- Migrez votre [chaîne d’outils d’accélération du déploiement](./toolchain.md) du développement vers la production.
- Mettre à jour les recommandations relatives à l’architecture et distribuer le document aux principales parties prenantes.
- Développez une documentation et des ressources pédagogiques, des communications de sensibilisation, des incitations et d’autres programmes afin d’encourager l’adoption par les équipes informatiques et de développement.

**Activités potentielles :**

- Vérifiez que les bonnes pratiques définies pendant les phases de génération/prédéploiement sont correctement mises en œuvre.
- Assurez-vous que chaque application ou charge de travail est alignée avec la stratégie d’accélération du déploiement avant la mise en production.

## <a name="operate-and-post-implementation"></a>Exploitation et post-implémentation

Une fois la transformation terminée, la gouvernance et les opérations doivent perdurer tout au long du cycle de vie naturel d’une application ou d’une charge de travail. Cette phase de maturité de la gouvernance est centrée sur les activités qui interviennent généralement après l’implémentation de la solution et le début de stabilisation du cycle de transformation.

**Activités minimales suggérées :**

- Personnalisez votre [chaîne d’outils d’accélération du déploiement](./toolchain.md) en fonction de l’évolution des besoins de votre organisation.
- Automatisez les notifications et les rapports pour vous avertir des problèmes de configuration ou menaces potentiels.
- Analysez et créez des rapports sur l’utilisation des ressources et des applications.
- Générez des rapports sur les métriques post-déploiement et distribuez-les aux parties prenantes.
- Révisez les instructions relatives à l’architecture pour guider les futurs processus d’adoption.
- Continuez à communiquer avec les équipes et personnes concernées et formez-les régulièrement pour vous assurer de leur adhésion continue aux instructions relatives à l’architecture.

**Activités potentielles :**

- Configurez un outil de création de rapports et de surveillance de la configuration de l’état souhaité.
- Passez régulièrement en revue des outils et scripts de configuration pour améliorer les processus et identifier les problèmes courants.
- Travailler avec les équipes responsables du développement, des opérations et de la sécurité pour faire mûrir les pratiques DevSecOps et supprimer les silos organisationnels à l’origine du manque d’efficacité.

## <a name="next-steps"></a>Étapes suivantes

À présent que vous avez compris le concept de gouvernance des identités cloud, examinez la [chaîne d’outils de base de référence des identités](./toolchain.md) pour identifier les outils et fonctionnalités Azure dont vous aurez besoin lors du développement de votre discipline Base de référence des identités sur la plateforme Azure.

> [!div class="nextstepaction"]
> [Chaîne d’outils de base de référence des identités pour Azure](./toolchain.md)
