---
title: supportsOuterJoins, méthode (SQLServerDatabaseMetaData)
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsOuterJoins
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9dd19257-b120-4b74-8055-6570a343fc8d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82235669c871943f1560224a4adf0c63e74bb66d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37988391"
---
# <a name="supportsouterjoins-method-sqlserverdatabasemetadata"></a>Méthode supportsOuterJoins (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge certaines formes de jointures externes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsOuterJoins()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode supportsOuterJoins est spécifiée par la méthode supportsOuterJoins dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
