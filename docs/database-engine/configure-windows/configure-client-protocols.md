---
title: "Configurer des protocoles clients | Microsoft Docs"
ms.custom: ""
ms.date: "07/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "protocoles par défaut"
  - "protocoles réseau [SQL Server], configuration du client"
  - "TCP/IP [SQL Server], protocoles clients"
  - "désactivation des protocoles clients"
  - "organisation des protocoles [SQL Server]"
  - "protocoles [SQL Server], ordre pour les ordinateurs clients"
  - "configurer des protocoles clients"
  - "protocoles clients [SQL Server]"
  - "protocoles [SQL Server], configuration du client"
  - "protocoles par défaut, client"
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Configurer des protocoles clients
  Cette rubrique décrit comment configurer les protocoles clients utilisés par les applications clientes dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge la communication cliente par le biais du protocole réseau TCP/IP et du protocole des canaux nommés. Le protocole de mémoire partagée est également disponible si le client se connecte à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur le même ordinateur. Il existe trois méthodes courantes de sélection du protocole.  
  
-   Configurer toutes les applications clientes de manière à ce qu'elles utilisent le même protocole réseau, en définissant l'ordre des protocoles dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Configurer une application cliente spécifique de manière à ce qu'elle utilise un protocole réseau particulier, en créant un alias. Pour plus d’informations, consultez [Créer ou supprimer un alias de serveur devant être utilisé par un client &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/create or delete a server alias for use by a client.md).  
  
-   Certaines applications clientes, telles que sqlcmd.exe, peuvent spécifier le protocole dans la chaîne de connexion. Pour plus d’informations, consultez [Se connecter au moteur de base de données avec sqlcmd](../../relational-databases/scripting/connect-to-the-database-engine-with-sqlcmd.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
###  <a name="EnableDisable"></a> Pour activer ou désactiver un protocole client  
  
1.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], développez **Configuration de SQL Server Native Client**, cliquez avec le bouton droit sur **Protocoles clients**, puis sélectionnez **Propriétés**.  
  
2.  Dans la zone **Protocoles désactivés**, cliquez sur un protocole, puis sélectionnez **Activer** pour l’activer.  
  
3.  Dans la zone **Protocoles activés**, cliquez sur un protocole, puis sélectionnez **Désactiver** pour le désactiver.  
  
###  <a name="ChangeDefault"></a> Pour modifier le protocole par défaut ou l'ordre des protocoles pour les ordinateurs clients  
  
1.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], développez **Configuration de SQL Server Native Client**, cliquez avec le bouton droit sur **Protocoles clients**, puis sélectionnez **Propriétés**.  
  
2.  Dans la zone **Protocoles activés**, cliquez sur **Monter** ou sur **Descendre** pour modifier l’ordre dans lequel les protocoles sont essayés lors d’une tentative de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le protocole figurant en première position dans la zone **Protocoles activés** est le protocole par défaut.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le Gestionnaire de configuration crée des entrées de Registre pour les configurations d’alias de serveur et la bibliothèque réseau cliente par défaut. Toutefois, l'application n'installe pas les bibliothèques réseau clientes, ni les protocoles réseau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les bibliothèques réseau clientes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont installées au cours de l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les protocoles réseau sont installés lors de l’installation de Microsoft Windows (ou via **Réseaux** dans le **Panneau de configuration**). Un protocole réseau spécifique peut ne pas être disponible lors de l’installation de Windows. Pour plus d'informations concernant l’installation de ces protocoles réseau, consultez la documentation de l'éditeur.  
  
###  <a name="Configure"></a> Pour configurer un client pour l'utilisation de TCP/IP  
  
1.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], développez **Configuration de SQL Server Native Client**, cliquez avec le bouton droit sur **Protocoles clients**, puis sélectionnez **Propriétés**.  
  
2.  Dans la zone **Protocoles activés**, cliquez sur la flèche vers le haut ou vers le bas pour modifier l’ordre dans lequel les protocoles sont essayés lors d’une tentative de connexion à SQL Server. Le protocole figurant en première position dans la zone **Protocoles activés** est le protocole par défaut.  
  
 Vous pouvez activer le protocole de mémoire partagée séparément en cochant la case **Activer le protocole de mémoire partagée**.  
  
## Voir aussi  
 [Configurer l'option de configuration du serveur remote login timeout](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md)  
  
  