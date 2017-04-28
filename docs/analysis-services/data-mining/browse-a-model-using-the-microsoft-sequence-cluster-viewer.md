---
title: "Explorer un mod&#232;le &#224; l&#39;aide de la visionneuse de l&#39;algorithme MSC (Microsoft Sequence Cluster) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visionneuse de l’algorithme MSC"
  - "clusters [Analysis Services]"
  - "exploration de données [Analysis Services], séquences"
  - "discrimination [Analysis Services]"
  - "contenu du modèle d'exploration de données, affichage"
  - "modèles d’exploration de données [Analysis Services], séquences"
  - "visionneuse de l'algorithme MSC (Microsoft Sequence Clustering)"
  - "sequence [Analysis Services]"
  - "transitions [Analysis Services]"
ms.assetid: 3ada00aa-da9e-488a-9f53-c3e188f81f84
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# Explorer un mod&#232;le &#224; l&#39;aide de la visionneuse de l&#39;algorithme MSC (Microsoft Sequence Cluster)
  La Visionneuse de l’algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] affiche les modèles d’exploration de données qui sont générés avec l’algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering). L’algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) est un algorithme d’analyse de séquence conçu pour l’exploration des données qui contiennent des événements pouvant être liés par des chemins consécutifs, ou *séquences*. Pour plus d’informations sur cet algorithme, consultez [Algorithme MSC (Microsoft Sequence Clustering)](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md).  
  
> [!NOTE]  
>  La visionneuse de l'arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)] permet de consulter des informations détaillées relatives aux équations utilisées dans le modèle et les motifs découverts. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) ou [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md).  
  
> [!NOTE]  
>  La visionneuse de l'algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) fournit des fonctionnalités et des options similaires à celles de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer. Pour plus d’informations, consultez [Explorer un modèle à l’aide de Microsoft Sequence Cluster](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md).  
  
##  <a name="BKMK_ViewerTabs"></a> Onglets de la visionneuse  
 Lorsque vous parcourez un modèle d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le modèle s'affiche sous l'onglet **Visionneuse de modèle d'exploration de données** du Concepteur d'exploration de données, à l'aide de la visionneuse appropriée pour ce modèle. La Visionneuse de l’algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) fournit les onglets suivants pour explorer les modèles d’exploration de données MSC :  
  
-   [Diagramme de cluster](#BKMK_Diagram)  
  
-   [Profils du cluster](#BKMK_Profile)  
  
-   [Caractéristiques du cluster](#BKMK_Characteristics)  
  
-   [Discrimination de cluster](#BKMK_Discrimination)  
  
-   [Transitions d'état](#BKMK_Transitions)  
  
###  <a name="BKMK_Diagram"></a> Diagramme de cluster  
 L’onglet **Diagramme de cluster** de la Visionneuse de l’algorithme MSC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) affiche tous les clusters se trouvant dans un modèle d’exploration de données. L'ombrage de la ligne reliant un cluster à un autre représente le niveau de similarité des clusters. Si l'ombrage est clair ou inexistant, les clusters ne sont pas très similaires. Plus la ligne est sombre, plus la similarité des liens est grande. Vous pouvez modifier le nombre de lignes affichées par la visionneuse à l'aide du curseur situé à droite des clusters. Si vous déplacez le curseur vers le bas, seuls les liens les plus forts sont affichés.  
  
 Par défaut, l'ombre représente le remplissage du cluster. À l’aide des options **Variable d’ombrage** et **État**, vous pouvez sélectionner la paire attribut-état que l’ombrage représente. Plus l'ombrage est sombre, plus la distribution d'attribut est grande pour un état spécifique. Inversement, plus l'ombrage est clair, plus la distribution diminue.  
  
 Pour renommer un cluster, cliquez avec le bouton droit sur son nœud et sélectionnez **Renommer le cluster**. Le nouveau nom est enregistré sur le serveur.  
  
 Pour copier la partie visible du diagramme dans le Presse-papiers, cliquez sur **Copier la vue du graphique**. Pour copier l'intégralité du diagramme, cliquez sur **Copier le graphique entier**. Vous pouvez également faire un zoom avant et arrière à l'aide des boutons **Zoom avant** et **Zoom arrière**ou vous pouvez ajuster le diagramme à la taille de l'écran à l'aide de **Ajuster le diagramme à la fenêtre**.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Profile"></a> Profils du cluster  
 L’onglet **Profil du cluster** fournit une vue d’ensemble des clusters créés par l’algorithme de votre modèle. Chacune des colonnes situées après la colonne **Remplissage** dans la grille représente un cluster qui a été découvert par le modèle. La ligne \<attribut>.samples représente les différentes séquences de données existant dans le cluster tandis que la ligne \<attribut> décrit tous les éléments contenus dans le cluster et leur distribution globale.  
  
 L’option **Barres de l’histogramme** contrôle le nombre de barres qui sont visibles dans l’histogramme. Si le nombre réel de barres est supérieur au nombre de barres à afficher, les barres les plus importantes sont conservées et le reste des barres est regroupé dans un compartiment gris.  
  
 Vous pouvez modifier le nom par défaut des clusters afin de définir des noms plus descriptifs. Pour renommer un cluster, cliquez avec le bouton droit sur son en-tête de colonne et sélectionnez **Renommer le cluster**. Vous pouvez masquer des clusters en sélectionnant **Masquer la colonne** et vous pouvez aussi faire glisser des colonnes pour changer l’ordre dans lequel elles apparaissent dans la visionneuse.  
  
 Pour ouvrir une fenêtre fournissant une vue plus détaillée et plus grande des clusters, double-cliquez soit sur une cellule de la colonne **États**, soit sur un histogramme dans la visionneuse.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> Caractéristiques du cluster  
 Pour utiliser l’onglet **Caractéristiques du cluster** , sélectionnez un cluster dans la liste **Cluster** . Après avoir sélectionné un cluster, vous pouvez examiner les caractéristiques qui composent ce cluster spécifique. Les attributs contenus dans le cluster sont répertoriés dans les colonnes **Variables** et l'état de l'attribut répertorié est répertorié dans la colonne **Valeurs** . Les états d'attribut apparaissent par ordre d'importance, en fonction de leur probabilité d'apparition dans le cluster. La probabilité est indiquée dans la colonne **Probabilité** .  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Discrimination"></a> Discrimination de cluster  
 Vous pouvez utiliser l’onglet **Discrimination de cluster** pour comparer les attributs entre deux clusters afin de déterminer comment les éléments d’une séquence privilégient un cluster par rapport à l’autre. Utilisez les listes **Cluster 1** et **Cluster 2** pour sélectionner les clusters à comparer. La visionneuse détermine les différences les plus importantes entre les clusters et affiche, par ordre d'importance, les états d'attribut associés à ces différences. Une barre à droite de l'attribut indique quel cluster est privilégié par l'état et la taille de la barre indique à quel point l'état privilégie le cluster.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Transitions"></a> Transitions d'état  
 En sélectionnant un cluster sous l’onglet **Transitions d’état**, vous pouvez parcourir les transitions entre les états de séquence dans le cluster sélectionné. Chaque nœud figurant dans la visionneuse représente un état de la colonne de séquence. Une flèche représente une transition entre deux états et la probabilité associée à la transition. Si une transition revient au nœud d'origine, une flèche peut repointer vers le nœud d'origine.  
  
 Une flèche provenant d'un point représente la probabilité que le nœud est le début d'une séquence. Une extrémité de fin menant à une valeur NULL représente la probabilité que le nœud est la fin de la séquence.  
  
 Vous pouvez filtrer l'extrémité des nœuds à l'aide du curseur à gauche de l'onglet.  
  
 [Retour au début](#BKMK_ViewerTabs)  
  
## Voir aussi  
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Algorithme MSC (Microsoft Sequence Clustering)](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Outils d'exploration de données](../../analysis-services/data-mining/data-mining-tools.md)   
 [Visionneuses de modèle d’exploration de données](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [Explorer un modèle à l'aide de Microsoft Sequence Cluster](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
  