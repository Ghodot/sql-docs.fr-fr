---
title: catalog.add_execution_worker (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: dbf3db6560e4a32969abd5162479cb41ca6c40e9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38063938"
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>catalog.add_execution_worker (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Ajoute un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker à une instance d’exécution dans Scale Out.

## <a name="syntax"></a>Syntaxe

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Arguments
[ @execution_id = ] *execution_id*  
 Identificateur unique de l'instance d'exécution. *execution_id* est de type **bigint**.  
 
[@workeragent_id = ] *workeragent_id*  
ID d’agent de Worker d’un Scale Out Worker. *workeragent_id* est de type **uniqueIdentifier**.

## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  

## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
 
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
 
- L’utilisateur n’a pas les autorisations appropriées.

- L’identificateur d’exécution n’est pas valide.

- L’ID d’agent de Worker n’est pas valide.

- L’exécution n’a pas lieu dans Scale Out.

## <a name="see-also"></a> Voir aussi
[Exécuter des packages dans Scale Out](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

