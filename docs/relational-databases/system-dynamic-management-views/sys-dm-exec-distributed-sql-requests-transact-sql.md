---
title: Sys.dm_exec_distributed_sql_requests (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_SQL_REQUESTS_TSQL
- DM_EXEC_DISTRIBUTED_SQL_REQUESTS
dev_langs: TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_distributed_requests management view
- dm_exec_distributed_requests management view
ms.assetid: d065dc01-35d4-472f-9554-53ac41e7d104
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 922f2ce79dbabe3670b3488299a530b2a28e0cc2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecdistributedsqlrequests-transact-sql"></a>Sys.dm_exec_distributed_sql_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur toutes les distributions de requête SQL dans le cadre d’une étape SQL dans la requête.  Cette vue affiche les données pour les demandes de 1000 derniers ; demandes actives ont toujours des données présentes dans cette vue.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|execution_id et step_index composent la clé pour cette vue. Id numérique unique associé à la demande.|Consultez le code dans [sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)|  
|step_index|**int**|Index de cette distribution est la partie de l’étape de requête.|Consultez step_index dans [sys.dm_exec_distributed_request_steps &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|compute_node_id|**int**|Type de l’opération représentée par cette étape.|Consultez compute_node_id dans [sys.dm_exec_compute_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|Où l’étape s’exécute.|La valeur -1 pour les demandes qui s’exécutent dans l’étendue du nœud pas l’étendue de la distribution.|  
|status|**nvarchar(32)**|État de cette étape.|Active, annulé, terminé, échec, en file d’attente|  
|error_id|**nvarchar(36)**|Id unique de l’erreur associée à cette étape, le cas échéant|Consultez l’id de [sys.dm_exec_compute_node_errors &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md), La valeur NULL si aucune erreur ne s’est produite.|  
|start_time|**datetime**|Heure de début de l’exécution de l’étape|Inférieure ou égale à l’heure actuelle et supérieurs ou égaux à end_compile_time de la requête à laquelle appartient cette étape.|  
|end_time|**datetime**|Heure à laquelle cette étape exécution s’est terminée, a été annulée ou a échoué.|Inférieure ou égale à l’heure actuelle et supérieurs ou égaux à heure_début, la valeur NULL pour les étapes d’exécution ou en file d’attente.|  
|total_elapsed_time|**int**|Quantité totale de temps à qu'exécuter l’étape de requête, en millisecondes|Comprise entre 0 et la différence entre heure_fin et heure_début. 0 pour les étapes en attente.|  
|row_count|**bigint**|Nombre total de lignes modifiées ou retournée par cette demande|0 pour les étapes qui ne pas de modification ou de retourner des données, le nombre de lignes affectées dans le cas contraire. La valeur -1 pour obtenir des instructions DMS.|  
|spid|**int**|Id de session sur l’instance de SQL Server que l’exécution de la distribution des requêtes||  
|commande|nvarchar(4000)|Contient le texte intégral de la commande de cette étape.|Toute chaîne de requête valide pour une étape. Tronquée à 4000 caractères.|  
  
## <a name="see-also"></a>Voir aussi  
 [PolyBase, résolution des problèmes avec les vues de gestion dynamique](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  