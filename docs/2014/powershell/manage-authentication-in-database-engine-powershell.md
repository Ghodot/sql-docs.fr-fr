---
title: Gérer l’authentification dans le moteur de base de données PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f7ec9327a35e9ba110dd9d93db53c50b5c130f6c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227809"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>Gérer l'authentification dans le moteur de base de données PowerShell
  Par défaut, les composants de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell utilisent l'authentification Windows lors de la connexion à une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)]. Vous pouvez utiliser l’authentification SQL Server en définissant un lecteur virtuel PowerShell ou en spécifiant le `–Username` et `–Password` paramètres pour `Invoke-Sqlcmd`.  
  
1.  **Avant de commencer :**  [Autorisations](#Permissions)  
  
2.  **Pour définir l’authentification en utilisant :**  [Un lecteur virtuel](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Permissions  
 Toutes les actions que vous pouvez effectuer dans une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] sont contrôlées par les autorisations accordées aux informations d'identification utilisées pour la connexion à l'instance. Par défaut, le fournisseur et les applets de commande [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilisent le compte Windows sous lequel ils s'exécutent pour établir une connexion via l'authentification Windows au [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
 Pour établir une connexion via l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous devez fournir un ID de connexion et un mot de passe d'authentification SQL Server. Lorsque vous utilisez le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournisseur, vous devez associer le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] informations d’identification de connexion à un lecteur virtuel, puis utilisez la commande Changer de répertoire (`cd`) pour se connecter à ce lecteur. Dans Windows PowerShell, les informations d'identification de sécurité peuvent être associées uniquement à des lecteurs virtuels.  
  
##  <a name="SQLAuthVirtDrv"></a> Authentification SQL Server avec un lecteur virtuel  
 **Pour créer un lecteur virtuel associé à une connexion via l'authentification SQL Server**  
  
1.  Créez une fonction qui :  
  
    1.  Possède des paramètres pour le nom indiquant le lecteur virtuel, l'ID de connexion et le chemin d'accès du fournisseur à associer au lecteur virtuel.  
  
    2.  Utilise `read-host` pour inviter l'utilisateur à fournir le mot de passe.  
  
    3.  Utilise `new-object` pour créer un objet d'informations d'identification.  
  
    4.  Utilise `new-psdrive` pour créer un lecteur virtuel avec les informations d’identification fournies.  
  
2.  Appelez la fonction pour créer un lecteur virtuel avec les informations d'identification fournies.  
  
### <a name="example-virtual-drive"></a>Exemple (lecteur virtuel)  
 Cet exemple crée une fonction nommée **sqldrive** que vous pouvez utiliser pour créer un lecteur virtuel associé à la connexion via l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et à l'instance spécifiées.  
  
 La fonction **sqldrive** vous invite à entrer le mot de passe de votre connexion, en masquant celui-ci à mesure que vous le tapez. Ensuite, chaque fois que vous utilisez la commande Changer de répertoire (`cd`) pour vous connecter à un chemin d’accès en utilisant le nom de lecteur virtuel, toutes les opérations sont effectuées en utilisant le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] informations d’identification de connexion d’authentification que vous avez fournies lorsque vous avez créé le lecteur.  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> Authentification SQL Server avec Invoke-Sqlcmd  
 **Pour utiliser Invoke-Sqlcmd avec l'authentification SQL Server**  
  
1.  Utilisez le `–Username` paramètre pour spécifier un ID de connexion et le `–Password` paramètre pour spécifier le mot de passe associé.  
  
### <a name="example-invoke-sqlcmd"></a>Exemple (Invoke-Sqlcmd)  
 Cet exemple utilise l'applet de commande read-host pour inviter l'utilisateur à entrer un mot de passe, puis se connecte via l'authentification SQL Server.  
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" –Username “MyLogin” –Password $pwd  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](sql-server-powershell.md)   
 [fournisseur PowerShell SQL Server](sql-server-powershell-provider.md)   
 [Invoke-Sqlcmd, applet de commande](../database-engine/invoke-sqlcmd-cmdlet.md)  
  
  
