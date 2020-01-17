---
title: Mettre en place un examen de santé opérationnel
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aide sur les principes opérationnels de base
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 9607bf217d8638f2337fa337a4cb57c7ba919608
ms.sourcegitcommit: 390b374dc7af4c4b85ef9fcb381c7c1bc6076ac7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75868050"
---
# <a name="establish-an-operational-fitness-review"></a>Mettre en place un examen de santé opérationnel

Dès lors que votre entreprise commence à exécuter des charges de travail dans Azure, l’étape suivante consiste à établir un processus de *passage en revue de l’adéquation opérationnelle*. Ce processus énumère, implémente et passe en revue de façon itérative les *exigences non fonctionnelles* pour ces charges de travail. Ces exigences non fonctionnelles sont liées au comportement opérationnel attendu du service.

Il existe cinq catégories principales d’exigences non fonctionnelles, qui sont appelées [piliers de la qualité des logiciels](https://docs.microsoft.com/azure/architecture/guide/pillars) :

- Extensibilité
- Disponibilité
- Résilience, incluant la continuité d’activité et de la reprise d’activité
- Gestion
- Sécurité

Un processus de passage en revue de l’adéquation opérationnelle garantit que les charges de travail critiques répondent aux attentes de votre entreprise relativement aux piliers de la qualité.

Créez un processus d'évaluation de l'adéquation opérationnelle pour bien comprendre les problèmes résultant de l'exécution des charges de travail dans un environnement de production, et pour déterminer comment remédier à ces problèmes et les résoudre. Cet article décrit un processus général de passage en revue de l’adéquation opérationnelle, que votre entreprise peut utiliser pour atteindre cet objectif.

## <a name="operational-fitness-at-microsoft"></a>L’adéquation opérationnelle chez Microsoft

Depuis le début, de nombreuses équipes de Microsoft ont participé au développement de la plateforme Azure. Il est difficile de garantir la qualité et la cohérence d’un projet d’une telle taille et d’une telle complexité. Un processus robuste est nécessaire pour énumérer et implémenter de façon régulière les exigences non fonctionnelles fondamentales.

Les processus suivis par Microsoft forment la base des processus décrits dans cet article.

## <a name="understand-the-problem"></a>Comprendre le problème

Comme vous l’avez découvert dans [Bien démarrer](../getting-started/migrate.md), la première étape de la transformation numérique d’une entreprise consiste à identifier les problèmes métier à résoudre avec l’adoption d’Azure. L’étape suivante est de déterminer une solution générale au problème, comme la migration d’une charge de travail dans le cloud, ou l’adaptation d’un service local existant pour y inclure des fonctionnalités cloud. Enfin, vous devez concevoir et implémenter la solution.

Pendant ce processus, la principale considération porte sur les fonctionnalités du service : l’ensemble des spécifications _fonctionnelles_ que vous voulez que le service effectue. Prenons par exemple un service de livraison de produits. Plusieurs fonctionnalités sont nécessaires : déterminer les lieux de départ et de destination du produit, assurer son suivi au cours de la livraison, et envoyer des notifications au client.

Les exigences _non fonctionnelles_ se rapportent quant à elles à des propriétés comme la [disponibilité](https://docs.microsoft.com/azure/architecture/checklist/availability), la [résilience](https://docs.microsoft.com/azure/architecture/resiliency) et la [scalabilité](https://docs.microsoft.com/azure/architecture/checklist/scalability) du service. Ces propriétés diffèrent des exigences fonctionnelles, car elles n’affectent pas directement les fonctions finales du service. Elles concernent en revanche les performances et la continuité du service.

Vous pouvez spécifier certaines exigences non fonctionnelles dans les conditions d'un Contrat de niveau de service (SLA). Par exemple, vous pouvez exprimer la continuité du service sous forme de pourcentage de disponibilité : « disponible 99,99 % du temps ». D’autres exigences non fonctionnelles sont plus difficiles à définir et sont susceptibles de changer en fonction de l’évolution des besoins de production. Par exemple, un service orienté consommateurs risque de se retrouver face à des exigences de débit imprévues après une forte hausse de popularité.

> [!NOTE]
> Pour plus d'informations sur les exigences en matière de résilience, consultez [Conception d'applications Azure fiables](https://docs.microsoft.com/azure/architecture/reliability#define-requirements). Cet article contient des explications sur des concepts tels que l'objectif de point de récupération (RPO), l'objectif de temps de récupération (RTO) et les contrats SLA.

## <a name="process-for-operational-fitness-review"></a>Processus de passage en revue de l’adéquation opérationnelle

L’élément clé pour préserver les performances et la continuité des services d’une entreprise est d’implémenter un processus de passage en revue de l’adéquation opérationnelle.

![Vue d’ensemble du processus de passage en revue de l’adéquation opérationnelle](../_images/manage/ofr-flow.png)

À haut niveau, le processus se compose de deux phases. Dans la *phase des prérequis*, les exigences sont établies, puis mises en correspondance avec les services qui les prennent en charge. Cette phase se produit peu fréquemment, peut-être une fois par an ou à l’introduction de nouvelles opérations. Le résultat de la phase des prérequis est utilisé dans la *phase des flux*. Cette dernière est plus fréquente (périodicité mensuelle, par exemple).

### <a name="prerequisites-phase"></a>La phase des prérequis

Les étapes de cette phase capturent les exigences associées à un passage en revue régulier des services importants.

1. **Identifier les opérations d’entreprise critiques**. Identifiez les opérations stratégiques de l’entreprise. Les opérations d’entreprise sont indépendantes des fonctions de service de soutien. En d’autres termes, elles représentent les activités réelles que doit effectuer l’entreprise et elles sont prises en charge par un ensemble de services informatiques.

    Le terme *stratégique* (ou *critique pour l’entreprise*) reflète un impact grave pour l’entreprise si l’opération est empêchée. Par exemple, un revendeur en ligne peut avoir une opération métier, comme « permettre à un client d’ajouter un article au panier » ou « traiter un paiement par carte de crédit ». Si une de ces opérations échoue, un client ne peut pas mener à bien la transaction et l’entreprise ne peut pas réaliser de ventes.

1. **Faire correspondre les opérations aux services**. Établissez un mappage des opérations métier aux services qui les prennent en charge. Dans l'exemple du panier d'achats ci-dessus, plusieurs services peuvent être impliqués, comme un service de gestion des stocks et un service de panier d'achats. Pour traiter un paiement par carte de crédit, un service de paiement local peut interagir avec un service tiers de traitement des paiements.

1. **Analyser les dépendances entre les services**. La plupart des opérations métier nécessitent une orchestration entre plusieurs services qui en assurent la prise en charge. Il est important de comprendre les dépendances entre les services et le flux de transactions stratégiques via ces services.

    Prenez aussi en compte les dépendances entre les services locaux et les services Azure. Dans l’exemple de panier d’achats, le service de gestion des stocks d’inventaire peut être hébergé localement et recevoir des données entrées par les employés d’un entrepôt physique. Cependant, il peut stocker des données hors site dans un service Azure, comme [Stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction) ou dans une base de données, comme [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction).

À partir de ces activités est produite une série *d’indicateurs de tableau de bord* pour les opérations de service. Le tableau de bord mesure des critères tels que la disponibilité, l'extensibilité et la récupération d'urgence. Les métriques de tableau de bord expriment les critères opérationnels que le service doit respecter. Elles peuvent être exprimées à un niveau de granularité adapté au fonctionnement du service.

Le tableau de bord doit être exprimé en termes simples pour faciliter la discussion entre les responsables des résultats d’entreprise et les ingénieurs. Par exemple, une métrique de tableau de bord relative à l'extensibilité peut comporter un code couleur simple. Le vert indique que les critères définis sont remplis, le jaune qu'ils ne sont pas remplis mais qu'une correction planifiée est en cours d'implémentation, et le rouge qu'ils ne sont pas remplis et qu'aucun plan ni aucune action n'est en cours.

Il est important de souligner que ces métriques doivent refléter directement les besoins métier.

### <a name="service-review-phase"></a>Phase de passage en revue des services

La phase de passage en revue des services est essentielle dans le processus de passage en revue de l’adéquation opérationnelle. Elle comprend ces étapes :

1. **Mettre en place des métriques de service**. Utilisez les métriques de carte de performance pour superviser les services et garantir qu’ils répondent aux attentes métier. La supervision des services est essentielle. Si vous ne pouvez pas superviser un ensemble de services relativement aux exigences non fonctionnelles, envisagez d’afficher en rouge les métriques de carte de performance correspondantes. La première étape pour y remédier consiste à implémenter le monitoring du service en question. Par exemple, si l’entreprise attend d’un service qu’il fonctionne avec une disponibilité de 99,99 %, mais qu’aucune télémétrie de production n’est en place pour en mesurer la disponibilité, partez du principe que vous ne répondez pas à cette exigence.

2. **Prévoir des mesures de correction**. Pour chaque opération de service dont les métriques se trouvent sous le seuil acceptable, calculez ce que coûterait une correction du service permettant d’y remédier. Si ce coût est supérieur au revenu attendu du service, prenez en compte les coûts intangibles, comme l’expérience utilisateur. Par exemple, si les clients ont des difficultés à passer une commande en utilisant le service, ils risquent de choisir à la place un concurrent.

3. **Implémenter la correction**. Dès que les responsables de l'entreprise et l'équipe d'ingénierie se sont mis d'accord sur un plan, implémentez-le. Signalez l'état de l'implémentation à chaque passage en revue des métriques de tableau de bord.

Ce processus est itératif et dans l’idéal, l’entreprise doit avoir une équipe qui y est dédiée. Des réunions régulières doivent être organisées pour passer en revue les projets de correction existants, lancer le passage en revue fondamental des nouvelles charges de travail et effectuer le suivi de la carte de performance globale de l’entreprise. L’équipe doit avoir l’autorité nécessaire pour demander des comptes aux équipes de correction qui ne respectent pas les métriques ou sont en retard sur la planification.

## <a name="structure-of-the-review-team"></a>Structure de l’équipe de passage en revue

L’équipe responsable du passage en revue de l’adéquation opérationnelle se compose des rôles suivants :

- **Responsable métier :** Apporte les connaissances métier pour identifier et hiérarchiser les opérations métier critiques. Il compare également le coût des mesures d'atténuation à l'impact sur l'entreprise, et prend la décision finale concernant les mesures correctives à appliquer.

- **Responsable métier :** Décompose les opérations métier en parties discrètes et les associe aux services et à l'infrastructure, qu'ils soient locaux ou dans le cloud. Une connaissance approfondie des technologies associées à chaque opération est nécessaire.

- **Responsable de l’ingénierie :** Implémente les services associés à l’opération métier. Ces personnes doivent participer à la conception, à l’implémentation et au déploiement de solutions pour des problèmes liés aux exigences non fonctionnelles qui ne sont pas révélés par l’équipe de passage en revue.

- **Responsable des services :** Exploite les applications et services métier. Ils collectent des données de journalisation et d’utilisation de ces applications et services, Ces données sont utilisées pour identifier les problèmes et pour vérifier les correctifs une fois qu’ils sont déployés.

## <a name="review-meeting"></a>Réunion de passage en revue

Nous recommandons d’organiser des réunions régulières de votre équipe de passage en revue. Elle peut par exemple se réunir tous les mois, puis envoyer à la direction un rapport trimestriel sur l'état et les métriques.

Adaptez les détails du processus et des réunions à vos besoins spécifiques. Nous recommandons les tâches suivantes pour commencer :

1. Le responsable de l’entreprise et le responsable métier énumèrent et déterminent les exigences non fonctionnelles de chaque opération métier, avec la participation des responsables de l’ingénierie et des services. Pour les opérations métier qui ont été identifiées précédemment, passez en revue et vérifiez la priorité. Pour ce qui est des nouvelles opérations, attribuez-leur une priorité dans la liste existante.

2. Les responsables de l’ingénierie et des services mappent l’état actuel des opérations métier aux services cloud et locaux correspondants. Le mappage est une liste des composants de chaque service, sous la forme d’une arborescence des dépendances. Les responsables de l'ingénierie et des services déterminent ensuite les chemins critiques dans l'arborescence.

3. Les responsables de l’ingénierie et des services évaluent l’état actuel de la journalisation et du monitoring opérationnels des services listés à l’étape précédente. Une journalisation et une supervision robustes sont critiques : elles identifient les composants des services qui contribuent au non-respect des exigences non fonctionnelles. Si la journalisation et la supervision sont insuffisantes, l'équipe doit les mettre en place en créant et en implémentant un plan.

4. L'équipe crée des métriques de tableau de bord pour les nouvelles opérations métier. La carte de performance se compose de la liste des composants constitutifs de chaque service identifié à l’étape 2. Il est aligné sur les exigences non fonctionnelles et comprend une mesure de la façon dont chaque composant répond aux exigences.

5. Pour les composants constitutifs qui ne répondent pas aux exigences non fonctionnelles, l'équipe conçoit une solution globale et lui attribue un responsable de l'ingénierie. À ce stade, le responsable de l’entreprise et le responsable métier doivent alors établir un budget pour le travail de correction, en fonction du revenu attendu de l’opération métier.

6. Enfin, l'équipe évalue le travail de correction en cours. Chacune des métriques de carte de performance pour le travail en cours est passée en revue par rapport aux critères attendus. Pour les composants constitutifs qui satisfont aux critères des métriques, le responsable du service présente les données de journalisation et de supervision pour confirmer que les critères sont respectés. Pour les composants constitutifs qui ne répondent pas aux critères des métriques, chaque responsable de l'ingénierie explique les problèmes qui empêchent le respect des critères et présente les nouvelles conceptions permettant d'y remédier.

## <a name="recommended-resources"></a>Ressources recommandées

- [Piliers de la qualité logicielle](https://docs.microsoft.com/azure/architecture/guide/pillars).
    Cette section du Guide d’architecture des applications Azure décrit les cinq piliers de la qualité des logiciels : scalabilité, disponibilité, résilience, gestion et sécurité.
- [Dix principes de conception pour les applications Azure](https://docs.microsoft.com/azure/architecture/guide/design-principles).
    Cette section du Guide d’architecture des applications Azure présente un ensemble de principes de conception visant à rendre les applications plus évolutives, plus résilientes et plus faciles à gérer.
- [Concevoir des applications résilientes pour Azure](https://docs.microsoft.com/azure/architecture/resiliency).
    Ce guide commence par une définition du terme _résilience_ et des concepts associés. Il décrit ensuite un processus pour atteindre la résilience selon une approche structurée pendant la durée de vie d’une application, depuis la conception et l’implémentation jusqu’au déploiement et à l’exploitation.
- [Modèles de conception cloud](https://docs.microsoft.com/azure/architecture/patterns).
    Ces modèles de conception sont utiles aux équipes d’ingénieurs qui souhaitent créer des applications selon les piliers de la qualité logicielle.
- [Azure Advisor](https://docs.microsoft.com/azure/advisor).
    Advisor fournit des recommandations qui sont personnalisées en fonction de votre utilisation et de vos configurations pour vous permettre d’optimiser vos ressources en termes de haute disponibilité, sécurité, performances et coûts.
