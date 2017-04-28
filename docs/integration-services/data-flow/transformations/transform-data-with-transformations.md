---
title: "Transformer des donn&#233;es avec des transformations | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "flux de données [Integration Services], transformations"
  - "transformations [Integration Services], à propos des transformations"
  - "transformation de données [Integration Services]"
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Transformer des donn&#233;es avec des transformations
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] inclut trois types de composants de flux de données : les sources, les transformations et les destinations.  
  
 Le schéma suivant illustre un flux de données simple qui possède une source, deux transformations et une destination.  
  
 ![Flux de données](../../../integration-services/data-flow/transformations/media/mw-dts-08.gif "Flux de données")  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Les transformations procurent la fonctionnalité suivante :  
  
-   Fractionnement, copie et fusion d'ensembles de lignes et opérations de recherche.  
  
-   Mise à jour de valeurs de colonnes et création de colonnes en appliquant des transformations telles que la modification de minuscules en majuscules.  
  
-   Exécution d'opérations Business Intelligence telles que le nettoyage de données, l'exploration de texte et l'exécution de requêtes de prédictions d'exploration de données.  
  
-   Création d'ensembles de lignes constitués de valeurs agrégées ou triées, d'échantillons de données ou de données croisées dynamiques et non croisées dynamiques.  
  
-   Exécution de tâches telles que l'exportation et l'importation de données, l'apport d'informations d'audit et l'utilisation de dimensions à variation lente.  
  
 Pour plus d’informations, consultez [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md).  
  
 Vous pouvez également écrire des transformations personnalisées. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) et [Développement de types spécifiques de composants de flux de données](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).  
  
 Après avoir ajouté la transformation au concepteur de flux de données, mais avant de configurer la transformation, vous devez connecter la transformation au flux de données en connectant la sortie d'une autre transformation ou source du flux de données à l'entrée de cette transformation. Le connecteur entre ces deux composants de flux de données porte le nom de chemin d'accès. Pour plus d’informations sur la connexion des composants et l’utilisation des chemins d’accès, consultez [Connecter des composants avec des chemins d’accès](../Topic/Connect%20Components%20with%20Paths.md).  
  
### Pour ajouter une transformation à un flux de données  
  
-   [Ajouter ou supprimer un composant dans un flux de données](../../../integration-services/data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
### Pour connecter une transformation à un flux de données  
  
-   [Connecter des composants dans un flux de données](../../../integration-services/data-flow/connect-components-in-a-data-flow.md)  
  
### Pour définir les propriétés d'une transformation  
  
-   [Définir les propriétés d'un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## Voir aussi  
 [tâche de flux de données](../../../integration-services/control-flow/data-flow-task.md)   
 [Flux de données](../../../integration-services/data-flow/data-flow.md)   
 [Connecter des composants avec des chemins d'accès](../Topic/Connect%20Components%20with%20Paths.md)   
 [Gestion des erreurs dans les données](../../../integration-services/data-flow/error-handling-in-data.md)   
 [Flux de données](../../../integration-services/data-flow/data-flow.md)  
  
  