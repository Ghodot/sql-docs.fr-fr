---
title: MSdistpublishers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0cf48f494c04bd57e1bf20930917e4f9a3d015b
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102677"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Le **MSdistpublishers** table contient une ligne pour chaque serveur de publication distant pris en charge par le serveur de distribution local. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du serveur de distribution du serveur de publication.|  
|**distribution_db**|**sysname**|Le nom de la base de données de distribution.|  
|**working_directory**|**nvarchar(255)**|Le nom du répertoire de travail utilisé pour stocker les fichiers de données et le schéma de la publication.|  
|**security_mode**|**Int**|Mode de sécurité implémenté sur le serveur de distribution :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.<br /><br /> **1** = l’authentification Windows.|  
|**connexion**|**sysname**|L’ID de connexion pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**password**|**nvarchar (524)**|Mot de passe (chiffré) pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Active**|**bit**|Indique si le serveur de distribution local est utilisé par le serveur de publication distant.|  
|**approuvé**|**bit**|Indique si le serveur de publication distant utilise le même mot de passe que le serveur de distribution local :<br /><br /> **0** = un mot de passe est requis sur le serveur de publication distant pour se connecter au serveur de distribution.<br /><br /> **1** = aucun mot de passe est nécessaire.|  
|**third_party**|**bit**|Spécifie si le serveur de publication est une installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation. **1** = source de données hétérogènes.|  
|**publisher_type**|**sysname**|Type du serveur de publication :<br /><br /> **MSSQLSERVER**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.<br /><br /> **ORACLE** = serveur de publication Oracle standard.<br /><br /> **ORACLE GATEWAY** = serveur de publication Oracle Gateway.|  
|**storage_connection_string**|**nvarchar(779)**|Valeur de chaîne de connexion de stockage de base de données SQL Azure.|  

  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
