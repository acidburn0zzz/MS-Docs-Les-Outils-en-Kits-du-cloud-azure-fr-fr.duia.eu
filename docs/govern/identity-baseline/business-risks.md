---
title: Risques d’affaires et motivations associés à la base de référence des identités
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Risques d’affaires et motivations associés à la base de référence des identités
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: e4203944d6ab5de891f637034d60381290a31c46
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222175"
---
# <a name="identity-baseline-motivations-and-business-risks"></a>Risques d’affaires et motivations associés à la base de référence des identités

Cet article décrit les raisons pour lesquelles les clients adoptent une discipline Base de référence des identités au sein d’une stratégie de gouvernance cloud. Des exemples sur les risques métier conduisant à la rédaction d’instructions de stratégie sont également présentés.

<!-- markdownlint-disable MD026 -->

## <a name="identity-baseline-relevancy"></a>Pertinence de la Base de référence des identités

Les répertoires locaux traditionnels sont conçus pour permettre aux entreprises de contrôler strictement les autorisations et les stratégies pour les utilisateurs, les groupes et les rôles au sein de leurs réseaux et centres de données internes. Il s’agit généralement du support d’implémentations à locataire unique, les services ne s’appliquant qu’au sein de l’environnement local.

Les services d’identité cloud étendent les capacités d’authentification et de contrôle d’accès d’une organisation à l’Internet. Ils prennent en charge la mutualisation et permettent de gérer les utilisateurs et les stratégies d’accès dans les applications et les déploiements cloud. Les plateformes de cloud public possèdent des services d’identité cloud natifs prenant en charge les tâches de gestion et de déploiement. Par ailleurs, elles offrent [différents niveaux d’intégration](../../decision-guides/identity/index.md) avec vos solutions d’identité locales existantes. Par rapport à la gestion des identités de vos solutions locales existantes, toutes ces fonctionnalités peuvent compliquer la stratégie d’identité cloud.

La discipline Base de référence des identités pour votre déploiement cloud s’avère particulièrement utile en fonction de la taille de votre équipe et de la nécessité d’intégrer votre solution d’identité basée sur le cloud à un service d’identité local existant. Les déploiements de tests initiaux peuvent ne pas nécessiter beaucoup d’organisation ou de gestion des utilisateurs, mais au fur et à mesure que votre investissement cloud se développe, vous devrez probablement prendre en charge une intégration organisationnelle et une gestion centralisée plus complexes.

## <a name="business-risk"></a>Risque métier

La discipline Base de référence des identités tente d’aborder les principaux risques métier liés aux services d’identité et au contrôle d’accès. Collaborez avec votre entreprise pour identifier ces risques et surveiller la pertinence de chacun d’entre eux lorsque vous planifiez et implémentez vos déploiements cloud.

Les risques diffèrent en fonction de l’organisation, mais ceux liés aux identités et présentés ci-dessous peuvent vous servir à initier des discussions au sein de votre équipe de gouvernance cloud :

- **Accès non autorisé.** Les données et ressources sensibles accessibles à des utilisateurs non autorisés peuvent entraîner des fuites de données ou des interruptions de service, enfreignant ainsi le périmètre de sécurité de votre entreprise et engageant votre responsabilité commerciale ou juridique.
- **Inefficacité en raison de plusieurs solutions d’identité.** Les organisations ayant des locataires de services d’identité multiples peuvent avoir besoin de plusieurs comptes pour les utilisateurs. Cette approche est contreproductive pour les utilisateurs qui doivent se souvenir de plusieurs jeux d’informations d’identification et pour le département informatique qui doit gérer des comptes sur plusieurs systèmes. Si les affectations d’accès des utilisateurs ne sont pas mises à jour dans l’ensemble des solutions d’identité à mesure que le personnel, les équipes et les objectifs commerciaux changent, vos ressources cloud peuvent devenir vulnérables aux accès non autorisés ou aux utilisateurs qui ne sont pas en mesure d’accéder aux ressources requises.
- **Impossibilité de partager des ressources avec des partenaires externes**. La difficulté d’ajouter des partenaires commerciaux externes à vos solutions d’identité existantes peut empêcher le partage efficace des ressources et la communication commerciale.
- **Dépendances d’identité locales.** Les mécanismes d’authentification hérités ou l’authentification multifacteur tierce partie peuvent ne pas être disponibles dans le cloud, ce qui nécessite soit de ré-outiller les charges de travail en cours de migration, soit de déployer des services d’identité supplémentaires dans le cloud. L’une ou l’autre de ces exigences peut retarder ou empêcher la migration et augmenter les coûts.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle Gestion de cloud](./template.md), documentez les risques métier susceptibles d’être introduits par le plan d’adoption du cloud actuel.

Une fois tous les risques métier réalistes appréhendés, l’étape suivante consiste à documenter la tolérance de l’activité aux risques, ainsi que les indicateurs et métriques clés permettant de surveiller cette tolérance.

> [!div class="nextstepaction"]
> [Comprendre les indicateurs, les métriques et la tolérance au risque](./metrics-tolerance.md)
