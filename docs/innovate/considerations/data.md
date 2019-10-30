---
title: 'Innovation cloud : Démocratiser les données'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduction à l’innovation cloud – Démocratiser les données
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: c0ef1165fc416814e0563ec29c4ad5901a83b032
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683269"
---
# <a name="democratize-data"></a>Démocratiser les données

Le charbon, le pétrole et le potentiel humain ont été les trois principaux atouts de la révolution industrielle. Ces ressources ont permis de bâtir des entreprises, de déplacer des marchés et, en définitive, de changer des nations. Dans l’économie numérique, il existe trois ressources d’égale importance : les données, les appareils et le potentiel humain. Chacune d’entre elles recèle un grand potentiel d’innovation. Dans tout effort d’innovation, les données représentent le nouveau pétrole.

Aujourd’hui, dans toutes les entreprises, il existe des poches de données qui pourraient être exploitées pour trouver et répondre plus rapidement aux besoins des clients. Malheureusement, le processus d’exploitation de ces données pour stimuler l’innovation a longtemps été coûteux et chronophage. La plupart des solutions les plus précieuses pour les clients ne sont pas satisfaisantes, car les utilisateurs ne peuvent pas accéder aux données dont ils ont besoin.

La démocratisation des données est le processus qui consiste à mettre ces données entre les bonnes mains pour stimuler l’innovation. Ce processus peut prendre plusieurs formes, mais comprend généralement des solutions pour l’acquisition ou l’intégration des données brutes et la centralisation, le partage et la sécurisation des données. En cas de réussite, des experts de l’entreprise peuvent tirer parti des données pour vérifier les hypothèses. Dans de nombreux cas, les équipes d’adoption du cloud peuvent [développer en faisant preuve d’empathie vis-à-vis des clients](./build.md) en utilisant uniquement des données, ce qui a un impact rapide sur les besoins actuels des clients.

## <a name="process-of-democratizing-data"></a>Processus de démocratisation des données

Les phases suivantes guideront les décisions et les approches nécessaires à l’adoption d’une solution qui démocratise les données. Toutes les phases ne sont pas nécessairement requises pour créer une solution spécifique. Toutefois, chacune d’elles doit être évaluée lors de la création d’une solution à une hypothèse du client. Chacune offre une approche unique à la création de solutions innovantes.

![Processus de démocratisation des données](../../_images/innovate/democratize-data.png)

### <a name="share-data"></a>Partager des données

Lorsque le [développement fait preuve d’empathie vis-à-vis du client](./build.md), tous les processus se concentrent sur les besoins du client plutôt que sur une solution technique. La démocratisation des données ne fait pas exception ; nous commençons donc par partager les données. Pour démocratiser des données, le développement doit inclure une solution qui partage des données avec un consommateur de données. Le consommateur des données peut être un client direct ou un mandataire qui prend des décisions pour les clients. Les consommateurs de données approuvés peuvent analyser, interroger et créer des rapports sur des données centralisées, sans l’aide du personnel informatique.

De nombreuses innovations ont été lancées avec succès en tant que MVP qui proposent des processus manuels et pilotés par les données au nom du client. Dans ce modèle de conciergerie, un employé est le consommateur de données. Cet employé utilise les données pour aider le client. Chaque fois que le client engage le support manuel, une hypothèse peut être testée et validée. Cette approche est souvent un moyen rentable de tester une hypothèse axée sur le client avant d’investir massivement dans des solutions intégrées.

Les principaux outils permettant de partager des données directement avec les consommateurs de données incluent des rapports en libre-service ou des données intégrées dans d’autres expériences à l’aide d’outils tels que [Power BI](https://docs.microsoft.com/power-bi).

> [!NOTE]
> Avant de partager des données, il est important de prendre connaissance des sections suivantes. Le partage de données peut requérir une gouvernance pour assurer la protection des données partagées. De plus, les données peuvent être réparties sur plusieurs clouds et pourraient nécessiter une centralisation. Une grande partie des données peut même résider dans des applications qui nécessitent la collecte des données avant de les partager.

### <a name="govern-data"></a>Régir les données

Le partage de données peut rapidement produire un MVP utilisable lors de conversations avec les clients. Toutefois, les données seules ne sont que des données. Pour transformer ces données partagées en connaissances exploitables, il faut souvent un peu plus. Une fois qu’une hypothèse a été validée par le partage des données, la phase suivante du développement est souvent la gouvernance des données.

La gouvernance des données est un vaste sujet qui pourrait nécessiter son propre cadre dédié. Cela dépasse la portée du [Framework d’adoption du cloud](../../index.md). Toutefois, quelques aspects de la gouvernance des données doivent être pris en compte dès que l’hypothèse du client est validée. En voici quelques exemples :

- **Les données partagées sont-elles sensibles ?** [Les données doivent être classées secrètes](../../govern/policy-compliance/data-classification.md) avant tout partage public afin de protéger les intérêts des clients et de l’entreprise.
- **Si les données sont sensibles, ont-elles été sécurisées ?** La protection des données sensibles doit être obligatoire pour toutes les données démocratisées. L’exemple de la charge de travail axée sur la [sécurisation des solutions de données](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/securing-data-solutions.md) fournit quelques références relatives à la sécurisation des données.
- **Les données sont-elles cataloguées ?** La saisie de détails sur les données partagées facilitera la gestion des données à long terme. Les outils permettant de documenter les données, comme Azure Data Catalog, peuvent rendre ce processus beaucoup plus facile dans le cloud. L’aide relative à l’[annotation des données](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-annotate) et à la [documentation des sources de données](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-documentation) peuvent accélérer le processus.

Lorsque la démocratisation des données est importante pour une hypothèse axée sur le client, la gouvernance des données partagées devrait figurer quelque part dans le plan de mise en service pour protéger les clients, les consommateurs de données et l’entreprise.

### <a name="centralize-data"></a>Centraliser des données

Lorsque les données sont interrompues dans un environnement informatique, les possibilités d’innovation peuvent être extrêmement contraignantes, coûteuses et chronophages. Le cloud offre de nouvelles opportunités pour centraliser les données entre différents silos de données. Lorsque la centralisation de plusieurs sources de données est requise pour [développer en faisant preuve d’empathie vis-à-vis du client](./build.md), le cloud peut accélérer le test des hypothèses.

> [!CAUTION]
> La centralisation des données est un point de risque courant dans tout processus d’innovation. Lorsque la centralisation des données est un [pic technique](./build.md#reduce-complexity-and-delay-technical-spikes), par opposition à une source de valeur pour le client, il est recommandé de retarder la centralisation jusqu’à ce que l’hypothèse du client soit validée.

Si la centralisation des données est nécessaire, la première étape consiste à définir la banque de données appropriée pour les données centralisées. L’approche recommandée consiste à établir un entrepôt de données dans le cloud. Cette option évolutive fournira un emplacement central pour toutes les données. Ce type de solution est disponible dans les options de traitement analytique en ligne (OLAP) ou de Big Data.

Les architectures de référence pour les solutions [OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-analytical-processing) et [Big Data](https://docs.microsoft.com/azure/architecture/data-guide/big-data) peuvent vous aider à choisir la solution la plus pertinente dans Azure. Si une solution hybride est requise, l’architecture de référence pour [l’extension des données locales](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/hybrid-on-premises-and-cloud) peut également contribuer à accélérer le développement de la solution.

> [!IMPORTANT]
> Selon les besoins du client et la solution alignée, une solution plus simple peut suffire. L’architecte du cloud doit mettre l’équipe au défi d’envisager des solutions à moindre coût qui permettraient une validation plus rapide de l’hypothèse du client, surtout au début du développement. La section sur la collecte des données ci-dessous donne un aperçu de quelques scénarios qui pourraient donner lieu à une solution différente.

### <a name="collect-data"></a>Collecter les données

Lorsque les données doivent être centralisées pour répondre aux besoins d’un client, il est très probable que les données devront également être collectées auprès de différentes sources et transférées dans la banque de données centralisée. Il existe deux principales formes de collecte de données : Intégration et l’ingestion. Chacune offre un moyen différent de collecter des données.

**Intégration :** Les données existantes qui résident dans une banque de données existante peuvent être intégrées dans la banque de données centralisée à l’aide des techniques traditionnelles de déplacement des données. Cela est particulièrement courant pour les scénarios qui impliquent un stockage de données multicloud. Ces techniques consistent à extraire les données de la banque de données existante. Il faut ensuite les charger dans la banque de données centrale. À un moment de ce processus, les données sont souvent transformées pour être plus utiles et pertinentes dans la banque centrale.

Les outils cloud ont transformé ces techniques en outils de paiement à l’utilisation, réduisant ainsi la barrière à l’entrée pour la collecte et la centralisation des données. Des outils tels que Data Migration Service et Data Factory sont deux exemples courants dans Azure. L’architecture de référence pour une [fabrique de données avec une banque de données OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/etl) est un exemple d’une telle solution.

**Ingestion :** Certaines données ne se trouvent pas dans une banque de données existante. Lorsque ces données temporaires constituent une source principale d’innovation, d’autres approches doivent être prises en compte. Les données temporaires sont accessibles dans différentes sources existantes, telles que les applications, les API, les flux de données, les appareils IoT, la blockchain, le cache d’applications, le contenu multimédia ou même les fichiers plats.

Ces différentes formes de données peuvent être intégrées dans une banque de données centrale sur une solution OLAP ou Big Data. Toutefois, pour les premières itérations des cycles de développement, de mesure et d’apprentissage, une solution de traitement transactionnel en ligne (OLTP) peut être plus que suffisante pour valider une hypothèse client. Les solutions OLTP ne sont pas la solution de la plus haute qualité pour les scénarios de création de rapports. Toutefois, lorsque le [développement fait preuve d’empathie vis-à-vis du client](./build.md), l’accent est mis sur les besoins du client plutôt que sur les décisions techniques concernant les outils. Une fois que l’hypothèse du client est validée à l’échelle, une plateforme plus appropriée peut s’avérer nécessaire. L’architecture de référence sur les[banques de données OLTP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-transaction-processing) peut vous aider à déterminer quelle banque de données est la plus appropriée pour votre solution.

**Virtualisation :** L’intégration et l’ingestion de données peuvent parfois ralentir l’innovation. Lorsqu’une solution de virtualisation des données est déjà disponible, cette approche peut s’avérer plus pertinente. L’ingestion et l’intégration peuvent à la fois dupliquer les exigences de stockage/développement, ajouter une latence des données, augmenter la surface d’attaque, injecter des problèmes de qualité et accroître les efforts de gouvernance. La virtualisation des données est une alternative plus moderne qui laisse les données d’origine dans un emplacement unique et crée des requêtes directes ou mises en cache des données sources.

SQL Server 2017 et Azure SQL Data Warehouse prennent en charge [PolyBase](/sql/relational-databases/polybase/polybase-guide), qui est l’approche de la virtualisation des données la plus couramment utilisée dans Azure.

## <a name="next-steps"></a>Étapes suivantes

Avec une stratégie de démocratisation des données en place, l’étape suivante consiste à évaluer les approches permettant d’[impliquer les clients par le biais d’applications](./apps.md).

> [!div class="nextstepaction"]
> [Impliquer les clients par le biais d’applications](./apps.md)
