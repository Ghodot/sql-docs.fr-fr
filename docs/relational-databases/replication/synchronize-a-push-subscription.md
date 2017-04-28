---
title: "Synchronize a Push Subscription | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "synchronization [SQL Server replication], push subscriptions"
  - "subscriptions [SQL Server replication], push"
  - "abonnements par envoi de données (push) [réplication SQL Server], synchronisation"
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Synchronize a Push Subscription
  Cette rubrique décrit comment synchroniser un abonnement envoyé dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md), ou Replication Management Objects (RMO).  
  
 **Dans cette rubrique**  
  
-   **Pour synchroniser un abonnement par émission de données (push) à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Agents de réplication](#ReplProg)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Les abonnements sont synchronisés par l'Agent de distribution (pour la réplication transactionnelle et d'instantané) ou l'Agent de fusion (pour la réplication de fusion). Les agents peuvent s'exécuter en continu, à la demande ou selon une planification. Pour plus d’informations sur la spécification des planifications de synchronisation, consultez [spécifier des planifications de synchronisation](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
 Synchronisez un abonnement à la demete à partir des dossiers **Publications locales** et **Abonnements locaux** dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et the **Tous les abonnements** du moniteur de réplication. Les abonnements aux publications Oracle ne peuvent pas être synchronisés à la demande à partir de l'Abonné. Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
#### Pour synchroniser un abonnement par envoi de données à la demande dans Management Studio (sur le serveur de publication)  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication pour laquelle vous souhaitez synchroniser des abonnements.  
  
4.  Cliquez sur l’abonnement que vous souhaitez synchroniser, puis cliquez sur **Afficher l’état de synchronisation**.  
  
5.  Dans la **Afficher l’état de synchronisation - \< abonné>: \< BasededonnéesAbonnement>** boîte de dialogue, cliquez sur **Démarrer**. Lorsque la synchronisation est terminée, le message **Synchronisation terminée** s'affiche.  
  
6.  Cliquez sur **Fermer**.  
  
#### Pour synchroniser un abonnement par envoi de données à la demande dans Management Studio (sur l'Abonné)  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez sur l’abonnement que vous souhaitez synchroniser, puis cliquez sur **Afficher l’état de synchronisation**.  
  
4.  Un message sur l'établissement d'une connexion avec le serveur de distribution s'affiche. Cliquez sur **OK**.  
  
5.  Dans la **Afficher l’état de synchronisation - \< abonné>: \< BasededonnéesAbonnement>** boîte de dialogue, cliquez sur **Démarrer**. Lorsque la synchronisation est terminée, le message **Synchronisation terminée** s'affiche.  
  
6.  Cliquez sur **Fermer**.  
  
#### Pour synchroniser un abonnement par envoi de données à la demande dans le moniteur de réplication  
  
1.  Dans le moniteur de réplication, développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
3.  Cliquez sur l’abonnement que vous souhaitez synchroniser, puis cliquez sur **Démarrer la synchronisation**.  
  
4.  Pour afficher la progression de la synchronisation, cliquez sur l’abonnement, puis cliquez sur **Afficher les détails**.  
  
##  <a name="ReplProg"></a> Utilisation des Agents de réplication  
 Les abonnements par envoi de données (push) peuvent être synchronisés par le biais de la programmation et à la demande en appelant le fichier exécutable de l'Agent de réplication approprié à partir de l'invite de commandes. Le fichier exécutable de l'Agent de réplication qui est appelé dépend du type de publication à laquelle l'abonnement par envoi de données (push) appartient.  
  
#### Pour démarrer l'Agent de distribution et synchroniser un abonnement par envoi de données (push) vers une publication transactionnelle  
  
1.  À partir de l'invite de commandes ou dans un fichier de commandes sur le serveur de distribution, exécutez **distrib.exe**. Spécifiez les arguments suivants sur la ligne de commande :  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     Si vous utilisez l'authentification SQL Server, vous devez également spécifier les arguments suivants :  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### Pour démarrer l'Agent de fusion et synchroniser un abonnement par envoi de données (push) vers une publication de fusion  
  
1.  À partir de l'invite de commandes ou dans un fichier de commandes sur le serveur de distribution, exécutez **replmerg.exe**. Spécifiez les arguments suivants sur la ligne de commande :  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Publication**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     Si vous utilisez l'authentification SQL Server, vous devez également spécifier les arguments suivants :  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="TsqlExample"></a> Exemples (Agents de réplication)  
 L'exemple suivant démarre l'Agent de distribution pour synchroniser un abonnement par envoi de données (push).  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4  
  
```  
  
 L'exemple suivant démarre l'Agent de fusion pour synchroniser un abonnement par envoi de données (push).  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez synchroniser des abonnements par envoi de données par programme à l'aide des objets RMO (Replication Management Objects) et gérer l'accès au code pour les fonctionnalités de l'Agent de réplication. Les classes que vous utilisez pour créer un abonnement par envoi de données dépendent du type de publication à laquelle l'abonnement appartient.  
  
> [!NOTE]  
>  Si vous voulez démarrer une synchronisation qui s'exécute de façon autonome sans affecter votre application, démarrez l'agent en mode asynchrone. Toutefois, si vous souhaitez contrôler la sortie de la synchronisation et recevoir les rappels de l'Agent pendant le processus de synchronisation (par exemple, pour afficher une barre de progression), vous devez démarrer l'Agent en mode synchrone. Pour des Abonnés [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] , vous devez démarrer l'agent en mode synchrone.  
  
#### Pour synchroniser un abonnement par envoi de données vers un instantané ou une publication transactionnelle  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransSubscription> classe et définissez les propriétés suivantes :  
  
    -   Nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Le nom de la publication à laquelle l’abonnement appartient pour <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Le nom de la base de données d’abonnement pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Le nom de l’abonné pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   La connexion créée à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode permettant d’obtenir les propriétés d’abonnement restants. Si cette méthode retourne **false**, vérifiez que l’abonnement existe.  
  
4.  Démarrez l'Agent de distribution sur le serveur de distribution selon l'une des manières suivantes :  
  
    -   Appelez le <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> méthode sur l’instance de <xref:Microsoft.SqlServer.Replication.TransSubscription> à l’étape 2. Cette méthode démarre l'Agent de distribution en mode asynchrone et votre application récupère immédiatement le contrôle pendant l'exécution du travail de l'agent. Vous ne pouvez pas appeler cette méthode si l’abonnement a été créé avec la valeur **false** pour <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.  
  
    -   Pour obtenir une instance de la <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> de classe à partir de la <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> propriété et appelez la <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> (méthode). Cette méthode démarre l'agent en mode synchrone, et le travail d'agent en cours d'exécution conserve le contrôle. Lors de l’exécution synchrone, vous pouvez gérer les <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> événements tandis que l’agent est en cours d’exécution.  
  
#### Pour synchroniser un abonnement par envoi de données vers une publication de fusion  
  
1.  Créer une connexion au serveur de distribution à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergeSubscription> puis définissez les propriétés suivantes :  
  
    -   Nom de la base de données de publication pour <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>.  
  
    -   Le nom de la publication à laquelle l’abonnement appartient pour <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>.  
  
    -   Le nom de la base de données d’abonnement pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>.  
  
    -   Le nom de l’abonné pour <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>.  
  
    -   La connexion créée à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode permettant d’obtenir les propriétés d’abonnement restants. Si cette méthode retourne **false**, vérifiez que l’abonnement existe.  
  
4.  Démarrez l'Agent de distribution sur le serveur de distribution selon l'une des manières suivantes :  
  
    -   Appelez le <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> méthode sur l’instance de <xref:Microsoft.SqlServer.Replication.MergeSubscription> à l’étape 2. Cette méthode démarre l'Agent de fusion en mode asynchrone et votre application récupère immédiatement le contrôle pendant l'exécution du travail de l'agent. Vous ne pouvez pas appeler cette méthode si l’abonnement a été créé avec la valeur **false** pour <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>.  
  
    -   Pour obtenir une instance de la <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> de classe à partir de la <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> propriété et appelez la <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> (méthode). Cette méthode démarre l'Agent de fusion en mode synchrone, et le travail d'agent en cours d'exécution conserve le contrôle. Pendant l’exécution synchrone, vous pouvez gérer les <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> événements tandis que l’agent est en cours d’exécution.  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple synchronise un abonnement par envoi de données vers une publication transactionnelle, dans laquelle l'Agent est démarré en mode asynchrone à l'aide du travail de l'Agent.  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 Cet exemple synchronise un abonnement par envoi de données vers une publication transactionnelle, dans laquelle l'Agent est démarré en mode synchrone.  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 Cet exemple synchronise un abonnement par envoi de données vers une publication de fusion, dans laquelle l'Agent est démarré en mode asynchrone à l'aide du travail de l'Agent.  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 Cet exemple synchronise un abonnement par envoi de données vers une publication de fusion, dans laquelle l'Agent est démarré en mode synchrone.  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## Voir aussi  
 [Concepts liés à Replication Management Objects](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Synchronisez les données](../../relational-databases/replication/synchronize-data.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  