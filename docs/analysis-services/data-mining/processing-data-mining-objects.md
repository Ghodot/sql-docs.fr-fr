---
title: "Traitement des objets d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "traitement des objets [Analysis Services]"
  - "structures d'exploration de données [Analysis Services]"
  - "traitement [Analysis Services]"
  - "structures d’exploration de données [Analysis Services], création"
  - "structures d'exploration de données [Analysis Services], rubriques de procédures"
  - "structures d’exploration de données [Analysis Services], traitement"
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
caps.latest.revision: 20
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 20
---
# Traitement des objets d&#39;exploration de donn&#233;es
  Un objet d'exploration de données n'est rien de plus qu'un conteneur vide tant qu'il n'est pas traité. Le *traitement* d’un modèle d’exploration de données est également appelé *apprentissage*.  
  
 **Traitement des structures d’exploration de données :** une structure d’exploration de données reçoit les données d’une source de données externe, comme défini par les liaisons de colonne et les métadonnées d’utilisation, puis elle les lit. Ces données sont lues entièrement, puis analysées pour extraire différentes statistiques. Analysis Services contient une représentation compacte des données, appropriée pour l'analyse par les algorithmes d'exploration de données, dans un cache local. Vous pouvez conserver ce cache ou le supprimer lorsque les modèles ont été traités. Par défaut, le cache est stocké. Pour plus d’informations, consultez [Traiter une structure d’exploration de données](../../analysis-services/data-mining/process-a-mining-structure.md).  
  
 **Traitement des modèles d’exploration de données :**un modèle d’exploration de données est vide (contenant uniquement des définitions) jusqu’à ce qu’il soit traité. Pour traiter un modèle d'exploration de données, la structure d'exploration de données doit avoir fait l'objet d'un traitement. Le modèle d'exploration de données reçoit les données du cache de la structure d'exploration de données, il applique tous les filtres qui ont pu être créés sur le modèle, puis transmet le jeu de données via l'algorithme pour détecter des motifs. Une fois le modèle traité, il stocke uniquement les résultats du traitement, et non les données. Pour plus d’informations, consultez [Traiter un modèle d’exploration de données](../../analysis-services/data-mining/process-a-mining-model.md).  
  
 Le diagramme suivant illustre le flux de données lors du traitement d'une structure d'exploration de données et d'un modèle d'exploration de données.  
  
 ![Traitement des données : de la source à la structure au modèle](../../analysis-services/data-mining/media/dmcon-modelarch.gif "Traitement des données : de la source à la structure au modèle")  
  
## Affichage des résultats du traitement  
 Lorsqu'une structure d'exploration de données a été traitée, elle contient une représentation compacte des données à utiliser dans l'analyse statistique. Si le cache n'a pas été effacé, il est possible d'accéder à ses données en utilisant l'une des méthodes suivantes :  
  
-   Création d'une requête Data Mining Extensions (DMX) sur le modèle et extraction dans la structure. Pour plus d’informations, consultez [SELECT FROM &#60;modèle&#62;.CASES &#40;DMX&#41;](../Topic/SELECT%20FROM%20%3Cmodel%3E.CASES%20\(DMX\).md).  
  
-   Navigation dans un modèle découlant de la structure et utilisation de l'une des options de l'interface utilisateur pour extraire des cas de structure. Pour plus d’informations, consultez [Visionneuses de modèle d’exploration de données](../../analysis-services/data-mining/data-mining-model-viewers.md) ou [Extraire des données de cas à partir d’un modèle d’exploration de données](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md).  
  
-   Création d'une requête DMX sur les cas de structure. Pour plus d’informations, consultez [SELECT FROM &#60;structure&#62;.CASES](../Topic/SELECT%20FROM%20%3Cstructure%3E.CASES.md).  
  
 Lorsqu'un modèle d'exploration de données a été traité, il contient uniquement les motifs découlant de l'analyse et les mappages des résultats du modèle vers les données d'apprentissage mises en cache. Vous pouvez parcourir ou interroger les résultats du modèle, appelés *contenu du modèle*, ou bien interroger le modèle et les cas de structure, s’ils ont été mis en cache.  
  
 Le contenu de chaque modèle d'exploration de données dépend de l'algorithme utilisé pour sa création. Par exemple, si un modèle est un modèle de clustering et si un autre est un modèle d'arbres de décision, le contenu de ces modèles sera très différent même s'ils utilisent exactement les mêmes données. Pour plus d’informations, consultez [Contenu du modèle d’exploration &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## Impératifs liés au traitement  
 Les impératifs liés au traitement peuvent être différents selon que vos modèles d'exploration de données sont basés uniquement sur les données relationnelles ou sur une source de données multidimensionnelles.  
  
 Pour la source de données relationnelles, le traitement requiert uniquement la création de données d'apprentissage et l'exécution d'algorithmes d'exploration sur ces données. Toutefois, les modèles d'exploration de données basés sur les objets OLAP, tels que les dimensions et les mesures, requièrent que les données sous-jacentes soient dans un état traité. Il peut être nécessaire que les objets multidimensionnels soient traités pour remplir le modèle d'exploration de données.  
  
 Pour plus d’informations, consultez [Exigences et considérations concernant le traitement &#40;exploration de données&#41;](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## Voir aussi  
 [Requêtes d’extraction &#40;exploration de données&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)   
 [Architecture logique &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/logical-architecture-analysis-services-data-mining.md)  
  
  