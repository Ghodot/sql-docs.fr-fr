---
title: "Démarrer et arrêter un Agent de réplication (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6af13f3427ae5787e1c1e4872c8f75f247e8c6b1
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a>Démarrer et arrêter un Agent de réplication (SQL Server Management Studio)
  Démarrez et arrêtez les Agents à partir des dossiers **Travaux** et **Réplication** de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from Réplication Monitor. Démarrez et arrêtez les Agents et les travaux suivants :  
  
-   Agent d'instantané, utilisé par toutes les publications  
  
-   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
-   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
-   Agent de distribution, qui synchronise les abonnements aux publications transactionnelles et d'instantané  
  
-   Agent de fusion, qui synchronise les abonnements aux publications de fusion  
  
-   Travaux de maintenance de la réplication  
  
 Pour plus d’informations sur le démarrage de l’Agent de fusion et de l’Agent de Distribution, consultez [Synchroniser un abonnement par émission de données](../../../relational-databases/replication/synchronize-a-push-subscription.md) et [Synchroniser un abonnement par extraction](../../../relational-databases/replication/synchronize-a-pull-subscription.md). Pour plus d’informations sur les travaux de maintenance, consultez [Exécuter des travaux de maintenance de réplication &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a>Pour démarrer et arrêter un Agent d'instantané ou un Agent de lecture du journal à partir de Management Studio  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]puis développez le nœud du serveur et le dossier **Réplication** .  
  
2.  Développez le dossier **Publications locales** , puis cliquez avec le bouton droit sur une publication.  
  
3.  Cliquez sur **Afficher l'état de l'Agent d'instantané** ou **Afficher l'état de l'Agent de lecture du journal**.  
  
4.  Cliquez sur **Démarrer** ou sur **Arrêter**.  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a>Pour démarrer et arrêter un Agent de lecture de file d'attente à partir de Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez avec le bouton droit sur le travail de l'agent puis cliquez sur **Démarrer le travail** ou **Arrêter le travail**. Le nom du travail de l’Agent de lecture de la file d’attente se présente sous la forme **[\<Serveur de distribution>].\<entier>**.  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a>Pour démarrer et arrêter un Agent d'instantané, un Agent de lecture du journal ou un Agent de lecture de file d'attente dans le moniteur de réplication  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez avec le bouton droit sur un Agent puis cliquez sur **Démarrer l'Agent** ou **Arrêter l'Agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Concepts des exécutables de l’agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Présentation des Agents de réplication](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  