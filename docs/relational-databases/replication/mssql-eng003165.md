---
title: "MSSQL_ENG003165 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG003165 (erreur)"
ms.assetid: 707d33dd-644e-4cc9-ac51-dddd49031530
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG003165
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3165|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|La base de données « %ls » a été restaurée, cependant, une erreur a été rencontrée pendant la restauration/suppression de la réplication. La base de données est restée hors ligne. Consultez la rubrique MSSQL_ENG003165 dans la documentation en ligne de SQL Server.|  
  
## Explication  
 Cette erreur est déclenchée si un problème se produit lors de la restauration d'une sauvegarde d'un base de données répliquée :  
  
-   Si la sauvegarde est restaurée sur la même base de données et sur le même serveur sur laquelle elle a été effectuée, l'erreur indique que les paramètres de la réplication n'ont pas pu être restaurés correctement.  
  
-   Si la sauvegarde est restaurée sur une base de données ou un serveur différent, l'erreur indique que les paramètres de la réplication n'ont pas pu être supprimés correctement (par défaut, les paramètres de la réplication sont supprimés si la base de données ou le serveur est différent).  
  
 L’erreur résulte probablement d’une incompatibilité entre l’état de la base de données restaurée et une ou plusieurs bases de données système contenant des métadonnées de réplication : **msdb**, **master**, ou la base de données de distribution.  
  
## Action de l'utilisateur  
 Pour résoudre ce problème :  
  
1.  Exécutez ALTER DATABASE pour mettre en ligne la base de données, par exemple : `ALTER DATABASE AdventureWorks SET ONLINE`. Pour plus d’informations, consultez [ALTER DATABASE & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/alter-database-transact-sql.md). Si vous souhaitez conserver les paramètres de la réplication, passez à l'étape 2. Sinon, passez à l'étape 3.  
  
2.  Exécutez [sp_restoredbreplication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-restoredbreplication-transact-sql.md). Si cette procédure stockée s'exécute avec succès, la restauration est terminée. Dans le cas contraire, passez à l'étape 3.  
  
3.  Exécutez [sp_removedbreplication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) Pour supprimer tous les paramètres de réplication.  
  
     Reconfigurez la réplication si nécessaire. Si la topologie de réplication a fait l'objet d'un script comme il a été recommandé, utilisez des scripts pour reconfigurer la topologie.  
  
## Voir aussi  
 [Sauvegarde et restauration des bases de données SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Sauvegarder et restaurer des bases de données répliquées](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  