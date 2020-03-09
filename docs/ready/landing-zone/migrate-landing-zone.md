---
title: Déployer une zone d’accueil de migration dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Découvrez comment déployer une zone d’accueil de migration dans Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 2c9b932bd1a9500b7308fa24be65a12e46221a99
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78228588"
---
<!-- cSpell:ignore vCPUs jumpbox -->

# <a name="deploy-a-migration-landing-zone"></a>Déployer une zone d’accueil de migration

*Zone d’accueil de migration* est un terme utilisé pour décrire un environnement qui a été approvisionné et préparé pour héberger des charges de travail qui sont migrées vers Azure à partir d’un environnement local.

## <a name="deploy-the-first-landing-zone"></a>Déployer votre première zone d’atterrissage

Avant d’utiliser le blueprint de zone d’atterrissage de migration Cloud Adoption Framework, passez en revue les hypothèses, décisions et recommandations d’implémentation suivantes. Si ces informations s’alignent sur le plan d’adoption cloud souhaité, le [blueprint de zone d’atterrissage de migration](https://docs.microsoft.com/azure/governance/blueprints/samples/caf-migrate-landing-zone/index) peut être déployé à l’aide des [étapes de déploiement][deploy-sample].

> [!div class="nextstepaction"]
> [Déployer l’exemple de blueprint][deploy-sample]

## <a name="assumptions"></a>Hypothèses

La zone d’atterrissage initiale est associée aux hypothèses ou contraintes suivantes. Si ces hypothèses s’alignent sur vos contraintes, vous pouvez utiliser le blueprint pour créer votre première zone d’accueil. Le blueprint peut également être étendu pour créer un blueprint de zone d’accueil qui réponde à vos contraintes uniques.

- **Limites d’abonnement :** Cet effort d’adoption ne doit pas dépasser les [limites d’abonnement](https://docs.microsoft.com/azure/azure-subscription-service-limits). Deux indicateurs courants sont un excès de 25 000 machines virtuelles ou 10 000 processeurs virtuels.
- **Conformité :** Aucune exigence de tiers en matière de conformité n’est nécessaire dans cette zone d’accueil.
- **Complexité architecturale :** La complexité architecturale ne nécessite pas d’abonnements de production supplémentaires.
- **Services partagés :** Aucun des services partagés existants dans Azure ne nécessite que cet abonnement soit traité comme un spoke dans une architecture hub and spoke.
- **Étendue de production limitée :** Cette zone d’atterrissage peut potentiellement héberger des charges de travail de production. Toutefois, il ne s’agit pas d’un environnement adapté pour les données sensibles ou les charges de travail stratégiques.

Si ces hypothèses s’alignent sur vos besoins d’adoption actuels, ce blueprint peut être un bon point de départ pour la création de votre zone d’atterrissage.

## <a name="decisions"></a>Décisions

Les décisions suivantes sont représentées dans le blueprint de zone d’accueil.

| Composant                    | Décisions                                                                                         | Autres approches                                                                                                                                                                                                                                                               |
|------------------------------|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Outils de migration              | Azure Site Recovery sera déployé et un projet Azure Migrate sera créé.                | [Guide de décision sur les outils de migration](../../decision-guides/migrate-decision-guide/index.md)                                                                                                                                                                                              |
| Enregistrement et surveillance       | L’espace de travail Operational Insights et le compte de stockage des diagnostics seront approvisionnés.                |                                                                                                                                                                                                                                                                                      |
| Réseau                      | Un réseau virtuel sera créé avec des sous-réseaux pour la passerelle, le pare-feu, le jumpbox et la zone d’accueil.  | [Décisions en matière de mise en réseau](../considerations/networking-options.md)                                                                                                                                                                                                                      |
| Identité                     | Il est supposé que l’abonnement est déjà associé à une instance de Azure Active Directory. | [Meilleures pratiques de gestion des identités](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json) |
| Stratégie                       | Ce blueprint suppose actuellement qu’aucune stratégie Azure ne doit être appliquée.                        |                                                                                                                                                                                                                                                                                      |
| Conception de l’abonnement          | N/A : conçu pour un abonnement de production unique.                                              | [Abonnements de mise à l’échelle](../azure-best-practices/scaling-subscriptions.md)                                                                                                                                                                                                            |
| Groupes d’administration            | N/A : conçu pour un abonnement de production unique.                                              | [Abonnements de mise à l’échelle](../azure-best-practices/scaling-subscriptions.md)                                                                                                                                                                                                            |
| Groupes de ressources              | N/A : conçu pour un abonnement de production unique.                                              | [Abonnements de mise à l’échelle](../azure-best-practices/scaling-subscriptions.md)                                                                                                                                                                                                            |
| Données                         | N/A                                                                                               | [Choix de la bonne option SQL Server dans Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas) et [instructions relatives aux magasins de données Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview)                      |
| Stockage                      | N/A                                                                                               | [Conseils relatifs à Stockage Azure](../considerations/storage-options.md)                                                                                                                                                                                                                       |
| Standards de nommage et de catégorisation | N/A                                                                                               | [Meilleures pratiques en matière de nommage et de catégorisation](../azure-best-practices/naming-and-tagging.md)                                                                                                                                                                                                   |
| la gestion des coûts ;              | N/A                                                                                               | [Coûts de suivi](../azure-best-practices/track-costs.md)                                                                                                                                                                                                                             |
| Calcul                      | N/A                                                                                               | [Options de calcul](../considerations/compute-options.md)                                                                                                                                                                                                                              |

## <a name="customize-or-deploy-a-landing-zone"></a>Personnaliser ou déployer une zone d’atterrissage

Découvrez plus d’informations et téléchargez un exemple de référence du blueprint de zone d’atterrissage de migration afin de le déployer ou de le personnaliser à partir des [exemples Azure Blueprint][deploy-sample].

> [!div class="nextstepaction"]
> [Déployer l’exemple de blueprint][deploy-sample]

Pour obtenir des conseils sur les modifications qui doivent être apportées à ce blueprint ou à la zone d’atterrissage qui en résulte, consultez les [considérations relatives à la zone d’atterrissage](../considerations/index.md).

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez déployé votre première zone d’atterrissage, vous êtes prêt à [développer votre zone d’atterrissage](../considerations/index.md).

> [!div class="nextstepaction"]
> [Étendre votre zone d’atterrissage](../considerations/index.md)

<!-- links -->

[deploy-sample]: https://docs.microsoft.com/azure/governance/blueprints/samples/caf-migrate-landing-zone/deploy
