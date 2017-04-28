---
title: "Cr&#233;er un attribut bas&#233; sur un domaine (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributs basés sur un domaine [Master Data Services], création"
  - "création d'attributs basés sur un domaine [Master Data Services]"
  - "attributs [Master Data Services], création d’attributs basés sur un domaine"
ms.assetid: 11c31c9f-e6cc-47b7-b76a-d691f84c93c6
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Cr&#233;er un attribut bas&#233; sur un domaine (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un attribut basé sur un domaine pour remplir les valeurs d'un attribut avec les membres d'une entité.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Une entité doit exister pour servir de source de valeurs d'attribut. Par exemple, vous devez créer l'entité Color avant de créer un attribut basé sur un domaine et sur l'entité Color. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
-   Une entité doit exister pour créer l'attribut qui lui est destiné. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## Informations sur les attributs  
 Pour chaque attribut créé, une ligne comportant sept colonnes est ajoutée à la grille. Le tableau suivant décrit ces colonnes.  
  
|Colonne|Description|  
|------------|-----------------|  
|État|État de l’attribut.<br /><br /> Quand vous cliquez sur Enregistrer, l’image ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status") indique que l’attribut est en cours de mise à jour.<br /><br /> En cas d’erreur pendant la création ou la modification d’un attribut, l’image ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status") s’affiche.<br /><br /> Dans le cas contraire, l’état présente la valeur OK et l’image ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status") s’affiche.|  
|Nom|Nom de l'attribut.|  
|Nom complet|Nom de l’attribut.|  
|Description|Description de l’attribut.|  
|Largeur d’affichage en pixels|Largeur de l’attribut.|  
|Types et propriétés|Informations sur le type et le type de données de l’attribut.|  
|Activer le suivi des modifications|Spécifie si le suivi des modifications est activé sur l’attribut et indique le numéro du groupe entre parenthèses.|  
  
 Quand vous cliquez sur un attribut, les informations suivantes s’affichent.  
  
-   **Créé par**: nom de l’utilisateur qui a créé l’attribut.  
  
-   **Le**: date et heure de création de l’attribut.  
  
-   **Mis à jour par**: nom du dernier utilisateur qui a mis à jour l’attribut.  
  
-   **Le**: date et heure de la dernière mise à jour de l’attribut.  
  
### Pour créer un attribut basé sur un domaine  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Sur la page **Gérer les modèles** , sélectionnez un modèle, puis cliquez sur **Entités**.  
  
3.  Sur la page **Gérer les entités** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer un attribut.  
  
4.  Cliquez sur **Attributs**.  
  
5.  Dans la page **Gérer les attributs** , effectuez l’une des opérations suivantes, puis cliquez sur **Ajouter**.  
  
    -   Si l’attribut concerne les membres feuille, sélectionnez **Feuille** dans la zone de liste **Types de membre** .  
  
    -   Si l’attribut concerne les membres consolidés, sélectionnez **Consolidé** dans la zone de liste **Types de membre** .  
  
    -   Si l’attribut concerne les collections, sélectionnez **Collection** dans la zone de liste **Types de membre** .  
  
6.  Dans la zone **Nom** , tapez un nom pour l'attribut. Pour obtenir la liste des mots qui ne doivent pas être utilisés comme noms d’attribut, consultez [Mots réservés &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
7.  Si vous le souhaitez, entrez le nom complet et une description dans le champ **Description** .  
  
8.  Dans la zone **Largeur d'affichage en pixels** , tapez la largeur de la colonne d'attribut à afficher dans la grille **Explorateur** .  
  
9. Dans la liste **Type d’attribut**, sélectionnez **Basé sur un domaine**.  
  
10. Dans la liste **Entité de domaine** , sélectionnez l’entité à utiliser pour renseigner les valeurs d’attribut.  
  
11. **Facultatif, pour les attributs basés sur un domaine des membres feuille.** Sélectionnez un attribut parent de filtre utilisé pour limiter les valeurs autorisées pour l’attribut basé sur un domaine.  
  
     L’attribut parent du filtre doit être un autre attribut basé sur un domaine d’un membre feuille attaché à la même entité. Ceci suppose d’instaurer une hiérarchie dérivée contenant un niveau qui définit la relation parent-enfant entre les entités de domaine des deux attributs.  
  
     Pour plus d’informations sur la restriction des valeurs autorisées, consultez le billet [How to filter Domain Based Attribute drop down lists](https://blogs.msdn.microsoft.com/mds/2015/12/03/in-sql-server-2016-master-data-services-how-to-filter-domain-based-attribute-drop-down-lists/)(Filtrage des listes déroulantes d’attributs basés sur un domaine) sur le blog Master Data Services.  
  
12. **Ce paramètre est facultatif.** Sélectionnez **Activer le suivi des modifications** pour effectuer le suivi des modifications apportées aux groupes d'attributs. Pour plus d’informations, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Cliquez sur **Enregistrer**.  
  
## Voir aussi  
 [Attributs basés sur un domaine &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)   
 [Créer une hiérarchie dérivée &#40;Master Data Services&#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)   
 [Modifier le nom d’un attribut et un type de données &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Supprimer un attribut &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-master-data-services.md)  
  
  