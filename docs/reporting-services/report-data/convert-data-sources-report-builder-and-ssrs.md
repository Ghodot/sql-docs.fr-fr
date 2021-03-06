---
title: Convertir des sources de données (Générateur de rapports et SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-data
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f023eb10a1d9108ffe09c737525f7a88885148f9
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43282254"
---
# <a name="convert-data-sources-report-builder-and-ssrs"></a>Convertir des sources de données (Générateur de rapports et SSRS)
  Chaque source de données dans le volet des données de rapport est incorporée et est spécifique au rapport ou est partagée. Dans le Générateur de rapports, une source de données partagée pointe vers une source de données partagée publiée sur un serveur de rapports ou un site SharePoint. Dans le Concepteur de rapports, une source de données partagée pointe vers une source de données partagée dans l’Explorateur de solutions sous le dossier **Sources de données partagées** .  
  
 Pour plus d’informations sur les différences entre les sources de données incorporées et partagées, consultez [Connexions de données ou sources de données incorporées et partagées &#40;Générateur de rapports et SSRS&#41;](http://msdn.microsoft.com/library/f417782c-b85a-4c4d-8a40-839176daba56).  
  
 Pour plus d’informations sur la création d’une source de données partagée, consultez [Créer une source de données incorporée ou partagée &#40;SSRS&#41;](http://msdn.microsoft.com/library/b111a8d0-a60d-4c8b-b00a-51644b19c34b).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a>Concepteur de rapports  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>Pour convertir une source de données incorporée en source partagée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données, puis cliquez sur **Convertir en source de données partagée**.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**. Si le volet s'ouvre comme une fenêtre flottante, vous pouvez l'ancrer. Pour plus d’informations, consultez [Ancrer le volet des données de rapport dans le Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/tools/dock-the-report-data-pane-in-report-designer-ssrs.md).  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée. Dans l’Explorateur de solutions, une source de données partagée avec le même nom s’affiche sous le dossier **Sources de données partagées** .  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>Pour convertir une source de données partagée en source incorporée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données, ouvrez la boîte de dialogue **Propriétés de la source de données** , puis cliquez sur **Connexion incorporée**. Entrez les informations nécessaires.  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée.  
  
## <a name="report-builder"></a>Générateur de rapports  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>Pour convertir une source de données incorporée en source partagée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données pour ouvrir la boîte de dialogue **Propriétés de la source de données** , puis cliquez sur **Connexion incorporée**. Entrez les informations nécessaires.  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée.  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>Pour convertir une source de données partagée en source incorporée  
  
-   Dans le volet des données de rapport, cliquez avec le bouton droit sur la source de données, ouvrez la boîte de dialogue **Propriétés de la source de données** , puis cliquez sur **Connexion incorporée**. Entrez les informations nécessaires.  
  
     Dans le volet des données de rapport, l'icône de source de données se transforme en icône de source de données partagée.  
  
## <a name="see-also"></a> Voir aussi  
 [Gérer des sources de données de rapports](../../reporting-services/report-data/manage-report-data-sources.md)   
 [Connexions de données, sources de données et chaînes de connexion &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
