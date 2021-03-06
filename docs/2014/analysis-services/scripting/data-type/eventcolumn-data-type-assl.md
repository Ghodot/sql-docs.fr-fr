---
title: Type de données EventColumn (ASSL) | Microsoft Docs
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
- EventColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EventColumn
helpviewer_keywords:
- EventColumn data type
ms.assetid: c0009f1d-d136-4155-9a1b-7baacda4b552
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f99484bdc41228dee28f6437631e0c05a542d9d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293319"
---
# <a name="eventcolumn-data-type-assl"></a>Type de données EventColumn (ASSL)
  Définit un type de données primitif qui représente une colonne d’informations à capturer pour un [événement](../objects/event-element-assl.md) élément en tant que partie d’un [Trace](../objects/trace-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
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
|Éléments enfants|[ColumnID](../properties/columnid-element-eventcolumn-assl.md)|  
|Éléments dérivés|[Colonne](../objects/column-element-assl.md) ([colonnes](../collections/columns-element-assl.md) collection de [Trace](../objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Events &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
