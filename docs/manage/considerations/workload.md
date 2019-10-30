---
title: Opérations de charge de travail - Gestion cloud et opérations
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Opérations de charge de travail - Gestion cloud et opérations
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5f250362e93a81c6bb38ef11e8659484ef023182
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683731"
---
# <a name="workload-operations-in-cloud-management"></a>Opérations de charge de travail en gestion cloud

Certaines charges de travail sont essentielles pour le succès de l’entreprise. Pour ces charges de travail, une base de référence de gestion ne suffit pas pour répondre aux engagements métier de la gestion cloud. Les opérations de plateforme peuvent ne pas être suffisantes pour répondre aux engagements métier. Ce sous-ensemble très important de charges de travail nécessite que vous prêtiez une attention particulière au fonctionnement et à la prise en charge des charges de travail.

En retour, cet investissement dans les opérations de charge de travail peut améliorer les performances, réduire les risques d’interruption et accélérer la récupération en cas de défaillance du système. Cet article explique comment investir dans les opérations continues de ces charges de travail haute priorité afin d’améliorer les engagements métier.

## <a name="when-to-invest-in-workload-operations"></a>Quand investir dans les opérations de charge de travail

Le principe de Pareto (également appelé règle 80/20) stipule que 80 % des effets proviennent de 20 % des causes. Lorsque les portefeuilles informatiques sont autorisés à croître avec le temps, cette règle peut généralement être vérifiée lors d’un examen du portefeuille informatique. La cause peut varier en fonction de l’effet qui nécessite un investissement, mais le principe général reste le même :

- 80 % des défaillances système ont tendance à résulter des 20 % d’erreurs et bogues courants
- 80 % de la valeur métier ont tendance à provenir de 20 % des charges de travail du portefeuille
- 80 % de l’effort de migration vers le cloud proviennent de 20 % des charges de travail déplacées
- 80 % des efforts de gestion cloud prendront en charge 20 % des incidents de service ou des tickets d’incident
- 80 % de l’impact commercial de la panne proviennent de 20 % des systèmes concernés par la panne

Les opérations de charge de travail doivent être appliquées uniquement lorsque la stratégie d’adoption cloud, les résultats commerciaux et les métriques opérationnelles ont été bien compris. Il s’agit d’un changement de paradigme par rapport à la vue classique de l’informatique. Traditionnellement, le service informatique supposait que toutes les charges de travail bénéficiaient du même niveau de prise en charge et qu’elles nécessitaient des niveaux de priorité similaires.

Avant d’investir dans des opérations de charges de travail avancées, le service informatique et l’entreprise doivent comprendre les justifications métier, ainsi que les attentes relatives à un plus grand investissement en gestion cloud.

## <a name="start-with-the-data"></a>Prise en main des données

Les opérations de charge de travail commencent par une compréhension approfondie des performances des charges de travail et des exigences de prise en charge. Avant d’investir dans des opérations de charge de travail, l’équipe doit disposer de données significatives concernant : les dépendances des charges de travail, les performances des applications, les diagnostics des bases de données, les données de télémétrie des machines virtuelles et l’historique des incidents.

Ces données sont à l’origine des insights sur lesquels sont basées les opérations de charge de travail.

## <a name="continued-observation"></a>Observation continue

Les données initiales et les données de télémétrie actuelles peuvent aider à formuler et à tester les théories concernant les performances d’une charge de travail. Toutefois, les opérations de charge de travail en cours sont basées sur une observation continue et étendue des performances de la charge de travail, avec une attention particulière sur les performances des applications et des données.

### <a name="testing-automation"></a>Test de l’automatisation

Au niveau de l’application, les premières exigences des opérations de charge de travail concernent l’investissement dans des tests approfondis. Pour toutes les applications prises en charge par le biais d’opérations de charge de travail, un plan de test doit être établi et exécuté régulièrement pour fournir des tests fonctionnels et à l’échelle dans les applications.

L’obtention régulière de données de télémétrie de test fournit une validation immédiate des différentes hypothèses d’opérations concernant le fonctionnement de la charge de travail. L’amélioration des modèles opérationnels et architecturaux peut être exécutée et testée. Le delta de ces résultats fournit une analyse d’impact claire permettant de guider les investissements continus.

### <a name="understand-releases"></a>Comprendre les mises en production

Il est important de bien comprendre les cycles et les pipelines de mise en production pour les opérations de charge de travail.

La compréhension des cycles permet de se préparer aux interruptions potentielles, et permet à l’équipe de traiter de manière proactive les mises en production susceptibles d’avoir un impact négatif sur les opérations. Cette compréhension permet également à l’équipe de gestion cloud de collaborer avec des équipes d’adoption pour améliorer en permanence la qualité du produit et résoudre les bogues qui pourraient avoir un impact sur la stabilité.

Plus important encore, une compréhension des pipelines de mise en production peut améliorer de manière significative le RTO d’une charge de travail. Dans de nombreux scénarios, le moyen le plus rapide et le plus précis pour la récupération d’une application consiste à utiliser un pipeline de mise en production. Pour les couches Application qui changent uniquement lorsqu’une nouvelle version est publiée, il peut être judicieux d’investir de manière plus importante dans l’optimisation du pipeline, que dans la récupération de l’application à partir de processus de sauvegarde traditionnels.

Le pipeline de déploiement est le moyen le plus rapide d’effectuer une récupération, mais également d’effectuer une correction. Quand une application dispose d’un pipeline de mise en production rapide, efficace et fiable, l’équipe de gestion cloud peut automatiser le déploiement sur un nouvel hôte sous la forme d’une correction automatisée.

Il peut y avoir de nombreux autres mécanismes plus rapides et plus efficaces pour la correction et la récupération. Toutefois, lorsque l’utilisation d’un pipeline existant est compatible avec les engagements métier de l’entreprise et permet de tirer parti des investissements DevOps existants, il s’agit probablement d’une alternative viable.

### <a name="clearly-communicate-changes-to-the-workload"></a>Communiquer clairement les modifications apportées à la charge de travail

La modification des charges de travail fait partie des opérations de charge de travail les plus risquées. Pour toutes les charges de travail de niveau Opérations de charge de travail dans la gestion cloud, l’équipe chargée de la gestion cloud doit s’aligner sur les équipes d’adoption cloud afin de comprendre les modifications apportées par chaque version. Cet investissement dans une compréhension proactive aura un impact direct sur la stabilité opérationnelle.

## <a name="improve-outcomes"></a>Améliorer les résultats

Les opérations en cours peuvent généralement être améliorées de deux façons. Dans une charge de travail, les investissements relatifs aux données et à la communication produiront des suggestions d’amélioration à l’un des deux niveaux suivants : la correction automatisée ou la conception améliorée du système.

### <a name="technical-debt-resolution"></a>Résolution de la dette technique

Le meilleur des plans d’opérations de charge de travail nécessitera toujours une correction. De même que l’équipe de gestion cloud cherche à rester connectée pour comprendre les efforts d’adoption et les mises en production, elle doit également partager régulièrement les exigences de correction afin de garantir que la dette technique et les bogues sont une priorité continue pour les équipes de développement.

### <a name="automate-remediation"></a>Automatiser la correction

D’après le principe de Pareto, 80 % de l’impact négatif sur l’entreprise est probablement dû à 20 % des incidents de service. Lorsque ces incidents ne peuvent pas être traités dans le cadre de cycles de développement normaux, des investissements en automatisation des corrections peuvent réduire considérablement les interruptions d’activité.

### <a name="improved-system-design"></a>Conception améliorée du système

Dans les deux cas (résolution de la dette technique ou correction automatisée), les défauts du système sont la cause de la plupart des pannes système. L’application de quelques principes de conception peut avoir un impact important sur les opérations globales de charge de travail.

1. Scalabilité : Capacité d’un système à traiter une charge accrue.
2. Disponibilité : Durée pendant laquelle le système est fonctionnel et opérationnel.
3. Résilience : Capacité d’un système à récupérer après des défaillances et à continuer de fonctionner.
4. Gestion : Processus d’opérations assurant l’exécution d’un système en production.
5. Sécurité : Protection des applications et des données contre les menaces.

Le [Centre des architectures Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) fournit une méthode permettant de vérifier si les charges de travail suivent ces principes, en vue d’améliorer les opérations globales. Ces principes peuvent être appliqués aussi bien aux opérations de plateforme qu’aux opérations de charge de travail.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez une compréhension complète de la méthodologie de gestion dans le Framework d’adoption cloud, vous êtes prêt à implémenter les principes de la gestion cloud. Pour obtenir des conseils sur l’application de cette méthodologie dans votre environnement d’exploitation, consultez la [page d’accueil de la phase de gestion](../index.md) du cycle de vie d’adoption.

> [!div class="nextstepaction"]
> [Appliquer cette méthodologie](../index.md)