---
title: Alignement des responsabilités entre les équipes
titleSuffix: Microsoft Cloud adoption Framework for Azure
description: Apprenez à aligner les responsabilités entre les équipes.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 818d2fa74c480b8aee36c4d268ae7a83cb93fab3
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031858"
---
# <a name="align-responsibilities-across-teams"></a>Aligner les responsabilités entre les équipes

Apprenez à aligner les responsabilités entre les équipes en développant une matrice entre les équipes qui identifie les parties *en charge, responsables, consultées et informées* (RACI). Cet article fournit un exemple de matrice RACI pour les structures organisationnelles décrites dans [Établir des structures d’équipe](./organization-structures.md) :

- [Équipe d’adoption du cloud uniquement](#cloud-adoption-team-only)
- [Meilleure pratique MVP](#best-practice-minimum-viable-product-mvp)
- [Équipe informatique centrale](#central-it)
- [Alignement stratégique](#strategic-alignment)
- [Alignement opérationnel](#operational-alignment)
- [Centre d’excellence du cloud (CCoE)](#cloud-center-of-excellence-ccoe)

Pour suivre les décisions de structure organisationnelle au fur et à mesure, téléchargez et modifiez le [modèle de feuille de calcul RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx).

Les exemples inclus dans cet article spécifient ces constructions RACI :

- L’équipe *en charge* d’une fonction.
- Les équipes *responsables* des résultats.
- Les équipes qui doivent être *consultées* pendant la planification.
- Les équipes qui doivent être *informées* quand le travail est terminé.

La dernière ligne de chaque tableau (à l’exception du premier) contient un lien vers la compétence cloud la plus alignée pour plus d’informations.

## <a name="cloud-adoption-team-only"></a>Équipe d’adoption du cloud uniquement

|  |Livraison de solution  |Alignement de l’entreprise  |Gestion des changements  |Opérations de solution  |Gouvernance |Maturité de plateforme  |Opérations de plateforme  |Automatisation de plateforme  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Équipe d’adoption du cloud |Responsable|Responsable|Responsable|Responsable|Responsable|Responsable|Responsable|Responsable|

## <a name="best-practice-minimum-viable-product-mvp"></a>Bonne pratique : produit minimum viable (MVP)

|  |Livraison de solution  |Alignement de l’entreprise  |Gestion des changements  |Opérations de solution  |Gouvernance |Maturité de plateforme  |Opérations de plateforme  |Automatisation de plateforme  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Équipe d’adoption du cloud|Responsable|Responsable|Responsable|Responsable|Consultée|Consultée|Consultée|Informée|
|Équipe de gouvernance cloud|Consultée|Informée|Informée|Informée|Responsable|Responsable|Responsable|Responsable|
||||||||||
|Compétence cloud alignée|[Adoption du cloud](./cloud-adoption.md)|[Stratégie cloud](./cloud-strategy.md)|[Stratégie cloud](./cloud-strategy.md)|[Opérations cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md)-[Gouvernance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Automatisation du cloud](./cloud-automation.md)|

## <a name="central-it"></a>Équipe informatique centrale

| |Livraison de solution  |Alignement de l’entreprise  |Gestion des changements  |Opérations de solution  |Gouvernance |Maturité de plateforme  |Opérations de plateforme  |Automatisation de plateforme  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Équipe d’adoption du cloud  |Responsable|Responsable|En charge    |En charge|Informée   |Informée   |Informée   |Informée   |
|Équipe de gouvernance cloud|Consultée  |Informée   |Informée   |Informée   |Responsable|Consultée  |En charge|Informée   |
|Équipe informatique centrale           |Consultée  |Informée   |Responsable   |Responsable   |En charge  |Responsable|Responsable|Responsable|
||||||||||
|Compétence cloud alignée|[Adoption du cloud](./cloud-adoption.md)|[Stratégie cloud](./cloud-strategy.md)|[Stratégie cloud](./cloud-strategy.md)|[Opérations cloud](./cloud-operations.md)|[Gouvernance cloud](./cloud-governance.md)|[Équipe informatique centrale](./central-it.md)|[Équipe informatique centrale](./central-it.md)|[Équipe informatique centrale](./central-it.md)|

## <a name="strategic-alignment"></a>Alignement stratégique

|  |Livraison de solution  |Alignement de l’entreprise  |Gestion des changements  |Opérations de solution  |Gouvernance |Maturité de plateforme  |Opérations de plateforme  |Automatisation de plateforme  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Équipe de stratégie cloud  |Consultée  |Responsable|Responsable|Consultée  |Consultée  |Informée   |Informée   |Informée   |
|Équipe d’adoption du cloud  |Responsable|Consultée  |En charge|Responsable|Informée   |Informée   |Informée   |Informée   |
|Modèle RACI CCoE      |Consultée  |Informée   |Informée   |Informée   |Responsable|Responsable|Responsable|Responsable|
||||||||||
|Compétence cloud alignée|[Adoption du cloud](./cloud-adoption.md)|[Stratégie cloud](./cloud-strategy.md)|[Stratégie cloud](./cloud-strategy.md)|[Opérations cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md)-[Gouvernance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Automatisation du cloud](./cloud-automation.md)|

## <a name="operational-alignment"></a>Alignement opérationnel

|  |Livraison de solution  |Alignement de l’entreprise  |Gestion des changements  |Opérations de solution  |Gouvernance |Maturité de plateforme  |Opérations de plateforme  |Automatisation de plateforme  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Équipe de stratégie cloud  |Consultée  |Responsable|Responsable|Consultée  |Consultée  |Informée   |Informée   |Informée   |
|Équipe d’adoption du cloud  |Responsable|Consultée  |En charge|Consultée  |Informée   |Informée   |Informée   |Informée   |
|Équipe des opérations cloud|Consultée  |Consultée  |En charge|Responsable|Consultée  |Informée   |Responsable|Consultée  |
|Modèle RACI CCoE      |Consultée  |Informée   |Informée   |Informée   |Responsable|Responsable|En charge|Responsable|
||||||||||
|Compétence cloud alignée|[Adoption du cloud](./cloud-adoption.md)|[Stratégie cloud](./cloud-strategy.md)|[Stratégie cloud](./cloud-strategy.md)|[Opérations cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md)-[Gouvernance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Automatisation du cloud](./cloud-automation.md)|

## <a name="cloud-center-of-excellence-ccoe"></a>Centre d’excellence du cloud (CCoE)

|  |Livraison de solution  |Alignement de l’entreprise  |Gestion des changements  |Opérations de solution  |Gouvernance |Maturité de plateforme  |Opérations de plateforme  |Automatisation de plateforme  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Équipe de stratégie cloud  |Consultée  |Responsable|Responsable|Consultée  |Consultée  |Informée   |Informée   |Informée   |
|Équipe d’adoption du cloud  |Responsable|Consultée  |En charge|Consultée  |Informée   |Informée   |Informée   |Informée   |
|Équipe des opérations cloud|Consultée  |Consultée  |En charge|Responsable|Consultée  |Informée   |Responsable|Consultée  |
|Équipe de gouvernance cloud|Consultée  |Informée   |Informée   |Consultée  |Responsable|Consultée  |En charge|Informée   |
|Équipe de plateforme cloud  |Consultée  |Informée   |Informée   |Consultée  |Consultée  |Responsable|En charge|En charge|
|Équipe d’automatisation du cloud|Consultée  |Informée   |Informée   |Informée   |Consultée  |En charge|En charge|Responsable|
||||||||||
|Compétence cloud alignée|[Adoption du cloud](./cloud-adoption.md)|[Stratégie cloud](./cloud-strategy.md)|[Stratégie cloud](./cloud-strategy.md)|[Opérations cloud](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md)-[Gouvernance cloud](./cloud-governance.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Plateforme cloud](./cloud-platform.md)|[CCoE](./cloud-center-of-excellence.md)-[Automatisation du cloud](./cloud-automation.md)|

## <a name="next-steps"></a>Étapes suivantes

Pour suivre les décisions prises sur la structure de l’organisation au fil du temps, téléchargez et modifiez le [modèle de feuille de calcul RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx). Copiez et modifiez l’exemple le plus étroitement aligné à partir des matrices RACI dans cet article.

> [!div class="nextstepaction"]
> [Télécharger le modèle de feuille de calcul RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx)
