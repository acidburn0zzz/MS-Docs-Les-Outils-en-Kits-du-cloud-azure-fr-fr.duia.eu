---
title: Comment les produits Azure prennent-ils en charge la hiérarchie du portefeuille ?
description: Comment les produits Azure prennent-ils en charge la hiérarchie du portefeuille ?
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 17d6368eb8e0d55e8ad8107601a690046af1c2e9
ms.sourcegitcommit: 9a84c2dfa4c3859fd7d5b1e06bbb8549ff6967fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83755631"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-do-azure-products-support-the-portfolio-hierarchy"></a>Comment les produits Azure prennent-ils en charge la hiérarchie du portefeuille ?

Dans [Compréhension et alignement de la hiérarchie du portefeuille](./hosting-hierarchy.md), un ensemble de définitions pour la hiérarchie du portefeuille et le mappage de rôle a établi une hiérarchie d’étendue pour la plupart des approches de portefeuille. Comme expliqué dans cet article, vous n’avez peut-être pas besoin de chacun des niveaux ou des _étendues_ décrits. La minimisation du nombre de couches a pour effet de réduire la complexité : ces couches ne doivent donc pas toutes être considérées comme une exigence.

Cet article montre comment chaque niveau ou étendue de la hiérarchie est pris en charge dans Azure via des outils d’organisation, des outils de déploiement et de gouvernance, ainsi que par certaines solutions dans le Microsoft Cloud Adoption Framework pour Azure.

## <a name="organizing-the-hierarchy-in-azure"></a>Organisation de la hiérarchie dans Azure

Azure Resource Manager comprend plusieurs approches organisationnelles qui permettent d’organiser des ressources à chaque niveau de la hiérarchie du cloud.

Les barres de défilement dans le diagramme suivant montrent des variantes courantes dans l’alignement. Les parties grisées des barres de défilement sont courantes, mais doivent être utilisées seulement pour des besoins métier spécifiques. Les points qui suivent l’image décrivent une suggestion de bonne pratique.

![Organisation des ressources alignée sur la hiérarchie](../../_images/ready/hierarchy-with-organizing-tools.png)

- **Portefeuille :** L’entreprise ou la division ne contiendra probablement pas de ressources techniques, mais elle pourrait affecter les décisions en matière de coût. L’entreprise et les divisions sont représentées dans les nœuds racine de la hiérarchie du groupe d’administration.
- **Plateformes cloud :** Chaque environnement a son propre nœud dans la hiérarchie du groupe d’administration.
- **Zones d’atterrissage et fondations de plateforme :** Chaque zone d’atterrissage est représentée en tant qu’abonnement. De même, les fondations de plateforme sont contenues dans leurs propres abonnements. Certaines conceptions d’abonnement peuvent appeler un abonnement par cloud ou par charge de travail, ce qui modifie l’outil d’organisation pour chacun.
- **Charges de travail :** Chaque charge de travail est représentée en tant que groupe de ressources. Les groupes de ressources sont souvent utilisés pour représenter des solutions, des déploiements ou d’autres regroupements techniques de ressources.
- **Ressources :** chaque ressource est représentée intrinsèquement comme une ressource dans Azure.

## <a name="organizing-with-tags"></a>Organisation avec des étiquettes

Les variantes par rapport à la bonne pratique sont courantes. Vous pouvez les enregistrer en étiquetant toutes les ressources. Utilisez une étiquette pour représenter chacune des couches pertinentes de la hiérarchie. Pour plus d’informations, consultez [Conventions de nommage et de catégorisation recommandées](../../ready/azure-best-practices/naming-and-tagging.md).
