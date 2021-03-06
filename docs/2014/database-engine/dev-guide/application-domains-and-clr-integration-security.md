---
title: Domaines d’application et de sécurité de l’intégration CLR | Microsoft Docs
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
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
caps.latest.revision: 14
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab43d57679dca1f241b6deb3d955681c443c7809
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215619"
---
# <a name="application-domains-and-clr-integration-security"></a>Domaines d'application et sécurité de l'intégration du CLR
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge des assemblys qui appartiennent au même propriétaire dans le même domaine d'application. En raison d'un jeu d'assemblys s'exécutant dans le même domaine d'application, les assemblys sont capables de se découvrir les uns les autres au moment de l'exécution à l'aide d'interfaces de programmation d'applications de réflexion du .NET Framework ou par d'autres moyens, et ils sont capables d'y faire des appels en mode de liaison tardive. De tels appels se produisant sur des assemblys qui appartiennent au même propriétaire, aucune autorisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est vérifiée pour ces appels. Le schéma de positionnement des assemblys dans les domaines d'application est principalement conçu pour répondre à des objectifs en matière d'évolutivité, de sécurité et d'isolation. Il est susceptible d'être modifié dans des versions ultérieures. Pour cette raison, il est possible que la recherche d'assemblys dans le même domaine d'application par le biais de mécanismes à liaison tardive s'avère infructueuse.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’intégration du CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
