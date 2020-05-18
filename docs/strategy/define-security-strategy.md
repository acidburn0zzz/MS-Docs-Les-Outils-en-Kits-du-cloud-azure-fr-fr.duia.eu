---
title: Définir une stratégie de sécurité
description: Le Cloud Adoption Framework pour Azure explique comment développer une argumentation métier à l’appui d’une migration vers le cloud.
author: MarkSimos
ms.author: mas
ms.date: 04/04/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 36fa032ce989dedd393886e7154aa46e1c7e376b
ms.sourcegitcommit: 60d8b863d431b5d7c005f2f14488620b6c4c49be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83230621"
---
<!-- cSpell:ignore MarkSimos NIST CISO COVID -->

# <a name="define-a-security-strategy"></a>Définir une stratégie de sécurité

Les objectifs fondamentaux d’une organisation de sécurité ne changent pas avec l’adoption de services cloud. En revanche, ce qui change, c’est la manière de les atteindre. Les équipes de sécurité doivent toujours se concentrer sur la réduction des risques liés aux attaques et s’efforcer d’intégrer des garanties de confidentialité, d’intégrité et de disponibilité dans l’ensemble des systèmes d’information et des données.

## <a name="modernize-your-security-strategy"></a>Moderniser votre stratégie de sécurité

À mesure que l’organisation adopte le cloud et l’utilise dans la durée, les équipes de sécurité doivent moderniser leurs stratégies, architectures et technologies. Si la taille et le nombre des changements peuvent à première vue sembler colossaux, la modernisation du programme de sécurité permet à la sécurité de s’affranchir de certains fardeaux associés aux anciennes approches. Une organisation peut fonctionner temporairement avec une stratégie et des outils hérités, mais il est difficile de se contenter durablement à cette approche compte tenu du rythme de l’évolution du cloud et de l’environnement de menace :

- Les équipes de sécurité risquent de se trouver écartées de la prise de décision en matière d’adoption du cloud si elles s’en tiennent au principe hérité de sécurité « autonome » où la réponse initiale est toujours « non », au lieu de collaborer avec les équipes informatiques et commerciales afin de minimiser les risques tout en permettant la conduite des affaires.
- Les équipes en charge de la sécurité éprouveront des difficultés à détecter et résoudre des attaques dans le cloud si elles s’obligent à n’utiliser que des outils locaux hérités et appliquent au pied de la lettre la doctrine consistant à limiter au périmètre réseau le traitement de l’ensemble des opérations de défense et de surveillance. La défense à l’échelle du cloud impose le recours à des fonctionnalités de détection et d’automatisation natives du cloud et l’introduction d’un périmètre d’identité pour la surveillance et la protection des ressources cloud et mobiles.

Parce que cette transformation peut être conséquente, nous recommandons aux équipes de sécurité d’adopter une approche agile de la modernisation de la sécurité, qui réforme rapidement les aspects les plus critiques de la stratégie, et s’améliore par la suite de façon continue et progressive.

### <a name="security-of-the-cloud-and-from-the-cloud"></a>Sécurité du cloud et au sein du cloud

Pendant que votre organisation adopte des services cloud, les équipes de sécurité poursuivent deux objectifs majeurs :

- **Sécurité\* du \*cloud (sécurisation des ressources cloud) :** La sécurité doit être intégrée dans la planification et l’exploitation des services cloud pour s’assurer que ces garanties de sécurité fondamentales sont appliquées de manière cohérente à toutes les ressources.
- **Sécurité\* au sein du \*cloud (utilisant le cloud pour transformer la sécurité) :** La sécurité doit immédiatement commencer à planifier et penser la façon d’utiliser les technologies cloud pour moderniser les outils et processus de sécurité, en particulier ceux qui sont intégrés en mode natif. De plus en plus d’outils de sécurité sont hébergés dans le cloud et offrent des fonctionnalités difficiles ou impossibles à exploiter dans un environnement local.

De nombreuses organisations commencent par traiter le cloud comme un _centre de données virtuel_ supplémentaire, ce qui constitue un bon point de départ pour la sécurité du cloud. La plupart des organisations qui se modernisent en utilisant la sécurité au sein du cloud dépassent rapidement les limites de cette approche. La sécurisation d’un centre de données à définition logicielle en se servant d’outils hébergés dans le cloud offre des capacités allant au-delà de ce que des modèles locaux peuvent offrir :

- Rapidité de l’activation et de la mise à l’échelle des capacités de sécurité.
- Efficacité élevée de l’inventaire des ressources et de la découverte de l’hygiène de configuration de la sécurité.
- Évaluation continue de la posture et des contrôles de sécurité de l’organisation.
- Amélioration considérable de la détection des menaces qui exploite de vastes référentiels de renseignement sur les menaces et la capacité de traitement/stockage pratiquement illimitée du cloud.

### <a name="the-right-level-of-security-friction"></a>Niveau approprié de friction de sécurité

La sécurité créant naturellement une friction qui ralentit les processus, il est essentiel d’identifier les éléments sains dans vos processus informatiques et de DevOps, et ceux qui ne le sont pas :

- **Friction saine :** Tout comme la résistance à l’exercice rend un muscle plus fort, l’intégration du niveau approprié de friction de sécurité renforce le système ou l’application en forçant une réflexion critique au moment opportun. Celle-ci consiste généralement à examiner comment et pourquoi un attaquant peut tenter de compromettre une application ou un système pendant la conception, ainsi que lors de l’identification, de l’examen et, idéalement, de la correction des vulnérabilités qu’un attaquant pourrait exploiter dans du code logiciel, des configurations ou des pratiques opérationnelles.
- **Friction malsaine :** Entrave plus qu’elle ne protège. Cela se produit souvent lorsque des bogues de sécurité générés par des outils présentent un taux élevé de faux positifs (tels que de fausses alarmes), ou lorsque l’effort de détection ou de résolution d’éventuels problèmes de sécurité dépasse de loin l’impact potentiel d’une attaque.

### <a name="standalone-and-integrated-responsibilities"></a>Responsabilités autonomes et intégrées

Pour garantir la confidentialité, l’intégrité et la disponibilité, les experts en sécurité doivent recourir à des fonctions de sécurité dédiées, et travailler en étroite collaboration avec d’autres équipes au sein de l’organisation :

- **Fonctions de sécurité uniques :** Les équipes de sécurité exercent au sein de l’organisation des fonctions autonomes et exclusives, telles que la conduite des opérations de sécurité ou la gestion des vulnérabilités.
- **Intégration de la sécurité dans d’autres fonctions :** Les équipes de sécurité exercent également un rôle d’experts pour d’autres équipes et fonctions de l’organisation, qui pilotent des initiatives commerciales, évaluent les risques, conçoivent ou développent des applications, et exploitent des systèmes informatiques. Les équipes de sécurité conseillent ainsi les autres équipes en contextualisant les attaquants, les méthodes et tendances des attaques, les vulnérabilités susceptibles de permettre un accès non autorisé, et les options de résolution ou de contournement des problèmes, ainsi que les avantages ou écueils potentiels respectifs de celles-ci. Cette fonction de sécurité fait figure de fonction de qualité, car elle opère dans de nombreux emplacements de toutes tailles, pour produire un résultat unique.

Pour assumer ces responsabilités tout en suivant le rythme rapide de l’évolution du cloud et de la transformation des activités, les équipes de sécurité doivent moderniser leurs outils, technologies et processus.

## <a name="transformations-mindsets-and-expectations"></a>Transformations, mentalités et attentes

De nombreuses organisations gèrent une chaîne de transformations simultanées multiples en leur sein. Ces bouleversements internes commencent généralement parce que presque tous les marchés externes se transforment en réponse aux nouvelles préférences des clients pour des technologies mobiles et cloud. Les organisations sont souvent confrontées à la menace concurrentielle de nouvelles start-ups et à la transformation numérique de concurrents traditionnels qui peuvent perturber le marché.

![Chaîne de transformations simultanées au sein de l’organisation](../_images/security/transformation-chain.png)

Le processus de transformation interne comprend généralement trois types de transformations :

- **Transformation numérique** de l’entreprise pour saisir de nouvelles opportunités et rester compétitive face aux start-ups numériques natives.
- **Transformation technologique** du service informatique pour soutenir l’initiative avec des services cloud, des pratiques de développement modernisées et d’autres changements connexes.
- **Transformation de la sécurité** pour l’adapter au cloud et faire face à un environnement de menaces de plus en plus sophistiqué.

### <a name="internal-conflict-can-be-costly"></a>Coût potentiel d’un conflit interne

Tout changement est source de stress et de conflits, et peut enrayer le processus de décision. C’est particulièrement vrai en matière de sécurité, où la responsabilité du risque de sécurité pèse souvent erronément sur les experts en la matière (équipes de sécurité), plutôt que sur les propriétaires des ressources (entrepreneurs) qui doivent répondre des résultats commerciaux et de tous les autres types de risques. Ce glissement de responsabilité se produit souvent parce que toutes les parties intéressées considèrent à tort la sécurité comme un problème technique ou absolu à résoudre, plutôt que comme un risque continu dynamique comparable à de l’espionnage industriel et à d’autres activités criminelles classiques.

Pendant cette période de transition, les responsables de toutes les équipes doivent œuvrer activement à modérer les conflits susceptibles à la fois de faire dérailler des projets critiques et d’inciter les équipes à outrepasser les processus d’atténuation des risques de sécurité. Des conflits intestins entre équipes peuvent avoir les conséquences néfastes suivantes :

- **Accroissement du risque de sécurité**, par exemple, en raison de la survenance d’incidents de sécurité évitables ou de dommages occasionnés par des attaques (en particulier, lorsque des équipes frustrées par des mesures de sécurité contournent les procédures normales ou quand des attaquants parviennent facilement à leurrer des dispositifs de sécurité obsolètes).
- **Impact négatif sur l’activité ou la mission** , par exemple, quand des processus métier ne sont pas activés ou mis à jour assez rapidement pour répondre aux besoins du marché (souvent lorsque des processus de sécurité obèrent des initiatives commerciales clés).

Il est essentiel de rester conscient de la santé des relations au sein des équipes et entre elles pour les aider à naviguer dans un paysage changeant qui pourrait avoir pour effet de mettre en danger certains membres précieux des équipes ou de les déstabiliser. La patience, l’empathie et l’éducation en lien avec ces attitudes, ainsi que le potentiel positif de l’avenir aideront vos équipes à mieux traverser cette période, générant ainsi de bons résultats sur le plan de la sécurité de l’organisation.

Les dirigeants peuvent aider à promouvoir des changements de culture en adoptant des attitudes proactives concrètes telles que les suivantes :

- Démonstration publique du comportement attendu des équipes.
- Transparence concernant les défis liés aux changements, en mettant l’accent sur leurs propres difficultés à s’adapter.
- Rappel régulier aux équipes de l’urgence et de l’importance de modernisation et de l’intégration de la sécurité.

### <a name="cybersecurity-resilience"></a>Résilience à la cybersécurité

Bon nombre de stratégies de sécurité classiques se concentraient uniquement sur la prévention des attaques, ce qui est insuffisant pour les menaces modernes. Les équipes de sécurité doivent veiller à ce que leur stratégie aille plus loin et permette une détection, un traitement et une récupération rapides des attaques afin d’augmenter la résilience. Les organisations doivent admettre l’hypothèse que les attaquants parviendront à compromettre certaines ressources, et veiller à ce que les ressources et les conceptions techniques respectent un équilibre entre la prévention et la gestion des attaques (au lieu de l’approche par défaut classique consistant à tenter uniquement de prévenir les attaques).

De nombreuses organisations sont déjà engagées dans cette voie, qui ont fait l’expérience de l’augmentation constante du volume et de la sophistication des attaques au cours des dernières années. Le parcours commence souvent par un incident majeur déclenchant une puissante réaction émotionnelle qui a pour effet de balayer tout sentiment préalable d’invulnérabilité et de sécurité. Bien que ce type d’événement ne soit pas aussi grave qu’un décès, il peut susciter une chaîne de réactions similaires, allant du déni à l’acceptation. Si cette hypothèse d’« échec » peut être difficile à accepter pour certains de prime abord, elle présente d’étroites similitudes avec le principe d’ingénierie bien connu de « fiabilité » qui permet à vos équipes de se concentrer sur une meilleure définition du succès : la résilience.

Les fonctions du [NIST cybersecurity framework](https://www.nist.gov/cyberframework) servent de guide utile sur la manière d’équilibrer les investissements entre les activités complémentaires d’identification, de protection, de détection, de réponse et de récupération dans le cadre d’une stratégie résiliente.

Pour en savoir plus sur la résilience de la cybersécurité et les finalités ultimes des contrôles de cybersécurité, consultez [Comment limiter les risques pour votre organisation](https://docs.microsoft.com/azure/architecture/framework/security/resilience).

### <a name="how-the-cloud-is-changing-security"></a>Comment le cloud change la sécurité

Le passage au cloud pour la sécurité est plus qu’un simple changement technologique. Il participe d’un glissement générationnel de la technologie qui s’apparente au passage des ordinateurs mainframe aux ordinateurs de bureau et aux serveurs d’entreprise. Pour réussir à gérer ce changement, les équipes de sécurité doivent modifier radicalement leurs attentes et attitudes. L’adoption d’attentes et d’attitudes appropriées réduira les conflits au sein de votre organisation et augmentera l’efficacité des équipes de sécurité.

Si ces attentes et attitudes pourraient faire partie de tout plan de modernisation de la sécurité, le rythme rapide d’évolution du cloud fait de leur adoption une priorité urgente.

- **Partenariat avec objectifs partagés.** À l’ère des prises de décision rapides et de l’évolution constante des processus, la sécurité ne peut plus se contenter d’une approche « autonome » de l’approbation ou du refus des changements d’environnement. Les équipes de sécurité doivent collaborer étroitement avec les équipes commerciales et informatiques pour fixer des objectifs communs en matière de productivité, de fiabilité et de sécurité, et travailler collectivement avec ces partenaires pour les atteindre.

  Ce partenariat est la forme ultime du « Shift Left », le principe consistant à intégrer la sécurité le plus tôt possible en amont dans les processus afin de pouvoir résoudre les problèmes de sécurité avec plus de facilité et d’efficacité. Cela nécessite un changement de culture de la part de tous les départements concernés (sécurité, commercial et informatique), exigeant que chaque groupe assimile la culture et les normes des autres groupes tout en enseignant les siennes à ceux-ci.

  Les équipes de sécurité doivent donc :

  - **Découvrir** les objectifs commerciaux et informatiques, pourquoi ils sont importants et comment les atteindre au terme de la transformation.
  - **Expliquer** les raisons pour lesquelles la sécurité est importante dans le contexte de ces objectifs commerciaux et des risques associés, ce que les autres équipes peuvent faire pour contribuer à la réalisation des objectifs de sécurité, et comment elles doivent le faire.

  Si la tâche n’est pas facile, elle est essentielle pour sécuriser durablement l’organisation et ses ressources. Ce partenariat aboutira probablement à des compromis équilibrés où seuls des objectifs minimaux en termes de sécurité, d’affaires et de fiabilité pourront être atteints au départ, mais dont les ambitions progresseront inexorablement au fil du temps.

- **La sécurité est un instrument de gestion du risque, pas un problème.** Il n’est pas possible d’« éradiquer » le crime. À la base, la sécurité n’est qu’une discipline de gestion des risques, qui se concentre sur des actions humaines malveillantes plutôt que sur des événements naturels. La sécurité n’est donc pas un problème qui peut être résolu, mais une combinaison de la probabilité et de l’impact des dommages que peut occasionner un événement négatif nommé attaque. Elle est très comparable à l’espionnage industriel ainsi qu’aux activités criminelles traditionnelles conduites par des agresseurs humains que l’appât du gain pousse à attaquer l’organisation.

- **Le succès repose sur une symbiose entre la productivité et la sécurité.** Dans l’environnement d’aujourd’hui où le défaut d’innovation conduit tout droit à l’obsolescence, une organisation doit se concentrer à la fois sur la sécurité et la productivité. Si une organisation n’est pas productive et innovante, sa compétitivité sur le marché s’émousse. Elle s’affaiblit financièrement et finit par échouer. Il en va de même si l’organisation n’est pas sécurisée et perd le contrôle de ressources au profit d’attaquants.

- **Personne n’est parfait.** Aucune organisation n’est parfaite sur le plan de l’adoption du cloud. Microsoft ne fait pas exception. Nos équipes informatiques et de sécurité sont confrontées aux mêmes défis que nos clients, tels ceux de déterminer comment bien structurer les programmes et de trouver un équilibre dans la prise en charge tout à la fois des logiciels hérités, des innovations les plus pointues, et même des lacunes technologiques des services cloud. À mesure que ces équipes apprennent à mieux exploiter et sécuriser le cloud, elles partagent activement ces enseignements au travers de documents tels que celui-ci sur le [site vitrine informatique](https://www.microsoft.com/itshowcase), tout en fournissant un retour d’expérience continu à nos équipes d’ingénierie ainsi qu’à des fournisseurs tiers pour améliorer leurs offres.

  Sur la base de notre expérience, nous recommandons que les équipes soient tenues au respect de normes d’apprentissage et d’amélioration continus plutôt qu’à celui d’une norme de perfection.

- **Opportunité liée à la transformation.** Il est important de considérer la transformation numérique comme une opportunité positive pour la sécurité. S’il est facile de percevoir les inconvénients et les risques potentiels de ce changement, il est également facile de passer à côté de cette occasion de réinventer le rôle de l’équipe de sécurité et de lui permettre de siéger à la table où se prennent les décisions. Un partenariat serein avec l’équipe commerciale peut entraîner une augmentation du financement de la sécurité, réduire le gaspillage des efforts répétitifs consacrés à celle-ci et rendre le travail de l’équipe plus agréable en l’intégrant davantage à la mission de l’organisation.

## <a name="adopting-the-shared-responsibility-model"></a>Adoption du modèle de responsabilité partagée

L’hébergement des services informatiques dans le cloud a pour effet de répartir les responsabilités opérationnelles et de sécurité en lien avec les charges de travail entre le fournisseur de services cloud et le client locataire, créant ainsi un partenariat de facto où les responsabilités sont partagées. Toutes les équipes de sécurité doivent étudier et comprendre ce modèle de responsabilité partagée pour adapter leurs processus, outils et compétences au monde nouveau. Cela permettra d’éviter de générer par inadvertance dans le dispositif de sécurité des lacunes ou des chevauchements qui entraîneraient une exposition accrue aux risques de sécurité ou un gaspillage de ressources.

Ce diagramme illustre la répartition des responsabilités en matière de sécurité entre les fournisseurs de services cloud et les organisations clientes dans un partenariat de facto :

![Partage des responsabilités en matière de sécurité](../_images/security/security-responsibilities.png)

Compte tenu de l’existence de différents modèles de services cloud, les responsabilités pour chaque charge de travail varient selon que celle-ci est hébergée sur un logiciel en tant que service (SaaS), une plateforme en tant que service (PaaS), une infrastructure en tant que service (IaaS) ou dans un centre de données local.

## <a name="building-security-initiatives"></a>Prise d’initiatives de sécurité

Ce diagramme illustre les trois principales initiatives de sécurité que la plupart des programmes de sécurité doivent prendre pour adapter leur stratégie de sécurité et les objectifs de leur programme de sécurité au cloud :

![Initiatives de sécurité prioritaires](../_images/security/primary-security-initiatives.png)

L’acquisition d’une posture de sécurité résiliente dans le cloud nécessite d’adopter plusieurs approches parallèles et complémentaires :

- **Faire confiance mais vérifier :** en ce qui concerne les responsabilités du fournisseur de services cloud, les organisations doivent adopter une approche consistant à « faire confiance mais vérifier ». Les organisations doivent évaluer les pratiques de sécurité de leurs fournisseurs de services cloud, ainsi que les contrôles de sécurité qu’elles mettent en place pour s’assurer que ces fournisseurs satisfont à leurs besoins de sécurité.

- **Moderniser la sécurité de l’infrastructure et des applications :** sur le plan des aspects techniques sous le contrôle de l’organisation, privilégiez la modernisation des outils de sécurité et constituez des ensembles de compétences afin de minimiser les lacunes de couverture pour la sécurisation des ressources dans le cloud. Cette modernisation nécessite deux efforts complémentaires :

  - **Sécurité de l’infrastructure :** les organisations doivent tirer parti du cloud pour moderniser leur approche de la protection et de la surveillance des composants communs qu’utilisent de nombreuses applications telles que les systèmes d’exploitation, les réseaux et l’infrastructure de conteneurs. Ces capacités cloud peuvent souvent inclure la gestion de composants d’infrastructure dans des environnements tant IaaS que locaux. L’optimisation de cette stratégie est importante parce que cette infrastructure est dépendante des applications et des données qui s’exécutent en son sein, qui permettent souvent d’activer des processus commerciaux critiques et de stocker des données commerciales essentielles.
  - **Sécurité des applications :** les organisations doivent également moderniser la façon dont elles sécurisent les applications et technologies uniques qu’elles développent ou qu’elles font développer. Cette discipline évolue rapidement avec l’adoption de processus de DevOps agiles, l’utilisation croissante de composants open source et l’introduction d’API et de services cloud pour remplacer des composants applicatifs ou interconnecter des applications.

    Il est essentiel de bien faire les choses, car ces applications permettent souvent d’activer des processus commerciaux critiques et de stocker des données commerciales essentielles.

  - **Périmètre moderne :** les organisations doivent adopter une approche globale pour la protection des données des charges de travail. Elles doivent établir un périmètre moderne de contrôles des identités cohérents et managés de manière centralisée pour protéger leurs données, leurs appareils et leurs comptes. Cela est fortement influencé par une stratégie de confiance zéro discutée en détail dans le module 3 de l’atelier RSSI, ainsi que dans d’autres ressources ici.

### <a name="security-and-trust"></a>Sécurité et confiance

Notez que l’utilisation du mot « confiance » en lien avec la sécurité peut être source de confusion. Cette documentation l’utilise de deux manières qui illustrent des applications utiles de ce concept :

- La [Confiance zéro](https://www.microsoft.com/security/business/zero-trust) est une expression courante désignant une approche stratégique de la sécurité qui part du principe qu’un réseau ou intranet d’entreprise est hostile a priori (et offre donc un niveau zéro de confiance), et conçoit la sécurité en conséquence.
- [Faire confiance mais vérifier](https://en.wikipedia.org/wiki/trust,_but_verify) est une expression qui reflète l’essence de deux organisations distinctes œuvrant ensemble à la poursuite d’un objectif commun en faisant abstraction d’autres intérêts spécifiques potentiellement divergents. Elle exprime de manière concise bon nombre des nuances des étapes précoces du partenariat entre une organisation et un fournisseur de services cloud commercial.

Un fournisseur de services cloud et ses pratiques et processus peuvent être tenus pour responsables du respect d’exigences contractuelles et réglementaires, et, à ce titre, gagner ou perdre la confiance de l’organisation. Un réseau est une connexion inerte qui ne peut pas subir de conséquences s’il est exploité par des attaquants (tout comme une route ou une voiture ne peuvent pas être tenues pour responsables des usages délictueux que d’aucuns peuvent en faire).

## <a name="how-cloud-is-changing-security-relationships-and-responsibilities"></a>Comment le cloud change les relations et les responsabilités en matière de sécurité

Tout comme ce fut le cas lors d’évolutions précédentes vers de nouvelles technologies telles que l’informatique de bureau et l’informatique de serveur d’entreprise, le passage au cloud computing bouleverse une série de relations, rôles, responsabilités et autres compétences établis de longue date. Les descriptions de tâches auxquelles nous nous étions habitués ces dernières décennies ne correspondent plus exactement aux capacités désormais disponibles dans le cloud. À l’heure où l’industrie s’efforce collectivement de normaliser un nouveau modèle, les organisations doivent s’efforcer d’apporter des clarifications aussi précises que possible pour aider à gérer l’incertitude naissant de l’ambiguïté pendant cette période de mutation.

Les équipes de sécurité sont elles aussi touchées par ces changements dans les activités et technologies qu’elles soutiennent, au même titre que par leurs propres efforts de modernisation interne visant à mieux se concentrer sur les acteurs des menaces. Tandis que les cyber-criminels évoluent activement dans leur recherche permanente des points faibles les plus faciles à exploiter parmi les personnes, les processus et les technologies des organisations, les équipes de sécurité doivent acquérir les capacités et compétences nécessaires pour contrer leurs attaques.

Cette section décrit les relations clés qui changent fréquemment au gré d’une migration vers le cloud, et inclut les leçons apprises concernant la réduction des risques et les opportunités d’amélioration :

- **Entre les parties prenantes sur les plans de la sécurité et de l’activité commerciale :** les responsables de la sécurité doivent collaborer davantage et plus étroitement avec les responsables commerciaux pour permettre aux organisations d’atténuer les risques. Ils doivent contribuer aux prises de décisions commerciales en tant qu’experts, et s’efforcer de devenir des conseillers de confiance des responsables commerciaux. Cette relation permettra de s’assurer que les responsables commerciaux tiennent compte des risques de sécurité quand ils prennent des décisions commerciales, informent les responsables de la sécurité des priorités commerciales, et veillent à ce que les investissements en matière de sécurité soient correctement hiérarchisés par rapport aux autres investissements.

- **Entre les responsables de la sécurité et les membres de leurs équipes :** les responsables de la sécurité doivent partager les informations recueillies auprès des responsables commerciaux avec leurs équipes afin d’orienter leurs priorités en matière d’investissements.

  En donnant le ton de la coopération avec les responsables commerciaux et leurs équipes au lieu de veiller jalousement sur leur pré carré d’« autonomie », les responsables de la sécurité peuvent éviter une dynamique antagoniste qui entrave les objectifs tant de sécurité que de productivité.

  Les responsables de la sécurité doivent s’efforcer de clarifier pour leurs équipes la manière de gérer les décisions quotidiennes en trouvant des compromis entre productivité et sécurité, car cela peut être nouveau pour bon nombre de leur collaborateurs.

- **Entre les équipes en charge de la gestion des applications et de l’infrastructure (et les fournisseurs de services cloud) :** cette relation subit des changements importants en raison des multiples tendances dans les secteurs de l’informatique et de la sécurité, visant à augmenter la vitesse de l’innovation et la productivité des développeurs.

  Les anciennes normes et fonctions organisationnelles sont perturbées, mais de nouvelles normes et fonctions ne cessent d’émerger. Nous vous recommandons donc d’accepter l’ambiguïté, de suivre l’évolution des courants de pensée et d’expérimenter ce qui peut fonctionner pour votre organisation jusqu’à obtenir le résultat escompté. Nous ne recommandons nullement d’adopter une attitude « attentiste » dans ce domaine, car celle-ci pourrait avoir pour effet mettre votre organisation dans une situation de désavantage concurrentiel majeur.

  Ces tendances remettent en question les normes traditionnelles régissant les rôles et les relations entre les applications et l’infrastructure :

  - **Disciplines fusionnant le DevOps :** dans une situation idéale, cela crée effectivement une seule équipe hautement fonctionnelle qui combine les deux expertises pour innover, publier des mises à jour et résoudre des problèmes (de sécurité et autres) rapidement. Même si l’aboutissement à cette situation idéale prend du temps et si les responsabilités restent entre-temps très ambiguës, des organisations récoltent déjà les fruits de mises en production rapides basées sur cette approche coopérative. Microsoft recommande d’intégrer la sécurité dans ce cycle pour faciliter l’apprentissage de ces cultures, partager les apprentissages en matière de sécurité et œuvrer à l’objectif commun de publier rapidement des applications sécurisées et fiables.

  ![Disciplines de fusion du DevOps](../_images/security/devops-disciplines.png)

  - **Évolution vers la conteneurisation en tant que composant d’infrastructure commun :** les applications sont de plus en plus hébergées et orchestrées par des technologies telles que Docker, Kubernetes et autres solutions de même nature. Ces technologies simplifient le développement et la mise en production en faisant abstraction de nombreux aspects de l’installation et de la configuration du système d’exploitation sous-jacent.

  ![Infrastructure de conteneurisation](../_images/security/containerization.png)

  Alors que les conteneurs commencent à être utilisés en tant que technologie de développement d’applications gérée par des équipes de développement, ils deviennent un composant d’infrastructure commun qui se évolue de plus en plus vers le recours à des équipes d’infrastructure. Cette transition est toujours en cours au sein de nombreuses organisations, mais il s’agit d’une tendance naturelle et positive. Bon nombre des défis actuels seront résolus de façon optimale en faisant appel aux compétences traditionnelles en matière d’infrastructure, telles que la mise en réseau, le stockage et la gestion des capacités.

  Les équipes d’infrastructure et les membres de l’équipe de sécurité qui les épaulent devraient recevoir une formation, des instructions en matière de processus et des outils pour gérer, surveiller et sécuriser cette technologie.

  - **Services d’applications sans serveur et cloud :** à l’heure actuelle, l’une des tendances dominantes du secteur est la réduction du temps et du travail de développement requis pour créer ou mettre à jour des applications.

    ![Services d’applications sans serveur et cloud](../_images/security/serverless-model.png)

    Les développeurs utilisent également de plus en plus les services cloud pour effectuer les opérations suivantes :

    - Exécuter du code au lieu d’héberger des applications sur des machines virtuelles et des serveurs.
    - Fournir des fonctions applicatives au lieu de développer leurs propres composants. Cela a conduit à un modèle _sans serveur_ qui utilise les services cloud existants pour des fonctions courantes. Le nombre et la variété des services cloud (ainsi que leur rythme d’innovation) ont également dépassé la capacité des équipes de sécurité à évaluer et à approuver l’utilisation de ces services, les laissant choisir entre autoriser les développeurs à utiliser n’importe quel service, tenter d’empêcher les équipes de développement d’utiliser des services non approuvés, ou essayer de trouver une meilleure solution.
    - **Applications sans code et Power Apps :** une autre tendance émergente est l’utilisation de technologies sans code telles que les Power Apps de Microsoft. Cette technologie permet à des personnes sans compétences de codage de créer des applications qui produisent des résultats métier. En raison de cette faible friction et de sa valeur potentielle élevée, cette tendance technologique peut gagner rapidement en popularité et les professionnels de la sécurité seraient avisés d’en comprendre rapidement les implications. Les efforts de sécurité doivent se concentrer sur des domaines dans lesquels un humain pourrait commettre des erreurs dans l’application, à savoir la conception des autorisations d’applications et de ressources via une modélisation des menaces, des composants applicatifs, des interactions/relations et des autorisations de rôle.

- **Entre les développeurs et les auteurs de composants open source :** les développeurs gagnent également en efficacité en utilisant des composants et des bibliothèques open source au lieu de développer leurs propres composants. Cela apporte de la valeur au travers de l’efficacité, mais introduit aussi des risques de sécurité en créant une dépendance externe et une exigence de maintenance et de correction appropriées de ces composants. Les développeurs assument effectivement le risque de bogues de sécurité et autres quand ils utilisent ces composants, et doivent s’assurer qu’il existe un plan pour les atténuer respectant les mêmes normes que le code qu’ils développeraient.

- **Entre les applications et les données :** la ligne de démarcation entre la sécurité des données et celle des applications devient floue par endroits, et les nouvelles réglementations créent un besoin de coopération plus étroite entre les équipes chargées de la protection des données et de la confidentialité et celles chargées de la sécurité :

  - **Algorithmes d’apprentissage automatique (Machine Learning) :** les algorithmes d’apprentissage automatique sont similaires aux applications en ce qu’ils sont conçus pour traiter des données afin de produire un résultat. Les principales différences sont les suivantes :

    - **Apprentissage automatique de valeur supérieure :** l’apprentissage automatique confère souvent un avantage concurrentiel important et est généralement considéré comme une propriété intellectuelle sensible et un secret commercial.

    - **Empreinte de sensibilité :** l’apprentissage automatique supervisé est réglé à l’aide de jeux de données, qui impriment les caractéristiques du jeu de données sur l’algorithme. De ce fait, l’algorithme réglé peut être considéré comme sensible en raison du jeu de données utilisé pour l’entraîner. Par exemple, la formation d’un algorithme d’apprentissage automatique pour trouver des bases militaires secrètes sur une carte à l’aide d’un jeu de données de bases militaires secrètes en ferait un atout sensible.

    > [!NOTE]
    > Tous les exemples n’étant pas évidents, il est essentiel de constituer une équipe avec les bonnes parties prenantes, qu’il s’agisse des équipes scientifiques, commerciales, de sécurité, de protection de la vie privée ou autres. Ces équipes doivent avoir pour mission d’atteindre des objectifs communs d’innovation et de responsabilité. Elles doivent apporter des réponses à des questions courantes telles que comment et où stocker des copies de données dans des configurations non sécurisées, comment classifier les algorithmes, ainsi qu’à toutes les questions que posent vos organisations.
    >
    > Microsoft a publié ses [principes d’intelligence artificielle responsable](https://www.microsoft.com/ai/responsible-ai) pour guider ses propres équipes et clients.

    - **Propriété des données et confidentialité :** des réglementations telles que le RGPD ont accru la visibilité des problèmes de données et des applications. Les équipes d’application ont désormais la possibilité de contrôler, protéger et suivre les données sensibles à un niveau comparable à celui que les banques et autres institutions financières exercent sur les données financières. Les propriétaires de données et les équipes d’applications doivent acquérir une compréhension approfondie de ce que les applications de données stockent et des contrôles requis.

- **Entre les organisations et les fournisseurs de services cloud :** lorsque des organisations hébergent des charges de travail dans le cloud, elles nouent une relation commerciale avec chacun de ces fournisseurs de services cloud. L’utilisation de services cloud apporte souvent une valeur commerciale, par exemple :

  - **Accélération des initiatives de transformation numérique** en réduisant les délais de commercialisation des nouvelles fonctionnalités.

  - **Augmentation de la valeur des activités informatiques et de sécurité** en laissant aux équipes les coudées franches pour se concentrer sur des activités à plus forte valeur ajoutée (à connotation commerciale) plutôt que sur des tâches courantes de niveau inférieur qui sont assurées plus efficacement par des services cloud.

  - **Fiabilité et réactivité accrues :** la plupart des clouds modernes ont également une durée de bon fonctionnement extrêmement longue par rapport aux centres de données traditionnels locaux, et ont montré qu’ils peuvent se mettre à l’échelle rapidement (comme lors de la pandémie de COVID-19) et offrir une résilience par rapport à des événements naturels tels que la foudre (qui auraient maintenu de nombreux équivalents locaux à un niveau bas pendant beaucoup plus longtemps).

    Bien qu’extrêmement bénéfique, ce glissement vers cloud n’est pas sans risque. À mesure que les organisations adoptent des services cloud, elles doivent considérer certains risques potentiels, à savoir :

  - **continuité d’activité et reprise d’activité :** le fournisseur de services cloud est-il en bonne santé financière avec un modèle commercial susceptible de survivre et de prospérer pendant l’utilisation du service par votre organisation ? Le fournisseur de services cloud a-t-il pris des dispositions pour assurer la continuité de la clientèle en cas de défaillance financière ou autre, par exemple en fournissant son code source aux clients ou en l’offrant en libre accès ?

    Pour plus d’informations et de documentation sur la santé financière de Microsoft, consultez les [relations de Microsoft avec les investisseurs](https://www.microsoft.com/investor).

  - **Sécurité :** le fournisseur de services cloud respecte-t-il les meilleures pratiques du secteur en matière de sécurité ? Cela a-t-il été validé par des organes de régulation indépendants ?

    - [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/risk-score) vous permet de découvrir l’usage qui est fait de plus de 16 000 applications cloud, classées et évaluées sur la base de plus de 70 facteurs de risque, pour vous fournir une visibilité constante de l’utilisation du cloud, de l’informatique fantôme ainsi que du risque que celle-ci fait peser sur votre organisation.
    - Le [portail d’approbation de services Microsoft](https://servicetrust.microsoft.com) met à la disposition des clients des certifications de conformité réglementaire, des rapports d’audit, des tests de pénétration, et bien plus encore. Ces documents contiennent de nombreux détails sur les pratiques de sécurité internes (dont le rapport SOC 2 Type 2 et le plan de sécurité du système FedRAMP modéré).

  - **Concurrent commercial :** le fournisseur de services cloud est-il un concurrent commercial important dans votre secteur ? Disposez-vous de suffisamment de protections dans le contrat de services cloud, ou d’autres moyens pour protéger votre entreprise contre des actions potentiellement hostiles ?

    Pour obtenir des commentaires sur la façon dont Microsoft évite de concurrencer ses clients cloud, consultez [cet article](https://www.cnbc.com/2019/03/16/why-volkswagen-chose-microsoft-azure-over-aws.html).

  - **Multicloud :** de nombreuses organisations ont une stratégie multicloud de fait ou intentionnelle . Il peut s’agir d’un choix délibéré visant à réduire la dépendance à l’égard d’un seul fournisseur ou à accéder à des capacités uniques, mais cela peut également résulter du fait que les développeurs ont choisi des services cloud préférés ou familiers, ou que votre organisation a acquis une autre entreprise. Quelle que soit la raison, cette stratégie peut exposer à des risques et des coûts potentiels qu’il convient de gérer, à savoir :

    - **Temps d’arrêt de plusieurs dépendances :** les systèmes architecturés pour s’appuyer sur plusieurs clouds sont exposés à davantage de risques d’indisponibilité, car des interruptions de services cloud de fournisseurs (ou leur utilisation par votre équipe) pourraient entraîner une panne ou une perturbation de votre activité. Cette complexité accrue du système augmente également la probabilité de survenance d’événements perturbateurs, car les membres de l’équipe sont moins susceptibles de comprendre pleinement un système plus complexe.
    - **Pouvoir de négociation :** les grandes entreprises doivent également se demander si une stratégie de cloud unique (engagement/partenariat mutuel) ou multicloud (possibilité de changer de fournisseur) leur permettra d’exercer une plus grande influence sur leur(s) fournisseur(s) de services cloud afin que leurs demandes de fonctionnalités soient traitées en priorité.
    - **Surcharge de maintenance :** les ressources informatiques et de sécurité sont déjà écrasées par leurs charges de travail existantes et la nécessité de suivre les changements d’une plateforme cloud unique. Chaque plateforme supplémentaire accentue cette surcharge et éloigne les membres de l’équipe d’activités à plus forte valeur ajoutée, telles que la rationalisation des processus techniques pour accélérer l’innovation commerciale, la concertation avec les groupes commerciaux concernant une utilisation plus efficace des technologies, etc.
    - **Recrutement et formation :** souvent, les organisations ne tiennent pas compte des effectifs nécessaires pour prendre en charge plusieurs plateformes et de la formation requise pour maintenir le niveau des connaissances nécessaires et suivre l’actualité des nouvelles fonctionnalités publiées à un rythme rapide.
