---
title: Afficher le code XML pour un projet (SSDT) Analysis Services | Microsoft Docs
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
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: df5f976c08f6c16b73628ce96b459f6fd8b0fc5b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187226"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Afficher le code XML d'un projet Analysis Services (SSDT)
  Si vous utilisez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode projet, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée une définition XML pour chaque objet dans le dossier du projet. Vous pouvez afficher le contenu du fichier XML pour chaque objet dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Vous pouvez également modifier le fichier XML directement. Toutefois, nous vous déconseillons de procéder ainsi, car certaines modifications peuvent rendre le fichier XML illisible dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Vous ne pouvez pas afficher le code XML d'un projet complet. Cependant, vous pouvez afficher le code de chaque objet car il existe un fichier distinct pour chaque objet. La seule façon d’afficher le code d’un projet complet consiste à générer le projet et afficher l’ASSL de code dans le \<nom_projet > fichier .asdatabase.  
  
### <a name="to-view-the-xml-code-for-an-object"></a>Pour afficher le code XML d'un objet  
  
1.  Ouvrez le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur l’objet dans l’Explorateur de solutions, puis cliquez sur **Afficher le code**.  
  
     Le code XML de l’objet s’affiche dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Générer des projets Analysis Services &#40;SSDT&#41;](build-analysis-services-projects-ssdt.md)  
  
  
