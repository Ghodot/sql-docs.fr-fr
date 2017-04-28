---
title: "Table temporaire et variable de table plus rapides &#224; l’aide de l’optimisation en m&#233;moire | Microsoft Docs"
ms.custom: ""
ms.date: "01/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38512a22-7e63-436f-9c13-dde7cf5c2202
caps.latest.revision: 20
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 19
---
# Table temporaire et variable de table plus rapides &#224; l’aide de l’optimisation en m&#233;moire
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  
Si vous utilisez des tables temporaires, des variables de table ou des paramètres table, envisagez de les convertir pour tirer parti des tables optimisées en mémoire et des variables de table afin d’améliorer les performances. Les modifications de code sont généralement minimes.  
  
Cet article décrit :  
  
- Scénarios en faveur d’une conversion en mémoire.  
- Étapes techniques pour implémenter les conversions en mémoire.  
- Configuration requise avant la conversion en mémoire.  
- Exemple de code qui met en évidence les avantages en matière de performances de l’optimisation en mémoire
  
  
## A. Principes de base des variables de table optimisées en mémoire  
  
Une variable de table optimisée en mémoire offre une grande efficacité en utilisant les mêmes algorithme et structures de données optimisés en mémoire que ceux utilisés par les tables optimisées en mémoire. L’efficacité est optimale quand la variable de table est accessible à partir d’un module compilé en mode natif.  
  
  
Une variable de table optimisée en mémoire :  
  
- Est stockée uniquement en mémoire et n’a aucun composant sur le disque.  
- N’implique aucune activité d’E/S.  
- N’implique aucune contention ni utilisation de tempdb.  
- Peut être passée dans une procédure stockée comme un paramètre table.  
- Doit avoir au moins un index, de hachage ou non cluster.  
  - Pour un index de hachage, le nombre de compartiments doit idéalement être égal à 1 à 2 fois le nombre de clés d’index uniques attendu, mais une surestimation du nombre de compartiments convient habituellement (jusqu’à 10 fois). Pour plus d’informations, consultez [Index pour les tables optimisées en mémoire](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  

  
  
#### Types d'objets  
  
OLTP en mémoire fournit les objets suivants qui peuvent être utilisés pour l’optimisation en mémoire des tables temporaires et des variables de table :  
  
- Tables optimisées en mémoire  
  - Durabilité = SCHEMA_ONLY  
- Variables de table optimisées en mémoire  
  - Déclaration en deux étapes (plutôt qu’inline) :  
    - `CREATE TYPE my_type AS TABLE ...;` , puis  
    - `DECLARE @mytablevariable my_type;`.  
  
  
## B. Scénario : Remplacer la table temporaire globale &#x23;&#x23;tempGlobalB  
  
Supposons que vous disposez de la table temporaire globale suivante.  
  
  
  
  
    CREATE TABLE ##tempGlobalB  
    (  
        Column1   INT   NOT NULL ,  
        Column2   NVARCHAR(4000)  
    );  
  
  
  
  
Envisagez de remplacer la table temporaire globale par la table optimisée en mémoire suivante qui affiche DURABILITY = SCHEMA_ONLY.  
  
  
  
  
    CREATE TABLE dbo.soGlobalB  
    (  
        Column1   INT   NOT NULL   INDEX ix1 NONCLUSTERED,  
        Column2   NVARCHAR(4000)  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
            DURABILITY        = SCHEMA_ONLY);  
  
  
  
  
#### B.1 Étapes  
  
La conversion de la table temporaire globale en SCHEMA_ONLY s’effectue comme suit :  
  
  
1. Créez la table **dbo.soGlobalB** unique comme n’importe quelle table sur disque classique.  
2. Dans votre code Transact-SQL, supprimez la création de la table **&#x23;&#x23;tempGlobalB**.  
3. Dans votre code T-SQL, remplacez toutes les mentions de **&#x23;&#x23;tempGlobalB** par **dbo.soGlobalB**.  
  
  
## C. Scénario : Remplacer la table temporaire de session &#x23;tempSessionC  
  
Les tâches de préparation pour remplacer une table temporaire de session impliquent plus de code T-SQL que pour le scénario de table temporaire globale précédent. Heureusement, le code T-SQL supplémentaire n’implique pas plus de travail pour effectuer la conversion.  
  
Supposons que vous disposez de la table temporaire de session suivante.  
  
  
  
  
    CREATE TABLE #tempSessionC  
    (  
        Column1   INT   NOT NULL ,  
        Column2   NVARCHAR(4000)  
    );  
  
  
  
  
Tout d’abord, créez la fonction table suivante pour filtrer sur **@@spid**. La fonction sera utilisable par toutes les tables SCHEMA_ONLY que vous convertissez à partir des tables temporaires de session.  
  
  
  
  
    CREATE FUNCTION dbo.fn_SpidFilter(@SpidFilter smallint)  
        RETURNS TABLE  
        WITH SCHEMABINDING , NATIVE_COMPILATION  
    AS  
        RETURN  
            SELECT 1 AS fn_SpidFilter  
                WHERE @SpidFilter = @@spid;  
  
  
  
  
Ensuite, créez la table SCHEMA_ONLY, ainsi qu’une stratégie de sécurité sur la table.  
  
  
Notez que chaque table optimisée en mémoire doit avoir au moins un index.  
  
- Pour la table dbo.soSessionC, un index de hachage peut être préférable, si nous calculons la valeur BUCKET_COUNT appropriée. Toutefois, pour cet exemple, nous simplifions l’opération avec un index non cluster.  
  
  
  
  
    CREATE TABLE dbo.soSessionC  
    (  
        Column1     INT         NOT NULL,  
        Column2     NVARCHAR(4000)  NULL,  
  
        SpidFilter  SMALLINT    NOT NULL   DEFAULT (@@spid),  
  
        INDEX ix_SpidFiler NONCLUSTERED (SpidFilter),  
        --INDEX ix_SpidFilter HASH  
        --    (SpidFilter) WITH (BUCKET_COUNT = 64),  
          
        CONSTRAINT CHK_soSessionC_SpidFilter  
            CHECK ( SpidFilter = @@spid ),  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
             DURABILITY = SCHEMA_ONLY);  
    go  
  
  
    CREATE SECURITY POLICY dbo.soSessionC_SpidFilter_Policy  
        ADD FILTER PREDICATE dbo.fn_SpidFilter(SpidFilter)  
        ON dbo.soSessionC  
        WITH (STATE = ON);  
    go  
  
  
  
  
Troisièmement, dans votre code T-SQL général :  
  
1. Effacez toute instruction CREATE TABLE pour l’ancienne table temporaire de session.  
2. Remplacez l’ancien nom de table par le nouveau nom :  
  - _Ancien :_ &#x23;tempSessionC  
  - _Nouveau :_ dbo.soSessionC  
  
  
  
## D. Scénario : Une variable de table peut afficher MEMORY_OPTIMIZED=ON  
  
  
Une variable de table classique représente une table dans la base de données tempdb. Pour des performances beaucoup plus rapides, vous pouvez optimiser votre variable de table en mémoire.  
  
Voici le code T-SQL pour une variable de table classique. Son étendue s’arrête quand le lot ou la session se termine.  
  
  
  
  
    DECLARE @tvTableD TABLE  
        ( Column1   INT   NOT NULL ,  
          Column2   CHAR(10) );  
  
  
  
  
#### D.1 Convertir inline en explicite  
  
La syntaxe précédente permet de créer la variable de table *inline*. La syntaxe inline ne prend pas en charge l’optimisation en mémoire. C’est pourquoi nous allons convertir la syntaxe inline en syntaxe explicite pour TYPE.  
  
*Étendue :* la définition TYPE créée par le premier lot délimité par une commande go est conservée même après l’arrêt et le redémarrage du serveur. Toutefois, après le premier délimiteur go, la table déclarée @tvTableC est conservée uniquement jusqu’à ce que le délimiteur go suivant soit atteint et la fin du lot.  
  
  
  
  
    CREATE TYPE dbo.typeTableD  
        AS TABLE  
        (  
            Column1  INT   NOT NULL ,  
            Column2  CHAR(10)  
        );  
    go  
          
    SET NoCount ON;  
    DECLARE @tvTableD dbo.typeTableD  
    ;  
    INSERT INTO @tvTableD (Column1) values (1), (2)  
    ;  
    SELECT * from @tvTableD;  
    go  
  
  
  
  
#### D.2 Convertir une table sur disque explicite en table optimisée en mémoire  
  
Une variable de table optimisée en mémoire ne se trouve pas dans tempdb. L’optimisation en mémoire entraîne une augmentation de la vitesse, qui est souvent 10 fois supérieure ou plus.  
  
La conversion en table optimisée en mémoire est effectuée en une seule étape. Améliorez la création TYPE explicite pour obtenir le résultat suivant, qui ajoute :  
  
- Un index. Là encore, chaque table optimisée en mémoire doit avoir au moins un index.  
- MEMORY_OPTIMIZED = ON.  
  
  
  
  
    CREATE TYPE dbo.typeTableD  
        AS TABLE  
        (  
            Column1  INT   NOT NULL   INDEX ix1,  
            Column2  CHAR(10)  
        )  
        WITH  
            (MEMORY_OPTIMIZED = ON);  
  
  
  
  
Opération terminée.  
  
  
## E. Groupe de fichiers requis pour SQL Server  
  
Dans Microsoft SQL Server, pour utiliser les fonctionnalités optimisées en mémoire, votre base de données doit avoir un groupe de fichiers qui est déclaré avec **MEMORY_OPTIMIZED_DATA**.  
  
- La base de données SQL Azure ne nécessite pas la création de ce groupe de fichiers.  
  
  
*Condition préalable :* le code Transact-SQL suivant pour un groupe de fichiers est requis pour les exemples de code T-SQL longs dans les sections ultérieures de cet article.  
  
1. Vous devez utiliser SSMS.exe ou un autre outil qui peut envoyer du code T-SQL.  
2. Collez l’exemple de code T-SQL de groupe de fichiers dans SSMS.  
3. Modifiez le code T-SQL pour changer ses noms et chemins d’accès aux répertoires spécifiques à votre convenance.  
  - Tous les répertoires dans la valeur de nom de fichier doivent exister au préalable, à l’exception du répertoire final.  
4. Exécutez votre code T-SQL modifié.  
  - Il est inutile d’exécuter le code T-SQL de groupe de fichiers plusieurs fois, même si vous ajustez et réexécutez à plusieurs reprises le code T-SQL de comparaison de vitesse dans la sous-section suivante.  
  
  
  
 
  
    ALTER DATABASE InMemTest2  
        ADD FILEGROUP FgMemOptim3  
            CONTAINS MEMORY_OPTIMIZED_DATA;  
    go  
    ALTER DATABASE InMemTest2  
        ADD FILE  
        (  
            NAME = N'FileMemOptim3a',  
            FILENAME = N'C:\DATA\FileMemOptim3a'  
                     --  C:\DATA\    preexisted.  
        )  
        TO FILEGROUP FgMemOptim3;  
    go  
  
  
Le script suivant crée le groupe de fichiers pour vous et configure les paramètres de base de données recommandés : [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)
  
Pour plus d’informations sur `ALTER DATABASE ... ADD` pour les fichiers et groupes de fichiers, consultez :  
  
- [Options de fichiers et de groupes de fichiers ALTER DATABASE (Transact-SQL)](ALTER%20DATABASE%20File%20and%20Filegroup%20Options%20(Transact-SQL).xml)  
- [Groupe de fichiers optimisé en mémoire](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)    
  
  
## F. Test rapide pour prouver l’amélioration de la vitesse  
  
  
Cette section fournit le code Transact-SQL que vous pouvez exécuter pour tester et comparer le gain de vitesse pour INSERT-DELETE à partir de l’utilisation d’une variable de table optimisée en mémoire. Le code est composé de deux parties presque identiques sauf que, dans la première partie, le type de table est optimisé en mémoire.  
  
Le test de comparaison dure environ 7 secondes. Pour exécuter l’exemple :  
  
1. *Condition préalable :* vous devez déjà avoir exécuté le code T-SQL de groupe de fichiers de la section précédente.  
2. Exécutez le script T-SQL INSERT-DELETE suivant.  
  - Notez l’instruction « GO 5001 », qui renvoie le code T-SQL 5001 fois. Vous pouvez ajuster le nombre et l’exécuter à nouveau.  
  
Quand vous exécutez le script dans une base de données SQL Azure, veillez à effectuer l’opération à partir d’une machine virtuelle dans la même région.
  
  
    PRINT ' ';  
    PRINT '---- Next, memory-optimized, faster. ----';  
  
    DROP TYPE IF EXISTS dbo.typeTableC_mem;  
    go  
    CREATE TYPE dbo.typeTableC_mem  -- !!  Memory-optimized.  
         AS TABLE  
         (  
              Column1  INT NOT NULL INDEX ix1,  
              Column2  CHAR(10)  
         )  
         WITH  
              (MEMORY_OPTIMIZED = ON);  
    go  
    DECLARE @dateString_Begin nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_Begin, '  = Begin time, _mem.');  
    go  
    SET NoCount ON;  
    DECLARE @tvTableC dbo.typeTableC_mem;  -- !!  
  
    INSERT INTO @tvTableC (Column1) values (1), (2);  
    INSERT INTO @tvTableC (Column1) values (3), (4);  
    DELETE @tvTableC;  
  
    GO 5001  
  
    DECLARE @dateString_End nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_End, '  = End time, _mem.');  
    go  
    DROP TYPE IF EXISTS dbo.typeTableC_mem;  
    go  
  
    ---- End memory-optimized.  
    -------------------------------------------------  
    ---- Start traditional on-disk.  
  
    PRINT ' ';  
    PRINT '---- Next, tempdb based, slower. ----';  
  
    DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
    go  
    CREATE TYPE dbo.typeTableC_tempdb  -- !!  Traditional tempdb.  
        AS TABLE  
        (  
            Column1  INT NOT NULL ,  
            Column2  CHAR(10)  
        );  
    go  
    DECLARE @dateString_Begin nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_Begin, '  = Begin time, _tempdb.');  
    go  
    SET NoCount ON;  
    DECLARE @tvTableC dbo.typeTableC_tempdb;  -- !!  
  
    INSERT INTO @tvTableC (Column1) values (1), (2);  
    INSERT INTO @tvTableC (Column1) values (3), (4);  
    DELETE @tvTableC;  
  
    GO 5001  
  
    DECLARE @dateString_End nvarchar(64) =  
        Convert(nvarchar(64), GetUtcDate(), 121);  
    PRINT Concat(@dateString_End, '  = End time, _tempdb.');  
    go  
    DROP TYPE IF EXISTS dbo.typeTableC_tempdb;  
    go  
    ----  
  
    PRINT '---- Tests done. ----';  
  
    go  
  
    /*** Actual output, SQL Server 2016:  
  
    ---- Next, memory-optimized, faster. ----  
    2016-04-20 00:26:58.033  = Begin time, _mem.  
    Beginning execution loop  
    Batch execution completed 5001 times.  
    2016-04-20 00:26:58.733  = End time, _mem.  
  
    ---- Next, tempdb based, slower. ----  
    2016-04-20 00:26:58.750  = Begin time, _tempdb.  
    Beginning execution loop  
    Batch execution completed 5001 times.  
    2016-04-20 00:27:05.440  = End time, _tempdb.  
    ---- Tests done. ----  
    ***/  
  

  
  
  
## G. Prédire la consommation de mémoire active  
  
Vous pouvez apprendre à prévoir les besoins en mémoire active de vos tables optimisées en mémoire avec les ressources suivantes :  
  
- [Estimer les besoins en mémoire des tables optimisées en mémoire](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)  
- [Taille de la table et des lignes dans les tables optimisées en mémoire : exemple de calcul](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
Pour les variables de table plus importantes, les index non cluster utilisent plus de mémoire que pour les *tables* optimisées en mémoire. Plus le nombre de lignes et la clé d’index sont importants, plus la différence augmente.  
  
Si la variable de table optimisée en mémoire est accessible uniquement avec une valeur de clé exacte par accès, un index de hachage peut être un meilleur choix qu’un index non cluster. Toutefois, si vous ne pouvez pas estimer la valeur BUCKET_COUNT appropriée, un index non cluster représente une bonne alternative.  
  
## H. Voir aussi  
  
- [Tables optimisées en mémoire](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)
- [Définition de la durabilité des objets optimisés en mémoire](../../relational-databases/in-memory-oltp/defining-durability-for-memory-optimized-objects.md)  
  
  
  
  
\<!--  
CAPS Title: "Faster temp table and table variable by using memory optimization"  
  
https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/  
  
  
[ALTER DATABASE File and Filegroup Options (Transact-SQL)](http://msdn.microsoft.com/library/bb522469.aspx)  
  
[The Memory Optimized Filegroup](http://msdn.microsoft.com/library/dn639109.aspx)  
  
[Resource Governor Resource Pool](http://msdn.microsoft.com/library/hh510189.aspx)  
  
  
[Memory Optimization Advisor](http://msdn.microsoft.com/library/dn284308.aspx)  
  
[Estimate Memory Requirements for Memory-Optimized Tables](http://msdn.microsoft.com/library/dn282389.aspx)  
  
[Table and Row Size in Memory-Optimized Tables: Example Calculation](http://msdn.microsoft.com/library/dn205318.aspx)  
  
  
[Durability for Memory-Optimized Tables](http://msdn.microsoft.com/library/dn553125.aspx)  
  
[Defining Durability for Memory-Optimized Objects](http://msdn.microsoft.com/library/dn553122.aspx)  
  
[Memory-Optimized Table Variables](http://msdn.microsoft.com/library/dn535766.aspx)  
  
  
GeneMi , 2016-05-02  Monday  18:40pm  
-->  
  
  
  