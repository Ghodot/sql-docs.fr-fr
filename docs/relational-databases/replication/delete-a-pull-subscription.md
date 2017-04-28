---
title: "Supprimer un abonnement par extraction (pull) | Microsoft Docs"
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
  - "removing subscriptions"
  - "deleting subscriptions"
  - "pull subscriptions [SQL Server replication], deleting"
  - "abonnements [réplication SQL Server], par extraction de données (pull)"
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Supprimer un abonnement par extraction (pull)
  Cette rubrique explique comment supprimer un abonnement par extraction de données (pull) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Pour supprimer un abonnement par extraction de données (pull) à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Supprimer un abonnement par extraction de données du serveur de publication (à partir de la **Publications locales** dossier [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) ou sur l’abonné (à partir de la **abonnements locaux** dossier). La suppression d'un abonnement ne supprime pas les objets ou les données de ce dernier : ils doivent être supprimés manuellement.  
  
#### Pour supprimer un abonnement extrait sur le serveur de publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Développez la publication associée à l'abonnement à supprimer.  
  
4.  Cliquez sur l’abonnement, puis cliquez sur **Supprimer**.  
  
5.  Dans la boîte de dialogue de confirmation, indiquez si vous souhaitez vous connecter à l'Abonné pour supprimer les informations d'abonnement. Si vous désactivez la case à cocher **Se connecter à l'Abonné** , vous devez vous connecter ultérieurement à l'Abonné pour supprimer les informations.  
  
#### Pour supprimer un abonnement extrait sur l'Abonné  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez sur l’abonnement que vous souhaitez supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue de confirmation, indiquez si vous souhaitez vous connecter au serveur de publication pour supprimer les informations d'abonnement. Si vous désactivez la case à cocher **Se connecter au serveur de publication** , vous devez vous connecter ultérieurement au serveur de publication pour supprimer les informations.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les abonnements par extraction peuvent être supprimés par programme en utilisant des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'abonnement appartient.  
  
#### Pour supprimer un abonnement par extraction à une publication transactionnelle ou d'instantané  
  
1.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_droppullsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md). Spécifiez **@publication**, **@publisher**, et **@publisher_db**.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_dropsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md). Spécifiez **@publication** et **@subscriber**. Affectez la valeur **all** à **@article**. (Facultatif) Si le serveur de distribution n’est pas accessible, spécifiez la valeur **1** pour **@ignore_distributor** pour supprimer l’abonnement sans supprimer les objets connexes dans le distributeur.  
  
#### Pour supprimer un abonnement par extraction à une publication de fusion  
  
1.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_dropmergepullsubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md). Spécifiez **@publication**, **@publisher**, et **@publisher_db**.  
  
2.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_dropmergesubscription & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md). Spécifiez **@publication**, **@subscriber**, et **@subscriber_db**. Spécifiez une valeur de **extraction** pour **@subscription_type**. (Facultatif) Si le serveur de distribution n’est pas accessible, spécifiez la valeur **1** pour **@ignore_distributor** pour supprimer l’abonnement sans supprimer les objets connexes dans le distributeur.  
  
###  <a name="TsqlExample"></a> Exemples (Transact-SQL)  
 L'exemple suivant supprime un abonnement par extraction à une publication transactionnelle. Le premier lot est exécuté sur l'Abonné, le second sur le serveur de publication.  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_1.sql)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_2.sql)]  
  
 L'exemple suivant supprime un abonnement par extraction à une publication de fusion. Le premier lot est exécuté sur l'Abonné, le second sur le serveur de publication.  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_3.sql)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_4.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez supprimer par programme des abonnements par extraction à l'aide d'objets RMO (Replication Management Objects). Les classes RMO utilisées pour supprimer un abonnement par extraction dépendent du type de publication auquel l'abonnement par extraction est souscrit.  
  
#### Pour supprimer un abonnement par extraction à une publication transactionnelle ou d'instantané  
  
1.  Créer des connexions à l’abonné et le serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPullSubscription> puis définissez la <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, et <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Propriétés. Utilisez la connexion de l’abonné à l’étape 1 pour définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
3.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier l’existence de l’abonnement. Si la valeur de cette propriété est **false**, les propriétés de l'abonnement ont été définies de manière incorrecte à l'étape 2, ou l'article n'existe pas.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> méthode.  
  
5.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.TransPublication> classe à l’aide de la connexion du serveur de publication de l’étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, soit les propriétés spécifiées à l’étape 5 sont incorrectes, soit la publication n’existe pas sur le serveur.  
  
7.  Appelez le <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> (méthode). Spécifiez le nom de l'Abonné et la base de données d'abonnement pour les paramètres *subscriber* et *subscriberDB* .  
  
#### Pour supprimer un abonnement par extraction à une publication de fusion  
  
1.  Créer des connexions à l’abonné et le serveur de publication à l’aide de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePullSubscription> puis définissez la <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, et <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> Propriétés. Utilisez la connexion à l’étape 1 pour définir le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété.  
  
3.  Vérifier la <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> propriété pour vérifier l’existence de l’abonnement. Si la valeur de cette propriété est **false**, les propriétés de l'abonnement ont été définies de manière incorrecte à l'étape 2, ou l'article n'existe pas.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> méthode.  
  
5.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.MergePublication> classe à l’aide de la connexion du serveur de publication de l’étape 1. Spécifiez <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> et <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
6.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, soit les propriétés spécifiées à l’étape 5 sont incorrectes, soit la publication n’existe pas sur le serveur.  
  
7.  Appelez le <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> (méthode). Spécifiez le nom de l'Abonné et la base de données d'abonnement pour les paramètres *subscriber* et *subscriberDB* .  
  
###  <a name="PShellExample"></a> Exemples (RMO)  
 Cet exemple supprime un abonnement par extraction à une publication transactionnelle et supprime l'inscription de l'abonnement au niveau du serveur de publication.  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 Cet exemple supprime un abonnement par extraction à une publication de fusion et supprime l'inscription de l'abonnement au niveau du serveur de publication.  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## Voir aussi  
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  