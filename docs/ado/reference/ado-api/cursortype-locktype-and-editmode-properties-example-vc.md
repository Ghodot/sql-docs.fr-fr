---
title: CursorType, LockType et EditMode, propriétés-exemple (VC ++) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LockType property [ADO], VC++ example
- EditMode property [ADO], VC++ example
- CursorType property [ADO], VC++ example
ms.assetid: b2a80e44-03d8-426e-81b6-dd9dfc30e181
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 726a7b346052cd847c599f4389480007b6698999
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277368"
---
# <a name="cursortype-locktype-and-editmode-properties-example-vc"></a>CursorType, LockType et EditMode, propriétés-exemple (VC ++)
Cet exemple illustre la définition du [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) et [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) propriétés avant d’ouvrir un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Il montre également la valeur de la [EditMode](../../../ado/reference/ado-api/editmode-property.md) propriété sous différentes conditions. La fonction EditModeOutput est requise pour exécuter cette procédure.  
  
## <a name="example"></a>Exemple  
  
```  
// CursorType_LockType_EditMode_Property_Example.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declaration  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void EditModeX();  
void EditModeOutput(char *, int);  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   EditModeX();  
   ::CoUninitialize();  
}  
  
void EditModeX() {  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB:: namespace.  
   _RecordsetPtr pRstEmployees = NULL;  
   _ConnectionPtr pConnection = NULL;  
  
   HRESULT hr = S_OK;  
  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open a connection  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
      hr = pConnection->Open(strCnn, "", "", adConnectUnspecified);  
  
      // Open recordset with data from employee table   
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));  
  
      pRstEmployees->CursorLocation = adUseClient;  
      pRstEmployees->CursorType = adOpenStatic;  
      pRstEmployees->LockType = adLockBatchOptimistic;  
  
      pRstEmployees->Open("employee", _variant_t((IDispatch *) pConnection,true),  
         adOpenStatic, adLockBatchOptimistic, adCmdTable);  
  
      // Show the EditMode property under different editing states.  
      pRstEmployees->AddNew ();  
      pRstEmployees->Fields->Item["emp_id"]->Value = (_bstr_t)("T-T55555M");  
      pRstEmployees->Fields->Item["fname"]->Value = (_bstr_t)("temp_fname");  
      pRstEmployees->Fields->Item["lname"]->Value = (_bstr_t)("temp_lname");  
      EditModeOutput("After AddNew: ", pRstEmployees->EditMode);  
  
      pRstEmployees->UpdateBatch(adAffectCurrent);  
      EditModeOutput("After Update: ", pRstEmployees->EditMode);  
  
      pRstEmployees->Fields->Item["fname"]->Value = (_bstr_t)("test");  
      EditModeOutput("After Edit: ", pRstEmployees->EditMode);  
  
      // Delete new record because this is a demonstration.  
      pConnection->Execute("DELETE FROM employee WHERE emp_id = 'T-T55555M'",   
         NULL, adCmdText);  
   }  
   catch(_com_error &e) {  
      // Display errors, if any. Pass connection pointer accessed from the Recordset.  
      PrintProviderError(pConnection);  
      PrintComError(e);  
   }  
  
   // Clean up objects before exit.  
   if (pRstEmployees)  
      if (pRstEmployees->State == adStateOpen)  
         pRstEmployees->Close();  
   if (pConnection)  
      if (pConnection->State == adStateOpen)  
         pConnection->Close();  
}  
  
void EditModeOutput(char *strTemp, int intEditMode) {  
   // Print report based on the value of the EditMode property.  
   printf("\n%s", strTemp);  
   printf("\n  EditMode = ");  
  
   switch (intEditMode) {  
   case adEditNone :  
      printf("adEditNone");  
      break;  
   case adEditInProgress :  
      printf("adEditInProgress");  
      break;  
   case adEditAdd :  
      printf("adEditAdd");  
      break;  
   }  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\n\t Error number: %x\t%s\n", pErr->Number, (LPCSTR)pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.  
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
  **Après avoir AddNew :**   
 **EditMode = adEditAdd**  
**Après la mise à jour :**   
 **EditMode = adEditNone**  
**Après modification :**   
 **EditMode = adEditInProgress**   
## <a name="see-also"></a>Voir aussi  
 [CursorType, propriété (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)   
 [EditMode, propriété](../../../ado/reference/ado-api/editmode-property.md)   
 [LockType, propriété (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
