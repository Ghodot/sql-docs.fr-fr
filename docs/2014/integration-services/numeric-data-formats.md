---
title: Formats de données numériques | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- integer data types [Integration Services]
- numeric data formats for fast parse
- locale-sensitive parsing [Integration Services]
- fast parse [Integration Services]
ms.assetid: fa3975ce-9d21-408a-857d-f85e30af27b0
caps.latest.revision: 33
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1ed822a26c5722a249c3fda635288c282f3e2834
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180286"
---
# <a name="numeric-data-formats"></a>Formats de données numériques
  L'analyse rapide fournit un ensemble de routines simple, rapide et insensible aux paramètres régionaux pour l'analyse des données. Elle prend en charge uniquement un ensemble limité de formats pour les types de données integer.  
  
## <a name="integer-data-types"></a>Types de données integer  
 Les types de données integer fournis par [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sont DT_I1, DT_UI1, DT_I2, DT_UI2, DT_I4, DT_UI4, DT_I8 et DT_UI8. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).  
  
 L'analyse rapide prend en charge les formats suivants pour les types de données integer :  
  
-   Zéro ou plusieurs espaces de début et de fin ou taquets de tabulation. Par exemple, la valeur «  123  » est valide. Une valeur composée uniquement d'espaces est évaluée comme zéro.  
  
-   Un signe plus ou signe moins de début, ou ni l'un ni l'autre. Par exemple, les valeurs +123, -123 et 123 sont valides.  
  
-   Un ou plusieurs chiffres hindou-arabe (0-9). Par exemple, la valeur 345 est valide. Aucun autre chiffre linguistique n'est pris en charge.  
  
 Les formats de données non pris en charge sont les suivants :  
  
-   Caractères spéciaux. Par exemple, le symbole monétaire $ n'est pas pris en charge et la valeur $20 ne peut pas être analysée.  
  
-   Les caractères d'espaces blancs tels que les sauts de ligne, les retours chariot et les espaces insécables. Par exemple, la valeur « 123» ne peut pas être analysée.  
  
-   Les représentations hexadécimales d'entiers. Par exemple, la valeur 2EE ne peut pas être analysée.  
  
-   La représentation en notation scientifique d'entiers. Par exemple, la valeur 1E+10 ne peut pas être analysée.  
  
 Les formats suivants sont des formats de données de sortie pour les entiers :  
  
-   Un signe moins pour les nombres négatifs et rien pour les nombres positifs.  
  
-   Aucun espace blanc.  
  
-   Un ou plusieurs chiffres hindou-arabe (0-9).  
  
  
