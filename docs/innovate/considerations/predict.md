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
ms.openlocfilehash: bcb01ada3589b733fe97de2689352ab414ef469b
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752987"
---
# <a name="predict-and-influence"></a>Prédire et influencer

Il existe deux catégories d’applications dans l’économie numérique : *historiques* et *prédictives*. Seule l’utilisation de données historiques, notamment de données quasi en temps réel, permet de satisfaire à de nombreuses exigences des clients. À l’heure actuelle, la plupart des solutions se concentrent principalement sur l’agrégation des données. Ensuite, elles traitent et partagent ces données avec le client, sous la forme d’une expérience numérique ou ambiante.

Comme la modélisation prédictive devient de plus en plus rentable et facile d’accès, les clients exigent des expériences visionnaires modernes afin d’améliorer les prises de décisions et les actions. Cependant, cette demande n’aboutit pas toujours à une solution prédictive. Dans la plupart des cas, un affichage historique peut fournir suffisamment de données pour éclairer le client lors de ses prises de décision.

Malheureusement, les clients ont souvent une vision à court terme. Leurs décisions sont dictées par leur environnement immédiat et leur sphère d’influence. Et comme les choix et leurs conséquences se complexifient avec le temps, un client prisonnier d’une vision à court terme peut passer à côté de ses besoins. Dans le même temps, lorsqu’une hypothèse est prouvée à l’échelle d’un vaste ensemble, l’entreprise qui la vérifie bénéficie alors d’un point de vue clair et global sur des milliers voire des millions de décisions de clients. Cette approche globale permet de voir des modèles dans leur ensemble et d’évaluer leur impact. La capacité prédictive est un investissement judicieux lorsqu’il est nécessaire de comprendre ces modèles afin de prendre les décisions les plus avantageuses pour le client.

## <a name="examples-of-predictions-and-influence"></a>Exemples de prédictions et d’influence

Diverses applications et expériences ambiantes utilisent des données pour faire des prédictions :

- **E-commerce :** En se basant sur les achats d’autres clients semblables, un site web d’e-commerce suggère à un client des produits susceptibles de l’intéresser.
- **Réalité ajustée :** IoT offre des instances plus avancées des fonctionnalités prédictives. Par exemple, certaines chaînes de montage sont dotées d’appareils capables de détecter si une machine se met à chauffer. Ces appareils transmettent leurs données dans le cloud, qui héberge un modèle prédictif qui détermine les actions appropriées. Selon les calculs de ce modèle, des instructions sont transmises du cloud vers un autre appareil chargé de ralentir la chaîne de montage jusqu’à ce que la machine puisse refroidir.
- **Produits de consommation :** Les téléphones portables, les maisons intelligentes et même votre voiture : tous ces biens utilisent des capacités prédictives grâce auxquelles ils suggèrent à l’utilisateur un comportement basé sur des facteurs tels que la localisation ou l’heure de la journée. Lorsqu’une prédiction correspond à l’hypothèse initiale, elle amène à agir. À un stade très avancé, cet alignement peut permettre de créer des produits comme une voiture autonome.

## <a name="develop-predictive-capabilities"></a>Développer des capacités prédictives

Les solutions dotées de fonctionnalités de prédiction exactes présentent généralement cinq caractéristiques principales : *des données*, *des insights*, *des modèles*, *des prédictions* et *des interactions*. Tous ces éléments sont nécessaires pour développer des capacités prédictives. Comme toutes les grandes innovations, le développement de capacités prédictives nécessite un [engagement dans l’itération](./index.md#commitment-to-iteration). Dans chaque itération, une ou plusieurs des caractéristiques suivantes ont évolué pour valider des hypothèses clients de plus en plus complexes.

![Procédure de développement des capacités prédictives](../../_images/innovate/predict-and-influence.png)

> [!CAUTION]
> Si l’hypothèse client développée dans [Développer en faisant preuve d’empathie vis-à-vis du client](./build.md) inclut des capacités prédictives, les principes décrits ici peuvent s’appliquer. Cependant, les capacités prédictives nécessitent un investissement significatif de temps et d’énergie. Lorsque les capacités prédictives sont des [pics techniques](./build.md#reduce-complexity-and-delay-technical-spikes), par opposition à une source de valeur réelle pour le client, nous vous suggérons de repousser les prédictions jusqu’à ce que les hypothèses du client aient été validées à l’échelle.

## <a name="data"></a>Données

Les données sont les plus élémentaires des caractéristiques mentionnées précédemment. Toutes les activités de développement d’inventions numériques génèrent des données. Ces données contribuent toutes au développement de prévisions. Si vous souhaitez en savoir plus sur les méthodes d’intégration des données dans une solution prédictive, consultez les articles [Démocratisation des données](./data.md) ou [Interaction avec des appareils](./devices.md).

Des sources de données variées peuvent être utilisées pour fournir des capacités prédictives :

## <a name="insights"></a>Insights

Les experts en la matière utilisent les données sur les besoins et les comportements des clients pour développer des insights métier de base en étudiant des données brutes. Ces informations permettent d’identifier les comportements des clients souhaités (ou bien les résultats indésirables). Au cours des itérations sur les prédictions, ces insights peuvent aider à identifier les corrélations potentielles susceptibles de générer des résultats positifs. Si vous souhaitez obtenir des conseils sur la façon de permettre aux experts de développer des insights, consultez l’article [Démocratisation des données](./data.md).

## <a name="patterns"></a>Modèles

Les utilisateurs ont toujours essayé de détecter des modèles dans de gros volumes de données. C’est pour cela que l’ordinateur a été inventé. La technologie Machine Learning accélère cette quête en détectant avec précision ces modèles, une compétence qui comprend le modèle de Machine Learning. Ces modèles sont ensuite appliqués, par le biais d’algorithmes Machine Learning, pour prédire les résultats lorsqu’un nouvel ensemble de données sera entré dans les algorithmes.

La technologie Machine Learning s’appuie sur les insights pour former et appliquer des modèles prédictifs aux données afin d’exploiter les modèles des données. Grâce à de multiples itérations de formations, de tests et d’adoptions, ces modèles et algorithmes peuvent prédire avec précision des résultats futurs.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) est le service cloud natif d’Azure. Il permet de construire et former des modèles basés sur vos données. Cet outil inclut également un [workflow pour accélérer le développement d’algorithmes Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/concept-azure-machine-learning-architecture). Ce workflow permet de développer des algorithmes via une interface visuelle ou Python.

Pour des modèles d’apprentissage machine plus robustes, les services [Machine Learning d’Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview) fournissent une plate-forme Machine Learning basée sur des clusters Apache Hadoop. Cette approche permet un contrôle plus granulaire des clusters sous-jacents, du stockage et des nœuds de calcul. Azure HDInsight offre également une intégration plus poussée, grâce à des outils tels que ScaleR et SparkR, qui génèrent des prédictions basées sur des données intégrées et ingérées, même en travaillant avec les données d’un flux. La [solution de prédiction des retards d’avions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-r-scaler-sparkr) démontre chacune de ces capacités avancées lorsqu’elle est utilisée pour prédire des retards d’avions en fonction des conditions météorologiques. La solution HDInsight permet également la mise en place de contrôles au niveau de l’entreprise, tels que la sécurisation des données, l’accès au réseau et l’analyse des performances pour opérationnaliser les modèles.

## <a name="predictions"></a>Prédictions

Après qu’un modèle est construit et formé, il peut être appliqué à l’aide d’API, qui peuvent faire des prédictions tout en fournissant une expérience numérique. La plupart de ces API sont développées à partir d’un modèle correctement formé, basé sur un modèle tiré de vos données. À mesure que de plus en plus de clients déploient des charges de travail quotidiennes dans le cloud, les API de prédiction utilisées par les fournisseurs de cloud en accélèrent l’adoption.

[Azure Cognitive Services](https://docs.microsoft.com/azure/cognitive-services) est un exemple d’API prédictive créée par un fournisseur de cloud. Ce service comprend des API prédictives pour la modération de contenu, la détection d’anomalies et des suggestions de personnalisation de contenu. Ces API sont prêtes à l’emploi et basées sur des modèles de contenu bien connus, que Microsoft a utilisés pour former des modèles. Chacune de ces API fait des prédictions basées sur les données que vous introduisez dans l’API.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning) vous permet de déployer des algorithmes personnalisés, que vous pouvez créer et former uniquement sur la base de vos propres données. En savoir plus sur le déploiement des prédictions avec [Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/how-to-deploy-and-where).

L’article [Configurer les clusters HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-provision-linux-clusters) traite des procédures de présentation des prédictions développées pour les services Machine Learning sur Azure HDInsight.

## <a name="interactions"></a>Interactions

Après qu’une prédiction est disponible via une API, vous pouvez l’utiliser pour influencer le comportement du client. Cette influence prend la forme d’une interaction. Une interaction avec un algorithme Machine Learning se produit dans le cadre de vos autres expériences numériques ou ambiantes. À mesure que les données sont collectées via l’application ou l’expérience, elles sont traitées par des algorithmes Machine Learning. Lorsque l’algorithme prédit un résultat, cette prédiction peut être partagée avec le client grâce à l’expérience existante.

En savoir plus sur la création d’une expérience ambiante par le biais d’une [solution de réalité ajustée](./devices.md#adjusted-reality).

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous vous êtes familiarisé avec les [disciplines de l’invention](./invention.md) et la [méthodologie d’innovation](./index.md), vous êtes prêt à apprendre comment [Développer en faisant preuve d’empathie vis-à-vis du client](./build.md).

> [!div class="nextstepaction"]
> [Développez en faisant preuve d’empathie](./build.md)
