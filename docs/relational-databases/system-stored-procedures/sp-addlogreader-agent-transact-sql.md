---
title: sp_addlogreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addlogreader_agent
- sp_addlogreader_agent_TSQL
helpviewer_keywords:
- sp_addlogreader_agent
ms.assetid: d83096b9-96ee-4789-bde0-940d4765b9ed
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de60712c8ad865881e04c01c0a43bb5a46baee0b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017437"
---
# <a name="spaddlogreaderagent-transact-sql"></a>sp_addlogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un Agent de lecture du journal pour une base de données. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
> [!IMPORTANT]  
>  Lors de la configuration d'un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées en texte brut au serveur de distribution. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addlogreader_agent [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@job_login**=] **'***job_login***'**  
 Nom de connexion pour le [!INCLUDE[msCoName](../../includes/msconame-md.md)] du compte Windows sous lequel l’agent s’exécute. *job_login* est **nvarchar (257)**, avec NULL comme valeur par défaut. Ce compte Windows est toujours utilisé pour les connexions des agents au serveur de distribution.  
  
> [!NOTE]  
>  Pour les non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication, il doit être la même connexion que celui spécifiée dans [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
 [ **@job_password**=] **'***job_password***'**  
 Mot de passe du compte Windows sous lequel l'Agent s'exécute. *job_password* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour une sécurité optimale, les noms de connexion et les mots de passe doivent être fournis au moment de l'exécution.  
  
 [ **@job_name**=] **'***nom_travail***'**  
 Nom d'un travail de l'agent existant. *job_name* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre n'est défini que lorsque l'Agent est démarré avec un travail existant au lieu d'un nouveau travail (la valeur par défaut).  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 Mode de sécurité utilisé par l'agent lors de la connexion au serveur de publication. *publisher_security_mode* est **smallint**, avec une valeur par défaut **1**. **0** spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, et **1** Spécifie l’authentification Windows. La valeur **0** doit être spécifié pour les non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication.  
  
 [ **@publisher_login**=] **'***publisher_login***'**  
 Connexion au serveur de publication. *publisher_login* est **sysname**, avec NULL comme valeur par défaut. *publisher_login* doit être spécifié lorsque *publisher_security_mode* est **0**. Si *publisher_login* a la valeur NULL et *publisher_security_mode* est **1**, le compte Windows spécifié dans *job_login* sera utilisé lors de la connexion au serveur de publication.  
  
 [ **@publisher_password**=] **'***publisher_password***'**  
 Mot de passe utilisé lors de la connexion au serveur de publication. *publisher_password* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour une sécurité optimale, les noms de connexion et les mots de passe doivent être fournis au moment de l'exécution.  
  
 [ **@publisher**=] **'***publisher***'**  
 Est le nom de la non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Ne spécifiez pas ce paramètre pour un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addlogreader_agent** est utilisé dans la réplication transactionnelle.  
  
 Vous devez exécuter **sp_addlogreader_agent** pour ajouter un agent de lecture du journal si vous mettez à niveau une base de données qui a été activée pour la réplication vers cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant la création d’une publication qui a utilisé la base de données.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_addlogreader_agent**.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addlogreader-agent-tr_1.sql)]  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
