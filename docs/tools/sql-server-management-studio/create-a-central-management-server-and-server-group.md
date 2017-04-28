---
title: "Cr&#233;er un serveur d&#39;administration centralis&#233;e et un groupe de serveurs (SQL Server Management Studio) | Microsoft Docs"
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
  - "serveur de configuration"
ms.assetid: da265482-3953-440a-ac23-0ab7e42a55eb
caps.latest.revision: 35
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# Cr&#233;er un serveur d&#39;administration centralis&#233;e et un groupe de serveurs (SQL Server Management Studio)
  Cette rubrique explique comment désigner une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme serveur de gestion centralisée dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Les serveurs d'administration centralisée stockent une liste d'instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette liste est organisée en un ou plusieurs groupes de serveurs d'administration centralisée. Les actions prises en utilisant un groupe de serveurs d'administration centralisée s'appliquent à tous les serveurs du groupe. Cela inclut la connexion aux serveurs à l'aide de l'Explorateur d'objets et l'exécution d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] et de stratégies de la Gestion basée sur des stratégies sur plusieurs serveurs simultanément.  
  
> [!NOTE]  
>  Les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ne peuvent pas être désignées en tant que serveur d'administration centralisée.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer un serveur de gestion centralisée et un groupe de serveurs à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Dans la base de données msdb, deux rôles de base de données accordent l'accès aux serveurs d'administration centralisée. Seuls les membres du rôle ServerGroupAdministratorRole peuvent gérer le serveur d'administration centralisée. L'appartenance au rôle ServerGroupReaderRole est requise pour se connecter à un serveur d'administration centralisée.  
  
 Dans la mesure où les connexions gérées par un serveur d'administration centralisée s'exécutent dans le contexte de l'utilisateur, avec l'authentification Windows, les autorisations effectives sur les serveurs inscrits peuvent varier. Par exemple, l'utilisateur peut être membre du rôle serveur fixe sysadmin sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, mais disposer d'autorisations limitées sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Les procédures suivantes expliquent comment effectuer les étapes suivantes.  
  
1.  Créez un serveur d'administration centralisée.  
  
2.  Ajoutez un ou plusieurs groupes de serveurs au serveur de gestion centralisée et ajoutez un ou plusieurs serveurs inscrits dans les groupes.  
  
#### Créer un serveur d'administration centralisée  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
  
2.  Dans Serveurs inscrits, développez **Moteur de base de données**, cliquez avec le bouton droit sur **Serveurs de gestion centralisée**, puis cliquez sur **Inscrire le serveur de gestion centralisée**.  
  
3.  Dans la boîte de dialogue **Nouvelle inscription de serveur**, sélectionnez l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous souhaitez désigner en tant que serveur d’administration centralisée dans la liste déroulante. Vous devez utiliser l'authentification Windows pour le serveur d'administration centralisée.  
  
4.  Dans **Serveur inscrit**, entrez un nom de serveur et une description facultative.  
  
5.  Dans l'onglet **Propriétés de connexion** , consultez ou modifiez les propriétés réseau et de connexion. Pour plus d’informations, consultez [Se connecter au serveur &#40;page Propriétés de connexion&#41; — Moteur de base de données](../../ssms/f1-help/connect-to-server-connection-properties-page-database-engine.md).  
  
6.  Cliquez sur **Tester**pour tester la connexion.  
  
7.  Cliquez sur **Enregistrer**. L'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] apparaît sous le dossier **Serveurs de gestion centralisée** .  
  
#### Créer un nouveau groupe de serveurs et ajouter des serveurs au groupe  
  
1.  Dans **Serveurs inscrits**, développez **Serveurs de gestion centralisée**. Cliquez avec le bouton droit sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ajoutée dans la procédure ci-dessus et sélectionnez **Nouveau groupe de serveurs**.  
  
2.  Dans **Propriétés du nouveau groupe de serveurs**, entrez un nom de groupe et une description facultative.  
  
3.  Dans **Serveurs inscrits**, cliquez avec le bouton droit sur le groupe de serveurs, puis cliquez sur **Nouvelle inscription de serveur**.  
  
4.  Dans Nouvelle inscription de serveur, sélectionnez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Créer un serveur inscrit &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/create-a-new-registered-server-sql-server-management-studio.md). Ajoutez davantage de serveurs le cas échéant.  
  
#### Pour exécuter des requêtes sur plusieurs cibles de configuration en même temps  
  
-   Après avoir créé un serveur d'administration centralisée, un ou plusieurs groupes de serveurs et un ou plusieurs serveurs inscrits, vous pouvez exécuter des requêtes simultanément sur l'ensemble d'un groupe. Pour plus d’informations sur l’exécution simultanée d’instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] sur les serveurs d’un groupe de serveurs, consultez [Exécuter des instructions sur plusieurs serveurs simultanément &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/execute statements against multiple servers simultaneously.md).  
  
## Voir aussi  
 [Administrer plusieurs serveurs à l'aide de serveurs de gestion centralisée](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  