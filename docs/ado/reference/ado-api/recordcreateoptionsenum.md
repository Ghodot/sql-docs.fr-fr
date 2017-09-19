---
title: RecordCreateOptionsEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f108d977c278d9f86ca47853e07c7960ee574b8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Spécifie si un existant **enregistrement** doit être ouvert ou un nouveau **enregistrement** créé pour le [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet [ouvrir](../../../ado/reference/ado-api/open-method-ado-record.md) (méthode). Les valeurs peuvent être combinées avec un opérateur AND.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Crée un nouveau **enregistrement** au niveau du nœud spécifié par *Source* paramètre, au lieu d’ouvrir un existant **enregistrement**. Si la source pointe sur un nœud existant, une erreur d’exécution se produit, sauf si **adCreateCollection** est combiné avec **adOpenIfExists** ou **adCreateOverwrite**.|  
|**adCreateNonCollection**|0|Crée un nouveau **enregistrement** de type [adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Modifie les indicateurs de création de **adCreateCollection**, **adCreateNonCollection**, et **adCreateStructDoc**. Quand OR est utilisé avec cette valeur et l’une des valeurs d’indicateur de création, si l’URL source pointe vers un nœud existant ou **enregistrement**, puis existants **enregistrement** est remplacé et aucune nouvelle est créée à la place. Cette valeur ne peut pas être utilisée avec **adOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Crée un nouveau **enregistrement** de type [adStructDoc](../../../ado/reference/ado-api/recordtypeenum.md), au lieu d’ouvrir un existant **enregistrement**.|  
|**adFailIfNotExists**|-1|Valeur par défaut. Génère une erreur d’exécution si *Source* pointe vers un nœud inexistant.|  
|**adOpenIfExists**|0x2000000|Modifie les indicateurs de création de **adCreateCollection**, **adCreateNonCollection**, et **adCreateStructDoc**. Quand OR est utilisé avec cette valeur et l’une des valeurs d’indicateur de création, si l’URL source pointe vers un nœud existant ou **enregistrement** de l’objet, le fournisseur doit ouvrir existants **enregistrement** au lieu de créer un nouveau une. Cette valeur ne peut pas être utilisée avec **adCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [Open (méthode) (enregistrement ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)