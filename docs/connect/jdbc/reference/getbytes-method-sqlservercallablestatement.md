---
title: "Méthode getBytes (SQLServerCallableStatement) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6e88cea-54b3-4d18-a9af-db54abf19f45
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 99f9e5cc54854e1406e4375b358657b3cbfde192
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getbytes-method-sqlservercallablestatement"></a>Méthode getBytes (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant que tableau d'octets.  
  
## <a name="overload-list"></a>Liste de surcharge  
  
|Nom| Description|  
|----------|-----------------|  
|[getBytes (int)](../../../connect/jdbc/reference/getbytes-method-int.md)|Récupère la valeur du paramètre désigné en tant que valeur de tableau d'octets en fonction de l'index de paramètre.|  
|[getBytes (java.lang.String)](../../../connect/jdbc/reference/getbytes-method-java-lang-string.md)|Récupère la valeur du paramètre désigné en tant que valeur de tableau d'octets en fonction du nom du paramètre.|  
  
## <a name="remarks"></a>Notes  
 Dans une version précédente de la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], vous pouviez utiliser SQLServerCallableStatement.getBytes pour convertir des valeurs entre des tableaux d’octets et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] type de données **date**, **temps**, **datetime2**, ou **datetimeoffset**. À présent, l'utilisation de cette méthode avec ces types de données lève une exception indiquant que la conversion n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  