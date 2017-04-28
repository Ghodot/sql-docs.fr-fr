---
title: "Utilisation des tables temporelles avec contr&#244;le de version du syst&#232;me &#224; m&#233;moire optimis&#233;e | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 691d4f80-6754-43f5-8b43-d4facf08f6fc
caps.latest.revision: 12
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Utilisation des tables temporelles avec contr&#244;le de version du syst&#232;me &#224; m&#233;moire optimis&#233;e
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique décrit la façon dont l’utilisation d’une table temporelle avec contrôle de version du système à mémoire optimisée diffère de celle d’une table temporelle avec contrôle de version du système sur disque.  
  
> [!NOTE]  
>  L’utilisation de la technologie Temporal avec des tables optimisées en mémoire s’applique uniquement à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et ne s’applique pas à [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## Découverte des métadonnées  
 Pour découvrir les métadonnées relatives à une table temporelle avec version gérée par le système et optimisée en mémoire, vous devez combiner les informations de [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) et [sys.internal_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-tables-transact-sql.md). Une table temporelle avec contrôle de version du système est présentée en tant que parent_object_id de la table de l’historique en mémoire interne.  
  
 Cet exemple indique comment exécuter une requête sur ces tables et joindre ces dernières.  
  
```  
SELECT SCHEMA_NAME (T1.schema_id) as TemporalTableSchema  
   , OBJECT_NAME(IT.parent_object_id) as TemporalTableName  
   , T1.object_id as TemporalTableObjectId  
   , IT.Name as InternalHistoryStagingName   
   , SCHEMA_NAME (T2.schema_id) as HistoryTableSchema  
   , OBJECT_NAME (T1.history_table_id) as HistoryTableName   
FROM sys.internal_tables IT    
JOIN sys.tables T1   
   ON IT.parent_object_id = T1.object_id   
JOIN sys.tables T2   
   ON T1.history_table_id = T2.object_id   
WHERE T1.is_memory_optimized  = 1 AND T1.temporal_type = 2  
  
```  
  
## Modification de données  
 Les tables temporelles mémoire optimisées avec contrôle de version du système sont modifiables par le biais de procédures stockées compilées en mode natif, ce qui vous permet de convertir des tables mémoire optimisées non temporelles en tables avec contrôle de version du système et de conserver les procédures stockées en mode natif existantes.  
  
 Cet exemple indique la façon dont une table créée précédemment peut être modifiée dans un module compilé en mode natif.  
  
```  
CREATE PROCEDURE dbo.UpdateFXCurrencyPair  
   (   
       @ProviderID int  
     , @CurrencyID1 int  
     , @CurrencyID2 int  
     , @BidRate decimal(8,4)  
     , @AskRate decimal(8,4)   
   )   
WITH NATIVE_COMPILATION, SCHEMABINDING  
   , EXECUTE AS OWNER   
AS    
   BEGIN ATOMIC WITH   
   (TRANSACTION ISOLATION LEVEL = SNAPSHOT  , LANGUAGE = N'English')   
      UPDATE dbo.FXCurrencyPairs SET AskRate = @AskRate, BidRate  = @BidRate   
     WHERE ProviderID = @ProviderID AND CurrencyID1 = @CurrencyID1 AND CurrencyID2 = @CurrencyID2   
END   
GO ;  
  
```  
  
## Cet article vous a-t-il été utile ? Nous sommes à votre écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous tenons compte de vos commentaires pour améliorer le contenu de nos articles. Envoyez vos commentaires à l’adresse [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Working%20with%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page).  
  
## Voir aussi  
 [Tables temporelles à système par version avec tables optimisées en mémoire](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Création d’une table temporelle de contrôle de version du système à mémoire optimisée](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)   
 [Surveillance des tables temporelles avec contrôle de version du système à mémoire optimisée](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [Considérations relatives aux performances des tables temporelles optimisées en mémoire à version contrôlée par le système](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)   
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)   
 [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Gérer la rétention des données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  