<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->

## <a name="policy-statements"></a>Policy statements

Les instructions stratégiques suivantes établissent les exigences visant à éliminer les risques définis. Ces stratégies définissent les exigences fonctionnelles pour le produit minimum viable de la gouvernance. Chacune d’entre elle sera représentée dans l’implémentation du produit minimum viable de la gouvernance.

Gestion des coûts :

- À des fins de suivi, toutes les ressources doivent être associées à un propriétaire d’application dans l’une des fonctions métier principales.
- En cas de préoccupations relatives aux coûts, des exigences de gouvernance supplémentaires sont établies avec le service financier.

Base de référence de la sécurité :

- Toutes les ressources déployées dans le cloud doivent entrer dans la classification approuvée des données.
- Les ressources identifiées avec un niveau de données protégé ne peuvent pas être déployées sur le cloud tant que les exigences de sécurité et de gouvernance suffisantes ne sont pas approuvées et implémentées.
- Tant que les exigences de sécurité réseau minimales ne sont pas validées et régies, les environnements cloud sont considérés comme des zones démilitarisées et doivent répondre aux mêmes exigences de connexion que d’autres centres de données ou réseaux internes.

Cohérence des ressources :

- Étant donné qu’aucune charge de travail critique n’est déployée à ce stade, il n’existe aucune exigence à respecter par rapport à un contrat de niveau de service, aux performances ou à la continuité d’activité et reprise d’activité.
- Lorsque des charges de travail critiques sont déployées, des exigences de gouvernance supplémentaires sont établies avec le service des opérations informatiques.

Base de référence des identités :

- Toutes les ressources déployées dans le cloud doivent être contrôlées à l’aide d’identités et de rôles approuvés par les stratégies de gouvernance en vigueur.
- Tous les groupes de l’infrastructure Active Directory locale qui disposent de privilèges élevés doivent être mappés vers un rôle RBAC approuvé.

Accélération du déploiement :

- Toutes les ressources doivent être regroupées et libellées en fonction de stratégies définies.
- Toutes les ressources doivent utiliser un modèle de déploiement approuvé.
- Une fois que les fondements de la gouvernance sont établis pour un fournisseur de cloud, tous les outils de déploiement doivent être compatibles avec les outils définis par l’équipe de gouvernance.

## <a name="processes"></a>Processus

Aucun budget n’a été alloué à la surveillance et à l’application continues de ces stratégies de gouvernance. C’est pourquoi l’équipe de gouvernance cloud dispose de quelques solutions ponctuelles afin de veiller au bon respect des instructions stratégiques.

- **Formation :** L’équipe de gouvernance coud consacre du temps à former les équipes d’adoption du cloud aux guides de gouvernance qui sous-tendent ces stratégies.
- **Révisions du déploiement :** Avant de déployer une ressource, l’équipe de gouvernance cloud examine le guide de gouvernance aux côtés de l’équipe d’adoption du cloud.
