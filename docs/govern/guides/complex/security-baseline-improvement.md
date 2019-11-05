---
title: 'Guide de gouvernance pour les entreprises complexes : Améliorer la discipline Base de référence de la sécurité'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guide de gouvernance pour les entreprises complexes : Améliorer la discipline Base de référence de la sécurité'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 075d587b60b7da1748cd6d06ce01a1a5866f8304
ms.sourcegitcommit: e0a783dac15bc4c41a2f4ae48e1e89bc2dc272b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73058121"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-security-baseline-discipline"></a>Guide de gouvernance pour les entreprises complexes : Améliorer la discipline Base de référence de la sécurité

Cet article fait progresser le scénario en ajoutant des contrôles de sécurité qui prennent en charge le déplacement des données protégées vers le cloud.

## <a name="advancing-the-narrative"></a>Développement du scénario

Durant des mois, le directeur informatique a collaboré avec ses collègues et le service juridique de l'entreprise. Un consultant spécialisé en cybersécurité a été engagé pour aider les équipes de sécurité informatique et de gouvernance informatique existantes à rédiger une nouvelle stratégie en matière de données protégées. Le groupe a convaincu le conseil d’administration de remplacer la stratégie existante, ce qui a permis à des fournisseurs cloud approuvés d’héberger des données financières et personnelles sensibles. Cela a nécessité l'adoption d'un ensemble d'exigences de sécurité et d'un processus de gouvernance afin de vérifier et de documenter l'adhésion à ces stratégies.

Au cours des 12 derniers mois, les équipes d'adoption du cloud ont effacé la plupart des 5 000 ressources des deux centres de données qui seront mis hors service. Les 350 ressources incompatibles ont été déplacées vers un autre centre de données. Seules les 1 250 machines virtuelles contenant des données protégées ont été conservées.

### <a name="changes-in-the-cloud-governance-team"></a>Modifications apportées à l’équipe de gouvernance cloud

L’équipe de gouvernance cloud continue de se transformer au fil du scénario. Les deux membres fondateurs de l’équipe comptent désormais parmi les architectes cloud les plus respectés de l'entreprise. La collection de scripts de configuration s'est étoffée au fil des déploiements innovants réalisés par les nouvelles équipes. L’équipe de gouvernance cloud s’est également étoffée. Récemment, des membres de l’équipe des opérations informatiques ont participé aux activités de l’équipe de gouvernance cloud dans l’optique de préparer les opérations cloud. Les architectes cloud qui ont encouragé cette communauté sont perçus en tant que gardiens et accélérateurs du cloud.

Si cette différence est subtile, il s’agit néanmoins d’une distinction importante lors de l’élaboration d’une culture informatique centrée sur la gouvernance. Un gardien du cloud s’occupe de la remise en ordre rendue nécessaire par les actions innovantes des architectes cloud, et les deux rôles engendrent naturellement des frictions et ont des objectifs opposés. Un gardien du cloud aide à conserver le cloud sécurisé, afin que d’autres architectes cloud puissent effectuer les migrations plus rapidement, avec moins de désordres. Un accélérateur de cloud remplit deux fonctions, mais participe également à la création de modèles qui en accélèrent le déploiement et l’adoption, ce qui en fait un accélérateur de l’innovation et un défenseur des cinq disciplines de la gouvernance cloud.

### <a name="changes-in-the-current-state"></a>Modifications apportées à l’état actuel

Dans la phase précédente de ce scénario, l'entreprise s'était attelée au processus de mise hors service de deux centres de données. Cet effort continu passe par la migration de plusieurs applications présentant des exigences d’authentification héritée, ce qui a nécessité l’apport d’améliorations incrémentielles à la base de référence des identités, et qui est décrite dans le [précédent article](./identity-baseline-improvement.md).

Depuis, certains changements ont eu lieu et ceux-ci vont avoir un impact sur la gouvernance :

- Des milliers de ressources informatiques et d'entreprise ont été déployées dans le cloud.
- L’équipe de développement d’applications a implémenté un pipeline d’intégration et déploiement continus (CI/CD) pour déployer une application cloud native avec une expérience utilisateur améliorée. Cette application n’interagit pas encore avec les données protégées : elle n’est donc pas prête pour la production.
- Au sein du département informatique, l’équipe Décisionnel traite activement les données dans le cloud pour les aspects relatifs à la logistique, à l’inventaire et aux données tierces. Ces données sont utilisées pour établir de nouvelles prédictions, qui peuvent modeler les processus de l’entreprise. Cependant, ces prédictions et ces insights ne sont pas exploitables tant que les données des clients et les données financières ne peuvent pas être intégrées à la plateforme de données.
- L’équipe informatique avance sur les plans du directeur informatique et du directeur financier pour mettre hors service deux centres de données. Près de 3 500 ressources des deux centres de données ont fait l'objet d'une mise hors service ou d'une migration.
- Les stratégies concernant les données financières et personnelles sensibles ont été modernisées. Cependant, les nouvelles stratégies d’entreprise sont déterminées par l’implémentation de stratégies de sécurité et de gouvernance associées. Les équipes restent donc bloquées.

### <a name="incrementally-improve-the-future-state"></a>Améliorer progressivement l’état futur

- Les premières expérimentations effectuées par les équipes Développement d’applications et Décisionnel montrent des améliorations potentielles dans les expériences des clients et dans les décisions pilotées par les données. Les deux équipes souhaiteraient étendre l’adoption du cloud au cours des 18 prochains mois en déployant ces solutions en production.
- Le service informatique a mis au point une justification professionnelle visant à migrer cinq autres centres de données vers Azure afin de réduire les coûts informatiques et d'offrir une plus grande agilité opérationnelle. Bien que de moindre envergure, la mise hors service de ces centres de données devrait doubler les économies totales réalisées.
- Les budgets liés aux dépenses d’investissement et de fonctionnement ont autorisé l’implémentation des stratégies, outils et processus nécessaires en matière de sécurité et de gouvernance. La réduction des coûts escomptée suite à la mise hors service des centres de données suffit amplement à financer cette nouvelle initiative. Les responsables informatiques et commerciaux sont convaincus que cet investissement portera également ses fruits dans d'autres . L’équipe de gouvernance cloud d’origine est devenue une équipe reconnue, dotée d’un leadership et d’un personnel dédiés.
- Ensemble, les équipes d’adoption cloud, l’équipe de gouvernance cloud, l’équipe de sécurité informatique et l’équipe de gouvernance informatique implémenteront les exigences de sécurité et de gouvernance pour permettre aux équipes d’adoption du cloud de migrer les données protégées dans le cloud.

## <a name="changes-in-tangible-risks"></a>Modifications apportées aux risques tangibles

**Violation des données :** L’adoption d’une nouvelle plateforme de données entraîne une augmentation inhérente des responsabilités liées à des violations potentielles des données. Les techniciens adoptant des technologies cloud ont des responsabilités plus grandes quant à l’implémentation de solutions pouvant réduire ce risque. Une stratégie de gouvernance et de sécurité robuste doit être implémentée pour garantir que ces techniciens prennent bien ces responsabilités.

Ce risque métier peut être lié à plusieurs risques techniques :

1. Des applications critiques ou des données protégées peuvent être déployées par inadvertance.
2. Des données protégées peuvent être exposées lors du stockage en raison de mauvaises décisions quant au chiffrement.
3. Des utilisateurs non autorisés peuvent accéder à des données protégées.
4. Une intrusion depuis l’extérieur peut aboutir à l’accès à des données protégées.
5. Des intrusions externes ou des attaques par déni de service peuvent conduire à une interruption de l’activité.
6. Des changements dans l’organisation ou dans le personnel peuvent rendre possibles des accès non autorisés à des données protégées.
7. L’exploitation de nouvelles failles de sécurité peut créer de nouvelles opportunités d’intrusion ou d’accès non autorisé.
8. Des processus de déploiement incohérents peuvent entraîner des failles de sécurité susceptibles de provoquer des fuites de données ou des interruptions.
9. Des changements de configuration ou des correctifs manqués peuvent entraîner des failles de sécurité susceptibles de provoquer des fuites de données ou des interruptions.
10. Des appareils de périmètre disparates peuvent augmenter les coûts d’exploitation réseau.
11. Des configurations d’appareils disparates peuvent entraîner des oublis de configuration et des compromis de sécurité.
12. L'équipe de cybersécurité insiste sur le fait qu'il existe un risque de dépendance vis-à-vis d'un fournisseur en cas de génération de clés de chiffrement sur une seule plateforme de fournisseur de cloud. Bien que cela ne soit pas confirmé, l'équipe a pour l'instant retenu cette possibilité.

## <a name="incremental-improvement-of-the-policy-statements"></a>Amélioration incrémentielle des instructions de stratégie

Les modifications suivantes apportées à la stratégie contribueront à traiter les nouveaux risques et à guider l’implémentation. La liste peut sembler longue, mais l’adoption de ces stratégies est plus simple qu’il n’y paraît.

1. Toutes les ressources déployées doivent être classées par criticité et par classification des données. Les classifications doivent être examinées par l’équipe de gouvernance cloud, et l’application avant le déploiement sur le cloud.
2. Les applications qui stockent des données protégées ou y accèdent doivent être gérées différemment des autres applications. Au minimum, elles doivent être segmentées de façon à éviter tout accès involontaire à des données protégées.
3. Toutes les données protégées doivent être chiffrées au repos.
4. Les autorisations avec élévation de privilèges dans les segments contenant des données protégées doivent être des exceptions. Ces exceptions seront validées avec l’équipe de gouvernance cloud et auditées régulièrement.
5. Les sous-réseaux de réseau qui contiennent des données protégées doivent être isolés de tous les autres sous-réseaux. Le trafic réseau entre les sous-réseaux de données protégées doit être audité régulièrement.
6. Aucun sous-réseau contenant des données protégées ne doit être accessible directement via l’Internet public ou entre les centres de données. L’accès à ces sous-réseaux doit être routé via des sous-réseaux intermédiaires. Tous les accès à ces sous-réseaux doivent transiter par une solution de pare-feu capable d’effectuer des analyses de paquets et de mettre en œuvre des fonctions de blocage.
7. Les outils de gouvernance doivent auditer et appliquer les exigences de configuration réseau définies par l’équipe de gestion de la sécurité.
8. Les outils de gouvernance doivent limiter le déploiement des machines virtuelles seulement avec des images approuvées.
9. Quand c’est possible, la gestion de la configuration des nœuds doit appliquer les exigences de la stratégie à la configuration de tous les systèmes d’exploitation invités. La gestion de la configuration des nœuds doit respecter l'investissement existant dans l'objet de stratégie de groupe en termes de configuration des ressources.
10. Les outils de gouvernance s'assureront que les mises à jour automatiques soient activées sur toutes les ressources déployées. Dans la mesure du possible, des mises à jour automatiques seront appliquées. Les violations au niveau du nœud doivent être examinées avec les équipes de gestion opérationnelle et corrigées conformément aux stratégies d’exploitation. Les ressources qui ne sont pas mises à jour automatiquement doivent être incluses dans les processus détenus par l’équipe responsable des opérations informatiques.
11. La création de nouveaux abonnements ou de groupes d’administration pour les applications stratégiques ou les données protégées nécessite un examen par l’équipe de gouvernance cloud pour vérifier que le blueprint approprié est affecté.
12. Un modèle d’accès de moindre privilège doit être appliqué aux abonnements qui contiennent des applications critiques ou des données protégées.
13. Le fournisseur de cloud doit être capable d'intégrer des clés de chiffrement gérées par la solution locale existante.
14. Le fournisseur de cloud doit être capable de prendre en charge la solution d'appareil de périmètre existante, ainsi que toutes les configurations requises pour protéger la limite de réseau exposée publiquement.
15. Le fournisseur de cloud doit être capable de prendre en charge une connexion partagée au réseau étendu, avec transmission des données acheminées via la solution d'appareil de périmètre actuelle.
16. Les tendances et les attaques susceptibles d’affecter les déploiements cloud doivent être régulièrement examinées par l’équipe de sécurité pour fournir des mises à jour aux outils de base de référence de sécurité utilisés dans le cloud.
17. Les outils de déploiement doivent être approuvés par l’équipe de gouvernance cloud pour s’assurer de la gouvernance en continu des ressources déployées.
18. Les scripts de déploiement doivent être conservés dans un référentiel centralisé, accessible par l’équipe de gouvernance cloud pour effectuer des audits et des révisions périodiques.
19. Les processus de gouvernance doivent inclure des audits, à intervalles réguliers, au point de déploiement pour garantir la cohérence entre toutes les ressources.
20. Le déploiement des applications nécessitant une authentification des clients doit utiliser un fournisseur d'identité approuvé compatible avec le fournisseur d'identité principal pour les utilisateurs internes.
21. Les processus de gouvernance cloud doivent inclure des révisions trimestrielles avec les équipes de base de référence des identités, avec pour objectif d'identifier les modèles d'utilisation ou les acteurs malveillants devant être bloqués par la configuration des ressources cloud.

## <a name="incremental-improvement-of-the-best-practices"></a>Amélioration incrémentielle des bonnes pratiques

Cette section de l’article va modifier la conception du MVP de gouvernance, afin d’inclure de nouvelles stratégies Azure ainsi qu’une implémentation d’Azure Cost Management. Ensemble, ces deux modifications de la conception permettront de répondre aux nouvelles instructions de la stratégie d’entreprise.

Les nouvelles meilleures pratiques se répartissent dans deux catégories : Informatique d’entreprise (hub) et Adoption du cloud (spoke).

**Établissement d’un abonnement informatique d’entreprise hub-and-spoke pour centraliser la Base de référence de la sécurité :** Dans cette bonne pratique, la capacité de gouvernance existante est encapsulée par une [topologie hub-and-spoke avec des services partagés](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services), accompagnée de quelques ajouts importants apportés par l’équipe de gouvernance cloud.

1. Référentiel Azure DevOps. Créez un référentiel dans Azure DevOps pour stocker et gérer les versions de tous les modèles Azure Resource Manager pertinents et des configurations utilisant des scripts.
2. Modèle hub-and-spoke :
    1. Les instructions de l’architecture de référence de la [topologie hub-and-spoke avec des services partagés](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services) peuvent servir à générer des modèles Resource Manager pour les ressources nécessaires dans un hub informatique d’entreprise.
    2. À l'aide de ces modèles, cette structure peut être reproductible, dans le cadre d’une stratégie de gouvernance centrale.
    3. En plus de l’architecture de référence actuelle, il est conseillé de créer un modèle de groupe de sécurité réseau, qui capture tout blocage de port ou exigence de mise en liste verte permettant au réseau virtuel d’héberger le pare-feu. Ce groupe de sécurité réseau diffère des groupes précédents, car il est le premier groupe de sécurité réseau à autoriser le trafic public vers un réseau virtuel.
3. Créez des stratégies Azure. Créez une stratégie nommée `Hub NSG Enforcement` pour appliquer la configuration du groupe de sécurité réseau attribué à un réseau virtuel créé dans cet abonnement. Appliquez les stratégies intégrées pour la configuration des invités comme suit :
    1. Vérifiez que les serveurs web Windows utilisent des protocoles de communication sécurisés.
    2. Vérifiez que les paramètres de sécurité des mots de passe sont correctement définis dans les machines Linux et Windows.
4. Blueprint informatique d’entreprise
    1. Créez un blueprint Azure nommé `corporate-it-subscription`.
    2. Ajoutez les modèles hub-and-spoke et la stratégie `Hub NSG Enforcement`.
5. Extension de la hiérarchie initiale de groupes d'administration.
    1. Pour chaque groupe d’administration ayant demandé la prise en charge des données protégées, le blueprint `corporate-it-subscription-blueprint` constitue une solution hub accélérée.
    2. Les groupes d’administration dans cet exemple fictif incluant une hiérarchie régionale en plus d’une hiérarchie d'unités commerciales, ce blueprint sera déployé dans chaque région.
    3. Pour chaque région de la hiérarchie de groupes d'administration, créez un abonnement nommé `Corporate IT Subscription`.
    4. Appliquez le blueprint `corporate-it-subscription-blueprint` à chaque instance régionale.
    5. Cela permettra d’établir un hub pour chaque unité commerciale dans chaque région. Remarque : le partage de hubs entre les unités commerciales de chaque région permet une plus importante réduction des coûts.
6. Intégrez des objets de stratégie de groupe (GPO) par le biais d'une configuration d'état souhaité (DSC) :
    1. Conversion GPO vers DSC - Le [projet de gestion de la base de référence Microsoft](https://github.com/Microsoft/BaselineManagement) dans GitHub peut accélérer cet effort. * Assurez-vous de stocker la configuration de l'état souhaité (DSC) dans le référentiel, en parallèle avec les modèles Resource Manager.
    2. Déployez la configuration d’état souhaité Azure Automation sur plusieurs instances de l'abonnement informatique d'entreprise. Azure Automation peut être utilisé pour appliquer la configuration d'état souhaité aux machines virtuelles déployées dans des abonnements pris en charge au sein du groupe d’administration.
    3. La feuille de route actuelle prévoit de permettre les stratégies de configuration personnalisée invité. Une fois cette fonctionnalité disponible, l’utilisation d’Azure Automation dans le cadre de cette meilleure pratique ne sera plus requise.

**Application d’une plus grande gouvernance dans le cadre d’un abonnement d’adoption cloud (Spoke) :** En s’appuyant sur l’`Corporate IT Subscription`, des modifications mineures apportées au MVP de gouvernance et appliquées à chaque abonnement dédié à la prise en charge des archétypes d’application peuvent contribuer à une amélioration rapide.

Dans les modifications itératives précédentes apportées à la bonne pratique, nous avons défini des groupes de sécurité réseau pour bloquer le trafic public et mettre en liste verte le trafic interne. En outre, le blueprint Azure a temporairement créé des fonctionnalités DMZ et Active Directory. Dans le cadre de la présente itération, nous allons légèrement ajuster ces ressources et créer une nouvelle version du blueprint Azure.

1. Modèle de peering de réseau. Ce modèle appairera le réseau virtuel à chaque abonnement avec le réseau virtuel hub dans l’abonnement informatique d’entreprise.
    1. L’architecture de référence de la section précédente, la [topologie hub-and-spoke avec des services partagés](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services), a généré un modèle Resource Manager permettant le peering de réseau virtuel.
    2. Ce modèle peut faire office de guide pour modifier le modèle DMZ à partir de la précédente itération de gouvernance.
    3. Nous ajoutons à présent le VNet Peering au réseau virtuel DMZ précédemment connecté à l’appareil de périmètre local via VPN.
    4. *** Il est aussi vivement conseillé de supprimer le VPN de ce modèle et de veiller à ce qu'aucun trafic ne soit directement routé vers le centre de données local, sans transiter via l'abonnement informatique d'entreprise et la solution de pare-feu. Vous pouvez également définir ce VPN comme circuit de basculement en cas de défaillance d’un circuit ExpressRoute.
    5. Une [configuration réseau](https://docs.microsoft.com/azure/automation/automation-dsc-overview#network-planning) supplémentaire sera requise par Azure Automation pour appliquer la configuration d'état souhaité aux machines virtuelles hébergées.
2. Modifiez le groupe de sécurité réseau. Bloquez tout le trafic public **et** dirigez le trafic local vers le groupe de sécurité réseau. Seul le trafic entrant doit transiter via l'homologue de réseau virtuel dans l'abonnement informatique d'entreprise.
    1. Dans le cadre de la précédente itération, un groupe de sécurité réseau a été créé pour bloquer tout le trafic public et mettre le trafic interne sur liste verte. À présent, nous voulons légèrement déplacer ce groupe de sécurité réseau.
    2. La nouvelle configuration de groupe de sécurité réseau doit bloquer tout le trafic public, et tout le trafic provenant du centre de données local.
    3. Le trafic entrant dans ce réseau virtuel doit uniquement provenir du réseau virtuel situé de l'autre côté de l'homologue de réseau virtuel.
3. Implémentation d’Azure Security Center :
    1. Configurez Azure Security Center pour les groupes d’administration qui contiennent des classifications de données protégées.
    2. Définissez le provisionnement automatique sur Activé par défaut pour garantir la conformité des mises à jour correctives.
    3. Établissez des configurations de sécurité des systèmes d’exploitation. Équipe Sécurité informatique pour définir la configuration.
    4. Apportez un support à la sécurité informatique pour l’utilisation initiale d'Azure Security Center. Transférez l’utilisation du centre de sécurité à la sécurité informatique, mais conservez un accès pour toute amélioration continue de la gouvernance.
    5. Créez un modèle Resource Manager qui reflète les modifications nécessaires pour la configuration d'Azure Security Center au sein d’un abonnement.
4. Mettez à jour Azure Policy pour tous les abonnements.
    1. Auditez et appliquez la classification de la criticité et des données sur tous les groupes d’administration et tous les abonnements, de façon à identifier tous les abonnements avec des classifications de données protégées.
    2. Auditez et appliquez l’utilisation exclusive d’images de système d'exploitation approuvées.
    3. Auditez et appliquez les configurations invité basées sur les exigences de sécurité pour chaque nœud.
5. Mettez à jour Azure Policy pour tous les abonnements qui contiennent des classifications de données protégées.
    1. Auditez et appliquez l’utilisation de rôles standard uniquement.
    2. Auditez et imposez l'application de chiffrement au repos pour tous les comptes de stockage et tous les fichiers sur les nœuds individuels.
    3. Auditez et imposez l'application de la nouvelle version du groupe de sécurité réseau DMZ.
    4. Auditez et appliquez l’utilisation d’un réseau virtuel et sous-réseau de réseau approuvé par interface réseau.
    5. Auditez et imposez la limitation des tables de routage définies par l’utilisateur.
6. Blueprint Azure :
    1. Créez un blueprint Azure nommé `protected-data`.
    2. Ajoutez l’homologue de réseau virtuel, le groupe de sécurité réseau et les modèles Azure Security Center au blueprint.
    3. Assurez-vous que le modèle correspondant à Active Directory de la précédente itération ne soit **pas** inclus dans le blueprint. Toutes les dépendances Active Directory seront fournies par l’abonnement informatique d’entreprise.
    4. Arrêtez les machines virtuelles Active Directory existantes déployées dans le cadre de l’itération précédente.
    5. Ajoutez les nouvelles stratégies pour les abonnements de données protégées.
    6. Publiez le blueprint dans tous les groupes d’administration qui hébergeront des données protégées.
    7. Appliquez le nouveau blueprint à chaque abonnement affecté, ainsi qu'aux blueprints existants.

## <a name="conclusion"></a>Conclusion

L’ajout de ces processus et modifications au MVP de gouvernance permet de traiter de nombreux risques associés à la gouvernance de la sécurité. Ensemble, ils ajoutent les outils de surveillance du réseau, des identités et de la sécurité nécessaires pour protéger les données.

## <a name="next-steps"></a>Étapes suivantes

À mesure que l’adoption du cloud se poursuit et offre davantage de valeur aux activités métier, les risques et les besoins en matière de gouvernance du cloud changent également. Pour la société fictive utilisée dans ce guide, l’étape suivante consiste à prendre en charge les charges de travail critiques. C’est ici que les contrôles de cohérence des ressources sont nécessaires.

> [!div class="nextstepaction"]
> [Améliorer la discipline Cohérence des ressources](./resource-consistency-improvement.md)
