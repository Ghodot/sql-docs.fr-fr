---
title: XML Data Modification Language (DML XML) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- modifying data [SQL Server], XML DML
- XML [SQL Server], DML
- XML DML [SQL Server]
- data modification language [XML DML]
- data modifications [XML DML]
- DML [XML in SQL Server]
- XQuery, XML DML
- xml data type [SQL Server], XML DML
ms.assetid: 20ce50d2-c07b-4e41-93a7-1380d2cd49cb
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18fb5825297754c59f2824b6f05150ddaed7bb9c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-modification-language-xml-dml"></a>Langage de modification de données XML (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le langage de modification de données XML (XML DML) est une extension du langage XQuery. Tel qu'il est défini par le consortium W3C, le langage XQuery ne possède pas la partie de manipulation des données (DML). Le langage XML DML présenté dans cette rubrique, ainsi que le langage XQuery, fournit une requête pleinement fonctionnel et un langage de modification de données que vous pouvez utiliser sur le **xml** type de données.  
  
 Le XML DML ajoute dans XQuery les mots clés respectant la casse suivants :  
  
-   **INSERT**  
  
-   **supprimer**  
  
-   **Remplacez la valeur de**  
  
 Comme décrit dans [Type de données XML et les colonnes &#40; SQL Server &#41; ](../../relational-databases/xml/xml-data-type-and-columns-sql-server.md), vous pouvez créer des variables et des colonnes de la **xml** de type et leur attribuer des documents XML ou des fragments. Pour modifier ou mettre à jour ces instances XML, procédez comme suit :  
  
-   Utilisez le [xml Type de données de la méthode modify())](../../t-sql/xml/modify-method-xml-data-type.md) de la **xml** type de données.  
  
-   Spécifiez les instructions XML DML appropriées à l’intérieur de la **modify()** (méthode).  
  
 Notez que certains attributs ne peuvent pas être insérés ou supprimés, et que leur valeur ne peut pas être modifiée. Exemple :  
  
-   Pour non typés **xml,** les attributs sont **xmlns**, **xmlns :\***, et **XML : base**.  
  
-   Pour typées **xml** uniquement, les attributs sont **xsi : nil**, et **xsi : type**.  
  
 Autres restrictions :  
  
-   Pour non typés **xml**, insertion de l’attribut **XML : base** échoue.  
  
-   Pour typées **xml**, la suppression et modification de la **xsi : nil** attribut échouera. Pour non typées **xml**, vous pouvez supprimer l’attribut ou modifier sa valeur.  
  
-   Pour typées **xml**, modification de la valeur de la **msdata** attribut échouera. Pour non typées **xml**, vous pouvez modifier la valeur d’attribut.  
  
 Lorsque vous modifiez une instance XML typée, le format final doit être une instance valide de ce type. Dans le cas contraire, une erreur de validation est retournée.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer &#40; XML DML &#41;](../../t-sql/xml/insert-xml-dml.md)   
 [supprimer le s &#40; XML DML &#41;](../../t-sql/xml/delete-xml-dml.md)   
 [Remplacez la valeur de &#40; XML DML &#41;](../../t-sql/xml/replace-value-of-xml-dml.md)   
 [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [Méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)  
  
  