---
title: Objet SqlXmlAdapter (Classes managées de SQLXML) | Microsoft Docs
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
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 192f356052289725043ae2b3dc748931aedb11fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331409"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>Objet SqlXmlAdapter (classes managées SQLXML)
  Cet objet fournit des méthodes qui facilitent l'interaction avec le dataset dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Pour obtenir un exemple fonctionnel, consultez [l’accès à des fonctionnalités de SQLXML dans l’environnement .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 L’objet SqlXmlAdapter prend en charge ces méthodes :  
  
 void Fill (DataSet ds)  
 Remplit le dataset dans le .NET Framework avec les données XML extraites de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 mise à jour void (DataSet ds)  
 Applique des mises à jour aux enregistrements dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir des données dans le dataset.  
  
 L’objet SqlXmlAdapter prend en charge ces constructeurs :  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlXmlCommand &#40;Classes managées SQLXML&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [Objet SqlXmlParameter &#40;Classes managées SQLXML&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
