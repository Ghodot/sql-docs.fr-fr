---
title: Accorder des autorisations administrateur du serveur (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4af61a59de6175d4241cb6b1b9700ff7ba816430
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328849"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a>Octroyer des autorisations d'administration de serveur (Analysis Services)
  Les membres du rôle administrateur de serveur dans une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ont un accès illimité à tous les objets et données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de cette instance. Un utilisateur doit être membre du rôle administrateur de serveur pour pouvoir exécuter n'importe quelle tâche sur le serveur, telle que créer ou traiter une base de données, modifier des propriétés du serveur ou lancer une trace (autre que pour les événements de traitement).  
  
 L'appartenance au rôle est établie lorsque [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est installé. L'utilisateur exécutant le programme d'installation peut s'ajouter lui-même au rôle, ou ajouter un autre utilisateur, lors de la mise en service du serveur. Vous pouvez modifier l'appartenance au rôle en tant que tâche consécutive à l'installation à l'aide de la procédure suivante.  
  
## <a name="modify-server-role-membership"></a>Modifier l'appartenance au rôle de serveur  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], cliquez avec le bouton droit sur le nom de l’instance dans l’Explorateur d’objets, puis sélectionnez **Propriétés**.  
  
2.  Cliquez sur **Sécurité** dans le volet **Sélectionner une page** , puis sur **Ajouter** au bas de la page pour ajouter un ou plusieurs utilisateurs ou groupes Windows au rôle de serveur.  
  
     ![Boîte de dialogue Ajouter les utilisateurs dans management studio](../media/ssas-serveradminadd.png "boîte de dialogue Ajouter les utilisateurs dans management studio")  
  
 Au moment de l'installation, le programme d'installation de SQL Server nécessite de spécifier au moins un compte d'utilisateur en tant qu'administrateur système Analysis Services.  
  
 Par défaut, des droits d'administration sont également accordés aux membres du groupe local Administrateurs dans Analysis Server. Bien que l'appartenance au rôle administrateur de serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne soit pas accordée explicitement au groupe local, les administrateurs locaux peuvent créer des bases de données, ajouter des utilisateurs et des autorisations et effectuer toute autre tâche autorisée aux administrateurs système. Ce comportement est configurable. Il est déterminé par le `BuiltinAdminsAreServerAdmins` propriété du serveur, qui est définie sur **true** par défaut. Vous pouvez modifier cette propriété dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, voir [Security Properties](../server-properties/security-properties.md).  
  
 Vous pouvez également gérer les rôles de serveur en utilisant AMO (Analysis Management Objects). Pour plus d’informations, consultez [Développement avec AMO &#40;Analysis Management Objects&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Autoriser l’accès aux objets et aux opérations &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Rôles de sécurité &#40;Analysis Services - données multidimensionnelles&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
