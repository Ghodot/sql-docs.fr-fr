---
title: Sélectionnez la méthode de création (Assistant Cube) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubewizard.cubedefinition.f1
ms.assetid: 985d3b5b-7891-465b-862d-f7e75431b342
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e3a623381738e4d2f96222aaa193cf09ec619889
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37259425"
---
# <a name="select-creation-method-cube-wizard"></a>Sélectionner la méthode de création (Assistant Cube)
  Utilisez la page **Sélectionner la méthode de création** pour spécifier la méthode de création du cube.  
  
## <a name="options"></a>Options  
 **Utiliser des tables existantes**  
 Sélectionnez pour créer un cube en utilisant des tables existantes dans une source de données. L'Assistant vous guidera à travers le processus de sélection et de définition des groupes de mesures et de dimensions d'après des tables existantes pour générer votre nouveau cube.  
  
 **Créer un cube vide**  
 Sélectionnez pour créer un cube vide. Cette option est utile lorsque vous souhaitez tout créer manuellement, ou lorsque tous les groupes de mesures dans le cube sont des groupes de mesures liés.  
  
> [!NOTE]  
>  Cette option est disponible uniquement lorsque vous travaillez avec un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et pas lorsque vous êtes connecté directement à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Générer des tables dans la source de données**  
 Sélectionnez cette option pour créer d'abord un cube puis générer de nouvelles tables dans la source de données selon la définition de cube.  
  
> [!NOTE]  
>  Pour utiliser cette option, vous devez avoir l'autorisation de créer des objets dans la source de données sous-jacente.  
  
 Si vous sélectionnez cette option, l'option **Modèle** devient alors disponible.  
  
 **Modèle**  
 Sélectionnez le modèle que vous souhaitez utiliser pour créer le cube. Les modèles fournissent un jeu de définitions orienté vers un objectif commercial spécifique.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand l’option **Générer des tables dans la source de données** a été sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets de cube &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [Cubes dans les modèles multidimensionnels](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
