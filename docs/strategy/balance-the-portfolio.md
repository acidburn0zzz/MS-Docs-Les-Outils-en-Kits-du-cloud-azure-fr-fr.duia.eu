---
title: Équilibrer le portefeuille
description: Découvrez les stratégies pour équilibrer la migration, l’innovation et l’expérimentation pour tirer le meilleur parti des vos efforts de migration vers le cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 381359391d7fc39281d49d202f66edf5691be293
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80433801"
---
<!-- cSpell:ignore CSAT -->

# <a name="balance-the-portfolio"></a>Équilibrer le portefeuille

L’adoption du cloud est un effort de gestion de portefeuille, habilement déguisé en implémentation technique. Comme n’importe quel exercice de gestion de portefeuille, l’équilibre du portefeuille est essentiel. À un niveau stratégique, cela signifie équilibrer la migration, l’innovation et l’expérimentation pour tirer le meilleur parti du cloud. Quand l’effort d’adoption du cloud va trop loin dans une direction, la complexité va de pair. Cet article guide le lecteur à travers les approches pour atteindre un équilibre dans le portefeuille.

## <a name="general-scope-expansion"></a>Expansion de l’étendue générale

L’équilibrage du portefeuille est intrinsèquement stratégique. Par conséquent, l’approche adoptée dans cet article est tout aussi stratégique. Pour baser la stratégie sur des décisions fondées sur des données, cet article part du principe que le lecteur a évalué le [patrimoine numérique](../digital-estate/index.md) existant (ou est en train de le faire). L’objectif de cette approche est de vous aider à évaluer les charges de travail afin de garantir un bon équilibre dans le portefeuille grâce à des questions qualitatives et à l’amélioration du portefeuille.

### <a name="document-business-outcomes"></a>Documenter les résultats opérationnels

Avant d’équilibrer le portefeuille, il est important de documenter et de partager les résultats opérationnels dans le cadre de l’effort de migration cloud. Le tableau suivant peut vous aider à documenter et à partager les résultats métier souhaités. Il est important de noter que la plupart des entreprises recherchent plusieurs résultats à la fois. L’importance de cet exercice consiste à clarifier les résultats qui sont le plus directement liés à l’effort de migration cloud :

|Résultat  |Mesuré par  |Objectif  |Délai d’exécution  |Priorité pour cet effort  |
|---------|---------|---------|---------|---------|
|Réduire les coûts informatiques     |Budget du centre de données         |Réduire de 2 millions de dollars         |12 mois         |No 1         |
|Sortie des centres de données     |Sortir de centres de centres         |2 centres de données         |6 mois         |No 2         |
|Augmenter la réactivité de l’entreprise     |Améliorer le délai de commercialisation  |Réduire le temps de déploiement de six mois         |2 ans         |No 3        |
|Améliorer l’expérience client     |Satisfaction client (CSAT)         |Amélioration de 10 %         |12 mois         |No 4         |

> [!IMPORTANT]
> Le tableau ci-dessus est un exemple fictif et ne doit pas être utilisé pour définir des priorités. Dans de nombreux cas, ce tableau peut être considéré comme un contre-modèle quand les économies de coûts se situent au-dessus de l’expérience utilisateur du client.

Le tableau ci-dessus peut représenter avec précision les priorités de l’équipe de stratégie cloud et de l’équipe d’adoption du cloud. En raison de contraintes à terme, cette équipe insiste davantage sur la réduction des coûts informatiques et donne la priorité à une sortie de centre de données pour atteindre les réductions souhaitées en matière de coûts informatiques. Toutefois, en documentant les priorités en concurrence dans ce tableau, l’équipe d’adoption du cloud est habilitée à aider l’équipe de stratégie cloud à identifier les possibilités de mieux aligner l’implémentation de la stratégie globale du portefeuille.

### <a name="move-fast-while-maintaining-balance"></a>Déplacer rapidement tout en maintenant l’équilibre

Les conseils relatifs à la [rationalisation incrémentielle du patrimoine numérique](../digital-estate/index.md) suggèrent une approche dans laquelle la rationalisation commence par une position déséquilibrée. L’équipe de stratégie cloud doit évaluer chaque charge de travail pour s’assurer de sa compatibilité avec une approche de réhébergement. Une telle approche est suggérée, car elle permet l’évaluation rapide d’un patrimoine numérique complexe basé sur des données quantitatives. Une telle hypothèse initiale permet à l’équipe d’adoption du cloud de s’impliquer rapidement, ce qui réduit le temps nécessaire à l’atteinte des résultats métier. Toutefois, comme indiqué dans cet article, les questions qualitatives fournissent l’équilibre nécessaire dans le portefeuille. Cet article décrit le processus de création de l’équilibre promis.

### <a name="importance-of-sunset-and-retire-decisions"></a>Importance des décisions d’extinction et de mise hors service

Le tableau de la section relative à la [documentation des résultats métier](#document-business-outcomes) ci-dessus n’aboutit pas à un résultat clé qui permettrait de réduire les coûts informatiques. Lorsque les réductions de coûts informatiques se classent n’importe où dans la liste des résultats métier, il est important de prendre en compte la possibilité de mettre fin à des charges de travail ou de les mettre hors service. Dans certains scénarios, les économies de coûts peuvent provenir de la non-migration de charges de travail qui ne justifient pas un investissement à court terme. Certains clients ont rapporté des économies au-delà de 20 % de la réduction du coût total grâce à la mise hors service des charges de travail sous-exploitées.

Pour équilibrer le portefeuille et mieux refléter les décisions d’extinction et de mise hors service, les équipes de stratégie cloud et d’adoption du cloud sont encouragées à poser les questions suivantes pour chaque charge de travail dans le cadre des processus d’évaluation et de migration :

- La charge de travail a-t-elle été utilisée par des utilisateurs finaux au cours des six derniers mois ?
- Le trafic d’utilisateurs finaux est-il constant ou en augmentation ?
- Cette charge de travail sera-t-elle requise par l’entreprise dans 12 mois ?

Si la réponse à l’une de ces questions est « non », la charge de travail peut alors être une candidate à la mise hors service. Si le potentiel de mise hors service est confirmé par le propriétaire de l’application, il n’est peut-être pas judicieux de migrer la charge de travail. Cela soulève quelques questions de qualification :

- Un plan de mise hors service ou d’extinction peut-il être établi pour cette charge de travail ?
- Cette charge de travail peut-elle être mise hors service avant la sortie du centre de données ?

Si la réponse à ces deux questions est « oui », il est conseillé de _ne pas_ migrer la charge de travail. Cette approche peut aider à atteindre les objectifs de réduction des coûts et de sortie du centre de données.

Si la réponse à l’une des questions est « non », il peut être judicieux d’établir un plan d’hébergement de la charge de travail jusqu’à ce qu’elle puisse être mise hors service. Ce plan peut inclure le déplacement des ressources vers un centre de données à moindre coût ou un autre centre de données, ce qui permettrait également de réduire les coûts et de quitter un centre de données.

## <a name="adopt-process-changes"></a>Adopter les changements de processus

L’équilibrage du portefeuille nécessite une analyse qualitative supplémentaire durant le processus d’adoption, ce qui contribue à la rationalisation du portefeuille.

D’après les données du tableau figurant dans la section relative à la [documentation des résultats métier](#document-business-outcomes) ci-dessus, il existe un risque probable que le portefeuille s’oriente trop vers un modèle d’exécution axé sur la migration. Si l’expérience client était la priorité la plus élevée, un portefeuille axé sur les innovations serait plus probable. Ni l’un ni l’autre n’est bon ou mauvais, mais une trop grande inclinaison dans une direction entraîne généralement une diminution des rendements, ajoute une complexité inutile et augmente le temps d’exécution lié aux efforts d’adoption du cloud.

Pour réduire la complexité, vous devez suivre une approche traditionnelle de la rationalisation des portefeuilles, mais selon un modèle itératif. Les étapes suivantes décrivent un modèle qualitatif pour une telle approche :

- L’équipe de stratégie cloud gère un backlog classé par ordre de priorité des charges de travail à migrer.
- Les équipes de stratégie cloud et d’adoption du cloud organisent une réunion de planification des mises en production avant la fin de chaque mise en production.
- Lors de la réunion de planification des mises en production, les équipes s’accordent sur les 5 à 10 premières charges de travail dans le backlog classé par ordre de priorité.
- En dehors de la réunion de planification des mises en production, l’équipe d’adoption du cloud pose les questions suivantes aux propriétaires d’applications et aux experts en la matière :
  - Cette application peut-elle être remplacée par un équivalent Platform as a service (PaaS) ?
  - Cette application est-elle une application tierce ?
  - Le budget a-t-il été approuvé pour investir dans le développement continu de l’application au cours des 12 prochains mois ?
  - Le développement supplémentaire de cette application améliorerait-t-il l’expérience client ? Crée un avantage concurrentiel ? Génère des revenus supplémentaires pour l’entreprise ?
  - Les données de cette charge de travail contribueront-elles à une innovation en aval liée à BI, Machine Learning, l’IoT ou aux technologies connexes ?
  - La charge de travail est-elle compatible avec des plateformes d’applications modernes telles qu’Azure App Service ?
- Les réponses aux questions ci-dessus et toutes les autres analyses qualitatives requises influencent alors les ajustements du backlog classé par ordre de priorité. Ces ajustements peuvent inclure :
  - Si une charge de travail peut être remplacée par une solution PaaS, elle peut être entièrement supprimée du backlog de migration. Au minimum, une diligence raisonnable supplémentaire pour décider entre le réhébergement et le remplacement serait ajoutée en tant que tâche, ce qui réduirait temporairement la priorité de la charge de travail dans le backlog de migration.
  - Si une charge de travail est (ou devrait être) en cours de développement, elle peut mieux s’adapter à un modèle de refactorisation-réarchitecture-regénération. Étant donné que l’innovation et la migration nécessitent des compétences techniques différentes, les applications qui s’alignent sur une approche de refactorisation-réarchitecture-regénération doivent être gérées via un backlog d’innovation au lieu d’un backlog de migration.
  - Si une charge de travail fait partie d’une innovation en aval, il peut être judicieux de refactoriser la plateforme de données, mais de conserver les couches Application en tant que candidates au réhébergement. Une refactorisation mineure de la plateforme de données d’une charge de travail peut souvent être traitée dans une migration ou un backlog d’innovation. Ce résultat de rationalisation peut entraîner des éléments de travail plus détaillés dans le backlog, mais ne modifie pas les priorités.
  - Si une charge de travail n’est pas stratégique, mais qu’elle est compatible avec des plateformes informatiques modernes d’hébergement d’applications, il peut être judicieux d’effectuer une refactorisation mineure sur l’application pour la déployer en tant qu’application moderne. Cela peut contribuer aux économies globales en réduisant les exigences globales de la migration cloud en matière de licences IaaS et de système d’exploitation.
  - Si une charge de travail est une application tierce et que les données de cette charge de travail ne sont pas planifiées pour une utilisation dans le cadre d’une innovation en aval, il peut être préférable de la conserver comme option de réhébergement dans le backlog.

Ces questions ne doivent pas être l’étendue de l’analyse qualitative effectuée pour chaque charge de travail, mais elles aident à guider une conversation sur la façon d’aborder la complexité d’un portefeuille déséquilibré.

## <a name="migrate-process-changes"></a>Migrer les changements de processus

Pendant la migration, les activités d’équilibrage du portefeuille peuvent avoir un impact négatif sur la vélocité de la migration (vitesse à laquelle les ressources sont migrées). Les instructions suivantes expliquent pourquoi et comment aligner le travail afin d’éviter les interruptions de l’effort de migration.

La rationalisation des portefeuilles nécessite une diversité d’efforts techniques. Il est tentant pour les équipes d’adoption du cloud de faire correspondre la diversité de ce portefeuille aux efforts de migration. Les parties prenantes de l’entreprise demandent souvent à une seule équipe d’adoption du cloud de traiter l’intégralité du backlog de migration. Il s’agit rarement d’une approche souhaitable et, dans de nombreux cas, cela peut être contre-productif.

Ces différents efforts doivent être répartis entre deux équipes d’adoption du cloud ou plus. En utilisant un modèle à deux équipes comme exemple de mode d’exécution, l’équipe 1 est l’équipe de migration, et l’équipe 2 est l’équipe d’innovation. Pour les efforts plus importants, ces équipes peuvent être segmentées davantage pour résoudre d’autres approches, telles que les efforts de remplacement/PaaS ou la refactorisation mineure. L’exemple suivant présente les qualifications et les rôles nécessaires pour un réhébergement, une refactorisation ou une refactorisation mineure :

**Réhébergement :** Le réhébergement requiert que les membres de l’équipe implémentent des modifications axées sur l’infrastructure. En général, un outil comme Azure Site Recovery est utilisé pour migrer des machines virtuelles ou d’autres ressources vers Azure. Ce travail s’aligne bien sur les administrateurs de centres de données ou les implémenteurs informatiques. L’équipe de migration cloud est bien structurée pour effectuer ce travail à grande échelle. Il s’agit de l’approche la plus rapide pour migrer des ressources existantes dans la plupart des scénarios.

**Refactorisation :** Refactoriser oblige les membres de l’équipe à modifier le code source, à changer l’architecture d’une application ou à adopter de nouveaux services cloud. En général, cet effort utilise des outils de développement tels que Visual Studio et des outils de pipeline de déploiement comme Azure DevOps pour redéployer des applications modernisées sur Azure. Ce travail s’aligne bien sur les rôles de développement d’applications ou ceux de développement de pipelines DevOps. L’équipe d’innovation cloud est la mieux structurée pour effectuer ce travail. Dans cette approche, le remplacement des ressources existantes par des ressources cloud peut prendre plus de temps, mais les applications peuvent tirer parti des fonctionnalités natives du cloud.

**Refactorisation mineure :** Certaines applications peuvent être modernisées avec une refactorisation mineure au niveau des données ou de l’application. Ce travail oblige les membres de l’équipe à déployer des données sur des plateformes de données informatiques ou à apporter des modifications mineures à la configuration de l’application. Cela peut nécessiter un support limité des experts en matière de développement d’applications ou de données. Toutefois, ce travail est similaire au travail effectué par les implémenteurs informatiques lors du déploiement d’applications tierces. Ce travail peut facilement s’aligner sur l’équipe de migration cloud ou celle de stratégie cloud. Bien que cet effort ne soit pas aussi rapide qu’une migration de réhébergement, il prend moins de temps que les efforts de refactorisation.

Lors de la migration, les efforts devraient être segmentés des trois manières répertoriées ci-dessus et fournis par l’équipe appropriée dans l’itération appropriée. Même si vous devez diversifier le portefeuille, veillez également à ce que les efforts restent très concentrés et séparés.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment les [décisions du marché mondial](./global-markets.md) peuvent affecter votre parcours de transformation.

> [!div class="nextstepaction"]
> [Comprendre les marchés mondiaux](./global-markets.md)
