---
title: "Rechercher la cha&#238;ne de processus | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6303ea4-fbbf-4cba-bc60-828df62be8c2
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Rechercher la cha&#238;ne de processus
  Utilisez la boîte de dialogue **Rechercher la chaîne de processus** pour rechercher une chaîne de processus qui est définie dans le système SAP Netweaver BW. Lorsque la liste de chaînes de processus disponibles apparaît, sélectionnez la chaîne de votre choix. La source remplira les options associées à l'aide des valeurs requises.  
  
 La source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW utilise la boîte de dialogue **Rechercher la chaîne de processus** . Pour en savoir plus sur la source SAP BW, consultez [SAP BW Source](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Rechercher la chaîne de processus**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données**, double-cliquez sur la source SAP BW.  
  
3.  Dans l' **Éditeur de source SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la zone de groupe **Chaîne de processus** , cliquez sur **Rechercher** pour afficher la boîte de dialogue **Rechercher la chaîne de processus** .  
  
     La zone de groupe **Chaîne de processus** apparaît uniquement si la valeur de **Mode d’exécution** est **P - Déclencher une chaîne de processus**.  
  
## Options de recherche  
 Dans les champs de recherche, vous pouvez filtrer les résultats à l'aide du caractère générique astérisque (*), ou en utilisant une chaîne partielle conjointement avec le caractère générique astérisque. Cependant, si vous laissez un champ de recherche vide, l'opération de recherche mettra uniquement en correspondance les chaînes vides de ce champ.  
  
 **Chaîne de processus**  
 Entrez le nom de la chaîne de processus à rechercher, ou entrez un nom partiel avec le caractère générique astérisque (*). Sinon, utilisez le caractère générique astérisque seul pour inclure toutes les chaînes de processus.  
  
 **Rechercher**  
 Recherchez des chaînes de processus correspondantes définies dans le système SAP Netweaver BW.  
  
## Résultats de la recherche  
 Après avoir cliqué sur le bouton Rechercher, une liste de chaînes de processus dans le système SAP Netweaver BW apparaît dans un tableau avec les en-têtes de colonnes suivants :  
  
 **Chaîne de processus**  
 Affiche le nom de la chaîne de processus qui est définie dans le système SAP Netweaver BW.  
  
 **Description**  
 Affiche la description de la chaîne de processus.  
  
 Lorsque la liste de chaînes de processus disponibles apparaît, sélectionnez la chaîne de votre choix. La source remplira les options associées à l'aide des valeurs requises.  
  
## Voir aussi  
 [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  