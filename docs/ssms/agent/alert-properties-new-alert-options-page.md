---
title: "Propriétés de l’alerte - Nouvelle alerte (page Options) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 360fc93c7f1e8cf7194637b7f5cffb20cb772c3c
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="alert-properties---new-alert-options-page"></a>Propriétés de l’alerte - Nouvelle alerte (page Options)
Cette page vous permet d'afficher et de modifier les options des alertes de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Options  
**Courrier électronique**  
Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications par courrier électronique.  
  
**Récepteur de radiomessagerie**  
Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications de radiomessagerie.  
  
**Envoi réseau**  
Permet d'inclure le texte d'erreur de l'événement, le cas échéant, dans les notifications d'envoi réseau.  
  
**Message de notification supplémentaire à envoyer**  
Tapez tout texte supplémentaire à inclure dans les messages de notification.  
  
**Délai entre les réponses**  
Spécifiez un délai pour les occurrences répétées de l'événement. Certains événements peuvent se produire fréquemment au court d'une courte période de temps. Dans ce cas, vous voudrez peut-être savoir que l'événement s'est produit sans vouloir de réponse pour chaque événement. Utilisez cette option pour spécifier un délai d'attente. Avec un délai, une fois que l'alerte a répondu à un événement, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent attend jusqu'au délai spécifié avant de répondre de nouveau, que l'événement se produise ou non pendant ce délai d'attente.  
  
**Minutes**  
Spécifiez un délai en minutes. Pour répondre chaque fois qu'un événement se produit, spécifiez 0 minutes et 0 secondes.  
  
**Secondes**  
Spécifiez un délai en secondes. Pour répondre chaque fois qu'un événement se produit, spécifiez 0 minutes et 0 secondes.  
  
## <a name="see-also"></a>Voir aussi  
[Alertes](../../ssms/agent/alerts.md)  
  
