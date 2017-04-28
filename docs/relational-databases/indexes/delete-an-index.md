---
title: "Supprimer un index | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "suppression d'index"
  - "suppression d'index"
  - "élimination d'index"
  - "index [SQL Server], suppression"
  - "suppressions d'index [SQL Server]"
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Supprimer un index
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique explique comment supprimer un index dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer un index, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Les index résultant d'une contrainte PRIMARY KEY ou UNIQUE ne peuvent pas être supprimés au moyen de cette méthode. Dans ce cas, c'est la contrainte qui doit être supprimée. Pour supprimer la contrainte et l'index correspondant, utilisez [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) avec la clause DROP CONSTRAINT dans [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour plus d’informations, consultez [Delete Primary Keys](../../relational-databases/tables/delete-primary-keys.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite une autorisation ALTER sur la table ou la vue. L’autorisation est accordée par défaut au rôle serveur fixe **sysadmin** et aux rôles de base de données fixes **db_ddladmin** et **db_owner**.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour supprimer un index à l'aide de l'Explorateur d'objets  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez supprimer un index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Développez la table contenant l'index à supprimer.  
  
4.  Développez le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index à supprimer, puis sélectionnez **Supprimer**.  
  
6.  Dans la boîte de dialogue **Supprimer un objet** , vérifiez que l'index correct figure dans la grille **Objet à supprimer** , puis cliquez sur **OK**.  
  
#### Pour supprimer un index à l'aide du Concepteur de tables  
  
1.  Dans l'Explorateur d'objets, développez la base de données qui contient la table sur laquelle vous souhaitez supprimer un index.  
  
2.  Développez le dossier **Tables** .  
  
3.  Cliquez avec le bouton droit sur la table contenant l'index que vous souhaitez supprimer et cliquez sur Conception.  
  
4.  Dans le menu **Concepteur de tables**, cliquez sur **Index/Clés**.  
  
5.  Dans la boîte de dialogue **Index/Clés**, sélectionnez l’index que vous souhaitez supprimer.  
  
6.  Cliquez sur **Supprimer**.  
  
7.  Cliquez sur **Fermer**.  
  
8.  Dans le menu **Fichier**, sélectionnez **Enregistrer***nom_table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour supprimer un index  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md).  
  
  