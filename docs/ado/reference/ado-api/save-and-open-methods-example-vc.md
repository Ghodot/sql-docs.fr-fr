---
title: Enregistrez et ouvrez l’exemple de méthodes (VC ++) | Documents Microsoft
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
- Save method [ADO], VC++ example
- Open method [ADO]
ms.assetid: 334ae655-8cac-48e6-8d00-1d28f3436e1e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 870ae7f5776b601b312d799b643c09bd589dc26b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281328"
---
# <a name="save-and-open-methods-example-vc"></a>Enregistrez et ouvrez l’exemple de méthodes (VC ++)
Ces trois exemples montrent comment les [enregistrer](../../../ado/reference/ado-api/save-method.md) et **ouvrir** méthodes peuvent être utilisés ensemble.  
  
 Supposons que vous allez en voyage d’entreprise et que vous souhaitez prendre le long d’une table à partir d’une base de données. Avant de commencer, vous accéder aux données en tant qu’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) et enregistrez-le dans un formulaire transportable. Lorsque vous arrivez à destination, vous accédez le **Recordset** comme une variable locale, déconnecté **Recordset**. Vous apportez des modifications à la **Recordset**, puis enregistrez-le à nouveau. Enfin, lorsque vous revenez accueil, vous reconnectez à la base de données et mettre à jour avec les modifications apportées sur la route.  
  
```  
// BeginSaveCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
#include <io.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
bool FileExists();  
void SaveX1();  
void SaveX2();  
void SaveX3();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   // If File exists in the specified directory, then display error  
   if (!FileExists()) {  
      SaveX1();  
      SaveX2();  
      SaveX3();  
   }  
  
   ::CoUninitialize();  
}  
  
// First, access and save the authors table.  
void SaveX1() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstAuthors = NULL;  
  
   // Definitions of other variables  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source' ; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      pRstAuthors->Open("SELECT * FROM authors",strCnn, adOpenDynamic,   
         adLockBatchOptimistic, adCmdText);  
  
      // For sake of illustration, save the Recordset to a diskette in XML format.  
      pRstAuthors->Save("c:\\pubs.xml", adPersistXML);  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors, if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
}  
  
// At this point, you have arrived at your destination.  
// You will access the authors table as a local, disconnected Recordset.   
// Don't forget you must have the MSPersist provider on the machine you   
// are using in order to access the saved file, c:\pubs.xml.  
void SaveX2() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstAuthors = NULL;  
  
   try {  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      // For sake of illustration, we specify all parameters.  
      pRstAuthors->Open("c:\\pubs.xml", "Provider='MSPersist';", adOpenForwardOnly, adLockBatchOptimistic, adCmdFile);  
  
      // Now you have a local, disconnected Recordset.  
      // (In this example, changes will not be saved).  
      pRstAuthors->Find("au_lname = 'Carson'", NULL, adSearchForward);  
      if (pRstAuthors->EndOfFile) {  
         printf("Name not found ...\n");  
         pRstAuthors->Close();  
         return;  
      }  
      pRstAuthors->GetFields()->GetItem("City")->PutValue("Chicago");  
      pRstAuthors->Update();  
  
      // Save changes in ADTG format this time, purely for sake of  illustration.   
      // Note that the previous version is still on the diskette as c:\pubs.xml.  
      pRstAuthors->Save("c:\\pubs.adtg", adPersistADTG);  
   }  
   catch(_com_error &e){  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
}  
  
// Now update the database with changes.  
void SaveX3() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers.  Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstAuthors = NULL;  
   _ConnectionPtr pCnn = NULL;  
  
   // Definitions of other variables  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      TESTHR(pCnn.CreateInstance(__uuidof(Connection)));  
  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      // If there is no ActiveConnection, you can open with defaults.  
      pRstAuthors->Open("c:\\pubs.adtg", "Provider=MSPersist;",  
         adOpenForwardOnly, adLockBatchOptimistic, adCmdFile);  
  
      // Connect to the database, associate the Recordset with the connection,   
      // then update the database table with the changed Recordset.  
      pCnn->Open(strCnn, "", "", NULL);  
  
      pRstAuthors->PutActiveConnection(_variant_t((IDispatch *) pCnn));  
      pRstAuthors->UpdateBatch(adAffectAll);  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      // Pass a connection pointer accessed from the Recordset.  
      _variant_t vtConnect = pRstAuthors->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
      case VT_BSTR:  
         PrintComError(e);  
         break;  
      case VT_DISPATCH:  
         PrintProviderError(vtConnect);  
         break;  
      default:  
         printf("Errors occured.");  
         break;  
      }  
   }  
  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
   if (pCnn)  
      if (pCnn->State == adStateOpen)  
         pCnn->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print COM errors.   
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
  
bool FileExists() {  
   struct _finddata_t xml_file;  
   long hFile;  
  
   if( (hFile = _findfirst("c:\\pubs.xml", &xml_file )) != -1L)  
   {  
      printf( "File already exists!\n" );  
      return(true);  
   }  
   else  
      return (false);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Open (méthode) (jeu d’enregistrements ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
