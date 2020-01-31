---
title: Qu’est-ce que la classification des données ?
description: La classification des données vous permet de déterminer et d’affecter la valeur aux données de votre organisation et constitue un point de départ commun pour la gouvernance.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 1f476aaccfc88eab4a2bea1db17e7b1d33f31ee9
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76805079"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-data-classification"></a>Qu’est-ce que la classification des données ?

La classification des données vous permet de déterminer et d’affecter la valeur aux données de votre organisation et constitue un point de départ commun pour la gouvernance. Le processus de classification des données classe les données en fonction de leur sensibilité et de leur impact commercial afin d’identifier les risques. Une fois les données classées, vous pouvez les gérer de manière à protéger les données sensibles ou importantes contre le vol ou la perte.

## <a name="understand-data-risks-then-manage-them"></a>Comprendre les risques liés aux données, puis les gérer

Avant d’atténuer un risque, il convient de le comprendre. En cas de responsabilité face à une violation des données, cette compréhension passe par la classification des données. Le processus de classification des données consiste à associer une caractéristique de métadonnées à chaque ressource du patrimoine numérique afin d’identifier le type de données associé à cette ressource.

Toutes les ressources identifiées comme des candidates potentielles à la migration ou au déploiement vers le cloud doivent être associées à des métadonnées qui permettent d’enregistrer la classification des données, l’importance dans l’entreprise et le responsable de facturation. Ces trois points de classification peuvent se révéler très utiles à la compréhension et l’atténuation des risques.

## <a name="classifications-microsoft-uses"></a>Classifications utilisées par Microsoft

La liste ci-dessous répertorie les classifications utilisées par Microsoft. En fonction de votre secteur d’activité ou de vos exigences de sécurité existantes, il se peut que des normes de classifications des données existent déjà au sein de votre organisation. Si ce n’est pas le cas, nous vous invitons à utiliser cet exemple de classification. Il vous permettra de comprendre votre patrimoine numérique et votre profil de risque.

- **Non professionnelles :** Données concernant votre vie personnelle qui n’appartiennent pas à Microsoft.
- **Public :** Données d’entreprise qui sont mises à disposition librement et destinées à être utilisées publiquement.
- **Généralités :** Données d’entreprise non destinées au public.
- **Confidentielles :** Données d’entreprise susceptibles de nuire à Microsoft si elles sont partagées.
- **Hautement confidentielles :** Données d’entreprise susceptibles de porter un préjudice important à Microsoft si elles sont partagées.

## <a name="tagging-data-classification-in-azure"></a>Balisage de classification des données dans Azure

Les balises de ressource sont une bonne approche suggérée pour le stockage des métadonnées, et vous pouvez utiliser ces balises pour appliquer des informations de classification aux ressources déployées. Bien que le marquage des ressources cloud par classification ne remplace pas le processus formel de classification des données, il s’agit d’un outil précieux pour la gestion des ressources et l’application de la stratégie. [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection) offre une excellente solution pour classer les _données_, et ce, quel que soit leur emplacement (en local, dans Azure ou ailleurs). Considérez-le comme s’inscrivant dans une stratégie de classification globale.

Pour plus d’informations sur le balisage des ressources dans Azure, consultez [Organisation des ressources Azure à l'aide de balises](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="next-steps"></a>Étapes suivantes

Appliquez les classifications des données dans le cadre des guides de gouvernance exploitable.

> [!div class="nextstepaction"]
> [Choisissez un guide de gouvernance exploitable](../guides/index.md)
