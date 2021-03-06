---
title: sp_cursoroption (Transact-SQL) | Microsoft Docs
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
- sp_cursoroption_TSQL
- sp_cursoroption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursoroption
ms.assetid: 88fc1dba-f4cb-47c0-92c2-bf398f4a382e
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5b3bb6500d4d1bc29859c428820d28ec48d6aa72
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026554"
---
# <a name="spcursoroption-transact-sql"></a>sp_cursoroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Définit les options de curseur ou retourne des informations de curseur créées par la procédure stockée sp_cursoropen. sp_cursoroption est appelée en spécifiant ID = 8 dans un paquet data stream (TDS).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_cursoroption cursor, code, value  
```  
  
## <a name="arguments"></a>Arguments  
 *cursor*  
 Est un *gérer* valeur générée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et retournée par la procédure stockée sp_cursoropen. *curseur* nécessite un **int** d’entrée de valeur pour l’exécution.  
  
 *Code*  
 Permet de stipuler différents facteurs des valeurs de retour de curseur. *code* requiert l’une des opérations suivantes **int** valeurs d’entrée :  
  
|Valeur|Nom   |Description|  
|-----------|----------|-----------------|  
|0x0001|TEXTPTR_ONLY|Retourne le pointeur de texte, et non les données réelles, pour certaines colonnes text ou image désignées.<br /><br /> TEXTPTR_ONLY permet l’utilisation des pointeurs de texte à utiliser comme *handles* vers des objets blob qui peuvent être récupérés ultérieurement à sélectivement ou mis à jour à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou les fonctions DBLIB (par exemple) [!INCLUDE[tsql](../../includes/tsql-md.md)] READTEXT ou DBLIB DBWRITETEXT).<br /><br /> Si une valeur « 0 » est affectée, toutes les colonnes text et image dans la liste de sélection retourneront des pointeurs de texte plutôt que des données.|  
|0x0002|CURSOR_NAME|Assigne le nom spécifié dans *valeur* jusqu’au curseur. Ceci, à son tour, ODBC peut ainsi utiliser [!INCLUDE[tsql](../../includes/tsql-md.md)] positionné les instructions UPDATE/DELETE sur les curseurs ouverts via sp_cursoropen.<br /><br /> La chaîne peut être spécifiée comme tout caractère ou type de données Unicode.<br /><br /> Dans la mesure où [!INCLUDE[tsql](../../includes/tsql-md.md)] des instructions UPDATE/DELETE positionnées fonctionnent, par défaut, sur la première ligne dans un curseur fat, sp_cursor SETPOSITION doit être utilisé pour positionner le curseur avant d’émettre l’instruction UPDATE/DELETE positionnée.|  
|0x0003|TEXTDATA|Retourne les données réelles, et non le pointeur de texte, pour certaines colonnes text ou image sur les extractions suivantes (autrement dit, cela annule l'effet de TEXTPTR_ONLY).<br /><br /> Si TEXTDATA est activé pour une colonne particulière, la ligne est à nouveau extraite ou actualisée, et TEXTPTR_ONLY peut ensuite lui être à nouveau affecté. Comme avec TEXTPTR_ONLY, le paramètre de valeur est un entier qui spécifie le numéro de colonne et une valeur zéro retourne toutes les colonnes text et image.|  
|0x0004|SCROLLOPT|Option de défilement. Pour plus d'informations, consultez « Valeurs des codes de retour » plus loin dans cette rubrique.|  
|0x0005|CCOPT|Option de contrôle en matière d'accès concurrentiel. Pour plus d'informations, consultez « Valeurs des codes de retour » plus loin dans cette rubrique.|  
|0x0006|ROWCOUNT|Nombre de lignes actuellement dans le jeu de résultats.<br /><br /> Remarque : Le nombre de lignes peut avoir changé depuis la valeur retournée par sp_cursoropen si le remplissage asynchrone est utilisé. La valeur –1 est retournée si le nombre de lignes est inconnu.|  
  
 *value*  
 Désigne la valeur retournée par *code*. *valeur* est un paramètre obligatoire qui appelle un 0 x 0001, 0 x 0002 ou 0 x 0003 *code* valeur d’entrée.  
  
> [!NOTE]  
>  Un *code* valeur 2 est un type de données de chaîne. N’importe quel autre *code* valeur entrée ou retournée par *valeur* est un entier.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Le *valeur* paramètre peut retourner l’une des opérations suivantes *code* valeurs.  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|0x0004|SCROLLOPT|  
|0X0005|CCOPT|  
|0X0006|ROWCOUNT|  
  
 Le *valeur* paramètre retourne une des valeurs SCROLLOPT suivantes.  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
  
 Le *valeur* paramètre retourne une des valeurs CCOPT suivantes.  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS|  
|0x0004 ou 0x0008|OPTIMISTIC|  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)  
  
  
