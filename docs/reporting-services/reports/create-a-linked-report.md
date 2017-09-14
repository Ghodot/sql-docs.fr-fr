---
title: "Créer un rapport lié | Documents Microsoft"
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
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
caps.latest.revision: 44
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 232e24ef08c24d5c6a2c9799094fc492305eea46
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="create-a-linked-report"></a>Créer un rapport lié
  Un rapport lié est un élément de serveur de rapports qui fournit un point d'accès à un rapport existant. Au niveau conceptuel, il est assimilable au raccourci d'un programme que vous utilisez pour exécuter une application ou ouvrir un fichier.  
  
 Un rapport lié est issu d'un rapport existant et il reste fidèle à la définition de rapport d'origine. Il hérite toujours des propriétés de la source de données et de la mise en page du rapport d'origine. Toutes les autres propriétés et toutes les autres valeurs peuvent différer, notamment la sécurité, les paramètres, l'emplacement, les abonnements et les planifications.  
  
 Vous créez un rapport lié lorsque vous voulez créer des versions supplémentaires d'un rapport existant. Ainsi, vous pouvez trouver pratique d'utiliser un rapport de ventes régional unique pour créer des rapports spécifiques aux régions pour tous vos secteurs de ventes.  
  
 Bien que les rapports liés soient généralement basés sur des rapports paramétrés, il n'est pas obligatoire de recourir à des rapports paramétrés. Vous pouvez créer des rapports liés dès lors que vous souhaitez déployer un rapport existant avec des paramètres différents.  
  
### <a name="to-create-a-linked-report"></a>Pour créer un rapport lié  
  
1.  Dans le Gestionnaire de rapports, accédez au dossier qui contient le rapport à lier, puis ouvrez le menu d’options et cliquez sur **Créer un rapport lié**.  
  
2.  Indiquez un nom pour le nouveau rapport lié. Tapez éventuellement une description.  
  
3.  Pour sélectionner un autre dossier pour le rapport, cliquez sur **Modifier l’emplacement**. Cliquez ensuite sur le dossier à utiliser ou tapez son nom dans la zone **Emplacement** . [!INCLUDE[clickOK](../../includes/clickok-md.md)]Si vous ne sélectionnez pas un autre dossier, le rapport lié est créé dans le dossier actif (où est stocké le rapport, sur qu'il est basé).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]Le rapport lié s’ouvre.  
  
     L'icône d'un rapport lié est différente des autres éléments gérés par un serveur de rapports. L'icône ci-après indique un rapport lié :  
  
     ![Icône Rapport lié](../../reporting-services/report-server/media/hlp-16linked.gif "Icône Rapport lié")  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir et fermer un rapport &#40; Le Gestionnaire de rapports &#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [Page nouveau rapport lié &#40; Le Gestionnaire de rapports &#41;](http://msdn.microsoft.com/library/fefb46e8-6901-4d50-a3f8-7c49ad72e7b1)   
 [Choisissez la Page d’emplacement de l’élément &#40; Le Gestionnaire de rapports &#41;](http://msdn.microsoft.com/library/4a53a1a8-d1e1-47ef-b1fc-63352ece7d3c)   
 [Page propriétés générales, rapports &#40; Le Gestionnaire de rapports &#41;](http://msdn.microsoft.com/library/66c99d28-ab41-45f0-bf02-ed560293595d)   
 [Reporting Services Concepts &#40; SSRS &#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Le Gestionnaire de rapports &#40; En Mode natif de SSRS &#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)  
  
  