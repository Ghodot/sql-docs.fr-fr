---
title: Création des fichiers de connexion de serveur (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Creating Server Connection Files
- Sybase Console,Server Connection File Validation
ms.assetid: 35ef396f-9f98-429d-9fc5-4f413d08fb37
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c51bc4e86c14fa1f7f45818f8ca18f751c8cd892
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394473"
---
# <a name="creating-the-server-connection-files-sybasetosql"></a>Création des fichiers de connexion de serveur (SybaseToSQL)
Informations sur le serveur peuvent être spécifiées dans la section serveurs du fichier de script ou dans un fichier de connexion de serveur distinct. Le paramètre de ligne de commande pour le fichier de connexion de serveur est, `-c <serverconnectionfile>`. Si le même id de serveur est présent dans le fichier de script et le fichier de connexion de serveur, la définition du serveur dans le fichier de script est considéré comme.  
  
**Exemple :**  
  
```  
1.<!--Sample of server connection file commands -->  
  
<sybase name="<source-server-unique-name>">  
  
  <standard-mode>  
  
    <provider value="Ole DB Provider"/>  
  
    <server-name value="<server-name>"/>  
  
    <server-port value="<port>"/>  
  
    <user-id value="<password>"/>  
  
  </standard-mode>  
  
</sybase>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication>  
  
    <database value="<database-name>"/>  
  
    <server value="<server-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
    <encrypt value="<true/false>"/>  
  
    <trust-server-certificate value="<true/false>"/>  
  
  </sql-server-authentication >  
  
</sql-server>  
```  
  
```  
2.<!—Sample of server connection file commands-->  
<sybase name="<source-server-unique-name>">  
  
  <advanced-mode>  
  
    <connection-string value="User ID=<user-name>;Password=<password>;Provider=ASEOLEDB.1;Server=<server-name>;Port=<port>;OLE DB Services = -2;"/>  
  
  </advanced-mode >  
  
</sybase>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication >  
  
    <database value="<database-name>"/>  
  
    <server value="<server-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
  </sql-server-authentication >  
  
</sql-server>  
```  
  
## <a name="server-connection-file-validation"></a>Validation de fichier de connexion de serveur  
L’utilisateur peut valider facilement son fichier de connexion de serveur par rapport au fichier de définition de schéma **S2SSConsoleScriptServersSchema.xsd** disponibles dans le dossier « Schémas ».  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante de d’exploitation de la console est [l’exécution de la Console SSMA &#40;SybaseToSQL&#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de la console SSMA](executing-the-ssma-console-sybasetosql.md)  
  
