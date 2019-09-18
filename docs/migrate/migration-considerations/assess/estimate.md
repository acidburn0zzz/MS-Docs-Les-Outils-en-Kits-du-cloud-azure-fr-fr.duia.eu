---
title: Estimer les coûts du cloud avant la migration
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explication du processus d’estimation des coûts du cloud avant la migration.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 2bbafffd50cba58fc5304489f31521e6da8a8345
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025431"
---
# <a name="estimate-cloud-costs"></a>Estimer les coûts du cloud

Pendant la migration, plusieurs facteurs peuvent affecter les décisions et les activités d’exécution. Pour comprendre les options les plus adaptées à différentes situations, cet article présente les différentes options d’estimation des coûts du cloud.

## <a name="digital-estate-size"></a>Taille du patrimoine numérique

La taille de votre patrimoine numérique affecte directement les décisions de migration. Les migrations qui impliquent moins de 250 machines virtuelles peuvent être estimées beaucoup plus facilement qu’une migration impliquant plus de 10 000 machines virtuelles. Il est fortement recommandé de sélectionner une charge de travail plus petite pour votre première migration. Cela permet à votre équipe d’apprendre à estimer les coûts d’un effort de migration simple avant de tenter d’estimer des migrations de charges de travail plus importantes et plus complexes.

Toutefois, notez que les migrations de charges de travail uniques et de taille modeste peuvent tout de même impliquer un volume très variable de ressources de soutien. Si votre migration implique moins de 1 000 machines virtuelles, un outil comme [Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-overview) est probablement suffisant pour collecter les données sur l’inventaire et prévoir les coûts. D’autres options d’outils de calcul des coûts sont décrites dans l’article sur les [calculs des coûts du patrimoine numérique](../../../digital-estate/calculate.md).

Pour les patrimoines numériques de plus de 1 000 appareils, il est toujours possible de diviser une estimation en quatre ou cinq itérations actionnables, ce qui rend le processus d’estimation plus gérable. Pour les grands patrimoines ou lorsqu’un degré de précision des prévisions plus élevé est requis, une approche plus complète, comme celle décrite dans la section « [Patrimoine numérique](../../../digital-estate/index.md) » du Framework d’adoption du cloud, sera probablement nécessaire.

## <a name="accounting-models"></a>Modèles de comptabilité

Modèles de comptabilité

Si vous êtes familiarisé avec les processus traditionnels d’approvisionnement en informatique, l’estimation dans le cloud peut vous paraître étrangère. Lors de l’adoption de technologies cloud, l’acquisition passe d’un modèle de dépenses d’investissement rigide et structuré à un modèle de dépenses au fonctionnement fluide. Dans le modèle de dépenses en capital traditionnel, l’équipe informatique tente de consolider le pouvoir d’achat pour plusieurs charges de travail à travers différents programmes afin de centraliser un pool de ressources informatiques partagées pouvant prendre en charge chacune de ces solutions. Dans le modèle de dépenses d’exploitation du cloud, les coûts peuvent être directement attribués aux besoins des charges de travail individuelles, des équipes ou des unités commerciales. Cette approche permet une attribution plus directe des coûts au client interne soutenu. Lors de l’estimation des coûts, il est important de comprendre d’abord la mesure dans laquelle cette nouvelle fonctionnalité de gestion des comptes sera utilisée par l’équipe informatique.

Pour ceux souhaitant répliquer l’approche héritée des dépenses d’investissement dans la comptabilité, utilisez les sorties de l'une des approches suggérées dans la section « [Taille du patrimoine numérique](#digital-estate-size) » ci-dessus pour obtenir un coût annuel. Ensuite, multipliez ce coût annuel par le cycle habituel d’actualisation du matériel de l’entreprise. Le cycle d’actualisation du matériel correspond à la fréquence à laquelle une entreprise remplace le matériel vieillissant, généralement mesuré en années. La fréquence d’exécution annuelle multipliée par le cycle d’actualisation du matériel crée une structure de coûts similaire à un modèle d’investissement en dépenses de capital.

## <a name="next-steps"></a>Étapes suivantes

Après l’estimation des coûts, la migration peut commencer. Toutefois, il est judicieux d’examiner les options de [partenariat et de support](./partnership-options.md) avant de commencer la migration.

> [!div class="nextstepaction"]
> [Comprendre les options de partenariat](./partnership-options.md)
