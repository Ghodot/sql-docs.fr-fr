---
title: Créer une requête de prédiction à l’aide du Générateur de requêtes de prédiction | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- Mining Model Prediction [Analysis Services], prediction queries
ms.assetid: e02836e5-dd8c-4c97-a078-840ae79d3660
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed339e0e0f4abb626233a5b3193c799c3041b6f5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167650"
---
# <a name="create-a-prediction-query-using-the-prediction-query-builder"></a>Créer une requête de prédiction à l’aide du Générateur de requêtes de prédiction
  Vous pouvez créer des requêtes de prédiction soit quand vous générez une solution d’exploration de données dans BI Development Studio, soit en cliquant avec le bouton droit sur un modèle d’exploration de données existant dans SQL Server Management Studio, puis en choisissant l’option **Générer une requête de prédiction**.  
  
 Le **Générateur de requêtes de prédiction** dispose des trois modes de création suivants, que vous pouvez utiliser tour à tour en cliquant sur les icônes dans l’angle supérieur gauche.  
  
-   **Conception**  
  
-   **Requête**  
  
-   **Result**  
  
 Le mode**Création** vous permet de générer une requête de prédiction en choisissant des données d’entrée, en mappant les données au modèle, puis en ajoutant des fonctions de prédiction dans les instructions que vous créez à l’aide de la grille. La grille de création contient ces blocs de construction :  
  
 **Source**  
 Choisissez la source de la nouvelle colonne. Vous pouvez utiliser des colonnes du modèle d'exploration de données, les tables d'entrée incluses dans la vue de source de données, une fonction de prédiction ou une expression personnalisée.  
  
 **Field**  
 Détermine la colonne ou la fonction spécifique associée à la sélection dans la colonne **Source** .  
  
 **Alias**  
 Détermine comment la colonne doit être nommée dans le jeu de résultats.  
  
 **Afficher**  
 Détermine si la sélection dans la colonne **Source** doit être affichée dans les résultats.  
  
 **Grouper**  
 Utilise la colonne **et/ou** pour grouper des expressions à l’aide de parenthèses. Par exemple, (expr1 ou expr2) et expr3.  
  
 **et/ou**  
 Crée une logique dans la requête. Par exemple, (expr1 ou expr2) et expr3.  
  
 **Critères/Argument**  
 Spécifie une condition ou une expression utilisateur qui s'applique à la colonne. Vous pouvez faire glisser des colonnes à partir des tables dans la cellule.  
  
 Le mode de**Requête** fournit un éditeur de texte qui vous donne un accès direct au langage DMX (Data Mining Extensions), ainsi qu’une vue des données d’entrée et des colonnes du modèle. Quand vous sélectionnez le mode **Requête** , la grille que vous avez utilisée pour définir la requête est remplacée par un éditeur de texte de base. Vous pouvez utiliser cet éditeur pour copier et enregistrer les requêtes que vous avez composées, ou pour coller les requêtes DMX existantes et du Presse-papiers, puis pour les exécuter.  
  
 La vue**Résultat** exécute la requête actuelle et affiche les résultats dans une grille. Si les données sous-jacentes ont changé et que vous souhaitez réexécuter la requête, cliquez sur le bouton Lecture dans la barre d'état.  
  
 Vous pouvez concevoir une requête d'exploration de données à l'aide d'une combinaison d'outils visuels et de l'éditeur de texte. Si vous apportez des modifications à la requête dans l’éditeur de texte et que vous revenez en mode **Création** , toutes les modifications sont perdues et la requête initiale créée par le Générateur de requêtes de prédiction est restaurée. Cette rubrique vous décrit pas à pas comment utiliser le Générateur de requêtes graphiques.  
  
### <a name="to-create-a-prediction-query"></a>Pour créer une requête de prédiction  
  
1.  Cliquez sur **Prévision de modèle d’exploration de données** dans le Concepteur d’exploration de données.  
  
2.  Cliquez sur **Sélectionner un modèle** dans la table **Modèle d’exploration de données** .  
  
     La boîte de dialogue **Sélectionner un modèle d’exploration de données** s’ouvre pour afficher toutes les structures d’exploration de données qui existent dans le projet actuel.  
  
3.  Sélectionnez le modèle pour lequel vous voulez créer une prédiction, puis cliquez sur **OK**.  
  
4.  Dans la table **Sélectionner une ou plusieurs tables d’entrée** , cliquez sur **Sélectionner la table de cas**.  
  
     La boîte de dialogue **Sélectionner une table** s’ouvre.  
  
5.  Dans la liste **Source de données** , sélectionnez la source de données qui contient les données pour lesquelles vous voulez créer une prédiction.  
  
6.  Dans la zone **Nom de la table/vue** , sélectionnez la table qui contient les données pour lesquelles vous voulez créer une prédiction, puis cliquez sur **OK**.  
  
     Une fois la table d'entrée sélectionnée, le Générateur de requêtes de prédiction crée un mappage par défaut entre le modèle d'exploration de données et la table d'entrée en fonction des noms des colonnes. Pour supprimer un mappage, cliquez pour sélectionner la ligne qui lie la colonne de la table **Modèle d’exploration de données** à la colonne associée de la table **Sélectionner une ou plusieurs tables d’entrée** et appuyez sur Suppr. Vous pouvez également créer des mappages manuellement. Pour ce faire, cliquez sur une colonne dans la table **Sélectionner une ou plusieurs tables d’entrée** et faites-la glisser vers la colonne correspondante dans la table **Modèle d’exploration de données** .  
  
7.  Ajoutez à la grille Générateur de requêtes de prédiction n'importe quelles combinaisons constituées des trois types d'informations suivants :  
  
    -   Colonnes prédictibles de la zone **Modèle d’exploration de données** .  
  
    -   Toute combinaison de colonnes d’entrée de la zone **Sélectionner une ou plusieurs tables d’entrée** .  
  
    -   Fonctions de prédiction  
  
8.  Exécutez la requête en cliquant sur le premier bouton de la barre d’outils de l’onglet **Prévision de modèle d’exploration de données** et en sélectionnant **Résultat**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une requête Singleton dans le Concepteur d’exploration de données](create-a-singleton-query-in-the-data-mining-designer.md)   
 [Requêtes d’exploration de données](data-mining-queries.md)  
  
  
