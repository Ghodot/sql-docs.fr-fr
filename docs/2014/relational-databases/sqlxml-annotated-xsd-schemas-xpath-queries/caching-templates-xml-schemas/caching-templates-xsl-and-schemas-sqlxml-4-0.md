---
title: La mise en cache des modèles, XSL et schémas (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 279e26691ab40104bc4e77a871110b0710fb2a4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198869"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Mise en cache des modèles, XSL et schémas (SQLXML 4.0)
  Pour améliorer les performances, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 prend en charge la mise en cache des modèles, des fichiers XSL et des schémas.  
  
 Tous les schémas, modèles et fichiers XSL (sauf les fichiers provenant d'un emplacement http:// ou ftp://) sont mis en cache. Les fichiers mis en cache demeurent en mémoire pendant que le processus est en cours d'exécution. Lorsque le processus s'arrête, la totalité du cache est perdue. Par conséquent, si vous exécutez un processus par requête, l'avantage de la mise en cache peut ne pas être perceptible.  
  
 Les rubriques de cette section fournissent plus d'informations sur la mise en cache.  
  
## <a name="in-this-section"></a>Dans cette section  
 [La mise en cache de modèle &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)  
 Décrit et fournit une clé de Registre pour la mise en cache des modèles.  
  
 [La mise en cache XSL &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
 Décrit et fournit une clé de Registre pour la mise en cache des fichiers XSL.  
  
 [La mise en cache de schéma &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
 Explique les installations SQLXML côte à côte en rapport avec la mise en cache de schémas, et fournit les clés de Registre pour la mise en cache des schémas.  
  
  
