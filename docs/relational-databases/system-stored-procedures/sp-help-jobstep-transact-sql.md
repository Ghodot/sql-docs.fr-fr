---
title: sp_help_jobstep (Transact-SQL) | Microsoft Docs
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
- sp_help_jobstep_TSQL
- sp_help_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobstep
ms.assetid: 4a13b804-45f2-4f82-987f-42d9a57dd6db
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e610198b2a7c26ad11811157b52a066639592a8
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396527"
---
# <a name="sphelpjobstep-transact-sql"></a>sp_help_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur les étapes d'un travail utilisé par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour procéder à des actions automatisées.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_jobstep { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]   
     [ , [ @step_name = ] 'step_name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id =**] **'***job_id***'**  
 Numéro d’identification pour lequel retourner des informations sur les travaux. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
 [  **@job_name =**] **'***nom_travail***'**  
 Nom du travail. *job_name* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [ **@step_id =**] *step_id*  
 Numéro d'identification de l'étape du travail. S'il n'est pas inclus, toutes les étapes du travail sont englobées. *l’argument id_étape* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@step_name =**] **'***nom_de_l***'**  
 Nom de l'étape du travail. *nom_de_l* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@suffix =**] *suffixe*  
 Un indicateur qui spécifie si une description de texte est ajoutée à la **indicateurs** colonne de sortie. *suffixe*est **bits**, avec la valeur par défaut de **0**. Si *suffixe* est **1**, une description est appliquée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**step_id**|**Int**|Identificateur unique de l'étape.|  
|**step_name**|**sysname**|Nom de l’étape du travail.|  
|**subsystem**|**nvarchar(40)**|Sous-système dans lequel la commande d'étape doit être exécutée.|  
|**commande**|**nvarchar(max)**|Commande exécutée dans l'étape.|  
|**flags**|**Int**|Masque de bits des valeurs qui contrôle le comportement de l'étape.|  
|**cmdexec_success_code**|**Int**|Pour un **CmdExec** étape, voici le code de sortie d’une commande réussie.|  
|**on_success_action**|**tinyint**|Action à effectuer si l'étape est exécutée correctement :<br /><br /> **1** = quitter le travail rapportant une réussite.<br /><br /> **2** = quitter le travail rapportant un échec.<br /><br /> **3** = passer à l’étape suivante.<br /><br /> **4** = passer à l’étape.|  
|**on_success_step_id**|**Int**|Si **on_success_action** 4, cela indique la prochaine étape à exécuter.|  
|**on_fail_action**|**tinyint**|Action à exécuter si l'étape échoue. Les valeurs sont les mêmes que **on_success_action**.|  
|**on_fail_step_id**|**Int**|Si **on_fail_action** 4, cela indique la prochaine étape à exécuter.|  
|**server**|**sysname**|Réservé.|  
|**database_name**|**sysname**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], c'est la base de données dans laquelle la commande est exécutée.|  
|**database_user_name**|**sysname**|Pour une étape [!INCLUDE[tsql](../../includes/tsql-md.md)], c'est le contexte de l'utilisateur de la base de données dans lequel la commande est exécutée.|  
|**retry_attempts**|**Int**|Nombre maximum de tentatives de la commande (en cas d'échecs).|  
|**retry_interval**|**Int**|Intervalle (en minutes) entre les tentatives.|  
|**os_run_priority**|**Int**|Réservé.|  
|**output_file_name**|**nvarchar(200)**|Fichier de commande de sortie doit être écrite ([!INCLUDE[tsql](../../includes/tsql-md.md)], **CmdExec**, et **PowerShell** étapes uniquement).|  
|**last_run_outcome**|**Int**|Résultat de l'étape lors de sa dernière exécution.<br /><br /> **0** = Échec<br /><br /> **1** = a réussi<br /><br /> **2** = nouvelle tentative<br /><br /> **3** = annulée<br /><br /> **5** = inconnu|  
|**last_run_duration**|**Int**|Durée (en secondes) de l'étape lors de sa dernière exécution.|  
|**last_run_retries**|**Int**|Nombre de tentatives de la commande lors de la dernière exécution de l'étape.|  
|**last_run_date**|**Int**|Date de début de la dernière exécution de l'étape.|  
|**last_run_time**|**Int**|Heure de début de la dernière exécution de l'étape.|  
|**proxy_id**|**Int**|Proxy pour les étapes du travail.|  
  
## <a name="remarks"></a>Notes  
 **sp_help_jobstep** est dans le **msdb** base de données.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer de l'un des rôles de base de données fixes suivants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans la base de données **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Pour en savoir plus sur les autorisations de ces rôles, consultez [Rôles de base de données fixes de l'Agent SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Membres de **SQLAgentUserRole** peuvent uniquement afficher les étapes de travail pour les travaux dont ils sont propriétaires.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-return-information-for-all-steps-in-a-specific-job"></a>A. Renvoi d'informations sur toutes les étapes d'un travail spécifique  
 L'exemple suivant renvoie toutes les étapes du travail intitulé `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-information-about-a-specific-job-step"></a>B. Renvoi d'informations sur une étape spécifique d'un travail  
 Cet exemple renvoie des informations sur la première étape du travail `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
