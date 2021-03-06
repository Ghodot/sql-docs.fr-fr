---
title: Supprimer les instructions qui suppriment des objets système | Microsoft Docs
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
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7bb577db82aae98356481657faa9bd76a0ab2a82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161830"
---
# <a name="remove-statements-that-drop-system-objects"></a>Supprimer les instructions qui suppriment des objets système
  Le Conseiller de mise à niveau a détecté des instructions qui suppriment les objets système. Les objets système, y compris les procédures stockées étendues, sont déployés dans une base de données de **ressources** en lecture seule (mssqlsystemresource) et ne peuvent pas être supprimés. Modifiez vos applications pour révoquer ou refuser l'autorisation EXECUTE sur les objets système.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Des instructions telles que DROP TABLE, DROP PROCEDURE et **sp_dropextendedproc** ne peuvent pas être utilisées pour supprimer des objets système parce que ces objets sont déployés dans la base de données des **ressources** en lecture seule.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez toutes les instructions qui tentent d'éliminer des objets système de votre application. Modifiez vos applications pour révoquer ou refuser l'autorisation EXECUTE sur les objets système. Vous pouvez également utiliser l'outil Configuration de la surface d'exposition pour désactiver certains de ces objets. Par exemple, la procédure stockée étendue **xp_cmdshell** peut être désactivée ou activée à l'aide de l'outil SAC.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
