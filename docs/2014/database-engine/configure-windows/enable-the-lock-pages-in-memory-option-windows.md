---
title: Activer l’option Verrouiller les pages en mémoire (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 64b922b5181ddb5fdab24b232864671d60457a97
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200239"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>Activer l'option Verrouiller les pages en mémoire (Windows)
  Cette stratégie Windows détermine quels comptes peuvent utiliser un processus destiné à conserver les données en mémoire physique pour éviter leur pagination en mémoire virtuelle sur le disque.  
  
> [!NOTE]  
>  Le verrouillage des pages en mémoire permet d'optimiser les performances lorsque la pagination de la mémoire sur disque est prévue.  
  
 L'outil Stratégie de groupe de Windows (gpedit.msc) vous permet d'activer cette stratégie pour le compte utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous devez être administrateur système pour modifier cette stratégie.  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>Pour activer l'option Verrouiller les pages en mémoire  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**. Dans le **Open** , tapez `gpedit.msc`.  
  
2.  Sur la console **Éditeur de stratégie de groupe locale** , développez **Configuration ordinateur**, puis **Paramètres Windows**.  
  
3.  Développez **Paramètres de sécurité**, puis **Stratégies locales**.  
  
4.  Sélectionnez le dossier **Attribution des droits utilisateur** .  
  
     Les stratégies s'affichent dans le volet Détails.  
  
5.  Dans le volet, double-cliquez sur **Verrouiller les pages en mémoire**.  
  
6.  Dans la boîte de dialogue **Paramètre de sécurité locale – Verrouiller les pages en mémoire** , cliquez sur **Ajouter un utilisateur ou un groupe**.  
  
7.  Dans la boîte de dialogue **Sélectionner des utilisateurs, des comptes de service ou des groupes** , ajoutez un compte avec les privilèges nécessaires pour exécuter sqlservr.exe.  
  
8.  Fermez la session, puis rouvrez-la pour que cette modification prenne effet.  
  
## <a name="see-also"></a>Voir aussi  
 [server memory (options de configuration du serveur)](server-memory-server-configuration-options.md)  
  
  
