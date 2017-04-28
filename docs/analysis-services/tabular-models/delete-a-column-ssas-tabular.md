---
title: "Supprimer une colonne (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# Supprimer une colonne (SSAS Tabulaire)
  Cette rubrique explique comment supprimer une colonne d'une table de modèle tabulaire.  
  
## Supprimer une colonne de table de modèle  
  
> [!NOTE]  
>  La suppression d'une colonne d'une table de modèle ne supprime pas la colonne d'une définition de requête de partition. Si la colonne que vous supprimez fait partie d'une partition, vous devez supprimer manuellement la colonne de la définition de requête de partition. Si vous ne supprimez pas la colonne de la définition de requête de partition, la colonne sera interrogée et des données retournées, mais elles ne seront pas ajoutées la table de modèle pendant le traitement des opérations. Pour plus d’informations, consultez [Partitions &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### Pour supprimer une colonne de table de modèle  
  
-   Dans le générateur de modèles, dans la table qui contient la colonne à supprimer, cliquez avec le bouton droit sur la colonne, puis cliquez sur **Supprimer**.  
  
#### Pour supprimer une colonne de table de modèle à l'aide de la boîte de dialogue Propriétés de la table  
  
1.  Dans le générateur de modèles, cliquez sur la table qui contient la colonne à supprimer, cliquez sur le menu **Table**, puis sur **Propriétés de la table**.  
  
2.  Dans **Origine des noms de colonnes**, sélectionnez **Modèle** (*pour utiliser les noms de colonne de la table de modèle, si différents de la source*).  
  
3.  Dans la boîte de dialogue **Modifier les propriétés de la table**, dans la fenêtre d’aperçu de la table, décochez la colonne à supprimer, puis cliquez sur **OK**.  
  
## Voir aussi  
 [Ajouter des colonnes à une table &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [Partitions &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  