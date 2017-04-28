---
title: "LOWER (expression SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conversion de caractères majuscules en caractères minuscules"
  - "LOWER, fonction"
  - "caractères majuscules [Integration Services]"
  - "caractères minuscules"
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LOWER (expression SSIS)
  Renvoie une expression de caractères après avoir transformé les caractères majuscules en caractères minuscules.  
  
## Syntaxe  
  
```  
  
LOWER(character_expression)  
```  
  
## Arguments  
 *character_expression*  
 Expression de type caractère à convertir en caractères minuscules.  
  
## Types des résultats  
 DT_WSTR  
  
## Notes  
 La fonction LOWER n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *character_expression* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que UPPER effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 La fonction LOWER renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
 L'exemple suivant convertit un littéral de chaîne en caractères minuscules. Le résultat obtenu est « new york ».  
  
```  
LOWER("New York")  
```  
  
 L’exemple suivant convertit tous les caractères de la colonne d’entrée **Color**, à l’exception du premier caractère, en caractères minuscules. Si la colonne Color a pour valeur JAUNE, le résultat obtenu est « Jaune ». Pour plus d’informations, consultez [SUBSTRING &#40;expression SSIS&#41;](../../integration-services/expressions/substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 L’exemple suivant convertit la valeur de la variable **CityName** en caractères minuscules.  
  
```  
LOWER(@CityName)  
```  
  
## Voir aussi  
 [UPPER &#40;expression SSIS&#41;](../../integration-services/expressions/upper-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  