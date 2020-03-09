---
title: Métriques et indicateurs de tolérance au risque liée à la base de référence de la sécurité
description: Utilisez le Framework d’adoption du cloud pour Azure pour savoir comment quantifier la tolérance au risque métier liée à la base de référence de la sécurité.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5f85fd62f78b3be30faab452f12113790e6455d8
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77707337"
---
# <a name="security-baseline-metrics-indicators-and-risk-tolerance"></a>Métriques, indicateurs et tolérance au risque de la base de référence de sécurité

Cet article vous aide à quantifier la tolérance aux risques métier en lien avec la base de référence de sécurité. La définition de métriques et d’indicateurs vous aide à créer une étude d’opportunité pour investir dans la maturation de la discipline Base de référence de sécurité.

## <a name="metrics"></a>Mesures

La base de référence de sécurité se concentre généralement sur l’identification de potentielles vulnérabilités dans vos déploiements cloud. Dans le cadre de votre analyse des risques, vous allez collecter des données relatives à votre environnement de sécurité pour déterminer le risque auquel vous êtes exposé et l’importance d’investir dans la gouvernance de la base de référence de sécurité pour vos déploiements cloud planifiés.

Chaque organisation dispose de ses propres environnements et exigences de sécurité, ainsi que de ses propres sources potentielles de données de sécurité. Voici quelques exemples de métriques utiles que vous devez rassembler pour mieux évaluer la tolérance aux risques dans la discipline Base de référence de la sécurité :

- **Classification des données :** Nombre des données et services stockés dans le cloud qui ne sont pas classifiés selon les normes d’impact relatives à l’entreprise, la conformité et la confidentialité de l’organisation.
- **Nombre de magasins de données sensibles :** Nombre de points de terminaison ou bases de données de stockage qui contiennent des données sensibles et doivent être protégés.
- **Nombre de magasins de données non chiffrés :** Nombre de magasins de données sensibles qui ne sont pas chiffrés.
- **Surface d’attaque :** La quantité totale de source de données, services et applications qui seront hébergés sur le cloud. Parmi ces sources de données, quel pourcentage correspond aux données sensibles ? Quel pourcentage de ces applications et services sont critiques ?
- **Normes couvertes :** Nombre de normes de sécurité définies par l’équipe de sécurité.
- **Ressources couvertes :** Ressources déployées qui sont couvertes par les normes de sécurité.
- **Conformité aux normes globales :** Taux de conformité aux normes de sécurité.
- **Attaques par gravité :** À combien de tentatives coordonnées pour interrompre vos services hébergés sur le cloud, comme les attaques de déni de service distribué (DDoS), votre infrastructure doit-elle faire face ? Quelle est la taille et la gravité de ces attaques ?
- **Protection contre les programmes malveillants :** Pourcentage de machines virtuelles déployées qui disposent de tous les logiciels anti-programme malveillant, pare-feu ou autres logiciels de sécurité installés.
- **Latence des correctifs :** Quelle est la dernière fois où des correctifs logiciels ou de système d’exploitation ont été appliqués aux machines virtuelles.
- **Recommandations en matière d’intégrité de la sécurité :** Nombre de recommandations relatives aux logiciels de sécurité, organisées par niveau de gravité ; ces recommandations permettent de résoudre les normes d’intégrité pour les ressources déployées.

## <a name="risk-tolerance-indicators"></a>Indicateurs de tolérance au risque

Les plateformes cloud fournissent un ensemble de fonctionnalités de base qui permettent aux petites équipes de déploiement de configurer des paramètres de sécurité basiques sans avoir recours à une planification considérable. Par conséquent, les premières charges de travail de développement/test ou d’expérimentation qui n’incluent pas de données sensibles présentent un faible niveau de risque, et n’auront probablement pas besoin de beaucoup pour la mise en place d’une stratégie formelle Base de référence de sécurité. Toutefois, dès que des données importantes ou des fonctionnalités critiques sont déplacées sur le cloud, les risques de sécurité augmentent, et la tolérance à ces risques diminue rapidement. Plus vos données et vos fonctionnalités sont déployées sur le cloud, plus vous avez besoin d’investir dans la discipline Base de référence de sécurité.

Au début de l’adoption du cloud, collaborez avec votre équipe Sécurité informatique et les parties prenantes de l’entreprise pour identifier les [risques métier](./business-risks.md) liés à l’identité, puis déterminez une base de référence acceptable pour la tolérance au risque de sécurité. Cette section du Framework d’adoption du cloud fournit des exemples, mais les risques et les bases de référence détaillés pour votre entreprise ou vos déploiements peuvent être différents.

Une fois que vous avez une base de référence, établissez des seuils minimaux représentant une augmentation inacceptable de vos risques identifiés. Ces seuils font office de déclencheurs lorsque vous devez prendre des mesures pour corriger ces risques. Voici quelques exemples montrant comment des métriques de sécurité, comme celles décrites ci-dessus, peuvent justifier un investissement accru dans la discipline Base de référence de sécurité.

- **Déclencheur de charges de travail critiques.** Une entreprise déployant des charges de travail critiques dans le cloud doit investir dans la discipline Base de référence de sécurité pour empêcher toute interruption de service ou exposition des données sensibles.
- **Déclencheur de données protégées.** Une entreprise qui héberge dans le cloud des données pouvant être classifiées comme confidentielles, privées ou sujettes à d’autres problématiques réglementaires. Cette entreprise a besoin d’une discipline Base de référence de sécurité pour s’assurer que ces données ne seront pas perdues, exposées ou volées.
- **Déclencheur d’attaques externes.** Une entreprise qui subit des attaques graves envers son infrastructure réseau _X_ fois par mois peut tirer profit de la discipline Base de référence de sécurité.
- **Déclencheur de conformité aux normes.** Une entreprise disposant de plus de _X_ % de ressources non conformes aux normes de sécurité doit investir dans la discipline Base de référence de sécurité pour s’assurer que les normes sont appliquées de manière homogène dans toute l’infrastructure informatique.
- **Déclencheur de taille de parc cloud.** Une entreprise hébergeant plus de _X_ applications, services et sources de données. Les larges déploiements cloud tirent profit de l’investissement dans la discipline Base de référence de sécurité, car ils peuvent s’assurer que l’ensemble de la surface d’attaque est protégée correctement contre les accès non autorisés et autres menaces.
- **Déclencheur de conformité des logiciels de sécurité.** Une entreprise dans laquelle moins de _X_ % des machines virtuelles déployées disposent de tous les logiciels de sécurité requis installés. Une discipline Base de référence de sécurité peut être utilisée pour s’assurer que les logiciels sont installés de manière homogène sur toutes les machines virtuelles.
- **Déclencheur de l’application de correctifs.** Une entreprise dans laquelle l’application de correctifs logiciels ou SE n’a pas été effectuée sur les services ou machines virtuelles déployés depuis _X_ jours. Une discipline Base de référence de sécurité peut être utilisée pour s’assurer que l’application de correctifs est effectuée selon la planification requise.
- **Axée sur la sécurité.** Certaines entreprises imposent des exigences strictes en matière de confidentialité des données et de sécurité, même pour les charges de travail de test et expérimentales. Ces entreprises doivent investir dans la discipline Base de référence de sécurité avant que tout déploiement puisse être effectué.

Les métriques et déclencheurs exacts à utiliser pour évaluer la tolérance au risque, et le niveau d’investissement dans la discipline Base de référence de sécurité sont spécifiques à votre organisation, mais les exemples ci-dessus devraient constituer une base utile pour la discussion au sein de votre équipe de gouvernance cloud.

## <a name="next-steps"></a>Étapes suivantes

À l’aide du [modèle de gestion cloud ](./template.md), documenter les métriques et les indicateurs de tolérance correspondant au plan d’adoption du cloud actuel.

Considérez les exemples de stratégies de base de référence de la sécurité comme des points de départ permettant de développer des stratégies qui répondent à des risques métier spécifiques, dans la continuité de vos plans d’adoption du cloud.

> [!div class="nextstepaction"]
> [Examiner les exemples de stratégies](./policy-statements.md)
