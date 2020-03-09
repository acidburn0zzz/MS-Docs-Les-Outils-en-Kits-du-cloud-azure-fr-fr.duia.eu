---
title: Conception de gouvernance multi-équipe dans Azure
description: Trouvez des conseils pour configurer des contrôles de gouvernance Azure pour plusieurs équipes, plusieurs charges de travail et plusieurs environnements.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 62c47f8d4b3c386129c6a6a9eeb966393573ea16
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78223890"
---
<!-- cSpell:ignore netops -->

# <a name="governance-design-for-multiple-teams"></a>Conception de gouvernance pour plusieurs équipes

Ce guide a pour but de vous aider à comprendre comment concevoir un modèle de gouvernance des ressources dans Azure, destiné à prendre en plusieurs équipes, charges de travail et environnements. Vous allez commencer par passer en revue plusieurs exigences de gouvernance hypothétiques, puis étudier plusieurs exemples d’implémentation qui répondent à ces exigences.

Les conditions requises sont :

- L’entreprise prévoit d’effectuer la transition de nouveaux rôles cloud et responsabilités vers un ensemble d’utilisateurs et demande par conséquent de gérer les identités de plusieurs équipes avec différents besoins d’accès aux ressources dans Azure. Ce système de gestion des identités est nécessaire pour stocker l’identité des utilisateurs suivants :
  - La personne de votre organisation qui détient la propriété des **abonnements**.
  - La personne de votre organisation responsable des **ressources d’infrastructure partagée** utilisées pour connecter votre réseau local à un réseau virtuel Azure.
  - Deux personnes de votre organisation responsables de la gestion d’une **charge de travail**.
- Prise en charge de plusieurs **environnements**. Un environnement est un regroupement logique de ressources, telles que des machines virtuelles, des réseaux virtuels et des services de routage de trafic réseau. Ces groupes de ressources ont des exigences similaires en matière de sécurité et de gestion, et sont généralement utilisés dans un but bien spécifique, à des fins de test ou de production par exemple. Dans cet exemple, l’exigence porte sur quatre environnements :
  - Un **environnement d’infrastructure partagée** qui inclut les ressources partagées par des charges de travail d’autres environnements. Par exemple, un réseau virtuel ayant un sous-réseau de passerelle qui assure la connectivité au niveau local.
  - Un **environnement de production** associé aux stratégies de sécurité les plus restrictives. Peut inclure des charges de travail internes ou externes.
  - Un **environnement de préproduction** pour le travail de développement et de test. Cet environnement comporte des stratégies de sécurité, de conformité et de coût qui diffèrent de celles de l’environnement de production. Dans Azure, il prend la forme d’un abonnement Enterprise Dev/Test.
  - Un **environnement de bac à sable** pour la preuve de concept et à des fins de formation. Cet environnement est généralement attribué par employé (parmi ceux participant à des activités de développement). Il inclut des contrôles procéduraux et de sécurité opérationnels stricts pour empêcher que des données d’entreprise y soient accessibles. Dans Azure, il prend la forme d’abonnements Visual Studio. Ces abonnements ne doivent _pas_ être liés au service Azure Active Directory de l’entreprise.
- Un **modèle d’autorisations de privilège minimal** dans lequel les utilisateurs ne disposent d’aucune autorisation par défaut. Le modèle doit prendre en charge les éléments suivants :
  - Un seul utilisateur approuvé (traité comme un compte de service) à l'échelle de l'abonnement, avec autorisation d'attribuer des droits d'accès aux ressources.
  - Chaque propriétaire de charge de travail se voit refuser l’accès aux ressources par défaut. Les droits d’accès aux ressources sont accordés explicitement par le seul utilisateur approuvé dans l’étendue du groupe de ressources.
  - Accès à la gestion des ressources d’infrastructure partagée limité aux propriétaires de l’infrastructure partagée.
  - Accès à la gestion de chaque charge de travail limité au propriétaire de la charge de travail (en production) et niveaux de contrôle croissants suivant l’évolution du développement (développement, test, démonstration, puis production).
  - L’entreprise ne souhaite pas avoir à gérer les rôles de façon indépendante dans chacun des trois environnements principaux et a donc besoin d’utiliser seulement des [rôles intégrés](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles) disponibles dans le contrôle d’accès en fonction du rôle (RBAC) d’Azure. Si l’entreprise a réellement besoin de rôles RBAC personnalisés, des processus supplémentaires seront nécessaires pour synchroniser les rôles personnalisés pour les trois environnements.
- Suivi des coûts par nom de propriétaire de la charge de travail et/ou par environnement.

## <a name="identity-management"></a>Gestion des identités

Avant de concevoir la gestion des identités pour votre modèle de gouvernance, il est important de comprendre les quatre aspects majeurs que cela englobe :

- **Administration :** processus et outils de création, de modification et de suppression d’identité d’utilisateur.
- **Authentication (Authentification) :** vérification de l’identité de l’utilisateur par validation des informations d’identification, comme un nom d’utilisateur et un mot de passe.
- **Authorization :** identification des ressources auxquelles un utilisateur authentifié est autorisé à accéder ou des opérations qu’il est autorisé à effectuer.
- **Audit :** examen régulier des journaux et autres informations dans le but de détecter les problèmes de sécurité liés à l’identité de l’utilisateur. Ceci inclut la vérification des modèles d’utilisation suspects, la révision régulière des autorisations utilisateur pour en vérifier l’exactitude, ainsi que d’autres fonctions.

Azure Active Directory (Azure AD) est le seul service d’identité approuvé par Azure. Vous allez ajouter des utilisateurs à Azure AD et l’utiliser pour toutes les fonctions répertoriées ci-dessus. Mais avant de voir comment vous allez configurer Azure AD, il est important de comprendre les comptes privilégiés qui sont utilisés pour gérer l’accès à ces services.

Lorsque votre organisation s’est inscrite pour bénéficier d’un compte Azure, un **propriétaire du compte** Azure minimum a été désigné. En outre, un **locataire** Azure AD a été créé, sauf si un locataire existant était déjà associé à l’utilisation d’autres services Microsoft, tels qu’Office 365, par votre organisation. Un **administrateur global** disposant de toutes les autorisations sur le locataire Azure AD a été associé au moment de sa création.

Les identités utilisateur du propriétaire du compte Azure et de l’administrateur global Azure AD sont stockées dans un système d’identité hautement sécurisé géré par Microsoft. Le propriétaire du compte Azure est autorisé à créer, mettre à jour et supprimer des abonnements. Bien que l’administrateur global Azure AD soit autorisé à effectuer de nombreuses actions dans Azure AD, vous allez ici vous concentrer uniquement sur la création et la suppression d’identités d’utilisateur.

> [!NOTE]
> Votre organisation possède peut-être déjà un locataire Azure AD si une licence Office 365, Intune ou Dynamics est associée à votre compte.

Le propriétaire du compte Azure possède l’autorisation de créer, mettre à jour et supprimer des abonnements :

![Compte Azure avec responsable du compte Azure et administrateur général Azure AD](../../_images/govern/design/governance-3-0.png)
*Figure 1 - Compte Azure avec responsable du compte et administrateur général Azure AD.*

**L’administrateur global** Azure AD est autorisé à créer des comptes d’utilisateur :

![Compte Azure avec responsable du compte Azure et administrateur général Azure AD](../../_images/govern/design/governance-3-0a.png)
*Figure 2 : L’administrateur général Azure AD crée les comptes d’utilisateur nécessaires dans le locataire.*

Les deux premiers comptes **Propriétaire de la charge de travail App1** et **Propriétaire de la charge de travail App2** sont associés à une personne de votre organisation responsable de la gestion d’une charge de travail. Le compte **Opérations réseau** est détenu par la personne responsable des ressources d’infrastructure partagée. Enfin, le compte **Propriétaire de l’abonnement** est associé à la personne responsable de la propriété des abonnements.

## <a name="resource-access-permissions-model-of-least-privilege"></a>Modèle d’autorisations d’accès aux ressources de privilège minimal

Maintenant que votre système de gestion des identités et vos comptes d’utilisateur ont été créés, vous devez déterminer de quelle manière vous allez appliquer les rôles RBAC (contrôle d’accès basé sur des rôles) à chaque compte pour prendre en charge un modèle d’autorisations de privilège minimal.

Une autre exigence stipule que les ressources associées à chaque charge de travail doivent être isolées les unes des autres, de sorte qu’aucun propriétaire d’une charge de travail donnée ne puisse disposer d’un accès administratif à toute autre charge de travail dont il n’est pas propriétaire. Une exigence supplémentaire impose d’implémenter ce modèle en utilisant uniquement des rôles intégrés pour le contrôle d’accès en fonction du rôle Azure.

Chaque rôle RBAC est appliqué à l’une des trois étendues suivantes dans Azure : **abonnement**, **groupe de ressources** et **ressource** individuelle. Les rôles sont hérités à des étendues inférieures. Par exemple, si un utilisateur se voit attribuer le [rôle de propriétaire intégré](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) au niveau de l’abonnement, ce rôle est également attribué à cet utilisateur aux niveaux du groupe de ressources et des ressources individuelles, sauf en cas de remplacement.

Par conséquent, pour créer un modèle d’accès avec privilège minimum, vous devez déterminer quelles actions un type d’utilisateur particulier est autorisé à effectuer au niveau de chacune de ces trois étendues. Imaginons par exemple que nous devions autoriser un propriétaire d’une charge de travail à gérer l’accès aux seules ressources associées à sa charge de travail, à l’exclusion de toute autre. Si vous deviez affecter le rôle de propriétaire intégré à l’étendue de l’abonnement, chaque propriétaire de charge de travail aurait un accès en gestion à toutes les charges de travail.

Jetons un œil à deux exemples de modèles d’autorisation pour mieux comprendre ce concept. Dans le premier exemple, le modèle fait confiance uniquement à l’administrateur de services fédérés pour créer des groupes de ressources. Dans le deuxième exemple, le modèle attribue le rôle de propriétaire intégré à chaque propriétaire d’une charge de travail dans l’étendue de l’abonnement.

Dans les deux exemples, un administrateur de services d’abonnement se voit attribuer le rôle de propriétaire intégré dans l’étendue de l’abonnement. N’oubliez pas que le rôle de propriétaire intégré accorde toutes les autorisations, dont la gestion de l’accès aux ressources.

![Administrateur de service d’abonnement avec le rôle de propriétaire](../../_images/govern/design/governance-2-1.png)
*Figure 3 - Abonnement dans lequel un administrateur de service est doté du rôle de propriétaire intégré.*

1. Dans le premier exemple, le **propriétaire de la charge de travail A** ne possède pas d’autorisation au niveau de l’étendue de l’abonnement ; par défaut, il ne possède donc pas de droit de gestion des accès aux ressources. Cet utilisateur souhaite déployer et gérer les ressources de sa charge de travail. Il doit contacter **l’administrateur de services fédérés** pour demander la création d’un groupe de ressources.
    ![Le propriétaire de la charge de travail demande la création du groupe de ressources A](../../_images/govern/design/governance-2-2.png)
2. **L’administrateur de services fédérés** passe en revue la demande et crée le **groupe de ressources A**. À ce stade, le **propriétaire de la charge de travail A** n’est toujours pas autorisé à faire quoi que ce soit.
    ![L’administrateur de service crée le groupe de ressources A](../../_images/govern/design/governance-2-3.png)
3. **L’administrateur de services fédérés** ajoute le **propriétaire de la charge de travail A** au **groupe de ressources A** et lui affecte le [rôle de contributeur intégré](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor). Le rôle de contributeur accorde toutes les autorisations sur le **groupe de ressources A**, à l’exception de la gestion des autorisations d’accès.
    ![L’administrateur de service ajoute le propriétaire de la charge de travail A au groupe de ressources A](../../_images/govern/design/governance-2-4.png)
4. Supposons que le **propriétaire de la charge de travail A** ait besoin que deux membres de l’équipe puissent visualiser les données d’analyse de l’UC et du trafic réseau, afin de planifier les capacités pour la charge de travail. Étant donné que le **propriétaire de la charge de travail A** dispose du rôle de contributeur, il n’est pas autorisé à ajouter un utilisateur au **groupe de ressources A**. Il doit en fait la demande à **l’administrateur de services fédérés**.
    ![Le propriétaire de la charge de travail demande l’ajout de contributeurs au groupe de ressources](../../_images/govern/design/governance-2-5.png)
5. **L’administrateur de services fédérés** examine la demande et ajoute les deux **contributeurs de la charge de travail** au **groupe de ressources A**. Aucun de ces deux utilisateurs n’ayant besoin de l’autorisation de gérer les ressources, le [rôle de lecteur intégré](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) leur est attribué.
    ![L’administrateur de service ajoute les contributeurs de la charge de travail au groupe de ressources A](../../_images/govern/design/governance-2-6.png)
6. Le **propriétaire de la charge de travail B** a également besoin d’un groupe de ressources auquel rattacher les ressources de sa charge de travail. Comme pour le **propriétaire de la charge de travail A**, le **propriétaire de la charge de travail B** ne dispose au départ d’aucune autorisation d’exécuter une action dans l’étendue de l’abonnement. Il doit donc envoyer une demande à **l’administrateur de services fédérés**.
    ![Le propriétaire de la charge de travail B demande la création du groupe de ressources B](../../_images/govern/design/governance-2-7.png)
7. **L’administrateur de services fédérés** passe en revue la demande et crée le **groupe de ressources B**.  ![L’administrateur de services fédérés crée le groupe de ressources B](../../_images/govern/design/governance-2-8.png)
8. **L’administrateur de services fédérés** ajoute alors le **propriétaire de la charge de travail B** au **groupe de ressources B** et lui attribue le rôle de contributeur intégré.
    ![L’administrateur de services fédérés ajoute le propriétaire de la charge de travail B au groupe de ressources B](../../_images/govern/design/governance-2-9.png)

À ce stade, chacun des propriétaires de charges de travail est isolé dans son propre groupe de ressources. Ni les propriétaires de charges de travail ni les membres de leur équipe ne disposent d’un accès administratif aux ressources d’un autre groupe de ressources.

![Abonnement avec les groupes de ressources A et B](../../_images/govern/design/governance-2-10.png)
*Figure 4 - Abonnement avec deux propriétaires de charges de travail isolés avec leur propre groupe de ressources.*

Ce modèle est un modèle avec privilège minimum : chaque utilisateur se voit attribuer l’autorisation appropriée dans l’étendue de gestion des ressources qui convient.

Mais, comme vous le voyez, chaque tâche décrite dans cet exemple a été effectuée par **l’administrateur de services fédérés**. Bien qu’il s’agisse d’un exemple simplifié qui ne pose en apparence aucun problème étant donné qu’il n’y a que deux propriétaires de charges de travail, il est facile d’imaginer les types de problèmes que cela pourrait occasionner dans une organisation de grande envergure. Par exemple, **l’administrateur de services fédérés** peut devenir un goulot d’étranglement, voir s’accumuler les demandes en souffrance et entraîner des retards.

Examinons un deuxième exemple qui réduit le nombre de tâches confiées à **l’administrateur de services fédérés**.

1. Dans ce modèle, le **propriétaire de charge de travail A** se voit attribuer le rôle de propriétaire intégré dans l’étendue de l’abonnement, ce qui lui permet de créer son propre groupe de ressources : **le groupe de ressources A**.  ![L’administrateur de services fédérés ajoute le propriétaire de la charge de travail A à l’abonnement](../../_images/govern/design/governance-2-11.png)
2. Une fois le **groupe de ressources A** créé, le **propriétaire de charge de travail A** est ajouté par défaut et hérite du rôle de propriétaire intégré de l’étendue de l’abonnement.
    ![Le propriétaire de la charge de travail A crée le groupe de ressources A](../../_images/govern/design/governance-2-12.png)
3. Le rôle de propriétaire intégré accorde au **propriétaire de charge de travail A** l’autorisation de gérer l’accès au groupe de ressources. Le **propriétaire de charge de travail A** ajoute deux **contributeurs de charge de travail** et attribue à chacun d’eux le rôle de lecteur intégré.
    ![Le propriétaire de la charge de travail A ajoute des contributeurs de la charge de travail](../../_images/govern/design/governance-2-13.png)
4. **L’administrateur de services fédérés** ajoute à présent le **propriétaire de la charge de travail B** à l’abonnement en lui attribuant le rôle de propriétaire intégré.
    ![L’administrateur de services fédérés ajoute le propriétaire de la charge de travail B à l’abonnement](../../_images/govern/design/governance-2-14.png)
5. Le **propriétaire de la charge de travail B** crée le **groupe de ressources B** et est ajouté par défaut. Là encore, le **propriétaire de la charge de travail B** hérite du rôle de propriétaire intégré de l’étendue de l’abonnement.
    ![Le propriétaire de la charge de travail B crée le groupe de ressources B](../../_images/govern/design/governance-2-15.png)

Notez que dans ce modèle, **l’administrateur de services fédérés** est moins intervenu que dans le premier exemple car l’accès administratif a été délégué à chaque propriétaire de la charge de travail.

![Abonnement avec les groupes de ressources A et B](../../_images/govern/design/governance-2-16.png)
*Figure 5 - Abonnement avec un administrateur de service et deux propriétaires de charges de travail auxquels le rôle de propriétaire intégré a été attribué.*

Toutefois, étant donné que le **propriétaire de la charge de travail A** et le **propriétaire de la charge de travail B** se sont vu attribuer le rôle de propriétaire intégré dans l’étendue de l’abonnement, chacun d’eux a hérité du rôle de propriétaire intégré pour le groupe de ressources de l’autre. Cela signifie que non seulement ils ont chacun un accès complet aux ressources de l’autre, mais ils peuvent aussi déléguer l’accès en gestion à leurs groupes de ressources respectifs. Par exemple, le **propriétaire de la charge de travail B** a le droit d’ajouter n’importe quel autre utilisateur au **groupe de ressources A** et peut lui attribuer le rôle de son choix, y compris le rôle de propriétaire intégré.

Si vous comparez chaque exemple aux exigences, vous pouvez voir que les deux exemples prennent en charge un seul utilisateur approuvé dans l’étendue de l’abonnement, lequel dispose de l’autorisation d’accorder des droits d’accès aux ressources aux deux propriétaires de charges de travail. Aucun des deux propriétaires de charges de travail ne disposait par défaut d’un accès à la gestion des ressources et devait demander à **l’administrateur de services fédérés** de lui attribuer explicitement les autorisations nécessaires. En revanche, seul le premier exemple répond à notre besoin d’isoler les ressources associées à chaque charge de travail, de telle sorte qu’aucun propriétaire d’une charge de travail n’ait accès aux ressources d’une autre charge de travail.

## <a name="resource-management-model"></a>Modèle de gestion des ressources

Maintenant que vous avez conçu un modèle d’autorisations de privilège minimal, examinez quelques exemples pratiques d’utilisation de ces modèles de gouvernance. Souvenez-vous que vous devez prendre en charge les trois environnements suivants :

1. **Environnement à infrastructure partagée :** un groupe de ressources partagé par toutes les charges de travail. Il s’agit par exemple des passerelles de réseau, des pare-feu et des services de sécurité.
2. **Environnement de production :** plusieurs groupes de ressources représentant plusieurs charges de travail de production. Ces ressources sont utilisées pour héberger les artefacts d’application privés et publics. Ces ressources sont généralement adossées à des modèles de gouvernance et de sécurité plus stricts afin de protéger les ressources, le code d’application et les données contre tout accès non autorisé.
3. **Environnement de préproduction :** plusieurs groupes de ressources représentant plusieurs charges de travail prêtes hors production. Ces ressources sont utilisées à des fins de développement et de test. Elles peuvent avoir un modèle de gouvernance plus souple pour renforcer l’agilité des développeurs. Le niveau de sécurité de ces groupes doit s’accroître à mesure que le processus de développement d’applications évolue vers le stade de la « production ».

Pour chacun de ces trois environnements, vous avez besoin de suivre les données de coût par **propriétaire de charges de travail** et/ou par **environnement**. Autrement dit, vous souhaitez connaître le coût récurrent de **l'infrastructure partagée**, les frais engagés par les personnes intervenant à la fois dans les environnements de **préproduction** et de **production** ainsi que le coût global des environnements de **préproduction** et de **production**.

Vous savez déjà que les ressources sont limitées à deux niveaux : **abonnement** et **groupe de ressources**. Il faut donc commencer par déterminer la façon d’organiser les environnements par **abonnement**. Il existe deux possibilités : un abonnement unique ou plusieurs abonnements.

Avant d’examiner des exemples de chacun de ces modèles, passez en revue la structure de gestion des abonnements dans Azure.

À titre de rappel, une personne de l’organisation est responsable des abonnements et cet utilisateur possède le compte **Propriétaire de l’abonnement** dans le locataire Azure AD. Ce compte n’est cependant pas autorisé à créer des abonnements. Seul le **Propriétaire du compte Azure** a l’autorisation de le faire :

![Un propriétaire de compte Azure crée un abonnement](../../_images/govern/design/governance-3-0b.png)
*Figure 6 - Un propriétaire de compte Azure crée un abonnement.*

Une fois l’abonnement créé, le **Propriétaire du compte Azure** peut ajouter le compte **Propriétaire de l’abonnement** à l’abonnement en lui attribuant le rôle de **propriétaire** :

![Le propriétaire du compte Azure ajoute le compte d’utilisateur du propriétaire de l’abonnement à l’abonnement en lui attribuant le rôle de propriétaire.](../../_images/govern/design/governance-3-0c.png)
*Figure 7 - Le propriétaire du compte Azure ajoute le compte d’utilisateur du **propriétaire de l’abonnement** à l’abonnement en lui attribuant le rôle de **propriétaire**.*

Le **Propriétaire de l’abonnement** peut à présent créer des **groupes de ressources** et déléguer la gestion des accès aux ressources.

Voyons tout d’abord un exemple de modèle de gestion des ressources utilisant un seul abonnement. Il faut commencer par aligner les groupes de ressources sur les trois environnements. Deux options s'offrent à vous :

1. Aligner chaque environnement sur un seul groupe de ressources. Toutes les ressources de l’infrastructure partagée sont déployées sur un seul groupe de ressources de **l’infrastructure partagée**. Toutes les ressources associées aux charges de travail de développement sont déployées sur un seul groupe de ressources de **développement**. Toutes les ressources associées aux charges de travail de production sont déployées dans un seul groupe de ressources de **production** pour l’environnement de **production**.
2. Créer des groupes de ressources distincts pour chaque charge de travail, en utilisant une convention d’affectation de noms et des balises pour aligner les groupes de ressources sur chacun des trois environnements.

Commençons par examiner la première option. Vous allez utiliser le modèle d’autorisations dont il a été question dans la section précédente, avec un seul administrateur de services fédérés d’abonnement qui crée des groupes de ressources et y ajoute des utilisateurs disposant du rôle de **contributeur** ou de **lecteur** intégré.

1. Le premier groupe de ressources déployé représente l’environnement **d’infrastructure partagée**. Le **propriétaire de l’abonnement** crée un groupe de ressources nommé `netops-shared-rg`pour les ressources de l’infrastructure partagée.
    ![Création d’un groupe de ressources](../../_images/govern/design/governance-3-0d.png)
2. Le **propriétaire de l’abonnement** ajoute le compte d’utilisateur **opérations réseau** au groupe de ressources et lui affecte le rôle de **contributeur**.
    ![Ajout d’un utilisateur d’opérations réseau](../../_images/govern/design/governance-3-0e.png)
3. L’utilisateur des **opérations réseau** crée une [passerelle VPN](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) et la configure pour se connecter à l’appareil VPN local. L’utilisateur des **opérations réseau** applique également une paire de [balises](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) à chacune des ressources : *environment:shared* et *managedBy:netOps*. Lorsque **l’administrateur de services fédérés d’abonnement** exporte un rapport de coûts, les coûts seront alignés sur chacune de ces balises. Cela permet à **l’administrateur de services fédérés d’abonnement** de basculer les coûts à l’aide de la balise *environment* et de la balise *managedBy*. Notez le compteur de **limites de ressources** situé en haut à droite de la figure. Chaque abonnement Azure possède des [limites de service](https://docs.microsoft.com/azure/azure-subscription-service-limits), et pour vous aider à comprendre l’impact de ces limites, vous allez suivre la limite du réseau virtuel pour chaque abonnement. Il existe une limite de 1 000 réseaux virtuels par abonnement ; après avoir déployé le premier réseau virtuel, il en reste 999 de disponibles.
    ![Création d’une passerelle VPN](../../_images/govern/design/governance-3-1.png)
4. Deux groupes de ressources supplémentaires sont déployés. Le premier s’appelle `prod-rg`. Ce groupe de ressources est aligné sur l’environnement de production. Le second, nommé `dev-rg`, est aligné sur l’environnement de développement. Toutes les ressources associées aux charges de travail de production sont déployées dans l’environnement de production, et toutes les ressources associées aux charges de travail de développement sont déployées dans l’environnement de développement. Dans cet exemple, vous allez déployer uniquement deux charges de travail pour chacun de ces deux environnements afin de ne pas rencontrer les limites de service d’abonnement Azure. Notez cependant que chaque groupe de ressources est limité à 800 ressources par groupe de ressources. Si vous continuez d’ajouter des charges de travail à chaque groupe de ressources, cette limite peut potentiellement être atteinte.
    ![Création de groupes de ressources](../../_images/govern/design/governance-3-2.png)
5. Le premier **propriétaire de charges de travail** envoie une demande à **l’administrateur de services fédérés d’abonnement** et est ajouté aux groupes de ressources de l’environnement de développement et de l’environnement de production avec le rôle de **contributeur**. Comme expliqué précédemment, le rôle de **contributeur** permet à l’utilisateur d’effectuer n’importe quelle opération, sauf attribuer un rôle à un autre utilisateur. Le premier **propriétaire de la charge de travail** peut maintenant créer les ressources associées à sa charge de travail.
    ![Ajout de contributeurs](../../_images/govern/design/governance-3-3.png)
6. Le premier **propriétaire de la charge de travail** crée dans chacun des deux groupes de ressources un réseau virtuel comprenant chacun une paire de machines virtuelles. Le premier **propriétaire de la charge de travail** applique les balises *environment* et *managedBy* à toutes les ressources. Notez que le compteur de limite de service Azure indique qu’il reste désormais 997 réseaux virtuels.
    ![Création de réseaux virtuels](../../_images/govern/design/governance-3-4.png)
7. Aucun des réseaux virtuels ne possède de connectivité en local au moment de leur création. Dans ce type d’architecture, chaque réseau virtuel doit être appairé au *hub-vnet* dans l’environnement de **l’infrastructure partagée**. Le peering de réseaux virtuels crée une connexion entre deux réseaux virtuels distincts et autorise le trafic réseau entre eux. Notez que ce peering n’est pas transitif par nature. Un peering doit être spécifié dans chacun des deux réseaux virtuels connectés, et si seulement un des réseaux virtuels spécifie un peering, la connexion est incomplète. Pour mieux illustrer cet effet, le premier **propriétaire de la charge de travail** spécifie un peering entre **prod-vnet** et **hub-vnet**. Le premier peering est créé, mais aucun trafic n’est acheminé car le peering complémentaire entre **hub-vnet** et **prod-vnet** n’a pas encore été spécifié. Le premier **propriétaire de la charge de travail** contacte l’utilisateur des **opérations réseau** et lui demandes la connexion de ce peering complémentaire.
    ![Création d’une connexion d’appairage](../../_images/govern/design/governance-3-5.png)
8. L’utilisateur des **opérations réseau** examine la demande, l’approuve, puis spécifie le peering dans les paramètres de **hub-vnet**. La connexion du peering est maintenant terminée et le trafic réseau transite entre les deux réseaux virtuels.
    ![Création d’une connexion d’appairage](../../_images/govern/design/governance-3-6.png)
9. À présent, un deuxième **propriétaire de charge de travail** envoie une demande à **l’administrateur de services fédérés d’abonnement** et est ajouté aux groupes de ressources existants des environnements de **production** et de **développement** avec le rôle de **contributeur**. Le deuxième **propriétaire de la charge de travail** possède les mêmes autorisations sur toutes les ressources que le premier **propriétaire de la charge de travail** dans chaque groupe de ressources.
    ![Ajout de contributeurs](../../_images/govern/design/governance-3-7.png)
10. Le deuxième **propriétaire de la charge de travail** crée un sous-réseau dans le réseau virtuel **prod-vnet**, puis ajoute deux machines virtuelles. Le deuxième **propriétaire de la charge de travail** applique les balises *environment* et *managedBy* à chaque ressource.
    ![Création de sous-réseaux](../../_images/govern/design/governance-3-8.png)

Cet exemple de modèle de gestion de ressources nous permet de gérer les ressources dans les trois environnements dont nous avons besoin. Les ressources de l’infrastructure partagée sont protégées, car un seul utilisateur de l’abonnement a l’autorisation d’accéder à ces ressources. Chacun des propriétaires de charge de travail peut utiliser les ressources de l’infrastructure partagée sans avoir la moindre autorisation sur les ressources partagées proprement dites. Cependant, ce modèle de gestion ne répond pas à l’exigence d’isolation des charges de travail, car les deux **propriétaires de charge de travail** peuvent accéder aux ressources de la charge de travail de l’autre.

Il existe un autre élément important à prendre en compte avec ce modèle, qui peut ne pas sembler évident de prime abord. Dans l’exemple, c’est le **propriétaire de la charge de travail app1** qui a demandé la connexion du peering réseau avec le réseau virtuel **hub-vnet** afin d’obtenir une connectivité en local. L’utilisateur des **opérations réseau** a évalué cette demande compte tenu des ressources déployées avec cette charge de travail. Lorsque le **propriétaire de l’abonnement** a ajouté le **propriétaire de la charge de travail app2** avec le rôle de **contributeur**, cet utilisateur disposait des droits d’accès administratif sur toutes les ressources du groupe de ressources  **prod-rg**.

![Diagramme montrant les droits d’accès à la gestion](../../_images/govern/design/governance-3-10.png)

Autrement dit, le **propriétaire de la charge de travail app2** disposait de l’autorisation de déployer son propre sous-réseau avec des machines virtuelles dans le réseau virtuel **prod-vnet**. Par défaut, ces machines virtuelles ont désormais accès au réseau local. L’utilisateur des **opérations réseau** n’a pas connaissance de ces machines et n’a pas approuvé leur connectivité au niveau local.

Voyons maintenant le cas d’un abonnement unique avec plusieurs groupes de ressources pour différents environnements et charges de travail. Notez que dans l’exemple précédent, les ressources pour chaque environnement étaient facilement identifiables, car elles se trouvaient dans le même groupe de ressources. Maintenant que vous n’avez plus ce regroupement, il vous faut utiliser une convention d’affectation des noms de groupe de ressources pour proposer ces fonctionnalités.

1. Les ressources de **l’infrastructure partagée** auront toujours un groupe de ressources distinct dans ce modèle, qui reste le même. Chaque charge de travail a besoin de deux groupes de ressources (un pour l’environnement de **développement** et un pour l’environnement de **production**). Pour la première charge de travail, le **propriétaire de l’abonnement** crée deux groupes de ressources. Le premier s’appelle **app1-prod-rg** et le deuxième s’appelle **app1-dev-rg**. Comme indiqué précédemment, cette convention d’affectation de noms identifie les ressources comme étant associées à la première charge de travail, **app1**, et soit à l’environnement **dev** soit à l’environnement **prod**. Là encore, le propriétaire de l’*abonnement* ajoute le **propriétaire de la charge de travail app1** au groupe de ressources avec le rôle de **contributeur**.
    ![Ajout de contributeurs](../../_images/govern/design/governance-3-12.png)
2. De la même façon que dans le premier exemple, le **propriétaire de la charge de travail app1** déploie un réseau virtuel nommé **app1-prod-vnet** dans l’environnement de **production** et un autre réseau virtuel nommé **app1-dev-vnet** dans l’environnement de **développement**. Là encore, le **propriétaire de la charge de travail app1** envoie une demande à l’utilisateur des **opérations réseau** afin de créer une connexion de peering. Notez que le **propriétaire de la charge de travail app1** ajoute les mêmes balises que dans le premier exemple et que le compteur de limite indique qu’il ne reste que 997 réseaux virtuels dans l’abonnement.
    ![Création d’une connexion d’appairage](../../_images/govern/design/governance-3-13.png)
3. Le **propriétaire de l’abonnement** crée deux groupes de ressources pour le **propriétaire de la charge de travail app2**. En suivant les mêmes conventions que pour le **propriétaire de la charge de travail app1**, les groupes de ressources sont nommés **app2-prod-rg** et **app2-dev-rg**. Le **propriétaire de l’abonnement** ajoute le **propriétaire de la charge de travail app2** à chacun des groupes de ressources avec le rôle de **contributeur**.
    ![Ajout de contributeurs](../../_images/govern/design/governance-3-14.png)
4. Le *propriétaire de la charge de travail App2* déploie des réseaux virtuels et des machines virtuelles sur les groupes de ressources en utilisant les mêmes conventions d’affectation de noms. Les balises sont ajoutées et le compteur de limite indique qu’il reste 995 réseaux virtuels dans *l’abonnement*.
    ![Déploiement de réseaux virtuels et de machines virtuelles](../../_images/govern/design/governance-3-15.png)
5. Le *propriétaire de la charge de travail App2* envoie une demande à l’utilisateur des *opérations réseau* pour appairer les réseaux virtuels *app2-prod-vnet* et *hub-vnet*. L’utilisateur des *opérations réseau* crée la connexion de peering.
    ![Création d’une connexion d’appairage](../../_images/govern/design/governance-3-16.png)

Le modèle de gestion qui en résulte est similaire au premier exemple, mais présente quelques différences majeures :

- Chacune des deux charges de travail est isolée par charge de travail et par environnement.
- Ce modèle a besoin de deux réseaux virtuels de plus que le premier exemple de modèle. Bien que cela ne fasse pas grande différence dans le cas de deux charges de travail, la limite théorique imposée au nombre de charges de travail pour ce modèle est de 24.
- Les ressources ne sont plus regroupées dans un seul groupe de ressources pour chaque environnement. Le regroupement des ressources suppose de comprendre les conventions d’affectation de noms utilisées pour chaque environnement.
- Chacune des connexions des réseaux virtuels appairés a été vérifiée et approuvée par l’utilisateur des *opérations réseau*.

Voyons maintenant le cas d’un modèle de gestion des ressources utilisant plusieurs abonnements. Dans ce modèle, vous allez aligner chacun des trois environnements sur un abonnement distinct : un abonnement de **services partagés**, un abonnement de **production** et un abonnement de **développement**. Les aspects à prendre en compte pour ce modèle sont similaires à ceux d’un modèle qui utilise un seul abonnement. Par conséquent, vous allez devoir déterminer la manière dont vous allez aligner les groupes de ressources sur les charges de travail. Vous savez déjà que la création d’un groupe de ressources pour chaque charge de travail permettait d’isoler les charges de travail, aussi vous allez rester fidèles à ce modèle dans cet exemple.

1. Dans ce modèle, nous avons trois *abonnements* : *infrastructure partagée*, *production* et *développement*. Chacun de ces trois abonnements a besoin d’un *propriétaire de l’abonnement* ; dans l’exemple simplifié, vous allez utiliser le même compte d’utilisateur pour les trois. Les ressources de *l’infrastructure partagée* sont gérées de la même façon que pour les deux premiers exemples ci-dessus, et la première charge de travail est associée à *app1-rg* dans l’environnement de *production* et au groupe de ressources du même nom dans l’environnement de *développement*. Le *propriétaire de la charge de travail app1* est ajouté à chacun des groupes de ressources avec le rôle de *contributeur*.
    ![Ajout de contributeurs](../../_images/govern/design/governance-3-17.png)
2. Comme pour les exemples précédents, le *propriétaire de la charge de travail app1* crée les ressources et demande la connexion de peering avec le réseau virtuel de *l’infrastructure partagée*. Le *propriétaire de la charge de travail App1* ajoute uniquement la balise *managedBy* car la balise *environment* n’est plus nécessaire. Autrement dit, les ressources pour chaque environnement sont maintenant regroupées dans le même *abonnement* et la balise *environment* est redondante. Le compteur de limite indique qu’il reste 999 réseaux virtuels.
    ![Création d’une connexion d’appairage](../../_images/govern/design/governance-3-18.png)
3. Pour finir, le *propriétaire de l’abonnement* répète le processus pour la deuxième charge de travail, en ajoutant les groupes de ressources avec le *propriétaire de la charge de travail app2* dans le rôle de *contributeur. Le compteur de limite pour chaque abonnement d’environnement indique qu’il reste 998 réseaux virtuels.

Ce modèle de gestion présente les mêmes avantages que ceux du deuxième exemple ci-dessus. Le problème de limitation est cependant moindre étant donné que les limites sont réparties entre deux *abonnements*. L’inconvénient est que les données de coût suivies par les balises doivent être regroupées dans les trois *abonnements*.

En conclusion, vous pouvez choisir l’un de ces deux exemples de modèles de gestion des ressources selon la priorité de vos besoins. Si vous pensez que votre organisation n’atteindra pas les limites de service pour un seul abonnement, vous pouvez utiliser un seul abonnement avec plusieurs groupes de ressources. À l’inverse, si votre organisation prévoit de nombreuses charges de travail, le mieux est de privilégier plusieurs abonnements pour chaque environnement.

## <a name="implement-the-resource-management-model"></a>Implémenter le modèle de gestion des ressources

Vous avez découvert plusieurs modèles différents pour gouverner l’accès aux ressources Azure. Vous allez maintenant parcourir les étapes nécessaires pour implémenter le modèle de gestion des ressources avec un seul abonnement pour chacun des environnements **d’infrastructure partagée**, de **production** et de **développement** du guide de conception. Vous allez prendre un seul **propriétaire d’abonnement** pour les trois environnements. Chaque charge de travail sera isolée dans un **groupe de ressources** avec un **propriétaire de charge de travail** disposant du rôle de **contributeur**.

> [!NOTE]
> Pour en savoir plus sur la relation entre les abonnements et les comptes Azure, consultez [Présentation de l’accès aux ressources dans Azure](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles).

Procédez comme suit :

1. Créez un [compte Azure](https://docs.microsoft.com/azure/active-directory/sign-up-organization) si vous n’en avez pas encore. La personne qui s’inscrit pour le compte Azure devient l’administrateur de compte Azure et la direction de votre organisation doit choisir une personne pour assumer ce rôle. Cette personne possède les responsabilités suivantes :
    - Création d’abonnements.
    - Création et administration des locataires [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) qui stockent l’identité de l’utilisateur pour ces abonnements.
2. L’équipe dirigeante de votre organisation désigne les personnes qui auront les responsabilités suivantes :
    - Gestion des identités d’utilisateur ; un [locataire Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant) est créé par défaut lors de la création du compte Azure de votre organisation et l’administrateur de compte est ajouté en tant [qu’administrateur global Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) par défaut. Votre organisation peut désigner un autre utilisateur chargé de gérer les identités d’utilisateur en [attribuant à cet utilisateur le rôle d’administrateur global Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal).
    - Abonnements, ce qui signifie que ces utilisateurs :
        - Gèrent les coûts associés à l’utilisation des ressources dans cet abonnement.
        - Implémentent et gèrent le modèle d’autorisations minimales pour l’accès aux ressources.
        - Effectuent un suivi des limites de service.
    - Services d’infrastructure partagée (si votre organisation décide d’utiliser ce modèle), ce qui signifie que cet utilisateur est responsable de :
        - La connectivité entre le réseau local et Azure.
        - La propriété de la connectivité réseau dans Azure via le peering de réseaux virtuels.
    - Propriétaires de charges de travail.
3. L’administrateur global Azure AD crée les [nouveaux comptes d’utilisateur](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory) pour :
    - La personne qui sera le **propriétaire de l’abonnement** pour chaque abonnement associé à chaque environnement. Notez que cela est nécessaire uniquement si **l’administrateur de services fédérés** de l’abonnement n’est pas chargé de gérer l’accès aux ressources pour chaque abonnement/environnement ;
    - La personne qui sera l’**utilisateur des opérations réseau**.
    - Les personnes qui seront les **propriétaires de charges de travail**.
4. L’administrateur de compte Azure crée les trois abonnements suivants à l’aide du [portail de compte Azure](https://account.azure.com) :
    - Un abonnement pour l’environnement d’**infrastructure partagée**.
    - Un abonnement pour l’environnement de **production**.
    - Un abonnement pour l’environnement de **développement**.
5. L’administrateur de compte Azure [ajoute le propriétaire de service d’abonnement à chaque abonnement](https://docs.microsoft.com/azure/billing/billing-add-change-azure-subscription-administrator#to-assign-a-user-as-an-administrator).
6. Un processus d’approbation est créé pour permettre aux **propriétaires de charges de travail** de demander la création de groupes de ressources. Le processus d’approbation peut être implémenté de différentes façons (par e-mail par exemple), mais vous pouvez également utiliser un outil de gestion des processus tel que les [flux de travail SharePoint](https://support.office.com/article/introduction-to-sharepoint-workflow-07982276-54e8-4e17-8699-5056eff4d9e3). Le processus d’approbation peut se dérouler comme suit :
    - Le **propriétaire de la charge de travail** prépare une nomenclature pour les ressources Azure nécessaires, dans l’environnement de **développement** et/ou dans l’environnement de **production**, et la soumet au **propriétaire de l’abonnement**.
    - Le **propriétaire de l’abonnement** passe en revue la nomenclature et valide les ressources requises pour s’assurer que les ressources demandées sont adaptées à l’utilisation prévue ; par exemple en vérifiant que les [ tailles de machine virtuelle](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) demandées sont correctes.
    - Si la demande n’est pas approuvée, le **propriétaire de la charge de travail** en est informé. Si la demande est approuvée, le **propriétaire de l’abonnement** [crée le groupe de ressources demandé](https://docs.microsoft.com/azure/azure-resource-manager/manage-resource-groups-portal#create-resource-groups) suivant les [conventions de nommage](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) de votre organisation, [ajoute le **propriétaire de la charge de travail**](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal#add-a-role-assignment) avec le rôle de [**contributeur**](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) et envoie une notification au **propriétaire de la charge de travail** pour l’informer de la création du groupe de ressources.
7. Un processus d’approbation est créé pour permettre aux propriétaires de charges de travail de demander au propriétaire de l’infrastructure partagée l’établissement d’une connexion pour le peering des réseaux virtuels. Comme dans l’étape précédente, ce processus d’approbation peut être implémenté par e-mail ou à l’aide d’un outil de gestion de processus.

Maintenant que vous avez implémenté votre modèle de gouvernance, vous pouvez déployer vos services d’infrastructure partagée.

## <a name="related-resources"></a>Ressources associées

[Rôles intégrés pour les ressources Azure](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [En savoir plus sur le déploiement d’une infrastructure de base](../../infrastructure/virtual-machines/basic-workload.md)
