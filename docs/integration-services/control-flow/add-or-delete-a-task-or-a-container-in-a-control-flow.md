---
title: "Ajouter ou supprimer une t&#226;che ou un conteneur dans un flux de contr&#244;le | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conteneurs [Integration Services], ajout"
  - "ajout de tâches"
  - "ajout de conteneurs"
  - "tâches [Integration Services], ajout"
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Ajouter ou supprimer une t&#226;che ou un conteneur dans un flux de contr&#244;le
  Quand vous travaillez dans le concepteur de flux de contrôle, la boîte à outils du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] énumère les tâches proposées par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour créer le flux de contrôle d’un package. Pour plus d’informations sur la boîte à outils, consultez [Boîte à outils SSIS](../../integration-services/ssis-toolbox.md).  
  
 Un package peut inclure plusieurs instances de la même tâche. Chaque instance d'une tâche est identifiée de manière unique dans le package et vous pouvez configurer chaque instance différemment.  
  
 Si vous supprimez une tâche, les contraintes de précédence connectant la tâche à d'autres tâches et les conteneurs du flux de contrôle sont également supprimés.  
  
 Les procédures ci-dessous décrivent comment ajouter ou supprimer une tâche ou un conteneur dans le flux de contrôle d'un package.  
  
### Pour ajouter une tâche ou un conteneur à un flux de contrôle  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Pour ouvrir la **boîte à outils**, cliquez sur **Boîte à outils** dans le menu **Affichage**.  
  
5.  Développez **Éléments de flux de contrôle** et **Tâches du plan de maintenance**.  
  
6.  Faites glisser des tâches et des conteneurs de la **boîte à outils** vers l’aire de conception de l’onglet **Flux de contrôle**.  
  
7.  Connectez une tâche ou un conteneur du flux de contrôle du package à un autre composant du flux de contrôle en faisant glisser son connecteur vers cet autre composant.  
  
8.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### Pour supprimer une tâche ou un conteneur d'un flux de contrôle  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir. Procédez de l’une des manières suivantes :  
  
    -   Cliquez sur l’onglet **Flux de contrôle**, cliquez avec le bouton droit sur la tâche ou le conteneur à supprimer, puis cliquez sur **Supprimer**.  
  
    -   Ouvrez **Explorateur de package**. Dans le dossier **Exécutables**, cliquez avec le bouton droit sur la tâche ou le conteneur à supprimer, puis cliquez sur **Supprimer**.  
  
3.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## Voir aussi  
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Conteneurs Integration Services](../../integration-services/control-flow/integration-services-containers.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)  
  
  