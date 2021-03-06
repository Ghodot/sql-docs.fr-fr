---
title: Modification des mesures | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 447032ab32e222f3827c34020aef612e8125a518
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232379"
---
# <a name="modifying-measures"></a>Modification des mesures
  Vous pouvez utiliser la propriété **FormatString** pour définir des paramètres de mise en forme qui contrôlent comment les mesures sont affichées aux utilisateurs. Au cours de cette tâche, vous allez spécifier des propriétés de formatage pour les mesures relatives aux devises et aux pourcentages dans le cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
### <a name="to-modify-the-measures-of-the-cube"></a>Pour modifier les mesures du cube  
  
1.  Affichez l’onglet **Structure de cube** du Concepteur de cube pour le cube du didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , développez le groupe de mesures **Internet Sales** dans le volet **Mesures** , cliquez avec le bouton droit sur **Order Quantity**, puis choisissez **Propriétés**.  
  
2.  Dans la fenêtre des propriétés, cliquez sur l'icône en forme de punaise **Masquer automatiquement** pour épingler la fenêtre des propriétés.  
  
     Il est plus facile de modifier les propriétés de plusieurs éléments à la fois dans le cube lorsque la fenêtre des propriétés reste ouverte.  
  
3.  Dans la fenêtre Propriétés, cliquez sur la liste **FormatString** , puis tapez **#,#**.  
  
4.  Dans la barre d'outils de l'onglet **Structure de cube** , cliquez sur l'icône **Afficher la grille de mesures** à gauche.  
  
     L'affichage de la grille permet de sélectionner plusieurs mesures en même temps.  
  
5.  Sélectionnez l'une des mesures suivantes. Vous pouvez sélectionner plusieurs mesures en cliquant sur chacune d'elles tout en maintenant enfoncée la touche CTRL :  
  
    -   **Unit Price**  
  
    -   **Extended Amount**  
  
    -   **Discount Amount**  
  
    -   **Product Standard Cost**  
  
    -   **Total Product Cost**  
  
    -   **Sales Amount**  
  
    -   **Tax Amt**  
  
    -   **Freight**  
  
6.  Dans la fenêtre des propriétés, dans la liste **FormatString** , sélectionnez **Currency**.  
  
7.  Dans la zone de liste déroulante en haut de la fenêtre des propriétés (sous la barre de titre), sélectionnez la mesure **Unit Price Discount Pct**, puis sélectionnez **Percent** dans la liste **FormatString** .  
  
8.  Dans la fenêtre Propriétés, modifiez le **nom** propriété pour le **Unit Price Discount Pct** mesure `Unit Price Discount Percentage`.  
  
9. Dans le **mesures** volet, cliquez sur **Tax Amt** et modifiez le nom de cette mesure en `Tax Amount`.  
  
10. Dans la fenêtre des propriétés, cliquez sur l'icône **Masquer automatiquement** pour masquer la fenêtre des propriétés, puis cliquez sur **Afficher l'arborescence de mesures** dans la barre d'outils de l'onglet **Structure de cube** .  
  
11. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Modification de la dimension Customer](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des Dimensions de base de données](multidimensional-models/define-database-dimensions.md)   
 [Configurer des propriétés de mesure](multidimensional-models/configure-measure-properties.md)  
  
  
