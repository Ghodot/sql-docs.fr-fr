---
title: "Conditions préalables requises pour consulter des didacticiels (Générateur de rapports) | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2c2056dccbb2d65e880928e4ec37a70080cfbf53
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---

# <a name="prerequisites-for-tutorials-report-builder"></a>Éléments requis pour les didacticiels (Générateur de rapports)

L’utilisation des didacticiels du Générateur de rapports suppose que vous pouvez afficher et enregistrer des rapports paginés [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] sur un serveur de rapports ou un site SharePoint intégré à un serveur de rapports. Pour les données, tous les didacticiels utilisent des requêtes littérales qui doivent être traités par une instance de SQL Server.  
  
Si vous n'avez pas accès à un serveur de rapports, un site de serveur de rapports ou une source de données, vous pouvez en apprendre plus sur le Générateur de rapports en générant un rapport hors connexion. Consultez [didacticiel : créer un rapport de graphique rapide en mode hors connexion &#40; Le Générateur de rapports &#41; ](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  

## <a name="requirements"></a>Spécifications

Pour exécuter les didacticiels du Générateur de rapports, vous devez réunir les conditions suivantes :  
  
-   Accès au Générateur de rapports. Vous pouvez exécuter le Générateur de rapports depuis un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] ou un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] en mode intégré SharePoint. Seule la première étape, l’ouverture du Générateur de rapports, varie selon les différents serveurs.  
  
    Sur un serveur de rapports, sélectionnez **Nouveau** > **Rapport paginé**.
  
    Sur un serveur de rapports en mode intégré SharePoint, sous l’onglet **Documents** , sélectionnez **Nouveau Document**et, dans la liste déroulante, sélectionnez **Rapport du Générateur de rapports**. Par exemple, `http://<servername>/sites/mySite/reports`. L'administrateur SharePoint doit activer la fonctionnalité Rapport du Générateur de rapports pour chaque bibliothèque de documents.  
  
-   URL pointant vers un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] ou un site SharePoint intégré à un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] . Vous devez être autorisé à enregistrer et consulter des rapports, des sources de données partagées, des datasets partagés, des parties de rapports et des modèles. Par défaut, l’URL d’un serveur de rapports est `http://<servername>/reportserver`. Par défaut, l’URL d’un site SharePoint est `http://<sitename>` ou `http://<server>/site`.  
  
-   Le nom d’une instance de SQL Server et les informations d’identification suffisantes pour l’accès en lecture seule aux bases de données. Les requêtes de jeu de données dans les didacticiels utilisent des données littérales, mais chaque requête doit être traitée par une instance de SQL Server pour retourner les métadonnées qui est requises pour un dataset de rapport. Par exemple, la chaîne de connexion suivante spécifie uniquement un serveur : `data source=<servername>`. Vous devez avoir un accès en lecture à la base de données par défaut qui vous est affectée par l'administrateur système qui vous accorde l'autorisation d'accès au serveur. Vous pouvez également spécifier une base de données, comme indiqué dans la chaîne de connexion suivante : `data source=<servername>;initial catalog=<database>`.  
  
-   Pour le [didacticiel : rapport cartographique (Générateur de rapports)](Tutorial:%20Map%20Report%20\(Report%20Builder\).md), le serveur de rapports doit être configuré pour prendre en charge de Bing maps en guise d’arrière-plan. Pour plus d’informations, consultez [Planifier la prise en charge de rapport cartographique](http://msdn.microsoft.com/en-us/5ddc97a7-7ee5-475d-bc49-3b814dce7e19).   

-   Le [didacticiel : création et extraction principal rapports (Générateur de rapports)](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md) didacticiel requiert l’accès au cube Contoso Sales. Pour plus d’informations, consultez le didacticiel. 
  
L’administrateur du serveur de rapports doit vous accorder les autorisations nécessaires sur le serveur de rapports, configurer les emplacements des dossiers [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] et configurer les options par défaut du Générateur de rapports. Pour plus d’informations, consultez [Installer et désinstaller le Générateur de rapports](http://msdn.microsoft.com/library/2c9a5814-17bf-4947-8fb3-6269e7caa416).  

## <a name="next-steps"></a>Étapes suivantes

[Didacticiels du Générateur de rapports](../reporting-services/report-builder-tutorials.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)