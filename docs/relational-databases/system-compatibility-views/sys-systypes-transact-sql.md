---
title: Sys.systypes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.systypes_TSQL
- systypes_TSQL
- sys.systypes
- systypes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.systypes compatibility view
- systypes system table
ms.assetid: 1b0b1d0c-5f7b-470b-bd52-8bfa922d7889
caps.latest.revision: 50
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: edcf376f9127ec1d9b874c24e0a11f67f7e334ff
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074146"
---
# <a name="syssystypes-transact-sql"></a>sys.systypes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque type de données système et chaque type de données défini par l'utilisateur définis dans la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du type de données.|  
|**xtype**|**tinyint**|Type de stockage physique|  
|**status**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|Type d'utilisateur étendu Déborde ou retourne la valeur NULL si le nombre de types de données dépasse 32 767.|  
|**Longueur**|**smallint**|Longueur physique du type de données.|  
|**xprec**|**tinyint**|Précision interne, telle qu'utilisée par le serveur. À ne pas utiliser dans les requêtes.|  
|**XScale**|**tinyint**|Échelle interne, telle qu'utilisée par le serveur. À ne pas utiliser dans les requêtes.|  
|**tdefault**|**Int**|ID de la procédure stockée qui contient les contrôles d'intégrité de ce type de données.|  
|**Domaine**|**Int**|ID de la procédure stockée qui contient les contrôles d'intégrité de ce type de données.|  
|**uid**|**smallint**|ID de schéma du propriétaire du type.<br /><br /> Pour les bases de données mises à niveau à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'ID de schéma correspond à l'ID d'utilisateur du propriétaire.<br /><br /> **\*\* Important \* \***  si vous utilisez une des opérations suivantes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instructions DDL, vous devez utiliser le [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) affichage au lieu de catalogue **sys.systypes**.<br /><br /> ALTER AUTHORIZATION ON TYPE<br /><br /> CREATE TYPE<br /><br /> Déborde ou retourne la valeur NULL si le nombre d'utilisateurs et de rôles dépasse 32 767.|  
|**réservé**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**collationid**|**Int**|Si le caractère **collationid** est l’id du classement de la base de données actuelle ; sinon, sa valeur est NULL.|  
|**usertype**|**smallint**|ID de type d'utilisateur. Déborde ou retourne la valeur NULL si le nombre de types de données dépasse 32 767.|  
|**variable**|**bit**|Type de données de longueur variable.<br /><br /> 1 = True<br /><br /> 0 = False|  
|**AllowNulls**|**bit**|Détermine la possibilité de valeur NULL par défaut pour ce type de données. Cette valeur par défaut est remplacée par si la possibilité de valeur NULL est spécifiée à l’aide de [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) ou [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).|  
|**type**|**tinyint**|Type de données de stockage physique.|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**PREC**|**smallint**|Niveau de précision de ce type de données<br /><br /> -1 = **xml** ou types de valeur élevée.|  
|**Mise à l’échelle**|**tinyint**|Échelle de ce type de données, basée sur la précision.<br /><br /> NULL = le type de données est non numérique.|  
|**classement**|**sysname**|Si le caractère **classement** est le classement de la base de données actuelle ; sinon, sa valeur est NULL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
