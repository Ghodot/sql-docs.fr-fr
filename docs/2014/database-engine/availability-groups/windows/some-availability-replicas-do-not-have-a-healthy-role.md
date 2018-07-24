---
title: Certains réplicas de disponibilité n’ont pas un rôle sain | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3a335109387ffae960cc129d1d249731d5226a9e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188896"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a>Certains réplicas de disponibilité n'ont pas un rôle sain
    
## <a name="introduction"></a>Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État du rôle des réplicas de disponibilité|  
|**Problème**|Certains réplicas de disponibilité n'ont pas un rôle sain.|  
|**Catégorie**|**Avertissement**|  
|**Facette**|Groupe de disponibilité|  
  
## <a name="description"></a>Description  
 Cette stratégie détermine l'état de connexion de tous les réplicas de disponibilité et vérifie s'il existe des réplicas de disponibilité qui n'ont pas un rôle sain. La stratégie se trouve dans un état non sain lorsqu'un réplica de disponibilité n'est ni principal ni secondaire. Autrement, l'état de la stratégie est sain.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [Certains réplicas de disponibilité n’ont pas un rôle sain](http://go.microsoft.com/fwlink/p/?LinkId=220854) sur TechNet Wiki.  
  
## <a name="possible-causes"></a>Causes possibles  
 Dans ce groupe de disponibilité, au moins un réplica de disponibilité n'a pas de rôle principal ou secondaire pour le moment.  
  
## <a name="possible-solution"></a>Solution possible  
 Utilisez l'état de la stratégie de réplica de disponibilité pour rechercher le réplica de disponibilité dont le rôle n'est ni principal ni secondaire, puis résolvez le problème qui affecte le réplica de disponibilité.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  