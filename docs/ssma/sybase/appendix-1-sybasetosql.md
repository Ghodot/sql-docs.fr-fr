---
title: Annexe - 1 (SybaseToSQL) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Appendix
ms.assetid: 6dcfd6d5-772c-4876-aa94-a7f43c4b9d59
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a6121c15131cc42ee064767cd5a25e428e0968cb
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="appendix---1-sybasetosql"></a>Annexe - 1 (SybaseToSQL)
Aperçu rapide des options de ligne de commande de Console de SSMA :  
  
|Sl. Non.|Commutateur|Requis ?|Argument de commutateur|Valeurs autorisées|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Oui|scriptfile|Nom de fichier XML valide.<br /><br />Fichier de Script de définition de la console.|  
|2|variable ou - v|Non|variablevaluefile|Nom de fichier XML valide.<br /><br />Si les variables sont utilisées dans le fichier de script, ce fichier doit être spécifié.|  
|3|-c/serverconnection|Non|serverconnectionfile|Nom de fichier XML valide.<br /><br />Ce fichier contient des informations de connexion de serveur.|  
|4|x-/ xmloutput|Non|xmloutputfile|Cette option indique la sortie de la console au format XML. Si cette option n’est pas spécifiée, la sortie par défaut est au format texte.<br /><br />Si xmloutputfile n’est pas spécifié, la sortie XML est dirigée dans STDOUT.<br /><br />Xmloutputfile est le nom du fichier dans lequel la sortie de console est écrite au format XML.|  
|5|-l/journal|Non|logfile|Nom de fichier valide.|  
|6|e/projectenvironment|Non|projectenvironmentfolder|Nom de dossier valide contenant les fichiers d’environnement de projet SSMA.|  
|7|-p/securepassword|Non|-une/add {< server_id > [,... n] &#124; toutes les} – c &#124; serverconnection < fichier de connexion serveur > [-v &#124; variable < variable-valeur-fichier >] [-o/remplacer]<br /><br />ou<br /><br />-une/add {< server_id > [,... n] &#124; toutes les} – s &#124; le script < fichier de script > [-v &#124; variable < variable-valeur-fichier >] [-o/remplacer]<br /><br />– r/supprimer {< server_id > [,... n] &#124; toutes les}<br /><br />-l/liste<br /><br />– e/exportation {< server-id > [,... n] &#124; toutes les} < chiffré-password - fichier ><br /><br />– i / importation {< server-id > [,... n] &#124; toutes les} < chiffré-mot de passe-fichier >|Si spécifié, cette option ne doit pas être combinée avec d’autres options.<br /><br />id du serveur : un ID unique est fournie pour un serveur {string}<br /><br />fichier de connexion de serveur : fichier de définition de serveur (serverconnectionfile ou scriptfile).<br /><br />fichier de valeurs de variable : il est un fichier de définition de la variable et utilisé dans le fichier de connexion de serveur.<br /><br />mot de passe chiffré – fichier : il est un fichier de mots de passe de serveur chiffré à l’aide d’une phrase secrète spécifiée par l’utilisateur.|  
|8|-?|Non|Non Applicable|Non Applicable|  
  
## <a name="see-also"></a>Voir aussi  
[L’exécution de la Console SSMA (Sybase)](http://msdn.microsoft.com/en-us/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
