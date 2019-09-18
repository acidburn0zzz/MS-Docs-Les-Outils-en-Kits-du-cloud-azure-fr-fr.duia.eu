---
title: 'Guide de gouvernance pour les entreprises complexes : Améliorer la discipline Base de référence des identités'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guide de gouvernance pour les entreprises complexes : Améliorer la discipline Base de référence des identités'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/06/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 0c17f9043dd88f401b07293a6b93e50ccefe0137
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031911"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-identity-baseline-discipline"></a>Guide de gouvernance pour les entreprises complexes : Améliorer la discipline Base de référence des identités

Cet article fait progresser le scénario en ajoutant des contrôles de la Base de référence des identités au MVP de gouvernance.

## <a name="advancing-the-narrative"></a>Développement du scénario

La justification commerciale pour migrer les deux centres de données vers le cloud a été approuvée par le directeur financier. Lors de l’étude de faisabilité technique, plusieurs obstacles ont été identifiés :

- Les données protégées et les applications stratégiques représentent 25 % des charges de travail des deux centres de données. Aucune des deux ne peut être éliminée tant que les stratégies de gouvernance en vigueur concernant les données personnelles sensibles et les applications stratégiques n’ont pas été modernisées.
- Dans ces centres de données, 7 % des ressources ne sont pas compatibles avec le cloud. Elles seront déplacées vers un autre centre de données avant l’arrêt du contrat régissant le centre de données.
- 15 % des ressources du centre de données (750 machines virtuelles) présentent une dépendance à l’authentification héritée ou à l’authentification multifacteur proposée par des fournisseurs tiers.
- La connexion VPN entre les centres de données existants et Azure offre des vitesses de transmission des données et une latence insuffisantes pour migrer le volume de ressources dans un délai de deux ans avant de mettre le centre de données hors service.

Les deux premiers obstacles seront gérés en parallèle. Cet article porte sur la résolution des troisième et quatrième obstacles.

### <a name="expanding-the-cloud-governance-team"></a>Étoffement de l’équipe de gouvernance cloud

L’équipe de gouvernance cloud se développe. Étant donné l’accroissement du besoin de prise en charge en matière de gestion des identités, un administrateur des systèmes issu de l’équipe de base de référence des identités participe désormais à une réunion hebdomadaire afin d’informer les membres actuels de l’équipe sur les nouveautés.

### <a name="changes-in-the-current-state"></a>Modifications apportées à l’état actuel

L’équipe informatique est autorisée à mettre en œuvre les plans du directeur informatique et du directeur financier qui visent à mettre les deux centres de données hors service. Toutefois, le service informatique est préoccupé, car 750 ressources (15 % du total) de ces centres de données devront être déplacées ailleurs que dans le cloud.

### <a name="incrementally-improve-the-future-state"></a>Améliorer progressivement l’état futur

Les nouveaux plans relatifs à l’état futur requièrent une solution de base de référence des identités plus robuste afin de migrer les 750 machines virtuelles tout en conservant les exigences d’authentification héritées. Hormis pour ces deux centres de données, il est probable que ce même défi affecte un pourcentage semblable de ressources d’autres centres de données.

Désormais, l’état futur doit également bénéficier d’une connexion entre le fournisseur de cloud et la solution de l’entreprise (MPLS ou location de ligne).

Les modifications apportées aux états actuel et futur exposent à de nouveaux risques qui nécessiteront de nouvelles instructions de stratégie.

## <a name="changes-in-tangible-risks"></a>Modifications apportées aux risques tangibles

**Interruption des activités pendant la migration.** La migration vers le cloud crée un risque contrôlé et limité dans le temps qu’il est possible de gérer. Le déplacement de matériel vieillissant à l’autre bout du monde fait courir un risque bien plus élevé. Une stratégie d’atténuation des risques est nécessaire pour éviter les interruptions des activités.

**Dépendances d’identité existantes.** Les dépendances entre des services d’authentification et d’identité existants sont susceptibles de retarder ou d’empêcher la migration de certaines charges de travail vers le cloud. Si les deux centres de données ne peuvent pas être retournés à temps, les frais de location des centres de données s’élèveront à des millions de dollars.

Ce risque métier peut être lié à quelques risques techniques :

- Il se peut que l’authentification héritée ne soit pas disponible dans le cloud, limitant ainsi le déploiement de certaines applications.
- Il se peut que la solution d’authentification multifacteur tierce actuelle ne soit pas disponible dans le cloud, limitant ainsi le déploiement de certaines applications.
- Le réoutillage ou le déplacement peuvent entraîner des interruptions et générer des coûts supplémentaires.
- La vitesse et la stabilité de la connexion VPN risquent de compromettre la migration.
- Le trafic entrant dans le cloud peut entraîner des problèmes de sécurité dans d’autres parties du réseau global.

## <a name="incremental-improvement-of-the-policy-statements"></a>Amélioration incrémentielle des instructions de stratégie

Les modifications suivantes apportées à la stratégie contribueront à traiter les nouveaux risques et à guider l’implémentation.

- Le fournisseur de cloud choisi doit proposer un moyen d’authentification via des méthodes héritées.
- Le fournisseur de cloud choisi doit proposer un moyen d’authentification via la solution d’authentification multifacteur tierce actuelle.
- Une connexion privée à haute vitesse doit être établie entre le fournisseur de cloud et le fournisseur de télécommunications de l’entreprise. Cette connexion relie le fournisseur de cloud au réseau international de centres de données.
- Tant que des exigences de sécurité suffisantes ne sont pas établies, le trafic public entrant ne peut pas accéder aux ressources de l’entreprise qui sont hébergées dans le cloud. Tous les ports sont bloqués depuis n’importe quelle source en hors du réseau étendu global.

## <a name="incremental-improvement-of-the-best-practices"></a>Amélioration incrémentielle des bonnes pratiques

Cette conception du MVP de gouvernance change de façon à inclure de nouvelles stratégies Azure ainsi qu’une implémentation d’Active Directory sur une machine virtuelle. Ensemble, ces deux modifications de la conception permettent de répondre aux nouvelles instructions de la stratégie d’entreprise.

Voici les nouvelles meilleures pratiques :

- **Blueprint de réseau virtuel hybride sécurisé :** le côté local du réseau hybride doit être configuré de manière à autoriser la communication entre la solution suivante et les serveurs Active Directory locaux. Pour respecter cette meilleure pratique, la zone démilitarisée doit activer Active Directory Domain Services au-delà des limites du réseau.
- **Modèles Azure Resource Manager :**
    1. Définissez un groupe de sécurité réseau pour bloquer le trafic externe et autoriser le trafic interne.
    1. Déployez deux machines virtuelles Active Directory dans une paire à charge équilibrée basée sur une image finale (golden). Au premier démarrage, cette image exécute un script PowerShell pour joindre le domaine et s’inscrire auprès des services du domaine. Pour plus d’informations, consultez la page [Extension d’Active Directory Domain Services (AD DS) à Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adds-extend-domain).
- Azure Policy : Appliquez le groupe de sécurité réseau à toutes les ressources.
- Blueprint Azure :
    1. Créez un blueprint nommé `active-directory-virtual-machines`.
    1. Ajoutez chaque modèle et stratégie Active Directory au blueprint.
    1. Publiez le blueprint sur un groupe d’administration valable quelconque.
    1. Appliquez le blueprint à un abonnement quelconque exigeant l’authentification multifacteur tierce ou héritée.
    1. L’instance d’Active Directory qui est en cours d’exécution dans Azure est désormais utilisable en tant qu’extension de la solution Active Directory locale. Elle peut ainsi s’intégrer à l’outil d’authentification multifacteur existant et proposer l’authentification par revendication via des fonctionnalités Active Directory existantes.

## <a name="conclusion"></a>Conclusion

L’ajout de ces modifications au MVP de gouvernance permet de traiter bon nombre des risques évoqués dans cet article. Chaque équipe d’adoption du cloud peut alors rapidement dépasser ces obstacles.

## <a name="next-steps"></a>Étapes suivantes

À mesure que l’adoption du cloud se poursuit et offre davantage de valeur aux activités métier, les risques et les besoins en matière de gouvernance cloud changent également. Voici quelques changements susceptibles de se produire. Pour cette entreprise fictive, le prochain déclencheur consiste à inclure des données protégées dans le plan d’adoption du cloud. Cette modification exige de nouveaux contrôles de sécurité.

> [!div class="nextstepaction"]
> [Améliorer la discipline Base de référence de la sécurité](./security-baseline-improvement.md)
