---
title: Type de données MeasureGroupHierarchy (ASSL) | Microsoft Docs
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
- MeasureGroupHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupHierarchy
helpviewer_keywords:
- MeasureGroupHierarchy data type
ms.assetid: 63c2fd97-d7ad-4715-8c49-24d684bc92d7
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e34d9c7983ea1a94c8c303e746e28191318f2c58
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245639"
---
# <a name="measuregrouphierarchy-data-type-assl"></a>Type de données MeasureGroupHierarchy (ASSL)
  Définit un type de données primitif qui fournit des informations sur une hiérarchie dans un groupe de mesures.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroupHierarchy>  
   <HierarchyID>...</HierarchyID>  
      <Annotations>...</Annotations>  
</MeasureGroupHierarchy>  
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
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [HierarchyID](../properties/id-element-assl.md)|  
|Éléments dérivés|[Hierarchy](../objects/hierarchy-element-assl.md) (collection[Hierarchies](../collections/hierarchies-element-assl.md) de [RegularMeasureGroupDimension](dimension-data-type-assl.md))|  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
