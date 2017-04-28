---
title: "MSSQL_ENG014152 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014152 (erreur)"
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014152
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14152|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Réplication-%s : agent %s programmé pour réessayer. %s|  
  
## Explication  
 L'agent de réplication spécifié a été programmé pour retenter l'opération demandée. Le processus continue à réessayer jusqu'à ce qu'il atteigne le nombre maximal de tentatives de reprise configuré pour l'étape du travail.  
  
 Une nouvelle tentative est effectuée généralement pour l'une des raisons suivantes :  
  
-   Le **QueryTimeout** valeur est dépassée.  
  
-   Le **LoginTimeout** valeur est dépassée.  
  
-   Le processus de réplication a été choisi comme victime du blocage.  
  
## Action de l'utilisateur  
 Si ce message est occasionnel, aucune action de l'utilisateur n'est requise.  
  
 Utilisez [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) pour afficher le paramètre actuel pour le nombre maximal de fois où le **exécuter l’agent** étape va tenter de l’agent de réplication spécifié. Vous pouvez utiliser la **@retry_attempts** paramètre de la [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) procédure stockée pour ajuster le nombre de tentatives d’une étape de travail.  
  
 Si ce message est récurrent, résolvez le problème en fonction du message qui est à l'origine de la nouvelle tentative. Vérifiez si l'historique de l'agent contient des messages indiquant pourquoi la reprise a dû être planifiée. Dans certains cas, vous devrez peut-être activer une journalisation plus détaillée pour votre agent de réplication. Pour plus d’informations sur la façon de configurer la journalisation pour la réplication, consultez l’article de la Base de connaissances Microsoft [312292](http://support.microsoft.com/kb/312292).  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  