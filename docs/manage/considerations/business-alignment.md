---
title: Alignement des activités - Gestion cloud et opérations
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Alignement des activités - Gestion cloud et opérations
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 9c6884d57b9238f58921b14ec3ddbbe3623506af
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558587"
---
# <a name="create-business-alignment-in-cloud-management"></a>Créer un alignement des activités en gestion cloud

Dans les environnements locaux, les ressources informatiques (applications, machines virtuelles, hôtes de machines virtuelles, disques, serveurs, appareils et sources de données) sont gérées par le service informatique dans le cadre de la prise en charge des opérations de charge de travail. En termes informatiques, une charge de travail est un ensemble de ressources informatiques qui prennent en charge une opération métier. Dans les environnements locaux, la gestion informatique fournit des processus conçus pour réduire les perturbations subies par ces ressources informatiques, en vue de réduire les perturbations qui se produisent au niveau des opérations métier. Lors d’une migration vers le cloud, la gestion et les opérations changent légèrement, ce qui est l’occasion de créer un meilleur alignement des activités.

## <a name="business-vernacular"></a>Terminologie

Lorsque vous procédez à l’alignement des activités, la première chose à faire est de procéder à l’alignement des termes utilisés. L’équipe chargée de la gestion informatique, comme la plupart des équipes d’ingénierie, utilise pas mal de jargon et de termes très techniques. Ces termes peuvent entraîner une confusion du côté des parties prenantes, et compliquer la mise en correspondance des services de gestion avec la valeur commerciale.

Heureusement, la création d’une stratégie d’adoption cloud et d’un plan d’adoption cloud fournit un cadre idéal pour l’alignement des termes. Elle crée également une formidable opportunité de repenser les engagements relatifs à la gestion opérationnelle, en partenariat avec l’entreprise. La série d’articles suivante décrit cette nouvelle approche à travers trois termes qui peuvent faciliter les discussions avec les parties prenantes :

- **[Criticité](./criticality.md)**  : Mise en correspondance des charges de travail avec les processus métier. Classement de la criticité pour mieux définir les investissements.
- **[Impact](./impact.md)**  : Comprendre l’impact des pannes potentielles pour faciliter l’évaluation du retour sur investissement pour la gestion cloud.
- **[Engagement](./commitment.md)**  : Développer de vrais partenariats, en créant et en documentant des contrats **avec l’entreprise**.

> [!NOTE]
> Sous chacun de ces termes se trouvent des termes informatiques classiques tels que le contrat SLA, le RTO et le RPO. La mise en correspondance des termes métier et des termes informatiques est abordée plus en détail dans l’article sur l’engagement.

## <a name="ops-management-planning-workbook"></a>Classeur de planification de la gestion des opérations

Pour noter les décisions prises lors de cette discussion, vous pouvez utiliser le [classeur de gestion des opérations](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) qui est disponible dans notre dépôt GitHub. Ce classeur ne permet pas de créer le contrat SLA ni de calculer les coûts. Il sert uniquement de guide pour capturer ces mesures et prévoir le retour sur les efforts de prévention des pertes.

Les mêmes charges de travail et ressources associées peuvent également être étiquetées directement dans Azure, si les solutions sont déjà déployées dans le cloud.

## <a name="next-steps"></a>Étapes suivantes

Procédez à l’alignement des activités en définissant la [criticité des charges de travail](./criticality.md).

> [!div class="nextstepaction"]
> [Définir la criticité des charges de travail](./criticality.md)
