---
title: "Cr&#233;er, modifier et supprimer des instantan&#233;s dans l&#39;historique de rapport | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instantanés [Reporting Services]"
  - "instantanés de rapport [Reporting Services]"
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
caps.latest.revision: 40
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 40
---
# Cr&#233;er, modifier et supprimer des instantan&#233;s dans l&#39;historique de rapport
  L'historique de rapport est un ensemble d'instantanés de rapport. Vous pouvez gérer l'historique de rapport en ajoutant et en supprimant des instantanés, ou en modifiant les propriétés qui affectent le stockage de l'historique de rapport. Vous pouvez créer un historique de rapport manuellement ou de manière planifiée.  
  
 Pour créer un historique de rapport, votre attribution de rôle doit inclure la tâche « Gérer l'historique de rapport ». Pour afficher un historique de rapport, votre attribution de rôle doit inclure la tâche « Afficher les rapports ». L'historique de rapport est mis à la disposition de tous les utilisateurs ayant accès au rapport. Vous ne pouvez pas activer ou désactiver sélectivement l'historique de rapport pour un sous-ensemble d'utilisateurs.  
  
 Les instantanés dans l'historique de rapport sont identifiés par la date et l'heure de leur création. La date et l'heure dépendent du moment d'exécution de la requête.  
  
## Création d'instantanés l'historique de rapport  
 Les instantanés peuvent être créés manuellement ou à intervalles planifiés pour un rapport pouvant s'exécuter de manière automatisée. Pour pouvoir s'exécuter de manière automatisée, le rapport doit utiliser des informations d'identification stockées ou ne pas en utiliser du tout. Par ailleurs, si le rapport utilise des paramètres, vous devez spécifier les valeurs par défaut à utiliser lors de l'exécution du rapport. Vous pouvez spécifier les informations d'identification stockées et les valeurs des paramètres dans les pages des propriétés du rapport. Pour plus d’informations, consultez [Page de propriétés des paramètres &#40;Gestionnaire de rapports&#41;](../Topic/Parameters%20Properties%20Page%20\(Report%20Manager\).md).  
  
 Lorsque vous créez un instantané de rapport, les éléments suivants sont stockés avec l'instantané de rapport dans la base de données du serveur de rapports :  
  
-   Le jeu de résultats (c'est-à-dire les données du rapport, extraites par le biais des informations d'identification spécifiées dans la page des propriétés des sources de données du rapport).  
  
-   La définition de rapport sous-jacente, telle qu'elle existait lors de la création de l'instantané. Si la définition de rapport est modifiée après la génération de l'instantané, les modifications ne sont pas prises en compte dans l'instantané.  
  
-   Les valeurs de paramètres qui sont utilisées pour obtenir ou filtrer le jeu de résultats.  
  
-   Les ressources intégrées, comme les images. Les ressources externes qui sont liées à un rapport ne sont pas stockées avec l'instantané de rapport.  
  
 Les façons dont l'historique de rapport peut être créé et le nombre d'instantanés de rapport qui peut être stocké sont déterminés par des paramètres.  
  
 Si un rapport produit une erreur, aucun instantané n'est créé. Les rapports qui produisent des avertissements peuvent néanmoins s'exécuter et être utilisés pour générer des instantanés.  
  
## Modification de propriétés et suppression de l'historique de rapport  
 Un instantané de rapport existant ne peut pas être modifié. Vous pouvez toutefois modifier les propriétés de manière à supprimer l'historique de rapport.  
  
 Un historique de rapport peut être supprimé des façons suivantes :  
  
-   Suppression manuelle d'instantanés individuels ou en groupes.  
  
     Vous pouvez supprimer les instantanés de la page Historique du Gestionnaire de rapports. Accédez au rapport, cliquez sur Historique, cochez la case correspondant aux instantanés à supprimer, puis cliquez sur **Supprimer**.  
  
-   Diminution de la limite de l'historique de rapport afin de réduire le nombre d'instantanés qui sont stockés. La limite de l'historique de rapport peut être définie pour le serveur de rapports ou pour des rapports spécifiques. Lorsque la limite est abaissée, les instantanés les plus anciens sont supprimés de l'historique.  
  
 Vous ne pouvez pas supprimer en bloc l'ensemble de l'historique de rapport stocké sur un serveur de rapports.  
  
 L'historique de rapport est également supprimé lorsque vous supprimez un rapport. Si, par exemple, vous supprimez un rapport de ventes mensuelles pour le remplacer par une version plus récente, l'ensemble de l'historique de rapport associé au rapport est également supprimé. Cependant, si vous déplacez un rapport, son historique l'accompagne.  
  
## Voir aussi  
 [Créer un historique de rapport &#40;Reporting Services en mode intégré SharePoint&#41;](../../reporting-services/report-server/create-report-history-reporting-services-in-sharepoint-integrated-mode.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Gestion du contenu du serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Ajout d’un instantané à un historique de rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Limiter l’historique de rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/reports/limit-report-history-report-manager.md)  
  
  