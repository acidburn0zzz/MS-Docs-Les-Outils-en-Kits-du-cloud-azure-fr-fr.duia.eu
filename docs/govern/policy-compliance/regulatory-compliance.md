---
title: Présentation de la conformité réglementaire
description: Découvrez les règles de conformité en vigueur dans divers secteurs d’activité et zones géographiques qui sont susceptibles d’affecter la gouvernance cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 22e74aabc56ae25d0448bf321c645449e4989668
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80809128"
---
# <a name="introduction-to-regulatory-compliance"></a>Présentation de la conformité réglementaire

Il s’agit d’un article introductif sur la conformité réglementaire. Il ne vise donc pas l’implémentation d’une stratégie de conformité. Des informations plus détaillées sur les [offres de conformité Azure](https://aka.ms/allcompliance) sont disponibles dans le [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trust-center). En outre, toute la documentation téléchargeable est disponible à certains clients Azure sur le [portail d’approbation de services Microsoft](https://servicetrust.microsoft.com).

La conformité réglementaire fait référence à la discipline et au processus consistant à garantir qu’une entreprise respecte les lois appliquées par les organes directeurs dans sa zone géographique ou les lois imposées par les normes du secteur volontairement adoptées. Pour la conformité réglementaire informatique, les personnes et les processus supervisent les systèmes de l’entreprise dans le but de détecter et d’empêcher les violations de stratégies et de procédures établies par ces lois, règlements et normes en vigueur. Cette notion concerne une un large éventail de processus d’application et de supervision. En fonction du secteur et de la zone géographique, ces processus peuvent être longs et complexes.

La conformité peut être difficile pour les organisations multinationales, en particulier dans des secteurs fortement réglementés, comme les services de santé et financiers. Les normes et réglementations abondent et, dans certains cas, peuvent changer régulièrement. Il est donc difficile pour les entreprises de suivre les changements des lois internationales sur le traitement des données électroniques.

Comme avec les contrôles de sécurité, les organisations doivent comprendre la répartition des responsabilités en matière de conformité réglementaire dans le cloud. Les fournisseurs de cloud mettent tout en œuvre pour que leurs plateformes et leurs services soient conformes. Toutefois, les organisations doivent également vérifier que leurs applications, l’infrastructure dont dépendent ces applications et les services fournis par des tiers sont également certifiés comme conformes.

Voici des descriptions de règles de conformité dans divers secteurs et zones géographiques :

## <a name="hipaa"></a>HIPAA

Une application de santé qui traite des informations PHI (Protected Health Information, ou informations de santé protégées) doit respecter les règles de confidentialité et les règles de sécurité édictées par la loi Health Information Portability and Accountability Act (HIPAA). Au minimum, la loi HIPAA peut exiger qu’un établissement de soins de santé recevoir impérativement par écrit une garantie du fournisseur de cloud indiquant que les données PHI reçues ou créées seront protégées.

## <a name="pci"></a>PCI

La norme de sécurité de l’industrie des cartes de paiement (PCI DSS) concerne les informations propriétaires pour les organisations, lorsque celles-ci traitent les cartes de crédit venant des grands systèmes de carte comme Visa, MasterCard, American Express, Discover et JCB. La norme PCI est mandatée par les sociétés de carte de paiement, et administrée par le Payment Card Industry Security Standards Council. La norme a été créée pour augmenter les contrôles sur les données des titulaires de carte, et ainsi réduire les fraudes. La validation de la conformité est effectuée tous les ans par un Qualified Security Assessor (QSA) externe ou un Internal Security Assessor (ISA) spécifique à la firme. Il crée alors un Report on Compliance (ROC, ou rapport sur la conformité) pour les organisations traitant de larges volumes de transactions. Pour les entreprises, cette validation est effectuée par un Self-Assessment Questionnaire (SAQ).

## <a name="personal-data"></a>Données à caractère personnel

Les données personnelles sont des informations qui peuvent être utilisées pour identifier un consommateur, un employé, un partenaire ou toute autre entité légale ou vivante. Beaucoup de nouvelles lois, surtout celles liées à la confidentialité et aux données personnelles, exigent que les entreprises elles-mêmes se conforment aux normes, le prouvent, et signalent les violations qui se produisent.

## <a name="gdpr"></a>RGPD

Un des développements les plus importants dans ce sens est le Règlement général sur la protection des données (RGPD). Celui-ci a été conçu pour renforcer la protection des données pour les personnes au sein de l’Union européenne. Le RGPD exige que les données concernant les personnes (comme « un nom, une adresse postale, une photo, une adresse e-mail, des coordonnées bancaires, des publications sur des réseaux sociaux, des informations médicales ou l’adresse IP d’un ordinateur ») restent sur des serveurs au sein de l’UE et ne soient pas transférées hors de celle-ci. Il exige également que les entreprises informent les personnes en cas de violations des données, et engagent un délégué à la protection des données (DPD). D’autres pays ont développé des réglementations semblables, ou sont en train de le faire.

## <a name="compliant-foundation-in-azure"></a>Conformité dans Azure

Pour aider les clients à répondre à leurs propres obligations en matière de conformité dans les industries et sur les marchés réglementés du monde entier, Azure gère la plus grande gamme de solutions de conformité du secteur, aussi bien en termes de largeur (nombre total d’offres) et de profondeur (nombre de services B2C dans l’étendue d’évaluation). Les offres de conformité Azure sont regroupées dans quatre segments : applicables globalement, gouvernement des États-Unis, propres à un secteur d’activité, et propres à une région ou un pays.

Les offres de conformité Azure sont basées sur divers types de garanties, notamment des certifications, attestations, validations, autorisations et évaluations officielles créées par des sociétés d’audit tierces indépendantes, ainsi que des modifications contractuelles, des auto-évaluations et des documents de conseils pour les clients créés par Microsoft. Chaque description d’offre de ce document fournit une instruction mise à jour indiquant quels services Azure orientés client se trouvent dans le champ d’application de l’évaluation, et donne des liens vers des ressources téléchargeables pour aider les clients à gérer leurs obligations en matière de conformité.

Le centre de gestion de la confidentialité Microsoft fournit des informations plus détaillées sur les [offres de conformité Azure](https://www.microsoft.com/trust-center/compliance/compliance-overview). En outre, toute la documentation téléchargeable est disponible à certains clients Azure sur le [portail d’approbation de services](https://servicetrust.microsoft.com) dans les sections suivantes :

- **Rapports d’audit :** Comprend les sections relatives aux rapports FedRAMP, d’évaluation GRC, ISO, PCI DSS et SOC.
- **Ressources de protection des données :** Inclut des guides de conformité, des questions fréquentes (FAQ), des livres blancs, ainsi que des sections sur les tests d’intrusion et les évaluations de sécurité.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur la préparation de la sécurité du cloud.

> [!div class="nextstepaction"]
> [Préparation de la sécurité du cloud](./cloud-security-readiness.md)
