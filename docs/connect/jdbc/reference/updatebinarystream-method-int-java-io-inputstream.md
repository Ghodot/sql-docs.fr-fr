---
title: updateBinaryStream, méthode (int, java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d871361c45b47444427a33dd85c9b31fcc35d8b0
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784020"
---
# <a name="updatebinarystream-method-int-javaioinputstream"></a>Méthode updateBinaryStream (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec la valeur de flux binaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
 *x*  
  
 Un objet InputStream.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode updateBinaryStream est spécifiée par la méthode updateBinaryStream dans l’interface java.sql.ResultSet.  
  
 À l’aide de cette méthode pour le **image**, **texte**, et **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] types de données peuvent avoir un impact sur les performances.  
  
 Cette méthode passe les octets à partir d’un objet InputStream à des colonnes binaires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sélectionnées, telles que binary, varbinary, varbinary(max), image, xml et udt. La mise à jour de colonnes de caractères n'est pas prise en charge avec cette méthode. Pour mettre à jour des colonnes de caractères avec InputStream, utilisez la méthode [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md).  
  
## <a name="see-also"></a> Voir aussi  
 [updateBinaryStream, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
