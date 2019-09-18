---
title: 'Guide pour les entreprises standard : Améliorer la discipline Base de référence de la sécurité'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guide pour les entreprises standard : Améliorer la discipline Base de référence de la sécurité'
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a9b67b20f0f9169f5da7f941615612218ef29f94
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71031702"
---
# <a name="standard-enterprise-guide-improve-the-security-baseline-discipline"></a>Guide pour les entreprises standard : Améliorer la discipline Base de référence de la sécurité

Cet article fait progresser le scénario en ajoutant des contrôles de sécurité qui prennent en charge le déplacement des données protégées vers le cloud.

## <a name="advancing-the-narrative"></a>Développement du scénario

La direction du département informatique et celle de l’entreprise ont été satisfaites des résultats des premières expérimentations effectuées par les équipes chargées de l’informatique, du développement d’applications et du décisionnel. Pour tirer une valeur ajoutée tangible de ces expérimentations, ces équipes doivent être autorisées à intégrer des données protégées dans les solutions. Ceci induit des changements de stratégie des entreprises, mais nécessite également une amélioration incrémentielle des implémentations de la gouvernance du cloud avant que des données protégées puissent être placées dans le cloud.

### <a name="changes-to-the-cloud-governance-team"></a>Modifications apportées à l’équipe de gouvernance cloud

Étant donné l’effet du changement de scénario et de la prise en charge fournie jusqu’à présent, l’équipe de gouvernance cloud est maintenant vue différemment. Les deux administrateurs système qui ont démarré l’équipe sont maintenant vus comme des architectes cloud expérimentés. Au fil du développement de ce scénario, la perception de ces deux personnes va passer d’agents de maintenance du cloud à un rôle qui sera davantage celui de gardien du cloud.

Si cette différence est subtile, il s’agit néanmoins d’une distinction importante lors de l’élaboration d’une culture informatique centrée sur la gouvernance. Un agent de maintenance du cloud s’occupe de la remise en ordre rendue nécessaire par les actions innovantes des architectes cloud. Les deux rôles engendrent naturellement des frictions et ont des objectifs opposés. D’un autre côté, un gardien du cloud aide à conserver le cloud sécurisé, afin que d’autres architectes cloud puissent effectuer les migrations plus rapidement, avec moins de désordres. De plus, un gardien du cloud est impliqué dans la création de modèles qui en accélèrent le déploiement et l’adoption, ce qui en fait un accélérateur de l’innovation et un défenseur des cinq disciplines de la gouvernance cloud.

### <a name="changes-in-the-current-state"></a>Modifications apportées à l’état actuel

Au début de ce scénario, les équipes de développement d’applications travaillaient encore dans une optique de développement/test et l’équipe Décisionnel était encore en phase expérimentale. Le département informatique exploitait deux environnements d’infrastructure hébergés, nommés Prod (Production) et DR (Disaster Recovery, Reprise d’activité).

Depuis, certains changements ont eu lieu et ceux-ci vont avoir un impact sur la gouvernance :

- L’équipe de développement d’applications a implémenté un pipeline CI/CD pour déployer une application cloud native avec une expérience utilisateur améliorée. Cette application n’interagit pas encore avec les données protégées : elle n’est donc pas prête pour la production.
- Au sein du département informatique, l’équipe Décisionnel traite activement les données dans le cloud pour les aspects relatifs à la logistique, à l’inventaire et aux sources tierces. Ces données sont utilisées pour établir de nouvelles prédictions, qui peuvent modeler les processus de l’entreprise. Cependant, ces prédictions et ces insights ne sont pas exploitables tant que les données des clients et les données financières ne peuvent pas être intégrées à la plateforme de données.
- L’équipe informatique avance sur les plans du directeur informatique et du directeur financier pour mettre hors service le centre de données DR. Plus de 1 000 ressources sur les 2 000 du centre de données DR ont été mises hors service ou migrées.
- Les stratégies à l’origine peu contraignantes concernant les données personnelles et les données financières ont été modernisées. Cependant, les nouvelles stratégies d’entreprise sont déterminées par l’implémentation de stratégies de sécurité et de gouvernance associées. Les équipes restent donc bloquées.

### <a name="incrementally-improve-the-future-state"></a>Améliorer progressivement l’état futur

Les premières expérimentations effectuées par les équipes Développement d’applications et Décisionnel montrent des améliorations potentielles dans les expériences des clients et dans les décisions pilotées par les données. Les deux équipes veulent étendre l’adoption du cloud au cours des 18 prochains mois en déployant ces solutions en production.

Pendant les six mois restants, l’équipe gouvernance du cloud implémentera les exigences de sécurité et de gouvernance pour permettre aux équipes d’adoption du cloud de migrer les données protégées dans ces centres de données.

Les modifications apportées aux états actuel et futur exposent à de nouveaux risques qui nécessitent l’établissement de nouvelles stratégies.

## <a name="changes-in-tangible-risks"></a>Modifications apportées aux risques tangibles

**Violation des données :** L’adoption d’une nouvelle plateforme de données entraîne une augmentation inhérente des responsabilités liées à des violations potentielles des données. Les techniciens adoptant des technologies cloud ont des responsabilités plus grandes quant à l’implémentation de solutions pouvant réduire ce risque. Une stratégie de gouvernance et de sécurité robuste doit être implémentée pour garantir que ces techniciens prennent bien ces responsabilités.

Ce risque métier peut s’associer à quelques risques techniques :

1. Des applications critiques ou des données protégées peuvent être déployées par inadvertance.
2. Des données protégées peuvent être exposées lors du stockage en raison de mauvaises décisions quant au chiffrement.
3. Des utilisateurs non autorisés peuvent accéder à des données protégées.
4. Une intrusion depuis l’extérieur peut aboutir à l’accès à des données protégées.
5. Des intrusions depuis l’extérieur ou des attaques par déni de service peuvent conduire à une interruption de l’activité.
6. Des changements dans l’organisation ou dans le personnel peuvent rendre possibles des accès non autorisés à des données protégées.
7. L’exploitation de nouvelles failles de sécurité peut créer de nouvelles opportunités d’intrusion ou d’accès.
8. Des processus de déploiement incohérents peuvent entraîner des failles de sécurité pouvant être à l’origine de fuites de données ou d’interruptions.
9. Des changements de configuration ou des correctifs non appliqués peuvent entraîner des failles de sécurité pouvant être à l’origine de fuites de données ou d’interruptions.

## <a name="incremental-improvement-of-the-policy-statements"></a>Amélioration incrémentielle des instructions de stratégie

Les modifications suivantes apportées à la stratégie contribueront à traiter les nouveaux risques et à guider l’implémentation. La liste peut sembler longue, mais l’adoption de ces stratégies est plus simple qu’il n’y paraît.

1. Toutes les ressources déployées doivent être classées par criticité et par classification des données. Les classifications doivent être examinées par l’équipe de gouvernance cloud et le propriétaire de l’application avant le déploiement sur le cloud.
2. Les applications qui stockent des données protégées ou y accèdent doivent être gérées différemment des autres applications. Au minimum, elles doivent être segmentées de façon à éviter tout accès involontaire à des données protégées.
3. Toutes les données protégées doivent être chiffrées au repos.
4. Les autorisations avec élévation de privilèges dans les segments contenant des données protégées doivent être des exceptions. Ces exceptions seront validées avec l’équipe de gouvernance cloud et auditées régulièrement.
5. Les sous-réseaux de réseau qui contiennent des données protégées doivent être isolés de tous les autres sous-réseaux. Le trafic réseau entre les sous-réseaux de données protégées doit être audité régulièrement.
6. Aucun sous-réseau contenant des données protégées ne doit être accessible directement via l’Internet public ou entre les centres de données. L’accès à ces sous-réseaux doit être routé via des sous-réseaux intermédiaires. Tous les accès à ces sous-réseaux doivent transiter par une solution de pare-feu qui peut effectuer des analyses des paquets et mettre en œuvre des fonctions de blocage.
7. Les outils de gouvernance doivent auditer et appliquer les exigences de configuration réseau définies par l’équipe Gestion de la sécurité.
8. Les outils de gouvernance doivent limiter le déploiement des machines virtuelles seulement avec des images approuvées.
9. Quand c’est possible, la gestion de la configuration des nœuds doit appliquer les exigences de la stratégie à la configuration de tous les systèmes d’exploitation invités.
10. Les outils de gouvernance doivent veiller à ce que les mises à jour automatiques soient activées sur toutes les ressources déployées. Les violations doivent être examinées avec les équipes de gestion opérationnelle et corrigées conformément aux stratégies d’exploitation. Les ressources qui ne sont pas mises à jour automatiquement doivent être incluses dans les processus détenus par l’équipe responsable des opérations informatiques.
11. La création de nouveaux abonnements ou de groupes d’administration pour les applications critiques ou les données protégées nécessite un examen par l’équipe de gouvernance du cloud pour vérifier que le blueprint approprié est affecté.
12. Un modèle d’accès de moindre privilège doit être appliqué aux groupes d’administration ou aux abonnements qui contiennent des applications critiques ou des données protégées.
13. Les tendances et les attaques susceptibles d’affecter les déploiements cloud doivent être régulièrement examinées par l’équipe Sécurité de façon à fournir des mises à jour aux outils de gestion de la sécurité utilisés dans le cloud.
14. Les outils de déploiement doivent être approuvés par l’équipe de gouvernance cloud pour s’assurer de la gouvernance en continu des ressources déployées.
15. Les scripts de déploiement doivent être conservés dans un référentiel centralisé, accessible par l’équipe de gouvernance cloud pour effectuer des audits et des révisions périodiques.
16. Les processus de gouvernance doivent inclure des audits, à intervalles réguliers, au point de déploiement pour garantir la cohérence entre toutes les ressources.
17. Le déploiement des applications nécessitant une authentification des clients doit utiliser un fournisseur d’identité approuvé qui est compatible avec le fournisseur d’identité principal pour les utilisateurs internes.
18. Les processus de gouvernance du cloud doivent inclure des révisions trimestrielles avec les équipes de gestion des identités. Ces révisions peuvent aider à identifier les personnes malveillantes ou des modèles d’utilisation que la configuration des ressources cloud doit empêcher.

## <a name="incremental-improvement-of-governance-practices"></a>Amélioration incrémentielle des pratiques de gouvernance

Cette conception du produit minimum viable (MVP) de la gouvernance va changer de façon à inclure de nouvelles stratégies Azure ainsi qu’une implémentation d’Azure Cost Management. Ensemble, ces deux modifications de la conception permettront de répondre aux nouvelles instructions de la stratégie d’entreprise.

1. Les équipes Réseau et Sécurité informatique définissent la configuration réseau requise. L’équipe de gouvernance cloud prend en charge la conversion.
1. Les équipes Identité et Sécurité informatique définissent les exigences liées aux identités et apportent les modifications nécessaires à l’implémentation locale d’Active Directory. L’équipe de gouvernance cloud passe en revue les modifications.
1. Créez un référentiel dans Azure DevOps pour stocker et gérer les versions de tous les modèles Azure Resource Manager pertinents et des configurations utilisant des scripts.
1. Implémentation d’Azure Security Center :
    1. Configurez Azure Security Center pour les groupes d’administration qui contiennent des classifications de données protégées.
    1. Définissez le provisionnement automatique sur Activé par défaut pour garantir la conformité des mises à jour correctives.
    1. Établissez des configurations de sécurité des systèmes d’exploitation. L’équipe Sécurité informatique définit la configuration.
    1. Apportez un support à l’équipe Sécurité informatique pour l’utilisation initiale de Security Center. Confiez l’utilisation de Security Center à l’équipe Sécurité informatique, mais conservez un accès dans le but d’améliorer continuellement la gouvernance.
    1. Créez un modèle Resource Manager qui reflète les modifications nécessaires pour la configuration de Security Center au sein d’un abonnement.
1. Mettez à jour les stratégies Azure pour tous les abonnements :
    1. Auditez et appliquez la classification de la criticité et des données sur tous les groupes d’administration et tous les abonnements, de façon à identifier tous les abonnements avec des classifications de données protégées.
    1. Auditez et imposez l’utilisation exclusive d’images approuvées.
1. Mettez à jour les stratégies Azure pour tous les abonnements qui contiennent des classifications de données protégées :
    1. Auditez et imposez l’utilisation exclusive de rôles RBAC Azure standard.
    1. Auditez et imposez le chiffrement au repos pour tous les comptes de stockage et tous les fichiers sur les nœuds individuels.
    1. Auditez et imposez l’application d’un groupe de sécurité réseau à toutes les cartes réseau et à tous les sous-réseaux. Les équipes Réseau et Sécurité informatique définissent le groupe de sécurité réseau.
    1. Auditez et imposez l’utilisation d’un sous-réseau approuvé et d’une interface réseau par réseau virtuel.
    1. Auditez et imposez la limitation des tables de routage définies par l’utilisateur.
    1. Appliquez les stratégies intégrées pour la configuration des invités comme suit :
        1. Vérifiez que les serveurs web Windows utilisent des protocoles de communication sécurisés.
        1. Vérifiez que les paramètres de sécurité des mots de passe sont correctement définis dans les machines Linux et Windows.
1. Configuration du pare-feu :
    1. Identifiez une configuration de Pare-feu Azure qui répond aux exigences de sécurité nécessaires. Vous pouvez également identifier une appliance de tiers qui est compatible avec Azure.
    1. Créez un modèle Resource Manager pour déployer le pare-feu avec les configurations nécessaires.
1. Blueprint Azure :
    1. Créez un blueprint nommé `protected-data`.
    1. Ajoutez les modèles de pare-feu et Azure Security Center au blueprint.
    1. Ajoutez les nouvelles stratégies pour les abonnements de données protégées.
    1. Publiez le blueprint sur le groupe d’administration qui prévoit d’héberger des données protégées.
    1. Appliquez le nouveau blueprint à chaque abonnement affecté, en plus des blueprints existants.

## <a name="conclusion"></a>Conclusion

L’ajout des processus et des modifications ci-dessus au produit minimum viable pour la gouvernance permet de remédier à de nombreux risques associés à la gouvernance de la sécurité. Ensemble, ils ajoutent les outils de surveillance du réseau, des identités et de la sécurité nécessaires pour protéger les données.

## <a name="next-steps"></a>Étapes suivantes

À mesure que l’adoption du cloud se poursuit et offre davantage de valeur aux activités métier, les risques et les besoins en matière de gouvernance du cloud changent également. Pour la société fictive utilisée dans ce guide, l’étape suivante consiste à prendre en charge les charges de travail critiques. C’est ici que les contrôles de cohérence des ressources sont nécessaires.

> [!div class="nextstepaction"]
> [Amélioration de la cohérence des ressources](./resource-consistency-improvement.md)
