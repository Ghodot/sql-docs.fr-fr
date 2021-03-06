---
title: sp_help_log_shipping_monitor_primary (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_primary
- sp_help_log_shipping_monitor_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor_primary
ms.assetid: d9dfcb8f-1da6-49ca-a2c8-411574915434
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07b8769d1c466b9f70f0a84cfab53dea518227c2
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43029280"
---
# <a name="sphelplogshippingmonitorprimary-transact-sql"></a>sp_help_log_shipping_monitor_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur une base de données primaire à partir des tables du moniteur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_log_shipping_monitor_primary  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@primary_server =** ] '*primary_server*'  
 Le nom de l’instance principale de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dans la configuration d’envoi de journaux. *primary_server* est **sysname** et ne peut pas être NULL.  
  
 [  **@primary_database =** ] '*primary_database*'  
 Nom de la base de données sur le serveur principal. *primary_database* est **sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Description|  
|-----------------|-----------------|  
|**primary_id**|ID de la base de données primaire pour la configuration de la copie des journaux de transaction.|  
|**primary_server**|Le nom de l’instance principale de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dans la configuration d’envoi de journaux.|  
|**primary_database**|Nom de la base de données primaire dans la configuration d'envoi de journaux.|  
|**backup_threshold**|Le nombre de minutes qui peuvent s'écouler entre les opérations de sauvegarde avant le déclenchement d'une alerte.|  
|**threshold_alert**|Alerte à déclencher lorsque le seuil de sauvegarde est dépassé.|  
|**threshold_alert_enabled**|Détermine si les alertes du seuil de sauvegarde sont activées. 1 = activées ; 0 = désactivées.|  
|**last_backup_file**|Chemin d'accès absolu de la sauvegarde la plus récente des journaux de transactions.|  
|**last_backup_date**|Heure et date de la dernière opération de sauvegarde des journaux de transactions sur la base de données primaire.|  
|**last_backup_date_utc**|Date et heure de la dernière opération de sauvegarde des journaux de transactions sur la base de données primaire, exprimée en temps universel coordonné (UTC).|  
|**history_retention_period**|Durée de conservation (en minutes) avant suppression des enregistrements historiques de copie des journaux de transaction pour une base de données primaire donnée.|  
  
## <a name="remarks"></a>Notes  
 **sp_help_log_shipping_monitor_primary** doit être exécuté à partir de la **master** base de données sur le serveur moniteur.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
