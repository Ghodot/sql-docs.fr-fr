---
title: sp_deletemergeconflictrow (Transact-SQL) | Microsoft Docs
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
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords:
- sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c4290c07ddb9e7f352c6fe6177205ce6add03ead
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017392"
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime des lignes d’une table de conflits ou [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) table. Cette procédure stockée est exécutée dans n'importe quelle base de données de l'ordinateur sur lequel la table de conflits est stockée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@conflict_table=**] **'***conflict_table***'**  
 Nom de la table de conflits. *conflict_table* est **sysname**, avec une valeur par défaut **%**. Si le *conflict_table* est spécifié comme NULL ou **%**, le conflit est considéré comme un conflit de suppression et la ligne correspondant *rowguid* et *origin_datasource* et *source_object* est supprimé de la [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) table.  
  
 [  **@source_object=**] **'***source_object***'**  
 Est le nom de la table source. *source_object* est **nvarchar (386)**, avec NULL comme valeur par défaut.  
  
 [  **@rowguid =**] **'***rowguid***'**  
 Identificateur de ligne pour le conflit de suppression. *ROWGUID* est **uniqueidentifier**, sans valeur par défaut.  
  
 [  **@origin_datasource=**] **'***origin_datasource***'**  
 Est l’origine du conflit. *origin_datasource* est **varchar (255)**, sans valeur par défaut.  
  
 [  **@drop_table_if_empty=**] **'***suppr_table_si_vide***'**  
 Est un indicateur qui spécifie si le *conflict_table* doit être supprimée lorsqu’elle est vide. *suppr_table_si_vide* est **varchar (10)**, avec FALSE comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_deletemergeconflictrow** est utilisé dans la réplication de fusion.  
  
 [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) table est une table système et n’est pas supprimée à partir de la base de données, même si elle est vide.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
