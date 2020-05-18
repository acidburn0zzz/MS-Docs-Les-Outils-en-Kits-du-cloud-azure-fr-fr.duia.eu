---
title: Créer une cohérence de cloud hybride
description: Utilisez le Cloud Adoption Framework pour Azure afin d’apprendre à définir l’approche qui permet de créer un cloud hybride cohérent.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/27/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 609c4f9f369e27c699f72cf85ebe311dbf918019
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83219272"
---
<!-- cSpell:ignore ISVs Bitnami Yourhosting Revera Avanade Pulsant PricewaterhouseCoopers Pointnext -->

# <a name="create-hybrid-cloud-consistency"></a>Créer une cohérence de cloud hybride

Cet article vous guide dans les approches générales pour la création de la cohérence de cloud hybride.

Les modèles de déploiement hybrides pendant la migration peuvent réduire les risques et contribuer à une transition fluide d’infrastructure. Les plateformes cloud offrent le meilleur niveau de flexibilité quand il s’agit des processus métier. De nombreuses organisations hésitent à migrer vers le cloud. Elles préfèrent garder un contrôle total sur leurs données les plus sensibles. Malheureusement, les serveurs locaux ne permettent pas le même taux d’innovation que le cloud. Une solution cloud hybride offre l’accès à l’innovation rapide dans le cloud et au contrôle qu’offre la gestion locale.

## <a name="integrate-hybrid-cloud-consistency"></a>Intégrer la cohérence de cloud hybride

L’utilisation d’une solution de cloud hybride permet aux organisations d’adapter l’échelle des ressources de calcul. Elle élimine aussi la nécessité de consentir des investissements conséquents pour gérer de brefs pics de demande. Les changements dans votre entreprise peuvent entraîner la libération de ressources locales pour des données ou des applications plus sensibles. Il est plus facile, plus rapide et moins onéreux de mettre hors service les ressources cloud. Vous payez uniquement pour les ressources que votre organisation utilise temporairement, au lieu de devoir acheter et gérer des ressources supplémentaires. Cette approche réduit la quantité d’équipements qui pourraient rester inutilisés pendant de longues périodes. Le cloud computing hybride est une plateforme offrant tous les avantages du cloud computing (flexibilité, extensibilité et rentabilité), et une exposition minimale des données conservées en local.

![Création de la cohérence de cloud hybride entre identité, gestion, sécurité, données, développement et DevOps](../../_images/hybrid-consistency.png)
_Figure 1 : Création de la cohérence de cloud hybride entre identité, gestion, sécurité, données, développement et DevOps._

Une solution de cloud hybride véritable doit fournir quatre composants, chacun d’eux apportant des avantages significatifs :

- **Identité commune pour les applications cloud et locales :** Ce composant améliore la productivité des utilisateurs en leur fournissant l’authentification unique (SSO) pour se connecter à toutes leurs applications. Elle garantit également la cohérence quand les applications et utilisateurs franchissent les limites du réseau/cloud.
- **Sécurité et gestion intégrées dans l’ensemble de votre cloud hybride :** Ce composant procure un moyen cohésif de superviser, gérer et sécuriser l’environnement, avec une visibilité et un contrôle accrus.
- **Plateforme de données cohérente pour le centre de données et le cloud :** Ce composant offre la portabilité des données, combinée avec un accès transparent aux services de données en local et dans le cloud pour connaître plus en détail toutes les sources de données.
- **Développement unifié et DevOps dans les centres de données cloud et locaux :** Ce composant vous permet de déplacer des applications entre les deux environnements en fonction des besoins. La productivité des développeurs est améliorée, car les deux emplacements disposent désormais du même environnement de développement.

Voici quelques exemples de ces composants d’un point de vue Azure :

- Azure Active Directory (Azure AD), qui fonctionne avec Active Directory en local pour fournir une identité commune à tous les utilisateurs. L’authentification unique en local et via le cloud permet aux utilisateurs d’accéder facilement et en toute sécurité aux applications et ressources dont ils ont besoin. Les administrateurs peuvent gérer les contrôles de sécurité et de gouvernance, avec la possibilité d’adapter ces autorisations sans affecter l’expérience utilisateur.
- Azure fournit des services intégrés de gestion et de sécurité pour les infrastructures cloud et locales. Ces services comprennent tout un ensemble intégré d’outils utilisés pour analyser, configurer et protéger les clouds hybrides. Cette approche de bout en bout de la gestion concerne plus particulièrement les défis du monde réel auxquels font face les organisations qui envisagent une solution de cloud hybride.
- Le cloud hybride Azure fournit des outils courants qui garantissent un accès sécurisé à toutes les données, efficacement et en toute transparence. Les services de données Azure s’associent à Microsoft SQL Server pour créer une plateforme de données cohérente. Un modèle de cloud hybride cohérent permet aux utilisateurs de travailler avec des données opérationnelles et analytiques. Les mêmes services sont fournis localement et dans le cloud pour l’entreposage des données, leurs données et leur visualisation.
- Les services cloud Azure, associés à Azure Stack en local, fournissent un développement unifié et DevOps. La cohérence dans le cloud et en local signifie que votre équipe DevOps peut créer des applications qui s’exécutent dans un environnement et peut facilement déployer sur l’emplacement approprié. Vous pouvez aussi réutiliser les modèles dans la solution hybride, ce qui peut grandement simplifier les processus DevOps.

## <a name="azure-stack-in-a-hybrid-cloud-environment"></a>Azure Stack dans un environnement cloud hybride

Azure Stack est une solution de cloud hybride qui permet aux organisations d’exécuter des services Azure cohérents dans leur centre de données. Elle offre une expérience de développement, de gestion et de sécurité simplifiée, compatible avec les services cloud publics d’Azure. Azure Stack est une extension d’Azure. Elle vous permet d’exécuter des services Azure à partir de vos environnements locaux et de passer au cloud Azure si nécessaire.

Avec Azure Stack, vous pouvez déployer et exploiter à la fois l’IaaS et la PaaS en utilisant les mêmes outils et en offrant la même expérience que le cloud public Azure. La gestion d’Azure Stack, via le portail de l’interface utilisateur web ou PowerShell, a une apparence cohérente pour les administrateurs informatiques et les utilisateurs finaux auprès d’Azure.

Azure et Azure Stack offrent de nouveaux cas d’utilisation hybride pour les applications orientées client et métier internes :

- **Solutions edge et déconnectées.** Afin de répondre aux besoins de latence et de connectivité, les utilisateurs peuvent traiter les données localement dans Azure Stack, puis les agréger dans Azure pour une analytique plus poussée. Ils peuvent utiliser une logique d’application commune sur les deux systèmes. De nombreux clients sont intéressés par ce scénario de périphérie entre différents contextes, notamment les sites de production, les bateaux de croisière et les sites miniers.
- **Applications cloud conformes à diverses réglementations.** Les clients peuvent développer et déployer des applications dans Azure, en profitant de l’entière flexibilité de déployer localement sur Azure Stack pour répondre aux exigences réglementaires ou stratégiques. Le code n’a pas besoin d’être modifié. Les exemples d’applications incluent l’audit global, les rapports financiers, les opérations de change, les jeux en ligne et les notes de frais. Les clients cherchent parfois à déployer des instances différentes de la même application sur Azure ou Azure Stack, selon les exigences techniques et professionnelles. Même si Azure satisfait à la plupart des exigences, Azure Stack complète l’approche de déploiement si nécessaire.
- **Modèle d’application cloud en local.** Les clients peuvent utiliser les services web, conteneurs, microservices et architectures serverless Azure pour mettre à jour et étendre des applications existantes ou en générer de nouvelles. Vous pouvez utiliser des processus DevOps cohérents sur Azure dans le cloud et sur Azure Stack en local. Il existe un intérêt croissant pour la modernisation des applications, notamment des applications stratégiques de base.

Vous disposez de deux options pour déployer Azure Stack :

- **Systèmes intégrés Azure Stack :** Les systèmes intégrés Azure Stack sont disponibles par le biais de Microsoft et des fournisseurs de matériel partenaires, qui aboutit à la création d’une solution combinant innovation cloud et simplicité de gestion. Azure Stack étant proposé en tant que système intégré de matériels et de logiciels, vous bénéficiez de la flexibilité et du contrôle adéquats, tout en adoptant l’innovation propre au cloud. Les systèmes intégrés d’Azure Stack ont une taille comprise entre 4 et 12 nœuds. Ils sont pris en charge conjointement par le partenaire fournisseur de matériel et Microsoft. Utilisez des systèmes intégrés Azure Stack pour autoriser de nouveaux scénarios pour vos charges de travail de production.
- **Kit de développement Azure Stack :** Le Kit de développement Microsoft Azure Stack est un déploiement à nœud unique d’Azure Stack. Vous pouvez l’utiliser pour évaluer et découvrir Azure Stack. Vous pouvez également utiliser le kit comme environnement de développement, où vous pouvez développer à l’aide d’API et d’outils cohérents avec Azure. Le Kit de développement Azure Stack n’est pas destiné à être utilisé en tant qu’environnement de production.

## <a name="azure-stack-one-cloud-ecosystem"></a>Écosystème cloud Azure Stack

Vous pouvez accélérer les initiatives Azure Stack avec l’écosystème Azure complet :

<!-- cSpell:ignore ISVs Bitnami Yourhosting Revera Avanade Pulsant PricewaterhouseCoopers -->

- Azure garantit que la plupart des applications et services certifiés pour Azure fonctionnent sur Azure Stack. Plusieurs éditeurs de logiciels indépendants étendent leurs solutions sur Azure Stack. Ces éditeurs de logiciels indépendants sont notamment Bitnami, Docker, Kemp Technologies, Pivotal Cloud Foundry, Red Hat Enterprise Linux et SUSE Linux.
- Vous pouvez décider qu’Azure Stack doit être fourni et utilisé comme un service complètement managé. Plusieurs partenaires recevront des offres de services managés sur Azure et Azure Stack sous peu. Ces partenaires sont Tieto, Yourhosting, Revera, Pulsant et NTT. Ces partenaires fournissent des services gérés pour Azure via le programme fournisseur de solutions cloud (CSP). Ils étendent leurs offres pour y inclure des solutions hybrides.
- En guise d’exemple de solution cloud hybride entièrement gérée, Avanade propose une offre tout-en-un. Elle comprend les services de transformation cloud, les logiciels, l’infrastructure, l’installation et la configuration, ainsi que les services gérés en continu. De cette façon, les clients peuvent utiliser Azure Stack de la même manière qu’Azure aujourd’hui.
- Les fournisseurs peuvent aider à accélérer les initiatives de modernisation des applications en créant des solutions Azure de bout en bout pour les clients. Ils apportent des compétences Azure approfondies, une connaissance du domaine et du secteur ainsi qu’une expertise sur les processus (par exemple, DevOps). Chaque cloud Azure Stack est une opportunité pour le fournisseur de concevoir la solution et d’orienter le déploiement du système. Il peut également personnaliser les fonctionnalités incluses et fournir des activités d’exploitation. Voici quelques exemples de fournisseurs : Avanade, DXC, Dell EMC Services, InFront Consulting Group, HPE Pointnext et PwC (Pricewaterhouse Coopers).
