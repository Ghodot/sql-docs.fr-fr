---
title: "Rechercher des expressions cl&#233;s dans les documents avec la recherche s&#233;mantique | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "recherche sémantique [SQL Server], requêtes d’expressions clés"
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 17
---
# Rechercher des expressions cl&#233;s dans les documents avec la recherche s&#233;mantique
  Explique comment rechercher des expressions clés dans des documents ou des colonnes de texte configurés pour l'indexation sémantique statistique.  
  
##  <a name="BasicsQueryKey"></a> Recherche d'expressions clés dans des documents  
  
###  <a name="howtofind"></a> Procédure : rechercher des expressions clés dans des documents avec SEMANTICKEYPHRASETABLE  
 Pour identifier les expressions clés dans des documents spécifiques, ou pour identifier des documents qui contiennent des expressions clés spécifiques, vous pouvez interroger la fonction [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
 SEMANTICKEYPHRASETABLE retourne une table avec zéro, une ou plusieurs lignes pour les expressions clés associées aux colonnes de la table spécifiée. Cette fonction d'ensemble de lignes peut uniquement être référencée dans la clause FROM d'une instruction SELECT comme tout nom de table standard.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], seuls les mots isolés sont indexés pour la recherche sémantique ; les expressions constituées de plusieurs mots (ngrams) ne sont pas indexées. En outre, des formes différentes du même mot sont indexées séparément ; par exemple, « ordinateur » et « ordinateurs » sont indexés séparément.  
  
 Pour plus d’informations sur les paramètres requis par la fonction SEMANTICKEYPHRASETABLE, ainsi que sur la table de résultats qu’elle renvoie, consultez [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
> [!IMPORTANT]  
>  L'indexation sémantique et de texte intégral doit être activée pour les colonnes que vous ciblez.  
  
###  <a name="HowToTopPhrases"></a> Exemple 1 : rechercher les expressions clés de niveau supérieur dans un document spécifique  
 L'exemple suivant extrait les 10 expressions clés de niveau supérieur du document spécifié par la variable @DocumentId dans la colonne Document de la table Production.Document de l'exemple de base de données AdventureWorks. La variable @DocumentId représente une valeur de la colonne clé de l'index de recherche en texte intégral.  
  
```tsql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 La fonction **SEMANTICKEYPHRASETABLE** récupère efficacement ces résultats en utilisant une recherche d'index au lieu d'une analyse de table.  
  
###  <a name="HowToTopDocuments"></a> Exemple 2 : rechercher les documents de niveau supérieur qui contiennent une expression clé spécifique  
 L'exemple suivant extrait les 25 documents de niveau supérieur qui contiennent l'expression clé « bracket » dans la colonne Document de la table Production.Document de l'exemple de base de données AdventureWorks.  
  
```tsql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  