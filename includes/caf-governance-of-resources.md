<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->
> [!NOTE]
>Si vos besoins métier viennent à changer, les groupes d’administration Azure vous permettent de réorganiser facilement la hiérarchie de votre administration et les attributions de groupe d’abonnements. Toutefois, gardez en tête que les attributions de rôle et de stratégie appliquées à un groupe d’administration sont héritées par tous les abonnements qui se trouvent sous ce groupe dans la hiérarchie. Si vous envisagez de réattribuer des abonnements entre des groupes d’administration, veillez à connaître tous les changements d’attribution de rôle et de stratégie que cela peut entraîner. Pour plus d’informations, consultez la [documentation sur les groupes d’administration Azure](/azure/governance/management-groups).

### <a name="governance-of-resources"></a>Gouvernance des ressources

Un ensemble de stratégies globales et de rôles RBAC fournit un niveau de référence de la mise en œuvre de la gouvernance. Pour répondre aux exigences de stratégie de l’équipe de gouvernance cloud, l’implémentation du MVP de gouvernance nécessite d’effectuer les tâches suivantes :

1. Identifier les définitions de stratégie Azure Policy nécessaires pour appliquer les besoins métier. Cela peut inclure l’utilisation de définitions intégrées et la création de nouvelles définitions personnalisées.
2. Créer une définition de blueprint avec ces attributions de rôle et de stratégie intégrées et personnalisées requises par le MVP de gouvernance.
3. Appliquer globalement des stratégies et une configuration en attribuant la définition de blueprint à tous les abonnements.

#### <a name="identify-policy-definitions"></a>Identifier les définitions de stratégie

Azure offre plusieurs stratégies et définitions de rôle intégrées que vous pouvez attribuer à un groupe d’administration, un abonnement ou un groupe de ressources de votre choix. De nombreuses exigences de gouvernance courantes peuvent être gérées à l’aide de définitions intégrées. Toutefois,vous devrez probablement créer aussi des définitions de stratégie personnalisée pour gérer vos besoins spécifiques.

Les définitions de stratégie personnalisées sont enregistrées dans un groupe d’administration ou dans un abonnement et sont héritées via la hiérarchie des groupes d’administration. Si l’emplacement d’enregistrement d’une définition de stratégie est un groupe d’administration, cette définition de stratégie peut être attribuée à n’importe quel groupe d’administration ou abonnement enfant de ce groupe.

Étant donné que les stratégies nécessaires à la prise en charge du MVP de gouvernance sont destinées à s’appliquer à tous les abonnements actuels, les besoins métier suivants seront implémentés à l’aide d’une combinaison de définitions intégrées et de définitions personnalisées créées dans le groupe d’administration racine :

1. Limitez la liste des attributions de rôle disponibles à un ensemble de rôles Azure intégrés autorisé par votre équipe de gouvernance cloud. Cela nécessite une [définition de stratégie personnalisée](https://github.com/Azure/azure-policy/tree/master/samples/Authorization/allowed-role-definitions). 
2. Exigez l’utilisation des étiquettes suivantes sur toutes les ressources : *Département/Unité de facturation*, *Géographie*, *Classification des données*, *Caractère critique*, *SLA*, *Environnement*, *Archétype d’application*, *Application* et *Propriétaire de l’application*. Cela peut être géré en utilisant la définition intégrée « Exiger une étiquette spécifiée ».
3. Exigez que l’étiquette *Application* des ressources corresponde au nom du groupe de ressources approprié. Cela peut être gérée à l’aide de la définition intégrée « Exiger une étiquette et sa valeur ».

Pour plus d’informations sur la définition de stratégies personnalisées, consultez la [documentation Azure Policy](/azure/governance/policy/tutorials/create-custom-policy-definition). Pour des conseils et des exemples de stratégies personnalisées, consultez le [site d’exemples Azure Policy](/azure/governance/policy/samples) et le [dépôt GitHub](https://github.com/Azure/azure-policy) associé.

#### <a name="assign-azure-policy-and-rbac-roles-using-azure-blueprints"></a>Attribuer des stratégies Azure Policy et des rôles RBAC avec Azure Blueprints

Les stratégies Azure peuvent être affectées au niveau du groupe de ressources, de l’abonnement et du groupe d’administration, et peuvent être incluses dans des définitions [Azure Blueprints](/azure/governance/blueprints/overview). Bien que les conditions de stratégie définies dans ce MVP de gouvernance s’appliquent à tous les abonnements actuels, il est très probable que les futurs déploiements nécessiteront des exceptions ou d’autres stratégies. Par conséquent, l’attribution d’une stratégie en utilisant des groupes d’administration, avec tous les abonnements enfants héritant de ces attributions, risque de ne pas être suffisamment flexible pour prendre en charge ces scénarios.

Azure Blueprints autorise l’attribution cohérente de stratégies et de rôles, l’application de modèles Resource Manager et le déploiement de groupes de ressources parmi plusieurs abonnements. Comme avec les définitions de stratégie, les définitions de blueprint sont enregistrées dans des abonnements ou des groupes d’administration et sont disponibles par héritage pour tous les enfants de la hiérarchie des groupes d’administration.

L’équipe de la gouvernance cloud a décidé que la mise en œuvre des attributions de rôle RBAC et de stratégie Azure Policy requises sur les abonnements sera implémentée via Azure Blueprints et les artefacts associés :

1. Dans le groupe d’administration racine, créez une définition de blueprint nommée `governance-baseline`.
2. Ajoutez les artefacts de blueprint suivants à la définition de blueprint :
    1. Attributions de stratégie pour les définitions de stratégie Azure Policy personnalisées définies à la racine du groupe d’administration.
    2. Définitions de groupe de ressources pour tous les groupes nécessaires dans les abonnements créés ou gouvernés par le MVP de gouvernance.
    3. Attributions de rôle standard nécessaires dans les abonnements créés ou gouvernés par le MVP de gouvernance.
3. Publiez la définition de blueprint.
4. Attribuez la définition de blueprint `governance-baseline` à tous les abonnements.

Consultez la [documentation Azure Blueprints](/azure/governance/blueprints/overview) pour plus d’informations sur la création et l’utilisation de définitions de blueprint.

### <a name="secure-hybrid-vnet"></a>Sécuriser le réseau virtuel hybride

Certains abonnements spécifiques demandent souvent un niveau d’accès aux ressources locales. C’est courant dans les scénarios de migration ou de développement où résident des ressources dépendantes dans le centre de données local.

Tant que la confiance dans l’environnement cloud n’est pas totalement établie, il est important de contrôler et de surveiller étroitement toutes les communications autorisées entre l’environnement local et les charges de travail cloud, et de s’assurer que le réseau local est sécurisé et protégé contre un accès non autorisé potentiel provenant de ressources cloud. Pour prendre en charge ces scénarios, le MVP de gouvernance ajoute les bonnes pratiques suivantes :

1. Établissez un réseau virtuel cloud hybride sécurisé.
    1. L’[architecture de référence VPN](/azure/architecture/reference-architectures/hybrid-networking/vpn) établit un schéma et un modèle de déploiement pour la création d’une passerelle VPN dans Azure.
    2. Confirmez que les mécanismes de gestion de la sécurité et du trafic locaux traitent les réseaux cloud connectés comme étant non approuvés. Les ressources et les services hébergés dans le cloud doivent avoir uniquement accès aux services locaux autorisés.
    3. Vérifiez que l’appareil de périphérie local dans le centre de données local est compatible avec les [exigences de passerelle VPN Azure](/azure/vpn-gateway/vpn-gateway-about-vpn-devices) et configuré pour accéder à l’Internet public.
1. Dans le groupe d’administration racine, créez une seconde définition de blueprint nommée `secure-hybrid-vnet`.
    1. Ajoutez le modèle Resource Manager pour la passerelle VPN comme artefact de la définition de blueprint.
    2. Ajoutez le modèle Resource Manager pour le réseau virtuel comme artefact de la définition de blueprint.
    3. Publiez la définition de blueprint.
1. Attribuez la définition de blueprint `secure-hybrid-vnet` aux abonnements nécessitant une connectivité locale. Cette définition doit être assignée en plus de la définition de blueprint `governance-baseline`.

Une des principales préoccupations soulevées par les équipes de sécurité informatique et de gouvernance traditionnelle est le risque qu’une adoption du cloud trop précoce mette en péril les ressources existantes. L’approche ci-dessus permet aux équipes d’adoption du cloud de créer et de migrer des solutions hybrides, ce qui réduit les risques pour les ressources locales. Au fur et à mesure que la confiance l’environnement cloud augmente, les dernières évolutions peuvent éliminer cette solution temporaire.

> [!NOTE]
> La méthode ci-dessus est un point de départ permettant de créer rapidement un MVP de gouvernance de référence. Il ne s’agit que du début du parcours de gouvernance. Des évolutions futures seront nécessaires à mesure que l’entreprise poursuit son adoption du cloud et prend plus de risques dans les domaines suivants :
>
> - Charges de travail critiques
> - Données protégées
> - la gestion des coûts ;
> - Scénarios multiclouds
>
> Par ailleurs, les détails de ce MVP se basent sur l’exemple de parcours d’une entreprise fictive, qui est décrit dans les articles qui suivent. Nous vous recommandons vivement de consulter les autres articles de cette série avant d’implémenter cette meilleure pratique.
