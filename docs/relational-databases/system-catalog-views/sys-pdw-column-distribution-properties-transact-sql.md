---
title: Sys.pdw_column_distribution_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 46b74f99-2e22-4dbd-872a-533fce0e239c
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f3c34825e8bdc8e1e1947575894596c3c1897ddb
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000951"
---
# <a name="syspdwcolumndistributionproperties-transact-sql"></a>Sys.pdw_column_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations de distribution pour les colonnes.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**Int**|ID de l’objet auquel appartient la colonne.||  
|**column_id**|**Int**|ID de la colonne.||  
|**distribution_ordinal**|**tinyint**|Ordinal (de base 1) au sein de l’ensemble de la distribution.|0 ne = pas d’une colonne de distribution. 1 = [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] est à l’aide de cette colonne pour distribuer la table parente.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
