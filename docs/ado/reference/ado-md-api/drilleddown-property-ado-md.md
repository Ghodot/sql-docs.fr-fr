---
title: DrilledDown, propriété (ADO MD) | Documents Microsoft
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
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19d1ae46067d933941548b877da2cd2973947156
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284008"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown, propriété (ADO MD)
Indique si les enfants suivent immédiatement la [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) sur l’axe.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **booléenne** valeur et est en lecture seule. **DrilledDown** retourne **True** si aucun membre enfant du membre actuel sur l’axe. **DrilledDown** retourne **False** si le membre actuel a un ou plusieurs membres enfants sur l’axe.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **DrilledDown** propriété pour déterminer s’il existe au moins un enfant de ce membre sur l’axe suit immédiatement ce membre. Ces informations sont utiles lors de l’affichage du membre.  
  
 Cette propriété est uniquement prise en charge sur [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objets appartenant à un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet. Une erreur se produit lorsque cette propriété est référencée à partir de **membre** objets appartenant à un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ParentSameAsPrev, propriété (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
