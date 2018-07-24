---
title: Utilisation des Types de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 306b227a4b193811c7207f111fc35a48148e4bbf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228919"
---
# <a name="working-with-data-types"></a>Utilisation des types de données
  Il existe des données de nombreux types et tailles différents, telles qu'une chaîne qui a une longueur définie, un nombre qui a une précision spécifique ou un type de données défini par l'utilisateur qui est un autre objet ayant son propre ensemble de règles. Le <xref:Microsoft.SqlServer.Management.Smo.DataType> objet classifie le type de données afin qu’il puisse être géré correctement par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L'objet <xref:Microsoft.SqlServer.Management.Smo.DataType> est associé aux objets qui acceptent des données. Ce qui suit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les objets Management Objects (SMO) acceptent des données qui doivent être définies par un <xref:Microsoft.SqlServer.Management.Smo.DataType> propriété d’objet :  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 La propriété `DataType` pour les objets qui acceptent des données peut être définie de plusieurs façons.  
  
-   Utilisez le constructeur par défaut et spécifiez <xref:Microsoft.SqlServer.Management.Smo.DataType> propriétés de l’objet explicitement  
  
-   Utilisez un constructeur surchargé et spécifiez le <xref:Microsoft.SqlServer.Management.Smo.DataType> propriétés en tant que paramètres.  
  
-   Spécifiez le <xref:Microsoft.SqlServer.Management.Smo.DataType> inline dans le constructeur d’objet.  
  
-   Utilisez l'un des membres statiques de la classe <xref:Microsoft.SqlServer.Management.Smo.DataType>, par exemple `Int`. Cela retourne en fait une instance d'un objet <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.DataType> a plusieurs propriétés qui définissent le type de données. Par exemple, la propriété <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> spécifie le type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les valeurs constantes qui représentent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les types de données sont répertoriés dans le <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> énumération. Cela fait référence à des types de données tels que `varchar`, `nchar`, `currency`, `integer`, `float` et `datetime`.  
  
 Lorsque le type de données est établi, des propriétés spécifiques doivent être définies pour les données. Par exemple, s'il s'agit d'un type `nchar`, la longueur des données de chaîne doit être définie dans la propriété `Length`. La même règle s'applique aux valeurs numériques, pour lesquelles il vous faudrait spécifier la précision et l'échelle.  
  
 Les types de données <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> et <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> font référence à des objets qui contiennent la définition du type de données défini par l'utilisateur. Le type <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> est basé sur les types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de l'énumération <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. Le <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> repose sur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] types de données .NET. En général, ces types représentent des données d'un type spécifique qui est fréquemment réutilisé par la base de données à cause de règles d'entreprise définies par l'organisation. Par exemple, un type de données qui stocke une somme d'argent et un dénominateur de devise serait utile dans une société qui négocie dans plusieurs devises.  
  
 Le <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> énumération contient une liste de toutes les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-types de données pris en charge.  
  
## <a name="examples"></a>Exemples  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Construction d'un objet DataType avec la spécification dans le constructeur en Visual Basic  
 Cet exemple de code montre comment utiliser le constructeur pour créer des instances de types de données qui sont basées sur différents [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] types de données.  
  
> [!NOTE]  
>  Les types <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> et XML requièrent tous une valeur de nom afin d'identifier l'objet.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Construction d'un objet DataType avec la spécification dans le constructeur en Visual C#  
 Cet exemple de code montre comment utiliser le constructeur pour créer des instances de types de données qui sont basées sur différents [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] types de données.  
  
> [!NOTE]  
>  Les types <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> et XML requièrent tous une valeur de nom afin d'identifier l'objet.  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguements specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Construction d'un objet DataType à l'aide du constructeur par défaut en Visual Basic  
 Cet exemple de code montre comment utiliser le constructeur par défaut pour créer des instances de types de données qui sont basées sur différents [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] types de données. Les propriétés sont ensuite utilisées pour spécifier le type de données.  
  
 **Remarque** le <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, et de tous les types XML requièrent une valeur de nom pour identifier l’objet.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Construction d'un objet DataType à l'aide du constructeur par défaut en Visual C#  
 Cet exemple de code montre comment utiliser le constructeur par défaut pour créer des instances de types de données qui sont basées sur différents [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] types de données. Les propriétés sont ensuite utilisées pour spécifier le type de données.  
  
 **Remarque** le <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, et de tous les types XML requièrent une valeur de nom pour identifier l’objet.  
  
```  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  