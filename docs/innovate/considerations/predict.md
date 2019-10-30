---
title: 'Innovation cloud : Prédire et influencer'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduction à l’innovation cloud - Prédire et influencer
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: e6187bc926aacd9a09e67b8cd2bfe94e5a4a42dd
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682627"
---
# <a name="predict-and-influence"></a>Prédire et influencer

Il existe deux catégories d’applications dans l’économie numérique : Les historiques et les prédictives. Les données des applications historiques, telles que les données en temps quasi réel, peuvent répondre à bon nombre des besoins de vos clients. À l’heure actuelle, la plupart des solutions se concentrent principalement sur l’agrégation de données. Puis elles traitent et partagent ensuite ces données avec le client, sous la forme d’une expérience numérique ou ambiante.

Comme la modélisation prédictive devient de plus en plus rentable et facile d’accès, les clients exigent des expériences plus modernes, qui améliorent les prises de décisions et les actions. Cependant, il n’est pas nécessaire que cette demande mène systématiquement au développement d’une solution prédictive. Dans la plupart des scénarios, un affichage historique peut fournir suffisamment de données pour éclairer le client lors de ses prises de décision.

Malheureusement, les clients ont une vision à court terme. Leurs décisions sont dictées par leur environnement immédiat et leur sphère d’influence. Et comme les choix et leurs conséquences se complexifient avec le temps, un client prisonnier d’une vision à court terme ne pourra plus obtenir ce dont il a vraiment besoin. Dans le même temps, lorsqu’une hypothèse est prouvée à l’échelle d’un vaste ensemble, l’entreprise qui la vérifie bénéficie alors d’un point de vue clair et global sur des milliers voire des millions de décisions de clients. Elle peut élaborer des modèles et mesurer leurs impacts. La capacité prédictive est un investissement judicieux lorsqu’il est nécessaire de comprendre des modèles, afin de prendre des décisions qui répondent aux besoins des clients.

## <a name="examples-of-predictions-and-influence"></a>Exemples de prédictions et d’influence

L’utilisation des données pour faire des prédictions a fait ses preuves dans diverses applications et expériences ambiantes.

- **:** La suggestion d’articles constitue un bon exemple de prédiction. En se basant sur les achats d’autres clients, un site web peut suggérer à un client des produits susceptibles de l’intéresser.
- **Réalité ajustée :** Nous pouvons trouver d’autres exemples dans ce que l’on appelle « l’Internet des objets », ou « objets connectés ». Ainsi, certaines chaînes de montage sont dotées d’appareils capables de détecter si une machine se met à chauffer. Ces appareils transmettent leurs données dans le cloud, qui héberge un modèle prédictif qui détermine les actions appropriées. Selon les calculs de ce modèle, des instructions sont transmises du cloud vers un autre appareil chargé de ralentir l’activité de la chaîne de montage jusqu’à ce que la machine puisse refroidir.
- **Produits de consommation :** Les téléphones portables, les maisons intelligentes et même votre voiture : tous ces biens contiennent un certain degré de capacités prédictives en suggérant des activités basées sur des facteurs tels que la géolocalisation ou l’heure de la journée. Lorsqu’une prédiction correspond à l’hypothèse initiale, elle influence votre comportement. Lorsque les deux s’affinent, la prédiction mène à l’action, comme une voiture à pilotage automatique.

## <a name="developing-predictive-capabilities"></a>Développement de capacités prédictives

Les solutions qui fournissent des prédictions s’avérant exactes suivent généralement une procédure d’exploitation de 5 éléments : des données, des idées, des modèles, des prédictions et des interactions. Tous ces éléments sont nécessaires pour développer des capacités prédictives. Comme toutes les grandes innovations, le développement des capacités prédictives nécessitera un [engagement à l’itération](./index.md#commitment-to-iteration). À chaque itération, un ou plusieurs des éléments suivants sont affinés pour valider des hypothèses de plus en plus complexes sur les clients.

![Procédure de développement des capacités prédictives](../../_images/innovate/predict-and-influence.png)

> [!CAUTION]
> Si une hypothèse sur un client développée à partir de l’article [ pour le client](./build.md) inclut des capacités prédictives, le contenu de cet article peut s’appliquer. Mais les capacités de prédiction exigent un investissement considérable en temps et en énergie. Si les capacités prédictives constituent des [pics techniques](./build.md#reduce-complexity-and-delay-technical-spikes), par opposition à une source de valeur réalisable pour le client, nous vous conseillons de reporter l’application des prédictions jusqu’à la validation à l’échelle de l’hypothèse sur le client.

## <a name="data"></a>Données

Les données constituent l’élément le plus simple à exploiter. La moindre interaction avec le monde numérique génère des données. Ces données peuvent toutes contribuer à l’élaboration de prévisions. Si vous souhaitez en savoir plus sur les méthodes d’intégration des données dans une solution prédictive, veuillez consulter les articles consacrés à la [démocratisation des données](./data.md) ou l’[interaction avec les appareils](./devices.md).

Un certain nombre de sources de données peuvent être utilisées pour fournir des capacités prédictives :

## <a name="insights"></a>Insights

Les experts en la matière exploitent les données sur les besoins et les comportements des clients pour développer des informations commerciales de base, ou « insights », en étudiant les données brutes. Ces informations permettent d’identifier les comportements des clients souhaités (ou d’autres résultats indésirables). Au cours des itérations sur les prédictions, ces insights peuvent aider à identifier les corrélations potentielles, susceptibles d’impacter les résultats positifs. Si vous souhaitez obtenir des conseils sur la façon de permettre aux experts en la matière d’acquérir des insights, veuillez consulter l’article sur la [démocratisation des données](./data.md).

## <a name="patterns"></a>Modèles

C’est dans la nature de l’être humain de développer des modèles à partir des informations qu’il perçoit. C’est pour cela que l’ordinateur a été inventé. L’apprentissage automatique, ou « Machine Learning », accélère la réalisation de cet objectif. Cette technologie permet de détecter des modèles en étudiant d’immenses quantités de données, appelées « modèle Machine Learning ». Ces modèles sont ensuite appliqués, par le biais d’algorithmes Machine Learning, pour prédire ce qui se passera lorsqu’un nouvel ensemble de points de données sera entré dans les algorithmes.

La technologie Machine Learning s’appuie sur les connaissances acquises pour former et appliquer des modèles prédictifs aux données afin de capitaliser sur les modèles des données et d’en tirer parti. Grâce à de multiples itérations de formations, de tests et d’adoptions, ces modèles et algorithmes peuvent prédire avec précision des résultats futurs.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) est un outil cloud natif d’Azure. Il permet de construire et former des modèles basés sur vos données. Cet outil inclut également un [workflow pour accélérer le développement d’algorithmes Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/concept-azure-machine-learning-architecture). Ce workflow permet de développer des algorithmes en utilisant une interface visuelle ou Python.

Pour des modèles d’apprentissage machine plus robustes, les services [Machine Learning d’Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview) fournissent une plate-forme Machine Learning basée sur des clusters Apache Hadoop. Cette approche permet un contrôle plus fin des clusters sous-jacents, du stockage et des nœuds de calcul. L’utilisation d’Azure HDInsight permet également une intégration plus poussée, grâce à des outils tels que ScaleR et SparkR, qui génèrent des prédictions basées sur des données intégrées et ingérées, même en travaillant avec les données d’un flux. La [solution de prédiction des retards d’avions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-r-scaler-sparkr) démontre chacune de ces capacités avancées en émettant des prédictions de retards d’avions en fonction des conditions météorologiques. La solution HDInsight permet également la mise en place de contrôles au niveau de l’entreprise, tels que la sécurisation des données, l’accès au réseau et l’analyse des performances pour opérationnaliser les modèles.

## <a name="predictions"></a>Prédictions

Lorsqu’un modèle est construit et formé, il peut être appliqué à l’aide d’API, qui peuvent faire des prédictions pendant la livraison d’une expérience numérique. La plupart de ces API sont développées à partir d’un modèle correctement formé, basé sur un modèle tiré de vos données. Cependant, comme de plus en plus de clients déploient des charges de travail communes dans le cloud, les fournisseurs de cloud peuvent à présent fournir des API de prédiction communes, pour accélérer l’adoption des prédictions.

[Azure Cognitive Services](https://docs.microsoft.com/azure/cognitive-services) est un exemple d’API prédictive construite par un fournisseur de cloud. Ce service comprend des API prédictives pour la modération de contenu, la détection d’anomalies ou des suggestions de personnalisation de contenu. Ces API sont prêtes à l’emploi, basées sur des modèles de contenu communs, que Microsoft a utilisés pour former des modèles. Chacune de ces API fait des prédictions basées sur les données que vous introduisez dans l’API.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning) permet le déploiement d’algorithmes personnalisés, que vous pouvez créer et former uniquement sur la base de vos propres données. Si vous souhaitez en savoir plus sur le déploiement des prédictions avec Azure Machine Learning, veuillez cliquer [ici](https://docs.microsoft.com/azure/machine-learning/service/how-to-deploy-and-where).

Cet article sur [la configuration des clusters HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-provision-linux-clusters) présente les procédures à suivre pour exposer les prédictions développées pour les services Machine Learning sur Azure HDInsight.

## <a name="interactions"></a>Interactions

Lorsqu’une prédiction est disponible via une API, vous pouvez l’utiliser pour influencer le comportement des clients. Cette influence consiste en une suite d’interactions. Une interaction avec un algorithme Machine Learning se produit dans le cadre de vos autres expériences numériques ou ambiantes. Au fur et à mesure que les données sont collectées via l’application ou l’expérience, elles sont traitées par des algorithmes Machine Learning. Lorsque l’algorithme prédit un résultat, cette prédiction peut être partagée avec le client grâce à l’expérience existante.

Découvrez les interactions possibles au sein d’une [solution de réalité ajustée](./devices.md#adjusted-reality), pour en savoir plus sur la création d’une interaction dans une expérience ambiante.

## <a name="next-steps"></a>Étapes suivantes

En vous basant sur les connaissances acquises sur les [disciplines d’innovation](./invention.md) de la [méthodologie d’innovation](./index.md), vous disposez à présent des outils techniques nécessaires pour [développer en faisant preuve d’empathie](./build.md).

> [!div class="nextstepaction"]
> [Développez en faisant preuve d’empathie](./build.md)
