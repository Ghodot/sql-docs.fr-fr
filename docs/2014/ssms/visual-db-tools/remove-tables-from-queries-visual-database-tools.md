---
title: Supprimer des tables des requêtes (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25d995d1049956652a326a3b759f272a5ecfc5e9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200609"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>Supprimer des tables des requêtes (Visual Database Tools)
  Vous pouvez supprimer une table, ou un objet table, dans une requête.  
  
> [!NOTE]  
>  Lorsque vous procédez à la suppression d'une table ou d'un objet table, cette suppression ne s'effectue que dans la requête en cours et non dans la base de données. Pour plus d’informations sur la suppression d’une table à partir d’une base de données, consultez [supprimer les Tables &#40;moteur de base de données&#41;](../../relational-databases/tables/delete-tables-database-engine.md).  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>Pour supprimer une table ou un objet structuré comme une table  
  
-   Dans le **volet Schéma**, sélectionnez la table, la vue, la fonction définie par l’utilisateur, le synonyme ou la requête, puis appuyez sur la touche Suppr ou cliquez avec le bouton droit sur l’objet et sélectionnez **Supprimer** dans la boîte de dialogue qui s’affiche. Vous pouvez sélectionner et supprimer plusieurs objets à la fois.  
  
     - ou -  
  
-   Supprimez toutes les références à l’objet dans le **volet SQL**.  
  
 Quand vous supprimez une table ou un objet table, le Concepteur de requêtes et de vues supprime automatiquement les jointures relatives à cette table ou à cet objet table, ainsi que les références aux colonnes de l’objet dans le **volet SQL** et le **volet Critères**. Si la requête comporte toutefois des expressions complexes relatives à l'objet, la suppression automatique de cet objet ne s'effectue pas tant que toutes les références le concernant n'ont pas été supprimées.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des Tables à des requêtes &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Créer des alias de Table &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md)   
 [Spécifiez les critères de recherche &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Résumer les résultats de la requête &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Effectuer des opérations de base concernant les requêtes &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
