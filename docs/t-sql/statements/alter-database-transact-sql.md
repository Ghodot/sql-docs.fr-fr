---
title: ALTER DATABASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/07/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_DATABASE_TSQL
- ALTER DATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- databases [SQL Server], modifying
- ALTER DATABASE statement
- databases [SQL Server], renaming
- renaming databases
- database modifications [SQL Server]
- ALTER DATABASE statement, syntax described
- database names [SQL Server], ALTER DATABASE
- modifying databases
- collations [SQL Server], modifying
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 15f8affd-8f39-4021-b092-0379fc6983da
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-current||=azuresqldb-mi-current||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 1256884f13a576580588e877dd490f0757bfba9e
ms.sourcegitcommit: aac654706b21f70962c7311f3b193000113d00d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "42802568"
---
# <a name="alter-database-transact-sql"></a>ALTER DATABASE (Transact-SQL) 

Modifie certaines options de configuration d’une base de données. 

Cet article fournit la syntaxe, les arguments, les notes, les autorisations et des exemples associés au produit SQL que vous choisissez.

Pour plus d’informations sur les conventions de la syntaxe, consultez [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). 

## <a name="click-a-product"></a>Cliquez sur un produit !

Dans la ligne suivante, cliquez sur le nom du produit qui vous intéresse. Le clic affiche un contenu différent ici dans cette page web, approprié pour le produit sur lequel vous cliquez.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]  
> ||||||  
> |---|---|---|---|---|  
> |**_\* SQL Server \*_** &nbsp;|[SQL Database<br />Logical Server](alter-database-transact-sql.md?view=azuresqldb-current)|[SQL Database<br />Managed Instance](alter-database-transact-sql.md?view=azuresqldb-mi-current)|[SQL Data<br />Warehouse](alter-database-transact-sql.md?view=azure-sqldw-latest)|[SQL Parallel<br />Data Warehouse](alter-database-transact-sql.md?view=aps-pdw-2016)|  

&nbsp;

# <a name="sql-server"></a>SQL Server

## <a name="overview"></a>Vue d'ensemble

Dans SQL Server, cette instruction modifie une base de données ou les fichiers et groupes de fichiers associés à la base de données. Ajoute ou supprime des fichiers et des groupes de fichiers d'une base de données, modifie ses attributs ou ses fichiers et groupes de fichiers, modifie le classement de la base de données et définit les options de la base de données. Les instantanés de base de données ne peuvent pas être modifiés. Pour modifier les options de base de données associées à la réplication, utilisez [sp_replicationdboption](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md).  
   
En raison de sa longueur, la syntaxe d’ALTER DATABASE est divisée en plusieurs articles.  

ALTER DATABASE  
Le présent article indique la syntaxe à utiliser et les informations associées pour modifier le nom et le classement d’une base de données.  
  
[Options de fichiers et de groupes de fichiers ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
Indique la syntaxe à utiliser et les informations associées pour ajouter et supprimer des fichiers et groupes de fichiers d’une base de données, et pour modifier les attributs des fichiers et groupes de fichiers.  
  
[Options ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
Indique la syntaxe à utiliser et les informations associées pour modifier les attributs d’une base de données à l’aide des options SET d’ALTER DATABASE.  
  
[Mise en miroir de bases de données ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)  
Indique la syntaxe et les informations associées des options SET d’ALTER DATABASE relatives à la mise en miroir de bases de données.  
  
[ALTER DATABASE SET HADR](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)  
Indique la syntaxe et les informations associées des options [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] d’ALTER DATABASE pour configurer une base de données secondaire sur un réplica secondaire d’un groupe de disponibilité Always On.  
  
[Niveau de compatibilité ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
Indique la syntaxe et les informations associées des options SET d’ALTER DATABASE relatives aux niveaux de compatibilité des bases de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- SQL Server Syntax  
ALTER DATABASE { database_name  | CURRENT }  
{  
    MODIFY NAME = new_database_name   
  | COLLATE collation_name  
  | <file_and_filegroup_options>  
  | SET <option_spec> [ ,...n ] [ WITH <termination> ] 
  | SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 | 90 }   
  
}  
[;]  
  
<file_and_filegroup_options>::=  
  <add_or_modify_files>::=  
  <filespec>::=   
  <add_or_modify_filegroups>::=  
  <filegroup_updatability_option>::=  
  
<option_spec>::=  
  <auto_option> ::=   
  <change_tracking_option> ::=  
  <cursor_option> ::=   
  <database_mirroring_option> ::=   
  <date_correlation_optimization_option> ::=  
  <db_encryption_option> ::=  
  <db_state_option> ::=  
  <db_update_option> ::=  
  <db_user_access_option> ::=  <delayed_durability_option> ::=  <external_access_option> ::=  
  <FILESTREAM_options> ::=  
  <HADR_options> ::=    
  <parameterization_option> ::=  
  <query_store_options> ::=  
  <recovery_option> ::=   
  <service_broker_option> ::=  
  <snapshot_option> ::=  
  <sql_option> ::=   
  <termination> ::=  
 
<compatibility_level>
   { 140 | 130 | 120 | 110 | 100 | 90 }   
```  
  
## <a name="arguments"></a>Arguments  
*database_name*  
Nom de la base de données à modifier.  
  
> [!NOTE]  
>  Cette option n'est pas disponible dans une base de données autonome.  
  
CURRENT  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Indique que la base de données actuelle en cours d'utilisation doit être modifiée.  
  
MODIFY NAME **=***new_database_name*  
Renomme la base de données avec le nom spécifié *nouveau_nom_base_de_données*.  
  
COLLATE *collation_name*  
Spécifie le classement par défaut de la base de données. *collation_name* peut être un nom de classement Windows ou SQL. S'il n'est pas spécifié, le classement par défaut de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera appliqué à la base de données.  
  
Lors de la création de bases de données autrement qu'avec le classement par défaut, les données dans la base de données respectent toujours le classement spécifié. Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quand vous créez une base de données autonome, les informations de catalogue interne sont conservées à l'aide du classement par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **Latin1_General_100_CI_AS_WS_KS_SC**.  
  
Pour plus d’informations sur les noms de classements Windows et SQL, voir [COLLATE](~/t-sql/statements/collations.md).  
  
**\<delayed_durability_option> ::=**  
**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Pour plus d’informations, voir [Options d’ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md) et [Contrôler la durabilité d’une transaction](../../relational-databases/logs/control-transaction-durability.md).  
  
**\<file_and_filegroup_options>::=**  
Pour plus d’informations, voir [Options de fichiers et de groupes de fichiers d’ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md).  
  
## <a name="remarks"></a>Notes   
Pour supprimer une base de données, utilisez [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
  
Pour diminuer la taille d'une base de données, utilisez [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
L'instruction ALTER DATABASE doit être exécutée en mode de validation automatique (mode de gestion des transactions par défaut) et n'est pas autorisée dans une transaction explicite ou implicite.  
  
L'état d'un fichier de base de données (par exemple, en ligne ou hors connexion) est préservé indépendamment de l'état de la base de données. Pour plus d’informations, consultez [États des fichiers](../../relational-databases/databases/file-states.md). L'état des fichiers dans un groupe de fichiers détermine la disponibilité de tout le groupe de fichiers. Pour qu'un groupe de fichiers soit disponible, tous ses fichiers doivent être en ligne. Si un groupe de fichiers est hors connexion, toute tentative d'accès au groupe par une instruction SQL échoue avec une erreur. Lorsque vous créez des plans de requête pour les instructions SELECT, l'optimiseur de requête évite les index non cluster et les vues indexées qui résident dans les groupes de fichiers hors connexion. Cela permet aux instructions de s'exécuter correctement. Cependant, si le groupe de fichiers hors connexion contient le segment ou l'index cluster d'une table cible, les instructions SELECT échouent. De plus, toute instruction INSERT, UPDATE ou DELETE modifiant une table assortie d'un index dans un groupe de fichiers hors connexion ne peut être exécutée.  
  
Lorsque l'état d'une base de données est RESTORING, les instructions ALTER DATABASE, pour la plupart, échouent. La définition des options de mise en miroir de bases de données fait exception. Une base de données peut être à l'état RESTORING durant une opération de restauration active, ou lorsqu'une opération de restauration d'un fichier de base de données ou d'un fichier journal échoue car un fichier de sauvegarde est corrompu.  
  
Le cache du plan pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est effacé par la définition de l'une des options suivantes :  
  
|||  
|-|-|  
|OFFLINE|READ_WRITE|  
|ONLINE|MODIFY FILEGROUP DEFAULT|  
|MODIFY_NAME|MODIFY FILEGROUP READ_WRITE|  
|COLLATE|MODIFY FILEGROUP READ_ONLY|  
|READ_ONLY|PAGE_VERIFY|  
  
Cette opération entraîne la recompilation de tous les plans d'exécution ultérieurs et peut entraîner une baisse temporaire et brutale des performances des requêtes. Pour chaque mémoire cache effacée dans le cache de plan, le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient le message d'information suivant : « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a rencontré %d occurrence(s) de vidages de mémoire cache pour la mémoire cache '%s' (partie du cache du plan) en raison d'opérations de maintenance ou de reconfiguration de base de données ». Ce message est enregistré toutes les cinq minutes si le cache est vidé au cours de cet intervalle de temps.  
  
Le cache de procédures est également vidé dans les scénarios suivants :  
  
- L'option de base de données AUTO_CLOSE est activée (ON). Lorsqu'aucune connexion utilisateur ne fait référence ou n'utilise la base de données, la tâche en arrière-plan essaie de fermer et d'arrêter la base de données automatiquement.  
- Vous exécutez plusieurs requêtes sur une base de données dont les options par défaut sont activées. Puis, la base de données est supprimée.  
- Un instantané de base de données pour une base de données source est supprimé.  
- Vous reconstruisez avec succès le journal des transactions d'une base de données.  
- Vous restaurez une sauvegarde de base de données.  
- Vous détachez une base de données.  
  
## <a name="changing-the-database-collation"></a>Modification du classement de la base de données  
Avant d'appliquer un autre classement à une base de données, veillez à ce que les conditions suivantes soient remplies :  
  
- Vous êtes actuellement le seul à utiliser la base de données.  
- Aucun objet lié à un schéma ne dépend du classement de la base de données.  
  
  Si les objets suivants, qui dépendent du classement de base de données, existent dans la base de données, l’instruction ALTER DATABASE*database_name*COLLATE échoue. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un message d'erreur pour chaque objet bloquant l'action ALTER :  
  
  - Fonctions et vues définies par l'utilisateur créées avec SCHEMABINDING  
  
  - Colonnes calculées  
  
  - Contraintes CHECK  
  
  - Fonctions table qui retournent des tables comportant des colonnes de type caractère avec des classements hérités du classement par défaut de la base de données  
  
    Les informations de dépendance des entités non liées au schéma sont mises à jour automatiquement lorsque le classement de la base de données est modifié.  
  
La modification du classement de la base de données ne crée pas de doublons parmi les noms système des objets de la base de données. Si cette modification entraîne la duplication de noms, les espaces de noms suivants peuvent faire échouer une modification du classement de la base de données :  
  
- Noms d'objets tels qu'une procédure, une table, un déclencheur ou une vue  
- Noms de schémas.  
- Principaux, tels qu'un groupe, un rôle ou un utilisateur  
- Noms de types scalaires, comme les types système ou définis par l'utilisateur  
- Noms de catalogues de texte intégral  
- Noms de colonnes ou de paramètres dans un objet  
- Noms d'index dans une table  
  
Les noms en double qui résultent du nouveau classement entraînent l'échec de l'action de modification et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un message d'erreur spécifiant l'espace de noms en cause.  
  
## <a name="viewing-database-information"></a>Affichage des informations de bases de données  
Vous pouvez utiliser les affichages catalogue, les fonctions système et les procédures stockées du système pour retourner des informations sur les bases de données, les fichiers et les groupes de fichiers.  
  
## <a name="permissions"></a>Permissions  
Nécessite l'autorisation ALTER sur la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-name-of-a-database"></a>A. Modification du nom d'une base de données  
L'exemple suivant modifie le nom de la base de données `AdventureWorks2012` en `Northwind`.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
### <a name="b-changing-the-collation-of-a-database"></a>B. Modification du classement d'une base de données  
L'exemple suivant crée une base de données nommée `testdb` qui utilise le classement `SQL_Latin1_General_CP1_CI_A`S, puis modifie le classement de la base de données `testdb` en `COLLATE French_CI_AI`.  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```sql  
USE master;  
GO  
  
CREATE DATABASE testdb  
COLLATE SQL_Latin1_General_CP1_CI_AS ;  
GO  
  
ALTER DATABASE testDB  
COLLATE French_CI_AI ;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
- [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
- [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
- [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
- [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
- [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
- [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
- [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
- [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
- [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
- [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
- [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
- [Bases de données système](../../relational-databases/databases/system-databases.md)  

::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="alter-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><strong><em>* SQL Database<br />de base de données SQL *</em></strong></th>
>   <th><a href="alter-database-transact-sql.md?view=azuresqldb-mi-current">SQL Database<br />Managed Instance</a></th>
>   <th><a href="alter-database-transact-sql.md?view=azure-sqldw-latest">SQL Data<br />Warehouse</a></th>
>   <th><a href="alter-database-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-database-logical-server"></a>Serveur logique Azure SQL Database

## <a name="overview"></a>Vue d'ensemble

Dans Azure SQL Database, utilisez cette instruction pour modifier une base de données sur un serveur logique : modifier son nom, son édition et son objectif de service, la joindre à un pool élastique ou l’en supprimer, définir ses options, l’ajouter ou la supprimer comme base de données secondaire dans une relation de géoréplication et définir son niveau de compatibilité.

En raison de sa longueur, la syntaxe d’ALTER DATABASE est divisée en plusieurs articles.  

ALTER DATABASE  
Le présent article indique la syntaxe à utiliser et les informations associées pour modifier le nom et le classement d’une base de données.  
  
[Options ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md?&tabs=sqldbls)  
Indique la syntaxe à utiliser et les informations associées pour modifier les attributs d’une base de données à l’aide des options SET d’ALTER DATABASE.  
  
[Niveau de compatibilité ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md?&tabs=sqldbls)  
Indique la syntaxe et les informations associées des options SET d’ALTER DATABASE relatives aux niveaux de compatibilité des bases de données.  

## <a name="syntax"></a>Syntaxe 

```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name | CURRENT }  
{  
    MODIFY NAME = new_database_name  
  | MODIFY ( <edition_options> [, ... n] ) 
  | SET { <option_spec> [ ,... n ] WITH <termination>} 
  | SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
  | ADD SECONDARY ON SERVER <partner_server_name>  
    [WITH ( <add-secondary-option>::= [, ... n] ) ]  
  | REMOVE SECONDARY ON SERVER <partner_server_name>  
  | FAILOVER  
  | FORCE_FAILOVER_ALLOW_DATA_LOSS  
}  
[;] 

<edition_options> ::= 
{  

  MAXSIZE = { 100 MB | 250 MB | 500 MB | 1 … 1024 … 4096 GB }  
  | EDITION = { 'basic' | 'standard' | 'premium' | 'GeneralPurpose' | 'BusinessCritical'} 
  | SERVICE_OBJECTIVE = 
       {  <service-objective>
       | { ELASTIC_POOL (name = <elastic_pool_name>) } 
       } 
}  

<add-secondary-option> ::=  
   {  
      ALLOW_CONNECTIONS = { ALL | NO }  
     | SERVICE_OBJECTIVE = 
       {  <service-objective> 
       | { ELASTIC_POOL ( name = <elastic_pool_name>) } 
       } 
   }  

<service-objective> ::=  { 'S0' | 'S1' | 'S2' | 'S3'| 'S4'| 'S6'| 'S7'| 'S9'| 'S12' |
       | 'P1' | 'P2' | 'P4'| 'P6' | 'P11'  | 'P15'
      | 'GP_GEN4_1' | 'GP_GEN4_2' | 'GP_GEN4_4' | 'GP_GEN4_8' | 'GP_GEN4_16' | 'GP_GEN4_24' |
      | 'BC_GEN4_1' | 'BC_GEN4_2' | 'BC_GEN4_4' | 'BC_GEN4_8' | 'BC_GEN4_16' | 'BC_GEN4_24' |
      | 'GP_GEN5_2' | 'GP_GEN5_4' | 'GP_GEN5_8' | 'GP_GEN5_16' | 'GP_GEN5_24' | 'GP_GEN5_32' | 'GP_GEN5_48' | 'GP_GEN5_80' |
      | 'BC_GEN5_2' | 'BC_GEN5_4' | 'BC_GEN5_8' | 'BC_GEN5_16' | 'BC_GEN5_24' | 'BC_GEN5_32' | 'BC_GEN5_48' | 'BC_GEN5_80' |
      }

<option_spec> ::= 
{  
    <auto_option> 
  | <change_tracking_option> 
  | <cursor_option> 
  | <db_encryption_option>  
  | <db_update_option> 
  | <db_user_access_option> 
  | <delayed_durability_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <snapshot_option>  
  | <sql_option> 
  | <target_recovery_time_option> 
  | <termination>  
  | <temporal_history_retention>  
}  
```
  
## <a name="arguments"></a>Arguments  

*database_name*  

Nom de la base de données à modifier.  
  
CURRENT  

Indique que la base de données actuelle en cours d'utilisation doit être modifiée.  
  
MODIFY NAME **=***new_database_name*  

Renomme la base de données avec le nom spécifié *nouveau_nom_base_de_données*. L’exemple suivant remplace le nom de la base de données `db1` par `db2` :   

```sql  
ALTER DATABASE db1  
    MODIFY Name = db2 ;  
```    

MODIFY (EDITION **=** ['basic' | 'standard' | 'premium' |'GeneralPurpose' | 'BusinessCritical'])    

Modifie le niveau de service de la base de données. 

L’exemple suivant remplace l’édition par `premium` :
  
```sql  
ALTER DATABASE current 
    MODIFY (EDITION = 'premium');
``` 

La modification d’EDITION échoue si la propriété MAXSIZE de la base de données a une valeur située en dehors de la plage valide prise en charge par cette édition.  

MODIFY (MAXSIZE **=** [100 MB | 500 MB | 1 | 1024…4096] GB)  

Spécifie la taille maximale de la base de données. La taille maximale doit être conforme au jeu de valeurs valide pour la propriété EDITION de la base de données. Le fait de modifier la taille maximale de la base de données peut entraîner la modification de la propriété EDITION de la base de données. Le tableau suivant contient la liste des valeurs de MAXSIZE prises en charge et des valeurs par défaut (D) des couches de service [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
**Modèle basé sur DTU**

|**MAXSIZE**|**De base**|**S0-S2**|**S3-S12**|**P1-P6**|**P11-P15**|  
|-----------------|---------------|------------------|-----------------|-----------------|-----------------|-----------------|  
|100 Mo|√|√|√|√|√|  
|250 Mo|√|√|√|√|√|  
|500 Mo|√|√|√|√|√|  
|1 Go|√|√|√|√|√|  
|2 Go|√ (D)|√|√|√|√|  
|5 Go|Néant|√|√|√|√|  
|10 GB|Néant|√|√|√|√|  
|20 Go|Néant|√|√|√|√|  
|30 Go|Néant|√|√|√|√|  
|40 Go|Néant|√|√|√|√|  
|50 Go|Néant|√|√|√|√|  
|100 Go|Néant|√|√|√|√|  
|150 Go|Néant|√|√|√|√|  
|200 Go|Néant|√|√|√|√|  
|250 Go|Néant|√ (D)|√ (D)|√|√|  
|300 Go|Néant|√|√|√|√|  
|400 Go|Néant|√|√|√|√|  
|500 Go|Néant|√|√|√ (D)|√|  
|750 Go|Néant|√|√|√|√|  
|1 024 Go|Néant|√|√|√|√ (D)|  
|À partir de 1 024 Go jusqu’à 4 096 Go par incréments de 256 Go*|Néant|Néant|Néant|Néant|√|√|  
  
\* P11 et P15 autorisent MAXSIZE jusqu’à 4 To, 1 024 Go étant la taille par défaut.  P11 et P15 peuvent utiliser jusqu’à 4 To de stockage inclus sans frais supplémentaires. Dans le niveau Premium, une taille supérieure à 1 To est actuellement disponible pour MAXSIZE dans les régions suivantes : Est des États-Unis2, États-Unis de l'Ouest, Gouvernement des États-Unis - Virginie, Europe de l’Ouest, Centre de l’Allemagne, Asie du Sud-Est, Japon de l'Est, Est de l’Australie, Centre du Canada et Est du Canada. Pour plus d’informations concernant les limitations des ressources pour le modèle basé sur DTU, consultez [Limites des ressources basées sur DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits).  

La valeur MAXSIZE pour le modèle basé sur DTU, si elle est spécifiée, doit être une valeur valide indiquée dans le tableau ci-dessus pour le niveau de service spécifié.
 
**Modèle basé sur vCore**

**Niveau de service Usage général - Plateforme de calcul de 4e génération**
|MAXSIZE|GP_Gen4_1|GP_Gen4_2|GP_Gen4_4|GP_Gen4_8|GP_Gen4_16|GP4_24|
|:--- | --: |--: |--: |--: |--: |--:|
|Taille maximale des données (Go)|1024|1024|1536|3072|4096|4096|

**Niveau de service Usage général - Plateforme de calcul de 5e génération**
|MAXSIZE|GP_Gen5_2|GP_Gen5_4|GP_Gen5_8|GP_Gen5_16|GP_Gen5_24|GP_Gen5_32|GP_Gen5_48|GP_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Taille maximale des données (Go)|1024|1024|1536|3072|4096|4096|4096|4096|


**Niveau de service Critique pour l’entreprise - Plateforme de calcul de 4e génération**
|Niveau de performance|BC_Gen4_1|BC_Gen4_2|BC_Gen4_4|BC_Gen4_8|BC_Gen4_16|
|:--- | --: |--: |--: |--: |--: |--: |
|Taille maximale des données (Go)|1024|1024|1024|1024|1024|1024|

**Niveau de service Critique pour l’entreprise - Plateforme de calcul de 5e génération**
|MAXSIZE|BC_Gen5_2|BC_Gen5_4|BC_Gen5_8|BC_Gen5_16|BC_Gen5_24|BC_Gen5_32|BC_Gen5_48|BC_Gen5_80|
|:----- | ------: |-------: |-------: |--------: |--------: |---------:|--------: |---------: |
|Taille maximale des données (Go)|1024|1024|1024|1024|2048|4096|4096|4096|

Si aucune valeur `MAXSIZE` n’est définie lors de l’utilisation du modèle vCore, la valeur par défaut est de 32 Go. Pour plus d’informations sur les limitations des ressources du modèle basé sur vCore, consultez [Limites des ressources basées sur vCore](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits).
  
Les règles suivantes s'appliquent aux arguments MAXSIZE et EDITION.  
  
- Si EDITION est spécifié, mais MAXSIZE n'est pas spécifié, la valeur par défaut de l'édition est utilisée. Par exemple, si EDITION est défini à Standard et que MAXSIZE n'est pas spécifié, MAXSIZE est automatiquement défini à 500 Mo.  
  
- Si MAXSIZE et EDITION ne sont pas spécifiés, la valeur de EDITION est définie sur Standard (S0), et celle de MAXSIZE sur 250 Go.  

MODIFY (SERVICE_OBJECTIVE = \<service-objective>)  

Spécifie le niveau de performances. L’exemple suivant modifie l’objectif de service d’une base de données Premium `P6` :
 
```sql  
ALTER DATABASE current 
    MODIFY (SERVICE_OBJECTIVE = 'P6');
```  

Spécifie le niveau de performances. Les valeurs disponibles pour l’objectif de service sont : `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `GP_GEN4_24`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`, `BC_GEN4_24`, `GP_Gen5_2`, `GP_Gen5_4`, `GP_Gen5_8`, `GP_Gen5_16`, `GP_Gen5_24`, `GP_Gen5_32`, `GP_Gen5_48`, `GP_Gen5_80`, `BC_Gen5_2`,  `BC_Gen5_4`, `BC_Gen5_8`, `BC_Gen5_16`, `BC_Gen5_24`, `BC_Gen5_32`, `BC_Gen5_48`, `BC_Gen5_80`.  

Pour plus d’informations sur les objectifs de service, ainsi que sur la taille, les éditions et les combinaisons d’objectifs de service, consultez [Niveaux de service et de performance d’Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/), [Limites des ressources basées sur DTU](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits) et [Limites des ressources basées sur vCore](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits). La prise en charge des objectifs de service PRS a été supprimée. Pour poser des questions, utilisez cet alias de messagerie : premium-rs@microsoft.com. 
  
MODIFY (SERVICE_OBJECTIVE = ELASTIC\_POOL (name = \<elastic_pool_name>)  

Pour ajouter une base de données existante à un pool élastique, définissez le SERVICE_OBJECTIVE de la base de données sur ELASTIC_POOL et fournissez le nom du pool élastique. Vous pouvez également utiliser cette option pour ajouter la base de données à un autre pool élastique du même serveur. Pour plus d’informations, consultez [Créer et gérer un pool élastique SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/). Pour supprimer une base de données d’un pool élastique, utilisez ALTER DATABASE pour définir le SERVICE_OBJECTIVE sur un niveau de performance de base de données.  

ADD SECONDARY ON SERVER \<partner_server_name>  

Crée une base de données secondaire de géoréplication de même nom sur un serveur partenaire, faisant ainsi de la base de données locale la base de données de géoréplication primaire, et commence à répliquer des données de manière asynchrone entre la base de données primaire et la nouvelle base de données secondaire. Si une base de données portant le même nom existe déjà dans la base de données secondaire, la commande échoue. La commande est exécutée sur la base de données MASTER, située sur le serveur qui héberge la base de données locale qui devient la base de données primaire.  
  
WITH ALLOW_CONNECTIONS { **ALL** | NO }  

Lorsque ALLOW_CONNECTIONS n’est pas spécifié, il est défini sur ALL par défaut. S’il est défini sur ALL, il s’agit d’une base de données en lecture seule qui autorise toutes les connexions disposant des autorisations nécessaires.  
  
WITH SERVICE_OBJECTIVE {  `S0`, `S1`, `S2`, `S3`, `S4`, `S6`, `S7`, `S9`, `S12`, `P1`, `P2`, `P4`, `P6`, `P11`, `P15`, `GP_GEN4_1`, `GP_GEN4_2`, `GP_GEN4_4`, `GP_GEN4_8`, `GP_GEN4_16`, `GP_GEN4_24`, `BC_GEN4_1` `BC_GEN4_2` `BC_GEN4_4` `BC_GEN4_8` `BC_GEN4_16`, `BC_GEN4_24`, `GP_Gen5_2`, `GP_Gen5_4`,    `GP_Gen5_8`,    `GP_Gen5_16`,   `GP_Gen5_24`,   `GP_Gen5_32`,   `GP_Gen5_48`,   `GP_Gen5_80`, `BC_Gen5_2`,  `BC_Gen5_4`,    `BC_Gen5_8`,    `BC_Gen5_16`,   `BC_Gen5_24`,   `BC_Gen5_32`,   `BC_Gen5_48`,   `BC_Gen5_80` }  

Quand SERVICE_OBJECTIVE n’est pas spécifié, la base de données secondaire est créée au même niveau de service que la base de données primaire. Quand SERVICE_OBJECTIVE est spécifié, la base de données secondaire est créée au niveau spécifié. Cette option prend en charge la création de bases de données secondaires géorépliquées avec des niveaux de service moins coûteux. Le SERVICE_OBJECTIVE spécifié doit appartenir à la même édition que la source. Par exemple, vous ne pouvez pas spécifier S0 si l’édition est Premium.  
  
ELASTIC_POOL (name = \<elastic_pool_name>)  

Quand ELASTIC_POOL n’est pas spécifié, la base de données secondaire n’est pas créée dans un pool élastique. Quand ELASTIC_POOL est spécifié, la base de données secondaire est créée dans le pool spécifié.  
  
> [!IMPORTANT]  
>  L’utilisateur qui exécute la commande ADD SECONDARY doit avoir le rôle de DBManager pour le serveur principal, appartenir au groupe db_owner de la base de données locale et avoir le rôle de DBManager pour le serveur secondaire.  
  
REMOVE SECONDARY ON SERVER  \<partner_server_name>  

Supprime la base de données secondaire géorépliquée spécifiée du serveur spécifié. La commande est exécutée sur la base de données MASTER, située sur le serveur qui héberge la base de données primaire.  
  
> [!IMPORTANT]  
>  L’utilisateur qui exécute la commande REMOVE SECONDARY doit avoir le rôle de DBManager pour le serveur principal.  
  
FAILOVER  

Promeut la base de données secondaire du partenariat de géoréplication sur laquelle est exécutée la commande, pour qu’elle devienne la base de données primaire et que la base de données primaire actuelle devienne secondaire. Dans le cadre de ce processus, le mode de géoréplication passe temporairement du mode asynchrone au mode synchrone. Pendant le processus de basculement :  
  
1.  La base de données primaire cesse d’accepter les nouvelles transactions.  
  
2.  Toutes les transactions en attente sont envoyées vers la base de données secondaire.  
  
3.  La base de données secondaire devient primaire, et commence la géoréplication asynchrone avec l’ancienne primaire/nouvelle secondaire.  
  
Cette séquence garantit qu’aucune perte de données ne se produit. Lorsque les rôles sont permutés, la période pendant laquelle les deux bases de données sont indisponibles est d’environ 0 à 25 secondes. Au total, l’opération prend environ une minute. Si la base de données primaire n’est pas disponible lorsque cette commande est émise, la commande échoue et un message d’erreur indique que la base de données primaire n’est pas disponible. Si le processus de basculement ne se termine pas et semble bloqué, vous pouvez utiliser la commande de basculement forcé et accepter la perte de données. Ensuite, si vous avez besoin de récupérer les données perdues, adressez-vous à l’équipe DevOps (CSS).  
  
> [!IMPORTANT]  
>  L’utilisateur qui exécute la commande FAILOVER doit avoir le rôle de DBManager pour le serveur principal et le serveur secondaire.  
  
FORCE_FAILOVER_ALLOW_DATA_LOSS  

Promeut la base de données secondaire du partenariat de géoréplication sur laquelle est exécutée la commande, pour qu’elle devienne la base de données primaire et que la base de données primaire actuelle devienne secondaire. Utilisez cette commande uniquement lorsque la base de données primaire actuelle n’est plus disponible. Elle ne doit être utilisée qu’en cas de récupération d’urgence, lorsque la restauration de la disponibilité est critique, et qu’une petite perte de données est acceptable.  
  
Pendant un basculement forcé :  
  
1. La base de données secondaire spécifiée devient immédiatement la base de données primaire et commence à accepter les nouvelles transactions.  
  
2. Lorsque la base de données primaire d’origine peut se reconnecter à la nouvelle base de données primaire, une sauvegarde incrémentielle est effectuée à partir de la base de données primaire d’origine et celle-ci devient la nouvelle base de données secondaire.  
  
3. Pour récupérer des données à partir de cette sauvegarde incrémentielle de l’ancienne base de données primaire, l’utilisateur s’adresse à l’équipe DevOps/CSS.  
  
4. S’il existe d’autres bases de données secondaires, celles-ci sont automatiquement reconfigurées pour devenir des bases de données secondaires de la nouvelle primaire. Ce processus est asynchrone et peut prendre un certain temps. Tant que la reconfiguration n’est pas terminée, les bases de données secondaires continuent d’être associées à l’ancienne base de données primaire.  
  
> [!IMPORTANT]  
>  L’utilisateur qui exécute la commande FORCE_FAILOVER_ALLOW_DATA_LOSS doit avoir le rôle de DBManager pour le serveur principal et le serveur secondaire.  
  
## <a name="remarks"></a>Notes   

Pour supprimer une base de données, utilisez [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
Pour diminuer la taille d'une base de données, utilisez [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
L'instruction ALTER DATABASE doit être exécutée en mode de validation automatique (mode de gestion des transactions par défaut) et n'est pas autorisée dans une transaction explicite ou implicite.  
  
Cette opération entraîne la recompilation de tous les plans d'exécution ultérieurs et peut entraîner une baisse temporaire et brutale des performances des requêtes. Pour chaque mémoire cache effacée dans le cache de plan, le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient le message d'information suivant : « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a rencontré %d occurrence(s) de vidages de mémoire cache pour la mémoire cache '%s' (partie du cache du plan) en raison d'opérations de maintenance ou de reconfiguration de base de données ». Ce message est enregistré toutes les cinq minutes si le cache est vidé au cours de cet intervalle de temps.  
  
Le cache de procédures est également vidé dans le scénario suivant : plusieurs requêtes sont exécutées sur une base de données qui a les options par défaut. Puis, la base de données est supprimée.    
  
## <a name="viewing-database-information"></a>Affichage des informations de bases de données  

Vous pouvez utiliser les affichages catalogue, les fonctions système et les procédures stockées du système pour retourner des informations sur les bases de données, les fichiers et les groupes de fichiers.  
  
## <a name="permissions"></a>Permissions  

Seule la connexion principale au niveau du serveur (créée par le processus de configuration) ou les membres du rôle de base de données `dbmanager` peuvent modifier une base de données.  
  
> [!IMPORTANT]  
>  Le propriétaire de la base de données ne peut pas modifier la base de données à moins d'être membre du rôle `dbmanager`.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-check-the-edition-options-and-change-them"></a>A. Vérifier et modifier les options d’édition :

```sql
SELECT Edition = DATABASEPROPERTYEX('db1', 'EDITION'),
        ServiceObjective = DATABASEPROPERTYEX('db1', 'ServiceObjective'),
        MaxSizeInBytes =  DATABASEPROPERTYEX('db1', 'MaxSizeInBytes');

ALTER DATABASE [db1] MODIFY (EDITION = 'Premium', MAXSIZE = 1024 GB, SERVICE_OBJECTIVE = 'P15');
```

### <a name="b-moving-a-database-to-a-different-elastic-pool"></a>B. Déplacer une base de données vers un autre pool élastique  

Déplace une base de données existante dans un pool nommé pool1 :  
  
```sql  
ALTER DATABASE db1   
MODIFY ( SERVICE_OBJECTIVE = ELASTIC_POOL ( name = pool1 ) ) ;  
```  
  
### <a name="c-add-a-geo-replication-secondary"></a>C. Ajouter une base de données secondaire de géoréplication  

Crée une base de données secondaire accessible en lecture db1 sur le serveur `secondaryserver`, qui est associée à la base de données db1 du serveur local.  
  
```sql  
ALTER DATABASE db1   
ADD SECONDARY ON SERVER secondaryserver   
WITH ( ALLOW_CONNECTIONS = ALL )  
```  
  
### <a name="d-remove-a-geo-replication-secondary"></a>D. Supprimer une base de données secondaire de géoréplication  
 
Supprime la base de données secondaire db1 du serveur `secondaryserver`.  
  
```sql  
ALTER DATABASE db1   
REMOVE SECONDARY ON SERVER testsecondaryserver   
```  
  
### <a name="e-failover-to-a-geo-replication-secondary"></a>E. Basculer vers une base de données secondaire de géoréplication  

Promeut la base de données secondaire db1 sur le serveur `secondaryserver` pour qu’elle devienne la nouvelle base de données primaire lorsqu’elle est exécutée sur le serveur `secondaryserver`.  
  
```sql  
ALTER DATABASE db1 FAILOVER  
```  
  
## <a name="see-also"></a>Voir aussi
  
[CREATE DATABASE - Azure SQL Database](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldbls)   
 [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
 [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Bases de données système](../../relational-databases/databases/system-databases.md)  

::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="alter-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="alter-database-transact-sql.md?view=azuresqldb-current">SQL Database<br />de base de données SQL</a></th>
>   <th><strong><em>* SQL Database<br />Managed Instance *</em></strong></th>
>   <th><a href="alter-database-transact-sql.md?view=azure-sqldw-latest">SQL Data<br />Warehouse</a></th>
>   <th><a href="alter-database-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-database-managed-instance"></a>Azure SQL Database Managed Instance

## <a name="overview"></a>Vue d'ensemble

Dans Azure SQL Database Managed Instance, utilisez cette instruction pour définir des options de base de données.

En raison de sa longueur, la syntaxe d’ALTER DATABASE est divisée en plusieurs articles.  

ALTER DATABASE  
Le présent article indique la syntaxe à utiliser et les informations associées pour définir des options de fichiers et de groupes de fichiers, des options de base de données et le niveau de compatibilité de la base de données.  
  
[Options de fichiers et de groupes de fichiers d’ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md?&tabs=sqldbmi) Indique la syntaxe à utiliser et les informations associées pour ajouter et supprimer des fichiers et groupes de fichiers d’une base de données, et pour modifier les attributs des fichiers et groupes de fichiers.  
  
[Options d’ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md?&tabs=sqldbmi) Indique la syntaxe à utiliser et les informations associées pour modifier les attributs d’une base de données à l’aide des options SET d’ALTER DATABASE.  
  
[Niveau de compatibilité ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md?&tabs=sqldbmi) Indique la syntaxe et les informations associées des options SET d’ALTER DATABASE relatives aux niveaux de compatibilité des bases de données.  

## <a name="syntax"></a>Syntaxe 

```  
-- Azure SQL Database Syntax  
ALTER DATABASE { database_name | CURRENT }  
{  
    <file_and_filegroup_options>  
  | SET <option_spec> [ ,...n ]  
  | SET COMPATIBILITY_LEVEL = { 140 | 130 | 120 | 110 | 100 }   
}  
[;] 

<file_and_filegroup_options>::=  
  <add_or_modify_files>::=  
  <filespec>::=   
  <add_or_modify_filegroups>::=  
  <filegroup_updatability_option>::=  

<option_spec> ::= 
{  
    <auto_option> 
  | <change_tracking_option> 
  | <cursor_option> 
  | <db_encryption_option>  
  | <db_update_option> 
  | <db_user_access_option> 
  | <delayed_durability_option>  
  | <parameterization_option>  
  | <query_store_options>  
  | <snapshot_option>  
  | <sql_option> 
  | <target_recovery_time_option> 
  | <temporal_history_retention>  
}  

```
  
## <a name="arguments"></a>Arguments  

*database_name*  

Nom de la base de données à modifier.  
  
CURRENT  

Indique que la base de données actuelle en cours d'utilisation doit être modifiée.  
  
## <a name="remarks"></a>Notes   

Pour supprimer une base de données, utilisez [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md).  
Pour diminuer la taille d'une base de données, utilisez [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
L'instruction ALTER DATABASE doit être exécutée en mode de validation automatique (mode de gestion des transactions par défaut) et n'est pas autorisée dans une transaction explicite ou implicite.  
  
Cette opération entraîne la recompilation de tous les plans d'exécution ultérieurs et peut entraîner une baisse temporaire et brutale des performances des requêtes. Pour chaque mémoire cache effacée dans le cache de plan, le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient le message d'information suivant : « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a rencontré %d occurrence(s) de vidages de mémoire cache pour la mémoire cache '%s' (partie du cache du plan) en raison d'opérations de maintenance ou de reconfiguration de base de données ». Ce message est enregistré toutes les cinq minutes si le cache est vidé au cours de cet intervalle de temps.  
  
Le cache de procédures est également vidé dans le scénario suivant : plusieurs requêtes sont exécutées sur une base de données qui a les options par défaut. Puis, la base de données est supprimée.    
  
## <a name="viewing-database-information"></a>Affichage des informations de bases de données  

Vous pouvez utiliser les affichages catalogue, les fonctions système et les procédures stockées du système pour retourner des informations sur les bases de données, les fichiers et les groupes de fichiers.  
  
## <a name="permissions"></a>Permissions  

Seule la connexion principale au niveau du serveur (créée par le processus de configuration) ou les membres du rôle de base de données `dbmanager` peuvent modifier une base de données.  
  
> [!IMPORTANT]  
>  Le propriétaire de la base de données ne peut pas modifier la base de données à moins d'être membre du rôle `dbmanager`.  
  
## <a name="examples"></a>Exemples
Les exemples suivants vous montrent comment définir le réglage automatique et comment ajouter un fichier dans une instance gérée.

```sql
ALTER DATABASE WideWorldImporters
    SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON)

ALTER DATABASE WideWorldImporters
    ADD FILE (NAME = 'data_17')
```

## <a name="see-also"></a>Voir aussi
  
[CREATE DATABASE - Azure SQL Database](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldbmi)   
[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)   
[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)   
[SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
[EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
[sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
[sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
[sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md) [sys.data_spaces](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
[sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
[sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
[Bases de données système](../../relational-databases/databases/system-databases.md)  

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="alter-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="alter-database-transact-sql.md?view=azuresqldb-current">SQL Database<br />de base de données SQL</a></th>
>   <th><a href="alter-database-transact-sql.md?view=azuresqldb-mi-current">SQL Database<br />Managed Instance</a></th>
>   <th><strong><em>* SQL Data<br />Warehouse *</em></strong></th>
>   <th><a href="alter-database-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-data-warehouse"></a>Azure SQL Data Warehouse

## <a name="overview"></a>Vue d'ensemble

Modifie le nom, la taille maximale ou l’objectif de service d’une base de données.

## <a name="syntax"></a>Syntaxe  
  
```  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 
            250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 
          | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 
          | 92160 | 102400 | 153600 | 204800 | 245760 
      } GB  
      | SERVICE_OBJECTIVE = { 
            'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' 
          | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' 
          | 'DW3000' | 'DW6000' | 'DW1000c' | 'DW1500c' | 'DW2000c' 
          | 'DW2500c' | 'DW3000c' | 'DW5000c' | 'DW6000c' | 'DW7500c' 
          | 'DW10000c' | 'DW15000c' | 'DW30000c'
      }  
```  
  
## <a name="arguments"></a>Arguments  
*database_name*  
Spécifie le nom de la base de données à modifier.  

MODIFY NAME = *nouveau_nom_base_de_données*  
Renomme la base de données avec le nom spécifié *nouveau_nom_base_de_données*.  
  
MAXSIZE  
La valeur par défaut est 245 760 Go (240 To).  

**S’applique à :** Niveau de performance Optimisé pour l’élasticité

Taille maximale autorisée pour la base de données. La base de données ne peut pas croître au-delà de MAXSIZE. 

**S’applique à :** Niveau de performance Optimisé pour le calcul

Taille maximale autorisée pour les données rowstore dans la base de données. Les données stockées dans les tables rowstore, dans un deltastore d’index columnstore ou un index non cluster sur un index columnstore cluster ne peuvent pas croître au-delà de MAXSIZE.  Les données compressées au format columnstore n’ont pas de taille limite et ne sont pas restreintes par MAXSIZE. 
  
SERVICE_OBJECTIVE  
Spécifie le niveau de performances. Pour plus d’informations sur les objectifs de service concernant [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], consultez [Niveaux de performance](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="permissions"></a>Permissions  
Nécessite ces autorisations :  
  
- Connexion au principal de niveau serveur (créée par le processus de provisionnement) ou  
- Membre du rôle de base de données `dbmanager`.  
  
Le propriétaire de la base de données ne peut pas modifier la base de données à moins d'être membre du rôle `dbmanager`.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
La base de données actuelle doit être différente de celle que vous modifiez, par conséquent **ALTER doit être exécuté tout en étant connecté à la base de données master**.  
  
SQL Data Warehouse est défini sur COMPATIBILITY_LEVEL 130 et ne peut pas être modifié. Pour plus d’informations, consultez [Meilleures performances des requêtes avec le niveau de compatibilité 130 dans Azure SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
Pour diminuer la taille d'une base de données, utilisez [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
Pour exécuter ALTER DATABASE, la base de données doit être en ligne et ne peut pas être dans un état suspendu.  
  
L’instruction ALTER DATABASE doit s’exécuter en mode de validation automatique, qui est le mode de gestion de transaction par défaut. Ce mode est défini dans les paramètres de connexion.  
  
L’instruction ALTER DATABASE ne peut pas faire partie d’une transaction définie par l’utilisateur.

Vous ne pouvez pas changer le classement de la base de données.  
  
## <a name="examples"></a>Exemples  
Avant d’exécuter ces exemples, vérifiez que la base de données que vous modifiez n’est pas la base de données actuelle. La base de données actuelle doit être différente de celle que vous modifiez, par conséquent **ALTER doit être exécuté tout en étant connecté à la base de données master**.  

### <a name="a-change-the-name-of-the-database"></a>A. Changer le nom de la base de données  

```sql  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>B. Changer la taille maximale de la base de données  
  
```sql  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>C. Changer le niveau de performance  
  
```sql  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>D. Changer la taille maximale et le niveau de performance  
  
```sql  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a> Voir aussi  
[CREATE DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqldw.md)
[Articles de référence pour SQL Data Warehouse](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-overview-reference/) 
 
::: moniker-end
::: moniker range="=aps-pdw-2016||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="alter-database-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="alter-database-transact-sql.md?view=azuresqldb-current">SQL Database<br />de base de données SQL</a></th>
>   <th><a href="alter-database-transact-sql.md?view=azuresqldb-mi-current">SQL Database<br />Managed Instance</a></th>
>   <th><a href="alter-database-transact-sql.md?view=azure-sqldw-latest">SQL Data<br />Warehouse</a></th>
>   <th><strong><em>* SQL Parallel<br />Data Warehouse *</em></strong></th>
> </tr>
> </table>

&nbsp;

# <a name="sql-parallel-data-warehouse"></a>SQL Parallel Data Warehouse

## <a name="overview"></a>Vue d'ensemble

Modifie les options de taille de base de données maximale pour les tables répliquées, les tables distribuées et le journal des transactions dans Parallel Data Warehouse. Cette instruction permet de gérer les allocations de l’espace disque à mesure que la taille d’une base de données augmente ou diminue. L’article décrit également la syntaxe relative à la définition des options de base de données dans Parallel Data Warehouse.

## <a name="syntax"></a>Syntaxe  
  
```  
-- Parallel Data Warehouse  
ALTER DATABASE database_name    
    SET ( <set_database_options>   | <db_encryption_option> )  
[;]  
  
<set_database_options> ::=   
{  
    AUTOGROW = { ON | OFF }  
    | REPLICATED_SIZE = size [GB]  
    | DISTRIBUTED_SIZE = size [GB]  
    | LOG_SIZE = size [GB]
    | SET AUTO_CREATE_STATISTICS { ON | OFF }
    | SET AUTO_UPDATE_STATISTICS { ON | OFF } 
    | SET AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF }
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
```  
  
## <a name="arguments"></a>Arguments  
*database_name*  
Nom de la base de données à modifier. Pour afficher une liste des bases de données sur l’appliance, utilisez [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
AUTOGROW = { ON | OFF }  
Met à jour l’option AUTOGROW. Quand AUTOGROW est défini sur ON, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] augmente automatiquement l’espace alloué pour les tables répliquées, les tables distribuées et le journal des transactions en fonction des besoins pour s’adapter à la croissance des besoins de stockage. Quand AUTOGROW est défini sur OFF, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] retourne une erreur si des tables, répliquées, des tables distribuées ou le journal des transactions dépasse le paramètre de taille maximale.  
  
REPLICATED_SIZE = *size* [GB]  
Spécifie le nouveau nombre maximal de gigaoctets par nœud de calcul pour le stockage de toutes les tables répliquées dans la base de données en cours de modification. Si vous planifiez l’espace de stockage de l’appliance, vous devez multiplier REPLICATED_SIZE par le nombre de nœuds de calcul dans l’appliance.  
  
DISTRIBUTED_SIZE = *size* [GB]  
Spécifie le nouveau nombre maximal de gigaoctets par base de données pour le stockage de toutes les tables distribuées dans la base de données en cours de modification. La taille est répartie entre tous les nœuds de calcul dans l’appliance.  
  
LOG_SIZE = *size* [GB]  
Spécifie le nouveau nombre maximal de gigaoctets par base de données pour le stockage de tous les journaux des transactions dans la base de données en cours de modification. La taille est répartie entre tous les nœuds de calcul dans l’appliance.  
  
ENCRYPTION { ON | OFF }  
Spécifie si la base de données doit être chiffrée (ON) ou non chiffrée (OFF). Le chiffrement peut être configuré uniquement pour [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] quand [sp_pdw_database_encryption](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md) a été défini sur **1**. Une clé de chiffrement de base de données doit être créée avant de pouvoir configurer le chiffrement transparent des données. Pour plus d’informations sur le chiffrement des bases de données, consultez [Chiffrement transparent des données &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  

SET AUTO_CREATE_STATISTICS { ON | OFF } Quand l’option de création automatique de statistiques AUTO_CREATE_STATISTICS est ON, l’optimiseur de requête crée les statistiques nécessaires sur les colonnes individuelles du prédicat de requête pour améliorer les estimations de cardinalité pour le plan de requête. Ces statistiques de colonne unique sont créées sur les colonnes où ne figure pas déjà un histogramme au niveau d'un objet de statistiques existant.

La valeur par défaut est ON pour les nouvelles bases de données créées après la mise à niveau vers AU7. La valeur par défaut est OFF pour les bases de données créées avant la mise à niveau. 

Pour plus d’informations sur les statistiques, consultez [Statistiques](../../relational-databases/statistics/statistics.md).

SET AUTO_UPDATE_STATISTICS { ON | OFF } Quand l’option de mise à jour automatique des statistiques AUTO_UPDATE_STATISTICS est ON, l’optimiseur de requête détermine si les statistiques sont obsolètes, puis les met à jour le cas échéant quand elles sont utilisées par une requête. Les statistiques deviennent obsolètes si des opérations d’insertion, de mise à jour, de suppression ou de fusion changent la distribution des données dans la table ou la vue indexée. L'optimiseur de requête détermine si les statistiques sont obsolètes en comptant le nombre de modifications de données depuis la dernière mise à jour des statistiques et en comparant le nombre de modifications à un seuil. Ce seuil est basé sur le nombre de lignes contenues dans la table ou la vue indexée.

La valeur par défaut est ON pour les nouvelles bases de données créées après la mise à niveau vers AU7. La valeur par défaut est OFF pour les bases de données créées avant la mise à niveau. 

Pour plus d’informations sur les statistiques, consultez [Statistiques](../../relational-databases/statistics/statistics.md).


SET AUTO_UPDATE_STATISTICS_ASYNC { ON | OFF } L’option de mise à jour asynchrone des statistiques, AUTO_UPDATE_STATISTICS_ASYNC, détermine si l’optimiseur de requête utilise des mises à jour de statistiques synchrones ou asynchrones. L’option AUTO_UPDATE_STATISTICS_ASYNC s’applique aux objets de statistiques créés pour les index, aux colonnes uniques contenues dans les prédicats de requête et aux statistiques créées à l’aide de l’instruction CREATE STATISTICS.

La valeur par défaut est ON pour les nouvelles bases de données créées après la mise à niveau vers AU7. La valeur par défaut est OFF pour les bases de données créées avant la mise à niveau. 

Pour plus d’informations sur les statistiques, consultez [Statistiques](/sql/relational-databases/statistics/statistics).

## <a name="permissions"></a>Permissions  
Nécessite l’autorisation ALTER sur la base de données.  
  
## <a name="error-messages"></a>Messages d'erreur
Si les statistiques automatiques sont désactivées et que vous essayez de modifier les paramètres des statistiques, PDW affiche l’erreur « Cette option n’est pas prise en charge dans PDW. » L’administrateur système peut activer les statistiques automatiques en activant le commutateur de fonctionnalité [AutoStatsEnabled](../../analytics-platform-system/appliance-feature-switch.md).

## <a name="general-remarks"></a>Remarques d'ordre général  
Les valeurs de REPLICATED_SIZE, DISTRIBUTED_SIZE et LOG_SIZE peuvent être supérieures, égales ou inférieures aux valeurs actuelles de la base de données.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
Les opérations d’augmentation et de réduction sont approximatives. Les tailles réelles obtenues peuvent varier en fonction des paramètres de taille.  
  
[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] n’exécute pas l’instruction ALTER DATABASE comme une opération atomique. Si l’instruction est interrompue pendant l’exécution, les modifications qui ont déjà eu lieu sont conservées.  

Les paramètres de statistiques fonctionnent uniquement si l’administrateur a activé les statistiques automatiques.  Si vous êtes un administrateur, utilisez le commutateur de fonctionnalité [AutoStatsEnabled](../../analytics-platform-system/appliance-feature-switch.md) pour activer ou désactiver les statistiques automatiques. 
  
## <a name="locking-behavior"></a>Comportement de verrouillage  
Prend un verrou partagé sur l’objet DATABASE. Vous ne pouvez pas modifier une base de données qui est en cours d’utilisation par un autre utilisateur pour une opération de lecture ou d’écriture. Cela inclut les sessions qui ont émis une instruction [USE](../language-elements/use-transact-sql.md) sur la base de données.  
  
## <a name="performance"></a>Performances  
La réduction de la taille d’une base de données peut prendre beaucoup de temps et consommer beaucoup de ressources système, en fonction de la taille des données réelles contenues dans la base de données et du volume de fragmentation sur le disque. Par exemple, la réduction de la taille d’une base de données peut prendre plusieurs heures ou plus.  
  
## <a name="determining-encryption-progress"></a>Détermination de la progression du chiffrement  
Pour déterminer la progression du chiffrement transparent des données de base de données sous la forme d’un pourcentage, utilisez la requête suivante :  
  
```sql  
WITH  
database_dek AS (  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id,  
        dek.encryption_state, dek.percent_complete,  
        dek.key_algorithm, dek.key_length, dek.encryptor_thumbprint,  
        type  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
    INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
        ON dek.database_id = node_db_map.database_id   
        AND dek.pdw_node_id = node_db_map.pdw_node_id  
    LEFT JOIN sys.pdw_database_mappings AS db_map  
        ON node_db_map .physical_name = db_map.physical_name  
    INNER JOIN sys.dm_pdw_nodes nodes  
        ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
),  
dek_percent_complete AS (  
    SELECT database_dek.database_id, AVG(database_dek.percent_complete) AS percent_complete  
    FROM database_dek  
    WHERE type = 'COMPUTE'  
    GROUP BY database_dek.database_id  
)  
SELECT DB_NAME( database_dek.database_id ) AS name,  
    database_dek.database_id,  
    ISNULL(  
       (SELECT TOP 1 dek_encryption_state.encryption_state  
        FROM database_dek AS dek_encryption_state  
        WHERE dek_encryption_state.database_id = database_dek.database_id  
        ORDER BY (CASE encryption_state  
            WHEN 3 THEN -1  
            ELSE encryption_state  
            END) DESC), 0)  
        AS encryption_state,  
dek_percent_complete.percent_complete,  
database_dek.key_algorithm, database_dek.key_length, database_dek.encryptor_thumbprint  
FROM database_dek  
INNER JOIN dek_percent_complete   
    ON dek_percent_complete.database_id = database_dek.database_id  
WHERE type = 'CONTROL';  
```  
  
Pour obtenir un exemple complet illustrant toutes les étapes de l’implémentation de TDE, consultez [Chiffrement transparent des données &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. Modification du paramètre AUTOGROW  
Définissez AUTOGROW sur ON pour la base de données `CustomerSales`.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>B. Modification du stockage maximal pour les tables répliquées  
L’exemple suivant définit la limite de stockage des tables répliquées sur 1 Go pour la base de données `CustomerSales`. Il s’agit de la limite de stockage par nœud de calcul.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>C. Modification du stockage maximal pour les tables distribuées  
 L’exemple suivant définit la limite de stockage des tables distribuées sur 1 000 GB (un téraoctet) pour la base de données `CustomerSales`. Il s’agit de la limite de stockage combiné sur l’ensemble de l’appliance pour tous les nœuds de calcul, et non pas la limite de stockage par nœud de calcul.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>D. Modification du stockage maximal pour le journal des transactions  
 L’exemple suivant met à jour la base de données `CustomerSales` pour avoir une taille maximale du journal de transactions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de 10 Go pour l’appliance.  
  
```sql  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  

### <a name="e-check-for-current-statistics-values"></a>E. Rechercher les valeurs des statistiques actuelles

La requête suivante retourne les valeurs des statistiques actuelles pour toutes les bases de données. La valeur 1 signifie que la fonctionnalité est activée, et 0 qu’elle est désactivée.

```sql
SELECT NAME,
    is_auto_create_stats_on,
    is_auto_update_stats_on,
    is_auto_update_stats_async_on
FROM sys.databases;
```
### <a name="f-enable-auto-create-and-auto-update-stats-for-a-database"></a>F. Activer les statistiques de création automatique et de mise à jour automatique pour une base de données
Utilisez l’instruction suivante pour activer les statistiques de création et de mise à jour, de façon automatique et asynchrone, pour la base de données CustomerSales.  Cette opération crée et met à jour, selon les besoins, des statistiques dans une seule colonne pour créer des plans de requête de haute qualité.

```sql
ALTER DATABASE CustomerSales
    SET AUTO_CREATE_STATISTICS ON;
ALTER DATABASE CustomerSales
    SET AUTO_UPDATE_STATISTICS ON; 
ALTER DATABASE CustomerSales
    SET AUTO_UPDATE_STATISTICS_ASYNC ON;
```
  
## <a name="see-also"></a> Voir aussi  
 [CREATE DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlpdw)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  

::: moniker-end
