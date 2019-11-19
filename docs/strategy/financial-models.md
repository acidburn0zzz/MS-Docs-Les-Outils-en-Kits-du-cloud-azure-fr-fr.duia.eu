---
title: Créer un modèle financier pour la transformation cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Comment créer un modèle financier pour la transformation cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: cb5653de592fb92fa9ad9f5866997703a928ee4e
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566588"
---
# <a name="create-a-financial-model-for-cloud-transformation"></a>Créer un modèle financier pour la transformation cloud

La création d’un modèle financier qui fait un état précis de tous les bénéfices d’une transformation cloud pour l’entreprise peut être compliquée. Les modèles financiers et les justifications métier ont tendance à varier selon les organisations. Cet article établit certaines formules et met en évidence certains points souvent négligés quand les stratèges créent des modèles financiers.

## <a name="return-on-investment"></a>Retour sur investissement

Le ROI (retour sur investissement) est souvent un critère important pour la direction ou les responsables d’une entreprise. Il est utilisé pour comparer différents moyens d’investir une partie des ressources du capital. La formule du retour sur investissement est relativement simple, mais les valeurs de données à entrer dans cette formule peuvent être plus difficiles à déterminer. Globalement, le retour sur investissement est ce que vous fait gagner un investissement initial. Il est généralement représenté sous forme de pourcentage :

![ROI est égal à (gain lié à l’investissement moins coût de l’investissement) divisé par coût de l’investissement](../_images/strategy/formula-roi.png)

Dans les sections suivantes, nous allons voir quelles sont les données à inclure dans le calcul de l’investissement initial et du gain résultant de cet investissement (revenus).

## <a name="calculate-initial-investment"></a>Calculer l’investissement initial

L’investissement initial correspond aux dépenses en capital et aux dépenses d’exploitation à engager pour effectuer une transformation. La classification des coûts dépend du modèle comptable utilisé et des préférences du directeur financier. Toutefois, cette catégorie doit comprendre des éléments tels que les services professionnels à transformer, les licences logicielles utilisées uniquement durant la transformation, le coût des services cloud durant la transformation et, éventuellement, le coût des employés salariés durant la transformation.

Ajoutez ces coûts pour créer une estimation de l’investissement initial.

## <a name="calculate-the-gain-from-investment"></a>Calculer le gain de l’investissement

Le calcul du gain résultant de l’investissement nécessite souvent une seconde formule spécifique aux résultats opérationnels et aux changements techniques associés. Le calcul des revenus est plus difficile que le calcul des réductions de coûts.

Pour calculer les revenus, vous avez besoin de deux variables :

![Le gain de l’investissement est égal aux deltas des revenus plus les deltas des coûts](../_images/strategy/formula-gain-from-investment.png)

Ces variables sont décrites dans les sections suivantes.

## <a name="revenue-deltas"></a>Deltas des revenus

Les deltas des revenus doivent être estimés en partenariat avec les parties prenantes de l’entreprise. Une fois que les parties prenantes de l’entreprise se sont entendues sur l’impact sur les revenus, cette donnée peut être utilisée pour améliorer les résultats.

## <a name="cost-deltas"></a>Écarts de coûts

Les deltas des coûts correspondent à la variation des coûts, à la hausse ou à la baisse, résultant de la transformation. Des variables indépendantes peuvent affecter les deltas des coûts. Les revenus dépendent en grande partie de coûts de base comme les réductions de dépenses d’investissement, l’évitement de coûts, les réductions de coûts d’exploitation et les amortissements dégressifs. Les sections suivantes décrivent certains deltas des coûts à prendre en compte.

### <a name="depreciation-reduction-or-acceleration"></a>Réduction ou accélération de l’amortissement

Vous pouvez obtenir des conseils sur l’amortissement auprès du service financier de l’entreprise. Les informations suivantes sont destinées à servir de référence générale sur l’amortissement.

Quand du capital est investi dans l’acquisition d’une ressource, cet investissement peut être utilisé à des fins financières ou fiscales pour générer des revenus tout au long de la durée de vie attendue de la ressource. Certaines entreprises voient l’amortissement comme un avantage fiscal positif. D’autres le considèrent comme une dépense permanente engagée, similaire à d’autres dépenses récurrentes attribuées au budget informatique annuel.

Discutez avec le service financier pour déterminer si l’élimination de l’amortissement est envisageable et si cela peut avoir un impact positif sur les deltas des coûts.

### <a name="physical-asset-recovery"></a>Récupération de ressources physiques

Dans certains cas, les ressources mises hors service peuvent être vendues, générant ainsi des revenus supplémentaires. Ces revenus sont souvent amalgamés dans la réduction des coûts par facilité, alors qu’ils correspondent à une augmentation de revenus et qu’ils sont imposables en tant que tels. Discutez avec le service financier pour comprendre la viabilité de cette option et savoir comment prendre en compte les revenus qui en résultent.

### <a name="operational-cost-reductions"></a>Réductions des coûts d’exploitation

Les dépenses récurrentes nécessaires au fonctionnement d’une entreprise sont souvent appelées dépenses d’exploitation. Il s’agit d’une catégorie large. Dans la plupart des modèles de comptabilité, elle comprend les éléments suivants :

- Gestion de licences des logiciels
- Frais d’hébergement
- Factures d’électricité
- Location immobilière
- Frais de climatisation
- Équipes temporaires nécessaires aux opérations d’exploitation
- Location de matériel
- Pièces de rechange
- Contrats de maintenance
- Services de réparation
- Services BCDR (continuité de l’activité et reprise d’activité)
- Autres dépenses qui ne nécessitent pas d’approbations des dépenses en capital

Cette catégorie fournit l’un des deltas les plus rémunérateurs. Quand vous réfléchissez à une migration cloud, le temps investi pour rendre la liste ci-dessus exhaustive est rarement perdu. Interrogez le DSI et le service financier pour vérifier si tous les coûts opérationnels ont bien été pris en compte.

### <a name="cost-avoidance"></a>Évitement des coûts

Quand une dépense d’exploitation est prévue, mais qu’elle n’est pas encore intégrée à un budget approuvé, elle risque de ne pas entrer dans une catégorie de réductions des coûts. Par exemple, si les licences VMware et Microsoft doivent être renégociées et achetées l’année prochaine, elles ne constituent pas encore des coûts engagés. Les réductions de ces coûts prévus sont traitées comme des coûts opérationnels pour des raisons liées aux calculs du delta des coûts. Toutefois, de manière informelle, ces dépenses doivent rester dans la catégorie « Évitement des coûts » jusqu’à la fin de la négociation et de l’approbation du budget.

### <a name="soft-cost-reductions"></a>Réductions des coûts accessoires

Dans certaines entreprises, les coûts accessoires, par exemple les réductions de la complexité opérationnelle ou les réductions des équipes à plein temps en charge d’un centre de données, peuvent également être inclus dans les deltas des coûts. Toutefois, l’inclusion des coûts accessoires n’est peut-être pas une bonne idée. Quand vous incluez des réductions de coûts accessoires, vous introduisez une hypothèse non documentée selon laquelle cette réduction va générer des économies de coûts tangibles. Les projets technologiques donnent rarement lieu à une récupération réelle des coûts accessoires.

### <a name="headcount-reductions"></a>Réductions d’effectifs

Les gains de temps pour les équipes sont souvent inclus dans la réduction des coûts accessoires. Quand ces gains de temps correspondent à une réduction réelle des effectifs ou de la masse salariale du service informatique, ils peuvent être calculés séparément en tant que réduction d’effectifs.

Cela dit, les compétences nécessaires localement correspondent généralement à des compétences similaires (ou supérieures) nécessaires dans le cloud. Ainsi, les employés ne sont généralement pas licenciés après une migration cloud.

Il existe une exception, quand la capacité opérationnelle est fournie par un tiers ou un MSP (fournisseur de services managés). Si les systèmes informatiques sont managés, les coûts opérationnels peuvent être remplacés par une solution cloud native ou un MSP de cloud natif. Un MSP de cloud natif travaille souvent plus efficacement et potentiellement à moindre coût. Si tel est le cas, les réductions des coûts opérationnels entrent dans les calculs des coûts réels.

### <a name="capital-expense-reductions-or-avoidance"></a>Réductions ou évitement des dépenses d’investissement

Les dépenses en capital sont légèrement différentes des dépenses d’exploitation. En règle générale, cette catégorie s’applique aux cycles de renouvellement ou à l’extension des centres de données. L’ajout d’un nouveau cluster hautes performances pour l’hébergement d’une solution Big Data ou d’un entrepôt de données est un exemple d’extension de centre de données. Cette dépense entre généralement dans une catégorie de dépenses en capital. Les cycles standards de renouvellement sont les cas les plus courants. Certaines entreprises ont mis en place des cycles fixes de renouvellement de leur matériel, c’est-à-dire qu’elles mettent hors service et remplacent leurs ressources selon un cycle régulier (généralement tous les trois, cinq ou huit ans). Ces cycles coïncident souvent avec les cycles de location des ressources ou la durée de vie prévue des équipements. À chaque nouveau cycle de renouvellement, le service informatique effectue des dépenses en capital pour acquérir du nouveau matériel.

Si un cycle de renouvellement est approuvé et budgété, la transformation cloud peut vous aider à éliminer ce coût. Si un cycle de renouvellement est planifié, mais pas encore approuvé, la transformation cloud peut permettre d’éviter des dépenses en capital. Les deux réductions sont ajoutées au delta des coûts.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur les modèles de [comptabilité cloud](./cloud-accounting.md).

> [!div class="nextstepaction"]
> [Comptabilité cloud](./cloud-accounting.md)
