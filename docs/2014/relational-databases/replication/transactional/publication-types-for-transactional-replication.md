---
title: Types de publication pour la réplication transactionnelle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 88941deda14053fdf2eac1e1600b4ef02253b401
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181896"
---
# <a name="publication-types-for-transactional-replication"></a>Types de publication pour la réplication transactionnelle
  La réplication transactionnelle propose trois types de publication :  
  
|Type de publication|Description|  
|----------------------|-----------------|  
|Publication transactionnelle standard|Adaptée aux topologies dans lesquelles toutes les données de l'Abonné sont en lecture seule (la réplication transactionnelle ne l'applique pas sur l'Abonné).<br /><br /> Les publications transactionnelles standard sont créées par défaut lorsque vous utilisez Transact-SQL ou Replication Management Objects. Lorsque vous utilisez l'Assistant Nouvelle publication, elles sont créées par la sélection de l'option **Publication transactionnelle** dans la page **Type de publication** .<br /><br /> Pour plus d’informations sur la création de publications, consultez [Publier des données et des objets de base de données](../publish/publish-data-and-database-objects.md).|  
|Publication transactionnelle dans une topologie d'égal à égal|Les caractéristiques de ce type de publication sont les suivantes :<br /><br /> Chaque emplacement possède des données identiques et est à la fois un serveur de publication et un Abonné.<br /><br /> La même ligne ne peut être modifiée qu'à un seul emplacement à la fois.<br /><br /> Cette topologie convient surtout aux environnements serveur exigeant une disponibilité élevée et des possibilités d'évolutivité en lecture.<br /><br /> <br /><br /> Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication transactionnelle](transactional-replication.md)  
  
  
