---
title: 'Innovation cloud : impliquer par le biais d’applications'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Introduction à l’innovation cloud : impliquer par le biais d’applications'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 3db2349e3c1da7c80f3089ea187a3de72d006d1f
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683286"
---
# <a name="engage-through-applications"></a>Impliquer par le biais d’applications

Comme évoqué dans l’article sur la [démocratisation des données](./data.md), les données représentent le nouveau carburant qui alimente la plupart des innovations de l’économie numérique. Dans le contexte de cette analogie, les applications représentent les stations d’approvisionnement et l’infrastructure nécessaires pour fournir ce carburant aux bonnes personnes.

Dans certains cas, les données sont suffisantes pour produire des changements et répondre aux besoins des clients. De façon plus générale, la solution répondant aux besoins des clients nécessitera des applications pouvant structurer les données et créer une expérience. Les applications incarnent le moyen par lequel nous impliquons l’utilisateur. Elles hébergent les processus nécessaires pour répondre aux déclencheurs clients. Elles offrent aux clients les outils leur permettant de fournir des données et d’obtenir de l’aide. Cet article décrit quelques principes simplifiant l’alignement de la solution d’application appropriée en fonction des hypothèses à valider.

![Impliquer par le biais d’applications](../../_images/innovate/engage-via-apps.png)

## <a name="shared-code"></a>Code partagé

Les équipes capables de répondre plus rapidement et plus précisément aux retours des clients, aux évolutions du marché et aux opportunités d’innovation sont celles qui domineront l’innovation sur leurs marchés respectifs. Le premier principe sur lequel reposent les applications innovantes est décrit dans la section « Partager le code » de la [présentation de l’esprit de croissance](./learn.md#growth-mindset). L’innovation au fil du temps ne peut s’appuyer que sur un axe culturel. L’innovation doit être soutenue par différentes perspectives et contributions.

Dans une perspective d’innovation, tout développement d’application doit commencer par un dépôt de code partagé. [GitHub](https://guides.github.com/) est l’outil de gestion de dépôts de code le plus courant. Il permet de créer un dépôt de code partagé en quelques clics. Vous pouvez également utiliser la fonctionnalité [Azure Repos](/azure/devops/repos/get-started/what-is-repos?view=azure-devops) d’Azure DevOps pour créer un dépôt [Git](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) ou [Team Foundation](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc).

## <a name="citizen-developers"></a>Développeurs citoyens

Les développeurs professionnels représentent un composant vital de l’innovation. Quand une hypothèse se révèle exacte à grande échelle, les développeurs professionnels doivent stabiliser la solution et la préparer en vue d’un développement à grande échelle. La plupart des principes auxquels cet article fait référence nécessitent un support de la part de développeurs professionnels. Malheureusement, les tendances actuelles suggèrent que le nombre de développeurs professionnels disponibles ne suffit pas à satisfaire la demande. En outre, quand la rigueur d’un développement professionnel est nécessaire, le coût et le rythme de l’innovation peuvent se révéler moins favorables. Les développeurs citoyens offrent un moyen d’adapter les efforts de développement et d’accélérer les premiers tests d’hypothèse.

Les développeurs citoyens peuvent incarner une approche judicieuse quand les premières hypothèses peuvent être validées à l’aide d’outils tels que [PowerApps](https://docs.microsoft.com/powerapps/powerapps-overview) pour les interfaces d’application, [AI Builder](/powerapps/use-ai-builder) pour les processus et les prédictions, [Microsoft Flow](https://docs.microsoft.com/flow) pour les workflows ou [Power BI](https://docs.microsoft.com/power-bi) pour la consommation de données.

> [!NOTE]
> Quand vous vous appuyez sur des développeurs citoyens pour tester les hypothèses, il est recommandé d’obtenir un support, une revue et de l’aide auprès de développeurs professionnels. Une fois qu’une hypothèse est validée à grande échelle, un processus de transition de l’application vers un modèle de programmation plus robuste accélère les retours sur l’innovation. L’implication de développeurs professionnels dès les premières définitions de processus peut conduire à des transitions plus fluides par la suite.

## <a name="intelligent-experiences"></a>Expériences intelligentes

Les expériences intelligentes combinent la vitesse et l’échelle des applications web modernes à l’intelligence des bots et services cognitifs qui, même indépendamment les uns des autres, peuvent être suffisants pour répondre aux besoins de vos clients. Le spectre combiné des besoins pouvant être satisfaits par une expérience numérique est étendu, mais les investissements en développement restent maîtrisables.

### <a name="modern-web-apps"></a>Applications web modernes

Quand une application ou une expérience est nécessaire pour répondre à un besoin d’un client, les applications web modernes peuvent offrir le moyen le plus rapide de répondre à ce besoin. Les expériences web modernes peuvent impliquer des clients internes ou externes rapidement et permettre une itération rapide de la solution.

### <a name="infusing-intelligence"></a>Infusion de l’intelligence

Le machine learning et l’intelligence artificielle sont toujours plus accessibles aux développeurs. De par la vaste disponibilité des API courantes, dotées de fonctionnalités prédictives, les développeurs bénéficient d’un accès étendu aux données et aux prédictions et peuvent ainsi répondre plus efficacement aux besoins du client.

L’ajout d’intelligence à une solution ouvre la voie à la reconnaissance vocale, à la traduction de texte, à la vision par ordinateur et même à la recherche visuelle. Grâce à ces fonctionnalités étendues, il est plus facile pour les développeurs de générer des solutions qui tirent parti de l’intelligence pour créer une expérience interactive et moderne.

### <a name="bots"></a>Bots

Les bots offrent une expérience qui donne l’impression aux utilisateurs d’avoir moins à faire à un ordinateur, et plus à une personne, ou du moins à un robot intelligent. Les bots peuvent être utilisés pour faire passer des tâches répétitives et simples, comme la réservation de table ou le recueil d’informations de profil, vers des systèmes automatisés qui ne nécessitent plus d’intervention humaine directe. Les utilisateurs conversent avec le bot à l’aide de texte, de cartes interactives et avec la voix. Une interaction avec un bot peut se composer d’une question-réponse rapide, ou il peut s’agir d’une conversation plus sophistiquée fournissant un accès à des services de manière plus intelligente.

Les bots sont comparables à des applications web modernes. Ils résident sur Internet et utilisent des API pour envoyer et recevoir des messages. Le contenu d’un bot varie considérablement selon son type. Les logiciels de bots modernes s’appuient sur une pile de technologies et d’outils qui offrent des expériences de plus en plus complexes sur un large éventail de plateformes. Toutefois, un bot simple peut se contenter de recevoir un message et de répondre à l’utilisateur avec très peu de code.

Les bots peuvent effectuer les mêmes opérations que d’autres types de logiciels : lire et écrire des fichiers, utiliser des bases de données et des API, et réaliser des tâches de calcul classiques. Ce qui rend les bots uniques, c’est leur utilisation de mécanismes généralement réservés à la communication entre humains.

## <a name="cloud-native-solutions"></a>Solutions cloud natives

Les applications cloud natives sont créées de A à Z. Elles sont optimisées pour l’échelle et les performances du cloud. Les applications cloud natives sont généralement créées selon une approche microservices, serverless, basée sur des événements ou basée sur des conteneurs. Le plus souvent, elles tirent parti d’une combinaison d’architectures microservices, de services managés et de livraison continue pour offrir la fiabilité nécessaire et réduire le délai de mise sur le marché.

Une solution cloud native permet aux équipes de développement centralisées de conserver le contrôle de la logique métier sans avoir à recourir à des solutions centralisées monolithiques. Ce type de solution crée également un ancrage favorisant la cohérence entre les développeurs citoyens et les expériences modernes. Enfin, les solutions cloud natives offrent un accélérateur d’innovation. En effet, elles donnent toute latitude aux développeurs citoyens et professionnels pour innover de façon sûre avec très peu d’obstacles.

## <a name="innovate-through-existing-solutions"></a>Innover avec des solutions existantes

La version moderne d’une solution existante peut représenter le meilleur moyen de satisfaire de nombreuses hypothèses clients. Quand la logique métier actuelle répond aux besoins du client (ou y répond quasiment), vous pouvez être en mesure d’accélérer l’innovation en vous appuyant sur une solution modernisée.

La plupart des formes de modernisation (même une légère refactorisation de l’application) s’inscrivent dans la [méthodologie de migration](../../migrate/index.md) du framework d’adoption du cloud. Cette méthodologie guide les équipes d’adoption du cloud dans les processus de migration d’un [patrimoine numérique](../../digital-estate/index.md) vers le cloud. Le [Guide de migration Azure](../../migrate/azure-migration-guide/index.md) fournit une approche simplifiée de la même méthodologie, qui convient à un petit nombre de charges de travail ou même à une seule application.

Une fois la solution migrée et modernisée, il existe de nombreuses façons d’en tirer parti pour créer de nouvelles solutions innovantes répondant aux besoins des clients. Par exemple, les [développeurs citoyens](#citizen-developers) peuvent tester des hypothèses, ou les développeurs professionnels peuvent créer des [expériences intelligentes](#intelligent-experiences) ou des [solutions cloud natives](#cloud-native-solutions).

### <a name="extend-an-existing-solution"></a>Extension d’une solution existante

L’extension d’une solution est une forme courante de modernisation. Cette approche peut représenter la voie la plus rapide vers l’innovation quand l’hypothèse client présente les caractéristiques suivantes :

- La logique métier existante doit répondre au besoin existant du client (ou y répondre quasiment).
- Une expérience améliorée répondrait mieux aux besoins d’une cohorte de clients spécifique.
- La logique métier nécessaire à la solution MVP a été centralisée, généralement par le biais d’une approche [multiniveau](/azure/architecture/guide/architecture-styles/n-tier), [microservices](/azure/architecture/guide/architecture-styles/microservices), basée sur des services web ou basée sur des API. Cette approche consiste à wrapper la solution existante avec une nouvelle expérience hébergée dans le cloud. Cette solution est probablement disponible dans Azure App Services.

### <a name="rebuild-an-existing-solution"></a>Regénérer une solution existante

Si une application ne peut pas être étendue facilement, il peut être nécessaire de refactoriser la solution. Dans le cadre de cette approche, la charge de travail est migrée vers le cloud. Une fois la migration effectuée, certaines parties de l’application sont modifiées ou dupliquées en tant que services web ou [microservices](/azure/architecture/guide/architecture-styles/microservices) déployés parallèlement à la solution existante. La solution parallèle basée sur les services peut être traitée comme une solution étendue. Cette approche consiste simplement à wrapper la solution existante avec une nouvelle expérience hébergée dans le cloud. Cette solution est probablement disponible dans Azure App Services.

> [!CAUTION]
> La refactorisation ou la réorganisation des solutions ou la centralisation de la logique métier peut rapidement devenir un [spike technique](./build.md#reduce-complexity-and-delay-technical-spikes) chronophage, à l’opposé de la source de valeur client. Il s’agit d’un risque pour l’innovation, particulièrement au début de la validation de l’hypothèse. En faisant preuve d’un peu de créativité dans la conception d’une solution, il doit être possible de créer un MVP n’impliquant pas la refactorisation de solutions existantes. Il est recommandé de retarder la refactorisation jusqu’à ce que l’hypothèse initiale puisse être validée à grande échelle.

## <a name="operating-model-innovations"></a>Innovations relatives aux modèles de fonctionnement

Au-delà des approches modernes de la création d’applications basées sur l’innovation, le fonctionnement des applications a également fait l’objet de diverses innovations. Ces approches ont engendré de nombreux mouvements organisationnels. L’un des plus importants est le mouvement vers les modèles de fonctionnement du [centre d’excellence du cloud](../../organize/cloud-center-of-excellence.md). Quand elles sont complètes et matures, les équipes commerciales peuvent fournir leur propre support opérationnel pour une solution.

Le type de modèle de gestion opérationnelle en libre-service, que l’on trouve dans un centre d’excellence du cloud, offre des contrôles plus stricts et des itérations plus rapides au sein de l’environnement de la solution. Pour cela, la responsabilité et le contrôle des opérations sont transférés à l’équipe commerciale.

Quand l’objectif consiste à mesurer ou répondre à une demande mondiale vis-à-vis d’une solution existante, cette approche peut être suffisante pour valider une hypothèse client. Une fois les solutions migrées et légèrement modernisées, l’équipe commerciale a la possibilité de les mettre à l’échelle pour tester une diversité d’hypothèses relatives à des cohortes de clients préoccupés par l’impact des opérations informatiques sur les performances, la distribution mondiale ou d’autres attentes qu’ils pourraient avoir.

## <a name="reduce-overhead-and-management"></a>Réduire la surcharge et l’effort de gestion

Plus il y a de composants à gérer dans une solution, plus l’itération de la solution sera lente. Accélérez l’innovation en réduisant l’impact des opérations sur la vélocité disponible.

Pour préparer les nombreuses itérations nécessaires à la fourniture d’une solution innovante, il est important de réfléchir à l’avance. Minimisez les charges opérationnelles au début du processus en privilégiant les options serverless.

Dans Azure, [Azure App Service](https://docs.microsoft.com/azure/app-service/overview) et les [conteneurs](https://docs.microsoft.com/azure/architecture/cloud-adoption/migrate/azure-best-practices/contoso-migration-rearchitect-container-sql) peuvent représenter des options d’application serverless.

En parallèle, Azure fournit des options de données de transaction serverless qui réduisent également la surcharge. La [liste des produits de base de données](https://docs.microsoft.com/azure/#pivot=products&panel=databases) présente des options d’hébergement des données n’impliquant pas le recours à une plateforme de données complète.

## <a name="next-steps"></a>Étapes suivantes

Selon l’hypothèse et la solution, les principes décrits dans cet article peuvent vous aider à concevoir des applications en phase avec les définitions de MVP et impliquant les utilisateurs. Vous pouvez maintenant lire l’article sur la [favorisation de l’adoption](./ci-cd.md) et sur les principes correspondants, qui traite des méthodes permettant de mettre plus rapidement l’application et les données entre les mains des clients.

> [!div class="nextstepaction"]
> [Favoriser l’adoption](./ci-cd.md)