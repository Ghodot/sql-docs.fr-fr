---
title: Surveiller l’utilisation du disque | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fcd06bddde4b1c720140da4c4af0cae25ad1a2a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166940"
---
# <a name="monitor-disk-usage"></a>Surveiller l'utilisation du disque
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise les appels d'entrées/sorties (E/S) du système d'exploitation Microsoft Windows pour effectuer des opérations de lecture et d'écriture sur le disque. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère quand et comment les E/S disque sont effectuées, mais le système d’exploitation Windows effectue les opérations d’E/S sous-jacentes. Le sous-système d'E/S comporte le bus système, les cartes contrôleurs de disque, les disques, les unités de sauvegarde sur bande, les unités de CD-Rom et de nombreux autres périphériques d'E/S. Les E/S sur le disque sont souvent responsables des problèmes de goulot d’étranglement d’un système.  
  
 La surveillance de l'activité du disque est double :  
  
-   Surveillance des E/S du disque et détection des excès de pagination  
  
-   Isolement de l'activité de disque créée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Pour plus d'informations sur l'utilisation du disque, consultez [Surveillance de l'utilisation du disque](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx).  
  
  
