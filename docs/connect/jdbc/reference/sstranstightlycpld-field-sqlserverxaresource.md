---
title: Champ SSTRANSTIGHTLYCPLD (SQLServerXAResource) | Documents Microsoft
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
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad4c44ab74c75a0f4d058edbad792cea721bdcd6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>Champ SSTRANSTIGHTLYCPLD (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Utilisé pour permettre les transactions XA étroitement couplées, qui ont des ID de transaction de branche XA (XID) différents mais le même ID de transaction global (GTRID).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Valeur de champ  
 Un **int** valeur de 32 768.  
  
## <a name="remarks"></a>Notes  
 Chaque transaction est identifiée par un ID de transaction de branche XA (XID) et un ID de transaction global (GTRID). Pour permettre aux applications d’utiliser des transactions XA étroitement couplées qui ont des XID différents mais le même gtrid, vous devez définir le [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) sur le paramètre d’indicateurs de la méthode XAResource.start. Pour plus d’informations sur l’utilisation de cet indicateur, consultez [compréhension des Transactions XA](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Champs SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [Membres de SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource, classe](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  