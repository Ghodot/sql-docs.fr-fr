---
title: Exécuter directement une instruction (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5dd4c28a6d1c025352db117d1aa163d3464989eb
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421528"
---
# <a name="execute-a-statement-directly-odbc"></a>Exécuter directement une instruction (ODBC)
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>Pour exécuter une instruction directement et une seule fois  
  
1.  Si l'instruction contient des marqueurs de paramètres, utilisez [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) pour lier chaque paramètre à une variable de programme. Remplissez les variables de programme de valeurs de données, puis configurez tous les paramètres de données en cours d'exécution.  
  
2.  Appelez [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) pour exécuter l'instruction.  
  
3.  Si vous utilisez des paramètres d'entrée de données en cours d'exécution, [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) retourne SQL_NEED_DATA. Envoyez les données par segments à l'aide de [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405) et [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>Pour exécuter plusieurs fois une instruction au moyen d'une liaison de paramètre selon les colonnes  
  
1.  Appelez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour définir les attributs suivants :  
  
     Définissez SQL_ATTR_PARAMSET_SIZE au nombre de jeux (S) de paramètres.  
  
     Définissez SQL_ATTR_PARAM_BIND_TYPE à SQL_PARAMETER_BIND_BY_COLUMN.  
  
     Définissez l'attribut SQL_ATTR_PARAMS_PROCESSED_PTR de sorte qu'il pointe vers une variable SQLUINTEGER contenant le nombre de paramètres traités.  
  
     Définissez SQL_ATTR_PARAMS_STATUS_PTR de sorte qu'il pointe vers un tableau [S] de variables SQLUSSMALLINT contenant les indicateurs d'état de paramètre.  
  
2.  Pour chaque marqueur de paramètre :  
  
     Allouez un tableau de S mémoires tampons de paramètres pour stocker les valeurs de données.  
  
     Allouez un tableau de S mémoires tampons de paramètres pour stocker les longueurs de données.  
  
     Appelez [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) pour lier les tableaux de valeur de données et de longueur de données de paramètre au paramètre d'instruction.  
  
     Configurez toutes les paramètres d'image ou de texte de données en cours d'exécution.  
  
     Mettez les valeurs de données S et les longueurs de données S dans les tableaux de paramètres liés.  
  
3.  Appelez [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) pour exécuter l'instruction. Le pilote exécute efficacement l'instruction S fois, une fois pour chaque jeu de paramètres.  
  
4.  Si vous utilisez des paramètres d'entrée de données en cours d'exécution, [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) retourne SQL_NEED_DATA. Envoyez les données par segments à l'aide de [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405) et [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>Pour exécuter plusieurs fois une instruction au moyen d'une liaison de paramètre selon les lignes  
  
1.  Allouez un tableau [S] de structures, où S est le nombre de jeux de paramètres. La structure dispose d'un élément pour chaque paramètre et chaque élément contient deux parties :  
  
     La première partie est une variable du type de données approprié destinée à contenir les données de paramètres.  
  
     La deuxième partie est une variable SQLINTEGER destinée à contenir l'indicateur d'état.  
  
2.  Appelez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour définir les attributs suivants :  
  
     Définissez SQL_ATTR_PARAMSET_SIZE au nombre de jeux (S) de paramètres.  
  
     Définissez SQL_ATTR_PARAM_BIND_TYPE à la taille de la structure allouée à l'étape 1.  
  
     Définissez l'attribut SQL_ATTR_PARAMS_PROCESSED_PTR de sorte qu'il pointe vers une variable SQLUINTEGER contenant le nombre de paramètres traités.  
  
     Définissez SQL_ATTR_PARAMS_STATUS_PTR de sorte qu'il pointe vers un tableau [S] de variables SQLUSSMALLINT contenant les indicateurs d'état de paramètre.  
  
3.  Pour chaque marqueur de paramètre, appelez [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) pour diriger les pointeurs de valeur de données et de longueur de données de paramètre vers leurs variables dans le premier élément du tableau de structures alloué à l'étape 1. Si le paramètre est un paramètre de données en cours d'exécution, installez-le.  
  
4.  Remplissez le tableau de tampons de paramètres liés avec les valeurs de données.  
  
5.  Appelez [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) pour exécuter l'instruction. Le pilote exécute efficacement l'instruction S fois, une fois pour chaque jeu de paramètres.  
  
6.  Si vous utilisez des paramètres d'entrée de données en cours d'exécution, [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) retourne SQL_NEED_DATA. Envoyez les données par segments à l'aide de [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405) et [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
 **Remarque** En règle générale, la liaison selon les colonnes et les lignes est davantage employée avec les fonctions [SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) et [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) qu'avec [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à l’exécution de requêtes &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
