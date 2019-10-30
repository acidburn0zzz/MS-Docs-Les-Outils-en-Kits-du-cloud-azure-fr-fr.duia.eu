---
title: 'Innovation cloud : Interagir avec les appareils'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduction à l’innovation cloud – Interagir avec les appareils
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 5a9ec9f38d89683482d7f98923aa0ef2ccf201b9
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683229"
---
# <a name="ambient-experiences-interact-with-devices"></a>Expériences ambiantes : Interagir avec les appareils

Dans [développer en faisant preuve d’empathie vis-à-vis du client](./build.md), nous avons abordé les trois tests de la véritable innovation : résoudre un besoin client, inciter le client à revenir et mettre à l’échelle une base de cohortes de clients. Chaque test de votre hypothèse nécessitera des efforts et des itérations sur l’approche à adopter. Cet article donne un aperçu de certaines approches avancées visant à réduire ces effort par le biais d’**expériences ambiantes**. En interagissant avec des appareils, au lieu d’une application, le client peut être plus susceptible de se tourner d’abord vers votre solution pour répondre à leurs besoins.

## <a name="ambient-experiences"></a>Expériences ambiantes

Une expérience ambiante est une expérience numérique qui se réfère à l’environnement immédiat. Une solution qui comporte des expériences ambiantes s’efforce de répondre aux besoins du client au moment où il en a besoin. Dans la mesure du possible, la solution répond aux besoins du client sans quitter le déroulement naturel de ce qu’il faisait.

Dans l’économie numérique, la vie est pleine de distractions. Nous sommes tous bombardés de messages visuels et verbaux, que ce soit sur les réseaux sociaux, par e-mail ou sur Internet, chacun d’eux présentant un risque de distraction. Le risque de distraction augmente à chaque seconde entre le besoin du client et une interaction avec la solution. D’innombrables clients sont perdus dans ce bref laps de temps. Pour favoriser l’augmentation de la récurrence de l’adoption, réduisez le nombre de distractions en réduisant le temps consacré à trouver une solution (TTS).

## <a name="interacting-with-devices"></a>Interaction avec des appareils

Une expérience web standard est la technique de développement d’applications la plus couramment utilisée pour répondre aux besoins d’un client. L’hypothèse qui sous-tend cette approche est que le client sera devant son ordinateur. Si votre client exprime invariablement un besoin lorsqu’il se trouve devant son ordinateur portable, créez une application web. Cette application web fournira une « expérience ambiante » pour ce client, dans ce scénario. Toutefois, nous savons que ce scénario est de moins en moins probable dans la société moderne.

![Expériences ambiantes](../../_images/innovate/ambient-experiences.png)

Les expériences ambiantes, comme illustré ci-dessus, requièrent généralement plus qu’une application web. Grâce à des [mesures](./measure.md) et à un [apprentissage avec le client](./learn.md), le comportement qui conduit au déclencheur du besoin du client peut être observé, suivi et utilisé pour créer une meilleure expérience ambiante. Les éléments suivants résument quelques approches permettant d’intégrer des solutions ambiantes dans vos hypothèses ; vous trouverez plus de détails sur chacune dans les paragraphes suivants.

- **[Expérience mobile](#mobile-experience)**  : tout comme un ordinateur portable, les applications mobiles font généralement partie de l’environnement des clients. Dans certains scénarios, cela peut offrir un niveau d’interactivité suffisant pour rendre une solution ambiante.
- **[Réalité mixte](#mixed-reality) :** parfois, l’environnement naturel d’un client doit être modifié pour créer un environnement d’interaction. Cela crée un peu une fausse réalité dans laquelle le client peut interagir avec la solution et répondre à un besoin. Dans ce cas, la solution est ambiante dans le cadre de la fausse réalité.
- **[Réalité intégrée](#integrated-reality) :** s’approchant de l’ambiance réelle, les solutions de réalité intégrée sont axées sur l’utilisation d’un appareil qui existe dans la réalité du client pour intégrer la solution dans des comportements naturels. Un assistant virtuel est un excellent exemple d’intégration de la réalité dans l’environnement immédiat. Une option moins connue consiste à utiliser des technologies de l’Internet des objets (IoT) pour intégrer des appareils qui existent déjà dans l’environnement du client.
- **[Réalité ajustée](#adjusted-reality) :** quand l’une des solutions ambiantes ci-dessus utilise l’analyse prédictive dans le cloud pour définir et produire une interaction avec le client à travers l’environnement naturel, la solution a adapté la réalité.

Comprendre le besoin du client et mesurer l’impact sur ce dernier permettra de déterminer si une interaction avec l’appareil ou une expérience ambiante sera nécessaire pour valider votre hypothèse. Pour chacun de ces points de données, les sections suivantes vous aideront à trouver la meilleure solution.

## <a name="mobile-experience"></a>Expérience mobile

La première étape de l’expérience ambiante consiste à s’éloigner de l’ordinateur. Aujourd’hui, les consommateurs et les professionnels passent facilement d’un appareil mobile à un ordinateur. Chaque plateforme ou appareil utilisé par votre client crée une nouvelle expérience potentielle pour le client. L’ajout d’une expérience mobile qui étend la solution principale est le moyen le plus rapide d’améliorer l’intégration dans l’environnement immédiat du client. Bien qu’un appareil mobile soit éloigné des conditions ambiantes, il peut être plus proche du besoin du client.

Lorsque les clients sont mobiles et changent fréquemment d’emplacement, il peut s’agir de la forme d’expérience ambiante la plus pertinente pour une solution donnée. L’une des principales sources d’innovation au cours de la dernière décennie est l’expansion des solutions existantes pour intégrer une expérience mobile.

Vous pouvez consulter des exemples de cette approche dans Azure App Services. Lors des premières itérations, la [fonctionnalité d’application web d’Azure App Service](/azure/app-service/overview) peut être utilisée pour tester l’hypothèse. À mesure que les hypothèses deviennent plus complexes, la [fonctionnalité d’application mobile d’Azure App Services](/azure/app-service-mobile/) peut étendre l’application web pour l’exécuter sur diverses plateformes mobiles.

## <a name="mixed-reality"></a>Réalité mixte

Le niveau de maturité suivant pour les expériences ambiantes est l’augmentation ou la réplication de l’environnement du client grâce à des solutions de réalité mixte. Dans cette approche, la solution devient plus ambiante en créant une extension de la réalité dans laquelle le client peut opérer.

> [!IMPORTANT]
> Si un appareil de réalité virtuelle (RV) est nécessaire et *ne fait pas déjà partie de son environnement immédiat ou de ses comportements naturels*, la réalité augmentée/virtuelle est alors plus une expérience alternative et moins une expérience ambiante.

Cette forme d’expérience est de plus en plus courante pour les travailleurs à distance. L’utilisation de ces expériences croît encore plus rapidement dans les secteurs nécessitant une collaboration ou des compétences spécialisées qui ne sont pas immédiatement disponibles sur le marché local. Un scénario courant nécessitant une réalité augmentée dans le cadre d’un comportement naturel est le support destiné à l’implémentation centralisée d’un produit complexe pour une main d’œuvre distante. Dans ces scénarios, l’équipe centrale du support technique et le travailleur à distance peuvent tirer parti de la réalité augmentée pour détecter un problème ou installer le produit.

Pour le scénario ci-dessus ou d’autres scénarios similaires, un exemple d’expérience ambiante est l’utilisation d’ancres spatiales. Les ancres spatiales vous permettent de créer des expériences de réalité mixte avec des objets qui conservent leur emplacement sur les appareils et dans le temps. Grâce aux ancres spatiales, un comportement spécifique peut être capturé, enregistré et rendu persistant, fournissant une expérience ambiante la prochaine fois que l’utilisateur opère dans cet environnement augmenté. [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview) est un service qui adapte cette logique au cloud, permettant de partager les expériences entre les appareils et même entre les solutions.

## <a name="integrated-reality"></a>Réalité intégrée

Au-delà de la réalité mobile ou même de la réalité mixte se trouve l’utilisation de la réalité intégrée. Dans cette approche, l’objectif est de supprimer entièrement l’expérience numérique. Tout autour de nous se trouvent des appareils dotés de capacités de calcul et de connectivité. Ces appareils peuvent être utilisés pour collecter des données dans l’environnement immédiat sans que le client n’ait à toucher un téléphone, un ordinateur portable ou un appareil RV.

Cette forme d’expérience est idéale lorsqu’une certaine forme d’appareil se trouve systématiquement dans le même environnement que celui dans lequel le besoin du client se manifeste. Les scénarios les plus courants comprennent les ateliers, les ascenseurs ou même votre voiture. Ces types d’appareils de grande taille ont déjà une puissance de calcul. Vous pouvez également utiliser les données de l’appareil lui-même pour détecter les comportements des clients et les envoyer dans le cloud. Cette capture automatique des données relatives aux comportements des clients réduit considérablement la nécessité pour un client d’entrer des données. En outre, l’expérience web, mobile ou RV peut être utilisée comme retour d’informations pour partager ce qui a été appris dans la solution de réalité intégrée.

Voici quelques exemples de réalité intégrée dans Azure :

- [Les solutions Azure Internet of Things (IoT)](https://docs.microsoft.com/azure/iot-fundamentals), une collection de services dans Azure qui contribuent chacun à la gestion des appareils et du flux de données entre ces appareils et le cloud et entre le cloud et les utilisateurs finaux.
- [Azure Sphere](/azure-sphere), une combinaison de matériel et de logiciels, Azure Sphere est un moyen intrinsèquement sécurisé pour permettre à un appareil existant de transmettre des données en toute sécurité entre l’appareil et les solutions Azure IoT.
- [Azure Kinect Developers Kit](https://docs.microsoft.com/azure/Kinect-dk), des capteurs IA avec des modèles vocaux et de vision par ordinateur sophistiqués, qui peuvent collecter des données audio et visuelles à partir de l’environnement immédiat et alimenter votre solution grâce à ces entrées.

Tous trois peuvent être utilisés pour collecter des données dans l’environnement naturel, au moment où le client en a besoin. À partir de là, votre solution peut répondre à ces entrées de données pour répondre au besoin, parfois avant même que le client ne sache qu’un déclencheur pour ce besoin s’est manifesté.

## <a name="adjusted-reality"></a>Réalité ajustée

La forme d’expérience ambiante la plus avancée est la réalité ajustée, souvent appelée intelligence ambiante. La réalité ajustée est une approche qui consiste à utiliser les informations de votre solution pour modifier la réalité du client, sans qu’il soit nécessaire d’interagir directement avec une application. Dans cette approche, l’application que vous avez créée initialement pour prouver votre hypothèse n’est peut-être plus pertinente. Au lieu de cela, les appareils de l’environnement facilitent les entrées et les sorties pour répondre aux besoins des clients.

Les assistants virtuels/enceintes connectées peuvent fournir un excellent exemple de réalité ajustée. Seule, une enceinte connectée est un exemple de réalité intégrée simple. Ajoutez un éclairage intelligent et un détecteur de mouvement à une solution d’enceinte connectée, et il est facile de créer une solution de base qui allume les lumières lorsque vous entrez dans une pièce.

Les ateliers dans le monde entier fournissent des scénarios supplémentaires de réalité ajustée. Lors des premières phases de la réalité intégrée, les capteurs sur les appareils ont détecté des conditions, telles qu’une surchauffe, et ont signalé à un être humain un besoin de modification par le biais d’une application. Dans la réalité ajustée, le client peut toujours être impliqué. Cependant, le retour d’informations est plus restreint. Dans un atelier de réalité ajustée, un appareil détecterait la surchauffe d’une machine essentielle quelque part dans la chaîne de montage. Quelque part ailleurs dans l’atelier, un deuxième appareil ralentirait légèrement la production pour permettre à la machine de refroidir et de reprendre le rythme lorsque la situation serait résolue. Dans ce scénario, le client est un participant indirect. Le client utilise votre application pour définir les règles et comprendre comment ces règles ont influé sur la production, mais il ne serait un élément requis du retour d’informations.

Les services Azure de la section précédente, les [solutions Azure Internet of Things (IoT)](https://docs.microsoft.com/azure/iot-fundamentals), [Azure Sphere](/azure-sphere) et [Azure Kinect Developers Kit](https://docs.microsoft.com/azure/Kinect-dk) peuvent tous être des composants d’une solution de réalité ajustée. Votre application d’origine et votre logique métier serviraient d’intermédiaire entre l’entrée environnementale et la modification qui doit être apportée à l’environnement physique.

Un autre exemple de réalité ajustée est la création d’un jumeau numérique, qui est une représentation numérique d’un appareil physique, présentée sous forme d’ordinateur, de mobile ou de réalité mixte. Contrairement aux modèles 3D moins sophistiqués,un jumeau numérique reflète les données collectées à partir d’un appareil réel dans l’environnement physique. Cela permet à l’utilisateur d’interagir avec la représentation numérique d’une manière qui n’aurait jamais été possible dans le monde réel. Dans cette approche, les appareils physiques ajustent un environnement de réalité mixte. Toutefois, la solution consiste toujours à rassembler des données à partir d’une solution de réalité intégrée et à les utiliser pour façonner la réalité de l’environnement actuel du client.

Dans Azure, les jumeaux numériques sont créés et accessibles via un service appelé [Azure Digital Twins](https://docs.microsoft.com/azure/digital-twins/about-digital-twins).

## <a name="next-steps"></a>Étapes suivantes

Grâce à une meilleure compréhension des interactions entre les appareils et de l’expérience ambiante qui convient à votre solution, vous êtes maintenant prêt à explorer la discipline finale de l’innovation, [Prédire et influencer](./predict.md).

> [!div class="nextstepaction"]
> [Prédire et influencer](./predict.md)
