---
title: 'Guide pratique : Créer un projet de test pour des tests unitaires de base de données SQL Server | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4b3e7ba8-b565-4689-af1a-34cc255b7c60
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a7997f7b2acf88ea358c9ddd42df5cca073a8f28
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087121"
---
# <a name="how-to-create-a-test-project-for-sql-server-database-unit-testing"></a>Procédure : créer un projet de test pour un test unitaire de base de données SQL Server
Avant de commencer à écrire des tests unitaires qui évaluent les objets de base de données, vous devez d'abord créer un projet de test. Ce projet contient des tests unitaires SQL Server, mais il pourrait en comporter d’autres types.  
  
Vous pouvez placer tous vos tests unitaires SQL Server pour un projet de base de données donné dans un seul projet de test. Toutefois, vous pouvez créer des projets de test supplémentaires selon les réponses que vous donnez aux questions suivantes :  
  
|||  
|-|-|  
|**Question**|**Décision**|  
|Les différents tests unitaires SQL Server doivent-ils accéder à différentes connexions de base de données pour l’exécution ou la validation des tests ?|Dans l'affirmative, vous avez besoin de plusieurs projets de test. Vous ne pouvez pas spécifier plus d'une connexion de base de données pour l'exécution des tests. Toutefois, vous pouvez spécifier une connexion de base de données différente pour la validation des tests.|  
|Voulez-vous déployer des projets de base de données distincts pour les différents tests unitaires ?|Dans l'affirmative, vous avez besoin de plusieurs projets de test. Un projet de test ne peut déployer qu'un seul projet de base de données.|  
  
Pour plus d’informations sur chacune de ces questions, voir [Guide pratique : Configurer l’exécution des tests unitaires SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md). Au lieu de créer plusieurs projets de test, vous pouvez également fournir votre propre implémentation Microsoft.Data.Schema.UnitTesting.DatabaseTestService [DatabaseTestService](https://msdn.microsoft.com/en-us/library/microsoft.data.schema.unittesting.databasetestservice.aspx).  
  
Trois options sont à votre disposition pour ajouter un projet de test à une solution contenant un projet de base de données :  
  
-   Ajouter un projet de test à la solution. Le projet de test contient un test unitaire standard, que vous pouvez supprimer. Ce projet ne contient aucune classe de test unitaire SQL Server, qu’il vous faudra ajouter.  
  
-   Ajouter un nouveau test unitaire SQL Server dans le menu **Test**. Lorsque vous ajoutez le test unitaire, SQL Server Data Tools crée également un projet de test si vous le demandez. Ce projet contient une classe de test unitaire SQL Server. Les classes de test unitaire SQL Server contiennent un ou plusieurs tests unitaires.  
  
-   Créer un test unitaire à partir d’une procédure stockée, d’une fonction ou d’un déclencheur dans un projet ouvert de l’Explorateur d’objets SQL Server. Lorsque vous créez le test unitaire, SQL Server Data Tools crée également un projet de test si vous le demandez. Ce projet contient une classe de test unitaire SQL Server. Les classes de test SQL Server contiennent un ou plusieurs tests unitaires.  
  
Chaque approche est décrite dans les procédures suivantes.  
  
### <a name="to-add-a-test-project-to-an-existing-solution"></a>Pour ajouter un projet de test à une solution existante  
  
1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
    La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sous **Modèles installés**, développez le nœud **SQL Server**, puis sélectionnez **Projet de base de données SQL Server**.  
  
3.  Dans **Nom**, tapez un nom de projet.  
  
### <a name="to-create-a-test-project-with-a-sql-server-unit-test-class"></a>Pour créer un projet de test avec une classe de test unitaire SQL Server  
  
-   Suivez la procédure décrite dans [Guide pratique : Créer un test unitaire SQL Server vide](../ssdt/how-to-create-an-empty-sql-server-unit-test.md) ou dans [Guide pratique : Créer des tests unitaires SQL Server pour des fonctions, des déclencheurs et des procédures stockées](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md).  
  
## <a name="see-also"></a> Voir aussi  
[Création et définition de tests unitaires SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
  
