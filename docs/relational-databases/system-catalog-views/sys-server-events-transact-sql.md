---
title: Sys.server_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_events_TSQL
- sys.server_events_TSQL
- server_events
- sys.server_events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_events catalog view
ms.assetid: 996f6c9b-6426-4847-95d9-6b77541422be
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 82996f4b08a9567769da56a925d199d4a477ace0
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43037322"
---
# <a name="sysserverevents-transact-sql"></a>sys.server_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne par événement pour lequel est activé un déclencheur DDL de niveau serveur ou une notification d'événement de niveau serveur. Les colonnes **object_id** et **type** identifient l’événement de serveur.  

  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de la notification d'événements de niveau serveur ou du déclencheur DDL de niveau serveur à activer.|  
|**type**|**Int**|Type de l'événement à l'origine de l'activation de la notification d'événement ou du déclencheur DDL.|  
|**type_desc**|**nvarchar(60)**|Description de l'événement à l'origine de l'activation du déclencheur DDL ou de la notification d'événement.|  
|**event_group_type**|**Int**|Groupe d'événements sur lequel le déclencheur ou la notification d'événements est créé(e), ou null si le déclencheur n'est pas créé sur un groupe d'événements.|  
|**event_group_type_desc**|**nvarchar(60)**|Description du groupe sur lequel la notification d’événements ou de déclencheur est créée, ou null si ne pas créé sur un groupe d’événements|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
