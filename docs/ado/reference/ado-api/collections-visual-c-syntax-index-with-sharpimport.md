---
title: 'Collections (Index de la syntaxe Visual C++ avec #import) | Documents Microsoft'
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'syntax indexes [ADO], ADO for Visual C++ syntax with #import'
- 'collections [ADO], ADO for Visual C++ syntax with #import'
- 'ADO for Visual C++ syntax with #import [ADO]'
- '#import [ADO]'
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 093e3933796d490f2dc40d8af493dc639fdb19a3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="collections-visual-c-syntax-index-with-import"></a>Collections (Index de la syntaxe Visual C++ avec #import)
Il est utile de savoir que les collections héritent certaines méthodes et propriétés communes.  
  
 Toutes les collections héritent la **nombre** propriété et **Actualiser** (méthode) et toutes les collections ajoutent la **élément** propriété. Le **erreurs** collection ajoute le **clair** (méthode). Le **paramètres** hérite de la collection le **Append** et **supprimer** méthodes, tandis que la **champs** collection ajoute la **Append**, **supprimer**, et **mise à jour** méthodes.  
  
## <a name="properties-collection"></a>Collection Properties  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="errors-collection"></a>Collection d’erreurs  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Clear( );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="parameters-collection"></a>Collection Parameters  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Append( IDispatch * Object );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="fields-collection"></a>Collection Fields  
  
### <a name="methods"></a>Méthodes  
  
```  
HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t & FieldValue = vtMissing );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
HRESULT Update( );  
```  
  
### <a name="properties"></a>Propriétés  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Collection d’erreurs (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Collection de champs (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Collection de paramètres (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)