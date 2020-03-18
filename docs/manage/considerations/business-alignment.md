---
title: Alignement commercial dans la gestion cloud
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à mieux gérer vos opérations cloud et à développer un alignement commercial plus strict.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: ee88c1fc88e5c678f7356aa15b473d0fe61eaa2d
ms.sourcegitcommit: 388e32dd4861039149c846c926c0e9230cf28ae3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79140652"
---
# <a name="create-business-alignment-in-cloud-management"></a>Créer un alignement des activités en gestion cloud

Dans les environnements locaux, les ressources informatiques (applications, machines virtuelles, hôtes de machines virtuelles, disques, serveurs, appareils et sources de données) sont gérées par le service informatique dans le cadre de la prise en charge des opérations de charge de travail. En termes informatiques, une charge de travail est un ensemble de ressources informatiques qui prennent en charge une opération métier. Pour aider à prendre en charge les opérations métier, la gestion informatique fournit des processus conçus pour minimiser les interruptions de ces ressources. Lorsqu’une organisation migre vers le cloud, la gestion et les opérations changent légèrement, ce qui est l’occasion de créer un meilleur alignement des activités.

## <a name="business-vernacular"></a>Terminologie

Lorsque vous procédez à l’alignement des activités, la première chose à faire est de vérifier l’alignement des termes utilisés. L’équipe chargée de la gestion informatique, comme la plupart des équipes d’ingénierie, a accumulé de nombreux termes de jargon ou très techniques. De tels termes peuvent entraîner une confusion du côté des parties prenantes et compliquer la mise en correspondance des services de gestion avec la valeur commerciale.

Heureusement, la mise en œuvre d’une stratégie d’adoption cloud et d’un plan d’adoption cloud fournit un cadre idéal pour le remappage de ces termes. Elle crée également des opportunités pour repenser les engagements relatifs à la gestion opérationnelle, en partenariat avec l’entreprise. La série d’articles suivants décrit cette nouvelle approche à travers trois termes qui peuvent faciliter les conversations avec les parties prenantes d’entreprise :

- **[État critique](./criticality.md)**  : Mise en correspondance des charges de travail avec les processus métier. Classement de la criticité pour mieux définir les investissements.
- **[Impact](./impact.md) :** Compréhension de l’impact des pannes potentielles pour faciliter l’évaluation du retour sur investissement pour la gestion cloud.
- **[Engagement](./commitment.md) :** Développement de vrais partenariats, en créant et en documentant des contrats *avec l’entreprise*.

> [!NOTE]
> Les termes soulignés sont des termes informatiques classiques tels que le contrat de niveau de service, le RTO et le RPO. Le mappage des termes métier et des termes informatiques est abordé plus en détail dans l’article [Engagement](./commitment.md).

## <a name="ops-management-planning-workbook"></a>Classeur de planification de la gestion des opérations

Pour noter les décisions prises lors de cette conversation sur l’alignement des termes, un [classeur de gestion des opérations](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) est disponible sur notre site GitHub. Ce classeur ne permet pas de créer le contrat SLA ni de calculer les coûts. Il permet uniquement de capturer ces mesures et prévoir le retour sur les efforts de prévention des pertes.

Les mêmes charges de travail et ressources associées peuvent également être étiquetées directement dans Azure, si les solutions sont déjà déployées dans le cloud.

## <a name="next-steps"></a>Étapes suivantes

Procédez à l’alignement des activités en définissant la [criticité des charges de travail](./criticality.md).

> [!div class="nextstepaction"]
> [Définir la criticité des charges de travail](./criticality.md)
