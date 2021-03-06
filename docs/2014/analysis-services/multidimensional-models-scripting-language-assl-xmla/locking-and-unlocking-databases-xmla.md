---
title: Verrouillage et déverrouillage de bases de données (XMLA) | Microsoft Docs
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
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa6eab7a4d0ebe15e87ee83b60020b7a1f809ae8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278355"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Verrouillage et déverrouillage de bases de données (XMLA)
  Vous pouvez verrouiller et déverrouiller des bases de données à l’aide, respectivement, la [verrou](../xmla/xml-elements-commands/lock-element-xmla.md) et [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) commandes XML for Analysis (XMLA). En règle générale, les autres commandes XMLA verrouillent et déverrouillent automatiquement les objets, selon le cas, pour faire aboutir la commande pendant l'exécution. Vous pouvez explicitement verrouiller ou déverrouiller une base de données pour exécuter plusieurs commandes dans une transaction unique, comme un [Batch](../xmla/xml-elements-commands/batch-element-xmla.md) commande, tout en empêchant les autres applications à partir de la validation d’une transaction d’écriture à la base de données.  
  
## <a name="locking-databases"></a>Verrouillage de bases de données  
 La commande `Lock` verrouille un objet, pour un usage partagé ou exclusif, dans le contexte de la transaction actuellement active. Un verrou sur un objet empêche la validation des transactions aussi longtemps que le verrou n'est pas supprimé. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge deux types de verrous : les verrous partagés et les verrous exclusifs. Pour plus d’informations sur les types de verrou pris en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consultez [élément Mode &#40;XMLA&#41;](../xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] autorise uniquement le verrouillage des bases de données. Le [objet](../xmla/xml-elements-properties/object-element-xmla.md) élément doit contenir une référence d’objet à un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données. Si l'élément `Object` n'est pas spécifié ou si cet élément `Object` fait référence à un objet autre qu'une base de données, une erreur survient.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de bases de données ou de serveurs peuvent émettre une commande `Lock` de manière explicite.  
  
 D'autres commandes permettent d'émettre une commande `Lock` dans une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de manière implicite. Toute opération qui lit des données ou les métadonnées à partir d’une base de données, telles que les [Discover](../xmla/xml-elements-methods-discover.md) méthode ou un [Execute](../xmla/xml-elements-methods-execute.md) méthode en cours d’exécution un [instruction](../xmla/xml-elements-commands/statement-element-xmla.md) commande, émettent implicitement un partagé verrou sur la base de données. Toutes les transactions qui valident des modifications de données ou les métadonnées d’un objet sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de base de données, comme un `Execute` méthode en cours d’exécution un [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) commande, émettent implicitement un verrou exclusif sur la base de données.  
  
## <a name="unlocking-objects"></a>Déverrouillage d'objets  
 La commande `Unlock` supprime un verrou établi dans le contexte de la transaction actuellement active.  
  
> [!IMPORTANT]  
>  Seuls les administrateurs de base de données ou serveur peut émettre explicitement un `Unlock` commande.  
  
 Tous les verrous sont conservés dans le contexte de la transaction en cours. Lors de la validation ou de la restauration de la transaction en cours, tous les verrous définis dans celle-ci sont libérés automatiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Verrouiller l’élément &#40;XMLA&#41;](../xmla/xml-elements-commands/lock-element-xmla.md)   
 [Élément Unlock &#40;XMLA&#41;](../xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
