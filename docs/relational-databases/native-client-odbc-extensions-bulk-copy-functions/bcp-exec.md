---
title: bcp_exec | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_exec
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2592a8a2b15369ecd15185cd3ccb9b9d6bd13356
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43078000"
---
# <a name="bcpexec"></a>bcp_exec
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Exécute une copie en bloc complète des données entre une table de base de données et un fichier utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_exec (  
        HDBC hdbc,  
        LPDBINT pnRowsProcessed);  
```  
  
## <a name="arguments"></a>Arguments  
 *pas*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *pnRowsProcessed*  
 Pointeur vers un DBINT. La fonction **bcp_exec** remplit ce DBINT avec le nombre de lignes copiées avec succès. Si *pnRowsProcessed* a la valeur NULL, la fonction **bcp_exec**l'ignore.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED, SUCCEED_ASYNC ou FAIL. La fonction **bcp_exec** retourne SUCCEED si toutes les lignes sont copiées. **bcp_exec** retourne SUCCEED_ASYNC si une opération de copie en bloc asynchrone est toujours en attente. **bcp_exec** retourne FAIL en cas de défaillance complète, ou si le nombre de lignes générant des erreurs atteint la valeur spécifiée pour BCPMAXERRS à l’aide [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md). La valeur par défaut de BCPMAXERRS est 10. L'option BCPMAXERRS affecte uniquement les erreurs de syntaxe détectées par le fournisseur lorsqu'elle lit les données du fichier de données (et non les lignes transmises au serveur). Le serveur interrompt le lot dès qu'il détecte une erreur avec une ligne. Vérifiez le paramètre *pnRowsProcessed* correspondant au nombre de lignes copiées avec succès.  
  
## <a name="remarks"></a>Notes  
 Cette fonction copie les données à partir d’un fichier utilisateur vers une table de base de données ou vice versa, selon la valeur de la *eDirection* paramètre dans [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md).  
  
 Avant d'appeler **bcp_exec**, appelez **bcp_init** avec un nom de fichier utilisateur valide. L'échec de cette opération entraîne une erreur.  
  
 **bcp_exec** est la seule fonction de copie en bloc qui est susceptible d'être en attente pendant une durée prolongée. Il s'agit par conséquent de la seule fonction de copie en bloc qui prend en charge le mode asynchrone. Pour définir le mode asynchrone, utilisez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) pour définir SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_ON avant d’appeler **bcp_exec**. Pour tester son exécution en bonne et due forme, appelez la méthode **bcp_exec** avec les mêmes paramètres. Si la copie en bloc n'a pas encore été exécutée, **bcp_exec** retourne SUCCEED_ASYNC. Il retourne également dans *pnRowsProcessed* un état du nombre de lignes envoyées au serveur. Les lignes envoyées au serveur sont validées uniquement une fois la fin du lot atteinte.  
  
 Pour plus d’informations sur les importantes modifier une copie en bloc de début dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], consultez [effectuant des opérations de copie en bloc &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="example"></a>Exemple  
 L'exemple ci-après décrit comment utiliser la fonction **bcp_exec**:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
