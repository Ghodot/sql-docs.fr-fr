---
title: Importer un projet Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3301c328-b0f5-4517-915c-93713413e453
caps.latest.revision: 5
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a433b21a4713388376c3b5c513e755d706e93c84
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296789"
---
# <a name="import-an-integration-services-project"></a>Importer un projet Integration Services
  Utilisez [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]**l’Assistant Importation de projet** pour créer un projet à partir d’un fichier existant de déploiement (.ispac) ou d’un projet déployé sur le catalogue Integration Services. Cette fonctionnalité est particulièrement utile lorsque vous n'avez pas la copie originale du projet, mais que vous voulez en créer un à partir d'un fichier .ispac ou d'un catalogue SSISDB.  
  
### <a name="to-import-a-project"></a>Pour importer un projet  
  
1.  Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cliquez sur **Nouveau** > **Projet** dans le menu **Fichier** .  
  
2.  Dans la zone **Modèles installés** de la fenêtre **Nouveau projet** , développez **Business Intelligence**, puis cliquez sur **Integration Services**.  
  
3.  Sélectionnez **l’Assistant Importation de projet Integration Services** dans la liste des types de projets.  
  
4.  Tapez le nom du nouveau projet à créer dans la zone de texte **Nom** .  
  
5.  Tapez le chemin ou l’emplacement du projet dans la zone de texte **Emplacement** ou cliquez sur **Parcourir** pour en sélectionner un.  
  
6.  Dans la zone de texte **Nom de solution** , tapez le nom de la solution.  
  
7.  Cliquez sur **OK** pour ouvrir la boîte de dialogue **Assistant Importation de projet Integration Services** .  
  
8.  Cliquez sur **Suivant** pour basculer vers la page **Sélectionner une source** .  
  
9. Si vous importez à partir d’un fichier **.ispac** , tapez le chemin avec le nom de fichier dans la zone de texte **Chemin d’accès** . Cliquez sur **Parcourir** pour accéder au dossier où vous souhaitez que la solution soit stockée et tapez le nom de fichier dans la zone de texte **Nom de fichier** , puis cliquez sur **Ouvrir**.  
  
     Si vous importez à partir d’un **Catalogue Integration Services**, tapez le nom de l’instance de base de données dans la zone de texte **Nom du serveur** ou cliquez sur **Parcourir** et sélectionnez l’instance de base de données contenant le catalogue.  
  
     Cliquez sur **Parcourir** en regard de la zone de texte **Chemin d’accès** , développez le dossier dans le catalogue, sélectionnez le projet que vous souhaitez importer, puis cliquez sur **OK**.  
  
     Cliquez sur **Suivant** pour passer à la page **Vérifier** .  
  
10. Vérifiez les informations et cliquez sur **Importer** pour créer un projet basé sur le projet existant sélectionné.  
  
11. Facultatif : cliquez **Enregistrer le rapport** pour enregistrer les résultats dans un fichier  
  
12. Cliquez sur **Fermer** pour fermer la boîte de dialogue **Assistant Importation de projet Integration Services** .  
  
  
