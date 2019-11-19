---
title: Déployer une zone d’accueil de migration dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment déployer une zone d’accueil de migration dans Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit
ms.openlocfilehash: b3adddc6b68d07084ec8c3909d6c8010c25bb387
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73239852"
---
# <a name="deploy-a-migration-landing-zone"></a>Déployer une zone d’accueil de migration

*Zone d’accueil de migration* est un terme utilisé pour décrire un environnement qui a été approvisionné et préparé pour héberger des charges de travail qui sont migrées vers Azure à partir d’un environnement local. Une zone d’accueil de migration est le dernier livrable du guide de configuration Azure. Cet article regroupe tous les sujets relatifs à la préparation abordés dans ce guide et applique les décisions prises au déploiement de votre première zone d’accueil de migration.

Les sections suivantes décrivent une zone d’accueil couramment utilisée pour établir un environnement dont l’utilisation convient lors d’une migration. L’environnement ou la zone d’accueil décrits dans cet article est également capturé dans un blueprint Azure. Vous pouvez utiliser le blueprint de zone d’accueil de migration du Framework d’adoption du cloud pour déployer l’environnement défini en un seul clic.

## <a name="purpose-of-the-blueprint"></a>Objectif du blueprint

Le blueprint de zone d’accueil de migration du Framework d’adoption du cloud crée une zone d’accueil. Cette zone d’accueil est intentionnellement limitée. Elle est conçue pour créer un point de départ cohérent qui permet d’apprendre l’infrastructure sous forme de code. Pour certains efforts de migration, cette zone d’accueil peut être suffisante pour répondre à vos besoins. Il est également probable que vous devrez modifier le blueprint pour qu’il réponde à vos contraintes uniques.

## <a name="blueprint-alignment"></a>Alignement du blueprint

L’image suivante montre le blueprint de zone d’accueil de migration du Framework d’adoption du cloud quant à la complexité architecturale et aux exigences de conformité.

![Alignement du blueprint](../../_images/ready/blueprint-overview.png)

- La lettre A se trouve à l’intérieur d’une ligne courbe qui marque l’étendue de ce blueprint. Cette étendue vise à indiquer que ce blueprint couvre une complexité architecturale limitée, mais repose sur des exigences de conformité relativement moyennes.
- Les clients qui ont un degré élevé de complexité et des exigences strictes en matière de conformité sont susceptibles d’être mieux servis en recourant au blueprint étendu d’un partenaire ou à l’un des [exemples de blueprints basés sur des normes](https://docs.microsoft.com/azure/governance/blueprints/samples).
- La plupart des besoins des clients se situent entre ces deux extrêmes. La lettre B représente le processus décrit dans les articles portant sur les [considérations relatives à la zone d’accueil](../considerations/index.md). Pour les clients dans cet espace, vous pouvez utiliser les guides de décision qui se trouvent dans ces articles pour identifier les nœuds à ajouter au blueprint de zone d’accueil de migration du Framework d’adoption du cloud. Cette approche vous permet de personnaliser le blueprint en fonction de vos besoins.

## <a name="use-this-blueprint"></a>Utilisation du blueprint

Avant d’utiliser le blueprint de zone d’accueil de migration du Framework d’adoption du cloud, passez en revue les hypothèses, décisions et recommandations d’implémentation suivantes.

## <a name="assumptions"></a>Hypothèses

Les hypothèses ou contraintes suivantes ont été utilisées lors de la définition de cette zone d’accueil initiale. Si ces hypothèses s’alignent sur vos contraintes, vous pouvez utiliser le blueprint pour créer votre première zone d’accueil. Le blueprint peut également être étendu pour créer un blueprint de zone d’accueil qui réponde à vos contraintes uniques.

- **Limites d’abonnement :** Cet effort d’adoption ne doit pas dépasser les [limites d’abonnement](https://docs.microsoft.com/azure/azure-subscription-service-limits). Deux indicateurs courants sont un excès de 25 000 machines virtuelles ou 10 000 processeurs virtuels.
- **Conformité :** Aucune exigence de tiers en matière de conformité n’est nécessaire dans cette zone d’accueil.
- **Complexité architecturale :** La complexité architecturale ne nécessite pas d’abonnements de production supplémentaires.
- **Services partagés :** Aucun des services partagés existants dans Azure ne nécessite que cet abonnement soit traité comme un spoke dans une architecture hub and spoke.

Si ces hypothèses semblent alignées sur votre environnement actuel, ce blueprint peut être un bon point de départ pour commencer à créer votre zone d’accueil.

## <a name="decisions"></a>Décisions

Les décisions suivantes sont représentées dans le blueprint de zone d’accueil.

| Composant | Décisions | Autres approches |
|---------|---------|---------|
|Outils de migration|Azure Site Recovery sera déployé et un projet Azure Migrate sera créé.|[Guide de décision sur les outils de migration](../../decision-guides/migrate-decision-guide/index.md)|
|Enregistrement et surveillance|L’espace de travail Operational Insights et le compte de stockage des diagnostics seront approvisionnés.|         |
|Réseau|Un réseau virtuel sera créé avec des sous-réseaux pour la passerelle, le pare-feu, le jumpbox et la zone d’accueil.|[Décisions en matière de mise en réseau](../considerations/networking-options.md)|
|Identité|Il est supposé que l’abonnement est déjà associé à une instance de Azure Active Directory.|[Meilleures pratiques de gestion des identités](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)         |
|Stratégie|Ce blueprint suppose actuellement qu’aucune stratégie Azure ne doit être appliquée.|         |
|Conception de l’abonnement|N/A : conçu pour un abonnement de production unique.|[Abonnements de mise à l’échelle](../azure-best-practices/scaling-subscriptions.md)|
|Groupes d’administration|N/A : conçu pour un abonnement de production unique.|[Abonnements de mise à l’échelle](../azure-best-practices/scaling-subscriptions.md)         |
|Groupes de ressources|N/A : conçu pour un abonnement de production unique.|[Abonnements de mise à l’échelle](../azure-best-practices/scaling-subscriptions.md)         |
|Données|N/A|[Choix de la bonne option SQL Server dans Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/architecture/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) et [instructions relatives aux magasins de données Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview) |
|Stockage|N/A|[Conseils relatifs à Stockage Azure](../considerations/storage-options.md)         |
|Standards de nommage et de catégorisation|N/A|[Meilleures pratiques en matière de nommage et de catégorisation](../azure-best-practices/naming-and-tagging.md)         |
|la gestion des coûts ;|N/A|[Coûts de suivi](../azure-best-practices/track-costs.md)|
|Calcul|N/A|[Options de calcul](../considerations/compute-options.md)|

## <a name="customize-or-deploy-a-landing-zone-from-this-blueprint"></a>Personnaliser ou déployer une zone d’accueil à partir de ce blueprint

Découvrez plus d’informations et téléchargez un exemple de référence du blueprint de zone d’accueil de migration du Framework d’adoption du cloud pour le déployer ou le personnaliser à partir des [exemples de blueprints Azure](https://docs.microsoft.com/azure/governance/blueprints/samples).

Les exemples de blueprints sont également disponibles dans le portail. Pour des détails sur la création d’un blueprint, consultez [Azure Blueprints](./govern-org-compliance.md?tabs=azureblueprints#create-a-blueprint).

Pour obtenir des conseils sur les modifications qui doivent être apportées à ce blueprint ou à la zone d’accueil qui en résulte, consultez les articles portant sur les [considérations relatives à la zone d’accueil](../considerations/index.md).

## <a name="next-steps"></a>Étapes suivantes

Après le déploiement d’une zone d’accueil de migration, vous êtes prêt à migrer des charges de travail vers Azure.
Pour obtenir des conseils sur les outils et les processus nécessaires à la migration de votre première charge de travail, consultez le [guide de migration Azure](../../migrate/azure-migration-guide/index.md).

> [!div class="nextstepaction"]
> [Migrer votre première charge de travail à l’aide du guide de migration Azure](../../migrate/azure-migration-guide/index.md)
