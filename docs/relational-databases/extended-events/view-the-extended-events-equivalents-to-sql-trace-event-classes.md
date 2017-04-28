---
title: "Consulter les &#201;v&#233;nements &#233;tendus &#233;quivalents aux classes d&#39;&#233;v&#233;nements Trace SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
  - "xevents"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Trace SQL, équivalents des événements étendus"
  - "événements étendus [SQL Server], équivalents Trace SQL"
  - "événements étendus [SQL Server], événements configurables par l’utilisateur"
ms.assetid: 7f24104c-201d-4361-9759-f78a27936011
caps.latest.revision: 13
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 13
---
# Consulter les &#201;v&#233;nements &#233;tendus &#233;quivalents aux classes d&#39;&#233;v&#233;nements Trace SQL
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Si vous souhaitez utiliser Événements étendus pour recueillir des données d'événement qui sont équivalentes aux classes et colonnes d'événements Trace SQL, il est utile de comprendre comment les événements Trace SQL sont mappés aux événements et actions Événements étendus.  
  
 Vous pouvez utiliser la procédure suivante pour consulter les événements et actions Événements étendus équivalents à chaque événement Trace SQL et à ses colonnes associées.  
  
## Pour afficher les événements étendus équivalents aux événements Trace SQL à l'aide de l'éditeur de requête  
  
-   Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez la requête suivante :  
  
    ```  
    USE MASTER;  
    GO  
    SELECT DISTINCT  
       tb.trace_event_id,  
       te.name AS 'Event Class',  
       em.package_name AS 'Package',  
       em.xe_event_name AS 'XEvent Name',  
       tb.trace_column_id,  
       tc.name AS 'SQL Trace Column',  
       am.xe_action_name as 'Extended Events action'  
    FROM (sys.trace_events te LEFT OUTER JOIN sys.trace_xe_event_map em  
       ON te.trace_event_id = em.trace_event_id) LEFT OUTER JOIN sys.trace_event_bindings tb  
       ON em.trace_event_id = tb.trace_event_id LEFT OUTER JOIN sys.trace_columns tc  
       ON tb.trace_column_id = tc.trace_column_id LEFT OUTER JOIN sys.trace_xe_action_map am  
       ON tc.trace_column_id = am.trace_column_id  
    ORDER BY te.name, tc.name  
    ```  
  
 Lorsque vous affichez les résultats, gardez présentes à l'esprit les considérations suivantes :  
  
-   Si toutes les colonnes retournent NULL à l’exception de la colonne Event Class, cela indique que la classe d’événements n’a pas été migrée à partir de Trace SQL.  
  
-   Si seule la valeur de la colonne Extended Events est NULL, cela indique que l’une des conditions suivantes est vraie :  
  
    -   La colonne Trace SQL mappe à l'un des champs de données associé à l'événement Événements étendus.  
  
        > [!NOTE]  
        >  Chaque événement Événements étendus a un jeu par défaut des champs de données inclus automatiquement dans le jeu de résultats.  
  
    -   La colonne d'action n'a pas d'équivalent Événements étendus explicite. Citons par exemple la colonne EventClass dans Trace SQL. Cette colonne n'est pas nécessaire dans Événements étendus, car le nom d'événement est nécessaire.  
  
-   Pour les classes d’événements Trace SQL utilisateur configurables (UserConfigurable:1 via UserConfigurable:9), les événements étendus utilisent un événement unique pour les remplacer. L’événement se nomme user_event. Cet événement est déclenché à l’aide de sp_trace_generateevent, qui est la même procédure stockée que celle utilisée par Trace SQL. L’événement user_event est retourné indépendamment de l’ID d’événement passé à la procédure stockée. Toutefois, un champ event_id est retourné dans les données d’événement. Cela vous permet de générer un prédicat basé sur l'ID d'événement. Par exemple, si vous utilisez UserConfigurable:0 (ID d’événement : 82) dans le code, vous pouvez ajouter l’événement user_event à la session et spécifier un prédicat 'event_id = 82'. Par conséquent, vous n’avez pas à modifier le code parce que la procédure stockée sp_trace_generateevent génère l’événement user_event des événements étendus, et la classe d’événements Trace SQL équivalente.  
  
-   Si toutes les colonnes retournent NULL à l’exception de la colonne Event Class, cela indique que la classe d’événements n’a pas été migrée à partir de Trace SQL.  
  
-   Si seule la valeur de la colonne Extended Events est NULL, cela indique que l’une des conditions suivantes est vraie :  
  
    -   La colonne Trace SQL mappe à l'un des champs de données associé à l'événement Événements étendus.  
  
        > [!NOTE]  
        >  Chaque événement Événements étendus a un jeu par défaut des champs de données inclus automatiquement dans le jeu de résultats.  
  
    -   La colonne d'action n'a pas d'équivalent Événements étendus explicite. Citons par exemple la colonne EventClass dans Trace SQL. Cette colonne n'est pas nécessaire dans Événements étendus, car le nom d'événement est nécessaire.  
  
-   Pour les classes d’événements Trace SQL utilisateur configurables (UserConfigurable:1 via UserConfigurable:9), les événements étendus utilisent un événement unique pour les remplacer. L’événement se nomme user_event. Cet événement est déclenché à l’aide de sp_trace_generateevent, qui est la même procédure stockée que celle utilisée par Trace SQL. L’événement user_event est retourné indépendamment de l’ID d’événement passé à la procédure stockée. Toutefois, un champ event_id est retourné dans les données d’événement. Cela vous permet de générer un prédicat basé sur l'ID d'événement. Par exemple, si vous utilisez UserConfigurable:0 (ID d’événement : 82) dans le code, vous pouvez ajouter l’événement user_event à la session et spécifier un prédicat 'event_id = 82'. Par conséquent, vous n’avez pas à modifier le code parce que la procédure stockée sp_trace_generateevent génère l’événement user_event des événements étendus, et la classe d’événements Trace SQL équivalente.  
  
## Voir aussi  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)  
  
  