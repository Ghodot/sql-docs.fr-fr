---
title: "Configurer l&#39;option de configuration du serveur network packet size | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "taille de paquet par défaut"
  - "taille [SQL Server], paquets"
  - "paquets [SQL Server], taille"
  - "network packet size (option)"
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Configurer l&#39;option de configuration du serveur network packet size
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment configurer l'option de configuration de serveur **Taille du paquet réseau** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L’option **Taille du paquet réseau** définit la taille de paquet (en octets) utilisée sur tout le réseau. Les paquets constituent les morceaux de taille définie de données qui transfèrent les requêtes et les résultats entre les clients et les serveurs. La taille des paquets par défaut est 4 096 octets.  
  
> [!NOTE]  
>  Ne modifiez pas la taille des paquets, sauf si vous êtes certain que cela permettra d'accroître les performances. Pour la plupart des applications, la taille de paquet par défaut représente la meilleure solution.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option Taille du paquet réseau, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option Taille du paquet réseau](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   La taille de paquet réseau maximale pour les connexions chiffrées est 16 383 octets.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Si une application effectue des opérations de copie en bloc, ou envoie ou reçoit de grandes quantités de données de type texte ou image, l'utilisation d'une taille de paquet supérieure à la taille par défaut peut améliorer les performances car elle permet de réduire les opérations de lecture et d'écriture sur le réseau. Si une application envoie et reçoit de petites quantités d'informations, la taille de paquets peut être définie à 512 octets, ce qui est suffisant pour la plupart des transferts de données.  
  
-   Pour des systèmes utilisant différents protocoles réseau, attribuez à l’option network packet size la taille adaptée au protocole le plus utilisé. L'option network packet size permet d'accroître les performances lorsque les protocoles réseau prennent en charge les paquets de grande taille. Les applications clientes peuvent remplacer cette valeur.  
  
-   Vous pouvez également appeler les fonctions OLE DB, ODBC (Open Database Connectivity ) et DB-Library pour demander une modification de la taille des paquets. Si le serveur ne peut pas prendre en charge la taille des paquets demandée, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] envoie un message d’avertissement au client. Dans certains cas, la modification de la taille des paquets peut entraîner un échec de la liaison de communication, tel que :  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure**, sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres pour modifier une option de configuration ou exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour configurer l'option Taille du paquet réseau  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur le nœud **Avancé** .  
  
3.  Sous **Réseau**, sélectionnez une valeur pour la zone **Taille du paquet réseau** .  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour configurer l'option Taille du paquet réseau  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `network packet size` la valeur `6500` octets.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option Taille du paquet réseau  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  