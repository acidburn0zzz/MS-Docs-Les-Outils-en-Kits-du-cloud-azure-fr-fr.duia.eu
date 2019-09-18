---
title: Recommandations en matière de sécurité Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Quelles sont les recommandations formulées par Microsoft en matière de sécurité ?
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6a4b256c665e0f4a86bca5a538de9ae950ccd400
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71032124"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-security-guidance-does-microsoft-provide"></a>Quelles sont les recommandations formulées par Microsoft en matière de sécurité ?

## <a name="security-guidance-and-tools"></a>Conseils de sécurité et outils

Microsoft a introduit la [Plateforme d'approbation de services](https://servicetrust.microsoft.com) et le Gestionnaire de conformité pour faciliter ce qui suit :

- Surmonter les défis en matière de gestion de la conformité.
- Satisfaire aux exigences réglementaires.
- Réaliser des audits et des évaluations des risques en libre service liés à l’utilisation de services cloud d’entreprise.

Ces outils sont conçus pour aider les organisations à répondre aux obligations complexes de conformité et à améliorer les fonctionnalités de protection des données lors du choix et de l'utilisation de services de cloud computing Microsoft.

La **Plateforme d'approbation de services (STP)** fournit des informations détaillées et des outils pour répondre à vos besoins d'utilisation de services de cloud computing Microsoft, notamment Azure, Office 365, Dynamics 365 et Windows. La STP rassemble les informations relatives à la sécurité, la réglementation, la conformité et la confidentialité ayant trait à Microsoft Cloud. C’est là que nous publions les informations et les ressources nécessaires à la réalisation d'évaluations des risques en libre-service des services et outils cloud. La STP a été créée pour faciliter le suivi des activités de conformité réglementaire au sein d'Azure, notamment :

- **Gestionnaire de conformité** : Le Gestionnaire de conformité, un outil d'évaluation des risques basé sur les flux de travail dans la Plateforme d'approbation de services Microsoft, vous permet de suivre, d'affecter et de vérifier les activités de conformité réglementaire de votre organisation ayant trait aux services de cloud computing Microsoft, tels que Dynamics 365, Office 365 et Azure. Pour plus d’informations, consultez la section suivante.
- **Documents de test** : Actuellement, il existe trois catégories de guides qui vous fournissent de nombreuses ressources afin d’évaluer Microsoft Cloud. Ces ressources vous permettre d'en savoir plus sur les opérations de Microsoft en matière de sécurité, de conformité et de confidentialité et vous aident à améliorer les fonctionnalités de protection de vos données. Il s’agit des actions suivantes :
- **Rapports d’audit :** Les rapports d'audit vous permettent de vous tenir informé des dernières informations relatives à la confidentialité, à la sécurité et à la conformité liées aux services de cloud computing Microsoft. Cela englobe notamment des rapports d'audit ISO, SOC, FedRAMP, des lettres d'accompagnement et des documents relatifs aux audits tiers indépendants des services de cloud computing Microsoft tels que Dynamics 365, Azure, Office 365, etc.
- **Guides de protection des données** : Les guides de protection des données fournissent des informations sur la manière dont les services de cloud computing Microsoft protègent vos données, ainsi que sur la manière dont vous gérez la sécurité et la conformité des données cloud de votre entreprise. Il s'agit notamment de livres blancs détaillés qui expliquent comment Microsoft conçoit et exploite les services cloud, de FAQ, de rapports d’évaluations de sécurité de fin d’année, de résultats de tests de pénétration et de recommandations pour vous aider à évaluer les risques et à améliorer les fonctionnalités de protection de vos données.
- **Blueprint de sécurité et de conformité Azure** : Les blueprints fournissent des ressources pour vous aider à créer et à lancer des applications cloud qui vous aident à vous conformer aux réglementations et normes strictes. Avec plus de certifications que tout autre fournisseur de cloud, vous pouvez déployer en toute confiance vos charges de travail critiques sur Azure, avec des blueprints comprenant :
  - Vue d'ensemble et des recommandations spécifiques au secteur.
  - Matrice de responsabilités des clients.
  - Architectures de référence avec modèles de menaces.
  - Matrices de mise en œuvre des contrôles.
  - Automatisation pour déployer des architectures de référence.
  - Ressources liées à la confidentialité : la documentation relative aux évaluations d'impact sur la protection des données, aux requêtes DSR (droits de la personne concernée) et à la notification de violation de données est fournie pour être incorporée dans votre propre programme de responsabilité dans le cadre du Règlement général sur la protection des données (RGPD).
- **Premiers pas avec le RGPD** : Les produits et services Microsoft aident les organisations à répondre aux exigences du RGPD lors de la collecte ou du traitement de données personnelles. La STP est conçue pour vous fournir des informations sur les fonctionnalités des services Microsoft que vous pouvez utiliser pour répondre aux exigences spécifiques du RGPD. Cette documentation améliore votre responsabilité RGPD et votre compréhension des mesures techniques et organisationnelles. La documentation relative aux évaluations d'impact sur la protection des données, aux requêtes DSR (droits de la personne concernée) et à la notification de violation de données est fournie pour être incorporée dans votre propre programme de responsabilité dans le cadre du RGPD.
  - **Demandes des personnes concernées** : Le RGPD accorde aux particuliers (ou personnes concernées) certains droits en rapport avec le traitement de leurs données personnelles. Ils peuvent notamment corriger des données inexactes, effacer des données ou limiter leur traitement, ainsi que recevoir leurs données et formuler une demande de transmission de ces données à un autre contrôleur.
  - **Violation des données :** Le RGPD impose des exigences de notification pour les contrôleurs et responsables du traitement des données en cas de violation des données personnelles. La STP vous fournit des informations sur la manière dont Microsoft s'efforce de prévenir les violations, détecte une violation, y réagit et vous en informe en tant que contrôleur de données.
  - **Évaluation de l'impact de la protection des données :** Microsoft aide les contrôleurs à effectuer des évaluations d'impact sur la protection des données RGPD. Le RGPD fournit une liste exhaustive de situations dans lesquelles des évaluations d'impact sur la protection des données (DPIA) s'imposent, comme le traitement automatique à des fins de profilage et activités similaires, le traitement à grande échelle de catégories spécifiques de données à caractère personnel et la surveillance systématique à grande échelle d'une zone accessible au public.
  - **Autres ressources** : En plus des recommandations relatives aux outils décrits dans les sections ci-dessus, la STP fournit également d'autres ressources, comprenant notamment des ressources de conformité régionale, des ressources supplémentaires pour le Centre de sécurité et de conformité, ainsi que des questions fréquemment posées sur la Plateforme d'approbation de services, le Gestionnaire de conformité et la confidentialité /RGPD.
- **Conformité régionale** : La STP fournit de nombreux documents de conformité et recommandations liés aux services en ligne Microsoft pour répondre aux exigences de conformité de différentes régions, y compris la République tchèque, la Pologne et la Roumanie.

## <a name="unique-intelligent-insights"></a>Intelligent Insights

Au fur et à mesure que le volume et la complexité des signaux de sécurité augmentent, il apparaît bien trop long de déterminer si ces signaux constituent des menaces crédibles, puis d'agir. Microsoft propose un éventail inégalé d'informations de sécurité fournies à l'échelle du cloud pour mieux détecter les menaces et y remédier.

## <a name="azure-threat-intelligence"></a>Informations sur les menaces Azure

Grâce à l’option Informations sur les menaces disponible dans Security Center, les administrateurs informatiques peuvent détecter les menaces de sécurité pour l’environnement. Par exemple, ils peuvent déterminer si un ordinateur particulier fait partie d’un botnet. Un ordinateur peut devenir un nœud d’un botnet si un pirate installe de manière illicite un programme malveillant qui connecte secrètement l’ordinateur à la commande et au contrôle. Les informations sur les menaces peuvent également identifier les menaces potentielles provenant de canaux de communication obscurs, tel que le dark web.

Pour générer ces informations sur les menaces, Security Center utilise des données provenant de nombreuses sources au sein de Microsoft. Security Center utilise ces données afin d’identifier les menaces potentielles pour votre environnement. Le volet Informations sur les menaces est composé de trois options principales :

- Detected threat types (Types de menaces détectés)
- Origine de la menace
- Threat intelligence map (Carte d’informations sur les menaces)

## <a name="machine-learning-in-azure-security-center"></a>Machine Learning dans Azure Security Center

Azure Security Center analyse en profondeur une multitude de données provenant de diverses solutions Microsoft et partenaires pour vous aider à renforcer la sécurité. Pour tirer parti de ces données, l'entreprise a recours à la science des données et au Machine Learning à des fins de prévention, de détection et d'examen des menaces.

Globalement, Azure Machine Learning permet d’atteindre deux résultats :

## <a name="next-generation-detection"></a>Détection de nouvelle génération

Les attaquants sont de plus en plus automatisés et sophistiqués. Ils ont également recours à la science des données. Ils reconstituent la logique des protections et construisent des systèmes qui prennent en charge les mutations de comportement. Ils masquent leurs activités en bruit et tirent des enseignements rapides de leurs erreurs. Le Machine Learning nous permet de répondre à ces évolutions.

## <a name="simplified-security-baseline"></a>Base de référence de la sécurité simplifiée

En matière de sécurité, il n'est pas toujours facile de prendre des décisions efficaces. Cela requiert savoir-faire et expérience. Si certaines grandes entreprises disposent d'experts en la matière, beaucoup en sont dépourvues. Azure Machine Learning permet aux clients de tirer parti du savoir-faire d'autres entreprises pour prendre les décisions de sécurité qui s'imposent.

## <a name="behavioral-analytics"></a>Analyse comportementale

L’analyse comportementale est une technique qui analyse et compare les données à une collection de modèles connus. Toutefois, ces modèles ne sont pas de simples signatures. Ils sont déterminés par le biais d’algorithmes d’apprentissage automatique appliqués aux ensembles de données massifs. Ils sont également déterminés à travers une analyse minutieuse des comportements malveillants par des experts. Azure Security Center peut utiliser l’analyse comportementale pour identifier les ressources compromises en se basant sur l’analyse des journaux d’activité de la machine virtuelle, des journaux d’activité du périphérique réseau virtuel, des journaux d’activité Service Fabric, des vidages sur incident et d’autres sources.
