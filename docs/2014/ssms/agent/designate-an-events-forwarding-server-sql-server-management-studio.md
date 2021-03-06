---
title: Désigner un serveur (SQL Server Management Studio) de transfert d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 36b795f0f4ecb1c594073a98da7dfc03bf5bed3c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220769"
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Designate an Events Forwarding Server (SQL Server Management Studio)
  Cette rubrique explique comment désigner un serveur auquel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transfère les événements dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Notez que le transfert d'événements s'applique aux événements transférés entre serveurs, et non aux événements transférés entre instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hébergées sur un même ordinateur. Notez également qu'afin de recevoir les événements transférés, le serveur de gestion des alertes doit être une instance par défaut de SQL Server.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour désigner un serveur de transfert d'événements, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-designate-an-events-forwarding-server"></a>Pour désigner un serveur de transfert d'événements  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur depuis lequel vous souhaitez transférer des événements vers un autre serveur.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de SQL Server Agent –***nom_serveur*, sous **Sélectionner une page**, sélectionnez **Avancé**.  
  
4.  Sous **Transfert d'événements SQL Server**, sélectionnez la case à cocher **Transférer les événements sur un autre serveur** .  
  
5.  Dans la liste **Serveur** , sélectionnez un serveur, puis, sous **Événements**, sélectionnez l'une des options suivantes :  
  
    -   Sélectionnez **Événements non gérés** pour ne transmettre que les événements qui n'ont pas été gérés par des alertes locales.  
  
    -   Sélectionnez **Tous les événements** pour transférer tous les événements, indépendamment de leur gestion par des alertes locales ou non.  
  
6.  Dans la liste **Si l'événement a une gravité au moins égale à** , cliquez sur le niveau de gravité auquel les événements sont transférés au serveur sélectionné.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
