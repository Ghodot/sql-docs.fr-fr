---
title: Ajouter, modifier ou supprimer un paramètre de rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 9844fbe92d37a440bda6a165481e00de5a72c2d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37212529"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a>Ajouter, modifier ou supprimer un paramètre de rapport (Générateur de rapports et SSRS)
  Un paramètre de rapport permet de choisir les données du rapport, d'interconnecter les rapports associés et de varier la présentation du rapport concerné. Vous pouvez fournir une valeur par défaut et une liste de valeurs disponibles. De son côté, l'utilisateur peut modifier la sélection.  
  
 Après la publication d'un rapport, vous pouvez modifier les valeurs par défaut, les valeurs disponibles et d'autres propriétés d'un paramètre de rapport sur le serveur de rapports. Vous pouvez fournir plusieurs jeux de valeurs de paramètre par défaut en créant des rapports liés. Pour plus d’informations, consultez « Paramètre paramètre propriétés pour un rapport publié » dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation dans [la documentation en ligne de SQL Server](http://go.microsoft.com/fwlink/?linkid=120955).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a>Pour ajouter ou modifier un paramètre de rapport  
  
1.  Dans le volet **Données du rapport** , cliquez avec le bouton droit sur le nœud **Paramètres** , puis cliquez sur **Ajouter un paramètre**. La boîte de dialogue **Propriétés du paramètre de rapport** s'ouvre.  
  
2.  Dans **Nom**, tapez le nom du paramètre ou acceptez le nom par défaut.  
  
3.  Dans **Demander**, tapez le texte à afficher en regard de la zone de texte du paramètre lorsque l'utilisateur exécute le rapport.  
  
4.  Dans **Type de données**, sélectionnez le type de données pour la valeur du paramètre.  
  
5.  Si le paramètre peut contenir une valeur vide, sélectionnez **Autoriser une valeur vide**.  
  
6.  Si le paramètre peut contenir une valeur Null, sélectionnez **Autoriser les valeurs de type NULL**.  
  
7.  Pour autoriser un utilisateur à sélectionner plusieurs valeurs pour le paramètre, sélectionnez **Autoriser les valeurs multiples**.  
  
8.  Définissez l'option de visibilité.  
  
    -   Pour afficher le paramètre dans la barre d'outils en haut du rapport, sélectionnez **Visible**.  
  
    -   Pour masquer le paramètre afin qu'il n'affiche pas dans la barre d'outils, sélectionnez **Masqué**.  
  
    -   Pour masquer le paramètre et empêcher sa modification sur le serveur de rapports une fois le rapport publié, sélectionnez **Interne**. Le paramètre de rapport ne peut alors être affiché que dans la définition du rapport. Pour cette option, vous devez définir une valeur par défaut ou autoriser le paramètre à accepter une valeur nulle.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a>Pour supprimer un paramètre de rapport  
  
1.  Dans le volet **Données du rapport** , développez le nœud **Paramètres** .  
  
2.  Cliquez avec le bouton droit sur le paramètre de rapport, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter, modifier ou supprimer les valeurs disponibles pour un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)   
 [Ajouter, modifier ou supprimer les valeurs par défaut d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md)   
 [Modifier l’ordre d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Didacticiel : ajouter un paramètre à un rapport &#40;Générateur de rapports&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Didacticiels &#40;Générateur de rapports&#41;](../report-builder-tutorials.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Références à la collection Parameters&#40;Générateur de rapports et SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)   
 [Ajouter un paramètre à valeurs multiples à un rapport](add-a-multi-value-parameter-to-a-report.md)  
  
  
