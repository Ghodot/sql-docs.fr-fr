---
title: Mise à jour de données | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ed34a235a489feb13d31ef38e84e821cce961dc
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273124"
---
# <a name="updating-data"></a>Mise à jour des données
Comportement de mise à jour et fonctionnalités dépend en grande partie mettre à jour le mode (type de verrou), type de curseur et l’emplacement du curseur.  
  
 Utilisez le **mise à jour** méthode pour enregistrer les modifications apportées à l’enregistrement en cours d’un **Recordset** objet depuis l’appel le **AddNew** (méthode) ou parce que la modification des valeurs de champs dans un enregistrement existant. Le **Recordset** objet doit prendre en charge les mises à jour.  
  
 Si le **Recordset** objet prend en charge la mise à jour par lot, vous pouvez mettre en cache plusieurs modifications apportées à un ou plusieurs enregistrements localement jusqu'à ce que vous appeliez la **UpdateBatch** (méthode). Si vous modifiez l’enregistrement actif ou ajoutez un nouvel enregistrement lorsque vous appelez le **UpdateBatch** (méthode), ADO appelle automatiquement la **mise à jour** méthode pour enregistrer les modifications en attente à l’enregistrement actif avant transmettre les modifications par lot au fournisseur.  
  
 L’enregistrement actif reste actif après avoir appelé la **mise à jour** ou **UpdateBatch** méthodes.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Mode immédiat](../../../ado/guide/data/immediate-mode.md)  
  
-   [Mode batch](../../../ado/guide/data/batch-mode.md)  
  
-   [Traitement des transactions](../../../ado/guide/data/transaction-processing.md)
