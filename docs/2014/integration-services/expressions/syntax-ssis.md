---
title: Syntaxe (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], syntax
- syntax [Integration Services]
ms.assetid: 61c053c5-1182-4ad0-b804-51cbd19aa0ba
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2fc62fbd298f5559dff9dc5d944bd668a17a79bd
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082971"
---
# <a name="syntax-ssis"></a>Syntaxe (SSIS)
  La syntaxe des expressions [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est similaire à la syntaxe utilisée par les langages C et C#. Les expressions comprennent des éléments tels que des identificateurs (colonnes et variables), des littéraux, des opérateurs et des fonctions. Cette rubrique récapitule les contraintes de la syntaxe de l'évaluateur d'expression applicables aux différents éléments d'une expression.  
  
> [!NOTE]  
>  Les versions précédentes de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]limitaient à 4000 caractères le résultat de l'évaluation d'une expression lorsqu'il était caractérisé par le type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DT_WSTR ou DT_STR. Cette limite a été supprimée.  
  
 Pour obtenir des exemples d’expressions utilisant des opérateurs et des fonctions spécifiques, consultez la rubrique relative à chaque opérateur et fonction dans les rubriques : [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md) et [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md).  
  
 Pour obtenir des exemples d’expressions utilisant plusieurs opérateurs et fonctions, ainsi que des identificateurs et des littéraux, consultez [Exemples d’expressions Integration Services avancées](examples-of-advanced-integration-services-expressions.md).  
  
 Pour obtenir des exemples d’expressions de propriété, consultez [Utiliser des expressions de propriété dans les packages](use-property-expressions-in-packages.md).  
  
## <a name="identifiers"></a>Identificateurs  
 Les expressions peuvent comprendre des identificateurs de colonne et de variable. Les colonnes peuvent provenir de la source de données ou être créées par des transformations dans le flux de données. Les expressions peuvent utiliser des identificateurs de lignage pour faire référence aux colonnes. Les identificateurs de lignage sont des nombres qui identifient de manière unique les éléments du package. Les identificateurs de lignage référencés dans une expression doivent être préfixés du signe dièse ( # ). Par exemple, l'identificateur de lignage 138 est référencé sous la forme « #138 ».  
  
 Les expressions peuvent contenir les variables système fournies par [!INCLUDE[ssIS](../../includes/ssis-md.md)] , ainsi que des variables personnalisées. Variables référencées dans une expression, doivent inclure le \@ préfixe. Par exemple, le `Counter` variable est référencée à l’aide de \@compteur. Le \@ caractère ne fait pas partie du nom de variable ; il indique simplement à l’évaluateur d’expression que l’identificateur est une variable. Pour plus d’informations, consultez [Identificateurs &#40;SSIS&#41;](identifiers-ssis.md).  
  
## <a name="literals"></a>Littéraux  
 Les expressions peuvent contenir des littéraux numériques, booléens et de chaîne. Les littéraux de chaîne utilisés dans les expressions doivent être placés entre guillemets. Les littéraux numériques et booléens ne prennent pas de guillemets. Le langage des expressions comprend des séquences d'échappement pour les caractères fréquemment placés en mode échappement. Pour plus d’informations, consultez [Littéraux &#40;SSIS&#41;](numeric-string-and-boolean-literals.md).  
  
## <a name="operators"></a>Opérateurs  
 L'évaluateur d'expression fournit un ensemble d'opérateurs dont les fonctionnalités sont similaires à celles de l'ensemble des opérateurs de langages tels que Transact-SQL, C++ et C#. Toutefois, le langage des expressions comprend des opérateurs supplémentaires et utilise des symboles auxquels vous n'êtes peut-être pas habitué. Pour plus d’informations, consultez [Opérateurs &#40;expression SSIS&#41;](operators-ssis-expression.md).  
  
### <a name="namespace-resolution-operator"></a>Opérateur de résolution d'espace de noms  
 Les expressions utilisent l'opérateur de résolution d'espace de noms (::) pour lever toute ambiguïté sur les variables de même nom. Grâce à l'opérateur de résolution d'espace de noms, vous pouvez qualifier la variable avec son espace de noms, ce qui vous permet d'utiliser plusieurs variables du même nom dans un package.  
  
#### <a name="cast-operator"></a>Opérateur de conversion  
 L'opérateur de conversion convertit, d'un type de données vers un autre, les résultats des expressions, les valeurs des colonnes, les valeurs des variables et les constantes. L'opérateur de conversion fourni par le langage des expressions est similaire à celui des langages C et C#. Dans Transact-SQL, les fonctions CAST et CONVERT offrent cette fonctionnalité. La syntaxe de l'opérateur de conversion diffère de celles utilisées par les fonctions CAST et CONVERT dans les aspects suivants :  
  
-   Elle peut utiliser une expression comme argument.  
  
-   Elle ne comprend pas le mot clé CAST.  
  
-   Elle ne comprend pas le mot clé AS.  
  
##### <a name="conditional-operator"></a>Opérateur conditionnel  
 L'opérateur conditionnel retourne une des deux expressions en fonction de l'évaluation d'une expression booléenne. L'opérateur conditionnel fourni par le langage des expressions est similaire à celui des langages C et C#. Dans les expressions multidimensionnelles (MDX), la fonction IIF offre une fonctionnalité similaire.  
  
###### <a name="logical-operators"></a>Opérateurs logiques  
 Le langage des expressions prend en charge le caractère « ! » pour l'opérateur logique NOT. Dans Transact-SQL, l'opérateur « ! » est intégré à l'ensemble des opérateurs relationnels. Par exemple, Transact-SQL fournit les opérateurs « > » et « !> ». Le langage d’expression [!INCLUDE[ssIS](../../includes/ssis-md.md)] ne permet pas de combiner l’opérateur ! avec d’autres opérateurs. Par exemple, vous ne pouvez pas combiner ! et > pour donner !>. Toutefois, le langage des expressions prend en charge une combinaison de caractères intégrée « != » pour la comparaison « différent de » .  
  
###### <a name="equality-operators"></a>Opérateurs d'égalité  
 La grammaire de l'évaluateur d'expression fournit l'opérateur d'égalité « == ». Cet opérateur est l'équivalent de l'opérateur « = » dans Transact-SQL et de l'opérateur « == » dans C#.  
  
## <a name="functions"></a>Fonctions  
 Le langage des expressions comprend des fonctions de date et d'heure, des fonctions mathématiques et des fonctions de chaîne similaires aux fonctions Transact-SQL et aux méthodes C#.  
  
 Certaines fonctions portent le même nom que des fonctions Transact-SQL, mais leurs fonctionnalités diffèrent légèrement dans l'évaluateur d'expression.  
  
-   Dans Transact-SQL, la fonction ISNULL remplace les valeurs NULL par une valeur spécifiée, tandis que la fonction ISNULL de l'évaluateur d'expression retourne une valeur booléenne basée sur le test de la valeur NULL d'une expression.  
  
-   Dans Transact-SQL, la fonction ROUND comprend une option qui permet de tronquer le jeu de résultats, fonctionnalité que n'offre pas la fonction ROUND de l'évaluateur d'expression.  
  
 Pour plus d’informations, consultez [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 [Utiliser une expression dans un composant de flux de données](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article technique, [SSIS Expression Cheat Sheet](http://go.microsoft.com/fwlink/?LinkId=217683), sur pragmaticworks.com  
  
-   Article technique, [SSIS Expression Examples](http://go.microsoft.com/fwlink/?LinkId=220761), sur social.technet.microsoft.com  
  
  
