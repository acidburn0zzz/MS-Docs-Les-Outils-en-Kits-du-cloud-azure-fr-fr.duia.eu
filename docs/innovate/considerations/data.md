---
title: Démocratiser les données avec l’invention numérique
description: Découvrez le processus de démocratisation, qui consiste à mettre les données entre les bonnes mains pour tester des hypothèses et favoriser l’innovation.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 878127e904adb28b873f642bb7d8ef152d7e63ff
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80997192"
---
# <a name="democratize-data"></a>Démocratiser les données

Le charbon, le pétrole et le potentiel humain ont été les trois principaux atouts de la révolution industrielle. Ces ressources ont permis de bâtir des entreprises, de déplacer des marchés et, en définitive, de changer des nations. Dans l’économie numérique, il existe trois ressources d’égale importance : les données, les appareils et le potentiel humain. Chacune d'entre elles recèle un grand potentiel d'innovation. Dans tout effort d'innovation de l'ère moderne, les données représentent le nouveau pétrole.

Aujourd’hui, dans toutes les entreprises, il existe des poches de données qui pourraient être utilisées pour identifier et répondre plus efficacement aux besoins des clients. Malheureusement, le processus d’exploitation de ces données pour stimuler l’innovation a longtemps été coûteux et chronophage. La plupart des solutions les plus précieuses pour les clients ne sont pas satisfaisantes, car les utilisateurs ne peuvent pas accéder aux données dont ils ont besoin.

La démocratisation des données est le processus qui consiste à mettre ces données entre les bonnes mains pour stimuler l’innovation. Ce processus peut prendre différentes formes, mais il comprend généralement des solutions pour l'acquisition ou l'intégration des données brutes ainsi que pour la centralisation, le partage et la sécurisation des données. Lorsque ces méthodes fonctionnent, des experts de l'entreprise peuvent utiliser les données pour tester des hypothèses. Très souvent, les équipes d'adoption du cloud peuvent [développer en faisant preuve d'empathie vis-à-vis des clients](./build.md) en utilisant uniquement des données et en répondant rapidement aux besoins des clients existants.

## <a name="process-of-democratizing-data"></a>Processus de démocratisation des données

Les phases suivantes guideront les décisions et les approches nécessaires à l'adoption d'une solution de démocratisation des données. Toutes ces phases ne seront pas forcément nécessaires pour élaborer une solution spécifique. Néanmoins, vous devez évaluer chacune d'entre elles lorsque vous élaborez une solution en fonction d'une hypothèse client. Chacune offre une approche unique à la création de solutions innovantes.

![Processus de démocratisation des données](../../_images/innovate/democratize-data.png)

### <a name="share-data"></a>Partager des données

Lorsque vous [développez en faisant preuve d'empathie vis à vis du client](./build.md), tous les processus font passer les besoins du client avant une solution technique. Parce que la démocratisation des données ne fait pas exception, nous commençons par partager les données. Pour démocratiser des données, le développement doit inclure une solution qui partage des données avec un consommateur de données. Le consommateur de données peut être un client direct ou un mandataire qui prend des décisions pour les clients. Les consommateurs de données approuvés peuvent analyser, interroger et créer des rapports sur des données centralisées, sans l'aide du personnel informatique.

De nombreuses innovations ont été lancées avec succès en tant que produit minimum viable (PMV) qui proposent des processus manuels et pilotés par les données au nom du client. Dans ce modèle de conciergerie, un employé est le consommateur de données. Cet employé utilise les données pour aider le client. Chaque fois que le client a recours au support manuel, une hypothèse peut être testée et validée. Cette approche est souvent un moyen rentable de tester une hypothèse centrée sur le client avant d'investir massivement dans des solutions intégrées.

Les principaux outils permettant de partager des données directement avec les consommateurs de données sont les rapports en libre-service ou les données intégrées dans d'autres expériences à l'aide d'outils tels que [Power BI](https://docs.microsoft.com/power-bi).

> [!NOTE]
> Avant de partager des données, lisez les sections suivantes. Le partage de données peut nécessiter une gouvernance pour assurer la protection des données partagées. En outre, ces données peuvent être réparties sur plusieurs clouds ​​et nécessiter une centralisation. Une grande partie des données peut même se trouver dans des applications. Leur collecte est alors nécessaire avant tout partage.

### <a name="govern-data"></a>Régir les données

Le partage de données peut rapidement produire un PMV utilisable dans le cadre des conversations avec les clients. Toutefois, pour transformer ces données partagées en connaissances utiles et exploitables, il en faut généralement un peu plus. Une fois qu'une hypothèse a été validée par le partage des données, la phase suivante du développement est généralement la gouvernance des données.

La gouvernance des données est un vaste sujet qui pourrait nécessiter son propre framework. Ce degré de granularité dépasse la portée du [Framework d'adoption du cloud](../../index.md). Toutefois, certains aspects de la gouvernance des données doivent être pris en compte dès que l'hypothèse du client est validée. Par exemple :

- **Les données partagées sont-elles sensibles ?** [Les données doivent être classées secrètes](../../govern/policy-compliance/data-classification.md) avant d’être partagées publiquement afin de protéger les intérêts des clients et de l’entreprise.
- **Si les données sont sensibles, ont-elles été sécurisées ?** La protection des données sensibles doit être obligatoire pour toutes les données démocratisées. L’exemple de la charge de travail axée sur la [sécurisation des solutions de données](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/securing-data-solutions) fournit quelques références relatives à la sécurisation des données.
- **Les données sont-elles cataloguées ?** La saisie de détails sur les données partagées facilitera la gestion des données à long terme. Les outils permettant de documenter les données, comme Azure Data Catalog, peuvent rendre ce processus beaucoup plus facile dans le cloud. L’aide relative à l’[annotation des données](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-annotate) et à la [documentation des sources de données](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-documentation) peuvent accélérer le processus.

Lorsque la démocratisation des données est importante pour une hypothèse centrée sur le client, assurez-vous que la gouvernance des données partagées figure quelque part dans le plan de mise en service. Cela permettra de protéger les clients, les consommateurs de données et l'entreprise

### <a name="centralize-data"></a>Centraliser des données

Lorsque les données sont interrompues dans un environnement informatique, les possibilités d'innovation peuvent être extrêmement limitées, coûteuses et chronophages. Le cloud offre de nouvelles opportunités pour centraliser les données entre les silos de données. Lorsque la centralisation de plusieurs sources de données est requise pour [développer en faisant preuve d'empathie vis-à-vis du client](./build.md), le cloud peut accélérer le test des hypothèses.

> [!CAUTION]
> Quel que soit le processus d'innovation, la centralisation des données constitue toujours un risque. Lorsque la centralisation des données représente un [défi technique](./build.md#reduce-complexity-and-delay-technical-spikes) (par opposition à une source de valeur pour le client), nous vous conseillons de reporter la centralisation jusqu'à ce que les hypothèses du client aient été confirmées.

Si une centralisation des données est nécessaire, vous devez d'abord définir le magasin de données approprié pour les données centralisées. L'approche recommandée consiste à établir un entrepôt de données dans le cloud. Cette option évolutive fournira un emplacement central pour toutes vos données. Ce type de solution est disponible dans les options de traitement analytique en ligne (OLAP) ou de Big Data.

Les architectures de référence des solutions [OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-analytical-processing) et [Big Data](https://docs.microsoft.com/azure/architecture/data-guide/big-data) peuvent vous aider à choisir la solution la plus pertinente dans Azure. Si une solution hybride est requise, l'architecture de référence de [l'extension des données locales](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/hybrid-on-premises-and-cloud) peut également contribuer à accélérer le développement de la solution.

> [!IMPORTANT]
> Selon les besoins du client et la solution proposée, une approche plus simple peut suffire. L'architecte du cloud doit mettre l'équipe au défi d'envisager des solutions à moindre coût qui permettraient une confirmation plus rapide de l'hypothèse du client, en particulier au début du développement. La section suivante sur la collecte des données couvre certains scénarios qui peuvent vous inspirer une autre solution en fonction de votre situation.

### <a name="collect-data"></a>Collecter les données

Lorsque vous devez centraliser des données pour répondre aux besoins d'un client, vous pouvez également être amené à collecter les données issues de différentes sources et les transférer vers le magasin de données centralisé. Il existe deux principales formes de collecte de données : l'*intégration* et l'*ingestion*.

**Intégration :** Les données qui résident dans un magasin de données existant peuvent être intégrées au magasin de données centralisé en utilisant des techniques traditionnelles de déplacement des données. Cela est particulièrement courant pour les scénarios qui impliquent un stockage de données multicloud. Ces techniques consistent à extraire les données du magasin de données existant, puis à les charger dans le magasin de données central. À un moment donné de ce processus, les données sont généralement transformées pour être plus utiles et pertinentes dans le magasin central.

Les outils cloud ont transformé ces techniques en outils de paiement à l'utilisation, réduisant ainsi les obstacles à l'entrée pour la collecte et la centralisation des données. Azure Database Migration Service et Azure Data Factory sont des exemples d’outils de ce type. L'architecture de référence d'une [fabrique de données avec magasin de données OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/etl) est un exemple de solution de ce type.

**Ingestion :** Certaines données ne figurent dans aucun magasin de données existant. Lorsque ces données temporaires constituent une source principale d'innovation, vous devez envisager d'autres approches. Les données temporaires figurent dans différents types de sources existantes, comme les applications, les API, les flux de données, les appareils IoT, les blockchains, le cache des applications, le contenu multimédia ou même les fichiers plats.

Vous pouvez intégrer ces différentes formes de données dans un magasin de données central sur une solution OLAP ou Big Data. Toutefois, pour les premières itérations des cycles de développement, de mesure et d'apprentissage, une solution de traitement transactionnel en ligne (OLTP) peut être plus que suffisante pour confirmer une hypothèse client. Les solutions OLTP ne sont pas les meilleures en termes de qualité pour les scénarios de création de rapports. Mais lorsque vous [développez en faisant preuve d'empathie vis-à-vis des clients](./build.md), il est plus important de vous concentrer sur les besoins du client que sur les décisions techniques relatives aux outils. Une fois l'hypothèse du client confirmée à grande échelle, une plateforme plus appropriée peut s'avérer nécessaire. L'architecture de référence des [magasins de données OLTP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-transaction-processing) peut vous aider à déterminer le magasin de données le plus approprié pour votre solution.

**Virtualisation :** L’intégration et l’ingestion de données peuvent parfois ralentir l’innovation. Lorsqu'une solution de virtualisation des données est déjà disponible, cette approche peut s'avérer plus raisonnable. L'ingestion et l'intégration peuvent à la fois dupliquer les exigences relatives au stockage et au développement, ajouter une latence des données, augmenter la surface d'attaque, générer des problèmes de qualité et accroître les efforts de gouvernance. La virtualisation des données est une alternative plus contemporaine qui laisse les données d'origine dans un emplacement unique et crée des requêtes directes ou mises en cache des données sources.

SQL Server 2017 et Azure SQL Data Warehouse prennent en charge [PolyBase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide), qui est l’approche de la virtualisation des données la plus couramment utilisée dans Azure.

## <a name="next-steps"></a>Étapes suivantes

Lorsqu'une stratégie de démocratisation des données est en place, l'étape suivante consiste à évaluer les approches permettant d'[impliquer les clients par le biais d'applications](./apps.md).

> [!div class="nextstepaction"]
> [Impliquer les clients par le biais d’applications](./apps.md)
