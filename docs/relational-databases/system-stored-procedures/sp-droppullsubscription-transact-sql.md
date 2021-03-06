---
title: sp_droppullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73c7f78803805c03acef7e0c7055c60eab2b1924
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021112"
---
# <a name="spdroppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un abonnement à la base de données en cours de l'Abonné. Cette procédure stockée est exécutée sur la base de données d'abonnement par extraction de données (pull) de l'abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publisher=** ] **'***publisher***'**  
 Nom du serveur distant. *serveur de publication* est **sysname**, sans valeur par défaut. Si **tous les**, l’abonnement est supprimé sur tous les serveurs de publication.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nom de la base de données du serveur de publication. *publisher_db* est **sysname**, sans valeur par défaut. **tous les** signifie que toutes les bases de données de serveur de publication.  
  
 [  **@publication=** ] **'***publication***'**  
 Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut. Si **tous les**, l’abonnement est supprimé dans toutes les publications.  
  
 [  **@reserved=** ] *réservé*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_droppullsubscription** est utilisé dans la réplication d’instantané ou transactionnelle.  
  
 **sp_droppullsubscription** supprime la ligne correspondante dans le [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) table et l’Agent de distribution correspondant sur l’abonné. Si aucune ligne n’est pas dans [MSreplication_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md), elle supprime la table.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou l’utilisateur qui a créé l’abonnement par extraction peut exécuter **sp_droppullsubscription**. Le **db_owner** rôle de base de données fixe n’est en mesure d’exécuter **sp_droppullsubscription** si l’utilisateur qui a créé l’abonnement par extraction appartient à ce rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer un abonnement par extraction](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
