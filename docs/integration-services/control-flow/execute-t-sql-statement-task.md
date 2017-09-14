---
title: "Exécuter la tâche de l’instruction T-SQL | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94fd411504f1781041e8d36f3f1cf41f6082aa09
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="execute-t-sql-statement-task"></a>Tâche Exécuter l'instruction T-SQL
  La tâche Exécuter l'instruction T-SQL exécute des instructions Transact-SQL. Pour plus d’informations, consultez [Référence Transact-SQL &#40;moteur de base de données&#41;](../../t-sql/transact-sql-reference-database-engine.md) et [Requêtes Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-queries.md).  
  
 Cette tâche est similaire à la tâche d'exécution SQL. Toutefois, la tâche Exécuter l'instruction T-SQL ne prend en charge que la version Transact-SQL du langage SQL et vous ne pouvez pas recourir à cette tâche pour exécuter des instructions sur les serveurs qui utilisent d'autres dialectes du langage SQL. Pour exécuter des requêtes paramétrables, enregistrer les résultats des requêtes dans des variables ou utiliser des expressions de propriété, vous devez utiliser la tâche d'exécution SQL et non pas la tâche Exécuter l'instruction T-SQL. Pour plus d'informations, consultez [Execute SQL Task](../../integration-services/control-flow/execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Configuration de la tâche Exécuter l'instruction T-SQL  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Cette tâche se trouve dans la section **Tâches du plan de maintenance** de la **boîte à outils** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Exécuter la tâche de l’instruction T-SQL &#40;Plan de maintenance&#41;](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)   
 [FUSIONNER des Packages Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)  
  
  