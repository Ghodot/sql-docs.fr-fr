---
title: Création d’ensembles de lignes avec ICommand::Execute | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28bfeafa028ce88b0d8132d0fdd2e29eab85b246
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420768"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Création d'ensembles de lignes avec ICommand::Execute
  Pour les ensembles de lignes créés à l’aide de la **ICommand::Execute** (méthode), les propriétés que vous voulez dans l’ensemble de lignes résultant peut limiter le texte de la commande. Cela est particulièrement important pour les consommateurs qui prennent en charge un texte de commande dynamique.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne peut pas utiliser [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseurs pour prendre en charge les résultats de plusieurs ensembles de lignes générés par de nombreuses commandes. Lorsqu'un consommateur demande un ensemble de lignes qui requiert la prise en charge de curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une erreur se produit si le texte de commande génère plusieurs ensembles de lignes comme résultat. Pour plus d’informations, consultez [commandes générant plusieurs ensembles de lignes résultats](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Défilement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensembles de lignes de fournisseur OLE DB Native Client sont prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les curseurs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impose des limitations aux curseurs qui sont sensibles aux modifications effectuées par d'autres utilisateurs de la base de données. En particulier, dans certains curseurs, les lignes ne peuvent pas être triées ; en outre, toute tentative de création d'un ensemble de lignes à l'aide d'une commande qui contient une clause SQL ORDER BY peut échouer. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  
