---
title: "Cr&#233;er des informations d&#39;identification - Authentification dans le stockage Azure | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2014"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.backuptourl.createcred.f1"
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Cr&#233;er des informations d&#39;identification - Authentification dans le stockage Azure
  Utilisez la boîte de dialogue **Sauvegarde sur un périphérique URL - Créer des informations d'identification** pour créer de nouvelles informations d'identification SQL.  
  
 Lorsque vous utilisez cette boîte de dialogue pour créer des informations d'identification, vous devez ajouter un certificat de gestion Windows Azure au magasin de certificats local, ou un profil de publication téléchargé sur votre ordinateur, pour valider l'abonnement et les informations d'identification du compte de stockage.  
  
 **Informations d'identification SQL**  
 Spécifiez le nom des informations d'identification SQL que vous souhaitez créer.  
  
## Informations d'identification Windows Azure  
 **Certificat de gestion**  
 Utilisez cette option pour spécifier un certificat dans le magasin de certificats local qui correspond au certificat de gestion Windows Azure. Pour plus d'informations sur le certificat de gestion Windows Azure, consultez [Créer et télécharger un certificat de gestion pour Windows Azure](http://go.microsoft.com/fwlink/?LinkId=320781).  
  
 **Abonnement**  
 Sélectionnez, entrez ou collez votre ID d'abonnement Windows Azure qui correspond au certificat de gestion dans le magasin de certificats local.  
  
 **Profil de publication**  
 Utilisez cette option si vous avez un profil de publication téléchargé sur votre ordinateur. Si vous utilisez cette option, l'ID d'abonnement et le certificat sont remplis automatiquement.  
  
> [!CAUTION]  
>  SQL Server prend actuellement en charge la version 2.0 du profil de publication. Pour télécharger la version prise en charge du profil de publication, consultez [Télécharger le profil de publication 2.0](http://go.microsoft.com/fwlink/?LinkId=396421).  
  
## Compte de stockage  
 Sélectionnez le compte de stockage que vous souhaitez utiliser pour stocker les fichiers de sauvegarde.  
  
  