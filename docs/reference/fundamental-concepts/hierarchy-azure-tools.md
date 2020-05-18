---
title: Comment les produits Azure prennent-ils en charge la hiérarchie du portefeuille ?
description: Comment les produits Azure prennent-ils en charge la hiérarchie du portefeuille ?
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: c4ab25ee9cf9a72f6b5a5750157601510d5d050d
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230633"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-do-azure-products-support-the-portfolio-hierarchy"></a>Comment les produits Azure prennent-ils en charge la hiérarchie du portefeuille ?

Dans [Compréhension et alignement de la hiérarchie du portefeuille](./hosting-hierarchy.md), un ensemble de définitions pour la hiérarchie du portefeuille et le mappage de rôle a établi une hiérarchie d’étendue pour la plupart des approches de portefeuille. Comme expliqué dans cet article, vous n’avez peut-être pas besoin de chacun des niveaux ou des _étendues_ décrits ci-dessous. La réduction du nombre de couches a pour effet de réduire la complexité, de sorte que ces couches ne doivent pas toutes être considérées comme une meilleure pratique requise.

Cet article montre comment chaque niveau ou étendue de la hiérarchie est pris en charge dans Azure via des outils d’organisation, des outils de déploiement et de gouvernance, ainsi que certaines solutions dans Cloud Adoption Framework.

## <a name="organizing-the-hierarchy-in-azure"></a>Organisation de la hiérarchie dans Azure

Azure Resource Manager comprend plusieurs approches organisationnelles qui permettent d’organiser des ressources à chaque niveau de la hiérarchie du cloud.

> [!NOTE]
> Les barres de défilement ci-dessous présentent des variantes courantes d’alignement. Les parties grisées des barres de défilement sont courantes, mais ne doivent être utilisées que si un besoin métier spécifique l’exige. Les points qui suivent l’image ci-dessous décrivent uniquement les meilleurs pratiques suggérées.

![Organisation des ressources alignée sur la hiérarchie](../../_images/ready/hierarchy-with-organizing-tools.png)

- **Portefeuille :** l’entreprise ou l’unité commerciale ne contiendra probablement pas de ressources techniques, mais pourrait affecter les décisions en matière de coût. l’entreprise ou l’unité commerciale devraient être représentées dans les nœuds racine de la hiérarchie du groupe d’administration.
- **Plateformes cloud :** chaque environnement doit avoir son propre nœud dans la hiérarchie du groupe d’administration.
- **Zones d’atterrissage et fondations de plateforme :** chaque zone d’atterrissage doit être représentée en tant qu’abonnement. De même, les fondations de plateforme doivent être contenues dans leurs propres abonnements. Diverses conceptions d’abonnement pourraient appeler un abonnement par cloud ou par charge de travail, ce qui modifierait l’outil d’organisation pour chacune.
- **Charge de travail :** chaque charge de travail doit être représentée en tant que groupe de ressources. Des groupes de ressources sont également couramment utilisés pour représenter des solutions, des déploiements ou d’autres regroupements techniques de ressources.
- **Ressource :** chaque ressource est représentée intrinsèquement comme une ressource dans Azure.

### <a name="organize-with-tags"></a>Organiser avec des étiquettes

Des variantes de la meilleure pratique sont courantes. Des écarts par rapport aux meilleures pratiques ci-dessus doivent être enregistrés en marquant toutes les ressources d’une balise pour représenter chacune des couches pertinentes de la hiérarchie. Pour plus d’informations, consultez [Conventions de nommage et de catégorisation recommandées](../../ready/azure-best-practices/naming-and-tagging.md).
