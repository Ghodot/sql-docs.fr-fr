---
title: "Applet de commande Restore-ASDatabase | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8ab7a2d0-679c-40e6-b9b9-042184b2dfc9
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Applet de commande Restore-ASDatabase
  Restaure une base de données multidimensionnelle ou tabulaire à partir d’un fichier de sauvegarde (.abf) vers une instance Analysis Services.  
  
## Syntaxe  
 `Restore-ASDatabase [-RestoreFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] Locations <Microsoft.AnalysisServices.RestoreLocation[]>] [-Security <Microsoft.AnalysisServices.RestoreSecurity>] [-Password <System.SecureString>] [-StorageLocation <System.string>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Permet à un administrateur système Analysis Services de restaurer une base de données multidimensionnelle ou tabulaire à partir d’un fichier de sauvegarde (.abf) vers une instance de serveur locale ou distante. Si le fichier que vous restaurez a été chiffré, utilisez –FilePassword ou –Credential pour fournir le mot de passe utilisé pour déchiffrer le fichier.  
  
 Cette applet de commande prend en charge le paramètre –Credential, qui peut être utilisé si vous avez configuré l'instance Analysis Services pour l'accès HTTP. Le paramètre –Credential accepte un objet PSCredential qui fournit une identité d'utilisateur Windows. IIS emprunte l'identité de cet utilisateur lors de la connexion à Analysis Services. L'identité doit avoir des autorisations d'administrateur système sur l'instance Analysis Services pour restaurer le fichier.  
  
## Paramètres  
  
### -RestoreFile \<string>  
 Spécifie le chemin d'accès et le nom du fichier à restaurer. Si vous spécifiez simplement le nom de fichier sans un chemin d'accès, l'emplacement de sauvegarde par défaut est utilisé.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Name \<string>  
 Spécifie la base de données Analysis Services à restaurer.  
  
|||  
|-|-|  
|Requis ?|true|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -AllowOverwrite \<SwitchParameter>  
 Remplace une base de données qui utilise les mêmes nom et emplacement.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Locations \<Microsoft.AnalysisServices.RestoreLocation[]>  
 Spécifie l'emplacement distant des partitions à restaurer.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Security \<Microsoft.AnalysisServices.RestoreSecurity>  
 Représente les paramètres de sécurité utilisés pour l'opération de restauration. Les valeurs valides sont CopyAll, SkipMembership, IgnoreSecurity. CopyAll restaure les rôles et l'appartenance. SkipMembership recrée simplement le rôle. IgnoreSecurity restaure la base de données, sans les rôles.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Password \<SecureString>  
 Spécifie un mot de passe à utiliser pour restaurer un fichier de sauvegarde chiffré. Vous devez spécifier le mot de passe utilisé à l'origine pour chiffrer le fichier.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -StorageLocation \<string>  
 Spécifie l'emplacement de stockage de base de données. Il s'agit de l'emplacement des fichiers de base de données sur le système de fichiers. Définissez ce paramètre si vous n'utilisez pas l'emplacement par défaut, qui est le dossier de sauvegarde de l'instance cible.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Server \<string>  
 Spécifie l'instance Analysis Services à laquelle l'applet de commande se connectera et qu'il exécutera. Si aucun nom de serveur n'est fourni, une connexion sera établie à localhost. Pour les instances par défaut, spécifiez simplement le nom du serveur. Pour les instances nommées, utilisez le format nom_serveur\nom_instance. Pour les connexions HTTP, utilisez le format http[s]://serveur[:port]/répertoirevirtuel/msmdpump.dll.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut|localhost|  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Credential \<PSCredential>  
 Spécifie un objet PSCredential qui fournit un nom et un mot de passe d'utilisateur Windows. Spécifiez ce paramètre uniquement si l'instance Analysis Services est configurée pour l'accès HTTP, à l'aide de l'authentification de base. Pour les connexions natives utilisant la sécurité intégrée, ce paramètre est ignoré.  
  
 Si ce paramètre est présent, les informations d'identification qu'il fournit sont ajoutées à la chaîne de connexion. IIS emprunte l'identité de cet utilisateur lors de la connexion à Analysis Services. Si aucune information d'identification n'est indiquée, le compte Windows par défaut de l'utilisateur qui exécute l'outil sera utilisé.  
  
 Pour utiliser ce paramètre, créez d’abord un objet PSCredential à l’aide de Get-Credential pour spécifier le nom d’utilisateur et le mot de passe, par exemple, `$Cred=Get-Credential “adventure-works\admin”`). Vous pouvez ensuite canaliser cet objet vers le paramètre –Credential `(-Credential:$Cred`).  
  
 Pour plus d’informations sur l’authentification et l’utilisation des informations d’identification, consultez [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md) (Scripts PowerShell dans Analysis Services). Pour plus d’informations sur l’accès HTTP, consultez [Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md).  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|True (ByValue)|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 La commande cmdlet prend en charge les paramètres communs : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|System.string<br /><br /> Vous pouvez canaliser les valeurs de chaîne vers l'applet de commande.|  
|Sorties|Aucun.|  
  
## Exemple 1  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase awtest.abf testawrestoredb –security:CopyAll  
```  
  
 Cette commande restaure un fichier de sauvegarde Analysis Services (awtest.abf) dans le dossier de sauvegarde local sur une instance par défaut Analysis Services locale. Il n'est pas nécessaire que le nom de la base de données existe ; dans ce cas, le nom de la base de données est spécifié dans le cadre de l'opération de restauration. L'ajout de –Security:CopyAll remplit les rôles et l'appartenance au rôle à partir de la base de données de sauvegarde vers la nouvelle base de données restaurée.  
  
## Exemple 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile testdb.abf –name AWTEST2 –password:$pwd  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 Les lignes 1 et 2 sont utilisées de manière à demander le mot de passe utilisé pour chiffrer le fichier.  
  
 La ligne 3 restaure un fichier de sauvegarde Analysis Services chiffré (testdb.abf) à partir d'un dossier de sauvegarde local d'une instance par défaut Analysis Services.  
  
 Les lignes 4 et 5 suppriment le mot de passe.  
  
## Exemple 3 (scénario à distance)  
 Cet exemple montre comment restaurer un fichier de sauvegarde local à partir d’un partage de fichiers vers une instance d’Analysis Services. Dans cet exemple, un fichier de sauvegarde est restauré sous la forme d’une base de données nommée **internetsales** sur une instance par défaut d’Analysis Services, sur un ordinateur nommé **ssas-aw-srv01**.  
  
 Le fichier de sauvegarde se trouve sur un partage réseau, avec un accès en lecture public. L’instance Analysis Services distante doit avoir un accès en lecture au fichier. L’emplacement du fichier doit être un partage réseau (pas de disques).  
  
 Notez que cet exemple ne repose pas sur le fournisseur SQLAS. Vous pouvez exécuter l’applet de commande comme une commande autonome.  
  
```  
PS SQLSERVER:\> restore-asdatabase -restorefile "\\FileServer01\DBFiles\InternetSalesTabular.abf" -name "internetsales  
" -server "SSAS-AW-SRV01"  
```  
  
## Exemple 4  
  
```  
PS SQLSERVER:\SQLAS\localhost\default> restore-asdatabase –restorefile “\\myremoteserver\backups\testdb.abf” –name Contoso_Retail –server myremoteserver –storagelocation “\\myremoteserver\restoreDBFiles”  
```  
  
 Cette commande restaure un fichier de sauvegarde Analysis Services chiffré (testdb.abf) dans un dossier de sauvegarde distant sur une instance par défaut Analysis Services distante. Le paramètre –StorageLocation est utilisé pour placer les fichiers de base de données dans un emplacement non défini par défaut, dans ce cas un fichier partagé nommé restoreDBfiles.  
  
## Voir aussi  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Gérer les modèles tabulaires à l'aide de PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  