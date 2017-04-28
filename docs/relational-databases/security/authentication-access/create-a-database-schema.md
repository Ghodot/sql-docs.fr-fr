---
title: "Cr&#233;er un sch&#233;ma de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.schemas.general.f1"
helpviewer_keywords: 
  - "création de schémas à l'aide de Management Studio"
  - "CREATE SCHEMA [Management Studio]"
  - "schémas de base de données"
  - "schémas [SQL Server], création"
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Cr&#233;er un sch&#233;ma de base de donn&#233;es
  Cette rubrique explique comment créer un schéma dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer un schéma, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Le nouveau schéma appartient à l'un des principaux de base de données suivants : utilisateur de base de données, rôle de base de données ou rôle d'application. Les objets créés dans un schéma appartiennent au propriétaire du schéma. La valeur **principal_id** de ces objets est NULL dans **sys.objects**. Il est possible de transférer la propriété des objets contenus dans le schéma à n'importe quel principal de base de données, mais le propriétaire du schéma conserve toujours l'autorisation CONTROL sur les objets dans le schéma.  
  
-   Lors de la création d'un objet de base de données, si vous spécifiez un principal de domaine valide (utilisateur ou groupe) comme propriétaire de l'objet, le principal du domaine est ajouté à la base de données en tant que schéma. Le nouveau schéma appartiendra à ce principal de domaine.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
  
-   Nécessite l'autorisation CREATE SCHEMA sur la base de données.  
  
-   Pour spécifier un autre utilisateur comme propriétaire du schéma à créer, l'appelant doit avoir l'autorisation IMPERSONATE sur cet utilisateur. Si un rôle de base de données est spécifié en tant que propriétaire, l'appelant doit disposer de l'un des éléments suivants : appartenance au rôle ou autorisation ALTER pour le rôle.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
##### Pour créer un schéma  
  
1.  Dans l'Explorateur d'objets, développez le dossier **Bases de données** .  
  
2.  Développez la base de données où créer le schéma de la base de données.  
  
3.  Cliquez avec le bouton droit sur le dossier **Sécurité**, pointez sur **Nouveau**, puis sélectionnez **Schéma**.  
  
4.  Dans la boîte de dialogue **Schéma - Nouveau**, sur la page **Général**, entrez un nom pour le nouveau schéma dans la zone **Nom du schéma**.  
  
5.  Dans la zone **Propriétaire du schéma** , entrez le nom d'un utilisateur de base de données ou d'un rôle propriétaire du schéma. Vous pouvez également cliquer sur **Rechercher** pour ouvrir la boîte de dialogue **Rechercher les rôles et les utilisateurs** .  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Options supplémentaires  
 La boîte de dialogue **Schéma - Nouveau** offre également des options sur deux pages supplémentaires : **Autorisations** et **Propriétés étendues**.  
  
-   La page **Autorisations** répertorie tous les éléments sécurisables possibles et les autorisations sur les éléments sécurisables qui peuvent être accordées à la connexion.  
  
-   La page **Propriétés étendues** vous permet d'ajouter des propriétés personnalisées aux utilisateurs de base de données.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour créer un schéma  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [CREATE SCHEMA &#40;Transact-SQL&#41;](../../../t-sql/statements/create-schema-transact-sql.md).  
  
  