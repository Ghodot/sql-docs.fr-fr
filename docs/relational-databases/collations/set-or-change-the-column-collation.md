---
title: "D&#233;finir ou modifier le classement des colonnes | Microsoft Docs"
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
  - "base de données tempdb [SQL Server], classements"
  - "classements [SQL Server], colonne"
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# D&#233;finir ou modifier le classement des colonnes
  Vous pouvez remplacer le classement de la base de données pour les données **char**, **varchar**, **text**, **nchar**, **nvarchar** et **ntext** en spécifiant un classement différent pour une colonne spécifique d’une table et en utilisant l’un des éléments suivants :  
  
-   Clause COLLATE de [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) et [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md). Par exemple :  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Utilisation de la propriété **Column.Collation** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).  
  
 Vous ne pouvez pas modifier le classement d'une colonne actuellement référencée par l'un des éléments suivants :  
  
-   une colonne calculée ;  
  
-   un index ;  
  
-   des statistiques de distribution, générées automatiquement ou à l'aide de l'instruction CREATE STATISTICS ;  
  
-   une contrainte CHECK ;  
  
-   une contrainte FOREIGN KEY.  
  
 Quand vous utilisez **tempdb**, la clause [COLLATE](../Topic/COLLATE%20\(Transact-SQL\).md) contient une option *database_default* pour spécifier qu’une colonne de table temporaire utilise, pour la connexion, le classement par défaut de la base de données utilisateur active à la place du classement de **tempdb**.  
  
## Classements et colonnes text  
 Vous pouvez insérer ou mettre à jour les valeurs d’une colonne **text** dont le classement est différent de la page de codes du classement par défaut de la base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit implicitement les valeurs en fonction du classement de la colonne.  
  
## Classements et tempdb  
 La base de données **tempdb** est créée à chaque démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et a le même classement par défaut que la base de données **model**. Il est en général identique au classement par défaut de l'instance. Si vous créez une base de données utilisateur et spécifiez un classement par défaut différent de **model**, la base de données utilisateur a un classement par défaut différent de **tempdb**. Toutes les procédures stockées ou tables temporaires sont créées et stockées dans **tempdb**. En d'autres termes, toutes les colonnes implicites des tables temporaires et toutes les constantes, variables et paramètres modifiables par défaut des procédures stockées temporaires ont d'autres classements que les objets comparables créés dans les tables et procédures stockées permanentes.  
  
 Ceci pourrait provoquer des problèmes de non-correspondance de classement entre les bases de données définies par l'utilisateur et les objets de base de données système. Par exemple, une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le classement Latin1_General_CS_AS et vous exécutez les instructions suivantes :  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 Dans ce système, la base de données **tempdb** utilise le classement Latin1_General_CS_AS avec la page de codes 1252, et `TestDB` et `TestPermTab.Col1` utilisent le classement `Estonian_CS_AS` avec la page de codes 1257. Par exemple :  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 Dans l’exemple précédent, la base de données **tempdb** utilise le classement Latin1_General_CS_AS, et `TestDB` et `TestTab.Col1` utilisent le classement `Estonian_CS_AS`. Par exemple :  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 Comme **tempdb** utilise le classement par défaut du serveur et que `TestPermTab.Col1` utilise un autre classement, SQL Server affiche l’erreur suivante : impossible de résoudre le conflit de classement entre « Latin1_General_100_CI_AS_KS_WS » et « Chinese_Simplified_Pinyin_100_CI_AS » dans l’opération égal à.  
  
 Pour éviter l'erreur, vous pouvez utiliser une des solutions suivantes :  
  
-   Spécifiez que la colonne de table temporaire utilise le classement par défaut de la base de données utilisateur à la place de **tempdb**. Cela permet à la table temporaire de fonctionner avec des tables formatées de la même manière dans différentes bases de données, si votre système l'exige.  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   Spécifiez le classement approprié pour la colonne `#TestTempTab` :  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## Voir aussi  
 [Définir ou modifier le classement du serveur](../../relational-databases/collations/set-or-change-the-server-collation.md)   
 [Définir ou modifier le classement de la base de données](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  