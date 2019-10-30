---
title: 'Innovation cloud : Développer en faisant preuve d’empathie vis à vis du client'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Apprenez à développer en faisant preuve d’empathie vis-à-vis du client.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 5faaaf5b4c6b4c766c47dc6331723bed31e02d8e
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558299"
---
# <a name="build-with-customer-empathy"></a>Développer en faisant preuve d’empathie vis à vis du client

« La nécessité est mère de l’invention ». Ce proverbe anglais illustre le caractère omniprésent de l’esprit humain et notre tendance naturelle à inventer. Comme expliqué dans l’Oxford English Dictionary, quand quelque chose devient vraiment indispensable, vous devez trouver le moyen de l’obtenir. Qui pourrait contredire ces vérités universelles sur l’invention ? Toutefois, comme décrit dans la [méthodologie d’innovation](./index.md), l’innovation nécessite un équilibre entre **invention** et **adoption**.

Dans le contexte de cette analogie, l’innovation émane d’un concept plus étendu. *L’empathie vis-à-vis du client est mère de l’innovation.* La création d’une solution favorisant l’innovation implique un besoin légitime du client &mdash; un besoin qui incite le client à revenir pour résoudre des problèmes critiques. Ces solutions sont basées sur les besoins du client et non sur ses souhaits ou ses envies. L’identification des véritables besoins des clients commence par l’empathie &mdash; une compréhension approfondie de l’expérience du client. Il s’agit d’une compétence insuffisamment développée chez de nombreux ingénieurs et chefs produits, voire chez les dirigeants d’entreprise. Heureusement, les différentes interactions et l’évolution rapide du rôle d’architecte du cloud semblent avoir déjà déclenché le développement de ces compétences.

Pourquoi l’empathie est-il si importante ? De la première version d’un produit minimum viable (MVP, minimum viable product) à la disponibilité générale d’une solution commercialisable, l’empathie vis-à-vis du client nous permet de comprendre et de partager son expérience. Cette empathie nous aide à comprendre comment développer une meilleure solution. Plus important encore : elle nous permet de mieux nous positionner pour **inventer** des solutions qui encouragent l’**adoption**. Dans une économie numérique, ceux qui développent le plus rapidement une empathie vis-à-vis du client peuvent contribuer à créer un avenir meilleur, qui redéfinit et trace la voie du marché.

## <a name="how-to-build-with-empathy"></a>Comment développer en faisant preuve d’empathie

La planification consiste, de façon intrinsèque, à définir des hypothèses. Plus nous planifions, plus les hypothèses s’intègrent dans les bases d’une grande idée. D’une manière générale, les hypothèses ont tendance à résulter d’une empathie envers soi-même &mdash; en d’autres termes, « que voudrais-je si j’étais dans cette situation ? ». Commencer par la phase de développement permet de réduire la période pendant laquelle les hypothèses peuvent envahir une solution. De plus, cette approche accélère la boucle de rétroaction avec les clients réels, ce qui déclenche des opportunités précoces d’apprentissage et d’affinement de l’empathie.

> [!CAUTION]
> Définir correctement ce qui doit être développé peut se révéler délicat et nécessite de la pratique. Si vous développez une solution trop rapidement, elle ne reflétera peut-être pas les besoins du client. Si vous passez trop de temps à comprendre le besoin initial du client et ses exigences vis-à-vis de la solution, une autre solution en phase avec ce besoin peut aborder le marché avant que vous n’ayez pu développer quoi que ce soit. Quel que soit le scénario, l’opportunité d’apprentissage peut être considérablement limitée ou retardée. Parfois, les données peuvent même être endommagées.

Les solutions les plus innovantes de l’histoire sont nées d’une intime conviction. Ce sentiment intuitif repose sur l’expertise existante et l’observation directe. Nous commençons par le développement, car il nous permet de tester rapidement cette intuition. Nous pouvons alors cultiver une compréhension plus approfondie et des degrés d’empathie plus clairs. À chaque itération ou version d’une solution, l’équilibre s’appuie sur le développement de MVP illustrant l’empathie vis-à-vis du client.

Pour orienter cet effort d’équilibrage, les deux sections qui suivent abordent les concepts relatifs au développement dans un esprit d’empathie vis-à-vis du client et à la définition d’un MVP.

### <a name="define-a-customer-focused-hypothesis"></a>Définir une hypothèse axée sur le client

Développer en faisant preuve d’empathie signifie qui la création d’une solution doit s’appuyer sur des hypothèses définies illustrant un besoin spécifique du client. Les étapes suivantes vous permettent de formuler une hypothèse entraînant le développement d’une solution dans un esprit d’empathie.

1. Quand vous développez une solution en faisant preuve d’empathie, le client est toujours le centre d’attention. Cette approche peut prendre de nombreuses formes. Vous pouvez prendre pour référence un archétype du client, une personne spécifique ou même l’image d’un client confronté au problème que vous souhaitez résoudre. En outre, les clients peuvent être internes (employés ou partenaires) ou externes (consommateurs ou clients professionnels). Cette définition du client représente la première hypothèse à tester &mdash; pouvez-vous aider ce client spécifique ?
2. La seconde consiste à comprendre l’expérience du client. Développer en faisant preuve d’empathie signifie que l’expérience du client peut être appréhendée et que son problème est compris. Il s’agit de l’hypothèse suivante à tester &mdash; pouvons-nous aider ce client spécifique à résoudre ce problème surmontable ?
3. La troisième consiste à définir une solution simple à un problème spécifique. Il convient de s’appuyer sur l’expertise des personnes, des processus et des experts technologiques pour définir une solution potentielle. Il s’agit de l’hypothèse complète à tester &mdash; pouvons-nous aider ce client spécifique à résoudre ce problème surmontable à l’aide de la solution proposée ?
4. L’énoncé de la valeur représente la dernière étape du développement dans un esprit d’empathie. Quelle valeur à long terme espérez-vous offrir à ces clients ? Cette réponse détermine votre hypothèse complète &mdash; comment les clients verront-ils leur vie améliorée en utilisant la solution proposée pour résoudre ce problème surmontable ?

Cette dernière étape représente l’aboutissement d’une hypothèse basée sur l’empathie. Elle définit le public concerné, le problème, la solution et la métrique d’amélioration à atteindre, le tout étant axé sur le client. Pendant les phases de mesure et d’apprentissage, chaque hypothèse doit être testée. Les modifications relatives au client, à l’énoncé de la valeur ou à la solution sont anticipées, à mesure que l’équipe développe une plus grande empathie vis-à-vis de la clientèle potentielle.

> [!CAUTION]
> L’objectif consiste à _développer_ (et non _planifier_) en faisant preuve d’empathie vis-à-vis du client. Vous pouvez facilement vous retrouver bloqué dans des cycles infinis de planification et d’ajustement pour établir l’énoncé parfait de l’empathie vis-à-vis du client. Avant d’essayer de développer un tel énoncé, consultez les deux sections suivantes sur la définition et le développement d’un MVP.

Une fois les hypothèses de base démontrées, les itérations ultérieures seront axées sur des tests de croissance en plus des tests d’empathie. Une fois l’empathie établie, testée et validée, nous pouvons commencer à appréhender le marché potentiel à grande échelle. Pour ce faire, vous pouvez développer l’une des formules d’hypothèse standard ci-dessus. En vous basant sur les données disponibles, estimez la taille du marché total (en d’autres termes, le nombre de clients potentiels). Puis, estimez le pourcentage de ce marché total rencontrant un problème similaire et pouvant être intéressé par cette solution si elle est en mesure de résoudre le problème. Il s’agit de votre marché potentiel. La prochaine hypothèse à tester est l’hypothèse suivante : comment _x %_ des clients verront-ils leur vie améliorée en utilisant la solution proposée pour résoudre ce problème surmontable ? Un petit échantillon de clients révélera des indicateurs clés suggérant l’impact sur les clients engagés en pourcentage.

### <a name="define-a-solution-to-test-the-hypothesis"></a>Définir une solution pour tester l’hypothèse

Pendant chaque itération d’une boucle de rétroaction développer-mesurer-apprendre, la tentative de développement dans un esprit d’empathie est définie par un MVP.

Un MVP représente la plus petite unité d’effort à consacrer (invention, ingénierie, développement d’application ou architecture de données) afin de créer une solution dans une mesure suffisante pour _apprendre avec le client_. Chaque MVP doit permettre de tester tout ou partie de l’hypothèse précédente et d’obtenir directement les retours du client. Le résultat n’est pas une belle application dotée de fonctionnalités qui vont révolutionner votre secteur d’activité. Le résultat souhaité de chaque itération est une opportunité d’apprentissage &mdash; la possibilité de tester une hypothèse de façon plus approfondie.

Inscrire la création de la solution dans une boîte de temps représente une façon courante de s’assurer qu’un produit est un produit minimum. Assurez-vous que l’équipe de développement pense que la solution peut être créée en une seule itération pour permettre un test rapide. Pour mieux comprendre l’utilisation de la vélocité, des itérations et des versions afin de définir ce qu’est un produit minimum, consultez l’article sur la [planification de la vélocité, des itérations, des versions et des chemins d’itération](../../plan/iteration-paths.md).

### <a name="reduce-complexity-and-delay-technical-spikes"></a>Réduire la complexité et retarder les spikes techniques

Les [disciplines de l’innovation](./invention.md) présentées dans la [méthodologie d’innovation](./index.md) décrivent les fonctionnalités souvent nécessaires pour produire une innovation mature ou une solution MVP prête pour un développement à grande échelle. Utilisez ces disciplines comme guide à long terme pour l’inclusion des fonctionnalités. De même, utilisez-les comme guide de sécurité lors des premiers tests de la valeur client et de l’empathie dans votre solution.

L’éventail de fonctionnalités et les différentes disciplines de l’innovation ne peuvent pas être établis en une seule itération. Souvent, plusieurs versions sont nécessaires pour qu’une solution MVP puisse inclure la complexité de plusieurs disciplines. En fonction de l’investissement en développement, plusieurs équipes peuvent travailler en parallèle dans différentes disciplines pour tester plusieurs hypothèses. Même s’il est préférable de préserver l’alignement architectural entre ces équipes, il est déconseillé d’essayer de développer des solutions intégrées complexes tant que les hypothèses de valeur ne sont pas validées.

C’est en observant la fréquence ou le volume des **spikes techniques** que l’on peut le mieux identifier la complexité. Les spikes techniques représentent les efforts à consacrer pour créer des solutions techniques qui ne peuvent pas être facilement testées avec les clients. Quand la valeur client et l’empathie vis-à-vis du client ne sont pas testées, les spikes techniques représentent un risque pour l’innovation et doivent être minimisés dans la mesure du possible. Concernant les types de solutions matures testées dans le cadre d’un effort de migration, il est courant d’effectuer des spikes techniques tout au long de l’adoption. Cependant, ils retardent le test des hypothèses durant les efforts d’innovation et doivent être reportés dans la mesure du possible.

Il est recommandé d’adopter une approche basée sur la simplification constante pour toute définition de MVP. La simplification constante consiste à supprimer tout ce qui ne contribue pas à votre capacité à valider l’hypothèse. Pour réduire la complexité, limitez les intégrations et les fonctionnalités qui ne sont pas nécessaires pour tester l’hypothèse.

### <a name="build-a-minimum-viable-product-mvp"></a>Développer un produit minimum viable

À chaque itération, une solution MVP peut prendre de nombreuses formes différentes. Généralement, la seule exigence consiste à obtenir un résultat permettant de mesurer et tester l’hypothèse. Cette exigence simple déclenche le processus scientifique et permet à l’équipe de développer la solution en faisant preuve d’empathie. Cette approche axée sur le client implique que le premier MVP s’appuie uniquement sur l’une des [disciplines de l’innovation](./invention.md).

Dans certains cas, la voie la plus rapide vers l’innovation consiste à éviter ces disciplines (de façon temporaire mais totale) jusqu’à ce que l’équipe d’adoption du cloud soit convaincue que l’hypothèse est validée avec exactitude. Venant d’une entreprise technologique comme Microsoft, ce conseil peut sembler illogique. Cette proposition a pour but de souligner que le besoin du client (et non une décision technologique spécifique) doit être considéré avec une priorité absolue dans une solution MVP.

En règle générale, une solution MVP est constituée d’une simple application web ou d’une solution de données dotée de fonctionnalités minimales et d’une finition basique. Pour les organisations bénéficiant d’une expertise professionnelle en matière de développement, il s’agit souvent de la voie la plus rapide vers l’apprentissage et l’itération. Une équipe peut adopter d’autres approches pour développer un MVP, par exemple :

- Un algorithme prédictif incorrect 99 % du temps, mais démontrant des résultats souhaités spécifiques
- Un appareil IoT qui ne communique pas de manière sécurisée en environnement de production, mais qui peut démontrer la valeur de données en quasi-temps réel au sein d’un processus
- Une application créée par un développeur citoyen pour tester une hypothèse ou répondre à des besoins à plus petite échelle
- Un processus manuel qui recrée les avantages de l’application à suivre
- Une maquette ou une vidéo suffisamment détaillée pour permettre au client d’interagir

Le développement d’un MVP ne doit pas nécessiter un lourd investissement en développement. Pour minimiser le nombre d’hypothèses testées à un moment donné, il est préférable de limiter cet investissement autant que possible. Ensuite, dans chaque itération et avec chaque version, la solution est intentionnellement améliorée afin d’évoluer vers une solution prête pour un développement à grande échelle, représentant plusieurs disciplines de l’innovation.

### <a name="accelerate-mvp-development"></a>Accélérer le développement d’un MVP

Le délai de commercialisation est essentiel à la réussite de toute innovation. Des mises en production plus rapides accélèrent l’apprentissage, ce qui permet une mise à l’échelle plus rapide des produits. Parfois, les cycles de développement d’application traditionnels peuvent ralentir ce processus. Plus souvent, l’innovation est limitée par l’expertise disponible. Les budgets, les effectifs et la disponibilité du personnel peuvent limiter le nombre d’innovations que les équipes peuvent gérer.

Les contraintes en termes d’équipe et le désir de développer en faisant preuve d’empathie ont suscité une tendance à recourir aux développeurs citoyens, qui évolue rapidement. Ces développeurs réduisent les risques et assurent la mise à l’échelle au sein de la communauté de développeurs professionnels d’une organisation. Les développeurs citoyens sont des experts techniques spécialisés dans l’expérience client, mais ils ne sont pas formés en tant qu’ingénieurs. Ils utilisent des outils de prototypage ou des outils de développement plus légers qui peuvent être désapprouvés par les développeurs professionnels. Cette nouvelle génération de développeurs orientés vers l’entreprise crée des solutions MVP et des théories de test. Quand il est aligné correctement, ce processus permet de créer des solutions de production qui peuvent fournir de la valeur sans pour autant passer une hypothèse d’échelle suffisamment efficace. Elles peuvent également être utilisées pour la validation d’un prototype avant que ne soient mis en œuvre les efforts de mise à l’échelle.

Dans le cas d’un plan d’innovation, il est préférable que les équipes d’adoption du cloud diversifient leur portefeuille pour inclure les efforts des développeurs citoyens. L’adaptation des efforts de développement permet de former et tester plus d’hypothèses moyennant un investissement réduit. Quand une hypothèse est validée et qu’un marché potentiel est identifié, les développeurs professionnels peuvent renforcer et mettre à l’échelle la solution à l’aide d’outils de développement modernes.

### <a name="final-build-gate-customer-pain"></a>Dernier obstacle au développement : problématique du client

Quand l’empathie vis-à-vis du client est forte, il doit être facile d’identifier un problème clair. La problématique du client doit être évidente. Au cours du développement, l’équipe d’adoption du cloud développe une solution permettant de tester une hypothèse basée sur une problématique du client. Si l’hypothèse est bien définie mais que la problématique ne l’est pas, la solution n’est pas véritablement basée sur l’empathie vis-à-vis du client. Dans ce scénario, le développement ne représente pas le bon point de départ. En fait, vous devez d’abord investir dans la création de l’empathie et l’apprentissage auprès des clients réels. En termes de création d’empathie et de validation des problématiques, la meilleure approche consiste simplement à écouter les clients. Consacrez du temps à la rencontre et à l’observation de vos clients, et ce, jusqu’à ce que vous puissiez identifier une problématique récurrente. Une fois que la problématique comprise, cette approche permet de tester une solution basée sur des hypothèses pour résoudre cette problématique.

## <a name="when-not-to-apply-this-approach"></a>Dans quels cas ne pas appliquer cette approche

De nombreuses exigences juridiques, de conformité et sectorielles peuvent nécessiter une autre approche. Si les versions publiques d’une solution en développement créent un risque en termes de calendrier des brevets, de protection de la propriété intellectuelle, de fuite de données client ou de violation des exigences de conformité établies, cette approche ne sera peut-être pas appropriée. Quand vous percevez l’existence de tels risques, consultez des conseillers juridiques avant d’adopter une quelconque approche guidée de la gestion des versions.

## <a name="references"></a>Références

Certains concepts de cet article s’appuient sur les sujets abordés dans l’ouvrage _[The Lean Startup](http://theleanstartup.com/book)(Eric Ries, Crown Business, 2011)_ .

## <a name="next-steps"></a>Étapes suivantes

Une fois qu’une solution MVP a été développée, la valeur d’empathie et la valeur d’échelle peuvent être mesurées. Découvrez comment [mesurer l’impact sur le client](./measure.md).

> [!div class="nextstepaction"]
> [Mesurer l’impact sur le client](./measure.md)
