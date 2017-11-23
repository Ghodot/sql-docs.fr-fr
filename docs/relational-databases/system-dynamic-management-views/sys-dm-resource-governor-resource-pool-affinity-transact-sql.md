---
title: Sys.dm_resource_governor_resource_pool_affinity (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_affinity_TSQL
- sys.dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_affinity
- sys.dm_resource_governor_resource_pool_affinity
ms.assetid: a197ec19-a2ba-44f5-a4f2-3eee33ebd77d
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5261a64154de7603e4925437cb89271466ec97ce
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmresourcegovernorresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Suit l'affinité du pool de ressources.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Nom de Colmn|Type de données| Description|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|ID du pool de ressources. N'accepte pas la valeur NULL.|  
|Processor_group|**smallint**|ID du groupe de processeur logique Windows. N'accepte pas la valeur NULL.|  
|Scheduler_mask|**bigint**|Masque binaire qui représente les planificateurs associés à ce pool. N'accepte pas la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 Les pools créés avec une affinité AUTO n'apparaîtront pas dans cette vue car elles n'ont pas d'affinité. Pour plus d’informations, consultez le [CREATE RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-resource-pool-transact-sql.md) et [ALTER RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-resource-pool-transact-sql.md) instructions.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  