---
title: Résoudre les problèmes de performances courants avec des index de hachage mémoire optimisés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1954a997-7585-4713-81fd-76d429b8d095
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 28fea2aed82e86d58264311914a341fb6ecca4fc
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396297"
---
# <a name="troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes"></a>Résoudre les problèmes de performance courants avec les index de hachage mémoire optimisés
  Cette rubrique traite du dépannage et des solutions de contournement des problèmes couramment rencontrés avec les index de hachage.  
  
## <a name="search-requires-a-subset-of-hash-index-key-columns"></a>La recherche nécessite un sous-ensemble de colonnes clés d'index de hachage  
 **Problème :** index de hachage exigent des valeurs pour toutes les colonnes clés d’index afin de calculer la valeur de hachage et rechercher les lignes correspondantes dans la table de hachage. Par conséquent, si une requête contient des prédicats d'égalité pour un seul sous-ensemble de clés d'index dans la clause WHERE, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peut pas utiliser la recherche d'index pour trouver les lignes correspondant aux prédicats dans la clause WHERE.  
  
 Par opposition, les index triés comme les index non cluster sur disque et les index non cluster mémoire optimisés, prennent en charge la recherche d'index sur un sous-ensemble de colonnes clés d'index, tant qu'il s'agit des premières colonnes de l'index.  
  
 **Symptôme :** cela entraîne une dégradation des performances, en tant que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit exécuter des analyses de tables complètes plutôt que d’une recherche d’index, ce qui est généralement une opération plus rapide.  
  
 **Comment résoudre les problèmes :** en dehors de la dégradation des performances, l’inspection des plans de requête indiquera une analyse au lieu d’une recherche d’index. Si la requête est relativement simple, l'inspection du texte de la requête et de la définition d'index montrera également si la recherche nécessite un sous-ensemble de colonnes clés d'index.  
  
 Prenons l'exemple de la table et de la requête suivantes :  
  
```tsql  
CREATE TABLE [dbo].[od]  
(  
     o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
     CONSTRAINT PK_od PRIMARY KEY NONCLUSTERED HASH (o_id, od_id) WITH (BUCKET_COUNT = 10000)  
)  
WITH (MEMORY_OPTIMIZED = ON)  
  
 SELECT p_id  
 FROM dbo.od  
 WHERE o_id=1  
```  
  
 La table a un index de hachage sur les deux colonnes (o_id, od_id), tandis que la requête a un prédicat d'égalité sur (o_id). Étant donné que la requête possède des prédicats d'égalité uniquement sur un sous-ensemble de colonnes clés d'index, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peut pas effectuer d'opération de recherche d'index à l'aide de PK_od ; à la place, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit revenir à une analyse complète d'index.  
  
 **Solutions de contournement :** un certain nombre de solutions de contournement possibles. Exemple :  
  
-   Recréez l'index en tant que type non cluster au lieu d'un hachage non cluster. L'index mémoire optimisé non cluster est trié, et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut effectuer une recherche d'index sur les colonnes clés d'index. La définition de clé primaire de l'exemple serait `constraint PK_od primary key nonclustered`.  
  
-   Modifiez la clé d'index actuelle pour correspondre aux colonnes dans la clause WHERE.  
  
-   Ajoutez un nouvel index de hachage qui correspond aux colonnes dans la clause WHERE de la requête. Dans l'exemple, la définition de table s'apparenterait à ce qui suit :  
  
    ```tsql  
    CREATE TABLE dbo.od  
     ( o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
  
     CONSTRAINT PK_od PRIMARY KEY   
     NONCLUSTERED HASH (o_id,od_id) WITH (BUCKET_COUNT=10000),  
  
     INDEX ix_o_id NONCLUSTERED HASH (o_id) WITH (BUCKET_COUNT=10000)  
  
     ) WITH (MEMORY_OPTIMIZED=ON)  
    ```  
  
 Notez qu'un index de hachage mémoire optimisé ne fonctionne pas de façon optimale s'il existe de nombreuses lignes dupliquées pour une valeur de clé d'index donnée : dans l'exemple, si le nombre de valeurs uniques pour la colonne o_id est beaucoup plus petit que le nombre de lignes dans la table, il n'est pas conseillé d'ajouter un index sur (o_id) ; à la place, changer le type de l'index PK_od en le modifiant d'index de hachage en index non cluster est la meilleure solution. Pour plus d’informations, consultez [déterminer le nombre de compartiments Correct pour les index de hachage](../relational-databases/indexes/indexes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Index sur des tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
