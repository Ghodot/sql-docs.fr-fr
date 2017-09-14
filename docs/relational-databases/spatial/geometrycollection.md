---
title: GeometryCollection | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ad3b942675c879183f8be2fe8bc8b82effee8bf2
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="geometrycollection"></a>GeometryCollection
  Un objet **GeometryCollection** est une collection de zéro ou plusieurs instances de **geometry** ou **geography** . Un objet **GeometryCollection** peut être vide.  
  
## <a name="geometrycollection-instances"></a>Instances GeometryCollection  
  
### <a name="accepted-instances"></a>Instances acceptées  
 Pour qu’une instance **GeometryCollection** soit acceptée, il faut qu’il s’agisse d’une instance **GeometryCollection** vide ou que toutes les instances composant l’instance **GeometryCollection** soient des instances acceptées. L'exemple suivant illustre des instances acceptées.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 L’exemple suivant lève une exception `System.FormatException` , car l’instance **LinesString** dans l’instance **GeometryCollection** n’est pas acceptée.  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a>Instances valides  
 Une instance **GeometryCollection** est valide quand toutes les instances qui composent l’instance **GeometryCollection** sont valides. L’exemple suivant illustre trois instances **GeometryCollection** valides et une instance non valide.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` n’est pas valide car l’instance **Polygon** dans l’instance **GeometryCollection** n’est pas valide.  
  
 Pour plus d’informations sur les instances acceptées et valides, consultez [Point](../../relational-databases/spatial/point.md), [MultiPoint](../../relational-databases/spatial/multipoint.md), [LineString](../../relational-databases/spatial/linestring.md), [MultiLineString](../../relational-databases/spatial/multilinestring.md), [polygone](../../relational-databases/spatial/polygon.md)et [MultiPolygon](../../relational-databases/spatial/multipolygon.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant instancie un objet `geometry``GeometryCollection` avec les valeurs Z dans SRID 1 contenant une instance `Point` et une instance `Polygon` .  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  