---
title: Type d’élément (MeasureGroupAttribute) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Type Element (MeasureGroupAttribute)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 93740504-297a-4a06-ab3e-b598e466eebb
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 49155b00ca70c613ffec01e898e7c6f071e24c84
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254851"
---
# <a name="type-element-measuregroupattribute-assl"></a>Élément Type (MeasureGroupAttribute) (ASSL)
  Contient le type d’un [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroupAttribute>  
   ...  
   <Type>...</Type>  
   ...  
</MeasureGroupAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Régulière*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Régulière*|Représente un attribut régulier.|  
|*Granularité*|Represents a granularity attribute.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `Type` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MeasureGroupAttributeType>.  
  
 L’élément qui correspond au parent de `Type` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs d’élément &#40;ASSL&#41;](../collections/attributes-element-assl.md)   
 [Type de données RegularMeasureGroupDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
