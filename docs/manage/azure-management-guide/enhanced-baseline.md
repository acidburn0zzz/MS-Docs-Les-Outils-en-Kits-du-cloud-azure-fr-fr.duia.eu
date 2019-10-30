---
title: Base de référence de gestion améliorée dans Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Améliorations courantes de la ligne de base de gestion
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 85e289867ac69f3403d964078a7c3f3b2a6c96a7
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683701"
---
# <a name="enhanced-management-baseline-in-azure"></a>Base de référence de gestion améliorée dans Azure

Les trois premières disciplines de gestion cloud décrivent une base de référence de gestion. Les articles précédents de ce guide ont décrit un produit viable minimal (MVP) pour les services de gestion cloud, appelé ligne de base de gestion. Cet article décrit quelques-unes des améliorations courantes apportées à la ligne de base.

L’objectif d’une base de référence de gestion est de créer une offre cohérente fournissant un niveau minimal d’engagement commercial pour **toutes** les charges de travail prises en charge. Cette base de référence d’offres de gestion reproductibles communes permet à l’équipe de fournir une gestion opérationnelle hautement optimisée, avec une déviation minime. Toutefois, un engagement plus important envers l’entreprise au-delà de l’offre standard peut être nécessaire. L’image et la liste à puces suivantes présentent trois façons d’aller au-delà de la base de référence de gestion.

![Au-delà de la base de référence de gestion cloud](../../_images/manage/beyond-the-baseline.png)

- **Opérations de charge de travail :**
  - Plus grand investissement d’opérations par charge de travail.
  - Degré de résilience le plus élevé.
  - Suggéré pour environ 20 % des charges de travail qui pilotent la valeur commerciale.
  - Généralement réservé aux charges de travail importantes ou critiques.
- **Opérations de plateforme :**
  - Les investissements opérationnels sont répartis sur de nombreuses charges de travail.
  - Les améliorations de la résilience ont un impact sur toutes les charges de travail qui utilisent la plate-forme définie.
  - Suggéré pour +/- 20% des plateformes les plus importantes.
  - Habituellement réservé aux charges de travail de niveau moyen ou critique.
- **Base de référence de gestion améliorée :**
  - Investissement opérationnel le plus bas.
  - Des engagements commerciaux légèrement améliorés à l’aide d’outils et de processus d’opérations natifs du cloud.

Les opérations de charge de travail et de plateforme peuvent nécessiter la modification des principes de conception et d’architecture. Ces modifications peuvent prendre du temps et entraîner des frais d’exploitation accrus. Pour réduire le nombre de charges de travail nécessitant de tels investissements, une base de référence de gestion améliorée peut représenter une amélioration suffisante pour l’engagement commercial.

Le tableau suivant présente quelques processus, outils et impacts potentiels courants communs aux lignes de base de gestion améliorée des clients.

|Discipline  |Process  |Outil  |Impact potentiel| En savoir plus |
|---------|---------|---------|---------|---------|
|Inventaire et visibilité|Service de suivi des modifications|Azure Resource Graph|Une meilleure visibilité des modifications apportées aux services Azure peut aider à détecter les impacts négatifs plus tôt ou à les corriger plus rapidement|[Vue d’ensemble d’Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/overview)|
|Inventaire et visibilité|Intégration de la gestion des services informatiques (ITSM)|Connecteur de gestion des services informatiques|La connexion ITSM automatisée crée une sensibilisation plus tôt|[Connecteur ITSM Azure](https://docs.microsoft.com/azure/azure-monitor/platform/itsmc-overview)|
|Conformité opérationnelle|Automatisation des opérations|Azure Automation|Automatisez la conformité opérationnelle pour une réponse plus rapide et plus précise aux changements|Voir ci-dessous|
|Conformité opérationnelle|Opérations multiclouds|Runbook Worker hybride Azure Automation|Automatiser les opérations sur plusieurs clouds|[Vue d’ensemble du runbook hybride](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)|
|Conformité opérationnelle|Automatisation invité|Configuration d’état souhaité (DSC)|Configuration basée sur le code des systèmes d’exploitation invités pour réduire les erreurs et la dérive de configuration|[Vue d’ensemble de la DSC](/powershell/scripting/dsc/overview/overview)|
|Protection et récupération|Notification de violation|Azure Security Center|Étendre la protection pour inclure les déclencheurs de récupération de violation de sécurité|Voir ci-dessous|

::: zone target="docs"

## <a name="azure-automation"></a>Azure Automation

::: zone-end
::: zone target="chromeless"

## <a name="azure-automationtabazureautomation"></a>[Azure Automation](#tab/AzureAutomation)

::: zone-end

Azure Automation fournit un système centralisé pour la gestion des contrôles automatisés. Dans Azure Automation, il est possible d’exécuter des processus simples de mise à jour, de mise à l’échelle et d’optimisation en réponse aux mesures environnementales, ce qui réduit la surcharge associée au traitement manuel des incidents. Plus important encore, la correction automatisée peut être effectuée en temps quasi-réel, ce qui réduit considérablement les interruptions des processus d’entreprise. Une étude des interruptions d’entreprise les plus courantes permettra d’identifier les activités pouvant être automatisées au sein de votre environnement.

### <a name="runbooks"></a>Runbooks

L’unité de code de base pour fournir une correction automatisée est le runbook. Les runbooks contiennent les instructions de correction ou de récupération d’un incident.

Pour créer ou gérer des runbooks :

1. Accédez à [Azure Automation](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
2. Choisissez l’un des **comptes Automation** de la liste.
3. Recherchez la section**Automatisation de processus** de la navigation dans le portail.
4. Les options de cette section vous permettent de créer ou de gérer des runbooks, des planifications et d’autres fonctionnalités de correction automatisée.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts]" submitText="Assign Policy" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
::: zone target="docs"

## <a name="azure-security-center"></a>Azure Security Center

::: zone-end
::: zone target="chromeless"

## <a name="azure-security-centertabazuresecuritycenter"></a>[Centre de sécurité Azure](#tab/AzureSecurityCenter)

::: zone-end

Azure Security Center joue également un rôle important dans votre stratégie de protection et de récupération. Il peut vous aider à superviser la sécurité de vos machines, réseaux, systèmes de stockage, services de données et applications. Azure Security Center fournit la détection avancée des menaces en utilisant l’apprentissage automatique et l’analytique comportementale pour aider à identifier les menaces actives ciblant vos ressources Azure. Il met également à disposition une protection contre les menaces qui bloque les programmes malveillants ou autres codes indésirables et réduit la surface d’exposition aux attaques par force brute et autres attaques réseau.

Quand Azure Security Center identifie une menace, il déclenche une alerte de sécurité qui indique les étapes à effectuer en réponse à l’attaque. Il fournit également un rapport contenant des informations sur la menace qui a été détectée.

Azure Security Center est proposé en deux niveaux de service : Gratuit et Standard. Les fonctionnalités telles que les recommandations de sécurité sont disponibles gratuitement. Le niveau de service Standard fournit une protection supplémentaire comme la détection avancée des menaces et une protection de l’ensemble des charges de travail cloud hybrides.

::: zone target="chromeless"

### <a name="action"></a>Action

**Essayez gratuitement le niveau de service Standard pendant les 30 premiers jours.**

Après avoir activé et configuré des stratégies de sécurité pour les ressources d’un abonnement, vous pouvez voir l’état de sécurité de vos ressources et les problèmes éventuels dans la section **Prévention**. Vous pouvez également afficher une liste de ces problèmes dans la mosaïque **Recommandations** .

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Pour explorer Azure Security Center, accédez au [portail Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

### <a name="learn-more"></a>En savoir plus

Pour plus d’informations, consultez la [documentation d’Azure Security Center](https://docs.microsoft.com/azure/security-center).

::: zone-end