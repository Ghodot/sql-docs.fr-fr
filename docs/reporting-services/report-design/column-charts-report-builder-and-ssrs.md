---
title: "Column Charts (Report Builder and SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae8c138b-e356-4ad8-862c-a4a8d0c04149
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Column Charts (Report Builder and SSRS)
  Un histogramme affiche une série sous la forme d'un ensemble de barres verticales regroupées par catégorie. Les histogrammes sont utiles pour montrer des modifications de données sur une période ou pour illustrer des comparaisons entre éléments. L'histogramme ordinaire est étroitement lié au graphique à barres, qui affiche une série sous la forme d'un ensemble de barres horizontales, ainsi qu'au graphique d'étendue en colonnes, qui affiche une série sous la forme d'un ensemble de barres verticales avec des points de départ et de fin variables. Pour plus d’informations, consultez [Graphiques à barres &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md) et [Graphiques d’étendue&#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md).  
  
 L'histogramme convient bien pour ces données, car les trois séries partagent une période commune, ce qui permet d'effectuer des comparaisons valables.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Variantes d'un histogramme  
  
-   **Empilé**. Histogramme où plusieurs séries sont empilées verticalement. Si le graphique ne comporte qu'une seule série, l'histogramme empilé affichera la même chose qu'un histogramme.  
  
-   **Empilé 100 %**. Histogramme où plusieurs séries sont empilées verticalement pour occuper 100 % de la zone de graphique. Si le graphique ne comporte qu'une seule série, toutes les barres s'ajusteront à 100 % de la zone de graphique.  
  
-   **Groupé 3D**. Histogramme qui affiche les séries individuelles en lignes séparées sur un graphique 3D.  
  
-   **Cylindre 3D**. Histogramme dont les barres ont la forme de cylindres sur un graphique 3D.  
  
-   **Histogramme**. Histogramme que le graphique calcule afin que ses barres soient ordonnées en distribution normale.  
  
-   **Pareto**. Histogramme dont les barres sont ordonnées de la plus haute à la plus basse.  
  
## Considérations relatives aux données pour un histogramme  
  
-   Les graphiques à barres et histogrammes sont plus couramment utilisés pour montrer des comparaisons entre groupes. Si le graphique comporte plus de trois séries, pensez plutôt à utiliser un graphique à barres empilées ou un histogramme empilé. Si le graphique comporte plusieurs séries, vous pouvez également rassembler les graphiques à barres empilées ou les histogrammes empilés en plusieurs groupes. Pour plus d’informations, consultez [Graphiques à barres &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md).  
  
-   Dans un histogramme, vous disposez de moins de place pour l'affichage horizontal des étiquettes de l'axe des abscisses. Si vos étiquettes sont assez longues, envisagez d'utiliser un graphique à barres ou de modifier l'angle de rotation de l'étiquette.  
  
-   Vous pouvez ajouter des styles de dessin spéciaux aux barres d'un histogramme pour augmenter l'impact visuel. Les styles de dessin incluent les effets de coin, de relief, de cylindre et de clair à sombre. Ces effets sont destinés à améliorer l'apparence de votre graphique 2D. Si vous utilisez un graphique 3D, les styles de dessin seront toujours appliqués, mais ils peuvent ne pas avoir le même effet. Pour plus d’informations sur l’ajout d’un style de dessin à un graphique à barres, consultez [Ajouter des styles de biseau, du relief et des textures à un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs.md).  
  
-   La possibilité d'afficher votre graphique sous la forme d'un histogramme ou diagramme de Pareto est une spécificité des histogrammes. Pour ce faire, attribuez à la propriété ShowColumnAs la valeur **Histogramme** ou **Pareto** et définissez-la sur **true** dans la fenêtre Propriétés.  
  
## Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Types de graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [Graphiques à barres &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Graphiques d’étendue &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md)   
 [Didacticiel : Ajout d’un graphique à barres à un rapport &#40;Générateur de rapports&#41;](../../reporting-services/tutorial-add-a-bar-chart-to-your-report-report-builder.md)   
 [Points de données vides et Null dans les graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  