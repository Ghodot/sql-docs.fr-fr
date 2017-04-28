---
title: "Ajouter, modifier ou supprimer un param&#232;tre de rapport (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Ajouter, modifier ou supprimer un param&#232;tre de rapport (G&#233;n&#233;rateur de rapports et SSRS)
  Un paramètre de rapport permet de choisir les données du rapport, d'interconnecter les rapports associés et de varier la présentation du rapport concerné. Vous pouvez fournir une valeur par défaut et une liste de valeurs disponibles. De son côté, l'utilisateur peut modifier la sélection.  
  
 Après la publication d'un rapport, vous pouvez modifier les valeurs par défaut, les valeurs disponibles et d'autres propriétés d'un paramètre de rapport sur le serveur de rapports. Vous pouvez fournir plusieurs jeux de valeurs de paramètre par défaut en créant des rapports liés. Pour plus d’informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 Cet article porte sur l’ajout de paramètres de rapport à un rapport paginé dans le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] ou le Concepteur de rapports dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Vous pouvez également ajouter des paramètres de rapport à des rapports mobiles dans  [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long-md.md)]. Consultez la rubrique [Create mobile reports with SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) (éventuellement en anglais) pour plus d'informations.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour ajouter ou modifier un paramètre de rapport  
  
1.  Dans [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]Concepteur de rapports dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans le volet **Données du rapport**, cliquez avec le bouton droit sur le nœud **Paramètres**, puis cliquez sur **Ajouter un paramètre**. La boîte de dialogue **Propriétés du paramètre de rapport** s'ouvre.  
  
2.  Dans **Nom**, tapez le nom du paramètre ou acceptez le nom par défaut.  
  
3.  Dans **Demander**, tapez le texte à afficher en regard de la zone de texte du paramètre lorsque l'utilisateur exécute le rapport.  
  
4.  Dans **Type de données**, sélectionnez le type de données pour la valeur du paramètre.  
  
5.  Si le paramètre peut contenir une valeur vide, sélectionnez **Autoriser une valeur vide**.  
  
6.  Si le paramètre peut contenir une valeur Null, sélectionnez **Autoriser les valeurs de type NULL**.  
  
7.  Pour autoriser un utilisateur à sélectionner plusieurs valeurs pour le paramètre, sélectionnez **Autoriser les valeurs multiples**.  
  
8.  Définissez l'option de visibilité.  
  
    -   Pour afficher le paramètre dans la barre d'outils en haut du rapport, sélectionnez **Visible**.  
  
    -   Pour masquer le paramètre afin qu'il n'affiche pas dans la barre d'outils, sélectionnez **Masqué**.  
  
    -   Pour masquer le paramètre et empêcher sa modification sur le serveur de rapports une fois le rapport publié, sélectionnez **Interne**. Le paramètre de rapport ne peut alors être affiché que dans la définition du rapport. Pour cette option, vous devez définir une valeur par défaut ou autoriser le paramètre à accepter une valeur nulle.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour supprimer un paramètre de rapport  
  
1.  Dans le volet **Données du rapport** , développez le nœud **Paramètres** .  
  
2.  Cliquez avec le bouton droit sur le paramètre de rapport, puis cliquez sur **Supprimer**.  
  
## Voir aussi  
 [Ajouter, modifier ou supprimer les valeurs disponibles d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add, change, or delete available values for a report parameter.md)   
 [Ajouter, modifier ou supprimer les valeurs par défaut d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add, change, or delete default values for a report parameter.md)   
 [Modifier l’ordre d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Ajouter des paramètres en cascade à un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Didacticiel : Ajout d’un paramètre à un rapport &#40;Générateur de rapports&#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add dataset filters, data region filters, and group filters.md)   
 [Informations de référence sur la collection de paramètres &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/parameters-collection-references-report-builder-and-ssrs.md)   
 [Ajouter un paramètre à valeurs multiples sur un rapport](../../reporting-services/report-design/add-a-multi-value-parameter-to-a-report.md)  
  
  