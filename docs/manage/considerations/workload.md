---
title: Opérations de charge de travail en gestion cloud
description: Découvrez une approche permettant d’investir dans les opérations continues de ces charges de travail de haute priorité pour améliorer les engagements commerciaux.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 1b3f21999cea35de59f30d882f9d8b104169952c
ms.sourcegitcommit: 070e6a60f05519705828fcc9c5770c3f9f986de5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83815223"
---
# <a name="workload-operations-in-cloud-management"></a>Opérations de charge de travail en gestion cloud

Certaines charges de travail sont essentielles pour le succès de l’entreprise. Pour ces charges de travail, une base de référence de gestion ne suffit pas pour répondre aux engagements métier de la gestion cloud. Les opérations de plateforme peuvent ne pas être suffisantes pour répondre aux engagements métier. Ce sous-ensemble très important de charges de travail nécessite que vous prêtiez une attention particulière au fonctionnement et à la prise en charge des charges de travail.

En retour, cet investissement dans les opérations de charge de travail peut améliorer les performances, réduire les risques d’interruption et accélérer la récupération en cas de défaillance du système. Cet article explique comment investir dans les opérations continues de ces charges de travail haute priorité afin d’améliorer les engagements métier.

<!-- docsTest:disable Pareto -->

## <a name="when-to-invest-in-workload-operations"></a>Quand investir dans les opérations de charge de travail

Le _principe de Pareto_ (également appelé _règle 80/20_) stipule que 80 pour cent des effets proviennent de 20 pour cent des causes. Lorsque les portefeuilles informatiques sont autorisés à croître avec le temps, cette règle est souvent illustrée lors d’un examen du portefeuille informatique. La cause peut varier en fonction de l’effet qui nécessite un investissement, mais le principe général reste le même :

- 80 pour cent des défaillances système ont tendance à résulter des 20 pour cent d’erreurs et de bogues courants.
- 80 pour cent de la valeur métier ont tendance à provenir de 20 pour cent des charges de travail du portefeuille.
- 80 pour cent de l’effort de migration vers le cloud proviennent de 20 pour cent des charges de travail déplacées.
- 80 % des efforts de gestion cloud prendront en charge 20 % des incidents de service ou des tickets d’incident.
- 80 pour cent de l’impact commercial de la panne proviennent de 20 pour cent des systèmes concernés par la panne.

Les opérations de charge de travail doivent être appliquées uniquement lorsque la stratégie d’adoption cloud, les résultats commerciaux et les métriques opérationnelles ont été bien compris. Il s’agit d’un changement de paradigme par rapport à la vue classique de l’informatique. Traditionnellement, le service informatique supposait que toutes les charges de travail bénéficiaient du même niveau de prise en charge et qu’elles nécessitaient des niveaux de priorité similaires.

Avant d’investir dans des opérations de charges de travail avancées, le service informatique et l’entreprise doivent comprendre les justifications métier, ainsi que les attentes relatives à un plus grand investissement en gestion cloud.

## <a name="start-with-the-data"></a>Prise en main des données

Les opérations de charge de travail commencent par une compréhension approfondie des performances des charges de travail et des exigences de prise en charge. Avant d’investir dans des opérations de charge de travail, l’équipe doit disposer de données significatives concernant les dépendances des charges de travail, les performances des applications, les diagnostics des bases de données, les données de télémétrie des machines virtuelles et l’historique des incidents.

Ces données sont à l’origine des insights sur lesquels sont basées les opérations de charge de travail.

## <a name="continued-observation"></a>Observation continue

Les données initiales et les données de télémétrie actuelles peuvent aider à formuler et à tester les théories sur les performances d’une charge de travail. Toutefois, les opérations de charge de travail en cours sont basées sur une observation continue et étendue des performances de la charge de travail, avec une attention particulière sur les performances des applications et des données.

### <a name="test-the-automation"></a>Tester l’automatisation

Au niveau de l’application, les premières exigences des opérations de charge de travail concernent l’investissement dans des tests approfondis. Pour toutes les applications prises en charge par le biais d’opérations de charge de travail, un plan de test doit être établi et exécuté régulièrement pour fournir des tests fonctionnels et à l’échelle dans les applications.

L’obtention régulière de données de télémétrie de test peut fournir une validation immédiate des différentes hypothèses d’opérations concernant le fonctionnement de la charge de travail. L’amélioration des modèles opérationnels et architecturaux peut être exécutée et testée. Les deltas en résultant fournissent une analyse d’impact claire pour guider des investissements continus.

### <a name="understand-releases"></a>Comprendre les mises en production

Il est important de bien comprendre les cycles et les pipelines de mise en production pour les opérations de charge de travail.

La compréhension des cycles permet de se préparer aux interruptions potentielles, et permet à l’équipe de traiter de manière proactive les mises en production susceptibles d’avoir un effet négatif sur les opérations. Cette compréhension permet également à l’équipe de gestion cloud de collaborer avec des équipes d’adoption pour améliorer en permanence la qualité du produit et résoudre les bogues qui pourraient affecter la stabilité.

Plus important encore, une compréhension des pipelines de mise en production peut améliorer de manière significative l’objectif de point de récupération (RTO) d’une charge de travail. Dans de nombreux scénarios, le moyen le plus rapide et le plus précis pour la récupération d’une application consiste à utiliser un pipeline de mise en production. Pour les couches Application qui changent uniquement lorsqu’une nouvelle version est publiée, il peut être judicieux d’investir de manière plus importante dans l’optimisation du pipeline plutôt que dans la récupération de l’application à partir de processus de sauvegarde traditionnels.

Le pipeline de déploiement peut être le moyen le plus rapide d’effectuer une récupération, mais également d’effectuer une correction. Quand une application dispose d’un pipeline de mise en production rapide, efficace et fiable, l’équipe de gestion cloud peut automatiser le déploiement sur un nouvel hôte sous la forme d’une correction automatisée.

Il peut y avoir de nombreux autres mécanismes plus rapides et plus efficaces pour la correction et la récupération. Toutefois, lorsque l’utilisation d’un pipeline existant est compatible avec les engagements métier de l’entreprise et permet de tirer parti des investissements DevOps existants, ce pipeline est probablement une alternative viable.

### <a name="clearly-communicate-changes-to-the-workload"></a>Communiquer clairement les modifications apportées à la charge de travail

La modification des charges de travail fait partie des opérations de charge de travail les plus risquées. Pour toutes les charges de travail de niveau Opérations de charge de travail dans la gestion cloud, l’équipe chargée de la gestion cloud doit s’aligner sur les équipes d’adoption cloud afin de comprendre les modifications apportées par chaque version. Cet investissement dans une compréhension proactive aura un impact direct et positif sur la stabilité opérationnelle.

## <a name="improve-outcomes"></a>Améliorer les résultats

Dans une charge de travail, les investissements relatifs aux données et à la communication produiront des suggestions d’amélioration des opérations dans l’un des trois domaines suivants :

- Résolution de la dette technique
- Correction automatisée
- Conception améliorée du système

### <a name="technical-debt-resolution"></a>Résolution de la dette technique

Le meilleur des plans d’opérations de charge de travail nécessite toujours une correction. De même que votre équipe de gestion cloud cherche à rester connectée pour comprendre les efforts d’adoption et les mises en production, elle doit également partager régulièrement les exigences de correction afin de garantir que la dette technique et les bogues sont une priorité continue pour vos équipes de développement.

### <a name="automated-remediation"></a>Correction automatisée

Il ressort de l’application du principe de Pareto que 80 pour cent de l’impact métier négatif viennent probablement des 20 pour cent des incidents de service. Lorsque ces incidents ne peuvent pas être traités dans le cadre de cycles de développement normaux, des investissements en automatisation des corrections peuvent réduire considérablement les interruptions d’activité.

### <a name="improved-system-design"></a>Conception améliorée du système

En cas de résolution de la dette technique et de la correction automatisée, les défauts du système sont la cause de la plupart des pannes système. L’application de quelques principes de conception peut vous permettre d’avoir un impact important sur les opérations globales de charge de travail :

- **Scalabilité :** Capacité d’un système à traiter une charge accrue.
- **Disponibilité :** Pourcentage de temps pendant lequel le système est fonctionnel et opérationnel.
- **Résilience :** Capacité d’un système à récupérer après des défaillances et à continuer de fonctionner.
- **Gestion :** Processus d’opérations assurant l’exécution d’un système en production.
- **Sécurité :** Protection des applications et des données contre les menaces.

Pour contribuer à améliorer les opérations globales, le [Centre des architectures Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) fournit une approche permettant de vérifier si les charges de travail respectent ces principes. Vous pouvez les appliquer aussi bien aux opérations de plateforme qu’aux opérations de charge de travail.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez une compréhension complète de la méthodologie de gestion dans le Framework d’adoption cloud, vous êtes prêt à implémenter les principes de la gestion cloud. Pour obtenir des conseils sur l’application de cette méthodologie dans votre environnement d’exploitation, consultez la [gestion du cloud dans le framework d’adoption du cloud](../index.md) du cycle de vie d’adoption.

> [!div class="nextstepaction"]
> [Appliquer cette méthodologie](../index.md)
