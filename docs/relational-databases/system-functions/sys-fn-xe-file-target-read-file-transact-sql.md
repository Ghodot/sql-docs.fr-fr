---
title: Sys.fn_xe_file_target_read_file (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_xe_file_target_read_file_TSQL
- fn_xe_file_target_read_file
- sys.fn_xe_file_target_read_file_TSQL
- sys.fn_xe_file_target_read_file
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], functions
- fn_xe_file_target_read_file function
- sys.fn_xe_file_target_read_file function
ms.assetid: cc0351ae-4882-4b67-b0d8-bd235d20c901
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 29a0eda47d510292d657bfdb7912a9fe8940b023
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43099617"
---
# <a name="sysfnxefiletargetreadfile-transact-sql"></a>sys.fn_xe_file_target_read_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Lit des fichiers créés par la cible de fichier asynchrone d'événements étendus. Au format XML, un événement par ligne est retourné.  
  
> [!WARNING]  
>  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] accepter les résultats de trace générés au format XEL et XEM. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Étendue des résultats de trace au format XEL prennent uniquement en charge les événements. Nous vous recommandons d'utiliser SQL Server Management Studio pour lire les résultats de trace au format XEL.    
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_xe_file_target_read_file ( path, mdpath, initial_file_name, initial_offset )  
```  
  
## <a name="arguments"></a>Arguments  
 *path*  
 Chemin d'accès aux fichiers à lire. *chemin d’accès* peut contenir des caractères génériques et inclure le nom d’un fichier. *chemin d’accès* est **nvarchar (260)**. Il n'y a pas de valeur par défaut. Dans le contexte de base de données SQL Azure, cette valeur est une URL HTTP dans un fichier dans le stockage Azure.
  
 *mdpath*  
 Le chemin d’accès au fichier de métadonnées qui correspond au fichier ou des fichiers spécifiés par le *chemin d’accès* argument. *mdpath* est **nvarchar (260)**. Il n'y a pas de valeur par défaut. À compter de SQL Server 2016, ce paramètre peut être fourni comme null.
  
> [!NOTE]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ne nécessite pas la *mdpath* paramètre. Toutefois, celui-ci est conservé pour la compatibilité descendante des fichiers journaux générés dans les versions antérieures de SQL Server.  
  
 *initial_file_name*  
 Le premier fichier à lire à partir de *chemin d’accès*. *initial_file_name* est **nvarchar (260)**. Il n'y a pas de valeur par défaut. Si **null** est spécifié comme argument de tous les fichiers trouvés dans *chemin d’accès* sont lus.  
  
> [!NOTE]  
>  *initial_file_name* et *initial_offset* sont des arguments appariés. Si vous spécifiez une valeur pour l'un des arguments, vous devez en spécifier une pour l'autre.  
  
 *initial_offset*  
 Utilisé pour spécifier le dernier décalage lu et ignorer tous les événements jusqu'au décalage (inclus). Commence l'énumération d'événements après le décalage spécifié. *initial_offset* est **bigint**. Si **null** est spécifié comme l’argument de l’intégralité du fichier est lues.  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|module_guid|**uniqueidentifier**|GUID du module d'événements. N'accepte pas la valeur NULL.|  
|package_guid|**uniqueidentifier**|GUID du package d'événement. N'accepte pas la valeur NULL.|  
|object_name|**nvarchar (256)**|Nom de l’événement. N'accepte pas la valeur NULL.|  
|event_data|**nvarchar(max)**|Contenu de l'événement, au format XML. N'accepte pas la valeur NULL.|  
|file_name|**nvarchar(260)**|Nom du fichier qui contient l'événement. N'accepte pas la valeur NULL.|  
|file_offset|**bigint**|Offset du bloc dans le fichier qui contient l'événement. N'accepte pas la valeur NULL.|  
|timestamp_utc|**datetime2**|**S’applique à** : [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br />La date et l’heure (fuseau horaire UTC) de l’événement. N'accepte pas la valeur NULL.|  

  
## <a name="remarks"></a>Notes  
 Lecture des résultats volumineux définit en exécutant **sys.fn_xe_file_target_read_file** dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] peut entraîner une erreur. Utilisez le **résultats dans un fichier** mode (**Ctrl + Maj + F**) pour exporter les grands jeux de résultats dans un fichier et de lire le fichier avec un autre outil à la place.  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-retrieving-data-from-file-targets"></a>A. Récupération des données de cibles de fichiers  
 L'exemple ci-dessous obtient toutes les lignes de tous les fichiers. Dans cet exemple, les cibles de fichiers et les métafichiers se trouvent dans le dossier de trace sur le lecteur C:\.  
  
```  
SELECT * FROM sys.fn_xe_file_target_read_file('C:\traces\*.xel', 'C:\traces\metafile.xem', null, null);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de gestion dynamique des Événements étendus](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Affichages catalogue des événements étendus &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
