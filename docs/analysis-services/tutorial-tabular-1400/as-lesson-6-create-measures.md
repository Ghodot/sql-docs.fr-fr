---
title: 'Leçon du didacticiel Analysis Services 6 : créer des mesures | Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9b466a703dd04a53c6ebf7c6fac624476abcc52
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43093962"
---
# <a name="create-measures"></a>Créer des mesures

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Dans cette leçon, vous créez des mesures à inclure dans votre modèle. Comme pour les colonnes calculées que vous avez créé, une mesure est un calcul créé à l’aide d’une formule DAX. Toutefois, contrairement aux colonnes calculées, les mesures sont évaluées selon un utilisateur a sélectionné *filtre*. Par exemple, une colonne particulière ou segment ajouté au champ étiquettes de ligne dans un tableau croisé dynamique. Une valeur pour chaque cellule dans le filtre est ensuite calculée par la mesure appliquée. Les mesures sont des calculs puissants et flexibles que vous souhaitez inclure dans quasiment tous les modèles tabulaires pour effectuer des calculs dynamiques sur des données numériques. Pour plus d’informations, consultez [mesures](../tabular-models/measures-ssas-tabular.md).
  
Pour créer des mesures, vous utilisez le *grille de mesures*. Par défaut, chaque table possède une grille de mesures vide ; Toutefois, vous en général, ne créez pas des mesures pour chaque table. La grille de mesures s'affiche sous une table au sein du générateur de modèles dans la vue de données. Pour cacher ou afficher la grille de mesures d'une table, cliquez sur le menu **Table** , puis sur **Afficher la grille de mesures**.  
  
Vous pouvez créer une mesure en cliquant sur une cellule vide dans la grille de mesures, puis en tapant une formule DAX dans la barre de formule. Lorsque vous appuyez sur ENTRÉE pour terminer la formule, la mesure, puis s’affiche dans la cellule. Vous pouvez également créer des mesures à l’aide d’une fonction d’agrégation standard en cliquant sur une colonne, puis en cliquant sur le bouton Somme automatique (**∑**) dans la barre d’outils. Les mesures créées à l’aide de la fonction Somme automatique apparaissent dans la cellule de grille de mesures directement sous la colonne, mais peuvent être déplacés.  
  
Dans cette leçon, vous créez des mesures en entrant une formule DAX dans la barre de formule et à l’aide de la fonction Somme automatique.  
  
Durée estimée pour effectuer cette leçon : **30 minutes**  
  
## <a name="prerequisites"></a>Prérequis  

Cet article fait partie d’un didacticiel de modélisation tabulaire, qui doit être effectué dans l’ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [leçon 5 : créer des colonnes calculées](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Créer des mesures  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Pour créer une mesure DaysCurrentQuarterToDate dans la table DimDate  
  
1.  Dans le Concepteur de modèles, cliquez sur le **DimDate** table.  
  
2.  Dans la grille de mesures, cliquez sur la cellule vide en haut à gauche.  
  
3.  Dans la barre de formule, entrez la formule suivante :  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Notez que la cellule en haut à gauche contient maintenant une mesure nommée **DaysCurrentQuarterToDate**, suivie du résultat, **92**. Le résultat n’est pas pertinent à ce stade, car aucun filtre de l’utilisateur n’a été appliqué.
    
      ![en tant que newmeasure de lesson6](../tutorial-tabular-1400/media/as-lesson6-newmeasure.png) 
    
    Contrairement aux colonnes calculées, avec les formules de mesure, vous pouvez taper le nom de mesure, suivi par un signe deux-points, suivi par l’expression de formule.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Pour créer une mesure DaysInCurrentQuarter dans la table DimDate  
  
1.  Avec le **DimDate** toujours active dans le Générateur de modèles, dans la grille de mesures, cliquez sur la cellule vide sous la mesure que vous avez créé.  
  
2.  Dans la barre de formule, entrez la formule suivante :  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    Lorsque vous créez un rapport de comparaison entre une période incomplète et la période précédente. La formule doit calculer la proportion de la période qui s’est écoulé et comparez-la à la même partie de la période précédente. Dans ce cas, [DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] donne la proportion écoulé dans la période actuelle.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Pour créer une mesure InternetDistinctCountSalesOrder dans la table FactInternetSales  
  
1.  Cliquez sur le **FactInternetSales** table.   
  
2.  Cliquez sur le **SalesOrderNumber** en-tête de colonne.  
  
3.  Dans la barre d’outils, cliquez sur la flèche du bas en regard du bouton de somme automatique (**∑**), puis sélectionnez **DistinctCount**.  
  
    La fonction de somme automatique crée automatiquement une mesure pour la colonne sélectionnée à l'aide de la formule de regroupement standard DistinctCount.  
    
       ![en tant que newmeasure2 de lesson6](../tutorial-tabular-1400/media/as-lesson6-newmeasure2.png)
  
4.  Dans la grille de mesures, cliquez sur la nouvelle mesure, puis, dans le **propriétés** fenêtre, dans **nom de la mesure**, renommez la mesure en **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Pour créer des mesures supplémentaires dans la table FactInternetSales  
  
1.  En utilisant la fonction de somme automatique, créez et nommez les mesures suivantes :  

    |colonne|Nom de la mesure|Somme automatique (∑)|Formule|  
    |----------------|----------|-----------------|-----------|  
    |SalesOrderLineNumber|InternetOrderLinesCount|Compter|=COUNTA([SalesOrderLineNumber])|  
    |OrderQuantity|InternetTotalUnits|SUM|=SUM([OrderQuantity])|  
    |DiscountAmount|InternetTotalDiscountAmount|SUM|=SUM([DiscountAmount])|  
    |TotalProductCost|InternetTotalProductCost|SUM|=SUM([TotalProductCost])|  
    |SalesAmount|InternetTotalSales|SUM|=SUM([SalesAmount])|  
    |Margin|InternetTotalMargin|SUM|=SUM([Margin])|  
    |TaxAmt|InternetTotalTaxAmt|SUM|=SUM([TaxAmt])|  
    |Freight|InternetTotalFreight|SUM|=SUM([Freight])|  
  
2.  En cliquant sur une cellule vide dans la grille de mesures et à l’aide de la barre de formule, créez, les mesures personnalisées suivantes dans l’ordre :  
  
      ```
      InternetPreviousQuarterMargin:=CALCULATE([InternetTotalMargin],PREVIOUSQUARTER('DimDate'[Date]))
      ```
      
      ```
      InternetCurrentQuarterMargin:=TOTALQTD([InternetTotalMargin],'DimDate'[Date])
      ```
  
      ```
      InternetPreviousQuarterMarginProportionToQTD:=[InternetPreviousQuarterMargin]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
      ```
      InternetPreviousQuarterSales:=CALCULATE([InternetTotalSales],PREVIOUSQUARTER('DimDate'[Date]))
      ```
  
      ```
      InternetCurrentQuarterSales:=TOTALQTD([InternetTotalSales],'DimDate'[Date])
      ```
      
      ```
      InternetPreviousQuarterSalesProportionToQTD:=[InternetPreviousQuarterSales]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
Les mesures créées pour la table FactInternetSales peuvent être utilisées pour analyser les données financières critiques telles que les ventes, les coûts et marge pour les éléments définis par le filtre sélectionné d’utilisateur.  
  
## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Leçon 7 : Créer des indicateurs de Performance clés](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  

  
