---
title: "Paramètres du serveur de publication | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.publishersettings.f1
helpviewer_keywords:
- Publisher Settings dialog box
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8fcc0c12988b1daf5ffa6cfc7f45a5c2e2ff9d88
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="publisher-settings"></a>Paramètres du serveur de publication
  La boîte de dialogue **Paramètres du serveur de publication** permet de changer les paramètres des serveurs de publication ajoutés dans le volet de gauche du Moniteur de réplication.  
  
## <a name="options"></a>Options  
 **Connexion du serveur de publication**  
 Cliquez pour ouvrir la boîte de dialogue **Connexion du serveur de publication** qui permet d'afficher et de changer les propriétés de la connexion et les informations d'identification qu'utilise le Moniteur de réplication pour se connecter à un serveur de publication.  
  
 **Connexion au serveur de distribution**  
 Affiché uniquement si le serveur de publication utilise un serveur de distribution distant. Cliquez pour ouvrir la boîte de dialogue **Se connecter au serveur** qui permet d'afficher et de changer les propriétés de la connexion et les informations d'identification qu'utilise le Moniteur de réplication pour se connecter à un serveur de distribution distant.  
  
 **Se connecter automatiquement au démarrage du Moniteur de réplication**  
 Sélectionnez cette option pour permettre au Moniteur de réplication de se connecter automatiquement au serveur de distribution et d'extraire les informations d'état du serveur de publication sélectionné dans la grille située dans la partie supérieure de la boîte de dialogue. Si cette case à cocher est désactivée, vous devez vous connecter manuellement après le lancement du Moniteur de réplication : cliquez avec le bouton droit dans le volet de gauche du Moniteur de réplication et cliquez sur **Se connecter**.  
  
 **Actualiser automatiquement le statut de ce serveur de publication et de ses publications**  
 Sélectionnez cette option pour permettre au Moniteur de réplication d'actualiser l'état du serveur de publication sélectionné dans la grille située dans la partie supérieure de la boîte de dialogue. Si cette option est sélectionnée, le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état du serveur de publication et de ses publications. La fréquence d'interrogation est définie par l'option **Fréquence d'actualisation** . Pour plus d’informations sur l’actualisation du moniteur de réplication, consultez [Mise en cache, actualisation et performances du moniteur de réplication](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Fréquence d'actualisation**  
 Entrez une valeur (en secondes) pour définir la fréquence à laquelle le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état. Une valeur basse augmente la fréquence d'interrogation, ce qui peut affecter les performances du serveur de distribution si vous contrôlez un grand nombre de serveurs de publication. Il est recommandé de tester le système pour déterminer la valeur appropriée. L'option **Fréquence d'actualisation** est également utilisée si vous sélectionnez **Actualisation automatique** dans une fenêtre de détail du Moniteur de réplication.  
  
 **Afficher ce ou ces serveurs de publication dans le groupe suivant**  
 Sélectionnez un groupe de serveurs de publication dans la liste. Le serveur de publication se trouve dans ce groupe dans le volet de gauche. Les groupes permettent d'organiser les serveurs de publication et n'ont aucun impact sur le fonctionnement de la réplication.  
  
 **Nouveau groupe**  
 Cliquez pour créer un nouveau groupe de serveurs de publication. Un groupe de serveurs de publication permet d'organiser aisément les serveurs de publication dans le Moniteur de réplication. Les groupes n'affectent pas la réplication des données ni la relation entre les serveurs dans une topologie de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Moniteur de réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  