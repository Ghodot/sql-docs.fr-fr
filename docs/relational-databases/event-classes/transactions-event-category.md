---
title: "Cat&#233;gorie d&#39;&#233;v&#233;nements Transactions | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "classes d’événements SQL Server, catégorie d’événement Transactions"
  - "classes d’événements [SQL Server], catégorie d’événement Transactions"
  - "Transactions (catégorie d'événement) [SQL Server]"
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Cat&#233;gorie d&#39;&#233;v&#233;nements Transactions
  Les classes d’événements **Transactions** permettent de surveiller l’état des transactions. Les noms de classes d’événements portant le préfixe **TM:** sont utilisées pour assurer le suivi des opérations liées aux transactions qui sont envoyées à travers l’interface de gestion des transactions.  
  
## Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événements DTCTransaction](../../relational-databases/event-classes/dtctransaction-event-class.md)|Assure le suivi des transactions coordonnées par [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC). Ce sont les transactions distribuées entre plusieurs bases de données ou instances du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Classe d'événements SQLTransaction](../../relational-databases/event-classes/sqltransaction-event-class.md)|Surveille les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN et ROLLBACK TRAN.|  
|[Classe d'événements TM: Begin Tran Completed](../../relational-databases/event-classes/tm-begin-tran-completed-event-class.md)|Indique qu'une demande BEGIN TRANSACTION est terminée.|  
|[Classe d'événements TM: Begin Tran Starting](../../relational-databases/event-classes/tm-begin-tran-starting-event-class.md)|Indique qu'une demande BEGIN TRANSACTION démarre.|  
|[Classe d'événements TM: Commit Tran Completed](../../relational-databases/event-classes/tm-commit-tran-completed-event-class.md)|Indique qu'une demande COMMIT TRANSACTION est terminée.|  
|[Classe d'événements TM: Commit Tran Starting](../../relational-databases/event-classes/tm-commit-tran-starting-event-class.md)|Indique qu'une demande COMMIT TRANSACTION démarre.|  
|[Classe d'événements TM: Promote Tran Completed](../../relational-databases/event-classes/tm-promote-tran-completed-event-class.md)|Indique qu'une demande PROMOTE TRANSACTION est terminée.|  
|[Classe d'événements TM: Promote Tran Starting](../../relational-databases/event-classes/tm-promote-tran-starting-event-class.md)|Indique qu'une demande PROMOTE TRANSACTION démarre.|  
|[Classe d'événements TM: Rollback Tran Completed](../../relational-databases/event-classes/tm-rollback-tran-completed-event-class.md)|Indique qu'une demande ROLLBACK TRANSACTION est terminée.|  
|[Classe d'événements TM: Rollback Tran Starting](../../relational-databases/event-classes/tm-rollback-tran-starting-event-class.md)|Indique qu'une demande ROLLBACK TRANSACTION démarre.|  
|[Classe d'événements TM: Save Tran Completed](../../relational-databases/event-classes/tm-save-tran-completed-event-class.md)|Indique qu'une demande SAVE TRANSACTION est terminée.|  
|[Classe d'événements TM: Save Tran Starting](../../relational-databases/event-classes/tm-save-tran-starting-event-class.md)|Indique qu'une demande SAVE TRANSACTION démarre.|  
|[Classe d'événements TransactionLog](../../relational-databases/event-classes/transactionlog-event-class.md)|Assure le suivi du moment où les transactions sont écrites dans un journal des transactions de la base de données.|  
  
  