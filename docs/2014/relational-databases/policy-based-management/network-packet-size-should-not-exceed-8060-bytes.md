---
title: La taille du paquet réseau ne doit pas dépasser 8060 octets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b7af9200587423dd8229ce699ed036cc4ce24f1f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303679"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>La taille du paquet réseau ne doit pas dépasser 8060 octets
  Si la valeur spécifiée pour sp_configure 'network packet size' ou si la taille du paquet réseau de tout utilisateur connecté est supérieure à 8060 octets, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des opérations d'allocation de mémoire différentes. Cela peut entraîner une augmentation de l'espace d'adressage virtuel de processus qui n'est pas réservé pour le pool de mémoires tampons.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 La taille du paquet réseau ne doit pas dépasser 8060 octets.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Article 903002 de la Base de connaissances Microsoft](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
