---
title: 'Tâche 9 : Configuration d’un Service de données de référence | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3a743fd3fe576296a67072762cdfa3a186584cd0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326855"
---
# <a name="task-9-configuring-a-reference-data-service"></a>Tâche 9 : Configuration d'un service de données de référence
  Dans cette tâche, vous allez configurer DQS pour utiliser un service de données de référence dans Windows Azure Marketplace. Dans la tâche suivante, vous allez configurer le domaine **Validation d'adresses** pour utiliser ce service. Au moment de l'exécution, pendant l'activité de nettoyage, DQS passe les valeurs des domaines du domaine **Validation d'adresses** au service pour le nettoyage. Consultez [Configurer DQS pour utiliser des données de référence](http://msdn.microsoft.com/library/hh213070.aspx) pour plus de détails.  
  
1.  Dans la page principale du **Client DQS**, cliquez sur **Configuration** dans le volet **Administration**.  
  
2.  Assurez-vous que l'onglet **Données de référence** est actif.  
  
3.  Dans la zone **Paramètres réseau** , entrez les valeurs appropriées dans les champs **Serveur proxy** et **Port** si vous devez utiliser un serveur proxy pour vous connecter à Internet.  
  
4.  Entrez votre **Clé de compte Windows Azure Marketplace** dans le champ **ID de compte DataMarket** .  
  
     ![Compte de Service de données Azure Data Market référence](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "compte de Service de données Azure Data Market référence")  
  
5.  Cliquez sur le bouton **Valider** en regard de la zone de texte pour valider l'ID de compte.  
  
6.  Cliquez sur **OK** dans le message de confirmation.  
  
7.  Cliquez sur **Fermer** en bas de la page pour passer à la page principale du Client DQS.  
  
## <a name="next-task"></a>Tâche suivante  
 [Tâche 10 : Configuration d’un domaine pour utiliser un service de données de référence](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
