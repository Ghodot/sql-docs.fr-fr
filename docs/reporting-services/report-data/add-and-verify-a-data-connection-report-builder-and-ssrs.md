---
title: "Ajouter et v&#233;rifier une connexion de donn&#233;es (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: 1d3b2573-e29d-480d-9dde-d26379c86618
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 11
---
# Ajouter et v&#233;rifier une connexion de donn&#233;es (G&#233;n&#233;rateur de rapports et SSRS)
  Dans le Générateur de rapports, vous pouvez ajouter une source de données partagée depuis le serveur de rapports ou créer une source de données incorporée pour votre rapport. Dans le Concepteur de rapports, vous pouvez créer une source de données partagée ou une source de données incorporée et la déployer sur un serveur de rapports.  
  
 Pour ajouter une source de données partagée à votre rapport, accédez à un serveur de rapports et sélectionnez une source de données partagée. La source de données partagée de votre rapport pointe vers la définition de la source de données partagée sur le serveur de rapports.  
  
 Pour créer une source de données incorporée, vous devez disposer des informations de connexion à la source de données externe et connaître les autorisations dont vous avez besoin pour accéder aux données. Ces informations proviennent généralement du propriétaire de la source de données. Vous pouvez tester la connexion pour vérifier que les informations d'identification spécifiées sont suffisantes.  
  
 Pour plus d’informations, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md) ou [Spécifier des informations d’identification dans le Générateur de rapports](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour créer une connexion à une source de données partagée dans le Générateur de rapports  
  
1.  Dans la barre d’outils du volet des données de rapport, cliquez sur **Nouveau**, puis sur **Source de données**. La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
2.  Dans la zone de texte **Nom**, tapez le nom de la source de données.  
  
    > [!NOTE]  
    >  Ce nom est enregistré dans la définition de rapport locale. Ce nom ne correspond pas au nom de la source de données partagée sur le serveur de rapports.  
  
3.  Sélectionnez **Utiliser une connexion partagée ou un modèle de rapport**. Vous obtenez la liste des sources de données partagées et des modèles de rapport utilisés récemment. Pour en sélectionner un à partir d’un serveur de rapports, cliquez sur **Parcourir** et accédez au dossier où sont stockées les sources de données partagées disponibles sur le serveur de rapports.  
  
4.  Sélectionnez la source de données partagée, puis cliquez sur **Ouvrir**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 La source de données apparaît dans le volet des données de rapport.  
  
### Pour vérifier une connexion de données  
  
1.  Dans la barre d'outils du volet des données de rapport, double-cliquez sur la source de données. La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
2.  Cliquez sur **Tester la connexion**.  
  
3.  Si la connexion a abouti, le message suivant apparaît : « La connexion a été correctement créée ». [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  Si la connexion n'a pas abouti, le message suivant s'affiche : « Impossible de se connecter à la source de données ».  
  
5.  Cliquez sur **Détails** et utilisez les informations pour corriger le problème.  
  
     Pour plus d’informations, consultez [Spécifier des informations d’identification dans le Générateur de rapports](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Jeux de données du rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)  
  
  