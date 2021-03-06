---
title: Développement avec Analysis Services le langage de script (ASSL) | Microsoft Docs
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
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7b68282f6327ac52cdf47bb761c764609292d7c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185176"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Développement avec le langage de script Analysis Services (ASSL)
  Le langage de script ASSL (Analysis Services Scripting Language) est une extension de XMLA qui ajoute un langage de définition d'objets et un langage de commande pour créer et gérer les structures des services Analysis Services directement sur le serveur. Vous pouvez utiliser ASSL dans l'application personnalisée pour communiquer avec Analysis Services sur le protocole XMLA. ASSL comprend deux parties :  
  
-   Un langage de définition de données (DDL), ou un langage de définition d’objets, définit et décrit une instance de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ainsi que les bases de données et les objets de base de données qui contient l’instance.  
  
-   Un langage de commande qui envoie des commandes d'action, telles que `Create`, `Alter` ou `Process`, à une instance d'Analysis Services. Ce langage de commande est abordé dans le [XML for Analysis &#40;XMLA&#41; référence](../../xmla/xml-for-analysis-xmla-reference.md).  
  
 Pour afficher l'ASSL qui décrit une solution multidimensionnelle dans [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], vous pouvez utiliser la commande Afficher le code au niveau du projet. Vous pouvez également créer ou modifier le script ASSL dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] à l'aide de l'éditeur de requête XMLA. Les scripts que vous créez peuvent être utilisés pour gérer des objets ou pour exécuter des commandes sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets ASSL et caractéristiques des objets](assl-objects-and-object-characteristics.md)   
 [Conventions ASSL XML](assl-xml-conventions.md)   
 [Sources de données et liaisons &#40;SSAS multidimensionnel&#41;](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
