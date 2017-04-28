---
title: "Exemple&#160;: restauration fragmentaire de quelques groupes de fichiers (mode de restauration compl&#232;te) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode de récupération complète [SQL Server], exemple RESTORE"
  - "restaurations fragmentaires [SQL Server], mode de récupération complète"
  - "séquences de restauration [SQL Server], fragmentaires"
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Exemple&#160;: restauration fragmentaire de quelques groupes de fichiers (mode de restauration compl&#232;te)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique concerne les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui relèvent du mode de récupération complète et qui contiennent plusieurs fichiers ou groupes de fichiers.  
  
 Une séquence de restauration fragmentaire restaure et récupère une base de données par étapes au niveau des groupes de fichiers, en commençant par le groupe de fichiers primaire et tous les groupes de fichiers secondaires en lecture-écriture.  
  
 Dans cet exemple, une base de données appelée `adb` qui utilise le mode de restauration complète, contient trois groupes de fichiers. Le groupe de fichiers `A` est en lecture-écriture, et les groupes de fichiers `B` et `C` sont en lecture seule. Au départ, tous les groupes de fichiers sont en ligne.  
  
 Le groupe de fichiers primaire et le groupe de fichiers `B` de la base de données `adb` semblent endommagés. Le groupe de fichiers primaire est relativement petit et peut être restauré rapidement. L'administrateur de la base de données décide de restaurer les groupes de fichiers à l'aide d'une séquence de restauration fragmentaire. D'abord, le groupe de fichiers primaire et les journaux des transactions consécutifs sont restaurés, puis la base de données est récupérée.  
  
 Les groupes de fichiers intacts `A` et `C` contiennent des données critiques. Ils seront donc récupérés ensuite pour les mettre en ligne le plus vite possible. Enfin le groupe de fichiers secondaire endommagé, `B`, est restauré et récupéré.  
  
## Séquences de restauration :  
  
> [!NOTE]  
>  La syntaxe pour une séquence de restauration en ligne est la même que pour une séquence de restauration hors connexion.  
  
1.  Effectuez une sauvegarde de la fin du journal pour la base de données `adb`. Cette étape est essentielle pour que les groupes de fichiers intacts `A` et `C` soient en phase avec le point de récupération de la base de données.  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  Restauration partielle du groupe de fichiers primaire.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     Le groupe de fichiers primaire est déjà en ligne. Les fichiers dans les groupes de fichiers `A`, `B` et `C` sont en attente de récupération et les groupes de fichiers sont hors connexion.  
  
3.  Restauration en ligne des groupes de fichiers `A` et `C`.  
  
     Étant donné que leurs données ne sont pas endommagées, ces groupes de fichiers n'ont pas besoin d'être restaurés à partir d'une sauvegarde, mais ils ont besoin d'être récupérés pour être mis en ligne.  
  
     L'administrateur de base de données récupère immédiatement `A` et `C`.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     À ce stade, le groupe de fichiers primaire et les groupes de fichiers `A` et `C` sont en ligne. Les fichiers du groupe de fichiers `B` restent en attente de récupération et le groupe de fichiers est déconnecté.  
  
4.  Restauration en ligne du groupe de fichiers `B`.  
  
     Les fichiers du groupe de fichiers `B` sont restaurés à n'importe quel moment ensuite.  
  
    > [!NOTE]  
    >  La sauvegarde du groupe de fichiers `B` a été effectuée après que le groupe de fichiers soit passé en lecture seule, ces fichiers n'ont donc pas besoin d'être restaurés par progression.  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     Tous les groupes de fichiers sont maintenant en ligne.  
  
## Autres exemples  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;Mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers uniquement &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;Mode de récupération simple&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture/écriture &#40;Mode de récupération complète&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Restauration en ligne &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Restaurations fragmentaires &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  