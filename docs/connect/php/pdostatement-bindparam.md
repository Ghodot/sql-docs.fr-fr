---
title: PDOStatement::bindParam | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 02d31959423de5c0df4dc06e9caa16ea983ef000
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lie un paramètre à un espace réservé nommé ou de point d’interrogation dans l’instruction SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDOStatement::bindParam( $parameter, &$variable [,$data_type[, $length[, $driver_options]]] );  
```  
  
#### <a name="parameters"></a>Paramètres  
$*paramètre*: un identificateur de paramètre (mixte). Pour une instruction qui utilise des espaces réservés nommés, nom d’un paramètre (:name). Pour une instruction préparée qui utilise la syntaxe constituée de points d’interrogation, il s’agit de l’index en base 1 du paramètre.  
  
&$*variable*: le nom (mixte) de la variable PHP à lier au paramètre d’instruction SQL.  
  
$*data_type*: constante PDO::PARAM_ * facultative (entier). Valeur par défaut est PDO::PARAM_STR.  
  
$*longueur*: une longueur (entier) facultatif du type de données. Vous pouvez spécifier PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE pour indiquer la taille par défaut lorsque vous utilisez PDO::PARAM_INT ou PDO::PARAM_BOOL dans $*data_type*.  
  
$*driver_options*: les options spécifiques au pilote de (mixtes) facultatif. Par exemple, vous pouvez spécifier PDO::SQLSRV_ENCODING_UTF8 pour lier la colonne à une variable en tant que chaîne encodée au format UTF-8.  
  
## <a name="return-value"></a>Valeur retournée  
TRUE en cas de réussite ; sinon, FALSE.  
  
## <a name="remarks"></a>Notes  
Lors de la liaison de données de type null pour les colonnes de serveur de type varbinary, binary ou varbinary (max), vous devez spécifier le codage binaire (PDO::SQLSRV_ENCODING_BINARY) à l’aide de la $*driver_options*. Pour plus d’informations sur l’encodage des constantes, consultez [Constantes](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md) .  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
Cet exemple de code montre qu’après la liaison de $contact au paramètre, le fait de modifier la valeur change la valeur transmise dans la requête.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>Exemple  
Cet exemple de code montre comment accéder à un paramètre de sortie.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(* ) from Sys.tables");  
$stmt->bindParam( 1, $input1, PDO::PARAM_STR, 10 );  
$stmt->execute();  
echo $input1;  
?>  
```  
  
## <a name="example"></a>Exemple  
Cet exemple de code montre comment utiliser un paramètre d’entrée/sortie.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
