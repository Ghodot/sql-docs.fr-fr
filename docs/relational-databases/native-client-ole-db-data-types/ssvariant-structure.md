---
title: Structure SSVARIANT | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 55e5cb798b9172b88ec8857eee449cc99c0a5f74
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43070452"
---
# <a name="ssvariant-structure"></a>Structure SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le **SSVARIANT** structure, qui est définie dans sqlncli.h, correspond à une valeur DBTYPE_SQLVARIANT dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB.  
  
 **SSVARIANT** est une union de discrimination. En fonction de la valeur du membre vt, le consommateur peut identifier le membre à lire. Les valeurs de vt correspondent aux types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ainsi, la structure **SSVARIANT** peut contenir n’importe quel type SQL Server. Pour plus d’informations sur la structure de données pour les types OLE DB standard, consultez [indicateurs de Type](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Notes  
 Quand DataTypeCompat==80, plusieurs sous-types **SSVARIANT** deviennent des chaînes. Par exemple, les valeurs de vt suivantes apparaissent dans **SSVARIANT** en tant que VT_SS_WVARSTRING :  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Lorsque DateTypeCompat == 0, ces types s'affichent sous leur forme native.  
  
 Pour plus d’informations sur SSPROP_INIT_DATATYPECOMPATIBILITY, consultez [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Le fichier sqlncli.h contient des macros d’accès de type variant qui simplifient les types de membres dans la référence à la **SSVARIANT** structure. Un exemple est V_SS_DATETIMEOFFSET, que vous pouvez utiliser comme suit :  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Pour l’ensemble complet de macros d’accès pour chaque membre de la **SSVARIANT** structure, consultez le fichier sqlncli.hi.  
  
 Le tableau suivant décrit les membres de la structure **SSVARIANT** :  
  
|Membre|Indicateur de type OLE DB|Type de données OLE DB C|Valeur vt|Commentaires|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Spécifie le type de valeur contenu dans la structure **SSVARIANT**.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Prend en charge la **tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|Prend en charge la **smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Prend en charge la **int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Prend en charge la **bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Prend en charge la **réel** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Prend en charge la **float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Prend en charge la **money** et **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Prend en charge la **bits** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Prend en charge la **uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Prend en charge la **numérique** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Prend en charge le type de données **date**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Prend en charge la **smalldatetime**, **datetime**, et **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Prend en charge la **temps** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.<br /><br /> Inclut les membres suivants :<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**octets**) spécifie l’échelle pour *tTime2Val* valeur.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Prend en charge la **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.<br /><br /> Inclut les membres suivants :<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**octets**) spécifie l’échelle pour *tsDataTimeVal* valeur.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Prend en charge la **datetimeoffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données.<br /><br /> Inclut les membres suivants :<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**octets**) spécifie l’échelle pour *tsoDateTimeOffsetVal* valeur.|  
|NCharVal|Aucun indicateur de type OLE DB correspondant.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Prend en charge la **nchar** et **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* (**court**) spécifie la longueur réelle de la chaîne vers laquelle *pwchNCharVal* points. N'inclut pas le zéro de fin.<br /><br /> *sMaxLength* (**court**) spécifie la longueur maximale de la chaîne vers laquelle *pwchNCharVal* points.<br /><br /> *pwchNCharVal* (**WCHAR** \*) pointeur vers la chaîne.<br /><br /> Membres non utilisés : *rgbReserved*, *dwReserved*, et *pwchReserved*.|  
|CharVal|Aucun indicateur de type OLE DB correspondant.|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Prend en charge la **char** et **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* (**court**) spécifie la longueur réelle de la chaîne vers laquelle *pchCharVal* points. N'inclut pas le zéro de fin.<br /><br /> *sMaxLength* (**court**) spécifie la longueur maximale de la chaîne vers laquelle *pchCharVal* points.<br /><br /> *pchCharVal* (**CHAR** \*) pointeur vers la chaîne.<br /><br /> Membres non utilisés :<br /><br /> *rgbReserved*, *dwReserved*, et *pwchReserved*.|  
|BinaryVal|Aucun indicateur de type OLE DB correspondant.|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Prend en charge la **binaire** et **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* (**court**) indique la longueur réelle des données vers lesquelles *prgbBinaryVal* points.<br /><br /> *sMaxLength* (**court**) spécifie la longueur maximale des données vers lesquelles *prgbBinaryVal* points.<br /><br /> *prgbBinaryVal* (**octets** \*) pointeur vers les données binaires.<br /><br /> Membre non utilisé : *dwReserved*.|  
|UnknownType|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
