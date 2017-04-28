---
title: "Le groupe de disponibilit&#233; n&#39;est pas pr&#234;t pour le basculement automatique | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.agp3autofailover.issues.f1"
helpviewer_keywords: 
  - "groupes de disponibilité [SQL Server], stratégies"
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# Le groupe de disponibilit&#233; n&#39;est pas pr&#234;t pour le basculement automatique
    
## Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|Disponibilité du groupe de disponibilité pour le basculement automatique|  
|**Problème**|Le groupe de disponibilité n'est pas prêt pour le basculement automatique.|  
|**Catégorie**|**Critique**|  
|**Facette**|Groupe de disponibilité|  
  
## Description  
 Cette stratégie vérifie que le groupe de disponibilité a au moins un réplica secondaire prêt pour le basculement. La stratégie se trouve dans un état non sain et une alerte est déclenchée lorsque le mode de basculement du réplica principal est automatique, mais qu'aucun des réplicas secondaires dans le groupe de disponibilité n'est prêt pour le basculement.  
  
 La stratégie se trouve dans un état sain lorsqu'au moins un réplica secondaire est prêt pour le basculement automatique.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles figurent sous [Le groupe de disponibilité n’est pas prêt pour le basculement automatique](http://go.microsoft.com/fwlink/p/?LinkId=220851) sur le Wiki TechNet.  
  
## Causes possibles  
 Le groupe de disponibilité n'est pas prêt pour le basculement automatique. Le réplica principal est configuré pour le basculement automatique ; toutefois, le réplica secondaire n'est pas prêt pour le basculement automatique. Le réplica secondaire configuré pour le basculement automatique est peut-être indisponible ou son état de synchronisation des données n'est pas SYNCHRONIZED pour le moment.  
  
## Solutions possibles  
 Voici les solutions possibles à ce problème :  
  
-   Vérifiez qu'au moins un réplica secondaire est configuré pour le basculement automatique. Si aucun réplica secondaire n'est configuré pour le basculement automatique, mettez à jour la configuration d'un réplica secondaire de sorte qu'il soit la cible de basculement automatique avec validation synchrone.  
  
-   Utilisez la stratégie pour vérifier que les données sont dans un état de synchronisation et que la cible de basculement automatique est à l'état SYNCHRONIZED, puis pour résoudre le problème qui affecte le réplica de disponibilité.  
  
## Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  