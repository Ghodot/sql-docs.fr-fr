---
title: Valider un package DAC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-data-tier-apps
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], validate
- data-tier application [SQL Server], compare
- validate DAC
- compare DACs
- data-tier application [SQL Server], view
- view DAC
ms.assetid: 726ffcc2-9221-424a-8477-99e3f85f03bd
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29496d117c1fde896bcf72cc6e485e6b3a1cef62
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322289"
---
# <a name="validate-a-dac-package"></a>Valider un package DAC
  Il est conseillé d'examiner le contenu d'un package DAC avant de le déployer en production et de valider les actions de mise à niveau avant de mettre à niveau une DAC existante. Ceci tout particulièrement lors du déploiement de packages qui n'ont pas été développés dans votre organisation.  
  
1.  **Avant de commencer :**  [Conditions préalables](#Prerequisites)  
  
2.  **Pour mettre à niveau une DAC, à l'aide de :**  [Afficher le contenu d'une DAC](#ViewDACContents), [Afficher les modifications de base de données](#ViewDBChanges), [Afficher les actions de mise à niveau](#ViewUpgradeActions), [Compare DACs](#CompareDACs)  
  
##  <a name="Prerequisites"></a> Conditions préalables  
 Nous vous recommandons de ne pas déployer un package DAC provenant de sources inconnues ou non approuvées. Ces DAC peuvent contenir du code malveillant susceptible d'exécuter un code [!INCLUDE[tsql](../../includes/tsql-md.md)] indésirable ou de provoquer des erreurs en modifiant le schéma. Avant d’utiliser une DAC provenant d’une source inconnue ou non approuvée, déployez-la sur une instance de test isolée de [!INCLUDE[ssDE](../../includes/ssde-md.md)], exécutez [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sur la base de données sur un serveur autre qu’un serveur de production et examinez également le code (par exemple les procédures stockées ou tout autre code défini par l’utilisateur) contenu dans la base de données.  
  
##  <a name="ViewDACContents"></a> Afficher le contenu d'une DAC  
 Il existe deux mécanismes d'affichage du contenu d'un package d'application de la couche Données (DAC). Vous pouvez importer le package DAC vers un projet DAC dans les outils de développement de SQL Server. Vous pouvez décompresser le contenu du package dans un dossier.  
  
 **Afficher une DAC dans les outils de développement de SQL Server**  
  
1.  Dans le menu **Fichier** , sélectionnez **Nouveau**, puis **Projet**.  
  
2.  Sélectionnez le modèle de projet **SQL Server** , puis spécifiez un **Nom**, un **Emplacement**et un **Nom de solution**.  
  
3.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet, puis sélectionnez **Propriétés**.  
  
4.  Sous l’onglet **Paramètres du projet** , dans la section **Type de sortie** , cochez la case **Application de la couche Données (fichier .dacpac)** , puis fermez la boîte de dialogue de propriétés.  
  
5.  Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Importer une application de la couche Données**.  
  
6.  Utilisez l’ **Explorateur de solutions** pour ouvrir tous les fichiers de la DAC, tels que la stratégie de sélection du serveur et les scripts de pré- et post-déploiement.  
  
7.  Utilisez le **Mode schéma** pour examiner tous les objets du schéma, en particulier le code des objets, comme les fonctions ou les procédures stockées.  
  
 **Afficher une DAC dans un dossier**  
  
-   Décompressez le package DAC dans un dossier en suivant les instructions fournies dans [Unpack a DAC Package](unpack-a-dac-package.md).  
  
-   Affichez le contenu des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] en les ouvrant dans l'Éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
-   Affichez le contenu des fichiers texte dans des outils tels que le Bloc-notes.  
  
##  <a name="ViewDBChanges"></a> Afficher les modifications de base de données  
 Après la version actuelle de la DAC déployée en production, des modifications ont pu être apportées directement à la base de données associée qui peuvent être en conflit avec le schéma défini dans une nouvelle version de la DAC. Avant la mise à niveau vers une nouvelle version de la DAC, vérifiez si de telles modifications ont été apportées à la base de données.  
  
 **Afficher les modifications de base de données à l'aide d'un Assistant**  
  
1.  Exécutez l’Assistant **Mettre à niveau une application de la couche Données** , en spécifiant la DAC actuellement déployée et le package DAC qui contient la nouvelle version de la DAC.  
  
2.  Sur la page de **Détecter les modifications** , examinez le rapport des modifications apportées à la base de données.  
  
3.  Sélectionnez **Annuler** si vous ne souhaitez pas poursuivre la mise à niveau.  
  
4.  Pour plus d’informations sur l’utilisation de l’Assistant, consultez [Mettre à niveau une application de la couche Données](upgrade-a-data-tier-application.md).  
  
 **Afficher les modifications de base de données à l'aide de PowerShell**  
  
1.  Créez un objet serveur SMO et définissez-le sur l'instance qui contient la DAC à afficher.  
  
2.  Ouvrir un `ServerConnection` de l’objet et de se connecter à la même instance.  
  
3.  Spécifiez le nom de la DAC dans une variable.  
  
4.  Utilisez le `GetDatabaseChanges()` méthode pour récupérer un `ChangeResults` objet et redirigez l’objet vers un fichier texte pour générer un rapport simple des nouveaux, supprimés, objets et modifiés.  
  
### <a name="view-database-changes-example-powershell"></a>Afficher une exemple de modifications de base de données (PowerShell)  
 **Afficher une exemple de modifications de base de données (PowerShell)**  
  
 L'exemple suivant signale toutes les modifications de base de données qui ont été apportées dans une DAC déployée nommée MyApplication.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the change list and save to file.  
$dacChanges = $dacstore.GetDatabaseChanges($dacName) | Out-File -Filepath C:\DACScripts\MyApplicationChanges.txt  
```  
  
##  <a name="ViewUpgradeActions"></a> Afficher les actions de mise à niveau  
 Avant d'utiliser une nouvelle version d'un package DAC en vue de mettre à niveau une DAC déployée à partir d'une version antérieure d'un package DAC, vous pouvez générer un rapport contenant les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui seront exécutées durant la mise à niveau, puis passer en revue ces instructions.  
  
 **Signaler les actions de mise à niveau à l'aide d'un Assistant**  
  
1.  Exécutez l’Assistant **Mettre à niveau une application de la couche Données** , en spécifiant la DAC actuellement déployée et le package DAC qui contient la nouvelle version de la DAC.  
  
2.  Sur la page **Résumé** , examinez le rapport des actions de mise à niveau.  
  
3.  Sélectionnez **Annuler** si vous ne souhaitez pas poursuivre la mise à niveau.  
  
4.  Pour plus d’informations sur l’utilisation de l’Assistant, consultez [Mettre à niveau une application de la couche Données](upgrade-a-data-tier-application.md).  
  
 **Signaler les actions de mise à niveau à l'aide de PowerShell**  
  
1.  Créez un objet serveur SMO et définissez-le sur l'instance qui contient la DAC déployée.  
  
2.  Ouvrir un `ServerConnection` de l’objet et de se connecter à la même instance.  
  
3.  Utilisez `System.IO.File` pour charger le fichier de package DAC.  
  
4.  Spécifiez le nom de la DAC dans une variable.  
  
5.  Utilisez le `GetIncrementalUpgradeScript()` méthode pour obtenir une liste des instructions Transact-SQL à une mise à niveau est exécuté et redirigez cette liste dans un fichier texte.  
  
6.  Fermez le flux de fichier utilisé pour lire le fichier de package DAC.  
  
### <a name="view-upgrade-actions-example-powershell"></a>Afficher un exemple d'actions de mise à niveau (PowerShell)  
 **Afficher un exemple d'actions de mise à niveau (PowerShell)**  
  
 L'exemple suivant signale les instructions Transact-SQL qui seraient exécutées pour mettre à niveau une DAC nommée MyApplication vers le schéma défini dans un fichier MyApplicationVNext.dacpac.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the upgrade script and save to file.  
$dacstore.GetIncrementalUpgradeScript($dacName, $dacType) | Out-File -Filepath C:\DACScripts\MyApplicationUpgrade.sql  
  
## Close the filestream to the new DAC package.  
$fileStream.Close()  
```  
  
##  <a name="CompareDACs"></a> Compare DACs  
 Avant de mettre à niveau une DAC, il est conseillé d'examiner les différences dans la base de données et les objets au niveau de l'instance entre les DAC actuelles et nouvelles. Si vous ne disposez pas d'une copie du package de la DAC actuelle, vous pouvez extraire un package de la base de données actuelle.  
  
 Si vous importez les deux packages DAC dans des projets DAC dans les outils de développement de SQL Server, vous pouvez utiliser l'outil Comparaison de schémas pour analyser les différences entre les deux DAC.  
  
 Ou bien, décompressez les DAC dans des dossiers distincts. Vous pouvez ensuite utiliser un outil de comparaison, tel que l'utilitaire WinDiff, pour analyser les différences.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications de la couche Données](data-tier-applications.md)   
 [Déployer une application de la couche Données](deploy-a-data-tier-application.md)   
 [Mettre à niveau une application de la couche Données](upgrade-a-data-tier-application.md)  
  
  
