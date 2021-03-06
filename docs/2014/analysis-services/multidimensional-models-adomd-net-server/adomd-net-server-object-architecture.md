---
title: Architecture des objets serveur ADOMD.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f18dd57b9232a9ef9e3405ccc77b5db1bb8a1c82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237719"
---
# <a name="adomdnet-server-object-architecture"></a>Architecture des objets serveur ADOMD.NET
  Les objets serveur ADOMD.NET sont des objets d’assistance qui peuvent être utilisées pour créer des fonctions définies par l’utilisateur (UDF) ou des procédures stockées de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Pour utiliser l'espace de noms `Microsoft.AnalysisServices.AdomdServer` (et ces objets), une référence à msmgdsrv.dll doit être ajoutée au projet UDF ou à la procédure stockée.  
  
 ![Affiche les relations d’objet de serveur ADOMD.NET](../../../2014/analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "montre les relations d’objet dans le serveur ADOMD.NET")  
Modèle objet ADOMD.NET  
  
 L'interaction avec la hiérarchie d'objets ADOMD.NET débute généralement avec un ou plusieurs objets de la couche de niveau supérieur, comme indiqué dans le tableau suivant.  
  
|Pour|Utiliser cet objet|  
|--------|---------------------|  
|Évaluer des instructions MDX (Multidimensional Expressions)|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> L'objet <xref:Microsoft.AnalysisServices.AdomdServer.Expression> permet d'exécuter une expression MDX et d'évaluer cette expression sous un tuple spécifié.|  
|Offrir la possibilité d'exécuter des fonctions MDX sans construire l'instruction MDX entière|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> L'objet <xref:Microsoft.AnalysisServices.AdomdServer.MDX> s'avère très pratique pour appeler des fonctions MDX prédéfinies sans utiliser l'objet <xref:Microsoft.AnalysisServices.AdomdServer.Expression>. Des fonctions supplémentaires pour l'objet <xref:Microsoft.AnalysisServices.AdomdServer.MDX> devraient être disponibles dans les futures versions.|  
|Représenter le contexte d'exécution actuel pour la fonction définie par l'utilisateur|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> L'objet <xref:Microsoft.AnalysisServices.AdomdServer.Context> affiche des informations telles que le cube ou le modèle d'exploration de données actuel, ainsi que diverses collections de métadonnées. L'une des principales utilisations de l'objet <xref:Microsoft.AnalysisServices.AdomdServer.Context> est la propriété <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy>. Cette utilisation clé permet à l'auteur de la fonction définie par l'utilisateur ou de la procédure stockée de prendre des décisions en fonction du membre d'une certaine dimension sur lequel la requête porte.|  
|Créer des ensembles et des tuples|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> L'objet <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> permet de créer des ensembles immuables, tandis que l'objet <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> permet de créer des tuples immuables.|  
|Prendre en charge une conversion implicite entre les six types de base du langage MDX|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> L'objet <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> assure une conversion implicite entre les types suivants :<br /><br /> -   <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Level><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Member><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Set><br />-Scalaire, ou des types valeur|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du serveur ADOMD.NET](../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
