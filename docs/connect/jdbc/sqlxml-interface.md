---
title: Interface SQLXML | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 406c1c25c346680caba70c467e20e99df9977f13
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787201"
---
# <a name="sqlxml-interface"></a>Interface SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le pilote JDBC prend en charge l'API JDBC 4.0, ce qui permet l'introduction de l'interface java.sql.SQLXML. L’interface SQLXML définit des méthodes d’interaction et de manipulation des données XML. Le **SQLXML** mappe le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **xml** type de données.  
  
L’interface SQLXML fournit des méthodes pour accéder à la valeur XML comme un **chaîne**, un **lecteur** ou **Writer**, ou en tant qu’un **Stream**. La valeur XML est également accessible à l’aide de **Source** ou via la définition de **Result**, qui sont utilisés avec les API d’analyseurs XML tels que DOM (Document Object Model), SAX (Simple API for XML) et StAX (Streaming API for XML), ainsi que les transformations XSLT et XPath.  
  
## <a name="remarks"></a>Notes   

Le tableau suivant décrit les méthodes définies dans l'interface SQLXML :  
  
|Syntaxe de la méthode|Description de la méthode|  
|-------------------|------------------------|  
|[void free()](http://go.microsoft.com/fwlink/?LinkId=131685)|Cette méthode libère l'objet SQLXML ainsi que les ressources qu'il détient.|  
|[InputStream getBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131754)|Retourne un flux d'entrée pour la lecture des données de l'objet SQLXML.|  
|[Reader getCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131755)|Retourne les données **XML** en tant qu’objet java.io.Reader ou flux de caractères.|  
|[T étend Source T getSource (classe\<T > sourceClass)](http://go.microsoft.com/fwlink/?LinkId=131756)|Retourne un **Source** pour la lecture du **XML** valeur spécifiée par ce **SQLXML** objet.<br /><br /> **Remarque :**  La méthode getSource prend en charge les sources suivantes : javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource et java.io.InputStream.|  
|[String getString()](http://go.microsoft.com/fwlink/?LinkId=131757)|Retourne une représentation sous forme de chaîne de la valeur **XML** désignée par cet objet SQLXML.|  
|[OutputStream setBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131758)|Récupère un flux qui permet d’écrire la valeur **XML** représentée par cet objet SQLXML.|  
|[Writer setCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131759)|Retourne un flux à utiliser pour écrire la valeur **XML** représentée par cet objet SQLXML.|  
|[T étend setResult de résultat T (classe\<T > resultClass)](http://go.microsoft.com/fwlink/?LinkId=131760)|Retourne un **résultat** pour le paramètre de la **XML** valeur spécifiée par ce **SQLXML** objet.<br /><br /> **Remarque :** La méthode setResult prend en charge les sources suivantes : javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult et java.io.OutputStream.|  
|[void setString(String value)](http://go.microsoft.com/fwlink/?LinkId=131762)|Affecte la valeur XML désignée par cet objet SQLXML à la représentation **String** spécifiée.|  
  
Les applications ne peuvent lire et écrire des valeurs XML dans un objet SQLXML qu'une seule fois.  
  
Quand la méthode free() est appelée, l’objet SQLXML devient non valide et n’est plus accessible en lecture ni en écriture. Si l’application tente d’appeler sur cet objet SQLXML une autre méthode que free(), une exception est levée.  
  
L’objet SQLXML cesse ni lisible ni accessible en écriture lorsque l’application appelle les méthodes getter suivantes : getSource, getCharacterStream, getBinaryStream et getString.  
  
L’objet SQLXML devient accessible en lecture ni en écriture lorsque l’application appelle les méthodes setter suivantes : setResult, setCharacterStream, setBinaryStream et setString.  
  
## <a name="see-also"></a> Voir aussi  

[Prise en charge des données XML](../../connect/jdbc/supporting-xml-data.md)  
