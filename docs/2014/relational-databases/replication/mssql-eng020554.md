---
title: MSSQL_ENG020554 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020554 error
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 64c590135a3055ac8bc349676d063aae56e15e78
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318319"
---
# <a name="mssqleng020554"></a>MSSQL_ENG020554
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|20554|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'agent de réplication n'a enregistré aucun message d'état d'avancement en %ld minutes. Il se peut que l'agent ne réponde pas ou que l'activité du système soit élevée. Vérifiez que les enregistrements sont répliqués vers la destination et que les connexions à l'Abonné, au serveur de publication et au serveur de distribution sont toujours actives.|  
  
## <a name="explanation"></a>Explication  
 Le travail **Vérification des agents de réplication** s'exécute à des intervalles spécifiés (10 minutes par défaut) pour vérifier l'état de chaque agent de réplication. Si un agent n'a consigné aucun message d'avancement depuis la dernière fois où le travail de vérification des agents s'est exécuté, une erreur MSSQL_ENG020554 peut être signalée. L'agent est supposé consigner au moins des messages d'historique, même si aucune autre activité de réplication ne se produit. Même si l'agent de réplication ne répond pas comme attendu, il n'est pas nécessairement arrêté ou en échec (si un agent a échoué, l'erreur MSSQL_ENG020536 est normalement signalée).  
  
 Les problèmes suivants peuvent provoquer l'apparition de l'erreur MSSQL_ENG020554 :  
  
-   L’Agent est occupé.  
  
     Si l'agent est trop occupé pour répondre quand il est interrogé par le travail de vérification des agents, ce travail ne peut pas rapporter si l'agent de réplication fonctionne correctement. Il y a plusieurs raisons pour lesquelles l'agent de réplication peut être occupé : il peut y avoir un grande quantité de données en cours de réplication, ou il peut y avoir des problèmes de conception ou de configuration de l'application qui aboutissent à des processus très longs à s'exécuter.  
  
-   L'agent ne peut pas se connecter à un des ordinateurs de la topologie.  
  
     Tous les agents comportent un paramètre **-LoginTimeOut** (défini sur 15 secondes par défaut), qui détermine la durée pendant laquelle un agent tente de se connecter à un nœud de réplication, par exemple l’Agent de fusion qui se connecte au serveur de publication. Si **-LoginTimeOut** est défini sur une valeur supérieure à celle de l’intervalle auquel le travail de vérification des agents de réplication s’exécute, un problème de connexion peut être la cause principale de l'erreur : l’erreur MSSQL_ENG020554 est alors générée avant que l’agent puisse signaler une erreur plus spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L'action requise dépend de la cause de l'erreur :  
  
-   Dans tous les cas où cette erreur est signalée :  
  
     Vérifiez les détails de l'erreur dans le moniteur de réplication, puis redémarrez l'agent s'il s'est arrêté. Les détails de l'erreur devraient fournir des informations supplémentaires sur la raison pour laquelle l'agent ne fonctionnait pas correctement. Si l'agent ne fonctionne pas, n'arrêtez pas et ne redémarrez pas l'agent car cela peut aggraver le problème. Pour des informations sur l'affichage de l'état et des informations détaillées des erreurs des agents dans le moniteur de réplication, consultez les rubriques suivantes :  
  
    -   Pour l’Agent d’instantané, l’Agent de lecture du journal et l’Agent de lecture de la file d’attente, consultez [Afficher des informations et effectuer des tâches pour les agents associés à une publication &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
    -   Pour l’Agent de distribution et l’Agent de fusion, consultez [Afficher des informations et effectuer des tâches pour les agents associés à un abonnement &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
-   Si l'erreur est signalée fréquemment parce que l'agent est occupé :  
  
     Il peut être nécessaire de reconcevoir l'application de façon à ce que les traitements effectués par l'agent soient moins longs.  
  
     Vous pouvez augmenter l'intervalle auquel l'état de l'agent est vérifié à l'aide de la boîte de dialogue **Propriétés du travail** . Pour obtenir des informations sur l’accès à cette boîte de dialogue pour les tâches de réplication, consultez [Afficher des informations et exécuter des tâches pour un serveur de publication &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md).  
  
-   Si un agent ne peut pas se connecter à un des ordinateurs de la topologie :  
  
     Il est recommandé de définir **-LoginTimeOut** sur une valeur inférieure à celle de l’intervalle auquel le travail de vérification des agents de réplication s’exécute. Dans certains cas, **-LoginTimeOut** est défini sur une valeur supérieure en raison de problèmes réseau entraînant l’expiration du délai d’attente des connexions. Si **-LoginTimeOut** est défini sur une valeur inférieure, la réplication peut signaler des erreurs plus spécifiques, ce qui vous permet de résoudre des problèmes de connexion pouvant eux-mêmes découler de problèmes d’autorisations, réseau ou autres. Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez :  
  
    -   [Utiliser des profils d’agent de réplication](agents/replication-agent-profiles.md)  
  
    -   [Afficher et modifier des paramètres d’invite de commandes d’un Agent de réplication &#40;SQL Server Management Studio&#41;](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’Agent de réplication](agents/replication-agent-administration.md)   
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)   
 [Agent de distribution de réplication](agents/replication-distribution-agent.md)   
 [Agent de lecture du journal de réplication](agents/replication-log-reader-agent.md)   
 [Agent de fusion de réplication](agents/replication-merge-agent.md)   
 [Agent de lecture de la file d’attente de réplication](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  
