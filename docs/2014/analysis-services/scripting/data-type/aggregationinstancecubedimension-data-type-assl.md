---
title: Type de données AggregationInstanceCubeDimension (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AggregationInstanceCubeDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstanceCubeDimension data type
ms.assetid: b321ad9e-f034-4a7b-b0b7-8ba5fb162e7e
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1e6c6cc46c975eb89b1ecde559f87328005eb7a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237519"
---
# <a name="aggregationinstancecubedimension-data-type-assl"></a>Type de données AggregationInstanceCubeDimension (ASSL)
  Définit un type de données primitif qui fournit des informations sur une dimension de cube utilisée par une instance d'agrégation.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AggregationInstanceCubeDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <KeyColumns>...</KeyColumns>  
   <Attributes>...</Attributes>  
</AggregationInstanceCubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Attributes](../collections/attributes-element-assl.md), [CubeDimensionID](../properties/id-element-assl.md), [KeyColumns](../collections/columns-element-assl.md)|  
|Éléments dérivés|[Dimension](../objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
