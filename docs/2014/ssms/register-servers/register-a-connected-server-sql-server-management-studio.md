---
title: Inscrire un serveur connecté (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f50b659c4b42a644dfd0510769bbfe7047c13595
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278195"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a>Inscrire un serveur connecté (SQL Server Management Studio)
  Cette rubrique explique comment inscrire des serveurs dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Lors de l'inscription du serveur, vous pouvez enregistrer les informations de connexion relatives aux serveurs auxquels vous accédez fréquemment. Un serveur peut être inscrit avant la connexion ou au moment de la connexion depuis l'Explorateur d'objets.  
  
 **Dans cette rubrique**  
  
-   **Pour inscrire un serveur, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-register-a-connected-server"></a>Pour inscrire un serveur connecté  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur auquel vous êtes déjà connecté, puis cliquez sur **Inscrire**.  
  
     **Nom du serveur**  
     Entrez le nom que vous souhaitez donner au serveur inscrit. L'inscription d'un serveur local ou distant à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] vous permet de stocker les informations relatives à la connexion au serveur pour des connexions futures. La valeur par défaut de ce champ est le nom du serveur entré lors de la connexion à celui-ci. Vous pouvez conserver ce nom ou entrer un autre nom plus convivial.  
  
     **Description du serveur**  
     Entrez une description facultative du serveur. Le nombre maximal de caractères autorisé est 250.  
  
     **Sélectionnez un groupe de serveurs**  
     Sélectionnez le groupe de serveurs dans lequel vous souhaitez enregistrer l'inscription du serveur.  
  
     **Nouveau groupe**  
     Cliquez sur cette option pour ouvrir la boîte de dialogue **Nouveau groupe** et créer un nouveau groupe de serveurs pour le serveur inscrit.  
  
     **Enregistrer**  
     Cliquez sur ce bouton pour enregistrer les informations entrées et créer un serveur inscrit.  
  
  
