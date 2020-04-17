---
title: Interagir avec des appareils via l’invention numérique
description: Découvrez des approches avancées permettant de réduire les efforts d’innovation grâce à l’interaction du client avec des expériences ambiantes et des appareils, plutôt qu’avec des applications.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: f7207b71f88bb311d28c8d1794dde7fddc425a30
ms.sourcegitcommit: 7d3fc1e407cd18c4fc7c4964a77885907a9b85c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "80433299"
---
# <a name="ambient-experiences-interact-with-devices"></a>Expériences ambiantes : Interagir avec les appareils

Dans [Développer en faisant preuve d’empathie vis-à-vis du client](./build.md), nous avons abordé les trois tests de la véritable innovation : résoudre un besoin client, inciter le client à revenir et mettre à l’échelle une base de cohortes de clients. Chaque test de votre hypothèse nécessite des efforts et des itérations sur l’approche à adopter. Cet article donne un aperçu de certaines approches avancées visant à réduire ces effort par le biais d’*expériences ambiantes*. En interagissant avec des appareils au lieu d’une application, le client peut être plus susceptible de se tourner d’abord vers votre solution.

## <a name="ambient-experiences"></a>Expériences ambiantes

Une expérience ambiante est une expérience numérique qui se réfère à l’environnement immédiat. Une solution qui comporte des expériences ambiantes vise à répondre aux besoins du client au moment où il en a besoin. Dans la mesure du possible, la solution répond aux besoins du client sans quitter le flux d’activité qui l’a déclenchée.

Dans l’économie numérique, la vie est pleine de distractions. Nous sommes tous bombardés de messages visuels et verbaux, que ce soit sur les réseaux sociaux, par e-mail ou sur Internet, chacun d’eux présentant un risque de distraction. Ce risque augmente à chaque seconde qui s’écoule entre le moment où le besoin du client se fait sentir et le moment où il trouve une solution. D’innombrables clients sont perdus dans ce bref laps de temps. Pour favoriser une augmentation de la récurrence de l’adoption, vous devez réduire le nombre de distractions en réduisant le temps consacré à trouver une solution (TTS).

## <a name="interacting-with-devices"></a>Interaction avec des appareils

Une expérience web standard est la technique de développement d’applications la plus couramment utilisée pour répondre aux besoins d’un client. Cette approche suppose que le client se trouve devant son ordinateur. Si votre client exprime invariablement un besoin lorsqu’il se trouve devant son ordinateur portable, créez une application web. Cette application web fournira une expérience ambiante pour ce client, dans ce scénario. Toutefois, nous savons que ce scénario est de moins en moins probable à notre époque.

![Expériences ambiantes](../../_images/innovate/ambient-experiences.png)

De nos jours, les expériences ambiantes requièrent généralement plus qu’une application web. Grâce à des [mesures](./measure.md) et à un [apprentissage avec le client](./learn.md), le comportement qui déclenche le besoin du client peut être observé, suivi et utilisé pour créer une meilleure expérience ambiante. La liste suivante résume quelques approches permettant d’intégrer des solutions ambiantes dans vos hypothèses, avec plus de détails sur chacune dans les paragraphes suivants.

- **[Expérience mobile](#mobile-experience) :** Comme pour les ordinateurs portables, les applications mobiles sont omniprésentes dans les environnements des clients. Dans certaines situations, cela est susceptible de fournir un niveau d’interactivité suffisant pour rendre une solution ambiante.
- **[Réalité mixte](#mixed-reality) :** Parfois, l’environnement habituel d’un client doit être modifié pour créer un environnement d’interaction. Ce facteur crée en quelque sorte une fausse réalité dans laquelle le client interagit avec la solution et répond à un besoin. Dans ce cas, la solution est ambiante dans le cadre de la fausse réalité.
- **[Réalité intégrée](#integrated-reality) :** S’approchant de l’ambiance réelle, les solutions de réalité intégrée sont axées sur l’utilisation d’un appareil qui existe dans la réalité du client pour intégrer la solution dans ses comportements naturels. Un assistant virtuel est un excellent exemple d’intégration de la réalité dans l’environnement immédiat. Une option moins connue concerne les technologies de l’Internet des objets (IoT), qui intègrent des appareils qui existent déjà dans l’environnement du client.
- **[Réalité ajustée](#adjusted-reality) :** Quand l’une de ces solutions ambiantes utilise l’analyse prédictive dans le cloud pour définir et produire une interaction avec le client à travers l’environnement naturel, la solution a adapté la réalité.

Comprendre le besoin du client et mesurer l’impact sur ce dernier vous aident à déterminer si une interaction avec l’appareil ou une expérience ambiante sont nécessaires pour valider votre hypothèse. Pour chacun de ces points de données, les sections suivantes vous aideront à trouver la meilleure solution.

## <a name="mobile-experience"></a>Expérience mobile

Dans la première étape de l’expérience ambiante, l’utilisateur s’éloigne de l’ordinateur. Aujourd’hui, les consommateurs et les professionnels passent facilement d’un appareil mobile à un ordinateur. Chaque plateforme ou appareil utilisé par votre client crée une nouvelle expérience potentielle. L’ajout d’une expérience mobile qui étend la solution principale est le moyen le plus rapide d’améliorer l’intégration dans l’environnement immédiat du client. Bien qu’un appareil mobile soit éloigné des conditions ambiantes, il peut être plus proche du besoin du client.

Lorsque les clients sont mobiles et changent fréquemment d’emplacement, cela peut représenter la forme d’expérience ambiante la plus pertinente pour une solution particulière. Au cours de la dernière décennie, l’innovation a souvent été déclenchée par l’intégration de solutions existantes à une expérience mobile.

Azure App Services est un excellent exemple de cette approche. Lors des premières itérations, la [fonctionnalité d’application web d’Azure App Services](https://docs.microsoft.com/azure/app-service/overview) peut être utilisée pour tester l’hypothèse. À mesure que les hypothèses deviennent plus complexes, la [fonctionnalité d’application mobile d’Azure App Services](https://docs.microsoft.com/azure/app-service-mobile) peut étendre l’application web pour l’exécuter sur diverses plateformes mobiles.

## <a name="mixed-reality"></a>Réalité mixte

Les solutions de réalité mixte représentent le niveau de maturité suivant pour les expériences ambiantes. Cette approche augmente ou reproduit l’environnement du client ; elle crée une extension de la réalité à l’intérieur de laquelle le client peut opérer.

> [!IMPORTANT]
> Si un appareil de réalité virtuelle (RV) est nécessaire et *ne fait pas déjà partie de l’environnement immédiat ou des comportements naturels d’un client*, la réalité augmentée ou virtuelle relève plus de l’expérience de remplacement que de l’expérience ambiante.

Les expériences de réalité mixte sont de plus en plus courantes parmi les travailleurs à distance. Leur utilisation croît encore plus rapidement dans les secteurs nécessitant une collaboration ou des compétences spécialisées qui ne sont pas immédiatement disponibles sur le marché local. Les situations qui requièrent la prise en charge centralisée de l’implémentation d’un produit complexe pour une main-d’œuvre à distance sont un terreau particulièrement fertile pour la réalité augmentée. Dans ces scénarios, l’équipe centrale du support technique et les travailleurs à distance peuvent utiliser la réalité augmentée pour travailler sur le produit, détecter un problème sur celui-ci et l’installer.

Considérez par exemple le cas des ancres spatiales. Les ancres spatiales vous permettent de créer des expériences de réalité mixte avec des objets qui conservent leurs emplacements respectifs sur les appareils et dans le temps. Grâce aux ancres spatiales, un comportement spécifique peut être capturé, enregistré et rendu persistant, fournissant ainsi une expérience ambiante la prochaine fois que l’utilisateur opère dans cet environnement augmenté. [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview) est un service qui adapte cette logique au cloud, permettant de dupliquer les expériences entre les appareils et même entre les solutions.

## <a name="integrated-reality"></a>Réalité intégrée

Au-delà de la réalité mobile ou même de la réalité mixte se trouve la réalité intégrée. La réalité intégrée vise à supprimer complètement l’expérience numérique. Tout autour de nous se trouvent des appareils dotés de capacités de calcul et de connectivité. Ces appareils peuvent être utilisés pour collecter des données dans l’environnement immédiat sans que le client n’ait à toucher un téléphone, un ordinateur portable ou un appareil RV.

Cette expérience est idéale lorsqu’une certaine forme d’appareil se trouve systématiquement dans le même environnement que celui dans lequel le besoin du client se manifeste. Les scénarios les plus courants comprennent les ateliers, les ascenseurs et même la voiture. Ces types d’appareils de grande taille ont déjà une puissance de calcul. Vous pouvez également utiliser les données de l’appareil lui-même pour détecter les comportements des clients et les envoyer vers le cloud. Cette capture automatique des données relatives aux comportements des clients réduit considérablement la nécessité pour un client d’entrer des données. En outre, l’expérience web, mobile ou RV peut fonctionner comme un retour d’informations pour transmettre ce qui a été appris dans la solution de réalité intégrée.

Voici quelques exemples de réalité intégrée dans Azure :

- [Les solutions Azure Internet of Things (IoT)](https://docs.microsoft.com/azure/iot-fundamentals), une collection de services dans Azure qui contribuent chacun à la gestion des appareils et du flux de données entre ces appareils et le cloud et entre le cloud et les utilisateurs finaux.
- [Azure Sphere](https://docs.microsoft.com/azure-sphere), une combinaison de matériel et de logiciels. Azure Sphere est un moyen intrinsèquement sécurisé pour permettre à un appareil existant de transmettre des données en toute sécurité entre l’appareil et les solutions Azure IoT.
- [Azure Kinect Developers Kit](https://docs.microsoft.com/azure/Kinect-dk), des capteurs IA avec des modèles vocaux et de vision par ordinateur avancés. Ces capteurs peuvent collecter des données visuelles et audio à partir de l’environnement immédiat et alimenter ces entrées dans votre solution.

Vous pouvez utiliser ces trois outils pour collecter des données sur l’environnement naturel et au moment où le client en a besoin. À partir de là, votre solution peut répondre à ces entrées de données pour répondre au besoin, parfois avant même que le client ne sache qu’un déclencheur pour ce besoin s’est manifesté.

## <a name="adjusted-reality"></a>Réalité ajustée

La forme d’expérience ambiante la plus avancée est la réalité ajustée, souvent appelée *intelligence ambiante*. La réalité ajustée est une approche qui consiste à utiliser les informations de votre solution pour modifier la réalité du client sans que ce dernier ait à interagir directement avec une application. Dans cette approche, l’application que vous avez créée initialement pour prouver votre hypothèse pourrait ne plus être pertinente. Au lieu de cela, les appareils de l’environnement aident à moduler les entrées et les sorties pour répondre aux besoins des clients.

Les assistants virtuels et les enceintes connectées offrent d’excellents exemples de réalité ajustée. Seule, une enceinte connectée est un exemple de réalité intégrée simple. Mais en ajoutant un éclairage intelligent et un détecteur de mouvement à une solution d’enceinte connectée, il devient facile de créer une solution de base qui allume les lumières lorsque vous entrez dans une pièce.

Les ateliers dans le monde entier fournissent d’autres exemples de réalité ajustée. Lors des premières phases de la réalité intégrée, les capteurs sur les appareils ont détecté des conditions telles qu’une surchauffe, puis ont alerté un être humain par le biais d’une application. Dans la réalité ajustée, le client peut rester impliqué, mais le retour d’informations est plus restreint. Dans un atelier de réalité ajustée, un appareil pourrait détecter la surchauffe d’une machine essentielle quelque part sur la chaîne de montage. Quelque part ailleurs dans l’atelier, un deuxième appareil ralentit alors légèrement la production pour permettre à la machine de refroidir et de reprendre à plein régime lorsque la situation est résolue. Dans cette situation, le client est un participant indirect. Le client utilise votre application pour définir les règles et comprendre comment ces règles ont influé sur la production, mais celles-ci ne sont pas nécessaires au retour d’informations.

Les services Azure décrits dans [Solutions Azure Internet of Things (IoT)](https://docs.microsoft.com/azure/iot-fundamentals), [Azure Sphere](https://docs.microsoft.com/azure-sphere) et [Azure Kinect Developers Kit](https://docs.microsoft.com/azure/Kinect-dk) peuvent tous être des composants d’une solution de réalité ajustée. Votre application d’origine et votre logique métier serviraient alors d’intermédiaire entre l’entrée environnementale et la modification qui doit être apportée dans l’environnement physique.

Un jumeau numérique est un autre exemple de réalité ajustée. Ce terme fait référence à la représentation numérique d’un appareil physique, présentée par le biais d’un ordinateur, d’un téléphone mobile ou de formats à réalité mixte. Contrairement aux modèles 3D moins sophistiqués,un jumeau numérique reflète les données collectées à partir d’un appareil réel dans l’environnement physique. Cette solution permet à l’utilisateur d’interagir avec la représentation numérique d’une manière qui n’aurait jamais été possible dans le monde réel. Dans cette approche, des appareils physiques ajustent un environnement de réalité mixte. Toutefois, la solution continue de rassembler des données à partir d’une solution de réalité intégrée et de les utiliser pour façonner la réalité de l’environnement actuel du client.

Dans Azure, les jumeaux numériques sont créés et accessibles via un service appelé [Azure Digital Twins](https://docs.microsoft.com/azure/digital-twins/about-digital-twins).

## <a name="next-steps"></a>Étapes suivantes

À présent que vous avez une meilleure compréhension des interactions entre les appareils et de l’expérience ambiante qui convient à votre solution, vous êtes prêt à explorer la discipline finale de l’innovation, [Prédire et influencer](./predict.md).

> [!div class="nextstepaction"]
> [Prédire et influencer](./predict.md)
