---
title: Interface ISQLServerStatement | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f83b514-6e76-4f37-baf3-a10db2010e7c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8865b6478b685231c4421166134fabde57aa70e7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="isqlserverstatement-interface"></a>Interface ISQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente l'implémentation de base de la fonctionnalité d'instruction JDBC. Cette interface a été ajoutée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] version 3.0 du pilote JDBC.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** java.sql.Statement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public interface ISQLServerStatement  
```  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée par [classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 Cette interface expose les éléments suivants [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-des méthodes spécifiques :  
  
|Méthode|Pour plus d'informations, consultez|  
|------------|-------------------------------|  
|public String getResponseBuffering|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|  
|public void setResponseBuffering|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  