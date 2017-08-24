---
title: "&lt;requête de source de données&gt; | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- data sources [DMX]
- predictions [DMX]
- source data query element
- queries [DMX], source data
- external data access [DMX]
- <source data query> element
- training mining models
ms.assetid: 9dce5e37-1354-4d28-87c2-f9c419cb5b09
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 195c2ecd04a28ad830aca2d90df821b76d46e98e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt"></a>&lt;requête de source de données&gt;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Pour former un modèle d’exploration de données et créer des prédictions à partir d’un modèle d’exploration de données, vous devez accéder aux données qui sont externes à la [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. Vous utilisez la \<requête de source de données > clause dans les Extensions DMX (Data Mining) pour définir ces données externes. Le [INSERT INTO &#40; DMX &#41;](../dmx/insert-into-dmx.md), [SELECT FROM &#60; modèle &#62; JOINTURE de prédiction &#40; DMX &#41; ](../dmx/select-from-model-prediction-join-dmx.md), et [SELECT FROM NATURAL PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) toutes les instructions utilisent  **\<requête de source de données >**.  
  
## <a name="query-types"></a>Types de requêtes  
 Les trois méthodes les plus courantes pour spécifier les données source sont :  
  
 [OPENQUERY &#40; DMX &#41;](../dmx/source-data-query-openquery.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 Alors que **OPENQUERY** est similaire dans la fonction à **OPENROWSET**, **OPENQUERY** présente les avantages suivants :  
  
-   Une requête DMX est beaucoup plus facile à écrire avec **OPENQUERY**. Au lieu de créer une nouvelle chaîne de connexion à chaque fois que vous écrivez une requête, vous pouvez bénéficier de la chaîne de connexion existante dans la source de données. L'objet de source de données peut également contrôler l'accès aux données pour les utilisateurs individuels.  
  
-   L'administrateur a davantage de contrôle sur le mode d'accès aux données sur le serveur. Par exemple, il peut déterminer les fournisseurs à charger dans le serveur et les données externes accessibles.  
  
 [OPENROWSET &#40; DMX &#41;](../dmx/source-data-query-openrowset.md)  
 Cette instruction interroge des données qui sont externes à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], en utilisant une source de données existante.  
  
 [FORME &#40; DMX &#41;](../dmx/source-data-query-shape.md)  
 Cette instruction interroge plusieurs sources de données pour créer une table imbriquée. À l’aide de **forme**, vous pouvez combiner des données provenant de plusieurs sources dans une table hiérarchique unique. Ceci vous permet de bénéficier de la capacité de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] d'imbriquer les tables en incorporant une table dans une autre.  
  
 Pour spécifier les données source, vous pouvez également utiliser les options suivantes :   
  
-   Une instruction DMX valide  
  
-   Une instruction MDX (Multidimensional Expressions) valide  
  
-   Une table qui retourne une procédure stockée  
  
-   Un ensemble de lignes XMLA (XML for Analysis)  
  
-   Un paramètre d'ensemble de lignes  
  
## <a name="see-also"></a>Voir aussi  
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Tables imbriquées &#40; Analysis Services - Exploration de données &#41;](../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)  
  
  
