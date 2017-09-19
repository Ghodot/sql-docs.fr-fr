---
title: "Exemple de Code de bibliothèque de curseurs | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], examples
- cursor library [ODBC], examples
ms.assetid: 958a179c-97d9-4717-8d06-d33b715a9773
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: acf011e1a3c41a5d16ca39740b8dcd099ff3bf77
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-library-code-example"></a>Exemple de Code de bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 L’exemple suivant utilise la bibliothèque de curseurs pour récupérer les ID de chaque commande, ouvrez date et l’état de la table ORDERS. Il affiche ensuite les 20 lignes de données. Si l’utilisateur met à jour ces données, le code met à jour les mémoires tampons de lignes et exécute une instruction de mise à jour positionnée. Enfin, il invite l’utilisateur à la direction pour faire défiler et répète le processus.  
  
```  
#define ROWS 20  
#define STATUS_LEN 6  
#define OPENDATE_LEN 11  
#define DONE -1  
  
SQLHENV        henv;  
SQLHDBC        hdbc;  
SQLHSTMT       hstmt1, hstmt2;  
SQLRETURN      retcode;  
SQLCHAR        szStatus[ROWS][STATUS_LEN],   
               szOpenDate[ROWS][OPENDATE_LEN];  
SQLCHAR        szNewStatus[STATUS_LEN], szNewOpenDate[OPENDATE_LEN];  
SQLSMALLINT    sOrderID[ROWS], sNewOrderID[ROWS];  
SQLINTEGER     cbStatus[ROWS], cbOrderID[ROWS], cbOpenDate[ROWS];  
SQLUINTEGER    FetchOrientation, crow, FetchOffset, irowUpdt;  
SQLUSMALLINT   RowStatusArray[ROWS];  
  
SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, SQL_OV_ODBC3,0);  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
// Specify that the ODBC Cursor Library is always used, then connect.  
  
SQLSetConnectAttr(hdbc, SQL_ATTR_ODBC_CURSORS, SQL_CUR_USE_ODBC);  
SQLConnect(hdbc, "SalesOrder", SQL_NTS,  
            "JohnS", SQL_NTS,  
            "Sesame", SQL_NTS);  
  
if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
   /* Allocate a statement handle for the result set and a statement */  
   /* handle for positioned update statements. */  
  
   SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt1);  
   SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt2);  
  
   /* Specify an updatable static cursor with 20 rows of data. Set */  
   /* the cursor name, execute the SELECT statement, and bind the */  
   /* rowset buffers to result set columns in column-wise fashion. */  
   SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQL_CONCUR_VALUES, 0);  
   SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_STATIC, 0);  
   SQLSetStmtAttr(hstmt1, SQL_ATTR_ROW_ARRAY_SIZE, ROWS, 0);  
   SQLSetStmtAttr(hstmt1, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
   SQLSetStmtAttr(hstmt1, SQL_ATTR_ROWS_FETCHED_PTR, &crow, 0);  
   SQLSetCursorName(hstmt1, "ORDERCURSOR", SQL_NTS);  
   SQLExecDirect(hstmt1,  
                  "SELECT ORDERID, OPENDATE, STATUS FROM ORDERS ",  
                  SQL_NTS);  
   SQLBindCol(hstmt1, 1, SQL_C_SSHORT, sOrderID, 0, cbName);  
   SQLBindCol(hstmt1, 2, SQL_C_CHAR, szOpenDate, OPENDATE_LEN, cbOpenDate);  
   SQLBindCol(hstmt1, 3, SQL_C_CHAR, szStatus, STATUS_LEN, cbStatus);  
  
   /* Fetch the first block of data and display it. Prompt the user */  
   /* for new data values. If the user supplies new values, update */  
   /* the rowset buffers, bind them to the parameters in the update */  
   /* statement, and execute a positioned update on another hstmt. */  
   /* Prompt the user for how to scroll. Fetch and redisplay data as */  
   /* needed. */  
  
   FetchOrientation = SQL_FETCH_FIRST;  
   FetchOffset = 0;  
   do {  
  
      SQLFetchScroll(hstmt1, FetchOrientation, FetchOffset);  
      DisplayRows(sOrderID, szOpenDate, szStatus, RowStatusArray);  
  
      if (PromptUpdate(&irowUpdt,&sNewOrderID,szNewOpenDate,szNewStatus)==TRUE){  
         sOrderID[irowUpdt] = sNewOrderID;  
         cbOrderID[irowUpdt] = 0;  
         strcpy_s((char*)szOpenDate[irowUpdt], _countof(szOpenDate[irowUpdt]), szNewOpenData);  
         cbOpenDate[irowUpdt] = SQL_NTS;  
         strcpy_s((char*)szStatus[irowUpdt], _countof(szStatus[irowUpdt]), szNewStatus);  
         cbStatus[irowUpdt] = SQL_NTS;  
         SQLBindParameter(hstmt2, 1, SQL_PARAM_INPUT,  
                           SQL_C_SSHORT, SQL_INTEGER, 0, 0,  
                           &sOrderID[irowUpdt], 0, &cbOrderID[irowUpdt]);  
         SQLBindParameter(hstmt2, 2, SQL_PARAM_INPUT,  
                           SQL_C_CHAR, SQL_TYPE_DATE, OPENDATE_LEN, 0,  
                           szOpenDate[irowUpdt], OPENDATE_LEN, &cbOpenDate[irowUpdt]);  
         SQLBindParameter(hstmt2, 3, SQL_PARAM_INPUT,  
                           SQL_C_CHAR, SQL_CHAR, STATUS_LEN, 0,  
                           szStatus[irowUpdt], STATUS_LEN, &cbStatus[irowUpdt]);  
         SQLExecDirect(hstmt2,  
                        "UPDATE EMPLOYEE SET ORDERID = ?, OPENDATE = ?, STATUS = ?"  
                        "WHERE CURRENT OF EMPCURSOR",  
                        SQL_NTS);  
      }  
  
   while (PromptScroll(&FetchOrientation, &FetchOffset) != DONE)  
}  
```