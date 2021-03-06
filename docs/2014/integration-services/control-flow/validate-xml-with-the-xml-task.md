---
title: Effectuer une validation XML avec la tâche XML | Microsoft Docs
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
- XML validation
- XML, validating
ms.assetid: 224fc025-c21f-4d43-aa9d-5ffac337f9b0
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8ea74ad195b97541147c3d1b19dc01c5033b962c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182826"
---
# <a name="validate-xml-with-the-xml-task"></a>Validate XML with the XML Task
  Valider des documents XML et obtenez la sortie d’erreur détaillée en activant le `ValidationDetails` propriété de la tâche XML.  
  
 La capture d’écran ci-après affiche l’ **Éditeur de tâche XML** avec les paramètres requis pour l’exécution d’une validation XML avec une sortie d’erreur détaillée.  
  
 ![Propriétés de la tâche XML dans l’Éditeur de tâche XML](../media/xmltaskproperties.jpg "Propriétés de la tâche XML dans l’Éditeur de tâche XML")  
  
 Avant du `ValidationDetails` propriété n’était disponible, la validation de XML par la tâche XML ne renvoyait qu’un résultat true ou false, sans aucune information sur les erreurs ou leur emplacement. Désormais, lorsque vous définissez `ValidationDetails` sur true, la sortie de fichier contient des informations détaillées sur chaque erreur, notamment le numéro de ligne et la position. Vous pouvez utiliser ces informations pour comprendre, localiser et corriger les erreurs dans les documents XML.  
  
 La fonctionnalité de validation XML s’adapte aisément aux documents XML volumineux et aux nombres d’erreurs élevés. Étant donné que le fichier de sortie proprement dit présente le format XML, vous pouvez exécuter des requêtes sur la sortie et analyser cette dernière. Par exemple, si la sortie contient un grand nombre d’erreurs, vous pouvez regrouper les erreurs en exécutant une requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] , comme décrit dans cette rubrique.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) introduit la `ValidationDetails` propriété dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 2. La propriété est également disponible dans [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et dans SQL Server 2016.  
  
## <a name="sample-output-for-xml-thats-valid"></a>Exemple de sortie pour XML valide  
 Voici un exemple de fichier de sortie présentant les résultats de validation d’un fichier XML valide.  
  
```xml  
  
<root xmlns:ns="http://schemas.microsoft.com/xmltools/2002/xmlvalidation">  
    <metadata>  
        <result>true</result>  
        <errors>0</errors>  
        <warnings>0</warnings>  
        <startTime>2015-05-28T10:27:22.087</startTime>  
        <endTime>2015-05-28T10:29:07.007</endTime>  
        <xmlFile>d:\Temp\TestData.xml</xmlFile>  
        <xsdFile>d:\Temp\TestSchema.xsd</xsdFile>  
    </metadata>  
    <messages />  
</root>  
```  
  
## <a name="sample-output-for-xml-thats-not-valid"></a>Exemple de sortie pour XML non valide  
 Voici un exemple de fichier de sortie présentant les résultats de validation d’un fichier XML contenant un petit nombre d’erreurs. Le texte des éléments \<error> a été encapsulé pour améliorer la lisibilité.  
  
```xml  
  
<root xmlns:ns="http://schemas.microsoft.com/xmltools/2002/xmlvalidation">  
    <metadata>  
        <result>false</result>  
        <errors>2</errors>  
        <warnings>0</warnings>  
        <startTime>2015-05-28T10:45:09.538</startTime>  
        <endTime>2015-05-28T10:45:09.558</endTime>  
        <xmlFile>C:\Temp\TestData.xml</xmlFile>  
        <xsdFile>C:\Temp\TestSchema.xsd</xsdFile>  
    </metadata>  
    <messages>  
        <error line="5" position="26">The 'ApplicantRole' element is invalid - The value 'wer3' is invalid  
    according to its datatype 'ApplicantRoleType' - The Enumeration constraint failed.</error>  
        <error line="16" position="28">The 'Phone' element is invalid - The value 'we3056666666' is invalid  
     according to its datatype 'phone' - The Pattern constraint failed.</error>  
    </messages>  
</root>  
```  
  
## <a name="analyze-xml-validation-output-with-a-transact-sql-query"></a>Analyser la sortie de validation XML avec une requête Transact-SQL  
 Si le résultat de la validation XML contient un grand nombre d’erreurs, vous pouvez utiliser une requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour charger la sortie dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez ensuite analyser la liste d’erreurs avec toutes les fonctionnalités du langage T-SQL, notamment WHERE, GROUP BY, ORDER BY, JOIN, et ainsi de suite.  
  
```tsql  
DECLARE @xml XML;  
  
SELECT @xml = XmlDoc     
FROM OPENROWSET (BULK N'C:\Temp\XMLValidation_2016-02-212T10-41-00.xml', SINGLE_BLOB) AS Tab(XmlDoc);  
  
-- Query # 1, flat list of errors  
-- convert to relational/rectangular  
;WITH XMLNAMESPACES ('http://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS  
(  
SELECT col.value('@line','INT') AS line  
     , col.value('@position','INT') AS position  
     , col.value('.','VARCHAR(1024)') AS error  
FROM @XML.nodes('/root/messages/error') AS tab(col)  
)  
SELECT * FROM rs;  
-- WHERE error LIKE ‘%whatever_string%’  
  
-- Query # 2, count of errors grouped by the error message  
-- convert to relational/rectangular  
;WITH XMLNAMESPACES ('http://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS  
(  
SELECT col.value('@line','INT') AS line  
     , col.value('@position','INT') AS position  
     , col.value('.','VARCHAR(1024)') AS error  
FROM @XML.nodes('/root/messages/error') AS tab(col)  
)  
SELECT COALESCE(error,'Total # of errors:') AS [error], COUNT(*) AS [counter]  
FROM rs  
GROUP BY GROUPING SETS ((error), ())  
ORDER BY 2 DESC, COALESCE(error, 'Z');  
  
```  
  
 Voici le résultat dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] du second exemple de requête figurant dans le texte précédent.  
  
 ![Requête de regroupement des erreurs XML dans Management Studio](../media/queryforxmlerrors.jpg "Requête de regroupement des erreurs XML dans Management Studio")  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche XML](xml-task.md)   
 [Éditeur de tâche XML &#40;Page Général&#41;](../xml-task-editor-general-page.md)  
  
  
