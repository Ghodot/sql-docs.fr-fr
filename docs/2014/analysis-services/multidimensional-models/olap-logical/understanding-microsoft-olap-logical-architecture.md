---
title: Architecture logique (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7813bd9d7e5bb0fec74bbf9249755355765c3fd9
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395114"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>Architecture logique (Analysis Services - Données multidimensionnelles)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilise des composants serveur et client pour fournir un traitement analytique en ligne (OLAP) et les fonctionnalités d’exploration de données pour les applications décisionnelles :  
  
-   Le composant serveur d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est implémenté comme un service Microsoft Windows. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge plusieurs instances sur le même ordinateur, chaque instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implémentée comme une instance distincte du service Windows.  
  
-   Les clients communiquent avec [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] à l’aide de la norme publique XMLA (XML for Analysis), un protocole SOAP qui permet d’émettre des commandes et de recevoir des réponses, exposée en tant que service web. Des modèles objet clients sont aussi fournis via XMLA, et sont accessibles soit à l'aide d'un fournisseur managé, notamment ADOMD.NET ou un fournisseur OLE DB natif.  
  
-   Les commandes de requête peuvent être émises à l'aide des langages suivants : SQL, MDX (Multidimensional Expressions), un langage de requête standard orienté analyse ou DMX (Data Mining Extensions), un langage de requête standard orienté exploration de données. Vous pouvez aussi utiliser ASSL (Analysis Services Scripting Language) pour gérer les objets de la base de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend également en charge un moteur de cube local qui permet aux applications exécutées sur des clients déconnectés de parcourir les données multidimensionnelles stockées localement. Pour plus d’informations, consultez [Architecture de Client requise pour le développement Analysis Services](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>Dans cette section  
 **Vue d’ensemble de l’architecture logique**  
 [Vue d’ensemble de l’Architecture logique &#40;Analysis Services - données multidimensionnelles&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Objets de serveur**  
 [Objets serveur &#40;Analysis Services - données multidimensionnelles&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de base de données**  
 [Objets de base de données &#40;Analysis Services - données multidimensionnelles&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de dimension**  
 [Objets de dimension &#40;Analysis Services - données multidimensionnelles&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Objets de cube**  
 [Objets de cube &#40;Analysis Services - données multidimensionnelles&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Sécurité d’accès utilisateur**  
 [Architecture de sécurité d’accès utilisateur](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’Architecture Microsoft OLAP](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [Architecture physique &#40;Analysis Services - données multidimensionnelles&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
