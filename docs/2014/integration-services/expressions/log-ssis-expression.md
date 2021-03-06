---
title: LOG (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8d53a1a4c67e4447fd64d47c609e2a0f244e75c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300509"
---
# <a name="log-ssis-expression"></a>LOG (expression SSIS)
  Renvoie le logarithme de base 10 d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique valide différente de zéro ou non négative.  
  
## <a name="result-types"></a>Types de résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 *L’expression numérique* est convertie vers le type de données DT_R8 avant le calcul du logarithme. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
 Si l’argument *numeric_expression* donne une valeur inférieure ou égale à zéro, le résultat obtenu est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant utilise un littéral numérique. La fonction renvoie la valeur 1,988291341907488.  
  
```  
LOG(97.34)  
```  
  
 L'exemple suivant utilise la colonne **Length**. Si la valeur de la colonne est 101,24, la fonction renvoie 2,005352136486217.  
  
```  
LOG(Length)   
```  
  
 L'exemple suivant utilise la variable **Length**. La variable doit être d'un type de données numérique ou l'expression doit comprendre une conversion explicite en un type de données [!INCLUDE[ssIS](../../includes/ssis-md.md)] numérique. Si la variable **Length** a pour valeur 234,567, la fonction renvoie 2,370266913465859.  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a>Voir aussi  
 [EXP &#40;SSIS Expression&#41;](exp-ssis-expression.md)   
 [LN &#40;expression SSIS&#41;](ln-ssis-expression.md)   
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
