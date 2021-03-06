---
title: À l’aide des Types de données avancés | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b39461d3-48d6-4048-8300-1a886c00756d
caps.latest.revision: 58
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ef615f695209cf01c2307c53effc7e84b06eb11
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278610"
---
# <a name="using-advanced-data-types"></a>Utilisation des types de données avancés
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilise les types de données avancés JDBC pour convertir les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en un format compréhensible par le langage de programmation Java.  
  
## <a name="remarks"></a>Notes   
 Le tableau suivant liste les mappages par défaut entre les types de données avancés [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], JDBC et du langage de programmation Java.  
  
|Types SQL Server|Types JDBC (java.sql.Types)|Types langage Java|  
|----------------------|-----------------------------------|-------------------------|  
|varbinary(max)<br /><br /> image|LONGVARBINARY|byte[] \(par défaut), Blob, InputStream, String|  
|texte<br /><br /> varchar(max)|LONGVARCHAR|String (par défaut), Clob, InputStream|  
|ntext<br /><br /> nvarchar(max)|LONGVARCHAR<br /><br /> LONGNVARCHAR (Java SE 6.0)|String (par défaut), Clob, NClob (Java SE 6.0)|  
|xml|LONGVARCHAR<br /><br /> SQLXML (Java SE 6.0)|String (par défaut), InputStream, Clob, byte[], Blob, SQLXML (Java SE 6.0)|  
|Udt<sup>1</sup>|VARBINARY|String (par défaut), byte[], InputStream|  
  
 <sup>1</sup> Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l'envoi et la récupération d'UDT CLR sous forme de données binaires, et non la manipulation des métadonnées CLR.  
  
 Les sections suivantes proposent des exemples d'utilisation du pilote JDBC et des types de données avancés.  
  
## <a name="blob-and-clob-and-nclob-data-types"></a>Types de données BLOB, CLOB et NCLOB  
 Le pilote JDBC implémente toutes les méthodes des interfaces java.sql.Blob, java.sql.Clob et java.sql.NClob.  
  
> [!NOTE]  
>  Les valeurs CLOB peuvent être utilisées avec les types de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] (ou version ultérieure) de grande valeur. Plus précisément, les types CLOB peuvent être utilisés avec la **varchar (max)** et **nvarchar (max)** des types de données, types d’objets BLOB peuvent être utilisés avec **varbinary (max)** et **image**  types de données et les types NCLOB peuvent être utilisés avec **ntext** et **nvarchar (max)**.  
  
## <a name="large-value-data-types"></a>Types de données de grande valeur  
 Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], l'utilisation de types de données de grande valeur nécessitait un traitement spécial. Les types de données à valeur élevée sont ceux qui dépassent la taille de ligne maximale de 8 Ko. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] introduit un spécificateur max pour les types de données **varchar**, **nvarchar** et **varbinary**, qui permet le stockage de valeurs pouvant atteindre 2^31 octets. Les colonnes de table et les variables [!INCLUDE[tsql](../../includes/tsql_md.md)] peuvent spécifier des types de données **varchar(max)**, **nvarchar(max)** ou **varbinary(max)**.  
  
 Les principaux scénarios de travail sur des types de données de grande valeur impliquent l'extraction d'une base de données ou l'ajout à une base de données. Les sections suivantes décrivent les différentes approches de réalisation de ces tâches.  
  
### <a name="retrieving-large-value-types-from-a-database"></a>Extraction de types de données de grande valeur d'une base de données  
 Pour récupérer un type de données de grande valeur non binaire, par exemple, **varchar(max)**, dans une base de données, une approche consiste à lire ces données sous forme de flux de caractères. L'exemple suivant utilise la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) pour extraire des données de la base de données et les retourner dans un jeu de résultats. Ensuite, la méthode [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) de la classe [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) est appelée pour lire les données de grande valeur dans le jeu de résultats.  
  
```java
ResultSet rs = stmt.executeQuery("SELECT TOP 1 * FROM Test1");  
rs.next();  
Reader reader = rs.getCharacterStream(2);  
```  
  
> [!NOTE]  
>  Cette même approche peut également être utilisée pour le **texte**, **ntext**, et **nvarchar (max)** des types de données.  
  
 Pour récupérer un type de données de grande valeur binaire, par exemple, **varbinary(max)**, dans une base de données, plusieurs approches sont possibles. La plus efficace consiste à lire les données en tant que flux de données binaire, comme suit :  
  
```java
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
InputStream is = rs.getBinaryStream(2);  
```  
  
 Vous pouvez également utiliser la méthode [getBytes](../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md) pour lire les données sous forme de tableau d'octets, comme dans l’exemple suivant :  
  
```java
ResultSet rs = stmt.executeQuery("SELECT photo FROM mypics");  
rs.next();  
byte [] b = rs.getBytes(2);  
```  
  
> [!NOTE]  
>  Vous pouvez également lire les donnés en tant que BLOB. Cependant, cette méthode est moins efficace que les deux précédentes.  
  
### <a name="adding-large-value-types-to-a-database"></a>Ajout de types de données de grande valeur à une base de données  
 Le téléchargement de données de grande valeur avec le pilote JDBC fonctionne correctement dans les cas de correspondance avec la taille de la mémoire ; dans les cas de dépassement de la taille de la mémoire, la transmission de flux de données en continu constitue l'option principale. Cependant, la méthode la plus efficace consiste à télécharger des données de grande valeur via les interfaces de flux.  
  
 L'utilisation d'une chaîne ou d'octets est également une option, comme suit :  
  
```java
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (c1_id, c2_vcmax) VALUES (?, ?)");  
pstmt.setInt(1, 1);  
pstmt.setString(2, htmlStr);  
pstmt.executeUpdate();  
```  
  
> [!NOTE]  
>  Cette approche peut également être utilisée pour les valeurs qui sont stockés dans **texte**, **ntext**, et **nvarchar (max)** colonnes.  
  
 Si vous disposez d'une bibliothèque d'images sur le serveur et que vous devez charger des fichiers image binaires entiers dans une colonne **varbinary(max)**, la méthode la plus efficace impliquant le pilote JDBC consiste à utiliser directement les flux, comme dans l’exemple suivant :  
  
```java
PreparedStatement pstmt = con.prepareStatement("INSERT INTO test1 (Col1, Col2) VALUES(?,?)");  
File inputFile = new File("CLOBFile20mb.jpg");  
FileInputStream inStream = new FileInputStream(inputFile);  
int id = 1;  
pstmt.setInt(1,id);  
pstmt.setBinaryStream(2, inStream);  
pstmt.executeUpdate();  
inStream.close();  
```  
  
> [!NOTE]  
>  L'utilisation de la méthode CLOB ou BLOB n'est pas efficace pour le téléchargement de données de grande valeur.  
  
### <a name="modifying-large-value-types-in-a-database"></a>Modification de types de données de grande valeur dans une base de données  
 Dans la plupart des cas, la méthode recommandée pour mettre à jour ou modifier des données de grande valeur dans la base de données consiste à transmettre des paramètres par le biais des classes [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), avec des commandes [!INCLUDE[tsql](../../includes/tsql_md.md)] comme UPDATE, WRITE et SUBSTRING.  
  
 Si vous devez remplacer l'instance d'un mot dans un fichier texte volumineux, comme un fichier HTML archivé, vous pouvez utiliser un objet Clob, comme dans l’exemple suivant :  
  
```java
String SQL = "SELECT * FROM test1;";  
Statement stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);  
ResultSet rs = stmt.executeQuery(SQL);  
rs.next();  
  
Clob clob = rs.getClob(2);  
long pos = clob.position("dog", 1);  
clob.setString(pos, "cat");  
rs.updateClob(2, clob);  
rs.updateRow();  
```  
  
 De plus, vous pouvez effectuer tout le travail sur le serveur et simplement transmettre les paramètres à une instruction UPDATE préparée.  
  
 Pour plus d'informations sur les types de données de grande valeur, consultez « Utilisation de types de données de grande valeur » dans la documentation en ligne de SQL Server.  
  
## <a name="xml-data-type"></a>Type de données XML  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] propose un type de données **xml** qui vous permet de stocker des documents et des fragments XML dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le type de données **xml** est intégré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et s’apparente à certains égards à d’autres types intégrés, comme **int** et **varchar**. Tout comme d’autres types intégrés, il est possible d’utiliser le type de données **xml** comme type de colonne pour créer une table ; comme type de variable, type de paramètre ou type de retour de fonction ; ou dans les fonctions [!INCLUDE[tsql](../../includes/tsql_md.md)] CAST et CONVERT.  
  
 Dans le pilote JDBC, le type de données **xml** peut être mappé en tant que chaîne, tableau d’octets, flux, objet CLOB, objet BLOB ou objet SQLXML. Chaîne est la valeur par défaut. À partir de la version 2.0 du pilote JDBC, l'API JDBC 4.0 est prise en charge, ce qui permet l'introduction de l'interface SQLXML. L’interface SQLXML définit des méthodes d’interaction et de manipulation des données XML. Le **SQLXML** mappe le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** type de données. Pour savoir comment lire et écrire des données XML dans la base de données relationnelle avec le type de données Java **SQLXML**, voir [Prise en charge des données XML](../../connect/jdbc/supporting-xml-data.md).  
  
 L’implémentation du type de données **xml** dans le pilote JDBC permet la prise en charge des éléments suivants :  
  
-   Accès à XML en tant que chaîne standard Java UTF-16 pour les scénarios de programmation les plus courants  
  
-   Entrée de XML en UTF-8 ou codé sur 8 bits  
  
-   Accès à XML en tant que tableau d'octets avec un BOM de début lors de l'encodage en UTF-16 pour l'échange avec d'autres processeurs XML et fichiers de disque  
  
 Avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il est nécessaire d’ajouter une marque d'ordre d'octet au début des fichiers XML encodés en UTF-16. L'application doit le fournir quand les valeurs de paramètre XML sont fournies en tant que tableaux d'octets. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] retourne toujours les valeurs XML sous forme de chaînes UTF-16 sans marque d'ordre d'octet ou déclaration d’encodage incorporée. Lorsque des valeurs XML sont récupérées en tant que byte[], BinaryStream ou Blob, une marque d'ordre d'octet (BOM, Byte-Order Mark) UTF-16 est ajoutée au début de la valeur.  
  
 Pour plus d’informations sur le type de données **xml**, voir « Type de données xml » dans la Documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="user-defined-data-type"></a>Type de données défini par l'utilisateur  
 L’introduction des types définis par l’utilisateur (UDT) dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] étend le système de type SQL en permettant de stocker des objets et des structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Les UDT peuvent contenir plusieurs types de données et avoir des comportements, ce qui les différencie des types de données d'alias traditionnels qui ne comportent qu'un seul type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Les types UDT sont définis à l'aide d'un des langages pris en charge par le CLR (Common Language Runtime) Microsoft .NET produisant un code vérifiable. Cela inclut Microsoft Visual C# et Visual Basic .NET. Les données sont exposées en tant que champs et propriétés d'une classe ou structure basée sur le .NET Framework ; par ailleurs, les comportements sont définis par les méthodes de la classe ou de la structure.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], un type UDT peut être utilisé comme définition de colonne d’une table, comme variable dans un lot [!INCLUDE[tsql](../../includes/tsql_md.md)] ou comme argument d’une fonction ou d’une procédure stockée [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
 Pour plus d’informations sur les types de données définis par l’utilisateur, voir « Utiliser et modifier des instances de types définis par l’utilisateur » dans la Documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
