---
title: "Configurer les fonctionnalités de SQL Server compatibles avec Stretch Database | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8121ede-1aec-459b-b7b0-1408bb3e62fb
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 84464c4553eab6d8e65c0bf6b476ae728e2a8463
ms.lasthandoff: 04/11/2017

---
# <a name="configure-compatible-sql-server-features-with-stretch-database"></a>Configurer les fonctionnalités de SQL Server compatibles avec Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Suivez des étapes simples pour configurer les fonctionnalités SQL Server suivantes afin de les rendre compatibles avec Stretch Database.
-   Always On
-   Always Encrypted
-   Chiffrement transparent des données (TDE)
-   Tables temporelles

## <a name="configure-always-on-with-stretch-database"></a>Configurer Always On avec Stretch Database
Si vous utilisez Always On avec Stretch Database, vous devez vous assurer que la clé principale de base de données est disponible sur les réplicas secondaires. Stretch Database utilise la clé principale de base de données pour sécuriser les informations d’identification utilisées pour la connexion à la base de données Azure distante.

Après avoir configuré le groupe de disponibilité Always On, exécutez la procédure stockée **sp_control_dbmasterkey_password** sur chaque réplica secondaire et fournissez le mot de passe pour la base de données Stretch. Pour plus d’informations et des exemples, consultez [sp_control_dbmasterkey_password](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md). 

## <a name="configure-always-encrypted-with-stretch-database"></a>Configurer Always Encrypted avec Stretch Database
Si vous souhaitez utiliser conjointement Always Encrypted et Stretch Database, vous devez configurer le chiffrement sur les colonnes sélectionnées avant d’activer la base de données Stretch sur la table.

Si vous avez déjà activé la base de données Stretch sur la table et que vous souhaitez utiliser les colonnes Always Encrypted, vous devez effectuer les opérations suivantes.
1.   Désactiver Stretch Database sur la table et afficher à nouveau les données distantes à partir d’Azure. Pour plus d’informations, consultez [Désactiver Stretch Database et récupérer les données distantes](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).
2.   Configurez Always Encrypted sur les colonnes sélectionnées.
3. Réactivez Stretch Database sur la table. Pour plus d’informations, consultez [Activer Stretch Database pour une base de données](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).

## <a name="configure-transparent-data-encryption-tde-with-stretch-database"></a>Configurer le chiffrement transparent des données (TDE) avec Stretch Database

Si le chiffrement transparent des données est activé sur votre base de données locale, il n’est pas automatiquement activé sur le point de terminaison distant de la base de données Stretch. Vous devez penser à activer le chiffrement transparent des données sur le point de terminaison distant après l’activation de Stretch sur votre base de données.

## <a name="configure-temporal-tables-with-stretch-database"></a>Configurer les tables temporelles avec Stretch Database
Si vous utilisez des tables temporelles, vous pouvez activer Stretch Database sur la table d’historique, mais pas sur la table actuelle.
-   Pour obtenir des conseils sur l’utilisation de tables temporelles avec Stretch Database, consultez [Gérer la rétention de données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md).
-   Pour filtrer les lignes pour migrer à partir de la table d’historique à l’aide d’une fenêtre glissante, consultez [Sélectionner les lignes à migrer à l’aide d’une fonction de filtre](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).