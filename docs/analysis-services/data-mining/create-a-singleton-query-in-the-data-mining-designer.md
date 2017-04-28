---
title: "cr&#233;er une requ&#234;te singleton dans le Concepteur d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "requêtes singleton [Analysis Services]"
  - "Prédiction de modèle d’exploration de données [Analysis Services], requêtes singletons"
ms.assetid: 6cdca8a0-cf16-46eb-a652-0bff820625ab
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# cr&#233;er une requ&#234;te singleton dans le Concepteur d&#39;exploration de donn&#233;es
  Une requête singleton est utile si vous voulez créer une prédiction pour un seul cas. Pour plus d’informations sur les requêtes singleton, consultez [Requêtes d’exploration de données](../../analysis-services/data-mining/data-mining-queries.md).  
  
 Sous l’onglet **Prévision de modèle d’exploration de données** du Concepteur d’exploration de données, vous pouvez créer différents types de requêtes. Vous pouvez créer une requête en utilisant le concepteur ou en tapant des instructions DMX (Data Mining Extensions). Vous pouvez également utiliser le concepteur pour commencer, puis modifier la requête créée en modifiant les instructions DMX ou en ajoutant une clause WHERE ou ORDER BY.  
  
 Pour basculer entre l'affichage de conception de requête et l'affichage du texte de la requête, cliquez sur le premier bouton dans la barre d'outils. Lorsque vous vous trouvez dans la vue de texte de requête, vous pouvez afficher le code créé par le Générateur de requêtes de prédiction. Vous pouvez également exécuter la requête, la modifier et exécuter la requête modifiée. Toutefois, la requête modifiée n'est pas conservée si vous réaffichez la vue de conception de requête.  
  
 Le code suivant montre un exemple de requête singleton sur le modèle de publipostage ciblé TM_Decision_Tree.  
  
```  
SELECT [Bike Buyer], PredictProbability([Bike Buyer]) as ProbableBuyer  
FROM [TM_Decision_Tree]  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 Les étapes suivantes expliquent comment créer cette requête de prédiction.  
  
### Pour créer une requête singleton à l'aide du Concepteur d'exploration de données  
  
1.  Cliquez sur **Prévision de modèle d’exploration de données** dans le Concepteur d’exploration de données.  
  
2.  Cliquez sur **Sélectionner un modèle** dans la table **Modèle d’exploration de données**.  
  
     La boîte de dialogue **Sélectionner un modèle d’exploration de données** s’ouvre pour afficher toutes les structures d’exploration de données qui existent dans le projet actuel.  
  
     Sélectionnez le modèle à utiliser pour créer une prédiction.  
  
     Par exemple, pour créer l’exemple de code donné au début de cette rubrique, sélectionnez TM_Decision_Tree, puis cliquez sur **OK**.  
  
3.  Cliquez sur **Requête singleton** dans la barre d’outils de l’onglet **Prévision de modèle d’exploration de données**.  
  
     La table **Entrée de requête singleton** s’affiche dans l’onglet avec les colonnes mappées automatiquement aux colonnes de la table **Modèle d’exploration de données**.  
  
4.  Dans la table **Entrée de requête singleton**, sélectionnez les valeurs dans la colonne **Valeur** pour décrire le cas pour lequel vous voulez créer une prévision.  
  
     Par exemple, sélectionnez **2** pour **Number Children At Home**, puis tapez **45** pour **Age**.  
  
5.  Faites glisser une colonne prédictible de la table **Modèle d’exploration** vers la colonne **Source** au bas de l’onglet. Vous pouvez éventuellement taper un alias pour la colonne.  
  
     Par exemple, faites glisser **Bike Buyer** vers la colonne **Source**.  
  
6.  Ajoutez des fonctions supplémentaires à la requête en sélectionnant **Fonction de prédiction** ou **Expression personnalisée** dans la liste déroulante de la colonne **Source**.  
  
     Par exemple, cliquez sur **Fonction de prédiction** et sélectionnez **PredictProbability**.  
  
7.  Cliquez sur **Critères/Argument** dans la ligne **PredictProbability**, puis tapez le nom de la colonne à prédire et éventuellement une valeur spécifique à prédire.  
  
     Par exemple, tapez **[Bike Buyer], 1**.  
  
8.  Cliquez sur la zone **Alias** dans la ligne **PredictProbability**, puis tapez un nom pour faire référence à la nouvelle colonne.  
  
     Par exemple, tapez **ProbableBuyer**.  
  
9. Cliquez sur **Basculer vers l’affichage du résultat de la requête** dans la barre d’outils de l’onglet **Prévision de modèle d’exploration de données**.  
  
     Un nouvel écran s'affiche avec le résultat de la requête. Pour examiner l’instruction DMX que vous venez de créer, cliquez sur **SQL**.  
  
## Voir aussi  
 [Requêtes de prédiction &#40;Exploration de données&#41;](../../analysis-services/data-mining/prediction-queries-data-mining.md)  
  
  