---
title: "&#201;diteur de t&#226;che de transfert d&#39;objets SQL (page Objets) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transfersqlserverobjects.objects.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de transfert d'objets SQL"
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# &#201;diteur de t&#226;che de transfert d&#39;objets SQL (page Objets)
  Utilisez la page **Objets** de la boîte de dialogue **Éditeur de tâche de transfert d’objets SQL** pour spécifier les propriétés de copie d’un ou plusieurs objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une autre. Les tables, les vues, les procédures stockées et les fonctions définies par l’utilisateur représentent quelques exemples des objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous pouvez copier. Pour plus d'informations sur cette tâche, consultez [Transfer SQL Server Objects Task](../../integration-services/control-flow/transfer-sql-server-objects-task.md).  
  
> [!NOTE]  
>  L’utilisateur qui crée la tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit disposer des autorisations suffisantes sur les objets du serveur source pour les sélectionner pour la copie, ainsi que de l’autorisation d’accéder à la base de données du serveur de destination où les objets seront transférés.  
  
## Options statiques  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO (SQL Server Management Objects) dans la liste, ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur source.  
  
 **SourceDatabase**  
 Sélectionnez une base de données sur le serveur source à partir duquel les objets seront copiés.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste, ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur de destination.  
  
 **DestinationDatabase**  
 Sélectionnez une base de données sur le serveur de destination dans lequel les objets seront copiés.  
  
 **DropObjectsFirst**  
 Déterminez si les objets sélectionnés sont d'abord supprimés du serveur de destination avant la copie.  
  
 **IncludeExtendedProperties**  
 Déterminez si les propriétés étendues sont incluses lorsque les objets sont copiés du serveur source au serveur de destination.  
  
 **CopyData**  
 Déterminez si les données sont incluses lorsque les objets sont copiés du serveur source au serveur de destination.  
  
 **ExistingData**  
 Spécifiez comment les données seront copiées sur le serveur de destination. Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Remplacer**|Les données du serveur de destination seront remplacées.|  
|**Append**|Les données copiées à partir du serveur source seront ajoutées aux données existantes sur le serveur de destination.|  
  
> [!NOTE]  
>  L’option **ExistingData** est disponible uniquement quand **CopyData** a la valeur **True**.  
  
 **CopySchema**  
 Déterminez si le schéma est copié pendant la tâche de transfert d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  **CopySchema** est disponible uniquement pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **UseCollation**  
 Déterminez si le transfert des objets doit inclure le classement spécifié sur le serveur source.  
  
 **IncludeDependentObjects**  
 Déterminez si la copie des objets sélectionnés inclut en cascade les autres objets qui dépendent de ces objets sélectionnés pour la copie.  
  
 **CopyAllObjects**  
 Déterminez si la tâche copie tous les objets de la base de données source spécifiée ou uniquement les objets sélectionnés.  Si cette option a la valeur False, vous pouvez sélectionner les objets à transférer et afficher les options dynamiques dans la section **CopyAllObjects**.  
  
 **ObjectsToCopy**  
 Développez **ObjectsToCopy** pour spécifier les objets qui doivent être copiés de la base de données source dans la base de données de destination.  
  
> [!NOTE]  
>  **ObjectsToCopy** est disponible uniquement quand **CopyAllObjects** a la valeur **False**.  
  
 Les options de copie des types d’objets suivants sont prises en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
 Assemblys  
  
 Fonctions de partition  
  
 Schémas de partition  
  
 Schémas  
  
 Fonctions d'agrégation définies par l'utilisateur  
  
 Types définis par l'utilisateur  
  
 Collections de schémas XML  
  
 **CopyDatabaseUsers**  
 Déterminez si les utilisateurs de la base de données doivent être inclus dans le transfert.  
  
 **CopyDatabaseRoles**  
 Déterminez si les rôles de la base de données doivent être inclus dans le transfert.  
  
 **CopySqlServerLogins**  
 Déterminez si les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être incluses dans le transfert.  
  
 **CopyObjectLevelPermissions**  
 Déterminez si les autorisations au niveau objet doivent être incluses dans le transfert.  
  
 **CopyIndexes**  
 Déterminez si les index doivent être inclus dans le transfert.  
  
 **CopyTriggers**  
 Déterminez si les déclencheurs doivent être inclus dans le transfert.  
  
 **CopyFullTextIndexes**  
 Déterminez si les index de texte intégral doivent être inclus dans le transfert.  
  
 **CopyPrimaryKeys**  
 Déterminez si les clés primaires doivent être incluses dans le transfert.  
  
 **CopyForeignKeys**  
 Déterminez si les clés étrangères doivent être incluses dans le transfert.  
  
 **GenerateScriptsInUnicode**  
 Déterminez si les scripts de transfert créés sont au format Unicode.  
  
## Options dynamiques  
  
### CopyAllObjects = False  
 **CopyAllTables**  
 Déterminez si la tâche copie toutes les tables de la base de données source spécifiée ou uniquement les tables sélectionnées.  
  
 **TablesList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner des tables**.  
  
 **CopyAllViews**  
 Déterminez si la tâche copie toutes les vues de la base de données source spécifiée ou uniquement les vues sélectionnées.  
  
 **ViewsList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner des vues**.  
  
 **CopyAllStoredProcedures**  
 Déterminez si la tâche copie toutes les procédures stockées définies par l'utilisateur dans la base de données source spécifiée ou uniquement celles sélectionnées.  
  
 **StoredProceduresList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner des procédures stockées**.  
  
 **CopyAllUserDefinedFunctions**  
 Déterminez si la tâche copie toutes les fonctions définies par l'utilisateur dans la base de données source spécifiée ou uniquement celles sélectionnées.  
  
 **UserDefinedFunctionsList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les fonctions définies par l’utilisateur**.  
  
 **CopyAllDefaults**  
 Déterminez si la tâche copie toutes les valeurs par défaut de la base de données source spécifiée ou uniquement les valeurs par défaut sélectionnées.  
  
 **DefaultsList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les valeurs par défaut**.  
  
 **CopyAllUserDefinedDataTypes**  
 Déterminez si la tâche copie tous les types de données définis par l'utilisateur dans la base de données source spécifiée ou uniquement ceux sélectionnés.  
  
 **UserDefinedDataTypesList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les types de données définis par l’utilisateur**.  
  
 **CopyAllPartitionFunctions**  
 Déterminez si la tâche copie toutes les fonctions de partition définies par l'utilisateur dans la base de données source spécifiée ou uniquement celles sélectionnées. Cette option est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **PartitionFunctionsList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les fonctions de partition**.  
  
 **CopyAllPartitionSchemes**  
 Déterminez si la tâche copie tous les schémas de partition de la base de données source spécifiée ou uniquement ceux sélectionnés. Cette option est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **PartitionSchemesList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les schémas de partition**.  
  
 **CopyAllSchemas**  
 Déterminez si la tâche copie tous les schémas de la base de données source spécifiée ou uniquement les schémas sélectionnés. Cette option est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **SchemasList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les schémas**.  
  
 **CopyAllSqlAssemblies**  
 Déterminez si la tâche copie tous les assemblys SQL de la base de données source spécifiée ou uniquement les assemblys SQL sélectionnés. Cette option est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **SqlAssembliesList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les assemblys SQL**.  
  
 **CopyAllUserDefinedAggregates**  
 Déterminez si la tâche copie toutes les fonctions d'agrégation définies par l'utilisateur dans la base de données source spécifiée ou uniquement celles sélectionnées. Cette option est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **UserDefinedAggregatesList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les fonctions d’agrégation définies par l’utilisateur**.  
  
 **CopyAllUserDefinedTypes**  
 Déterminez si la tâche copie tous les types définis par l'utilisateur dans la base de données source spécifiée ou uniquement ceux sélectionnés. Cette option est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **UserDefinedTypes**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les types définis par l’utilisateur**.  
  
 **CopyAllXmlSchemaCollections**  
 Déterminez si la tâche copie toutes les collections de schémas XML de la base de données source spécifiée ou uniquement celles sélectionnées. Cette option est prise en charge uniquement sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **XmlSchemaCollectionsList**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner les collections du schéma XML**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert d’objets SQL Server &#40;page Général&#41;](../../integration-services/control-flow/transfer-sql-server-objects-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Formats de données pour l’importation ou l’exportation en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  