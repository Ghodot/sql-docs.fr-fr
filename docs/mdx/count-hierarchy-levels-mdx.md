---
title: Nombre (niveaux de hiérarchie) (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 657ce658704b519c31dfaa2186429a7df4110308
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739538"
---
# <a name="count-hierarchy-levels-mdx"></a>Count (Hierarchy Levels) (MDX)


  Retourne le nombre de niveaux dans la hiérarchie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchy_Expression.Levels.Count  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Retourne le nombre de niveaux dans une hiérarchie, notamment le niveau `[All]` (le cas échéant).  
  
> [!IMPORTANT]  
>  Lorsqu'une dimension contient uniquement une hiérarchie visible unique, cette hiérarchie peut être désignée soit par le nom de dimension, soit par le nom de la hiérarchie, puisque le nom de dimension est résolu à son unique hiérarchie visible. Par exemple, `Measures.Levels.Count` est une expression MDX valide parce qu'elle est résolue à la seule hiérarchie de la dimension de mesures.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne et comptabilise le nombre de niveaux dans la hiérarchie définie par l'utilisateur Product Categories du cube Adventure Works.  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Product Categories].Levels.Count   
Select Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Nombre &#40;Dimension&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [Nombre &#40;Tuple&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [Nombre &#40;définir&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
