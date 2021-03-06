---
title: sp_describe_cursor_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_columns
- sp_describe_cursor_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_columns
ms.assetid: 6eaa54af-7ba4-4fce-bf6c-6ac67cc1ac94
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a02701d091f2294af34450d3e370022a32cc143
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036232"
---
# <a name="spdescribecursorcolumns-transact-sql"></a>sp_describe_cursor_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit un rapport des attributs des colonnes contenues dans le jeu de résultats d'un curseur côté serveur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_describe_cursor_columns   
   [ @cursor_return = ] output_cursor_variable OUTPUT   
    { [ , [ @cursor_source = ] N'local' ,   
          [ @cursor_identity = ] N'local_cursor_name' ]   
    | [ , [ @cursor_source = ] N'global' ,   
          [ @cursor_identity = ] N'global_cursor_name' ]   
    | [ , [ @cursor_source = ] N'variable' ,   
          [ @cursor_identity = ] N'input_cursor_variable' ]   
   }  
```  
  
## <a name="arguments"></a>Arguments  
 [ @cursor_return=] *variable_de_curseur_sortie* sortie  
 Nom d'une variable de curseur déclarée devant recevoir la sortie du curseur. *variable_de_curseur_sortie* est **curseur**, sans valeur par défaut et doit ne pas être associé à des curseurs au moment de la procédure sp_describe_cursor_columns est appelée. Le curseur retourné est un curseur en lecture seule, dynamique et permettant les défilements.  
  
 [ @cursor_source=] {Ne local ' | Ne global ' | Ne variable '}  
 Indique si le curseur qui fait l'objet du rapport est défini en utilisant le nom d'un curseur local, d'un curseur global ou d'une variable de curseur. Le paramètre est **nvarchar (30)**.  
  
 [ @cursor_identity=] N'*nom_de_curseur_local*'  
 Nom d'un curseur créé par une instruction DECLARE CURSOR contenant soit le mot clé LOCAL, soit celui défini par défaut pour LOCAL. *nom_de_curseur_local* est **nvarchar (128)**.  
  
 [ @cursor_identity=] N'*ne nom_de_curseur_global*'  
 Est le nom d’un curseur créé par une instruction DECLARE CURSOR contenant soit le mot clé GLOBAL soit celui défini par défaut pour GLOBAL. *ne nom_de_curseur_global* est **nvarchar (128)**.  
  
 *ne nom_de_curseur_global* peut également être le nom d’un curseur de serveur d’API qui est ouvert par une application ODBC puis nommé en appelant SQLSetCursorName.  
  
 [ @cursor_identity=] N'*ne variable_de_curseur_entrée*'  
 Nom d'une variable de curseur associée à un curseur ouvert. *Ne variable_de_curseur_entrée* est **nvarchar (128)**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 None  
  
## <a name="cursors-returned"></a>Curseurs retournés  
 sp_describe_cursor_columns encapsule son rapport sous la forme un [!INCLUDE[tsql](../../includes/tsql-md.md)] **curseur** paramètre de sortie. Cela permet aux lots, procédures stockées et déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)] de travailler sur une seule ligne de sortie à la fois. Cela signifie également que la procédure ne peut pas être appelée directement à partir de fonctions d’API de base de données. Le **curseur** paramètre de sortie doit être lié à une variable de programme, mais l’API de base de données ne prennent pas en charge la liaison **curseur** variables ou des paramètres.  
  
 Vous trouverez dans le tableau suivant une présentation du format de curseur renvoyé par sp_describe_cursor_columns.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|column_name|**sysname** (null)|Nom attribué à la colonne du jeu de résultats. La colonne est NULL si elle a été spécifiée sans être accompagnée de la clause AS.|  
|ordinal_position|**Int**|Position relative de la colonne par rapport à la colonne la plus à gauche du jeu de résultats. La première colonne est à la position 0.|  
|column_characteristics_flags|**Int**|Masque de bits indiquant les informations stockées dans DBCOLUMNFLAGS dans OLE DB. Il peut s'agir d'un des éléments suivants ou d'une combinaison de ceux-ci :<br /><br /> 1 = Signet<br /><br /> 2 = Longueur fixe<br /><br /> 4 = Pouvant être Null<br /><br /> 8 = Contrôle de version de ligne<br /><br /> 16 = Colonne pouvant être mise à jour (définie dans le cas de colonnes projetées d'un curseur n'ayant pas de clause FOR UPDATE. Si une colonne de ce type existe, il ne peut y en avoir qu'une par curseur).<br /><br /> Lorsque les valeurs binaires sont combinées, les caractéristiques des valeurs binaires combinées s'appliquent. Par exemple, si la valeur binaire est égale à 6, la colonne est de longueur fixe (2) et accepte les valeurs NULL (4).|  
|column_size|**Int**|Taille maximale possible d'une valeur de cette colonne.|  
|data_type_sql|**smallint**|Numéro indiquant le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la colonne.|  
|column_precision|**tinyint**|Précision maximale de la colonne en tant que par le *bPrecision* valeur dans OLE DB.|  
|column_scale|**tinyint**|Nombre de chiffres à droite de la virgule décimale pour la **numérique** ou **décimal** des types de données en tant que par le *bScale* valeur dans OLE DB.|  
|order_position|**Int**|Position de la colonne dans la clé d'ordre relative à la colonne la plus à gauche si la colonne prend part à la définition de l'ordre du jeu de résultats.|  
|order_direction|**varchar (1)**(null)|A = La colonne fait partie de la clé d'ordre et l'ordre est croissant.<br /><br /> D = La colonne fait partie de la clé d'ordre et l'ordre est décroissant.<br /><br /> NULL = La colonne ne fait pas partie de la clé d'ordre.|  
|hidden_column|**smallint**|0 = Cette colonne apparaît dans la liste de sélection.<br /><br /> 1 = Réservé pour un usage ultérieur.|  
|columnid|**Int**|Identification de la colonne de base. Si la colonne de l'ensemble de résultats a été créée à partir d'une expression, columnid est égal à -1.|  
|objectid|**Int**|ID d'objet de l'objet ou de la table de base qui fournit la colonne. Si la colonne de l'ensemble de résultats a été créée à partir d'une expression, objectid est égal à -1.|  
|dbid|**Int**|ID de la base de données contenant la table de base qui fournit la colonne. Si la colonne de l'ensemble de résultats a été créée à partir d'une expression, dbid est égal à -1.|  
|dbname|**sysname**<br /><br /> (accepte les valeurs NULL)|Nom de la base de données contenant la table de base qui fournit la colonne. Si la colonne de l'ensemble de résultats a été créée à partir d'une expression, dbname a la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 La procédure sp_describe_cursor_columns décrit les attributs des colonnes de l'ensemble de résultats d'un curseur de serveur, tels que le nom et le type de données de chaque curseur. Utilisez sp_describe_cursor pour obtenir une description des attributs globaux du curseur de serveur. Utilisez sp_describe_cursor_tables pour générer un rapport sur les tables de base référencées par le curseur. Pour obtenir un rapport sur les curseurs côté serveur [!INCLUDE[tsql](../../includes/tsql-md.md)] visibles pour la connexion, utilisez sp_cursor_list.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant ouvre un curseur global et utilise `sp_describe_cursor_columns` pour fournir un rapport sur colonnes utilisées dans le curseur.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person;  
GO  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_columns.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_columns into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_columns  
    @cursor_return = @Report OUTPUT  
    ,@cursor_source = N'global'   
    ,@cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_columns output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_columns.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs](../../relational-databases/cursors.md)   
 [CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [sp_describe_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [sp_cursor_list &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-tables-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
