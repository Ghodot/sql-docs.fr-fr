---
title: sp_removedistpublisherdbreplication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sp_removedistpublisherdbreplication_TSQL
- sp_removedistpublisherdbreplication
helpviewer_keywords:
- sp_removedistpublisherdbreplication
ms.assetid: 9bfe002a-25b5-4226-bcfb-feb2060d6b4a
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a99244a59c0022ed92797fc8c5e10bd3bf3dae63
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022567"
---
# <a name="spremovedistpublisherdbreplication-transact-sql"></a>sp_removedistpublisherdbreplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime les métadonnées de publication appartenant à une publication spécifique sur le serveur de distribution. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_removedistpublisherdbreplication [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publisher=** ] **'***publisher***'**  
 Est le nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nom de la base de données de publication. *publisher_db* est **sysname** sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_removedistpublisherdbreplication** est utilisé par la réplication transactionnelle et d’instantané.  
  
 **sp_removedistpublisherdbreplication** est utilisé lorsqu’une base de données publiée doit être recréée sans supprimer également la base de données de distribution. Les métadonnées suivantes sont supprimées :  
  
-   Toutes les métadonnées de publication  
  
-   Les métadonnées de tous les articles appartenant à la publication  
  
-   Les métadonnées de tous les abonnements à la publication  
  
-   Les métadonnées de tous les travaux d'Agent de réplication appartenant à la publication  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe sur le serveur de distribution ou les membres de la **db_owner** du rôle fixe de base de données dans la base de données de distribution peuvent exécuter **sp_ removedistpublisherdbreplication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
