---
title: Compatibilité des versions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eeb8fc05485b90b1bafbcc3585e3e8160673e2cf
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43090553"
---
# <a name="cross-version-compatibility"></a>Compatibilité des versions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les conflits de version peuvent se produire lorsque les instances client ou serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sont censées traiter les paramètres table.  
  
 En général, les fonctionnalités des paramètres table ne sont accessibles qu'aux clients [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (avec SQL Server Native Client 10.0) ou version ultérieure connectés aux serveurs [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure). Nouvelles colonnes dans les jeux de résultats de fonction de catalogue ne sont présentes dans le cas de connexion à un [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure) server.  
  
 Si une application cliente compilée avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client exécute des instructions qui attendent des paramètres table, le serveur détecte cette situation via une erreur de conversion de données, et ODBC retourne celle-ci comme SQLSTATE 07006, avec le message « Violation de l'attribut de type de données restreint ».  
  
 Si une application cliente qui a été compilée avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 ou version ultérieure essaye d’utiliser des paramètres table lorsque connecté à une instance de serveur antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client détecte et SQLBindCol, Appels SQLBindParameter, SQLSetDescFields et SQLSetDescRec échouera avec SQLSTATE 07006 et le message « Restricted violation d’attribut de type de données (la version de SQL Server pour cette connexion ne prend pas en charge les paramètres table) ».  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
