---
title: Données d’inventaire pour un patrimoine numérique
description: Apprenez à dresser une liste d’inventaire des ressources informatiques qui prennent en charge des fonctions métier spécifiques en vue d’être analysées et rationalisées ultérieurement.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 186013e2f626be18f0cef8beea66d638be9a793c
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80434829"
---
# <a name="gather-inventory-data-for-a-digital-estate"></a>Collecter des données d’inventaire pour un patrimoine numérique

Le développement d’un inventaire est la première étape de [planification du patrimoine numérique](./index.md). Au cours de ce processus, des ressources informatiques prenant en charge des fonctions métier spécifiques sont collectées en vue d’être analysées et rationalisées. Cet article part du principe qu’une analyse ascendante est plus appropriée pour la planification. Pour plus d’informations, consultez [Approches de la planification du patrimoine numérique](./approach.md).

## <a name="take-inventory-of-a-digital-estate"></a>Inventaire du patrimoine numérique

L’inventaire d’un patrimoine numérique est différent selon la transformation numérique souhaitée et le processus de transformation qui lui est associé.

- **Migration cloud :**  Dans le cadre d’une migration cloud, nous vous recommandons souvent de collecter l’inventaire à partir des outils d’analyse qui créent une liste centralisée de toutes les machines virtuelles et de tous les serveurs. Certains outils peuvent également créer des mappages et des dépendances réseau, qui aident à définir l’alignement des charges de travail.

- **Innovation des applications :** L’inventaire au cours d’un effort d’innovation de l’application basée sur le cloud commence par le client. Le mappage de l’expérience client du début à la fin est un bon point de départ. L’alignement de ce mappage sur les applications, les API, les données et autres ressources permet de créer un inventaire détaillé pour l’analyse.

- **Innovation des données :** Les efforts en matière d’innovation des données cloud se concentrent sur le produit ou le service. Un inventaire comprend également un mappage des opportunités de perturbation du marché, ainsi que des fonctionnalités nécessaires.

- **Sécurité :** L’inventaire apporte aux responsables de la sécurité un éclairage leur permettant d’évaluer, protéger et superviser les ressources de l’organisation.

## <a name="accuracy-and-completeness-of-an-inventory"></a>Exactitude et complétude de l’inventaire

Un inventaire est rarement complet après sa première itération. Nous recommandons vivement que l’équipe chargée des stratégies cloud aligne les parties prenantes et encourage les utilisateurs avancés afin de valider l’inventaire. Lorsque cela est possible, utilisez d’autres outils, comme l’analyse du réseau et des dépendances pour identifier les ressources qui reçoivent du trafic, mais qui ne figurent pas dans l’inventaire.

## <a name="next-steps"></a>Étapes suivantes

Une fois l’inventaire compilé et validé, il peut être rationalisé. La rationalisation de l’inventaire est l’étape qui suit dans la planification du patrimoine numérique.

> [!div class="nextstepaction"]
> [Rationaliser le patrimoine numérique](./rationalize.md)
