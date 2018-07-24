---
title: (SSAS) sur la modélisation multidimensionnelle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 509df042-fdb3-4e2c-a6b8-86943ce1b0fc
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 078ed4d8a791aba089255c725ddbedaa313920ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171670"
---
# <a name="multidimensional-modeling-ssas"></a>Modélisation multidimensionnelle (SSAS)
  La solution multidimensionnelle Analysis Services utilise des structures de cube pour analyser les données d'entreprise entre plusieurs dimensions. Le mode multidimensionnel est le mode serveur par défaut d'Analysis Services. Il inclut une requête et un moteur de calcul pour les données OLAP, avec les modes de stockage MOLAP, ROLAP et HOLAP pour équilibrer les performances par des conditions de données évolutives. Le moteur OLAP d'Analysis Services est un serveur OLAP leader de l'industrie qui fonctionne parfaitement avec de nombreux outils BI. La plupart des déploiements Analysis Services sont installés comme des serveurs OLAP classiques.  
  
## <a name="benefits-of-using-multidimensional-solutions"></a>Avantages de l'utilisation des solutions multidimensionnelles  
 La raison première de générer un modèle multidimensionnel Analysis Services est d'accélérer les performances des requêtes ad hoc sur des données d'entreprise. Un modèle multidimensionnel est composé de cubes et de dimensions qui peuvent être annotés et étendus pour prendre en charge des constructions de requêtes complexes. Les développeurs BI créent des cubes pour accélérer les temps de réponse et fournir une seule source de données pour les rapports d'entreprise. Étant donné l'importance croissante des solutions décisionnelles à tous les niveaux d'une organisation, le fait d'avoir une seule source de données analytiques garantit que les anomalies sont limitées au minimum faute de pouvoir les éliminer entièrement.  
  
 Un autre avantage procuré par les bases de données multidimensionnelles Analysis Services est l'intégration avec les outils de création de rapports BI couramment utilisés tels qu'Excel, Reporting Services et PerformancePoint, ainsi que des application personnalisées et des solutions tierces.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Solutions de modèles multidimensionnels &#40;SSAS&#41;](multidimensional-model-solutions-ssas.md)  
  
 [Bases de données Model multidimensionnelles &#40;SSAS&#41;](multidimensional-model-databases-ssas.md)  
  
 [Traitement des objets de modèle multidimensionnel](processing-a-multidimensional-model-analysis-services.md)  
  
 [Rôles et autorisations &#40;Analysis Services&#41;](roles-and-permissions-analysis-services.md)  
  
 [Power View pour les modèles multidimensionnels](power-view-for-multidimensional-models.md)  
  
 [Gestion des assemblys de modèle multidimensionnel](multidimensional-model-assemblies-management.md)  
  
  