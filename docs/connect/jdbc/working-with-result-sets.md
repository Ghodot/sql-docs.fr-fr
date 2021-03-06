---
title: Utilisation des jeux de résultats | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86c2d4fdcaee554f9e4ed04a2765e7a02779a94b
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784777"
---
# <a name="working-with-result-sets"></a>Travail sur des jeux de résultats

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Quand vous travaillez sur les données contenues dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une méthode de manipulation des données consiste à utiliser un jeu de résultats. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge l’utilisation des jeux de résultats par le biais de l’objet [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Grâce à l’objet SQLServerResultSet, vous pouvez extraire les données retournées à partir d’une instruction SQL ou d’une procédure stockée, mettre à jour les données si nécessaire, puis remettre ces données dans la base de données.  
  
En outre, l’objet SQLServerResultSet fournit des méthodes de navigation dans ses lignes de données, d’obtention ou de définition des données qu’il contient et d’établissement de plusieurs niveaux de sensibilité aux modifications apportées à la base de données sous-jacente.  
  
> [!NOTE]  
> Pour plus d’informations sur la gestion des jeux de résultats, y compris leur sensibilité aux modifications, consultez [la gestion des jeux de résultats avec le pilote JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
Les rubriques de cette section décrivent différentes façons d’utiliser un jeu de résultats pour manipuler les données contenues dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
| Rubrique                                                                                        | Description                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Exemple de récupération de données du jeu de résultats](../../connect/jdbc/retrieving-result-set-data-sample.md) | Décrit l’utilisation d’un jeu de résultats pour extraire des données à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les afficher.                                                         |
| [Exemple de modification des données du jeu de résultats](../../connect/jdbc/modifying-result-set-data-sample.md)   | Décrit l’utilisation d’un jeu de résultats pour insérer, extraire et modifier des données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].                                                      |
| [Exemple de mise en cache de données du jeu de résultats](../../connect/jdbc/caching-result-set-data-sample.md)       | Décrit l’utilisation d’un jeu de résultats pour extraire de grandes quantités de données à partir d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et pour contrôler la manière dont ces données sont mises en cache sur le client. |
  
## <a name="see-also"></a> Voir aussi

 [Exemples d’applications JDBC Driver](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  