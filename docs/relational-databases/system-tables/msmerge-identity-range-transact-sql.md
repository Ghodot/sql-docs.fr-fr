---
title: MSmerge_identity_range (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bbd06dae4c34b2b5c77b81db64f9d12408539b01
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101227"
---
# <a name="msmergeidentityrange-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSmerge_identity_range** table est utilisée pour suivre les plages numériques affectées aux colonnes d’identité pour l’abonnement à des publications sur lesquels la réplication gère automatiquement ces affectations de plage. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Numéro d'identification unique d'un abonnement donné.|  
|**artid**|**uniqueidentifier**|Numéro d'identification unique de l'article donné.|  
|**range_begin**|**numeric(38)**|Valeur d'identité au début de la plage actuelle.|  
|**range_end**|**numeric(38)**|Valeur d'identité à la fin de la plage actuelle.|  
|**next_range_begin**|**numeric(38)**|Valeur d'identité au début de la plage suivante à affecter.|  
|**next_range_end**|**numeric(38)**|Valeur d'identité à la fin de la plage suivante à affecter.|  
|**is_pub_range**|**bit**|La valeur **1** si la plage d’identité est assignée à la publication.|  
|**max_used**|**numeric(38)**|Valeur d'identité maximale pouvant être affectée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
