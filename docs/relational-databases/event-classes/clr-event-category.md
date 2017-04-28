---
title: "Cat&#233;gorie d&#39;&#233;v&#233;nement CLR | Microsoft Docs"
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
  - "classes d’événements [SQL Server], catégorie d’événements CLR"
  - "classes d’événements SQL Server, catégorie d’événements CLR"
  - "CLR (catégorie d'événement ) [SQL Server]"
ms.assetid: a7c0cd60-3bec-42be-ad5e-473bd26a06d9
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# Cat&#233;gorie d&#39;&#233;v&#233;nement CLR
  La catégorie d’événement **CLR** inclut les classes d’événements qui sont produites par l’exécution d’objets CLR (Common Language Runtime) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 
 ## Classe d'événements Assembly Load 
  La classe d'événements **Assembly Load** se produit lorsqu'une demande de chargement d'un assembly est exécutée.  
  
 Pour contrôler des chargements d'assemblys, incluez la classe d'événements **Assembly Load** dans des traces. Ceci peut être utile lors du dépannage d'une requête qui utilise CLR, lors du dépannage d'un serveur à exécution lente qui exécute des requêtes CLR, ou lors de la surveillance d'un serveur pour réunir des informations sur les utilisateurs, les bases de données, les opérations réussies ou d'autres informations sur les chargements d'assemblys.  
  
## Colonnes de données de la classe d'événements Assembly Load  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application qui a demandé le chargement.|10|Oui|  
|**ClientProcessID**|**int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par l'instruction de base de données USE ou celui de la base de données par défaut si aucune instruction de base de données USE n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**EventSequence**|**int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**GroupID**|**int**|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|**LoginSID**|**image**|Identificateur de sécurité (SID) de l'utilisateur connecté. Vous trouverez ces informations dans l’affichage catalogue **sys.server_principals**. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom d'utilisateur Windows.|6|Oui|  
|**ObjectID**|**int**|ID d'assembly.|22|Oui|  
|**ObjectName**|**nvarchar**|Nom complet de l'assembly.|34|Oui|  
|**RequestID**|**int**|ID de la demande contenant l'instruction.|49|Oui|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**Réussi**|**int**|Indique si le chargement de l'assembly a réussi (1) ou échoué (0).|23|Oui|  
|**TextData**|**ntext**|« Chargement d'assembly réussi » si le chargement a réussi ; sinon  « Échec du chargement d'assembly ».|1|Oui|  
  
## Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [Assemblys &#40;moteur de base de données&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)  
  
   
  
## Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  