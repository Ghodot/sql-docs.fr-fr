---
title: Mémoire optimisée vues de gestion dynamique de Table (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ccd82fed-1a3f-47de-85c4-1c9bdd80b027
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 546b7c3c09526a9068885bbc1fa3caca1be79f57
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43071271"
---
# <a name="memory-optimized-table-dynamic-management-views-transact-sql"></a>Vues de gestion dynamique des tables mémoire optimisées (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Ce qui suit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vues de gestion dynamique (DMV) sont utilisés avec l’OLTP en mémoire :  
  
 Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|||  
|-|-|   
|[sys.dm_db_xtp_checkpoint_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md)|[sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md)|
|[sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql.md)|[sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)| 
|[sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)|[sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)|
|[sys.dm_db_xtp_merge_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-merge-requests-transact-sql.md)|[sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)|
|[sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)|[sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)|  
|[sys.dm_db_xtp_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-transactions-transact-sql.md)|[sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md)|  
|[sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql.md)|[sys.dm_xtp_system_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-system-memory-consumers-transact-sql.md)|
|[sys.dm_xtp_transaction_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-transaction-stats-transact-sql.md)||

### <a name="object-catalog-views"></a>Affichages catalogue d'objets

Les affichages de catalogue d’objet suivants sont utilisés en particulier avec OLTP en mémoire.

|||  
|-|-|   
|[sys.hash_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md)|[sys.memory_optimized_tables_internal_attributes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-memory-optimized-tables-internal-attributes-transact-sql.md)|  

### <a name="internal-dmvs"></a>Vues de gestion dynamique internes

Il existe des vues DMV supplémentaires qui est destinées à un usage interne uniquement, et pour lequel nous ne fournit aucune documentation directe. Dans la zone de tables mémoire optimisées, vues de gestion dynamique non documentées sont les suivantes :

- Sys.dm_xtp_threads
- Sys.dm_xtp_transaction_recent_rows

