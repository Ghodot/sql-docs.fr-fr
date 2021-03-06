---
title: CopyRecordOptionsEnum | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6314f9ab11e0704075b6a6cf8d0f9e529a3c0b69
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277158"
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Spécifie le comportement de la [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) (méthode).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Indique que le *Source* fournisseur tente de simuler une copie à l’aide de téléchargement et opérations de téléchargement si cette méthode échoue en raison *Destination*en cours sur un autre serveur ou est traitée par une autre fournisseur de *Source*. Notez que les différentes possibilités du fournisseur peuvent entraver les performances ou de perdre des données.|  
|**adCopyNonRecursive**|2|Copie le répertoire en cours, mais aucune de ses sous-répertoires, vers la destination. L’opération de copie n’est pas récursive.|  
|**adCopyOverWrite**| 1|Remplace le fichier ou le répertoire si le *Destination* pointe vers un fichier ou répertoire existant.|  
|**adCopyUnspecified**|-1|Valeur par défaut. Effectue l’opération de copie par défaut : l’opération échoue si le fichier de destination ou le répertoire existe déjà et l’opération de copie récursive.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [CopyRecord, méthode (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
