---
title: Démarrer une trace | Microsoft Docs
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
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 678bf2b9140d5df7d19aa28088d598f4cca450c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224579"
---
# <a name="start-a-trace"></a>Démarrer une trace
  Après avoir défini une nouvelle trace ou créé un modèle en utilisant le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], vous pouvez démarrer, suspendre ou arrêter la capture des données en utilisant la définition de la nouvelle trace ou le modèle.  
  
## <a name="starting-a-trace"></a>Démarrage d’une trace  
 Lorsque vous démarrez une trace et que la source définie est une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ou des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une file d'attente qui fournit un espace de stockage temporaire pour les événements serveur capturés.  
  
 Lorsque vous utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour accéder à Trace SQL, une nouvelle fenêtre de trace s'ouvre (si aucune n'est ouverte) au démarrage d'une trace et les données sont capturées immédiatement.  
  
 Lorsque vous utilisez des procédures stockées système [!INCLUDE[tsql](../../includes/tsql-md.md)] pour accéder à Trace SQL, vous devez démarrer une trace chaque fois qu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre pour capturer des données. Lorsqu’une trace est démarrée, vous pouvez modifier uniquement le nom de la trace.  
  
> [!NOTE]  
>  Lorsque vous utilisez des traces existantes, vous pouvez afficher les propriétés, mais pas les modifier. Pour modifier les propriétés, arrêtez ou suspendez la trace.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer automatiquement une Trace après connexion à un serveur &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [Suspendre une trace &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md)   
 [Arrêter une trace &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md)   
 [Effacer une fenêtre de trace &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md)   
 [Exécuter une trace après qu’elle a été suspendue ou arrêtée &#40;SQL Server Profiler&#41;](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
