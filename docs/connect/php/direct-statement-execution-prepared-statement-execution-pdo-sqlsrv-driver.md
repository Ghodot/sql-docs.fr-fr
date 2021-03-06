---
title: Diriger l’instruction - préparée pilote PDO_SQLSRV de l’exécution instruction | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c721a32936bf39d91042d6b7ac89a03a5fd85d6
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42783999"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Exécution d’instruction directe et exécution d’instruction préparée dans le pilote PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique décrit l’utilisation de l’attribut PDO::SQLSRV_ATTR_DIRECT_QUERY pour spécifier l’exécution d’une instruction directe plutôt que le comportement par défaut, qui est l’exécution d’une instruction préparée. À l’aide d’une instruction préparée peut entraîner de meilleures performances si l’instruction est exécutée plusieurs fois à l’aide de la liaison de paramètre.  
  
## <a name="remarks"></a>Notes   
Si vous souhaitez envoyer un [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction directement sur le serveur sans préparation de l’instruction par le pilote, vous pouvez définir l’attribut PDO::SQLSRV_ATTR_DIRECT_QUERY avec [PDO::setAttribute](../../connect/php/pdo-setattribute.md) (ou comme une option de pilote passée à [PDO::__construct](../../connect/php/pdo-construct.md)) ou lorsque vous appelez [PDO::prepare](../../connect/php/pdo-prepare.md). Par défaut, la valeur de PDO::SQLSRV_ATTR_DIRECT_QUERY est False (utilisez l’exécution d’instruction préparée).  
  
Si vous utilisez [PDO::query](../../connect/php/pdo-query.md), vous souhaiterez peut-être l’exécution directe. Avant d’appeler [PDO::query](../../connect/php/pdo-query.md), appelez [PDO::setAttribute](../../connect/php/pdo-setattribute.md) et PDO::SQLSRV_ATTR_DIRECT_QUERY la valeur True.  Chaque appel à [PDO::query](../../connect/php/pdo-query.md) peut être exécutée avec un autre paramètre de PDO::SQLSRV_ATTR_DIRECT_QUERY.  
  
Si vous utilisez [PDO::prepare](../../connect/php/pdo-prepare.md) et [PDOStatement::execute](../../connect/php/pdostatement-execute.md) pour exécuter une requête à plusieurs reprises à l’aide de paramètres liés, l’exécution d’instruction préparée permet d’optimiser l’exécution de la requête répétée.  Dans ce cas, appelez [PDO::prepare](../../connect/php/pdo-prepare.md) avec PDO::SQLSRV_ATTR_DIRECT_QUERY défini sur False dans le paramètre de tableau des options de pilote. Lorsque cela est nécessaire, vous pouvez exécuter des instructions préparées avec PDO::SQLSRV_ATTR_DIRECT_QUERY dont la valeur est False.  
  
Après avoir appelé [PDO::prepare](../../connect/php/pdo-prepare.md), la valeur de PDO::SQLSRV_ATTR_DIRECT_QUERY ne peut pas changer lors de l’exécution de la requête préparée.  
  
Si une requête requiert le contexte qui a été défini dans une requête précédente, exécutez vos requêtes avec PDO::SQLSRV_ATTR_DIRECT_QUERY dont la valeur est True. Par exemple, si vous utilisez des tables temporaires dans vos requêtes, PDO::SQLSRV_ATTR_DIRECT_QUERY doit être défini sur True.  
  
L’exemple suivant montre que lorsque le contexte à partir d’une instruction précédente est nécessaire, vous devez définir PDO::SQLSRV_ATTR_DIRECT_QUERY sur True.  Cet exemple utilise des tables temporaires, qui sont disponibles uniquement pour les instructions suivantes dans votre programme lorsque des requêtes sont exécutées directement.  
  
```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a> Voir aussi  
[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  
