---
title: Élément KpiGoal (CSDLBI) | Microsoft Docs
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
ms.assetid: fd8afbe7-b57d-4b47-862d-eb7b2489c327
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b64e3124ba7a848921e1b0844b20d03e9aa82af4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165240"
---
# <a name="kpigoal-element-csdlbi"></a>Élément KpiGoal (CSDLBI)
  L'élément KpiGoal fournit une référence à la colonne utilisée pour définir l'objectif d'un indicateur de performance clé (KPI).  
  
 Dans CSDLBI, les indicateurs de performance clés sont basés sur les mesures, et l’élément Measure contient la formule (le cas échéant), tandis que d’autres métadonnées associées à l’indicateur de performance clé sont définies en tant que partie intégrante de [l’élément KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md).  L'élément Kpigoal est un sous-type de l'élément Kpi.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les attributs qui définissent l'élément KpiGoal.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|PropertyRef|Oui|Référence à la colonne qui contient la valeur de l'objectif KPI.<br /><br /> L'élément Kpigoal doit contenir exactement un élément PropertyRef.<br /><br /> Consultez [Élément PropertyRef &#40;CSDLBI&#41;](propertyref-element-csdlbi.md).|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un indicateur de performance clé de l'exemple de modèle AdventureWorks.  
  
```  
  
<Property Name="InternetCurrentSalesPerformance" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre un indicateur de performance clé du cube Contoso Operations.  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément KPI &#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
  
