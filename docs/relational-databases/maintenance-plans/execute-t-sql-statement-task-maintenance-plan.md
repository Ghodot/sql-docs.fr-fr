---
title: "Exécuter la tâche de l’instruction T-SQL (Plan de maintenance) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.maint.tsql.f1
helpviewer_keywords:
- Execute T-SQL Statement Task dialog box
ms.assetid: fef3e259-0c47-4f6e-ade0-aee95e3d6c1a
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cc4fe80e02dfde259794807f700cee0e73dcd43f
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="execute-t-sql-statement-task-maintenance-plan"></a>Exécuter la tâche de l’instruction T-SQL (Plan de maintenance)
  Utilisez la boîte de dialogue **Exécuter la tâche de l’instruction T-SQL** pour personnaliser le plan de maintenance en y ajoutant les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] de votre choix.  
  
## <a name="options"></a>Options  
 **Connexion**  
 Sélectionnez la connexion serveur à utiliser pour exécuter la tâche.  
  
 **Nouveau**  
 Crée une nouvelle connexion serveur à utiliser pour exécuter la tâche. La boîte de dialogue **Nouvelle connexion** est décrite ci-dessous.  
  
 **Expiration du délai d'exécution**  
 Temps d'attente (en secondes) avant l'expiration du délai pour l'exécution de la tâche (arrêt de la tâche).  
  
 **Instruction T-SQL**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Instructions à exécuter.  
  
 **Vue T-SQL**  
 Affiche les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutées sur le serveur pour cette tâche, selon les options sélectionnées.  
  
> [!NOTE]  
>  Si le nombre d'objets impliqués est élevé, l'affichage des instructions peut prendre un temps considérable.  
  
## <a name="new-connection-dialog-box"></a>Boîte de dialogue Nouvelle connexion  
 **Nom de la connexion**  
 Entrez un nom pour la nouvelle connexion.  
  
 **Sélectionnez ou entrez un nom de serveur.**  
 Sélectionnez un serveur auquel établir la connexion pour exécuter la tâche.  
  
 **Actualiser**  
 Actualise la liste des serveurs disponibles.  
  
 **Entrez des informations pour vous connecter au serveur**  
 Spécifiez le mode d'authentification sur le serveur.  
  
 **Utiliser la sécurité intégrée à Windows NT**  
 Permet de se connecter à une instance du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] à l’aide de l’authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Utiliser un nom d'utilisateur et un mot de passe spécifiques**  
 Se connecte à une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette option n'est pas disponible.  
  
 **Nom d'utilisateur**  
 Fournit le nom d'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
 **Mot de passe**  
 Fournit un mot de passe à utiliser pour l'authentification. Cette option n'est pas disponible.  
  
  