---
title: CLOSE SYMMETRIC KEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CLOSE SYMMETRIC KEY
- CLOSE_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- closing symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], closing
- CLOSE SYMMETRIC KEY statement
- cryptography [SQL Server], symmetric keys
ms.assetid: 3b083cbb-3c6a-4f59-8d34-601db1efcc83
caps.latest.revision: 29
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: aa5b10cd64fbf7d77fe37cf1844d48a582643476
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790730"
---
# <a name="close-symmetric-key-transact-sql"></a>CLOSE SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ferme une clé symétrique ou ferme toutes les clés symétriques ouvertes pendant la session active.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CLOSE { SYMMETRIC KEY key_name | ALL SYMMETRIC KEYS }  
```  
  
## <a name="arguments"></a>Arguments  
 *KEY_NAME*  
 Nom de la clé symétrique à fermer.  
  
## <a name="remarks"></a>Notes   
 Les clés symétriques ouvertes sont liées à la session et non au contexte de sécurité. Une clé ouverte est disponible tant qu'elle n'a pas été explicitement fermée ou que la session n'a pas été arrêtée. CLOSE ALL SYMMETRIC KEYS ferme toutes les clés principales de base de données qui ont été ouvertes pendant la session actuelle à l’aide de l’instruction [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md).  Des informations relatives aux clés ouvertes sont consultables dans la vue de catalogue [sys.openkeys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Aucune autorisation explicite n'est requise pour fermer une clé symétrique.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-closing-a-symmetric-key"></a>A. Fermeture d'une clé symétrique  
 L'exemple suivant ferme la clé symétrique `ShippingSymKey04`.  
  
```  
CLOSE SYMMETRIC KEY ShippingSymKey04;  
GO  
```  
  
### <a name="b-closing-all-symmetric-keys"></a>B. Fermeture de toutes les clés symétriques  
 L'exemple suivant ferme toutes les clés symétriques ouvertes dans la session active, mais aussi la clé principale de la base de données qui a été ouverte explicitement.  
  
```  
CLOSE ALL SYMMETRIC KEYS;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)  
  
  
