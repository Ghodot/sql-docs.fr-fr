---
title: Téléchargement d’objets blob Azure, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d6825d61a997969691405f312eb91afd8b514087
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287675"
---
# <a name="azure-blob-download-task"></a>Tâche de téléchargement d’objet blob Azure
  La tâche de téléchargement d’objet blob Azure permet à un package SSIS de télécharger des fichiers à partir d’un stockage d’objets blob Azure.   
Pour ajouter une **tâche de téléchargement d’objet blob Azure**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de téléchargement d’objet blob Azure** .  
  
 Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureStorageConnection|Spécifiez un gestionnaire de connexions Azure Storage existant ou créez-en un qui fait référence à un compte Azure Storage et pointe vers l’emplacement où les fichiers d’objets blob sont hébergés.|  
|BlobContainer|Spécifie le nom du conteneur d’objets blob qui contient les fichiers d’objets blob à télécharger.|  
|BlobDirectory|Spécifie le répertoire d’objets blob qui contient les fichiers d’objets blob à télécharger. Le répertoire d’objets blob est une structure hiérarchique virtuelle.|  
|LocalDirectory|Spécifie le répertoire local où les fichiers d’objets blob téléchargés seront stockés.|  
|FileName|Spécifie un filtre de nom pour sélectionner des fichiers avec le modèle de nom spécifié. Par ex. MySheet*.xls\* inclut les fichiers MySheet001.xls et MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Spécifie un filtre d’intervalle de temps. Les fichiers modifiés après **TimeRangeFrom** et avant **TimeRangeTo** seront inclus.|  
  
  
