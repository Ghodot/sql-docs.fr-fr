---
title: CPU Threshold Exceeded, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8fefba60524cb8aec2e3c2328d965747864f57d4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43064725"
---
# <a name="cpu-threshold-exceeded-event-class"></a>Classe d'événements CPU Threshold Exceeded
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La classe d'événements CPU Threshold Exceeded indique que Resource Governor détecte une requête qui dépasse le seuil de l'UC spécifié pour REQUEST_MAX_CPU_TIME_SEC.  
  
> [!NOTE]  
>  L'intervalle de détection pour cet événement est cinq secondes. Il est garanti qu'un événement sera généré si une requête dépasse la limite spécifiée d'au moins cinq secondes. Toutefois, si une requête dépasse le seuil spécifié de moins de cinq secondes, sa détection peut être manquée selon le moment d'exécution de la requête et l'heure de la dernière analyse de détection.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>Colonnes de données CPU Threshold Exceeded  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|Unité centrale|**Int**|Utilisation de l'UC en millisecondes.|18|Oui|  
|EventClass|**Int**|214|27|non|  
|EventSubClass|**Int**|Violation de la limite de l'UC.|21|Oui|  
|GroupID|**Int**|ID de groupe où la violation s'est produite.|66|Oui|  
|OwnerID|**Int**|SPID du processus qui a provoqué la violation.|58|Oui|  
|SPID|**Int**|ID du processus serveur qui déclenche cet événement.<br /><br /> Remarque : il peut être différent du SPID de l’utilisateur réel si un thread système valide l’utilisation de l’UC comme une tâche en arrière-plan.|12|Oui|  
|StartTime|**datetime**|Heure de déclenchement de cet événement.|14|Oui|  
  
## <a name="see-also"></a> Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
