---
title: Récupération (fetch) de données BLOB avec IRow::GetColumns et ISequentialStream | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching BLOB data
- ISequentialStream interface
- GetColumns method
- BLOBs, fetching
ms.assetid: b57decda-b0c1-4ef6-8c81-491956de2890
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d5963bf5bd8a5d387a9809507004d1bdcb6b317
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43089598"
---
# <a name="fetching-blob-data-using-irowgetcolumns-and-isequentialstream"></a>Extraction de données BLOB à l'aide d'IRow::GetColumns et ISequentialStream
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  La fonction suivante utilise les interfaces **IRow::GetColumns** et **ISequentialStream** pour récupérer (fetch) les données volumineuses :  
  
```  
void InitializeAndExecuteCommand()  
{  
    ULONG iidx;  
    WCHAR* wCmdString=OLESTR("SELECT * FROM MyTable");  
    // Do the initialization, create the session, and set command text.  
    hr = pICommandText->Execute(NULL, IID_IRow, NULL,   
                         &cNumRows,(IUnknown **)&pIRow)))  
    //Get 1 column at a time.  
    for(ULONG i=0; i < NoOfColumns; i++)  
      GetSequentialColumn(pIRow, iidx);  
    // Do the clean up.  
}  
HRESULT GetSequentialColumn(IRow* pUnkRow, ULONG iCol)  
{  
    HRESULT hr = NOERROR;  
    ULONG cbRead = 0;  
    ULONG cbTotal = 0;  
    ULONG cColumns = 0;  
    ULONG cReads = 0;  
    ISequentialStream* pIStream = NULL;  
    WCHAR* pBuffer[kMaxBuff]; //50 chars read by ISequentialStream::Read()  
    DBCOLUMNINFO* prgInfo;  
    OLECHAR* pColNames;  
    IColumnsInfo* pIColumnsInfo;  
    DBID columnid;  
    DBCOLUMNACCESS column;  
    hr = pUnkRow->QueryInterface(IID_IColumnsInfo,   
                            (void**) &pIColumnsInfo);  
    if(FAILED(hr))  
        goto CLEANUP;  
    hr = pIColumnsInfo->GetColumnInfo(&cColumns, &prgInfo, &pColNames);  
    // Get Column ID.  
    columnid = (prgInfo + (iCol))->columnid;  
    IUnknown* pUnkStream = NULL;  
    ZeroMemory(&column, sizeof(column));  
    column.columnid = prgInfo[iCol].columnid;  
    // Ask for Iunknown interface pointer.  
    column.wType = DBTYPE_IUNKNOWN;  
    column.pData = (LPVOID*) &pUnkStream;  
  
    hr = pUnkRow->GetColumns(1, &column);  
    // Get ISequentialStream from Iunknown pointer retrieved from  
    // GetColumns().  
    hr = pUnkStream->QueryInterface(IID_ISequentialStream,   
                                   (LPVOID*) &pIStream);  
    ZeroMemory(pBuffer, kMaxBuff * sizeof(WCHAR));  
    // Read 50 chars at a time until no more data.  
    do  
    {  
        hr = pIStream->Read(pBuffer, kMaxBuff, &cbRead);  
        cbTotal = cbTotal + cbRead;  
        // Process the data.  
    } while(cbRead > 0);  
  // Do the cleanup.  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extraction de données Blob à l’aide d’IRow](http://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
  
