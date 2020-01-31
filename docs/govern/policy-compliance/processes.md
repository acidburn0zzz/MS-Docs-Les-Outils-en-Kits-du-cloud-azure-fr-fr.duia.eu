---
title: Établir des processus d’adhésion à la stratégie
description: Établissez des processus pour garantir la conformité avec les stratégies de l’entreprise.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: bf69c13d80063e44a49d945908e2cc319b90ce3e
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807170"
---
<!-- markdownlint-disable MD026 -->

# <a name="establish-policy-adherence-processes"></a>Établir des processus d’adhésion à la stratégie

Après avoir établi vos déclarations de stratégie cloud et rédigé un guide de conception, vous devez créer des consignes pour être sûr que votre déploiement cloud reste conforme aux exigences de votre stratégie. Ces consignes devront englober les processus continus d’examen et de communication de votre équipe de gouvernance cloud, établir des critères pour déterminer à quel moment les violations des stratégies doivent être sanctionnées et définir les exigences relatives aux systèmes automatisés de surveillance et de conformité qui détecteront les violations et déclencheront des mesures correctives.

Consultez les sections sur les stratégies d’entreprise des [guides de gouvernance actionnables](../guides/index.md) pour découvrir des exemples de méthodes d’intégration du processus de conformité à la stratégie dans un plan de gouvernance cloud.

## <a name="prioritize-policy-adherence-processes"></a>Classer par ordre de priorité des processus d’adhérence à la stratégie

Combien d’investissements dans l’élaboration de processus sont nécessaires pour appuyer vos objectifs stratégiques ? En fonction de la taille et de la maturité de votre déploiement cloud, l’effort requis pour établir des processus qui prennent en charge la conformité et les coûts associés à cet effort peuvent varier considérablement.

Pour les petits déploiements comprenant des ressources de développement et de test, les exigences de la stratégie peuvent être simples et nécessiter peu de ressources dédiées pour y répondre. En revanche, un déploiement cloud mature et essentiel à votre mission, dont les besoins sont prioritaires en matière de sécurité et de performances, peut nécessiter une équipe d’employés, des processus internes étendus et des outils de surveillance personnalisés pour soutenir vos objectifs stratégiques.

Commencez par évaluer comment les processus décrits ci-dessous peuvent répondre aux exigences de votre stratégie. Déterminez la quantité d’efforts nécessaire pour investir dans ces processus, puis utilisez cette information pour établir un budget et des plans de dotation réalistes pour répondre à ces besoins.

## <a name="establish-cloud-governance-team-processes"></a>Établir des processus d’équipe pour la gouvernance cloud

Avant de définir les déclencheurs de la correction de la conformité à la votre stratégie, vous devez établir les processus globaux que votre équipe utilisera, et la façon dont l’information sera partagée et transmise entre le personnel informatique et l’équipe de gouvernance cloud.

### <a name="assign-cloud-governance-team-members"></a>Affectation des membres de l’équipe de gouvernance cloud

Votre équipe de gouvernance cloud fournira des conseils continus sur la conformité à la stratégie et s’occupera des questions liées à la gestion de la stratégie qui émergent lors du déploiement et de l’exploitation de vos actifs cloud. Lors de la création de cette équipe, invitez les membres du personnel qui disposent d’une expertise dans les domaines couverts par les déclarations de stratégie définies et les risques identifiés.

Vous pouvez vous en tenir à quelques administrateurs système lors des premiers tests de déploiement. Ils établiront les bases de la gouvernance. Au fur et à mesure que vos processus de gouvernance évoluent, vous devrez examiner régulièrement les membres de l’équipe chargée des conseils cloud, pour vérifier qu’ils sont capables de répondre correctement les nouveaux risques possibles et les dernières exigences de stratégie. Identifiez les membres de votre personnel informatique et administratif ayant une expérience pertinente ou un intérêt dans des domaines spécifiques de gouvernance et intégrez-les dans vos équipes de façon permanente ou temporaire en fonction des besoins.

### <a name="reviews-and-policy-iteration"></a>Révisions et itération de la stratégie

Au fur et à mesure que d’autres ressources et charges de travail seront déployées, l’équipe de gouvernance du cloud devra s’assurer que les nouvelles charges de travail ou les nouvelles ressources sont conformes aux exigences de la stratégie. Évaluez les nouvelles exigences des équipes de développement des charges de travail pour vous assurer que les déploiements qu’ils prévoient sont alignés sur vos guides de conception et pour mettre à jour vos politiques pour prendre en charge ces exigences le cas échéant.

Évaluez les nouveaux risques potentiels et mettez à jour les instructions de stratégie et les guides de conception. Collaborez avec le personnel informatique et les équipes responsables des charges de travail pour évaluer de manière continue les nouveaux services et fonctionnalités Azure. Planifiez également des cycles d’examen réguliers pour chacune des cinq disciplines de gouvernance. Vous pourrez ainsi vous assurer que la stratégie est à jour et conforme.

### <a name="education"></a>Formation

Pour être conforme à votre stratégie, le personnel et les développeurs de votre service informatique doivent comprendre ses exigences vis-à-vis de leurs domaines de responsabilité. Prévoyez de consacrer des ressources à la documentation des décisions et des exigences, et formez toutes les équipes concernées à l’aide de vos guides de conception pour la prise en charge des exigences de votre stratégie.

Au fur et à mesure que votre stratégie évolue, mettez régulièrement à jour la documentation et le matériel de formation, et veillez à ce que toutes les exigences et les directives mises à jour soient communiquées au personnel informatique concerné lors des formations.

À différentes étapes de votre parcours d’adoption du cloud, il vous sera judicieux de vous adresser aux partenaires et de consulter les programmes de formation professionnelle pour améliorer la formation de votre équipe, tant sur le plan technique que sur celui des procédures. En outre, pour de nombreuses organisations, les certifications formelles représentent un ajout précieux à leur éventail d’outils de formation. Elles doivent donc être prises en considération.

### <a name="establish-escalation-paths"></a>Organiser la remontée des informations

Si une ressource n’est pas conforme, qui en est avisé ? Si le personnel informatique détecte un problème de conformité à la stratégie, à qui s’adresse-t-il ? Assurez-vous que la remontée des informations vers l’équipe de gouvernance cloud est clairement définie. Veillez à ce que les canaux de communication soient tenus à jour afin de refléter les modifications au sein de votre personnel et de votre organisation.

## <a name="violation-triggers-and-actions"></a>Déclencheurs de violations et actions

Après avoir défini votre équipe de gouvernance cloud et ses processus, vous devez définir explicitement les déclencheurs, c’est-à-dire les événements constituant une violation de conformité susceptible d’entraîner des actions. Puis, vous devrez aussi définir quelles devraient être ces actions.

### <a name="define-triggers"></a>Définir des déclencheurs

Passez en revue les exigences de chacun de vos énoncés de votre stratégie, afin de déterminer ce qui en constitue une violation. Générez vos déclencheurs en utilisant les informations que vous avez déjà établies dans le cadre du processus de définition de la stratégie.

- **Tolérance aux risques :** créez des déclencheurs de violation basés sur les mesures et les indicateurs de risque que vous avez établis dans le cadre de votre [analyse de tolérance au risque](./risk-tolerance.md).
- **Exigences de stratégies définies :** les énoncés de stratégie peuvent fournir des contrats de niveau de service (SLA), des exigences de continuité d’activité et reprise d’activité (BRCD) ou des exigences de performances qui doivent servir de base aux déclencheurs de conformité.

### <a name="define-actions"></a>Définir des actions

Chaque déclencheur de violation doit entraîner une action. Les actions déclenchées doivent toujours déclencher l’envoi d’une notification à un membre approprié du personnel informatique ou de l’équipe de gouvernance du cloud lorsqu’une violation se produit. Cette notification peut entraîner un examen manuel du problème de conformité ou déclencher un processus de correction prédéfini en fonction du type et de la gravité de la violation détectée.

Exemples de déclencheurs de violations et d’actions :

| Discipline de gouvernance cloud | Exemple de déclencheur | Exemple d’action |
|-----------------------------|----------------|---------------|
| Cost Management | Les dépenses cloud mensuelles sont 20 % plus élevées que prévu. | Informez le responsable de l’unité de facturation qui examinera l’utilisation des ressources. |
| Base de référence de la sécurité | Détectez toute activité d’utilisateur suspecte. | Prévenez l’équipe de sécurité informatique et désactivez le compte de l’utilisateur suspect. |
| Cohérence des ressources | Une charge de travail utilise plus de 90 % du processeur. | Prévenez l’équipe des opérations informatiques et effectuez un scale-out des ressources supplémentaires pour gérer la charge. |

## <a name="automation-of-monitoring-and-compliance"></a>Automatisation de la surveillance et de la conformité

Lorsque vous avez défini vos déclencheurs et actions de violation de conformité, vous pouvez commencer à planifier la meilleure façon d’utiliser les outils de journalisation et de création de rapport, ainsi que les autres fonctionnalités de votre plate-forme cloud pour automatiser la surveillance et la mise en conformité vis-à-vis de votre stratégie.

Pour obtenir des conseils dans le choix du meilleur modèle de supervision pour votre déploiement, consultez le [guide de décision sur la journalisation et création de rapports](../../decision-guides/logging-and-reporting/index.md).

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur la conformité réglementaire dans le cloud.

> [!div class="nextstepaction"]
> [Conformité réglementaire](./regulatory-compliance.md)
