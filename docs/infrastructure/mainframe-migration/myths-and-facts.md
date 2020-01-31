---
title: 'Migration d’ordinateurs mainframe : Mythes et réalités'
description: Migrez des applications d’environnements mainframe vers Azure, infrastructure fiable, hautement disponible et scalable pour les systèmes qui s’exécutent sur des ordinateurs mainframe.
author: njray
ms.author: v-nanra
ms.date: 12/27/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: e3e14bca45f8e5531e663c76b346f295ccb64319
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808751"
---
# <a name="mainframe-myths-and-facts"></a>Mythes et réalités concernant les ordinateurs mainframe

Les ordinateurs mainframe occupent une place importante dans l’histoire de l’informatique et restent viables pour des charges de travail très spécifiques. La plupart des gens s’accordent à dire que les ordinateurs mainframe constituent une plateforme éprouvée avec des procédures d’exploitation depuis longtemps établies qui en font des environnements robustes et fiables. Le logiciel s’exécute en fonction de l’utilisation, mesurée en MIPS (million d’instructions par seconde) et des rapports d’utilisation complets sont disponibles pour la rétrofacturation.

La fiabilité, la disponibilité et la puissance de traitement des ordinateurs mainframe ont pris des proportions presque mythiques. Pour évaluer les charges de travail mainframe qui sont les plus adaptées à Azure, vous voulez tout d’abord faire la distinction entre mythes et réalités.

## <a name="myth-mainframes-never-go-down-and-have-a-minimum-of-five-9s-of-availability"></a>Mythe : les ordinateurs mainframe ne tombent jamais en panne et ont un minimum de cinq 9 (99,999 %) de taux de disponibilité

Les systèmes d’exploitation et le matériel des ordinateurs mainframe sont considérés comme fiables et stables. Or, la réalité est que des temps d’arrêt doivent être planifiés pour la maintenance et les redémarrages (appelés chargements de programmes initiaux). Quand ces tâches sont prises en compte, une solution d’ordinateur mainframe est souvent plus proche de deux ou trois 9 de disponibilité, ce qui équivaut à celle des serveurs Intel haut de gamme.

Les ordinateurs mainframe demeurent aussi vulnérables face aux sinistres que tous les autres serveurs et nécessitent des onduleurs pour gérer ces types de défaillances.

## <a name="myth-mainframes-have-limitless-scalability"></a>Mythe : les ordinateurs mainframe présentent une scalabilité illimitée

La scalabilité d’un ordinateur mainframe dépend de la capacité de son logiciel système, comme CICS (Customer information control system), et de la capacité de nouvelles instances de moteurs et de stockage mainframe. Certaines grandes entreprises qui utilisent des ordinateurs mainframe ont personnalisé leur système CICS pour optimiser les performances et ont par ailleurs dépassé la capacité des plus grands ordinateurs mainframe disponibles.

## <a name="myth-intel-based-servers-are-not-as-powerful-as-mainframes"></a>Mythe : les serveurs Intel ne sont pas aussi puissants que les ordinateurs mainframe

Les nouveaux systèmes multicœurs Intel ont une capacité de calcul égale à celle des ordinateurs mainframe.

## <a name="myth-the-cloud-cant-accommodate-mission-critical-applications-for-large-companies-such-as-financial-institutions"></a>Mythe : le cloud ne peut pas prendre en charge les applications critiques des grandes entreprises, telles que les institutions financières

Même s’il peut exister des cas isolés où les solutions cloud ne sont pas satisfaisantes, cela s’explique en général par le fait que les algorithmes d’application ne peuvent pas être distribués. Ces quelques exemples représentent plutôt l’exception que la règle.

## <a name="summary"></a>Résumé

En comparaison, Azure offre une plateforme alternative capable de fournir des fonctions et fonctionnalités de mainframe équivalentes à un coût nettement inférieur. De plus, le coût total de possession (TCO) du modèle de coût basé sur l’utilisation et sur un abonnement du cloud est bien moins onéreux que les ordinateurs mainframe.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Assurer la transition d’ordinateurs mainframe vers Azure](./migration-strategies.md)
