---
title: Mettre en correspondance les données similaires (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 5bc369f74b77db20a9f7766f8bce0bc93e510bc7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242859"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>Mettre en correspondance les données similaires (Complément MDS pour Excel)
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], utilisez la fonctionnalité Data Quality Services (DQS) pour rechercher des similitudes dans vos données.  
  
 Pour effectuer cette procédure, vous pouvez :  
  
-   Utiliser la base de connaissances Data Quality Services par défaut, ou  
  
-   Créer votre propre base de connaissances DQS personnalisée et la stratégie correspondante. Pour plus d’informations, consultez [Créer une stratégie de correspondance](../../data-quality-services/create-a-matching-policy.md).  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Vous devez disposer d'une feuille de calcul qui contient des données gérées par MDS. Pour plus d’informations, consultez [charger des données à partir de MDS dans Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Facultatif. Vous pouvez combiner d'autres données avec les données gérées par MDS avant de rechercher des similitudes. Pour plus d’informations, consultez [Combiner des données &#40;Complément MDS pour Excel&#41;](combine-data-mds-add-in-for-excel.md).  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a>Pour rechercher des similitudes à l'aide de la base de connaissances par défaut  
  
1.  Dans la feuille de calcul qui contient des données gérées par MDS, dans le groupe **Qualité des données** , cliquez sur **Faire correspondre les données**.  
  
2.  Dans la boîte de dialogue **Faire correspondre les données** , dans la liste **Base de connaissances DQS** , sélectionnez **Données DQS (par défaut)**.  
  
3.  Pour chaque colonne contenant des données que vous souhaitez mettre en correspondance, ajoutez une ligne dans la boîte de dialogue. Pour plus d’informations sur les champs de cette boîte de dialogue, consultez [Comment définir des paramètres de règle de correspondance](../../data-quality-services/create-a-matching-policy.md#MatchingRules).  
  
4.  Lorsque le total de toutes les valeurs de pondération est égal à 100 pour cent, cliquez sur **OK**.  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a>Pour rechercher des similitudes à l'aide d'une base de connaissances personnalisée  
  
1.  Dans la feuille de calcul qui contient des données gérées par MDS, dans le groupe **Qualité des données** , cliquez sur **Faire correspondre les données**.  
  
2.  Dans la liste **Base de connaissances DQS** , sélectionnez le nom de votre base de connaissances personnalisée.  
  
3.  Pour chaque colonne de la feuille de calcul, sélectionnez un domaine DQS.  
  
4.  Lorsque tous les domaines DQS sont mappés aux colonnes de la feuille de calcul, cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Affichez les informations supplémentaires pour déterminer les données similaires. Pour plus d’informations, consultez [Colonnes de mise en correspondance de la qualité des données &#40;Complément MDS pour Excel&#41;](data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Qualité des données correspondantes dans le complément MDS pour Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Correspondance de données](../../data-quality-services/data-matching.md)  
  
  