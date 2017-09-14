---
title: Attribut de groupes (Master Data Services) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b5c90f2a2df358af81f563f5740450ba130d24e5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="attribute-groups-master-data-services"></a>Groupes d'attributs (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les groupes d’attributs permettent d’organiser les attributs dans une entité. Lorsqu'une entité comporte un grand nombre d'attributs, les groupes d'attributs améliorent la manière dont elle est affichée dans l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="how-attribute-groups-change-the-display"></a>Comment les groupes d'attributs modifient l'affichage  
 Les groupes d’attributs sont affichés sous forme d’onglets au-dessus de la grille dans le domaine fonctionnel **Explorateur[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] de** .  
  
 Lorsqu’une entité a un grand nombre d’attributs et vous la consultez dans une grille dans l’**Explorateur**, vous devez faire défiler le curseur à droite pour consulter tous les attributs. Pour éviter ce défilement, vous pouvez créer des groupes d'attributs.  
  
-   Les groupes d'attributs incluent toujours les attributs Name et Code.  
  
-   Chaque attribut d'une entité peut appartenir à un ou plusieurs groupes d'attributs.  
  
-   Tous les attributs sont inclus automatiquement sous l’onglet **Tous les attributs** dans **l’Explorateur**.  
  
-   Il n’existe aucun moyen de masquer l’onglet **Tous les attributs** .  
  
 Les groupes d’attributs sont administrés dans la zone fonctionnelle **Administration de système** de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="show-or-hide-attribute-groups"></a>Afficher ou masquer les groupes d'attributs  
 Lorsque vous créez un groupe d'attributs, il est automatiquement masqué pour tous les utilisateurs, à l'exception de son créateur. Pour plus d’informations sur le fait de rendre visible le groupe, consultez [Rendre un groupe d’attributs visible pour les utilisateurs &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md).  
  
 Si vous souhaitez masquer un attribut spécifique dans un groupe, vous pouvez lui affecter une autorisation **Refuser**. Pour plus d’informations, consultez [les autorisations de feuille &#40; Master Data Services &#41; ](../master-data-services/leaf-permissions-master-data-services.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer un groupe d'attributs et y ajouter des attributs.|[Créer un groupe d’attributs &#40; Master Data Services &#41;](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|Rendre un groupe d'attributs visible pour les utilisateurs.|[Rendre un groupe d’attributs Visible pour les utilisateurs &#40; Master Data Services &#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)|  
|Modifier le nom d'un groupe d'attributs existant.|[Modifier un nom de groupe d’attributs &#40; Master Data Services &#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|Supprimer un groupe d'attributs existant.|[Supprimer un groupe d’attributs &#40; Master Data Services &#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a>Contenu connexe  
  
-   [Attributs &#40; Master Data Services &#41;](../master-data-services/attributes-master-data-services.md)  
  
  