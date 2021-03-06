---
title: À l’aide de métadonnées de la base de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf9fd776fc14c060d5624d704efc315cc04da85f
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661641"
---
# <a name="using-database-metadata"></a>Utilisation des métadonnées de base de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour interroger une base de données afin de recueillir des informations sur ce qu’elle prend en charge, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implémente la classe [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md). Cette classe contient plusieurs méthodes qui retournent des informations sous la forme d'une valeur unique ou d'un jeu de valeurs.

Pour créer un objet SQLServerDatabaseMetaData, vous pouvez utiliser la méthode [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) pour obtenir des informations concernant la base de données.

Dans l’exemple suivant, une connexion ouverte à la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de données est transmise à la fonction, la méthode getMetaData de la classe SQLServerConnection est utilisée pour retourner un objet SQLServerDatabaseMetadata et puis diverses méthodes de la Objet SQLServerDatabaseMetaData sont utilisés pour afficher des informations sur la version de base de données, version du pilote, de nom de la base de données et pilote.

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a> Voir aussi

[Gestion des métadonnées avec le pilote JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
