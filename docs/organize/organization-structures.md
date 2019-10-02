---
title: Établir des structures d’équipe
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Établir des structures d’équipe
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 8000847a46082be6116abb22e52def03243c69b0
ms.sourcegitcommit: 1dccf1aed8e98aa0f58c4f86d90c65f5fa5ac84d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71811088"
---
# <a name="establish-team-structures"></a>Établir des structures d’équipe

Chaque fonctionnalité cloud est fournie par un utilisateur lors de chaque effort d’adoption du cloud. Ces affectations et structures d’équipe peuvent se développer de façon organique ou être intentionnellement conçues pour correspondre à une structure d’équipe définie.

Si les besoins d’adoption augmentent, le besoin de disposer d’un équilibre et d’une structure augmente également. Cet article fournit des exemples de structures d’équipe courantes à différentes étapes de la maturité organisationnelle. Le graphique et la liste ci-dessous décrivent ces structures en fonction des étapes de maturation classiques. Utilisez ces exemples pour trouver la structure organisationnelle la mieux adaptée à vos besoins opérationnels.

![Cycle d’évolution de l’organisation](../_images/ready/org-ready-maturity.png)

Les structures organisationnelles ont tendance à passer par le modèle de maturité commun décrit ici :

1. [Équipe d’adoption du cloud uniquement](#cloud-adoption-team-only)
2. [Meilleure pratique MVP](#best-practice-minimum-viable-product-mvp)
3. [Équipe informatique centrale](#central-it)
4. [Alignement stratégique](#strategic-alignment)
5. [Alignement opérationnel](#operational-alignment)
6. [Centre d’excellence du cloud (CCoE)](#cloud-center-of-excellence)

La plupart des entreprises engagent le processus avec une simple *équipe d’adoption du cloud*. Toutefois, nous vous recommandons d’établir une structure organisationnelle qui ressemble davantage à la structure des [meilleures pratiques MVP](#best-practice-minimum-viable-product-mvp).

## <a name="cloud-adoption-team-only"></a>Équipe d’adoption du cloud uniquement

L’équipe d’adoption du cloud constitue le noyau de tous les efforts d’adoption du cloud. Cette équipe pilote les modifications techniques qui permettent l’adoption du cloud. Selon les objectifs de l’effort d’adoption, cette équipe peut comprendre des membres aux compétences diverses qui s’occupent d’un large éventail de tâches techniques et commerciales.

![Équipe d’adoption du cloud, avec les équipes de sécurité et de gouvernance](../_images/ready/org-ready-adoption-only.png)

Pour les efforts d’adoption à petite échelle ou précoces, cette équipe peut se limiter à une personne. Dans les efforts à grande échelle ou tardifs, il est courant d’avoir plusieurs équipes d’adoption du cloud, comptant chacune six ingénieurs environ. Quelles que soient la taille ou les tâches, le rôle d’une équipe d’adoption du cloud est de fournir les moyens d’intégrer des solutions dans le cloud. Pour certaines organisations, il peut s’agir d’une structure organisationnelle suffisante. L’article sur l’[équipe d’adoption du cloud](./cloud-adoption.md) fournit plus d’insights sur la structure, la composition et la fonction de l’équipe d’adoption du cloud.

> [!WARNING]
> Fonctionner *uniquement* avec une équipe d’adoption du cloud (ou plusieurs équipes d’adoption du cloud) est considéré comme un *anti-modèle* et doit, à ce titre, être évité. Au minimum, adoptez la [meilleure pratique MVP](#best-practice-minimum-viable-product-mvp).

## <a name="best-practice-minimum-viable-product-mvp"></a>Meilleure pratique : produit minimum viable (MVP)

Nous vous recommandons de disposer de deux équipes pour créer un équilibre entre les efforts d’adoption du cloud. Ces deux équipes sont responsables de diverses fonctionnalités tout au long du processus d’adoption.

- **Équipe d’adoption du cloud :** Cette équipe est responsable des solutions techniques, de l’alignement des activités, de la gestion des projets et de l’exploitation des solutions adoptées.
- **Équipe de gouvernance cloud :** Pour équilibrer l’équipe d’adoption du cloud, une équipe de gouvernance du cloud a pour mission d’assurer l’excellence des solutions adoptées. L’équipe de gouvernance cloud est responsable de la maturité de la plateforme, de son exploitation, de sa gouvernance et de son automatisation.

![Adoption du cloud avec contrepartie à la gouvernance cloud](../_images/ready/org-ready-best-practice.png)

Cette approche éprouvée est considérée comme un MVP, car elle n’est peut-être pas viable. Chaque équipe endosse plusieurs rôles et caractéristiques, comme indiqué dans les tableaux [*réalisateur, approbateur, consulté, informé* (RACI)](./raci-alignment.md).

Les sections suivantes décrivent une structure organisationnelle éprouvée et dotée d’un personnel complet, ainsi que des approches pour aligner la structure appropriée à votre organisation.

## <a name="central-it"></a>Équipe informatique centrale

Au fur et à mesure que l’adoption évolue, l’équipe de gouvernance cloud peut avoir du mal à suivre le rythme de l’innovation de plusieurs équipes d’adoption du cloud. C’est particulièrement vrai dans les environnements avec des exigences élevées en matière de conformité, d’exploitation ou de sécurité. À ce stade, il est courant pour les entreprises de transférer les responsabilités du cloud à une équipe informatique centrale existante. Si cette équipe est en mesure de réévaluer les outils, les processus et les personnes afin de mieux soutenir l’adoption du cloud à l’échelle, l’inclusion de l’équipe informatique centrale peut apporter une valeur ajoutée significative. Faire appel à des experts de l’exploitation, de l’automatisation, de la sécurité et de l’administration pour moderniser l’informatique centrale peut favoriser des innovations opérationnelles efficaces.

![Adoption du cloud avec un modèle informatique central](../_images/ready/org-ready-central-it.png)

Malheureusement, la phase informatique centrale peut constituer l’une des phases les plus risquées de la maturité organisationnelle. L’équipe informatique centrale doit faire preuve d’un fort esprit de croissance. Si l’équipe considère le cloud comme une opportunité de se développer et d’adapter ses capacités, elle peut lui apporter une grande valeur tout au long du processus. Cependant, si l’équipe informatique centrale considère l’adoption du cloud principalement comme une menace pour son modèle existant, elle devient un obstacle pour les équipes d’adoption du cloud et les objectifs commerciaux que celles-ci soutiennent. Certaines équipes informatiques centrales ont passé des mois, voire des années, à tenter de forcer le cloud à s’aligner sur les approches locales, sans succès. Le cloud ne nécessite pas que le bouleversement complet de l’informatique centrale mais que des changements se mettent en place. Si la résistance au changement prévaut au sein de l’équipe informatique centrale, cette phase de maturité peut rapidement devenir un anti-modèle culturel.

Les plans d’adoption du cloud principalement axés sur la plateforme en tant que service (PaaS), DevOps ou d’autres solutions qui nécessitent moins de support opérationnel sont moins susceptibles de tirer des avantages de cette phase de maturité. Au contraire, ces types de solutions sont les plus susceptibles d’être entravés ou bloqués par les tentatives de centralisation de l’informatique. Un niveau de maturité plus élevé, comme un [centre d’excellence dans le cloud (CCoE)](#cloud-center-of-excellence), est plus susceptible de donner des résultats positifs pour ces types d’efforts de transformation. Pour comprendre les différences entre l’informatique centrale dans le cloud et un CCoE, consultez [Centre d’excellence du cloud](./cloud-center-of-excellence.md).

## <a name="strategic-alignment"></a>Alignement stratégique

Au fur et à mesure que l’investissement dans l’adoption du cloud augmente et que l’entreprise en tire des bénéfices, les parties prenantes s’impliquent souvent davantage dans le processus. Comme l’illustre l’image suivante, une équipe de stratégie cloud définie aligne les parties prenantes de l’entreprise afin de maximiser les avantages et bénéfices issus des investissements dans le cloud.

![Ajouter une équipe de stratégie cloud définie](../_images/ready/org-ready-strategy-aligned.png)

Lorsque la maturité se produit de manière organique, à la suite d’efforts d’adoption du cloud menés par le service informatique, l’alignement stratégique est généralement précédé par une équipe de gouvernance ou une équipe informatique centrale. Lorsque les efforts d’adoption du cloud sont dirigés par l’entreprise, l’accent a tendance à être mis plus tôt sur le modèle d’exploitation et l’organisation. Dans la mesure du possible, les résultats opérationnels et l’équipe de stratégie cloud doivent être définis au début du processus.

## <a name="operational-alignment"></a>Alignement opérationnel

La réalisation de la valeur commerciale des efforts d’adoption du cloud nécessite des opérations stables. Les opérations dans le cloud peuvent nécessiter de nouveaux outils, processus ou compétences. Lorsque des opérations informatiques stables sont nécessaires pour atteindre les résultats de l’entreprise, il est important d’ajouter une équipe des opérations cloud définie, comme indiqué ici.

![Ajouter une équipe des opérations cloud définie](../_images/ready/org-ready-operations-aligned.png)

Les opérations cloud peuvent être assurées par les rôles d’exploitation informatique existants. Cependant, il n’est pas rare que les opérations cloud soient déléguées à d’autres parties en dehors des opérations informatiques. Les fournisseurs de services gérés, les équipes de DevOps et les services informatiques des unités opérationnelles assument souvent les responsabilités associées aux opérations cloud, avec le soutien et les garde-fous fournis par les opérations informatiques. Cela est de plus en plus courant pour les efforts d’adoption du cloud qui se concentrent essentiellement sur les déploiements DevOps ou PaaS.

## <a name="cloud-center-of-excellence"></a>Centre d’excellence de cloud

Au plus haut niveau de maturité, un centre d’excellence dans le cloud aligne les équipes autour d’un modèle d’exploitation moderne privilégiant le cloud. Cette approche fournit des fonctions informatiques centrales telles que la gouvernance, la sécurité, la plateforme et l’automatisation.

![Centre d’excellence de cloud](../_images/ready/org-ready-ccoe.png)

La principale différence entre cette structure et la structure informatique centrale ci-dessus est l’accent mis sur le libre-service. Les équipes de cette structure s’organisent dans le but de déléguer le contrôle autant que possible. L’alignement des pratiques de gouvernance et de conformité aux solutions natives du cloud crée des garde-fous et des mécanismes de protection. Contrairement au modèle informatique central, l’approche cloud native maximise l’innovation et minimise la surcharge opérationnelle. Pour que ce modèle soit adopté, il faut que les dirigeants de l’entreprise et de l’informatique s’entendent mutuellement sur la modernisation des processus informatiques. Du fait qu’il est peu susceptible d’apparaître spontanément dans l’entreprise, ce modèle nécessite souvent le soutien de la direction.

## <a name="next-steps"></a>Étapes suivantes

Après avoir atteint un certain stade de maturité de la structure organisationnelle, vous pouvez utiliser les [tableaux RACI](./raci-alignment.md) pour aligner la responsabilisation et la responsabilité dans chaque équipe.

> [!div class="nextstepaction"]
> [Aligner le tableau RACI approprié](./raci-alignment.md)
