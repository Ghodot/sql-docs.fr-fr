---
title: Indicateurs de table dans indexées vue définitions sont ignorées en mode de compatibilité 80 et ne sont pas autorisées en mode 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 93159a8c32f484fd9c734b4847dfd1e7fca854a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317429"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a>Les indicateurs de table dans les définitions de vues indexées sont ignorés en mode de compatibilité 80 et ne sont pas autorisés en mode 90 ou ultérieur
  Les indicateurs de table dans les définitions de vues indexées ne sont pas autorisés en mode de compatibilité 90 ou supérieur. Pour plus d'informations, consultez les rubriques suivantes dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : « Conception des vues indexées », "Création de vues indexées » et « Indicateur de requête ([!INCLUDE[tsql](../../includes/tsql-md.md)]) ».  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Les indicateurs de table doivent être supprimés des définitions des vues indexées. Quel que soit le mode de compatibilité utilisé, nous vous recommandons de tester l'application. Tester l'application vous permet de vérifier qu'elle fonctionne comme prévu lors de la création, de la mise à jour et de l'ouverture de vues indexées, notamment lorsque ces dernières sont mises en correspondance avec des requêtes.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
