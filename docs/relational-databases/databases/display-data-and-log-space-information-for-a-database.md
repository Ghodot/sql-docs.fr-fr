---
title: "Afficher les informations sur l’espace occupé par les données et par le journal d’une base de données | Microsoft Docs"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], space
- status information [SQL Server], space
- displaying space information
- disk space [SQL Server], displaying
- databases [SQL Server], space used
- viewing space information
- space allocation [SQL Server], displaying
- data space [SQL Server]
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81963fea993101e8483d8a00a45bf72e822bb1b1
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="display-data-and-log-space-information-for-a-database"></a>Afficher les informations sur l'espace occupé par les données et par le journal d'une base de données
  Cette rubrique explique comment afficher des informations sur l'espace occupé par les données et par le journal d'une base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  

  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 L’autorisation d’exécuter **sp_spaceused** est accordée au rôle **public** . Seuls les membres du rôle de base de données fixe **db_owner** peuvent spécifier le paramètre **@updateusage** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-display-data-and-log-space-information-for-a-database"></a>Pour afficher les informations sur l'espace occupé par les données et par le journal d'une base de données  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et développez-la.  
  
2.  Développez **Bases de données**.  
  
3.  Cliquez avec le bouton droit sur une base de données, pointez sur **Rapports**, sur **Rapports standard**, puis cliquez sur **Utilisation du disque**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-using-spspaceused"></a>Pour afficher les informations sur l'espace occupé par les données et par le journal d'une base de données à l'aide de sp_spaceused  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise la procédure stockée système [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) pour communiquer des informations sur l’espace disque pour la table `Vendor` et ses index.  
  
```tsql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabasefiles"></a>Pour afficher les informations sur l'espace occupé par les données et par le journal d'une base de données en interrogeant sys.database_files  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L’exemple suivant interroge l’affichage catalogue [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) pour retourner des informations spécifiques sur les fichiers de données et les fichiers journaux de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [Ajouter des fichiers de données ou journaux à une base de données](../../relational-databases/databases/add-data-or-log-files-to-a-database.md)   
 [Supprimer des fichiers de données ou des fichiers journaux d'une base de données](../../relational-databases/databases/delete-data-or-log-files-from-a-database.md)  
  
  
