---
title: 'SQL : overflow-field (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: f005182b-6151-432d-ab22-3bc025742cd3
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3b78db405442ea15fe3d62db4688eb82440dfb2c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246243"
---
# <a name="sqloverflow-field-sqlxml-40"></a>sql:overflow-field (SQLXML 4.0)
  Dans un schéma, vous pouvez identifier une colonne en tant que colonne de dépassement destinée à recevoir toutes les données non consommées du document XML. Cette colonne est spécifiée dans le schéma à l'aide de l'annotation `sql:overflow-field`. Un schéma peut contenir plusieurs colonnes de dépassement.  
  
 Dès qu'un nœud XML (élément ou attribut) pour lequel une annotation `sql:overflow-field` est définie entre dans la portée, la colonne de dépassement est activée et reçoit les données non consommées. Lorsque le nœud sort de la portée, la colonne de dépassement n'est plus active et le chargement en masse XML active le champ de dépassement précédent (le cas échéant).  
  
 En même temps qu'il stocke des données dans la colonne de dépassement, le chargement en masse XML stocke les balises d'ouverture et de fermeture de l'élément parent pour lequel `sql:overflow-field` est défini.  
  
 Par exemple, le schéma suivant décrit le  **\<clients >** et  **\<CustOrder >** éléments. Chacun de ces éléments identifie une colonne de dépassement :  
  
```  
<?xml version="1.0" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
 <xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
        parent="Cust"  
        parent-key="CustomerID"  
        child="CustOrder"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
 </xsd:annotation>  
 <xsd:element name="ROOT" sql:is-constant="1">  
  <xsd:complexType>  
    <xsd:sequence>   
      <xsd:element name="Customers"   
                   sql:relation="Cust"  
                   sql:overflow-field="OverflowColumn">  
        <xsd:complexType>  
             <xsd:sequence>   
             <xsd:element name="CustomerID" type="xsd:integer"/>  
             <xsd:element name="CompanyName"  type="xsd:string"/>  
             <xsd:element name="City" type="xsd:string"/>  
             <xsd:element name="Order"  
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder"  
                          sql:overflow-field="OverflowColumn">  
               <xsd:complexType>  
                 <xsd:attribute name="OrderID"/>  
                 <xsd:attribute name="CustomerID"/>  
               </xsd:complexType>  
             </xsd:element>  
          </xsd:sequence>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 Dans le schéma, le  **\<client >** élément est mappé à la table Cust et  **\<ordre >** élément est mappé à la table CustOrder.  
  
 Les deux le  **\<client >** et  **\<ordre >** éléments identifient une colonne de dépassement de capacité. Par conséquent, le chargement en masse XML enregistre tous les non consommées enfants éléments et attributs de la  **\<client >** élément dans la colonne de dépassement de capacité de la table Cust et tous les éléments enfants non consommées et attributs de la  **\<Ordre >** élément dans la colonne de dépassement de capacité de la table CustOrder.  
  
### <a name="to-test-a-working-sample"></a>Pour tester un exemple fonctionnel  
  
1.  Enregistrez le schéma fourni dans cet exemple sous le nom SampleSchema.xml.  
  
2.  Créez les tables suivantes :  
  
    ```  
    CREATE TABLE Cust (  
              CustomerID     int         PRIMARY KEY,  
              CompanyName    varchar(20) NOT NULL,  
              City           varchar(20) DEFAULT 'Seattle',  
              OverflowColumn nvarchar(200))  
    GO  
    CREATE TABLE CustOrder (  
              OrderID        int         PRIMARY KEY,  
              CustomerID     int         FOREIGN KEY REFERENCES  
                                              Cust(CustomerID),  
              OverflowColumn nvarchar(200))  
    GO  
    ```  
  
3.  Enregistrez l'exemple de données XML ci-après sous le nom SampleXMLData.xml :  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
          <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
     </Customers>  
     <Customers>  
       <CustomerID>1112</CustomerID>  
       <CompanyName>Toms Spezialitten</CompanyName>  
       <City><![CDATA[LA]]> </City>  
       <xyz><address>111 Maple, Seattle</address></xyz>     
       <Order OrderID="3" />  
     </Customers>  
       <Customers>  
       <CustomerID>1113</CustomerID>  
       <CompanyName>Victuailles en stock</CompanyName>  
       <Order OrderID="4" />  
      </Customers>  
    </ROOT>  
    ```  
  
4.  Pour exécuter le chargement en masse XML, enregistrez cet exemple [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) sous le nom Sample.vbs et exécutez-le :  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
