---
title: Téléchargez et installez Microsoft SQL Operations Studio (version préliminaire) | Microsoft Docs
description: Télécharger et installer Microsoft SQL Operations Studio (version préliminaire) pour Windows, macOS ou Linux
ms.custom: tools|sos
ms.date: 08/30/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30eea457bdba7ac671829bb02f01152235babaf3
ms.sourcegitcommit: 2a47e66cd6a05789827266f1efa5fea7ab2a84e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43348650"
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Téléchargez et installez SQL Operations Studio (version préliminaire)

[!INCLUDE[name-sos](../includes/name-sos.md)] s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version, le *version préliminaire publique d’août*:

|Plateforme|Télécharger|Date de publication| Version |
|:---|:---|:---|:---|
|Windows|[Programme d’installation](https://go.microsoft.com/fwlink/?linkid=2013365)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2013712)|30 août 2018 |0.32.8|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2013715)|30 août 2018 |0.32.8|
|Linux|[.DEB](https://go.microsoft.com/fwlink/?linkid=2013833)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2013830)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2013718)|30 août 2018 |0.32.8|

Pour plus d’informations sur la dernière version, consultez le [notes de version](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Obtenir SQL Operations Studio (version préliminaire) pour Windows

Cette version de [!INCLUDE[name-sos](../includes/name-sos-short.md)] inclut une expérience de programme d’installation Windows standard et un fichier zip : 

**Programme d’installation**

1. Téléchargez et exécutez le [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] programme d’installation pour Windows](https://go.microsoft.com/fwlink/?linkid=2013365).
1. Démarrer le [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] application.


**fichier .zip**

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] .zip pour Windows](https://go.microsoft.com/fwlink/?linkid=2013712).
2. Recherchez le fichier téléchargé et extrayez-le.
3. Exécutez `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Obtenir SQL Operations Studio (version préliminaire) pour macOS

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour macOS](https://go.microsoft.com/fwlink/?linkid=2013715).
2. Pour développer le contenu du fichier zip, double-cliquez dessus.
3. Pour rendre [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibles dans le *Launchpad*, faites glisser *sqlops.app* à la *Applications* dossier.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Obtenir SQL Operations Studio (version préliminaire) pour Linux

1. Télécharger [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour Linux à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
    - [.DEB](https://go.microsoft.com/fwlink/?linkid=2013833)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2013830)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2013718)
1. Pour extraire le fichier et le lancement [!INCLUDE[name-sos](../includes/name-sos-short.md)], ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation de Debian :**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **tours/minute d’Installation :**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **TAR.gz Installation :**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > Sur Ubuntu, Red Hat et Debian, vous pouvez avoir de dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :
   

   **Debian :** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat :** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu :** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>Désinstaller SQL Operations Studio (version préliminaire)

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] à l’aide du programme d’installation de Windows, puis désinstaller de la même manière que n’importe quelle application Windows.

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] avec un fichier ZIP ou autres archive, puis supprimez simplement les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

[!INCLUDE[name-sos](../includes/name-sos-short.md)] s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows
- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Nécessite Windows 7 (SP1) (64 bits) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Rechercher des mises à jour
Pour vérifier les dernières mises à jour, cliquez sur l’icône d’engrenage dans la coin inférieur gauche de la fenêtre et cliquez sur **vérifier les mises à jour**

## <a name="next-steps"></a>Étapes suivantes

Consultez les Démarrages rapides suivants pour commencer :
- [Connexion & interrogation de SQL Server](quickstart-sql-server.md)
- [Connexion & interrogation de base de données SQL Azure](quickstart-sql-database.md)
- [Connexion & interrogation d’entrepôt de données Azure](quickstart-sql-dw.md)

Contribuer à [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) et [collecte des données d’utilisation](usage-data-collection.md).
