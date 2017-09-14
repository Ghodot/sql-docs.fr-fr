---
title: "Concepts de paramètres (Générateur de rapports et SSRS) rapport | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cb4044deed8935af354e1c6f15ace89f0b3e5010
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="report-parameters-concepts-report-builder-and-ssrs"></a>Concepts de paramètres de rapport (Générateur de rapports et SSRS)
  Vous pouvez ajouter des paramètres à un rapport pour lier des rapports connexes, pour contrôler l'apparence d'un rapport, pour filtrer les données du rapport, ou pour limiter l'étendue d'un rapport à des utilisateurs ou des emplacements spécifiques.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Les paramètres de rapport sont créés des manières suivantes :  
  
-   Automatiquement, lorsque vous définissez la requête de dataset qui contient des variables de requête. Pour chaque variable de requête, un paramètre de requête de dataset et un paramètre de rapport correspondants portant les mêmes noms sont créés. Un paramètre de requête peut être une référence à une variable de requête ou à un paramètre d'entrée pour une procédure stockée.  
  
-   Automatiquement, lorsque vous ajoutez une référence à un dataset partagé qui contient des paramètres de requête.  
  
-   Manuellement, lorsque vous créez des paramètres de rapport dans le volet Données du rapport. Les paramètres font partie des collections intégrées que vous pouvez inclure dans une expression dans un rapport. Étant donné que les expressions sont utilisées pour définir des valeurs dans l'ensemble d'une définition de rapport, vous pouvez utiliser des paramètres pour contrôler l'apparence du rapport ou pour transmettre des valeurs aux sous-rapports ou aux rapports connexes qui utilisent également des paramètres.  
  
 Pour plus d’informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 Les paramètres sont fréquemment utilisés pour filtrer des données de rapport à la fois avant et après le retour des données sur le rapport. Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
 Lorsque vous concevez un rapport, les paramètres de rapport sont enregistrés dans la définition de rapport. Lorsque vous publiez un rapport, les paramètres de rapport sont enregistrés et gérés indépendamment de la définition de rapport. Après avoir enregistré le rapport sur le serveur de rapports, vous pouvez effectuer les opérations suivantes :  
  
-   Modifiez des valeurs de paramètres du rapport directement sur le serveur de rapports, indépendamment de la définition de rapport.  
  
-   Créez plusieurs rapports liés dans lesquels chaque rapport lié est un lien vers la définition de rapport avec un jeu distinct de valeurs de paramètres pouvant être gérées indépendamment sur le serveur de rapports.  
  
 Si vous projetez de créer des instantanés de rapport, des historiques ou des abonnements à un rapport publié, vous devez comprendre l'effet des paramètres de rapport sur les exigences de conception du rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Rapports création Concepts &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md)   
 [Rapport incorporé des jeux de données et des Datasets partagés &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Didacticiel : Ajouter un paramètre à votre rapport &#40; Le Générateur de rapports &#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  