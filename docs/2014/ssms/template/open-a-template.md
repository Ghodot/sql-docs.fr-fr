---
title: Ouvrir un modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 108f68c9501e4af37a2a2a1ee29787738b638522
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240029"
---
# <a name="open-a-template"></a>Ouvrir un modèle
  Vous pouvez ouvrir un modèle dans l'Explorateur de modèles.  
  
## <a name="to-open-a-template-from-template-explorer"></a>Pour ouvrir un modèle dans l'Explorateur de modèles  
 Vous pouvez ouvrir des modèles dans l'Explorateur de modèles.  
  
1.  Pour ouvrir l’Explorateur de modèles, dans le menu **Affichage** , cliquez sur **Explorateur de modèles**.  
  
2.  Dans la liste des catégories de modèles, développez la catégorie contenant le modèle que vous souhaitez ouvrir.  
  
3.  Il existe trois manières d'ouvrir le modèle :  
  
    1.  Double-cliquez sur le modèle pour l'ouvrir dans une fenêtre d'éditeur de code.  
  
    2.  Cliquez avec le bouton droit sur le modèle et sélectionnez **Ouvrir** pour l’ouvrir dans une fenêtre d’éditeur de code.  
  
    3.  Faites glisser le modèle dans une fenêtre d'éditeur de code pour ajouter le code du modèle au contenu de la fenêtre de l'éditeur.  
  
 Une fois que le modèle est ouvert, utilisez la boîte de dialogue **Remplacer les paramètres de modèle** pour remplacer les paramètres du modèle par vos valeurs.  
  
 Si l'ouverture d'un modèle lance une nouvelle fenêtre d'éditeur, la fenêtre s'ouvre avec les informations d'identification de la connexion active actuelle. Par exemple, si le focus se trouve sur une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans l'Explorateur d'objets lorsque vous ouvrez le modèle CREATE DATABASE, une nouvelle fenêtre d'éditeur est ouverte à l'aide d'une connexion à cette instance. S'il n'y a aucune connexion active, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] présente une boîte de dialogue de connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de modèles](template-explorer.md)   
 [Remplacer les paramètres de modèle](replace-template-parameters.md)  
  
  
