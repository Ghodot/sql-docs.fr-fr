---
title: Broker:Activation, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f95424242f62c946dc5d0787e54c8095e2f71a1f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250199"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation, classe d'événement
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Activation** quand un moniteur de file d’attente démarre une procédure stockée d’activation, envoie une notification QUEUE_ACTIVATION, ou quand une procédure stockée d’activation démarrée par un moniteur de file d’attente se termine.  
  
## <a name="brokeractivation-event-class-data-columns"></a>Colonnes de données de la classe d'événement Broker:Activation  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|`int`|Type de classe d'événements capturée. Toujours **163** pour **Broker:Activation**.|27|non|  
|**EventSequence**|`int`|Numéro de séquence de cet événement.|51|non|  
|**EventSubClass**|`nvarchar`|Action spécifique que cet événement signale. Une des valeurs suivantes :<br /><br /> **Démarrer**: <br />                [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a démarré une procédure stockée d'activation.<br /><br /> **fin**: la procédure d’activation s’est terminée normalement.<br /><br /> **abandonnée**: la procédure d’activation s’est arrêté avec une erreur.|21|non|  
|**HostName**|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IntegerData**|`int`|Nombre de tâches actives dans cette file d'attente.|25|non|  
|**IsSystem**|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|non|  
|**LoginSid**|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ObjectID**|`int`|File d'attente associée à cet événement.|22|non|  
|**ServerName**|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|**SPID**|`int`|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**StartTime**|`datetime`|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**TransactionID**|`bigint`|ID affecté à la transaction par le système.|4|non|  
  
  
