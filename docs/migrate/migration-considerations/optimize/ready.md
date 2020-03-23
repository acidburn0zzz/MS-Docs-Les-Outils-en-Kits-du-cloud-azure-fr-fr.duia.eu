---
title: Préparer une application migrée pour la promotion en production
description: Utilisez le Cloud Adoption Framework pour Azure afin de découvrir la validation impliquée dans la préparation d’une application migrée pour la promotion en production.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4b48a4ceea5d322e4a993cdba474269d73fbc7e3
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79312014"
---
# <a name="prepare-a-migrated-application-for-production-promotion"></a>Préparer une application migrée pour la promotion en production

Après la promotion d’une charge de travail, le trafic utilisateur de production est acheminé vers les ressources migrées. Les activités de préparation offrent la possibilité de préparer la charge de travail à ce trafic. Voici quelques considérations métier et technologiques qui vous aideront à guider les activités de préparation.

## <a name="validate-the-business-change-plan"></a>Valider le plan des changements opérationnels

La transformation se produit lorsque des utilisateurs professionnels ou des clients tirent parti d’une solution technique pour exécuter des processus qui stimulent l’activité. La préparation est une bonne occasion de valider le [plan des changements opérationnels](./business-change-plan.md) et de garantir une formation appropriée aux équipes techniques et à celles chargées des activités qui sont concernées. En particulier, assurez-vous que les aspects technologiques suivants du plan des changements sont correctement communiqués :

- La formation des utilisateurs finaux est terminée (ou du moins planifiée).
- Toutes les fenêtres de panne ont été communiquées et approuvées.
- Les données de production ont été synchronisées et validées par les utilisateurs finaux.
- Validez le calendrier de promotion et d’adoption et vérifiez que les chronologies et les modifications ont été communiquées aux utilisateurs finaux.

## <a name="final-technical-readiness-tests"></a>Tests finaux de la préparation technique

*Prêt* est la dernière étape avant la mise en production. Cela signifie qu’il s’agit également de la dernière possibilité de tester la charge de travail. Voici quelques tests recommandés au cours de cette phase :

- **Test de l’isolement réseau.** Testez et surveillez le trafic pour vous assurer d’une isolation appropriée et de l’absence de vulnérabilités inattendues sur le réseau. Vérifiez également qu’aucun routage de réseau à interrompre pendant le basculement n’est confronté à un trafic inattendu.
- **Test des dépendances.** Vérifiez que toutes les dépendances d’applications de charge de travail ont été migrées et sont accessibles à partir des ressources migrées.
- **Test de la continuité d’activité et de la reprise d’activité (BCDR).** Vérifiez que tous les SLA de sauvegarde et de récupération sont établis. Si possible, effectuez une récupération complète des ressources à partir de la solution BCDR.
- **Test d’itinéraires d’utilisateurs finaux.** Vérifiez les modèles de trafic et le routage relatifs au trafic des utilisateurs finaux. Veillez à ce que le niveau de performance du réseau s’aligne sur les attentes.
- **Vérification du niveau de performance final.** Assurez-vous que le test de performance a été effectué et approuvé par les utilisateurs finaux. Exécutez tout test de performance automatisé.

## <a name="final-business-validation"></a>Validation d’activité finale

Une fois que le plan des changements opérationnels et la préparation technique ont été validés, les étapes finales suivantes peuvent terminer la validation d’activité :

- **Validation des coûts (plan et réel).** Les tests sont susceptibles d’entraîner des modifications de dimensionnement et d’architecture. Assurez-vous que la tarification du déploiement réel s’aligne toujours sur le plan d’origine.
- **Communication et exécution du plan de basculement.** Avant le basculement, communiquez le plan de basculement et exécutez-le en conséquence.

## <a name="next-steps"></a>Étapes suivantes

Une fois toutes les activités de préparation terminées, il est temps de [promouvoir la charge de travail](./promote.md).

> [!div class="nextstepaction"]
> [Qu’est-ce qui est nécessaire pour promouvoir une ressource migrée en production ?](./promote.md)
