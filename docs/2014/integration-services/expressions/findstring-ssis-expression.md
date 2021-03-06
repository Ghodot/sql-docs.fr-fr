---
title: FINDSTRING (expression SSIS) | Microsoft Docs
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
- FINDSTRING function
ms.assetid: c83cb1b1-3c52-4496-b518-4c9253b9336d
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 82b5df9c4ee132a313b822da4aadc0bc5f90fd75
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272826"
---
# <a name="findstring-ssis-expression"></a>FINDSTRING (expression SSIS)
  Renvoie l'emplacement de l'occurrence spécifiée d'une chaîne dans une expression de caractères. Le résultat obtenu est l'index de base un de l'occurrence. Le paramètre de chaîne doit s'évaluer à une expression de caractères et le paramètre de l'occurrence doit s'évaluer à un entier. Si la chaîne est introuvable, la valeur retournée est 0. Si la chaîne se produit moins souvent que l'argument de l'occurrence ne le spécifie, la valeur retournée est 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FINDSTRING(character_expression, searchstring, occurrence)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 Chaîne de caractères dans laquelle la recherche doit être effectuée.  
  
 *searchstring*  
 Chaîne de caractères à rechercher.  
  
 *occurrence*  
 Entier signé ou non signé spécifiant l’occurrence de *searchstring* à signaler.  
  
## <a name="result-types"></a>Types de résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction FINDSTRING n'est opérationnelle qu'avec le type de données DT_WSTR.  Les arguments*character_expression* et *searchstring* qui représentent des littéraux de chaîne ou des colonnes de données du type de données DT_STR sont implicitement convertis dans le type de données DT_WSTR avant que la fonction FINDSTRING soit exécutée. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).  
  
 FINDSTRING retourne NULL si *character_expression* ou *searchstring* a la valeur Null.  
  
 Utilisez la valeur 1 dans l'argument *occurrence* pour obtenir l'index de la première occurrence, la valeur 2 pour obtenir celui de la deuxième occurrence, et ainsi de suite.  
  
 L'argument *occurrence* doit être un entier supérieur à 0.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant utilise un littéral de chaîne. Il renvoie la valeur 11.  
  
```  
FINDSTRING("New York, NY, NY", "NY", 1)   
```  
  
 L'exemple suivant utilise un littéral de chaîne. La chaîne « NY » ne se produisant que deux fois, le résultat retourné est 0.  
  
```  
FINDSTRING("New York, NY, NY", "NY", 3)   
```  
  
 L'exemple suivant utilise la colonne **Name** . Il renvoie l'emplacement de la valeur « n » dans la colonne **Name** . Le résultat obtenu varie en fonction de la valeur de la colonne **Name**. Si **Name** contient Anderson, la fonction retourne 8.  
  
```  
FINDSTRING(Name,"n", 2)   
```  
  
 L'exemple suivant utilise les colonnes **Name** et **Size** . Il renvoie l'emplacement du caractère situé à l'extrême gauche de la valeur **Size** de la colonne **Name** . Le résultat obtenu dépend des valeurs de la colonne. Si la colonne **Name** contient « Mountain,500Red,42 » et que la colonne **Size** contient « 42 », le résultat obtenu est 17.  
  
```  
FINDSTRING(Name,Size,1)   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Remplacez &#40;SSIS Expression&#41;](replace-ssis-expression.md)   
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
