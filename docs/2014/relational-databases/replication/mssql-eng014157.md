---
title: MSSQL_ENG014157 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c5b770e485621989dc39c790563d284cdab91f65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158200"
---
# <a name="mssqleng014157"></a>MSSQL_ENG014157
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14157|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'abonnement créé par l'Abonné '%1!' à la publication '%2!' a expiré et a été supprimé.|  
  
## <a name="explanation"></a>Explication  
 Un Abonné doit effectuer une synchronisation avec le serveur de publication dans les délais définis par la période de rétention de la publication. Si un Abonné n'effectue pas la synchronisation dans cette période, l'abonnement expire. Pour plus d’informations, voir [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L'abonnement doit être recréé et initialisé avant que l'Abonné ne recommence à recevoir des modifications de données :  
  
-   Pour plus d’informations sur la création d’abonnements, consultez [S’abonner à des publications](subscribe-to-publications.md).  
  
-   Pour plus d’informations sur l’initialisation des abonnements, consultez [Initialiser un abonnement](initialize-a-subscription.md).  
  
 Si la base de données d'abonnement contient des modifications qui n'ont pas été synchronisées avec le serveur de publication, vous pouvez utiliser l' [tablediff Utility](../../tools/tablediff-utility.md) pour identifier les lignes qui sont différentes dans les bases de publication et les bases d'abonnement.  
  
 Vous pouvez augmenter la période de rétention de la publication afin d'empêcher l'expiration des abonnements. Faites preuve de la plus grande vigilance lors de la définition d'une valeur élevée car plus le nombre de données et de métadonnées stockées est important, moins les performances sont bonnes. Pour plus d'informations, voir [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
