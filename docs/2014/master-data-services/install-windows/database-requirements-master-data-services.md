---
title: Configuration requise pour la base de données (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
caps.latest.revision: 13
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8ae9989f2ca04e0d0beb2d246fbea4d47fcf3a6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193395"
---
# <a name="database-requirements-master-data-services"></a>Configuration requise pour la base de données (Master Data Services)
  Toutes les données de référence sont stockées dans une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . L’ordinateur qui héberge cette base de données doit exécuter une instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Utilisez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour créer et configurer la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] sur un ordinateur local ou distant. Si vous déplacez la base de données d'un environnement à un autre, vous pouvez maintenir ces informations dans un nouvel environnement en associant le service Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à la base de données dans son nouvel emplacement.  
  
> [!NOTE]  
>  Tout ordinateur sur lequel vous installez les composants de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] doit disposer d'une licence. Pour plus d'informations, reportez-vous au Contrat de Licence Utilisateur Final (CLUF).  
  
## <a name="requirements"></a>Spécifications  
 Avant de créer une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , assurez -vous que les conditions suivantes sont remplies.  
  
### <a name="sql-server-edition"></a>Édition SQL Server  
 La base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] peut être hébergée sur les éditions suivantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence (64 bits) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Entreprise (64 bits) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer (64 bits) x64  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence (64 bits) x64  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Entreprise (64 bits) x64 – Mise à niveau de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Entreprise uniquement  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer (64 bits) x64  
  
-   Microsoft SQL Server 2008 R2 Enterprise (64 bits) x64  
  
-   Microsoft SQL Server 2008 R2 Developer x64 (64 bits)  
  
 Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
### <a name="operating-system"></a>Système d'exploitation  
 Pour plus d’informations sur les systèmes d’exploitation Windows pris en charge et autres exigences pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultez [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="accounts-and-permissions"></a>Comptes et autorisations  
  
|Type|Description|  
|----------|-----------------|  
|Compte d'utilisateur|Dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], vous pouvez utiliser un compte Windows ou un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vous connecter à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d’héberger la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Le compte d’utilisateur doit appartenir au rôle serveur **sysadmin** sur l’instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Pour plus d’informations sur le rôle **sysadmin** , consultez [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md).|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Compte administrateur|Lorsque vous créez une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , vous devez spécifier un compte d'utilisateur de domaine pour être l'administrateur système [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Pour toutes les applications Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] associées à cette base de données, cet utilisateur peut mettre à jour tous les modèles et toutes les données dans toutes les zones fonctionnelles. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).|  
  
### <a name="database-backup"></a>Sauvegarde de la base de données  
 À titre de recommandation, sauvegardez la base de données complète quotidiennement en période de faible activité et sauvegardez les journaux des transactions plus fréquemment selon les besoins de votre environnement. Pour plus d’informations sur les sauvegardes de bases de données, consultez [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Master Data Services](install-master-data-services.md)   
 [Créer une base de données Master Data Services](create-a-master-data-services-database.md)   
 [Base de données Master Data Services](../master-data-services-database.md)   
 [Boîte de dialogue Connexion à une base de données Master Data Services](../connect-to-a-master-data-services-database-dialog-box.md)   
 [Assistant Création d’une base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  
