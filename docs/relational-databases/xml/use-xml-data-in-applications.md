---
title: "Utiliser des donn&#233;es XML dans les applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres [XML dans SQL Server]"
  - "XML [SQL Server], ADO"
  - "colonnes [XML dans SQL Server], ADO.NET"
  - "ADO [XML dans SQL Server]"
  - "colonnes [XML dans SQL Server], SQL Server Native Client"
  - "type de données xml [SQL Server], ADO"
  - "SQLNCLI, XML"
  - "type de données xml [SQL Server], SQL Server Native Client"
  - "SQL Server Native Client, XML"
  - "ADO.NET [XML dans SQL Server]"
  - "XML [SQL Server], ADO.NET"
  - "colonnes [XML dans SQL Server], ADO"
  - "type de données xml [SQL Server], ADO.NET"
  - "XML [SQL Server], SQL Server Native Client"
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Utiliser des donn&#233;es XML dans les applications
  Cette rubrique décrit les options dont vous disposez pour utiliser le type de données **xml** dans votre application. Cette rubrique inclut des informations sur les thèmes suivants :  
  
-   Gestion de XML à partir d’une colonne de type **xml[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’ADO et de ** Native Client  
  
-   Gestion de XML à partir d'une colonne de type **xml** à l'aide d'ADO.NET  
  
-   Gestion du type **xml** dans les paramètres à l'aide d'ADO.NET  
  
## Gestion de XML à partir d'une colonne de type XML à l'aide d'ADO et de SQL Server Native Client  
 Pour utiliser des composants MDAC pour accéder aux types et aux fonctionnalités introduits dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], vous devez définir la propriété d’initialisation DataTypeCompatibility dans la chaîne de connexion ADO.  
  
 Par exemple, l’exemple VBScript (Visual Basic Scripting Edition) suivant affiche les résultats de l’interrogation d’une colonne de type de données **xml**, `Demographics`, dans la table `Sales.Store` de l’exemple de base de données `AdventureWorks2012`. La requête recherche plus particulièrement la valeur de l'instance de cette colonne pour la ligne dans laquelle `CustomerID` est égal à `3`.  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 Cet exemple montre comment définir la propriété de compatibilité du type de données. Par défaut, elle a la valeur 0 lorsque vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Si vous avez affecté la valeur 80 à cette propriété, le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fait apparaître les colonnes de type **xml** et définies par l’utilisateur comme des types de données [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Il s'agit respectivement de BTYPE_WSTR et de DBTYPE_BYTES.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client doit également être installé sur l'ordinateur client et la chaîne de connexion doit le désigner comme fournisseur de données avec «`Provider=SQLNCLI11;...`».  
  
#### Pour tester cet exemple  
  
1.  Vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est installé et que MDAC version 2.6.0 ou ultérieure est disponible sur l'ordinateur client.  
  
     Pour plus d’informations, consultez [Programmation de SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client-programming.md).  
  
2.  Vérifiez que l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
     Cet exemple requiert l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
3.  Copiez le code préalablement présenté dans cette rubrique et collez-le dans votre éditeur de texte ou de code. Enregistrez le fichier sous HandlingXmlDataType.vbs.  
  
4.  Modifiez le script comme le requiert votre installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et enregistrez vos modifications.  
  
     Par exemple, à l'endroit où `MyServer` est spécifié, vous devez le remplacer par `(local)` ou par le nom réel du serveur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
5.  Exécutez HandlingXmlDataType.vbs et exécutez le script.  
  
 Les résultats doivent être semblables à l'exemple suivant :  
  
```  
Row 1  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>1500000</AnnualSales>  
  <AnnualRevenue>150000</AnnualRevenue>  
  <BankName>Primary International</BankName>  
  <BusinessType>OS</BusinessType>  
  <YearOpened>1974</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>38000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>40</NumberEmployees>  
</StoreSurvey>  
  
Row 2  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## Gestion de XML à partir d'une colonne de type XML à l'aide d'ADO.NET  
 Pour gérer XML à partir d’une colonne de type de données **xml** à l’aide d’ADO.NET et de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez utiliser le comportement standard de la classe **SqlCommand**. Par exemple, une colonne de type de données **xml** et ses valeurs peuvent être récupérées comme toute colonne SQL à l'aide de **SqlDataReader**.Toutefois, si vous souhaitez utiliser le contenu d'une colonne de type de données **xml** sous la forme XML, vous devez d'abord assigner un type **XmlReader** au contenu.  
  
 Pour plus d'informations et d'exemples de code, consultez la rubrique relative aux valeurs de colonne XML dans un lecteur de données dans la documentation du Kit de développement logiciel de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] .  
  
## Gestion d'une colonne de type XML dans les paramètres à l'aide d'ADO.NET  
 Pour gérer un type de données xml passé en tant que paramètre dans ADO.NET et le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez fournir la valeur sous la forme d’une instance du type de données **SqlXml**. Aucune gestion spéciale n’est requise, car les colonnes de type de données **xml** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent accepter les valeurs de paramètre de la même façon que d’autres colonnes et types de données, tels que **string** ou **integer**.  
  
 Pour plus d'informations et d'exemples de code, consultez la rubrique relative aux valeurs XML en tant que paramètres de commande dans la documentation du Kit de développement logiciel de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] .  
  
## Voir aussi  
 [Données XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
  