<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->

## <a name="dependent-decisions"></a>Décisions dépendantes

Les décisions suivantes proviennent d’équipes hors de l’équipe de gouvernance cloud. L’implémentation de chacune d’entre elles est actée par ces mêmes équipes. Toutefois, l’équipe de gouvernance cloud est chargée de mettre en œuvre une solution permettant de vérifier que ces implémentations sont appliquées de manière cohérente.

### <a name="identity-baseline"></a>Base de référence des identités

La base de référence des identités constitue le point de départ fondamental de tout type de gouvernance. Avant toute tentative d’application de la gouvernance, vous devez établir les identités. Ensuite, la stratégie des identités définie est appliquée par le biais des solutions de gouvernance.
Dans ce guide de gouvernance, l’équipe de gestion des identités implémente le modèle de **[synchronisation d’annuaires](../../../../decision-guides/identity/index.md#directory-synchronization)**  :

- Le contrôle d’accès en fonction du rôle sera fourni par Azure Active Directory (Azure AD) à l’aide de la synchronisation d’annuaires ou de « l’authentification identique » qui a été implémentée lorsque l’entreprise a migré vers Office 365. Pour obtenir des conseils sur l’implémentation, consultez la page [Architecture de référence pour l’intégration Azure AD](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
- Le locataire Azure AD contrôlera également l’authentification et l’accès aux ressources déployées sur Azure.

Dans le produit minimum viable de la gouvernance, l’équipe de gouvernance fera respecter l’application du locataire répliqué via les outils de gouvernance des abonnements qui sont décrits ultérieurement dans cet article. Dans les itérations à venir, l’équipe de gouvernance pourra également promouvoir l’enrichissement des outils dans Azure AD afin de développer ses domaines de compétence.

### <a name="security-baseline-networking"></a>Base de référence de la sécurité : Mise en réseau

Software Defined Network est un aspect capital de la base de référence de la sécurité. L’établissement du produit minimum viable de la gouvernance dépend des premières décisions prises par l’équipe de gestion de la sécurité en matière de configuration des réseaux en toute sécurité.

Étant donné le manque de critères, le service de sécurité informatique ne prend pas de risques et demande un modèle **[Cloud DMZ](../../../../decision-guides/software-defined-network/cloud-dmz.md)** . Cela signifie que la gouvernance des déploiements Azure eux-mêmes sera minime.

- Les abonnements Azure peuvent être connectés à un centre de données existant via VPN, mais vous devez suivre les stratégies de gouvernance informatique locales concernant la connexion d’une zone démilitarisée à des ressources protégées. Pour obtenir des instructions d’implémentation concernant la connectivité VPN, consultez la page [Architecture VPN de référence](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/vpn).
- À l’heure actuelle, les décisions concernant le sous-réseau, le pare-feu et le routage sont différées à chaque responsable d’application ou de charge de travail.
- Une analyse supplémentaire est nécessaire avant de publier les données protégées ou les charges de travail critiques.

Dans ce modèle, les réseaux cloud peuvent être connectés uniquement à des ressources locales via un VPN existant qui est compatible avec Azure. Le trafic via cette connexion sera traité comme tout le trafic provenant d’une zone démilitarisée. Il peut être nécessaire d’étudier d’autres considérations relatives à l’appareil de périmètre local pour gérer en toute sécurité le trafic provenant d’Azure.

L’équipe de gouvernance cloud invite régulièrement les membres des équipes de sécurité informatique et de mise en réseau à participer à des réunions afin d’anticiper les demandes et les risques associés à la mise en réseau.

### <a name="security-baseline-encryption"></a>Base de référence de la sécurité : Chiffrement

Le chiffrement constitue une autre décision fondamentale dans la discipline Base de référence de la sécurité. À l’heure actuelle, l’entreprise ne stocke pas encore de données protégées dans le cloud. C’est pourquoi l’équipe de sécurité a choisi un modèle de chiffrement moins agressif.
À ce stade, un **[modèle natif cloud de chiffrement](../../../../decision-guides/encryption/index.md#key-management)** est suggéré, sans qu’il ne soit requis par les équipes de développement.

- Aucune exigence de gouvernance n’a été définie quant à l’utilisation du chiffrement, car la stratégie d’entreprise en vigueur n’autorise pas les données critiques ou protégées dans le cloud.
- Une analyse supplémentaire est nécessaire avant de publier les données protégées ou les charges de travail critiques.

## <a name="policy-enforcement"></a>Application de stratégies

La première décision à prendre en matière d’accélération du déploiement porte sur le modèle d’application. Dans ce scénario, l’équipe de gouvernance a décidé d’implémenter le modèle **[Application automatisée](../../../../decision-guides/policy-enforcement/index.md#automated-enforcement)** .

- Azure Security Center sera mis à disposition des équipes de sécurité et d’identité afin de surveiller les risques de sécurité. Les deux équipes sont également susceptibles d’utiliser Security Center pour identifier les nouveaux risques et améliorer la stratégie d’entreprise.
- Le contrôle d’accès en fonction du rôle est requis dans tous les abonnements afin de régir la mise en œuvre de l’authentification.
- Azure Policy sera publié pour chaque groupe d’administration et appliqué à tous les abonnements. Toutefois, le niveau des stratégies appliquées sera très limité dans ce produit minimum viable initial de la gouvernance.
- Bien que les groupes d’administration Azure soient utilisés, c’est une hiérarchie relativement simple qui est attendue.
- Azure Blueprints servira à déployer et mettre à jour les abonnements en appliquant les exigences de contrôle d’accès en fonction du rôle, les modèles Resource Manager et Azure Policy aux groupes d’administration.

## <a name="applying-the-dependent-patterns"></a>Application des modèles dépendants

Les décisions suivantes représentent les modèles qui doivent être appliqués grâce à la stratégie de mise en œuvre ci-dessus :

**Base de référence des identités.** Azure Blueprints définira les exigences de contrôle d’accès en fonction du rôle au niveau de l’abonnement pour garantir la configuration d’une identité cohérente pour tous les abonnements.

**Base de référence de la sécurité : Mise en réseau.** L’équipe de gouvernance cloud conserve un modèle Resource Manager pour établir une passerelle VPN entre Azure et le périphérique VPN local. Lorsqu’une équipe d’application a besoin d’une connexion VPN, l’équipe de gouvernance cloud applique le modèle Resource Manager de la passerelle via Azure Blueprints.

**Base de référence de la sécurité : Chiffrement.** À ce stade, la stratégie n’a pas besoin d’être appliquée à ce domaine. Nous nous pencherons à nouveau sur ce sujet dans les prochaines itérations.
