---
title: L’extraction de données de résultat | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLFetchScroll function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], fetching
- SQLBindCol function
- result sets [ODBC], fetching
- fetching [ODBC]
- ODBC data types, fetching
- SQLFetch function
- SQL Server Native Client ODBC driver, data types
- SQLGetData function
ms.assetid: b289c7fb-5017-4d7e-a2d3-19401e9fc4cd
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2228bb8fcbc7237fabfb0239c62f512b9a223d28
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408208"
---
# <a name="fetching-result-data"></a>Extraction des données de résultat
  Une application ODBC offre trois options pour l'extraction des données de résultat.  
  
 La première option est basée sur [SQLBindCol](../native-client-odbc-api/sqlbindcol.md). Avant que l’extraction du résultat défini, l’application utilise **SQLBindCol** pour lier chaque colonne dans le jeu de résultats à une variable de programme. Une fois que les colonnes ont été liés, le pilote transfère les données de la ligne actuelle dans les variables liées pour les colonnes de résultats chaque fois que l’application appelle **SQLFetch** ou [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md). Le pilote gère les conversions de données si la colonne du jeu de résultats et la variable de programme possèdent des types de données différents. Si l’application a une valeur SQL_ATTR_ROW_ARRAY_SIZE supérieure à 1, il peut lier des colonnes de résultats aux tableaux de variables qui seront tous remplis lors de chaque appel à **SQLFetchScroll**.  
  
 La deuxième option est basée sur [SQLGetData](../native-client-odbc-api/sqlgetdata.md). L’application n’utilise pas **SQLBindCol** pour lier le résultat de définie les colonnes aux variables de programme. Après chaque appel à **SQLFetch**, l’application appelle **SQLGetData** une fois pour chaque colonne dans le résultat défini. **SQLGetData** demande au pilote pour transférer des données à partir d’une colonne de jeu de résultat spécifique à une variable de programme spécifique et spécifie les types de données de la colonne et de la variable. Le pilote peut ainsi convertir des données si la colonne de résultat et la variable de programme possèdent des types de données différents. **Texte**, **ntext**, et **image** colonnes sont généralement trop volumineuses pour tenir dans une variable de programme mais peuvent néanmoins être extraites à l’aide de **SQLGetData**. Si le **texte**, **ntext**, ou **image** les données dans la colonne de résultats est supérieure à la variable de programme, **SQLGetData** retourne SQL_SUCCESS_ WITH_INFO et SQLSTATE 01004 (chaîne de données tronquée à droite). Les appels successifs à **SQLGetData** retournent des segments successifs de la **texte** ou **image** données. Lorsque la fin des données est atteinte, **SQLGetData** retourne SQL_SUCCESS. Chaque extraction retourne un jeu de lignes, ou « ensemble de lignes », si SQL_ATTR_ROW_ARRAY_SIZE est supérieur à 1. Avant d’utiliser **SQLGetData**, vous devez d’abord utiliser **SQLSetPos** pour spécifier une ligne spécifique dans l’ensemble de lignes que la ligne actuelle.  
  
 La troisième option consiste à utiliser un mélange de **SQLBindCol** et **SQLGetData**. Une application peut, par exemple, lier les dix premières colonnes d’un jeu de résultats et, lors de chaque extraction, appel **SQLGetData** trois fois pour récupérer les données à partir de trois colonnes indépendantes. Cela doit généralement être utilisé lorsqu’un jeu de résultats contient un ou plusieurs **texte** ou **image** colonnes.  
  
 Selon les options de curseur définies pour le jeu de résultats, une application peut également utiliser les options de défilement de **SQLFetchScroll** pour faire défiler le jeu de résultats.  
  
 Utilisation excessive de **SQLBindCol** pour lier un résultat de colonne de jeu à une variable de programme est coûteuse, car **SQLBindCol** provoque un pilote ODBC d’allocation de mémoire. Lorsque vous liez une colonne de résultats à une variable, cette liaison demeure en vigueur jusqu'à ce que vous appeliez [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) pour libérer le descripteur d’instruction ou l’appel [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) avec *fOption* défini sur SQL_UNBIND. Les liaisons ne sont pas automatiquement annulées à la fin de l'instruction.  
  
 Cette logique vous permet de gérer avec efficacité l'exécution à maintes reprises de la même instruction avec des paramètres différents. Étant donné que le jeu de résultats conserve la même structure, vous pouvez lier le jeu de résultats qu’une seule fois, traiter les instructions SELECT, puis appelez **SQLFreeStmt** avec *fOption* défini sur SQL_UNBIND après la dernière exécution. Vous ne devez pas appeler **SQLBindCol** pour lier les colonnes dans un jeu de résultats sans appeler d’abord **SQLFreeStmt** avec *fOption* défini sur SQL_UNBIND pour libérer toutes les liaisons précédentes.  
  
 Lorsque vous utilisez **SQLBindCol**, vous pouvez procéder selon les lignes ou de liaison. La liaison selon les lignes est un tantinet plus rapide que la liaison selon les colonnes.  
  
 Vous pouvez utiliser **SQLGetData** pour récupérer des données sur une base de la colonne par colonne au lieu de lier le résultat défini à l’aide de colonnes **SQLBindCol**. Si un jeu de résultats contient uniquement quelques lignes, à l’aide **SQLGetData** au lieu de **SQLBindCol** est plus rapide ; sinon, **SQLBindCol** offre de meilleures performances. Si vous n’insérez pas toujours les données dans le même ensemble de variables, vous devez utiliser **SQLGetData** au lieu de reliaison constamment. Vous pouvez uniquement utiliser **SQLGetData** sur les colonnes qui se trouvent dans la liste de sélection une fois que toutes les colonnes sont liées avec **SQLBindCol**. La colonne doit également apparaître après toutes les colonnes sur lequel vous avez déjà utilisé **SQLGetData**.  
  
 Les fonctions ODBC qui gèrent le déplacement des données vers ou à partir de variables de programme, tel que **SQLGetData**, **SQLBindCol**, et [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md), prennent en charge le type de données implicite conversion. Par exemple, si une application lie une colonne d'entiers à une variable de programme de chaîne de caractères, le pilote convertit automatiquement les données d'entier en caractère avant de les insérer dans la variable de programme.  
  
 La conversion de données dans les applications doit être réduite. À moins que la conversion de données ne soit nécessaire pour le traitement pris en charge par l'application, les applications doivent lier les colonnes et les paramètres à des variables de programme du même type de données. En revanche, si les données doivent être converties d'un type à un autre, il est plus efficace de confier la conversion au pilote plutôt que de l'effectuer dans l'application. Normalement, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client se contente de transférer directement les données des tampons réseau vers les variables de l'application. En confiant la conversion des données au pilote, vous forcez ce dernier à mettre les données en mémoire tampon et à les convertir au moyen de cycles processeur.  
  
 Variables de programme doivent être suffisamment grandes pour contenir les données transférées à partir d’une colonne, à l’exception de **texte**, **ntext**, et **image** données. Si une application tente d'extraire les données d'un jeu de résultats et de les placer dans une variable trop petite pour les contenir, le pilote émet un avertissement. Cette opération contraint le pilote à allouer de la mémoire pour le message et le pilote et l'application doivent tous les deux utiliser des cycles processeur pour traiter le message et gérer les erreurs. L'application doit soit allouer une variable suffisamment grande pour accueillir les données extraites, soit faire appel à la fonction SUBSTRING dans la liste de sélection pour réduire la taille de la colonne au sein du jeu de résultats.  
  
 Soyez vigilant lorsque vous utilisez SQL_C_DEFAULT pour définir le type de la variable C. SQL_C_DEFAULT spécifie que le type de la variable C correspond au type de données SQL de la colonne ou du paramètre. Si SQL_C_DEFAULT pour une **ntext**, **nchar**, ou **nvarchar** colonne, les données Unicode sont retournées à l’application. Ceci peut entraîner divers problèmes si l'application n'a pas été codée pour gérer des données Unicode. Les mêmes types de problèmes peuvent se produire avec la **uniqueidentifier** type de données (SQL_GUID).  
  
 **texte**, **ntext**, et **image** données sont généralement trop volumineuses pour tenir dans une variable de programme unique et est généralement traitées avec **SQLGetData** au lieu de **SQLBindCol**. Lors de l’utilisation de curseurs côté serveur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est optimisé pour ne pas transmettre les données pour indépendant **texte**, **ntext**, ou **image** colonnes au niveau de la heure de que la ligne est extraite. Le **texte**, **ntext**, ou **image** données ne sont pas réellement récupérées à partir du serveur jusqu'à ce que les problèmes des applications **SQLGetData** pour le colonne.  
  
 Cette optimisation peut être appliquée aux applications afin qu’aucun **texte**, **ntext**, ou **image** données s’affiche pendant un utilisateur fait défiler de haut et bas d’un curseur. Une fois que l’utilisateur sélectionne une ligne, l’application peut appeler **SQLGetData** pour récupérer le **texte**, **ntext**, ou **image** données. Ceci évite de transmettre le **texte**, **ntext**, ou **image** données pour toutes les lignes que l’utilisateur ne sélectionne pas et peut empêcher la transmission de très grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](processing-results-odbc.md)  
  
  
