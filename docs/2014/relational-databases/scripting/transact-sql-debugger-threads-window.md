---
title: Threads, fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d80d45fe58e6778dd0caef18cdf067f4055da01
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256121"
---
# <a name="threads-window"></a>Fenêtre Threads
  La fenêtre **Threads** affiche des informations sur le thread du [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilisé par la session de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] en cours de débogage. Vous devez être en mode débogage pour afficher les informations sur le thread.  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la fenêtre Threads**  
  
-   Dans le menu **Déboguer** , cliquez sur **Fenêtres**, puis sur **Threads**.  
  
## <a name="columns"></a>Colonnes  
 **ID**  
 Numéro d'identification unique que le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] attribue au thread. Vous pouvez obtenir des d'informations supplémentaires sur le thread en sélectionnant une ligne dans la vue de gestion dynamique sys.dm_os_threads.  
  
 Si vous n’êtes pas en mode Regroupement léger, sélectionnez la ligne dont la valeur dans os_thread_id correspond à la valeur dans la colonne **ID** . Si vous êtes en mode Regroupement léger, sélectionnez la ligne dont la valeur dans fiber_context_address correspond à la valeur dans la colonne **ID** .  
  
 **Nom**  
 Affiche des informations sur la session du [!INCLUDE[ssDE](../../includes/ssde-md.md)] au format **nom_ordinateur/nom_instance [SPID]**.  
  
 **ComputerName**  
 Nom de l'ordinateur qui exécute l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à laquelle la session de l'éditeur de requête est connectée.  
  
 **InstanceName**  
 Nom de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à laquelle la session de l'éditeur de requête est connectée.  
  
 **[SPID]**  
 ID de processus de session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui identifie de façon unique cette session. Vous pouvez obtenir des informations supplémentaires sur la session en sélectionnant la ligne dans la vue sys.sysprocesses dont la valeur est la même dans la colonne spid.  
  
 **Emplacement**  
 Affiche le nom du fichier de script utilisé dans la session de l'éditeur de requête en cours de débogage.  
  
 **Priorité**  
 Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ne prend pas en charge cette fonctionnalité.  
  
 **Suspendre**  
 Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ne prend pas en charge cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](transact-sql-debugger.md)   
 [Informations du débogueur Transact-SQL](transact-sql-debugger-information.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  
  
  
