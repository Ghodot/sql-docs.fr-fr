---
title: Configurer la destination du fichier plat (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 14e1742f83496b2976466d152cdd7aab39f76346
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289365"
---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>Configurer la destination du fichier plat (Assistant Importation et Exportation SQL Server)
  Utilisez le **configurer la Destination de fichier plat** page pour spécifier les options de mise en forme pour le fichier plat de destination et de prévisualiser les résultats avant de continuer.  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation SQL Server est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Fichier plat source**  
 Nom du fichier de destination.  
  
 **Séparateur de lignes**  
 Effectuez une sélection dans la liste des délimiteurs de lignes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|La ligne est délimitée par une combinaison retour chariot/saut de ligne.|  
|**{CR}**|La ligne est délimitée par un retour chariot.|  
|**{LF}**|La ligne est délimitée par un saut de ligne.|  
|**Point-virgule {;}**|La ligne est délimitée par un point-virgule.|  
|**Deux-points {:}**|La ligne est délimitée par un deux-points.|  
|**Virgule {,}**|La ligne est délimitée par une virgule.|  
|**Tabulation {t}**|La ligne est délimitée par une tabulation.|  
|**Barre verticale {&#124;}**|La ligne est délimitée par une barre verticale.|  
  
 **Délimiteur de colonne**  
 Effectuez une sélection dans la liste des délimiteurs de colonnes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les colonnes sont délimitées par une combinaison retour chariot/saut de ligne.|  
|**{CR}**|Les colonnes sont délimitées par un retour chariot.|  
|**{LF}**|Les colonnes sont délimitées par un saut de ligne.|  
|**Point-virgule {;}**|Les colonnes sont délimitées par un point-virgule.|  
|**Deux-points {:}**|Les colonnes sont délimitées par un deux-points.|  
|**Virgule {,}**|Les colonnes sont délimitées par une virgule.|  
|**Tabulation {t}**|Les colonnes sont délimitées par une tabulation.|  
|**Barre verticale {&#124;}**|Les colonnes sont délimitées par une barre verticale.|  
  
 **Aperçu**  
 Afficher dans le **aperçu des données** boîte de dialogue options de résultats de la mise en forme sélectionnée pour le fichier plat de destination.  
  
 **Modifier la transformation**  
 Supprimer des lignes, ajouter des lignes et configurer des colonnes dans le fichier de destination à l’aide de la **mappages de colonnes** boîte de dialogue.  
  
  
