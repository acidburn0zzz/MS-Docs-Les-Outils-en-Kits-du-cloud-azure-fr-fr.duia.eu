---
title: Passer en revue les décisions de rationalisation
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à évaluer les décisions de rationalisation et faciliter une conversation avec l’entreprise.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: aa544540c0bebb001f9256527a5f0ba388801c3c
ms.sourcegitcommit: ea63be7fa94a75335223bd84d065ad3ea1d54fdb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80354805"
---
# <a name="review-rationalization-decisions"></a>Passer en revue les décisions de rationalisation

Au cours des phases initiales de stratégie et de planification, nous vous suggérons d’appliquer une approche de type [rationalisation incrémentielle](../digital-estate/rationalize.md#incremental-rationalization) à votre patrimoine numérique. Toutefois, cette approche incorpore certaines hypothèses quant aux décisions résultantes. Nous conseillons à l’équipe de stratégie cloud et aux équipes d’adoption du cloud de passer en revue ces décisions au vu de la documentation étendue sur les charges de travail. Cet examen est également un moment propice pour impliquer les parties prenantes de l’entreprise et le principal commanditaire dans les décisions liées aux états futurs.

> [!IMPORTANT]
> Une validation supplémentaire des décisions de rationalisation aura lieu pendant la phase d’évaluation de la migration. Cette validation est axée sur l’examen opérationnel de la rationalisation afin d’aligner les ressources de manière appropriée.

Pour valider les décisions de rationalisation, utilisez les questions suivantes qui stimuleront un débat au sein de l’entreprise. Les questions sont regroupées par alignement de la rationalisation probable.

## <a name="innovation-indicators"></a>Indicateurs d’innovation

Si l’examen conjoint des questions suivantes aboutit à une réponse « Oui », une charge de travail peut être plus avantageuse pour l’innovation. Une telle charge de travail n’est pas migrée via un modèle lift-and-shift ou de modernisation. Au lieu de cela, la logique métier ou les structures de données seraient recréées en tant qu’application nouvelle ou remaniée. Cette approche peut éventuellement demander plus d’efforts et de temps. Toutefois, une charge de travail renforçant de façon significative le rendement de l’entreprise justifie un tel investissement.

- Les applications figurant dans cette charge de travail génèrent-elles une différenciation sur le marché ?
- Existe-t-il un investissement proposé ou approuvé visant à améliorer les expériences associées aux applications dans cette charge de travail ?
- Les données attenant à cette charge de travail favorisent-elles de nouvelles offres de produit ou de service ?
- Existe-t-il un investissement proposé ou approuvé visant à tirer parti des données associées à cette charge de travail ?
- L’effet de la différenciation sur le marché ou de nouvelles offres peut-il être quantifié ? Si oui, ce retour justifie-t-il l’augmentation du coût de l’innovation lors de l’adoption du cloud ?

Les deux questions suivantes peuvent vous aider à inclure des scénarios techniques de haut niveau dans l’examen de la rationalisation. Répondre « Oui » à l’une d’elles permettrait d’identifier des façons de comptabiliser ou de réduire le coût associé à l’innovation.

- Les structures de données et la logique métier changeront-elles au cours de l’adoption du cloud ?
- Un pipeline de déploiement existant est-il utilisé pour déployer cette charge de travail en production ?

Si la réponse à l’une de ces deux questions est « Oui », l’équipe doit envisager d’inclure cette charge de travail comme candidat d’innovation. Au minimum, l’équipe doit signaler cette charge de travail pour un examen d’architecture afin d’identifier les opportunités de modernisation.

## <a name="migration-indicators"></a>Indicateurs de migration

La migration est un moyen plus rapide et économique d’adopter le cloud. Toutefois, elle ne tire pas parti des opportunités d’innovation. Avant d’investir dans l’innovation, répondez aux questions suivantes. Elles peuvent vous aider à déterminer si un modèle de migration est plus applicable pour une charge de travail.

- Le code source soutenant cette application est-il stable ? Pensez-vous qu’il restera stable et inchangé pendant toute la durée de ce cycle de publication de version ?
- Cette charge de travail prend-elle en charge les processus de production actuels ? Continuera-t-elle à le faire tout au long du cycle de publication de version ?
- Est-ce une priorité que cet effort d’adoption du cloud améliore la stabilité et les performances de cette charge de travail ?
- La réduction des coûts associée à cette charge de travail est-elle un objectif dans le cadre de cet effort ?
- La réduction de la complexité opérationnelle pour cette charge de travail est-elle un objectif dans le cadre de cet effort ?
- L’innovation est-elle limitée par l’architecture ou les processus d’exploitation informatique actuels ?

Si la réponse à l’une de ces questions est « Oui », vous devez envisager un modèle de migration pour cette charge de travail. Cette recommandation est vraie même si la charge de travail est un candidat d’innovation.

Les défis liés à la complexité opérationnelle, aux coûts, aux performances et à la stabilité peuvent nuire au rendement de l’entreprise. Vous pouvez mettre à profit le cloud pour créer rapidement des améliorations liées à ces défis. Là où cela s’applique, nous vous suggérons d’utiliser l’approche de migration pour stabiliser dans un premier temps la charge de travail. Ensuite, approfondissez les opportunités d’innovation grâce à l’agilité et la stabilité de l’environnement cloud. Cette approche favorise des retours à court terme et réduit le coût nécessaire pour induire des changements à long terme.

> [!IMPORTANT]
> Les modèles de migration incluent une modernisation incrémentielle. L’utilisation d’architectures de plateforme en tant que service (PaaS) est un aspect courant des activités de migration. Il en est de même des modifications mineures de configuration qui utilisent ces services de plateforme. La limite de migration est définie comme une modification significative de la logique métier ou des structures opérationnelles. Ce changement est considéré comme un effort d’innovation.

## <a name="update-the-project-plan"></a>Mettre à jour le plan de projet

Les compétences requises pour un effort de migration sont différentes de celles requises pour un effort d’innovation. Au cours de l’implémentation d’un plan d’adoption du cloud, nous vous suggérons d’affecter les efforts de migration et d’innovation à des équipes différentes. Chaque équipe possède ses propres cadences d’itération, de publication de version et de planification. L’affectation à des équipes distinctes offre une flexibilité des processus favorisant la maintenance d’un plan d’adoption du cloud tout en tenant compte des efforts d’innovation et de migration.

Lorsque vous gérez le plan d’adoption du cloud dans Azure DevOps, cette gestion est reflétée par la modification de l’élément de travail parent (ou épopée) de la migration cloud à l’innovation cloud. Ce changement subtil permet de garantir que tous les participants au plan d’adoption du cloud pourront rapidement effectuer le suivi de l’effort requis et des modifications à apporter aux efforts de correction. Ce suivi permet également d’aligner les bonnes affectations à l’équipe d’adoption du cloud appropriée.

Pour de grands plans d’adoption complexes avec plusieurs projets distincts, envisagez de mettre à jour le chemin de l’itération. La modification du chemin de zone rend la charge de travail visible uniquement pour l’équipe affectée à ce chemin de zone. Cette modification peut faciliter le travail de l’équipe d’adoption du cloud en réduisant le nombre de tâches visibles. En revanche, cela complique les processus de gestion de projet.

## <a name="next-steps"></a>Étapes suivantes

[Établir des itérations et des plans de mise en production](./iteration-paths.md) pour commencer la planification du travail.

> [!div class="nextstepaction"]
> [Établir des itérations et des plans de mise en production](./iteration-paths.md) pour commencer la planification du travail.
