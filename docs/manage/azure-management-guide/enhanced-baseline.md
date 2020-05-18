---
title: Base de référence de gestion améliorée dans Azure
description: Utilisez le Cloud Adoption Framework pour Azure afin de prendre connaissance des innovations apportées à la base de référence de gestion.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: a5cafc31b5ede4060aedf78ff40215cb7d132aaa
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83216790"
---
<!-- cSpell:ignore ITSMC -->

# <a name="enhanced-management-baseline-in-azure"></a>Base de référence de gestion améliorée dans Azure

Les trois premières disciplines de gestion cloud décrivent une base de référence de gestion. Les articles précédents de ce guide ont décrit un produit viable minimal (MVP) pour les services de gestion cloud, appelé ligne de base de gestion. Cet article décrit quelques-unes des améliorations courantes apportées à la ligne de base.

L’objectif d’une base de référence de gestion est de créer une offre cohérente fournissant un niveau minimal d’engagement métier pour _toutes_ les charges de travail prises en charge. Cette ligne de base d’offres de gestion reproductibles et communes permet à l’équipe de fournir une gestion opérationnelle hautement optimisée, avec une déviation minime.

Toutefois, un engagement plus important envers l’entreprise au-delà de l’offre standard peut être nécessaire. L’image et la liste suivantes présentent trois façons d’aller au-delà de la ligne de base de gestion.

![Au-delà de la base de référence de gestion cloud](../../_images/manage/beyond-the-baseline.png)

- **Base de référence de gestion améliorée :**
  - Ajoutez des améliorations à la ligne de base de gestion lorsque la majorité des charges de travail du portefeuille ont une exigence partagée.
  - Des engagements commerciaux légèrement améliorés à l’aide d’outils et de processus d’opérations natifs Cloud.
  - Les améliorations apportées à la ligne de base ne doivent pas avoir d’impact sur l’architecture des charges de travail spécifiques.
- **Opérations de charge de travail :**
  - Plus grand investissement d’opérations par charge de travail.
  - Degré de résilience le plus élevé.
  - Suggéré pour environ 20 % des charges de travail qui pilotent la valeur commerciale.
  - Généralement réservé aux charges de travail importantes ou critiques.
- **Opérations de plateforme :**
  - Les investissements opérationnels sont répartis sur de nombreuses charges de travail.
  - Les améliorations de la résilience affectent toutes les charges de travail qui utilisent la plateforme définie.
  - Recommandé pour environ 20 % des plateformes ayant le niveau d’état critique le plus élevé.
  - Habituellement réservé aux charges de travail de niveau moyen ou critique.

Les opérations de charge de travail et de plateforme nécessitent la modification des principes de conception et d’architecture. Ces modifications peuvent prendre du temps et entraîner des frais d’exploitation accrus. Pour réduire le nombre de charges de travail nécessitant de tels investissements, une ligne de base de gestion améliorée peut représenter une amélioration suffisante pour l’engagement métier.

Ce tableau présente quelques processus, outils et effets potentiels courants communs aux lignes de base de gestion améliorée des clients :

| Discipline  | Process  | Outil | Impact potentiel | En savoir plus |
|---|---|---|---|---|
| Inventaire et visibilité | Service de suivi des modifications | Azure Resource Graph | Une meilleure visibilité des modifications apportées aux services Azure peut aider à détecter les impacts négatifs plus tôt ou à les corriger plus rapidement | [Aperçu d’Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/overview) |
| Inventaire et visibilité | Intégration de la gestion des services informatiques (ITSM) | Connecteur de gestion des services informatiques | La connexion ITSM automatisée crée une sensibilisation plus tôt. | [Connecteur de gestion des services informatiques (ITSMC)](https://docs.microsoft.com/azure/azure-monitor/platform/itsmc-overview) |
| Conformité opérationnelle | Automatisation des opérations | Azure Automation | Automatisez la conformité opérationnelle pour une réponse plus rapide et plus précise aux modifications. | Consultez les sections suivantes |
| Conformité opérationnelle | Automatisation des performances | Azure Automation | Automatisez la conformité opérationnelle avec les attentes en matière de performances pour résoudre les problèmes courants de mise à l’échelle ou de dimensionnement spécifiques aux ressources. | Consultez les sections suivantes |
| Conformité opérationnelle | Opérations multiclouds | Runbook Worker hybride Azure Automation | Automatiser les opérations sur plusieurs clouds. | [Vue d’ensemble des Runbooks Workers hybrides](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker) |
| Conformité opérationnelle | Automatisation invité |  Configuration d’état souhaité | Configuration basée sur le code des systèmes d’exploitation invités pour réduire les erreurs et la dérive de configuration. | [Vue d’ensemble de la DSC](https://docs.microsoft.com/powershell/scripting/dsc/overview/overview) |
| Protection et récupération | Notification de violation | Azure Security Center | Étendre la protection pour inclure les déclencheurs de récupération de violation de sécurité. | Consultez les sections suivantes |

::: zone target="docs"

## <a name="azure-automation"></a>Azure Automation

::: zone-end
::: zone target="chromeless"

## <a name="azure-automation"></a>[Azure Automation](#tab/AzureAutomation)

::: zone-end

Azure Automation fournit un système centralisé pour la gestion des contrôles automatisés. Dans Azure Automation, vous pouvez exécuter des processus de correction, de mise à l’échelle et d’optimisation simples en réponse aux mesures environnementales. Ces processus réduisent la surcharge associée au traitement manuel des incidents.

Plus important encore, la correction automatisée peut être délivrée en quasi temps réel, ce qui réduit considérablement les interruptions des processus métier. Une étude des interruptions d’activité les plus courantes identifie les activités qui être automatisées au sein de votre environnement.

### <a name="runbooks"></a>Runbooks

L’unité de code de base pour fournir une correction automatisée est le runbook. Les runbooks contiennent les instructions de correction ou de récupération d’un incident.

Pour créer ou gérer des runbooks :

1. Accédez à [Azure Automation](https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Automation%2FAutomationAccounts).
1. Sélectionnez **Comptes Automation**, puis choisissez un des comptes répertoriés.
1. Allez à **Automatisation de processus**.
1. Les options présentées vous permettent de créer ou de gérer des runbooks, des planifications et d’autres fonctionnalités de correction automatisée.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Automation%2FAutomationAccounts]" submitText="Assign Policy" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
::: zone target="docs"

## <a name="azure-security-center"></a>Azure Security Center

::: zone-end
::: zone target="chromeless"

## <a name="azure-security-center"></a>[Centre de sécurité Azure](#tab/AzureSecurityCenter)

::: zone-end

Azure Security Center joue également un rôle important dans votre stratégie de protection et de récupération. Il peut vous aider à superviser la sécurité de vos machines, réseaux, systèmes de stockage, services de données et applications.

Azure Security Center fournit la détection avancée des menaces en utilisant l’apprentissage automatique et l’analytique comportementale pour aider à identifier les menaces actives ciblant vos ressources Azure. Il met également à disposition une protection contre les menaces qui bloque les programmes malveillants ou autres codes indésirables et réduit la surface d’exposition aux attaques par force brute et autres attaques réseau.

Quand Azure Security Center identifie une menace, il déclenche une alerte de sécurité qui indique les étapes à effectuer en réponse à l’attaque. Il fournit également un rapport contenant des informations sur la menace détectée.

Azure Security Center est proposé en deux niveaux : Gratuit et Standard. Les fonctionnalités telles que les suggestions de sécurité sont disponibles gratuitement. Le niveau Standard fournit une protection supplémentaire comme la détection avancée des menaces et une protection de l’ensemble des charges de travail cloud hybrides.

::: zone target="chromeless"

### <a name="action"></a>Action

#### <a name="try-standard-tier-for-free-for-your-first-30-days"></a>Essayez gratuitement le niveau de service Standard pendant les 30 premiers jours

Après avoir activé et configuré des stratégies de sécurité pour les ressources d’un abonnement, vous pouvez voir l’état de sécurité de vos ressources et les problèmes éventuels dans le volet **Prévention**. Vous pouvez également afficher une liste de ces problèmes dans la mosaïque **Recommandations** .

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Pour explorer Azure Security Center, accédez au [portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

### <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez la [documentation d’Azure Security Center](https://docs.microsoft.com/azure/security-center).

::: zone-end
