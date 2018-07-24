---
title: Éditeur de source SAP BW (page Colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c2ec8bb7-be9b-4783-ad88-32512de784b0
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb981a6b5de420e90c42246825536816abe9ace5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37154870"
---
# <a name="sap-bw-source-editor-columns-page"></a>Éditeur de source SAP BW (page Colonnes)
  Utilisez la page **Colonnes** de **l’Éditeur de source SAP BW** pour mapper une colonne de sortie à chaque colonne (source) externe.  
  
 Pour en savoir plus sur le composant source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Source SAP BW](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
 **Pour ouvrir la page Colonnes**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source SAP BW.  
  
3.  Dans l' **Éditeur de source SAP BW**, cliquez sur **Colonnes** pour ouvrir la page **Colonnes** de l'éditeur.  
  
## <a name="options"></a>Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer la source, adressez-vous à votre administrateur SAP.  
  
 **Colonnes externes disponibles**  
 Affichez la liste des colonnes externes disponibles dans la source de données, puis sélectionnez les colonnes à inclure dans le flux de données.  
  
 Pour inclure une colonne dans le flux de données, activez la case à cocher correspondant à cette colonne. L'ordre dans lequel vous sélectionnez les cases à cocher détermine l'ordre dans lequel les colonnes sont générées. Autrement dit, la première case à cocher que vous sélectionnez sera la première colonne de sortie, la deuxième case à cocher correspondra à la deuxième colonne de sortie, etc.  
  
 **Colonne externe**  
 Affichez les colonnes externes (source) que vous avez sélectionnées. Les colonnes sélectionnées apparaissent dans l'ordre dans lequel vous verrez les colonnes de sortie correspondantes lorsque vous configurerez les composants en aval qui consomment des données de cette source.  
  
 Pour modifier l'ordre des colonnes, dans la liste **Colonnes externes disponibles** , désactivez les cases à cocher de toutes les colonnes. Puis, sélectionnez les colonnes dans l'ordre d'apparition souhaité.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. La valeur par défaut correspond au nom de la colonne externe (source) sélectionnée. Toutefois, vous pouvez entrer un nom descriptif unique. [!INCLUDE[ssIS](../../includes/ssis-md.md)] affiche les noms **Colonne de sortie** pour les colonnes lorsque vous configurez les composants en aval qui consomment des données de cette source.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source SAP BW &#40;Page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Éditeur de source SAP BW &#40;page Sortie d’erreur&#41;](sap-bw-source-editor-error-output-page.md)   
 [Éditeur de source SAP BW &#40;page Avancé&#41;](sap-bw-source-editor-advanced-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  