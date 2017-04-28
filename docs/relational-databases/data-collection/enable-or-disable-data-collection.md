---
title: "Activer ou d&#233;sactiver la collecte de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "collecteur de données [SQL Server], désactivation"
  - "collecteur de données [SQL Server], activation"
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Activer ou d&#233;sactiver la collecte de donn&#233;es
  Cette rubrique explique comment activer ou désactiver la collecte de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour activer ou désactiver la collecte de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l’appartenance au rôle de base de données fixe **dc_admin** ou **dc_operator** (avec l’autorisation EXECUTE) pour exécuter cette procédure.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour activer le collecteur de données  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** .  
  
2.  Cliquez avec le bouton droit sur **Collecte de données**, puis cliquez sur **Activer la collecte de données**.  
  
#### Pour désactiver le collecteur de données  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** .  
  
2.  Cliquez avec le bouton droit sur **Collecte de données**, puis sélectionnez **Désactiver la collecte de données**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour activer le collecteur de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_syscollector_enable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md) pour activer le collecteur de données.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### Pour désactiver le collecteur de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_syscollector_disable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql.md) pour désactiver le collecteur de données.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## Voir aussi  
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  