---
title: "Garbage collection de l&#39;OLTP en m&#233;moire | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Garbage collection de l&#39;OLTP en m&#233;moire
  Une ligne de données est considérée comme obsolète si elle a été supprimée par une transaction qui n'est plus active. Une ligne périmée est éligible à l'opération de garbage collection. Voici quelques caractéristiques du garbage collection dans [!INCLUDE[hek_2](../../includes/hek-2-md.md)] :  
  
-   Non bloquant. Le garbage collection est distribué dans le temps avec un impact minimal sur la charge de travail.  
  
-   Coopératif. Les transactions utilisateur participent au garbage collection avec le thread garbage-collection.  
  
-   Efficace. Les transactions détachent les lignes obsolètes dans le chemin d'accès (l'index) utilisé. Cela réduit le travail requis lorsque la ligne est finalement supprimée.  
  
-   Réactif. La pression exercée sur la mémoire déclenche un garbage collection agressif.  
  
-   Évolutif. Après la validation, les transactions utilisateur exécutent une partie du travail du garbage collection. Plus l'activité transactionnelle est importante, plus les transactions détachent de lignes obsolètes.  
  
 Le garbage collection est contrôlé par le thread principal du garbage collection. Le thread garbage collection principal s'exécute toutes les minutes, ou lorsque le nombre de transactions validées dépasse un seuil interne. Les tâches du garbage collector sont les suivantes :  
  
-   Identifier les transactions qui ont supprimé ou mis à jour un ensemble de lignes et qui ont été validées avant la transaction active la plus ancienne.  
  
-   Identifier les versions de ligne créées par les anciennes transactions.  
  
-   Grouper les anciennes lignes dans une ou plusieurs unités de 16 lignes chacune. Cela a pour but de distribuer le travail du garbage collector dans de plus petites unités.  
  
-   Déplacer ces unités de travail dans la file d'attente du garbage collection, une pour chaque planificateur. Pour plus de détails sur les vues de gestion dynamique du garbage collector : [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql.md), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql.md) et [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md).  
  
 Après qu'une transaction utilisateur est validée, elle identifie tous les éléments de la file d'attente associés au planificateur sur lequel elle s'exécute et désalloue la mémoire. Si la file d'attente du garbage collection sur le planificateur est vide, il recherche une file d'attente non vide dans le nœud NUMA actuel. En cas de faible activité transactionnelle et en cas de sollicitation de la mémoire, le thread principal garbage-collection peut accéder aux lignes extraites de n'importe quelle file d'attente pour les nettoyer. S'il n'y a aucune activité transactionnelle, par exemple, après avoir supprimé un grand nombre de lignes et s'il n'y a aucune sollicitation de la mémoire, les lignes supprimées ne sont extraites par le garbage collector que quand l'activité transactionnelle reprend ou quant la mémoire est sollicitée.  
  
## Voir aussi  
 [Gestion de la mémoire pour l'OLTP en mémoire](../Topic/Managing%20Memory%20for%20In-Memory%20OLTP.md)  
  
  