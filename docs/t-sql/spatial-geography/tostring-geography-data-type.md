---
title: "ToString (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ToString (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString method
ms.assetid: 045c12fa-8fc6-441a-9500-7021cb4ff13e
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 34e028dcd1a9fd141d0771e1b410d469d6dbd47c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="tostring-geography-data-type"></a>ToString (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la représentation de la réplication continue en cluster (WKT, Open Geospatial Consortium (OGC) Well-Known Text) d’un **geography** instance augmentée des Z (élévation) et les valeurs M (mesure) apportées par l’instance.  
  
 Ces données geography type prend en charge de la méthode **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **nvarchar (max)**  
  
 Type de retour CLR : **SqlString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne la chaîne « Null » lorsqu'elle est appelée sur des instances Null. Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le jeu de résultats possibles sur le serveur a été étendu aux **FullGlobe** instances. Cette méthode retourne la même valeur que `AsTextZM()`.  
  
 Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée un `LineString` instance et utilise `ToString()` pour retourner la description de l’instance.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [AsTextZM &#40;type de données geography&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  