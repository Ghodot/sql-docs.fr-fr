---
title: Afficher des valeurs en pourcentage sur un graphique à secteurs (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: d8c4cc67ad7a3719db277840e4ca535a373e8b44
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287015"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>Afficher des valeurs en pourcentage dans un graphique à secteurs (Générateur de rapports et SSRS)
  Par défaut, des catégories sont indiquées dans la légende pour identifier chaque valeur. Si vous avez créé des étiquettes de catégories pour le graphique à secteurs, vous avez la possibilité d'afficher des pourcentages dans la légende.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>Pour afficher des valeurs en pourcentage sous forme d'étiquettes sur un graphique à secteurs  
  
1.  Ajoutez un graphique à secteurs à votre rapport. Pour plus d’informations, consultez [Ajouter un graphique à un rapport &#40;Générateur de rapports et SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Dans l’aire de conception, cliquez avec le bouton droit sur le secteur, puis sélectionnez **Afficher les étiquettes de données**. Les étiquettes de données doivent apparaître dans chaque secteur du graphique.  
  
3.  Dans l’aire de conception, cliquez avec le bouton droit sur les étiquettes, puis sélectionnez **Propriétés de l’étiquette de la série**. La boîte de dialogue **Propriétés de l'étiquette de la série** s'affiche.  
  
4.  Type `#PERCENT` pour le **données de l’étiquette** option.  
  
5.  (Facultatif) Pour indiquer le nombre de décimales affichées sur l’étiquette, tapez « #PERCENT{P*n*} », où *n* correspond au nombre de décimales à afficher. Par exemple, pour ne pas afficher de décimale, tapez « #PERCENT{P0} ».  
  
### <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>Pour afficher des valeurs en pourcentage dans la légende d'un graphique à secteurs  
  
1.  Dans l’aire de conception, cliquez avec le bouton droit sur le graphique à secteurs, puis sélectionnez **Propriétés de la série**. La boîte de dialogue **Propriétés de la série** s’affiche.  
  
2.  Dans **légende**, type `#PERCENT` pour le **texte de légende personnalisé** propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques en secteurs &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Mise en forme de la légende sur un graphique &#40;Générateur de rapports et SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Étiquettes de Point de données d’affichage à l’extérieur un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Regrouper des petits secteurs sur un graphique à secteurs &#40;Générateur de rapports et SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
