---
title: "Valider des membres spécifiques par rapport aux règles d’entreprise (Master Data Services) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5ca1beaf471a1adfb91ec4fa66c32e0bde3c6514
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>Valider des membres spécifiques par rapport aux règles d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], appliquez des règles d'entreprise sélectivement lorsque vous souhaitez mettre à jour ou valider des sous-ensembles de membres par rapport à des règles d'entreprise.  
  
> [!NOTE]  
>  Si vous souhaitez appliquer des règles d’entreprise à tous les membres dans une version d’un modèle, consultez [Validate a Version against Business Rules &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez au minimum disposer de l'autorisation **Mettre à jour** sur l'objet modèle auquel vous appliquez les règles d'entreprise.  
  
### <a name="to-apply-business-rules-selectively"></a>Pour appliquer des règles d'entreprise sélectivement  
  
1.  Dans la page d’accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , dans la liste déroulante **Modèle** , sélectionnez un modèle.  
  
2.  Dans la liste déroulante **Version** , sélectionnez une version.  
  
3.  Cliquez sur l’onglet **Explorateur** .  
  
4.  Dans la barre de menus, pointez sur **Entités** , puis cliquez sur le nom de l'entité qui contient les membres auxquels vous souhaitez appliquer les règles.  
  
5.  Cliquez sur **Appliquer les règles**. Les règles d'entreprise sont appliquées uniquement aux membres affichés dans la grille.  
  
## <a name="see-also"></a>Voir aussi  
 [Valider une Version par rapport aux règles d’entreprise &#40; Master Data Services &#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)   
 [Les règles d’entreprise &#40; Master Data Services &#41;](../master-data-services/business-rules-master-data-services.md)  
  
  