---
title: Classe d’événements Showplan XML Statistics Profile | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan XML Statistics Profile event class
ms.assetid: 77e8ca69-d98a-4acd-9d6a-f825bf079d84
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5e82de0f80d8c3d52c58785cc27ab36944b1b516
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37266696"
---
# <a name="showplan-xml-statistics-profile-event-class"></a>Showplan XML Statistics Profile (classe d'événements)
  La classe d'événements Showplan XML Statistics Profile se produit lorsque [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute une instruction SQL. Incluez la classe d'événements Showplan XML Statististics Profile pour identifier les opérateurs Showplan sur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La classe d'événements Showplan XML Statistics Profile affiche les données de compilation complètes, si bien que les traces qui contiennent cette classe d'événements peuvent peser sensiblement sur les performances. Pour minimiser l'effet d'une telle charge, limitez l'utilisation de cette classe d'événements aux traces destinées à effectuer le suivi de problèmes précis pour de brèves durées.  
  
 Les documents Showplan XML ont un schéma qui leur est associé. Ce schéma se trouve sur le [site web de Microsoft](http://go.microsoft.com/fwlink/?LinkId=41740)ou dans le cadre de votre installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="showplan-xml-statistics-profile-event-class-data-columns"></a>Colonnes de données de la classe d'événements Showplan XML Statistics Profile  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|BinaryData|`image`|Coût estimé de la requête.|2|non|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|Classe d'événements|`int`|Type d’événement = 146.|27|non|  
|EventSequence|`int`|Séquence d'un événement donné au sein de la demande.|51|non|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IntegerData|`int`|Estimation du nombre de lignes retournées|25|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LineNumber|`int`|Affiche le numéro de la ligne qui contient l'erreur.|5|Oui|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|LoginSID|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|non|  
|NestLevel|`int`|Entier représentant les données retournées par @@NESTLEVEL.|29|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|ObjectID|`int`|ID affecté à l'objet par le système.|22|Oui|  
|ObjectName|`nvarchar`|Nom de l'objet référencé.|34|Oui|  
|ObjectType|`int`|Valeur représentant le type de l'objet qui intervient dans l'événement. Cette valeur correspond à la colonne type de l'affichage catalogue sys.objects. Pour connaître les valeurs, consultez [Colonne d’événements de trace ObjectType](objecttype-trace-event-column.md).|28|Oui|  
|RequestID|`int`|ID de la demande contenant l'instruction.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Valeur texte qui dépend de la classe d'événements capturée dans la trace.| 1|Oui|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
|XactSequence|`bigint`|Jeton utilisé pour décrire la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Guide de référence des opérateurs Showplan logiques et physiques](../showplan-logical-and-physical-operators-reference.md)  
  
  
