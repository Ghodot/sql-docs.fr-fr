---
title: Sqlerrorlogevent, classe | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
caps.latest.revision: 12
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 65c2eb3758524788d0c65645d3b5736c930d58ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204892"
---
# <a name="sqlerrorlogevent-class"></a>Classe SqlErrorLogEvent
  Fournit des propriétés pour l'affichage d'événements dans un fichier journal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a>Propriétés  
 La classe SQLErrorLogEvent définit les propriétés suivantes.  
  
|||  
|-|-|  
|FileName|Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Nom du fichier journal des erreurs.|  
|InstanceName|Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> Nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où le fichier journal réside.|  
|LogDate|Type de données : `datetime`<br /><br /> Type d'accès : Lecture seule<br /><br /> Qualificateurs : Clé<br /><br /> <br /><br /> Date et heure auxquelles l'événement a été enregistré dans le fichier journal.|  
|Message|Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Message d'événement.|  
|ProcessInfo|Type de données : `string`<br /><br /> Type d'accès : Lecture seule<br /><br /> <br /><br /> Informations sur l'ID du processus du serveur source (SPID) pour l'événement.|  
  
## <a name="remarks"></a>Notes  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Espace de noms|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant indique comment extraire des valeurs pour tous les événements enregistrés dans un fichier journal spécifié. Pour exécuter l’exemple, remplacez \< *nom_instance*> par le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple « Instance1 » et remplacez « Nom_fichier » par le nom de fichier du journal des erreurs, par exemple « ERRORLOG.1 ».  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a>Commentaires  
 Lorsque *InstanceName* ou *FileName* ne sont pas fournies dans l’instruction WQL, la requête retournera les informations pour l’instance par défaut et actuel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier journal. Par exemple, l’instruction WQL suivante retournera tous les événements du journal à partir du fichier journal actuel (ERRORLOG) sur l’instance par défaut (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Sécurité  
 Pour vous connecter à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier journal via WMI, vous devez disposer des autorisations suivantes sur les ordinateurs locaux et distants :  
  
-   Accès en lecture à la **Root\Microsoft\SqlServer\ComputerManagement10** espace de noms WMI. Par défaut, tout le monde dispose de l'accès en lecture via l'autorisation Activer le compte.  
  
-   Autorisation en lecture sur le dossier qui contient les journaux des erreurs. Par défaut, l’erreur journaux sont situés dans le chemin d’accès suivant (où \< *lecteur >* représente le lecteur où vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et \< *InstanceName*> est le nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) :  
  
     **\<Lecteur > : \Program Files\Microsoft SQL Server\MSSQL12** **.\< Nom_instance > \MSSQL\Log**  
  
 Si vous vous connectez via un pare-feu, vérifiez qu'une exception est définie dans le pare-feu pour WMI sur les ordinateurs cibles distants. Pour plus d’informations, consultez [connexion à WMI à distance avec Windows Vista](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Voir aussi  
 [Sqlerrorlogfile, classe](sqlerrorlogfile-class.md)   
 [Afficher les fichiers journaux hors connexion](../logs/view-offline-log-files.md)  
  
  
