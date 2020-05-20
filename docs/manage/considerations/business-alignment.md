---
title: Alignement commercial dans la gestion cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à mieux gérer vos opérations cloud et à développer un alignement commercial plus strict.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5a7bfbffa84e7a64221d560b88067caebd311e85
ms.sourcegitcommit: 5d6a7610e556f7b8ca69960ba76a3adfa9203ded
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83400781"
---
# <a name="create-business-alignment-in-cloud-management"></a>Créer un alignement des activités en gestion cloud

Dans les environnements locaux, les ressources informatiques (applications, machines virtuelles, hôtes de machines virtuelles, disques, serveurs, appareils et sources de données) sont gérées par le service informatique dans le cadre de la prise en charge des opérations de charge de travail. En termes informatiques, une charge de travail est un ensemble de ressources informatiques qui prennent en charge une opération métier. Pour aider à prendre en charge les opérations métier, la gestion informatique fournit des processus conçus pour minimiser les interruptions de ces ressources. Lorsqu’une organisation migre vers le cloud, la gestion et les opérations changent légèrement, ce qui est l’occasion de créer un meilleur alignement des activités.

## <a name="business-vernacular"></a>Terminologie

Lorsque vous procédez à l’alignement des activités, la première chose à faire est de vérifier l’alignement des termes utilisés. L’équipe chargée de la gestion informatique, comme la plupart des équipes d’ingénierie, a accumulé de nombreux termes de jargon ou très techniques. De tels termes peuvent entraîner une confusion du côté des parties prenantes et compliquer la mise en correspondance des services de gestion avec la valeur commerciale.

Heureusement, la mise en œuvre d’une stratégie d’adoption cloud et d’un plan d’adoption cloud fournit un cadre idéal pour le remappage de ces termes. Elle crée également des opportunités pour repenser les engagements relatifs à la gestion opérationnelle, en partenariat avec l’entreprise. La série d’articles suivants décrit cette nouvelle approche à travers trois termes qui peuvent faciliter les conversations avec les parties prenantes d’entreprise :

- **[État critique](./criticality.md)**  : Mise en correspondance des charges de travail avec les processus métier. Classement de la criticité pour mieux définir les investissements.
- **[Impact](./impact.md) :** Compréhension de l’impact des pannes potentielles pour faciliter l’évaluation du retour sur investissement pour la gestion cloud.
- **[Engagement](./commitment.md) :** Développement de vrais partenariats, en créant et en documentant des contrats _avec l’entreprise_.

> [!NOTE]
> Les termes soulignés sont des termes informatiques classiques tels que le contrat de niveau de service, le RTO et le RPO. Le mappage des termes métier et des termes informatiques est abordé plus en détail dans l’article [Engagement](./commitment.md).

## <a name="operations-management-workbook"></a>Classeur Operations Management

Pour noter les décisions prises lors de cette conversation sur l’alignement des termes, un [classeur Operations Management](https://raw.githubusercontent.com/Microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) est disponible sur notre site GitHub. Ce classeur ne permet pas de créer le contrat SLA ni de calculer les coûts. Il permet uniquement de capturer ces mesures et prévoir le retour sur les efforts de prévention des pertes.

Les mêmes charges de travail et ressources associées peuvent également être étiquetées directement dans Azure, si les solutions sont déjà déployées dans le cloud.

## <a name="next-steps"></a>Étapes suivantes

Procédez à l’alignement des activités en définissant la [criticité des charges de travail](./criticality.md).

> [!div class="nextstepaction"]
> [Définir la criticité des charges de travail](./criticality.md)
