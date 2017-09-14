---
title: ALTER SERVER AUDIT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_AUDIT_TSQL
- ALTER SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
- ALTER SERVER AUDIT statement
ms.assetid: 63426d31-7a5c-4378-aa9e-afcf4f64ceb3
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d2522a2876165f8e18222f2268dad091a6ba342
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-audit--transact-sql"></a>ALTER SERVER AUDIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Modifie un objet d'audit du serveur à l'aide de la fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Pour plus d’informations, consultez [SQL Server Audit &#40moteur de base de données&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ALTER SERVER AUDIT audit_name  
{  
    [ TO { { FILE ( <file_options> [, ...n] ) } | APPLICATION_LOG | SECURITY_LOG } ]  
    [ WITH ( <audit_options> [ , ...n] ) ]   
    [ WHERE <predicate_expression> ]  
}  
| REMOVE WHERE  
| MODIFY NAME = new_audit_name  
[ ; ]  
  
<file_options>::=  
{  
      FILEPATH = 'os_file_path'   
    | MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED }   
    | MAX_ROLLOVER_FILES = { integer | UNLIMITED }   
    | MAX_FILES = integer   
    | RESERVE_DISK_SPACE = { ON | OFF }   
}  
  
<audit_options>::=  
{  
      QUEUE_DELAY = integer   
    | ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION }   
    | STATE = = { ON | OFF }   
}  
  
<predicate_expression>::=  
{  
    [NOT ] <predicate_factor>   
    [ { AND | OR } [NOT ] { <predicate_factor> } ]   
    [,...n ]  
}  
  
<predicate_factor>::=   
    event_field_name { = | < > | ! = | > | > = | < | < = } { number | ' string ' }  
```  
  
## <a name="arguments"></a>Arguments  
 TO { FILE | APPLICATION_LOG | SECURITY }  
 Détermine l'emplacement de la cible de l'audit. Les options sont un fichier binaire, le journal des applications Windows ou le journal de sécurité Windows.  
  
 FILEPATH **= '***os_file_path***'**  
 Chemin d'accès de la piste d'audit. Le nom de fichier est généré en fonction du nom d'audit et du GUID d'audit.  
  
 MAXSIZE  **=**  *max_size*  
 Taille maximale que peut atteindre le fichier d'audit. Le *max_size* valeur doit être un entier suivi **Mo**, **Go**, **to**, ou **illimité**. La taille minimale que vous pouvez spécifier pour *max_size* est 2 **Mo** et la valeur maximale est 2 147 483 647 **to**. Lorsque **illimité** est spécifié, le fichier augmente jusqu'à ce que le disque est plein. Spécification d’une valeur inférieure à 2 Mo génère MSG_MAXSIZE_TOO_SMALL l’erreur. La valeur par défaut est **illimité**.  
  
 MAX_ROLLOVER_FILES  **=**  *entier* | **illimité**  
 Spécifie le nombre maximal de fichiers à conserver dans le système de fichiers. Lorsque le paramètre MAX_ROLLOVER_FILES = 0, aucune limite n’est imposée quant au nombre de fichiers de substitution qui sont créés. La valeur par défaut est 0 : Le nombre maximal de fichiers qui peuvent être spécifiés est 2 147 483 647.  
  
 MAX_FILES =*entier*  
 Spécifie le nombre maximal de fichiers d'audit qui peuvent être créés. Ne sont pas reportées sur le premier fichier lorsque la limite est atteinte. Lorsque la limite MAX_FILES est atteinte, toute action qui entraîne la génération d’événements d’audit supplémentaires échoue avec une erreur.  
**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 RESERVE_DISK_SPACE  **=**  {ON | {OFF}  
 Cette option pré-alloue la valeur MAXSIZE au fichier sur le disque. S'applique uniquement si MAXSIZE n'est pas égal à UNLIMITED. La valeur par défaut est OFF.  
  
 QUEUE_DELAY  **=**  *entier*  
 Détermine la durée, en millisecondes, qui peut s'écouler avant que le traitement des actions d'audit soit forcé. Une valeur de 0 indique la remise synchrone. La valeur minimale du délai de requête définissable est 1000 (1 seconde), qui est la valeur par défaut. Le maximum est 2 147 483 647 (2 147 483,647 secondes ou 24 jours, 20 heures, 31 minutes, 23,647 secondes). Spécifiez un nombre non valide, déclenche l’erreur MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE  **=**  {CONTINUER | ARRÊT | FAIL_OPERATION}  
 Indique si l'instance qui écrit dans la cible doit échouer, continuer ou s'arrêter si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas écrire dans le journal d'audit.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les opérations continuent. Les enregistrements d'audit ne sont pas conservés. L’audit continue de se connecter les événements et reprend si le problème est résolu. En sélectionnant l’option Continuer permet à une activité non auditée susceptible d’enfreindre vos stratégies de sécurité. Utilisez cette option, lors de la poursuite de l’opération de le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est plus importante que la conservation d’un audit complet.  
  
SHUTDOWN  
Force l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’arrêter, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne parvient pas à écrire des données dans la cible d’audit pour une raison quelconque. La connexion exécutant le `ALTER` instruction doit avoir le `SHUTDOWN` autorisation dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le comportement d’arrêt persiste même si le `SHUTDOWN` autorisation est révoquée ultérieurement à partir de la connexion en cours d’exécution. Si l’utilisateur n’a pas cette autorisation, puis l’instruction échoue et l’audit n’est pas modifiée. Utilisez cette option si une défaillance de l'audit risque de compromettre la sécurité ou l'intégrité du système. Pour plus d’informations, consultez [arrêt](../../t-sql/language-elements/shutdown-transact-sql.md). 
  
 FAIL_OPERATION  
 Les actions de base de données échouent si elles entraînent des événements audités. Les actions qui n’entraînent pas les événements audités peuvent continuer, mais aucun événement audité ne peut se produire. L’audit continue de se connecter les événements et reprend si le problème est résolu. Utilisez cette option lorsqu'il est plus important de conserver un audit complet que de disposer d'un accès complet au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].   
  
 ÉTAT  **=**  {ON | {OFF}  
 Active ou désactive la collecte d'enregistrements d'audit. La modification de l'état d'un audit en cours d'exécution (de ON à OFF) crée une entrée d'audit signalant que l'audit a été arrêté et indiquant le principal qui a arrêté l'audit et l'heure d'arrêt de l'audit.  
  
 MODIFY NAME = *new_audit_name*  
 Modifie le nom de l'audit. Ne peut être utilisée avec aucune autre option.  
  
 predicate_expression  
 Spécifie l'expression de prédicat utilisée pour déterminer si un événement doit ou non être traité. Les expressions de prédicat sont limitées à 3 000 caractères, ce qui limite les arguments de chaîne.  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 event_field_name  
 Nom du champ d'événement qui identifie la source de prédicat. Les champs d’audit sont décrits dans [sys.fn_get_audit_file &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Tous les champs peuvent être audités sauf `file_name` et `audit_file_offset`.  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 nombre  
 Est de n’importe quel type numérique, y compris **décimal**. Le manque de mémoire physique ou un nombre trop grand pour être représenté sous forme d'entier 64 bits sont les seules limitations.  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ' string '  
 Chaîne ANSI ou Unicode, comme requis par la comparaison de prédicat. Aucune conversion implicite de type chaîne n'est effectuée pour les fonctions de comparaison de prédicat. La transmission d'un type incorrect provoque une erreur.  
 **S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="remarks"></a>Notes  
 Vous devez spécifier au moins l'une des clauses TO, WITH ou MODIFY NAME lorsque vous appelez ALTER AUDIT.  
  
 Vous devez définir l'état d'un audit sur l'option OFF pour apporter des modifications à un audit. Si ALTER AUDIT est exécuté lorsqu’un audit est activé avec des options autres que STATE = OFF, vous recevez un message d’erreur MSG_NEED_AUDIT_DISABLED.  
  
 Vous pouvez ajouter, modifier et supprimer des spécifications d'audit sans arrêter un audit.  
  
 Vous ne pouvez pas modifier le GUID d'un audit après sa création.  
  
## <a name="permissions"></a>Permissions  
 Pour créer, modifier ou supprimer un principal de l'audit du serveur, vous devez posséder l'autorisation ALTER ANY SERVER AUDIT ou CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-a-server-audit-name"></a>A. Modification du nom d'un audit du serveur  
 L'exemple suivant remplace le nom de l'audit du serveur `HIPPA_Audit` par `HIPAA_Audit_Old`.  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
MODIFY NAME = HIPAA_Audit_Old;  
GO  
ALTER SERVER AUDIT HIPAA_Audit_Old  
WITH (STATE = ON);  
GO  
```  
  
### <a name="b-changing-a-server-audit-target"></a>B. Modification de la cible d'un audit du serveur  
 L'exemple suivant attribue à l'audit du serveur nommé `HIPPA_Audit` un fichier comme cible.  
  
```  
USE master  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = OFF);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
TO FILE (FILEPATH ='\\SQLPROD_1\Audit\',  
          MAXSIZE = 1000 MB,  
          RESERVE_DISK_SPACE=OFF)  
WITH (QUEUE_DELAY = 1000,  
       ON_FAILURE = CONTINUE);  
GO  
ALTER SERVER AUDIT HIPAA_Audit  
WITH (STATE = ON);  
GO  
```  
  
### <a name="c-changing-a-server-audit-where-clause"></a>C. Modification d'une clause WHERE d'audit du serveur  
 L’exemple suivant modifie le where clause créée dans l’exemple C de [CREATE SERVER AUDIT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-server-audit-transact-sql.md). La nouvelle clause WHERE filtre pour l’événement défini par l’utilisateur 27.  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
WHERE user_defined_event_id = 27;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="d-removing-a-where-clause"></a>D. Suppression d'une clause WHERE  
 L'exemple suivant supprime une expression de prédicat de clause WHERE.  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
REMOVE WHERE;  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = ON);  
GO  
```  
  
### <a name="e-renaming-a-server-audit"></a>E. Modification du nom d’un audit du serveur  
 L'exemple suivant renomme l'audit de serveur `FilterForSensitiveData` en `AuditDataAccess`.  
  
```tsql  
ALTER SERVER AUDIT [FilterForSensitiveData] WITH (STATE = OFF)  
GO  
ALTER SERVER AUDIT [FilterForSensitiveData]  
MODIFY NAME = AuditDataAccess;  
GO  
ALTER SERVER AUDIT [AuditDataAccess] WITH (STATE = ON);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DROP SERVER AUDIT &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CRÉER une spécification d’AUDIT de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys.fn_get_audit_file &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [Sys.server_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys.server_file_audits &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [Sys.server_audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [Sys.server_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [Sys.Database audit_specifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [Sys.database_audit_specification_details &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [Sys.dm_server_audit_status &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [Sys.dm_audit_actions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [Créer un audit du serveur et une spécification d’audit du serveur](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
