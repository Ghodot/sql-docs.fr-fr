---
title: Référence SQL Server Express LocalDB | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 25b71829-bdb1-46f4-ac36-80ddced52f3d
caps.latest.revision: 8
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 25ed8182742c68d2b7bd51502300135d6aa2c07c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253551"
---
# <a name="sql-server-express-localdb-reference"></a>Référence SQL Server Express LocalDB
  Cette section contient des informations sur SQL Server Express LocalDB :  
  
-   [Guide de référence des messages d’erreur propres à SQL Server Express LocalDB](express-localdb-error-messages/sql-server-express-localdb-reference-error-messages.md)  
  
-   [Guide de référence de l’API d’instance SQL Server Express LocalDB](express-localdb-instance-apis/sql-server-express-localdb-reference-instance-apis.md)  
  
## <a name="code-sample"></a>Exemple de code  
 L'exemple ci-dessous illustre l'API LocalDB.  Avant d'exécuter cet exemple, assurez-vous que LocalDB est installé sur l'ordinateur.  Vous pouvez installer LocalDB à partir du programme d'installation de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Express.  
  
```  
// compile with: Advapi32.lib  
#include <SDKDDKVer.h>  
#include <stdio.h>  
  
// To use LocalDB API, you must define LOCALDB_DEFINE_PROXY_FUNCTIONS before you include sqlncli.h in one (and only one) of the   
// source files in your program. LOCALDB_DEFINE_PROXY_FUNCTIONS causes code to be generated that binds to the LocalDB API at runtime.  
  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include "sqlncli.h"  
  
HRESULT CreateAndStartLocalDBInstance(PWCHAR wszVersion, PWCHAR wszInstanceName) {  
   HRESULT hr;  
  
   if (SUCCEEDED(hr = LocalDBCreateInstance(wszVersion, wszInstanceName, 0)))  
      hr = LocalDBStartInstance(wszInstanceName, 0, NULL, NULL);  
  
   return hr;  
}  
  
HRESULT StopAndDeleteLocalDBInstance(PWCHAR wszInstanceName) {  
   HRESULT hr;  
  
   if (SUCCEEDED(hr = LocalDBStopInstance(wszInstanceName, 0, 30)))   // 30 seconds timeout   
      hr = LocalDBDeleteInstance(wszInstanceName, 0);  
  
   return hr;  
}  
  
void PrintLocalDBError(HRESULT hr) {  
   HRESULT hrError;  
   WCHAR wszMessage[1024];  
   DWORD dwMessage = 1024;  
  
   if (hr == LOCALDB_ERROR_NOT_INSTALLED)  
      wprintf(L"Local DB is not installed.\n");  
  
   else if (hr == LOCALDB_ERROR_CANNOT_LOAD_RESOURCES)  
      wprintf(L"Cannot load resources for Local DB API DLL. Local DB installation is corrupted.\n");  
  
   else if (FAILED(hrError = LocalDBFormatMessage(hr, 0, 0, wszMessage, &dwMessage)))  
      wprintf(L"Cannot format an error message for a Local DB error code: %#x. LocalDBFormatMessage returned: %#x\n", hr, hrError);  
  
   else  
      wprintf(L"%s\n", wszMessage);  
}  
  
HRESULT PrintLocalDBInstances() {  
   HRESULT hr;  
   DWORD dwNumberOfInstances = 0;  
  
   if (FAILED(hr = LocalDBGetInstances(NULL, &dwNumberOfInstances)))  
      if (hr != LOCALDB_ERROR_INSUFFICIENT_BUFFER)  
         return hr;  
  
   PTLocalDBInstanceName localDBInstnces = (PTLocalDBInstanceName) malloc(dwNumberOfInstances * sizeof(TLocalDBInstanceName));  
   if (localDBInstnces == NULL) {  
      return HRESULT_FROM_WIN32(ERROR_OUTOFMEMORY);  
   }  
  
   if (FAILED(hr = LocalDBGetInstances(localDBInstnces, &dwNumberOfInstances))) {  
      free(localDBInstnces);  
      return hr;  
   }  
  
   for (DWORD i = 0; i < dwNumberOfInstances; i++) {  
      LocalDBInstanceInfo localDBInstanceInfo;  
  
      if (FAILED(hr = LocalDBGetInstanceInfo(localDBInstnces[i], &localDBInstanceInfo, sizeof(localDBInstanceInfo)))) {  
         free(localDBInstnces);  
         return hr;  
      }  
  
      wprintf(L"Name: %s State: %s Version: %u.%u.%u.%u\n",  
         localDBInstnces[i],   
         localDBInstanceInfo.bIsRunning ? L"running" : L"stopped",  
         localDBInstanceInfo.dwMajor,  
         localDBInstanceInfo.dwMinor,  
         localDBInstanceInfo.dwBuild,  
         localDBInstanceInfo.dwRevision);  
   }  
  
   free(localDBInstnces);  
   return S_OK;  
}  
  
int main() {  
   HRESULT hr;  
  
   WCHAR wszInstanceName[] = L"Contoso";  
   WCHAR wszVersion[] = L"11.0";  
  
   if (FAILED(hr = CreateAndStartLocalDBInstance(wszVersion, wszInstanceName)))  
      PrintLocalDBError(hr);  
  
   PrintLocalDBInstances();  
  
   if (FAILED(hr = StopAndDeleteLocalDBInstance(wszInstanceName)))  
      PrintLocalDBError(hr);  
  
   PrintLocalDBInstances();  
}  
```  
  
  
