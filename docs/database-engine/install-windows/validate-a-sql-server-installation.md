---
title: "Valider une installation SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "validation des installations [SQL Server]"
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
caps.latest.revision: 31
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 31
---
# Valider une installation SQL Server
  Le rapport de découverte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisé pour vérifier la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur. Le **rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées ** affiche un rapport de tous les produits et fonctionnalités [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] installés sur le serveur local. Le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est disponible sur la page **Outils** du Centre d'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Pour exécuter le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :**  
  
 Dans le menu **Démarrer**, lancez le Centre d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pointez sur **Tous les programmes**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<nom_de_version>**, **Outils de configuration**, puis cliquez sur **Centre d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**. Pour exécuter le rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cliquez sur **Outils** dans la zone de navigation gauche du **Centre d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**, puis cliquez sur **Rapport de découverte des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées**.  
  
 Le rapport de découverte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est enregistré dans %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<dernière session d’installation\>.  
  
 Vous pouvez également générer le rapport de découverte via la ligne de commande. Exécutez « Setup.exe /Action=RunDiscovery » à partir d’une invite de commandes. Si vous ajoutez « /q » à la ligne de commande ci-dessus, aucune interface utilisateur ne s’affiche, mais le rapport est toutefois créé dans %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<dernière session d’installation\>.  
  
## Voir aussi  
 [Afficher et lire les fichiers journaux d'installation de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  