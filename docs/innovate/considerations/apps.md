---
title: 'Innovation cloud : Impliquer par le biais d’applications'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Introduction à l’innovation cloud : impliquer par le biais d’applications'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 337eac12b3c01136f611d6a53693de4d29663f46
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752066"
---
# <a name="engage-through-applications"></a>Impliquer par le biais d’applications

Comme évoqué dans [Démocratisation des données](./data.md), les données représentent le nouveau carburant. qui alimente la plupart des innovations de l’économie numérique. Dans le contexte de cette analogie, les applications représentent les stations d’approvisionnement et l’infrastructure nécessaires pour fournir ce carburant aux bonnes personnes.

Dans certains cas, les données seules sont suffisantes pour produire des changements et répondre aux besoins des clients. De façon plus générale, la solution répondant aux besoins des clients nécessite des applications pouvant structurer les données et créer une expérience. Les applications incarnent le moyen par lequel nous impliquons l’utilisateur. Elles hébergent les processus nécessaires pour répondre aux déclencheurs clients. Elles offrent aux clients les outils leur permettant de fournir des données et d’obtenir de l’aide. Cet article résume quelques principes pouvant vous aider à vous aligner avec la solution d’application appropriée en fonction des hypothèses à valider.

![Impliquer par le biais d’applications](../../_images/innovate/engage-via-apps.png)

## <a name="shared-code"></a>Code partagé

Les équipes capables de répondre plus rapidement et plus précisément aux retours des clients, aux évolutions du marché et aux opportunités d’innovation sont celles dominent habituellement l’innovation sur leurs marchés respectifs. Le premier principe sur lequel reposent les applications innovantes est résumé dans la section [présentation de l’esprit de croissance](./learn.md#growth-mindset) : « Partager le code. » Au fil du temps, l’innovation émerge d’un thème culturel. L’innovation doit être soutenue par différentes perspectives et contributions.

Dans une perspective d’innovation, tout développement d’application doit commencer par un dépôt de code partagé. [GitHub](https://guides.github.com) est l’outil de gestion de dépôts de code le plus utilisé. Il vous permet de créer rapidement un dépôt de code partagé. [Azure Repos](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops) est également un ensemble d’outils de gestion de versions dans Azure DevOps Services que vous pouvez utiliser pour gérer votre code. Azure Repos offre deux types de gestion de version :

- [Git](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) : gestion de version distribuée
- [Team Foundation Version Control (TFVC)](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc) : gestion de versions centralisée

## <a name="citizen-developers"></a>Développeurs citoyens

Les développeurs professionnels représentent un composant vital de l’innovation. Quand une hypothèse se révèle exacte à grande échelle, les développeurs professionnels doivent stabiliser la solution et la préparer en vue d’un développement à grande échelle. La plupart des principes auxquels cet article fait référence nécessitent un support de la part de développeurs professionnels. Malheureusement, les tendances actuelles suggèrent qu’il y a une demande de développeurs professionnels dépassant le nombre de développeurs disponibles. En outre, quand un développement professionnel est nécessaire, le coût et le rythme de l’innovation peuvent se révéler moins favorables. En réponse à ces défis, les développeurs citoyens offrent un moyen d’adapter les efforts de développement et d’accélérer les premiers tests d’hypothèse.

L’utilisation de développeurs citoyens peut être une approche viable et efficace quand les premières hypothèses peuvent être validées à l’aide d’outils tels que [PowerApps](https://docs.microsoft.com/powerapps/powerapps-overview) pour les interfaces d’application, [AI Builder](https://docs.microsoft.com/powerapps/use-ai-builder) pour les processus et les prédictions, [Microsoft Flow](https://docs.microsoft.com/flow) pour les workflows et [Power BI](https://docs.microsoft.com/power-bi) pour la consommation de données.

> [!NOTE]
> Quand vous vous appuyez sur des développeurs citoyens pour tester les hypothèses, il est recommandé d’obtenir un support, une revue et de l’aide auprès de développeurs professionnels. Une fois qu’une hypothèse est validée à grande échelle, un processus de transition de l’application vers un modèle de programmation plus robuste accélère les retours sur l’innovation. L’implication de développeurs professionnels dès les premières définitions de processus peut conduire à des transitions plus fluides par la suite.

## <a name="intelligent-experiences"></a>Expériences intelligentes

Les expériences intelligentes combinent la vitesse et l’échelle des applications web modernes à l’intelligence des bots et services cognitifs qui, même indépendamment les uns des autres, peuvent être suffisants pour répondre aux besoins de vos clients. Lorsqu’elles sont combinées intelligemment, elles élargissent le spectre des besoins qui peuvent être pourvus via une expérience numérique, tout en aidant à maîtriser les coûts de développement.

### <a name="modern-web-apps"></a>Applications web modernes

Quand une application ou une expérience est nécessaire pour répondre à un besoin d’un client, les applications web modernes peuvent offrir le moyen le plus rapide de répondre à ce besoin. Les expériences web modernes peuvent impliquer des clients internes ou externes rapidement et permettre une itération rapide de la solution.

### <a name="infusing-intelligence"></a>Infusion de l’intelligence

Le Machine Learning et l’intelligence artificielle sont de plus en plus accessibles aux développeurs. De par la vaste disponibilité des API courantes, dotées de fonctionnalités prédictives, les développeurs bénéficient d’un accès étendu aux données et aux prédictions et peuvent ainsi répondre plus efficacement aux besoins du client.

L’ajout d’intelligence à une solution ouvre la voie à la reconnaissance vocale, à la traduction de texte, à la vision par ordinateur et même à la recherche visuelle. Grâce à ces fonctionnalités étendues, il est plus facile pour les développeurs de générer des solutions qui tirent parti de l’intelligence pour créer une expérience interactive et moderne.

### <a name="bots"></a>Bots

Les bots offrent une expérience qui donne l’impression aux utilisateurs d’avoir moins à faire à un ordinateur, et plus à une personne, ou du moins à un robot intelligent. Les bots peuvent être utilisés pour faire passer des tâches répétitives et simples (comme la réservation de table ou le recueil d’informations de profil) vers des systèmes automatisés qui ne nécessitent plus d’intervention humaine directe. Les utilisateurs conversent avec le bot par le biais de texte, de cartes interactives et avec la voix. Une interaction avec un bot peut aller d’une question-réponse rapide, à une conversation plus sophistiquée fournissant un accès à des services de manière plus intelligente.

Les bots sont comparables à des applications web modernes. Ils résident sur Internet et utilisent des API pour envoyer et recevoir des messages. Le contenu d’un bot varie considérablement selon son type. Les logiciels de bots modernes s’appuient sur une pile de technologies et d’outils qui offrent des expériences de plus en plus complexes sur un éventail de plateformes. Toutefois, un bot simple peut se contenter de recevoir un message et de répondre à l’utilisateur avec très peu de code.

Les bots peuvent effectuer les mêmes opérations que d’autres types de logiciels : lire et écrire des fichiers, utiliser des bases de données et des API, et traiter des tâches de calcul classiques. Ce qui rend les bots uniques, c’est leur utilisation de mécanismes généralement réservés à la communication entre humains.

## <a name="cloud-native-solutions"></a>Solutions cloud natives

Les applications cloud natives sont entièrement créées, et optimisées pour l’échelle et les performances du cloud. Les applications cloud natives sont généralement créées selon une approche microservices, serverless, basée sur des événements ou basée sur des conteneurs. Le plus souvent, elles tirent parti d’une combinaison d’architectures microservices, de services managés et de livraison continue pour offrir la fiabilité nécessaire et réduire le délai de mise sur le marché.

Une solution cloud native permet aux équipes de développement centralisées de conserver le contrôle de la logique métier sans avoir à recourir à des solutions centralisées monolithiques. Ce type de solution crée également un ancrage favorisant la cohérence entre les développeurs citoyens et les expériences modernes. Enfin, les solutions cloud natives offrent un accélérateur d’innovation. En effet, elles donnent toute latitude aux développeurs citoyens et professionnels pour innover de façon sûre avec très peu d’obstacles.

## <a name="innovate-through-existing-solutions"></a>Innover avec des solutions existantes

La version moderne d’une solution existante peut représenter le meilleur moyen de satisfaire de nombreuses hypothèses clients. Quand la logique métier actuelle répond aux besoins du client (ou y répond quasiment), vous pouvez être en mesure d’accélérer l’innovation en vous appuyant sur une solution modernisée.

La plupart des formes de modernisation (même une légère refactorisation de l’application) s’inscrivent dans la [méthodologie de migration](../../migrate/index.md) du framework d’adoption du cloud. Cette méthodologie guide les équipes d’adoption du cloud dans le processus de migration d’un [patrimoine numérique](../../digital-estate/index.md) vers le cloud. Le [Guide de migration Azure](../../migrate/azure-migration-guide/index.md) fournit une approche simplifiée de la même méthodologie, qui convient à un petit nombre de charges de travail ou même à une seule application.

Une fois la solution migrée et modernisée, il existe de nombreuses façons d’en tirer parti pour créer de nouvelles solutions innovantes répondant aux besoins des clients. Par exemple, les [développeurs citoyens](#citizen-developers) peuvent tester des hypothèses, ou les développeurs professionnels peuvent créer des [expériences intelligentes](#intelligent-experiences) ou des [solutions cloud natives](#cloud-native-solutions).

### <a name="extend-an-existing-solution"></a>Extension d’une solution existante

L’extension d’une solution est une forme courante de modernisation. Cette approche peut représenter la voie la plus rapide vers l’innovation quand l’hypothèse client présente les caractéristiques suivantes :

- La logique métier existante doit répondre au besoin existant du client (ou y répondre quasiment).
- Une expérience améliorée répondrait mieux aux besoins d’une cohorte de clients spécifique.
- La logique métier nécessaire à la solution de produit minimum viable (MVP) a été centralisée, généralement par le biais d’une approche [multiniveau](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier), [microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices), basée sur des services web ou basée sur des API. Cette approche consiste à wrapper la solution existante avec une nouvelle expérience hébergée dans le cloud. Cette solution est probablement disponible dans Azure App Services.

### <a name="rebuild-an-existing-solution"></a>Regénérer une solution existante

Si une application ne peut pas être étendue facilement, il peut être nécessaire de refactoriser la solution. Dans le cadre de cette approche, la charge de travail est migrée vers le cloud. Une fois la migration de l’application effectuée, certaines parties de l’application sont modifiées ou dupliquées en tant que services web ou [microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices) déployés parallèlement avec la solution existante. La solution parallèle basée sur les services peut être traitée comme une solution étendue. Cette approche consiste simplement à wrapper la solution existante avec une nouvelle expérience hébergée dans le cloud. Cette solution est probablement disponible dans Azure App Services.

> [!CAUTION]
> La refactorisation ou la réorganisation des solutions ou la centralisation de la logique métier peut rapidement déclencher un [spike technique](./build.md#reduce-complexity-and-delay-technical-spikes) chronophage,au lieu d’une source de valeur client. Il s’agit d’un risque pour l’innovation, particulièrement au début de la validation de l’hypothèse. En faisant preuve d’un peu de créativité dans la conception d’une solution, il doit être possible de créer un MVP n’impliquant pas la refactorisation de solutions existantes. Il est recommandé de retarder la refactorisation jusqu’à ce que l’hypothèse initiale puisse être validée à grande échelle.

## <a name="operating-model-innovations"></a>Innovations relatives aux modèles de fonctionnement

En plus des approches modernes et novatrices de la création d’applications, il y a eu des innovations notables dans les *opérations* d’application. Ces approches ont engendré de nombreux mouvements organisationnels. L’un des plus importants est le modèle de fonctionnement du [centre d’excellence du cloud](../../organize/cloud-center-of-excellence.md). Quand elles sont complètes et matures, les équipes commerciales peuvent fournir leur propre support opérationnel pour une solution.

Le type de modèle de gestion opérationnelle en libre-service, que l’on trouve dans un centre d’excellence du cloud, offre des contrôles plus stricts et des itérations plus rapides au sein de l’environnement de la solution. Pour accomplir ces buts, la responsabilité et le contrôle des opérations sont transférés à l’équipe commerciale.

Si vous essayez de mettre à l’échelle ou de répondre à une demande mondiale vis-à-vis d’une solution existante, cette approche peut être suffisante pour valider une hypothèse client. Une fois qu’une solution a été migrée et légèrement modernisée, l’équipe d’entreprise peut la mettre à l’échelle pour tester un large éventail d’opérations. Celles-ci impliquent généralement des cohortes de clients qui se soucient de l’impact des opérations informatiques sur les performances, la distribution mondiale et d’autres besoins qu’ils pourraient avoir.

## <a name="reduce-overhead-and-management"></a>Réduire la surcharge et l’effort de gestion

Plus il y a de composants à gérer dans une solution, plus l’itération de la solution sera lente. Cela signifie que vous pouvez accélérer l’innovation en réduisant l’impact des opérations sur la bande passante disponible.

Pour préparer les nombreuses itérations nécessaires à la fourniture d’une solution innovante, il est important de réfléchir à l’avance. Par exemple, minimisez les charges opérationnelles au début du processus en privilégiant les options serverless. Dans Azure, [Azure App Service](https://docs.microsoft.com/azure/app-service/overview) et les [conteneurs](https://docs.microsoft.com/azure/architecture/cloud-adoption/migrate/azure-best-practices/contoso-migration-rearchitect-container-sql) peuvent représenter des options d’application serverless.

En parallèle, Azure fournit des options de données de transaction serverless qui réduisent également la surcharge. La [liste des produits de base de données](https://docs.microsoft.com/azure/#pivot=products&panel=databases) fournit des options d’hébergement des données n’impliquant pas le recours à une plateforme de données complète.

## <a name="next-steps"></a>Étapes suivantes

Selon l’hypothèse et la solution, les principes décrits dans cet article peuvent vous aider à concevoir des applications en phase avec les définitions de MVP et impliquant les utilisateurs. Vous pouvez maintenant lire l’article sur la [favorisation de l’adoption](./ci-cd.md) et sur les principes correspondants, qui traite des méthodes permettant de mettre plus rapidement et plus efficacement l’application et les données entre les mains des clients.

> [!div class="nextstepaction"]
> [Favoriser l’adoption](./ci-cd.md)
