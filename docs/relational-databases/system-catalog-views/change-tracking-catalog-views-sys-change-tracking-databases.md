---
title: Sys.change_tracking_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- change_tracking_databases
- sys.change_tracking_databases_TSQL
- sys.change_tracking_databases
- change_tracking_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.change_tracking_databases
- change tracking [SQL Server], sys.change_tracking_databases
ms.assetid: bb233baa-2991-4904-a0eb-3772b81121a4
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 17175249b5c07aaab5787fcfbf64b8e1f6330bb1
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43065392"
---
# <a name="change-tracking-catalog-views---syschangetrackingdatabases"></a>Modifiez les vues de catalogue de suivi - sys.change_tracking_databases
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque base de données pour laquelle le suivi des modifications est activé.  

|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|database_id|**Int**|ID de la base de données. Cet ID est unique dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_auto_cleanup_on|**bit**|Indique si les données de suivi des modifications sont nettoyées automatiquement à l'issue de la période de rétention configurée :<br /><br /> 0 = désactivé<br /><br /> 1 = on|  
|retention_period|**Int**|Si le nettoyage automatique est utilisé, la période de rétention spécifie la durée pendant laquelle les données de suivi des modifications sont conservées dans la base de données.|  
|retention_period_units_desc|**nvarchar(60)**|Spécifie la description de la période de rétention :<br /><br /> Minutes<br /><br /> Heures<br /><br /> Jours|  
|retention_period_units|**tinyint**|Unité de temps de la période de rétention :<br /><br /> 1 = Minutes<br /><br /> 2 = Heures<br /><br /> 3 = Jours|  
  
## <a name="permissions"></a>Permissions  
 Les vérifications d'autorisation effectuées pour sys.change_tracking_databases sont les mêmes que celles effectuées pour sys.databases. Si l'appelant de sys.change_tracking_databases n'est pas le propriétaire de la base de données, les autorisations minimales requises pour consulter la ligne correspondante sont des autorisations ALTER ANY DATABASE ou VIEW ANY DATABASE au niveau du serveur, ou encore l'autorisation CREATE DATABASE dans la base de données master ou la base de données active.  
  
## <a name="see-also"></a>Voir aussi  
 [Le suivi des modifications des affichages catalogue &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Suivi des modifications de données &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
