---
title: Exporter et importer une base de données sur Linux | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.custom: sql-linux
ms.openlocfilehash: 1ce94cb159e552b147ad1798eeacf60b9c7ff25a
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085091"
---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>Exporter et importer une base de données sur Linux avec SSMS ou SqlPackage.exe sur Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article montre comment utiliser [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) et [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx) pour exporter et importer une base de données sur SQL Server 2017 sur Linux. SSMS et SqlPackage.exe sont les applications Windows, utilisez cette technique quand vous avez une machine Windows pouvant se connecter à une instance distante de SQL Server sur Linux.

Vous devez toujours installer et utiliser la dernière version de SQL Server Management Studio (SSMS), comme décrit dans [utiliser de SSMS sur Windows pour se connecter à SQL Server sur Linux](sql-server-linux-manage-ssms.md)

> [!NOTE]
> Si vous migrez une base de données à partir d’une instance de SQL Server vers un autre, la recommandation consiste à utiliser [sauvegarde et restauration](sql-server-linux-migrate-restore-database.md).

## <a name="export-a-database-with-ssms"></a>Exporter une base de données avec SSMS

1. Démarrez SSMS en tapant **Microsoft SQL Server Management Studio** dans la zone de recherche Windows, puis cliquez sur l'application de bureau.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Se connecter à votre base de données source dans l’Explorateur d’objets. La base de données source peut être dans Microsoft SQL Server s’exécutant en local ou dans le cloud, sur Linux, Windows ou Docker et Azure SQL Database ou Azure SQL Data Warehouse.

3. Avec le bouton droit de la base de données source dans l’Explorateur d’objets, pointez sur **tâches**, puis cliquez sur **exporter une Application de couche données...**

4. Dans l’Assistant Exportation, cliquez sur **suivant**, puis, dans le **paramètres** , configurez l’exportation pour enregistrer le fichier BACPAC à deux emplacements sur le disque local ou à un objet blob Azure.

5. Par défaut, tous les objets dans la base de données sont exportées. Cliquez sur le **onglet Avancé** et choisir les objets de base de données que vous souhaitez exporter.

6. Cliquez sur **Suivant** , puis sur **Terminer**.

Le *. Fichier BACPAC créé à l’emplacement que vous avez choisi, et vous êtes prêt à importer dans une base de données cible.

## <a name="import-a-database-with-ssms"></a>Importer une base de données avec SSMS

1. Démarrez SSMS en tapant **Microsoft SQL Server Management Studio** dans la zone de recherche Windows, puis cliquez sur l'application de bureau.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Se connecter à votre serveur cible dans l’Explorateur d’objets. Le serveur cible peut être Microsoft SQL Server s’exécutant en local ou dans le cloud, sur Linux, Windows ou Docker et Azure SQL Database ou Azure SQL Data Warehouse.

3. Cliquez sur le **bases de données** dossier dans l’Explorateur d’objets et cliquez sur **importer une Application de couche données...**

4. Pour créer la base de données dans votre serveur cible, spécifiez un fichier BACPAC à partir de votre disque local, ou sélectionnez le compte de stockage Azure et le conteneur auquel vous avez téléchargé votre fichier BACPAC.

5. Indiquez le nouveau nom de base de données pour la base de données. Si vous importez une base de données sur la base de données SQL Azure, définissez l’édition de Microsoft Azure SQL Database (niveau de service), taille de base de données maximale et l’objectif de Service (niveau de performance).

6. Cliquez sur **suivant** puis cliquez sur **Terminer** pour importer le fichier BACPAC dans une base de données dans votre serveur cible.

Le *. Fichier BACPAC est importé pour créer une nouvelle base de données dans le serveur cible spécifié.

## <a id="sqlpackage"></a> Option de ligne de commande SqlPackage

Il est également possible d’utiliser l’outil de ligne de commande SQL Server Data Tools (SSDT), [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx), pour exporter et importer des fichiers BACPAC.

L’exemple de commande suivant exporte un fichier BACPAC :

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

Utilisez la commande suivante pour importer des données de schéma et d’utilisateur de base de données à partir d’un. Fichier BACPAC :

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>Voir aussi
Pour plus d’informations sur l’utilisation de SSMS, consultez [utiliser SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx). Pour plus d’informations sur SqlPackage.exe, consultez le [documentation de référence sur SqlPackage](https://msdn.microsoft.com/library/hh550080.aspx).
