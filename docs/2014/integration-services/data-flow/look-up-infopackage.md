---
title: Rechercher un Infopackage| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce2da77e51370960d433981e28c32c5e7c4e55cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151320"
---
# <a name="look-up-infopackage"></a>Rechercher un InfoPackage
  Utilisez la boîte de dialogue **Rechercher un InfoPackage** pour rechercher un InfoPackage qui est défini dans le système SAP Netweaver BW. Lorsque la liste d'InfoPackages apparaît, sélectionnez l'InfoPackage de votre choix. La destination remplira les options associées à l'aide des valeurs requises.  
  
 La destination SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW utilise la boîte de dialogue **Rechercher la chaîne de processus** . Pour en savoir plus sur la destination SAP BW, consultez [SAP BW Destination](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Rechercher un InfoPackage**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la destination SAP BW.  
  
3.  Dans l' **Éditeur de destination SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la page **Gestionnaire de connexions** , dans la zone de groupe **InfoPackage/InfoSource** , cliquez sur **Rechercher** pour afficher la boîte de dialogue **Rechercher un InfoPackage** .  
  
## <a name="lookup-options"></a>Options de recherche  
 Dans les champs de recherche, vous pouvez filtrer les résultats à l'aide du caractère générique astérisque (*), ou en utilisant une chaîne partielle conjointement avec le caractère générique astérisque. Cependant, si vous laissez un champ de recherche vide, l'opération de recherche mettra uniquement en correspondance les chaînes vides de ce champ.  
  
 **InfoPackage**  
 Entrez le nom de l'InfoPackage à rechercher, ou un nom partiel avec le caractère générique astérisque (*). Sinon, utilisez le caractère générique astérisque seul pour inclure tous les InfoPackages.  
  
 **InfoSource**  
 Entrez le nom de l'InfoSource ou un nom partiel avec le caractère générique astérisque (*). Sinon, utilisez le caractère générique astérisque seul pour inclure tous les InfoPackages, indépendamment d'InfoSource.  
  
 **Système source**  
 Entrez le nom du système source ou un nom partiel avec le caractère générique astérisque (*). Sinon, utilisez le caractère générique astérisque seul pour inclure tous les InfoPackages, indépendamment des systèmes sources.  
  
 **Rechercher**  
 Recherchez les InfoPackages correspondants qui sont définis dans le système SAP Netweaver BW.  
  
## <a name="lookup-results"></a>Résultats de la recherche  
 Après avoir cliqué sur le bouton Rechercher, une liste des InfoPackages du système SAP Netweaver BW apparaît dans un tableau avec les en-têtes de colonnes suivants.  
  
 **InfoPackage**  
 Affiche le nom de l'InfoPackage qui est défini dans le système SAP Netweaver BW.  
  
 **Type**  
 Affiche le type de l'InfoPackage. Le tableau suivant répertorie les valeurs possibles pour le type.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Trans.|Données de transaction.|  
|Attr.|Données d'attribut.|  
|Textes|Textes.|  
  
 **Description**  
 Affiche la description de l'InfoPackage.  
  
 **InfoSource**  
 Affiche le nom de l'InfoSource, le cas échéant, qui est associé à l'InfoPackage.  
  
 **Source System**  
 Affiche le nom du système source.  
  
 Lorsque la liste d'InfoPackages apparaît, sélectionnez l'InfoPackage de votre choix. La destination remplira les options associées à l'aide des valeurs requises.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Destination SAP BW &#40;Page Gestionnaire de connexions&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
